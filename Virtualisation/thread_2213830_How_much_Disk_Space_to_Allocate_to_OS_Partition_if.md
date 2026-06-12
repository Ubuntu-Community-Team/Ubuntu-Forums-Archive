---
title: "How much Disk Space to Allocate to OS Partition if Planning to use VirtualBox?"
date: 2014-03-28
forum: Virtualisation
---

### Post by Ivan_C on 2014-03-28
Hi,

I have a noob question for you guys:  If I have a 1TB Hard Drive and I want to be efficient about allocating disk space to Ubuntu during the partitioning process, but also want to allocate "enough space" for a virtualbox setup how much disk space is enough?
[B]
Allow me to clarify my concern:
[/B]
I am afraid that if I allocate say 25GB to the Operating System partition (forgot the proper name for that partition) I may run out-of-space if I install another operating system via virtualbox.

I am not sure if I can instruct virtualbox to use another partition to install an OS other than my operating system partition. 

I know you may be thinking "You have a dam TB!, just allocate 100GB to the OS partition and done"... 

Well, while I realize that is an option, I don't want to be inefficient and have a ton of available space in the OS partition which I can use in other partitions "just because" ... 

Any input is vastly appreciated :)

---

### Post by GigabyteProduction on 2014-03-28
It's very possible to put stuff on another partition, i do this all the time because i transitioned from windows to ubuntu, and i still have it around just in case something in linux doesn't work out (this is a very real concern for me because i am a gamer) so i never know if i'm going to have to go back to windows, so i setup my actual os to be on a partition that's only 30 gigs, and setup an 800 gig ext3 partition for files that i want accessable from windows (i am going to use an ext3 driver for windows). So what you need to do to do this:
- make another partition (there are a bunch of filesystems that can be resized, all the exts are one of them, so if you run out of space, just enlarge it with gparted)
- move your "VirtualBox VMs" folder form your home into the secondary partition
- run "ln -s "the moved virtualbox vms folder" "your home folder"

you can also do this for your entire /home directory, i am going to do this because i create way to many symbolic links to wine prefixes, but if you do that after install, do it from a virtual terminal instead of the UI so no files end up locked on you.
if you do it from the installation, it's going to mount the home directory as that other partition so anything on the root of that partition is considered in the home directory, so use "ln -s" if you want a multipurpose partition, or use mounting if you want a dedicated partition to all of your non-os files and non-program files

these methods are pretty transparent, you shouldn't have any programs reset on you if you do this correctly

---

### Post by andrew.46 on 2014-03-29
I could be considered to have a simplistic view of things but I have only 2 partitions: a small one for swap (usually not even used) and a partition for everything else. I prefer a simple life....

---

### Post by gordintoronto on 2014-03-29
Virtualbox doesn't store its "hard drives" in the root, so you don't have to worry about that.

My root is 36 GB, which is much bigger than it needs to be, but it's such a disaster if it fills up that I didn't want to mess around.

---

### Post by GigabyteProduction on 2014-03-29
> **Ivan_C said:**
> I am not sure if I can instruct virtualbox to use another partition to install an OS other than my operating system partition.

that's why i offered the new partition idea.

> **gordintoronto said:**
> Virtualbox doesn't store its "hard drives" in the root, so you don't have to worry about that.

My root is 36 GB, which is much bigger than it needs to be, but it's  such a disaster if it fills up that I didn't want to mess  around.

virtualbox stores it's virtual disks in your home folder, which is usually on the root partition. I don't think the asker put his home folder on another partition, since that's *almost* what's he's asking about.

---

### Post by gordintoronto on 2014-03-29
> **GigabyteProduction said:**
> virtualbox stores it's virtual disks in your home folder, which is usually on the root partition.... 

Sorry, that's not true. The normal way to set up multiple partitions is to have a root (/) partition, a swap partition, and a home (/home) partition.

Doing this makes installing a new version much easier. My /home partition is almost five years old, and I have done multiple OS installations in that time.

---

### Post by GigabyteProduction on 2014-03-29
> **gordintoronto said:**
> Sorry, that's not true. The normal way to set up multiple partitions is to have a root (/) partition, a swap partition, and a home (/home) partition.

Doing this makes installing a new version much easier. My /home partition is almost five years old, and I have done multiple OS installations in that time.

I didn't realize that was the "normal" setup, that setup makes perfect sense and it's how i am going to do things once i reset xubuntu when i get a full idea on how i perfectly want my system to be set up, but the asker did say this was a noob question so it seemed like a valid asumption that they went with a simple setup without a lot of partition changes and especially since **they were worried about the "os partition" being filled**. It's also why i said it's *usually* on the root partition.

---

