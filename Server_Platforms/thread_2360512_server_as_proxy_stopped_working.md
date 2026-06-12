---
title: "server as proxy stopped working"
date: 2017-05-05
forum: Server Platforms
---

### Post by micahpage on 2017-05-05
I was using SOCKS5 for a proxy and giving my server terminal the command
```
ssh -D 9999 -CfqN USERNAME@ADDRESS
```
and then would set the browsers accordingly.


This would be my setup for using my server as a proxy, however today i woke up and noticed that it is no longer working. I didnt change anything on the server. I tried using a different port but got the same result. I tried rebooting, but got the same result.

---

### Post by TheFu on 2017-05-05
**ssh -f -C -D 64000 gw.example.com -NT**
is the command I use.

If it didn't work, I'd follow normal ssh troubleshooting techniques.  
[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

