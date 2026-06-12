---
title: "Confused"
date: 2008-06-13
forum: Virtualisation
---

### Post by jnw222 on 2008-06-13
Okay, i am a total newbe at linux and i need to run windos xp in ubuntu 8.04

i need a simple solution to esisly boot xp virtually

---

### Post by jnw222 on 2008-06-13
and i am ready to clean install it on my hd

---

### Post by paulderol on 2008-06-13
Virtualbox is suggested.

 search out the install guide on the ubuntu wiki which will allow you to have hotpluggable usb support [the version in the repositories does not support usb transparency]. From there you can do a clean install of XP into the virtual machine, or you can import your backed-up files and XP install into VirtualBox. 

if you do a clean xp install inside virtualbox, it'll go much smoother too.
happy hunting!

---

### Post by ktechman on 2008-06-13
Wubi. To my understanding Wubi is the bomb for windows just read up on it.  

Cheers

---

### Post by jnw222 on 2008-06-13
i want a virtual machine
linux is my primary os and i want to easily boot xp while switching back easily

---

### Post by jnw222 on 2008-06-13
but i want a tutotril link that is very easy to follow

---

### Post by jnw222 on 2008-06-13
which software is the easiest and ho do i use it

---

### Post by ktechman on 2008-06-13
Start here.  "Use the Google Luke"

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://www.petri.co.il/virtual_installing_ubuntu_as_virtual_machine.htm](http://www.petri.co.il/virtual_installing_ubuntu_as_virtual_machine.htm)

Cheers

---

### Post by jnw222 on 2008-06-13
i think i got gemu working YAY!!!!

---

### Post by spur on 2008-06-13
This is back to front? He says linux is the primary os so he wants to virtualise windows not ubuntu. wubi does not do that.

---

### Post by hopelessone on 2008-06-13
How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial]
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

Hope Helps...

---

### Post by Victormd on 2008-06-13
> **jnw222 said:**
> Okay, i am a total newbe at linux and i need to run windos xp in ubuntu 8.04

i need a simple solution to esisly boot xp virtually

I would go with [virtualbox]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). Don't use the one in the repos though because you won't have USB support.

Your other option is to dual-boot, but it all comes down to what you want windows for. If it's for gaming, virtualbox won't do you any good, no 3D support, then you'll have to dual boot. Also, depends on how much comp. resources you have (i.e., proc., RAM, etc.) because virtual machines require quite a bit.

You can also try [WINE]("winehq.org") which will allow you to install some windows softwares under ubuntu (there is a [database]("http://appdb.winehq.org/") that lets you check if the application you want will work with wine or not)

---

### Post by Victormd on 2008-06-13
> **spur said:**
> this Is Back To Front? He Says Linux Is The Primary Os So He Wants To Virtualise Windows Not Ubuntu. Wubi Does Not Do That.

+1

---

