---
title: "Raid ?"
date: 2010-08-20
forum: Server Platforms
---

### Post by Confucius! on 2010-08-20
How does mdadm RAID know what drives are in the array and where is that stored?

---

### Post by arrrghhh on 2010-08-20
From the mdadm configuration file.  I believe it's just /etc/mdadm.conf...

You can also configure mdadm from the command line.  See [this](http://linuxmanpages.com/man8/mdadm.8.php) page.

---

### Post by Confucius! on 2010-08-20
That really just gives information about the array. Not the disks that are assigned to the array.

---

### Post by arrrghhh on 2010-08-20
> **Confucius! said:**
> That really just gives information about the array. Not the disks that are assigned to the array.

Ah, I apologize - I don't actually use mdadm.

Have you looked at /proc/mdstat?

Per [this](http://man-wiki.net/index.php/8:mdadm) page: >   If  you're using the /proc filesystem, /proc/mdstat lists all active md
      devices with information about them.  mdadm uses this  to  find  arrays
      when  --scan is given in Misc mode, and to monitor array reconstruction
      on Monitor mode.

---

### Post by Confucius! on 2010-08-20
/proc is a virtual filesystem. So /proc/mdstat is not like a file you can edit it is created when you boot Ubuntu. Although it list the drives in the array it does not define what drives are in the array.

---

### Post by arrrghhh on 2010-08-20
> **Confucius! said:**
> /proc is a virtual filesystem. So /proc/mdstat is not like a file you can edit it is created when you boot Ubuntu. Although it list the drives in the array it does not define what drives are in the array.

I realize that.  I don't know why you would ever want to edit it.  I think you're SOL, I've given you all the information that is related to mdadm that I could find that applies to your question.

---

### Post by Seq on 2010-08-20
> **Confucius! said:**
> That really just gives information about the array. Not the disks that are assigned to the array.

I believe each array is identified by a UUID, and each array element contains the UUID of the array it belongs to. It is then a matter of probing.

---

### Post by Confucius! on 2010-08-20
I don't believe that to be right because of a problem I was having and solved. I first thought that that array info was stored on the disks. Then when you started Ubuntu it scan the disks to find the array info.

I have a 3 disk RAID 5 array that Ubuntu is installed on. I have a backup eSATA drive that I use to backup my OS/RAID 5 array. My RAID disk where on SATA Controller 1 (/dev/sda) ,2 (/dev/sdb), 4 (/dev/sdd) and my eSATA drive was on SATA controller 3 (/dev/sdc). During install my eSATA drive was off so one of my RAID drives then became /dev/sdc. 

When I turned on my eSATA drive before booting Ubuntu it would degrade my RAID array. If I turned it on after Ubuntu was running everything worked fine and the array did not become degraded. I believe this was happening because mdadm was using the drive path to define what drives where in the array. So when the eSATA drive was not turned on at boot. My drives paths would be /dev/sda, /dev/sdb, /dev/sdc. With the drive was turned on before I booted Ubuntu my backup drive then became /dev/sdc. Then one of my arrays drives would become /dev/sdd and my array would be degraded. All because of the way the plug into the MB. It was an easy fix I just change how the drives plugged into the MB. Everything works fine now.

So it cant be UUID or i would not have had this problem.

---

### Post by Seq on 2010-08-20
> **Confucius! said:**
> I don't believe that to be right because of a problem I was having and solved. I first thought that that array info was stored on the disks. Then when you started Ubuntu it scan the disks to find the array info.

Ubuntu only reassembles arrays that are indicated in /etc/mdadm/mdadm.conf. The actual physical devices are not in that file, just an array ID. If yours has device names in it, you might want to repair it and update your initrd.

```
ARRAY /dev/md0 level=raid1 num-devices=6 UUID=436c7c6f:5e12e5b6:42867bb5:1a960e64
ARRAY /dev/md1 level=raid5 num-devices=6 UUID=43c78439:8c9dc681:951c467d:45070cb7
```

According to the [kernel.org raid documentation]("https://raid.wiki.kernel.org/index.php/RAID_setup"), it should be fine if devices move.

> For complex cases (ie you pull in disks from other machines that you're trying to repair) this has the potential to start arrays you don't really want started. A safer mechanism is to use the uuid parameter and run:
```
  mdadm --scan --assemble --uuid=a26bf396:31389f83:0df1722d:f404fe4c
```
This will only assemble the array that you want - but **it will work no matter what has happened to the device names. This is particularly cool if, for example, you add in a new SATA controller card and all of a sudden /dev/sda becomes /dec/sde!!!**

Also according to that documentation:

> The persistent superblocks solve these problems. When an array is created with the persistent-superblock option (the default now), a special superblock is written to a location (different for different superblock versions) on all disks participating in the array. This allows the kernel to read the configuration of RAID devices directly from the disks involved, instead of reading from some configuration file that may not be available at all times.

---

