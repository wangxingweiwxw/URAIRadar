首先在此感谢TrendRadar大佬的项目。在此基础上最近都在玩知乎AI Works板块下的Vibe Coding项目，早早就得知了AI Works板块下面的使用知乎开放数据接口。当时就有一些预感知乎将要打开skill技能让Agent能够顺畅调用。现在Zhihu CLI上线体验下来非常好玩。我马上基于这个接口做了一个知乎热榜雷达，定时知乎热榜自动飞书推送。这下就不会错过热点信息啦~~~
<img src="https://pic1.zhimg.com/80/v2-5179978bb3d3d6477b84f3a41759dc7b_1440w.webp?source=1def8aca" width="600" alt="截图">

如果感兴趣的话就跟着我操作一下，在有workbuddy或者codex这样的AI助理的帮助下5分钟搞定。第一步当然是把Zhihu CLI这个技能对接到相应的AI助理。这里以workbuddy为例，在助理对话窗口点左下角+调出技能下面的管理技能，然后在弹出窗口点击创建技能。然后输入框就自动加入了skill-creator，把知乎官网推荐的安装关键词“请下载安装zhihu-cli skill并完成初始化配置https://developer-cdn.zhihu.com/zhihu-cli/releases/stable/skill/zhihu-cli-skill.zip” 输入其中。然后agent就会帮你完成安装的步骤，其中会提示输入zhihu开发者API密钥，登录知乎创建并喂给workbuddy就行。
<img src="https://pic1.zhimg.com/80/v2-8d431d011115b953cad7a397f1bb9c0b_1440w.webp?source=1def8aca" width="600" alt="截图">

安装完成后workbuddy会汇总安装过程比如密钥已经进入加密凭证管理器妥善保存和Zhihu CLI的主要功能比如搜索知乎上关于某话题的讨论、拉知乎热榜、用知乎直答回答问题或列出我的收藏。
<img src="https://picx.zhimg.com/80/v2-88c76ceb1b00edb01550ecfcf45302a3_1440w.webp?source=1def8aca" width="600" alt="截图">

可以进行一次快速测试，比如小星这里的拉知乎热榜。通过Zhihu CLI中的热榜接口列出TOP20的热榜话题和链接。当然你也可以将关键字改成汽车板块热榜，回应就会是汽车方面热门话题。这里大家就会发现一个问题，一个是每次20个热榜条目看不过来，另一个就是哪些新上榜的更新项目不能一目了然。而且每次搜索还得发一条命令略显繁琐。
<img src="https://pica.zhimg.com/80/v2-813a870c19a3a4082dcadf9dbb393f5b_1440w.webp?source=1def8aca" width="600" alt="截图">

在此基础上建立一个知乎热榜雷达，定时知乎热榜自动飞书推送的想法油然而生。之前其实小星就用网络爬虫接口定时调取知乎热门话题的经验。立马动手一步一步让AI助理快速迁移和实现该功能。感兴趣的朋友可以跟着小星走一遍流程，方法如下：
第一步，将github项目贴给workbuddy并输入“基于该github项目zip包帮我用zhihu CLI skill实现类似的自动化功能，定时抓取热点发送至飞书并建立R2存储”
项目可以在小星的github仓库查找URAIRadar并打包code下载
<img src="https://pica.zhimg.com/80/v2-14beaba2c582acf39948a48144394912_1440w.webp?source=1def8aca" width="600" alt="截图">

然后workbuddy就会询问飞书群机器人的地址和R2归档的信息。其中R2归档为可选项，大家可以按需填写。目前cloudflare提供免费每月10GB的网络数据存储，不过注册过程和密钥系统稍微复杂小星这边就略过。感兴趣的朋友可以自己搜索。输入完以后workbuddy就会建立一个定时任务在工作日每两小时抓取一次TOP20热榜并推送热榜变化条目发送到飞书群聊。
<img src="https://picx.zhimg.com/80/v2-3beabf9ffa3c0c33355442452a8312b6_1440w.webp?source=1def8aca" width="600" alt="截图">

很多朋友可能会有疑问飞书群机器人要如何建立。不用担心，跟着小星一步步往下操作就行。
第一步，建立群聊，群名称可以是ZhihuRadar或者任何喜欢的群组名字。
<img src="https://picx.zhimg.com/80/v2-91e33eb572268bba5cf1f508cfc8c79f_1440w.webp?source=1def8aca" width="600" alt="截图">

第二步，群组中点击右上角三个点，然后点击设置。
<img src="https://pica.zhimg.com/80/v2-432b01576992ff938d3a9188b4b08b56_1440w.webp?source=1def8aca" width="600" alt="截图">

在设置中点击群机器人。
<img src="https://pic1.zhimg.com/80/v2-c95c3d078db779b87a0c675d68013c2c_1440w.webp?source=1def8aca" width="600" alt="截图">

然后点击添加机器人。
<img src="https://pic1.zhimg.com/80/v2-989974f83f86287b178889ec3ff32c5d_1440w.webp?source=1def8aca" width="600" alt="截图">

在弹出的窗口中选择自定义机器人。
<img src="https://picx.zhimg.com/80/v2-9bfe1a28e9077de01dd20a157d44bbec_1440w.webp?source=1def8aca" width="600" alt="截图">

然后给机器人去一个你喜欢的名字，比如ZhihuRadar、小知或者甚至刘看山都可以。点击添加。
<img src="https://picx.zhimg.com/80/v2-8aa82a666c6137c81d764eca486b2000_1440w.webp?source=1def8aca" width="600" alt="截图">
然后将跳出的webhook地址复制发送给workbuddy即可，点击完成的时候会提示安全设置确认，选择保持默认就好。
<img src="https://picx.zhimg.com/80/v2-a73d584bd9b471bb8fab0394807184cd_1440w.webp?source=1def8aca" width="600" alt="截图">
至此基于这个接口做了一个知乎热榜雷达，定时知乎热榜自动飞书推送。这下就不会错过热点信息啦~~~
更多感兴趣的功能大家可以给我留言，有空我来进一步改进。
