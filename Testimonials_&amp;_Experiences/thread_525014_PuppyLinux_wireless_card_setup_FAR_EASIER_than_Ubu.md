---
title: "PuppyLinux wireless card setup FAR EASIER than Ubuntu's"
date: 2007-08-13
forum: Testimonials &amp; Experiences
---

### Post by EtniesBMX on 2007-08-13
After using Ubuntu for almost a year now (I am currently running Kubuntu 7.04), I have decided to venture into using other operating systems. I gave Puppy Linux, a very small OS, a try. To my surprise, setting up a wireless connection was orders of magnitude faster and simpler on Puppy than on Ubuntu. 

I use a Netgear wg111v1 USB wireless card to connect to the internet. 

To get this wireless card functioning properly on Ubuntu, it took me up to 20 min AFTER I found a wiki ([https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)). It is worth mentioning that I actually had to enter the MAC address (a fairly tedious and undesireable process) into a file while installing the card with Ubuntu. I also had to restart the computer.

On Puppy, there is an internet connection wizard. On it's first boot, it found the wireless card and asked which driver I'd like to install. I used the ndiswrapper option and pointed it towards the proper .inf file. A new wlan0 interface was found so I clicked it. Immediatly it showed the wireless networks in range. I connected and here I am. I was completely running in less than 2 minutes, without reboot, and witout entering a MAC  address. 

While I definitely appreciate the nice step-by-step wiki that helped me connect under Ubuntu, the easier installation in Puppy is more appealing to myself, and I would imagine anyone else in my situation. I understand that wireless networking is far more difficult than wired networking, but perhaps the developers at Ubuntu should take a look at PuppyLinux's intuitive, friendly approach to improve and simplify the process on Ubuntu.

---

### Post by wolfen69 on 2007-08-14
with a compatible wireless card, it takes 10 seconds in ubuntu. to say it's a pain when something is incompatible(initially) is kind of obvious.

---

### Post by dptxp on 2007-08-14
> **EtniesBMX said:**
> After using Ubuntu for almost a year now (I am currently running Kubuntu 7.04), I have decided to venture into using other operating systems. I gave Puppy Linux, a very small OS, a try. To my surprise, setting up a wireless connection was orders of magnitude faster and simpler on Puppy than on Ubuntu. 

I use a Netgear wg111v1 USB wireless card to connect to the internet. 

To get this wireless card functioning properly on Ubuntu, it took me up to 20 min AFTER I found a wiki ([https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)). It is worth mentioning that I actually had to enter the MAC address (a fairly tedious and undesireable process) into a file while installing the card with Ubuntu. I also had to restart the computer.

On Puppy, there is an internet connection wizard. On it's first boot, it found the wireless card and asked which driver I'd like to install. I used the ndiswrapper option and pointed it towards the proper .inf file. A new wlan0 interface was found so I clicked it. Immediatly it showed the wireless networks in range. I connected and here I am. I was completely running in less than 2 minutes, without reboot, and witout entering a MAC  address. 

While I definitely appreciate the nice step-by-step wiki that helped me connect under Ubuntu, the easier installation in Puppy is more appealing to myself, and I would imagine anyone else in my situation. I understand that wireless networking is far more difficult than wired networking, but perhaps the developers at Ubuntu should take a look at PuppyLinux's intuitive, friendly approach to improve and simplify the process on Ubuntu.

But for wired DHCP, you have to work in Puppy.
Puppy is nice anyway.

---

### Post by ugm6hr on 2007-08-15
> **wolfen69 said:**
> with a compatible wireless card, it takes 10 seconds in ubuntu. to say it's a pain when something is incompatible(initially) is kind of obvious.
I don't think that was the point.  The same wifi card is technically not compatible with PuppyLinux either - but installation using ndiswrapper is a lot easier with Puppy.  It would be nice if Ubuntu had a *working* GUI ndiswrapper installation procedure, ideally integrated with the default wifi manager (i.e. Network Manager in GNOME Ubuntu).  

This is essentially what Puppy does.  You select wifi / network wizard, it automatically selects your chipset (if it detects a supported chipset), or otherwise points you to ndiswrapper (suggesting that it might work), and asks you to tell it where the .inf file is.

I am not trying to say Puppy is better than Ubuntu (in fact I have essentially stopped using Puppy since installing Xubuntu), but there are some user-friendly features that Ubuntu could learn from Puppy.

---

### Post by EtniesBMX on 2007-08-15
> **ugm6hr said:**
> I don't think that was the point.  The same wifi card is technically not compatible with PuppyLinux either - but installation using ndiswrapper is a lot easier with Puppy.  It would be nice if Ubuntu had a *working* GUI ndiswrapper installation procedure, ideally integrated with the default wifi manager (i.e. Network Manager in GNOME Ubuntu).  

This is essentially what Puppy does.  You select wifi / network wizard, it automatically selects your chipset (if it detects a supported chipset), or otherwise points you to ndiswrapper (suggesting that it might work), and asks you to tell it where the .inf file is.

I am not trying to say Puppy is better than Ubuntu (in fact I have essentially stopped using Puppy since installing Xubuntu), but there are some user-friendly features that Ubuntu could learn from Puppy.

exactly.

there are a number of things ubuntu does more easily than puppy. i was just surprised at the difference in configuring the same card, both with ndiswrapper.

i mean honestly, how would a new user to ubuntu possibly know what ndiswrapper is or how to use it?

---

### Post by ugm6hr on 2007-08-16
> **EtniesBMX said:**
> i mean honestly, how would a new user to ubuntu possibly know what ndiswrapper is or how to use it?

I think it is clear that this Wizard is an important (and useful) feature for new users.

That's clear from the number of posts in these forums starting "My wireless doesn't work..."  Most users don't care what chipset they have, they just want it to work.  The Puppy wizard leads you by the hand through the various options - I had no idea what ndiswrapper was until it suggested I try it.

Given ndiswrapper is Open Source (it is, isn't it?) - there is no excuse for Ubuntu not to have it bundled (with something that works - not ndis-gtk).

---

### Post by armandh on 2007-08-16
slax works great on old ESS sound chips / cards.
I guess to get it all on one disk some main streaming is necessary.
but it is the ease of downloading needed stuff that makes ubuntu great.
If puppys wifi handling is as easy as ubuntu getting a codex,  put it in.

---

### Post by ukripper on 2007-08-16
Hope Gutsy covers most restricted drivers we are having problems with.

---

### Post by EtniesBMX on 2007-09-29
I am happy to be back in my own thread reporting the good news: I am currently on the Kubuntu 7.10 Beta1 Live CD with my netgear wg111 wifi card working with absolutely NO configuration (other than entering my password for the properly recognized wpa). 

Not only is this easier than Puppy Linux, it is now easier than Windows! I am actually posting this while the OS is being installed -- very cool.

---

### Post by ukripper on 2007-09-29
Great!! Oct 18 wil be great day for  us as Gutsy will be fully available

---

### Post by armandh on 2007-09-29
if the 7.1 live works in the wife's laptop, by by vista.

---

