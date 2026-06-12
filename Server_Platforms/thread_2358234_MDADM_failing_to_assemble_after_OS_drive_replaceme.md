---
title: "MDADM failing to assemble after OS drive replacement"
date: 2017-04-11
forum: Server Platforms
---

### Post by gimpacause on 2017-04-11
Hi all i'm running Ubuntu 14.04 LTS system has been running fine for 2 years, recently my / drive failed and i replaced it, but i cannot get my 15 disk RAID6 back online the following is what i have found on each disk

```


/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 836d1c10:92ddcbef:642269f6:970dcb7f


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : fe40b9dc - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)


/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 597da2de:23434722:4ffb76e9:4c1fce45


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : b85319e4 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 2117fd42:2694297f:3a425ede:845a5fd8


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 10886d4 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 9d4a3195:e7d1bbf2:a10318e1:0ab2eaf7


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : e91410ff - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 64301407:2016a90e:4da086e3:3f9afe7c


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : fe66bfdf - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 4
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : fa32d486:b6872526:07e12229:2dda4f2b


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 8990b4b4 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : f7013c7f:55b301bd:c924e51f:7a22b734


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 18fe3b61 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 6
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdh:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : dfa2dc6d:77b1e996:b0e99e47:bf74858f


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 640ef198 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 7
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)








/dev/sdi:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 7bd00a9f:df1101d0:93abfa1e:816e6ba5


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : bb963b42 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 8
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdj:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 0702a85a:4ad92e13:abbfd918:07ec3160


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 6f06c5d7 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 9
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdk:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 7737fa56:fdceb6ee:47a94f30:f19cd0a1


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 9ff58b82 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 10
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdl:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 18fdb6b4:0e770104:6f03b641:888b38f0


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 72cb41f4 - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 11
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdm:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : b9fcdfe2:e629398b:1999e79f:8cc5b6ee


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 84dbc41d - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 12
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdn:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : cd69f325:a5bb013f:eedebcb8:b40dbc9b


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 419250ed - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 13
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)

/dev/sdo:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Tue Dec 30 19:46:32 2014
     Raid Level : raid6
   Raid Devices : 15


 Avail Dev Size : 11720783024 (5588.90 GiB 6001.04 GB)
     Array Size : 76185088512 (72655.76 GiB 78013.53 GB)
  Used Dev Size : 11720782848 (5588.90 GiB 6001.04 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 6da0452b:b2d02fd7:9827eb58:1c446d33


Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Apr 11 13:30:43 2017
       Checksum : 16f21bad - correct
         Events : 629280


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 14
   Array State : AAAAAAAAAAAAAAA ('A' == active, '.' == missing)


```











cat /proc/mdstat shows

```


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdm[12] sdn[13] sdl[11] sdk[10] sdi[8] sdj[9] sdh[7] sdf[5] sdg[6]
      52743523608 blocks super 1.2


unused devices: <none>




```

any ideas how i can re-assemble this array without losing data, event counts are all the same for all disks, when i noticed my boot drive had failed i shutdown the server, waited for a new disk and re-installed Ubuntu, upon installing all required packages the system would drop straight to a busybox/initramfs prompt, rebooted into recovery mode now to try and sort this out


Many thanks

---

### Post by darkod on 2017-04-11
To start with, post the output of:
```
sudo blkid
cat /etc/mdadm/mdadm.conf | grep ARRAY
```

I didn't understand, after reinstalling the OS how did it know which array to assemble? Did it ask you to import an array, or you tried to add it to the new OS?

---

### Post by gimpacause on 2017-04-11
i have run

```


  mdadm --stop /dev/md0
  mdadm --assemble --scan


```


when i first had issues with my main os drive i tried to re install ubuntu, when i did this the first time it showed the array during the installer, when i replaced the drive after a second crash, i did not see the array during the installation process.



in answer to your query here are the results

sudo blkid

```


ben@ubuntu:~$ sudo blkid
[sudo] password for ben:
/dev/sda: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="836d1c10-92dd-cb                                                                                        ef-6422-69f6970dcb7f" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdb: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="597da2de-2343-47                                                                                        22-4ffb-76e94c1fce45" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdc: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="2117fd42-2694-29                                                                                        7f-3a42-5ede845a5fd8" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdd: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="9d4a3195-e7d1-bb                                                                                        f2-a103-18e10ab2eaf7" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sde: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="64301407-2016-a9                                                                                        0e-4da0-86e33f9afe7c" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdg: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="f7013c7f-55b3-01                                                                                        bd-c924-e51f7a22b734" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdf: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="fa32d486-b687-25                                                                                        26-07e1-22292dda4f2b" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdh: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="dfa2dc6d-77b1-e9                                                                                        96-b0e9-9e47bf74858f" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdj: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="0702a85a-4ad9-2e                                                                                        13-abbf-d91807ec3160" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdi: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="7bd00a9f-df11-01                                                                                        d0-93ab-fa1e816e6ba5" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdk: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="7737fa56-fdce-b6                                                                                        ee-47a9-4f30f19cd0a1" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdl: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="18fdb6b4-0e77-01                                                                                        04-6f03-b641888b38f0" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdn: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="cd69f325-a5bb-01                                                                                        3f-eede-bcb8b40dbc9b" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdm: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="b9fcdfe2-e629-39                                                                                        8b-1999-e79f8cc5b6ee" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdo: UUID="0a62c2c5-6ca3-0a41-e6f1-32f911bef5db" UUID_SUB="6da0452b-b2d0-2f                                                                                        d7-9827-eb581c446d33" LABEL="ubuntu:0" TYPE="linux_raid_member"
/dev/sdp1: UUID="5D49-CFEB" TYPE="vfat"
/dev/sdp2: UUID="0efbddcf-a15d-4501-bbfa-aeb3430df4a8" TYPE="ext4"
/dev/sdp3: UUID="8987726f-fd31-4965-9e59-8634ec74ff2e" TYPE="swap"


```



