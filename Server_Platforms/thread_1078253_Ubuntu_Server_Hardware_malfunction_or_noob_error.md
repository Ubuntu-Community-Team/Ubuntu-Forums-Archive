---
title: "Ubuntu Server: Hardware malfunction or noob error?"
date: 2009-02-23
forum: Server Platforms
---

### Post by shokks on 2009-02-23
Apologies for the post being long, being a noob, I dont want to miss out on anything which may have been the cause of trouble.:)

I have been using Ubuntu Desktop for more than a year now. With a very good experience working on it, I have been thinking why not try setting up a server which would act as a 
[LIST]
[*]File server
[*]back up
[*]torrent
[*]myth TV backend (perhaps later on)
[/LIST]
To think of it, I also had in the back of my mind a need to connect to my box from outside home network to access my music etc. 

I must admit, a lot of the commands that I type are still copied from what I read on internet to solve a problem, without really able to understand the nitty gritty of "what the heck does this actually do?".

But well one always learns by doing so.

So after spending couple of weeks in reading different material on hardware choices which fitted my pocket, low energy consuming, silent and also comparatively fast, I came to this configuration.
[LIST]
[*]Intel Pentium E5200, Dual Core, 2.5 GHz, 2MB
[*]Asus P5N73-CM, nForce 630i, VGA, DVI, mATX, LGA 775
[*]Western Digital Caviar GP, 7200rpm, 32MB, 1TB, SATA-II
[*]Seasonic S12II-380HB Energy Plus Series 80-Plus, 380 Watt
[*]Corsair 1GB DDR2-667 (taken from desktop computer as of now)
[/LIST]

This Friday I put the things together. Also I attached an old drive to read the Intrepid Server CD. As I booted, it went ahead fine till I hit "partioning drives" where it got stuck at 33%. I thought the HDD being 1TB perhaps is the reason for it taking so long. I went ahead to sleep. Next morning it was still at 33%. Whole day I tried various possibilities, like, changing the SATA port which the HDD was connected, inserted windows CD to delete the partition table to start fresh again with Ubuntu CD. Nada.

At the end I read on some forum that perhaps the kernel has something to do with the chipset, and to test Hardy instead of the Intrepid server. So again I went on to download the Hardy server LiveCd.

Installation this time went fine as it proceeded to partition the whole disc: 998GB as / and the rest as swap.

Everything went honky dory, I was in seventh heaven.:p
Installed sshserver, installed Samba, and webmin.

Upon logging in with Webmin, I find disc usage to be 49GB. Whereas the only thing that should be on the disc is Hardy Server installation, and that **should not** be so big!! (Note for myself, find out a command commandline to find disc usage, so that this information is webmin independent.)

Next tried installing torrentflux which required LAMP. Oh boy, that was not good! I started getting "segmentation errors" on the console. After that sometimes even "sudo apt-get update" also throws me segmentation errors.

My questions:
[LIST]
[*]Does someone have any idea whether my hardware is incompatible with Kernel or with each other?
[*]Possible changes in hardware or software which I might make so that it works smoothly as it is intended to?
[*]Any other ideas or notes which you would like to pass on to me, for improving my setup?
[/LIST]

Thanks a lot in advance for reading this long post. I hope one (or perhaps many) may have suggestions which may make this machine work better!:)

---

### Post by yoyoned on 2009-02-23
Your drive may be failing.  look in /var/log/messages for drive errors.

---

### Post by shokks on 2009-02-24
Thanks a lot yoyoned. I would definitely look into it once I get back home. Though I don't know what messages I am going to get, I am hoping it would be similar to "error I/O ... something something". I bought the HDD last Friday so its not even 4 days old, it would not be difficult to get it changed.

Sorry if I sound dumb, but by "drive may be failing" you mean hard disc and not the CD drive, isn't it? 

I ask this since someone at work mentioned it could also be the old CD drive that I am using to read the installer CD, or even perhaps the CD has to be written at low speed!

---

### Post by shokks on 2009-02-26
update: 
could not reach the /var/log directory without an install (perhaps there are ways but I was too damn frustrated). So attached the HDD with another computer with windows and tried checking for errors in the ext3 partition (and also formatting the whole HDD with NTFS) with partionmagic. Could not go ahead due to errors. :mad:

So
[LIST=1]
[*] Switched to command prompt in windows
[*] formatted the whole darn thing with NTFS
[*] ran chkdsk, no errors
[*] put it back in the server machine
[*] ran ubuntu server edition 8.04 again, choosing "select entire drive"
[*] installer ran like a charm with no problems.
[/LIST]

Does someone:
[LIST=2] 
[*] think that there is still possibility of errors in the HDD?  
[*] point me to a fool proof way of testing it in CLI in ubuntu server
[/LIST]

I am a little worried to be stuck with a faulty HDD (if at all it is) on the server which might go bust any moment at later date. Thanks in advance.

---

