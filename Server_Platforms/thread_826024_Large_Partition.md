---
title: "Large Partition"
date: 2008-06-11
forum: Server Platforms
---

### Post by shannondoko on 2008-06-11
Greetings! 

I have a backup server that has raid 0 setup with 8TB of space.
the OS (8.04 server) is installed on a seperate 160GB drive/ 

I've done *some* reading and from what I've read fdisk only supports 2TB and I've seen people say that ext3 isn't a good idea after 2TB also..

I've read that LVM's are a good way to go, but I know almost nothing about LVM's.  If I put an LVM on my array, wouldn't I still have to partition it and put ext3 on it? 

I heard somewhere that someone was able to partition their array using just LVM commands. 

Has anyone else had any experience with this sort of things?

any ideas? 


Thanks in advance!

---

### Post by anindya_m on 2008-06-11
Have a look at this page:
[[COLOR="Red"]http://www.knowplace.org/pages/howtos/linux_large_filesystems_support.php[/COLOR]]("http://www.knowplace.org/pages/howtos/linux_large_filesystems_support.php")
I found it useful.

---

### Post by samosamo on 2008-06-11
That is at LEAST 8 physical drives.  Wouldn't you want RAID5?  You lose 1TB but its just the peace of mind.

---

### Post by shannondoko on 2008-06-12
I have 2 of these servers, they are identical, and backup to eachother in seperate locations. I'm not too concerned about one of them failing. If one fails, then I can just rebuild the array, and copy the data back from the other one. No big deal. 

Also, I've had experience in the past with 2 seperate servers running raid 5, and one of the drives got corrupt, both systems were completely hosed, raid 5 is only good as long as you don't lose power or reboot (one lost power, the other was rebooted not knowing the drive had failed), otherwise you're more than likely screwed anyway (that's my experience anyway) 


I'm following that tutorial on that link from above and I'm getting almost through it  I'm at 

```
lvcreate -n bigvol -l3262837 vg0
```

After I run that  for my system (numbers and name changed accordingly) it just spews out the help message (seemingly twice)

Any ideas as to why it might be doing that? Or how to fix it? 

And thanks so much for the quick replies!

---

### Post by anindya_m on 2008-06-13
I am guessing that the PE (physical extent) entry (-l) option is wrong. Try putting a space between -l and the number. Also check the number. It is possible to enter the size as a % of free space (see the man page for lvcreate). The name "bigvol" (-n option) should not have any funny characters: keep it simple.

---

### Post by shannondoko on 2008-06-13
ok, so it really was spitting out the error twice for some unknown reason so what I did was 2> error 

then I opened the error, and at the top it said 

 /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
 
So I google'd that and found another forum post
[http://ubuntuforums.org/showthread.php?t=608369](http://ubuntuforums.org/showthread.php?t=608369)
and it said to load the modules into the kernel.
 
$ sudo modprobe dm_snapshot
$ sudo modprobe dm_mirror
$ sudo modprobe dm_crypt


I guess it's my fault for being new to this. 

Thanks for helping!

---

### Post by anindya_m on 2008-06-13
You're welcome. Setup your system to load these modules at runtime (/etc/modules or initrd) and everything should be fine.

---

