---
title: "Remove FakeRaid from server unit."
date: 2010-02-10
forum: Server Platforms
---

### Post by adam.ec on 2010-02-10
We have a small file server running Ubuntu 8.04.1 Server Edition. It has two 500GB drives set up in RAID1 (software raid). I want to remove one of the drives for reformatting and bring this unit down to just a single drive but I don't want to lose the information that is stored on it at the moment.

Can anybody point me in the direction of simple instructions to remove the raid system and just get the one drive to be seen as a single drive?

Ubuntu is stored on it's own 10GB partition with the data files being stored on the rest of the drive but when I type in "fdisk -l" I get MD0, MD1 and MD2.

If it is just a case of removing the second drive and Ubuntu will still boot please let me know as I can shift all the data files through the network onto the reformatted second drive and then just reformat the first one.

Many thanks.

---

### Post by realjaja on 2010-05-11
> **adam.ec said:**
> We have a small file server running Ubuntu 8.04.1 Server Edition. It has two 500GB drives set up in RAID1 (software raid). I want to remove one of the drives for reformatting and bring this unit down to just a single drive but I don't want to lose the information that is stored on it at the moment.

Can anybody point me in the direction of simple instructions to remove the raid system and just get the one drive to be seen as a single drive?

Ubuntu is stored on it's own 10GB partition with the data files being stored on the rest of the drive but when I type in "fdisk -l" I get MD0, MD1 and MD2.

If it is just a case of removing the second drive and Ubuntu will still boot please let me know as I can shift all the data files through the network onto the reformatted second drive and then just reformat the first one.

Many thanks.

were you able to solve your problem?

---

### Post by adam.ec on 2010-05-11
Hi,

yes I did manage to get the problem sorted though I can't remember the commands I used to start it off.

Basically I removed the partitions from the raid array, unmounted them all, took out the drive. On the one I wanted to keep I used Gparted to create a new partition at the beginning off the drive and reinstalled Ubuntu server. The data stayed intact and just came up as another ext3 partition which I mounted in fstab. It's been working fine ever since.

---

### Post by realjaja on 2010-05-11
> **adam.ec said:**
> Hi,

yes I did manage to get the problem sorted though I can't remember the commands I used to start it off.

Basically I removed the partitions from the raid array, unmounted them all, took out the drive. On the one I wanted to keep I used Gparted to create a new partition at the beginning off the drive and reinstalled Ubuntu server. The data stayed intact and just came up as another ext3 partition which I mounted in fstab. It's been working fine ever since.

ouch - so you have to reinstall the system?  thats nuts....  i hope there is another way...

---

### Post by gvernold on 2010-05-11
Well if you've already got an installation on at the beginning of the drive you can still disconnect and unmount the raid partitions, check what the partition numbers are in Gparted and then mount them as any normal partition through fstab. I do seem to remember having to get rid of the raid flag on the drive though which I also did through a Gparted livecd.

---

### Post by realjaja on 2010-05-11
> **gvernold said:**
> Well if you've already got an installation on at the beginning of the drive you can still disconnect and unmount the raid partitions, check what the partition numbers are in Gparted and then mount them as any normal partition through fstab. I do seem to remember having to get rid of the raid flag on the drive though which I also did through a Gparted livecd.

thanks for the info... here's my story...

1. had 8.10 + mdadm raid1 running (all partitions on raid1)
2. upgraded to 9.04
3. all hell broke loose
4. currently still stuck in busybox/initramfs

so i'm hoping to just revert back to a regular non raid setup and hook it up to my hardware raid setup.  the problem is that i can't start the system up... should i just skip up to 10.04 and upgrade?  i'm afraid that i'm still in the middle of this upgrade process, that i'm going to break things...  my plan is to download a disc image for 9.04 and try to fix it with that.

---

### Post by gvernold on 2010-05-11
My own personal opinion.... definitely not a guarantee of what to do or even that it would work, but, if your data is precious to you I would not touch the partition with data on it until I had a working operating system to access it with and keep it intact. Then I would start trying to get RAID working again.

Just as a question, and I know you are probably annoyed with people asking you this but are you using RAID for redundancy or backup? If it is for backup, take your RAID apart and get a decent back up utility. The redundancy I'm talking about is like if a drive fails and you're not in a position to reboot your server, you just need it to carry on. I've found that RAID just causes a lot of headaches when manipulating volumes and things and unless your server really needs to be on 24/7 for a couple of years its not so helpful in small business situations. Having said that I didn't know about your requirements but it's just an observation.

---

### Post by erogevets on 2010-05-11
Simple way to do this is just to change the devices in grub config and /etc/fstab

Just change device md0 for sda1, md1 for sda2 for example, change the partition type using fdisk and then reboot.

---

### Post by realjaja on 2010-05-12
> **gvernold said:**
> My own personal opinion.... definitely not a guarantee of what to do or even that it would work, but, if your data is precious to you I would not touch the partition with data on it until I had a working operating system to access it with and keep it intact. Then I would start trying to get RAID working again.

Just as a question, and I know you are probably annoyed with people asking you this but are you using RAID for redundancy or backup? If it is for backup, take your RAID apart and get a decent back up utility. The redundancy I'm talking about is like if a drive fails and you're not in a position to reboot your server, you just need it to carry on. I've found that RAID just causes a lot of headaches when manipulating volumes and things and unless your server really needs to be on 24/7 for a couple of years its not so helpful in small business situations. Having said that I didn't know about your requirements but it's just an observation.

this forum's been pretty good.... as for RAID - my main goal is redundancy, basically the ability to restart at a moments notice in case of hard drive failure.  i plan to switch to a hardware raid solution. and agree software raid is not worth it.

---

### Post by realjaja on 2010-05-12
> **erogevets said:**
> Simple way to do this is just to change the devices in grub config and /etc/fstab

Just change device md0 for sda1, md1 for sda2 for example, change the partition type using fdisk and then reboot.

thanks - i guess this is the answer i was looking for.

newbie here.... so is this what i should do?

1. burn up a 9.04 CD (i assume this is my best option since, i was technical in between upgrading between 8.10 and 9.04, everything was updated and this didn't boot up on the final restart)

2. enter the shell from the cdrom, edit grub and fstab - fstab seems pretty straight forward 'sudo nano /etc/fstab' - grub is in /boot/grub - and i assume edit the menu?

---

