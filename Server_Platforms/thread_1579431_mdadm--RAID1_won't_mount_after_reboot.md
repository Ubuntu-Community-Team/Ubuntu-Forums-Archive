---
title: "mdadm--RAID1 won't mount after reboot"
date: 2010-09-21
forum: Server Platforms
---

### Post by disconap on 2010-09-21
Hi!  Ok, going to be thorough here, but the main problem I'm having is that I can't seem to mount my RAID1 after rebooting my server (my RAID5 mounted fine).  I can assemble it fine, proc/mdstat shows it up and running with zero problems, but it refuses to open in its mount point.

Here are the details:

Rebooted.
Checked /proc/mdstat and saw a ghost RAID, md_d1, so I deleted it
Ran mdadm --assemble --scan; it ignored the RAID5 and started the RAID1 with only one drive
Stopped the RAID1 and the ghost md_d1 RAID
Assembled RAID5 manually (no problems)
Assembled RAID1 manually(no problems)
Mounted RAID5 and two external drives to their mount points, no problem.
Tried to mount RAID1 and got this error:
```
mount: /dev/md1 already mounted or /mnt/raid2 busy
```
Ran /proc/mdstat again, ghost RAID was there, so I stopped it.
Tried to mount RAID1 again, this time got this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Fdisk -l output showed this for both of the drives (and all 4 of the functioning RAID5 drives):
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sd*'! The util fdisk doesn't support GPT. Use GNU Parted.
```
mdadm --detail /dev/md1 shows this:
```
       Version : 00.90
  Creation Time : Tue Sep 14 23:27:26 2010
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Sep 15 19:01:41 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : REMOVED (but all normal)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       80        0      active sync   /dev/sdf
       1       8       96        1      active sync   /dev/sdg
```
Tried stopping and reassembling the RAID and still no dice.  Any idea what's going on?  I don't just want to fix this, I really want to understand why it's doing it, as I have had nothing but trouble with mdadm since I started using it (on EVERY reboot I have had to zero superblocks, replace filesystems, delete ghost RAIDs, reassemble manually, then stop, then reassemble manually, rebuild a drive that didn't crash, etc--never ONCE a smooth reboot)...

EDIT:  Forgot to add, now attempts to mount result in this:
```
mount: /dev/md1 already mounted or /mnt/raid2 busy
mount: according to mtab, /dev/md1 is already mounted on /mnt/raid2
```
Still cannot access the RAID at the mount point...

---

### Post by disconap on 2010-09-23
Well, I ran FSCK -y which worked and made it mountable but blanked the RAID.  Not a big deal as it was just a back-up drive, but still kinda sucks.  *shrug*

---

### Post by ian dobson on 2010-09-24
Hi,

I imagine you forgot to update your /etc/mdadm/mdadm.conf and recreate the inital ram disk. YOu need to recreate the inital ram disk as mdadm needs the dev mappings from this file in the pre boot environment.

If you don't have an actual mdadm.conf in your ram disk mdadm tries to workout what the array is called but ends up getting it wrong most of the time (/dev/md0_p1)

Regards
Ian Dobson

---

### Post by disconap on 2010-09-24
Appreciated, but this isn't a system drive, so I don't think that's a necessary step, is it?

---

### Post by ian dobson on 2010-09-25
> **disconap said:**
> Appreciated, but this isn't a system drive, so I don't think that's a necessary step, is it?

Well, if mdadm starts up and creates the block device (/dev/mdX) with the wrong name then it can't be renamed. So maybe it's better if the mdadm.conf in the init ram disk is correct.

Note: an update-initramfs -u only takes afew seconds :)

Regards
Ian Dobson

---

### Post by disconap on 2010-09-26
Ok, ran that.  Is that all I'll need to do to prevent this from happening again?  It'll be moot until the next major security update, as I don't reboot often, but eventually I'll need to...

---

### Post by ian dobson on 2010-09-27
> **disconap said:**
> Ok, ran that.  Is that all I'll need to do to prevent this from happening again?  It'll be moot until the next major security update, as I don't reboot often, but eventually I'll need to...

Just run update-initramfs -u whenever you change your RAID arrays.

Regards
Ian Dobson

---

### Post by disconap on 2010-10-06
Thank you for the help, Ian, it is greatly appreciated.  Will post back after next reboot.  :)

---

### Post by disconap on 2010-10-17
Ok, just (finally) had to reboot. And guess what?  The RAID1 won't assemble again.  Grrrr.

I don't get it at all, I'm getting the exact same error...

---

### Post by disconap on 2010-10-17
...and this time same thing.  The "ghost raid" was there again (md_d1) and it was using one of the R1 drives, which is why I couldn't assemble the R1.  I had to stop the md_d1 first; what is causing it to show up in the first place?  And why, once I assemble the R1 after stopping the fake one, can't I mount?

EDIT TO ADD: Oh, and re-reading this I realize my confusion from earlier--I do not have my arrays set to automatically assemble and mount, I do that manually (as I reboot very rarely, I felt it would be better to do it manually)...

EDIT2 TO ADD: Also, getting this error again:
mount: /dev/md1 already mounted or /mnt/raid2 busy

Tried unmounting /dev/md1 and it says it is not mounted; tried deleting the raid2 directory and making a new one and I'm still getting the same above error.   cat /proc/mdstat shows the ghost raid still there:

md_d1 : inactive md1p1[0](S)
      488383936 blocks

Tried --remove and it still shows up.  Also, there is no md1p1, no idea what that is.

---

### Post by disconap on 2010-10-24
*gentle nudge*

No ideas?  I can't get the RAID1 to mount OR stop now, so I can't even blank it and build a new one...

---

### Post by disconap on 2010-11-09
After much searching I found a thread on here actually that gave me an (I think) solution; at least it worked on the most recent reboot.  I already closed the window so I can't credit the person who suggested it (sorry whomever you are, but you are a saint), but here's the solution in case you googled your way to this thread:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Then reboot.  Somehow, even if you manually configure the mdadm.conf file, it can get all sorts of messed up.  Upon reboot everything seems to be working perfectly.

---

