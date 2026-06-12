---
title: "Installation to lenovo pc woes"
date: 2009-11-06
forum: Server Platforms
---

### Post by kindras on 2009-11-06
I have tried to install ubuntu server 9.10 on my cheap lenovo pc. I dont have the model# or anything right now. I will add it later.
 
My PC has a Broadcom ethernet BIOS that has no features at all. You cannot select boot device priority, or anything for that matter.
In order to get the PC to boot from CD, i had to disconnect the hard drive. Reboot the computer, and reconnect the hard drive once I saw the installation menu.
This was successful and I managed to install 9.10 server on my free partition i had set up.
I am using GRUB and dual booting with Vista basic.
 
I happened to select DNS server on installation, hoping i could choose more than 1 package. But the installer finished, so i realize i'd have to install the packages manually.

My problem is, I run TASKSEL, use the arrow keys to select "Manual packages"(I cant rememeber exactly what the options are) and hit enter.
Once i hit enter, text comes across the screen akwardly, and i can barely make out "mount problem"(or something to that effect)
and hit CONTROL-D to exit. I cant even get back to the shell from here. I have to reboot.
 
I am wondering if this a hardware incompatability problem, or some kind of installation error.  I tried using the command line for package installation, and when i enter
(as root, i disabled sudo)
"Tasksel install lamp-server" , it completes right away. Doesnt show or do anything, which leaves me to beleive its not executing.
 
Other things im looking for is a small guide on getting an xwindow desktop running on my server. I keep having to pipe everything to more so i can read it, since i cant scroll. I'd like to be able to run terminals. 
I was looking for network configuration utilities. I want to configure my wireless, but i dont know what to invoke to do so.
 
 
Any Suggestions?

---

### Post by awclemen on 2009-11-06
The best way I have found to install as desktop is to use:

```
sudo apt-get install ubuntu-desktop
```

Never tried tasksel... but to install the lamp server via apt-get:

```
sudo apt-get install lamp-server
```

Maybe that will get you where you want to go?

---

