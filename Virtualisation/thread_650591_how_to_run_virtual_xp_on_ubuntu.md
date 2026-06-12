---
title: "how to run virtual xp on ubuntu"
date: 2007-12-26
forum: Virtualisation
---

### Post by icelechi on 2007-12-26
Hi,
I am have no idea how to go about running XP on Ubuntu.

I know it's possible using VMware or other virtualization programs but I don't know how to go about that.

Could anyone help. :confused:

---

### Post by jasonrandolph on 2007-12-26
I would suggest installing VirtualBox, and then following the User's Manual step-by-step through the process.  I just did it yesterday.  It's pretty easy to follow along.  My only problem is that I can't get the internet to work inside XP.

---

### Post by KCPokes on 2007-12-26
> **jasonrandolph said:**
> I would suggest installing VirtualBox, and then following the User's Manual step-by-step through the process.  I just did it yesterday.  It's pretty easy to follow along.  My only problem is that I can't get the internet to work inside XP.

If your machine is set up to use NAT, shouldn't be an issue as long as your host machine (Ubuntu) can still access the internet.  Where it gets to be fun is when you start using other network options (bridging, for example).

---

### Post by kd5ful on 2007-12-27
I tried installing VB on my Ubuntu system the other night to no avail.
...are there dependencies I'm unaware of, or did I mess up the "Gunzip" process.
I also want to be able to run a virtual XP drive under Ubuntu for my logbook (the record of duty status I'm required by law to keep) as well as some good old school games like Quake and Q2.
...Help...?
Thanks.
-James

---

### Post by wolfvorkian1 on 2007-12-27
> **icelechi said:**
> Hi,
I am have no idea how to go about running XP on Ubuntu.

I know it's possible using VMware or other virtualization programs but I don't know how to go about that.

Could anyone help. :confused:

I just did it so I'll try and give some rough pointers.

First, install Vmware server. Then click 'add a new  virtual machine'. Stick your XP disk in the cd player and follow the wizard. Just take the suggested defaults if you can. 

Check the hardware, I had to add an audio device. 

Fire it up and let it install XP. Then be sure to add the Vmware tools. 

After it has installed you ought to be able to go in to windows, control-panel, etc. and correct the resolution, I had to. Don't forget to install the tools or nothing will work right. 

Adding the audio device made the sound work. It didn't work at first because I hadn't installed the Vmware audio device and once again the 'tools'. 

The printer only worked when I used it through the network but it works okay. 

A day after I had installed XP, it crashed.. severe crash. I had to reinstall it again. Just like windows, eh?

Good luck, it is mostly a matter of fiddling around for a few hours.

---

