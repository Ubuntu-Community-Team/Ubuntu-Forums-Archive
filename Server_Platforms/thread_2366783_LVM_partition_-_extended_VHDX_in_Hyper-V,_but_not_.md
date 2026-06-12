---
title: "LVM partition - extended VHDX in Hyper-V, but not sure how to extend drive in Ubuntu?"
date: 2017-07-21
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2017-07-21
Hello,

I've setup a new Ubuntu server (16.04.2 LTS).  I put the XFCE GUI on it (we are mostly a Windows shop).  This server resides on a Hyper-V host.  I originally created the server with a 250gb VHDX, but my boss wanted me to increase this to 1TB.  I extended the drive in Hyper-V succesfully.  In the past I've booted from Gparted and used that, but I guess it does not work with LVM?  I've done a ton of reading on this but haven't found anything that works.

How do I get the free space to show up?

How do I roll this free space into the root partition?

---

### Post by #&amp;thj^% on 2017-07-21
Will this help? [https://blogs.technet.microsoft.com/askcore/2008/09/18/expanding-disks-attached-to-hyper-v-vms-may-not-reflect-adjusted-size-immediately-on-ws2008/](https://blogs.technet.microsoft.com/askcore/2008/09/18/expanding-disks-attached-to-hyper-v-vms-may-not-reflect-adjusted-size-immediately-on-ws2008/)

---

### Post by 47_MasoN_47 on 2017-07-21
Thanks, but no.  I know how to handle the Windows part. It's how to make the Ubuntu part work that I'm not sure of.  It's been quite a number of years since I've been a linux server admin.

---

### Post by darkod on 2017-07-21
Start by listing the partition sizes in ubuntu. Assuming you have only one disk and that is /dev/sda, you can check the partition list in MiB with:
```
sudo parted /dev/sda unit MiB print
```

You extended the disk size from Hyper-V, but the partition on the disk is still X GiB. It doesn't extend automatically. You can extend the partiiton, or if you have LVM you could create new partitions in the free space and add it to the LVM. That has less possibility for errors and is easier to do.

Post the output of the above command and we will know more about how your disk looks like.

---

### Post by 47_MasoN_47 on 2017-07-21
That's what's bazaar to me.  I assumed sda should increase to 1tb instead of showing as 250gb.  It looks to me though like it's still showing as 250gb.

EDIT: The terminal output is in the attachment.

---

### Post by darkod on 2017-07-21
Hmmm, according to this the disk is extended but only to 512GB. You see it says disk sda is 512000MiB which is 500GiB. It's not 1TB, or at least it doesn't see it as 1TB.

If you want to, you can try extending the ubuntu installation as it is (to 500GB) or first try to check why you are not seeing 1TB.

---

### Post by 47_MasoN_47 on 2017-07-21
Oh, it is supposed to be 500gb.  I was thinking of another server I had to extend to 1tb.

So how would I extend it to take up the full 500gb?  I tried using GParted, but that didn't work.

---

### Post by darkod on 2017-07-21
1. You see that /dev/sda5 ends at 255999MiB. You also see the disk is 512000MiB. Open parted and create new logical partition from 256000MiB to 512000MiB.
```
sudo parted /dev/sda
unit MiB
mkpart logical 256000 512000
print   (check that you see sda6 and start and end points are correct)
quit   (quit parted if all looks good)
```

2. After that you need to add /dev/sda6 to the LVM:
```
sudo pvcreate /dev/sda6
sudo vgextend VGname /dev/sda6   (make sure you use the correct name for your existing Volume Group in the command)
```

After this the VG will have total size of 500GB. You can extend any Logical Volume that you want. You do that with lvextend.

The final step is to extend the filesystem. Lets say you have ext4 filesystem on the LV /dev/VGname/LVname:
```
sudo resize2fs /dev/VGname/LVname
```

That's it...

---

### Post by 47_MasoN_47 on 2017-07-21
Well, I ran the parted command.  It seemed to work and said I needed to reboot.  I rebooted, and now it says it cannot find the root LVM volume group and will not boot :(

---

### Post by darkod on 2017-07-21
It said you need to reboot, or you might need to reboot? There is a difference.

If you only created one more partition and rebooted that should not create any problems. Just creating one new partition does not affect the current LVM partitions.

Try to boot the VM with Ubuntu Desktop LiveCD into live mode (Try Ubuntu), and check the partition layout and the LVM status.

---

### Post by 47_MasoN_47 on 2017-07-24
Sorry, had a server migration project for a customer Friday evening that took until yesterday afternoon to finish.  I'm back at this again now.  I'm downloading a Lubuntu desktop live CD.  I'll check the partitions and whatnot and get back to you soon.  Thanks for all the help.

EDIT: Also, I believe it said that I might need to reboot, not that a reboot was required.

---

### Post by 47_MasoN_47 on 2017-07-24
Ok. I have attached the output of the parted command I used previously.  Running sudo pvdisplay and sudo lvdisplay both return nothing, it just drops back to the ~$ prompt.

---

### Post by darkod on 2017-07-24
Hmmm, according to that output you did not create any new partition. It has the same partitions as earlier, sda1 and sda5. And now it says sda5 has 0 size.

Did you run only the mkpart command in parted previously, or you tried to grow the extended partition first?

---

### Post by 47_MasoN_47 on 2017-07-24
I ran this: 

sudo parted /dev/sda
unit MiB
mkpart logical 256000 512000

And it said that message about rebooting.  So I rebooted and then it would not boot anymore.

---

### Post by 47_MasoN_47 on 2017-07-24
So, is this just dead?  I tried to mount /dev/sda2 via the live CD and it throws an error saying that it can't mount the partition - wrong fs type, bad option, bad superblock on dev/sda2, missing codepage or helper program, or other error.

---

### Post by darkod on 2017-07-24
sda2 is the extended partition container. You wouldn't be able to mount it.

Somehow sda5 got messed up but I still can't understand why. Do you have backups of the important data?

---

### Post by 47_MasoN_47 on 2017-07-24
No.  My boss wanted it expanded, then we were going to back it up.  I'm just going to blow it away, make a new 1tb VHDX, and use ext4 instead.  LVM seems like it is way too complex.

---

### Post by darkod on 2017-07-24
Do as you see best. Just to comment that LVM is not to blame here. Somehow the existing partition got destroyed when creating a new one.

In fact, since you had LVM, it would have been best option to simply add one more 250GB disk instead of expanding the current from 250GB to 500GB. LVM allows you to easily add more physical disks to it. You don't need to expand current disks, you can simply add more.

It looks complicated to save the partition now. And maybe Hyper-V had something to do with this too. MS will always favor Windows more than Linux for its VMs.

---

