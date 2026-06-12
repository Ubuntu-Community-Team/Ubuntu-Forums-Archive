---
title: "Ubuntu Server 9.10, ssl, security, logs and hardening"
date: 2010-01-24
forum: Security
---

### Post by mr-woof on 2010-01-24
Hello all,

In work we are currently decommising a number of older servers, my plan is bring one home to play around with it and install Ubuntu server 9.10. 

I would like to be able to confidentially install, configure, harden, use SSL, webmin etc in a Linux server environment. At the moment, we only use Windows 2003 in work, it's an avenue of IT that I could see myself working in sometime in the future.

So, I've been messing about with a virtual machine tonight, i've got it installed with a basic gui (just for now) and installed webmin. 

What other packages should I be installed? What logs should I be looking at on a daily basis? I've heard a lot of people on these good forums talking about SSL tunneling, I'd like a go of that as well :)

How do I harden the server from outside attacks? Any articles/tutorials etc that I can read? 

thanks all :)

---

### Post by cariboo on 2010-01-25
Have a look at this [stickie]("http://ubuntuforums.org/showthread.php?t=1046738"), I would also you suggest read some of the threads [here]("http://ubuntuforums.org/forumdisplay.php?f=339").

---

### Post by mr-woof on 2010-01-26
hi and thanks for the links, I'm just playing around now with a virtual machine Ubuntu 9.10 server, I've just installed dns and open SSH. 

A question, if i'm running the virtual machine in bridge mode, and i'm running an openssh server with port forwarding to that static ip. If that virtual machine was compromised by some naughty person on the internet, would they be able to get the physical windows XP desktop?

---

### Post by bodhi.zazen on 2010-01-26
> **mr-woof said:**
> A question, if i'm running the virtual machine in bridge mode, and i'm running an openssh server with port forwarding to that static ip. If that virtual machine was compromised by some naughty person on the internet, would they be able to get the physical windows XP desktop?

Short answer to that question is YES !!!

---

### Post by mr-woof on 2010-01-26
I thought that might be the answer :) Playing around with RDP it opened straight up onto the xp machine.

---

