---
title: "IBM BladeCenter Blade Hard Disks No Longer Recognized by Hardy Server Installer"
date: 2010-01-28
forum: Server Platforms
---

### Post by ChipA on 2010-01-28
I'm trying to reinstall Ubuntu Server 8.04.x LTS (Hardy, 64-bit) onto an IBM BladeCenter blade.  We have previously (4 months ago) installed 8.04.3 onto these exact blades without any problems.  Today, the server installer is saying that "No disk drive was detected."

Anyone know what might have changed to cause this?  I am trying the install from the US mirror.  I have tried this on two different blades in two different IBM chassis with the same results.  The BIOS recognizes the disks when the blade is booting.


The message that appears when booting is:
LSI Corporation MPT SAS BIOS
MPTBIOS-6.18.01.00 (2007.08.08)


The disks are "IBM-ESXS" drives.  The controller is listed as "LSILogic SAS1064E-IR   1.18.84.00"


If I press Alt-F4 after the installer reports the problem, I don't see any messages associated with the failure to detect the drives.


The drives _are_ working.  In fact, at this point if I reboot the machine, the old installation of Ubuntu 8.04.3 boots up fine.  This appears to be a problem with the installer, not Ubuntu itself.


I was under the strong impression that LTS versions did not make big changes like this appears to be.  What could have caused this?

Thanks for any help / suggestions,
Chip

---

### Post by ChipA on 2010-01-29
Updating the NETBOOT directory on our PXE server to the new 8.04.4 version fixed the problem.  I guess we got unlucky in terms of the timing of the rollout of 8.04.4.

---

### Post by Vegan on 2010-01-29
Are you booting from the network for the installer? I have thought about using blades but I was speculating how to update them myself.

At present I use an old desktop or 3 for servers.

---

