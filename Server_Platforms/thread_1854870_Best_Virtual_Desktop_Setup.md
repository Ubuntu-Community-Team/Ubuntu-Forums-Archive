---
title: "Best Virtual Desktop Setup"
date: 2011-10-05
forum: Server Platforms
---

### Post by clegends on 2011-10-05
Hi folks, wondering if I could get some advice on setting up a virtual desktop environment, and whether or not it's worth it. I have a dual core atom server running a D510MO motherboard. Dual core pinetrail chipset at 1.6ghz, with 2 gb of ram. I'm running Ubuntu 10.04.1 server on it.

Currently I've been using it as a mail server, and to host a couple websites, etc. I'm wondering about also using it for a virtual desktop. I have installed Virtualbox, and setup Ubuntu 11.04 desktop inside it. Have been able to use rdesktop to access it fine, but it's soooo slow! 

So I'm wondering a few things:
1. Is there anyway to speed up rdesktop, and still get a full Unity 3d expereince?
2. If I were to run this setup natively (i.e., no virtualbox, and only using the server for my 'desktop' machine) would it be any faster? I have tried a similar setup from both my netbooks, and accessing the desktop remotely was still very slow... am wondering it it's something to do with the protocol itself.
3. Are there better ways of getting a remote desktop experience?

Ideally I'd like to be able to utilise the fast internet connection of my server (always hooked up to the internet) and the processing power which is greater than the netbook I usually work on. Also, I'd like to be able to use something like an android tablet, and have a Ubuntu experience happening from another machine. Are there any easy ways, or recommended ways, currently to do this? Thanks.

---

### Post by volkswagner on 2011-10-05
I'm not sure about 3D experience, but you may get faster performance using ssh -X.  Yes, rdesktop can be slow.

try

```
ssh -X user@serverDesktop gimp
``` 

You can add the program at the end of the ssh command like above, or just enter the program name once you have an ssh session open, provided you used the -X switch.

---

### Post by lcman on 2011-10-05
> **clegends said:**
> Hi folks, wondering if I could get some advice on setting up a virtual desktop environment, and whether or not it's worth it. I have a dual core atom server running a D510MO motherboard. Dual core pinetrail chipset at 1.6ghz, with 2 gb of ram. I'm running Ubuntu 10.04.1 server on it.

Currently I've been using it as a mail server, and to host a couple websites, etc. I'm wondering about also using it for a virtual desktop. I have installed Virtualbox, and setup Ubuntu 11.04 desktop inside it. Have been able to use rdesktop to access it fine, but it's soooo slow! 

So I'm wondering a few things:
1. Is there anyway to speed up rdesktop, and still get a full Unity 3d expereince?
2. If I were to run this setup natively (i.e., no virtualbox, and only using the server for my 'desktop' machine) would it be any faster? I have tried a similar setup from both my netbooks, and accessing the desktop remotely was still very slow... am wondering it it's something to do with the protocol itself.
3. Are there better ways of getting a remote desktop experience?

Ideally I'd like to be able to utilise the fast internet connection of my server (always hooked up to the internet) and the processing power which is greater than the netbook I usually work on. Also, I'd like to be able to use something like an android tablet, and have a Ubuntu experience happening from another machine. Are there any easy ways, or recommended ways, currently to do this? Thanks.

The server looks really weak to me! You really can't expect it to perform any faster than it is now. I'd recommend at least a quad core with 4GB of RAM for that kind of setup.

---

### Post by [S|G] on 2011-10-05
Using a desktop remotely is usually slow due to connection latency and bandwidth limits. You could set up a server outside virtualbox but I doubt it would be any better since you'd have to use VNC which is a lot slower than RDP. You could try NoMachine's NX as an alternative, though. 

In any case, I wouldn't expect to be able to have a Full Unity 3D experience remotely - in fact I'd recommend turning off as many bells and whistles as possible (including unity itself) to improve usability.

---

### Post by clegends on 2011-10-16
Thanks for eveyones thoughts. I've given up on this idea for now. Cheers.

---

