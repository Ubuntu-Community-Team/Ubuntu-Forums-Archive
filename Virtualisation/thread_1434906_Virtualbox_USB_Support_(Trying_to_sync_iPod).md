---
title: "Virtualbox USB Support (Trying to sync iPod)"
date: 2010-03-20
forum: Virtualisation
---

### Post by xVehemencityx on 2010-03-20
Hiya.  I set up a Virtualbox running Windows XP Pro, and when I try to connect my iPod to it, it says there are no USB Devices connected.  I have both my iPod, and a 1TB External Hard Drive and it fails to recognize either of them.  What's the deal? (Haha)  By the way, I'm running Lucid.

---

### Post by bpalone on 2010-03-20
If you are using the OSE version there is no USB support.  If that is the case you need to go [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") and download the PUEL version.

---

### Post by areteichi on 2010-03-21
If you're having the same issue as I had, you should be able to solve it by adding your username to the groups 'vboxusers' and 'lp'.
You can do this by going to:
System > Administration > Users and Groups > Manage Groups

---

### Post by mine070 on 2010-03-21
Huh? PUEL?

---

### Post by chenxiaolong on 2010-03-21
The PUEL version of VirtualBox is the same as the OSE version of VirtualBox, except it has nonopensource features: USB support and Remote RDP support. Like bpalone said, you can download it from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

If USB doesn't work after installing the PUEL version, then follow this guide to fix it: [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml).

Also, uninstalling the OSE version and installing the PUEL version will NOT delete your settings or virtual machines.

I hope this information helps.

---

### Post by wangsuda on 2010-03-21
> **chenxiaolong said:**
> The PUEL version of VirtualBox is the same as the OSE version of VirtualBox, except it has nonopensource features: USB support and Remote RDP support. Like bpalone said, you can download it from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).


You can also read this post that has step-by-step instructions on getting VirtualBox to read the USP ports: [http://ubuntuforums.org/showthread.php?t=1365287](http://ubuntuforums.org/showthread.php?t=1365287)

---

### Post by St Nabi on 2010-03-29
Hi there, 

I have downloaded the PUEL version of Virtualbox as recommended by you and bpalone. It shows up in the Synaptic Package Manager but I can't seem to find how to access it...

---

### Post by mkvnmtr on 2010-03-29
<i believe mine is listed in the menu under system/ virtual box

---

### Post by bpalone on 2010-03-29
It will appear under Applications - System Tools.  At least that is where it is on my 8.04 machines.

Good luck.

---

### Post by wangsuda on 2010-03-29
> **bpalone said:**
> It will appear under Applications - System Tools.  At least that is where it is on my 8.04 machines.

Good luck.It is the same in Karmic as well. And it will show up after reboot.

---

