---
title: "xfreerdp on LTSP"
date: 2014-01-17
forum: Server Platforms
---

### Post by Pieterjan_Props on 2014-01-17
Hello,

I have following problem
I installed an ltsp server (ubuntu 12.04).
On that server, I installed xfreerdp packages

In the lts.conf I set following parameters
[PHP]
[DEFAULT]
SCREEN_07= xfreerdp
RDP_SERVER= 10.1.0.13
RDP_OPTIONS=--ignore-certificate --no-nla -f -a 24 -z -d sintguido.local --plugin drdynvc --data tsmf -- 10.1.0.13[/PHP]

the server 10.1.0.13 is our windows terminal server.
It works perfectly but I don't get a proper screen. Following screenshots describe the problem. As you can see, the icons are in right colours but all the rest gives problems. I have already searched the whole web but couldn't find a working solution for this problem.

Hope you can help me out!

thanks in advance

---

