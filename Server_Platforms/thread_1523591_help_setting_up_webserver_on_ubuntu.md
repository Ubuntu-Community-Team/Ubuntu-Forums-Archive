---
title: "help setting up webserver on ubuntu"
date: 2010-07-03
forum: Server Platforms
---

### Post by rtllz on 2010-07-03
i been trying for quite some time to make a webserver so i can access files while im away from home but i keep running into dead ends and cant seem to set it up myself, if someone could help me i would really appreciate it...thanks

---

### Post by DJYoshaBYD on 2010-07-03
well, i actually have a server at my house, and i use the following programs to access files and stream media from my pc to ANYWHERE.. a computer, my PSP, anywhere..


This one is a web based media server.. plays videos and music.. you can also download directly from that, via http..

gnmump3d

This one is for FTP file transfers.. works very well.. sets up hella quick

vsftpd

This one, you will need to run through WINE to get it to work.. it only works on the newest version of WINE

PimpStreamer


Now, with there, I have full access to my media.. I have no static IP, so I used Dynamic DNS with a FREE domain name from [http://www.dot.tk](http://www.dot.tk)

Then, you set your dynamic DNS to forward the IP of you current connection to yourname.tk

now, if you dont have static IPs, then you will have to do port forwarding to get it to work.. If you are planning on setting up a LAMP server, then you should know how to set up your network too :)

but yeah.. those programs will give you fast and east access to your stuff..

---

### Post by DJYoshaBYD on 2010-07-03
ps.. i have 1TB of media on my server.. its all secure, and has no monitor or anything.. i access it through VNC..

its totally worth it, and easy to maintain, once you got it.. if you need help setting it up, PM me, and I can give you some pointers, using my server as an example.. i just dont want to post my URL on here, and have some kid trying to hack it.. lol.. i do Net Security for a living, so they wont get for, but DoS attacks to my router would be just shitty.. hahahahah

---

### Post by SoFl W on 2010-07-03
What problems are you running into?  Set up or access?

---

### Post by rtllz on 2010-07-04
> **DJYoshaBYD said:**
> well, i actually have a server at my house, and i use the following programs to access files and stream media from my pc to ANYWHERE.. a computer, my PSP, anywhere..


This one is a web based media server.. plays videos and music.. you can also download directly from that, via http..

gnmump3d

This one is for FTP file transfers.. works very well.. sets up hella quick

vsftpd

This one, you will need to run through WINE to get it to work.. it only works on the newest version of WINE

PimpStreamer


Now, with there, I have full access to my media.. I have no static IP, so I used Dynamic DNS with a FREE domain name from [http://www.dot.tk](http://www.dot.tk)

Then, you set your dynamic DNS to forward the IP of you current connection to yourname.tk

now, if you dont have static IPs, then you will have to do port forwarding to get it to work.. If you are planning on setting up a LAMP server, then you should know how to set up your network too :)

but yeah.. those programs will give you fast and east access to your stuff..


can you help me configure those programs to get them running ?

---

### Post by rtllz on 2010-07-04
> **SoFl W said:**
> What problems are you running into?  Set up or access?

set up

---

### Post by davetelex on 2010-07-04
I found this website useful when I set up my own web server a few weeks ago. I followed it start to finish and now I have a web server that I can do ftp and host a website. [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
I had some trouble with setting up the firewall I guess because these instructions were written a while ago but the rest of the tutorial worked fine.

---

