---
title: "Server becoming unstable at random intervals"
date: 2015-12-01
forum: Server Platforms
---

### Post by renny2 on 2015-12-01
Hi All,

Having an issue with my Ubuntu 14.04.3 LTS install that only started happening in the last week.

The first symptom was when attempting to connect via SSH, the server gave the response "Server refused our key" - this was the first time seeing this issue, I pressed the power button a few times to turn off the server and it would not turn off so I had to hold the power button for 6 seconds to shut it down.

The server powered up as expected and operated normally - I connected via SSH and left my connection open.

About 12 hours later services stopped working again, but my SSH session was still active - running the command "ls" would work properly but trying to run "PS AUX" or "df -h" or "reboot" would all respond with a "Input/Output" error - again I had to shut the computer off via 6 seconds of power button.

The OS runs on a single 64GB SSD, there are two raid 0 volumes made up of 2x 3TB Sata HDD's - curiously the Samba network shares were still available to these raid volumes and could be accessed as expected from a Windows Host.

I have run fsck on the OS drive which showed no errors, the SMART data on the OS drive is fine, before the Input/Output errors start happening everything works as expected - Looking for suggestions as to how to diagnose what may be causing the issue or would a re-installation of Ubuntu be a good idea?

Thanks!

---

### Post by ian-weisser on 2015-12-02
Look for patterns. So far, you seem to have spotted that the issue crops up after the system has been powered on for several hours.
Hardware: Look for thermal (lm-sensors), look for bad RAM (memtest), look for dying hard drive (smartmon).
Software: Check /var/log/syslog, /var/log/demsg, and /var/crash for corresponding clues.

---

### Post by tgalati4 on 2015-12-02
Reseat your network cables.  If you have a dual NIC card, use the second ethernet port.  It's possible that your NIC is failing.  Use a different port on your switch.  Check the power supplies on both the server and the switch.

---

### Post by renny2 on 2015-12-03
After a failure DMESG gives this output spammed

[85764.452596] Core dump to |/usr/share/apport/apport 30039 7 0 30039 pipe fail$
[85764.560706] Core dump to |/usr/share/apport/apport 30055 7 0 30055 pipe fail$
[85764.674351] Core dump to |/usr/share/apport/apport 30071 7 0 30071 pipe fail$
[85764.785567] Core dump to |/usr/share/apport/apport 30087 7 0 30087 pipe fail$
[85764.896675] Core dump to |/usr/share/apport/apport 30103 7 0 30103 pipe fail$

sensors say the temps are all fine, around 47c for the CPU with a maximum of 85

acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8 C  (crit = +106.0 C)
temp2:        +29.8 C  (crit = +106.0 C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +47.0 C  (high = +85.0 C, crit = +105.0 C)
Core 0:         +46.0 C  (high = +85.0 C, crit = +105.0 C)
Core 1:         +47.0 C  (high = +85.0 C, crit = +105.0 C)




When the error occured this time...

sudo: unable to open /var/lib/sudo/xxxx/2: Read-only file system
sudo: unable to execute /sbin/reboot: Input/output error

I can't get the smartmon data till I get home later but last time I checked everything was reporting fine from the SMART data on the HDD....

It's only connected via a single NIC, network traffic still operates fine after the issue starts occuring.

I'll run a MEMTEST and see if it causes the issue again.

---

### Post by tgalati4 on 2015-12-03
This does not look good.  *Apport* is the framework for reporting application crash dumps.  In your first case, the crash dump could not be formatted for sending through *apport*.  In the second case, you encountered a read-only file system, which normally happens when the file system in unclean (requires an *fsck* to clean).  Since your SMART parameters of your disk check out, perhaps check the cabling to the disk.  Change SATA ports.

It's possible that your motherboard is failing or you have a SATA controller problem that is causing I/O errors.  The fact that you are getting multiple, different, and unhelpful log messages is consistent with a hardware issue.  Single, repeatable, helpful log messages would indicate a software error.

---

### Post by renny2 on 2015-12-03
smartctl completed an extended test without any errors and memory test completed 4 passes without any issue.

It seems strange that the issue will only occur after a certian time period of operation, I might try and reinstall the OS and swap the SATA port and see if that resolves the issue but it's a good point that the motherboard or SATA controller may be failing (the 4x 3TB SATA HDD's do seem to be operating ok even after the fault occurs though).

---

### Post by tgalati4 on 2015-12-03
Your PSU may be failing as it gets hot.  4 spinners requires a lot of 12VDC current.  Try a new or different PSU.

---

### Post by renny2 on 2015-12-03
its a 500 watt power supply  [FONT=arial]SilverStone ST50F-ES which has 34A on the 12v rail.

All that is connected via the 12V rail is 4x Spinning HDDs and 1x SSD

The CPU is just an i3 3225 which has a TDP of 55Watts

I mean it could be a faulty PSU but I would expect the Spinning drives to stop operating if there was an issue with the 12V rail, but these remain usable after the issue occurs and no read/writes are working to the OS drive.

Thanks for the suggestions so far![/FONT]

---

### Post by tgalati4 on 2015-12-03
AC noise bleeding from the PSU can cause the motherboard to have issues.  Unless you have an oscope to view the power, how else can you test it?

Rather than reinstall, make a LiveBoot USB of 14.04.  Run that for a few days.  If you get lockups, then that would be consistent with a hardware problem.  If you don't, then wipe the SSD and reinstall.

---

### Post by renny2 on 2015-12-03
Good idea, but if the issue is the SATA controller this would also not present a problem?

---

### Post by tgalati4 on 2015-12-04
True, you can only isolate certain components, like the SATA controller and disks, when you use a LiveBoot USB stick.  If you have a second hard disk, SSD or spinner, you can install it and put on the OS and test it.  If you get erratic behavior, then that would point to a motherboard/SATA controller issue.

