---
title: "New Installation Headache"
date: 2009-10-30
forum: Server Platforms
---

### Post by jonawald on 2009-10-30
Hi I have been away from Linux for a bit, but after acquiring a new Rackable Systems server to run a few services on our local network, I decided to install Ubuntu Server because I have used Ubuntu desktop and am familiar with it. The server seems to be a totally different animal especially when it comes to installing.

Now to my problem, I downloaded the ISO, and verified it using the checksum as suggested. Then I burned the CD and verified it. Everything was OK. The install started fine, I got my network configured and everything, but during the install process, I keep getting various messages that bootstrap files are corrupted. I then had the installer check if the CD was ok and everything checked out ok. 

My question is would these files be from the CD or are these files downloaded from the Internet during the install process? If they are from the CD, how can they be corrupt if the CD is ok by two different verification processes? If the files are downloaded from the Internet, I would assume that something is blocking the traffic for some reason. 

Long winded, but doggonit, I got to get to the bottom of this ASAP.

---

### Post by elvinatom on 2009-10-30
my suggestion is redownload the image.  btw you know the ubuntu server comes without a gui on default, right?  It won't be anything like ubuntu desktop.

---

### Post by jonawald on 2009-10-30
> **elvinatom said:**
> my suggestion is redownload the image.  btw you know the ubuntu server comes without a gui on default, right?  It won't be anything like ubuntu desktop.

I think I figured out the no gui part right away. I can apt-get that once I have the system installed. I just need to get it installed and running. After that I can figure things out.

---

### Post by elvinatom on 2009-10-30
I gotcha, but I don't know what to say about those errors you get - on one hand the disc is tested against the checksum and passed, but you still get corruption problems?  Are you sure your hardware is in good shape?  Flaky RAM or board etc do often introduce strange errors.

---

### Post by jonawald on 2009-10-30
The hardware is brand new. It could still be that there is something flaky about it though. I have had a bit of experience installing various flavours of operating systems on computers, but this one has stumped me more often than any other. It would not boot on a standard Ubuntu disk that I am sure worked before. It would not boot on an Old Linspire or even a Lindows CD I tried. I went mad last night and installed XP. I thought that went well till I tried getting on the network. No drivers for anything.

I will do a ram check right away when I get to it after work.

---

### Post by pi.boy.travis on 2009-10-30
> **jonawald said:**
> I think I figured out the no gui part right away. I can apt-get that once I have the system installed. I just need to get it installed and running. After that I can figure things out.

Sounds like a hardware issue to me, or perhaps you need to adjust your BIOS settings?

I would HIGHLY recommend NOT installing a GUI on a server!  It is a huge security and efficiency liability, and it ends up making things more complicated.  Use a web UI like webmin if you want to, but by any means, don't install Gnome, KDE, Xfce, or any other GUI.

Best of luck

---

### Post by jonawald on 2009-10-30
> **pi.boy.travis said:**
> ...

I would HIGHLY recommend NOT installing a GUI on a server!  It is a huge security and efficiency liability, and it ends up making things more complicated.  Use a web UI like webmin if you want to, but by any means, don't install Gnome, KDE, Xfce, or any other GUI.

Best of luck

See, this is the type of information I need too. I am a full time teacher, and don't have a whole lot of time to dedicate to this project. So I can't do all the research I want do do. I'm probably going to have another late night tonight trying to get this beast sorted out. 

What's the best way to get my hardware tested? I know I can test ram right from the Ubuntu CD, if not I have others that will do that. What's the next step after that though?

---

### Post by RC1139 on 2009-10-30
I absolutely agree. It's not a good idea to install a GUI as well as unnecessary. I just use ssh to access my server remotely from the terminal.

---

### Post by pi.boy.travis on 2009-10-31
> **jonawald said:**
> See, this is the type of information I need too. I am a full time teacher, and don't have a whole lot of time to dedicate to this project. So I can't do all the research I want do do. I'm probably going to have another late night tonight trying to get this beast sorted out. 

What's the best way to get my hardware tested? I know I can test ram right from the Ubuntu CD, if not I have others that will do that. What's the next step after that though?

The MEMTEST application on the Ubuntu CD runs indefinitely, as it is a stress test.  The longer it runs, the more load is put on your memory, the less efficient it becomes.  The general consensus is 24 hours of MEMTEST proves that your memory is in good working order.

I think I may have misunderstood your previous post.  Did you mean that no other live CD would boot on this hardware?  If not, then I would boot up the Ubuntu Desktop CD, and test as much of the hardware as you can that way.  Do some web browsing to check the LAN card, et cetera. 

If you can't boot the Ubuntu Desktop CD, what kind, if any, error messages do you get?  The more information we can get, the better.

Best Regards,

Travis

---

