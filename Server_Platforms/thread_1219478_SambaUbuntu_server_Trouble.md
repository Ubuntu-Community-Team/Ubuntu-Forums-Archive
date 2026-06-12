---
title: "Samba/Ubuntu server Trouble"
date: 2009-07-21
forum: Server Platforms
---

### Post by Arkaman on 2009-07-21
Ok, So I just installed Ubuntu server on a computer that I don't use much anymore.  It installed ok and I got samba installed.  When I goto my XP machine I can go start>run and type \\tuxx now and it brings up a empty folder with "printers and faxes"  When I right click I can't make a folder or anything.  I'm kinda stuff and I was wondering how to make it so that windows users can do what they want with the server drive tuxx. Such as make folders add files delete files.  If there is anyway it could be password based and not authentication based.  Cuz I would like it people could connect and do stuff.  Like friends, and stuff.  So if you know any good tutorials to do this or if you will help me that would be great.  I'll have my servers keyboard close.

thanks

---

### Post by swerdna on 2009-07-21
Tuxx is probably the network name of the server, and all that's shared there is a printer folder, which is not for files. So you should  add shared directories to the server configuration. Here is a basic tutorial for samba in Ubuntu 9.04 which you can extrapolate to your ubuntu release:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")
But if you're only interested in how to craft shares, look at the section titled  "Part II: Defining and Using File Shares" in this tutorial on advanced Samba server: 
[Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("hthttp://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

