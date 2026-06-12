---
title: "a raiding party"
date: 2016-08-28
forum: Server Platforms
---

### Post by maclenin on 2016-08-28
Just a few quick notes on software (mdadm) raid management.

I am learning how to create/rebuild raid1 arrays on (clean installs of) xubuntu (LTS) and have assembled this reference to faciliate.

Hope this helps others and invites critique.

A. DRIVES

250 gb sda system non-raid disk 
1000 gb sdb data-only raid disk 
1000 gb sdc data-only raid disk  

B. CONFIGURE

1. Install xubuntu 16.04.1 on sda

2. Install (aptitude and) mdadm and initramfs-tools
```
sudo apt-get install aptitude
sudo aptitude install mdadm
sudo aptitude install initramfs-tools
```
3. List disks, devices and partitions
```
sudo fdisk -l
```
4. Remove raid array metadata
```
sudo mdadm --zero-superblock /dev/sdb
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sdc
sudo mdadm --zero-superblock /dev/sdc1
```
5. Create partition table on disk sdb
```
sudo fdisk /dev/sdb
```
6. Select d to delete existing partition

7. Select n to create new partition

8. Option p to create primary partition

9. Select 1 as partiton number

10. Accept defaults to create partition using entire disk 

11. Select p to view current partition table

12. Select t and then fd (linux raid autodetect)

13. Select p to view current partition table

14. Select w to write choices to disk

15. Create partition table on disk sdc
```
sudo fdisk /dev/sdc
```
16. Return to steps 6. - 14.

17. Confirm raid device partitions are identical
```
sudo fdisk -l | sed -n '/fd/'p
```

18. Create raid level 1 array comprising 2 devices
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```
19. Watch raid array synchronize with 1 second refresh interval
```
watch -n 1 cat /proc/mdstat
```
20. Add file system to raid array (as it synchronizes)
```
sudo mkfs.ext4 /dev/md0
```
21. Mount raid array
```
sudo mkdir /shared
sudo mount /dev/md0 /shared
```
22. Find [correct raid array UUID]("https://ubuntuforums.org/showthread.php?t=2278809&p=13289519#post13289519") for use in fstab
```
sudo blkid
```
23. Open fstab
```
sudo nano /etc/fstab
```
24. Add raid array details to fstab
```
# /dev/md0
UUID=1-2-3-4-5 /shared ext4 defaults 0 0
```
25. Create mdadm.conf
```
sudo -i
/usr/share/mdadm/mkconf > /etc/mdadm/mdadm.conf
exit
```
26. Modify [ARRAY in mdadm.conf]("http://unix.stackexchange.com/questions/111479/linux-md-raid-dev-md0-vs-dev-md-0") by removing name field to address [md127 issue]("https://ubuntuforums.org/showthread.php?t=1764861&page=2&p=11452217#post11452217")
```
sudo nano /etc/mdadm/mdadm.conf
ARRAY /dev/md0  metadata=1.2 UUID=1:2:3:4
```
27. Update the [initial RAM filesystem]("https://kernel-handbook.alioth.debian.org/ch-initramfs.html")
```
sudo update-initramfs -u
```
28. Reboot system
```
sudo shutdown -r +0
```
29. Display [state of raid array]("https://raid.wiki.kernel.org/index.php/Mdstat") 
```
cat /proc/mdstat
```
30. Healthy state of synchronized raid array
```
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      976630464 blocks super 1.2 [2/2] [UU]
      bitmap: 0/8 pages [0KB], 65536KB chunk
```

C. STATUS

31. Display state of raid array 
```
cat /proc/mdstat
```
32. Query state of raid array components
```
sudo mdadm --query /dev/md0
sudo mdadm --query /dev/sdb1
sudo mdadm --query /dev/sdc1
```
33. Detail state of raid array
```
sudo mdadm --detail /dev/md0
```
34. Examine state of raid array devices
```
sudo mdadm --examine /dev/sdb1
sudo mdadm --examine /dev/sdc1
```

D. FAIL

35. Set device in raid array as faulty
```
sudo mdadm /dev/md0 --fail /dev/sdb1
```
36. Remove faulty device from raid array
```
sudo mdadm /dev/md0 --remove /dev/sdb1
```
37. Configure replacement disk using step 3. - 14.

38. Add new device to raid array
```
sudo mdadm /dev/md0 --add /dev/sdb1
```
39. Watch raid array synchronize with 1 second refresh interval
```
watch -n 1 cat /proc/mdstat
```

E. REPLACE

40. Add spare device to raid array
```
sudo mdadm /dev/md0 --add /dev/sdd1
```
41. Replace device in raid array with spare
```
sudo mdadm /dev/md0 --replace /dev/sdb1
```

F. TERMINATE

42. Unmount raid array
```
sudo umount /dev/md0
```
43. Stop raid array
```
sudo mdadm --stop /dev/md0
```
44. Remove raid array metadata
```
sudo mdadm --zero-superblock /dev/sdb
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sdc
sudo mdadm --zero-superblock /dev/sdc1
```
45. Remove mdadm.conf
```
sudo rm /etc/mdadm/mdadm.conf
```
46. Comment out raid array entry in fstab
```
sudo nano /etc/fstab
# /dev/md0
# UUID=1-2-3-4-5 /shared ext4 defaults 0 0
```
47. Goto 3. to configure a new raid array!

G. MISCELLANEOUS

48. Restart stopped raid array
```
sudo mdadm --assemble /dev/md0
```
49. Re-add removed device to raid array
```
sudo mdadm /dev/md0 --add /dev/sdb1
```

The steps I list here have been distilled from numerous sources (with thanks)...

[replace]("https://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array")
[manage]("http://www.tecmint.com/understanding-raid-setup-in-linux/")
[md127]("http://unix.stackexchange.com/questions/111479/linux-md-raid-dev-md0-vs-dev-md-0")
[md127]("https://ubuntuforums.org/showthread.php?t=2265120")
[md127]("https://ubuntuforums.org/showthread.php?t=1764861") 
[rescue]("https://ubuntuforums.org/showthread.php?t=2278809") 
[terminate]("https://ubuntuforums.org/showthread.php?t=1646982&p=10247465#post10247465")
[configure]("https://www.digitalocean.com/community/tutorial_series/how-to-configure-raid-arrays-on-ubuntu-16-04")

...including:

```
**man mdadm**
```

---

