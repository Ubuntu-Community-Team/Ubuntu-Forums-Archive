---
title: "Unable to mount MD raid device by UUID"
date: 2010-06-07
forum: Server Platforms
---

### Post by borahshadow on 2010-06-07
Hi I just set up a new raid device (RAID 1) for data on my file server. The system doesn't boot off of the RAID. I tried to add the device to /etc/fstab with a uuid like my old array was (created during install I believe also not root partition) but it can't find the UUID it says. 
mdadm --detail --scan --verbose states this
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=7a0f12a0:61985b7e:098b0d42:be7de1b3     
   devices=/dev/sda1,/dev/sdb1                                                        
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=8eac8063:bcfabbe2:c23bfab8:f28dd995     
   devices=/dev/sda2,/dev/sdb2  
```
but ls -l /dev/disk/by-uuid says this ```
lrwxrwxrwx 1 root root 10 2010-06-06 23:13 0a903984-7bbe-46f4-948c-e867f12a1444 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-06-06 23:14 309f98b8-8a75-4328-a4d4-98ef5a8ace73 -> ../../md0 
lrwxrwxrwx 1 root root  9 2010-06-06 23:13 538704a3-1b7d-4b9a-9f3b-ee9ed84fb94b -> ../../sda 

```
and after a reboot it says this
```
total 0
lrwxrwxrwx 1 root root 10 2010-06-06 23:37 0a903984-7bbe-46f4-948c-e867f12a1444 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-06-06 23:37 309f98b8-8a75-4328-a4d4-98ef5a8ace73 -> ../../md0
lrwxrwxrwx 1 root root  9 2010-06-06 23:37 538704a3-1b7d-4b9a-9f3b-ee9ed84fb94b -> ../../sdb
lrwxrwxrwx 1 root root  9 2010-06-06 23:37 b7a4446d-9304-453b-a1b9-ea20ffd95ad5 -> ../../md1

```

sdc1 is the root device
sda1 and sdb1 make up md0 (data)
sda2 and sdb2 make up md1 (swap)

The part that really weirds me out is that there is a sda (sdb after reboot) in the /dev/disk/by-uuid folder



OK I just tried using the UUID listed by the ls command and it worked but I am still confused as to why they are different UUIDs

---

### Post by disabledaccount on 2010-06-07
sda/sdb - same uuid:
well, afain this is bios issue, because it enumerates devices in different way, depanding on if you reboot or power off/on the system and on bios internal events -> at least that is what I have discovered. Conclusion is, that if you have more than one hdd you should allways reference it by UUID.
I have 5 hdd's and 1 SSD in my desktop (4 on adaptec controller, 2 on mobo): imagine, they are enumerated in different way every time I turn on the power/ reboot the machine ... :LOL:

md/sd[] UUIDs are different things, cuse they references array or single drive - but, I see that you already know it ;)

---

### Post by borahshadow on 2010-06-07
oh right that makes sense about the drive enumeration. and Yes I did know that the md device should have a different UUID than the sd devices, but why is there a sd drive listed by the ls command when it should be used up by the array? or why are they both not listed. Also why does mdadm --detail not tell me the right UUID to use?

---

### Post by disabledaccount on 2010-06-07
> **borahshadow said:**
> ...but why is there a sd drive listed by the ls command when it should be used up by the array? or why are they both not listed. Also why does mdadm --detail not tell me the right UUID to use?That's good question...
What I can tell, is that on my machines none of md-members are listed in ../by-uuid "directory" and this seems to be logical (however blkid shows them even if array is stopped) I can only guess, that there is some very unimportant bug in kernel raid module(s) or in mdadm itself, that prevents proper masking of array members, or there was problem during device access. My way of creating arrays is to first check device ID and to create array using UUID's, not SATA lib names.
By default, in mdadm.conf you have settings that causes scanning of all devices and partitions to find md array members - so in fact, there should be no problem at all. On other side, mdadm keeps UUID's in array's metadata (superblock) - it will not get confused due to differerent enumerating of devices.
After creating array blkid shows raid devices that have same UUID and their  corresponding SATA names - this is enough i think. Even if there is problem with device identification, you can use --auto or --examine to get necessary info and asemble the array. ;)

---

### Post by borahshadow on 2010-06-07
ok I guess that makes sense. Out of curiosity what version of Ubuntu are you using? or if your server is not Ubuntu what Kernel do you have?

---

### Post by disabledaccount on 2010-06-08
I am using 2.6.31-20 x86_64 kernel, Ubuntu 9.10,
mdadm v2.6.7.1 with "classic" v0.90 superblock.

"never touch working system" - that's my primary rule ;)

...ahh, I forgot about propably most commonly misunderstood matter:
There are md[x] device UUIDs, but they are completely different from Filesystem UUID.
You should mount Filesystem and not Device ;)

Fortunately, we can use Filesystem LABEL= instead of of UUID= in  fstab, what is also safe.

---

