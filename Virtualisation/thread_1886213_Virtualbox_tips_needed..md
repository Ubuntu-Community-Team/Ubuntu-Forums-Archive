---
title: "Virtualbox tips needed."
date: 2011-11-24
forum: Virtualisation
---

### Post by editheraven on 2011-11-24
Hello. I gonna upgrade my pc and i think of installng windows in virtualbox. Now, i know next to nothing about that. I'm not going to ask how to do it, i goona search and find. I have some questions, though
1. How virtualbox manages bootmanager from windows installer. Will it blow my grub setup?
2. Windows, in virtual box, have full driver support(assuming that the video card supports dx11, can it be used by windows apps?)
3. How dramatically is the performance reduced versus the native install?

---

### Post by teward on 2011-11-24
> 1. How virtualbox manages bootmanager from windows installer. Will it blow my grub setup?No, it wont.  Consider virtualbox VMs as virtual hard drives separate from your main hard drive.  VBox (as Virtual Box is sometimes shortened to) creates virtual hard drives for the virtual systems.  These virtual hard drives take up space on your Ubuntu main system, but do not actually impact the files on the main system.  As VBox VMs do not usually get automatically loaded on boot (i.e. you have to log into Ubuntu and then open the VirtualBox manager, and then start the VM), they wont affect GRUB in any real way, unless you install a Linux OS into the VM alongside Windows (although i dont know why you'd need to... your host machine is probably linux).

> 2. Windows, in virtual box, have full driver support(assuming that the  video card supports dx11, can it be used by windows apps?)I've had varying degrees of success with this.  Generally speaking, the VBox setups of WIndows I have are for testing ASP.NET, and I have no real need for the graphics support.  But i *have* seen setups where people have been able to play Call of Duty in semi-decent modes on Windows XP or Win 7 on a VBox'd setup. (note below where I mention the performance changes, and what I personally recommend for settings on a Windows VM and what not)

> 3. How dramatically is the performance reduced versus the native install?Little bit of background is needed for this one.  A VBox VM will always require you to apportion (that is to say, assign) a specific amount of RAM to the VM.  Therefore, if you have 4GB of RAM on your system, you can ideally assign up to about 2.5GB of that RAM without causing significant hardware lag, if all you're doing is running the Windows VM.  Most setups I use have 1GB out of 4GB RAM assigned to the VBox instance.  If your system has a graphics card, you'll have to assign some of the graphics memory to the VM as well.

Generally speaking, if you can get the recommended minimum settings for running the OS (as Microsoft says), you should not see any significant performance decrease, unless you're gaming, in which case native always beats virtualized.

I personally run two Windows Server VMs, and an XP VM and a Win7 VM off of my laptop, which isnt exactly powerful as it is.  But it works.  So if you can get the settings *just right*, it might work.  Note there's no general "just right" setup... i have had to tweak each VM separately in order to get them to run concurrently.

---

### Post by wolfen69 on 2011-11-24
> **editheraven said:**
> 
2. Windows, in virtual box, have full driver support(assuming that the video card supports dx11, can it be used by windows apps?)


No. Vbox does not use your actual video card per se, and the same with any other hardwares like audio. It creates it's own video card which is on par with integrated intel. Light gaming may be possible, but not much more. But for normal usage, performance can actually be pretty good. Just assign enough memory (including video memory) to vbox and you should be good to go.

---

### Post by philinux on 2011-11-24
Moved to virtualization forum.
This might help you.
 [https://www.virtualbox.org/wiki/User_FAQ](https://www.virtualbox.org/wiki/User_FAQ)

---

### Post by editheraven on 2011-11-26
Thank you, guys. I managed to make it work :) However, in gaming it has some performance issues :)

---

### Post by LinuxFan999 on 2011-11-28
> **editheraven said:**
> Thank you, guys. I managed to make it work :) However, in gaming it has some performance issues :)
Older games will work fine, but newer games will be very slow, if they work at all.

---