cat /etc/mdadm/mdadm.conf | grep ARRAY

```



ben@ubuntu:~$ cat /etc/mdadm/mdadm.conf | grep ARRAY
ben@ubuntu:~$


```

nothing comes up

cat /etc/mdadm/mdadm.conf | grep ARRAY




Thanks, Ben

---

### Post by darkod on 2017-04-11
For future reference, don't use the disk identifier in mdadm. It can work, but better option is to use partitions even if the partition spans the whole disk. For example /dev/sda1 instead of /dev/sda.

But now that you already have the array and data on it, you can't change that. Just remember that you used sda instead of sda1.

If you made a new install, why doesn't it boot now? Any error message shows up when trying to boot it?

Apart the situation with the mdadm array, I would focus first on getting the server to boot normally. After that adding the array to mdadm.conf is easy.

But anything you do in recovery or live mode will probably not be persistent. That's why I would focus on getting normal boot working first. This should not be related to the array, you should be able to boot even if the array is not there, or not assembled when the OS disk is separate from mdadm.

---

### Post by gimpacause on 2017-04-11
thanks Darko, I'm a Linux noob, should i start a new thread or can we continue here, thanks

---

### Post by darkod on 2017-04-11
You can continue in this thread, no problem about that...

---

### Post by gimpacause on 2017-04-11
Ok thank you, what logs do I need to check to see what happening at boot, thanks

---

### Post by darkod on 2017-04-11
I just noticed now you say in your first post you were running 14.04. Did you install 16.04 now or again 14.04?

in the initramfs prompt, try typing 'exit' and press enter. Write down any error messages it might show, you will need to research them later. Post them here too...

---

### Post by gimpacause on 2017-04-11
Ok thanks ill give that a try are those errors logged at all as I can say in now and get logs
I'm running 14.04 LTS

---

### Post by darkod on 2017-04-11
Not sure... If the system is not running, it might not have started logging except any messages in the initramfs prompt.

When you say recovery mode, how do you exactly boot it? Using the Advanced options and the root shell?

---

### Post by gimpacause on 2017-04-11
Yes, advanced recovery > root shell then started ssh and went from there

---

### Post by darkod on 2017-04-11
I'm not sure if anything is logged when you start the server like that. You can try checking in /var/log/syslog and /var/log/dmesg or something similar...

Try that exit command, it looks like people are using it in initramfs prompt from what I found online.

---

### Post by gimpacause on 2017-04-11
Hi Darkod

I believe it as at the following stage it drops to initramfs

[IMG]https://ibb.co/gnZ3BQ[/IMG]

now checking the UUID's in my system

[IMG]https://ibb.co/gnZ3BQ[/IMG]

it's showing /dev/sdp2

[IMG]https://ibb.co/kq0My5[/IMG]

which is my new 120 gig SSD i purchased to replaced the old failed drive, so i'm going to assume i screwed something up during install. should i just nuke the install go from there as there is nothing on the drive

---

### Post by darkod on 2017-04-11
I can't see the images. You can attach them to the post, not insert them inside. Also if you are working in ssh session it might be better to copy-paste text instead of images.

---

### Post by gimpacause on 2017-04-11
[ATTACH=CONFIG]274520[/ATTACH][ATTACH=CONFIG]274521[/ATTACH]

ok for some weird reason i cant post the third pic i had but this is what it said

```
 ALERT! /dev/disk/by-UUID/0efbddcf-a15d-4501-bbfa-aeb3430df4a8 does not exist. Dropping to shell! 
```

now looking at the list of uuid's in the second pic it looks like /dev/sdp/2 

which is one of the partitions of my 120 gig "new" ssd which i installed ubuntu onto, so i'm thinking something may have gone screwy on this new install


i couldn't work via ssh because this is what was happening at boot, if i didn't go into recovery mode i would just get a blinking curser/black screen now (wild guess, install is shot/corrupt) i know why

thank your for the help so far, i will be back online later on tonight, as i have to go to work

---

### Post by darkod on 2017-04-11
Yeah, looks like an issue with the install. It might be faster to reinstall again, you might as well use the latest 16.04 LTS this time. Because this install is new and clean and you still don't have any complex configration in it, it might be faster to reinstall again instead of spending much time troubleshooting it.

If you want to, try googling for that "does not exist" message. I think that by-UUID check can be disabled. Because the partition and the UUID is clearly there, you only need to disable this check that can't find it for what ever reason. That would be a way to troubleshoot this if you don't want to reinstall.

---

### Post by gimpacause on 2017-04-17
Hi Darkod, 16.04 lts installed waiting for mdadm resync (started automatically) it found all devices on this install, will let you know how it goes, thank you for the help thus far

---

### Post by gimpacause on 2017-04-18
Hi Darkod all working now, rebooted server several times, mdadm mounting at boot, no data loss, i suspect my install issues was due to faulty image/usb stick, thank you for all your help

---

