---
title: "Logical partitions (fork from Distro Fever thread)"
date: 2005-02-16
forum: The Cafe
---

### Post by TravisNewman on 2005-02-16
I'm thinking of making up a howto for those who want to do what I did and install a buttload of linux/bsd/windows to one drive.

I have one question though. I know that all flavors of traditional UNIX (Solaris, Free/Net/Open- BSD, etc) must have their own primary partition. Therefore you couldn't install Solaris, FreeBSD, NetBSD, and OpenBSD and then install Linux, because all primary partitions would be taken up. As far as I can tell there's no way around this.

However, i've also read that you can't install Windows on a Logical partition unless there's at least one primary windows-compatible partition to keep the boot files. Is there any way around this? Because I KNOW that I did it this weekend, but now I can't seem to. my 3 primary partitions were linux /boot, FreeBSD, and Solaris. All three of those have to be primary (Linux /boot does, right?) and I know that the Windows partition (fat32 so that Linux could read/write to it) was in the extended partition. Unless something got broken in some magical way that let me get around this, there must be some way. Could it be that there is a difference between the Windows way of making extended partitions and the Linux way? I also know because of recent trials that Windows CAN read partitions inside extended partitions created by Linux, but maybe it can't boot them? I dunno.

Any help is appreciated.

---

### Post by slackerj on 2005-02-17
Yes you can install Windows into an extended partition BUT you can not use thier boot loader to start Windows. This is because the Windows boot loader only searches the first 4 primary partions for Windows. So in theroy, you COULD install Windows into an extended partition and use grub/lilo to load it.

I think you are correct in saying that the linux /boot needs to be a primary partition.But I don't see why it has to be. It will still be called from the disk. But.. meh??

EDIT: Found this for you. Might be of some help??

[How-To: GRUB to Boot FreeBSD, Linux, and OpenBSD](http://geodsoft.com/howto/dualboot/grub.htm)

---

### Post by wallijonn on 2005-02-18
pt,

What boot managers have you tried?

---

### Post by ember on 2005-02-18
From what I remember, you can't install Windows (2000, I did not try XP) into an extended partition, because it complains it isn't able to write to the first primary partition (I had SuSE Linux installed on the system).
Yet it may have changed meanwhile, but I always sticked to "install Windows first, then Linux"

---

### Post by TravisNewman on 2005-02-18
XP doesn't work because it says that it can't find an xp compatible partition, even if I make it during windows setup. If I free up a primary partition it works fine. So poop. If I then install it to the extended partition it puts the boot files into the primary.

wallijonn: grub, and grub alone

---

### Post by ember on 2005-02-18
O.k. That confirms my suspection ... though I have to admit that I do not think Windows XP is that bad, sometimes it really stinks.

---