### Post by shokks on 2009-03-12
Bump.
sorry to bump this thread. I have somehow managed to install ubuntu server on the machine, but still 2-3 times a day, it starts giving "segmentation error" on apt-get or other commands. Sometimes "sync fail panic".
Can someone guide me to a solution, I hate to have my headless server suffer like this!:( Thanks a tonne in advance.

---

### Post by hyper_ch on 2009-03-12
> 
Upon logging in with Webmin, I find disc usage to be 49GB. Whereas the only thing that should be on the disc is Hardy Server installation, and that **should not** be so big!! (Note for myself, find out a command commandline to find disc usage, so that this information is webmin independent.)
5 % of the diskspace are reserved for root so that root always have enough space to login and correct things.

without logs or knowing what you setup and what the exact error is, nobody can help you.

---

### Post by BkkBonanza on 2009-03-12
A segmentation error is not generally related to disk problems. It could be in some cases but not directly. It may be worth removing and re-seating your RAM modules to see if that helps just to be sure you don't have memory issues. Generally segmentation errors for me have been relatedd to software libraries out of sync with programs. So be sure that everything is updated. I would not expect those kind of errors with fresh installs unless you have been doing unusual things with software. 

The advice to check /var/log/messages above is always a good place to see what may be going on. You can use a command like 

less /var/log/messages 

to view that file. If it says you don't have permission then just use sudo like,

sudo less /var/log/messages

Once open hit End key to go to end and start browsing back up with PgUp to look for anything that seems odd. Data errors, drive errors, CRC errors etc. If you knew what you were looking for you could use grep to locate it quickly but otherwise browsing works. 

Your hardware sounds decent enough and I can't see off hand any reason why Ubuntu would not be totally fine with it - unless there is some hw faults.

You asked about disk usage. The command for seeing how much of your file systems are used is

df -h

and if you want to know exactly where the big usage is then something like 

du -h

would be useful, though even more so if you do it like this,

du --max-depth=1 -h /

which will give you a top level summary. See the manual for more,

man du

Hope this all helps, though I suspect you'll need more than just this.

---

### Post by shokks on 2009-03-13
Thanks a tonne for the replies. I am really hitting wall here. As for the funny HDD eating up 49GB, its gone after I was able to fresh install again. But I have noted the commands if it ever tries to jump at me.

@hyper_ch: Yes I do see your point, all I have been able to write here is my system configuration and some particular problems. So debugging is perhaps not possible. Call me a BIG noob, but I have not been able to get the output of all these /var/log/messages to my clipboard and paste here.:( But only some part of it.

@bkk_bonaza: Your hints were helpful to point me to do 'something' fruitful atleast. started reading my log messages like "Memento". Well, thought the things below might be of interest, but I may be completely wrong. Bear with me.

```

Mar 13 19:32:03 shire kernel: [   18.932825] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932827] system 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932829] system 00:01: iomem range 0x37000000-0x3effffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932833] system 00:02: ioport range 0xb78-0xb7b has been reserved
Mar 13 19:32:03 shire kernel: [   18.932834] system 00:02: ioport range 0xf78-0xf7b has been reserved
Mar 13 19:32:03 shire kernel: [   18.932836] system 00:02: ioport range 0xa78-0xa7b has been reserved
Mar 13 19:32:03 shire kernel: [   18.932838] system 00:02: ioport range 0xe78-0xe7b has been reserved
Mar 13 19:32:03 shire kernel: [   18.932839] system 00:02: ioport range 0xbbc-0xbbf has been reserved
Mar 13 19:32:03 shire kernel: [   18.932841] system 00:02: ioport range 0xfbc-0xfbf has been reserved
Mar 13 19:32:03 shire kernel: [   18.932843] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 13 19:32:03 shire kernel: [   18.932844] system 00:02: ioport range 0x294-0x297 has been reserved
Mar 13 19:32:03 shire kernel: [   18.932846] system 00:02: ioport range 0x295-0x296 has been reserved
Mar 13 19:32:03 shire kernel: [   18.932848] system 00:02: ioport range 0x880-0x88f has been reserved
Mar 13 19:32:03 shire kernel: [   18.932854] system 00:0b: iomem range 0xf0000000-0xf1ffffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932858] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
Mar 13 19:32:03 shire kernel: [   18.932860] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932862] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932864] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932866] system 00:0c: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932868] system 00:0c: iomem range 0x3fef0000-0x3fefffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932870] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932872] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932873] system 00:0c: iomem range 0x100000-0x3feeffff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932875] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932877] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.932879] system 00:0c: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Mar 13 19:32:03 shire kernel: [   18.963118] PCI: Bridge: 0000:00:0a.0
Mar 13 19:32:03 shire kernel: [   18.963120]   IO window: c000-cfff
Mar 13 19:32:03 shire kernel: [   18.963123]   MEM window: efb00000-efbfffff

```

Do they indicate that my memory might be the culprit? I ordered 4gigs of Corsair memory so as to be able to isolate where the problem lies.



Another quick question, how does someone copy the whole log on clipboard and paste it here? I am accessing my headless server via ssh-putty or ubuntu CLI from my notebook.

Thanks a lot, you guys are really edging me to hang on, when I feel that the branch is too thin to hold me!!:)

---

### Post by hyper_ch on 2009-03-13
run memcheck... it's on the install cd - one of the menu points at boot up from it.

---

### Post by cariboo on 2009-03-14
It might be better to direct the output of:

```
cat /var/log/messages
```

to a text file:

```
cat /var/log/messages > messages.txt
```

then using the advanced editor include the text file as an attachment.

Jim

---

### Post by shokks on 2009-03-20
> **hyper_ch said:**
> run memcheck... it's on the install cd - one of the menu points at boot up from it.

Thanks hyper_ch for your advice. I ran mem check from liveCD, it went on for more than one hour for 1GB ram, is that normal? Nevertheless, till then it had not found any memory problem. I ran out of patience and stopped it.

Then I added another stick of 1GB Ram to the machine(same make model, bought together), on the primary slot (1st one to be populated according to the motherboard manual) and transferred the existing to the second slot. So now in total, I have 2GB memory. Re-installed OS scratch.

Installation went perfectly, and from last night on, I have it running. I will wait for few more days, to report back if the problem comes back again.

It is possible the memory I was using before, is faulty, though I continue using it now on the second slot.

Would that be a problem? since it seems that the memory on the 1st slot is perfect, and Ubuntu server does not actually need so 2GB RAM to run.(Well server is for very light usage anyway, file server, backup etc) should I continue using it anyway, would it bring instability to the system?

[QUOTE=cariboo907]
It might be better to direct the output of:

Code:
.....

[/QUOTE]
:) Thanks a tonne. I have been thinking about how to do it for long time, somehow everyone seems to know it, and no one thinks its worthy enough to be written. Makes a noob feel even more miserable!!
Thanks

---

### Post by hyper_ch on 2009-03-20
well, memcheck should run many cycles time and again and test different things.. I think 1h was too short but it's been ages since I done it.

