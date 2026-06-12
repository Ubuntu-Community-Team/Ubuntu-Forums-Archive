---
title: "Unable to install Ubuntu 64-bit although host is 64-bit"
date: 2012-09-23
forum: Virtualisation
---

### Post by JKyleOKC on 2012-09-23
I'm running into a strange problem. I'm trying to create an Xubuntu 12.04.1 VM, in my VBox 4.1.20 installation which is running on Xubuntu 12.04.1 64-bit version. The purpose is to have a "throwaway" test system on which I can experiment without risk to my production system.

However when I go to install, after creating the VM with all the correct options chosen, 1-GB RAM and 8 GB virtual disk, I get an error dialog that claims the required hardware settings are missing and must be set in the BIOS, so 64-bit systems cannot be installed! It's running on one, so this message is quite confusing, almost oxymoronous (if that's a word)...

Is it the fact that these hardware features are already in use by the host that is preventing them from being discovered during the install process? If so, this appears to imply that 64-bit guests could not be run at all...

Or is it simply a bug, or maybe I've overlooked something when creating the VM...

---

### Post by synaptix on 2012-09-23
Have you enabled virtualization technology in your BIOS?

---

### Post by JKyleOKC on 2012-09-23
The machine is an HP P2-1120 and its greatly-simplified BIOS dialogs don't have any such settings. It's running Xubuntu 12.04.1 in 64-bit mode, however. I've searched the VBox forums and tech areas for ideas but so far have found nothing. Looks like there may have been a reason this box was so low-priced for dual-core and plenty of RAM!

---

### Post by JKyleOKC on 2012-09-23
After a bit of digging through "lshw" reports for both of my machines, I found nothing in either to indicate that the virtualization features were present -- but I rebooted the other machine, an older and somewhat better Compaq desktop, and took a look in its BIOS. Sure enough, it had such a setting, which I enabled, and I was able to install the 64-bit VM even though the VirtualBox running there was version 3.2.12 and the Xubuntu host was a 32-bit 10.04.4 installation.

I'm marking the thread solved. My purpose in setting the VM up in the first place was to test whether I could use the Quetzal version of lightdm in a 12.04 system, since it has been updated to fix the zombie-creating tendency of the display manager. I'm happy to report that it seems to be perfectly okay; the test VM is now running with lightdm_1.3.3-0ubuntu4_amd64 (downloaded from the Quetzal builds on launchpad) instead of the much older version that came in the 12.04 package and nothing seems to be amiss...

---

