---
title: "Problematic BTRFS raid10  behavior."
date: 2012-06-02
forum: Server Platforms
---

### Post by Avanesov on 2012-06-02
Evening all.

Im having an odd problem with a BTRFS Raid10. I can/have sucessfully built the raid and mounted it etc..., but sometimes (not always) on reboot my HDD's show up in a different order and the BTRFS mount will fail until I rescan devices.

Originally I had fstab configured as such:
/dev/sdf /mnt/DATA01 btrfs device=/dev/sd?,(repeat for each drive in the pool),defaults,compress 0 0

When it failed the first time I changed it to :
UUID=53b023b5-4416-4ec2-9063-98411123f3af       /mnt/DATA01     btrfs   defaults,compress       0       0

It still seems to require a device scan to sucessfully mount the raid, so my questions are: 1. Is there a way to ensure it will mount without a device scan even if the drives change order? 2. If the first question cannot be answered (or the answer is no), what could possibly be causing my Hard drives to change order?

P.S. No hardware changes were made between reboots. 4 of the hard drives are connected via sata ports on the MB and 2 via a Rosewill sata + ultra ata raid controller (card is only being used for additional sata ports) RC-212

EDIT note: There doesnt seem to be any relation to what drives change order and what port (MB vs the sata card) the drive is plugged into.

---

### Post by rubylaser on 2012-06-03
Your drives are being presented in a different order because your controllers aren't being addressed in the same order everytime.  Using the UUID is the proper way to handle this mounting and really all disk mounts in /etc/fstab.  

As a sidebar, do you want to use btrfs when a stable fsck still doesn't exist?  I wouldn't trust my data to it especially when other options exist. You could use mdadm + ext4, or even use zfsonlinux.  Obviously, you can use whatever you'd like, but I just wanted to express my concern for you data :)

---

### Post by sandyd on 2012-06-03
> **rubylaser said:**
> Your drives are being presented in a different order because your controllers aren't being addressed in the same order everytime.  Using the UUID is the proper way to handle this mounting and really all disk mounts in /etc/fstab.  

As a sidebar, do you want to use btrfs when a stable fsck still doesn't exist?  I wouldn't trust my data to it especially when other options exist. You could use mdadm + ext4, or even use zfsonlinux.  Obviously, you can use whatever you'd like, but I just wanted to express my concern for you data :)

Note that ZFS is slower, and requires a bit more memory.
Preemption support is still in testing -> [https://github.com/zfsonlinux/zfs/issues/83](https://github.com/zfsonlinux/zfs/issues/83) , so its not a good idea to use ZFS on Ubuntu, which uses a voluntary preemptible kernel.

---

### Post by rubylaser on 2012-06-04
> **sandyd said:**
> Note that ZFS is slower, and requires a bit more memory.
Preemption support is still in testing -> [https://github.com/zfsonlinux/zfs/issues/83](https://github.com/zfsonlinux/zfs/issues/83) , so its not a good idea to use ZFS on Ubuntu, which uses a voluntary preemptible kernel.

Thanks for providing that info :)  I use ZFS on Openindiana at work and home along with mdadm in Ubuntu. I would still use either one of those two over btrfs at this point due to the fsck issue.  Personally, I use mdadm + ext4 unless I need greater than 16TB, then I go with ZFS on Solaris/Openindiana at that point.

ZFS does like to use RAM and the more you have (to a point), the faster it will go.  I don't find it slow though.  My (9) disk Hitachi 5K3000 ZFS array at home can read/write on the server at over 600MB/s. I do have 16GB of RAM in my fileserver, but with RAM prices as cheap as they are, 16GB of RAM costs way less than (1) of my 2TB drives would.

---

### Post by sandyd on 2012-06-04
> **rubylaser said:**
> Thanks for providing that info :)  I use ZFS on Openindiana at work and home along with mdadm in Ubuntu. I would still use either one of those two over btrfs at this point due to the fsck issue.  Personally, I use mdadm + ext4 unless I need greater than 16TB, then I go with ZFS on Solaris/Openindiana at that point.

ZFS does like to use RAM and the more you have (to a point), the faster it will go.  I don't find it slow though.  My (9) disk Hitachi 5K3000 ZFS array at home can read/write on the server at over 600MB/s. I do have 16GB of RAM in my fileserver, but with RAM prices as cheap as they are, 16GB of RAM costs way less than (1) of my 2TB drives would.
I found it slower - I used to have ZFS on two of my opteron HP blades (HP SAS 600G 15000RPMs x4). Used it to run 2 NFS Datastores on freebsd, while my webpages were served from it.

Performance was slower than now, which i've moved to RAID 10 with XFS on Fedora.

Though, the move was mainly due to the fact that FreeBSD ate RAM like nuts.

---

