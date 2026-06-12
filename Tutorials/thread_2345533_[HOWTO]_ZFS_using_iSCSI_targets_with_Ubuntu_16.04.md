---
title: "[HOWTO] ZFS using iSCSI targets with Ubuntu 16.04"
date: 2016-12-05
forum: Tutorials
---

### Post by mploots on 2016-12-05
Hi.

**What I was actually trying to do** [you may want to skip this and go to the guide part now]
I have a new server here, a HP DL60 Gen9 with a small mirrored SSD as system disk. It is meant as a big fileserver and to do some trickery for our Windows and Mac users on our LAN. In order to give it ample diskspace, it's connected to a 32 TByte Synology box, that only has to make sure the disks are available via iSCSI.
This setup is mirrored in our colocation, but the front-end to the NAS there is a VMware Ubuntu guest that also intelligently supports our out-of-office workers and selected 3rd parties.
The "trickery" is to make sure both setups are properly synced, independently where the new data is being added. I selected ZFS as the basis for the filesystem and volumes, because it is perfectly suited to help handle this: it's robust, handles large volumes with ease and syncing is quick and easy.

Before the hardware arrived, I tested the functionality with a VMware Ubuntu 14.04 guest. With 14.04, I had an issue with ZFS not being online on the iSCSI drives after reboot, but that was easily fixed after some Googling (see below). Installed Samba, connected to AD and Windows and MacOS clients could connect well and with great speed.

When the HP hardware arrived, I decided to go for Ubuntu Server 16.04 instead. It has native support for ZFS now, Samba 4 and the system is meant to be there for a while, so it seemed a logical choice to pick the most recent LTS version. I have a number of other 16.04 systems running without issue and was not affected by the switch to systemd. **Yet**, as it turned out.

I was really struggling to get it running with 16.04. The shutdown sequence always timed out on some issue and the system (that is: the hardware based DL60 server) became completely unresponsive with every reboot or shutdown. I had to manually powerdown and -up again. That should not happen to servers. You need to be able to reliably restart it, either remotely or via the console. I then tested 16.04 on a VMware based setup and found no issues rebooting that configuration. This led me to believe that the shutdown problems would be tightly coupled with the hardware base. I looked through the DL60 systemd journal ("journalctl") and found several places where systemd was complaining about bugs about the hardware (in fact suggesting I should bug the vendor about the issues). To make sure the hardware configuration would most closely be like the VMware counterpart in our colocation, I turned off UEFI in favor of the old fashioned BIOS boot, reinstalled 16.04 and configured it as described below. The DL60 server now reboots happily...

**Guide part**
The "iSCSI / ZFS volumes not being present" problem was a known issue. You won't find much about it yet in combination with Ubuntu 16.04, but there are plenty references to it with Ubuntu 14.04. In order to place it in perspective, I will discuss them both here.

**A recap for Ubuntu 14.04**
File [FONT=lucida console]/etc/init/zpool-import.conf[/FONT], change the autoimport probe to read this (= change 1 to 0):
```
modprobe zfs zfs_autoimport_disable=0
```

File [FONT=lucida console]/etc/rc.local[/FONT], add line above "exit 0":
```
zfs mount -a
```

The issue is that ZFS is thought to be running on _local _disks and thus starts before the iSCSI targets are online. With the small changes above, after booting the system, the zpools are automatically imported and when finally [FONT=lucida console]rc.local[/FONT] is being executed, ZFS mounts all available drives (which now include the iSCSI targets).

**Not so easy with Ubuntu 16.04...**
Ubuntu 16.04 uses systemd instead of the "usual" startup/shutdown scripts. The way Ubuntu thinks about ZFS running on local filesystems is still the same though, but [FONT=lucida console]systemd [/FONT]handles it in an entirely different manner. To make a long story short: 1) the 14.04 fix doesn't work and worse, 2) when you execute a reboot or shutdown with the ZFS volumes online on iSCSI targets, the system may hang if you are on hardware, ie. needs to be powered down/up the hard way... For some reason, if you run your Ubuntu 16.04 in a VMware virtual machine, there's no hangup on reboots. YMMV with other hypervisors.

So, the 16.04 fix does need a 2-tier approach, one for a clean startup and one for clean shutdowns/reboots/halts. Below is what I did; straightforward and maybe not the best way, but at least something I could understand with my current limited [FONT=lucida console]systemd [/FONT]experience.