Well, good it works better now but you wouldn't need 2gb on that server. I still think that the first ram stick may be damages and if you plugged it in as second then maybe it hasn't been used yet.

---

### Post by shokks on 2009-03-22
Worked fine for two days. 
This morning I again have "segmentation faulty tree", while running apt-get update. Is it my HDD which is at faulty or is it the second stick of RAM which I put back in at the second slot?
Though it has happened only once, I am wondering whether it continues malfunctioning.
I don't know whether this is related (and perhaps helpful in debugging), but sometimes "screen" command also terminates unexpectedly.
Thank you guys for all the help!!

@Hyper_ch: Thanks my Swiss friend, I bought the RAM sticks from Digitec, whose websites show warranty for 999 months!!:) Wouldn't be a bad idea to change them, what do you think? Of course I would first run the mem-check overnight before proceeding to do so.

Below is the output from /var/log/messages

```

Mar 22 12:37:15 shire syslogd 1.5.0#1ubuntu1: restart.
Mar 22 12:37:15 shire kernel: Inspecting /boot/System.map-2.6.24-23-server
Mar 22 12:37:15 shire kernel: Loaded 28764 symbols from /boot/System.map-2.6.24-23-server.
Mar 22 12:37:15 shire kernel: Symbols match kernel version 2.6.24.
Mar 22 12:37:15 shire kernel: Loaded 11672 symbols from 46 modules.
Mar 22 12:37:15 shire kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 22 12:37:15 shire kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 22 12:37:15 shire kernel: [    0.000000] Linux version 2.6.24-23-server (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:55:21 UTC 2009 (Ubuntu 2.6.24-23.48-server)
Mar 22 12:37:15 shire kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077000000 (usable)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 0000000077000000 - 000000007f000000 (reserved)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 000000007f000000 - 000000007fdf0000 (usable)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Mar 22 12:37:15 shire kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 22 12:37:15 shire kernel: [    0.000000] 1149MB HIGHMEM available.
Mar 22 12:37:15 shire kernel: [    0.000000] 896MB LOWMEM available.
Mar 22 12:37:15 shire kernel: [    0.000000] found SMP MP-table at 000f5560
Mar 22 12:37:15 shire kernel: [    0.000000] NX (Execute Disable) protection: active
Mar 22 12:37:15 shire kernel: [    0.000000] Zone PFN ranges:
Mar 22 12:37:15 shire kernel: [    0.000000]   DMA             0 ->     4096
Mar 22 12:37:15 shire kernel: [    0.000000]   Normal       4096 ->   229376
Mar 22 12:37:15 shire kernel: [    0.000000]   HighMem    229376 ->   523760
Mar 22 12:37:15 shire kernel: [    0.000000] Movable zone start PFN for each node
Mar 22 12:37:15 shire kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 22 12:37:15 shire kernel: [    0.000000]     0:        0 ->   523760
Mar 22 12:37:15 shire kernel: [    0.000000] DMI 2.5 present.
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7070 checksum 0
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: RSDP 000F7070, 0024 (r2 Nvidia)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: XSDT 7FEF30C0, 004C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: FACP 7FEF94C0, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: DSDT 7FEF3240, 6238 (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: FACS 7FEF1800, 0040
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: HPET 7FEF9700, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: MCFG 7FEF9780, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: APIC 7FEF9600, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: SSDT 7FEF9DA0, 087B (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 22 12:37:15 shire kernel: [    0.000000] Processor #0 7:7 APIC version 20
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 22 12:37:15 shire kernel: [    0.000000] Processor #1 7:7 APIC version 20
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Mar 22 12:37:15 shire kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Mar 22 12:37:15 shire kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 22 12:37:15 shire kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Mar 22 12:37:15 shire kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 22 12:37:15 shire kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
Mar 22 12:37:15 shire kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Mar 22 12:37:15 shire kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Mar 22 12:37:15 shire kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Mar 22 12:37:15 shire kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519669
Mar 22 12:37:15 shire kernel: [    0.000000] Kernel command line: root=UUID=329b45f5-c5a0-48bd-9474-780b67d7e589 ro quiet splash
Mar 22 12:37:15 shire kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 22 12:37:15 shire kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 22 12:37:15 shire kernel: [    0.000000] Initializing CPU#0
Mar 22 12:37:15 shire kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 22 12:37:15 shire kernel: [    0.000000] Detected 2500.192 MHz processor.
Mar 22 12:37:15 shire kernel: [   19.858893] Console: colour VGA+ 80x25
Mar 22 12:37:15 shire kernel: [   19.858896] console [tty0] enabled
Mar 22 12:37:15 shire kernel: [   19.859304] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 22 12:37:15 shire kernel: [   19.859612] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 22 12:37:15 shire kernel: [   19.918143] Memory: 1933984k/2095040k available (2258k kernel code, 28728k reserved, 1037k data, 384k init, 1046464k highmem)
Mar 22 12:37:15 shire kernel: [   19.918149] virtual kernel memory layout:
Mar 22 12:37:15 shire kernel: [   19.918149]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
Mar 22 12:37:15 shire kernel: [   19.918150]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Mar 22 12:37:15 shire kernel: [   19.918151]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
Mar 22 12:37:15 shire kernel: [   19.918152]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 22 12:37:15 shire kernel: [   19.918152]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
Mar 22 12:37:15 shire kernel: [   19.918153]       .data : 0xc03349d9 - 0xc0437fe4   (1037 kB)
Mar 22 12:37:15 shire kernel: [   19.918154]       .text : 0xc0100000 - 0xc03349d9   (2258 kB)
Mar 22 12:37:15 shire kernel: [   19.918156] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar 22 12:37:15 shire kernel: [   19.918193] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Mar 22 12:37:15 shire kernel: [   20.068091] Calibrating delay using timer specific routine.. 5004.12 BogoMIPS (lpj=25020612)
Mar 22 12:37:15 shire kernel: [   20.068111] Security Framework initialized
Mar 22 12:37:15 shire kernel: [   20.068117] SELinux:  Disabled at boot.
Mar 22 12:37:15 shire kernel: [   20.068129] AppArmor: AppArmor initialized
Mar 22 12:37:15 shire kernel: [   20.068132] Failure registering capabilities with primary security module.
Mar 22 12:37:15 shire kernel: [   20.068139] Mount-cache hash table entries: 512
Mar 22 12:37:15 shire kernel: [   20.068239] Initializing cgroup subsys ns
Mar 22 12:37:15 shire kernel: [   20.068243] Initializing cgroup subsys cpuacct
Mar 22 12:37:15 shire kernel: [   20.068257] monitor/mwait feature present.
Mar 22 12:37:15 shire kernel: [   20.068258] using mwait in idle threads.
Mar 22 12:37:15 shire kernel: [   20.068261] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 22 12:37:15 shire kernel: [   20.068262] CPU: L2 cache: 2048K
Mar 22 12:37:15 shire kernel: [   20.068264] CPU: Physical Processor ID: 0
Mar 22 12:37:15 shire kernel: [   20.068265] CPU: Processor Core ID: 0
Mar 22 12:37:15 shire kernel: [   20.068274] Compat vDSO mapped to ffffe000.
Mar 22 12:37:15 shire kernel: [   20.068285] Checking 'hlt' instruction... OK.
Mar 22 12:37:15 shire kernel: [   20.108366] SMP alternatives: switching to UP code
Mar 22 12:37:15 shire kernel: [   20.109616] Early unpacking initramfs... done
Mar 22 12:37:15 shire kernel: [   20.324834] ACPI: Core revision 20070126
Mar 22 12:37:15 shire kernel: [   20.324872] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Mar 22 12:37:15 shire kernel: [   20.329087] CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06
Mar 22 12:37:15 shire kernel: [   20.329101] SMP alternatives: switching to SMP code
Mar 22 12:37:15 shire kernel: [   20.329714] Booting processor 1/1 eip 3000
Mar 22 12:37:15 shire kernel: [   20.339939] Initializing CPU#1
Mar 22 12:37:15 shire kernel: [   20.487472] Calibrating delay using timer specific routine.. 4999.99 BogoMIPS (lpj=24999962)
Mar 22 12:37:15 shire kernel: [   20.487481] monitor/mwait feature present.
Mar 22 12:37:15 shire kernel: [   20.487483] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 22 12:37:15 shire kernel: [   20.487484] CPU: L2 cache: 2048K
Mar 22 12:37:15 shire kernel: [   20.487486] CPU: Physical Processor ID: 0
Mar 22 12:37:15 shire kernel: [   20.487486] CPU: Processor Core ID: 1
Mar 22 12:37:15 shire kernel: [   20.487888] CPU1: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 06
Mar 22 12:37:15 shire kernel: [   20.487909] Total of 2 processors activated (10004.11 BogoMIPS).
Mar 22 12:37:15 shire kernel: [   20.488103] ENABLING IO-APIC IRQs
Mar 22 12:37:15 shire kernel: [   20.488309] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 22 12:37:15 shire kernel: [   20.707234] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 22 12:37:15 shire kernel: [   20.727216] Brought up 2 CPUs
Mar 22 12:37:15 shire kernel: [   20.727392] net_namespace: 64 bytes
Mar 22 12:37:15 shire kernel: [   20.727400] Booting paravirtualized kernel on bare hardware
Mar 22 12:37:15 shire kernel: [   20.727747] Time: 11:37:01  Date: 03/22/09
Mar 22 12:37:15 shire kernel: [   20.727767] NET: Registered protocol family 16
Mar 22 12:37:15 shire kernel: [   20.727891] EISA bus registered
Mar 22 12:37:15 shire kernel: [   20.727894] ACPI: bus type pci registered
Mar 22 12:37:15 shire kernel: [   20.812743] PCI: PCI BIOS revision 3.00 entry at 0xf1e20, last bus=4
Mar 22 12:37:15 shire kernel: [   20.812745] PCI: Using configuration type 1
Mar 22 12:37:15 shire kernel: [   20.812758] Setting up standard PCI resources
Mar 22 12:37:15 shire kernel: [   20.820285] ACPI: Interpreter enabled
Mar 22 12:37:15 shire kernel: [   20.820290] ACPI: (supports S0 S1 S3 S4 S5)
Mar 22 12:37:15 shire kernel: [   20.820301] ACPI: Using IOAPIC for interrupt routing
Mar 22 12:37:15 shire kernel: [   20.826959] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 22 12:37:15 shire kernel: [   20.828412] PCI: Transparent bridge - 0000:00:0a.0
Mar 22 12:37:15 shire kernel: [   20.871262] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.871392] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.871519] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.871647] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.871774] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.871901] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.872028] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.872155] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.872282] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.872413] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Mar 22 12:37:15 shire kernel: [   20.872541] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Mar 22 12:37:15 shire kernel: [   20.872668] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Mar 22 12:37:15 shire kernel: [   20.872795] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 10 11 14 15) *0
Mar 22 12:37:15 shire kernel: [   20.872923] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 11 14 15) *0
Mar 22 12:37:15 shire kernel: [   20.873051] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Mar 22 12:37:15 shire kernel: [   20.873179] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Mar 22 12:37:15 shire kernel: [   20.873306] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.873434] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
Mar 22 12:37:15 shire kernel: [   20.873560] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.873689] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Mar 22 12:37:15 shire kernel: [   20.873841] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.873988] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.874135] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.874281] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.874427] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.874573] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.874719] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.874865] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.875011] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.875158] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.875305] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.875451] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.875598] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.875744] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.875891] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.876037] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.876184] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.876330] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.876477] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Mar 22 12:37:15 shire kernel: [   20.876624] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Mar 22 12:37:15 shire kernel: [   20.876719] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 22 12:37:15 shire kernel: [   20.876738] pnp: PnP ACPI init
Mar 22 12:37:15 shire kernel: [   20.876742] ACPI: bus type pnp registered
Mar 22 12:37:15 shire kernel: [   20.880052] pnp: PnP ACPI: found 12 devices
Mar 22 12:37:15 shire kernel: [   20.880054] ACPI: ACPI bus type pnp unregistered
Mar 22 12:37:15 shire kernel: [   20.880056] PnPBIOS: Disabled by ACPI PNP
Mar 22 12:37:15 shire kernel: [   20.880199] PCI: Using ACPI for IRQ routing
Mar 22 12:37:15 shire kernel: [   20.880201] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar 22 12:37:15 shire kernel: [   21.076635] NET: Registered protocol family 8
Mar 22 12:37:15 shire kernel: [   21.076636] NET: Registered protocol family 20
Mar 22 12:37:15 shire kernel: [   21.076655] NetLabel: Initializing
Mar 22 12:37:15 shire kernel: [   21.076656] NetLabel:  domain hash size = 128
Mar 22 12:37:15 shire kernel: [   21.076657] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 22 12:37:15 shire kernel: [   21.076665] NetLabel:  unlabeled traffic allowed by default
Mar 22 12:37:15 shire kernel: [   21.076670] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Mar 22 12:37:15 shire kernel: [   21.076673] hpet0: 3 32-bit timers, 25000000 Hz
Mar 22 12:37:15 shire kernel: [   21.077702] AppArmor: AppArmor Filesystem Enabled
Mar 22 12:37:15 shire kernel: [   21.086596] Time: tsc clocksource has been installed.
Mar 22 12:37:15 shire kernel: [   21.129055] system 00:01: ioport range 0x1000-0x107f has been reserved
Mar 22 12:37:15 shire kernel: [   21.129057] system 00:01: ioport range 0x1080-0x10ff has been reserved
Mar 22 12:37:15 shire kernel: [   21.129059] system 00:01: ioport range 0x1400-0x147f has been reserved
Mar 22 12:37:15 shire kernel: [   21.129061] system 00:01: ioport range 0x1480-0x14ff has been reserved
Mar 22 12:37:15 shire kernel: [   21.129063] system 00:01: ioport range 0x1800-0x187f has been reserved
Mar 22 12:37:15 shire kernel: [   21.129065] system 00:01: ioport range 0x1880-0x18ff has been reserved
Mar 22 12:37:15 shire kernel: [   21.129067] system 00:01: iomem range 0xfec80000-0xfecbffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129069] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129071] system 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129073] system 00:01: iomem range 0x77000000-0x7effffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129077] system 00:02: ioport range 0xb78-0xb7b has been reserved
Mar 22 12:37:15 shire kernel: [   21.129079] system 00:02: ioport range 0xf78-0xf7b has been reserved
Mar 22 12:37:15 shire kernel: [   21.129080] system 00:02: ioport range 0xa78-0xa7b has been reserved
Mar 22 12:37:15 shire kernel: [   21.129082] system 00:02: ioport range 0xe78-0xe7b has been reserved
Mar 22 12:37:15 shire kernel: [   21.129084] system 00:02: ioport range 0xbbc-0xbbf has been reserved
Mar 22 12:37:15 shire kernel: [   21.129086] system 00:02: ioport range 0xfbc-0xfbf has been reserved
Mar 22 12:37:15 shire kernel: [   21.129087] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Mar 22 12:37:15 shire kernel: [   21.129089] system 00:02: ioport range 0x294-0x297 has been reserved
Mar 22 12:37:15 shire kernel: [   21.129091] system 00:02: ioport range 0x295-0x296 has been reserved
Mar 22 12:37:15 shire kernel: [   21.129092] system 00:02: ioport range 0x880-0x88f has been reserved
Mar 22 12:37:15 shire kernel: [   21.129099] system 00:0a: iomem range 0xf0000000-0xf1ffffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129102] system 00:0b: iomem range 0xd0000-0xd3fff has been reserved
Mar 22 12:37:15 shire kernel: [   21.129104] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129106] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129108] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129110] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129112] system 00:0b: iomem range 0x7fef0000-0x7fefffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129114] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129116] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129117] system 00:0b: iomem range 0x100000-0x7feeffff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129119] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129121] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.129123] system 00:0b: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Mar 22 12:37:15 shire kernel: [   21.159356] PCI: Bridge: 0000:00:0a.0
Mar 22 12:37:15 shire kernel: [   21.159358]   IO window: c000-cfff
Mar 22 12:37:15 shire kernel: [   21.159361]   MEM window: efb00000-efbfffff
Mar 22 12:37:15 shire kernel: [   21.159364]   PREFETCH window: efa00000-efafffff
Mar 22 12:37:15 shire kernel: [   21.159367] PCI: Bridge: 0000:00:0b.0
Mar 22 12:37:15 shire kernel: [   21.159368]   IO window: b000-bfff
Mar 22 12:37:15 shire kernel: [   21.159371]   MEM window: ef900000-ef9fffff
Mar 22 12:37:15 shire kernel: [   21.159373]   PREFETCH window: ef800000-ef8fffff
Mar 22 12:37:15 shire kernel: [   21.159375] PCI: Bridge: 0000:00:0c.0
Mar 22 12:37:15 shire kernel: [   21.159377]   IO window: e000-efff
Mar 22 12:37:15 shire kernel: [   21.159379]   MEM window: ef700000-ef7fffff
Mar 22 12:37:15 shire kernel: [   21.159381]   PREFETCH window: efe00000-efefffff
Mar 22 12:37:15 shire kernel: [   21.159384] PCI: Bridge: 0000:00:0d.0
Mar 22 12:37:15 shire kernel: [   21.159385]   IO window: d000-dfff
Mar 22 12:37:15 shire kernel: [   21.159388]   MEM window: efd00000-efdfffff
Mar 22 12:37:15 shire kernel: [   21.159390]   PREFETCH window: efc00000-efcfffff
Mar 22 12:37:15 shire kernel: [   21.159431] NET: Registered protocol family 2
Mar 22 12:37:15 shire kernel: [   21.258895] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 22 12:37:15 shire kernel: [   21.259061] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 22 12:37:15 shire kernel: [   21.259425] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 22 12:37:15 shire kernel: [   21.259629] TCP: Hash tables configured (established 131072 bind 65536)
Mar 22 12:37:15 shire kernel: [   21.259630] TCP reno registered
Mar 22 12:37:15 shire kernel: [   21.288902] checking if image is initramfs... it is
Mar 22 12:37:15 shire kernel: [   21.715152] Freeing initrd memory: 7181k freed
Mar 22 12:37:15 shire kernel: [   21.715736] audit: initializing netlink socket (disabled)
Mar 22 12:37:15 shire kernel: [   21.715750] audit(1237721821.670:1): initialized
Mar 22 12:37:15 shire kernel: [   21.715962] highmem bounce pool size: 64 pages
Mar 22 12:37:15 shire kernel: [   21.715965] Total HugeTLB memory allocated, 0
Mar 22 12:37:15 shire kernel: [   21.717297] VFS: Disk quotas dquot_6.5.1
Mar 22 12:37:15 shire kernel: [   21.717351] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 22 12:37:15 shire kernel: [   21.717484] io scheduler noop registered
Mar 22 12:37:15 shire kernel: [   21.717485] io scheduler anticipatory registered
Mar 22 12:37:15 shire kernel: [   21.717487] io scheduler deadline registered (default)
Mar 22 12:37:15 shire kernel: [   21.717494] io scheduler cfq registered
Mar 22 12:37:15 shire kernel: [   21.735927] assign_interrupt_mode Found MSI capability
Mar 22 12:37:15 shire kernel: [   21.736037] assign_interrupt_mode Found MSI capability
Mar 22 12:37:15 shire kernel: [   21.736140] assign_interrupt_mode Found MSI capability
Mar 22 12:37:15 shire kernel: [   21.736312] isapnp: Scanning for PnP cards...
Mar 22 12:37:15 shire kernel: [   22.091690] isapnp: No Plug & Play device found
Mar 22 12:37:15 shire kernel: [   22.107884] Real Time Clock Driver v1.12ac
Mar 22 12:37:15 shire kernel: [   22.108073] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar 22 12:37:15 shire kernel: [   22.108177] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 22 12:37:15 shire kernel: [   22.108623] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 22 12:37:15 shire kernel: [   22.109103] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar 22 12:37:15 shire kernel: [   22.109147] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 22 12:37:15 shire kernel: [   22.109233] PNP: No PS/2 controller found. Probing ports directly.
Mar 22 12:37:15 shire kernel: [   22.111789] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 22 12:37:15 shire kernel: [   22.111792] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 22 12:37:15 shire kernel: [   22.165128] mice: PS/2 mouse device common for all mice
Mar 22 12:37:15 shire kernel: [   22.165199] EISA: Probing bus 0 at eisa.0
Mar 22 12:37:15 shire kernel: [   22.165204] Cannot allocate resource for EISA slot 1
Mar 22 12:37:15 shire kernel: [   22.165225] EISA: Detected 0 cards.
Mar 22 12:37:15 shire kernel: [   22.165228] cpuidle: using governor ladder
Mar 22 12:37:15 shire kernel: [   22.165229] cpuidle: using governor menu
Mar 22 12:37:15 shire kernel: [   22.165299] NET: Registered protocol family 1
Mar 22 12:37:15 shire kernel: [   22.165319] Using IPI No-Shortcut mode
Mar 22 12:37:15 shire kernel: [   22.165347] registered taskstats version 1
Mar 22 12:37:15 shire kernel: [   22.165425]   Magic number: 1:381:631
Mar 22 12:37:15 shire kernel: [   22.165442]   hash matches device ptyca
Mar 22 12:37:15 shire kernel: [   22.165470] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
Mar 22 12:37:15 shire kernel: [   22.165841] Freeing unused kernel memory: 384k freed
Mar 22 12:37:15 shire kernel: [   22.165871] Write protecting the kernel read-only data: 828k
Mar 22 12:37:15 shire kernel: [   22.277866] fuse init (API version 7.9)
Mar 22 12:37:15 shire kernel: [   22.285966] ACPI: Fan [FAN] (on)
Mar 22 12:37:15 shire kernel: [   22.289445] ACPI: SSDT 7FEF9800, 025A (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [   22.289781] ACPI: SSDT 7FEF9C70, 012F (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Mar 22 12:37:15 shire kernel: [   22.289965] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 22 12:37:15 shire kernel: [   22.289973] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 22 12:37:15 shire kernel: [   22.291404] ACPI: Thermal Zone [THRM] (43 C)
Mar 22 12:37:15 shire kernel: [   22.598276] usbcore: registered new interface driver usbfs
Mar 22 12:37:15 shire kernel: [   22.598294] usbcore: registered new interface driver hub
Mar 22 12:37:15 shire kernel: [   22.598642] SCSI subsystem initialized
Mar 22 12:37:15 shire kernel: [   22.609149] usbcore: registered new device driver usb
Mar 22 12:37:15 shire kernel: [   22.610328] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
Mar 22 12:37:15 shire kernel: [   22.610334] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [AUBA] -> GSI 23 (level, low) -> IRQ 16
Mar 22 12:37:15 shire kernel: [   22.610348] ohci_hcd 0000:00:04.0: OHCI Host Controller
Mar 22 12:37:15 shire kernel: [   22.610556] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 1
Mar 22 12:37:15 shire kernel: [   22.610569] ohci_hcd 0000:00:04.0: irq 16, io mem 0xeffff000
Mar 22 12:37:15 shire kernel: [   22.666494] usb usb1: configuration #1 chosen from 1 choice
Mar 22 12:37:15 shire kernel: [   22.666514] hub 1-0:1.0: USB hub found
Mar 22 12:37:15 shire kernel: [   22.666520] hub 1-0:1.0: 10 ports detected
Mar 22 12:37:15 shire kernel: [   22.774688] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
Mar 22 12:37:15 shire kernel: [   22.774696] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [AUB2] -> GSI 22 (level, low) -> IRQ 17
Mar 22 12:37:15 shire kernel: [   22.774712] ehci_hcd 0000:00:04.1: EHCI Host Controller
Mar 22 12:37:15 shire kernel: [   22.774730] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
Mar 22 12:37:15 shire kernel: [   22.774752] ehci_hcd 0000:00:04.1: debug port 1
Mar 22 12:37:15 shire kernel: [   22.774764] ehci_hcd 0000:00:04.1: irq 17, io mem 0xefffe000
Mar 22 12:37:15 shire kernel: [   22.794201] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 22 12:37:15 shire kernel: [   22.794279] usb usb2: configuration #1 chosen from 1 choice
Mar 22 12:37:15 shire kernel: [   22.794295] hub 2-0:1.0: USB hub found
Mar 22 12:37:15 shire kernel: [   22.794299] hub 2-0:1.0: 10 ports detected
Mar 22 12:37:15 shire kernel: [   22.904520] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Mar 22 12:37:15 shire kernel: [   22.904526] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
Mar 22 12:37:15 shire kernel: [   23.915138] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Mar 22 12:37:15 shire kernel: [   23.915142] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
Mar 22 12:37:15 shire kernel: [   23.915476] scsi0 : ahci
Mar 22 12:37:15 shire kernel: [   23.915643] scsi1 : ahci
Mar 22 12:37:15 shire kernel: [   23.915736] scsi2 : ahci
Mar 22 12:37:15 shire kernel: [   23.915826] scsi3 : ahci
Mar 22 12:37:15 shire kernel: [   23.915889] ata1: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8100 irq 220
Mar 22 12:37:15 shire kernel: [   23.915891] ata2: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8180 irq 220
Mar 22 12:37:15 shire kernel: [   23.915893] ata3: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8200 irq 220
Mar 22 12:37:15 shire kernel: [   23.915895] ata4: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8280 irq 220
Mar 22 12:37:15 shire kernel: [   24.601662] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 22 12:37:15 shire kernel: [   24.602367] ata1.00: ATA-8: WDC WD10EADS-00L5B1, 01.01A01, max UDMA/133
Mar 22 12:37:15 shire kernel: [   24.602369] ata1.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 0/32)
Mar 22 12:37:15 shire kernel: [   24.603143] ata1.00: configured for UDMA/133
Mar 22 12:37:15 shire kernel: [   24.953669] ata2: SATA link down (SStatus 0 SControl 300)
Mar 22 12:37:15 shire kernel: [   25.300680] ata3: SATA link down (SStatus 0 SControl 300)
Mar 22 12:37:15 shire kernel: [   25.660175] ata4: SATA link down (SStatus 0 SControl 300)
Mar 22 12:37:15 shire kernel: [   25.660270] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-00L 01.0 PQ: 0 ANSI: 5
Mar 22 12:37:15 shire kernel: [   25.660645] scsi4 : pata_amd
Mar 22 12:37:15 shire kernel: [   25.660742] scsi5 : pata_amd
Mar 22 12:37:15 shire kernel: [   25.661105] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Mar 22 12:37:15 shire kernel: [   25.661107] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Mar 22 12:37:15 shire kernel: [   25.665500] Driver 'sd' needs updating - please use bus_type methods
Mar 22 12:37:15 shire kernel: [   25.665561] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Mar 22 12:37:15 shire kernel: [   25.665569] sd 0:0:0:0: [sda] Write Protect is off
Mar 22 12:37:15 shire kernel: [   25.665581] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 22 12:37:15 shire kernel: [   25.665618] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Mar 22 12:37:15 shire kernel: [   25.665624] sd 0:0:0:0: [sda] Write Protect is off
Mar 22 12:37:15 shire kernel: [   25.665635] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 22 12:37:15 shire kernel: [   25.665637]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
Mar 22 12:37:15 shire kernel: [   25.751264] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 22 12:37:15 shire kernel: [   25.754315] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 22 12:37:15 shire kernel: [   25.842532] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Mar 22 12:37:15 shire kernel: [   25.842817] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Mar 22 12:37:15 shire kernel: [   25.842823] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 19
Mar 22 12:37:15 shire kernel: [   26.372300] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:23:54:6f:df:3e
Mar 22 12:37:15 shire kernel: [   26.372303] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
Mar 22 12:37:15 shire kernel: [   26.437051] Attempting manual resume
Mar 22 12:37:15 shire kernel: [   26.445391] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 22 12:37:15 shire kernel: [   26.445394] EXT3-fs: write access will be enabled during recovery.
Mar 22 12:37:15 shire kernel: [   26.488278] kjournald starting.  Commit interval 5 seconds
Mar 22 12:37:15 shire kernel: [   26.488285] EXT3-fs: recovery complete.
Mar 22 12:37:15 shire kernel: [   26.488501] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 12:37:15 shire kernel: [   28.172442] input: Power Button (FF) as /devices/virtual/input/input1
Mar 22 12:37:15 shire kernel: [   28.219147] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 22 12:37:15 shire kernel: [   28.229661] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 22 12:37:15 shire kernel: [   28.236591] ACPI: Power Button (FF) [PWRF]
Mar 22 12:37:15 shire kernel: [   28.236650] input: Power Button (CM) as /devices/virtual/input/input2
Mar 22 12:37:15 shire kernel: [   28.259528] parport_pc 00:09: reported by Plug and Play ACPI
Mar 22 12:37:15 shire kernel: [   28.259637] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar 22 12:37:15 shire kernel: [   28.303697] input: PC Speaker as /devices/platform/pcspkr/input/input3
Mar 22 12:37:15 shire kernel: [   28.306477] ACPI: Power Button (CM) [PWRB]
Mar 22 12:37:15 shire kernel: [   28.419192] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
Mar 22 12:37:15 shire kernel: [   28.419196] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 16
Mar 22 12:37:15 shire kernel: [   28.672174] ACPI: WMI-Acer: Mapper loaded
Mar 22 12:37:15 shire kernel: [   29.367224] loop: module loaded
Mar 22 12:37:15 shire kernel: [   29.388853] lp0: using parport0 (interrupt-driven).
Mar 22 12:37:15 shire kernel: [   29.514585] Adding 1951856k swap on /dev/sda5.  Priority:-1 extents:1 across:1951856k
Mar 22 12:37:15 shire kernel: [   30.012641] EXT3 FS on sda8, internal journal
Mar 22 12:37:15 shire kernel: [   34.221524] kjournald starting.  Commit interval 5 seconds
Mar 22 12:37:15 shire kernel: [   34.221808] EXT3 FS on sda1, internal journal
Mar 22 12:37:15 shire kernel: [   34.221810] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 12:37:15 shire kernel: [   34.265310] kjournald starting.  Commit interval 5 seconds
Mar 22 12:37:15 shire kernel: [   34.265597] EXT3 FS on sda10, internal journal
Mar 22 12:37:15 shire kernel: [   34.265599] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 12:37:15 shire kernel: [   34.294076] kjournald starting.  Commit interval 5 seconds
Mar 22 12:37:15 shire kernel: [   34.294231] EXT3 FS on sda6, internal journal
Mar 22 12:37:15 shire kernel: [   34.294233] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 12:37:15 shire kernel: [   34.325147] kjournald starting.  Commit interval 5 seconds
Mar 22 12:37:15 shire kernel: [   34.325299] EXT3 FS on sda7, internal journal
Mar 22 12:37:15 shire kernel: [   34.325302] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 12:37:15 shire kernel: [   34.350661] kjournald starting.  Commit interval 5 seconds
Mar 22 12:37:15 shire kernel: [   34.350883] EXT3 FS on sda9, internal journal
Mar 22 12:37:15 shire kernel: [   34.350885] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 12:37:15 shire kernel: [   34.996628] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 22 12:37:15 shire kernel: [   36.144712] NET: Registered protocol family 10
Mar 22 12:37:15 shire kernel: [   36.144880] lo: Disabled Privacy Extensions
Mar 22 12:41:37 shire kernel: [  297.554618] apt-get[4464]: segfault at 20000018 eip b7f3fa63 esp bfba1f00 error 4
Mar 22 12:57:15 shire -- MARK --

```

