---
title: "SCSI HD id when you have a SCA connector ... HELP!"
date: 2008-03-16
forum: Server Platforms
---

### Post by AntoC on 2008-03-16
Dear Ubuntu Community,
I recently got a Fujitsu Siemens TX200 2S server, I am amazed to communicate that Ubuntu recognises all the hardware natively and is going to be my next Server distro, after CentOS.

Now I have an issue, I received my server without hard drives installed, there was one on the side of the box (uninstalled for transport). This hard drive is a SCA connector SCSI 36.7 GB 15000 rpm (should :P).

When I start ubuntu to install in the hard drive, the distro says there there are not drives installed....

I thought that there was a id problem but SCA HD's don't allow you to set an ID for the Adapter....

Does anyone know a way around or a solution to my problem?
Thank you in advance

Antonio

---

### Post by netztier on 2008-03-17
> **AntoC said:**
> 
I thought that there was a id problem but SCA HD's don't allow you to set an ID for the Adapter....


There's no need to set SCSI IDs if you have slots with SCA connectors; the slot number determines the SCSI ID.

If the Ubuntu installation does not discover any drives, the fault is probably with the non-discovery of the SCSI controller. 

Jump into another console (Alt + F2), and issue the  **lspci** command to see wich PCI devices there are in your system, then do an **lsmod** to see which kernel modules have been loaded. We'll probably have to add one manually with **modprobe <module name> **, but first we have to know what kind of SCSI controller is your system.

regards

Marc

---

### Post by AntoC on 2008-03-17
Hi netzier and thank you for the reply,
I tried XP and it doesn't work either, it says "not hard drive present in the slot you may need to run the manufacturer disk to configure the Adapter".... That stinks :).....
Anyway, now running Ubuntu ls pci gives me a bunch of peripherals.... the ones related to the storage devices are:

01:04.0 SCSI Storage Controller: Adaptec AIC-7902 U320 (Rev 03)
01:04.1 SCSI Storage Controller: Adaptec AIC-7902 U320 (Rev 03)

I believe those are the SCSI controllers is that right?

Thanks in advance for your help,
Antonio

---

### Post by netztier on 2008-03-17
> **AntoC said:**
> Hi netzier and thank you for the reply,
I tried XP and it doesn't work either, it says "not hard drive present in the slot you may need to run the manufacturer disk to configure the Adapter".... That stinks :).....
Anyway, now running Ubuntu ls pci gives me a bunch of peripherals.... the ones related to the storage devices are:

01:04.0 SCSI Storage Controller: Adaptec AIC-7902 U320 (Rev 03)
01:04.1 SCSI Storage Controller: Adaptec AIC-7902 U320 (Rev 03)

I believe those are the SCSI controllers is that right?


Sounds like SCSI adapters allright. Can you check **dmesg**'s output for any entries relating to "SCSI" and/or "adaptec" and/or "AIC-7902"? Oh, and while you're at it, also look at **lsmod** if a kernel module's been loaded for this adapter.

