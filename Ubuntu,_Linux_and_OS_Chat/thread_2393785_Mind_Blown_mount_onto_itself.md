---
title: "Mind Blown mount onto itself"
date: 2018-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by julianvreug on 2018-06-07
Thought i would post this to see if anyone else has experianced this.

The issue first came to me as someone was transfering files to /mnt/raid ran out of space for some unknown reason as it should be 30tb, then lost their files yet someone else logged in was transfering data still yet could not see it on another system or if i logged directly onto the system.

But wait gets more confusing.

We rebooted said cant load consol. Booted off a usb could not mount the NVme 1tb drive.

Gparted said the Nvme was only 500gb and LVM partition, missing other logical drives. ( i did not set this up as LVM)

Started install to see what will happen when look at partitions. Sure enough saw Nvme as 1tb ext4 but then again underneath there was another 1tb NVme with a 500gb partition called Ubuntu-VG

Ok 

So we looked under Dev and found Ubuntu--vg-root  (this had two - not one as the actual NVme partitions name Ubuntu-vg)

We mounted Ubuntu--vg-root to /mnt/nv

had a look inside and it was the root / file system

Had a look inside MNT and we found Raid opened raid and the files where there which was good as we didnt loose them.

So how i see it

/mnt/raid was mounted to /mnt/raid but at the same time to /dev/md0

So not only did the NVME apear to have two completly seperate and differnt partition tables LVM 500gb and 1tb ext 4 it somehow mapped ontop of a mount directory and the physical raid.

Scifi parrallel universe infinity loop paradox file system moment?

Has anyone seen this?

My head hurts thinking about how this can happen?

---

### Post by TheFu on 2018-06-13
Could you be confusing devices and mapped devices via LVM with mount points?
Instead of explaining what you think you saw, perhaps if you could use data gathering commands to post things so we can see that directly?

Data please.  parted -l, vgscan -ya, lsblk, and  df -Th should get us started.  Might need pvs, lvs, vgs and the mdadm --details too.

BTW, nVME support is pretty new, so depending on the exact kernel loaded, things might not be seen the same. Same for release tools. If you aren't on 18.04, which release and kernel?

---

