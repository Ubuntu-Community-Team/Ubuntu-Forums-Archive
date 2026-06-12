---
title: "Server can't find /sbin/init on boot"
date: 2009-09-15
forum: Server Platforms
---

### Post by rinze on 2009-09-15
A couple of weeks ago, my old Debian server had a nasty hardware failure. An excellent time to build a new server and give Ubuntu server 9.04 a try. After a week of messing around I finally had configured everything just how I wanted it, and things were fine.

Until yesterday when I did an apt-get update/upgrade. During the upgrade I encountered some errors and after that I got errors when I tried to run commands like 'ls' (commands could not be found). Then, when I tried to reboot, the boot process hung with the following final message:

```
run-init: /sbin/init: No such file or directory
```I started searching the web and ubuntuforums.org, ran into quite a few people having the same problem (on different versions of ubuntu), but I never found some solid clues of suggestions.

So, next thing I tried was booting from my install cd, using the rescue option. I happy to see my raid1 arrays were intact, and I could mount all my logical volumes and partitions and inspect their contents. Running e2fsck showed no errors, and /sbin/init was right where it was supposed to be on my root partition (which is on a logical volume).

All my config files like grub menu.list, mdadm.conf and fstab seem to be in order.

Like I said, I haven't come across any info that was helpful to me, so before I post some more details about my setup and boot process, I really hope that there are a few people out there who might have some ideas for me on how to progress. (And yes, in the time I've spent investigating this, I could have configured a fresh install, but that's not my style ;) )

When booting in recovering mode, I get:
```

Begin: Mounting root file system...
        Begin: Running /scripts/local-top... Done
        Begin: Waiting for root file system...
            finding ether cards
            creating raid1 on md0 ok
            creating raid1 on md1 ok
            ** md0 and md1 unknown partition table **
        Done
        Begin: Running /sripts/local-premount..
            No resume image, doing normal boot
        Done.
        EXT4-fs: INFO: recovery required on readonly filesystem
        ...
        EXT4-fs: recovery comlete
        EXT4-fs: mounted filesystem with ordered data mode.
    Begin: Running /scripts/local-bottom...Done.
    Begin: Running /scripts/init-bottom...Done.
    run-init: /sbin/init: No such file or directory
        Kernel panic - not syncing: attempted to kill init!
        Dumping frace buffer:
        (ftrace buffer empty)
        
        *DEAD*
```My drives:

```
2 SATA drives forming 2 Raid1 partitions: 
/dev/md0: /dev/sde1 + /dev/sdf1 
/dev/md1: /dev/sde5 + /dev/sdf5
    
md0 = Logical volumes for root, swap and tmp
md1 = Boot partition

All accessible and error free using the install cd's rescue mode
```Grub menu.lst

```
title    Ubuntu 9.0 etc...
root     (hd0,4)
kernel  /vmlinuz-2.6.28-11-server root=/dev/mapper/<name of root volume> ro quiet splash
initr    /initrd.img-2.6.28-11-server
```vmlinuz and initrd.img are present.

Thanks in advance for any help!

---

### Post by rinze on 2009-09-16
Funny, just came back here by clicking on a google search result. :)

---

### Post by rinze on 2009-09-16
Making progress:

To escape the small world of Busybox from my Ubuntu Server rescue mode, I booted a Ubuntu live cd. After booting I had to install some extra packages since I needed raid and lvm. I got those packages from a USB key, containing Ubuntu server.

I installed:

<usb key>/pool/main/w/watershed (needed by lvm2)
<usb key>/pool/main/d/mdadm
<usb key>/pool/main/l/lvm2

then I ran (as root)
```

mdadm -A --scan
vgchange -a y
```

Now, all my raid and logical volumes were present and accounted for.

so, then I mounted my root volume using 'mount /dev/<volume group/root /mnt/'

Then when I tried 'chroot /mnt /bin/bash' I got the error 'no such file or directory'
Same when I tried 'chroot /mnt /bin/ls'.

Then I came across a golden piece of information: run 'ldd /bin/bash' to see on what libs bash depends. And sure enough /lib/ld-linux.so.2 was needed but not present. So once I copied that over from /lib to /mnt/lib and tried to chroot again, I started getting more useful messages about more missing libraries. 

Still copying atm, but I'm pretty confident I can resolve this. I'll check back in later with the final results.

---

### Post by rinze on 2009-09-16
Ok, final recap

What happened?
There was an error when apt-get upgrade was installing libc6_2.9-4ubuntu6.1_i386.deb

The result?
Missing libs, unbootable system

The fix?
Resupply some libs using a live cd, so the system can boot again (with permission errors for certain processes). After boot I had to manually copy ldconfig from /var/cache/apt/archives/libc6_2.9-4ubuntu6.1_i386.deb to /sbin, after which I could do a dpkg -i libc6_2.9-4ubuntu6.1_i386.deb, which resolved the remaining errors.

:guitar:

---

