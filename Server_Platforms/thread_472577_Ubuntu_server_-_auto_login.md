---
title: "Ubuntu server - auto login"
date: 2007-06-13
forum: Server Platforms
---

### Post by Sunforge on 2007-06-13
I'm considering using Ubuntu server to automatically log in a single user with no real privileges and automatically start tn5250 IBM terminal emulator programme. My reasons for choosing this method are:

1. Ubuntu server appears to be a pretty minimal installation and I don't need GNOME or any other graphical interface.
2. I want the system to run in minimal RAM on a pretty low spec machine and be relatively maintenance free.
3. I won't be running any other programmes on the server except for SSH for remote management.
4. This unit will only contact other machines via 5250 and it won't be serving anything to other users.

I can get Ubuntu installed, run tn5250 on one terminal screen but have a few remaining niggles:

1. How do you get Ubuntu server to log in a named user? I can see quite a few how-to's for GNOME and other graphical sessions but nothing for a straight terminal session.

2. I've disabled CTRL-ALT-DELETE but how/where do you edit the parameter of the ALT - number key that starts up alternate sessions?

I'm open to suggestions here with the caveat that I'd like to stick with Ubuntu so that I only have one distro to worry about.

---

### Post by dmizer on 2007-06-13
just add your tn5250 start command to /etc/rc.local or some other such boot sequence daemon.  this is far safer than trying to get a user to automatically log in on a server.

/etc/rc.local has root rights, so you can start root tasks without "sudo" and without entering a password.

---

### Post by Sunforge on 2007-06-14
Your suggestion works very neatly. One further question: is this the default for running commands and short scripts that you want to run at system startup?

---

### Post by dmizer on 2007-06-14
no ... i believe the "best" way to do things is to make the script start just like any other daemon. (sshd, proftpd, samba ... etc)&#12288;so it acts more like a service and you can stop and start it as needed.  but this, i'm afraid, is beyond my knowledge.  however, there is nothing wrong with making use of /etc/rc.local either.

the downside is that to stop the terminal emulator, you'll have to find the process in something like top, and kill it.  then to restart it again, you'll have to rerun the command.

something else you should be aware of is that your /etc/rc.local may be overwritten with a kernel update.  usually this is preserved during kernel updates, so you shouldn't have to worry about it, but it's something to keep in mind if you have problems.

if you intend to have basically 100% uptime, using /etc/rc.local should cause you zero issues.

---

### Post by Sunforge on 2007-06-14
I can see that. To be honest it's beyond my knowledge to make something into a daemon too. The rc.local method works quite well and I can ssh to a terminal and kill/restart a "service" started from rc.local, which is good enough for now. 

Now all I have to do is to get my head around lp5250d and host print transforms (Gak I hate AS/400's).

---

