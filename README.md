## 定时任务脚本

掘金自动签到 签到后会获得一次免费抽奖机会，自动触发免费抽奖。
执行结束发送邮件通知签到结果。

使用方法：fork 本仓库

打开浏览器，登陆掘金，F12 查看 Network 面板，复制 cookies[就是一堆key value值], 在doc目录下，F5刷新一下，然后查看那个requestHeader就能找到，不清楚的可以百度

打开 github 仓库的 Setting，选择 Secrets，新建下列 4 个仓库 Secret(不需要给邮箱发送邮件的，只添加cookie就行了)
| key | value |
| --- | ---|
| COOKIE | 值为上面复制掘金的 cookie |
| USER | 发送邮件的邮箱地址，该邮箱需要开启 SMTP |
| PASS | 该邮箱的 SMTP 密码 |
| TO | 接收邮件的邮箱 |

`注意：掘金的cookie的有效期，具体多久我也不清楚，所以需要定期更新Secret`

备注：PASS不是邮箱密码，而是你开启SMTP功能时候给的一个类似授权码的东西。

如果不需要邮件提醒。可以运行actions下边那个 notemail_juejin.yml 文件，这个执行的是index2.js 脚本，此脚本里把发送邮件功能删了。
workflow 语法查看这里 https://docs.github.com/cn/actions/using-workflows/workflow-syntax-for-github-actions#onschedule

`注意：workflow 60天没有操作就自动disable了，需要手动enable。我开始还以为secret过期了。`
