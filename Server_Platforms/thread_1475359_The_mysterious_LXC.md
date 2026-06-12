---
title: "The mysterious LXC"
date: 2010-05-06
forum: Server Platforms
---

### Post by jpl888 on 2010-05-06
I have a Ubuntu 10.04 server configured with an lxc container also running 10.04.

I wonder if somebody knows the correct procedure to move such a container to another server?  

I tried a straight rsync both with the source up and down but mysql won't start on boot after move and if I manually start it none of the websites within the container are able to connect to mysql. 

I can connect to mysql using telnet of the command line client.

I am a bit confused.

---

### Post by Adam Ryczkowski on 2010-05-08
As far as I could find there is only one unique guide how to setup a lxc virtual guest: [LXC Configure Ubuntu Lucid Containers]("http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/") by bodhi.zazen. This guide sometimes works for me and sometimes don't. Because of virtually no documentation otherwise, when something doesn't work it's very difficult to know what has gone wrong and how to fix it.

Many people say, that LXC is not yet ready for production. As you already know there is no documentation and there are multiple issues. 

I give it a try anyway, but I don't hope to have it working in less then few months :-( .

---

