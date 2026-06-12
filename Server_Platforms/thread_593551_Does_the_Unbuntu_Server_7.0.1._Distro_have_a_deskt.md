---
title: "Does the Unbuntu Server 7.0.1. Distro have a desktop interface."
date: 2007-10-27
forum: Server Platforms
---

### Post by mdccdm2000 on 2007-10-27
Is there anyway to install or access a desktop Interface/ Gui. From the Command Prompt in a regular Unbuntu 7.0 Server Installation..... Please Respond. Thanks..... :o). :(

---

### Post by Bliepo32 on 2007-10-27
No, it doesn't have a desktop environment. A desktop environment is considered a security risk, and seen as spoilage of resources. If you want a desktop environment anyway you can try:
```

sudo apt-get install xorg gdm xubuntu-desktop
reboot

```

---

### Post by mdccdm2000 on 2007-10-27
Hello. Sir. I tried running the Sudo command provided by yours truly. But once I executed the command I recieved. an E: couldn't find package xorg. error. Via the command line. Is there anyway I can install the sudo package. From the CD rom..... Please Respond. A.S.A.P. Ciao.... :o).

---

### Post by MJN on 2007-10-27
Can you not just do **sudo apt-get install ubuntu-desktop** to get the Ubuntu Gnome GUI (or kubuntu-desktop for Kubuntu's KDE)...?

(Any and all dependencies will be installed also)

Mathew

---

### Post by mdccdm2000 on 2007-10-27
nope... ! Got the E: Couldn't Find the ubuntu-desktop package error. Again.... :o).

---

### Post by MJN on 2007-10-27
It could well be you haven't got the right repositories enabled - post the output of **cat /etc/apt/sources.list**

Note that installing one of these desktops invariably pulls a whole load of other packages/programs that you may not actually want (e.g. OpenOffice to name but many). Perhaps you need to explain exactly what you need in case our answers are based on the wrong assumptions.

Mathew

---

### Post by Railsbuntu on 2007-10-27
Hi,

Ubuntu server Edition + GUI = Ubuntu Desktop Edition

That's basically the picture. 

The Ubuntu Server Edition comes with the minimal software installed so that you have the least security risk. It's up to you to add the missing stuff.

Typically, you set up a computer running Ubuntu Server, and you connect to it from your other OS. My server doesn't have a dedicated screen nor a mouse. Only a keyboard is required for the bios to boot correctly.

Currently I am accessing my Ubuntu server thourgh my Win XP computer using Putty, and it works perfectly. :guitar:

---

### Post by kerry_s on 2007-10-27
why did you start another thread for the same thing?
[http://ubuntuforums.org/showthread.php?p=3645178#post3645178](http://ubuntuforums.org/showthread.php?p=3645178#post3645178)

---

