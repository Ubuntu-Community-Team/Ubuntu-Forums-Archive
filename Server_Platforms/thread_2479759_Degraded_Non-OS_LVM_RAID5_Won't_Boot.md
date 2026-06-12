---
title: "Degraded Non-OS LVM RAID5 Won't Boot"
date: 2022-10-05
forum: Server Platforms
---

### Post by geebee75 on 2022-10-05
Trying LVM for the first time because I'd like to try SSD caching, however my failed disk test isn't working.

Note that this is a completely separate set of disks and volume than what the OS is on. In fact I added the disks after initial Ubuntu install.

I've created a small 10GB LVM pool, and assigned it all to a RAID5 LV group as follows:

pvcreate /dev/sda1 /dev/sdb1 /dev/sdc1
vgcreate LVMVolGroup /dev/sda1 /dev/sdb1 /dev/sdc1
lvcreate --type raid5 -l 100%FREE -i 2 -n test LVMVolGroup

Then I format and mount it. ( mount /dev/LVMVolGroup/test /data)

After waiting for the RAID to sync, I pull the plug on /dev/sdc thereby failing it. So long as the system stays booted, the mount still works and the test data I put on it is still accessible.

However when I reboot, the boot stops because it can't find/mount this failed volume. Remember, this is not an OS volume this is independent. If I remove the mount from fstab it will then boot, however  /dev/LVMVolGroup no longer exists at all.

Basically defeating the purpose of having RAID5 if it dies when one of the disks does. It's supposed to keep running degraded until the disk is replaced - even after reboot - just like non-LVM RAID does, shouldn't it?

What am I doing wrong?

Thanks in advance!

---

### Post by #&amp;thj^% on 2022-10-05
To be sure have a look in:
```
sudo lvmdiskscan
```
does it show?
Mine:
```
# lvmdiskscan
  /dev/nvme0n1p1 [       1.00 GiB] 
  /dev/sda1      [     511.99 MiB] 
  /dev/nvme0n1p2 [      <7.82 GiB] 
  /dev/sda2      [     237.94 GiB] LVM physical volume
  /dev/nvme0n1p3 [    <229.66 GiB] 
  /dev/sdb1      [      <4.55 TiB] 
  /dev/sdc1      [      <3.64 TiB] 
  /dev/sdf1      [     465.76 GiB] 
  /dev/sdg1      [      15.98 MiB] 
  /dev/sdg2      [    <495.56 GiB] 
  /dev/sdg3      [     435.94 GiB] 
  0 disks
  10 partitions
  0 LVM physical volume whole disks
  1 LVM physical volume

```
EDIT: Also check with:
```
# pvscan 
  PV /dev/sda2   VG system          lvm2 [237.91 GiB / 0    free]
  Total: 1 [237.91 GiB] / in use: 1 [237.91 GiB] / in no VG: 0 [0   ]

```
Also is grub installed on the needed drives?

---

### Post by geebee75 on 2022-10-05
Hello, remember I was saying this is not the OS set. It's just data, completely independent of the OS drives. System boots fine if I remove the mount with the problem from fstab. However, as I've pointed out, you shouldn't have to. And the volume shouldn't just disappear after reboot. Makes RAID5 pointless.

Long and short, after reboot, the /dev/LVM device is missing. When it should still be there, mount as Degraded. And because /dev/LVM device is missing - and it's in fstab - the system won't boot.

So if we solve why the LVM device disappears when it loses a disk that will also solve the boot problem.

EDIT: "vgchange -ay" re-establishes the device and it can now be mounted, but why do you need to run this each boot?

---

### Post by volkswagner on 2022-10-05
I’m no expert. I’ve only created LVM physical volumes on top of RAID. Looking at your commands it seems logical to me your LVM with missing disk causes fatal error. The PV is missing a member. 

Why not create MDADM RAID device first then use /dev/mdx as your PV?

---

### Post by #&amp;thj^% on 2022-10-06
> **geebee75 said:**
> Hello, remember I was saying this is not the OS set. It's just data, completely independent of the OS drives. System boots fine if I remove the mount with the problem from fstab. However, as I've pointed out, you shouldn't have to. And the volume shouldn't just disappear after reboot. Makes RAID5 pointless.


I found that to read very clear to me>>>frustration is not what is needed here. ;)
I'll leave you solve it then,  you seem to have firm grasp on your problem. ;)
Good Luck

---

