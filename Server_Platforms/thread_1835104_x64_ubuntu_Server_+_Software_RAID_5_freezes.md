---
title: "x64 ubuntu Server + Software RAID 5 freezes"
date: 2011-08-28
forum: Server Platforms
---

### Post by MarcLocchi on 2011-08-28
Hi all,
I am new to Linux / Ubuntu, and I must say I am really impressed with what the community has done with this OS. Awesome!
 
But I am running into an issue which is causing my installation to be unusable. I am setting up a media server for home, which will serve up files to my media center (Win 7 Home Prem) box. I set up the server all OK, but then when I copy files onto it, it freezes and requires a reboot. 
 
Here's what I have:
 
Ubuntu x64 server 11.04
Gnome GUI
Mobo: Gigabyte GA-X58A-UD3R (rev 2.0, latest GA BIOS - FF version) 
RAM: 3x 2GB 1666MHz 
HDDs: 
- 1x 320GB Hitachi partitioned as 10GB for /BOOT, 13GB for swap and rest for OS, attached to the Marvell 9128 SATA controller, running in ACHI mode
- 6x 2TB Caviar Green WD drives attached to ICH10R Intel SATA controller running in ACHI mode
- 2x 2TB Caviar Green WD drives attached to GYGABYTE SATA2 controller running in ACHI mode
VIDEO: nVidia Gforce 8800 GTS 512MB RAM
 
I have then set up the 8x 2TB HDDs as one software RAID 5 array, formatted with ETX4 file system. 2 days later, it completes resynching OK and lets me mount it. I can test its performance and blows me away with speeds of up to 585MB/s read, plenty for a media server!
 
I then set up  my share folders and update SAMBA.CONF to allow access from my Windows PCs where the media data resides at the moment. The copy process starts and I can see folders and files created on the SAMBA share OK, but at a random time the server freezes. I have to turn it off then on again, which triggers the 2 days resynching... 
 
I have tried first the desktop Ubuntu (more by mistake than by plan!) and had the same issue.
 
Questions I have are:
1. Can I set up software RAID 5 where the devices are across two separate controllers?
2. Should I use a different file system (than EXT4) for this large, 14TB volume?
3. Is there a flaw in my set up (i.e.: mobo not stable with Ubuntu for example)
 
I am at a loss here and anything I do to try to fix the issue requires 2 days resynching before finding out it does not work!
 
All suggestions welcome to this newbie!
 
Thanks
Marc

---

### Post by bakegoodz on 2011-08-28
How is the server freezing? Can you ssh in or change terminals on the system? Or is just your transfer freezing? Linux is typically very robust, it very rare to have kernel panic and have to hard reset the system without it being a hardware problem. So I suspect a hardware problem if you have to hard reset. With a software raid the last thing you want to do is hard reset. When a drive gets interrupted while writing it will often write a sector part-way, then the drive thinks that sector is bad. When the raid sees a bad sector it will often rebuild the raid array. Raid5 is processor intensive, it will be fast for a short period of time (or fairly small writes) until it gets bogged down in parity calculations and disk synchronizations. Hardware raid is better but has the same kinds of slow downs. I found that Raid 5 wasn't the right fit for my large file and performance needs. I sacrificed disk space for speed and when with Raid 10. Another thing I found is that found modern disk remap sectors frequently, especially ones over 1TB in size. I recommend Enterprise or Raid edition drives for any raid array or Raid rebuilding will be a too common occurrence.

---

### Post by MarcLocchi on 2011-08-28
Hi bakegoodz, thanks for the reply!
 
The server is freezing at hardware level and the machine becomes unusable, only a power reset is then possible.
 
I tried Linux for the first time after using Windows for the last so many years. Prior to Ubuntu I had Win 2008 Server 2008 R1 installed in the box with SW RAID 5, which worked fine other than it had troubles streaming movies from the RAID array. I found it would glitch at random times and thus the movie would skip / buffer. Having said this, the Server worked pretty reliably and did not freeze.
 
2008 server therefore was not meeting requirements of serving the movies without glitches, and thus I tried Ubuntu.
 
Ubuntu seems to be so much faster and more robust, but I have the freezing problem. I had this with the desktop version first and the server now. Same symptom, hw freezed when copying files to it.
 
I understand the drives are not the best for RAID but I inherited these from some work I had done in the past and was hoping to use them for a redundant media library. It would 
be a shame to not be able to get this working with so much storage at hand.
 
So not sure why with Win 2008 it would work (and not freeze) but not supply constant data feed (which says to me it is not a HW fault issue necessarily), while with Ubuntu it just freezes the whole box.
 
Any more help is really appreciated!
 
PS: all I want is a reliable file server, redundat storage so I can have peace of mind on my data. Thanks!

---

### Post by fatbotgw on 2011-08-28
To answer your questions:

1. Can I set up software RAID 5 where the devices are across two separate controllers?

Yes, this should not be a problem.  I did this in my server before a bunch of my drives died.  I used the onboard SATA and an add-on PCI SATA card.

2. Should I use a different file system (than EXT4) for this large, 14TB volume?

You can if you want to, I used XFS when I was running a RAID.

3. Is there a flaw in my set up (i.e.: mobo not stable with Ubuntu for example)

I don't know...  A google search could tell you more than I can.


As for the lock-ups, what have you done for trouble shooting?  Try starting out with a 3-disk RAID 5 array.  If it doesn't lock up, add another disk to the array.  Continue adding drives until it locks up.  If it locks up with only 3 disks, it's probably something other than the amount of disks.  From there I would look at the ports and which controller they're on...it could be a controller issue.

I'm not an expert at this, but hopefully it helps.

---

### Post by rubylaser on 2011-08-29
Have you looked in your log files for interesting messages ?

```
cat /var/log/syslog
cat /var/log/kern.log
dmesg
```

You didn't really mention how you setup your array.  I'm assuming just mdadm, but did you use LVM on top of mdadm, or just mdadm by itself? Also, with large multi disk arrays, I'd REALLY suggest using at a minimum RAID6, for your data's increased safety.

And to answer your questions...

1. Yes, multiple controllers are perfectly fine with mdadm
2. Currently EXT4 maximum file system size is 16 TB, so if you plan to expand in the future, you don't have much room to grow.  I used XFS in the past on top of mdadm, but had corruption issues that eventually moved me away from that filesystem.
3. Your motherboard is fine for Linux, but you'll want to check the log files to see if your having hardware problems.

---

### Post by MarcLocchi on 2011-08-29
Thank you fatbogw, rubylaser!

As mentioned in my original post I am new to Ubuntu so all your suggestions have helped me learn a lot!

One thinng I forgot to mention is I have 2 NICs in the box, the PCIe one (onboard) and a PCI add in card in slot. I disconnected the PCI add in and tried the suggestion from fatbotgw.

I created a RAID 5 3 disk array (4TB partition, all drives on the one ICH10R controller) and started the file copy. It worked for a longer period this time (1 hour +, rather than a few minutes) before freezing, so that was a step in the right direction. Shame the result was the same, only way to access the server was cold boot.

To answer questions from rubylaser, I created the array at installation for the server SW, I did not open a terminal and do it command line via mdadm. I assume it is mdadm in the background setting up array during install (am I right?). to create the 4TB array I used Disk Utility tool (GUI). I created it with EXT4 FS, one partition. I did not use LVM at all.

Also, here are the contents of the logs per rubylaser request (I hope I load these OK!):
SYSLOG:
```
Aug 30 09:34:07 LSERVER kernel: [    6.328443]  md127: unknown partition table
Aug 30 09:34:07 LSERVER kernel: [    6.725527] EXT4-fs (sdg6): INFO: recovery required on readonly filesystem
Aug 30 09:34:07 LSERVER kernel: [    6.725530] EXT4-fs (sdg6): write access will be enabled during recovery
Aug 30 09:34:07 LSERVER kernel: [    8.553960] EXT4-fs (sdg6): orphan cleanup on readonly fs
Aug 30 09:34:07 LSERVER kernel: [    8.553967] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 8651182
Aug 30 09:34:07 LSERVER kernel: [    8.554010] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 8651123
Aug 30 09:34:07 LSERVER kernel: [    8.554033] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996738
Aug 30 09:34:07 LSERVER kernel: [    8.554043] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996737
Aug 30 09:34:07 LSERVER kernel: [    8.554054] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996736
Aug 30 09:34:07 LSERVER kernel: [    8.554062] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996722
Aug 30 09:34:07 LSERVER kernel: [    8.554071] EXT4-fs (sdg6): 6 orphan inodes deleted
Aug 30 09:34:07 LSERVER kernel: [    8.554072] EXT4-fs (sdg6): recovery complete
Aug 30 09:34:07 LSERVER kernel: [    8.699880] EXT4-fs (sdg6): mounted filesystem with ordered data mode. Opts: (null)
Aug 30 09:34:07 LSERVER kernel: [   17.286584] <30>udev[429]: starting version 167
Aug 30 09:34:07 LSERVER kernel: [   17.295331] lp: driver loaded but no devices found
Aug 30 09:34:07 LSERVER kernel: [   17.327189] EDAC MC: Ver: 2.1.0 Jul 29 2011
Aug 30 09:34:07 LSERVER kernel: [   17.330073] EDAC i7core: Driver loaded.
Aug 30 09:34:07 LSERVER kernel: [   17.356863] [drm] Initialized drm 1.1.0 20060810
Aug 30 09:34:07 LSERVER kernel: [   17.408297] <30>udev[445]: renamed network interface eth0 to PCIe-NIC
Aug 30 09:34:07 LSERVER kernel: [   17.420120] nouveau 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [   17.420124] nouveau 0000:03:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [   17.422830] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x092000a2)
Aug 30 09:34:07 LSERVER kernel: [   17.426644] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
Aug 30 09:34:07 LSERVER kernel: [   17.455328] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 30 09:34:07 LSERVER kernel: [   17.455372] HDA Intel 0000:00:1b.0: irq 55 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [   17.455392] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [   17.479597] [drm] nouveau 0000:03:00.0: ... appears to be valid
Aug 30 09:34:07 LSERVER kernel: [   17.479601] [drm] nouveau 0000:03:00.0: BIT BIOS found
Aug 30 09:34:07 LSERVER kernel: [   17.479603] [drm] nouveau 0000:03:00.0: Bios version 62.92.16.00
Aug 30 09:34:07 LSERVER kernel: [   17.479605] [drm] nouveau 0000:03:00.0: TMDS table version 2.0
Aug 30 09:34:07 LSERVER kernel: [   17.479607] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
Aug 30 09:34:07 LSERVER kernel: [   17.479609] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 00000028
Aug 30 09:34:07 LSERVER kernel: [   17.479611] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01000302 00000030
Aug 30 09:34:07 LSERVER kernel: [   17.479612] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 04011310 00000028
Aug 30 09:34:07 LSERVER kernel: [   17.479614] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 02011312 00000030
Aug 30 09:34:07 LSERVER kernel: [   17.479615] [drm] nouveau 0000:03:00.0: Raw DCB entry 4: 010223f1 00c0c080
Aug 30 09:34:07 LSERVER kernel: [   17.479617] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 14 4
Aug 30 09:34:07 LSERVER kernel: [   17.479619] [drm] nouveau 0000:03:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Aug 30 09:34:07 LSERVER kernel: [   17.479621] [drm] nouveau 0000:03:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
Aug 30 09:34:07 LSERVER kernel: [   17.479623] [drm] nouveau 0000:03:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
Aug 30 09:34:07 LSERVER kernel: [   17.479624] [drm] nouveau 0000:03:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
Aug 30 09:34:07 LSERVER kernel: [   17.479626] [drm] nouveau 0000:03:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
Aug 30 09:34:07 LSERVER kernel: [   17.479629] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xC0C3
Aug 30 09:34:07 LSERVER kernel: [   17.537416] <30>udev[446]: renamed network interface eth1 to PCI-NIC
Aug 30 09:34:07 LSERVER kernel: [   17.574175] hda_codec: ALC889: BIOS auto-probing.
Aug 30 09:34:07 LSERVER kernel: [   17.577015] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xC47D
Aug 30 09:34:07 LSERVER kernel: [   17.582521] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Aug 30 09:34:07 LSERVER kernel: [   17.608256] Adding 12694524k swap on /dev/sdg5.  Priority:-1 extents:1 across:12694524k 
Aug 30 09:34:07 LSERVER kernel: [   17.618694] type=1400 audit(1314660846.110:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=681 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.618703] type=1400 audit(1314660846.110:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.618786] type=1400 audit(1314660846.110:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=758 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619207] type=1400 audit(1314660846.110:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=681 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619217] type=1400 audit(1314660846.110:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619298] type=1400 audit(1314660846.110:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=758 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619533] type=1400 audit(1314660846.110:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=681 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619544] type=1400 audit(1314660846.110:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619626] type=1400 audit(1314660846.110:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=758 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.626760] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xD1EB
Aug 30 09:34:07 LSERVER kernel: [   17.626771] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xD2EA
Aug 30 09:34:07 LSERVER kernel: [   17.656790] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xD51A
Aug 30 09:34:07 LSERVER kernel: [   17.656793] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xD57F
Aug 30 09:34:07 LSERVER kernel: [   17.686907] [drm] nouveau 0000:03:00.0: 0xD57F: Condition still not met after 20ms, skipping following opcodes
Aug 30 09:34:07 LSERVER kernel: [   17.733091] adt7475 0-002e: ADT7473 device, revision 1
Aug 30 09:34:07 LSERVER kernel: [   17.742923] [drm] nouveau 0000:03:00.0: Detected monitoring device: adt7473
Aug 30 09:34:07 LSERVER kernel: [   17.742926] [drm] nouveau 0000:03:00.0: 1 available performance level(s)
Aug 30 09:34:07 LSERVER kernel: [   17.742930] [drm] nouveau 0000:03:00.0: 3: memory 1000MHz core 700MHz shader 1700MHz voltage 1150mV fanspeed 100%
Aug 30 09:34:07 LSERVER kernel: [   17.742942] [drm] nouveau 0000:03:00.0: c: memory 499MHz core 399MHz shader 810MHz voltage 1150mV
Aug 30 09:34:07 LSERVER kernel: [   17.743078] [TTM] Zone  kernel: Available graphics memory: 3061308 kiB.
Aug 30 09:34:07 LSERVER kernel: [   17.743080] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
Aug 30 09:34:07 LSERVER kernel: [   17.743081] [TTM] Initializing pool allocator.
Aug 30 09:34:07 LSERVER kernel: [   17.743095] [drm] nouveau 0000:03:00.0: Detected 512MiB VRAM
Aug 30 09:34:07 LSERVER kernel: [   17.743112] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Aug 30 09:34:07 LSERVER kernel: [   17.788520] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
Aug 30 09:34:07 LSERVER kernel: [   17.872034] [drm] nouveau 0000:03:00.0: DCB encoder 1 unknown
Aug 30 09:34:07 LSERVER kernel: [   17.872037] [drm] nouveau 0000:03:00.0: TV-1 has no encoders, removing
Aug 30 09:34:07 LSERVER kernel: [   17.873459] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 30 09:34:07 LSERVER kernel: [   17.873461] [drm] No driver support for vblank timestamp query.
Aug 30 09:34:07 LSERVER kernel: [   18.053586] [drm] nouveau 0000:03:00.0: allocated 1440x900 fb: 0x60000000, bo ffff88018f85d800
Aug 30 09:34:07 LSERVER kernel: [   18.053642] fbcon: nouveaufb (fb0) is primary device
Aug 30 09:34:07 LSERVER kernel: [   18.053747] Console: switching to colour frame buffer device 180x56
Aug 30 09:34:07 LSERVER kernel: [   18.055097] fb0: nouveaufb frame buffer device
Aug 30 09:34:07 LSERVER kernel: [   18.055098] drm: registered panic notifier
Aug 30 09:34:07 LSERVER kernel: [   18.055102] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
Aug 30 09:34:07 LSERVER kernel: [   18.314118] EXT4-fs (sdg6): re-mounted. Opts: errors=remount-ro
Aug 30 09:34:07 LSERVER kernel: [   18.623352] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
Aug 30 09:34:07 LSERVER kernel: [   18.704015] type=1400 audit(1314660847.190:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1015 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER rpc.statd[1039]: Version 1.2.2 starting
Aug 30 09:34:07 LSERVER rpc.statd[1039]: Flags: 
Aug 30 09:34:07 LSERVER automount[1043]: syntax error in nsswitch config near [ syntax error ]
Aug 30 09:34:07 LSERVER init: apport pre-start process (1074) terminated with status 1
Aug 30 09:34:07 LSERVER cron[1082]: (CRON) INFO (pidfile fd = 3)
Aug 30 09:34:07 LSERVER init: apport post-stop process (1098) terminated with status 1
Aug 30 09:34:07 LSERVER anacron[1111]: Anacron 2.3 started on 2011-08-30
Aug 30 09:34:07 LSERVER cron[1120]: (CRON) STARTUP (fork ok)
Aug 30 09:34:07 LSERVER cron[1120]: (CRON) INFO (Running @reboot jobs)
Aug 30 09:34:07 LSERVER mdadm[1161]: DeviceDisappeared event detected on md device /dev/md/0
Aug 30 09:34:07 LSERVER mdadm[1161]: NewArray event detected on md device /dev/md127
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Found user 'avahi' (UID 104) and group 'avahi' (GID 114).
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Successfully dropped root privileges.
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: avahi-daemon 0.6.30 starting up.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> NetworkManager (version 0.8.3.998) is starting...
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 30 09:34:07 LSERVER anacron[1111]: Normal exit (0 jobs run)
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Successfully called chroot().
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Successfully dropped remaining capabilities.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> trying to start the modem manager...
Aug 30 09:34:07 LSERVER gdm-binary[1182]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  ModemManager (version 0.4) starting...
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Option
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Ericsson MBM
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin AnyData
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Longcheer
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin SimTech
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Huawei
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin X22X
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Novatel
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin MotoC
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Gobi
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Nokia
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Linktop
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Generic
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Sierra
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin Option High-Speed
Aug 30 09:34:07 LSERVER modem-manager[1214]: <info>  Loaded plugin ZTE
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Loading service file /services/udisks.service.
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Network interface enumeration completed.
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Server startup complete. Host name is LSERVER.local. Local service cookie is 2474206188.
Aug 30 09:34:07 LSERVER avahi-daemon[1187]: Service "LSERVER" (/services/udisks.service) successfully established.
Aug 30 09:34:07 LSERVER polkitd[1223]: started daemon version 0.101 using authority implementation `local' version `0.101'
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: init!
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: update_system_hostname
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: adding eth0 to iface_connections
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: adding iface eth0 to well_known_interfaces
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPluginIfupdown: guessed connection type (bond0) = 802-3-ethernet
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:bond0, type:802-3-ethernet, id:Ifupdown (bond0), uuid: cf3cb1bb-e060-1c88-9b60-ea19f208811a
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: adding bond0 to iface_connections
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: adding iface bond0 to well_known_interfaces
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: autoconnect
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: autoconnect
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPluginIfupdown: management mode: unmanaged
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0/net/PCIe-NIC, iface: PCIe-NIC)
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0/net/PCIe-NIC, iface: PCIe-NIC): no ifupdown configuration found.
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:08:00.0/net/PCI-NIC, iface: PCI-NIC)
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:08:00.0/net/PCI-NIC, iface: PCI-NIC): no ifupdown configuration found.
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: end _init.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    Ifupdown: get unmanaged devices count: 0
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: (12242272) ... get_connections.
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    SCPlugin-Ifupdown: (12242272) ... get_connections (managed=false): return empty list.
Aug 30 09:34:07 LSERVER gdm-simple-slave[1315]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 30 09:34:07 LSERVER gdm-binary[1182]: WARNING: Unable to find users: no seat-id found
Aug 30 09:34:07 LSERVER NetworkManager[1193]:    Ifupdown: get unmanaged devices count: 0
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> Networking is enabled by state file
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): carrier is OFF
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): now managed
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): device state change: 1 -> 2 (reason 2)
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): bringing up device.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): preparing device.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): deactivating device (reason: 2).
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): carrier is OFF
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): new Ethernet device (driver: 'r8169' ifindex: 3)
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): now managed
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): device state change: 1 -> 2 (reason 2)
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): bringing up device.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): preparing device.
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> (PCI-NIC): deactivating device (reason: 2).
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> modem-manager is now available
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 30 09:34:07 LSERVER NetworkManager[1193]: <info> Trying to start the supplicant...
Aug 30 09:34:07 LSERVER kernel: [   19.026922] r8169 0000:07:00.0: PCIe-NIC: link down
Aug 30 09:34:07 LSERVER kernel: [   19.026927] r8169 0000:07:00.0: PCIe-NIC: link down
Aug 30 09:34:07 LSERVER kernel: [   19.027467] ADDRCONF(NETDEV_UP): PCIe-NIC: link is not ready
Aug 30 09:34:07 LSERVER kernel: [   19.029066] r8169 0000:08:00.0: PCI-NIC: link down
Aug 30 09:34:07 LSERVER kernel: [   19.029609] ADDRCONF(NETDEV_UP): PCI-NIC: link is not ready
Aug 30 09:34:09 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): carrier now ON (device state 2)
Aug 30 09:34:09 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): device state change: 2 -> 3 (reason 40)
Aug 30 09:34:09 LSERVER kernel: [   20.919431] r8169 0000:07:00.0: PCIe-NIC: link up
Aug 30 09:34:09 LSERVER kernel: [   20.920137] ADDRCONF(NETDEV_CHANGE): PCIe-NIC: link becomes ready
Aug 30 09:34:09 LSERVER gdm-session-worker[1378]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 30 09:34:10 LSERVER anacron[1470]: Anacron 2.3 started on 2011-08-30
Aug 30 09:34:10 LSERVER anacron[1470]: Normal exit (0 jobs run)
Aug 30 09:34:10 LSERVER gdm-simple-greeter[1377]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Aug 30 09:34:10 LSERVER gdm-simple-greeter[1377]: WARNING: Unable to load CK history: no seat-id found
Aug 30 09:34:11 LSERVER avahi-daemon[1187]: Joining mDNS multicast group on interface PCIe-NIC.IPv6 with address fe80::6ef0:49ff:feed:e25.
Aug 30 09:34:11 LSERVER avahi-daemon[1187]: New relevant interface PCIe-NIC.IPv6 for mDNS.
Aug 30 09:34:11 LSERVER avahi-daemon[1187]: Registering new address record for fe80::6ef0:49ff:feed:e25 on PCIe-NIC.*.
Aug 30 09:34:11 LSERVER kernel: [   23.105678] EXT4-fs (sdg6): re-mounted. Opts: errors=remount-ro,commit=0
Aug 30 09:34:11 LSERVER kernel: [   23.189534] EXT4-fs (sdg1): re-mounted. Opts: commit=0
Aug 30 09:34:12 LSERVER gdm-session-worker[1378]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 30 09:34:20 LSERVER kernel: [   31.826783] PCIe-NIC: no IPv6 routers present
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Successfully called chroot.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Successfully dropped privileges.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Successfully limited resources.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Running.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Watchdog thread running.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Canary thread running.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Successfully made thread 1594 of process 1594 (n/a) owned by '1000' high priority at nice level -11.
Aug 30 09:34:20 LSERVER rtkit-daemon[1596]: Supervising 1 threads of 1 processes of 1 users.
Aug 30 09:34:22 LSERVER rtkit-daemon[1596]: Successfully made thread 1620 of process 1594 (n/a) owned by '1000' RT at priority 5.
Aug 30 09:34:22 LSERVER rtkit-daemon[1596]: Supervising 2 threads of 1 processes of 1 users.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) starting connection 'Auto Ethernet'
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): device state change: 3 -> 4 (reason 0)
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 1 of 5 (Device Prepare) started...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 1 of 5 (Device Prepare) complete.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 2 of 5 (Device Configure) starting...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): device state change: 4 -> 5 (reason 0)
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 2 of 5 (Device Configure) successful.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 2 of 5 (Device Configure) complete.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 3 of 5 (IP Configure Start) started...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): device state change: 5 -> 7 (reason 0)
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> dhclient started with pid 1623
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 09:34:22 LSERVER dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 30 09:34:22 LSERVER dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 30 09:34:22 LSERVER dhclient: All rights reserved.
Aug 30 09:34:22 LSERVER dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 30 09:34:22 LSERVER dhclient: 
Aug 30 09:34:22 LSERVER rtkit-daemon[1596]: Successfully made thread 1625 of process 1594 (n/a) owned by '1000' RT at priority 5.
Aug 30 09:34:22 LSERVER rtkit-daemon[1596]: Supervising 3 threads of 1 processes of 1 users.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): DHCPv4 state changed nbi -> preinit
Aug 30 09:34:22 LSERVER dhclient: Listening on LPF/PCIe-NIC/6c:f0:49:ed:0e:25
Aug 30 09:34:22 LSERVER dhclient: Sending on   LPF/PCIe-NIC/6c:f0:49:ed:0e:25
Aug 30 09:34:22 LSERVER dhclient: Sending on   Socket/fallback
Aug 30 09:34:22 LSERVER dhclient: DHCPREQUEST of 192.168.0.186 on PCIe-NIC to 255.255.255.255 port 67
Aug 30 09:34:22 LSERVER dhclient: DHCPACK of 192.168.0.186 from 192.168.0.1
Aug 30 09:34:22 LSERVER dhclient: bound to 192.168.0.186 -- renewal in 2147483648 seconds.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): DHCPv4 state changed preinit -> reboot
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 4 of 5 (IP4 Configure Get) started...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info>   address 192.168.0.186
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info>   prefix 24 (255.255.255.0)
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info>   gateway 192.168.0.1
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info>   nameserver '192.168.0.1'
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info>   domain name 'BigPond'
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Scheduling stage 5
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Done scheduling stage 5
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 30 09:34:22 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 5 of 5 (IP Configure Commit) started...
Aug 30 09:34:22 LSERVER avahi-daemon[1187]: Joining mDNS multicast group on interface PCIe-NIC.IPv4 with address 192.168.0.186.
Aug 30 09:34:22 LSERVER avahi-daemon[1187]: New relevant interface PCIe-NIC.IPv4 for mDNS.
Aug 30 09:34:22 LSERVER avahi-daemon[1187]: Registering new address record for 192.168.0.186 on PCIe-NIC.IPv4.
Aug 30 09:34:23 LSERVER NetworkManager[1193]: <info> (PCIe-NIC): device state change: 7 -> 8 (reason 0)
Aug 30 09:34:23 LSERVER NetworkManager[1193]: <info> Policy set 'Auto Ethernet' (PCIe-NIC) as default for IPv4 routing and DNS.
Aug 30 09:34:23 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) successful, device activated.
Aug 30 09:34:23 LSERVER NetworkManager[1193]: <info> Activation (PCIe-NIC) Stage 5 of 5 (IP Configure Commit) complete.
Aug 30 09:34:38 LSERVER ntpdate[1700]: step time server 91.189.94.4 offset 2.789796 sec
Aug 30 09:34:53 LSERVER mdadm[1161]: RebuildStarted event detected on md device /dev/md127
Aug 30 09:34:53 LSERVER kernel: [   61.899992] md: resync of RAID array md127
Aug 30 09:34:53 LSERVER kernel: [   61.899995] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Aug 30 09:34:53 LSERVER kernel: [   61.899996] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Aug 30 09:34:53 LSERVER kernel: [   61.900001] md: using 128k window, over a total of 1953510400 blocks.
Aug 30 09:34:55 LSERVER kernel: [   63.765719] EXT4-fs (md127): recovery complete
Aug 30 09:34:55 LSERVER kernel: [   63.765919] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
Aug 30 09:35:07 LSERVER kernel: [   75.857353] md: md127: resync done.
Aug 30 09:35:07 LSERVER kernel: [   75.989382] RAID conf printout:
Aug 30 09:35:07 LSERVER kernel: [   75.989386]  --- level:5 rd:3 wd:3
Aug 30 09:35:07 LSERVER kernel: [   75.989389]  disk 0, o:1, dev:sdd1
Aug 30 09:35:07 LSERVER kernel: [   75.989391]  disk 1, o:1, dev:sde1
Aug 30 09:35:07 LSERVER kernel: [   75.989393]  disk 2, o:1, dev:sdf1
Aug 30 09:35:07 LSERVER mdadm[1161]: RebuildFinished event detected on md device /dev/md127, component device  mismatches found: 1664

