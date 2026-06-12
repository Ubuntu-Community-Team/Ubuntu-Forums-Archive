---
title: "Safety of Windows 7 Virtualized in Karmic Question"
date: 2010-01-29
forum: Virtualisation
---

### Post by mikodo on 2010-01-29
Hello everyone,

Here's my situation. I am a newbie who got his first OS with Windows Vista and got hit with the Conficker Worm April 01, 2009. It compromised my banking institution contacts and generally attacked my software antimalware. I got rid of the OS and started with Ubuntu in April 2009, and couldn't be happier using Linux (Hardy and Karmic partitioned HD). I have no router for security, I just depend on the firewall provided by Ubuntu turned on with Firestarter. A friend has offered me a copy of Windows 7 Ultimate and I am intrigued by it, and would like to see what it is like. I worry about malware though. 

Question:   If I place the Windows 7 inside virtualization like Vbox, KVM, etc. and want to remove Windows because of getting myself in trouble with any nasties, can I be reasonably assured that they are gone when I remove Windows 7 and maybe reinstall again in a Virtual environment? I have no need to try to transfer data from the virtual environment to Ubuntu. 

EDIT: I fear my question(s) are too generalized to elicit responses. What I am asking is this: If I learn to use virtualization (of which I know nothing of now), and keep in mind to configure it in a way to ensure safety of my host OS (Ubuntu), can I set it up to be a safe environment? 

I have a reasonably new and fast computer with enough memory to use virtualization.

Thank you.

---

### Post by ebharv on 2010-01-29
If you can install Win7 in VirtualBox and choose do remove it then theoretically you should be fine. It all depends on how the virus/malware is coded. Simple explanation; If the virus/malware wasn't designed to run on Linux (which it more than likely won't be) your stuff should be fine. Just delete the virtual machine that VirtualBox created to remove the Win7 virtual system. You'll see this option once you start messing with VirtualBox.

---

### Post by mikodo on 2010-01-29
> **ebharv said:**
> If you can install Win7 in VirtualBox and choose do remove it then theoretically you should be fine. It all depends on how the virus/malware is coded. Simple explanation; If the virus/malware wasn't designed to run on Linux (which it more than likely won't be) your stuff should be fine. Just delete the virtual machine that VirtualBox created to remove the Win7 virtual system. You'll see this option once you start messing with VirtualBox.

Thank you. I am going to start learning and give VirtualBox a try. Not only for Windows 7, but down the road to do some testing with Alpha/Beta distro's and newer apps.

I'll mark this thread as solved after waiting to see if anyone else has any gems of info.

Mike

---

### Post by Objekt on 2010-01-29
You should be fine.  If your virtual Windows 7 machine gets infested with the latest Windows virus, you can restore it from a snapshot in seconds.  That is sure a lot easier than doing a manual reinstall.

I love Virtualbox.  It has been a great boon to me, because I still need to do stuff in Windows at times.  For example, I have one of the few printers that is not supported at all by CUPS, so I have to use it through a virtual Windows XP machine.  I can even share the printer to other Windows machines on my home network.  That is helpful to my roommate, as she is still using Windows XP for her main OS.

---

### Post by mikodo on 2010-01-29
> **Objekt said:**
> You should be fine.  If your virtual Windows 7 machine gets infested with the latest Windows virus, you can restore it from a snapshot in seconds.  That is sure a lot easier than doing a manual reinstall.

I love Virtualbox.  It has been a great boon to me, because I still need to do stuff in Windows at times.  For example, I have one of the few printers that is not supported at all by CUPS, so I have to use it through a virtual Windows XP machine.  I can even share the printer to other Windows machines on my home network.  That is helpful to my roommate, as she is still using Windows XP for her main OS.

I did some reading on Virtualbox. The snapshot feature looks like a very useful tool indeed! You and the previous poster have answered my question(s), and quieted my fears around safety. I'll mark this thread as as solved now.

Thank you.

---

### Post by Objekt on 2010-01-29
Glad we could help.  

By the way, make sure you get Virtualbox PUEL (Personal Use and Evaluation License) version for full function.  The Virtualbox in the Ubuntu "add/remove software" menu is the OSE (Open Source Edition).  Unfortunately, Virtualbox OSE does not support USB devices on the virtual machine.  I assume you will want USB support, since you are planning to connect your iPod Touch to a virtual Windows XP machine, so get Virtualbox PUEL.

For help on installing Virtualbox PUEL & making USB work, either use Google, or feel free to ask here.  This is a link to the Virtualbox PUEL download page, which also has other helpful links:
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by mikodo on 2010-01-29
> **Objekt said:**
> Glad we could help.  

By the way, make sure you get Virtualbox PUEL (Personal Use and Evaluation License) version for full function.  The Virtualbox in the Ubuntu "add/remove software" menu is the OSE (Open Source Edition).  Unfortunately, Virtualbox OSE does not support USB devices on the virtual machine.  I assume you will want USB support, since you are planning to connect your iPod Touch to a virtual Windows XP machine, so get Virtualbox PUEL.

For help on installing Virtualbox PUEL & making USB work, either use Google, or feel free to ask here.  This is a link to the Virtualbox PUEL download page, which also has other helpful links:
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Thanks for the tip, links and info on Virtualbox PUEL. I wouldn't have known about the difference between Virtualbox Puel and OSE, and no doubt would have gone into the repositories and installed OSE. I assume I will find a way to download a .deb file for the PUEL version from the links.

Again, very helpful.

Mike

---

### Post by mikodo on 2010-01-29
Well, I have Virtualbox PUEL on Ubuntu by following the link in the earlier post. Now to start learning about it. 

Thank you.

Mike

See Screenshot of the license aggreement

---

