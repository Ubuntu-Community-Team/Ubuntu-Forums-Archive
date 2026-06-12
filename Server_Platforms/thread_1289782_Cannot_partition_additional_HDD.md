---
title: "Cannot partition additional HDD"
date: 2009-10-12
forum: Server Platforms
---

### Post by rewsay on 2009-10-12
Hello there, I've been trying to mount a secondary HDD inside my server and it's been a disaster.

When I **sudo fdisk -l** both drives appear, /dev/sda and /dev/sdb. But, instead of showing the device boot, start, end blocks, id and system for sdb, it shows:
```

Disk /dev/sdb doesn't contain a valid partition table

```So then I **sudo gparted /dev/sdb** and this comes up

```
(gpartedbin:3822): Gtk-WARNING **: cannot open display:
```I'm a n00b that doesn't know what's going on anymore.

Thank you very much in advance.

P.S. If it helps this was the initial process:

```

*sudo mkdir /data*
 

 *sudo chmod -R 777 /data*
 

 *sudo mkfs.ext3 /dev/sdb*
 

 *sudo mount /dev/sdb /data*
 

 *sudo nano /etc/fstab: added */dev/sdb /data  ext3 defaults 0 0


*sudo mount -a*

```

---

### Post by kpholmes on 2009-10-12
well if you just want to mount it i believe you can just use "mnt" command.

im guessing you want to partition it since your using gparted, awesome program really, try just typing in sudo gparted, instead of telling gparted the path. what happens then?

---

### Post by rewsay on 2009-10-12
Ubuntu says **sudo: mnt: command not found**.

**sudo gparted **returns the same **cannot open display **message.

What I want to do is to make that drive visible to Ubuntu so that I can keep all the website files there, visible to the world wide web. The rest I want to keep for intranet use only.

---

### Post by kpholmes on 2009-10-12
> **rewsay said:**
> sudo gparted returns the same cannot open display 

are you using ssh? cause ive seen that same error when trying to use x11 forwarding.

---

### Post by cariboo on 2009-10-12
Gparted is a graphical program, if you don't have X installed, it won't work. What's wrong with fdisk? After starting it up:

```
sudo fdisk /dev/sdb
```

Just press m it will show you all the commands you need. Once you have partitioned the drive, you need to create a file systems, us mkfs, see man mkfs for options.

---

### Post by rewsay on 2009-10-12
I'm connected directly to the server. Would it give me and advantage if I installed X? Do i just **apt-get install X** ?

I'm not quite familiar with creating a partition. I've done **fdisk** and now **n**, added a new partition successfully. Then I **q!** (If I'm not wrong that's quit n save, right?)

I suppose now I have to **mkfs -t ext2 /dev/sdb**

Thank you guys very much for your patience and help I'm really sorry for the n00bness :/

**EDIT**

Okay so I figured I quit without saving changes. I added a new partition again, and then selected to write table to disk and exit.
Now I **sudo fdisk -l** and I can see the drive is cozily partitioned.

Is that it? Or do I still have to **mkfs -t ext2 /dev/sdb**, if that line's even correct. By the way, what's the difference between ext2 and ext3? Does it really matter which one I choose?

---

### Post by kpholmes on 2009-10-12
glad to hear you got you hd connected and partitioned.

i dont know the difference between ext2 and ext3, but i think ext3 is the standard currently. and i heard somewhere that 9.10 uses ext4. not to sure though

---

### Post by rewsay on 2009-10-12
Actually, after I **sudo mkdir **it went back to being unpartitioned!!! So I partitioned it again and now I'm kinda lost again, ha!

I found the only difference between ext2 and ext3 is the journaling. Not sure about ext4 :S

---

### Post by cariboo on 2009-10-13
Creating a file system in Linux is just like formatting a hard drive in Windows.

Use:

```
mke2fs -t /dev/sdb1
```

After you have created a partition using fdisk.

---

### Post by rewsay on 2009-10-15
I tried **sudo mk32fs -t ext3 /dev/sdb1** and it returns

```
mke2fs: inode_size (128) * inodes_count (1) too big for a filesystem with 0 blocks, specify higher inode_ratio (-i) or lower inode count (-N).
```

I add **-N 0** or **-i  65536** and it returns the same.

---

