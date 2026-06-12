---
title: "Home Network Server"
date: 2011-09-08
forum: Server Platforms
---

### Post by vchris on 2011-09-08
My current home network server is an old box with close to 1GB of ram and a p4 cpu running on Win XP. I'm currently using it as a file server, web server and media server.

I've been playing with Ubuntu since version 8.10 and I'm thinking of replacing xp with either xubuntu, lubuntu, ubuntu server or maybe another option I haven't heard of. I may be adding a mail server but not sure seems complicated from what I've seen. I will be setting up samba and lamp for now I guess. I rarely use the machine myself, I only access the data on the 6 drives in it. Which OS should I go with? I'd like something that takes little RAM and not too complex to setup (a GUI) but I can do some configs in the config files for some things.

---

### Post by sanderd17 on 2011-09-08
Try Lubuntu 11.04.

It has a GUI, but LXDE is very light.

certainly do not use 8.10 since it has reached the end of life (a while ago).

---

### Post by CharlesA on 2011-09-08
You could run the box without a GUI if you want and use a web-based admin tool to do admin tasks.

I've got an Ubuntu Server running 10.04 that I admin via ssh (no GUI)

---

### Post by lykwydchykyn on 2011-09-08
My personal preference for servers is Debian stable, but you'd be fine with Ubuntu Server or even Lubuntu.  It just depends on how scary the idea of a command-line-only system is to you.  Of course you can add something like Webmin or a desktop, but you'd start out at a command prompt and have to work things out from there.

You might want to look at ClearOS (based on Centos) or Zentyal (based on Ubuntu LTS), both of which are geared for home/small business servers and have much nicer web management consoles than you can get in Ubuntu.

---

