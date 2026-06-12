---
title: "Way to make sure you don't have problems with a new release of Ubuntu"
date: 2009-11-06
forum: Testimonials &amp; Experiences
---

### Post by samh785 on 2009-11-06
The method that I always employ to lessen the chances of having critical errors on the release day of a new distro is this: install the final beta first in a virtual machine (or on a spare computer). This allows you to see a fairly close representation of what the final release will be like, and keeps you from hurting your main computer. Also this reduces stress on the servers that distribute Ubuntu on release day, because those who install the beta will have to do very little updating on the official day of release. 

Just my 2 cents.

---

### Post by HappyFeet on 2009-11-06
> **samh785 said:**
> The method that I always employ to lessen the chances of having critical errors on the release day of a new distro is this: install the final beta first in a virtual machine (or on a spare computer). This allows you to see a fairly close representation of what the final release will be like, and keeps you from hurting your main computer. Also this reduces stress on the servers that distribute Ubuntu on release day, because those who install the beta will have to do very little updating on the official day of release. 

Just my 2 cents.

Also, I might add. if you are not part of the solution, you are part of the problem. Ubuntu needs as many people as possible to test new releases. If you can't or won't take part in it, then wait a couple of months for other people to fix the problems. People are very good at letting other people fix everything, I might add. We only have ourselves to blame for any problems. It is after all, a community effort.

---

### Post by samh785 on 2009-11-06
> **HappyFeet said:**
> Also, I might add. if you are not part of the solution, you are part of the problem. Ubuntu needs as many people as possible to test new releases. If you can't or won't take part in it, then wait a couple of months for other people to fix the problems. People are very good at letting other people fix everything, I might add. We only have ourselves to blame for any problems. It is after all, a community effort.
If nothing else report the bugs :P

---

### Post by jdrodrig on 2009-11-06
> **samh785 said:**
> The method that I always employ to lessen the chances of having critical errors on the release day of a new distro is this: install the final beta first in a virtual machine (or on a spare computer). This allows you to see a fairly close representation of what the final release will be like, and keeps you from hurting your main computer. Also this reduces stress on the servers that distribute Ubuntu on release day, because those who install the beta will have to do very little updating on the official day of release. 

Just my 2 cents.

I am sorry, but I fail to see the advantage of installing the beta in a virtual machine over using the live cd of the final release (boot of the cd and try it out)...am I missing something?

---

### Post by wojox on 2009-11-06
I don't get it either. A spare computer? With different hardware than the one you want to install it on?

---

### Post by HappyFeet on 2009-11-06
> **wojox said:**
> I don't get it either. **A spare computer?** With different hardware than the one you want to install it on?

Does it matter what computer? As long as you are reporting any bugs, it's all good.  ):P

---

### Post by wojox on 2009-11-06
10-4  I got ya.

---

### Post by tgalati4 on 2009-11-06
I just put in a second hard disk or partition the existing disk.  I have at least 4 distros on each of my machines.  I always keep a long-term-support (LTS) version and then add newer distros as they become available.

