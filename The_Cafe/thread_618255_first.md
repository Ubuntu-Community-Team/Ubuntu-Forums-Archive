---
title: "first"
date: 2007-11-20
forum: The Cafe
---

### Post by bratliff on 2007-11-20
Is there a place for suggestions?

Second, and I know you know this, but there needs to be better ways to move from XP to Ubuntu that keeps your email history and contact list.

Third. I assume MInt is using your loader, not sure, but the linux installations need to recognize that there may be another linux on another partition. If I have two Ubuntu's installed or a Ubuntu and Mint installed there are problems in booting and problems seeing all the other partitions.

Fourth, the IM'S have no video from my logitech quickcam 4000 webcam. I am running 7.10 Ubuntu. 


BobinPanama

---

### Post by az on 2007-11-20
> **bratliff said:**
> Is there a place for suggestions?

Sort of.  There are threads which discuss development.  Usually, there are specs on Launchpad.net and that's where concrete ideas get hashed out.

> **bratliff said:**
> 
Second, and I know you know this, but there needs to be better ways to move from XP to Ubuntu that keeps your email history and contact list.

File a bug.  The package that is responsible for what you describe is called "Migration-assistant".  You can file a bug for ubuntu packages on launchpad.net

> **bratliff said:**
> 
Third. I assume MInt is using your loader, not sure, but the linux installations need to recognize that there may be another linux on another partition. If I have two Ubuntu's installed or a Ubuntu and Mint installed there are problems in booting and problems seeing all the other partitions.

The Ubuntu installer should detect your other operating systems.  If it doesn't, it's a bug.  If another distribution is based on Ubuntu doesn't work, you need to file a bug with them.

> **bratliff said:**
> 
Fourth, the IM'S have no video from my logitech quickcam 4000 webcam. I am running 7.10 Ubuntu. 


BobinPanama

Unplug your webcam and reboot.  Open the system log tool and view the "messages" log.  Scroll to the bottom.  Plug in your webcam and post what appears in the log after a few seconds.

---

### Post by bratliff on 2007-11-20
MInt is not the only problem. If I install two Ubuntu's one of them don't see the drives correctly. 

Where do I find Migration-assistant? I assume it is only available during installation. If so another bad feture needed in snyaptic.

---

### Post by bratliff on 2007-11-20
The message is exiting on signal 15.

bob

---

### Post by lyceum on 2007-11-20
> **bratliff said:**
> MInt is not the only problem. If I install two Ubuntu's one of them don't see the drives correctly. 

I have done this many times on different PC's with no trouble. I have dual booted with XP, Vista, Kubuntu, Mint, SuSE, OpenSuSE, other Ubuntus etc... Az is right, you need to file a bug report. 

> **bratliff said:**
> Where do I find Migration-assistant? I assume it is only available during installation. If so another bad feture needed in snyaptic.

Yes, Migration assistant is only available when you load Ubuntu. It pulls data from the dual boot or what every you are installing over. I have only gotten it to work twice in the many installs I have done. Again, bug report. That is the best way to get things fixed. 

Good luck, and remember to have fun with it :)

---

