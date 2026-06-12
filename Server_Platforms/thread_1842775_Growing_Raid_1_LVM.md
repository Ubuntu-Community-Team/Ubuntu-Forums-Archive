---
title: "Growing Raid 1 LVM"
date: 2011-09-12
forum: Server Platforms
---

### Post by harveyd on 2011-09-12
Hi,

I have Ubuntu server 11.04 with 2 x 500GB in Raid 1 configuration with LVM on top.

I have 2 x 1.5TB drives that at some point I will want to replace the 500gb drives with.

What is the best way to replace the 500gb drives? I presume 1 at a time and allowing raid sets to rebuild and then growing the LVM.

Any advice would be appreciated.

Cheers

Harvey.

---

### Post by arrrghhh on 2011-09-12
I actually think setting up another RAID1 array with the two 1.5tb drives would be best.  Then copy the data from the old array to the new.

I'm not sure you can replace drives like you want to... I would assume the array would rebuild as 500gb, and you'd have 1tb wasted...

I'm no RAID or LVM expert, so perhaps I'm just misunderstanding - but the method I outlined would definitely work, assuming you have the ability to run both RAID array's at the same time.

---

### Post by YesWeCan on 2011-09-12
Many ways to approach this.

You could remove a 500GB drive from the array and disconnect it. Connect a 1.5TB and copy the partition table from the remaining 500GB to the 1.5TB. Then add the 1.5TB to the array. It will resync. Then remove the 500GB from the array and add the second 1.5TB to the array. Let it resync. Finally, resize the array partition and then expand the LVM.

Or, as arrrghhh says, make a big, LVM array with the 1.5TB drives first, then copy (using rsync) all your files to it, then reinstall Grub. Make sure everything works fine before recycling the 500GB drives.

I reckon I'd do the latter.

---

### Post by jtupulis on 2011-09-12
I think that first method will not work - you'll get 0.5TB array on 1.5TB disks.

And where is a value for LVM in your case?

---

### Post by harveyd on 2011-09-12
Thanks to you both.

Unfortunately it is a NAS case and only allows the 2x 3.5" drive and 1x 2.5" drive.

The 2.5" has the OS and the 2 x 3.5" holds the data and is raided.

@yeswecan, I like the sound of your first idea, that was the rough idea I had in mind. Do you have any specific steps I could follow?

Harvey

---

### Post by jtupulis on 2011-09-12
Case is not a bottleneck, number of (SATA?) ports on motherboard is. You can let the disks "hang in wires" while copying.

This could work: detach one disk from existing RAID array, remove it from system, add new 1.5TB one, create new array on this disk, copy data from old array to new one, detach last 0.5TB disk from system, add another 1.5TB one, add the disk to array, let it resync. Sounds sophisticated :)

Better, of course is to follow arrrghhh. Or backup data somewhere, destroy old array, create new one and copy data.

---

### Post by rubylaser on 2011-09-12
Either way YesWeCan mentioned will work fine.  I personally would do his first method, but if you're not very comfortable with mdadm and resizing LVM and filesystems, I'd avoid it.  The second method, if far safer if you don't feel very confident with the previous mentioned tools.

---

### Post by YesWeCan on 2011-09-12
> **harveyd said:**
> @yeswecan, I like the sound of your first idea, that was the rough idea I had in mind. Do you have any specific steps I could follow?
Let me have a go. Others please pitch in if I blunder. ;)

Shut down
Disconnect one of the 500GB drives. Connect a 1.5TB drive
Power-up and boot a live CD/USB

Determine the drive and partition names
```
sudo sfdisk -luS
```

I am going to assume the 500GB is sda and the 1.5TG is sdb, but change these names as appropriate to fit your reality.

Clone the 500GB to the 1.5TB
```
sudo dd if=/dev/sda of=/dev/sdb bs=64k conv=notrunc,noerror
```
This may take quite some time, perhaps an hour or more, and it will tell you absolutely nothing at all about its progress and this will put you on edge a little.

Shutdown.
Disconnect the 500GB
Connect the second 1.5TB
Boot (degraded) off the 1st 1.5TB

Check the drive names again. I am going to assume the first 1.5TB is sda and the second is sdb, change these names as appropriate to fit your reality.
Copy the partition table to the second 1.5TB
```
sudo sh -c "sfdisk -d /dev/sda | sfdisk /dev/sdb"
```

[NOTE: in the unlikely event that sfdisk reports finding a GPT format then stop here and report in.]

Now add sdb to the degraded array. I'm assuming your array name is md0 but change this name as appropriate to fit your reality.
```
sudo mdadm /dev/md0 --add /dev/sdb
```
and let it resync
```
watch cat /proc/mdstat
```
Well some people get a kick out of this. :P

Reinstall Grub.
```
sudo dpkg-reconfigure grub-pc
```
and select /dev/sda and /dev/sdb for the boot loader

Ok, so by this point you should have a 500GB size RAID-1 array on a pair of 1.5TB disks. Next step is to grow your array to fill the space. Report back at this point for the next instalment.

---

