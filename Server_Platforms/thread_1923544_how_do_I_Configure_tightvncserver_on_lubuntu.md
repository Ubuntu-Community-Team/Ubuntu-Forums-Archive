---
title: "how do I Configure tightvncserver on lubuntu"
date: 2012-02-10
forum: Server Platforms
---

### Post by lance bermudez on 2012-02-10
Looked at 
[http://www.linuxformat.com/forums/viewtopic.php?p=100567](http://www.linuxformat.com/forums/viewtopic.php?p=100567) but it did not help at all. I can go from lubuntu to ubuntu but not ubuntu to lubuntu.

user@ubuntu:~$ xtightvncviewer 192.168.2.5
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
user@ubuntu:~$ vncviewer 192.168.2.5
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

Have firewall turned off and have vino installed with vino-preferences set for remote access.

did sudo tightvncserver to set the passwords

like tightvnc for
xtightvncviewer -via "pete@1.2.3.4 -p 22" -compresslevel 9 -x11cursor

---

### Post by savanna on 2012-02-11
I would start by looking thru the logs on the vncserver:

cd /var/log
sudo grep vnc * | less

See if there are any obvious errors.

---

