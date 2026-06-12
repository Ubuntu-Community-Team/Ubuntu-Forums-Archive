---
title: "Permisssion denied writing to new ext4 RAID5 array"
date: 2012-08-18
forum: Server Platforms
---

### Post by apokkalyps on 2012-08-18
I am building a raid5 array and cannot get it to be writable.

I created it from 4 drives using mdadm. 
> sudo mdadm --create --raid-devices=4 --level=raid5 -N vault /dev/md0 /dev/sda /dev/sdb /dev/sdc /dev/sdd

Then I put ext4 on md0
> sudo mkfs.ext4 /dev/md0

From here I have not been able to write to the file system.  At first I tried doing a manual mount to /media/vault and now I have actually set it up in fstab to mount automatically, and still get permission denied trying to write to the mount, even with sudo.  I have no idea what could be wrong at this point.


Possibly relevant stuff:

> 
admin@fileserver:/media/vault$ sudo df -Th |grep md0
/dev/md0       ext4      5.5T   42G  5.2T   1% /media/vault

> admin@fileserver:/media/vault$ sudo blkid |grep md0
/dev/md0: UUID="9db5199d-2703-4db7-b10c-9a6164fb83a6" TYPE="ext4" 

> admin@fileserver:/media/vault$ cat /etc/fstab |grep 9db51
UUID=9db5199d-2703-4db7-b10c-9a6164fb83a6 /media/vault          ext4    defaults        0        2

> admin@fileserver:/media/vault$ cat /etc/mdadm/mdadm.conf |grep md0
ARRAY /dev/md0 UUID=8bc78af0:d9a981e3:73549f21:2f76cd24

> admin@fileserver:/media/vault$ dmesg | grep md0
[    2.695501] md/raid:md0: device sdb operational as raid disk 0
[    2.695503] md/raid:md0: device sde operational as raid disk 3
[    2.695504] md/raid:md0: device sdd operational as raid disk 2
[    2.695505] md/raid:md0: device sdc operational as raid disk 1
[    2.695744] md/raid:md0: allocated 4280kB
[    2.695819] md/raid:md0: raid level 5 active with 4 out of 4 devices, algorithm 2
[    2.695841] md0: detected capacity change from 0 to 6000792305664
[    2.733635]  md0: unknown partition table
[    7.024000] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)

> 
admin@fileserver:/media/vault$ mount |grep md0
/dev/md0 on /media/vault type ext4 (rw)

> admin@fileserver:/media/vault$ echo test > tester.txt
bash: tester.txt: Permission denied

admin@fileserver:/media/vault$ sudo echo test > tester.txt
bash: tester.txt: Permission denied

Thanks for any suggestions anyone has, and if theres any other relevant data to gather just let me know.

---

### Post by darkod on 2012-08-18
How did you create the directory /media/vault?

You can try setting read/write permissions to all first, to rule out permissions problems. Later you can change them if you want different settings. You can set RW to all with:
sudo chmod a+rw /media/vault

---

### Post by apokkalyps on 2012-08-18
Lol!  That did it!  Thanks.  I knew it had to be something silly.  I think I created the folder after sudo su?  Is that different permissions than sudo?  I figured no matter what, if it was a chmod type thing, sudo could do what it wanted.  

Anyway thanks!

---

