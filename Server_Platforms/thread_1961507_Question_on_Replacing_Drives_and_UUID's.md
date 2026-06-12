---
title: "Question on Replacing Drives and UUID's"
date: 2012-04-19
forum: Server Platforms
---

### Post by jlacroix on 2012-04-19
Hello everyone. I'm setting up a file server for home today, which will run Ubuntu Server 12.04. I figure since 12.04 is only a few days away I will start working on it now.

My server has two 2TB drives, and I am leaning toward software RAID. It has FakeRAID on this particular machine.

The question I have is about drive failures, and UUID's. I am a heavy Clonezilla user, and I will use Clonezilla to take an image of both drives when I finish setting up the server. My understanding is that I'd have to take an image of both drives since it's not hardware RAID. However, if both drives failed and I had to restore the image on two new drives, would the UUID's then change, and if so, make the RAID fail to come up with new drives?

---

### Post by CharlesA on 2012-04-19
Are you planning on using RAID 1? You could just image one drive and let the other rebuild.

If you are going to be using mdadm, it would see the array as a single device/drive.

---

### Post by albandy on 2012-04-19
> **CharlesA said:**
> Are you planning on using RAID 1? You could just image one drive and let the other rebuild.

If you are going to be using mdadm, it would see the array as a single device/drive.

Or buy one more drive and use RAID 5.

---

### Post by CharlesA on 2012-04-19
> **albandy said:**
> Or buy one more drive and use RAID 5.
Indeed. You'd have 4 TB of space instead of 2TB if you went with RAID5 instead of RAID1.

The only other RAID level you can do with just two drives is RAID0 and that's not really true RAID.

---

### Post by SeijiSensei on 2012-04-19
> **CharlesA said:**
> The only other RAID level you can do with just two drives is RAID0 and that's not really true RAID.

I've never really understood why RAID0 is called RAID at all, given that it's the acronym for "*Redundant* Array of Inexpensive Disks."  There's no redundancy with RAID0.

---

### Post by CharlesA on 2012-04-19
> **SeijiSensei said:**
> I've never really understood why RAID0 is called RAID at all, given that it's the acronym for "*Redundant* Array of Inexpensive Disks."  There's no redundancy with RAID0.
Indeed. It makes no sense to me.

---

### Post by jlacroix on 2012-04-19
Thanks guys.

Yes, it is going to be RAID 1, and I plan on using mdadm. I'm confused though, why wouldn't I have to image both drives with mdadm, wouldn't it not know the other drive was a RAID member unless I restored both drives at the same time? I'm also still confused on if the new drives have a different UUID, wouldn't that confuse mdadm?

---

### Post by albandy on 2012-04-19
Take a look:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

---

### Post by jlacroix on 2012-04-19
> **albandy said:**
> Take a look:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)
I've seen that before, but it doesn't answer my question, or at least I don't think it does. Are you saying that if I only image one drive, the URL you provided is the process for adding the second drive? In that case, I am thinking that if I create an image of both drives, it would save me the hassle, and if just one drive fails, I can follow the procedure you linked to replace a single drive.

But, if both drives failed and I wanted my server up fast, I would think just restoring the image of both drives would be the fastest way. However, this is where I question the UUID's. Say I grab two completely different drives (but still 2TB each) that would mean that they would have different UUID's and would cause the RAID to fail anyway, correct?

Just want to make sure my line of thinking is correct.

---

### Post by rubylaser on 2012-04-19
mdadm does not rebuild the arrays based off the disk's UUID.  It uses the array's UUID that is stored in the superblock on each raid member.  All you'd really need to do is image one of the disks for a backup.  

Each disk in a RAID1 is bootable by itself as I'm sure you know, so even if you lost both disks, you'd just need the one backup to get going again. You steps would be to use sfdisk to copy the partition structure over to a matching disk, add the new disk to the array, let it sync, and finally install grub to the new disk.

---

### Post by jlacroix on 2012-04-19
> **rubylaser said:**
> mdadm does not rebuild the arrays based off the disk's UUID.  It uses the array's UUID that is stored in the superblock on each raid member.  All you'd really need to do is image one of the disks for a backup.  

Each disk in a RAID1 is bootable by itself as I'm sure you know, so even if you lost both disks, you'd just need the one backup to get going again. You steps would be to use sfdisk to copy the partition structure over to a matching disk, add the new disk to the array, let it sync, and finally install grub to the new disk.
Thank you for your reply, that clears it up. But if I imaged both drives, am I correct in thinking that the image would be twice as large, but I'd avoid needing to do sfdisk and reinstalling grub?

---

### Post by rubylaser on 2012-04-19
> **jlacroix said:**
> Thank you for your reply, that clears it up. But if I imaged both drives, am I correct in thinking that the image would be twice as large, but I'd avoid needing to do sfdisk and reinstalling grub?

Yes, you'd end up with an image of two drives, so it should be twice as large, and you shouldn't have to copy the partitions over or re-install grub (I'd have to test this part).

---

### Post by SeijiSensei on 2012-04-19
Really I can't see any reason to image both drives since they contain identical content.  Here are the backup possibilities:

1)  Both drives fail because of an horrendous event like the server catching fire.  In that case you'd buy new drives (and probably a new server), install a clean copy of the Linux distro you ran before using mdadm to create a RAID1 array, then copy the backup onto the array.  You only need one backup copy since the mirroring would happen automatically as the files are copied.  You might need to pay attention to UUID references in /boot/grub/grub.cfg and /etc/fstab. In fstab, you could replace the UUID entry with the appropriate device name like /dev/md0 to avoid the issue.  I'm not sure how grub handles referencing the array since I never boot from a RAID device.  

