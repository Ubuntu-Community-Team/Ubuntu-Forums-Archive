---
title: "Ubuntu 7.04 (SPARC) Installation"
date: 2007-04-30
forum: Sun Sparc Users
---

### Post by Andrew1963 on 2007-04-30
I decided to try Ubuntu on my SPARC station, so downloaded the ISO for Feisty Fawn and burned it to CD.  Unfortunately, installation halts just after the installation program says it is creating a RAM disk.  The computer reports "Illegal instruction" and drops to an OK, prompt.

Anyone know what's happening ?

Andrew

---

### Post by ZzeusS on 2007-05-01
I have tried ubuntu-6.06-server-sparc.iso and 7.04 on a 420R and received:

Allocated 8 megs of memory at 0x40000000 for kernel
Loading kernel version 2.6.15
Loading initial ramdisk (4821666 bytes at 0x400000 phys, 0x40c00000 virt)...
Illegal instruction
(0) ok


I can do a 'boot cdrom' and stop-a out of anything else to get a full reset, but I don't get anything except the above error.

Rescue mode does the same thing.

---

### Post by virtualtoaster on 2007-05-02
try turning off the diag-switch at the ok prompt.. youll have to google for the exact command/syntax...  it worked for me with 6.10

---

### Post by jcastill on 2007-05-03
Do you have the lastest OBP? I've seen a lot of fixes for things like that when I updated.

---

### Post by ZzeusS on 2007-05-03
I'll have to Google how to reload the boot prom.  It's been years since I did any real work with Sun equipment.  I thought Sun boot proms had to be physically replaced, but the Open in OBP may lead me to greatness.  I will try that.

---

### Post by ykanello on 2007-05-07
Linux primer 2.6.17-10-sparc64 #2 Fri Oct 13 17:04:28 UTC 2006 sparc64 GNU/Linux
ykanello@primer:~$ cat /etc/issue                                               
Ubuntu 6.10 \n \l                       

I have installed successfully with mirroring the disks during installation of ubuntu 6.10 on sparc. 
Its older system T1 and v120 than the ones you asked, but I used  an internal CDrom.
the USB one was giving me the issues with not booting as well.

From OK prompt, I boot ide, and the rest is simple. (i think). :)

---

### Post by jdeisenberg on 2007-05-16
Updating the OBP is essential. The hardest part of that (for me) was getting the write-protect jumper off the pins the first time.

On the SunBlade 100s that I was using, I changed the [FONT="Courier New"]boot-device[/FONT] environment variable to start with [FONT="Courier New"]cdrom[/FONT]. For example, if your [FONT="Courier New"]boot-device[/FONT] variable currently is 

   [FONT="Courier New"]disk net[/FONT]

Do this:

  [FONT="Courier New"] setenv boot-device cdrom disk net[/FONT]

That eliminates the need for one more STOP-A.

---

### Post by Pete_C on 2007-05-23
Hello,

I've exactly the same problem with a SunBlade 1500. Using the latest OBP 4.17.1 gives the Illegal instruction error above, even from a cold boot. Using the older OBP (4.9.5) would allow the initial boot only to fail later.

The same problem exists for Ubuntu releases 7.04, 6.06 and 6.06.1, also for Debian Etch. I'm afraid something is certainly broke.

---

### Post by westfall@computer.org on 2007-06-07
I Seen this issue on an Ultra 60 with OBP 3.31.  The fix was simple I disconnected the floppy drive and the CD booted with out issue.  I then reconnected the floppy and the boot up died at the RAMDISK.

---

### Post by palanca on 2007-06-12
god aftenon in my 1º installation i have problem equal to ZzeusS.
Allocated 8 megs of memory at 0x40000000 for kernel
Loading kernel version 2.6.15
Loading initial ramdisk (4821666 bytes at 0x400000 phys, 0x40c00000 virt)...
Illegal instruction
(0) ok

i reboot my machine press Stop +A
write boot cdrom and i have two options 1=boot install 2=rescue
i chose (write)install enter .............................and go

