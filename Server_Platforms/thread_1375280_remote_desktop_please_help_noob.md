---
title: "remote desktop please help noob"
date: 2010-01-07
forum: Server Platforms
---

### Post by bgp. on 2010-01-07
Hey everyone,

I just started using Ubuntu. I installed Ubuntu Server 9.10 last night. I am setting up a new file server and I needed to run raid on usb external hard drives, so I decided to go with Ubuntu. I installed a gui because of my noobness as a fallback. I am going to try to do everything I need from the command line, but in case I need a gui I need a way to remotely connect to my gui, so I chose realvnc as I have run it happily on OS X and Windows. 

I installed Realvnc Enterprise, but now I have hit a dead end. I can only connect when I am logged in, running usermode. What I would like to do, is have realvnc run at start up without having to log into gnome. I would also like to set it up to attach to the current desktop session instead of creating its own. I have searched the forums and google but I cant really find what I am looking for.

Basically I would like it to run like it does on my server 03 box, runs at startup so I can log into windows remotely.

Thanks for reading and thanks for your help

bgp.

---

### Post by gordintoronto on 2010-01-07
I think the easiest thing is to set the server to autologon.  Don't fight it, embrace it.  [smile]

---

### Post by noway2 on 2010-01-07
Yes, you may need to enable remote login.  I may be wrong, but I think that this is for the remote desktop viewer application that installs by default under applications.  

I can't speak for VNC, but I can recommend that you look into FreeNX.  I believe that there is even an excellent Howto in the community documentation.  I personally use FreeNX to log into my (non server) systems both at home and at work remotely.  It works very well being both speedy and stable as well as being secure.

Ultimately you will be well served to learn how to use the command line interface and I suggest that you spend as much time as possible in the terminal prompt.  While a command line interface is more difficult for someone first learning, graphical interfaces quickly become limiting.

---

### Post by cariboo on 2010-01-07
The problem with using auto login, if the server is outward facing, it's like leaving the door wide open when you leave the house. A better solution is to use either [webmin]("http://www.webmin.com/") or ebox, which is in the repositories.

---

