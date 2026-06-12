---
title: "Lock screen after inactivity"
date: 2008-10-08
forum: Server Platforms
---

### Post by john-boy on 2008-10-08
Hi all,
I have Ubuntu 8.04 server running without the GUI desktop installed. 

If I log onto my server, do a bit of work and then get up and make a cup of coffee without logging off, I'd like the server to lock the screen/log me off after a short period of inactivity so that when I come back, I have to re-enter my logon details again.

Is this possible and how would I go about achieving this? 

I thought adding this line to /etc/profile would do it but this just logs me off after 60 seconds, even if I am typing.
TMOUT=60

Thanks.

---

### Post by erwall on 2008-10-08
> **john-boy said:**
> Hi all,
I have Ubuntu 8.04 server running without the GUI desktop installed. 

If I log onto my server, do a bit of work and then get up and make a cup of coffee without logging off, I'd like the server to lock the screen/log me off after a short period of inactivity so that when I come back, I have to re-enter my logon details again.

Is this possible and how would I go about achieving this? 

I thought adding this line to /etc/profile would do it but this just logs me off after 60 seconds, even if I am typing.
TMOUT=60

Thanks.

I may be wrong, but I thought you could set a blank screen for the screen saver and have it lock the screen when the screensaver is activated?

---

### Post by john-boy on 2008-10-08
Thanks for the reply and if you have the graphical desktop installed then I am sure you are right. But I have installed the server without a GUI so I don't think this is an option for me. If I am wrong then please let me know.

As this server is meant to be a minimal install then installing any extras such as a screensaver or desktop wouldn't be ideal.

---

### Post by erwall on 2008-10-08
> **john-boy said:**
> Thanks for the reply and if you have the graphical desktop installed then I am sure you are right. But I have installed the server without a GUI so I don't think this is an option for me. If I am wrong then please let me know.

As this server is meant to be a minimal install then installing any extras such as a screensaver or desktop wouldn't be ideal.
Ah, sorry, I misread your post, thought you said w/a gui.

---

### Post by lykwydchykyn on 2008-10-08
Check out "away" and "vlock", both in the repositories.  Not sure if you can trigger them with idle time, but you can at least lock a terminal session.

---

### Post by john-boy on 2008-10-14
Thanks very much for the input. 

I was looking at this problem from a Windows administrator point of view. Even if the Windows machine was locked away, I'd still want the screensaver to kick in after a period of inactivity and lock the screen, partly because the machine may not be kept in secured room and partly because it is possible a Windows administrator may be connecting remotely to it from their PC (so if they left their PC unlocked with a remote desktop connection and walked away from their PC, the server would be accessible to anyone walking by.)

After talking to a couple of Linux admins, they do not do this. Their approach is if the Linux server is locked down so only the 'root' admin can access it from the console and the machine is locked away in a secure room then there is no need to lock the screen after it has been left idle. 

I thought that what I was trying to achieve would be a common task that people would want to do on a Linux server but it looks like I was wrong.

I have not pursued this further as I have more urgent jobs to complete but thank you both for your assistance.

---

