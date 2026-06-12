---
title: "New Ubuntu Terminal Install -- Where are my drives?"
date: 2010-06-02
forum: Server Platforms
---

### Post by Ubapptu on 2010-06-02
Hi All,

This is the first time I have installed an Ubuntu Server.  I used the 10.04 LTS iso image to install.  During the install process I saw all of my drives 3 individual and 1 raid.  Now that I am in ubuntu server, how do I 

1. Get ubuntu to recognize the drives
2. Mount/Partition them.
3. Point Directories to them.

Here is what df looks like...

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubapptu-root
                      178G  1.3G  168G   1% /
none                  998M  264K  998M   1% /dev
none                 1004M  4.0K 1004M   1% /dev/shm
none                 1004M  296K 1004M   1% /var/run
none                 1004M     0 1004M   0% /var/lock
none                 1004M     0 1004M   0% /lib/init/rw
/dev/sda1             228M   19M  197M   9% /boot
/home/custserv/.Private
                      178G  1.3G  168G   1% /home/custserv

Thank you for your help.

---

### Post by Bachstelze on 2010-06-02
> **Ubapptu said:**
> 
1. Get ubuntu to recognize the drives

If they were recognized during installation, they will probably be recognized on the installed system as well. You have nothing particular to do.

> 2. Mount/Partition them.

Mounting is done using the mount command, like:

```
sudo mount /dev/something /somewhere
```

Partitioning is generally done with fdisk or maybe parted if you have very special needs.

> 3. Point Directories to them.

:confused:

---

### Post by Ubapptu on 2010-06-02
Thank you for you spedy reply.  However, I am just not connecting the wires.  If I use df -h, shouldn't that show me all the drives in my server?  If these are they, they don't seem to be part of the file system.  I was expecting them to look more like /dev/sda1 /dev/sda2 etc or whatever...  Again here is the df.

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubapptu-root
                      178G  1.3G  168G   1% /
none                  998M  264K  998M   1% /dev
none                 1004M  4.0K 1004M   1% /dev/shm
none                 1004M  296K 1004M   1% /var/run
none                 1004M     0 1004M   0% /var/lock
none                 1004M     0 1004M   0% /lib/init/rw
/dev/sda1             228M   19M  197M   9% /boot
/home/custserv/.Private
                      178G  1.3G  168G   1% /home/custserv

---

### Post by Bachstelze on 2010-06-02
> **Ubapptu said:**
> If I use df -h, shouldn't that show me all the drives in my server?

No, it shows all mounted filesystems. To see all your drives, do

```
sudo fdisk -l
```

---

### Post by Ubapptu on 2010-06-02
You are awesome, thanks, 




Disk /dev/sdd: 500.0 GB, 499999834112 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63       80324       40131   de  Dell Utility
/dev/sdd2           81920   976560127   488239104    7  HPFS/NTFS

So this is my raid.
Would I then

fdisk /dev/sdd2 

and then t 83

and then mount /dev/sdd2/var1

is that what you mean by mount /dev/something somewhere

---

### Post by Bachstelze on 2010-06-02
Well, what do you want to do now? Format the drive in a Linux filesystem and mount it? Then you would do something like

```
sudo fdisk /dev/sdd
```

Then t (change type), 2 (second partition), 83 (Linux), w (write changes).

Then format it for example as ext4 (this will erase all data!):

```
sudo mkfs.ext4 /dev/sdd2
```

Then mount it

```
]sudo mount /dev/sdd2 /var1
```

if that's where you want to mount it.

---

### Post by Ubapptu on 2010-06-02
Awesome.  Thank you so much...  It appears to be working.  Is there someplace I can find tutorials on admin stuff like this?  I wasn't really sure what to google.

---

### Post by Bachstelze on 2010-06-02
> **Ubapptu said:**
> Awesome.  Thank you so much...  It appears to be working.  Is there someplace I can find tutorials on admin stuff like this?  I wasn't really sure what to google.

A Google search for "linux partition command line" gives [this guide]("http://www.faqs.org/docs/Linux-mini/Partition.html") as a first result. ;)

---

### Post by Ubapptu on 2010-06-02
Again, thank you.  Everything is now rockin!

---

