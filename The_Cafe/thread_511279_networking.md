---
title: "networking"
date: 2007-07-27
forum: The Cafe
---

### Post by bribaetz on 2007-07-27
ok im a bit noobish here in this part of a comp can some one tell me how to start a shared network (that has username and password to be accessed by other computers in home or where every without buying a site to run off my own comp and also use windows along with ubuntu to acces files/folders
like a school network

---

### Post by bribaetz on 2007-07-27
oh and what software is available for this

---

### Post by ghandi69_ on 2007-07-27
Ok, basically, first things first your going to have to go out on the internet and research some things about setting up a home network.  You will probably want to learn how routers, switches, and hubs work.  Here are some places I would start...

[http://computer.howstuffworks.com/home-network.htm](http://computer.howstuffworks.com/home-network.htm)

Now, for the next step, and something I am just getting familiar with myself, is learning how to install and use either Samba, or NFS for linux.  I have no experience with this myself, but at least this will give you something to read about.

Setting up a network as you described will not be a simple, overnight thing, but while figuring it out you will probably learn a lot about linux and networking, which are both very valuable things to know.  Hopefully others will be able to help out here more so than I.

---

### Post by rich.bradshaw on 2007-07-27
I just use SSH.

sudo apt-get install ssh

on the server

use winscp to connect in Windows, Linux has builtin support.

For more details:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server)

---

### Post by xpod on 2007-07-27
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Thats a few of the guides that helped me understand sharing folders and accessing pc`s remotely.

EDIT:um too slow:)

---

### Post by bribaetz on 2007-07-27
one last question can i connect  wireless and Ethernet our router is Ethernet/wireless

---

