---
title: "Help needed with Raid 5 that was working OK"
date: 2016-07-10
forum: Server Platforms
---

### Post by andy451 on 2016-07-10
Hi,

My parents had a Netgear RN 104 that stopped working properly, they messed with some settings, messed it up and gave it to me to fix. It has 4 x 4tb drives in Raid 5. I've used mdadm before to recreate a very simple Raid array, so I connected all 4 drives to my computer, installed mdadm and ran 
sudo mdadm --assemble --scan
It told me that some devices had the same name. So I went into the config file, 2 were named md0 and two were named md1. So I renumbered them md0-m3 and ran that command again. It gave another error and suggested I use --force which I did, and that got it working, a 12tb volume mounted ok. 

I was 20 minutes in to copying photos off when it suddenly stopped, saying I/O error. It could then no longer see the volume. So I restarted, followed all the same steps and now I can't get it to work again. It will show up the 12tb volume but it won't mount it. It says 

Error mounting /dev/md127 at /media/ubuntu/7fffffff:data: Command-line `mount -t "btrfs" -o "uhelper=udisks2,nodev,nosuid" "/dev/md127" "/media/ubuntu/7fffffff:data"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/md127,missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so (udisks-error-quark, 0).

One thing I noticed was that two of the devices have the same UUID. Could this be an issue? I used the --verbose command and it reported some errors to do with the duplicate UUID, saying it can't decide which one to use, and also saying that one device had failed. I tried switching the drives around, leaving one out, but the one it kept reporting as failed would change, it was not unique to a particular physical drive and was not related to the sata cord.

Can anyone help? Would be massively appreciated, there's a million photos on there.

Thanks!

---

### Post by lukeiamyourfather on 2016-07-11
Why are you mounting the array as btrfs? It's unlikely that's what they actually are. Most consumer NAS that use Linux use XFS. This might be helpful.

[http://whenpicsfly.com/category/linux/](http://whenpicsfly.com/category/linux/)

---

### Post by andy451 on 2016-07-11
I didn't set any mount options, it just chose that itself. Maybe I could edit the mount options when the 12tb volume shows up, and set it to XFS. Thanks

---

### Post by darkod on 2016-07-11
With mdadm and UUID the thing is that there is array UUID (which will be identical on all partitions members of the same array) and SUB_UUID which should be unique for each partition.

You shouldn't use force too fast, until you have checked all other options and mdadm details.

Did you try running examine on all partitions? For example if the partitions members of the array are sda2, sdb2, sdc2 and sdd2 you would run:
```
sudo mdadm --examine /dev/sd[abcd]2
```

That should give you the mdadm superblock info for each partition you include in the command. Post it here if you need help understanding it...

---

### Post by andy451 on 2016-07-12
Ok thanks, I ran the examine command and this is what I get

```
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sd[abcd]3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b38d39a3:f740429a:8f75d416:d11f02e3
           Name : 7fffffff:data-0
  Creation Time : Sun Mar  2 15:46:34 2014
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7804333681 (3721.40 GiB 3995.82 GB)
     Array Size : 11706499968 (11164.19 GiB 11987.46 GB)
  Used Dev Size : 7804333312 (3721.40 GiB 3995.82 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=369 sectors
          State : clean
    Device UUID : eb625145:e7a2d6fc:28e6433c:e86ded2d

    Update Time : Mon Jul 11 00:41:52 2016
       Checksum : 1ae80f20 - correct
         Events : 2561

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : ..A. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b38d39a3:f740429a:8f75d416:d11f02e3
           Name : 7fffffff:data-0
  Creation Time : Sun Mar  2 15:46:34 2014
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7804333681 (3721.40 GiB 3995.82 GB)
     Array Size : 11706499968 (11164.19 GiB 11987.46 GB)
  Used Dev Size : 7804333312 (3721.40 GiB 3995.82 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=369 sectors
          State : clean
    Device UUID : 2af771f7:728cd015:7bfae9f0:2a67665b

    Update Time : Fri Jul  1 12:19:48 2016
       Checksum : c81c0f15 - correct
         Events : 2561

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b38d39a3:f740429a:8f75d416:d11f02e3
           Name : 7fffffff:data-0
  Creation Time : Sun Mar  2 15:46:34 2014
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7804333681 (3721.40 GiB 3995.82 GB)
     Array Size : 11706499968 (11164.19 GiB 11987.46 GB)
  Used Dev Size : 7804333312 (3721.40 GiB 3995.82 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=369 sectors
          State : active
    Device UUID : bb5d3faf:023c466e:774ef85b:78a7ca61

    Update Time : Mon Jul 11 00:39:39 2016
       Checksum : 49df4462 - correct
         Events : 2561

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b38d39a3:f740429a:8f75d416:d11f02e3
           Name : 7fffffff:data-0
  Creation Time : Sun Mar  2 15:46:34 2014
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 7804333681 (3721.40 GiB 3995.82 GB)
     Array Size : 11706499968 (11164.19 GiB 11987.46 GB)
  Used Dev Size : 7804333312 (3721.40 GiB 3995.82 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=369 sectors
          State : active
    Device UUID : 28f9311f:4798d463:bd04ef0f:4eb74a6f

    Update Time : Mon Jul 11 00:39:39 2016
       Checksum : 70d7022d - correct
         Events : 2557

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)
```


Also when I look up the config file at /etc/mdadm/mdadm.conf  this is what it says about the existing array

```
# definitions of existing MD arrays
ARRAY /dev/md/0  metadata=1.2 UUID=5fd431c3:363afcd3:71a3f0e8:0ae0c613 name=7fffffff:0
ARRAY /dev/md/1  metadata=1.2 UUID=8fdec04b:f180d4d3:b91d9d4b:7bd879f1 name=0e346a9e:1
ARRAY /dev/md/0  metadata=1.2 UUID=5fd431c3:363afcd3:71a3f0e8:0ae0c613 name=7fffffff:0
ARRAY /dev/md/1  metadata=1.2 UUID=51e9120d:5689bf7c:20b22118:c9a9facc name=7fffffff:1
ARRAY /dev/md/data-0  metadata=1.2 UUID=b38d39a3:f740429a:8f75d416:d11f02e3 name=7fffffff:data-0
```

Many thanks for your help!

---

### Post by darkod on 2016-07-12
Ok, this gives us more info...

First, I would ignore the definitions of previous arrays. If I understood correctly, you are not interested to have the device running again, only to access the big data array for data rescue. You mentioned you removed the disks from the original device... So having said that, previous arrays don't matter, or their names. I would comment out all ARRAY definitions in mdadm.conf before continuing...

Then, if you look at the --examine output, for each device it gives you the Device Role and the Events info, among other things... We can see that the events counter is almost identical, only on sdd3 it has 4 events less than the other three partitions. That is good, there is no huge difference in the counters.

The Device Role gives the order of the partitions, according to mdadm. With the output you posted it turns out to be sdb3, sdc3, sda3, sdd3. I would expect it to be abcd but if mdadm says it is bcad then you should try that first...

Now we come to the interesting part:
1. If there is any array active with these partitions (because of previous attempts), stop it... Check in /proc/mdstat and stop it:
```
cat /proc/mdstat
sudo mdadm --stop /dev/mdX
```

2. Then the first thing to try is to force an assemble:
```
sudo mdadm --assemble --verbose --force /dev/md0 /dev/sdb3 /dev/sdc3 /dev/sda3 /dev/sdd3
```

The --verbose will show you info while trying to assemble it. Note any errors and google them or post them here, they might point you in the right direction.

3. If the above gives no result, the next to try is adding --run into it:
```
sudo mdadm --assemble --verbose --run --force /dev/md0 /dev/sdb3 /dev/sdc3 /dev/sda3 /dev/sdd3
```

If that doesn't work too, there is another option, sort of last resort. I'm not posting it now because it should be rushed into. If you get there we will discuss it. Lets see how the above goes first.

If the array does manage to assemble with any of the above commands, I would try to check the filesystem first before trying to mount it. I use only ext4 so the command to check it is fsck. Depending on your array FS the command to check it might be different. If you get to that point you can probably use google to find info how to check the FS.

Let us know how it goes...

---

### Post by andy451 on 2016-07-13
Ok thanks for that. I commented out the array definitions and ran the first command. It assembled the 12tb volume with no issues (the only thing was it said one device was possibly out of date). I tried to mount it but got the same error as before

Error mounting /dev/md0 at /media/ubuntu/7fffffff:data: Command-line `mount -t "btrfs" -o "uhelper=udisks2,nodev,nosuid" "/dev/md0" "/media/ubuntu/7fffffff:data"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so. (udisks-error-quark, 0)

Does fsck alter anything on the disks, or just check for errors? The error it gives is saying its trying to mount the filesystem as btrfs, but I'm not sure this is correct. Is there any way to check what the file system actually is for sure?

Thanks again

---

### Post by darkod on 2016-07-13
According to the first reply here: [http://askubuntu.com/questions/309047/how-do-i-find-out-what-filesystem-my-partitions-are-using](http://askubuntu.com/questions/309047/how-do-i-find-out-what-filesystem-my-partitions-are-using) try with something like:
```
sudo file -sL /dev/md0
```

If that doesn't work, google is your friend. Search for how to check the filesystem on a partition, Note that many replies assume you have it mounted, that is easy to check. You need a command to check unmounted partition/array.

This has some info, but not how to check the type: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

