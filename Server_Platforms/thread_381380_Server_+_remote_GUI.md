---
title: "Server + remote GUI?"
date: 2007-03-10
forum: Server Platforms
---

### Post by Tom G on 2007-03-10
Hi

i decided to set up an Ubuntu server in my basement  on an 5y old computer i still had for 'educational purposes' and as preparation for a dedicated server (because Windows servers are expensive). I searched for a videocard and found one in one of my school's old (VERY old) computers, an S3 Trio64 with 1 MiB of RAM, just to get through my POST.
Now, my question is: is there a way (any way) to get a GUI on a server (running 6.06)? And on a dedicated server? Through virtualisation or something like it?(although Remote Desktop would be a lot better) Because let's face it: with a GUI it's easier to access and view certain things.

And it'd be perfect if i could connect to the server with windows, since we use that in school. but that's not a neccesity.


edit: i just found something...

[http://ubuntuforums.org/showthread.php?t=380140](http://ubuntuforums.org/showthread.php?t=380140)

Maybe the apt-get install (k/x)ubuntu-desktop works?

---

### Post by Mr. C. on 2007-03-10
I'm not sure exactly which packages you need to install the desktop.  Give the one you suggest a shot, and if anything is missing, the dependencies should be pulled in.

Once you have the desktop, use something like VNC to connect to your server's desktop to control it remotely.

As far as connecting with Windows, I presume you mean file sharing.  Answer yes.  Solution: Samba.

MrC

---

### Post by Nikron on 2007-03-10
Uhh... you realize server installs have all the same repos as the desktop installs....  I'm pretty sure the desktop install is basically a slightly different kernel with the ubuntu-desktop package already installed.  To get a GUI all you really need is xorg and whatever window manager/desktop environment you want.  For example, for VNC purposes I have xorg and fluxbox installed on my server.

---

### Post by Tom G on 2007-03-11
> **Nikron said:**
> Uhh... you realize server installs have all the same repos as the desktop installs....  I'm pretty sure the desktop install is basically a slightly different kernel with the ubuntu-desktop package already installed.  To get a GUI all you really need is xorg and whatever window manager/desktop environment you want.  For example, for VNC purposes I have xorg and fluxbox installed on my server.

So i don't need any videocard?

> **Mr. C. said:**
> I'm not sure exactly which packages you need to install the desktop.  Give the one you suggest a shot, and if anything is missing, the dependencies should be pulled in.

Once you have the desktop, use something like VNC to connect to your server's desktop to control it remotely.

As far as connecting with Windows, I presume you mean file sharing.  Answer yes.  Solution: Samba.

MrCactually, i ment remote desktop with windows.... but i think that'd be possible with VNC, right?

---

### Post by Rizado on 2007-03-11
> **Tom G said:**
> Actually, i ment remote desktop with windows.... but i think that'd be possible with VNC, right?Yah, that's right.

Ubuntu server installation is a installation without X if I remember correctly.

---

### Post by Nikron on 2007-03-11
You need a videocard on the server if you want a remote GUI, I believe.  I may be wrong, but I'm pretty sure most remote programs have the server render everything.

---

### Post by gaten on 2007-03-11
> You need a videocard on the server if you want a remote GUI, I believe. I may be wrong, but I'm pretty sure most remote programs have the server render everything.

No, I'm sorry but that is incorrect, no video card is needed for remote VNC sessions. 

Using something like TightVNC, you can easily set up a "headless" server (I have this setup at home), which uses no video card.

I believe this is the guide I followed (it was a long time ago), this should get you started. Google around for "headless vnc +ubuntu" if you need some more info, or ask me and I'll see if I can help.

You could also set up SSH and port forwarding so that you could SSH into the server from anywhere, then use TightVNC client to view your server as well. This site will help with that (at least conceptually): [http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)

---

### Post by Nikron on 2007-03-11
My bad, didn't really know... anyway this is a good tightvnc guide that I followed and worked perfectly 

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

