---
title: "Ubuntu kills my processes after some time on"
date: 2008-07-01
forum: Server Platforms
---

### Post by zmarty on 2008-07-01
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
RAM: 4GB

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23G  4.8G   17G  23% /
/dev/sda3             429G   19G  389G   5% /storage
tmpfs                 2.0G     0  2.0G   0% /dev/shm

Problem: Ubuntu any new-ish version and Fedora 8 kill my (new) processes on the machine after a while.

To make sure it's not because of my code I wrote two test programs, one in C++ and one in Java that just print an incremented number each second.

CPP version: [http://pastebin.com/f63cf5fa6](http://pastebin.com/f63cf5fa6)

run.sh bash script for CPP:
cd /right/folder/
nohup ./a.out &

Java version: [http://pastebin.com/f6252a9d8](http://pastebin.com/f6252a9d8)

run.sh for Java version:
export PATH=$PATH:/usr/local/jdk/bin/
cd /right/folder/
nohup strace -v java TestRunInfinit &

Last time I ran them they stopped after ~2370 seconds (~40 minutes).

In Ubuntu this happens in both the 32bit and 64bit versions. The processes just stop without any kind of warning. Since this happens in Fedora 8 also, this could be a hardware, kernel thing..? Under what circumstances does Linux kill processes without nay warning?

Please help, I've wasted many many days with this. I just want to continue my research.

Thank you,
Ovi

---

### Post by PmDematagoda on 2008-07-01
When a process gets suddenly killed, post the outputs of:-
```
dmesg | tail -25
```
```
cat /var/log/messages
```
and
```
cat /var/log/kern.log
```

---

### Post by PmDematagoda on 2008-07-01
If you are running Ubuntu Server with no GUI, then print the output to a file by appending it with a > and the file name.

---

### Post by zmarty on 2008-07-01
dmesg | tail -25
```

[17179587.272000] Adding 1951888k swap on /dev/disk/by-uuid/562aaee0-6449-4cf1-b680-bed36102b69d.  Priority:-1 extents:1 across:1951888k
[17179587.344000] EXT3 FS on sda1, internal journal
[17179587.596000] kjournald starting.  Commit interval 5 seconds
[17179587.608000] EXT3 FS on sda3, internal journal
[17179587.608000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.952000] ACPI: Power Button (FF) [PWRF]
[17179588.952000] ACPI: Sleep Button (CM) [SLPB]
[17179589.072000] ibm_acpi: ec object not found
[17179589.116000] pcc_acpi: loading...
[17179606.948000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179607.020000] Netfilter messages via NETLINK v0.30.
[17179607.024000] ip_conntrack version 2.4 (8120 buckets, 64960 max) - 224 bytes per conntrack
[17179607.672000] eth2: link up, 100Mbps, full-duplex, lpa 0xC5E1
[17255108.088000] tun: Universal TUN/TAP device driver, 1.6
[17255108.088000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[17779106.260000] ata1: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
[17779106.260000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17779106.260000] ata1: error=0x84 { DriveStatusError BadCRC }
[18082745.740000] ata1: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
[18082745.740000] ata1: status=0x51 { DriveReady SeekComplete Error }
[18082745.740000] ata1: error=0x84 { DriveStatusError BadCRC }
[20148191.672000] ata1: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
[20148191.672000] ata1: status=0x51 { DriveReady SeekComplete Error }
[20148191.672000] ata1: error=0x84 { DriveStatusError BadCRC }
[23120199.340000] NET: Registered protocol family 17

```

cat /var/log/messages
```

[...]
Jul  1 06:26:44 stan syslogd 1.4.1#18ubuntu6: restart.
Jul  1 06:46:44 stan -- MARK --
Jul  1 07:06:44 stan -- MARK --
Jul  1 07:26:44 stan -- MARK --
Jul  1 07:46:45 stan -- MARK --
Jul  1 08:06:45 stan -- MARK --
Jul  1 08:26:45 stan -- MARK --
Jul  1 08:46:45 stan -- MARK --
Jul  1 09:06:45 stan -- MARK --
Jul  1 09:26:45 stan -- MARK --
Jul  1 09:46:46 stan -- MARK --
Jul  1 10:06:46 stan -- MARK --
Jul  1 10:26:46 stan -- MARK --
Jul  1 10:46:46 stan -- MARK --
Jul  1 10:53:49 stan kernel: [23120199.340000] NET: Registered protocol family 17
Jul  1 11:06:46 stan -- MARK --
Jul  1 11:26:46 stan -- MARK --
Jul  1 11:46:47 stan -- MARK --
Jul  1 12:06:47 stan -- MARK --
Jul  1 12:26:47 stan -- MARK --
Jul  1 12:46:47 stan -- MARK --
Jul  1 13:06:47 stan -- MARK --
Jul  1 13:26:47 stan -- MARK --
Jul  1 13:46:48 stan -- MARK --
Jul  1 14:06:48 stan -- MARK --
Jul  1 14:26:48 stan -- MARK --
Jul  1 14:46:48 stan -- MARK --
Jul  1 15:06:48 stan -- MARK --
Jul  1 15:26:48 stan -- MARK --
Jul  1 15:46:48 stan -- MARK --
Jul  1 16:06:49 stan -- MARK --

```

cat /var/log/kern.log
```

Jul  1 10:53:49 stan kernel: [23120199.340000] NET: Registered protocol family 17

```

---

### Post by zmarty on 2008-08-04
It's still happening unfortunately. Currently running 8.04. It was fine for a few reboots after I installed it, now it started acting up again. Does anybody have any idea how to fix this?

Thanks,
Ovi

---

### Post by cariboo on 2008-08-04
I was just looking at the output of dmesg you posted, it looks like you have a hrd drive problem:

> ata1: status=0x51 { DriveReady SeekComplete Error }
[17779106.260000] ata1: error=0x84 { DriveStatusError BadCRC }
[18082745.740000] ata1: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
[18082745.740000] ata1: status=0x51 { DriveReady SeekComplete Error }
[18082745.740000] ata1: error=0x84 { DriveStatusError BadCRC }
[20148191.672000] ata1: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
[20148191.672000] ata1: status=0x51 { DriveReady SeekComplete Error }
[20148191.672000] ata1: error=0x84 { DriveStatusError BadCRC }

You can see the DriveRead SeekComplete error and DriveStatusError BadCRC. If I was you I would back up your data ASAP, then go to your hard drives manufacturers web site and download their diagnostic tools and run them to see if the hard drive is failing or if the software can repair the errors.

Jim

---

### Post by zmarty on 2008-08-04
I ran a few tests (bonnie++, smartctl stuff). I can't get it to generate the same error again. SMART says everything is fine. As far as I know that error only appeared in the past.

---

### Post by zmarty on 2008-08-04
Several tests later...

The problem is actually that Ubuntu keeps rebooting (in 8.04 anyway):

root@pinkunicorn:~# cat /var/log/messages | grep -i "inspecting /boot"
Aug  3 07:04:34 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 08:05:09 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 09:09:24 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 10:06:20 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 11:06:56 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 12:07:32 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 13:08:08 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 14:09:00 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 15:09:20 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 16:09:55 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 17:10:30 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 18:11:06 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 19:11:42 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 20:12:18 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 21:12:54 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 22:13:29 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  3 23:14:06 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  4 00:14:42 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  4 01:15:16 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  4 02:15:52 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  4 03:16:29 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  4 04:17:33 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server
Aug  4 05:17:41 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server

It seems that the machine resets every one hour and ~30 seconds. The only thing that comes to mind is the crond. I stopped it, we'll see how it goes. But still, why oh why?

dmesg has no other userful information, but I can attach the file if needed.

---

### Post by zmarty on 2008-08-04
crond is not the problem, after shutting it down it still restarted a few minutes later:

Aug  4 07:18:53 pinkunicorn kernel: Inspecting /boot/System.map-2.6.24-16-server

---

