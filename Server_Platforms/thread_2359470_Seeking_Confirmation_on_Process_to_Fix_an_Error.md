---
title: "Seeking Confirmation on Process to Fix an Error"
date: 2017-04-24
forum: Server Platforms
---

### Post by w-kym-wittal on 2017-04-24
I am running 14.04 LTS server, however, I think this is a general housekeeping/tool use question.

I am trying to run a backup, but after a couple of hours, it keeps failing and stating for an 'unknown reason'.  I recently had issues with a kernel upgrade, since resolved, but there may be lingering issues related to that.  I have reviewed the boot log and found:

```
ERROR: sil: invalid metadata in area 3 on /dev/dm-0

The following is the list of disks:
  NAME                                     FSTYPE   SIZE    MOUNTPOINT         LABEL

  sda                                                     1.8T                 

  &#9492;&#9472;sda1                                    ntfs       1.8T   /media/kym/Seag    Seagate Backup Plus Drive

  sr0                                                      1024M                 

  cciss!c0d0                                            136.7G                 

  &#9500;&#9472;cciss!c0d0p1                                     243M                 

  &#9500;&#9472;cciss!c0d0p2                                     1K                 

  &#9492;&#9472;cciss!c0d0p5                                     136.5G                 

    &#9500;&#9472;ubuntu-root (dm-0)           ext4         130.9G /                          Source Code

    &#9492;&#9472;ubuntu-swap_1 (dm-1)      swap         5.6G [SWAP]          

  cciss!c0d1                                             205G                 

  cciss!c0d2                                             698.6G
```

My question is:  can I unmount dm-0 only then run fsck on dm-0 only to try to fix this?
Commands to do this are:  unmount /dev/dm-0, fsck -f /dev/dm-0, mount /dev/dm-0 (I think these are not correct) 

Thanks.

---

### Post by slickymaster on 2017-04-24
Thread moved to ***Server Platforms*** for a better fit.

---

### Post by TheFu on 2017-04-25
You can't umount / on a running system.
If you want to run an fsck on /, **sudo touch /forcefsck** and reboot.
That will force an fsck on the next reboot.

---

### Post by w-kym-wittal on 2017-04-26
Ran fsck as suggested, it did run, however, no feedback/indicators of  anything.  Looked for logs, found nothing.  Does this means there were  no errors and nothing to fix or just looking in the wrong location?

Also,  I ran the backup successfully by NOT backing up the folder - Source  Code Folder, located at /home/kym/Public/Source Code Folder.  Does this  mean this folder might have errors on it, causing the backup to fail?   Is this related to the above:
ERROR: sil: invalid metadata in area 3 on /dev/dm-0

Thanks.

---

### Post by w-kym-wittal on 2017-04-26
I have another question, not sure if it is related to the above:  I am running our of disk space on /boot.  There are a number of older kernel files there.  GRUB reports only 2 kernels 'active'.  Can I delete from /boot the older, not listed, kernel files?

---

### Post by TheFu on 2017-04-26
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) System Maintenance for Ubuntu Systems.  You need to fix that kernel issue ASAP. It won't get better and is likely to end with a system that will not boot.

The disk issue could be anything.

Both of these are different from the first question. Best to ask 2 different questions on 2 different threads to get people expert in those areas.  "dm0 corruption?" and "full /boot help" would be my titles, but I'd search the forums, since these have been asked and answered before, many times.

---

### Post by w-kym-wittal on 2017-04-27
Thanks.  I will follow up on your advice.

---

