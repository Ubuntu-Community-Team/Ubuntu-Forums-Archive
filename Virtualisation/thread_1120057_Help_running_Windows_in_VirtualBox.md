---
title: "Help running Windows in VirtualBox"
date: 2009-04-08
forum: Virtualisation
---

### Post by Flexico on 2009-04-08
I'm running Windows XP insude Ubuntu through Virtualbox.

After installing Windows on a virtual drive, it keeps asking me to register, like I did when I first installed Windows on my laptop, but my registration numbers are not accepted. Also, every other time I installed from that XP startup disk, it never asked me to register, it just installed Windows and that was that. (Except for the first time I installed.)

Also, How do I get Windows-in-Vbox to recognize my usb flash drive and/or exchange files between Windows and Ubuntu?

---

### Post by PreviousN on 2009-04-08
First of all, I'm not sure why your reg. wouldn't be recognized. General XP Home/pro licenses are only valid for 3 computers. That is, you are allowed to install it on 3 computers. You may have reinstalled windows too often, and tripped a failover at microsoft. Meaning, you may have to actually CALL microsoft and get them to reset your ability to register your copy of XP. Seriously. It's kinda a PITA. 

About the usb flash drive question, you may want to try google. It's a really common problem with a really simple answer. From what I remember, you close your running xp virtual machine (not save state). And you click on the settings of that particular vm after it has shut down. You'll then be able to check a box. And from what I remember, that's about it. 

Also, what are you using windows for? I'm not being critical, just curious. Gaming in a virtual machine sucks. And wine finally has support for office 2003 and office 2007. I almost cried the day I was able to flawlessly install office2007 in wine. It made my year. :-)

Have you tried wine?

Edit: a cursory google search gives me this: [http://lifehacker.com/385959/unlock-usb-support-for-virtualbox-in-ubuntu-hardy-heron](http://lifehacker.com/385959/unlock-usb-support-for-virtualbox-in-ubuntu-hardy-heron)

[http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host](http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host)
Should be the same for ibex.

---

### Post by linuxuser21 on 2009-04-08
Did you get your activation code from a computer with Windows already installed on it?  Mine does the same thing and it had Windows preinstalled.  Mine also had a recovery partition on it, so I'm not sure if that has something to do with it possibly.  It might have been the people that had it before me and they used it one to many times.  Virtual box also does not recognize my flash drive as well; however, it is able to run my Zune with no problem.

---

### Post by Flexico on 2009-04-10
> **linuxuser21 said:**
> Did you get your activation code from a computer with Windows already installed on it?  Mine does the same thing and it had Windows preinstalled.  Mine also had a recovery partition on it, so I'm not sure if that has something to do with it possibly.  It might have been the people that had it before me and they used it one to many times.  Virtual box also does not recognize my flash drive as well; however, it is able to run my Zune with no problem.

Nope, but I did erase my hard drive and re-install a couple of times due to viruses and crap. That must be it. I'll try calling that 800 number or something. :)

---

### Post by Flexico on 2009-04-10
> **PreviousN said:**
> First of all, I'm not sure why your reg. wouldn't be recognized. General XP Home/pro licenses are only valid for 3 computers. That is, you are allowed to install it on 3 computers. You may have reinstalled windows too often, and tripped a failover at microsoft. Meaning, you may have to actually CALL microsoft and get them to reset your ability to register your copy of XP. Seriously. It's kinda a PITA. 

About the usb flash drive question, you may want to try google. It's a really common problem with a really simple answer. From what I remember, you close your running xp virtual machine (not save state). And you click on the settings of that particular vm after it has shut down. You'll then be able to check a box. And from what I remember, that's about it. 

Also, what are you using windows for? I'm not being critical, just curious. Gaming in a virtual machine sucks. And wine finally has support for office 2003 and office 2007. I almost cried the day I was able to flawlessly install office2007 in wine. It made my year. :-)

Have you tried wine?

Edit: a cursory google search gives me this: [http://lifehacker.com/385959/unlock-usb-support-for-virtualbox-in-ubuntu-hardy-heron](http://lifehacker.com/385959/unlock-usb-support-for-virtualbox-in-ubuntu-hardy-heron)

[http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host](http://www.howtoforge.com/virtualbox-2-how-to-pass-through-usb-devices-to-guests-on-an-ubuntu-8.10-host)
Should be the same for ibex.

All right, I'll try calling.

Couldn't find the checkbox that activates USB's; I'll look a bit more...

Thanks for the warning about gaming; are you familiar with Steam? I'm trying to run Portal in Ubuntu, but when I get to the main menu screen, it's just a blank screen with a cursor. I can tell be the music and sounds that the game is running and I can click stuff, but I can't see anything.

I did try to install my Office 2007 with Wine, but it returned an error about required files missing.

If I can get most things running in Wine or else find good alternatives for Ubuntu, I might be able to forget about Windows in V-box.

I have some Windows programs that run OK in Wine, but they aren't installer-exe's, so they don't show up in the Wine menu, and I can't make shortcuts/links to the .exe files on the desktop. How would I make one of those?

---

### Post by howefield on 2009-04-10
Are you running the PUEL version of Virtualbox, which has USB support, or the OSE version which hasn't ?

(OSE version is the one in the repository, PUEL the one downloadable from the virtualbox website)

---

