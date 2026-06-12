---
title: "Trouble installing 8.04 as Guest on 7.10 w/ VMware 1.0.5"
date: 2008-04-29
forum: Server Platforms
---

### Post by mvip on 2008-04-29
I'm just curious if anyone else has experienced trouble with installing Ubuntu 8.04 [Alternative / LTSP] as guest under VMWare 1.0.5. I've tried to run the installation twice and both times it seems to freeze about halfway through the installation (not at the same place though). I don't have any log files at hand, but I'm just curious if this is just my setup or a common problem.

---

### Post by Gorante on 2008-04-30
I've just installed some jeos 8.04 as guest (over vmware 1.0.5 running on a 8.04 server) and i've got some problems with vmware tools, but nothing that can't be sorted out.

No freeze during install here anyhows.

---

### Post by mctozzy on 2008-05-03
I've seen this happen installing under VMServer 2.0 beta2 as well. But if you wait long enough, it eventually continues. 

There are a few steps to getting the tools stuff working properly though. You have to install gcc and a couple of other things to get it all compiled/working.

---

### Post by DapperDanMan on 2008-05-03
I am having the same problem. Whenever a new kernel is released, VMServer is broken. Last time it was about a month after I updated that I got VM server to install. I'm going to check VMware forums to see if I can find a date for a fix.

---

### Post by DapperDanMan on 2008-05-03
I found the following at a vmserver forum 
[http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html](http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html)

Go there and follow the instructions. I am running vmserver 1.05 as we speak. I am a Linux man all the way but unfortunately I have to connect into my work place (that is why I need vmserver). I have never gotten the Cisco Linux client to work. If someone could tell me how to get the Cisco Linux client to work, I would not need vmserver :)

---