### Post by rubylaser on 2011-09-12
> **YesWeCan said:**
> Let me have a go. Others please pitch in if I blunder. ;)

Shut down
Disconnect one of the 500GB drives. Connect a 1.5TB drive
Power-up and boot a live CD/USB

Determine the drive and partition names
```
sudo sfdisk -luS
```

I am going to assume the 500GB is sda and the 1.5TG is sdb, but change these names as appropriate to fit your reality.

Clone the 500GB to the 1.5TB
```
sudo dd if=/dev/sda of=/dev/sdb bs=64k conv=notrunc,noerror
```
This may take quite some time, perhaps an hour or more, and it will tell you absolutely nothing at all about its progress and this will put you on edge a little.

Shutdown.
Disconnect the 500GB
Connect the second 1.5TB
Boot (degraded) off the 1st 1.5TB

Check the drive names again. I am going to assume the first 1.5TB is sda and the second is sdb, change these names as appropriate to fit your reality.
Copy the partition table to the second 1.5TB
```
sudo sh -c "sfdisk -d /dev/sda | sfdisk /dev/sdb"
```

[NOTE: in the unlikely event that sfdisk reports finding a GPT format then stop here and report in.]

Now add sdb to the degraded array. I'm assuming your array name is md0 but change this name as appropriate to fit your reality.
```
sudo mdadm /dev/md0 --add /dev/sdb
```
and let it resync
```
watch cat /proc/mdstat
```
Well some people get a kick out of this. :P

Reinstall Grub.
```
sudo dpkg-reconfigure grub-pc
```
and select /dev/sda and /dev/sdb for the boot loader

Ok, so by this point you should have a 500GB size RAID-1 array on a pair of 1.5TB disks. Next step is to grow your array to fill the space. Report back at this point for the next instalment.

This looks correct, also, if you want to monitor the process of the dd operation, you can get it to write to the screen for you. Just use top to get the pid of the dd process (1st column).
```
top - 20:31:34 up 1 day, 9 min,  2 users,  load average: 2.80, 2.74, 2.58
Tasks:  92 total,   3 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us, 57.7%sy,  0.0%ni, 26.6%id,  0.0%wa,  1.3%hi, 14.4%si,  0.0%st
Mem:   4063928k total,  4032172k used,    31756k free,    88520k buffers
Swap:  6369732k total,        0k used,  6369732k free,  3643500k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
**10428** root      20   0 10660 1688  552 R 31.9  0.0   0:02.88 dd
```

Then get the process to write to the screen for you. You'll want to open a new terminal window and run this as root.
```
sudo -i
watch -n 10 kill -USR1 **10428**
```

It will look like this back on the other window...
```
root@backup:~# dd if=/dev/zero of=/home/rubylaser/testfile.out bs=1M count=10000
1495+0 records in
1495+0 records out
1567621120 bytes (1.6 GB) copied, 30.6555 s, 51.1 MB/s
```

That should allow you to not be waiting in the dark for it to finish :)

@YesWeCan
Who doesn't like watching the process of a raid array re-syncing :)

---

### Post by harveyd on 2011-09-13
@rubylaser & @YesWeCan: Thanks to you both for your input. Presumably I would _not_ need to boot to a live CD as the Raid1/LVM device is data only and the OS is on a separate independent drive? Is just unmounting the LVM from the file system enough? If you can confirm I will get this part completed.

---

### Post by rubylaser on 2011-09-13
Yes, if it's not your root partition, just umount the filesystem, and you should be good to go.

---

### Post by YesWeCan on 2011-09-13
> **harveyd said:**
> @rubylaser & @YesWeCan: Thanks to you both for your input. Presumably I would _not_ need to boot to a live CD as the Raid1/LVM device is data only and the OS is on a separate independent drive? Is just unmounting the LVM from the file system enough? If you can confirm I will get this part completed.
You have a separate OS drive? In that case it is even easier.

Just disconnect a 500GB and connect a 1.5TB
Boot your Ubuntu drive
```
sudo sfdisk -luS
```to determine drive names. I'll assume the 500GB is sdb and 1.5TB is sdc and your array is md0, change to fit your reality.
```
sudo sh -c "sfdisk -d /dev/sdb | sfdisk /dev/sdc"
sudo mdadm /dev/md0 --add /dev/sdc
watch cat /proc/mdstat
```("watch" added for rubylaser's enjoyment ;) )

Shutdown
Disconnect 500GB and connect second 1.5TB
Boot your Ubuntu drive
```
sudo sfdisk -luS
```to determine drive names. I'll assume the first 1.5TB is sdb and the second 1.5TB is sdc, change to fit your reality.
```
sudo sh -c "sfdisk -d /dev/sdb | sfdisk /dev/sdc"
sudo mdadm /dev/md0 --add /dev/sdc
watch cat /proc/mdstat

```Once you've got to this point, would you post the outputs of:
[COLOR=DarkSlateBlue]sudo sfdisk -luS
sudo blkid
cat /proc/mdstat
sudo pvs[/COLOR]

---

### Post by harveyd on 2011-09-17
Hey guys im away at the moment. Will get back to you on my return!

---

