---
title: "LVM Questions"
date: 2011-08-10
forum: The Cafe
---

### Post by BrokenKingpin on 2011-08-10
I would like to setup 3 hard disks under an LVM disk so I can treat them as one large partition (the OS would be on a 4th disk by itself). Before I do this, I have a few questions:

1) Would Ubuntu see that LVM as a normal partition that I could format and use normally with something like GParted?

2) Where is the LVM information stored? Is it stored only on the 3 drives in the LVM, or does config get stored on the OS drive as well? The reason I ask is if I format the OS drive and setup a new OS, I wouldn't want to have to setup the LVM again. I would prefer that the LVM is self contained on those three disks so I only have to set it up once.

3) Would I have to format my existing drives to add them to the LVM configuration?

Any input on this would be greatly appreciated.

---

### Post by psusi on 2011-08-10
1) No, gparted does not understand LVM, but the disk utility does as of 11.04.

2) The LVM metadata is stored on the disks themselves.  You can boot a livecd and install the lvm2 package and it will recognize the volumes.

3) Yes, you have to format for LVM from the start.

You might want to read [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by medic2000 on 2011-08-10
Also a great explanation and how-to is in the Arch wiki:
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by BrokenKingpin on 2011-08-11
Thanks for the links guys. Are there any graphical tools out there that will aid me in setting up LVM?

---

### Post by medic2000 on 2011-08-11
I don't know any graphical tools but you can cfdisk. It supports LVM and very easy.
In fact LVM is not complex as it seems. I'll explain while showing my system. This is on one hdd. But for multiple hdd it is simple as this.(I will give examples for this too). You can view the output of display commands in attachments.

First my HDD partitions. In this section there is no LVM.

1-) /dev/sda1 - 20 GB - Windows - NTFS File System
2-) /dev/sda2 - 100 MB - Boot - EXT2 File System (Because Boot can not reside in LVM in GRUB - in GRUB2 maybe it is different)
3-) /dev/sda3 - 73 GB - Free Space

Small Note: I suggest Reiserfs for /var partition because it is very fast with small files in /var. Don't forget to use noatime and notail options. And also separate partitons for /home and /.

And i point /dev/sda3 as LVM in Cfdisk. Now:

3-) /dev/sda3 - 73 GB - LVM Type

Now i can create physical volume for LVM in there. Nothing is happening yet. We are kind of flagging. Command is pvcreate(Physical Volume Create)

```
pvcreate /dev/sda3
```

What happened? Well, we can see it with pvdisplay(Physical Volume Display)

```
pvdisplay
```

Ok. Time to create Volume Groups in this Phsyical Volume. 

```
vgcreate lvm(You can choose any name) /dev/sda3
```

Display:

```
vgdisplay
```

If there was only one HDD we would move to the next section. Assume we have more than one. These are:

/dev/sda
/dev/sdb
/dev/sdc

We want them to be as one. Like the mighty Archons in Aiur! :) OK. You have to create "Physical Volumes" in other drives too. Remember "pvcreate"? You will apply this to 2nd and 3rd drives too.

```

pvcreate /dev/sdb1(This can be sdb2 or sbd3 or what partition you choose as LVM)
pvcreate /dev/sdc3(Same as above)

```

Now they are ready! 
**ATTENTION!:** 
You won't create new groups in these drives like we did above with the command "vgcreate".

We want them to be together in the same "Volume Group". So we will "extend" first to group to inherit new partitions. Group name is "lvm". "Physical Volumes" are "/dev/sdb1" and "/dev/sdc3" Let's continue:

```
vgextend lvm /dev/sdb1
```
```
vgextend lvm /dev/sdc3
```

Congratulations! Your 3 drives are now connected(In fact the partitions you created as "Physical Volume" from hard-drives are connected. You can make all drive as LVM as well. This is the flexibility of Lvm.)

Now let's create "Logical Volumes". I will create 4 Volumes named as "root, var, swap, home"(You can choose other names).

```

lvcreate -L 7G lvm -n root
lvcreate -L 5G lvm -n var

For swap:

lvcreate -C y -L 2.2G lvm -n swap

And for home i want to use the remaining free space to be filled:

lvcreate -l +100%FREE lvm -n home

Let's view them:

lvdisplay

```

**Last Part:**
Note: This part can be done in Ubuntu Installer.

Create filesystems and finish. For this part i will citate from ArchWiki:

Your logical volumes should now be located in /dev/mapper/ and /dev/YourVolumeGroupName. If you can't find them, use the next commands to bring up the module for creating device nodes and to make volume groups available: 

```

modprobe dm-mod
vgscan
vgchange -ay

```

Now you can create filesystems on logical volumes and mount them as normal partitions (if you are installing Arch linux, skip this step. Use the arch installer to pick the LVM partitions that you have created):

```

mkfs.ext4 /dev/mapper/lvm-root
mount /dev/mapper/lvm-root /

mkfs.reiserfs /dev/mapper/lvm-var
mount /dev/mapper/lvm-root /var

mkfs.ext4 /dev/mapper/lvm-home
mount /dev/mapper/lvm-root /home

```

Phew :) Try it. It is not complicated as it seems. And it is very fun i guarentee you. I hope this small guide helps :)

---

### Post by BrokenKingpin on 2011-10-24
I did end up getting LVM going on my machine. I used system-config-lvm to get the basics going and then a few command line tools.

Thanks for the input medic2000.

---

### Post by mips on 2011-10-25
> **medic2000 said:**
> Try it. It is not complicated as it seems. And it is very fun i guarentee you.

Until one of your disks experiences a problem...

---

