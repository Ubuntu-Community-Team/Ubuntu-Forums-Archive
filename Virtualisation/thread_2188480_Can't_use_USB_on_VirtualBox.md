---
title: "Can't use USB on VirtualBox"
date: 2013-11-17
forum: Virtualisation
---

### Post by Lucas Malor on 2013-11-17
USB doesn't want to work on Virtualbox. I installed the Extension Pack and the Guest additions, enabled the USB 2.0 Controller, but nothing. I'm using a Windows XP guest.

USB devices are not recognized by VirtualBox itself: if I go to Settings -> USB and click to Add device, with the VM powered off, no one is listed even if my USB pen is attached and working on Linux.

I tried also to update VirtualBox to 4.3.2, but the problem remains the same.

Linux 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 17:26:33 UTC 2013 i686 athlon i686 GNU/Linux

---

### Post by softappstudio on 2013-11-18
I have an identical prblem (fatal for me) on three different Ubuntu installations.
I have tried doing* sudo chmod -a -G vboxusers grahame*    (my login name), but this does not work.
I'm sure this worked with previous versions, is there any way I can revert virtualbox until this gremlin is sorted out?
--Grahame

---

### Post by Lucas Malor on 2013-11-19
I've found it: [http://stackoverflow.com/a/20066190/1763602](http://stackoverflow.com/a/20066190/1763602)

---

### Post by VMC on 2013-11-20
> **softappstudio said:**
> I have an identical prblem (fatal for me) on three different Ubuntu installations.
I have tried doing* sudo chmod -a -G vboxusers grahame*    (my login name), but this does not work.
I'm sure this worked with previous versions, is there any way I can revert virtualbox until this gremlin is sorted out?
--Grahame
Did you try:  
```
sudo usermod -a -G vboxusers <USERNAME>
```

---

### Post by Lucas Malor on 2013-11-20
It doesn't work for me. The solution I posted on Stack Overflow works.

---

