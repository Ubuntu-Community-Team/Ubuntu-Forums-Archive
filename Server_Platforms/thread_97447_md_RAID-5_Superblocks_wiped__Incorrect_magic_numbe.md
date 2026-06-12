---
title: "md RAID-5 Superblocks wiped?  Incorrect magic number"
date: 2005-12-01
forum: Server Platforms
---

### Post by tarkus on 2005-12-01
I was running my machine normally for a while.  I have three disks in a RAID-5 (hdg2, hdf1, hde1) which is /dev/md0.  Then - kiss of death in a syslog:
> Nov 30 21:50:33 localhost kernel: [ 2115.626108] hdf: dma_intr: status=0x51 { Dr iveReady SeekComplete Error }
Nov 30 21:50:33 localhost kernel: [ 2115.626113] hdf: dma_intr: error=0x84 { Dri veStatusError BadCRC }
Nov 30 21:50:33 localhost kernel: [ 2115.626116] ide: failed opcode was: unknown
Nov 30 21:50:33 localhost kernel: [ 2115.670490] hdf: dma_intr: status=0x51 { Dr iveReady SeekComplete Error }
Nov 30 21:50:33 localhost kernel: [ 2115.670496] hdf: dma_intr: error=0x84 { Dri veStatusError BadCRC }
Nov 30 21:50:33 localhost kernel: [ 2115.670499] ide: failed opcode was: unknown
Nov 30 21:50:33 localhost kernel: [ 2115.692685] hdf: dma_intr: status=0x51 { Dr iveReady SeekComplete E
rror }
Nov 30 21:50:33 localhost kernel: [ 2115.692690] hdf: dma_intr: error=0x84 { Dri veStatusError BadCRC }
Nov 30 21:50:33 localhost kernel: [ 2115.692693] ide: failed opcode was: unknown
Nov 30 21:50:34 localhost kernel: [ 2115.717345] ide2: reset: success
Nov 30 21:55:43 localhost kernel: [ 2277.094066] warning: many lost ticks.
Nov 30 21:55:43 localhost kernel: [ 2277.094068] Your time source seems to be in stable or some driver is hogging interupts

I rebooted to hopefully calm the controller, but now I can't activate my RAID array!
> steven@godzilla:~$ sudo mdadm -A -v /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: /dev/hdg2 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/hdg1 is not one of /dev/hdf1,/dev/hdg2,/dev/hde1
mdadm: /dev/hdg is not one of /dev/hdf1,/dev/hdg2,/dev/hde1
mdadm: /dev/hdf2 is not one of /dev/hdf1,/dev/hdg2,/dev/hde1
mdadm: no RAID superblock on /dev/hdf1
mdadm: /dev/hdf1 has wrong uuid.
mdadm: /dev/hdf is not one of /dev/hdf1,/dev/hdg2,/dev/hde1
mdadm: /dev/hde3 is not one of /dev/hdf1,/dev/hdg2,/dev/hde1
mdadm: /dev/hde2 is not one of /dev/hdf1,/dev/hdg2,/dev/hde1
mdadm: no RAID superblock on /dev/hde1
mdadm: /dev/hde1 has wrong uuid.
--snip, lots of searching through drives that don't matter--
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: added /dev/hdg2 to /dev/md0 as 1
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

I try to examine the drives:
> steven@godzilla:~$ mdadm -E -f -v /dev/hdf1
mdadm: No super block found on /dev/hdf1 (Expected magic a92b4efc, got a92b4ffc)
steven@godzilla:~$ mdadm -E -f -v /dev/hde1
mdadm: No super block found on /dev/hde1 (Expected magic a92b4efc, got a92b4ffc)

The magic looks _almost_ right, just that a bit got twiddled.  But why would the same corruption happen to two different disks?  Granted, they are on the same bus, but this looks very strange.

Any bright ideas?  I've tried various combinations of the mdadm utility, including force, with no results.  I'd prefer not to break anything... 

Can I twiddle the single incorrect bit to make the magic number right?  Is this unlikely to help?

I used a hex editor to examine the last few megabytes of disk (docs say that the superblock is in the last 128kB-64kB) but didn't find either the correct magic number or the incorrect magic number in it.  What gives?

Thanks for any help,
Steven

---

### Post by tarkus on 2005-12-01
Any ideas?  Could you at least point me to where the magic number is?  I'm quite lost here...

---

### Post by tarkus on 2005-12-03
Well, I fixed it, so I'll post my solution for posterity.  What you have to do is with a steady hand (and good backups!) recreate the RAID array _exactly_ the same way you did at the start, except replace the trashed drive with 'missing'
so I did a
mdadm --create -l 5 -n 3 /dev/md0 missing /dev/hdg2 /dev/hde1
and the data appeared!  If everything's there, hotadd the missing drive and it will resync.  Off you go!

---

### Post by poptones on 2005-12-03
duh... never mind (bad magic number...)

---

