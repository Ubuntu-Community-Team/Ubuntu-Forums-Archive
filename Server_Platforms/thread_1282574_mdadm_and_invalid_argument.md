---
title: "mdadm and invalid argument"
date: 2009-10-04
forum: Server Platforms
---

### Post by Cl0cKw0rK on 2009-10-04
I am trying to Assemble my raid using mdadm, in ubuntu-server.

my command is sudo mdadm -A /dev/md0 -c /etc/mdadm.conf
gives me the errors

cannot add /dev/sdd1 to /dev/md0: invalid argument
cannot add /dev/sde1 to /dev/md0: invalid argument
cannot add /dev/sdf1 to /dev/md0: invalid argument

I also get an error saying that the raid cannot be started with 1 drive, which is odd because its a Raid5 with 5 drives, and its only giving me errors about 3.

Google is failing me, and so i plead your help.

Thanks,
Clockwork.

---

### Post by fjgaude on 2009-10-04
What I would do is rename or delete your **/etc/mdadm/mdadm.conf** file, re-boot, and then issue this command:

```
sudo mdadm --assemble --scan
```

That will have the effect of creating a new mdadm.conf file and you should be good to go. Let us know how you do. Thanks!

---

### Post by laluz on 2009-10-04
have you tried to say 
mdadm --assemble /dev/md0
what errors will you get?

---

### Post by fjgaude on 2009-10-04
The command I gave lets mdadm decide from the unique UUID of the several drives what the mdadm.conf file should be. By using /md0 in the command it uses the old conf file which may no longer be valid.

You can use this command to get a new file:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Hope this is of some help.

---

### Post by Cl0cKw0rK on 2009-10-05
Alright, writing a new config file didn't work. I have confirmed that all of the drivers are indeed found in ubuntu. Any othrr suggestions?

---

### Post by Cl0cKw0rK on 2009-10-05
bump.

---

### Post by fjgaude on 2009-10-05
Okay, try seeing if the drives are all connected:

```
sudo fdisk -l
```

When did the array stop auto assembling? What version of the OS are you using? Is your conf file in /etc/mdadm or in /etc?

---

### Post by Cl0cKw0rK on 2009-10-05
Yes, all of the drives are attached. they are in fdisk, as well as /dev. they also appear in /proc/partitions.

---

### Post by laluz on 2009-10-05
Do you get the same errors as in your first post when you try to assemble your array with the new config?

---

### Post by Cl0cKw0rK on 2009-10-05
Yes, same error

---

### Post by fjgaude on 2009-10-05
Who version of the OS are you using? Is your mdadm.conf file in /etc or in /etc/mdadm?

---

### Post by Cl0cKw0rK on 2009-10-05
im running ubuntu-server 8.10.Its in /etc

---

### Post by fjgaude on 2009-10-05
I see says the blind man! You need to put the newly generated **mdadm.conf** that went into **/etc/mdadm** into **/etc**. That may fix your issues.

Hmmm... 8.10 is not that old... wonder why the conf file is in /etc and not in /etc/mdadm?

---

### Post by Cl0cKw0rK on 2009-10-05
Sorry, but thats not the problem. the newly generated ones i tell to overwrite /etc/mdadm.conf. also i get the same results when running 
mdadm -A /dev/md0 /dev/sda1.../dev/sdf1

---

### Post by fjgaude on 2009-10-05
Okay, what does this show:

```
sudo mdadm -E /dev/sda1
```

Check to see if the UUID there is the same as the one in your **mdadm.conf** file. And you should see the status of the array.

---

### Post by Cl0cKw0rK on 2009-10-06
This is the -E result from the only disk that cannot be read.


```
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 8ed38d0a:f74e0c27:e368bf24:bd0fce41 (local to host ubuntu)
  Creation Time : Wed Jul 22 20:59:14 2009
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sun Oct  4 05:50:23 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 9f432bb8 - expected 9f432b88
         Events : 682292

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       17        4      active sync   /dev/sdb1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       81        2      active sync
   3     3       0        0        3      faulty removed
   4     4       8       17        4      active sync   /dev/sdb1

```

---

### Post by Cl0cKw0rK on 2009-10-06
Alright.

New info

Managed to start the raid degraded with 4 drives (of 5)
I try to mount it, and im getting an error.
```

sudo mount -t ext2 /dev/md0 drive/ -o ro
EXT2-fs error (device md0): ext2_check_decriptors: Block bitmap for group 26496 not in group (block 32976)!
mount: ...

```

---

### Post by kirbyfan101 on 2009-10-06
agggggggg i need help i downloaded the CD drive at [[COLOR=#444444]http://www.ubuntu.com/getubuntu/download[/COLOR]]("http://www.ubuntu.com/getubuntu/download")
I have WindowsXP I put the .iso file on a disk and loaded it
it didnt work 



PS: i would start my own forum but i don't know how:sad:

---