---

### Post by shokks on 2009-03-27
Sorry to bug you guys again. I have been noticing rtorrent not available sometimes when running in background with "screen" command.
This evening I found one of the error messages happening as I was still logged in.

rtorrent crash after this error message.

```

Caught Segmentation fault, dumping stack:B] [Port: 6918]     [U 18/18] [D 31/0] [H 0/32] [S 0/105/768] [F 104/128]
Stack dump not enabled.
Aborted

```

Can someone throw light, whether it is the 'faulty' RAM (which I have not removed, since I could not prove yet it is malfunctioning) or something else?

Thanks a tonne.

---

### Post by BkkBonanza on 2009-03-27
Take out the suspected faulty RAM and try running with 1GB only. See if things clear up.

---

### Post by epsolon77 on 2009-10-12
I agree with the rest of the posters that you should run an extensive check on your RAM.  This is fairly rare in my experience, but I did have a computer that was spotty running windows, so to test it I threw Ubuntu on there to test.  I kept running into strange segfult errors, especially while compiling, but it would also show up at the most unpredictable moments I could imagine (aka, oops I bumped the mouse...SEGFUALT).  I replaced everything but the MOBO and CPU and still had issues.  Dusted all the memory slots.  So I ruled this a motherboard issue.

Test the RAM.  Get a different hard drive and CD drive in there and install ubuntu on there and see how it runs.  Also for the hell of it, make sure your MOBO doesn't have a setting for installed OS.  I had a cheap one that for some reason kept screwing up with the incorrect OS was selected.

