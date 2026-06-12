---
title: "VirtualBox, Win7 freezing"
date: 2011-03-13
forum: Virtualisation
---

### Post by Shriner on 2011-03-13
While researching another issue, I ran accross something that may be what is causing Win7 to freeze while running VirtualBox.

After entering "dmesg | grep -e warn -e err" to determine any errors, I noticed that VB was running in legacy (32-bit) mode. This may be my problem, even though I have a 64-bit box and VB allowed me to install Win7 64-bit with no errors. I'm off to install the Win7 32-bit...will report my findings, but with all things 'doze, it'll take a bit......

---

### Post by Shriner on 2011-03-13
This seems to have worked. When I got to a certain point in service packing Win7 before it would freeze, I could reboot, but it would freeze again at some point shortly thereafter, regardless of whether I was trying to install that one particular update or not. 

I'm now well beyond installing that update in a 32-bit enviroment and all is well.

I don't have clue why VirtualBox will only in 32-bit and don't really care, I just have few things that I need to do under 'doze.

---

### Post by Welly Wu on 2011-03-17
I recently installed Microsoft Windows 7 Professional 32 bit and Microsoft Office Professional Plus 32 bit. I have had no problems whatsoever in installing or performing critical Windows Updates to my virtual machine under Sun/Oracle Virtualbox.

Microsoft still recommends that users choose the 32 bit version of their operating system and office suite for most general purposes.

For the record, I do own Microsoft Windows 7 Ultimate 64 bit and Office Professional Plus 64 bit among other popular Microsoft software applications with my Dreamspark and MSDN accounts, but I chose to stick with the 32 bit versions for maximum compatibility and a flawless Windows experience.

---

### Post by Shriner on 2011-03-17
Welly, I think you missed the point. I thought VB was running in 64bit, it wasn't. That was my problem. With VB running in 32bit, 64bit OSes are highly unlikely to run correctly.

---

