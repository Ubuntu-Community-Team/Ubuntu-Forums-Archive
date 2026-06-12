---
title: "XP does not open after Linux update"
date: 2007-11-16
forum: Virtualisation
---

### Post by jackdegroot on 2007-11-16
Hi, XP does not open anymore after I installed the Linux update. XP would be opened with Innotek Virtualbox but the computer says that I have to execute
'/etc/init.d/vboxdrvsetup'. As a complete beginner I do not know how to do that. To install Linux update I had to close the file wine.lowvoice/nl I did that.

---

### Post by jasay on 2007-11-16
Virtual Box uses what's called a kernel module to gain low level access to the host operating system (Ubuntu in this case) to allow for better performance for the guest OS (Windows).  It sounds like your Linux kernel was updated which broke the Virtual Box module.  

To fix it you need to recompile the module.  Luckily this is very easy as the developers have made a program to do it for you.  Open a terminal (Applications Menu -> Accessories -> Terminal) and copy paste the following (if you don't know, the easiest way to do this is to highlight the text and then middle click where you want it pasted):```
sudo /etc/init.d/vboxdrv setup
```You need sudo to allow the program to install the module after it finishes compiling it. Compiling also takes a fair amount of computation so don't be surprised if your CPU goes a little crazy.:)

---

