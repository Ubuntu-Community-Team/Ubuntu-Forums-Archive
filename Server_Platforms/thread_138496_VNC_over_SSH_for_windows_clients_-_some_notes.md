---
title: "VNC over SSH for windows clients - some notes"
date: 2006-03-02
forum: Server Platforms
---

### Post by rich on 2006-03-02
I wasted a small chunk of my life getting this to work yesterday, so I thought I'd post some notes in case anyone else struggles.

Begin by getting vnc itself to work. Follow Tichondrius' excellent example here
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Then you need ssh server as set out in the doc project here
[http://doc.ubuntu.com/ubuntu/serverguide/C/ch04s04.html](http://doc.ubuntu.com/ubuntu/serverguide/C/ch04s04.html)

(if you have a firewall you'll need to allow port 22 from your windows machine)

Back onto your windows box. Download putty and create a tunnel. This needs to forward port 5900 to localhost:5901. The 'localhost' is resolved at the far end of the ssh connection, so that if your windows machine is 'A' and your ubuntu box is 'B' you're tunnelling A:5900 to B:5901

This tunnel needs to be up, so start a session and log onto your ubuntu box. 

Download ultra vnc. I tried several others, fruitlessly. Then this thread

[http://www.trekweb.com/~jasonb/articles/vnc_ssh.shtml](http://www.trekweb.com/~jasonb/articles/vnc_ssh.shtml)

alerted me to the fact that loopback is disabled in many vnc clients. This behaviour just means that the viewer dies. No error message. No "I'm sorry but to make a loopback connection you'll have to edit the registry". Zip. Thanks, guys. 

Anyway, you'll need the full install of ultravnc. In the server admin properties you'll find a checkbox "Allow loopback connections". Check it. 

Finally* fire up the ultra vnc viewer and connect to localhost:0 in an excited manner. Rejoice. 



I hope this is of use to someone.

Rich


*Once rejoicing is complete you should return to your SSH config and set it up properly as per here
[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)

---

