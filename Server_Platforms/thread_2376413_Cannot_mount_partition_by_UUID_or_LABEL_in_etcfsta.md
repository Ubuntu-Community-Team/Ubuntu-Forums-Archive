---
title: "Cannot mount partition by UUID or LABEL in /etc/fstab"
date: 2017-11-02
forum: Server Platforms
---

### Post by onkelj on 2017-11-02
Hi,

I have an Ubuntu 16.04.3 LTS server which is my syslog server. It is running as a VMware guest.

After rebooting it today, after updates, it failed to mount /dev/sdb1 and dropped me to an emergency shell during boot asking med to run "journalctl -xb". After checking the journal I found the "timed out waiting for device dev-disk-by"-message.

After googling a bit, I went into /etc/fstab and changed mount from UUID of the /dev/sdb1 to /dev/sdb1 and rebooted the server. Then everything came up as normal. I checked with "blkid" and got this:
```
/dev/sdb1: UUID="ded49e25-8e02-43cd-89f0-5297bdca5063" TYPE="ext3" PARTUUID="abd312a9-01"

```
Then I compared that to what was earlier in /etc/fstab:
```
UUID=ded49e25-8e02-43cd-89f0-5297bdca5063 /syslog-ng/logs      ext3    defaults 1 2

```
...and they match!? Okay, so then I proceeded to label the partition with "e2label /dev/sdb1 LOGS" and added this entry to /etc/fstab instead:
```
LABEL=LOGS      /syslog-ng/logs        ext3    defaults 1 2

```
But after a reboot it still doesn't work - same error as before. Here's the new blkid:
```
/dev/sdb1: LABEL="LOGS" UUID="ded49e25-8e02-43cd-89f0-5297bdca5063" TYPE="ext3" PARTUUID="abd312a9-01"

```
So I reverted to using /dev/sdb1 in fstab - and it is working fine now. But I have no idea why it doesn't play well with either UUID or LABEL. Or why it happened now, after an update, when it previously did work. Also, I have several other partitions on the same server, and they mount just fine - either by UUID or LABEL. Just this one partition doesn't. The only difference is that the failing partition is ext3 and others are ext4.

Here's the output from "fdisk /dev/sdb":
```
Disk /dev/sdb: 5 GiB, 5368709120 bytes, 10485760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xabd312a9

Device     Boot Start      End  Sectors Size Id Type
/dev/sdb1        2048 10485759 10483712   5G 83 Linux
```

And from "df -h | egrep 'File|sdb1'":
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       4.8G  1.6G  3.0G  35% /syslog-ng/logs
```

From "ls -l /dev/disk/by-path | grep sdb1":
```
lrwxrwxrwx 1 root root 10 Nov  2 12:47 pci-0000:00:10.0-scsi-0:0:1:0-part1 -> ../../sdb1

```
The commands "ls -l /dev/disk/by-uuid | grep sdb1" and "ls -l /dev/disk/by-label | grep sdb1" does not return anything.

An expample with the same commands for another drive (/dev/sda1):
```
lrwxrwxrwx 1 root root 10 Nov  2 11:59 pci-0000:00:10.0-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  2 11:59 2d4c2e46-1121-4adf-abcc-9b0c6b699200 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  2 11:59 ROOT -> ../../sda1
```

So it seems like the by-uuid and by-label doesn't register anymore.

As explained before, this is not business critical as I'm running the system fine now, but does anyone have any ideas why this happened?

---

### Post by howefield on 2017-11-02
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by LHammonds on 2017-11-02
I checked my servers and fstab is only using ext2 for /boot and ext4 for all other LVM partitions.  I have nothing that mounts ext3.

Are there any error output entries related to the failed mounting in kern.log, dmesg or syslog?

LHammonds

---

### Post by onkelj on 2017-11-03
Hi,

I checked dmesg, syslog and kern.log I found quite a few of these in syslog:

```
Nov  2 11:59:05 syslogger systemd-udevd[277]: Process '/bin/sh  -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.

