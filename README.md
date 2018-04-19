这种古怪的需求......

### 首先申请一个telegram的bot

1. Telegram上关注botfather，申请一个bot(机器人)。关注之后发送`/newbot`创建新bot，起个难听的名字比如x6A0A，之后会让你再起个username。输入之后你会得到以下回复,请记住下面那个HTTP API
> Done! Congratulations on your new bot. You will find it at `t.me/x6AOA`. You can now add a description, about section and profile picture for your bot, see /help for a list of commands. By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. Just make sure the bot is fully operational before you do this.
Use this token to access the HTTP API:
`477905544:AAxxxxxxxxxxKzl0fSeb6Z_edLQOOf4KK5w`
For a description of the Bot API, see this page: https://core.telegram.org/bots/api

2. 这时候你就可以搜索到自己刚刚创建的bot了，进去先给那个bot打个招呼。

3. 关注`userinfobot`获得自己的id，一个九位的数字，记下来。

4. 接下来小试牛刀，重构以下URL，粘贴到浏览器中回车，不出意外的话是不是收到了`我吹呀吹`几个字？？

>https://api.telegram.org/bot[替换成刚刚的HTTP API]/sendMessage?chat_id=[你步骤3中的ID]&text=我吹呀吹
>
>替换完了长这个样子
>https://api.telegram.org/bot508980960:AAExxxxx_kcLaPcqTKWTXAzlGz_vsGmuKhUR4/sendMessage?chat_id=508911160&text=我吹呀吹

5. 粘贴到浏览器里面试一下看telegram里面收到了没有

### 电脑上建立一个powershell脚本

1. 将以下脚本保存为***.ps1，替换其中【】部分
```
for(;;) {
 try {
    $ipV4 = Test-Connection -ComputerName (hostname) -Count 1  | Select IPV4Address
    $url='https://api.telegram.org/【你的API】/sendMessage?chat_id=【你的ID】&text='+$ipV4.IPV4Address
    Invoke-WebRequest $url
 }
 catch {
 }
 #十分钟发一次
 Start-Sleep 600
}
```

2. 右键运行

3. Telegram中将bot静音

### 进阶

可以用Task scheduler自动运行脚本......
