---
title: "Help moving /home folder to RAID array and Auto Mounting via Fstab"
date: 2013-02-24
forum: Server Platforms
---

### Post by grunge09 on 2013-02-24
I recently setup a 12.10 core server on a 8 GB USB Flash Drive with a RAID 5 3x2tb array.  

I believe Ubuntu defaults to install /home on root drive (in my case the flash drive).

I would like to move it to the new RAID5 drive dubbed "/storage" that I have added to /etc/fstab and checked after boot using DF -H /storage and it works.  and I can access that drive and create files/folders.

I would like to know if its possible to add a line to /etc/fstab to automount this at boot and if so what other changed need to be made to ubuntu server to make it look at the new location?  

Thanks in advance.

---

### Post by darkod on 2013-02-24
Unfortunately I don't think it's easily done. The main problem is that for separate /home you will need a separate partition (or a md device).

You are using mdadm software raid, right?

If you had space on the hdds for separate partition/md device, making it a separate /home partition is very easy. But repartitioning now might be risky and depending on how much data you already have on the storage it might not be worth it.

If you installed the server with LVM it would have been much easier for example.

Why do you want to have separate /home partition exactly? Maybe there is another solution you can implement.

---

### Post by grunge09 on 2013-02-25
Yes I am using Mdadm RAID.   The Array is newly created & formated EXT4 so there is no data on it yet.  

I just wanted home directories on the RAID5 drive.  Did not want it on the USB Flash Drive that I use to boot the Server.

8 GB USB Flash Drive boots Core Server, and 3x2tb drives in RAID5 (I have another 2tb drive full of data to copy over to the array (once I get the samba shares working).

---

### Post by darkod on 2013-02-25
In that case, if the array is still empty, you can do this:
1. Delete the md device. Delete the partitions on the big disks by writing new bpank partition tables.
2. On each disk create identical small partition for raid5 /home, and big partition for raid5 /storage.
3. Make two new md devices, for /home and /storage.
4. Copy the content of the current /home to the new /home md device, keeping ownership and permissions.
5. In fstab, just like you did for /storage earlier, make two entries for the new /storage and /home.

To copy the current /home by keeping permissions you can mount the new md device to a temp mount point, and for example do:
```
cd /home
sudo cp -ax * /tempmountpoint
```

That will copy all. Make another copy to external device too, just in case. After that I think you will need to boot into live mode and remove the home folder inside / so that it doesn't clash with the newly created /home. After that reboot and the new /home should be mounted by fstab.

That's it.

---

