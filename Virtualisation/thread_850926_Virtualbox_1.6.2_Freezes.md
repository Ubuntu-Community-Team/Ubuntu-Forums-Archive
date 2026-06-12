---
title: "Virtualbox 1.6.2 Freezes"
date: 2008-07-06
forum: Virtualisation
---

### Post by lightnb on 2008-07-06
I'm running Ubuntu 8, with Virtualbox 1.6.2.

When trying to install WinXP as the guest OS, the entire system freezes. 

The last few lines of the log file:

```

00:00:56.368 Guest Log: BIOS: Booting from CD-ROM...
00:00:57.512 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:02:42.928 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:02:46.879 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xc4 (-1 usec ago)
00:02:46.879 PIIX3 ATA: LUN#0: aborting current command
00:02:50.933 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=396 bpp=0 cbLine=0x0
00:04:03.290 PATM: Stop monitoring IDT handler pages at 89be7044 - invalid write 89be72f4-89be72f6 (this is not a fatal error)
00:04:03.315 PATM: Stop monitoring IDT handler pages at 89be73ac - invalid write 89be72f4-89be72f6 (this is not a fatal error)
00:05:15.852 TM: Giving up catch-up attempt at a 65985113502 ns lag; new total: 65985113502 ns
00:06:47.281 TM: Giving up catch-up attempt at a 91091094736 ns lag; new total: 157076208238 ns
00:07:52.983 TM: Giving up catch-up attempt at a 64027745372 ns lag; new total: 221103953610 ns
00:08:55.505 TM: Giving up catch-up attempt at a 63277904017 ns lag; new total: 284381857627 ns
00:09:55.495 TM: Giving up catch-up attempt at a 60012414978 ns lag; new total: 344394272605 ns
00:11:34.515 TM: Giving up catch-up attempt at a 99498228362 ns lag; new total: 443892500967 ns
00:13:16.077 TM: Giving up catch-up attempt at a 98874244881 ns lag; new total: 542766745848 ns
00:14:17.762 TM: Giving up catch-up attempt at a 61386624883 ns lag; new total: 604153370731 ns
00:15:48.007 TM: Giving up catch-up attempt at a 90146700044 ns lag; new total: 694300070775 ns
00:16:51.454 TM: Giving up catch-up attempt at a 63120535169 ns lag; new total: 757420605944 ns
00:17:59.975 TM: Giving up catch-up attempt at a 67991430372 ns lag; new total: 825412036316 ns
00:18:59.899 TM: Giving up catch-up attempt at a 63371399670 ns lag; new total: 888783435986 ns
00:20:35.021 TM: Giving up catch-up attempt at a 93093408813 ns lag; new total: 981876844799 ns
00:21:58.406 TM: Giving up catch-up attempt at a 70534147322 ns lag; new total: 1052410992121 ns
00:23:03.988 TM: Giving up catch-up attempt at a 79882390942 ns lag; new total: 1132293383063 ns

```

---

### Post by lightnb on 2008-07-07
I'm running VB 1.6.0 on my laptop, and that's working fine. Is there anyway to force apt-get to install an older version?

---

### Post by ene_dene on 2008-07-07
I have 1.6.2 and winXP it and I'm not experiencing any problems.

---

### Post by lightnb on 2008-07-07
> **ene_dene said:**
> I have 1.6.2 and winXP it and I'm not experiencing any problems.

On my computer, the virtual machine causes the entire system to freeze. CTRL + ALT + BACKSPACE does nothing. The power has to be switched off and back on. It's been freezing when the hard drive formating reaches "100%", but has frozen in other places too.

I've read that older versions check for 'something' that 1.6.2 doesn't. If you had an older version and upgraded, the old version would have made you install or change that 'something', so it was already set correctly when you upgraded.

Since I'm fresh installing 1.6.2, that has the bug where the 'something check' isn't performed, I'm missing that 'something' but the program isn't catching it and isn't throwing an error like its supposed to.

So I need to know what that 'something' is, that I need to install or set.

---

### Post by ene_dene on 2008-07-07
I really don't know what could be the problem. You did download the version for Hardy from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)  ?
Try reinstalation of virtual box.

---

### Post by HotShotDJ on 2008-07-07
How much memory have you given the VM and how large is the virtual harddrive that you created for XP?

---

### Post by lightnb on 2008-07-08
> **HotShotDJ said:**
> How much memory have you given the VM and how large is the virtual harddrive that you created for XP?

Virtual Size: 20 G, Actual Size: 69 M
Memory: 2 G

I dropped the memory down to 1 GB, and it seems to be working.

I'm guessing that the memory option isn't "memory allowed" but is actually "memory reserved"?

How much memory can I safely allocate? (or rather, how much do I need to leave for the host machine?)

---

### Post by HotShotDJ on 2008-07-08
> **lightnb said:**
> Virtual Size: 20 G, Actual Size: 69 M
Memory: 2 G

I dropped the memory down to 1 GB, and it seems to be working.

I'm guessing that the memory option isn't "memory allowed" but is actually "memory reserved"?

How much memory can I safely allocate? (or rather, how much do I need to leave for the host machine?)Ok... yeah... that was your problem.  You must leave at least 512 MB (Preferably 1 G) for the host.  Any RAM that you assign to the VM will NOT be available to the host OS while the VM is running.

If you have 2 Gig installed memory, then 1 GB for the VM is a sane number.

---

