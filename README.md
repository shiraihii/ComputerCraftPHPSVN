# ComputerCraftPHPSVN
An Young Simple and Native subversion system for ComputerCraft of MInecraft

下载链接:http://mcsjtu.me/download.php?owner=shiraihii&filename=sae

废话不多说, 这次英文版的介绍我就不写了, 光写个中文版的说明就行. 

这是一个用lua实现的能在Minecraft电脑MOD(ComputerCraft)环境下跑的集总式文件版本管理系统的客户端代码(也就是电脑MOD的代码啦), 服务器代码我暂时不放出来, 等有机会再放吧, 还有一些功能没有实现, 囧. 

Q: 为什么需要这样一个东西呢, 你不是写了个从[gitlub上拖代码自动运行的程序](https://github.com/shiraihii/ComputerCraftAutoDownloader)吗, 自己再建一个不是蛋疼吗?
  - 蛋是有点疼, 我去吃点药. 
  - 在Minecraft里面直接编辑电脑MOD的代码是在是太不爽了, 行数太少, 还不能用快捷键和鼠标.   
  - 在使用这个从github上拖代码的程序过程中, 我们难免会遇到, 有时候代码有语法错误或者逻辑错误, 需要边在Minecraft里面调试边修改的情况, 调试完了还需要把程序修改过的地方存下来上传. 
  - 那个程序能从github上拖程序, 但没法往github上传程序啊.
  - 于是就写了个既能拖代码下来又能传上去的程序. 

Q: 你这个程序在哪下啊?
  - 下载(sae)(http://mcsjtu.me/download.php?owner=shiraihii&filename=sae)这个文件, 放进电脑MOD里面, 关于怎么放进去, 那个蛋疼的[gitlub上拖代码自动运行的程序](https://github.com/shiraihii/ComputerCraftAutoDownloader)的README里面已经写个了例子, 改一下地址就行
  - 这个程序在新浪云上有副本, [查看程序](http://mcsjtu.me/view.php?owner=shiraihii&filename=sae), 下载程序链接http://mcsjtu.me/download.php?owner=shiraihii&filename=sae 其实这个程序本身就被这个系统托管着.

Q: 你这个程序我怎么用啊?
  - 在电脑MOD里面运行sae会给出程序用法说明. 这里再详细说一下. 
  - sae register
    - 注册帐号, 目前本程序还处于公测期, 注册需要邀请码, 您需要的话只要给社团邮箱mcsjtu@sina.com或者我邮箱shiraihii@yahoo.co.jp发一封邮件说明情况即可.
    - 会提示输入用户名, 密码, 确认密码, 还有邀请码. 输入完成以后会连接服务器注册. 
    - 服务器会返回注册成功与否, 并显示在终端里面
    - 用户名不要长于32个字符, 只能使用英文数字和下划线, 密码不能短于6个字符.
  - sae pull \<owner\> \<filename\> \<dest\> \[\<version\>\]
    - 这个命令用来下载版本库中的文件.
    - 这个系统中, 没有repo的概念, 每个文件单独是一个repo. 
    - 每个文件有一个拥有者, 即上传者. 
    - 每个人可以上传名字相同的文件, 系统会储存在每个人的账户下面, 而不会混淆. 
    - 文件可以被拥有者设为私有, 这样其他用户不能下载这个文件. 文件默认是公开的, 除非被拥有者设为私有(TODO).
    - 文件可以被拥有者共享给另外一个账户(TODO), 并控制他是否可以上传.
    - 说了这么多废话, 我们来说说这个pull命令怎么用. 
    - owner是拥有者的名字, filename是文件名, dest是这个文件下下来之后存放的位置(强制覆盖, 操作的时候要小心). 
    - 对于私有文件, 会要求输入用户名和密码. 
  - sae list
    - 列出服务器上存在的文件列表和详细信息. 
    - 暂时信息有点多, 翻页很不爽, 我会想办法解决的. 
  - sae push \<filename\>
    - 这个命令用来上传文件. 
    - 会要求输入用户名和密码.
    - 然后会要求输入拥有者用户名, 因为拥有者可以对其他人开发修改权限. 如果是上传到自己的账户, 留空(直接回车)即可. 
    - 要求输入版本注释, 必须输入不能留空, 否则会被服务器拒收, 可以多行输入, 输入完后按两次回车确定.
  - sae token \<owner\> \<filename\>
    - 解释下这个token, 在有些场景中(比如说10个机器人跑一样的代码, 修改完一个以后要求其他自动更新, 需要自动下载程序, 而这个程序又是私有的), 需要自动下载一个私有的文件, 在代码中直接写入用户名和密码直接访问服务器固然可以但并不安全.
    - token可以用来授权下载私有文件, 输入这个命令后, 会要求输入用户名和密码.
    - 然后会返回一个8位的token, 用于自动下载文件(TODO, 实现这个平台上的自动更新).

Q: 这东西有什么限制吗?
  - 上传文件限制在50000字节以内(约3500行代码). 
  - 文件名不得含有特殊字符.
  - 文件中不能含有非ASCII字符. 

Q: 我只能在电脑MOD里面上传和下载吗?
  - 当然不, 您可以用网页[注册](http://mcsjtu/register.php), [下载或查看](http://mcsjtu.me/download.php), [上传](http://mcsjtu.me/upload.php), [查看文件列表](http://mcsjtu.me/list.php), 网页做的很丑陋, 以后有空可能会改进.

TODO:
 - 邮箱密码找回.
 - 电脑MOD内查看信息用上下键翻页.
 - 允许设置私有, 部分共享和全公开.
 - 自动用Token下载文件.
 - sae程序本身自动检查更新.
有什么问题和意见欢迎提Issue.
  
