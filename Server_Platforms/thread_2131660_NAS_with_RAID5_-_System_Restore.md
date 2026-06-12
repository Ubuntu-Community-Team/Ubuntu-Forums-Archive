---
title: "NAS with RAID5 - System Restore"
date: 2013-04-02
forum: Server Platforms
---

### Post by zambalek80 on 2013-04-02
Hi everyone

something's been bugging me for a while now - but thankfully hasn't happened yet. Let's hope it stays this way some more - fingers crossed.

Anyway, let me first give you my NAS setup:
Ubuntu 12.10 on a single HDD (system drive, that is)
RAID5 setup over 5 HDDs
Of course all data backed up (every now and then) on external drives stored in a safe place.

Now here's my questions:
If anything other than my RAID5 HDDs fails (e.g. the system drive); is it possible to reinstall ubuntu and have the NAS (i.e. the RAID5 array) back up and running with hopefully all data intact (using mdadm which was used to setup the RAID5 in the first place)? Or is it even possible to have some kind of a system image or backup that can be restored to a new system drive and have it work that way? How would I go about doing that?
To carry the thoughts further; would it be possible to (physically) migrate the RAID5 array/HDDs to a new NAS (case and what have you) running ubuntu?

Of course if everything fails I still have my external backups. But it is a huge pain in the a** to restore some 3.5 TB of data through a USB 2.0 connection, I'm sure you'll agree.

Thanx for anyone's feedback.

---

### Post by tgalati4 on 2013-04-02
RAID is not a backup strategy.  It can improve data availability in certain use cases.  You have pointed out the downsides of RAID.  If a component, other than a single drive, goes down, you have lost access to the array, and the data--at least temporarily.  What you are looking for is a RAID migration tool.  I'm not aware of one.  You could write a script, you could back up to the cloud, you could build a second NAS with periodic rsync.

[http://freenas.org](http://freenas.org) and [http://nas4free.org](http://nas4free.org) handle this situation with a slim freebsd operating system that runs entirely in RAM and is booted off of a USB stick.  Configuration files are backed up and stored on the USB stick.  So presumably you could take the USB stick and boot it on another machine (identical hardware) and have your mountpoints and zpools already defined.  I have not had to do this, but it is a nice feature.  The key is having identical hardware available, otherwise the config files are meaningless.  The USB stick also eliminates a spinning system drive and I have my syslog errors sent to an Ubuntu machine that is also running 24/7.  Otherwise log files vanish in RAM and it makes troubleshooting difficult.

You have identified a key issue with NAS and RAID, but I don't know of a good solution.

Depending on your use case, using JBOD (Just a Bunch of Disks) and having rotating backups might be easier.

---

### Post by darkod on 2013-04-02
Yes, one of the great flexibilities of mdadm is that you can move it to another machine and it will keep going, unless you have failures of the raid members and more than the raid level can sustain.

In this case, if your OS disk died, you can install ubuntu server on another disk and it will pick up the running mdadm array without any problems. From that point on, how fast can you restore your system to working state depends on how many changes you have done on the basic ubuntu install, which services are you running, and whether you can simply copy config files onto the new install and expect them to work.

For example, if I'm not mistaken, if you copy the smb.conf back for samba and restart the service, it's good to go.

---

### Post by rubylaser on 2013-04-02
> **darkod said:**
> For example, if I'm not mistaken, if you copy the smb.conf back for samba and restart the service, it's good to go.

As long as you've installed samba, and the mountpoint of your array in /etc/fstab is the same as it was previously :) On my home server (media server), since the base OS doesn't change much, I occasionally dd the OS disk to a second backup disk.  That way if the hard drive dies, I throw the new disk in, turn the computer on, and I'm right back where I was previously.

---

### Post by spynappels on 2013-04-02
It might be worth considering if it is possible to create a RAID1 volume for the OS on 2 small(ish) disks using mdadm and booting from that rather than a single system volume? Grub can cope with RAID1. This at least gives some redundancy for the OS in case of disk failure and may make recovery a little easier.

As said earlier though, RAID only makes it less of a PITA to recover from hardware (disk) failures, a good backup is still important.

---

### Post by zambalek80 on 2013-04-03
Thanx for the replies so far. There's something of interest in every answer for me.
The idea with the RAID1 system disk is appealing, as is the idea of dd'ing /dev/sda (in my case this would be the system disk).
But most of all I'm glad mdadm is a capable piece of software - as darkod pointed out. Since I don't care much for the reconfiguration of the ubuntu system, that's fine by me. The few packages that do matter are installed and configured within 1 or 2 hours.
But as I said in my opening post; if _everything_ goes south, I still have my data backups that I can restore.

---

