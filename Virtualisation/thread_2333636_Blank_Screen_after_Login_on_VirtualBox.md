---
title: "Blank Screen after Login on VirtualBox"
date: 2016-08-11
forum: Virtualisation
---

### Post by xaltotun on 2016-08-11
Hi all, the issue I ran into is very simple. I've been using Ubuntu on VirtualBox (versions 5.0 - 5.1) for a year always the newest versions available (15.04 - 16.04) and I always install all updates. But sometime this July an update came out that brought with it a very unpleasant issue. I installed all updates in July and rebooted. The login screen was OK. After I enter the password the screen becomes blank with only the wallpaper on it. Nothing else - no icons on the left, no nothing. I can open the context menu on the wallpaper and open the terminal. 

Here is what I tried to solve this problem:
1. Reinstall - doesn't work. I create a new virtual machine, install from the CD - all is OK. After I install the latest updates I see the same blank screen after a successful login.
2. Restart different graphics services - doesn't work. I found some solutions like "restart unity", "restart graphics". No commands I found worked for me. To test if these commands resolve the issue I got to the blank screen, started the terminal from the context menu on the wallpaper and ran the commands.
3. F7/F1 - something like "switch to terminal then back" also didn't help.

I guess this issue is somehow virtualization-related because it is highly unlikely that such an issue may exist in the "native ubuntu". But I don't think it is virtualbox-related because without the July updates (I installed only the security updates but no other updates) everything works fine and has worked fine for a year.

Does anyone know any solutions? Any help would be appreciated.

---

### Post by ajgreeny on 2016-08-11
There have been some big problems with 3D displays in VMs with VBox recently, so it may be worth trying the VMs after disabling 3D display in the VM settings if you currently have 3D enabled.

Incidentally I have had problems with VBox 5.1 versions; USBs have not worked for me in the VMs so I have reverted to VBox-5.0.26 at the moment and with the exception of that 3D display problem that works fine.

---

### Post by xaltotun on 2016-08-11
"3D Acceleration" is disabled. I tried with both enabled and disabled but the result is the same. But I didn't try combinations like "install with disabled then login and enable" etc. It doesn't seem to be 3D-related. Maybe it has something to do with the XServer update? (found it among other Ubuntu updates; maybe it was something like xorg update). It is not that the graphics doesn't work, the desktop cannot start.

---

### Post by ajgreeny on 2016-08-12
What is the spec of your host machine and the OS running as host, and what resources have you allocated to the problem guests?

Do you have the correct guest additions installed in the system?

I am running Ubuntu and Xubuntu 16.04 64bit systems as guests in VBox 5.0.26 on my Xubuntu 14.04 with no difficulties at all, so I can assure you that both OSs will run in VBox.  My guests have 4GB ram allocated out of my host's 8GB, and 128MB video memory.

---

### Post by xaltotun on 2016-08-14
Guest additions installed. I usually install the ones that come with the new VirtualBox versions. When I first start a VM there is an option to insert the guest additions CD. I use it and install the guest additions. Currently I use VirtualBox 5.1.2 and the guest additions (with ls /opt) 5.1.2.
Resources and systems:
Host: Windows 7 x64
Guest: Ubuntu 16.04 x64, 2 processors, PIIX chipset, 4096 MB RAM, 128 MB Video memory. 
Other settings: VT-x enabled (in my BIOS and in the VM settings), Nested paging enabled, Audio enabled, 1 network adapter attached to NAT, 

By the way do you know if it is possible to find anything in the VM log? Or is there a Ubuntu UI log that may show me what went wrong? This could help a lot.

---

### Post by estruble on 2016-08-18
> **xaltotun said:**
> Guest additions installed. I usually install the ones that come with the new VirtualBox versions. When I first start a VM there is an option to insert the guest additions CD. I use it and install the guest additions. Currently I use VirtualBox 5.1.2 and the guest additions (with ls /opt) 5.1.2.
Resources and systems:
Host: Windows 7 x64
Guest: Ubuntu 16.04 x64, 2 processors, PIIX chipset, 4096 MB RAM, 128 MB Video memory. 
Other settings: VT-x enabled (in my BIOS and in the VM settings), Nested paging enabled, Audio enabled, 1 network adapter attached to NAT, 

By the way do you know if it is possible to find anything in the VM log? Or is there a Ubuntu UI log that may show me what went wrong? This could help a lot.



I too played the game of trying to figure out whet went wrong. I re-started in safe mode and then did some recoveries and reinstalls, booted into an older distribution, still nothing worked. Since the problem started after the last round of updates I figured something got hosed in that process. So, I went into a terminal only boot then ran "sudo apt-get dist-upgrade" which seam to correct the problem. I know that I'm going to get flames for using apt-get but it worked for me. 

Eric

---

### Post by QIII on 2016-08-18
Why would you get flamed for apt-get?

---

### Post by xaltotun on 2016-08-20
> **estruble said:**
> So, I went into a terminal only boot then ran "sudo apt-get dist-upgrade" which seam to correct the problem. I know that I'm going to get flames for using apt-get but it worked for me. 

Eric

I'll try that when I have some time. That's the first solution I've found.

---

### Post by xaltotun on 2016-09-04
I waited a little bit and again installed all the latest updates (saving a snapshot first). Whatever it had been before it was gone with the latest updates. And the last but not the least: Ubuntu is a great OS! Because it is free anybody can use it even inside a virtual machine. I think this issue has been solved.

---

