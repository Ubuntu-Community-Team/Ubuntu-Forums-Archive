---
title: "Accessing HDD via Firewire"
date: 2012-10-11
forum: Ubuntu Studio
---

### Post by pburyk on 2012-10-11
Greetings Everyone!
 
I've been trying to access a HDD via Firewire and can't seem to get it up and running.
Here is some config info:
- Dell Precision M4600 (has 1394 connector), running Ubuntu Studio 12.04 - 3.2.0-30-generic-pae #48-Ubuntu SMP
 
- lsmod command shows:
firewire_ohci 40172 1 firewire_ohci
firewire_core 56906 1 firewire_core
 
- ls -l /dev/sd* shows:
... /dev/sda
... /dev/sda1
... /dev/sda2
... /dev/sda5
 
- ls -l /dev/dsk/by-id :
only lists the above shown system disk and DVD reader
 
- ps -ef shows:
root ... [firewire]
root ... [firegl]
root ... [firegl]
root ... [firegl]
 
- dmesg shows that device fw0 has been created. But
od -c /dev/fw0 produces no output when HDD is attached and powered up
(yes, /dev/fw0 is readable - chmod 644 /dev/fw0)
 
So... At this point I'm wondering if the dang FireWire port is even working.
Any ideas of how I might confirm that it is indeed conf'd properly in the OS
to handle HDD and to monitor I/O across that interface???
 
Thanks much, in advance!!!
Patrick
 
[EMAIL="PBuryk@Gmail.com"]PBuryk@Gmail.com[/EMAIL]

---

### Post by pburyk on 2012-10-11
Just thought I'd add some information about the target application I'm running and why
I'm trying to establish this particulat configuration...
 
My main use of Ubuntu-Studio is for multi-track recording. I will be using both
Ardour and Audacity to post-process 24-bit WAVE files recorded on an Alesis HD24.
I'm currently obtaining those WAVE files via FTP connection (using FileZilla) between
the HD24 and Dell computer. But that connection is sllllooooowwwwwwww... due to
the implementation of FTP on the HD24 and its 10Mbs interface. A much better option
would be to use my Alesis FirePort interface... which requires the FireWire interface
to be working (and so my previous post). An even better option would be to use a
VIPower external disk docking chassis w/ USB2 interface... but they are virtually
IMPOSSIBLE to find. So... there you have it.... If any readers have any better ideas,
I am certainly open to them!!!!
 
-pb

---

### Post by pburyk on 2012-10-11
Information update:
 
I just noticed the following diag messages accumulating while the external disk is
attached with power on:
 
In /var/log/syslog:
 
... kernel: firewire_ohci: inconsistent self IDs
... kernel: firewire_core: skipped bus generations, destroying all nodes
... kernel: firewire_core: rediscovered device fw0
... kernel: firewire_ohci: inconsistent self IDs
.
.
.
... kernel: firewire_core: topology build failed
 
Occasionally I also get:
 
... kernel: firewire_core: Parent port inconsistency for node 0: parent_count=1
 
and
 
... kernel: filrewire_core: giving up on config rom for noe id ffc0
 
Shut of power to disk and the above diags stop.
Power disk back on and they start being logged again.
 
Various other accounts in Google searches cite these errors but don't really 
address them for resolve in this particular situation and config.
 
-pb

---