** Startup fix**
Ubuntu 16.04 has no [FONT=lucida console]/etc/init/zpool-import.conf[/FONT] file that we used in 14.04 to make sure ZFS imports are being done automatically. To add to the confusion, the rc.local file is not being used by default. To fix the zpool imports before the mount, I tried this on the command line once the system had started and it worked:
```
# zpool import -a; zfs mount -a
```
So, not **that **much to put in an initialization script... :)

FYI: it turns out [FONT=lucida console]systemd [/FONT]***can ***start [FONT=lucida console]/etc/rc.local[/FONT], but it is being called after the network has come up and still before iSCSI is live and thus too early...

As we **will **need these commands, let's put them elsewhere. You can use these steps (log in as root, "[FONT=lucida console]sudo su -[/FONT]"):
```

# mkdir /usr/local/lib/zfs
# cat > /usr/local/lib/zfs/zfs-up.sh
#!/bin/bash
/sbin/zpool import -a
/sbin/zfs mount -a
<CTRL_D>
# chmod 755 /usr/local/lib/zfs/zfs-up.sh

```

**Shutdown fix**
This is basically the reverse, though unmounting is sufficient here, so let's set that up too (steps below, as root again):
```

# cat > /usr/local/lib/zfs/zfs-down.sh
#!/bin/bash
/sbin/zfs unmount -a
<CTRL_D>
# chmod 755 /usr/local/lib/zfs/zfs-down.sh

```

To verify, this is what you should see now (check the privilege bits, they should be executable):
```

# ls -l /usr/local/lib/zfs/
total 8
-rwxr-xr-x 1 755 root 33 Dec  3 12:55 zfs-down.sh
-rwxr-xr-x 1 755 root 53 Dec  3 12:54 zfs-up.sh
# 

```

You can test both scripts now. You should see the ZFS mounted volumes after you run [FONT=lucida console]zfs-up.sh[/FONT]. Verify the system shutdown by first running [FONT=lucida console]zfs-down.sh[/FONT] to dismount the ZFS volumes; after that, a reboot should function well.

**Integrate the ZFS scripts with [FONT=lucida console]systemd[/FONT]**
I'm working with UNIX for 33 years now and systemd was not really my thing, more or less based on unfamiliarity. As a Ubuntu Server fan for many years now, 16.04 turned my world a bit upside down confronting me with systemd the hard way... :mad:
Being in IT, one should be open for new things every day though, so I got stuck in. I must say, it's not all bad. Not bad at all, actually... I have grown to appreciate the [FONT=lucida console]systemd [/FONT]way of running UNIX. I guess there may be more "greybeards" like me, so I'm going to explain this step-by-step and maybe help some others with that.

Put the systemd service code in place first, as root, like before:
```

# cat > /lib/systemd/system/zfs-special.service
[Unit]
Description=Take care of all ZFS, even on iSCSI targets
Wants=network-online.target remote-fs.target iscsid.service
After=remote-fs.target iscsid.service
DefaultDependencies=no
Conflicts=shutdown.target
Before=shutdown.target

[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/usr/local/lib/zfs/zfs-up.sh
ExecStop=/usr/local/lib/zfs/zfs-down.sh

[Install]
WantedBy=sysinit.target
Alias=zfs-special.service
<CTRL_D>
# 

```

This file needs to be readable by systemd. You may want to verify that for yourself.

Now for the explanation. Keep in mind that systemd parses such services files as-if it is being read running for a startup job only, not as a shutdown job. I will explain that later.

**[Unit] part**
This declares the service, its name and dependancies.[INDENT]**Description**
Defines the name; you see it on the console when the service starts/stops and also in the [FONT=lucida console]systemd [/FONT]journal (the "log" of systemd).

**Wants**
Defines what should be present at its startup. In this case, it wants that the network is online, that remote filesystems are online, and (just to make sure here), that the [FONT=lucida console]iscsid [/FONT]service is working.

**After**
Specifically tells [FONT=lucida console]systemd [/FONT]to make sure this won't start until the remote file[FONT=lucida console]systems are online and the iscsi daemon has been started.[/FONT]

