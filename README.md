Shell bot

这是一个功能齐全的shellrunner Telegram机器人。您告诉它一个命令，它执行它并发布实时输出。您可以通过回复输出消息来将输入发送到命令。

这是一个相当复杂的示例，因为它实际上在命令中显示为终端，解释转义序列，并且如果触摸了它们的行，它将更新消息。这意味着诸如wget之类的交互式程序应该自然运行，您应该看到状态栏更新。

该机器人还允许上传或下载文件，并且还具有一个简单的文本编辑器，以方便使用。

注意：由于紧密集成，当前不支持在Windows上运行该机器人。

安装
首先安装node-pty依赖项：https://github.com/Microsoft/node-pty#dependencies

然后，例如，如果您使用的是
Ubuntu / Debian：

sudo apt install -y make python build-essential

Centos

yum install -y make python build-essential

如果您使用的是fedora：

sudo dnf install -y python
sudo dnf group install -y "C Development Tools and Libraries" 

在使用此功能之前，您应该已经为机器人获取了auth令牌，并且知道了个人用户的数字ID。如果您不知道这意味着什么，请查看博客文章以获取完整的分步指南。

git clone https://github.com/BlueSkyXN/shell-bot.git && cd shell-bot

npm install

要启动机器人(请先进入对应bot目录）（我的默认目录打开命令是cd shell-bot)

node server

第一次运行它时，它将询问您一些问题并自动创建配置文件：config.json。您也可以手动编写，请参见config.example.json。

启动后，它将在启动Bot ready.并运行时显示一条消息。为了方便起见，您可能需要与BotFather交谈并将命令列表设置为的内容commands.txt。

授权书

首次启动时，该漫游器将仅接受来自您的用户的消息。出于安全原因：您不希望任何人向您的计算机发出命令！

如果要允许其他用户使用该漫游器，请使用/token并为其提供结果链接。如果您想在网上论坛上使用此漫游器，/token则会向您发送一条消息，转发到网上论坛 。

代理服务器

shell-bot遵循https_proxyor all_proxy变量来使用代理，并支持HTTP / HTTPS / SOCKS4 / SOCKS4A / SOCKS5代理。例子：

导出 https_proxy = “ http://168.63.76.32:3128 ”
节点服务器

导出 https_proxy = “ socks://127.0.0.1:9050 ” 
节点服务器

警告：对于SOCKS代理，您需要使用IP地址（而不是DNS主机名）。

可能出现的问题
1，nodejs安装有误（安装失败，未安装，安装不完全，版本过久）

请参考这些文章

怎么更新升级node版本？           https://m.html.cn/qa/node-js/10667.html
如何在 CentOS 安装 node.js？   https://blog.csdn.net/luckydarcy/article/details/79138650
microsoft/node-pty                  https://github.com/Microsoft/node-pty#dependencies

（调整nodejs后请删除旧bot重新安装bot）

2，python环境有问题

适用于CentOS / Debian的Python 3.6一键安装脚本    https://www.moerats.com/archives/507/

也可尝试这些命令：
命令一：
python3 -m venv venv

命令二：
pip3 install virtualenv
virtualenv venv

3，Bot设置问题
获取Token：TG上加机器人（注意有认证V标）@BotFather
然后create a new bot：/newbot

BotFather：Alright, a new bot. How are we going to call it? Please choose a name for your bot.

You：XXX（Bot name）

BotFather：
Done! Congratulations on your new bot. 
You will find it at t.me/XXX. 
You can now add a description, about section and profile picture for your bot, see /help for a list of commands. 
By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. 
Just make sure the bot is fully operational before you do this.

Use this token to access the HTTP API:
一串数字：一串字母（你的Token）

Keep your token secure and store it safely, it can be used by anyone to control your bot.

For a description of the Bot API, see this page: https://core.telegram.org/bots/api

4，后台运行问题

使用screen或者宝塔SSH

5，不能yum/apt

先检查系统是不是对应的，然后sudo有没有开权限，然后自行安装对应工具

6，常用命令
https://github.com/BlueSkyXN/shell-bot/blob/master/commands.txt
