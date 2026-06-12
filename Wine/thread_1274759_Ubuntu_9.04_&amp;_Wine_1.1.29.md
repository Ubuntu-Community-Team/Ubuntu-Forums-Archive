---
title: "Ubuntu 9.04 &amp; Wine 1.1.29"
date: 2009-09-24
forum: Wine
---

### Post by Dave Lee on 2009-09-24
Hey folks, brand new here. I'm trying to install Wine 1.1.29 on Ubuntu 9.04. I keep getting this error: Dependency is not satisfiable: libaudio2" I have tried fixing the issue in Synaptic Package Manager. No luck. I've tried other versions of Wine. No luck. I have a desktop computer running XP with internet. The Ubuntu laptop is not connected to the internet. My goal is to also install XP on the laptop using wine. If there is some other way to go about it, please let me know so I can stop banging my head against a wall!
Thanks!

---

### Post by JDShu on 2009-09-24
For the dependency issue, try to install libaudio2, so either find the package in synaptic, or open the terminal and type "sudo apt-get install libaudio2"

For XP though, it sounds like you want to virtualize Windows on Jaunty. Look into VirtualBox OSE (sudo apt-get install virtualbox)

---

### Post by Dave Lee on 2009-09-24
By virtualize, do you mean install the OS over Ubuntu? I don't really want to retain Ubuntu. It's a client's computer and since I have little to no experience with linux or its variants, I wanted to ask how I could use Ubuntu to install Windows XP.
 
So, a couple questions, then.
1. If I use that command line in the terminal, does it require an active internet connection?
 
2. Would Virtualbox allow me to install XP as the only Operating System?
 
Oh, and BTW, that command line for apt-get says :
"libaudio2 is not available, but is referred to by another package. This may mean that the package is missing, has been obsolete, or is only available from another source. E: Package libaudio2 has no installation candidate"
 
What should I do?

---

### Post by hikaricore on 2009-09-25
If you want to istall XP on the computer as the only OS then boot from xp cd...

---

### Post by Dave Lee on 2009-09-25
That sounds pretty easy, but I already tried that, and with no luck. For some reason, it ignored the cd like it wasn't there. And yes, It was in the right order in the BIOS. 
Now, I know the CD will work if launched as an executable in Windows, cause I tested it on a Windows computer. It'll load up just fine. Evidently, it's not the bootable type or something.
So, my questions still stands. Where can I find the solution to my libaudio2 dependency problem? Is there a .deb file that I can install, and if so, where is the link to it?

---

### Post by Dave Lee on 2009-09-25
UPDATE: Wine is installed, now when I tried to run the setup executable for XP with wine, nothing happened. I right-clicked and clicked on Open with Wine Program Loader" Anyone help?

---

### Post by hikaricore on 2009-09-25
**You can't install Windows through WINE.**  How else can I explain this?
You are going to need to find a way to boot from the cd..

---

### Post by zupal1461 on 2009-09-25
Use java's virtualbox... although i have no idea how to install it yet..

currently, i am using win xp as my host and ubuntu linux as my guest with the help of virtualbox.

---

### Post by hikaricore on 2009-09-25
No you don't get it, he's trying to install Windows through linux as the ONLY operating system.
Virtualization is of no help in this strange case.

---

### Post by zaduma on 2009-09-25
You have to boot from CD

---

