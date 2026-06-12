---
title: "Ubuntu Server VM no keyboard or mouse"
date: 2017-10-19
forum: Server Platforms
---

### Post by tjcstuart on 2017-10-19
I'm running VMware ESXi 6.5. 
Ubuntu Server 16.04

Everything was working great in Ubuntu until I had the great idea to give a GUI a try. Instead of just spinning up another VM, like I should have, I tried installing kubuntu-desktop. 
When I now boot the VM it's going straight to a GUI login screen and the keyboard and mouse no longer work. 
I can get into Ubuntu recovery mode, and tried uninstalling kde-desktop, but a different GUI comes up now. 
I'd appreciate any help you can provide. I'd rather not just re-install, as this is one of the many ways I can learn more about the system. 
When I'm at the GUI login I cannot use ctl-alt-f2... It simply doesn't respond to any keyboard commands. The server is fully working, as it is hosting a SAMBA share and even with the unresponsive desktop the share is fully accessible.

---

### Post by LHammonds on 2017-10-20
In all the years I have been running Ubuntu Server, I have never installed a GUI so I won't be much help for this solution.  It sounds like the VM tools are not installed / working or maybe they just don't recognize the desktop GUI.  I've kinda have seen this behavior with MS Windows before the VMware tools are installed but they usually work somewhat rather than not at all.

But I will suggest using VirtualBox on your PC so you can have as many test OS's you want.  I like having a base Ubuntu Server installed, fully patched and then a snapshot on top of that.  Then I can try out some software and when done, simply revert to the snapshot...then apply any new OS patches and re-snap to have another fully-patched base OS ready for the next thing to test.

LHammonds

---

### Post by tjcstuart on 2017-10-20
I managed to get this fixed. 
Booted into recovery mode
Went to root console and ran 

```
sudo systemctl disable sddm
```

While logged in with the keyboard/mouse not working I told the VM to perform a shutdown. The first thing it displayed was SDDM, so I thought that might be the service that kept running. Did some googleing and came across [https://forum.manjaro.org/t/switching-to-lightdm-instead-of-sddm/9068](https://forum.manjaro.org/t/switching-to-lightdm-instead-of-sddm/9068)
This is where I found how to disable SDDM. 
After doing this I'm able to reboot to the normal console based login, keyboard fully functional.

---