### Post by MAFoElffen on 2022-10-06
You have not posted the contents of your '/etc/fstab' file... But if in your fstab line for that mount, in the mount options, use 'nobootwait' to tell it it's okay to boot if that specific mount fails. (The order of precedence on that option does matter there...)

Since that mount is non-OS, it should be okay to boot without it. That gives you a chance to boot and repair it if it does not come up.

I know you are testing for the what-if's... But that fstab mount option will take care of that test-case, if that use-case event occurs in the future.

---

### Post by geebee75 on 2022-10-06
> **1fallen said:**
> I found that to read very clear to me>>>frustration is not what is needed here. ;)
I'll leave you solve it then,  you seem to have firm grasp on your problem. ;)
Good Luck

Sorry you're so offended - your asking if I had Grub installed on the non-os, non-boot data array therefore seem to be troubleshooting a problem with  the boot volumes thus my reminder. Was just to save your time.

---

### Post by geebee75 on 2022-10-06
> **MAFoElffen said:**
> You have not posted the contents of your '/etc/fstab' file... But if in your fstab line for that mount, in the mount options, use 'nobootwait' to tell it it's okay to boot if that specific mount fails. (The order of precedence on that option does matter there...)

Since that mount is non-OS, it should be okay to boot without it. That gives you a chance to boot and repair it if it does not come up.

I know you are testing for the what-if's... But that fstab mount option will take care of that test-case, if that use-case event occurs in the future.

Ah sorry, I didn't think to include the relevant fstab line in my original post. It does not contain 'nobootwait', so I will try that. I think you're correct that will prevent it from failing a boot. Still won't solve the problem as to why LVM decides to not create it's /dev/device for a degraded R5 volume on boot however I'm going to try messing with using LVM under MD as was suggested earlier. (I didn't know you could do that, although I guess it makes some sense).

Here's the line anyway:

```
UUID=6d024e02-1a8b-4477-a8ee-e6e1043fa1a3 /data ext4 defaults,discard        1 2
```

---

