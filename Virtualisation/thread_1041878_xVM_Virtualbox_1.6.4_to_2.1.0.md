---
title: "xVM Virtualbox 1.6.4 to 2.1.0"
date: 2009-01-17
forum: Virtualisation
---

### Post by charonred on 2009-01-17
I'm running Hardy 8.04.1 and have xVM Virtualbox 1.6.4 installed with guest OS's - Intrepid, XP(SP3), Vista(SP1) and Win7(beta); and want to upgrade to the newer version 2.1.0

Simple question; do I uninstall 1.6.4 first, or just run 2.1.0 to upgrade it?

---

### Post by pansz on 2009-01-17
Both are the same, if you install 2.1.0 with apt-get, it will automatically uninstall your 1.6.4.

---

### Post by charonred on 2009-01-17
I'm using the Sun Microsystems' version of xVM Virtualbox, not the xVM Virtualbox Open Source edition available from Ubuntu via apt-get; so I assume that means I'll have to manually uninstall 1.6.4 before installing 2.1.0 ?

---

### Post by charonred on 2009-01-25
*Bump*

---

### Post by techstop on 2009-01-27
Have you actually *tried* anything? If in doubt, give it a go.

I was running 2.0.x (the non-OS edition) and got prompted to upgrade to 2.1.x. I downloaded the .deb, uninstalled the old version through synaptic, installed the new deb and loaded up VB. It then prompted me to accept some changed configuration files for the new version, then loaded up my old virtual machines like nothing had changed.

Go on, give it a go! What have you got to lose? :)

---

### Post by jack frost on 2009-01-27
> **charonred said:**
> I'm running Hardy 8.04.1 and have xVM Virtualbox 1.6.4 installed with guest OS's - Intrepid, XP(SP3), Vista(SP1) and Win7(beta); and want to upgrade to the newer version 2.1.0
 
Simple question; do I uninstall 1.6.4 first, or just run 2.1.0 to upgrade it?
 
 
I know it is off topic; but how is the vm of windows beta 7?  I saw a download for it.  I am currently running xp vm inside 8.04 64 bit.

---

### Post by HotShotDJ on 2009-01-27
> **charonred said:**
> I'm using the Sun Microsystems' version of xVM Virtualbox, not the xVM Virtualbox Open Source edition available from Ubuntu via apt-get; so I assume that means I'll have to manually uninstall 1.6.4 before installing 2.1.0 ?You will find that if you add the Sun Virtualbox repositories (see instruction about 1/2 way down this page: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)) that you'll have an easier time keeping track of upgrades and installing them.  While simply upgrading from the official Sun version of 1.6.4 should go with out a hitch, if you want to be particularly careful, you could completely uninstall it first (but leave your ~/.VirtualBox director intact!).  I think that is only necessary if you are moving from the OSE version to the PUEL version.

> **jack frost said:**
> I know it is off topic; but how is the vm of windows beta 7?  I saw a download for it.  I am currently running xp vm inside 8.04 64 bit.According to the VirtualBox web site, version 2.1.2 supports Windows 7 beta (see: [http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog) )

---

### Post by charonred on 2009-01-27
techstop
nah, I haven't tried anything, just wanted to make sure it wouldn't mess with existing VMs, and if I needed to uninstall 1.6.4 first or just upgrade, but will give it a go.

I'm still feeling my way around Linux, and have been using 'Hardy' for 7 months now and it's still as fast and reliable as when I installed it; unlike XP which got so bogged down, bloated and broken within 7 months of installing it on my new PC (Jan'08 ) - it simply became unworkable; and now it won't even boot. 


jack frost
I haven't played with Win7 much, just installed it and browsed through it; basically it's just Vista, but with better hardware support (so they say) ....typical MS, big hoohah over very little at all (except for the dollars they'll probably want for it) - still, it's worth a download and install just to compare.


HotShotDJ
I just installed it as a 'Vista' OS in VBox without any probs, except for installing Guest Additions as it's not supported for Win7, so maybe another reason to upgrade

---

### Post by charonred on 2009-01-27
HotShotDJ
thanks for advice, but I'm still getting confused by a lot of Linux terminology, so how do I 
> Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list:
```
 
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
```
[COLOR="Navy"]figured it out[/COLOR]

------------------------------------

The Sun public key for apt-secure can be downloaded here. You can add this key with
```
sudo apt-key add sun_vbox.asc
```
[COLOR="Navy"]did below instead[/COLOR]

------------------------------------

or combine downloading and registering:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
[COLOR="Navy"]added Sun's key, but doesn't seem to have added the repository source[/COLOR] - however, after successfully adding source repository, Vbox 2.1.2 is now installed

------------------------------------

The key fingerprint is
```
AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
```
[COLOR="Navy"]Do I do anything with this ?[/COLOR]

------------------------------------

To install VirtualBox, do
```
apt-get install virtualbox-2.1
```
[COLOR="Navy"]installed fine once repositories were added[/COLOR] 

------------------------------------

Note: Ubuntu users might want to install the **dkms** package (not available on Debian) to ensure that the VirtualBox host kernel modules (vboxdrv and vboxnetflt) are properly updated if the linux kernel version changes uring the next apt-get upgrade. 

[COLOR="Navy"]What is **dkms**, and how do I install it ?[/COLOR] 

---

### Post by HotShotDJ on 2009-01-27
> **charonred said:**
> HotShotDJ
thanks for advice, but I'm still getting confused by a lot of Linux terminology, so how do II'm sorry.  Yes, the instructions given at that site can be perplexing to those who are not more familiar with getting around in Linux from the command line.  Try the instruction here: [http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763)

Remember, you can skip the part about Authentication and importing the key, since it looks like you've already successfully done that.

---

### Post by charonred on 2009-01-27
Got it up n running, seem to have all VMs there, will check each in turn to confirm.

Only thing is, where do I get the correct 'Guest Additions' for VBox 2.1.2 as Guest Additions 1.5.6 doesn't support Win7

---

### Post by HotShotDJ on 2009-01-28
> **charonred said:**
> Only thing is, where do I get the correct 'Guest Additions' for VBox 2.1.2 as Guest Additions 1.5.6 doesn't support Win7All you have to do is start your guest OS. After it is booted up and ready to use, make sure you are in windowed mode (as opposed to full screen), open "Devices" from the menu bar, and select "Install Guest Additions..." Normally, it will start up automatically, but if it doesn't, just open the Windows "start" menu, go to "My Computer" (or "Computer") and double click on the CD labeled "VirtualBox Guest Additions."

---

### Post by charonred on 2009-01-28
done it now, thanks again - just had to uninstall previous incompatible one first, bit of a fiddle with Win7 programs, but eventually done after couple of reboots.

---

### Post by charonred on 2009-01-28
checked the rest out

had to install guest additions in XP & Vista, but they are working fine.

Intrepid was already broken, so need to re-install anyhow

Sabayon4...DOH, forgot password, but was loading fine till login screen

gOS 3 boots and runs fine, but will have to install Guest Additions in that too

But so far VBox 2.1.2 seems to work fine

---