2)  One drive fails.  In this case you'd replace the drive and use "mdadm --add" to insert the new drive into the array.  The system would then create the mirror automatically from the contents of the active drive.

It's easiest to think of the array as a single device just as Linux does.  Once the array is bound together, you're dealing with a single device like /dev/md0 not the component devices that compose the array.

---

### Post by rubylaser on 2012-04-19
> **SeijiSensei said:**
> Really I can't see any reason to image both drives since they contain identical content.  Here are the backup possibilities:

1)  Both drives fail because of an horrendous event like the server catching fire.  In that case you'd buy new drives (and probably a new server), install a clean copy of the Linux distro you ran before using mdadm to create a RAID1 array, then copy the backup onto the array.  You only need one backup copy since the mirroring would happen automatically as the files are copied.  You might need to pay attention to UUID references in /boot/grub/grub.cfg and /etc/fstab. In fstab, you could replace the UUID entry with the appropriate device name like /dev/md0 to avoid the issue.  I'm not sure how grub handles referencing the array since I never boot from a RAID device.  

2)  One drive fails.  In this case you'd replace the drive and use mdadm to add the new drive back into the array.  The system would then create the mirror automatically from the contents of the active drive.

It's easiest to think of the array as a single device just as Linux does.  Once the array is bound together, you're dealing with a single device like /dev/md0 not the component devices that compose the array.

+1. This is exactly what I would do.

---

### Post by CharlesA on 2012-04-19
> **SeijiSensei said:**
> Really I can't see any reason to image both drives since they contain identical content.  Here are the backup possibilities:

1)  Both drives fail because of an horrendous event like the server catching fire.  In that case you'd buy new drives (and probably a new server), install a clean copy of the Linux distro you ran before using mdadm to create a RAID1 array, then copy the backup onto the array.  You only need one backup copy since the mirroring would happen automatically as the files are copied.  You might need to pay attention to UUID references in /boot/grub/grub.cfg and /etc/fstab. In fstab, you could replace the UUID entry with the appropriate device name like /dev/md0 to avoid the issue.  I'm not sure how grub handles referencing the array since I never boot from a RAID device.  

2)  One drive fails.  In this case you'd replace the drive and use "mdadm --add" to insert the new drive into the array.  The system would then create the mirror automatically from the contents of the active drive.

It's easiest to think of the array as a single device just as Linux does.  Once the array is bound together, you're dealing with a single device like /dev/md0 not the component devices that compose the array.
+1 as well.

I am running hardware RAID, but it would act the same as software RAID.

In my case, if my server blew up, I'd recover my data from backups, but if one drive went out, I'd stick a new drive in and let it rebuild.

That being said - I do daily backups of stuff on my array, minus my dvd library (which gets backed up monthly, but hardly changes). That way if my array hoses itself - I lose 2 drives in my 3 drive array, I won't lose much data.

---

### Post by jlacroix on 2012-04-19
> **rubylaser said:**
> Yes, you'd end up with an image of two drives, so it should be twice as large, and you shouldn't have to copy the partitions over or re-install grub (I'd have to test this part).
Thank you, I appreciate your help and everyone elses too. Marking this as solved!

---

### Post by jlacroix on 2012-04-19
> **SeijiSensei said:**
> Really I can't see any reason to image both drives since they contain identical content.  Here are the backup possibilities:

1)  Both drives fail because of an horrendous event like the server catching fire.  In that case you'd buy new drives (and probably a new server), install a clean copy of the Linux distro you ran before using mdadm to create a RAID1 array, then copy the backup onto the array.  You only need one backup copy since the mirroring would happen automatically as the files are copied.  You might need to pay attention to UUID references in /boot/grub/grub.cfg and /etc/fstab. In fstab, you could replace the UUID entry with the appropriate device name like /dev/md0 to avoid the issue.  I'm not sure how grub handles referencing the array since I never boot from a RAID device.  

2)  One drive fails.  In this case you'd replace the drive and use "mdadm --add" to insert the new drive into the array.  The system would then create the mirror automatically from the contents of the active drive.

It's easiest to think of the array as a single device just as Linux does.  Once the array is bound together, you're dealing with a single device like /dev/md0 not the component devices that compose the array.
The problem with installing a clean copy of the OS is that I'd have to recopy my scripts, set up my cron jobs again, set up the users again, Unison profiles, and so on. with an image, it takes about 15 minutes or less with Clonezilla to restore the image with everything included on it.

---

### Post by jlacroix on 2012-04-19
Separate issue (not sure if I should make my own topic): I can't seem to get Ubuntu 12.04 to let me configure partitions on RAID. It seems like it wants me to have / on just one partition. When I create the RAID1 array, the option to create a partition is gone. Is this a bug?

---

### Post by rubylaser on 2012-04-19
No it's not.  You'd need to create partitions on each disk for / and swap space or /boot, /, and swap and then setup separate RAID1 arrays out of these partitions, or setup LVM on top of your array and partition that.

[These]("https://help.ubuntu.com/community/Installation/SoftwareRAID") are good directions if you haven't looked at them.

---

### Post by jlacroix on 2012-04-19
> **rubylaser said:**
> No it's not.  You'd need to create partitions on each disk for / and swap space or /boot, /, and swap and then setup separate RAID1 arrays out of these partitions, or setup LVM on top of your array and partition that.

[These]("https://help.ubuntu.com/community/Installation/SoftwareRAID") are good directions if you haven't looked at them.
Thank you!

---

