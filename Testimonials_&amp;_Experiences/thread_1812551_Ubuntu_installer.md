---
title: "Ubuntu installer"
date: 2011-07-26
forum: Testimonials &amp; Experiences
---

### Post by ottosykora on 2011-07-26
@bodhi zazen

>However, it is not Ubuntu's fault if you did not understand the installation process.<

well but it is Ubuntus fault that the installer tells the user it is going to install anything 'alongside' and in fact it is overwriting the partition. If there is a serious bug in the installer, you can not blame the user. If the user selects alongside, it means it has to be installed alongside period. 
Who ever did design this kind of installer and funny dialogs coming with it, had some sweet smoke before probably.

---

### Post by bodhi.zazen on 2011-07-26
> **ottosykora said:**
> @bodhi zazen

>However, it is not Ubuntu's fault if you did not understand the installation process.<

well but it is Ubuntus fault that the installer tells the user it is going to install anything 'alongside' and in fact it is overwriting the partition. If there is a serious bug in the installer, you can not blame the user. If the user selects alongside, it means it has to be installed alongside period. 
Who ever did design this kind of installer and funny dialogs coming with it, had some sweet smoke before probably.

You are jumping to conclusions. By default the installer will install alongside and not overwrite windows.

In my experience, data loss happens when people think they are smarter then the installer, and they do not go with the defaults.

The most common reason for the OP problem comes down to

1. Not understanding how linux sees partitions.

2. Not understanding how to mount pre-existing partitions.

---

### Post by bodhi.zazen on 2011-07-26
Note: these posts were off topic from another thread.

I have never seen data loss when a user goes with the default installer options.

I have seen data loss when new users think they can out smart the installer, and they start pulling hard drives, or installing grub on the second hard drive, or they in fact change from the defaults without reading the documentation on grub or partitioning.


Yes, if you do not read the documentation, and you start changing the defaults, you will have data loss.

I have never seen Ubuntu over write windows when a user goes with the defaults and installs Ubuntu "along side" windows.

So please do not propagate misinformation and make sure people understand what they are doing before they change the defaults.

---

### Post by el_koraco on 2011-07-26
Ubiquity mostly runs like clockwork, but when it breaks, boy does it break. It has been known to kill Windows with the "install alongside" option, and I had it format /home although I made real sure I told it not to.

---

### Post by sffvba[e0rt on 2011-07-27
It is like the man said when his horse dropped dead, "Funny, he has never done that before."


404

---

### Post by Arthur_D on 2011-07-27
I always partition manually. I don't trust the defaults. Call me paranoid, but it gives me more peace of mind. :)

---

### Post by lisati on 2011-07-27
Taking the time to read what's in front of you on the screen while installing, and making sure you understand it, goes a long way to helping avoid difficulties.

---

### Post by wolfen69 on 2011-07-27
> **Arthur_D said:**
> I always partition manually. I don't trust the defaults. Call me paranoid, but it gives me more peace of mind. :)

Same here. I just re-use the existing root, home, and swap partitions when I want to reinstall.

---

### Post by stalkingwolf on 2011-07-28
I have always manually repartitioned.  A word of caution though, on newer windows systems the las few years anyway.  There is a second small windows partition.  Do not remove it.  It is a recovery partition the answer to lost recovery disks.

---

### Post by ventrical on 2011-07-28
I have two PCs with WinXP and  Ubuntu Installs. They work flawlessly and there was no problem with my installs.

So that is an Acer Aspire 3220 and a Dell GTX Desktop with Dual Boots. (Dell with Lucid and Acer with Mint).

 The Auto Installer has always worked seamlessly, especially with pendrives. The Ubuntu Install mechanisms are very craftily written and make installing a breeze and Windows Oses actually run faster in VBox on Lucid.

 I also have an Acer Extensa with Kubuntu 11.04, Linux Mint and Ubuntu Lucid and those three installers all seem compatible with each other and nothing has busted or broken yet. - and thanks for the other info.

:)

---

