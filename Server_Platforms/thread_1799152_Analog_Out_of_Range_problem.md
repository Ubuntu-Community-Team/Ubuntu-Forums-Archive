---
title: "Analog Out of Range problem"
date: 2011-07-07
forum: Server Platforms
---

### Post by kyral210 on 2011-07-07
I am trying to setup a Ubuntu 11.04 Server (OpenSSH) and I have hit a brick wall. Installation seems to to go ok, but then I I restart, it runs through boot and then I get a blue box saying:
[INDENT][LEFT]ANALOG
OUT OF RANGE
4.62kHz / 43Hz[/LEFT]
[/INDENT]What is causing this error and how do I fix it? I am pretty familier with Ubuntu desktop, but this is my first adventure into Server, so scary teritory.
 
 
*P.S - I am setting up the server to work as a data processor since my two desktops just aren't powerful enough to convert the data fast enough.*

---

### Post by kyral210 on 2011-07-07
Ok, I re-installed Server 11.04, made special note to set up the raid drives properly, but still the problem persists. It is like the server is putting out the wrong resolution for the monitor. I could see everything fine while seting up the server installation, so why is this happening?

---

### Post by kyral210 on 2011-07-07
PS. Before the screen dies it flashes FD0 Fatal Error, what does this mean? Is GRUB not working as it should? How do I fix this?

---

### Post by Toz on 2011-07-07
Need to determine if its just the monitor that can't display the image or whether the system is hung. 

Can you ssh into the server after you get this message?

What video card do you have?

---

### Post by kyral210 on 2011-07-07
Not tried SSH in
 
Dont know what card it is, its just the bog standard motherboard job
 
Tried it with a great and a crap monitor, both didn't work, I think it is the machine/ GRUB not the monitor

---

### Post by kyral210 on 2011-07-23
I solved this buy installing Ubuntu Server 10.10. I think the 11.04 GRUB configuration is broken, or something like that.

---