You have to keep GRUB versions similar, and watch your swap partitions (don't mix 32-bit and 64-bit) and don't hibernate to disk in one distro then try to wake in another.  That generally messes things up.

---

### Post by hansdown on 2009-11-06
Ummm... Thank you?

---

### Post by JC Cheloven on 2009-11-07
> **samh785 said:**
>  (...) Also this reduces stress on the servers that distribute Ubuntu on release day, because those who install the beta will have to do very little updating on the official day of release. 

If you download vía torrent, you can download the new version the day of release without stressing the servers. In fact, if you keep seeding the torrent during some hours or days, you're helping to not stress the servers. 
It's what I did, seeding all the weekend 5 flavours of ubuntu ):P

---

### Post by 1roxtar on 2009-11-07
I waited until the Beta came out, tested it, & found bugs.  I didn't whine or cry.  I then moved on to the Release Candidate.  I have two desktops (Dell & HP), one laptop (Gateway) and a netbook (Acer Aspire One).  Karmic works perfectly on every one of them, except there is no sound on the Gateway laptop.  I'm working through it though.  Sound works with Jaunty, but doesn't with KK.  

Nevertheless, you are not gonna find me "tossing out the baby with the bathwater" as many Ubuntu and Linux fans are doing.  Ok. So there are some bugs.  Hell, even Microsoft's "savior" Windows 7, still has bugs and I am already reading about it's first Service Pack coming out soon.  I admire what Ubuntu is doing.

They are implementing so many newer technologies in the Karmic distro and I expected it to struggle in it's first few weeks. Ubuntu 10.4 Lucid Lynx is supposed to be an LTS distro, so Karmic is supposed to be the implementation of a series of new goodies for Ubuntu.  

I'm not gonna be like those Linux nerds who are too cowardly to share Ubuntu 9.10 with the masses, just because of the bugs.  Windows users are bitchin' about many of the same things with Seven as are Mac users whinin' about their "superior" Leopard.  Canonical is giving us Ubuntu for FREE so stop it with the Linux arrogance and self-righteousness. 

Give it some time, please, and support the Ubuntu/Linux/Open-Source movement.  We need your support and constructive criticism, not your condemnation.  Karmic Koala is not the new "Vista", it's a step towards a brighter future for Linux.

---

### Post by samh785 on 2009-11-07
> **jdrodrig said:**
> I am sorry, but I fail to see the advantage of installing the beta in a virtual machine over using the live cd of the final release (boot of the cd and try it out)...am I missing something?
Often when I use the live cd, I have issues that are not present after installation.

---

### Post by running_rabbit07 on 2009-11-07
If one installs the OS in a VBox, most problems will not show, because there are already drivers in place on the host OS making mostly everything run. Using a spare hard drive is a good idea, but many people here don't have the competency required for such a task as removing and installing HDDs.

The LiveCD may bring up some errors, but they won't show things that have been improved, such as kernel updates that will fix the problems that are showing up on the LiveCD. 

Basically, though the help of bug filing would be greatly helpful, if you are not capable of swapping HDDs nor making a small test partition to use for installing, then it is best to wait a few months after the release before installing it.

---

### Post by HappyFeet on 2009-11-07
> **tgalati4 said:**
> 
You have to keep GRUB versions similar, and watch your swap partitions (don't mix 32-bit and 64-bit) and don't hibernate to disk in one distro then try to wake in another.  That generally messes things up.

An even better way is to not even get grub involved in the first place. I have 3 hard drives, and just unplug 2 of them while I install on the other. Plug them all back in, and select which one to boot up upon restart. Otherwise screwing around with grub can get messy.

---

### Post by HappyFeet on 2009-11-07
> **running_rabbit07 said:**
> If one installs the OS in a VBox, most problems will not show, because there are already drivers in place on the host OS making mostly everything run. Using a spare hard drive is a good idea, but many people here don't have the competency required for such a task as removing and installing HDDs.

The LiveCD may bring up some errors, but they won't show things that have been improved, such as kernel updates that will fix the problems that are showing up on the LiveCD. 

Basically, though the help of bug filing would be greatly helpful, if you are not capable of swapping HDDs nor making a small test partition to use for installing, then it is best to wait a few months after the release before installing it.

Exactly. Spare hard drives are the best way to go.

---

### Post by FiveSidedPoly on 2009-11-07
> **HappyFeet said:**
> Also, I might add. if you are not part of the solution, you are part of the problem.
 
I just said that on here the other day! ;)
 
I haven't had issues with Karmic myself yet. I only have a few suggestions to improve the Software Center really, like showing dependencies, better descriptions all around, the download and install size, things like that. 
 
They have ClamAV as "Virus Scanner" which is ok, but I didn't install it through there because I figured it was something else. I mainly use the package manager still because of all this.

---

### Post by FiveSidedPoly on 2009-11-07
> **running_rabbit07 said:**
> If one installs the OS in a VBox, most problems will not show, because there are already drivers in place on the host OS making mostly everything run. Using a spare hard drive is a good idea, but many people here don't have the competency required for such a task as removing and installing HDDs.
 
The LiveCD may bring up some errors, but they won't show things that have been improved, such as kernel updates that will fix the problems that are showing up on the LiveCD. 
 
Basically, though the help of bug filing would be greatly helpful, if you are not capable of swapping HDDs nor making a small test partition to use for installing, then it is best to wait a few months after the release before installing it.
 
I have been installing on flash drives lately, haven't ran into any issues this way either, I'm able to get my hands on them easier then spare HDDs.
 
One thing I did notice was that one time the Live CD asked to load ATI drivers and when I booted off one flash drive it never asked for them. Not really a problem though.
 
BTW: rabbit, I really like your sig, I'm deployed to Iraq right now, leaving really soon, but I'm sure all those families and other soldiers appreciate the gesture!

---

### Post by Tamlynmac on 2009-11-07
> HappyFeet
Exactly. Spare hard drives are the best way to go. 	

I've been doing that for about two years. I keep a spare HDD specifically for testing new apps. and/or upgrades. I've yet to try KK, as our systems are cursing along just fine with 9.04. But when I do decide to install the upgrade it will be done on a separate HDD for testing purposes.

A wise ex-member of this forum is the one who suggested it to me. At the cost of a used or even new small HDD testing is a piece of cake. I wish that member where still around so I could thank him for his feedback. ;)

---