```

KERN.LOG:
```
Aug 30 09:34:07 LSERVER kernel: [    1.721611] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    1.721658] pcieport 0000:00:1c.4: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.721691] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    1.721752] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 30 09:34:07 LSERVER kernel: [    1.721767] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 30 09:34:07 LSERVER kernel: [    1.721800] intel_idle: MWAIT substates: 0x1120
Aug 30 09:34:07 LSERVER kernel: [    1.721810] intel_idle: v0.4 model 0x1A
Aug 30 09:34:07 LSERVER kernel: [    1.721811] intel_idle: lapic_timer_reliable_states 0x2
Aug 30 09:34:07 LSERVER kernel: [    1.721916] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Aug 30 09:34:07 LSERVER kernel: [    1.721919] ACPI: Power Button [PWRB]
Aug 30 09:34:07 LSERVER kernel: [    1.721955] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug 30 09:34:07 LSERVER kernel: [    1.721958] ACPI: Power Button [PWRF]
Aug 30 09:34:07 LSERVER kernel: [    1.722094] ACPI: acpi_idle yielding to intel_idle
Aug 30 09:34:07 LSERVER kernel: [    1.724063] ERST: Table is not found!
Aug 30 09:34:07 LSERVER kernel: [    1.724123] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 30 09:34:07 LSERVER kernel: [    1.949400] Linux agpgart interface v0.103
Aug 30 09:34:07 LSERVER kernel: [    1.950224] brd: module loaded
Aug 30 09:34:07 LSERVER kernel: [    1.950597] loop: module loaded
Aug 30 09:34:07 LSERVER kernel: [    1.950657] i2c-core: driver [adp5520] using legacy suspend method
Aug 30 09:34:07 LSERVER kernel: [    1.950659] i2c-core: driver [adp5520] using legacy resume method
Aug 30 09:34:07 LSERVER kernel: [    1.950767] pata_acpi 0000:05:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Aug 30 09:34:07 LSERVER kernel: [    1.950788] pata_acpi 0000:05:00.1: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.950800] pata_acpi 0000:05:00.1: PCI INT B disabled
Aug 30 09:34:07 LSERVER kernel: [    1.950810] pata_acpi 0000:06:00.1: enabling device (0000 -> 0001)
Aug 30 09:34:07 LSERVER kernel: [    1.950814] pata_acpi 0000:06:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    1.950829] pata_acpi 0000:06:00.1: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.950837] pata_acpi 0000:06:00.1: PCI INT B disabled
Aug 30 09:34:07 LSERVER kernel: [    1.951033] Fixed MDIO Bus: probed
Aug 30 09:34:07 LSERVER kernel: [    1.951052] PPP generic driver version 2.4.2
Aug 30 09:34:07 LSERVER kernel: [    1.951080] tun: Universal TUN/TAP device driver, 1.6
Aug 30 09:34:07 LSERVER kernel: [    1.951081] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 30 09:34:07 LSERVER kernel: [    1.951141] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 30 09:34:07 LSERVER kernel: [    1.951153] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 30 09:34:07 LSERVER kernel: [    1.951172] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.951174] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    1.951205] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Aug 30 09:34:07 LSERVER kernel: [    1.951248] ehci_hcd 0000:00:1a.7: debug port 1
Aug 30 09:34:07 LSERVER kernel: [    1.955140] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Aug 30 09:34:07 LSERVER kernel: [    1.955153] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbffe000
Aug 30 09:34:07 LSERVER kernel: [    1.977879] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Aug 30 09:34:07 LSERVER kernel: [    1.977967] hub 1-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    1.977970] hub 1-0:1.0: 6 ports detected
Aug 30 09:34:07 LSERVER kernel: [    1.978038] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 30 09:34:07 LSERVER kernel: [    1.978049] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.978051] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    1.978081] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Aug 30 09:34:07 LSERVER kernel: [    1.978123] ehci_hcd 0000:00:1d.7: debug port 1
Aug 30 09:34:07 LSERVER kernel: [    1.982010] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Aug 30 09:34:07 LSERVER kernel: [    1.982020] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffd000
Aug 30 09:34:07 LSERVER kernel: [    1.997867] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 30 09:34:07 LSERVER kernel: [    1.997943] hub 2-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    1.997946] hub 2-0:1.0: 6 ports detected
Aug 30 09:34:07 LSERVER kernel: [    1.998003] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 30 09:34:07 LSERVER kernel: [    1.998012] uhci_hcd: USB Universal Host Controller Interface driver
Aug 30 09:34:07 LSERVER kernel: [    1.998049] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    1.998054] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.998057] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    1.998083] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Aug 30 09:34:07 LSERVER kernel: [    1.998127] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
Aug 30 09:34:07 LSERVER kernel: [    1.998214] hub 3-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    1.998217] hub 3-0:1.0: 2 ports detected
Aug 30 09:34:07 LSERVER kernel: [    1.998270] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Aug 30 09:34:07 LSERVER kernel: [    1.998275] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.998277] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    1.998303] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Aug 30 09:34:07 LSERVER kernel: [    1.998347] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
Aug 30 09:34:07 LSERVER kernel: [    1.998433] hub 4-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    1.998435] hub 4-0:1.0: 2 ports detected
Aug 30 09:34:07 LSERVER kernel: [    1.998485] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 30 09:34:07 LSERVER kernel: [    1.998490] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    1.998492] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    1.998520] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Aug 30 09:34:07 LSERVER kernel: [    2.007888] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
Aug 30 09:34:07 LSERVER kernel: [    2.007975] hub 5-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    2.007977] hub 5-0:1.0: 2 ports detected
Aug 30 09:34:07 LSERVER kernel: [    2.008030] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 30 09:34:07 LSERVER kernel: [    2.008034] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.008037] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    2.008062] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Aug 30 09:34:07 LSERVER kernel: [    2.008098] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
Aug 30 09:34:07 LSERVER kernel: [    2.008186] hub 6-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    2.008189] hub 6-0:1.0: 2 ports detected
Aug 30 09:34:07 LSERVER kernel: [    2.008241] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 30 09:34:07 LSERVER kernel: [    2.008245] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.008247] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    2.008274] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Aug 30 09:34:07 LSERVER kernel: [    2.008318] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
Aug 30 09:34:07 LSERVER kernel: [    2.008407] hub 7-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    2.008409] hub 7-0:1.0: 2 ports detected
Aug 30 09:34:07 LSERVER kernel: [    2.008461] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 30 09:34:07 LSERVER kernel: [    2.008465] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.008468] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    2.008493] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Aug 30 09:34:07 LSERVER kernel: [    2.008529] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
Aug 30 09:34:07 LSERVER kernel: [    2.008616] hub 8-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    2.008619] hub 8-0:1.0: 2 ports detected
Aug 30 09:34:07 LSERVER kernel: [    2.008700] i8042: PNP: No PS/2 controller found. Probing ports directly.
Aug 30 09:34:07 LSERVER kernel: [    2.009049] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 30 09:34:07 LSERVER kernel: [    2.009054] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 30 09:34:07 LSERVER kernel: [    2.009108] mousedev: PS/2 mouse device common for all mice
Aug 30 09:34:07 LSERVER kernel: [    2.009180] rtc_cmos 00:04: RTC can wake from S4
Aug 30 09:34:07 LSERVER kernel: [    2.009262] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Aug 30 09:34:07 LSERVER kernel: [    2.009285] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Aug 30 09:34:07 LSERVER kernel: [    2.009357] device-mapper: uevent: version 1.0.3
Aug 30 09:34:07 LSERVER kernel: [    2.009415] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Aug 30 09:34:07 LSERVER kernel: [    2.009459] device-mapper: multipath: version 1.2.0 loaded
Aug 30 09:34:07 LSERVER kernel: [    2.009461] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 30 09:34:07 LSERVER kernel: [    2.009670] cpuidle: using governor ladder
Aug 30 09:34:07 LSERVER kernel: [    2.009879] cpuidle: using governor menu
Aug 30 09:34:07 LSERVER kernel: [    2.010059] TCP cubic registered
Aug 30 09:34:07 LSERVER kernel: [    2.010145] NET: Registered protocol family 10
Aug 30 09:34:07 LSERVER kernel: [    2.010540] NET: Registered protocol family 17
Aug 30 09:34:07 LSERVER kernel: [    2.010550] Registering the dns_resolver key type
Aug 30 09:34:07 LSERVER kernel: [    2.012304] PM: Hibernation image not present or could not be loaded.
Aug 30 09:34:07 LSERVER kernel: [    2.012310] registered taskstats version 1
Aug 30 09:34:07 LSERVER kernel: [    2.012713]   Magic number: 7:662:606
Aug 30 09:34:07 LSERVER kernel: [    2.012885] rtc_cmos 00:04: setting system clock to 2011-08-29 23:33:50 UTC (1314660830)
Aug 30 09:34:07 LSERVER kernel: [    2.012888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 30 09:34:07 LSERVER kernel: [    2.012890] EDD information not available.
Aug 30 09:34:07 LSERVER kernel: [    2.014803] Freeing unused kernel memory: 880k freed
Aug 30 09:34:07 LSERVER kernel: [    2.014911] Write protecting the kernel read-only data: 10240k
Aug 30 09:34:07 LSERVER kernel: [    2.016325] Freeing unused kernel memory: 100k freed
Aug 30 09:34:07 LSERVER kernel: [    2.020927] Freeing unused kernel memory: 1416k freed
Aug 30 09:34:07 LSERVER kernel: [    2.036732] <30>udev[87]: starting version 167
Aug 30 09:34:07 LSERVER kernel: [    2.040234] md: linear personality registered for level -1
Aug 30 09:34:07 LSERVER kernel: [    2.044646] md: multipath personality registered for level -4
Aug 30 09:34:07 LSERVER kernel: [    2.047103] md: raid0 personality registered for level 0
Aug 30 09:34:07 LSERVER kernel: [    2.050095] md: raid1 personality registered for level 1
Aug 30 09:34:07 LSERVER kernel: [    2.051742] async_tx: api initialized (async)
Aug 30 09:34:07 LSERVER kernel: [    2.064628] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    2.064650] xhci_hcd 0000:02:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.064655] xhci_hcd 0000:02:00.0: xHCI Host Controller
Aug 30 09:34:07 LSERVER kernel: [    2.064721] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
Aug 30 09:34:07 LSERVER kernel: [    2.075084] ahci 0000:00:1f.2: version 3.0
Aug 30 09:34:07 LSERVER kernel: [    2.075095] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 30 09:34:07 LSERVER kernel: [    2.075135] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    2.075166] ahci: SSS flag set, parallel bus scan disabled
Aug 30 09:34:07 LSERVER kernel: [    2.075206] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Aug 30 09:34:07 LSERVER kernel: [    2.075210] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems 
Aug 30 09:34:07 LSERVER kernel: [    2.075214] ahci 0000:00:1f.2: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.084370] firewire_ohci 0000:08:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 30 09:34:07 LSERVER kernel: [    2.085596] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug 30 09:34:07 LSERVER kernel: [    2.085608] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    2.085638] r8169 0000:07:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.085642] r8169 0000:07:00.0: (unregistered net_device): unknown MAC, using family default
Aug 30 09:34:07 LSERVER kernel: [    2.085690] r8169 0000:07:00.0: irq 45 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    2.086042] r8169 0000:07:00.0: eth0: RTL8168b/8111b at 0xffffc9000579c000, 6c:f0:49:ed:0e:25, XID 0c100000 IRQ 45
Aug 30 09:34:07 LSERVER kernel: [    2.087375] pata_jmicron 0000:05:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Aug 30 09:34:07 LSERVER kernel: [    2.087400] pata_jmicron 0000:05:00.1: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.087718] scsi0 : pata_jmicron
Aug 30 09:34:07 LSERVER kernel: [    2.087849] scsi1 : pata_jmicron
Aug 30 09:34:07 LSERVER kernel: [    2.088469] ata1: PATA max UDMA/100 cmd 0xaf00 ctl 0xae00 bmdma 0xab00 irq 18
Aug 30 09:34:07 LSERVER kernel: [    2.088472] ata2: PATA max UDMA/100 cmd 0xad00 ctl 0xac00 bmdma 0xab08 irq 18
Aug 30 09:34:07 LSERVER kernel: [    2.088492] pata_jmicron 0000:06:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    2.088521] pata_jmicron 0000:06:00.1: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.088835] scsi2 : pata_jmicron
Aug 30 09:34:07 LSERVER kernel: [    2.088908] scsi3 : pata_jmicron
Aug 30 09:34:07 LSERVER kernel: [    2.089434] ata3: PATA max UDMA/100 cmd 0xef00 ctl 0xee00 bmdma 0xeb00 irq 16
Aug 30 09:34:07 LSERVER kernel: [    2.089436] ata4: PATA max UDMA/100 cmd 0xed00 ctl 0xec00 bmdma 0xeb08 irq 16
Aug 30 09:34:07 LSERVER kernel: [    2.137977] firewire_ohci: Added fw-ohci device 0000:08:06.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Aug 30 09:34:07 LSERVER kernel: [    2.208395] scsi4 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.208613] scsi5 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.208831] scsi6 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.209049] scsi7 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.209267] scsi8 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.209484] scsi9 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.209612] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 44
Aug 30 09:34:07 LSERVER kernel: [    2.209615] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 44
Aug 30 09:34:07 LSERVER kernel: [    2.209617] ata7: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 44
Aug 30 09:34:07 LSERVER kernel: [    2.209619] ata8: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 44
Aug 30 09:34:07 LSERVER kernel: [    2.209621] ata9: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 44
Aug 30 09:34:07 LSERVER kernel: [    2.209623] ata10: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 44
Aug 30 09:34:07 LSERVER kernel: [    2.209640] ahci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    2.209677] ahci 0000:01:00.0: irq 46 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    2.209710] ahci 0000:01:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
Aug 30 09:34:07 LSERVER kernel: [    2.209712] ahci 0000:01:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
Aug 30 09:34:07 LSERVER kernel: [    2.209715] ahci 0000:01:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.209719] ahci 0000:01:00.0: port 0 is not capable of FBS
Aug 30 09:34:07 LSERVER kernel: [    2.209747] ahci 0000:01:00.0: port 1 is not capable of FBS
Aug 30 09:34:07 LSERVER kernel: [    2.209958] scsi10 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.210053] scsi11 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.210098] ata11: SATA max UDMA/133 abar m2048@0xfb9ff000 port 0xfb9ff100 irq 46
Aug 30 09:34:07 LSERVER kernel: [    2.210101] ata12: SATA max UDMA/133 abar m2048@0xfb9ff000 port 0xfb9ff180 irq 46
Aug 30 09:34:07 LSERVER kernel: [    2.210118] ahci 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 30 09:34:07 LSERVER kernel: [    2.217830] raid6: int64x1   2597 MB/s
Aug 30 09:34:07 LSERVER kernel: [    2.237871] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Aug 30 09:34:07 LSERVER kernel: [    2.237874] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Aug 30 09:34:07 LSERVER kernel: [    2.237879] ahci 0000:05:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.238226] scsi12 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.238444] scsi13 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.238520] ata13: SATA max UDMA/133 abar m8192@0xfb8fe000 port 0xfb8fe100 irq 17
Aug 30 09:34:07 LSERVER kernel: [    2.238523] ata14: SATA max UDMA/133 abar m8192@0xfb8fe000 port 0xfb8fe180 irq 17
Aug 30 09:34:07 LSERVER kernel: [    2.238539] ahci 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 30 09:34:07 LSERVER kernel: [    2.267845] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Aug 30 09:34:07 LSERVER kernel: [    2.267848] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Aug 30 09:34:07 LSERVER kernel: [    2.267854] ahci 0000:06:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [    2.268202] scsi14 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.268424] scsi15 : ahci
Aug 30 09:34:07 LSERVER kernel: [    2.268500] ata15: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 19
Aug 30 09:34:07 LSERVER kernel: [    2.268504] ata16: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 19
Aug 30 09:34:07 LSERVER kernel: [    2.298332] ata1.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
Aug 30 09:34:07 LSERVER kernel: [    2.298336] ata1.01: ATAPI: _NEC DVD+/-RW ND-3450A, 103C, max UDMA/33
Aug 30 09:34:07 LSERVER kernel: [    2.358295] ata1.00: configured for UDMA/33
Aug 30 09:34:07 LSERVER kernel: [    2.387758] raid6: int64x2   3434 MB/s
Aug 30 09:34:07 LSERVER kernel: [    2.408300] ata1.01: configured for UDMA/33
Aug 30 09:34:07 LSERVER kernel: [    2.415572] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    2.419534] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Aug 30 09:34:07 LSERVER kernel: [    2.419537] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 30 09:34:07 LSERVER kernel: [    2.419618] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 30 09:34:07 LSERVER kernel: [    2.419665] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 30 09:34:07 LSERVER kernel: [    2.422259] scsi 0:0:1:0: CD-ROM            _NEC     DVD+-RW ND-3450A 103C PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    2.423714] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Aug 30 09:34:07 LSERVER kernel: [    2.423780] sr 0:0:1:0: Attached scsi CD-ROM sr1
Aug 30 09:34:07 LSERVER kernel: [    2.423817] sr 0:0:1:0: Attached scsi generic sg1 type 5
Aug 30 09:34:07 LSERVER kernel: [    2.557615] raid6: int64x4   2314 MB/s
Aug 30 09:34:07 LSERVER kernel: [    2.557637] ata11: SATA link down (SStatus 0 SControl 330)
Aug 30 09:34:07 LSERVER kernel: [    2.607594] ata15: SATA link down (SStatus 0 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    2.617591] ata16: SATA link down (SStatus 0 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    2.627583] usb 3-1: new low speed USB device using uhci_hcd and address 2
Aug 30 09:34:07 LSERVER kernel: [    2.717500] Refined TSC clocksource calibration: 2664.769 MHz.
Aug 30 09:34:07 LSERVER kernel: [    2.717505] Switching to clocksource tsc
Aug 30 09:34:07 LSERVER kernel: [    2.727357] raid6: int64x8   2376 MB/s
Aug 30 09:34:07 LSERVER kernel: [    2.897237] raid6: sse2x1    4930 MB/s
Aug 30 09:34:07 LSERVER kernel: [    3.067117] raid6: sse2x2    6080 MB/s
Aug 30 09:34:07 LSERVER kernel: [    3.236999] raid6: sse2x4    5856 MB/s
Aug 30 09:34:07 LSERVER kernel: [    3.237001] raid6: using algorithm sse2x2 (6080 MB/s)
Aug 30 09:34:07 LSERVER kernel: [    3.237019] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
Aug 30 09:34:07 LSERVER kernel: [    3.237032] ata13: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    3.237036] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    3.237063] ata14: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    3.237066] firewire_core: created device fw0: GUID 00e9d3d5006cf049, S400
Aug 30 09:34:07 LSERVER kernel: [    3.248984] ata13.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.248990] ata13.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    3.249003] ata14.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.249008] ata14.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    3.253674] ata14.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.256057] ata13.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.263321] ata5.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.263326] ata5.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    3.269014] ata5.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.269176] scsi 4:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    3.269302] sd 4:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    3.269329] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 30 09:34:07 LSERVER kernel: [    3.269352] sd 4:0:0:0: [sda] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    3.269355] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    3.269378] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    3.274232]  sda:
Aug 30 09:34:07 LSERVER kernel: [    3.274809] sd 4:0:0:0: [sda] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    3.277417] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfbbfe000
Aug 30 09:34:07 LSERVER kernel: [    3.277460] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277464] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277468] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277472] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277477] xhci_hcd 0000:02:00.0: irq 51 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277481] xhci_hcd 0000:02:00.0: irq 52 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277485] xhci_hcd 0000:02:00.0: irq 53 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.277489] xhci_hcd 0000:02:00.0: irq 54 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [    3.280773] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
Aug 30 09:34:07 LSERVER kernel: [    3.280842] xHCI xhci_add_endpoint called for root hub
Aug 30 09:34:07 LSERVER kernel: [    3.280844] xHCI xhci_check_bandwidth called for root hub
Aug 30 09:34:07 LSERVER kernel: [    3.280873] hub 9-0:1.0: USB hub found
Aug 30 09:34:07 LSERVER kernel: [    3.280878] hub 9-0:1.0: 4 ports detected
Aug 30 09:34:07 LSERVER kernel: [    3.282980] ata12.00: HPA detected: current 625140335, native 625142448
Aug 30 09:34:07 LSERVER kernel: [    3.282987] ata12.00: ATA-7: ST3320620AS, 3.AAJ, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.282990] ata12.00: 625140335 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 30 09:34:07 LSERVER kernel: [    3.287195] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug 30 09:34:07 LSERVER kernel: [    3.287213] r8169 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    3.287337] r8169 0000:08:00.0: (unregistered net_device): no PCI Express capability
Aug 30 09:34:07 LSERVER kernel: [    3.287345] r8169 0000:08:00.0: (unregistered net_device): unknown MAC, using family default
Aug 30 09:34:07 LSERVER kernel: [    3.287791] r8169 0000:08:00.0: eth1: RTL8169 at 0xffffc900057b0000, 94:0c:6d:80:9c:91, XID 10000000 IRQ 16
Aug 30 09:34:07 LSERVER kernel: [    3.341238] ata12.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.606903] input:   USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Aug 30 09:34:07 LSERVER kernel: [    3.606996] generic-usb 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1a.0-1/input0
Aug 30 09:34:07 LSERVER kernel: [    3.693099] input:   USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input3
Aug 30 09:34:07 LSERVER kernel: [    3.693196] generic-usb 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1a.0-1/input1
Aug 30 09:34:07 LSERVER kernel: [    3.693209] usbcore: registered new interface driver usbhid
Aug 30 09:34:07 LSERVER kernel: [    3.693211] usbhid: USB HID core driver
Aug 30 09:34:07 LSERVER kernel: [    3.706715] usb 3-2: new low speed USB device using uhci_hcd and address 3
Aug 30 09:34:07 LSERVER kernel: [    3.816641] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    3.827878] ata6.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.827882] ata6.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    3.833613] ata6.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    3.833730] scsi 5:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    3.833867] sd 5:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    3.833896] sd 5:0:0:0: Attached scsi generic sg3 type 0
Aug 30 09:34:07 LSERVER kernel: [    3.833914] sd 5:0:0:0: [sdb] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    3.833917] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    3.833938] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    3.840497]  sdb:
Aug 30 09:34:07 LSERVER kernel: [    3.841033] sd 5:0:0:0: [sdb] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    3.908990] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
Aug 30 09:34:07 LSERVER kernel: [    3.909098] a4tech 0003:09DA:000A.0003: input,hidraw2: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1a.0-2/input0
Aug 30 09:34:07 LSERVER kernel: [    4.376295] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    4.410444] ata7.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    4.410448] ata7.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    4.415526] ata7.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    4.415679] scsi 6:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    4.415852] sd 6:0:0:0: Attached scsi generic sg4 type 0
Aug 30 09:34:07 LSERVER kernel: [    4.415942] sd 6:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    4.416027] sd 6:0:0:0: [sdc] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    4.416031] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    4.416067] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    4.432477]  sdc:
Aug 30 09:34:07 LSERVER kernel: [    4.433027] sd 6:0:0:0: [sdc] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    4.955883] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    4.972455] ata8.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    4.972459] ata8.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    4.976533] ata8.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    4.976688] scsi 7:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    4.976849] sd 7:0:0:0: Attached scsi generic sg5 type 0
Aug 30 09:34:07 LSERVER kernel: [    4.976962] sd 7:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    4.977100] sd 7:0:0:0: [sdd] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    4.977107] sd 7:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    4.977166] sd 7:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    4.989560]  sdd: sdd1
Aug 30 09:34:07 LSERVER kernel: [    4.990100] sd 7:0:0:0: [sdd] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    5.199719] md: bind<sdd1>
Aug 30 09:34:07 LSERVER kernel: [    5.525475] ata9: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    5.544418] ata9.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    5.544422] ata9.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    5.548526] ata9.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    5.548686] scsi 8:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    5.548850] sd 8:0:0:0: Attached scsi generic sg6 type 0
Aug 30 09:34:07 LSERVER kernel: [    5.548945] sd 8:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    5.549060] sd 8:0:0:0: [sde] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    5.549069] sd 8:0:0:0: [sde] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    5.549109] sd 8:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    5.561617]  sde: sde1
Aug 30 09:34:07 LSERVER kernel: [    5.562149] sd 8:0:0:0: [sde] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    5.775592] md: bind<sde1>
Aug 30 09:34:07 LSERVER kernel: [    6.095021] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 30 09:34:07 LSERVER kernel: [    6.115927] ata10.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    6.115931] ata10.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 30 09:34:07 LSERVER kernel: [    6.121514] ata10.00: configured for UDMA/133
Aug 30 09:34:07 LSERVER kernel: [    6.121670] scsi 9:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    6.121811] sd 9:0:0:0: Attached scsi generic sg7 type 0
Aug 30 09:34:07 LSERVER kernel: [    6.121867] sd 9:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    6.121962] sd 9:0:0:0: [sdf] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    6.121966] sd 9:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    6.122007] sd 9:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    6.122035] scsi 11:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    6.122191] sd 11:0:0:0: Attached scsi generic sg8 type 0
Aug 30 09:34:07 LSERVER kernel: [    6.122257] sd 11:0:0:0: [sdg] 625140335 512-byte logical blocks: (320 GB/298 GiB)
Aug 30 09:34:07 LSERVER kernel: [    6.122306] scsi 12:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    6.122360] sd 11:0:0:0: [sdg] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    6.122364] sd 11:0:0:0: [sdg] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    6.122404] sd 11:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    6.122437] sd 12:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    6.122483] sd 12:0:0:0: [sdh] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    6.122485] sd 12:0:0:0: [sdh] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    6.122499] sd 12:0:0:0: Attached scsi generic sg9 type 0
Aug 30 09:34:07 LSERVER kernel: [    6.122506] sd 12:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    6.122663] scsi 13:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
Aug 30 09:34:07 LSERVER kernel: [    6.122780] sd 13:0:0:0: [sdi] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Aug 30 09:34:07 LSERVER kernel: [    6.122831] sd 13:0:0:0: [sdi] Write Protect is off
Aug 30 09:34:07 LSERVER kernel: [    6.122833] sd 13:0:0:0: Attached scsi generic sg10 type 0
Aug 30 09:34:07 LSERVER kernel: [    6.122836] sd 13:0:0:0: [sdi] Mode Sense: 00 3a 00 00
Aug 30 09:34:07 LSERVER kernel: [    6.122859] sd 13:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:34:07 LSERVER kernel: [    6.126071]  sdh:
Aug 30 09:34:07 LSERVER kernel: [    6.126675] sd 12:0:0:0: [sdh] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    6.126851]  sdf: sdf1
Aug 30 09:34:07 LSERVER kernel: [    6.127273] sd 9:0:0:0: [sdf] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    6.136402]  sdi:
Aug 30 09:34:07 LSERVER kernel: [    6.136720] sd 13:0:0:0: [sdi] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    6.160580]  sdg: sdg1 sdg2 < sdg5 sdg6 >
Aug 30 09:34:07 LSERVER kernel: [    6.161028] sd 11:0:0:0: [sdg] Attached SCSI disk
Aug 30 09:34:07 LSERVER kernel: [    6.162646] xor: automatically using best checksumming function: generic_sse
Aug 30 09:34:07 LSERVER kernel: [    6.204885]    generic_sse: 10921.200 MB/sec
Aug 30 09:34:07 LSERVER kernel: [    6.204887] xor: using function: generic_sse (10921.200 MB/sec)
Aug 30 09:34:07 LSERVER kernel: [    6.209622] md: raid6 personality registered for level 6
Aug 30 09:34:07 LSERVER kernel: [    6.209623] md: raid5 personality registered for level 5
Aug 30 09:34:07 LSERVER kernel: [    6.209625] md: raid4 personality registered for level 4
Aug 30 09:34:07 LSERVER kernel: [    6.214362] md: raid10 personality registered for level 10
Aug 30 09:34:07 LSERVER kernel: [    6.256663] md: bind<sdf1>
Aug 30 09:34:07 LSERVER kernel: [    6.258383] bio: create slab <bio-1> at 1
Aug 30 09:34:07 LSERVER kernel: [    6.258388] md/raid:md127: not clean -- starting background reconstruction
Aug 30 09:34:07 LSERVER kernel: [    6.258397] md/raid:md127: device sdf1 operational as raid disk 2
Aug 30 09:34:07 LSERVER kernel: [    6.258398] md/raid:md127: device sde1 operational as raid disk 1
Aug 30 09:34:07 LSERVER kernel: [    6.258400] md/raid:md127: device sdd1 operational as raid disk 0
Aug 30 09:34:07 LSERVER kernel: [    6.258659] md/raid:md127: allocated 3230kB
Aug 30 09:34:07 LSERVER kernel: [    6.258793] md/raid:md127: raid level 5 active with 3 out of 3 devices, algorithm 2
Aug 30 09:34:07 LSERVER kernel: [    6.258794] RAID conf printout:
Aug 30 09:34:07 LSERVER kernel: [    6.258795]  --- level:5 rd:3 wd:3
Aug 30 09:34:07 LSERVER kernel: [    6.258796]  disk 0, o:1, dev:sdd1
Aug 30 09:34:07 LSERVER kernel: [    6.258798]  disk 1, o:1, dev:sde1
Aug 30 09:34:07 LSERVER kernel: [    6.258799]  disk 2, o:1, dev:sdf1
Aug 30 09:34:07 LSERVER kernel: [    6.258894] created bitmap (15 pages) for device md127
Aug 30 09:34:07 LSERVER kernel: [    6.259205] md127: bitmap initialized from disk: read 1/1 pages, set 6 bits
Aug 30 09:34:07 LSERVER kernel: [    6.327125] md127: detected capacity change from 0 to 4000789299200
Aug 30 09:34:07 LSERVER kernel: [    6.328443]  md127: unknown partition table
Aug 30 09:34:07 LSERVER kernel: [    6.725527] EXT4-fs (sdg6): INFO: recovery required on readonly filesystem
Aug 30 09:34:07 LSERVER kernel: [    6.725530] EXT4-fs (sdg6): write access will be enabled during recovery
Aug 30 09:34:07 LSERVER kernel: [    8.553960] EXT4-fs (sdg6): orphan cleanup on readonly fs
Aug 30 09:34:07 LSERVER kernel: [    8.553967] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 8651182
Aug 30 09:34:07 LSERVER kernel: [    8.554010] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 8651123
Aug 30 09:34:07 LSERVER kernel: [    8.554033] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996738
Aug 30 09:34:07 LSERVER kernel: [    8.554043] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996737
Aug 30 09:34:07 LSERVER kernel: [    8.554054] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996736
Aug 30 09:34:07 LSERVER kernel: [    8.554062] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996722
Aug 30 09:34:07 LSERVER kernel: [    8.554071] EXT4-fs (sdg6): 6 orphan inodes deleted
Aug 30 09:34:07 LSERVER kernel: [    8.554072] EXT4-fs (sdg6): recovery complete
Aug 30 09:34:07 LSERVER kernel: [    8.699880] EXT4-fs (sdg6): mounted filesystem with ordered data mode. Opts: (null)
Aug 30 09:34:07 LSERVER kernel: [   17.286584] <30>udev[429]: starting version 167
Aug 30 09:34:07 LSERVER kernel: [   17.295331] lp: driver loaded but no devices found
Aug 30 09:34:07 LSERVER kernel: [   17.327189] EDAC MC: Ver: 2.1.0 Jul 29 2011
Aug 30 09:34:07 LSERVER kernel: [   17.330073] EDAC i7core: Driver loaded.
Aug 30 09:34:07 LSERVER kernel: [   17.356863] [drm] Initialized drm 1.1.0 20060810
Aug 30 09:34:07 LSERVER kernel: [   17.408297] <30>udev[445]: renamed network interface eth0 to PCIe-NIC
Aug 30 09:34:07 LSERVER kernel: [   17.420120] nouveau 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 30 09:34:07 LSERVER kernel: [   17.420124] nouveau 0000:03:00.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [   17.422830] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x092000a2)
Aug 30 09:34:07 LSERVER kernel: [   17.426644] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
Aug 30 09:34:07 LSERVER kernel: [   17.455328] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 30 09:34:07 LSERVER kernel: [   17.455372] HDA Intel 0000:00:1b.0: irq 55 for MSI/MSI-X
Aug 30 09:34:07 LSERVER kernel: [   17.455392] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 30 09:34:07 LSERVER kernel: [   17.479597] [drm] nouveau 0000:03:00.0: ... appears to be valid
Aug 30 09:34:07 LSERVER kernel: [   17.479601] [drm] nouveau 0000:03:00.0: BIT BIOS found
Aug 30 09:34:07 LSERVER kernel: [   17.479603] [drm] nouveau 0000:03:00.0: Bios version 62.92.16.00
Aug 30 09:34:07 LSERVER kernel: [   17.479605] [drm] nouveau 0000:03:00.0: TMDS table version 2.0
Aug 30 09:34:07 LSERVER kernel: [   17.479607] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
Aug 30 09:34:07 LSERVER kernel: [   17.479609] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 00000028
Aug 30 09:34:07 LSERVER kernel: [   17.479611] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01000302 00000030
Aug 30 09:34:07 LSERVER kernel: [   17.479612] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 04011310 00000028
Aug 30 09:34:07 LSERVER kernel: [   17.479614] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 02011312 00000030
Aug 30 09:34:07 LSERVER kernel: [   17.479615] [drm] nouveau 0000:03:00.0: Raw DCB entry 4: 010223f1 00c0c080
Aug 30 09:34:07 LSERVER kernel: [   17.479617] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 14 4
Aug 30 09:34:07 LSERVER kernel: [   17.479619] [drm] nouveau 0000:03:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Aug 30 09:34:07 LSERVER kernel: [   17.479621] [drm] nouveau 0000:03:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
Aug 30 09:34:07 LSERVER kernel: [   17.479623] [drm] nouveau 0000:03:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
Aug 30 09:34:07 LSERVER kernel: [   17.479624] [drm] nouveau 0000:03:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
Aug 30 09:34:07 LSERVER kernel: [   17.479626] [drm] nouveau 0000:03:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
Aug 30 09:34:07 LSERVER kernel: [   17.479629] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xC0C3
Aug 30 09:34:07 LSERVER kernel: [   17.537416] <30>udev[446]: renamed network interface eth1 to PCI-NIC
Aug 30 09:34:07 LSERVER kernel: [   17.574175] hda_codec: ALC889: BIOS auto-probing.
Aug 30 09:34:07 LSERVER kernel: [   17.577015] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xC47D
Aug 30 09:34:07 LSERVER kernel: [   17.582521] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Aug 30 09:34:07 LSERVER kernel: [   17.608256] Adding 12694524k swap on /dev/sdg5.  Priority:-1 extents:1 across:12694524k 
Aug 30 09:34:07 LSERVER kernel: [   17.618694] type=1400 audit(1314660846.110:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=681 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.618703] type=1400 audit(1314660846.110:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.618786] type=1400 audit(1314660846.110:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=758 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619207] type=1400 audit(1314660846.110:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=681 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619217] type=1400 audit(1314660846.110:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619298] type=1400 audit(1314660846.110:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=758 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619533] type=1400 audit(1314660846.110:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=681 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619544] type=1400 audit(1314660846.110:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.619626] type=1400 audit(1314660846.110:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=758 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   17.626760] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xD1EB
Aug 30 09:34:07 LSERVER kernel: [   17.626771] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xD2EA
Aug 30 09:34:07 LSERVER kernel: [   17.656790] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xD51A
Aug 30 09:34:07 LSERVER kernel: [   17.656793] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xD57F
Aug 30 09:34:07 LSERVER kernel: [   17.686907] [drm] nouveau 0000:03:00.0: 0xD57F: Condition still not met after 20ms, skipping following opcodes
Aug 30 09:34:07 LSERVER kernel: [   17.733091] adt7475 0-002e: ADT7473 device, revision 1
Aug 30 09:34:07 LSERVER kernel: [   17.742923] [drm] nouveau 0000:03:00.0: Detected monitoring device: adt7473
Aug 30 09:34:07 LSERVER kernel: [   17.742926] [drm] nouveau 0000:03:00.0: 1 available performance level(s)
Aug 30 09:34:07 LSERVER kernel: [   17.742930] [drm] nouveau 0000:03:00.0: 3: memory 1000MHz core 700MHz shader 1700MHz voltage 1150mV fanspeed 100%
Aug 30 09:34:07 LSERVER kernel: [   17.742942] [drm] nouveau 0000:03:00.0: c: memory 499MHz core 399MHz shader 810MHz voltage 1150mV
Aug 30 09:34:07 LSERVER kernel: [   17.743078] [TTM] Zone  kernel: Available graphics memory: 3061308 kiB.
Aug 30 09:34:07 LSERVER kernel: [   17.743080] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
Aug 30 09:34:07 LSERVER kernel: [   17.743081] [TTM] Initializing pool allocator.
Aug 30 09:34:07 LSERVER kernel: [   17.743095] [drm] nouveau 0000:03:00.0: Detected 512MiB VRAM
Aug 30 09:34:07 LSERVER kernel: [   17.743112] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Aug 30 09:34:07 LSERVER kernel: [   17.788520] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
Aug 30 09:34:07 LSERVER kernel: [   17.872034] [drm] nouveau 0000:03:00.0: DCB encoder 1 unknown
Aug 30 09:34:07 LSERVER kernel: [   17.872037] [drm] nouveau 0000:03:00.0: TV-1 has no encoders, removing
Aug 30 09:34:07 LSERVER kernel: [   17.873459] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 30 09:34:07 LSERVER kernel: [   17.873461] [drm] No driver support for vblank timestamp query.
Aug 30 09:34:07 LSERVER kernel: [   18.053586] [drm] nouveau 0000:03:00.0: allocated 1440x900 fb: 0x60000000, bo ffff88018f85d800
Aug 30 09:34:07 LSERVER kernel: [   18.053642] fbcon: nouveaufb (fb0) is primary device
Aug 30 09:34:07 LSERVER kernel: [   18.053747] Console: switching to colour frame buffer device 180x56
Aug 30 09:34:07 LSERVER kernel: [   18.055097] fb0: nouveaufb frame buffer device
Aug 30 09:34:07 LSERVER kernel: [   18.055098] drm: registered panic notifier
Aug 30 09:34:07 LSERVER kernel: [   18.055102] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
Aug 30 09:34:07 LSERVER kernel: [   18.314118] EXT4-fs (sdg6): re-mounted. Opts: errors=remount-ro
Aug 30 09:34:07 LSERVER kernel: [   18.623352] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
Aug 30 09:34:07 LSERVER kernel: [   18.704015] type=1400 audit(1314660847.190:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1015 comm="apparmor_parser"
Aug 30 09:34:07 LSERVER kernel: [   19.026922] r8169 0000:07:00.0: PCIe-NIC: link down
Aug 30 09:34:07 LSERVER kernel: [   19.026927] r8169 0000:07:00.0: PCIe-NIC: link down
Aug 30 09:34:07 LSERVER kernel: [   19.027467] ADDRCONF(NETDEV_UP): PCIe-NIC: link is not ready
Aug 30 09:34:07 LSERVER kernel: [   19.029066] r8169 0000:08:00.0: PCI-NIC: link down
Aug 30 09:34:07 LSERVER kernel: [   19.029609] ADDRCONF(NETDEV_UP): PCI-NIC: link is not ready
Aug 30 09:34:09 LSERVER kernel: [   20.919431] r8169 0000:07:00.0: PCIe-NIC: link up
Aug 30 09:34:09 LSERVER kernel: [   20.920137] ADDRCONF(NETDEV_CHANGE): PCIe-NIC: link becomes ready
Aug 30 09:34:11 LSERVER kernel: [   23.105678] EXT4-fs (sdg6): re-mounted. Opts: errors=remount-ro,commit=0
Aug 30 09:34:11 LSERVER kernel: [   23.189534] EXT4-fs (sdg1): re-mounted. Opts: commit=0
Aug 30 09:34:20 LSERVER kernel: [   31.826783] PCIe-NIC: no IPv6 routers present
Aug 30 09:34:53 LSERVER kernel: [   61.899992] md: resync of RAID array md127
Aug 30 09:34:53 LSERVER kernel: [   61.899995] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Aug 30 09:34:53 LSERVER kernel: [   61.899996] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Aug 30 09:34:53 LSERVER kernel: [   61.900001] md: using 128k window, over a total of 1953510400 blocks.
Aug 30 09:34:55 LSERVER kernel: [   63.765719] EXT4-fs (md127): recovery complete
Aug 30 09:34:55 LSERVER kernel: [   63.765919] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
Aug 30 09:35:07 LSERVER kernel: [   75.857353] md: md127: resync done.
Aug 30 09:35:07 LSERVER kernel: [   75.989382] RAID conf printout:
Aug 30 09:35:07 LSERVER kernel: [   75.989386]  --- level:5 rd:3 wd:3
Aug 30 09:35:07 LSERVER kernel: [   75.989389]  disk 0, o:1, dev:sdd1
Aug 30 09:35:07 LSERVER kernel: [   75.989391]  disk 1, o:1, dev:sde1
Aug 30 09:35:07 LSERVER kernel: [   75.989393]  disk 2, o:1, dev:sdf1

```

DMESG:
```
[    1.721196] io scheduler noop registered
[    1.721198] io scheduler deadline registered (default)
[    1.721226] io scheduler cfq registered
[    1.721406] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.721444] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.721494] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.721527] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.721579] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.721611] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    1.721658] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.721691] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    1.721752] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.721767] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.721800] intel_idle: MWAIT substates: 0x1120
[    1.721810] intel_idle: v0.4 model 0x1A
[    1.721811] intel_idle: lapic_timer_reliable_states 0x2
[    1.721916] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.721919] ACPI: Power Button [PWRB]
[    1.721955] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.721958] ACPI: Power Button [PWRF]
[    1.722094] ACPI: acpi_idle yielding to intel_idle
[    1.724063] ERST: Table is not found!
[    1.724123] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.949400] Linux agpgart interface v0.103
[    1.950224] brd: module loaded
[    1.950597] loop: module loaded
[    1.950657] i2c-core: driver [adp5520] using legacy suspend method
[    1.950659] i2c-core: driver [adp5520] using legacy resume method
[    1.950767] pata_acpi 0000:05:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.950788] pata_acpi 0000:05:00.1: setting latency timer to 64
[    1.950800] pata_acpi 0000:05:00.1: PCI INT B disabled
[    1.950810] pata_acpi 0000:06:00.1: enabling device (0000 -> 0001)
[    1.950814] pata_acpi 0000:06:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.950829] pata_acpi 0000:06:00.1: setting latency timer to 64
[    1.950837] pata_acpi 0000:06:00.1: PCI INT B disabled
[    1.951033] Fixed MDIO Bus: probed
[    1.951052] PPP generic driver version 2.4.2
[    1.951080] tun: Universal TUN/TAP device driver, 1.6
[    1.951081] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.951141] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.951153] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.951172] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.951174] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.951205] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.951248] ehci_hcd 0000:00:1a.7: debug port 1
[    1.955140] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.955153] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbffe000
[    1.977879] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.977967] hub 1-0:1.0: USB hub found
[    1.977970] hub 1-0:1.0: 6 ports detected
[    1.978038] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.978049] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.978051] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.978081] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.978123] ehci_hcd 0000:00:1d.7: debug port 1
[    1.982010] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.982020] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffd000
[    1.997867] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.997943] hub 2-0:1.0: USB hub found
[    1.997946] hub 2-0:1.0: 6 ports detected
[    1.998003] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.998012] uhci_hcd: USB Universal Host Controller Interface driver
[    1.998049] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.998054] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.998057] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.998083] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.998127] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    1.998214] hub 3-0:1.0: USB hub found
[    1.998217] hub 3-0:1.0: 2 ports detected
[    1.998270] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.998275] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.998277] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.998303] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.998347] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    1.998433] hub 4-0:1.0: USB hub found
[    1.998435] hub 4-0:1.0: 2 ports detected
[    1.998485] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.998490] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.998492] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.998520] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.007888] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
[    2.007975] hub 5-0:1.0: USB hub found
[    2.007977] hub 5-0:1.0: 2 ports detected
[    2.008030] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.008034] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.008037] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.008062] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.008098] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    2.008186] hub 6-0:1.0: USB hub found
[    2.008189] hub 6-0:1.0: 2 ports detected
[    2.008241] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.008245] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.008247] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.008274] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.008318] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    2.008407] hub 7-0:1.0: USB hub found
[    2.008409] hub 7-0:1.0: 2 ports detected
[    2.008461] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.008465] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.008468] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.008493] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.008529] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    2.008616] hub 8-0:1.0: USB hub found
[    2.008619] hub 8-0:1.0: 2 ports detected
[    2.008700] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.009049] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.009054] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.009108] mousedev: PS/2 mouse device common for all mice
[    2.009180] rtc_cmos 00:04: RTC can wake from S4
[    2.009262] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.009285] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.009357] device-mapper: uevent: version 1.0.3
[    2.009415] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.009459] device-mapper: multipath: version 1.2.0 loaded
[    2.009461] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.009670] cpuidle: using governor ladder
[    2.009879] cpuidle: using governor menu
[    2.010059] TCP cubic registered
[    2.010145] NET: Registered protocol family 10
[    2.010540] NET: Registered protocol family 17
[    2.010550] Registering the dns_resolver key type
[    2.012304] PM: Hibernation image not present or could not be loaded.
[    2.012310] registered taskstats version 1
[    2.012713]   Magic number: 7:662:606
[    2.012885] rtc_cmos 00:04: setting system clock to 2011-08-29 23:33:50 UTC (1314660830)
[    2.012888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.012890] EDD information not available.
[    2.014803] Freeing unused kernel memory: 880k freed
[    2.014911] Write protecting the kernel read-only data: 10240k
[    2.016325] Freeing unused kernel memory: 100k freed
[    2.020927] Freeing unused kernel memory: 1416k freed
[    2.036732] <30>udev[87]: starting version 167
[    2.040234] md: linear personality registered for level -1
[    2.044646] md: multipath personality registered for level -4
[    2.047103] md: raid0 personality registered for level 0
[    2.050095] md: raid1 personality registered for level 1
[    2.051742] async_tx: api initialized (async)
[    2.064628] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.064650] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    2.064655] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.064721] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.075084] ahci 0000:00:1f.2: version 3.0
[    2.075095] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.075135] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    2.075166] ahci: SSS flag set, parallel bus scan disabled
[    2.075206] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    2.075210] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems 
[    2.075214] ahci 0000:00:1f.2: setting latency timer to 64
[    2.084370] firewire_ohci 0000:08:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.085596] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.085608] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.085638] r8169 0000:07:00.0: setting latency timer to 64
[    2.085642] r8169 0000:07:00.0: (unregistered net_device): unknown MAC, using family default
[    2.085690] r8169 0000:07:00.0: irq 45 for MSI/MSI-X
[    2.086042] r8169 0000:07:00.0: eth0: RTL8168b/8111b at 0xffffc9000579c000, 6c:f0:49:ed:0e:25, XID 0c100000 IRQ 45
[    2.087375] pata_jmicron 0000:05:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.087400] pata_jmicron 0000:05:00.1: setting latency timer to 64
[    2.087718] scsi0 : pata_jmicron
[    2.087849] scsi1 : pata_jmicron
[    2.088469] ata1: PATA max UDMA/100 cmd 0xaf00 ctl 0xae00 bmdma 0xab00 irq 18
[    2.088472] ata2: PATA max UDMA/100 cmd 0xad00 ctl 0xac00 bmdma 0xab08 irq 18
[    2.088492] pata_jmicron 0000:06:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    2.088521] pata_jmicron 0000:06:00.1: setting latency timer to 64
[    2.088835] scsi2 : pata_jmicron
[    2.088908] scsi3 : pata_jmicron
[    2.089434] ata3: PATA max UDMA/100 cmd 0xef00 ctl 0xee00 bmdma 0xeb00 irq 16
[    2.089436] ata4: PATA max UDMA/100 cmd 0xed00 ctl 0xec00 bmdma 0xeb08 irq 16
[    2.137977] firewire_ohci: Added fw-ohci device 0000:08:06.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.208395] scsi4 : ahci
[    2.208613] scsi5 : ahci
[    2.208831] scsi6 : ahci
[    2.209049] scsi7 : ahci
[    2.209267] scsi8 : ahci
[    2.209484] scsi9 : ahci
[    2.209612] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 44
[    2.209615] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 44
[    2.209617] ata7: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 44
[    2.209619] ata8: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 44
[    2.209621] ata9: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 44
[    2.209623] ata10: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 44
[    2.209640] ahci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.209677] ahci 0000:01:00.0: irq 46 for MSI/MSI-X
[    2.209710] ahci 0000:01:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    2.209712] ahci 0000:01:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    2.209715] ahci 0000:01:00.0: setting latency timer to 64
[    2.209719] ahci 0000:01:00.0: port 0 is not capable of FBS
[    2.209747] ahci 0000:01:00.0: port 1 is not capable of FBS
[    2.209958] scsi10 : ahci
[    2.210053] scsi11 : ahci
[    2.210098] ata11: SATA max UDMA/133 abar m2048@0xfb9ff000 port 0xfb9ff100 irq 46
[    2.210101] ata12: SATA max UDMA/133 abar m2048@0xfb9ff000 port 0xfb9ff180 irq 46
[    2.210118] ahci 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.217830] raid6: int64x1   2597 MB/s
[    2.237871] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.237874] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.237879] ahci 0000:05:00.0: setting latency timer to 64
[    2.238226] scsi12 : ahci
[    2.238444] scsi13 : ahci
[    2.238520] ata13: SATA max UDMA/133 abar m8192@0xfb8fe000 port 0xfb8fe100 irq 17
[    2.238523] ata14: SATA max UDMA/133 abar m8192@0xfb8fe000 port 0xfb8fe180 irq 17
[    2.238539] ahci 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.267845] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.267848] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.267854] ahci 0000:06:00.0: setting latency timer to 64
[    2.268202] scsi14 : ahci
[    2.268424] scsi15 : ahci
[    2.268500] ata15: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 19
[    2.268504] ata16: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 19
[    2.298332] ata1.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[    2.298336] ata1.01: ATAPI: _NEC DVD+/-RW ND-3450A, 103C, max UDMA/33
[    2.358295] ata1.00: configured for UDMA/33
[    2.387758] raid6: int64x2   3434 MB/s
[    2.408300] ata1.01: configured for UDMA/33
[    2.415572] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    2.419534] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    2.419537] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.419618] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.419665] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.422259] scsi 0:0:1:0: CD-ROM            _NEC     DVD+-RW ND-3450A 103C PQ: 0 ANSI: 5
[    2.423714] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.423780] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    2.423817] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.557615] raid6: int64x4   2314 MB/s
[    2.557637] ata11: SATA link down (SStatus 0 SControl 330)
[    2.607594] ata15: SATA link down (SStatus 0 SControl 300)
[    2.617591] ata16: SATA link down (SStatus 0 SControl 300)
[    2.627583] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.717500] Refined TSC clocksource calibration: 2664.769 MHz.
[    2.717505] Switching to clocksource tsc
[    2.727357] raid6: int64x8   2376 MB/s
[    2.897237] raid6: sse2x1    4930 MB/s
[    3.067117] raid6: sse2x2    6080 MB/s
[    3.236999] raid6: sse2x4    5856 MB/s
[    3.237001] raid6: using algorithm sse2x2 (6080 MB/s)
[    3.237019] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    3.237032] ata13: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.237036] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.237063] ata14: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.237066] firewire_core: created device fw0: GUID 00e9d3d5006cf049, S400
[    3.248984] ata13.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    3.248990] ata13.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.249003] ata14.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    3.249008] ata14.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.253674] ata14.00: configured for UDMA/133
[    3.256057] ata13.00: configured for UDMA/133
[    3.263321] ata5.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    3.263326] ata5.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.269014] ata5.00: configured for UDMA/133
[    3.269176] scsi 4:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    3.269302] sd 4:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.269329] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.269352] sd 4:0:0:0: [sda] Write Protect is off
[    3.269355] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.269378] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.274232]  sda:
[    3.274809] sd 4:0:0:0: [sda] Attached SCSI disk
[    3.277417] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfbbfe000
[    3.277460] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    3.277464] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    3.277468] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    3.277472] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[    3.277477] xhci_hcd 0000:02:00.0: irq 51 for MSI/MSI-X
[    3.277481] xhci_hcd 0000:02:00.0: irq 52 for MSI/MSI-X
[    3.277485] xhci_hcd 0000:02:00.0: irq 53 for MSI/MSI-X
[    3.277489] xhci_hcd 0000:02:00.0: irq 54 for MSI/MSI-X
[    3.280773] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    3.280842] xHCI xhci_add_endpoint called for root hub
[    3.280844] xHCI xhci_check_bandwidth called for root hub
[    3.280873] hub 9-0:1.0: USB hub found
[    3.280878] hub 9-0:1.0: 4 ports detected
[    3.282980] ata12.00: HPA detected: current 625140335, native 625142448
[    3.282987] ata12.00: ATA-7: ST3320620AS, 3.AAJ, max UDMA/133
[    3.282990] ata12.00: 625140335 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.287195] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.287213] r8169 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.287337] r8169 0000:08:00.0: (unregistered net_device): no PCI Express capability
[    3.287345] r8169 0000:08:00.0: (unregistered net_device): unknown MAC, using family default
[    3.287791] r8169 0000:08:00.0: eth1: RTL8169 at 0xffffc900057b0000, 94:0c:6d:80:9c:91, XID 10000000 IRQ 16
[    3.341238] ata12.00: configured for UDMA/133
[    3.606903] input:   USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
[    3.606996] generic-usb 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1a.0-1/input0
[    3.693099] input:   USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input3
[    3.693196] generic-usb 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1a.0-1/input1
[    3.693209] usbcore: registered new interface driver usbhid
[    3.693211] usbhid: USB HID core driver
[    3.706715] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    3.816641] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.827878] ata6.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    3.827882] ata6.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.833613] ata6.00: configured for UDMA/133
[    3.833730] scsi 5:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    3.833867] sd 5:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.833896] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.833914] sd 5:0:0:0: [sdb] Write Protect is off
[    3.833917] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.833938] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.840497]  sdb:
[    3.841033] sd 5:0:0:0: [sdb] Attached SCSI disk
[    3.908990] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
[    3.909098] a4tech 0003:09DA:000A.0003: input,hidraw2: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1a.0-2/input0
[    4.376295] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.410444] ata7.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    4.410448] ata7.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    4.415526] ata7.00: configured for UDMA/133
[    4.415679] scsi 6:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    4.415852] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    4.415942] sd 6:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.416027] sd 6:0:0:0: [sdc] Write Protect is off
[    4.416031] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.416067] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.432477]  sdc:
[    4.433027] sd 6:0:0:0: [sdc] Attached SCSI disk
[    4.955883] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.972455] ata8.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    4.972459] ata8.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    4.976533] ata8.00: configured for UDMA/133
[    4.976688] scsi 7:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    4.976849] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    4.976962] sd 7:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.977100] sd 7:0:0:0: [sdd] Write Protect is off
[    4.977107] sd 7:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.977166] sd 7:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.989560]  sdd: sdd1
[    4.990100] sd 7:0:0:0: [sdd] Attached SCSI disk
[    5.199719] md: bind<sdd1>
[    5.525475] ata9: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.544418] ata9.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    5.544422] ata9.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    5.548526] ata9.00: configured for UDMA/133
[    5.548686] scsi 8:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    5.548850] sd 8:0:0:0: Attached scsi generic sg6 type 0
[    5.548945] sd 8:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    5.549060] sd 8:0:0:0: [sde] Write Protect is off
[    5.549069] sd 8:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    5.549109] sd 8:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.561617]  sde: sde1
[    5.562149] sd 8:0:0:0: [sde] Attached SCSI disk
[    5.775592] md: bind<sde1>
[    6.095021] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.115927] ata10.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    6.115931] ata10.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    6.121514] ata10.00: configured for UDMA/133
[    6.121670] scsi 9:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    6.121811] sd 9:0:0:0: Attached scsi generic sg7 type 0
[    6.121867] sd 9:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    6.121962] sd 9:0:0:0: [sdf] Write Protect is off
[    6.121966] sd 9:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    6.122007] sd 9:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.122035] scsi 11:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    6.122191] sd 11:0:0:0: Attached scsi generic sg8 type 0
[    6.122257] sd 11:0:0:0: [sdg] 625140335 512-byte logical blocks: (320 GB/298 GiB)
[    6.122306] scsi 12:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    6.122360] sd 11:0:0:0: [sdg] Write Protect is off
[    6.122364] sd 11:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    6.122404] sd 11:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.122437] sd 12:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    6.122483] sd 12:0:0:0: [sdh] Write Protect is off
[    6.122485] sd 12:0:0:0: [sdh] Mode Sense: 00 3a 00 00
[    6.122499] sd 12:0:0:0: Attached scsi generic sg9 type 0
[    6.122506] sd 12:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.122663] scsi 13:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    6.122780] sd 13:0:0:0: [sdi] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    6.122831] sd 13:0:0:0: [sdi] Write Protect is off
[    6.122833] sd 13:0:0:0: Attached scsi generic sg10 type 0
[    6.122836] sd 13:0:0:0: [sdi] Mode Sense: 00 3a 00 00
[    6.122859] sd 13:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.126071]  sdh:
[    6.126675] sd 12:0:0:0: [sdh] Attached SCSI disk
[    6.126851]  sdf: sdf1
[    6.127273] sd 9:0:0:0: [sdf] Attached SCSI disk
[    6.136402]  sdi:
[    6.136720] sd 13:0:0:0: [sdi] Attached SCSI disk
[    6.160580]  sdg: sdg1 sdg2 < sdg5 sdg6 >
[    6.161028] sd 11:0:0:0: [sdg] Attached SCSI disk
[    6.162646] xor: automatically using best checksumming function: generic_sse
[    6.204885]    generic_sse: 10921.200 MB/sec
[    6.204887] xor: using function: generic_sse (10921.200 MB/sec)
[    6.209622] md: raid6 personality registered for level 6
[    6.209623] md: raid5 personality registered for level 5
[    6.209625] md: raid4 personality registered for level 4
[    6.214362] md: raid10 personality registered for level 10
[    6.256663] md: bind<sdf1>
[    6.258383] bio: create slab <bio-1> at 1
[    6.258388] md/raid:md127: not clean -- starting background reconstruction
[    6.258397] md/raid:md127: device sdf1 operational as raid disk 2
[    6.258398] md/raid:md127: device sde1 operational as raid disk 1
[    6.258400] md/raid:md127: device sdd1 operational as raid disk 0
[    6.258659] md/raid:md127: allocated 3230kB
[    6.258793] md/raid:md127: raid level 5 active with 3 out of 3 devices, algorithm 2
[    6.258794] RAID conf printout:
[    6.258795]  --- level:5 rd:3 wd:3
[    6.258796]  disk 0, o:1, dev:sdd1
[    6.258798]  disk 1, o:1, dev:sde1
[    6.258799]  disk 2, o:1, dev:sdf1
[    6.258894] created bitmap (15 pages) for device md127
[    6.259205] md127: bitmap initialized from disk: read 1/1 pages, set 6 bits
[    6.327125] md127: detected capacity change from 0 to 4000789299200
[    6.328443]  md127: unknown partition table
[    6.725527] EXT4-fs (sdg6): INFO: recovery required on readonly filesystem
[    6.725530] EXT4-fs (sdg6): write access will be enabled during recovery
[    8.553960] EXT4-fs (sdg6): orphan cleanup on readonly fs
[    8.553967] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 8651182
[    8.554010] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 8651123
[    8.554033] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996738
[    8.554043] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996737
[    8.554054] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996736
[    8.554062] EXT4-fs (sdg6): ext4_orphan_cleanup: deleting unreferenced inode 15996722
[    8.554071] EXT4-fs (sdg6): 6 orphan inodes deleted
[    8.554072] EXT4-fs (sdg6): recovery complete
[    8.699880] EXT4-fs (sdg6): mounted filesystem with ordered data mode. Opts: (null)
[   17.286584] <30>udev[429]: starting version 167
[   17.295331] lp: driver loaded but no devices found
[   17.327189] EDAC MC: Ver: 2.1.0 Jul 29 2011
[   17.330073] EDAC i7core: Driver loaded.
[   17.356863] [drm] Initialized drm 1.1.0 20060810
[   17.408297] <30>udev[445]: renamed network interface eth0 to PCIe-NIC
[   17.420120] nouveau 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.420124] nouveau 0000:03:00.0: setting latency timer to 64
[   17.422830] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x092000a2)
[   17.426644] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
[   17.455328] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.455372] HDA Intel 0000:00:1b.0: irq 55 for MSI/MSI-X
[   17.455392] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.479597] [drm] nouveau 0000:03:00.0: ... appears to be valid
[   17.479601] [drm] nouveau 0000:03:00.0: BIT BIOS found
[   17.479603] [drm] nouveau 0000:03:00.0: Bios version 62.92.16.00
[   17.479605] [drm] nouveau 0000:03:00.0: TMDS table version 2.0
[   17.479607] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
[   17.479609] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 00000028
[   17.479611] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01000302 00000030
[   17.479612] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 04011310 00000028
[   17.479614] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 02011312 00000030
[   17.479615] [drm] nouveau 0000:03:00.0: Raw DCB entry 4: 010223f1 00c0c080
[   17.479617] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 14 4
[   17.479619] [drm] nouveau 0000:03:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   17.479621] [drm] nouveau 0000:03:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   17.479623] [drm] nouveau 0000:03:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   17.479624] [drm] nouveau 0000:03:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   17.479626] [drm] nouveau 0000:03:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   17.479629] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xC0C3
[   17.537416] <30>udev[446]: renamed network interface eth1 to PCI-NIC
[   17.574175] hda_codec: ALC889: BIOS auto-probing.
[   17.577015] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xC47D
[   17.582521] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   17.608256] Adding 12694524k swap on /dev/sdg5.  Priority:-1 extents:1 across:12694524k 
[   17.618694] type=1400 audit(1314660846.110:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=681 comm="apparmor_parser"
[   17.618703] type=1400 audit(1314660846.110:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
[   17.618786] type=1400 audit(1314660846.110:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=758 comm="apparmor_parser"
[   17.619207] type=1400 audit(1314660846.110:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=681 comm="apparmor_parser"
[   17.619217] type=1400 audit(1314660846.110:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
[   17.619298] type=1400 audit(1314660846.110:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=758 comm="apparmor_parser"
[   17.619533] type=1400 audit(1314660846.110:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=681 comm="apparmor_parser"
[   17.619544] type=1400 audit(1314660846.110:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
[   17.619626] type=1400 audit(1314660846.110:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=758 comm="apparmor_parser"
[   17.626760] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xD1EB
[   17.626771] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xD2EA
[   17.656790] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xD51A
[   17.656793] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xD57F
[   17.686907] [drm] nouveau 0000:03:00.0: 0xD57F: Condition still not met after 20ms, skipping following opcodes
[   17.733091] adt7475 0-002e: ADT7473 device, revision 1
[   17.742923] [drm] nouveau 0000:03:00.0: Detected monitoring device: adt7473
[   17.742926] [drm] nouveau 0000:03:00.0: 1 available performance level(s)
[   17.742930] [drm] nouveau 0000:03:00.0: 3: memory 1000MHz core 700MHz shader 1700MHz voltage 1150mV fanspeed 100%
[   17.742942] [drm] nouveau 0000:03:00.0: c: memory 499MHz core 399MHz shader 810MHz voltage 1150mV
[   17.743078] [TTM] Zone  kernel: Available graphics memory: 3061308 kiB.
[   17.743080] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[   17.743081] [TTM] Initializing pool allocator.
[   17.743095] [drm] nouveau 0000:03:00.0: Detected 512MiB VRAM
[   17.743112] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   17.788520] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[   17.872034] [drm] nouveau 0000:03:00.0: DCB encoder 1 unknown
[   17.872037] [drm] nouveau 0000:03:00.0: TV-1 has no encoders, removing
[   17.873459] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.873461] [drm] No driver support for vblank timestamp query.
[   18.053586] [drm] nouveau 0000:03:00.0: allocated 1440x900 fb: 0x60000000, bo ffff88018f85d800
[   18.053642] fbcon: nouveaufb (fb0) is primary device
[   18.053747] Console: switching to colour frame buffer device 180x56
[   18.055097] fb0: nouveaufb frame buffer device
[   18.055098] drm: registered panic notifier
[   18.055102] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
[   18.314118] EXT4-fs (sdg6): re-mounted. Opts: errors=remount-ro
[   18.623352] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
[   18.704015] type=1400 audit(1314660847.190:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1015 comm="apparmor_parser"
[   19.026922] r8169 0000:07:00.0: PCIe-NIC: link down
[   19.026927] r8169 0000:07:00.0: PCIe-NIC: link down
[   19.027467] ADDRCONF(NETDEV_UP): PCIe-NIC: link is not ready
[   19.029066] r8169 0000:08:00.0: PCI-NIC: link down
[   19.029609] ADDRCONF(NETDEV_UP): PCI-NIC: link is not ready
[   20.919431] r8169 0000:07:00.0: PCIe-NIC: link up
[   20.920137] ADDRCONF(NETDEV_CHANGE): PCIe-NIC: link becomes ready
[   23.105678] EXT4-fs (sdg6): re-mounted. Opts: errors=remount-ro,commit=0
[   23.189534] EXT4-fs (sdg1): re-mounted. Opts: commit=0
[   31.826783] PCIe-NIC: no IPv6 routers present
[   61.899992] md: resync of RAID array md127
[   61.899995] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[   61.899996] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[   61.900001] md: using 128k window, over a total of 1953510400 blocks.
[   63.765719] EXT4-fs (md127): recovery complete
[   63.765919] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
[   75.857353] md: md127: resync done.
[   75.989382] RAID conf printout:
[   75.989386]  --- level:5 rd:3 wd:3
[   75.989389]  disk 0, o:1, dev:sdd1
[   75.989391]  disk 1, o:1, dev:sde1
[   75.989393]  disk 2, o:1, dev:sdf1
```

As mentioned in previous post, this is a hobby media server for my home. I am not too fussed about high write speeds but keen on high reads. The server feeds a media PC and two WDTVLive boxes for my 3 TVs in the house, so the most important part is fast reads and sends via my gigabit NW. The house is wired with Cat6, and I have a 24 port GB switch.

I found Win 2008 R1 server ran OK other than it would glitch wehn serving the files... so movies would skip / jump... when playing movies from the Ubuntu RAID array all smooth and perfect... for the movies I could get copied onto the server! 

Again, many thanks for your help. I am really excited about this new world I am learning about... and I hope I can get it working!

Marc

PS: the processor is Intel i7 920, so plenty of grunt for parity work for RAID5 writes.

---

### Post by fatbotgw on 2011-08-29
The first thing that stands out to me is this:

```
RebuildFinished event detected on md device /dev/md127, component device  mismatches found: 1664
```

A quick google search found me this: [http://bergs.biz/blog/2009/03/01/startled-by-component-device-mismatches-on-raid1-volumes/]("http://bergs.biz/blog/2009/03/01/startled-by-component-device-mismatches-on-raid1-volumes/")

I don't know if this is the cause of your issues, but it couldn't hurt to fix it.  I'll look more at the logs, but hopefully someone else has some more insight.

Edit:
Can you post the output of ```
mdadm --detail /dev/md127
```
You will need to run it from a terminal.

---

### Post by MarcLocchi on 2011-08-29
Hi fatbotgw, here's the mdadm info. thanks again for the help!

I will execute the other piece and post back.

```
root@LSERVER:/home/tm# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Mon Aug 29 19:03:34 2011
     Raid Level : raid5
     Array Size : 3907020800 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Aug 30 10:31:46 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :New RAID Array
           UUID : 2db579e2:9e91f85d:0248a1fb:5d14cdc6
         Events : 8213

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       3       8       81        2      active sync   /dev/sdf1
```

---

### Post by MarcLocchi on 2011-08-29
Hi fatbotgw,
I am not having success in running the cleanup command on the link you forwarded. Here's what I get:

```
root@LSERVER:/home/tm# mdadm echo repair >> /sys/block/md127/md/sync_action
mdadm: An option must be given to set the mode before a second device
       (repair) is listed
root@LSERVER:/home/tm# 

```

I may well be doing something wrong! Thanks for any advice.

Marc

---

### Post by fatbotgw on 2011-08-29
> **MarcLocchi said:**
> Hi fatbotgw,
I am not having success in running the cleanup command on the link you forwarded. Here's what I get:

```
root@LSERVER:/home/tm# mdadm echo repair >> /sys/block/md127/md/sync_action
mdadm: An option must be given to set the mode before a second device
       (repair) is listed
root@LSERVER:/home/tm# 

```

I may well be doing something wrong! Thanks for any advice.

Marc

It's not "mdadm echo repair" it's "/etc/mdadm# echo repair" as in use the "cd" command to go to the directory "/etc/mdadm" and then type the rest of the command.

---

### Post by MarcLocchi on 2011-08-29
Great, thanks! I run the command after changing dirs, and got back a command prompt (no messages). I assume this means it ran OK (it took less than asecond). If I look at the content of /sys/block/md127/md/sync_action via text viewer, all it contains is "repair" and /sys/block/md127/md/mysmatch_cnt contains "0".

---

### Post by fatbotgw on 2011-08-29
Run the following to see what's currently going on with your array:
```
watch cat /proc/mdstat
```

That will tell you if it's building, checking, rebuilding, etc...  To get out of it, use Ctrl-c

---

### Post by MarcLocchi on 2011-08-29
Thanks! I was just looking at the synch files in /sys/block/md127/md/ via text viewer as I was playing a movie file on my client and the array failed... this time without freezing the PC... 

It now shows up DEGRADED in Disk Utility and it will not rebuild.... although all disks show up as healthy...

Even after reboot I cannot stop the array nor rebuild it... keeps telling me it is busy... not sure why? Bloody thing is driving me MAD!

---

### Post by fatbotgw on 2011-08-29
Now that it's failed and you're able to access the system, what does ```
mdadm --detail /dev/md127
``` give you?

Also, did you put the array in fstab to automatically get mounted at boot?

---

### Post by MarcLocchi on 2011-08-29
The mdadm --detail command shows (I cannot copy the screen it seems!):

```

Peronalities : [linear] [multipath] [raid0] [raid1] raid6] [raid5] [raid4] [raid10]

md0 : active raid5 sdd1[0] sdf1[3]
          3907020800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
          bitmap: 2/15 pages [8KB], 65536KB chunk

unused devices: <none>
```

Since the last drop out, it showed up as DEGRADED and 3TB only as in one drive totally off the air... although all individual drives show up as healthy in Disk Util.

Drive 3 became "unattached" and I had to re-attach... then resynching (recovering) started... all back to normal now (at least the PC did not freeze!)

The array is mounted manually to answer your question.

Thanks for your patience and persistence! I cannot believe how much trouble I am having with what is the preferred OS by the best techies in the world!

---

### Post by fatbotgw on 2011-08-29
> **MarcLocchi said:**
> The mdadm --detail command shows (I cannot copy the screen it seems!):

```

Peronalities : [linear] [multipath] [raid0] [raid1] raid6] [raid5] [raid4] [raid10]

md0 : active raid5 sdd1[0] sdf1[3]
          3907020800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
          bitmap: 2/15 pages [8KB], 65536KB chunk

unused devices: <none>
```

Since the last drop out, it showed up as DEGRADED and 3TB only as in one drive totally off the air... although all individual drives show up as healthy in Disk Util.

Drive 3 became "unattached" and I had to re-attach... then resynching (recovering) started... all back to normal now (at least the PC did not freeze!)

The array is mounted manually to answer your question.

Thanks for your patience and persistence! I cannot believe how much trouble I am having with what is the preferred OS by the best techies in the world!

If you're still seeing the "md0 : active" line then do a Ctrl-c to exit the watch.  Then do the "mdadm -D /dev/md127" which you should then be able to copy.

---

### Post by MarcLocchi on 2011-08-29
Thanks! Here's the output:

```
/dev/md0:
        Version : 1.2
  Creation Time : Mon Aug 29 19:03:34 2011
     Raid Level : raid5
     Array Size : 3907020800 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Aug 30 13:31:32 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :New RAID Array
           UUID : 2db579e2:9e91f85d:0248a1fb:5d14cdc6
         Events : 9844

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       3       8       81        2      active sync   /dev/sdf1

```

I have been reading a file from the array from my client now for 30 mins and no freezes (other than the drive dropping out of the array)... it smells to me like a driver incompatibility? could it be the Video card driver or NIC driver? 

Is there a way to look at a dump of what happened at time of freezing? 

Thanks again!

---

### Post by fatbotgw on 2011-08-29
In my experience, a "driver incompatibility" tends to be more of a Windows thing.

This almost sounds like the drives are acting up.  I know the 2TB Caviar Greens are notorious for not being great RAID drives.  Not to mention they don't seem to be the longest lasting drives.  I've got one in my desktop that is less than 1 year old and has started having I/O errors...while the Disk Utility shows it as "Healthy".  I'm replacing it with a Samsung F4 drive.

Let the array run for a while, if it drops another drive take a note of which one.  Then try adding one of your other unused drives to the array.  If the array no longer fails it's probably a failing drive.  If it still locks up, continue swapping the drives while keeping note of which ones you've swapped.  This probably isn't the best method, but it works.  If it fails no matter what combination of drives, we'll go from there.


If the array crashes and you can still access the computer, look at the log files you posted earlier for errors.  If the whole computer locks up, you could try to log in remotely using SSH to view those logs.  If you can't log in remotely, I don't know of a way to view them without rebooting.

Also, don't forget about the "Log File Viewer" under System -> Administration menu.

---

### Post by MarcLocchi on 2011-08-30
Man, you are a star! Thanks!
 
I just saw your reply so I jumped into the log viewer (while I was copying into the array and playing out a movie - load testing it) and hey presto! Another freeze... the movie and copy had been running for 1 hr faultlessly... 
 
Isn't it late in Idaho? I really appreciate your help!!!
 
Marc

---

### Post by rubylaser on 2011-08-30
If this was my server, I would backup what I have on the array, and start again using mdadm via the CLI.  Here are the steps if you choose to go that route:
*** Note:** The following is all from the terminal as root user
```
sudo -i
```
 
1. I would backup any data I had on the array.
2. I would stop the currently running array.
```
mdadm --stop /dev/md0
```
3. I would look at the SMART data on each drive and look for UDMA_CRC_Error_Count to note a bad SATA cable, or any other values that are higher than their thresholds.
4. Assuming all devices pass a SMART test and are deemed worthy, I would zero the superblocks on each drive.
```
mdadm --zero-superblock /dev/sdd1
mdadm --zero-superblock /dev/sde1
mdadm --zero-superblock /dev/sdf1
```
5. Then I would create a new array (at /dev/md0)
```
mdadm --create --metadata 1.2 --verbose /dev/md0 --level=5 --chunk=512 --raid-devices=3 /dev/sd[def]1
```
6. Then, I'd create a new /etc/mdadm/mdadm.conf file
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```
7. Then, I'd add a filesystem
```
mkfs.ext4 -b 4096 -E stride=128,stripe-width=256
```
8. I'd make sure I had an entry in /etc/fstab to mount the array (mounted at /storage in this case).
```
/dev/md0        /storage           ext4    defaults,noatime,nodiratime,commit=60        0       2
```
9. Finally, I'd test it hard for a few hours to rule out overheating hardware. You array disappearing should not lock the system up unless the root filesystem is on the array.
10. Finally, I'd setup smartctl to alert me via email of any device failures, and mdadm to alert me of any changes in the array state.

---

### Post by MarcLocchi on 2011-08-30
Hey rubylaser, will do! Thanks for the detailed help for this beginner! Both you and fatbotgw have been awesome!
 
I am reinstalling now as I want  a clean start, no GUI. Will let you know how your suggestion goes!
 
Question though, I am using the 320GB HDD for the OS and its files (rest for data), should I partition as follows:
 
1GB for /BOOT
12GB for /SWAP (2x MEM)
307GB for /
 
Many thanks!!!
 
Marc

---

### Post by rubylaser on 2011-08-30
Personally, in your case, I'd just suggest to use the guided partitioning, and select the option for all files on one partition.  That will provide you with a fine partitioning scheme.  And +1 for a server with no GUI.  Post back if you have any further questions.

---

### Post by MarcLocchi on 2011-08-30
Hi rubylaser, all installed now and at command prompt. How do I check smart status of drives from command line? I have tried smartctl command but without success. Thanks
 
PS: sorry but I am new at his (with 20+ years of setting up Windows, how stupid can I feel!). I will install GUI first, check SMART status in Disk Util, then create array from command line? the superblock commands you mention are to be executed on drives as members of an array, and I am starting fresh, so my device names are now /dev/SDA, SDC, SDD, etc... 
 
Thanks!

---

### Post by rubylaser on 2011-08-30
No, you don't need the GUI to view SMART info, and don't apologize.  This is how you'll learn :)

```
sudo apt-get install smartmontools
```

will install the packages you need.  Then, you can enable SMART like this...
```
smartctl -s on  /dev/sdb
```

And, you can see detailed info like this...
```
smartctl -a /dev/sdb
```

Let me know if you have more questions.

Zeroing the superblocks, need to be done on the partitions that were array members before.

```
fdisk -l
```

will show you if you still have partitions on those disks (you should unless you formatted them).  If you did format them you'll need to use parted or fdisk to add a new partition spanning the whole disk onto each drive that will be part of the array.  Let me know if this isn't clear.

---

### Post by fatbotgw on 2011-08-30
I have to second the "+1" for the server with no GUI.  It can have a learning curve to it, but it's well worth learning.

You might want to keep this link handy while you're setting up your array by CLI:  [Linux Software RAID]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID")
I  found it a useful reference when I was setting up my array.

---

### Post by MarcLocchi on 2011-08-31
Hi guys, many thanks for all your help! After burning the midnight oil till 3:30AM, and following your advice, my box still freezes during copy onto array....
 
I even tried a fresh install, replacing my 320GB SATA HDD with a 500 GB IDE drive and installed OK (rubylaser, this was during my exchanges with you last night)... 
 
I followed the command sequence rubylaser suggested, array was created and resynched... I today created a folder on it and shared it, then started copy... 10 mins later, POOF! death by total freezing... even ALT+SYS REQ+REISUB did not work... I could not figure out SSH though... so cold boot.
 
Tried a different NIC, different Video card, still same result.
 
Not sure why this is the case. The drives all work OK in single mode and even though I used 3 different physical devices to create the array at different attempts, the end result is the same...
 
Man, I love figuring out this stuff, the detective work is how you learn best... but this time I am being beat...
 
Not sure if you guys could SKYPE with me (I know this is not usual, but hey, I can only ask!)... let me know if you would be kind enough and I will share with you my ID... you have been amazingly kind already!
 
Many thanks!
 
Marc

---

### Post by rubylaser on 2011-08-31
This sounds like a hardware problem to me.  Even pulling the plug on running hard disks in the array shouldn't take the host down (don't do this :) ).  It sounds like it's overheating or a power supply issue.  Have you tried street testing your machine, or not adding all of the drives for mdadm, and just sharing a test file from the OS drive?

---

### Post by MarcLocchi on 2011-08-31
Hi rubylaser, thanks for the further help!
 
One more thing I just tried is I have mounted each drive individually and formatted as single partition to EXT4. I have then kicked off 2 (1TB data) copies onto each drive (like I do onto the array, across 8 drives, so 16 copies going simultaneously) and 2 hrs later all running smoothly... so it seems to be the case that ONLY copying / reading fron the array that freezes the monster...
 
By the way, I do not know how to SSH from my Win 7 PC, but the server will not let me ALT + Sys Req + RSEIUB. Also I have a 850W PS, so by my calcs I have enough power to drive the box (and never had the freezing with Win 2008 SW RAID 5, although its performance was less than good...)
 
I have Googled and cannot find any complaints on RAID and my board with Ubuntu... and I do not want to go back to Windows... I am really enjoying learning this whole new beast, it is awesome...
 
I am at a loss though, as not sure what to try next. I have so far:
 
1. Tried a different OS drive (replaced the old 320GB with new 500GB)
2. replaced the Video card (nVidia GTS 8800 and GTX 7900)
3. Switched from onboard NIC to PCI nic
4. Created RAID 5 array on 3 drives, 3 times, each time on different set of drives
5. Built array from GUI (Disk  Util) and command line (per rubylaser suggestion)
6. Disabled onboard sound driver
7. Disabled Power management in BIOS
8. Different USB ports for kbd / mouse
9. Large data copies (2 processes per drive) and no freezing
 
My next step is to turn the controllers from AHCI to IDE and see if this helps... here goes another install!
 
Thanks for all your help!

---

### Post by rubylaser on 2011-08-31
No need to re-install again, let's work with what you have.

WD Green drives seem to work for some people with mdadm and others have drive members dropping out.  Your 850W PSU should be more than enough as long as it's a single rail. I have an 10 disk mdadm RAID6, and it works fine on my 600W PSU.

As far as ssh goes, have you installed ssh server on your Ubuntu box?
```
sudo apt-get install ssh
```

And then downloaded [Putty]("http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe") for your Windows machine.

Your motherboard should work fine with Linux and mdadm, so that shouldn't be the problem.  I assume, you're not trying to use any of it's raid capabilities and have presented the disks as JBOD to the OS.

Finally, leave the controllers at AHCI rather than IDE, that's the correct way to have it.

---

### Post by MarcLocchi on 2011-08-31
OK, so the IDE piece did not work either, back to AHCI... on IDE I got the GRUB not loaded error on boot (even after successful install)...
 
Now I have tried loading Fedora X64 desktop to see whether it is just UBUNTU that my hw does not like... will let you know if this worked... only issue I see now is the drives (which were set up as standalone partitions) cannot be deleted and recreated... I do not have access to create folders on these... I am doing this via Disk Util which I understand is using my admin user rights and not ROOT... 
 
Onto the next challenge... will let you know if I can get RAID 5 working with FEDORA instead...
 
Thanks for the help!

---

### Post by rubylaser on 2011-08-31
I hope it works for you, but since it uses a similar kernel, and packages, it should work basically the same.  I don't know what the problem is (WD green drives, or those with the combination of the controller), but I've used mdadm on a ton of different platforms for years, and I've never seen this type of freezing except with hardware problems.

If you get it working, please let me know.

---

### Post by fatbotgw on 2011-08-31
> **MarcLocchi said:**
> OK, so the IDE piece did not work either, back to AHCI... on IDE I got the GRUB not loaded error on boot (even after successful install)...
 
Now I have tried loading Fedora X64 desktop to see whether it is just UBUNTU that my hw does not like... will let you know if this worked... only issue I see now is the drives (which were set up as standalone partitions) cannot be deleted and recreated... I do not have access to create folders on these... I am doing this via Disk Util which I understand is using my admin user rights and not ROOT... 
 
Onto the next challenge... will let you know if I can get RAID 5 working with FEDORA instead...
 
Thanks for the help!

Like rubylaser said, Fedora should work pretty much the same.  If it locks as well, give Ubuntu 10.04 LTS server a try.  It could be the versions that came in 11.04 have a problem with your hardware.

Something to check in you BIOS...make sure you don't have any of the drives set to "raid" as they should be set as whatever the default is.  This goes with what rubylaser said about showing them as JBOD (Just a Bunch Of Disks) to Ubuntu.

One other thing to try a search for would be issues with your controller chipsets instead of the whole motherboard.

Let us know what happens with Fedora...

---

### Post by MarcLocchi on 2011-08-31
Guys, thanks again. As way of update I got stuck trying to get Fedora to access the drives as lo and behold these were set up with my UBUNTU installation... so it all became too hard... and back to UBUNTU now... installing as I type.
 
One other thing I am trying is a different set of memory sticks and see if this makes a difference. 
 
I will look at the ICH10R controller in Google with UBUNTU and see if this is causing heart ache to anybody else...
 
Lastly, I will try the 10.04 and see what it does if this current test locks up... another thing I would like to try is to work purely from console (no GUI) right from install... but I am afraid I am nowhere near good enough to know how to navigate setting up the RAID array / shared folders purely from console... so this may well be test #87 I try after 10.04...
 
What a ride! Learning the hard way! Thanks again for the ongoing tutorial! :)
 
Thanks!
 
PS: to confirm all my drive controllers are set up as AHCI in BIOS and all disks are seen by UBUNTU during install as JBOD... all drives are listed in partition manager as standalone units.
 
As mentioned, when I format and mount as standalone units all drives receive data over network and write OK... I run 2x copies per drive (each approx 1TB) for more than 2 hrs two days ago without a glitch... so these work standalone...

---

### Post by fatbotgw on 2011-08-31
> **MarcLocchi said:**
> Guys, thanks again. As way of update I got stuck trying to get Fedora to access the drivers as lo and behold these were set up with my UBUNTU installation... so it all became too hard... and back to UBUNTU now... installing as I type.
 
One other thing I am trying is a different set of memory sticks and see if this makes a difference. 
 
I will look at the ICH10R controller in Google with UBUNTU and see if this is causing heart ache to anybody else...
 
Lastly, I will try the 10.04 and see what it does if this current test locks up... another thing I would like to try is to work purely from console (no GUI) right from install... but I am afraid I am nowhere near good enough to know how to navigate setting up the RAID array / shared folders purely from console... so this may well be test #87 I try after 10.04...
 
What a ride! Learning the hard way! Thanks again for the ongoing tutorial! :)
 
Thanks!

The guide I linked in post #25 of this thread has all the steps you need to setup a RAID array by CLI (command line interface).  Also, I believe rubylaser posted steps as well.  The only way you will learn the command line is to use it...

Keep us posted.

---

### Post by fatbotgw on 2011-08-31
Ok, new thought...  I did some searching and came across this thread:  [http://ubuntuforums.org/showthread.php?t=1640909&page=2]("http://ubuntuforums.org/showthread.php?t=1640909&page=2")

Go down to the last two posts (15 & 16) and that's how he solved his problem.

I'm thinking that maybe your problem isn't the RAID.  Before trying the fix, start a large copy to the main drive and see if it locks up.  If it does, give the fix a try.  If not, no harm done.

Also, here's another thread with someone that had a similar problem to yours.  --> [http://ubuntuforums.org/showthread.php?t=939923]("http://ubuntuforums.org/showthread.php?t=939923")

---

### Post by MarcLocchi on 2011-09-01
One more finding... I created RAID0 3 drive volume and started the copy process... same reult as RAID 5... total freeze of the box... I think RAID is out of the question on this box unless I revert to the Win set up, which was working but not performing as fast as needed to server the movie files...

---

### Post by MarcLocchi on 2011-09-01
Hi fabtogw, I have done large copies (2x per drive) by setting up each drive as standalone mount... this worked for 2 hrs without a problem.
 
I tried installing the Interl microcode (which installed OK) then ran the simultaneous 3x threads copying to a RAID 0 3 disk volume and same result... total freeze...
 
I am now installing 10.04 and see what happens... I will go at it from command line and see how far I get after this steep learning curve of sleepless nights and ongoing re-installs... on the bright side by testing on RAID 0 (which shows the same symptoms as RAID 5 freezes) I do not have to wait for resynch for the next test... so this was a bonus...
 
I will post back!
 
Thanks for all the help!
 
Marc

---

### Post by MarcLocchi on 2011-09-02
Hi guys,
Quick update, it seems my UD3R (Ver 2.0) died last night, probably from all the rebooting for installs and tests...
 
I have another PC with a V 1.0 UD3R and loaded 11.04 x64 and testing with RAID 0 on 3x 2TB drives (since it required no synchs and with previous tests it was freezing the PC) and all AWESOME so far... as in loaded it with 3TB data while watching a movie from it and it has run perfect for the last 2 hours!
 
On your advice, I did it all from command line, so no GUI... Thanks for the fantastic help...
 
Only issue I have found so far is on the console the following message appeared:
 
```

[21140.102318] NOHZ: local_softirq_pending 08

```
 
Searching Google I found the following info on ArchLinux:
 
[https://bugs.archlinux.org/task/23429](https://bugs.archlinux.org/task/23429)
 
It references a Kernel issue, it seems at time of release.
 
I ran DMESG and found the very same in my log:
 
```

[21140.102318] NOHZ: local_softirq_pending 08
[203064.714974] r8169 0000:07:00.0: eth0: link up
[203065.254448] r8169 0000:07:00.0: eth0: link up

```
 
Do you have any suggestions on what to do about this please... do I roll back to previous kernel version from 11.04 release and if so, how do I do this? I do not see the screen mentioned by this thread (unless I am going insane, whcih is likely after some 96 hours of playing with RAID!)
 
[http://ubuntuforums.org/showthread.php?t=127217](http://ubuntuforums.org/showthread.php?t=127217)
 
 
Many thanks for all your help! I will post once I test RAID 5... feeling great about it so far though!

---

### Post by rubylaser on 2011-09-02
I'm glad to hear it's working better for you now.  It sounds like your old motherboard may have had a hardware problem that didn't present itself in Windows, but caused enough issues with mdadm for it to fail.

You are correct in stating that it's a newer kernel issue.  It seems related to the onboard Realtek nic.  You could either compile an older kernel 2.6.37, or disable the onboard nic and add and Intel CT gigabit NIC in one of your PCI-e x1 slots, and just be done with it.

---

### Post by fatbotgw on 2011-09-02
Congrats on finally getting a working setup...too bad it took a motherboard failure...  Does that mean you now have all the parts except the motherboard sitting around not being used?  If so, I'd go get another motherboard and get it up and running.

As for the NIC, I'd agree on getting an Intel one.  

Just get one of these and you shouldn't have any issues: [Intel NIC]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106036")

---

### Post by MarcLocchi on 2011-09-02
OK, freezed again... this time, because I was working it from console only (no GUI installed) I got to see the dump...
 
I tried to Putty to it but I get timeouts too, so total freeze.
 
What I take from it was (as I cannot copy the whole dump across):
 
RIP [<ffffffffff812e562b>] memcpy+0xb/0x120
Kernel panic - not syncing: Fatal exception in interrupt
 
So it seems all along the NIC may have been the issue... based on softirq message I posted earlier... nice... at least something to zero in on...
 
Will let you know how I go next...
 
Thanks

---

### Post by MarcLocchi on 2011-09-06
Latest update is, after another couple of long nights... it seems the 2 Gigabyte boards I have just will not work withough freezing... Both are GA-X58A-UD3Rs (V1.0 and V2.0)... well, so that is how it goes...
 
I have built a new box using an old MOBO and C2Q Xtreme and so far, copying into my RAID 5 array, watching a 1080p movie and no failures... 2hrs into it... let's see if it gets through the next two days of load testing...
 
I wanted to say a BIG THANK YOU to both rubylaser and fatbotgw for your wonderful patience and ongoing help... I am now kinda reasonable OK with working on the Server from console only, no GUI, and it is better as you had said... thanks for the education you gave this newbie, it is really appreciated!!
 
PS: If you even get to Australia, send me a private message and let me know, there are a few beers on me for both of you!! Thanks again!

Marc :D

---

### Post by MarcLocchi on 2011-09-08
Hi guys,
 
Sorry to ask another question, hope you can help... I tested my RAID config on the new MOBO and all seems to be working... I then set off a RAID6 build with now 10x 2TB WD Caviar Greens... (still all from console, no GUI!)
 
I set min & max speeds for RAID rebuild per the following commands:
 
```

# echo 1000000 >/proc/sys/dev/raid/speed_limit_max
# echo 500000 >/proc/sys/dev/raid/speed_limit_min

```
 
It increased the rebuild speed to 50MB/s and decreased my 4.6 month rebuild time to just two days! 
 
Only problem is after a while (say 1+ hrs) the rebuild slows down to 1MB/s and less...
 
If I reboot the box and reset max & min I get the same effect... the rebuild starts from where it left off and speeds up to 50MB/s then over time slows down...
 
smartcl shows all drives OK...
 
I saw the script you recommended to someone for their RAID5 config and that it worked in speeding it up ([http://ubuntuforums.org/showthread.php?t=1494846](http://ubuntuforums.org/showthread.php?t=1494846)) and I think I know how to adapt to my box... only problem is I do not know I am right or not and also how to execute (if OK during rebuild running). Lastly if I understand correctly, the script helps rebuild AND running performance, or is it only running performance?
 
Can you please let me know your advice? I have changed script to look like below:
 
```

#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
###############################################################################
 
## parameters ##
MDDEV=md01              # e.g. md51 for /dev/md51 --- I EDITED THIS TO MATCH MY ARRAY
CHUNKSIZE=512           # in kb --- I EDITED THIS TO MATCH MY ARRAY
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=false          # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]   --- I WILL USE EXT4... so should I set to TRUE?
RAIDLEVEL=raid6         # raid5, raid6
 
## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> /data51/smbshare1/#tuneraid.log
  exit 1
fi
# set number of parity devices
NUMPARITY=1
if [[ $RAIDLEVEL == "raid6" ]]
then
  NUMPARITY=2
fi
# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done
# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]; do
  CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
  if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]
  then
    SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
  elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]
  then
    DEVS="$DEVS${CURDEV:2:1}"
  fi
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done
NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}
# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]
then
  echo $(date): Need more devices >> /data51/smbshare1/#tuneraid.log
  exit 1
fi
# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
blockdev --setra $RASIZE /dev/sd[$DEVS]
blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
blockdev --setra $MDRASIZE /dev/$MDDEV
# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4]kb\)
echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size
# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
  if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]
  then
    MINMAXHWSECKB=$MAXHWSECKB
  fi
  DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] &&
  ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] )
then
  echo setting max sectors kb to match chunk size
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
fi
# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]
then
  if [[ $NCQ == "disable" ]]
  then
    NCQDEPTH=1
  fi
  echo setting NCQ queue depth to $NCQDEPTH
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
fi
# tune2fs
if [[ $DOTUNEFS == "true" ]]
then
  STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
  STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
  echo setting stride to $STRIDE blocks \($CHUNKSIZEkb\)
  echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE]kb\)
  tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
fi
# exit
echo $(date): Success >> /home/#tuneraid.log      #  --- I EDITED THIS TO PLACE FILE in my HOME DIR
exit 0

```
 
In advance, thank for your help!!
 
M

---

### Post by MarcLocchi on 2011-09-08
To add to my last post, I tried creating bitmap with (working as ROOT)
```

[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~# mdadm -G /dev/md0 --bitmap=internal
[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~## mdadm: failed to set internal bitmap

```
 
I tried stopping the array and setting the bitmap to restart it:
```

[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~## mdadm --grow bitmap=internal /dev/md0
[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~## mdadm: error opening bitmap=internal: No such file or directory

```
 
Hmmm... I am missing something here and Googled it but I cannot find my missing piece. Again, thanks in advance for your help!
 
M

---

### Post by MarcLocchi on 2011-09-08
Well, installed the Intel microcode and restarted with max / min settings per prev post... 
 
```

apt-get install intel-microcode microcode.ctl

```
 
restarted array and currently running consistenly at 52MB/s... I would still like to understand why I cannot get bitmap set up though...
 
Thanks again!

---

### Post by lawbright on 2011-09-09
I have been having similar problems with Raid 5 freezes, using 2 different motherboards and cpus, with different controllers. But the freezing only happens in 11.04 x64 - it works fine in 10.04 x64. I upgraded to 11.04 about a month ago, and problems started occurring about a week later. I thought it might be hardware related, as the system was freezing after a few minutes of operation. I couldn't see anything in any of the logs I looked up. 

Hardware wise, I was using an Asus Striker Extreme, using an older Intel Pentium Duo chip. I changed that for a new ASRock G31M and an Intel Core 2 Quad cpu, both with 4 GB of RAM. I've used various SATA controllers, all using the usual suspects - Silicon Image 3114 and 3132 chips. I am using 9 SATA disks,  of between 1 and 2TB each, that is, two sets of 9 disks. One of them is swapped out every week and sent off site. The two sets are not exactly the same in size, but close. Different disk manufacturers as well - Samsung by majority, but also WDM and Seagate. Haven't noticed any difference between them over time in terms of reliability. The disks do fail regularly  - about 1 disk ever 2 months or so, but I believe that is down to how they are handled off site. I have a very similar hardware/software arrangement with 2 file/mail servers, one using 8.04 and the other 10.04 - and there has been only 1 disk failure in 2 years. In that arrangement, there are no disks swapped out - just very stable  7/24 operation. These are all mdadm software raids. 

I couldn't contend with the problems with hardware RAID controllers - being picky about disk sizes, disk models, and replacement issues should the controller go wrong. I have also done i/o tests versus an older IBM eServer with 6 SCSI disks and hardware RAIDs running at 15,000 rpm - a standard enterprise setup, but running Windows Server 2003. And guess what - there is actually very little difference between the standard SATA software RAID set up and Ubuntu vs the IBM/Windows 2003/Hardware RAID/SCSI disks. The differences are actually less than 5%.    

I am only using mdadm for the raid management, no LVMs. I am also using rsnapshot for the backup management. I started doing this with 9.04, and it has been very stable and logical to deal with until 11.04. I did new reinstalls of 11.04 about 4 times, starting with the most basic set up and then tweaking things with the mdadm daemon, such as turning it off the monitoring function, checking the email addresses and doing sudo blkid -g. None of these tweaks actually made any difference. 

I think its a problem with mdadm or the kernel - more likely the latter. I say this because when doing the 4 installs with 11.04, the install would take some minutes when doing the partition check - when it was disk scanning. The same operation in the install process in 10.04 would take about 5 seconds.  It feels like there is some unnecessary checking going on - the RAID disk LEDs woud turn on the raids and just stay lit. The system disk is not part of the RAID - it is simply stand alone, to prevent complications.  Once installed, I noticed in the boot up that DRDY errors would come up, on disk after disk - this doesn't happen in 10.04. When disk failures do occur under 10.04, they almost always would show up during the short SMART tests using smartctl, so were easy enough to control and manage. There were no SMART failures or error logs on any of the disks when I ran repeated smartctl tests on all the disks under 11.04.

---

### Post by rubylaser on 2011-09-10
> **MarcLocchi said:**
> Well, installed the Intel microcode and restarted with max / min settings per prev post... 
 
```

apt-get install intel-microcode microcode.ctl

```
 
restarted array and currently running consistenly at 52MB/s... I would still like to understand why I cannot get bitmap set up though...
 
Thanks again!

You can't set the bitmap option on a syncing array, so that's why that's not working.  Once it's done syncing you'll be able to do it, but there's not really a huge benefit.

To run that script, you'll want to be root user.
```
sudo -i
```
Then make a file for it...
```
nano /root/raid_speedup.sh
```
Then copy / paste the contents of that script into that file, and save (ctrl + x then press y and enter).

Finally, execute it.
```
. /root/raid_speedup.sh
```
And, you should be all set.

---

### Post by rubylaser on 2011-09-10
> **lawbright said:**
> I have been having similar problems with Raid 5 freezes, using 2 different motherboards and cpus, with different controllers. But the freezing only happens in 11.04 x64 - it works fine in 10.04 x64. I upgraded to 11.04 about a month ago, and problems started occurring about a week later. I thought it might be hardware related, as the system was freezing after a few minutes of operation. I couldn't see anything in any of the logs I looked up. 


If you've had something that works great for you, why are you upgrading?  Your hardware is supported on 10.04, so that's not the issue.  If you needed a newer version of mdadm, you could just grab the one of our the Debian Squeeze repo.  10.04 is the LTS, so that's probably the one you should be running anyways, unless there's some package you really need out of 11.04, I'd run with 10.04.  That's just my 2 cents.

---

### Post by MarcLocchi on 2011-09-10
Hi rubylaser! Thanks for this! You sure get around these forums! I have seen many useful bits from you on other threads that I have already used!!
 
Still learning here... to give you an update, after testing UBUNTU on 2x different revisions of Gigabyte UD3R with same results, I switched to ASUS mobo (latest BIOS) with Q6850X, 8GB RAM, 500GB PATA drive.
 
I placed 6x 2TB Caviar Greens on onboard ICH9R controller and added an LSI SAS3444e SAS controller on PCIe slot with additional 4x 2TB Caviar Greens.
 
Started R6 array build on 11.04... and used one of your thread replied to set min speed... all worked reasonably well at approx 50MB/s rebuild speed... (not 100MB/s as I saw on other threads for same ddrives though!)... it worked fine until it got to 68.4%... then it slowed down to 100KB/s... and stayed there saying some 4 months to go on rebuild!
 
I run IOSTAT and TOP and noticed:
- One drive holding back the rebuild, device I, on the LSI controller... 6000 ms waits on reads / writes...
- CPU usage around 0.3% to 1%...
All drives passed SMARTCTL tests.
 
I stopped it, and installed 10.04 to try... exactly same result... at 68.4% it froze down to 70KB/s and IOSTAT showed all 4 drives on LSI controller at 10000ms read and write wait times...
 
I cannot believe this baptism of fire! I have learned more about UBUNTU in 3 weeks than I have on Win in 20 years!!! But it has not worked for me... I now think my problem is with the LSI controller as it came out of System X server...
 
I am seeing if I can get hold of another controller to try... this thing is not going to beat me!!! I want UBUNTU on my server and although frustrating, I have really enjoyed the learning!
 
Thanks for all your help! You have been terrific! Let me know if any other thoughts come to mind on the above!
 
Marc
 
PS: Thanks re hints on running script! Are my edits OK for it? Raid 6, 512K chunk size. Thanks!

---

### Post by rubylaser on 2011-09-10
I personally use an [IBM m1015]("http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=ibm+m1015&_sacat=See-All-Categories") that I've flashed with [LSI 9211-8i IT firmware]("http://lime-technology.com/forum/index.php?topic=12767.msg124393#msg124393") (if you time it right, I bought 2 of these for $55 each).  It's a PCI-e x8 card that supports drives greater than 2TB and SATAIII.  

If you want a controller that will work great controller, get one base off LSI 1068e, like [this]("http://www.ebay.com/itm/IBM-44E8689-IBM-ServeRAID-BR10i-Storage-controller-R-/230661281933?pt=LH_DefaultDomain_0&hash=item35b47bd88d"), and [flash it]("http://www.servethehome.com/ibm-serveraid-br10i-lsi-sas3082e-r-pciexpress-sas-raid-controller/") with the LSI firmware. But, after reading, I believe that your card is also capable of being flashed with the same firmware (1068e based controller), so it might be either the firmware, hardware, or bad 8087 cables.

Yes, your edits for the script are fine based on your previous RAID setup.

---

### Post by MarcLocchi on 2011-09-10
rubylaser, thanks for the continued help!!!
 
I searched around and found the following link for updating firmware for my SAS3444e controller... as my luck goes, I could not find it via Googling "SAS3444E firmware" but did find it here: [http://forums.servethehome.com/showthread.php?19-LSI-RAID-Controller-HBA-Equivalency-Mapping/page4](http://forums.servethehome.com/showthread.php?19-LSI-RAID-Controller-HBA-Equivalency-Mapping/page4)
 
I reinstalled UBUNTU x64 Server and run up my R6 array using the commands you had posted to help someone else:
 
```

echo 1024 > /sys/block/sdb/queue/read_ahead_kb
echo 1024 > /sys/block/sdc/queue/read_ahead_kb
echo 1024 > /sys/block/sdd/queue/read_ahead_kb
echo 1024 > /sys/block/sde/queue/read_ahead_kb
echo 1024 > /sys/block/sdf/queue/read_ahead_kb
echo 1024 > /sys/block/sdg/queue/read_ahead_kb
echo 1024 > /sys/block/sdh/queue/read_ahead_kb
echo 1024 > /sys/block/sdi/queue/read_ahead_kb
echo 1024 > /sys/block/sdj/queue/read_ahead_kb
echo 1024 > /sys/block/sdk/queue/read_ahead_kb
 
echo 256 > /sys/block/sdb/queue/nr_requests
echo 256 > /sys/block/sdc/queue/nr_requests
echo 256 > /sys/block/sdd/queue/nr_requests
echo 256 > /sys/block/sde/queue/nr_requests
echo 256 > /sys/block/sdf/queue/nr_requests
echo 256 > /sys/block/sdg/queue/nr_requests
echo 256 > /sys/block/sdh/queue/nr_requests
echo 256 > /sys/block/sdi/queue/nr_requests
echo 256 > /sys/block/sdj/queue/nr_requests
echo 256 > /sys/block/sdk/queue/nr_requests
 
# Set read-ahead.
blockdev --setra 65536 /dev/md0
 
# Set stripe-cache_size for RAID6
echo 16384 > /sys/block/md0/md/stripe_cache_size

```
 
Next I reset max & min speeds:
 
```

echo 200000 > /sys/block/md0/md/sync_speed_max
echo 100000 > /sys/block/md0/md/sync_speed_min

```
 
Now it is running at a "decent" rebuild speed:
 
```

Every 2.0s: cat /proc/mdstat                                                                                Sun Sep 11 12:22:36 2011
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdi1[7] sdk1[9] sdj1[8] sdh1[6] sdd1[2] sdc1[1] sde1[3] sdg1[5] sdf1[4] sdb1[0]
      15628095488 blocks super 1.2 level 6, 512k chunk, algorithm 2 [10/10] [UUUUUUUUUU]
      [=>...................]  resync =  7.2% (141965128/1953511936) finish=491.8min speed=61381K/sec
unused devices: <none>

```
 
Will let you know if I FINALLY cracked it once it finishes and I load test it!!
 
Thanks again for the help!
 
M
 
PS: the script in my prev post I should run after the array completes synching right? Will the settings remain after next reboot or do I need to re run every time I start the box?
 
Thanks!

---

### Post by Markka on 2011-09-10
> **MarcLocchi said:**
> Hi all,
I am new to Linux / Ubuntu, and I must say I am really impressed with what the community has done with this OS. Awesome!
 
But I am running into an issue which is causing my installation to be unusable. I am setting up a media server for home, which will serve up files to my media center (Win 7 Home Prem) box. I set up the server all OK, but then when I copy files onto it, it freezes and requires a reboot. 
 
Here's what I have:
 
Ubuntu x64 server 11.04
Gnome GUI
Mobo: Gigabyte GA-X58A-UD3R (rev 2.0, latest GA BIOS - FF version) 
RAM: 3x 2GB 1666MHz 
HDDs: 
- 1x 320GB Hitachi partitioned as 10GB for /BOOT, 13GB for swap and rest for OS, attached to the Marvell 9128 SATA controller, running in ACHI mode
- 6x 2TB Caviar Green WD drives attached to ICH10R Intel SATA controller running in ACHI mode
- 2x 2TB Caviar Green WD drives attached to GYGABYTE SATA2 controller running in ACHI mode
VIDEO: nVidia Gforce 8800 GTS 512MB RAM
 
I have then set up the 8x 2TB HDDs as one software RAID 5 array, formatted with ETX4 file system. 2 days later, it completes resynching OK and lets me mount it. I can test its performance and blows me away with speeds of up to 585MB/s read, plenty for a media server!
 
I then set up  my share folders and update SAMBA.CONF to allow access from my Windows PCs where the media data resides at the moment. The copy process starts and I can see folders and files created on the SAMBA share OK, but at a random time the server freezes. I have to turn it off then on again, which triggers the 2 days resynching... 
 
I have tried first the desktop Ubuntu (more by mistake than by plan!) and had the same issue.
 
Questions I have are:
1. Can I set up software RAID 5 where the devices are across two separate controllers?
2. Should I use a different file system (than EXT4) for this large, 14TB volume?
3. Is there a flaw in my set up (i.e.: mobo not stable with Ubuntu for example)
 
I am at a loss here and anything I do to try to fix the issue requires 2 days resynching before finding out it does not work!
 
All suggestions welcome to this newbie!
 
Thanks
Marc
Hi MarcLocchi
  the configuration you described is monstrous, for one I would look at the PSU which may be insufficient for the Load.

---

### Post by MarcLocchi on 2011-09-11
Hi Markka, thanks for the reply. It is monstrous, but it has been working with Windows for some months now with no problems other than some performance glitches... the PSU is coping OK with all the drives, and I ran up a few checks against PCU capacity calculators on the web and I have enough power to run it all so these tell me!
 
Let me know if you have a suggestion on how else to check. Thanks!
 
M

---

### Post by rubylaser on 2011-09-11
I have 11 total disks in my fileserver, all 7,200 RPM drives, on a 650 Watt single rail PSU.  As long as he's got a single rail power supply over 700 watts, I think he mentioned 850 watts earlier, he should be fine.

MarcLocchi, I'm glad you're progressing at a decent speed.  Please keep us posted.

---

### Post by MarcLocchi on 2011-09-11
hi rubylaser,
 
More questions! Overnight the array continued to rebuild... it seems with the firmware upgrade of the LSI card, things are working better (before it would slow down to 100KB/s and call out 4 months to complete! Now is it running at 12MB/s and 2 hrs to go).
 
Question is, I found a few IO error messages on the console and coincidentally these are on 2 drives hanging off the LSI controller... IOSTAT shows the 4 drives on this controller as the really busy ones.. same as before tghe firmware upgrade...
 
Here's the dump from DMSG (not sure why it mentions RAID5 in this as I am building RAID6...
 
```

[39753.951644] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021b49b100) (sn=8600884)
[39753.951846] mptscsih: ioc0: attempting task abort! (sc=ffff88021b529b00)
[39753.951848] sd 10:0:3:0: [sdk] CDB: Write(10): 2a 00 d4 3d d0 00 00 04 00 00
[39753.951857] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021b529b00) (sn=8600887)
[39753.952052] mptscsih: ioc0: attempting task abort! (sc=ffff88021b4fe000)
[39753.952054] sd 10:0:3:0: [sdk] CDB: Write(10): 2a 00 d4 3d d4 00 00 04 00 00
[39753.952063] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021b4fe000) (sn=8600890)
[39753.952257] mptscsih: ioc0: attempting task abort! (sc=ffff88021b4fe900)
[39753.952259] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3e 96 c8 00 04 00 00
[39753.952268] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021b4fe900) (sn=8600893)
[39753.952468] mptscsih: ioc0: attempting task abort! (sc=ffff88021b4fed00)
[39753.952470] sd 10:0:0:0: [sdh] CDB: Read(10): 28 00 d4 3e ac 00 00 04 00 00
[39753.952479] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021b4fed00) (sn=8600894)
[39799.204403] mptscsih: ioc0: attempting task abort! (sc=ffff88021c21e700)
[39799.204409] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3e da c8 00 04 00 00
[39799.204419] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021c21e700) (sn=8601169)
[39799.204641] mptscsih: ioc0: attempting task abort! (sc=ffff88021c21ed00)
[39799.204643] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3e de c8 00 04 00 00
[39799.204649] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021c21ed00) (sn=8601171)
[39799.204851] mptscsih: ioc0: attempting task abort! (sc=ffff88021c21ec00)
[39799.204853] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3e e2 c8 00 04 00 00
[39799.204858] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021c21ec00) (sn=8601173)
[39799.205061] mptscsih: ioc0: attempting task abort! (sc=ffff88021c213e00)
[39799.205063] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3f 0e c8 00 04 00 00
[39799.205068] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021c213e00) (sn=8601195)
[39799.205268] mptscsih: ioc0: attempting task abort! (sc=ffff88021c213800)
[39799.205270] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3f 12 c8 00 04 00 00
[39799.205275] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021c213800) (sn=8601196)
[39799.205476] mptscsih: ioc0: attempting task abort! (sc=ffff88021c213c00)
[39799.205478] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3f 16 c8 00 04 00 00
[39799.205483] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021c213c00) (sn=8601210)
[39799.205685] mptscsih: ioc0: attempting task abort! (sc=ffff88021b528e00)
[39799.205687] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3f 1a c8 00 04 00 00
[39799.205692] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff88021b528e00) (sn=8601213)
[39799.205891] mptscsih: ioc0: attempting task abort! (sc=ffff8801e5d5ac00)
[39799.205893] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d4 3f 1e c8 00 04 00 00
[39799.205899] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=ffff8801e5d5ac00) (sn=8601216)
[40537.427534] sd 10:0:2:0: [sdj] Unhandled sense code
[40537.427537] sd 10:0:2:0: [sdj]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[40537.427542] sd 10:0:2:0: [sdj]  Sense Key : Medium Error [current]
[40537.427546] Info fld=0xd5c136c5
[40537.427548] sd 10:0:2:0: [sdj]  Add. Sense: Unrecovered read error
[40537.427552] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d5 c1 34 00 00 04 00 00
[40537.427561] end_request: I/O error, dev sdj, sector 3586208768
[40569.777327] raid5_end_read_request: 118 callbacks suppressed
[40569.777331] md/raid:md0: read error corrected (8 sectors at 3586206720 on sdj1)
[40569.777334] md/raid:md0: read error corrected (8 sectors at 3586206728 on sdj1)
[40569.777336] md/raid:md0: read error corrected (8 sectors at 3586206736 on sdj1)
[40569.777338] md/raid:md0: read error corrected (8 sectors at 3586206744 on sdj1)
[40569.777340] md/raid:md0: read error corrected (8 sectors at 3586206752 on sdj1)
[40569.777343] md/raid:md0: read error corrected (8 sectors at 3586206760 on sdj1)
[40569.777345] md/raid:md0: read error corrected (8 sectors at 3586206768 on sdj1)
[40569.777347] md/raid:md0: read error corrected (8 sectors at 3586206776 on sdj1)
[40569.777349] md/raid:md0: read error corrected (8 sectors at 3586206784 on sdj1)
[40569.777351] md/raid:md0: read error corrected (8 sectors at 3586206792 on sdj1)
[40827.825543] sd 10:0:2:0: [sdj] Unhandled sense code
[40827.825547] sd 10:0:2:0: [sdj]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[40827.825551] sd 10:0:2:0: [sdj]  Sense Key : Medium Error [current]
[40827.825556] Info fld=0xd636e6c2
[40827.825558] sd 10:0:2:0: [sdj]  Add. Sense: Unrecovered read error
[40827.825562] sd 10:0:2:0: [sdj] CDB: Read(10): 28 00 d6 36 e6 08 00 04 00 00
[40827.825571] end_request: I/O error, dev sdj, sector 3593922056
[40851.849356] raid5_end_read_request: 118 callbacks suppressed
[40851.849360] md/raid:md0: read error corrected (8 sectors at 3593920008 on sdj1)
[40851.849363] md/raid:md0: read error corrected (8 sectors at 3593920016 on sdj1)
[40851.849365] md/raid:md0: read error corrected (8 sectors at 3593920024 on sdj1)
[40851.849367] md/raid:md0: read error corrected (8 sectors at 3593920032 on sdj1)
[40851.849369] md/raid:md0: read error corrected (8 sectors at 3593920040 on sdj1)
[40851.849372] md/raid:md0: read error corrected (8 sectors at 3593920048 on sdj1)
[40851.849374] md/raid:md0: read error corrected (8 sectors at 3593920056 on sdj1)
[40851.849376] md/raid:md0: read error corrected (8 sectors at 3593920064 on sdj1)
[40851.849378] md/raid:md0: read error corrected (8 sectors at 3593920072 on sdj1)
[40851.849380] md/raid:md0: read error corrected (8 sectors at 3593920080 on sdj1)

```
 
Do you think Drive I & J are on their way out? I have ran multiple smart tests and all passed, coincidentally though the drives are on the LSI card (last 4 drives in the chain) which show constantly busy...
 
Here's the IOSTAT snapshot:
 
```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.50    0.00    2.00    0.00    0.00   97.50
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00
sdc               0.00    63.50    0.00    0.50     0.00   256.00  1024.00     0.00    0.00    0.00    0.00   0.00   0.00
sdd               0.00   127.00    0.00    1.00     0.00   512.00  1024.00     0.00    0.00    0.00    0.00   0.00   0.00
sde               0.00   127.00    0.00    1.00     0.00   512.00  1024.00     0.00    0.00    0.00    0.00   0.00   0.00
sdf               0.00   127.00    0.00    1.00     0.00   512.00  1024.00     0.01    5.00    0.00    5.00   5.00   0.50
sdg               0.00   127.00    0.00    1.00     0.00   512.00  1024.00     0.00    0.00    0.00    0.00   0.00   0.00
md0               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00
sdh               0.00    63.50    2.00    0.00  1024.00     0.00  1024.00    87.59 26790.00 26790.00    0.00 500.00 100.00
sdi               0.00     0.00    2.50    0.00  1280.00     0.00  1024.00   106.84 26708.00 26708.00    0.00 400.00 100.00
sdk               0.00     0.00    1.50    0.00   768.00     0.00  1024.00   103.17 26743.33 26743.33    0.00 666.67 100.00
sdj               0.00     0.00    1.50    0.00   768.00     0.00  1024.00    86.42 26856.67 26856.67    0.00 666.67 100.00

```
 
Also, none of this happens when I have console active, it seems to happen while the box runs overnight... could it be the drives spin down through power management? I also notice the array rebuild speeds up when I wake the screen up or connect via PuTTy... I will look at the BIOS and disable all APM once the rebuild completes.
 
Again, thanks for your help!
 
M
 
PS: Even after the firmware flash I cannot enter the LSI console during post by hitting Ctrl+C... could it be a setting in the controller that needs changing (if drives are spinning down)? Could I counter this via a paramter set somewhere in boot / config files?

---

### Post by MarcLocchi on 2011-09-11
Hi rubylaser,
 
OK, all finished although drive J was dropped... when I check SMARTCTL it is full of errors... so I replaced and restarted rebuild...
 
array (degraded) copied (received over network) and played back (movie files read from client) files without any issues... so really nice!
 
It seems I had a faulty drive as the issue all along (even with my Win set up)... so this is why I had glitches in playback...
 
Only catch is I have to wait another 24hrs for recovery to finish!! 
 
I set up a bacth file to execute the raid synch speed up commands from prev post and it worked and saved a lot of typing to thanks for the hints on how to do this... will post when finally done and see if I succeeded!
 
Thanks for the help!
 
M

---

### Post by rubylaser on 2011-09-11
I was just going to post and tell you it looked like sdj was on it's way out.  Please keep me posted on how it turns out.

---

### Post by MarcLocchi on 2011-09-11
Hey rubylaser, you never sleep! I can see you are still online now...
 
Thanks for the reply... do you think any other drives are on their way? I think maybe drive I is too? 
 
I have replaced J and rebuilding now, but I can see constant heavier load on the LSI controller drives (over the ICH9R ones on the board)... why do you think this is the case?
 
```

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00
sdb           11553.00     0.00  305.00    1.00 44866.00     1.00   293.25     7.81   26.23   25.89  130.00   1.31  40.00
sdc           11670.50     0.00  188.00    1.00 45506.00     1.00   481.56    11.21   61.64   61.30  125.00   2.65  50.00
sdd           11634.00     0.00  225.00    1.50 45570.00     3.00   402.41    12.36   56.53   56.29   93.33   2.32  52.50
sde           11624.00    47.00  188.00    2.50 45186.00   195.00   476.44    11.46   63.57   63.51   68.00   2.89  55.00
sdf           11487.00    63.00  305.50    2.00 44034.00   257.00   288.07     7.96   25.46   25.16   72.50   1.45  44.50
sdg           11600.00    63.00  205.00    2.00 50502.00   257.00   490.43    12.10   73.65   73.24  115.00   2.92  60.50
md0               0.00     0.00    0.00   10.50     0.00  1024.00   195.05     0.00    0.00    0.00    0.00   0.00   0.00
sdi           12940.00    79.00  131.00    1.00 51650.00     1.00   782.59    40.38  328.45  328.21  360.00   6.86  90.50
sdh           11670.00    79.00  119.00    1.50 45448.00     3.00   754.37    30.09  259.71  258.87  326.67   6.80  82.00
sdj               0.00 13389.00    0.00  102.00     0.00 46991.00   921.39    31.25  289.61    0.00  289.61   7.01  71.50
sdk           11751.00     0.00  117.50    1.00 45344.00     1.00   765.32    30.16  264.39  264.04  305.00   6.62  78.50

``` 
 
Off subject question: can you point me to a good simple link which shows you how to, step by step, set up NIC bonding for aggregated bandwidth pls. I have 2 NICs in the box and since I am now pretty confident this thing will work (the R6 set up), I would like to set bonding up and make use of both NICs with dedicated bandwidth for each.
 
Stuff I have seen has not been clear enough for this "almost" newbie!
 
Many thanks!!
 
M

---

### Post by rubylaser on 2011-09-12
It's had to say with your LSI HBA.  Do you have the card installed in a slot that supports PCI-e x8 or x16?  In regards to NIC bonding, are you looking for LACP (you need a managed switch to support this) or are you just trying to get round robin (oad balancing and fault tolerance) working?

[This]("http://www.ubuntugeek.com/how-to-setup-bond-or-team-network-cards-in-ubuntu-10-1010-04.html") tutorial is about as easy as it comes and demonstrates setting up a round robin nic bond via ifenslave.

---

### Post by MarcLocchi on 2011-09-12
Hi rubylaser, 
Thanks again for the reply!
 
I was hoping to aggregate bandwidth so I can serve multiple movies to multiple devices simultaneously and have spare bandwidth to do so. If I understand round robin I will basically get load balancing and fault tolerance only, while total bandwidth is 1Gb/s? To achieve 2Gb/s I will need a special switch if I understand your post... hmmm I will have to Google my switch...
 
Re the HBA controller it is installed in a PCIEx16 slot which supports boxth x8 and x16 (the HBA is x8...).
 
The R6 finally just finished adding the replacement drive and I am now load testing it overnight with 5TB of data being copied from various PCs and via multiple copy streams, while playing back movies on one of the PCs... if it is still running tomorrow then success!!!
 
Lastly, as it just finished recovering the replacement drive into the R6 array, I saw the following messages on the console:
 
```

[40932.244377] ata5.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x0 action 0x0
[40932.244592] ata5.00: irq_stat 0x40000008
[40932.244680] ata5.00: failed command: READ FPDMA QUEUED
[40932.244754] ata5.00: cmd 60/00:00:00:8c:e0/04:00:e7:00:00/40 tag 0 ncq 524288 in
[40932.244755]          res 41/40:ef:06:8f:e0/00:00:e7:00:00/40 Emask 0x409 (media error) <F>
[40932.244903] ata5.00: status: { DRDY ERR }
[40932.244976] ata5.00: error: { UNC }
[40932.257227] ata5.00: configured for UDMA/133
[40932.257338] ata5: EH complete
[40936.777808] ata5.00: exception Emask 0x0 SAct 0x73f0f17f SErr 0x0 action 0x0
[40936.778042] ata5.00: irq_stat 0x40000008
[40936.778138] ata5.00: failed command: READ FPDMA QUEUED
[40936.778231] ata5.00: cmd 60/00:c8:00:a0:e0/04:00:e7:00:00/40 tag 25 ncq 524288 in
[40936.778232]          res 41/40:7f:7b:a0:e0/00:03:e7:00:00/40 Emask 0x409 (media error) <F>
[40936.778418] ata5.00: status: { DRDY ERR }
[40936.778511] ata5.00: error: { UNC }
[40936.790869] ata5.00: configured for UDMA/133
[40936.790943] ata5: EH complete
[40940.011213] ata5.00: exception Emask 0x0 SAct 0x1fffff SErr 0x0 action 0x0
[40940.011509] ata5.00: irq_stat 0x40000008
[40940.011621] ata5.00: failed command: READ FPDMA QUEUED
[40940.011733] ata5.00: cmd 60/00:00:00:8c:e0/04:00:e7:00:00/40 tag 0 ncq 524288 in
[40940.011733]          res 41/40:ef:06:8f:e0/00:00:e7:00:00/40 Emask 0x409 (media error) <F>
[40940.012029] ata5.00: status: { DRDY ERR }
[40940.012228] ata5.00: error: { UNC }
[40940.025632] ata5.00: configured for UDMA/133
[40940.025706] ata5: EH complete
[40943.233484] ata5.00: exception Emask 0x0 SAct 0x1fffff SErr 0x0 action 0x0
[40943.233825] ata5.00: irq_stat 0x40000008
[40943.233955] ata5.00: failed command: READ FPDMA QUEUED
[40943.234174] ata5.00: cmd 60/00:88:00:a0:e0/04:00:e7:00:00/40 tag 17 ncq 524288 in
[40943.234175]          res 41/40:7f:7b:a0:e0/00:03:e7:00:00/40 Emask 0x409 (media error) <F>
[40943.234678] ata5.00: status: { DRDY ERR }
[40943.234935] ata5.00: error: { UNC }
[40943.247492] ata5.00: configured for UDMA/133
[40943.247564] ata5: EH complete
[40946.466886] ata5.00: exception Emask 0x0 SAct 0x1fffff SErr 0x0 action 0x0
[40946.467278] ata5.00: irq_stat 0x40000008
[40946.467527] ata5.00: failed command: READ FPDMA QUEUED
[40946.467827] ata5.00: cmd 60/00:00:00:8c:e0/04:00:e7:00:00/40 tag 0 ncq 524288 in
[40946.467828]          res 41/40:ef:06:8f:e0/00:00:e7:00:00/40 Emask 0x409 (media error) <F>
[40946.468457] ata5.00: status: { DRDY ERR }
[40946.468780] ata5.00: error: { UNC }
[40946.480807] ata5.00: configured for UDMA/133
[40946.480877] ata5: EH complete
[40951.100306] ata5.00: exception Emask 0x0 SAct 0x1c0000 SErr 0x0 action 0x0
[40951.100780] ata5.00: irq_stat 0x40000008
[40951.101136] ata5.00: failed command: READ FPDMA QUEUED
[40951.101502] ata5.00: cmd 60/00:a0:00:8c:e0/04:00:e7:00:00/40 tag 20 ncq 524288 in
[40951.101503]          res 41/40:ef:06:8f:e0/00:00:e7:00:00/40 Emask 0x409 (media error) <F>
[40951.102264] ata5.00: status: { DRDY ERR }
[40951.102650] ata5.00: error: { UNC }
[40951.114557] ata5.00: configured for UDMA/133
[40951.114575] ata5: EH complete
[40954.333704] ata5.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[40954.334291] ata5.00: irq_stat 0x40000008
[40954.334712] ata5.00: failed command: READ FPDMA QUEUED
[40954.335136] ata5.00: cmd 60/00:00:00:8c:e0/04:00:e7:00:00/40 tag 0 ncq 524288 in
[40954.335136]          res 41/40:ef:06:8f:e0/00:00:e7:00:00/40 Emask 0x409 (media error) <F>
[40954.336021] ata5.00: status: { DRDY ERR }
[40954.336470] ata5.00: error: { UNC }
[40954.348872] ata5.00: configured for UDMA/133
[40954.348887] ata5: EH complete
[41207.488447] md: md0: recovery done.
[41208.887583] RAID conf printout:
[41208.887586]  --- level:6 rd:10 wd:10
[41208.887589]  disk 0, o:1, dev:sdb1
[41208.887591]  disk 1, o:1, dev:sdc1
[41208.887594]  disk 2, o:1, dev:sdd1
[41208.887596]  disk 3, o:1, dev:sde1
[41208.887598]  disk 4, o:1, dev:sdf1
[41208.887600]  disk 5, o:1, dev:sdg1
[41208.887602]  disk 6, o:1, dev:sdh1
[41208.887604]  disk 7, o:1, dev:sdi1
[41208.887606]  disk 8, o:1, dev:sdj
[41208.887608]  disk 9, o:1, dev:sdk1

```
 
Why would drive J not appear as dev:sdJ1 in the array listing at the tail of the log (it appears as dev:sdj without the "1" as in a device, not a partition)
 
Are the media errors related to any specific drive? I cannot see any reference to specific device in the listing, how could I find out whether there is another drive about to die?
 
I found this link which talks about data corruption but I cannot see a resolution... how do I do a CHKDSK on the R6 volume (as you would do in Windows? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)
 
Many thanks again for the ongoing tutorial!
 
M

---

### Post by MarcLocchi on 2011-09-12
Hi rubylaser, 
Further update, my switch does not support 802.3ad, so I set up load balancing (mode 0)... but it did not work per the tutorial, I finally got it working per a post at the bottom of the page:
```

# The loopback network interface
 auto lo
 iface lo inet loopback
 
#Failed until these two lines were added
 iface eth0 inet manual
 iface eth1 inet manual
 
auto bond0
 iface bond0 inet static
 address 192.168.1.xxx
 netmask 255.255.255.0
 gateway 192.168.1.xxx
 up ifenslave bond0 eth0 eth1
 down ifenslave -d bond0 eth0 eth1

```
 
Last question though, I tried running the script to tune the array per prev post (including my edits) and I can see the HDD activity lights flickering when the script is running but it will not complete... I have to Ctrl-C out of it... not sure how I can check why it is stuck.
 
Again, thanks for all the help! It all seems to be working now... what a hell of a ride!
 
M

---

### Post by rubylaser on 2011-09-12
Glad to hear it's going well so far :) That slot should work great for you.  Here are the bond modes via ifenslave

> 0 (balance-rr) Round-robin policy: Transmit packets in sequential order from the first available slave through the last. This mode provides load balancing and fault tolerance.

1 (active-backup) Active-backup policy: Only one slave in the bond is active. A different slave becomes active if, and only if, the active slave fails. The bond's MAC address is externally visible on only one port (network adapter) to avoid confusing the switch. This mode provides fault tolerance. The primary option affects the behavior of this mode.

2 (balance-xor) XOR policy: Transmit based on [(source MAC address XOR'd with destination MAC address) modulo slave count]. This selects the same slave for each destination MAC address. This mode provides load balancing and fault tolerance.

3 (broadcast) Broadcast policy: transmits everything on all slave interfaces. This mode provides fault tolerance.

4 (802.3ad) IEEE 802.3ad Dynamic link aggregation. Creates aggregation groups that share the same speed and duplex settings. Utilizes all slaves in the active aggregator according to the 802.3ad specification.

Pre-requisites:
Ethtool support in the base drivers for retrieving the speed and duplex of each slave.
A switch that supports IEEE 802.3ad Dynamic link aggregation. Most switches will require some type of configuration to enable 802.3ad mode.
5 (balance-tlb) Adaptive transmit load balancing: channel bonding that does not require any special switch support. The outgoing traffic is distributed according to the current load (computed relative to the speed) on each slave. Incoming traffic is received by the current slave. If the receiving slave fails, another slave takes over the MAC address of the failed receiving slave.

Prerequisite: Ethtool support in the base drivers for retrieving the speed of each slave.

You're basically looking at either mode 0 (round robin) or mode 4 (LACP).  Round robin won't give you the throughput of 2 gigabit connections to one host, but it will allow your machine to push 2 simultaneous gigabit streams at once (as long as your array can keep up :) ).  Also, it gives you fault tolerance, in that if 1 interface dies, the other will keep going without a hiccup. For your purposes, mode0 should be just fine.

In regards to drive j, what does this show you?
```
mdadm --detail /dev/md0
```
and 
```
mdadm -E /dev/sdj1
```

You'll want to use smartmontools to monitor the disks.  There's really not a better way to do that.  If you notice values increasing rapidly, it might be time to look at that disk.

You need to do a filesystem check.  To do that, you'd umount the array (I'm not sure where you have it mounted, but here's an example.
```
umount /storage
```
Then, run an fsck on it.
```
fsck.ext4 /dev/md0
```
after that's done, you can remount it.
```
mount -a
```

---

### Post by rubylaser on 2011-09-12
Try this [script]("http://ubuntuforums.org/showthread.php?t=1494846").  You'll need to be the root user to run it..
```
sudo -i
```
```
nano /root/raid_speedup.sh
```
paste this in...
```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
###############################################################################


## parameters ##
MDDEV=md0              # e.g. md51 for /dev/md51
CHUNKSIZE=512          # in kb
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=tru          # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid6         # raid5, raid6


## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> /root/tuneraid.log
  exit 1
fi

# set number of parity devices
NUMPARITY=1
if [[ $RAIDLEVEL == "raid6" ]]
then
  NUMPARITY=2
fi

# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]; do
  CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
  if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]
  then
    SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
  elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]
  then
    DEVS="$DEVS${CURDEV:2:1}"
  fi
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done
NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}

# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]
then
  echo $(date): Need more devices >> /root/tuneraid.log
  exit 1
fi

# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
blockdev --setra $RASIZE /dev/sd[$DEVS]
blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
blockdev --setra $MDRASIZE /dev/$MDDEV

# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4]kb\)
echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size

# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
  if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]
  then
    MINMAXHWSECKB=$MAXHWSECKB
  fi
  DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] &&
  ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] )
then
  echo setting max sectors kb to match chunk size
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]
then
  if [[ $NCQ == "disable" ]]
  then
    NCQDEPTH=1
  fi
  echo setting NCQ queue depth to $NCQDEPTH
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# tune2fs
if [[ $DOTUNEFS == "true" ]]
then
  STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
  STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
  echo setting stride to $STRIDE blocks \($CHUNKSIZEkb\)
  echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE]kb\)
  tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
fi

# exit
echo $(date): Success >> /root/tuneraid.log

```
Then, run it like this...
```
. /root/raid_speedup.sh
```

---

### Post by MarcLocchi on 2011-09-13
Hi rubylaser,
 
One more update and I think I am well on my way... all is working well now, although only disappointing thing is write speed on the array. When copying into it over network now I see a consistent 43MB/s when I am used to seeing 100MB/s+... so slow to receive files (although this is OK as I am more keen on read speed, which sits at 110MB/s over network)... could this be and issue with the NIC teaming?
 
Here's what hdparm -tT /dev/md0 tells me (which I think is OK?)
```

root@LSERVER:~# hdparm -tT /dev/md0
/dev/md0:
Timing cached reads:   1902 MB in  2.00 seconds = 950.96 MB/sec
Timing buffered disk reads: 588 MB in  3.51 seconds = 167.41 MB/sec

```
 
By the way, I did run the Raid Tuneup script prior to this and I did notice an error on the console: "/dev/sd[] no such file or directory", which seems like a drive letter parameter is not flowing through the script? Even though, the cached reads are awesome. I cannot see how to test the write speed with hdparm though.
 
To answer your questions, output of mdadm --detail /dev/md0 is:
```

root@LSERVER:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Sep 11 11:21:49 2011
     Raid Level : raid6
     Array Size : 15628095488 (14904.11 GiB 16003.17 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 10
  Total Devices : 10
    Persistence : Superblock is persistent
    Update Time : Tue Sep 13 23:02:00 2011
          State : clean
 Active Devices : 10
Working Devices : 10
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 512K
           Name : LSERVER:0  (local to host LSERVER)
           UUID : f65fe11e:2ae4eb81:1c2f1f32:7af495f1
         Events : 19878
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1
      10       8      144        8      active sync   /dev/sdj
       9       8      161        9      active sync   /dev/sdk1

```
 
Should I be concerned with the 19878 events (as in are these SMART events)?
 
Also on the mdadm -E /dev/sdj1 command I get a strange reply:
```

root@LSERVER:~# mdadm -E /dev/sdj1
mdadm: No md superblock detected on /dev/sdj1.

```
 
when I run this on /dev/sdi1 I get detailed info:
```

root@LSERVER:~# mdadm -E /dev/sdi1
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f65fe11e:2ae4eb81:1c2f1f32:7af495f1
           Name : LSERVER:0  (local to host LSERVER)
  Creation Time : Sun Sep 11 11:21:49 2011
     Raid Level : raid6
   Raid Devices : 10
 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 31256190976 (14904.11 GiB 16003.17 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 041a58a0:8c763556:1a8fba2c:af275e1b
    Update Time : Tue Sep 13 23:17:47 2011
       Checksum : a6e66eac - correct
         Events : 19878
         Layout : left-symmetric
     Chunk Size : 512K
   Device Role : Active device 7
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)

```
 
Is /dev/sdj on its way to hard drive hell:frown:? All other devices come up as "clean"... 
 
Lastly the file check returns clean... so this is good!
 
It has been working fine in terms of reads and (slow) writes... but this last test has now got me worried that I have not quite conquered it! Do I have to rebuild the array?
 
Thanks again for the help!

---

### Post by MarcLocchi on 2011-09-13
The plot thickens... I read someone else had this same issue with "no md superblock detected" on one of his array drives, and a reboot fixed it...
 
I try this and find /dev/sdj to be OK now, BUT /dev/sdk has the issue... and this is because the drive numbering is scrambled from last boot (i.e." sdj was drive 10 last time, sdk is drive 10 now)... This has happened because I have an external USB drive plugged in during boot (which was sdl before and it is sdh now)... I can only assume the "problem drive is the same phycial device both times?
 
Anyway, one more thing to learn / fix I guess... thanks for any advice!
 
M
 
PS: write speed over the network still sucks at 40MB/s... while reads are a decent 110MB/s... should I expect this from R6 (as in such a difference in performance?)

---

### Post by rubylaser on 2011-09-13
> **MarcLocchi said:**
> Hi rubylaser,
 
One more update and I think I am well on my way... all is working well now, although only disappointing thing is write speed on the array. When copying into it over network now I see a consistent 43MB/s when I am used to seeing 100MB/s+... so slow to receive files (although this is OK as I am more keen on read speed, which sits at 110MB/s over network)... could this be and issue with the NIC teaming?
 
Here's what hdparm -tT /dev/md0 tells me (which I think is OK?)
```

root@LSERVER:~# hdparm -tT /dev/md0
/dev/md0:
Timing cached reads:   1902 MB in  2.00 seconds = 950.96 MB/sec
Timing buffered disk reads: 588 MB in  3.51 seconds = 167.41 MB/sec

```
 
By the way, I did run the Raid Tuneup script prior to this and I did notice an error on the console: "/dev/sd[] no such file or directory", which seems like a drive letter parameter is not flowing through the script? Even though, the cached reads are awesome. I cannot see how to test the write speed with hdparm though.
 
To answer your questions, output of mdadm --detail /dev/md0 is:
```

root@LSERVER:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Sep 11 11:21:49 2011
     Raid Level : raid6
     Array Size : 15628095488 (14904.11 GiB 16003.17 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 10
  Total Devices : 10
    Persistence : Superblock is persistent
    Update Time : Tue Sep 13 23:02:00 2011
          State : clean
 Active Devices : 10
Working Devices : 10
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 512K
           Name : LSERVER:0  (local to host LSERVER)
           UUID : f65fe11e:2ae4eb81:1c2f1f32:7af495f1
         Events : 19878
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1
      10       8      144        8      active sync   /dev/sdj
       9       8      161        9      active sync   /dev/sdk1

```
 
Should I be concerned with the 19878 events (as in are these SMART events)?
 
Also on the mdadm -E /dev/sdj1 command I get a strange reply:
```

root@LSERVER:~# mdadm -E /dev/sdj1
mdadm: No md superblock detected on /dev/sdj1.

```
 
when I run this on /dev/sdi1 I get detailed info:
```

root@LSERVER:~# mdadm -E /dev/sdi1
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f65fe11e:2ae4eb81:1c2f1f32:7af495f1
           Name : LSERVER:0  (local to host LSERVER)
  Creation Time : Sun Sep 11 11:21:49 2011
     Raid Level : raid6
   Raid Devices : 10
 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 31256190976 (14904.11 GiB 16003.17 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 041a58a0:8c763556:1a8fba2c:af275e1b
    Update Time : Tue Sep 13 23:17:47 2011
       Checksum : a6e66eac - correct
         Events : 19878
         Layout : left-symmetric
     Chunk Size : 512K
   Device Role : Active device 7
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)

```
 
Is /dev/sdj on its way to hard drive hell:frown:? All other devices come up as "clean"... 
 
Lastly the file check returns clean... so this is good!
 
It has been working fine in terms of reads and (slow) writes... but this last test has now got me worried that I have not quite conquered it! Do I have to rebuild the array?
 
Thanks again for the help!

What file sharing protocol are you using?  If it's Samba/CIFS I would consider using NFS, it should be faster.

hdparm really isn't the best way to test anyways.  Use dd to your array's mount point (in this example it's mounted on /storage)
Write Speed
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
```
Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```
The events count is fine, as long as your array is working as it should be.

It looks like /dev/sdj is using the whole disk rather than the partition.  You should be able to see the superblock like this...
```
mdadm -E /dev/sdj
```

---

### Post by rubylaser on 2011-09-13
> **MarcLocchi said:**
> The plot thickens... I read someone else had this same issue with "no md superblock detected" on one of his array drives, and a reboot fixed it...
 
I try this and find /dev/sdj to be OK now, BUT /dev/sdk has the issue... and this is because the drive numbering is scrambled from last boot (i.e." sdj was drive 10 last time, sdk is drive 10 now)... This has happened because I have an external USB drive plugged in during boot (which was sdl before and it is sdh now)... I can only assume the "problem drive is the same phycial device both times?
 
Anyway, one more thing to learn / fix I guess... thanks for any advice!
 
M
 
PS: write speed over the network still sucks at 40MB/s... while reads are a decent 110MB/s... should I expect this from R6 (as in such a difference in performance?)

Drive order does not matter with mdadm, it uses the superblock data to assemble the array by UUID.  What do you have in your /etc/mdadm/mdadm.conf file?
```
cat /etc/mdadm/mdadm.conf
```

I won't know about the write speeds until you run the dd commands against your mounted array and post back, and also what file sharing protocol you're using.  You should be able to write faster than 40 MB/s if things are working correctly, and you're not using Samba/CIFS (these can be tuned for greater performance though).

---

### Post by MarcLocchi on 2011-09-13
Hi rubylaser, thanks again for the help!! To answer your questions:
 
1. access to superblocks on /dev/sdk shows:
```

[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~# mdadm -E /dev/sdk
/dev/sdk:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f65fe11e:2ae4eb81:1c2f1f32:7af495f1
           Name : LSERVER:0  (local to host LSERVER)
  Creation Time : Sun Sep 11 11:21:49 2011
     Raid Level : raid6
   Raid Devices : 10
 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 31256190976 (14904.11 GiB 16003.17 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f78934f7:71d8dd85:27fd792f:19c7dd96
    Update Time : Wed Sep 14 06:38:10 2011
       Checksum : abaa91e6 - correct
         Events : 19878
         Layout : left-symmetric
     Chunk Size : 512K
   Device Role : Active device 8
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)

```
I gues all this is normal / OK, so why the difference with this drive when running mdadm --detail? This is the drive I addeed to array after first drive failed on rebuild... so maybe I screwed something up? From what you are saying though, this is not a problem and array looks healthy (or did I misunderstand?). Is there anyhing I need to do / fix on this, or is it OK the way it is?
 
Read/Write speeds:
all this seems to be working at good speeds, so here's the results of dd commands:
```

[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~# dd if=/dev/zero of=/mnt/raid/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 44.3643 s, 236 MB/s
 
[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~# dd if=/mnt/raid/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 31.132 s, 337 MB/s

```
 
My mdadm conf was created using "mdadm --detail --scan > /etc/mdadm/mdadm.conf" command as part of raid set up... here's the contents:
```

[EMAIL="root@LSERVER"]root@LSERVER[/EMAIL]:~# cat /etc/mdadm/mdadm.conf
ARRAY /dev/md/0 metadata=1.2 name=LSERVER:0 UUID=f65fe11e:2ae4eb81:1c2f1f32:7af495f1

```
 
Do you know why is it "md/0" rather than "md0"?
 
Lastly re file sharing protocol, 
On the file sharing set up, I installed SAMBA and basically configured general folder access in SMB.conf.  Here's a copy of the file contents. Cannot seem to find how to check which file system it is using:
 
```

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes
# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user
########## Domains ###########
# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = [\\%N\profiles\%U]("file://\\%N\profiles\%U")
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = [\\%N\%U\profile]("file://\\%N\%U\profile")
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = [\\%N\%U]("file://\\%N\%U")
# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd
# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g
########## Printing ##########
# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes
# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap
# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups
############ Misc ############
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY
# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto
# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes
#======================= Share Definitions =======================
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as [\\server\username]("file://\\server\username")
;[homes]
;   comment = Home Directories
;   browseable = no
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700
# By default, [\\server\username]("file://\\server\username") shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to [\\server\username]("file://\\server\username")
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
 
# LHOME Shares
[databu]
    comment = LHOME movies directory
    path = /mnt/raid/databu
    browsable = yes
    huest ok = yes
    read only = no
    create mask = 0777

```
 
how do I check if CIFS is running? I can see the server and folder share from my windows box and this is where I am copying data to / from, only at low speed. I did nothing different in terms of SAMBA set up to prev. installations (other than the NIC bonding)... so not sure how I could not have enabled CIFS (if this is the default file sharing system). I may try disable the bonding and try copying to see how it goes... I will post back.
 
Thanks for all the help!! You are a STAR!!!
 
Marc

---

### Post by rubylaser on 2011-09-13
Everything looks good.  That one disk is using the whole disk rather than a partition, but that's okay.  Your speeds are respectable on your box.  SMB isn't ever going to set speed records for transfer speeds.  I don't have any Windows boxes at home anymore, but depending on your version of windows, you can enable Services for NFS on Windows 7 or on XP, Windows Services for Unix.

Either of those will allow you to mount NFS shares, which should be much faster for file transfers.

Finally, CIFS is an enhanced version of Microsoft's open, cross-platform Server Message Block (SMB) protocol, so you already have support for it.

---

### Post by MarcLocchi on 2011-09-16
Hi rubylaser, final update from me as all working perfect now! I have my 20TB of drives on RAID6 and all working just great! WHat a ride!
 
I fixed the network speed too on writes (I get constant 100MB/s now)... my bonding set up was wrong... 
 
Many thanks for all the help! 
 
Should I close this off with SOLVED although we did not really solve the initial problem (without changing MOBO and hardware 3 times!)
 
Thanks again!
M

---

### Post by rubylaser on 2011-09-16
Yes, I think you should.  I think the problem was really a result of some failing hardware, and a little bit of the learning curve of linux, mdadm, nic bonding, etc.  I'm glad you're working well, and that's one large array.  Hopefully, you have 1 or 2 spares in their in the event of a drive failure.

---

### Post by MarcLocchi on 2011-09-18
OK, the server has been running for a week, perfectly! Thanks for all the help rubylaser and fatbotgw! 
 
I will close this thread as soved!
 
Marc

---

### Post by rubylaser on 2011-09-18
That's great to hear :)  Enjoy, your you shiny new RAID array.

---