---

### Post by renny2 on 2015-12-04
So I manged to get the error messages that are produced from dmesg, the server operated fine for 17 hours then all of a sudden the hard drive is mounted as read only again.

[65250.364516] ata6.00: exception Emask 0x10 SAct 0x3 SErr 0x400100 action 0x6 frozen
[65250.364522] ata6.00: irq_stat 0x08000000, interface fatal error
[65250.364525] ata6: SError: { UnrecovData Handshk }
[65250.364529] ata6.00: failed command: WRITE FPDMA QUEUED
[65250.364535] ata6.00: cmd 61/10:00:40:a2:ab/00:00:05:00:00/40 tag 0 ncq 8192 out
[65250.364535]          res 40/00:08:60:a2:ab/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[65250.364537] ata6.00: status: { DRDY }
[65250.364540] ata6.00: failed command: WRITE FPDMA QUEUED
[65250.364545] ata6.00: cmd 61/08:08:60:a2:ab/00:00:05:00:00/40 tag 1 ncq 4096 out
[65250.364545]          res 40/00:08:60:a2:ab/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[65250.364547] ata6.00: status: { DRDY }
[65250.364552] ata6: hard resetting link
[65250.684098] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[65250.696092] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[65250.696101] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff880214bcc730), AE_NOT_FOUND (20131115/psparse-536)
[65250.706073] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[65250.706078] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff880214bcc730), AE_NOT_FOUND (20131115/psparse-536)
[65250.706121] ata6.00: configured for UDMA/133
[65250.706129] ata6: EH complete

This above repeats twice, then the following is displayed.

[65446.286626] ata6: limiting SATA link speed to 1.5 Gbps
[65446.286633] ata6.00: exception Emask 0x10 SAct 0x1 SErr 0x400100 action 0x6 frozen
[65446.286636] ata6.00: irq_stat 0x08000000, interface fatal error
[65446.286639] ata6: SError: { UnrecovData Handshk }
[65446.286643] ata6.00: failed command: WRITE FPDMA QUEUED
[65446.286649] ata6.00: cmd 61/30:00:a0:ea:0e/00:00:03:00:00/40 tag 0 ncq 24576 out
[65446.286649]          res 40/00:00:a0:ea:0e/00:00:03:00:00/40 Emask 0x10 (ATA bus error)
[65446.286652] ata6.00: status: { DRDY }
[65446.286657] ata6: hard resetting link
[65446.869628] ata6: SATA link down (SStatus 0 SControl 310)
[65446.875122] ata6: hard resetting link
[65447.309237] ata6: SATA link down (SStatus 0 SControl 310)
[65447.309242] ata6.00: link offline, clearing class 1 to NONE
[65447.369436] ata6: hard resetting link
[65448.164404] ata6: SATA link down (SStatus 0 SControl 310)
[65448.164410] ata6.00: link offline, clearing class 1 to NONE
[65448.164412] ata6.00: disabled
[65448.164425] sd 5:0:0:0: [sde]
[65448.164426] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[65448.164427] sd 5:0:0:0: [sde]

[65448.164428] Sense Key : Aborted Command [current] [descriptor]
[65448.164430] Descriptor sense data with sense descriptors (in hex):
[65448.164431]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
[65448.164436]         03 0e ea a0
[65448.164438] sd 5:0:0:0: [sde]
[65448.164439] Add. Sense: No additional sense information
[65448.164441] sd 5:0:0:0: [sde] CDB:
[65448.164441] Write(10): 2a 00 03 0e ea a0 00 00 30 00
[65448.164446] end_request: I/O error, dev sde, sector 51309216
[65448.164464] ata6: EH complete
[65448.164470] ata6.00: detaching (SCSI 5:0:0:0)
[65448.164485] Aborting journal on device dm-0-8.
[65448.164503] Buffer I/O error on device dm-0, logical block 6324224
[65448.164505] lost page write due to I/O error on dm-0
[65448.164510] Buffer I/O error on device dm-0, logical block 0
[65448.164512] lost page write due to I/O error on dm-0
[65448.164515] JBD2: Error -5 detected when updating journal superblock for dm-0-8.
[65448.164517] EXT4-fs error (device dm-0): ext4_journal_check_start:56: Detected aborted journal
[65448.164518] EXT4-fs (dm-0): Remounting filesystem read-only
[65448.164520] EXT4-fs (dm-0): previous I/O error to superblock detected
[65448.164524] Buffer I/O error on device dm-0, logical block 0
[65448.164525] lost page write due to I/O error on dm-0
[65448.165497] end_request: I/O error, dev sde, sector 0
[65448.166665] sd 5:0:0:0: [sde] Synchronizing SCSI cache
[65448.166695] sd 5:0:0:0: [sde]




Any thoughts? :S

---

### Post by ian-weisser on 2015-12-04
Seems like the disk, the cable, or the control chip on the motherboard. Time to swap components until you determine which is bad.

---

### Post by renny2 on 2015-12-04
good plan, if it were the control chip would it not be expected that the other hard drives would also be mounted in Read Only? yet they remain writable when the issue occurs.

---

### Post by renny2 on 2015-12-04
Swapped over the Cable + Sata Port, will see if the issue occurs again :)

---

### Post by tgalati4 on 2015-12-05
I would only be satisfied with 600+ days of uptime, not 17 hours.

---

### Post by renny2 on 2015-12-06
Seems the issue has been resolved with new SATA port + SATA Cable....

Pretty strange issue for it to operate for X amount of hours before crashing and then operate OK again after rebooting!

---

