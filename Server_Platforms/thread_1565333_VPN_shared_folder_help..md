---
title: "VPN shared folder help."
date: 2010-08-31
forum: Server Platforms
---

### Post by eddawg128 on 2010-08-31
I am attempting to make a shared folder for people that VPN into the network. This folder needs to be accessible to windows and mac machines.  So far I have the VPN through ppptd working.  I just don't know how to make a folder. I feel like this should be fairly easy.  I am using Lucid Lynx server edition.  Thank you for any help.

---

### Post by scorp123 on 2010-09-01
SAMBA perhaps?

[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)
[http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic](http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic)

... Google will give you more results. Search for "samba ubuntu 10.04".

The idea here is that you install and run a SAMBA server. Once people are connected via VPN they then mount the shares you give them. This works tip top for Linux, Mac and Windows clients.

Depending on how you configure this you could give everyone their own private folder and then a shared 'public' folder ... that's basically how my server here in the company is configured. So each user has a private location where they can store their stuff, but they also have a location where they can upload and share things if they want or need to. And I as admin don't need to get too much involved in this, the server "just works".

So I suppose you want something like this?

---

