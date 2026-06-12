---
title: "Setting up HAProxy on Ubuntu"
date: 2017-11-24
forum: Server Platforms
---

### Post by espressobeanmachine on 2017-11-24
So I have read the documentation but honestly without seeing an actual example of a config I am really having a hard time getting my head wrapped around this.


I have the following setup:


[https://i.imgur.com/hFuJqWb.png](https://i.imgur.com/hFuJqWb.png)


I have 1x physical baremetal machine that has Ubuntu running with HAProxy installed as an application directly on the operating system and then Docker that is running multiple containers.


[https://i.imgur.com/b7YqOo7.png](https://i.imgur.com/b7YqOo7.png)


[https://i.imgur.com/Q6gGAkd.png](https://i.imgur.com/Q6gGAkd.png)


[https://i.imgur.com/PGDCkU4.png](https://i.imgur.com/PGDCkU4.png)


Before anyone freaks out, this is just running as a temporary/example and is NOT production.


But I am not sure how to write out the HAProxy config file. I have it currently as:


[https://hastebin.com/edibifetif.cfg](https://hastebin.com/edibifetif.cfg)


I have the following domains that are going to be pointing to my public IP:



[LIST]
[*]chat.temp.com
[*]cloud1.temp.com
[*]crm.temp.com
[/LIST]


Can someone please assist me with showing the config file should be written. I am looking at this tutorial:


[https://www.upcloud.com/support/haproxy-load-balancer-ubuntu/](https://www.upcloud.com/support/haproxy-load-balancer-ubuntu/)


But I am not sure if the containers would be properly like this:


[https://hastebin.com/danuparoqi.cfg](https://hastebin.com/danuparoqi.cfg)


Can someone please help out?

---

