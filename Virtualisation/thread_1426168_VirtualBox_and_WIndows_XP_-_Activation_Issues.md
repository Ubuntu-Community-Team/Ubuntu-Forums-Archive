---
title: "VirtualBox and WIndows XP - Activation Issues"
date: 2010-03-09
forum: Virtualisation
---

### Post by gantww on 2010-03-09
Greetings,
I've re-installed Windows XP on my VirtualBox setup on the latest Ubuntu. Installation was easy and activation was not difficult. However, even after activation, it still prompts me for activation at every logon. If I click No, it doesn't let me in. If I click Yes, it brings up a page that says that the machine is activated already.

Anybody have any ideas on this one?

---

### Post by dcstar on 2010-03-10
> **gantww said:**
> Greetings,
I've re-installed Windows XP on my VirtualBox setup on the latest Ubuntu. Installation was easy and activation was not difficult. However, even after activation, it still prompts me for activation at every logon. If I click No, it doesn't let me in. If I click Yes, it brings up a page that says that the machine is activated already.

Anybody have any ideas on this one?

Yes, ask about the **Windows** issue in a** Windows** forum where people who know **Windows** may actually be.

If you had done that a few hours ago you probably have an answer by now.

Windows Activation issues have nothing to do with Ubuntu or the VM environment.

---

### Post by barclayharvey on 2010-03-10
you install windows Xp in virtual box You have to install the full  version of xp you can just pick and Tues what you want. read the virtual  box instructions on how to install other operating systems if you have  not got the manual the download it from virtual box website

---

### Post by coldraven on 2010-03-10
If your XP box is OEM you need to save a couple of files before formatting the hard drives. Otherwise when you run XP in Virtualbox it will not activate.
OEM is self activating by reading a string in your BIOS and comparing it with the OEM files on the install disk. It then writes to the following files.
You need \windows\system32\wpa.dbl and if it exists the wpa.bak files.
Keep them safe somewhere!
Just copy them into your virtual machine.

The Vbox virtual "BIOS" has some default settings that can be changed so 
read this as well [http://www.virtualbox.org/manual/ch09.html#changedmi](http://www.virtualbox.org/manual/ch09.html#changedmi)

I have not tried this but have a look [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

This does not apply if you have a COA version of XP.

Unlike the other post I think that the more people migrate to Linux the better. Some need to run Windows for legacy applications and helping them to do that must be good.
Eventually those applications will die off and we will not need M$ any more.

---

### Post by gantww on 2010-03-10
Same here. I'm only running it for the stupid VPN software for work. Otherwise I wouldn't be running windows at all. I just thought the bug might be something related to VirtualBox that I was missing, since this has run previously in VMWare without problems.

---

### Post by gantww on 2010-03-10
Just for anybody that might have the same problem in the future, it does look like it is some special issue with XP, not VirtualBox. You have to de-activate it and try it again when this happens.

[http://support.microsoft.com/kb/312295/en-us](http://support.microsoft.com/kb/312295/en-us)

Glad I'm running that OS in a VM :-)

---