---

### Post by Malley H.Kasuga on 2007-06-13
I also experienced the same problem in Netra T1.
This is my solution about it.
You may not be settled by this method.

To resolve:

Download Solaris 10 CD from sun.com download center.
Get only the 1st boot CD, wichi is named sol-10-u3-ga-sparc-v1.
The following errors are displayed at the end of 1st CD installation.

Hardware error
  or
unformatted disks
#
(Because I chose Japanese then, I could not read the messages in English)
(# is shell prompt)

and shutdown (poweroff)

Retry install Ubuntu. All is ok and you will find 'Login:' after rc.local runs...

---

### Post by vr76413 on 2007-06-14
Cant get GUI screen after installing UBUNTU 7.0.4 on SPARC

HELP:(

---

### Post by jdeisenberg on 2007-06-14
If you're getting a message like this when you try to start the GUI:
```
Fatal server error:
xf86MapPciMem: Could not mmap PCI memory [base=0x426000,hostbase=0x426000,size=2000] (Inappropriate ioctl for device)
```

Then try the fix specified in the post near the end of this thread: [http://ubuntuforums.org/showthread.php?t=430611](http://ubuntuforums.org/showthread.php?t=430611)

---

### Post by ykanello on 2007-09-19
Yesterday
 I had to reinstall Ubuntu on a Sun Fire V120.
I added two brand new scsi disks, and connected the LOM to my laptop.
Powered up at LOM, did the first tests, and reached the OK prompt.
There i typed boot cdrom 
and the ubuntu cdrom was booted and i started installation procedure.
I need the installation to be on software mirrored disks, so passing quickly the options of language and keyboards, reached the disk management. 
It took me about 30 mins to create 8 partitions on each disk, create a mirror for each two partitions and assign FS and mount location.
Rather long and tedius. I think a small script that does that automatically could have been in place at least for the server installations. Most of the server configurations nowdays have two identical local disks. There must be a small installation script to create the partitions the same way. Anyways.
Installation broke again on the networking because there was no cable plugged in. 
No biggy though. Moved on, installed the core, installed silo, and no extra software.
Asked me to reboot, and then the first boot failed.
The reason? Once again the stupid UUIDs. Some script decided to change the /etc/fstab with the uuid's instead of the /dev/md? that i just setup. 
As a result there is no other partition mounted except the /dev/md0. This is SO bad, because few details for a server edition that MUST be present: Cannot have /usr/bin/vi and not a single editor on /bin. In case of problems and cannot mount /usr you have NO TOOLS to edit any files. 
So I need to boot the system once again with a rescue disk, MANUALLY edit the fstab (good think I kept notes of the installation) and then reboot again.
I am not pleased at all with these development. I had the same issues (and still have) with an opteron server. Every time there is a new kernel installed it breaks the grub config since it adds uuids and not /dev/md values in.
And there is not a config file, that will change this behaviour. Or nothing that I know of.
More details and maybe a screenshot tomorrow, since last night it was way too late to boot with rescue disks.
:confused:
Shouldn't be ubuntu good for servers too?

---

### Post by jsunwalters on 2007-10-10
I am trying to install on a Netra T1 with 7.04.  I am using the LOM port.  After booting from
cdrom I get the following message and it just hangs

Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.20
Loading initial ramdisk (6428827 bytes at 0xC0000000 phys, 0x40C00000 virt)...
-
Remapping the kernel... done.
Booting Linux... 



Any pointers?

Never mind.  set diag-switch to false and off I went.

---

### Post by ykanello on 2007-10-15
> **jsunwalters said:**
> 
-
Remapping the kernel... done.
Booting Linux... 



Any pointers?

Never mind.  set diag-switch to false and off I went.

so it boots right?
(it seems like it)

---

### Post by gnikol on 2007-10-26
I had exactly the same problem ... After the error message I was booting from cdrom again and again, and after many many tries ,  Ubuntu linux booted normally and installed. 
I don't know why this happened ... some kind of magic I suppose :)

---