### Post by MAFoElffen on 2022-10-07
> **geebee75 said:**
> Ah sorry, I didn't think to include the relevant fstab line in my original post. It does not contain 'nobootwait', so I will try that. I think you're correct that will prevent it from failing a boot. [COLOR=#ff0000]Still won't solve the problem as to why LVM decides to not create it's /dev/device for a degraded R5 volume on boot [/COLOR]however I'm going to try messing with using LVM under MD as was suggested earlier. (I didn't know you could do that, although I guess it makes some sense).

Here's the line anyway:

```
UUID=6d024e02-1a8b-4477-a8ee-e6e1043fa1a3 /data ext4 defaults,discard        1 2
```

I'll try to explain that further to include... that will let it boot if there is something wrong with the "file system"... or the file system is not available... which I would test via changing the UUID in the fstab (not by not powering down the drives.) 

If the drives themselves are not powered up, then the drives are not available as Physical Volumes (PV's), then the LVM would fail. So logically, that would happen when you did that... as explained by others previously in this thread... So yes, if one of the drives completely fails, the LVM PV will fail, because you had everything contained within ONE LVM PV... Explained further below. 

The question is then even though your main system is on other disks, is it on LVM? and if on LVM, is it on the same PV as your Raid? if so, then it isn't segmented/isolated as you thought, right?

Usually. as an exercise, I would have students partition disks and set up a RAID0 for system and RAID5 for Data... That way if something was wrong with the system it is segmented/isolated from the system... or vice-versa.

If you setup LVM on those... then put them on different LVM-PV's.

When I lectured on setting up systems (Disks, RAID, LVM or ZFS), I would use the example of Russian Dolls, visualizing Nested Containers. RAID, LVM: PV, VG, LV... Or RAID, ZFS: Pools. Think of which container comes first, and if the container is nested within another container... If an outer container fails, the everything within that container fails... So then you isolate your outer containers and create another nesting object.

If a Disk fails, and the partition on that disk will fail. It the partition fails as a RAID member, RAID5 degrades but continues... But if the disk and the partition is a LVM PV extent, as part of an LVM, then the PV of that LVM fails (if completely gone.).

As you had it setup, it was the later... You had all setup within one LVM PV. If one LV of the RAID5 had a read/write problem in the filesystem, then the RAID5 would degrade. But if I disk failed completely, then the whole PV would fail. If the PV had been separate from the system's LVM PV, then whole whole would continue. But you tested the worst-case first.  Usually, you get disk and filesystem error's before that, when you can move a disk off the PV before then, but like I said, you tested worst-case (total failure) first...

Whereas, if you set the outer container as RAID1 for system and an LVM name PV1; RAID5 for Data and an LVM with name PV2. You can see then there is some isolation... where you can grow and or recover from... a bit more logical?

Then ZFS is a different animal...

EDIT: you can certainly setup RAID within LVM and ZFS. For those, that consideration is for the most common failure, which is read/write failures, which is usually a filesystem errors... Then the contained RAID would degrade. For LVM, you would move data off that disk: By shrinking the other nested containers, before removing the disk off as an extent, then add another disk as another PV extent, then grow the nested containers again. That is if the disk didn't have a complete total failure.

---

### Post by #&amp;thj^% on 2022-10-07
> **geebee75 said:**
> Sorry you're so offended - your asking if I had Grub installed on the non-os, non-boot data array therefore seem to be troubleshooting a problem with  the boot volumes thus my reminder. Was just to save your time.

Not offended at all, that's just a waste. It was a simple question with a yes or no answer. I'm unfamiliar with your skill set, so questions are how we trouble shoot.
Your in great hands with MAFoElffen.

---

### Post by TheFu on 2022-10-07
Are you using the "nofail" mount option for the LV that's RAID5?
lvmraid manpage has some repair commands with caveats.  The "Device Failure" section should help too.

```
$ lvchange -ay --activationmode complete|degraded|partial LV
```

To see the default activation mode, use:
```
$ lvmconfig --type default activation/activation_mode
```

It should go without saying, but backups, scrubbing, and monitoring of the physical and logical devices is necessary.

---

### Post by #&amp;thj^% on 2022-10-08
> **TheFu said:**
> Are you using the "nofail" mount option for the LV that's RAID5?
lvmraid manpage has some repair commands with caveats.  The "Device Failure" section should help too.

```
$ lvchange -ay --activationmode complete|degraded|partial LV
```

To see the default activation mode, use:
```
$ lvmconfig --type default activation/activation_mode
```

It should go without saying, but backups, scrubbing, and monitoring of the physical and logical devices is necessary.

just this minute, I was going to post your almost identical suggestion.
In the beginning OP states "Trying LVM for the first time because I'd like to try SSD caching"
So hopefully they don't have a lot of important data/stuff to lose.
I'm treading lightly here, I seemed to have asked a very silly question to the OP's view.
I don't discount installing grub to or for a Non-OS LVM is silly for someone that knows LVM, but you'd be shocked at the number of times that occurs...
Anyway still hoping the OP finds a solution. ;)

---

### Post by TheFu on 2022-10-08
> **volkswagner said:**
>  
Why not create MDADM RAID device first then use /dev/mdx as your PV?

mdadm isn't needed.  LVM has RAID capabilities built in.

---

### Post by geebee75 on 2022-10-10
> **MAFoElffen said:**
> I'll try to explain that further to include... that will let it boot if there is something wrong with the "file system"... or the file system is not available... which I would test via changing the UUID in the fstab (not by not powering down the drives.) 

If the drives themselves are not powered up, then the drives are not available as Physical Volumes (PV's), then the LVM would fail. So logically, that would happen when you did that... as explained by others previously in this thread... So yes, if one of the drives completely fails, the LVM PV will fail, because you had everything contained within ONE LVM PV... Explained further below. 

The question is then even though your main system is on other disks, is it on LVM? and if on LVM, is it on the same PV as your Raid? if so, then it isn't segmented/isolated as you thought, right?

The OS volume isn't on LVM - it's just straight MD. The LVM stuff in question is on other disks, and isolated.


> **MAFoElffen said:**
> Usually. as an exercise, I would have students partition disks and set up a RAID0 for system and RAID5 for Data... That way if something was wrong with the system it is segmented/isolated from the system... or vice-versa.

Yes, exactly my best-practice method as well - which is what I've done here. I guess the only difference is that in this case, since I'm new to using LVM under Linux I kept the LVM totally separate from the OS.

> **MAFoElffen said:**
> When I lectured on setting up systems (Disks, RAID, LVM or ZFS), I would use the example of Russian Dolls, visualizing Nested Containers. RAID, LVM: PV, VG, LV... Or RAID, ZFS: Pools. Think of which container comes first, and if the container is nested within another container... If an outer container fails, the everything within that container fails... So then you isolate your outer containers and create another nesting object.

If a Disk fails, and the partition on that disk will fail. It the partition fails as a RAID member, RAID5 degrades but continues... But if the disk and the partition is a LVM PV extent, as part of an LVM, then the PV of that LVM fails (if completely gone.).

As you had it setup, it was the later... You had all setup within one LVM PV. If one LV of the RAID5 had a read/write problem in the filesystem, then the RAID5 would degrade. But if I disk failed completely, then the whole PV would fail. If the PV had been separate from the system's LVM PV, then whole whole would continue. But you tested the worst-case first.  Usually, you get disk and filesystem error's before that, when you can move a disk off the PV before then, but like I said, you tested worst-case (total failure) first...

Whereas, if you set the outer container as RAID1 for system and an LVM name PV1; RAID5 for Data and an LVM with name PV2. You can see then there is some isolation... where you can grow and or recover from... a bit more logical?

This makes sense actually - thanks for the explanation. Up to this point I've been doing the RAID5 in LVM directly, nothing nested. (lvcreate --type raid5). So I'll keep the LVM alive if a drive is lost by taking a nested approach with MD to handle the RAID. At least I think that's what you're trying to say since it makes sense.

---

### Post by TheFu on 2022-10-10
I've been actively removing mdadm from my RAID setups and moving to LVM-only RAID that last 2 yrs. But I don't use RAID5 and haven't in about 10 yrs when we switched to RAID1 or RAID10 only.

For data storage, I'd move to ZFS for better data protection and straight RAID of any sort can provide.

We all have different requirements. Just be certain the correct level is selected for the data integrity required.

---

### Post by geebee75 on 2022-10-11
> **TheFu said:**
> mdadm isn't needed.  LVM has RAID capabilities built in.

True, but I found it to be a management nightmare. My failed disk tests resulted in an unbootable system - even though I don't have LVM on the boot disks. (These are just separate test disks). Plus some other issues with LVM was a real PITA when you have a failed disk.

Now ZFS on the other hand, is a investigation/test lab I'll do another day!

---

### Post by TheFu on 2022-10-11
The more you know and use LVM, the more you'll come to appreciate the flexibility which is lacking in multi-layered storage stacks.  I'm a little surprised that creating RAID sets doesn't automatically handle degraded storage. I think there's a setting in the lvm.conf file to do that, but it is definitely possible to mount a degraded RAID1 after a failure.  When I was testing it, I don't remember any problems doing it or finding the commands.  Usually if anything is non-obvious, I'll take some notes, but I don't have any.

OTOH, ZFS is a completely different way to looking at storage and there are huge groups of enterprise admins who won't use anything else unless it isn't an option.

---

### Post by MAFoElffen on 2022-10-11
> **geebee75 said:**
> True, but I found it to be a management nightmare. [COLOR=#ff0000]My failed disk tests resulted in an unbootable system - even though I don't have LVM on the boot disks.[/COLOR] (These are just separate test disks). Plus some other issues with LVM was a real PITA when you have a failed disk.
But  as I and TheFu posted, either of those options would have resulted in a  bootable system if that happened again... That was not the fault of LVM itself.

I agree with TheFu.

Now I can step up to defend LVM. I love it. Just like mdadm, *there  is a learning curve*, but less of a learning curve. I can personally tell you that years  ago I became a project leader for a GUI Wrapper for mdadm. 'mdadm' has sooooo many options and caveats.  (I would be pulling my hair out and discuss those things with TheFu... LOL)

Once you learn how LVM works and how to manage it, it  is easy and so useful. Snapshots, shrink/grow, moving off and adding  disks, RAID, etc. Most things while it is still running on a live filesystem! Very flexible and **very dependable**. (mdadm or real metal RAID does not allow live changes.)

The  dependability, ease of management, and learning how to recover LVM systems  is what won me over in changing how I did business with my own systems  and my own disaster/recovery plan.  (Have good backups. Always do backups!!!!)

The server business is uptime. RAID  takes a long time to assemble/reassemble. Storage disks are inexpensive. A lot  of times it is faster and easier to change out disks, boot off  pre-prepared boot media, install a clean system with LVM, and restore  data... Compared than rebuilding and reassembling large RAID Arrays. If someone wanted full uptime, you would be looking at clusters.

EDIT: Total failure.... Think of being back up in an hour, compared to days...
> **geebee75 said:**
> Now ZFS on the other hand, is a investigation/test lab I'll do another day!
I started doing ZFS with Solaris and OpenSolaris back in 2005. It is like LVM, but also different in how it works. It is also dynamic, flexible and dependable... and most can be done on live file systems. A bit more of a learning curve than LVM. I'm the contributor to 'bootinfo' and 'bootrepair' on recovering ZFS-On-Boot..

The thing with Linux is that there are so many choices.

---