However, these might be RAID-capable adapters that would not show the connected disks transparently, only after initial configuration of a RAID array (and even if it's only a "1-disk-array"). 

Some adapters can do this via their own BIOS - be sure to check if there is a hotkey combination that you can press  to jump into the controller's BIOS right after the initial boot phase. Something like Ctrl+S or Ctrl+F6 right after the server's BIOS boot phase.

Other RAID adapters (such as older HPs) need a special CD-ROM to be booted; from it's environment, you can configure the array and sometimes other hardware related stuff.

regards

Marc

---

### Post by AntoC on 2008-03-17
Hi Marc,
Apparently the problem is that my adapter can be configured just through software..(can you imagine :O !!!) ... And hopefully I will find a copy of the start cd that comes with the server.... Is there a chance that Ubuntu can configure it without the original cd.... that to me would be magical.....!!!

Thanks,
Antonio

---

### Post by netztier on 2008-03-17
> **AntoC said:**
> And hopefully I will find a copy of the start cd that comes with the server.... Is there a chance that Ubuntu can configure it without the original cd....

Hum.. not unless someone writes the tools for this card. 

Seems like this is a low-end RAID controller:

[http://ubuntuforums.org/showthread.php?t=310786](http://ubuntuforums.org/showthread.php?t=310786)

This thread suggests that you can use it as standard controller with no RAID functionality... so we first need a kernel module that fits

Looking at the contents of /lib/modules/<kernelversion>/scsi/... and subdirectories, the kernel module **aic79xx** should best suit your host adapter.

With the installation CD booted, jump into another console, do an **lsmod** and check if the module **aic79xx** is listed. If not, do a **modprobe aic79xx**, and then check **dmesg** to see if the module's been properly loaded. You probably won't be able to use the adapter's RAID functionalities, but with only a single disk availabe, this point is rather moot.

regards

Marc

---

### Post by AntoC on 2008-03-18
Thank you Marc,
I will let you know if the kernel module worked... 
Thanks again,
Antonio

---

### Post by AntoC on 2008-03-19
Hi Marc,
same problem.. GParted says "No devices detected"... lsmod says that aic79xx is loaded correctly.....
:confused: :confused: :confused:

PS. I tried fdik -l and obviously it returns an empty string (no partitions/disks)

PS2. I am in the SCSISelect Utility .... no drives (however it sees the tape drive..... how come......)
I am starting to think that my SCSI is broken..... :(

EUREKA!!!
My adapter works and is SUPER FAST (130 MB/S!!!!!!)

The problem was really me: I wasn't waiting enough for the system to scan the Adapter properly, after 3 failures the system itself opened the SCSI/ADAPTER reconfig utility, reconfigured the array (either if it has just 1 disk) and there you go!......

Any ideas?

Antonio

---

### Post by netztier on 2008-03-19
> **AntoC said:**
> Hi Marc,
same problem.. GParted says "No devices detected"... lsmod says that aic79xx is loaded correctly.....


Now then - let's see what we see in terms of scsi devices:

read the contents of /proc/scsi/scsi:

```
marc@blaze:/$ **cat /proc/scsi/scsi**
Attached devices:
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5001ABYS-0 Rev: 59.0
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5001ABYS-0 Rev: 59.0
  Type:   Direct-Access                    ANSI SCSI revision: 05


```

(this is the output from my server with two controllers an two Western Digital 500GB disks)

regards

Marc

---

### Post by AntoC on 2008-03-19
Now another problem,
While booting the server hangs, after rebooting in verbose  the error message is:```
dump card state Ends
``` 
What that means?!
After 2 minutes it drops to a shell saying :
```
ALERT! /dev/rd!c0d0p1 dows not exist. Dropping to Shell!
```

Another Ubuntu Nightmare.... :lolflag:

---

### Post by rustybronco on 2008-03-19
> **AntoC said:**
> 
After 2 minutes it drops to a shell saying :
```
ALERT! /dev/rd!c0d0p1 dows not exist. Dropping to Shell!
```
should it not be /dev/rd/c0d0p1? maybe that's why it complains, because it is looking for /dev/rd!c0d0p1

---

### Post by AntoC on 2008-03-19
Mmmmm! I don't think so....

.... Do you think I should change the  path?
Reading on the web it seems like lots of people have the same problem everything depends on the SCSI adpter drivers the Kernel is using at the moment the problem is on Debian, Ubuntu and Red Hat all with the very same type of SCSI controller that I have.... Do you think I should try CentOS on my Server...

---

### Post by rustybronco on 2008-03-19
> **AntoC said:**
> 
.... Do you think I should change the  path?
No. I'm not so sure thats what needs to be done.
but at the very least the kernel is complaining it can't find the partition/device at /dev/??/c0d0p1.

I now have centos5 on my dl380, but I plan on installing 7.04-server in a few weeks. (i like apt!)

---

### Post by netztier on 2008-03-20
> **AntoC said:**
> 
After 2 minutes it drops to a shell saying :
```
ALERT! /dev/rd!c0d0p1 dows not exist. Dropping to Shell!
```


Wait - are you saying that you were able to finish the installation after **modprobe aic79xx**, but now upon initial boot, you can't boot because of this message?

I assume the problem is this:

[LIST]
[*]the kernel on the installation CD probably didn't load aic79xx automatically
[*]you added it manually with **modprobe aic79xx**, but only to the now-running installation environment.
[*]the installation did finish, because the disk was now accessible
[*]the initrd-kernel that is now installed on disk does not include **aic79xx**
[*]therefore, Linux can't boot.
[/LIST]

The initrd-Kernel is kind of a mini-Linux-kernel that holds only the most minimal drivers/modules (such as the drivers for SCSI host adapters) needed to load the "real" Linux kernel afterwards. I had a similar problem once on a Sun Ultra2 that needed a module called "esp" to see it's hard disks, and I had to follow this procedure to include esp in the initrd-kernel ([http://ubuntuforums.org/showthread.php?t=166882](http://ubuntuforums.org/showthread.php?t=166882) ; not all file and directory names are the same, though).

The solution should be possible like this:

[LIST]
[*]boot the installation CD into **rescue** mode (type "rescue" at the boot prompt)
[*]at the first step possible, jump to another TTY and **modprobe aic79xx**; now the rescue system can find and access the harddisk(s).
[*]get back into the rescue mode TTY
[*]continue until rescue-mode offers you to chroot into an existing installation; you get a shell from the installed ubuntu on the harddisk.
[*] inside that chroot environment, edit the file **/etc/initramfs-tools/modules** to have a line with **aic79xx** at the end
[*] inside that chroot environment, run **/usr/sbin/update-initramfs**
[/LIST]

Now, the initrd-kernel is remade to include the aic79xx module, and it should be able to boot your Ubuntu installation properly.

hope that helps

Marc

---

### Post by AntoC on 2008-03-20
Hi Marc,
after having used the built-in Utility the hard drive was recognised by g parted that's why I could install.... So I did not need to load the aic79xx module myself, everything was there up and running.... after I installed rebotting the server hangs and drops to a shell (after a while) so .... I used grub to start with nosplash and in verbose mode.... the last message is:
```
dump card state Ends
```

:confused: :confused:

PS 
I read your thread and seems that your problem was that the module was not loaded @ boot but in my case it obviously is: double :confused:

---

