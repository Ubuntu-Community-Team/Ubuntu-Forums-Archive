---
title: "Server keeps locking up, usb drive issues?"
date: 2008-06-28
forum: Server Platforms
---

### Post by phillips321 on 2008-06-28
Hi guys,

I have a laptop running ubuntu 8.04 server. It's used for file sharing on my LAN and for a few websites.

For some reason it keeps looking up.

Here is a section of /var/log/messages, the computer locked up at June 27 12:30ish:

```

................................Code Start..............................
Jun 27 12:17:55 LinuxServer kernel: [  215.148082] Initializing USB Mass Storage driver...
Jun 27 12:17:55 LinuxServer kernel: [  215.153328] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 27 12:17:55 LinuxServer kernel: [  215.157832] usbcore: registered new interface driver usb-storage
Jun 27 12:17:55 LinuxServer kernel: [  215.157848] USB Mass Storage support registered.
Jun 27 12:18:00 LinuxServer kernel: [  220.155380] scsi 2:0:0:0: Direct-Access     ST350083 0AS                   PQ: 0 ANSI: 2
Jun 27 12:18:00 LinuxServer kernel: [  220.178078] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jun 27 12:18:00 LinuxServer kernel: [  220.180942] sd 2:0:0:0: [sdb] Write Protect is off
Jun 27 12:18:00 LinuxServer kernel: [  220.203532] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jun 27 12:18:00 LinuxServer kernel: [  220.206395] sd 2:0:0:0: [sdb] Write Protect is off
Jun 27 12:18:00 LinuxServer kernel: [  220.206473]  sdb: sdb1
Jun 27 12:18:00 LinuxServer kernel: [  220.226664] sd 2:0:0:0: [sdb] Attached SCSI disk
Jun 27 12:18:00 LinuxServer kernel: [  220.226760] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun 27 12:18:51 LinuxServer kernel: [  271.410649] kjournald starting.  Commit interval 5 seconds
Jun 27 12:18:51 LinuxServer kernel: [  271.411166] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Jun 27 12:18:51 LinuxServer kernel: [  271.418801] EXT3 FS on sdb1, internal journal
Jun 27 12:18:51 LinuxServer kernel: [  271.418813] EXT3-fs: recovery complete.
Jun 27 12:18:51 LinuxServer kernel: [  271.420115] EXT3-fs: mounted filesystem with ordered data mode.
Jun 27 12:27:17 LinuxServer kernel: [  776.162553] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 27 12:55:05 LinuxServer -- MARK --
Jun 27 13:15:05 LinuxServer -- MARK --
Jun 27 13:35:05 LinuxServer -- MARK --
Jun 27 13:55:05 LinuxServer -- MARK --
Jun 27 14:15:05 LinuxServer -- MARK --
Jun 27 14:35:05 LinuxServer -- MARK --
Jun 27 14:55:05 LinuxServer -- MARK --
Jun 27 15:15:05 LinuxServer -- MARK --
Jun 27 15:35:05 LinuxServer -- MARK --
Jun 27 15:55:05 LinuxServer -- MARK --
Jun 27 16:15:05 LinuxServer -- MARK --
Jun 27 16:35:05 LinuxServer -- MARK --
Jun 27 16:55:05 LinuxServer -- MARK --
Jun 27 17:15:05 LinuxServer -- MARK --
Jun 27 17:35:05 LinuxServer -- MARK --
Jun 27 17:55:05 LinuxServer -- MARK --
Jun 27 18:15:05 LinuxServer -- MARK --
Jun 27 18:35:05 LinuxServer -- MARK --
Jun 27 18:55:05 LinuxServer -- MARK --
Jun 27 19:15:05 LinuxServer -- MARK --
Jun 27 19:35:05 LinuxServer -- MARK --
Jun 27 19:55:05 LinuxServer -- MARK --
Jun 27 20:15:05 LinuxServer -- MARK --
Jun 27 20:35:05 LinuxServer -- MARK --
Jun 27 20:55:05 LinuxServer -- MARK --
Jun 27 21:15:05 LinuxServer -- MARK --
Jun 27 21:35:05 LinuxServer -- MARK --
Jun 27 21:55:05 LinuxServer -- MARK --
Jun 27 22:15:05 LinuxServer -- MARK --
Jun 27 22:35:05 LinuxServer -- MARK --
Jun 27 22:55:05 LinuxServer -- MARK --
Jun 27 23:15:05 LinuxServer -- MARK --
Jun 27 23:35:05 LinuxServer -- MARK --
Jun 28 12:13:23 LinuxServer syslogd 1.5.0#1ubuntu1: restart.
................................Code End................................

```

I think it has something to do with my external USB 500GB hard drive (ext3 formatted).

The machine was up for over 12hours before it locked up this time.

It doesn't respond to pings, or anything, a hard reboot is needed.

Cheers guys

---

### Post by be1952 on 2008-06-28
try turning acpi off and apm on
 append="acpi=off apm=on"

---

