---
title: "Resizing a GPT partition with a ext4 filesystem"
date: 2010-01-24
forum: Server Platforms
---

### Post by gertin on 2010-01-24
I'm trying to resize (grow) a large (3TB) GPT partition with the ext4 filesystem on Ubuntu Server 9.10 amd64.

I'm having some problems figuring out which tools to use, and the sheer amount of information returned by googling has left me a bit confused. So far I have boiled it down to the following:

[LIST]
[*] I can't use fdisk to resize the partition because fdisk doesn't support partitions larger than 2TB
[*] I can't use gparted because:
1) It's a headless server and I don't have physical access to it right now.
2) The developers of gparted have issued a warning regarding ext4 filesystems: [http://gparted-forum.surf4.info/viewtopic.php?id=13960](http://gparted-forum.surf4.info/viewtopic.php?id=13960)
[*] My best bet seems to be the parted resize command and resize2fs, if I have understood the manual for parted correctly
[/LIST]

The man page for parted says:
> KNOWN ISSUES
       ext3 filesystem functionality does not currently work.  To manage ext3 type filesystems use tools like resize2fs(8 ) or mke2fs(8 ).  Note that the currently supported ext2 filesystem
       will  be  deprecated  once  ext3  support  is finalized.  Further note that ext3 support will have limited functionality that is yet to be defined.  Use tools like resize2fs(8 ) and
       mke2fs(8 ) to manage these types of filesystems.

Does this mean that parted will resize the partition and don't touch the filesystem (leaving me to use resize2fs) or does it mean that it won't work at all?

---

### Post by Vegan on 2010-01-24
The Windows based Partition Manger from whoever owns it these days can resize partitions and recognized some Linux partitions. No sure if it supports GPT yet.

---

### Post by gertin on 2010-01-25
I solved this by doing the following with parted:
[LIST]
[*] Run parted on your device: parted /dev/sdX
[*] Change display unit to sectors: unit s
[*] Print current partition table and note the start sector for your partition: p
[*] Delete your partition (won't delete the data or filesystem): rm <number>
[*] Recreate the partition with the starting sector from above: mkpart primary <start> <end>
[*] Exit parted: quit
[*] Check the filesystem: sudo e2fsck -f /dev/sdXX
[*] Resize filesystem: sudo resize2fs /dev/sdXX
[/LIST]

---

### Post by Jimbro727 on 2011-02-02
> **gertin said:**
> I solved this by doing the following with parted:
[LIST]
[*] Run parted on your device: parted /dev/sdX
[*] Change display unit to sectors: unit s
[*] Print current partition table and note the start sector for your partition: p
[*] Delete your partition (won't delete the data or filesystem): rm <number>
[*] Recreate the partition with the starting sector from above: mkpart primary <start> <end>
[*] Exit parted: quit
[*] Check the filesystem: sudo e2fsck -f /dev/sdXX
[*] Resize filesystem: sudo resize2fs /dev/sdXX
[/LIST]

Thank you!! I thought this was going to be a major headache!

For anyone who's looking to grow a GPT partition with only command line tools, this works exactly, if you're unfamiliar with 'parted', use -1 for <end>, so "mkpart primary <start> -1", **if you're looking to expand an existing partition to fill the rest of the volume**.

Jim

---

### Post by srs5694 on 2011-02-02
It's a little surprising that GNU Parted (the "parted" command) can't resize an ext4 filesystem. It's based on the same underlying libparted tool that GParted uses, and GParted can do it just fine. (I just checked, using a GPT disk just to be sure there's no interaction there.) Sure enough, though, when I tried with parted, I got an error message. Maybe GParted is actually calling resize2fs behind the scenes....

Anyhow, GParted can be run remotely -- you just need to enable some way for X to work. This is usually easily implemented via SSH and its -X option, as in:

```

ssh -X user@server.example.com

```

This logs into server.example.com as user, enabling X-based programs to run. The server must support X tunneling. Of course, GParted would need to be installed on server.example.com, which it might not be if it's a dedicated server computer.

The procedure described will certainly work if it's the only option; however, there are at least three caveats. First, you've got to be *very very* careful to create a partition while *not* creating a filesystem on it. Since parted can do both tasks with one command, it's easy to slip up, and doing so will make for a Very Bad Day. You might want to use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) instead of parted for this; since GPT fdisk manipulates partition tables only, it can't damage your filesystems all by itself. (At least, not unless you do weird things with it.)

Second, modern partitioning tools often impose partition alignment requirements of 1 MiB on disks, so every partition must begin on a 1 MiB boundary. Older tools imposed different requirements, so a modern tool might complain or "fix" an "improperly aligned" partition, which will cause you problems. I just tried the operation with GNU Parted 2.3 using a partition that began at sector 63, and it worked, but it complained about the alignment. I can't promise that other versions will work the same way. GPT fdisk should work OK on relatively small disks (it tries to detect and match the disk's original alignment policy), but on disks larger than 596 GiB, it imposes 8-sector alignment. It's possible to override this using the "l" option on the experts' menu. In any event, no matter what tool you use, you've got to watch this carefully.

Third, when you delete and re-create a GPT partition in this way, its partition-specific GUID will change. To the best of my knowledge, no Linux tools rely on the GUID, so this change is unlikely to make any real difference; however, it's conceivable that there's a Linux tool out there that will get confused, or something in some other OS might get confused. If you want to preserve the GUID value, you'll have to use a tool that enables you to view it on the original and then change it back after re-creating the partition. AFAIK, parted doesn't have this ability. GPT fdisk can do it, though; you'd use the "i" option on the main menu to view the original GUID value (it's labelled "Partition unique GUID"), then delete and re-create the partition, then type "x" to get to the experts' menu and type "c" to change the GUID value (you'd cut-and-paste the value you obtained earlier). I doubt if it's worth the effort to do this, but if you think you've got a program that would get confused, you can do so. Note that the partition GUID value is distinct from the filesystem's UUID value, which Ubuntu uses in /etc/fstab and in its GRUB setup. The filesystem UUID will probably remain the same (it always has in my filesystem-resizing tests), but some people have reported it changing when filesystems are resized.

Anyhow, for all of these reasons, but especially the first two, IMO it's better to use GParted for this job if at all possible. If not, be very alert to the dangers. Don't try it while you're sleepy or distracted, and think carefully about every step as you perform it.

---

