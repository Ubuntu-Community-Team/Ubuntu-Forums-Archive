---
title: "vboxmanage doesn't work"
date: 2009-01-18
forum: Virtualisation
---

### Post by Rohan Kapoor on 2009-01-18
I'm using Ubuntu 8.10 32 bit edition with the closed source version of Virtual Box installed because I need USB support. I have built on machine and I'm trying to clone it. The command to clone should be
```
vboxmanage clonehd
``` or ```
vboxmanage clonevdi
```, however the command replies with

```
The program 'vboxmanage' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: vboxmanage: command not found

```.

This is the open source edition which I really don't want because of the USB limitations. Can anyone help me?

---

### Post by HotShotDJ on 2009-01-18
The command is VBoxManage.  Linux is case-sensitive.  You need to type the capital and lower-case letters exactly as indicated.

---

### Post by Rohan Kapoor on 2009-01-18
Thank You! You are the man!

---

### Post by pehden on 2010-05-13
sudo apt-get install VBoxManage
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package VBoxManage



Ubuntu 10.04 server edition...... Any idea

64bit also btw.

---

### Post by foolishchild on 2010-06-16
VBoxManage is part of virtualbox-3.2

---

### Post by John Bean on 2010-06-16
Just to clarify: the OSE version uses all lower case for "vboxmanage" and the non-free version uses mixed case. They are not the same program.

If you install the non-free version you get VBoxManage automatically as part of the package, you don't need to install it separately.

---

### Post by wilee-nilee on 2010-06-16
I have always been able to just copy the vdi, from the .VirtualBox file and save it somewhere else and use it later on another Vbox no matter the OS. There is a import export appliance option as well in the puel this must be the manager.

---

### Post by John Bean on 2010-06-16
> **wilee-nilee said:**
> I have always been able to just copy the vdi, from the .VirtualBox file and save it somewhere else and use it later on another Vbox no matter the OS.

You can. But you can't run the copy on the *same* VB as the original, so if you want two copies of the same VM running at the same time you need to clone with the VB tools rather than just copy the file.

---

### Post by wilee-nilee on 2010-06-16
> **John Bean said:**
> You can. But you can't run the copy on the *same* VB as the original, so if you want two copies of the same VM running at the same time you need to clone with the VB tools rather than just copy the file.

That makes sense I just copy one that I have a license for just to make it easy and a arch setup. Funny thing is that the licensed one is in a 30 gig dynamic, but only about 6.2 gigs in size, which on a previous Vbox I forget which it was in the 3 range I couldn't get it on a HD smaller then the dynamic. But on the latest I have it running inside of Maverick on a 16 gig thumb.

---

### Post by pehden on 2010-07-06
i even tried the vboxmanage in all lower and it still file not found..im using the free one yes.

---

