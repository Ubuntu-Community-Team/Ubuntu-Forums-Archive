---
title: "latency response"
date: 2008-04-28
forum: Server Platforms
---

### Post by cnsmith on 2008-04-28
I am running Ubuntu Server with out a GUI.  I use it for a web server, ssh server, NFS, and postfix.  I recently setup ldap, but currently dont have it running.  

My question is this, whenever I log into my machine via SSH it takes forever to get a response (at first).  For example, when I first login and do a `ls` or `w` command it acts as though the disks are in power saving mode and need to "wake up". However, I dont believe this is the problem becuase I recently checked my /etc/hdparm.conf file and the only think uncommented is quiet. Anyway, after the first one or two commands the server has a faster response time.

Does anyone have suggestions?

Thanks,
Cory

---

### Post by Dr Small on 2008-04-28
Are you connecting from outside the network?
There is generally a big latency with slow upstream and a remote connection.

---

### Post by cnsmith on 2008-04-29
Nope, I am connecting via LAN.

---

