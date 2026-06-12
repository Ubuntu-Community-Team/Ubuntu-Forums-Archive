---
title: "Windows activation in virtual desktop (dual boot system)"
date: 2008-04-22
forum: Virtualisation
---

### Post by gecko3940 on 2008-04-22
I dual boot xp and ubuntu 7.10, and only use the xp for some purchased games, adobe acrobat, shockwave games on firefox, and microsoft office. 
I have one oem version of xp and was wondering if I could use it as a guest OS within say Virtual box on Ubuntu host, and keep the existing xp installation. My question is: would I have problems with windows activation? If so, is there an alternative (wine doesnt work well for me)?

---

### Post by warbread on 2008-04-23
Yeah.  The purpose of Windows activation is to keep you from using using one license on more than one system.  There will be problems.  There are no legal alternatives.

---

### Post by supremedalek on 2008-04-26
I've always thought the idea was you cannot use it in more than one machine at a time.

---

### Post by seamuso on 2008-04-26
> **gecko3940 said:**
> I dual boot xp and ubuntu 7.10, and only use the xp for some purchased games, adobe acrobat, shockwave games on firefox, and microsoft office. 
I have one oem version of xp and was wondering if I could use it as a guest OS within say Virtual box on Ubuntu host, and keep the existing xp installation. My question is: would I have problems with windows activation? If so, is there an alternative (wine doesnt work well for me)?

You'll start triggering windows activation on each boot between the physical install hardware profile and the virtual machine. If you plan on just using XP as a virtual and never booting to the physical install again, you're safe.

You could go the alternative route .. Install virtualbox in XP and set up a virtual that directly accesses your Ubuntu install.

> **supremedalek said:**
> I've always thought the idea was you cannot use it in more than one machine at a time.

One license, one machine .. not one license with the install on multiple machines (regardless of only having one active at a time).

That's why XP isn't transportable .. you build a new machine, you're supposed to buy a new copy of XP.

At this point, I think Vista Ultimate Retail is the only one that allows an install to both a physical machine and virtual on the same computer.

---

### Post by gecko3940 on 2008-04-28
Thanks for your help. On scouring various threads, I came across a way to get around windows activation, I just wondered whether anyone has tried this (involves copying some system 32 files):

[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

---

### Post by damis648 on 2008-04-28
Do not use that! Use the file found here on rapidshare: [http://rapidshare.com/files/24049112/patch.zip.html](http://rapidshare.com/files/24049112/patch.zip.html) this has no viruses, however a good antivirus like norton may block it because it is a "Hacktool" as it calls it. Disable your anti virus (autoprotect for norton, however you probably will not have antivirus on the VM at this point so it doesnt matter) and download it, extract and run it on the machine that needs to be activated. Have fun :)

PS. "One machine, one license".... think about it... is the windows installation really on more than one machine??

---

### Post by timjohn7 on 2008-05-09
I have an interesting problem... my legal copy of XP Pro was installed in VirtualBox some weeks ago and the Activation grace period has now expired.  I have a number of Activation Bypass hacks, but as I cannot boot in anything other than Safe Mode, I have no access to my shared folders to access the hacks.  I also have no internet access from my VirtualBox.  Where can I put the hack files to access them in Safe Mode in VirtualBox?  VBox is running under Hardy and I still have a native Windows partition.

---