---

### Post by shokks on 2009-10-12
Thanks epsolon77 .. :)
To be honest, I have tried checking everything. All of a sudden couple of months back it just stopped. (No, I have no clue why). And I intend to install Lynx as an LTS (its not so far away anymore), and I am wondering whether I will again experience the same thing.:( Will keep you posted ...

---

### Post by viper250 on 2009-10-12
its possible that you may have those problems again your hard drive being so large may have bad sectors on it  this drive can still be used but expect more problems with it.
Download d-ban and run it.  this is a drive wiper and it will take quite a while to wipe a drive that size.
 but if the drive has errors dban will tell you it has finished early due to drive errors. 
d-ban does run an integrity test during final wipe
Another thing you want to check is the old memory stick if it is getting hot 
the chips should get a bit warm during normal operation but not hot to touch adding an extra fan is always a good idea when upgrading memory

---

### Post by Aanaddor on 2009-10-12
Greetings,

I am new to this forum and Ubuntu.

I am having a similar problem, I have a Toshiba laptop with Windows Vista Home Edition and I installed Ubuntu 9.04 couple months ago and all worked fine until I decided to make the partition larger.

I went into windows vista and by using the partition manager that I have, I resized the partition and, when I rebooted the laptop I got an error 17, which I corrected by following this [COLOR=DarkGreen]**[POST]("http://ubuntuforums.org/showthread.php?t=1086483")**[/COLOR] on the forum. [URL="http://ubuntuforums.org/showthread.php?t=1086483"]
[/URL]
I can now get into the Grub menu but I keep getting a new error. EXT3-fs error and the laptop hangs.

I can't even boot up using my Ubuntu's LiveCD anymore, but I can get into Windows with no problems.


Any help would be most grateful.

Thanks.

---

