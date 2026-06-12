---
title: "SATA RAID and liveCD"
date: 2009-02-17
forum: Server Platforms
---

### Post by dimothy10 on 2009-02-17
Dear all,

Have not used linux for a while but now have a need to use it to recover data off of my XP hard disk to a network share so I can reload XP again.  Have been trying to use the liveCD of ubuntu so as to minimise the impact to my XP setup.

My hard disk are in raid 0 on an nvraid SATA built in to my motherboard.  The tricky part i think is that there is no native support on the mobo, i have to use the F6 key during install of XP or slipstream in drivers prior.  

Now fdisk -l does show them as being there but i cant seem to access them.  Any help would be greatly appreciated.  Below is the fdisk -l output.

regards

tim

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01dd01dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801   42  SFS
/dev/sda2           48642       48642        8032+  42  SFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000101

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by dimothy10 on 2009-02-17
So it turns out i need dmraid.  have installed that from the repository.  it can see my nvidia raid but gives me errors.  here is the repsonse from sudo dmraid -r

ubuntu@ubuntu:/dev/mapper$ sudo dmraid -r
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: nvidia, "nvidia_adfihbce", stripe, ok, 390721966 sectors, data@ 0
/dev/sda: nvidia, "nvidia_adfihbce", stripe, ok, 390721966 sectors, data@ 0
ubuntu@ubuntu:/dev/mapper$ 


tried this command earlier before my dmraid excursion but to no avail:

 sudo mount -t ntfs-3g /dev/sda1 /mnt/disk
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


any help would be greatly appreciated.

---

### Post by handy on 2009-02-18
You will attract more attention over in the Server Platforms sub-forum.

I have asked a mod to move your thread.

---

### Post by bapoumba on 2009-02-18
So moved, thanks :)

---

### Post by fjgaude on 2009-02-18
From what little I know of **dmraid** and raid0 all you have to do is mount the array:

```
sudo -t ntfs /dev/mapper/nvidia_adfihbce /mnt/disk
```

That assumes you have the mountpoint created as /mnt/disk.

You might have to do something like this at first:

```
sudo dmraid -ay
```

I think that makes Ubuntu aware of the fakeRAID. Would be a good idea to read the **man** pages for dmraid, eh?

---