### Post by rubylaser on 2012-06-04
Not that it matters to the OP because he's not replied back, but for my own info, did you ever run a ZIL device or run at least 16GB of RAM in your server?  Otherwise, I'm not surprised that NFS on ZFS was slow due to the way that it syncs by default.  

What sort of speeds do you get now on your (I assume) hardware RAID10?  Thanks again for the info, and if it's too time consuming to answer, don't worry about it, this has just piqued my interest :)

---

### Post by sandyd on 2012-06-05
> **rubylaser said:**
> Not that it matters to the OP because he's not replied back, but for my own info, did you ever run a ZIL device or run at least 16GB of RAM in your server?  Otherwise, I'm not surprised that NFS on ZFS was slow due to the way that it syncs by default.  

What sort of speeds do you get now on your (I assume) hardware RAID10?  Thanks again for the info, and if it's too time consuming to answer, don't worry about it, this has just piqued my interest :)

Had 32GB RAM. FreeBSD was allocated 10G on each server. That might be it, but I get the same amount of data protection for much less RAM. 16 GB RAM for full speed is way too much in my opinion.

Speed?
Honestly, I'm not sure. I use vmware esxi on these servers, so anything that I measure will be skewed. However, I get around 1-1.5Gb/s of speed on the NFS. These are 3Gb/S SAS drives, so I think that is reasonable.

---

### Post by Avanesov on 2012-06-05
> **rubylaser said:**
> Your drives are being presented in a different order because your controllers aren't being addressed in the same order everytime.  Using the UUID is the proper way to handle this mounting and really all disk mounts in /etc/fstab.  

As a sidebar, do you want to use btrfs when a stable fsck still doesn't exist?  I wouldn't trust my data to it especially when other options exist. You could use mdadm + ext4, or even use zfsonlinux.  Obviously, you can use whatever you'd like, but I just wanted to express my concern for you data :)
Sorry for the delay in replying. I will test/double check whether using the UUID prevented this behavior, I thought it had done it again even after making this change but im not sure.

As for using BTRFS, I do want to give it a spin. All the data I have on it is either expendable or saved in an alternate location. Also, as I understand the scrub function will repair errors as long as there are mirror copies of it, and I am running a raid10.

Do you have any insight as to why my device controllers are being resolved in different orders? I work IT and have been in the business for about 8 years now but this is something I have never seen or had to take notice of before. I would think the device enumeration should happen the same order every time unless something changes.

---

### Post by rubylaser on 2012-06-05
> **sandyd said:**
> Had 32GB RAM. FreeBSD was allocated 10G on each server. That might be it, but I get the same amount of data protection for much less RAM. 16 GB RAM for full speed is way too much in my opinion.

Speed?
Honestly, I'm not sure. I use vmware esxi on these servers, so anything that I measure will be skewed. However, I get around 1-1.5Gb/s of speed on the NFS. These are 3Gb/S SAS drives, so I think that is reasonable.

You are right, 10GB should be fine, but without a ZIL device and ESXi's insistance on sync writes, I can understand your slowness issue.  ZFS definitely uses more RAM than a traditional filesystem, but it does use it for more throughput, so that's a good thing. 

1 -1.5GB/s is excellent, although that must be on smaller file transfers that are staying in the RAID controller's cache because 4 SAS disks that provide ~160MB/s each wouldn't provide that much speed without a cache.  Thanks again for taking the time to respond, and overall, I'm glad you have a solution that works well for you.

---

### Post by rubylaser on 2012-06-05
> **Avanesov said:**
> Sorry for the delay in replying. I will test/double check whether using the UUID prevented this behavior, I thought it had done it again even after making this change but im not sure.

As for using BTRFS, I do want to give it a spin. All the data I have on it is either expendable or saved in an alternate location. Also, as I understand the scrub function will repair errors as long as there are mirror copies of it, and I am running a raid10.

Do you have any insight as to why my device controllers are being resolved in different orders? I work IT and have been in the business for about 8 years now but this is something I have never seen or had to take notice of before. I would think the device enumeration should happen the same order every time unless something changes.

I wish I had a good answer for this, but I've never experienced it on my own servers or at work before, but I've seen a number of users on this forum with a similar problem, and addressing disks or arrays by UUIDs is the easiest way to mitigate this issue.

---

### Post by Avanesov on 2012-06-05
Well, it is currently addressed by UUID, but it diddnt resolve the problem. We had a storm come through while I was at work today and my wife shutdown the server (ungraciously), when I started it back up about 20 min ago it was the same thing. Mounting failed and I had to run "btrfs device scan" and then "mount -a" worked just fine.

I am still learning how to work some things in Linux, but I think ill try and get a script to run the device scan during boot, just before the mount takes place.

---

### Post by rubylaser on 2012-06-05
Or, you could remove the /etc/fstab entry, and add the scan followed by the mount to /etc/rc.local.

---

### Post by Avanesov on 2012-06-06
Good idea, I think ill do that.

---