```
But they correspond with the times when I was able to boot up successfully:

```
Nov  2 11:59:04 syslogger systemd[1]: Started udev Coldplug all Devices.
Nov  2 11:59:04 syslogger systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
Nov  2 11:59:05 syslogger systemd-udevd[277]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd-udevd[282]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd-udevd[274]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd-udevd[285]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Found device 82545EM Gigabit Ethernet Controller (Copper) (PRO/1000 MT Single Port Adapter).
Nov  2 11:59:05 syslogger systemd[1]: Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
Nov  2 11:59:05 syslogger systemd-udevd[285]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd-udevd[281]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk SWAP.
Nov  2 11:59:05 syslogger systemd-udevd[279]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd-udevd[285]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Activating swap /dev/disk/by-label/SWAP...
Nov  2 11:59:05 syslogger systemd-udevd[282]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk.
Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk INSPECT.
Nov  2 11:59:05 syslogger systemd-udevd[281]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Starting File System Check on /dev/disk/by-label/INSPECT...
Nov  2 11:59:05 syslogger systemd[1]: Starting File System Check on /dev/sdb1...
Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk ELK.
Nov  2 11:59:05 syslogger systemd[1]: Starting File System Check on /dev/disk/by-label/ELK...
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check Daemon to report status.
Nov  2 11:59:05 syslogger systemd[1]: Reached target Printer.
Nov  2 11:59:05 syslogger systemd[1]: Activated swap /dev/disk/by-label/SWAP.
Nov  2 11:59:05 syslogger systemd[1]: Reached target Swap.
Nov  2 11:59:05 syslogger systemd-fsck[396]: INSPECT: clean, 11/131072 files, 17196/524032 blocks
Nov  2 11:59:05 syslogger systemd-fsck[403]: ELK: clean, 115/196608 files, 29997/786176 blocks
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check on /dev/disk/by-label/INSPECT.
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check on /dev/disk/by-label/ELK.
Nov  2 11:59:05 syslogger systemd[1]: Mounting /syslog-ng/elk...
Nov  2 11:59:05 syslogger systemd-udevd[282]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Mounting /syslog-ng/inspect...
Nov  2 11:59:05 syslogger systemd[1]: Mounted /syslog-ng/elk.
Nov  2 11:59:05 syslogger systemd-udevd[276]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Mounted /syslog-ng/inspect.
Nov  2 11:59:05 syslogger systemd-fsck[402]: LOGS: clean, 674/327680 files, 455075/1310464 blocks
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check on /dev/sdb1.
Nov  2 11:59:05 syslogger systemd[1]: Mounting /syslog-ng/logs...
Nov  2 11:59:05 syslogger systemd-udevd[453]: Process '/bin/sh -c 'echo 180 >/sys$DEVPATH/device/timeout'' failed with exit code 2.
Nov  2 11:59:05 syslogger systemd[1]: Mounted /syslog-ng/logs.
Nov  2 11:59:05 syslogger systemd[1]: Reached target Local File Systems.
```

And it seems like udev finds the label on LOGS only after fsck (I guess the first entry here is /dev/sdb1):

```
Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk.
Nov  2 11:59:05 syslogger systemd[1]: Starting File System Check on /dev/sdb1...
Nov  2 11:59:05 syslogger systemd-fsck[402]: LOGS: clean, 674/327680 files, 455075/1310464 blocks
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check on /dev/sdb1.
Nov  2 11:59:05 syslogger systemd[1]: Mounting /syslog-ng/logs...
Nov  2 11:59:05 syslogger systemd[1]: Mounted /syslog-ng/logs.
```

...while the other labeled disk looks like this:
```

Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk SWAP.
Nov  2 11:59:05 syslogger systemd[1]: Activating swap /dev/disk/by-label/SWAP...
Nov  2 11:59:05 syslogger systemd[1]: Activated swap /dev/disk/by-label/SWAP.
Nov  2 11:59:05 syslogger systemd[1]: Reached target Swap.

Nov  2 11:59:05 syslogger systemd[1]: Found device Virtual_disk INSPECT.
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check on /dev/disk/by-label/INSPECT.
Nov  2 11:59:05 syslogger systemd-fsck[396]: INSPECT: clean, 11/131072 files, 17196/524032 blocks
Nov  2 11:59:05 syslogger systemd[1]: Started File System Check on /dev/disk/by-label/INSPECT.
Nov  2 11:59:05 syslogger systemd[1]: Mounting /syslog-ng/inspect...
Nov  2 11:59:05 syslogger systemd[1]: Mounted /syslog-ng/inspect.

```
...and the same for the disk labled ELK. And the same displayed itself when I had all the other on UUID, except the logs looked like this insted:
```
Nov  2 08:24:22 syslogger systemd[1]: Starting File System Check on /dev/disk/by-uuid/5efed327-37fb-4a53-94ff-4dfe57eadcf7...

```
...except for /dev/sdb1 which did not show up like this. But I think this is expected, as all the other entries where either by UUID or LABEL in /etc/fstab.

So, I cannot find anything useful in the logs. However, as this is an old, inherited system -which I've conciensously upgraded over the years without even registering the ext3 filesystem, I think this is the time to upgrade it to ext4.

I'll let you know if the problem presists after the upgrade.

---

### Post by LHammonds on 2017-11-03
[Reference article about ext3 and ext4](http://www.thegeekstuff.com/2011/05/Ext2-Ext3-Ext4/)
The above article says:
Maximum size a file can be is 2TB on ext3.
Maximum size a file can be is 16TB on ext4.

Maximum size of file system can be is 32TB on ext3.
Maximum size of file system can be is 1,023TB on ext4.

So if you are not hitting those limits, it may not make a difference.

However, it does say that you can mount an ext3 system as ext4 without actually upgrading to ext4.  But if the problem is related to it "being" ext3, then mounting it as ext4 might not solve anything but might be worth a try since it doesn't actually change anything (good for a quick test).

LHammonds

---

