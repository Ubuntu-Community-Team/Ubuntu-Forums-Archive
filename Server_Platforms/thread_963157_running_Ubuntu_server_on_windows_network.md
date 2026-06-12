---
title: "running Ubuntu server on windows network"
date: 2008-10-29
forum: Server Platforms
---

### Post by associates on 2008-10-29
Hi,

I wanted to try something different here. At the moment, i have a small network with 5 PCs (run on XP Pro) and 1 Server PC (run on Microsoft SBS 2003). What i would like to do here is to have a separate PC that run on Ubuntu 8.04 LTS Server edition (64-bit) and place this PC to the network. I suppose my objective here is to add a redundant file server to the network so that if the main server goes down, people in the office could still work without any disruption by accessing to the files on the other server (Ubuntu). I am not sure if this will work well between Microsoft and Ubuntu.

Appreciate your ideas and helps

Thank you in advance

---

### Post by bobmct on 2008-10-30
This should be no problem at all (I do it!)
I would recommend installing Ubuntu Server 8.04 and install webmin.  Then you can "manage" it from a browser on your desktop.  Using webmin (not limited to webmin) you can define your directories to share using Samba and this machine will look to the network as just another accessible server.

Good luck - its not hard!

---

