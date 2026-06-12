---
title: "LVM not available after reboot"
date: 2012-05-21
forum: Server Platforms
---

### Post by FORCED-INDUCTN on 2012-05-21
Hello

I have a hardware RAID array with LVM2 and a single logical volume.

Every time I reboot the LV comes up as not available:
FORTRESS[~]: lvdisplay
  --- Logical volume ---
  LV Name                /dev/backups/novell
  VG Name                backups
  LV UUID                fyvoDr-OohD-zRox-j6Nr-GIzq-RhUE-AqIzM0
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                10.00 TiB
  Current LE             2621440
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

Running vgchange -a y brings the LV online.

The RAID array used to be part of a software md array with another hardware array. I think that md or something might be locking the array at boot?

When I run blkid I get this:
/dev/sdb1: UUID="Linux-MDM-^M--M->M-o" TYPE="ddf_raid_member"

I have rebuilt and reportioned the array and it still shows up as ddf_raid_member

Any ideas how I can get the LV come up clean at boot?

Thanks!
--Forced

**EDIT***
Ubuntu version: 10.04
Kernel version: 3.0.0-17-server

---

### Post by darkod on 2012-05-21
I am not sure but I think ddf is bad news when you are running mdadm. What does

cat /proc/mdstat

say? Does the array look normal?

---

### Post by FORCED-INDUCTN on 2012-05-21
Yeah DDF is pretty annoying (mdamd does support it though) I was just experimenting.

/proc/mstat shows no arrays

FORTRESS[~]: cat /proc/mdstat
Personalities :
unused devices: <none>

Just to clear things up though I am not running software RAID anymore. LVM is on a hardware array with remnants of DDF metadata.

--Forced

---

### Post by darkod on 2012-05-21
Sorry, my bad. You clearly said you are running hardware raid.

Can you explain how the array was part of a software raid? I guess that led me towards mdadm.

Also, did this behavior started after a particular action/change you did, or not?

---

### Post by FORCED-INDUCTN on 2012-05-21
No problem,

The server has 2x 3ware 9650SE RAID cards with 24 2TB HDDs each. I had the hardware arrays in a software RAID 0 with mdadm to make a RAID 100 (double nested RAID 1+0+0). However I had problems with the softraid coming up broken on reboot, having to set it up every time (some bugs with the newer mdadm). I played around with the arrays for a while and tried the DDF metadata format with mdadm. I decided I didn't need RAID 100 and cleaned the disks, setup LVM and now the LV is coming up not available.

---

### Post by darkod on 2012-05-21
So, it never worked in this setup?

The only reference I found on google says that this can happen if the disks are not brought up online fast enough, usually with usb ext disks.

But since these ones are on a raid card, it might be that they are not coming up online fast enough too.

One solution suggested, although not a fancy one, is adding the vgchange -a y so that it can be run at start. I'm not sure if /etc/rc.local would be the best place for this or what.

You can also check dmesg or other logs for any hints what is wrong with the LVM coming online.

---

### Post by FORCED-INDUCTN on 2012-05-21
The server worked for about a year but when I would reboot the server it would complain that it couldn't mount the partitions on the array. But if I rebooted it again everything would come up fine. Finally it stopped working, I never found out why. 

I found that post/article before and I don't mind adding vgchange to rc.local I just don't want to break later down the road.

--Forced

---