**DefaultDependancies**
Nothing special here. These are ZFS scripts and ZFS has been installed and started already. I guess I could put a ZFS service here, but I basically copied a few lines from another [FONT=lucida console]systemd[/FONT] service that worked and "no" was in there, so I left it there. If it works, don't fix it, eh?

**Conflicts**
Remember, it is to be read as a startup description only? That is what this line means (I think, I did not really dive into this yet). I guess it tells [FONT=lucida console]systemd [/FONT]to not run this if for some reason the initialization is immediately taken over by a shutdown... (Copied it, so left it in)

**Before**
As with the "After" definition, this tells [FONT=lucida console]systemd [/FONT]that it should always be run before a shutdown. Seems a bit extra, but can't hurt I guess. (Copied it, so left it in)
[/INDENT]

**[Service] part**
This declares what to execute and how that is handled.[INDENT]**Type**
The "[FONT=lucida console]oneshot[/FONT]" tells systemd this is just  to be run once.

**RemainAfterExit**
This being "[FONT=lucida console]true[/FONT]" will make sure this service will persist being enabled once that is done.

**ExecStart**
This tells which command to run when the service is being started (ie. "[FONT=lucida console]systemctl start zfs-special[/FONT]", or like the olden days: "[FONT=lucida console]service zfs-special start[/FONT]")

**ExecStop**
This tells which command to run when the service is being stopped (ie. "[FONT=lucida console]systemctl stop zfs-special[/FONT]"). I will explain this below.
[/INDENT]

**[Install] part**
This tells [FONT=lucida console]systemd [/FONT]which part of the OS it belongs to.[INDENT]**WantedBy**
Tells [FONT=lucida console]systemd [/FONT]which target needs to work with this service. It has to run during system init of course.

**Alias**
I believe this is not essential, but copied it, so left it in place....[/INDENT]

**How will this help with system shutdowns/reboots, etc.?**
The trick is that [FONT=lucida console]systemd [/FONT]interprets the service as an order in which to run at startup, but then also says: "I should use the rules in the exact reverse order on shutdown, but use ExecStop instead of ExecStart". For us, this basically means that we now defined it for startup, the [FONT=lucida console]zfs-up.sh[/FONT] script will be run **after **iSCSI is up and running. For shutdown, the [FONT=lucida console]zfs-down.sh[/FONT] script will run **before **iSCSI is being brought down. It's like magic... :P
 
**Put it to work**
As root, type these commands. The first is to set the mounts live, the second to make sure the service is present at boot time:
```

# systemctl start zfs-special
# systemctl enable zfs-special

```

Now reboot, and it should work out fine (I had a first time fail, the system locked up as the ZFS volumes were still mounted when the iSCSI was down already, but it did work flawlessly every time after that, so I probably did something wrong on the command line before... YMMV).

**To get rid of it**
Just disable the service, as root:
```

# systemctl disable zfs-special

```

Disclaimer 1: This guide may have serious side effects if you mix local ZFS with iSCSI ZFS. It's meant for ZFS on iSCSI disks only.
Disclaimer 2: I probably did not explain each step exactly as it should be. As I mentioned, I copied another service script that looked like a good starting point and went from there. Don't reinvent the wheel, etc. But if you know better, I welcome additions and critiques...
Disclaimer 3: I think that systemd has a bit of a way to go though. Even with a less than optimal hardware fit, I have never seen shutdown lockups as persistent as these before with hardware that functions without any issue otherwise. IMHO of course, IMHO.

---

### Post by kingneutron on 2016-12-05
--Excellent HOWTO, thanks for posting it

---

### Post by QIII on 2016-12-05
Hello!

This has been moved to Tutorials.

Although this is very good, I'd like you to review [https://ubuntuforums.org/showthread.php?t=2143602](https://ubuntuforums.org/showthread.php?t=2143602)

In particular, see points 8, 9 and 10.  Please make any changes as necessary.

Cheers!

---

### Post by mploots on 2016-12-05
> **QIII said:**
> Hello!  This has been moved to Tutorials.  Although this is very good, I'd like you to review [https://ubuntuforums.org/showthread.php?t=2143602](https://ubuntuforums.org/showthread.php?t=2143602)  In particular, see points 8, 9 and 10.  Please make any changes as necessary.  Cheers!  Hi QIII.  I was wondering where to place it. Tutorials sounds good to me... :)  I'll try to add some new words to it too.  Thanks.

---