### Post by sgx on 2012-10-12
[http://www.gearslutz.com/board/remote-possibilities-acoustic-music-location-recording/584934-can-i-copy-audio-alesis-hd24-hd.html](http://www.gearslutz.com/board/remote-possibilities-acoustic-music-location-recording/584934-can-i-copy-audio-alesis-hd24-hd.html)

[http://tech.groups.yahoo.com/group/hd24/](http://tech.groups.yahoo.com/group/hd24/)

[http://ringbreak.dnd.utwente.nl/~mrjb/hd24tools/download.html](http://ringbreak.dnd.utwente.nl/~mrjb/hd24tools/download.html)

I would look at the case, if it is easy to open,
you may be able to modify the case by creating a hatch,
to simplify exchanging drives. The gearslutz article ends
in success, and mentions the donationware to deal with
the drive format differences, and the yahoo group
may be helpful on the hardware portions. Firewire would
not be needed.
Cheers

---

### Post by pburyk on 2012-10-12
SGX -
 
Yes... I've been to all the sites you posted. I already have HD24tools - works great on
my Windows machine (so does the Fireport firewire interface, by the way)... But that
is not the nut I'm trying to crack here. I invested in the Dell Precision and Ubuntu
Studio config in order to have a more robust and reliable multi-track plaform so I'd
really prefer to resolve the Ubuntu/Firewire access problem it that is possible.
 
Also... Just to express a personal position... It is never a good idea to uncase actively
used HDDs as part of an every-day data-transfer operation. The possibilities of 
fumbling the handling of the disk and portential damage to a portion of its exposed
circuit board by physical contact or static discharge are huge. The HD24's disks are
contained within a caddy that is designed to be extracted from the HD24 chassis
(they are "hot-swappable" w/ centronics type connectors on the caddy) and then
re-inserted into some other mating chassis, like what VIPower has produced in the
past. A VIPower external chassis (connecting to me Dell Precision laptop via USB2
cable) would be an ideal alternative to my currently non-functional FirePort.
But, like I mentioned earlier, the right VIPpower chassis (as there are various types)
is very hard to find!
 
Thank you for your suggestions!
-pb

---

### Post by sgx on 2012-10-12
Did you try the linux version of the HD24Tools?

A few options, one of which is installing the newest KX Studio
packages. Another is trying older ubuntu versions, maybe 10.04
with differing ffado firewire support.
Like usb, the qjackctl Periods/Buffer should be 3

Looking at your proprietary parts high market value, and
the low cost of trouble-free linux compatible alternatives,
I would undercut the many ebay HD24 units now offered,
in a BIN sale, and then get three or four matching and
fast hard disks, using bog standard sata pci and usb
connections, with proven linux compatible m-audio
Delta pci cards. The AVLinux maintainer has used a pair
of Delta 1010 pci cards, as have a few others, for lots
of quality i/o, and simple config, using the ice_1712
kernel module.

Also Trulan has solved a lot of firewire queries, searching
google for
trulan ubuntu firewire
should bring up some useful threads.
Cheers

---

### Post by jejeman on 2012-10-13
Hope this helps somehow:

 /dev/fw0 is your firewire card (controler)

any plugin device should be

 /dev/fw1,  /dev/fw2 etc. at least that is the case with camcoders and audio cards, maybe HDD works different.

So, your device is not detected by firewire stack or it can't create a node. First you need to get firewire node, then you can try to make it work.
I don't know how you can do that.

---

### Post by pburyk on 2012-10-15
sgx -
Thanks for all the info.. I will certainly look into the alternatives you offered...
Especially the Trulan link! Seems he has a LOT of Firewire experience.
 
-pb

---

### Post by pburyk on 2012-10-15
jejeman -
Yup! You are correct about the additional /dev/fw* nodes.
No... I all see here is /dev/fw0
So I suspect not being able to create required nodes is part of the problem.
 
Thanks!
-pb

---

### Post by pburyk on 2012-10-18
Well... It's been a real productive day here...
On a whim, I decided to pick up yet another Firewire cable while I was near my local RadioShack earlier this morning.
That ended up being the key to (all?) my problems with my Alesis FirePort, HD24tools and Ubuntu Studio 12.04.
I've pasted in some pertinent info, below, so it might help anyone else who has been laboring over this config.
*** Sorry about all the additional blank lines... I was just tring to help make some parts of this more readable.
Thanks to everyone for their postings to HD24 Group articles about this - ESPECIALLY - to those who recently
reminded us that (sometimes) cables really do go bad!!!!
Patrick
---------------------------------------------------------------------------------------------------------------
# First - - - Obtain "GigaWare" FireWire cable (PN/1500006 [03A11]).
# This cable has a "standard 6-pin" plug on one side and a smaller "4-pin" plug on the other.
# Connect the Firewire cable to the Alesis FirePort - LEFT-side FireWire socket.
# Attach Disk Caddy to FirePort
# Power to FirePort is - OFF
&#12288;
# Open up a terminal window and monitor the Syslog:
$ tail -f /var/log/syslog
# Plugin in the Firewire cable to the laptop:
Oct 18 15:49:34 patrick-Precision-M4600 kernel: [ 201.856912] firewire_ohci: Register access failure - please notify [EMAIL="linux1394-devel@lists.sf.net"]linux1394-devel@lists.sf.net[/EMAIL]
# Turn on power to the FirePort:
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 222.778842] firewire_core: created device fw1: GUID 0010100340000000, S400, 2 config ROM retries
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 222.778856] firewire_core: phy config: card 0, new root=ffc0, gap_count=5
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 222.838474] scsi6 : SBP-2 IEEE-1394
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.037819] firewire_sbp2: fw1.0: logged in to LUN 0000 (0 retries)
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.038461] scsi 6:0:0:0: Direct-Access Initio ST340014A 4.43 PQ: 0 ANSI: 0
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.039022] sd 6:0:0:0: Attached scsi generic sg2 type 0
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.039277] sd 6:0:0:0: [sdb] 78125000 512-byte logical blocks: (40.0 GB/37.2 GiB)
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.039510] sd 6:0:0:0: [sdb] Write Protect is off
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.039522] sd 6:0:0:0: [sdb] Mode Sense: 86 0b 00 02
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.039746] sd 6:0:0:0: [sdb] Missing header in MODE_SENSE response
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.039995] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.041475] sd 6:0:0:0: [sdb] Missing header in MODE_SENSE response
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.066251] sdb: unknown partition table
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.067476] sd 6:0:0:0: [sdb] Missing header in MODE_SENSE response
Oct 18 15:49:55 patrick-Precision-M4600 kernel: [ 223.067708] sd 6:0:0:0: [sdb] Attached SCSI disk
# Startup the HD24connect program... Still no drive detected.
$ cd /dev
$ sudo chmod 666 sdb # /dev/sdb and /dev/fw1 were created when I powered on the FirePort, but were not readble by user community "other".
# The drive is now detected by the HD24connect program!!!!!!!!
---------------------------------------------------------------------------------------------------------------------
# Here are some helpful pieces of information about my config:
$ ls -ld /dev/fw* /dev/sd*
crw------- 1 root root 251, 0 Oct 18 11:46 /dev/fw0
crw------- 1 root root 251, 1 Oct 18 15:49 /dev/fw1
brw-rw---- 1 root disk 8, 0 Oct 18 11:46 /dev/sda
brw-rw---- 1 root disk 8, 1 Oct 18 11:46 /dev/sda1
brw-rw---- 1 root disk 8, 2 Oct 18 11:46 /dev/sda2
brw-rw---- 1 root disk 8, 5 Oct 18 11:46 /dev/sda5
brw-rw-rw- 1 root disk 8, 16 Oct 18 15:49 /dev/sdb
&#12288;
&#12288;
$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
Vendor: ATA Model: WDC WD7500BPKT-7 Rev: 01.0
Type: Direct-Access ANSI SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
Vendor: TSSTcorp Model: DVD+-RW TS-U633J Rev: D800
Type: CD-ROM ANSI SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
Vendor: Initio Model: ST340014A Rev: 4.43
Type: Direct-Access ANSI SCSI revision: 00
&#12288;
&#12288;
$ lsmod | grep fire
firewire_sbp2 18346 1 
firewire_ohci 40172 0 
firewire_core 56906 2 firewire_sbp2,firewire_ohci
crc_itu_t 12627 1 firewire_core
&#12288;
&#12288;
$ find /dev/disk -exec ls -ld {} \;
drwxr-xr-x 5 root root 100 Oct 18 11:46 /dev/disk
&#12288;
drwxr-xr-x 2 root root 80 Oct 18 11:46 /dev/disk/by-uuid
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-uuid/511c1c5e-611b-459a-88e1-39a18de8c8c0 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-uuid/82e93de6-0625-4c3f-bbf7-8ed5b56c176f -> ../../sda5
&#12288;
drwxr-xr-x 2 root root 160 Oct 18 15:49 /dev/disk/by-path
lrwxrwxrwx 1 root root 9 Oct 18 15:49 /dev/disk/by-path/pci-0000:0b:00.0-ieee1394-0x0010100340000000:00042c:0000 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 9 Oct 18 11:46 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 9 Oct 18 11:46 /dev/disk/by-path/pci-0000:00:1f.2-scsi-3:0:0:0 -> ../../sr0
&#12288;
drwxr-xr-x 2 root root 320 Oct 18 15:49 /dev/disk/by-id
lrwxrwxrwx 1 root root 9 Oct 18 15:49 /dev/disk/by-id/ieee1394-0010100340000000:00042c:0000 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/wwn-0x50014ee6571bf16b-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/scsi-SATA_WDC_WD7500BPKT-_WD-WX71A9131931-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/ata-WDC_WD7500BPKT-75PK4T0_WD-WX71A9131931-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/wwn-0x50014ee6571bf16b-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/scsi-SATA_WDC_WD7500BPKT-_WD-WX71A9131931-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/ata-WDC_WD7500BPKT-75PK4T0_WD-WX71A9131931-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/wwn-0x50014ee6571bf16b-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/scsi-SATA_WDC_WD7500BPKT-_WD-WX71A9131931-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 18 11:46 /dev/disk/by-id/ata-WDC_WD7500BPKT-75PK4T0_WD-WX71A9131931-part2 -> ../../sda2
lrwxrwxrwx 1 root root 9 Oct 18 11:46 /dev/disk/by-id/wwn-0x50014ee6571bf16b -> ../../sda
lrwxrwxrwx 1 root root 9 Oct 18 11:46 /dev/disk/by-id/scsi-SATA_WDC_WD7500BPKT-_WD-WX71A9131931 -> ../../sda
lrwxrwxrwx 1 root root 9 Oct 18 11:46 /dev/disk/by-id/ata-WDC_WD7500BPKT-75PK4T0_WD-WX71A9131931 -> ../../sda
lrwxrwxrwx 1 root root 9 Oct 18 11:46 /dev/disk/by-id/ata-TSSTcorp_DVD+_-RW_TS-U633J_R7216GVBB67837 -> ../../sr0
----------------------------------------------------------------------------------------------------------
In Summary:
- It seems that the (2) "standard" 6-pin to 6-pin Firewire cables might be faulty... or
The (2) 6-pin to 4-pin adapter blocks I have are faulty. I've tried all combinations of
these components and my original problem symptons did not change.
- My new GigiWare cable resolved my Firewire base HDD detection problem.
- I did not have to load and new software or drivers to Ubuntu Studio 12.04.
What came with the release is now working.
- I am currently using HD24tools, version: 1.1.0betaRC2 (the download for Linux OS).
- I can transfer files from the HD24 disk on to my Linux desktop work area.
I have not tried to copy files from Linux to HD24 disk yet though... maybe later tonight.
- There are (2) features in HD24tools that (apparently) are not support to either this release
or to Linux in general. They are:
- The Recorder will not allow you to actually play back the WAV files on the disk.
The "info" tab states:
- HD24connect system info
JACK: Not Present
LIBSNDFILE: Loaded
PORTAUDIO: Not Present
Fine by me (for now)... The newly gained time savings in transferring HD24 WAV files alone
makes this option a blessing!!
&#12288;
Patrick
&#12288;
&#12288;

---

