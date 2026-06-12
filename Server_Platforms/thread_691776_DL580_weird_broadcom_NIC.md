---
title: "DL580 weird broadcom NIC"
date: 2008-02-09
forum: Server Platforms
---

### Post by NateMan on 2008-02-09
I just purchased a HP DL580 G2 server and I was attempting to set it up. There was one error during the install, saying that the network card I was using did not have any included drivers. I completed the install and did an lspci. The card showed up as a pci-x Broadcom NetXtreme 5701 NIC. I downloaded the drivers for it from broadcom's site and attempted to follow the very slim install instructions. I attempted to make the driver, but I got errors stating that the file location was not there and an exit error 2. I currently don't have internet on the machine so I have to download on another machine and move the files over with a usb key. I would really appreciate any help getting this PCI-X NIC properly installed over CLI since I am using ubuntu server. This is the first wired NIC problem I've found with ubuntu. Also I was unsure about which directories to install this driver into.

Here is the driver webpage:

[http://www.broadcom.com/support/ethernet_nic/netxtreme_server.php](http://www.broadcom.com/support/ethernet_nic/netxtreme_server.php)

Thanks in advance!

I found some more information out about this driver. It needs to be compiled as a "module". Perhaps I'm too green to know how to do this, but the program does and a Makefile and I believe I have the right packages installed for this to function. I read the man pages for make, but I did not see any specific commands related to this problem. Any ideas on how to go about this?

---

### Post by faulkes on 2008-02-09
Can you post the error messages you received?

You are correct that it should be compiled as a module.

Faulkes

---

### Post by NateMan on 2008-02-09
yeah I can post the errors. I'll have to type them up rather than copy and paste, due to not having a ethernet card to ssh through. I'm not sure exactly how to compile the program as a module. I tried just using make, but that command didn't work. I also made sure I had gcc and g++ installed along with automake. How does one compile as a module? As in what should I type, where should I decompress the files, and where should I make it?

Here's the errors:

make -C   SUBDIRS=/home/ nathan/tg3-3.81c modules
make: *** SUBDIRS=/home/nathan/tg3-3.81c: No such file or directory. Stop.
make: *** [default] Error 2

I think its probably a simple mistake on my part, however I have not had any trouble normally compiling make files.

thanks.

---

### Post by faulkes on 2008-02-09
The error typically means it can't find the path it expects or the directory does not exist.  As a test I downloaded the driver you listed (tg3 for linux).  

```

unzip linux-3.81c.zip
cd Server/Linux/Driver/
tar xvfz tg3-3.81c.tar.gz
cd tg3-3.81c/
make

```

The above compiled it perfectly on my 7.10 system (although I didn't test it as I don't have that card).

The output I received was

[QUOTE=faulkes]
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/michael/tmp/tg3/Server/Linux/Driver/tg3-3.81c modules
[/QUOTE]

The only difference I see from comparison is that it found my /lib/modules and not yours, have a look to see what exists in 
/lib/modules/<your kernel>/

My initial guess is that the kernel source and kernel header packages are not installed.

Faulkes

---

### Post by NateMan on 2008-02-09
That makes alot of sense. What are the names of the packages needed? I'll gladly try anything. I really wanna get that beast up and running on the net.

---

### Post by faulkes on 2008-02-09
iirc the commands would be

```

sudo apt-get install linux-headers-<kernel version>
i.e. sudo apt-get install linux-headers-2.6.22-14 - that may not be your kernel though

sudo apt-get install linux-source-<kernel base>
i.e. sudo apt-get install linux-source-2.6.22 - as above

```

Edit: which of course, I now realize is somewhat useless information if you don't have net access on the box itself.  I'm old and slow ;)

You can search directly for the .deb files to download and trasfer over here:

[Launchpad for 7.10 i386](https://launchpad.net/ubuntu/gutsy/i386)

Just make sure the files you download match the kernel runningon the machine.



Faulkes

---

### Post by NateMan on 2008-02-09
ok I was able to make the driver, I then installed the driver. From there I went to the directory where it was installed and the driver is located. I then did an lsmod to see if the driver was currently running and it is. From there I checked ifconfig to see if my machine saw my ethernet card. This showed that it only sees the internal loopback. Is there something that I now have to do to get it configured properly?

---

### Post by faulkes on 2008-02-09
> **NateMan said:**
> ok I was able to make the driver, I then installed the driver. From there I went to the directory where it was installed and the driver is located. I then did an lsmod to see if the driver was currently running and it is. From there I checked ifconfig to see if my machine saw my ethernet card. This showed that it only sees the internal loopback. Is there something that I now have to do to get it configured properly?

See the README.TXT file that came with the package for additional driver details.  However, if you are not currently seeing eth0 (or some such) via ifconfig I would look in /var/log/messages or issues a dmesg command to see if anything relevant was logged about the module loading.

Faulkes

---

### Post by NateMan on 2008-02-09
I did a dmesg and I found this relating to the driver: 

[79.329971] tg3_test_dma() Write the buffer failed -19
[79.330059] tg3: DMA engine test failed, aborting.

any ideas? I followed the readme very exactly.

---

### Post by NateMan on 2008-02-09
Also I went to /var/log/messages and found a line relating to my diver and I don't see any error messages only a date and release number for the driver.

---

### Post by faulkes on 2008-02-09
> **NateMan said:**
> I did a dmesg and I found this relating to the driver: 

[79.329971] tg3_test_dma() Write the buffer failed -19
[79.330059] tg3: DMA engine test failed, aborting.

any ideas? I followed the readme very exactly.

```

lsmod | grep tg3

```

If you see a tg3 driver there, remove it

```

sudo rmmod tg3

```

then try again to insmod the modules you created, specify the full path to the newly created driver, remember that the system has a default tg3 driver which didn't support your card.  

```

ls -l /lib/modules/path/to/new/tg3-module.ko

```

Check the date of the file matches todays date.  Note that I am assuming you are using a 2.6 based kernel here.

Faulkes

---

### Post by NateMan on 2008-02-09
Ok I removed the tg3 and then attempted to reinsert my made driver, but it did not work, giving me these errors:

[ 4678.002783] tg_test_dma() Write the buffer failed -19
[ 4678.002871] tg3: DMA engine test failed, aborting.

I think perhaps my made drivers were not compiled right. What is the linux source package for 2.6? oh by the way 2.6.22 is the kernal I'm using  (ubuntu server 7.10). Sorry to have such a tough NIC.

---

### Post by faulkes on 2008-02-09
> **NateMan said:**
> Ok I removed the tg3 and then attempted to reinsert my made driver, but it did not work, giving me these errors:

[ 4678.002783] tg_test_dma() Write the buffer failed -19
[ 4678.002871] tg3: DMA engine test failed, aborting.

I think perhaps my made drivers were not compiled right. What is the linux source package for 2.6? oh by the way 2.6.22 is the kernal I'm using  (ubuntu server 7.10). Sorry to have such a tough NIC.

Ok, I would suggest re-making the driver and when you do, pay attention to any output (don't re-install it though).  Just do the "make" part.  If anything looks odd on the output, paste it here.

Have you checked bios settings which might relate to the NIC itself?

the packages iirc are:

linux-source-2.6.22
linux-headers-2.6.22-14

As for being sorry, don't be, we're here as a community to help, so fixing your problem will help others who might encounter the same.

Faulkes

---

### Post by NateMan on 2008-02-09
well its not actually an integrated card so I don't think that the bios would be the problem.

I tried installing the linux source file, but it says that it is not available. I remade the drivers however and it seemed to go fine. Do you think the problem is with not finding the linux source file?

---

### Post by faulkes on 2008-02-09
> **NateMan said:**
> well its not actually an integrated card so I don't think that the bios would be the problem.

I tried installing the linux source file, but it says that it is not available. I remade the drivers however and it seemed to go fine. Do you think the problem is with not finding the linux source file?

You may still wish to look at the bios, DMA is typically controlled (if at all)
from there and the error you are seeing is DMA related.

If the compile did not spit out errors, then the compile should typically be fine, being that the dependencies were all there.

Could you send the output of:

```

lspci

as well as

dmesg | grep tg3

```

Faulkes

---

### Post by NateMan on 2008-02-10
I'll get those to you. Is there away to save the output of a command to a txt file? If the ethernet was working, I'd ssh into it and copy from terminal, but I'm unable to do so. I was thinking I could save the output of the commands to a txt file and get it off my thumbdrive.

---

### Post by faulkes on 2008-02-10
```

command >/path/to/thumb-drive/myfile.txt

```

---

### Post by NateMan on 2008-02-10
Ok I saved the output of the commands and I believe I attached the files to this post. If not I'll post it up.

---

### Post by faulkes on 2008-02-10
Ok, 

First, lets see all the tg3 modules the system thinks exist:

```

uname -a (to get the kernel version)

cd /lib/modules/<kernel-version>

find . -print | grep tg3 (copy/attach output)

ls -l /path/to/each/tg3/modules/found/above/ (copy/attach output)

```

When was the last time the server was rebooted? if it hasn't been, do so now, when you do this, just to be sure, check the bios for anything DMA related (and possibly IRQ related), if there is anything interesting there, reported it back.

When the server boots back up, attach a full copy of the dmesg command:

```

dmesg >/path/to/thumb-drive/dmesg-full.txt

```

Faulkes

---

### Post by NateMan on 2008-02-10
Ok I'm in the bios now and I'm looking at the IRQ and the NIC along with the integrated lights out processor and compaq usb controller are on the same IRQ 10.
Could this be causing an error? By the way this thing has a rather odd bios.

---

### Post by faulkes on 2008-02-10
> **NateMan said:**
> Ok I'm in the bios now and I'm looking at the IRQ and the NIC along with the integrated lights out processor and compaq usb controller are on the same IRQ 10.
Could this be causing an error? By the way this thing has a rather odd bios.

It is entirely possible that if two pieces of hardware are sharing an irq that it would cause problems, that would depend on how active those pieces of hardware are.  My suggestion would be to switch the NIC to a different unusued IRQ to sort things out properly.

Faulkes

---

### Post by NateMan on 2008-02-10
I found this in the startup:

[    80.396991] Uhhuh. NMI received for unknown reason 31 on cpu 0.
[    80.397057] Do you have a strange power saving mode enabled?
[    80.397118] Dazed and confused, but trying to continue
[    80.401019] tg3_test_dma() Write the buffer failed -19
[    80.401099] tg3:  DMA engine test failed, aborting.

This may be helpful as well.

---

### Post by NateMan on 2008-02-10
I attached the find command, but I cannot run the second command in that sequence.
ere is the very large dmesg:

[    0.000000] Linux version 2.6.22-14-server (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:34:23 GMT 2007 (Ubuntu 2.6.22-14.46-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000efff8000 (usable)
[    0.000000]  BIOS-e820: 00000000efff8000 - 00000000f0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013ffff000 (usable)
[    0.000000] 4223MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4fd0
[    0.000000] Entering add_active_range(0, 0, 1310719) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1310719
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1310719
[    0.000000] On node 0 totalpages: 1310719
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8447 pages used for memmap
[    0.000000]   HighMem zone: 1072896 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F4F70 checksum 0
[    0.000000] ACPI: RSDP 000F4F70, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT EFFF8000, 0038 (r1 COMPAQ P27             2   Ò     162E)
[    0.000000] ACPI: FACP EFFF8040, 0074 (r1 COMPAQ P27             2   Ò     162E)
[    0.000000] ACPI: DSDT EFFF82C0, 3F04 (r1 COMPAQ     DSDT        1 MSFT  100000B)
[    0.000000] ACPI: FACS EFFF80C0, 0040
[    0.000000] ACPI: APIC EFFF8100, 00AC (r1 COMPAQ 00000083        2             0)
[    0.000000] ACPI: SPCR EFFF81C0, 0050 (r1 COMPAQ SPCRRBSU        1   Ò     162E)
[    0.000000] ACPI: SRAT EFFF8240, 0058 (r1 HP     P32             1             0)
[    0.000000] ACPI: SSDT EFFFE000, 02EF (r1 COMPAQ     SSDT        1 MSFT  100000B)
[    0.000000] ACPI: PM-Timer IO Port: 0x920
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] Processor #2 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] Processor #4 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
[    0.000000] Processor #6 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] Processor #3 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] Processor #5 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] Processor #7 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-15
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec01000] gsi_base[16])
[    0.000000] IOAPIC[1]: apic_id 3, version 17, address 0xfec01000, GSI 16-31
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec02000] gsi_base[32])
[    0.000000] IOAPIC[2]: apic_id 4, version 17, address 0xfec02000, GSI 32-47
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec03000] gsi_base[48])
[    0.000000] IOAPIC[3]: apic_id 5, version 17, address 0xfec03000, GSI 48-63
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 4 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at f1000000 (gap: f0000000:0ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 1300480
[    0.000000] Kernel command line: root=UUID=4d4fa1f6-efbc-4b53-b244-54c627d0cfa7 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] mapped IOAPIC to ffffb000 (fec01000)
[    0.000000] mapped IOAPIC to ffffa000 (fec02000)
[    0.000000] mapped IOAPIC to ffff9000 (fec03000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1497.116 MHz processor.
[   66.548101] Console: colour VGA+ 80x25
[   66.548782] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   66.549619] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   67.376785] Memory: 4926464k/5242876k available (2047k kernel code, 52908k reserved, 920k data, 364k init, 4063196k highmem)
[   67.376804] virtual kernel memory layout:
[   67.376806]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   67.376808]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   67.376810]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   67.376812]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   67.376814]       .init : 0xc03eb000 - 0xc0446000   ( 364 kB)
[   67.376816]       .data : 0xc02ffcc6 - 0xc03e5f04   ( 920 kB)
[   67.376818]       .text : 0xc0100000 - 0xc02ffcc6   (2047 kB)
[   67.376823] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   67.376895] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=8, Nodes=1
[   67.526715] Calibrating delay using timer specific routine.. 2997.00 BogoMIPS (lpj=14985040)
[   67.526765] Security Framework v1.0.0 initialized
[   67.526780] SELinux:  Disabled at boot.
[   67.526807] Mount-cache hash table entries: 512
[   67.527075] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   67.527098] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   67.527104] CPU: L2 cache: 512K
[   67.527107] CPU: L3 cache: 1024K
[   67.527111] CPU: Physical Processor ID: 0
[   67.527116] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   67.527138] Compat vDSO mapped to ffffe000.
[   67.527162] Checking 'hlt' instruction... OK.
[   67.566930] SMP alternatives: switching to UP code
[   67.567973] Early unpacking initramfs... done
[   68.130952] ACPI: Core revision 20070126
[   68.131067] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   68.189718] CPU0: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   68.189749] SMP alternatives: switching to SMP code
[   68.189909] Booting processor 1/1 eip 3000
[   68.200364] Initializing CPU#1
[   68.345533] Calibrating delay using timer specific routine.. 2994.30 BogoMIPS (lpj=14971512)
[   68.345549] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   68.345569] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   68.345574] CPU: L2 cache: 512K
[   68.345577] CPU: L3 cache: 1024K
[   68.345582] CPU: Physical Processor ID: 0
[   68.345586] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   68.346356] CPU1: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   68.346409] SMP alternatives: switching to SMP code
[   68.346550] Booting processor 2/2 eip 3000
[   68.357005] Initializing CPU#2
[   68.505303] Calibrating delay using timer specific routine.. 2994.37 BogoMIPS (lpj=14971891)
[   68.505318] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   68.505335] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   68.505339] CPU: L2 cache: 512K
[   68.505342] CPU: L3 cache: 1024K
[   68.505345] CPU: Physical Processor ID: 1
[   68.505349] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   68.506048] CPU2: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   68.506076] SMP alternatives: switching to SMP code
[   68.506115] Booting processor 3/3 eip 3000
[   68.516571] Initializing CPU#3
[   68.665074] Calibrating delay using timer specific routine.. 2994.34 BogoMIPS (lpj=14971720)
[   68.665091] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   68.665110] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   68.665116] CPU: L2 cache: 512K
[   68.665119] CPU: L3 cache: 1024K
[   68.665123] CPU: Physical Processor ID: 1
[   68.665128] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   68.665914] CPU3: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   68.665942] SMP alternatives: switching to SMP code
[   68.665981] Booting processor 4/4 eip 3000
[   68.676435] Initializing CPU#4
[   68.824843] Calibrating delay using timer specific routine.. 2994.33 BogoMIPS (lpj=14971667)
[   68.824858] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   68.824874] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   68.824878] CPU: L2 cache: 512K
[   68.824881] CPU: L3 cache: 1024K
[   68.824884] CPU: Physical Processor ID: 2
[   68.824888] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   68.825579] CPU4: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   68.825611] SMP alternatives: switching to SMP code
[   68.825651] Booting processor 5/5 eip 3000
[   68.836107] Initializing CPU#5
[   68.984614] Calibrating delay using timer specific routine.. 2994.35 BogoMIPS (lpj=14971766)
[   68.984631] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   68.984650] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   68.984656] CPU: L2 cache: 512K
[   68.984659] CPU: L3 cache: 1024K
[   68.984664] CPU: Physical Processor ID: 2
[   68.984669] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   68.985450] CPU5: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   68.985481] SMP alternatives: switching to SMP code
[   68.985520] Booting processor 6/6 eip 3000
[   68.995974] Initializing CPU#6
[   69.144384] Calibrating delay using timer specific routine.. 2994.38 BogoMIPS (lpj=14971901)
[   69.144400] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   69.144418] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   69.144422] CPU: L2 cache: 512K
[   69.144425] CPU: L3 cache: 1024K
[   69.144428] CPU: Physical Processor ID: 3
[   69.144432] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   69.145115] CPU6: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   69.145143] SMP alternatives: switching to SMP code
[   69.145182] Booting processor 7/7 eip 3000
[   69.155638] Initializing CPU#7
[   69.304155] Calibrating delay using timer specific routine.. 2994.39 BogoMIPS (lpj=14971976)
[   69.304172] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   69.304191] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   69.304197] CPU: L2 cache: 512K
[   69.304200] CPU: L3 cache: 1024K
[   69.304204] CPU: Physical Processor ID: 3
[   69.304210] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   69.304973] CPU7: Intel(R) XEON(TM) MP CPU 1.50GHz stepping 02
[   69.304998] Total of 8 processors activated (23957.49 BogoMIPS).
[   69.305651] ENABLING IO-APIC IRQs
[   69.305891] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   69.524054] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   69.544121] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   69.564204] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   69.584276] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[   69.604355] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[   69.624426] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[   69.644510] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[   69.664512] Brought up 8 CPUs
[   69.896938] migration_cost=22,1232
[   69.897507] Booting paravirtualized kernel on bare hardware
[   69.897629] Time:  5:38:07  Date: 01/10/108
[   69.897680] NET: Registered protocol family 16
[   69.897876] EISA bus registered
[   69.897888] ACPI: bus type pci registered
[   69.911575] PCI: PCI BIOS revision 2.10 entry at 0xf0094, last bus=13
[   69.911579] PCI: Using configuration type 1
[   69.911583] Setting up standard PCI resources
[   69.918658] mtrr: your CPUs had inconsistent fixed MTRR settings
[   69.918664] mtrr: probably your BIOS does not setup all CPUs.
[   69.918667] mtrr: corrected configuration.
[   69.921070] ACPI: EC: Look up EC in DSDT
[   69.923648] ACPI Exception (evxface-0643): AE_BAD_PARAMETER, Installing notify handler failed [20070126]
[   69.928339] ACPI: Interpreter enabled
[   69.928345] ACPI: (supports S0 S4 S5)
[   69.928375] ACPI: Using IOAPIC for interrupt routing
[   69.939007] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   69.939023] PCI: Probing PCI hardware (bus 00)
[   69.940144] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   69.943855] ACPI: PCI Root Bridge [PCI1] (0000:01)
[   69.943867] PCI: Probing PCI hardware (bus 01)
[   69.944006] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   69.944223] ACPI: PCI Root Bridge [PCI2] (0000:02)
[   69.944234] PCI: Probing PCI hardware (bus 02)
[   69.944512] ACPI: PCI Interrupt Routing Table [\_SB_.PCI2._PRT]
[   69.945135] ACPI: PCI Root Bridge [PCI6] (0000:06)
[   69.945147] PCI: Probing PCI hardware (bus 06)
[   69.945359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI6._PRT]
[   69.945856] ACPI: PCI Root Bridge [PCIA] (0000:0a)
[   69.945868] PCI: Probing PCI hardware (bus 0a)
[   69.946318] ACPI: PCI Interrupt Routing Table [\_SB_.PCIA._PRT]
[   69.947266] ACPI: PCI Interrupt Link [IUSB] (IRQs 4 5 7 *10 11 15)
[   69.947505] ACPI: PCI Interrupt Link [I16] (IRQs 4 5 7 10 *11 15)
[   69.947739] ACPI: PCI Interrupt Link [I17] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.947969] ACPI: PCI Interrupt Link [I18] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.948202] ACPI: PCI Interrupt Link [I19] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.948437] ACPI: PCI Interrupt Link [I20] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.948670] ACPI: PCI Interrupt Link [I21] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.948903] ACPI: PCI Interrupt Link [I22] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.949149] ACPI: PCI Interrupt Link [I23] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.949381] ACPI: PCI Interrupt Link [I24] (IRQs 4 *5 7 10 11 15)
[   69.949610] ACPI: PCI Interrupt Link [I25] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.949843] ACPI: PCI Interrupt Link [I26] (IRQs 4 5 *7 10 11 15)
[   69.950076] ACPI: PCI Interrupt Link [I27] (IRQs 4 5 *7 10 11 15)
[   69.950304] ACPI: PCI Interrupt Link [I28] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.950538] ACPI: PCI Interrupt Link [I29] (IRQs 4 5 7 10 11 15) *3
[   69.950770] ACPI: PCI Interrupt Link [I30] (IRQs 4 5 7 *10 11 15)
[   69.951001] ACPI: PCI Interrupt Link [I31] (IRQs 4 5 7 10 11 15) *0, disabled.
[   69.951234] ACPI: PCI Interrupt Link [I32] (IRQs 4 *5 7 10 11 15)
[   69.951466] ACPI: PCI Interrupt Link [I33] (IRQs 4 5 7 10 11 15) *3
[   69.951714] Linux Plug and Play Support v0.97 (c) Adam Belay
[   69.951743] pnp: PnP ACPI init
[   69.951762] ACPI: bus type pnp registered
[   69.957740] pnp: PnP ACPI: found 13 devices
[   69.957745] ACPI: ACPI bus type pnp unregistered
[   69.957751] PnPBIOS: Disabled by ACPI PNP
[   69.957883] PCI: Using ACPI for IRQ routing
[   69.957890] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   69.963312] PCI: Device 0000:00:00.0 not found by BIOS
[   69.968607] PCI: Device 0000:00:00.1 not found by BIOS
[   69.973980] PCI: Device 0000:00:00.2 not found by BIOS
[   69.979277] PCI: Device 0000:00:00.3 not found by BIOS
[   70.000653] PCI: Device 0000:00:0f.0 not found by BIOS
[   70.016946] PCI: Device 0000:00:0f.3 not found by BIOS
[   70.022238] PCI: Device 0000:00:10.0 not found by BIOS
[   70.027536] PCI: Device 0000:00:10.2 not found by BIOS
[   70.032827] PCI: Device 0000:00:11.0 not found by BIOS
[   70.038124] PCI: Device 0000:00:11.2 not found by BIOS
[   70.083845] NET: Registered protocol family 8
[   70.083850] NET: Registered protocol family 20
[   70.083872] NetLabel: Initializing
[   70.083875] NetLabel:  domain hash size = 128
[   70.083879] NetLabel:  protocols = UNLABELED CIPSOv4
[   70.083908] NetLabel:  unlabeled traffic allowed by default
[   70.084032] pnp: 00:01: ioport range 0xf50-0xf58 has been reserved
[   70.084039] pnp: 00:01: ioport range 0x408-0x40f has been reserved
[   70.084044] pnp: 00:01: ioport range 0x900-0x903 has been reserved
[   70.084050] pnp: 00:01: ioport range 0x910-0x911 has been reserved
[   70.084055] pnp: 00:01: ioport range 0x920-0x923 has been reserved
[   70.084060] pnp: 00:01: ioport range 0x930-0x937 has been reserved
[   70.084066] pnp: 00:01: ioport range 0x940-0x947 has been reserved
[   70.093042] Time: tsc clocksource has been installed.
[   70.114802] NET: Registered protocol family 2
[   70.232904] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   70.233082] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   70.235040] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   70.235753] TCP: Hash tables configured (established 131072 bind 65536)
[   70.235759] TCP reno registered
[   70.263151] checking if image is initramfs...<6>Switched to high resolution mode on CPU 1
[   70.612604] Switched to high resolution mode on CPU 2
[   70.612708] Switched to high resolution mode on CPU 3
[   70.612819] Switched to high resolution mode on CPU 4
[   70.612917] Switched to high resolution mode on CPU 5
[   70.613030] Switched to high resolution mode on CPU 6
[   70.613127] Switched to high resolution mode on CPU 7
[   70.622280] Switched to high resolution mode on CPU 0
[   70.792925]  it is
[   71.380910] Freeing initrd memory: 6910k freed
[   71.381820] audit: initializing netlink socket (disabled)
[   71.381845] audit(1202621886.490:1): initialized
[   71.382027] highmem bounce pool size: 64 pages
[   71.387229] VFS: Disk quotas dquot_6.5.1
[   71.387352] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   71.387547] io scheduler noop registered
[   71.387552] io scheduler anticipatory registered
[   71.387557] io scheduler deadline registered (default)
[   71.387587] io scheduler cfq registered
[   71.387635] Boot video device is 0000:00:03.0
[   71.401632] isapnp: Scanning for PnP cards...
[   71.714519] isapnp: No Plug & Play device found
[   71.764289] Real Time Clock Driver v1.12ac
[   71.764490] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   71.764631] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   71.765819] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   71.767586] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   71.767865] input: Macintosh mouse button emulation as /class/input/input0
[   71.768055] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   71.769608] serio: i8042 KBD port at 0x60,0x64 irq 1
[   71.769622] serio: i8042 AUX port at 0x60,0x64 irq 12
[   71.770006] mice: PS/2 mouse device common for all mice
[   71.770276] EISA: Probing bus 0 at eisa.0
[   71.770427] EISA: Mainboard CPQ0736 detected.
[   71.770512] Cannot allocate resource for EISA slot 1
[   71.770518] Cannot allocate resource for EISA slot 2
[   71.770523] Cannot allocate resource for EISA slot 3
[   71.770564] EISA: Detected 0 cards.
[   71.771058] TCP cubic registered
[   71.771083] NET: Registered protocol family 1
[   71.771125] Using IPI No-Shortcut mode
[   71.771530]   Magic number: 12:832:617
[   71.771654]   hash matches device ptye7
[   71.771675]   hash matches device ptyba
[   71.772185] Freeing unused kernel memory: 364k freed
[   71.817000] input: AT Translated Set 2 keyboard as /class/input/input1
[   72.142714] AppArmor: AppArmor initialized<5>audit(1202621887.490:2):  type=1505 info="AppArmor initialized" pid=1129
[   72.160897] fuse init (API version 7.8)
[   72.172400] Failure registering capabilities with primary security module.
[   72.271073] ACPI: Thermal Zone [THM0] (8 C)
[   73.485251] SCSI subsystem initialized
[   73.499139] usbcore: registered new interface driver usbfs
[   73.499229] usbcore: registered new interface driver hub
[   73.499332] usbcore: registered new device driver usb
[   73.515138] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   73.515809] ACPI: PCI Interrupt Link [IUSB] enabled at IRQ 10
[   73.515829] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [IUSB] -> GSI 10 (level, low) -> IRQ 10
[   73.515863] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   73.516185] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[   73.516225] ohci_hcd 0000:00:0f.2: irq 10, io mem 0xf5fe0000
[   73.522136] libata version 2.21 loaded.
[   73.571754] HP CISS Driver (v 3.6.14)
[   73.584149] usb usb1: configuration #1 chosen from 1 choice
[   73.584239] hub 1-0:1.0: USB hub found
[   73.584264] hub 1-0:1.0: 4 ports detected
[   73.593656] Floppy drive(s): fd0 is 1.44M
[   73.609897] FDC 0 is a National Semiconductor PC87306
[   73.688123] ACPI: PCI Interrupt 0000:0a:01.0[A] -> GSI 26 (level, low) -> IRQ 16
[   73.688178] ohci_hcd 0000:0a:01.0: OHCI Host Controller
[   73.688219] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   73.688250] ohci_hcd 0000:0a:01.0: new USB bus registered, assigned bus number 2
[   73.688287] ohci_hcd 0000:0a:01.0: irq 16, io mem 0xf7ff0000
[   73.777936] usb usb2: configuration #1 chosen from 1 choice
[   73.778019] hub 2-0:1.0: USB hub found
[   73.778040] hub 2-0:1.0: 3 ports detected
[   73.787682] cciss0: <0xb060> at PCI 0000:02:02.0 IRQ 17 using DAC
[   73.817619]       blocks= 284522880 block_size= 512
[   73.827603]       heads=255, sectors=32, cylinders=34868
[   73.827606] 
[   73.827846]       blocks= 284522880 block_size= 512
[   73.827909]       heads=255, sectors=32, cylinders=34868
[   73.827912] 
[   73.827918]  cciss/c0d0: p1 p2
[   73.887728] ACPI: PCI Interrupt 0000:0a:01.1[B] -> GSI 27 (level, low) -> IRQ 18
[   73.887756] ohci_hcd 0000:0a:01.1: OHCI Host Controller
[   73.887810] ohci_hcd 0000:0a:01.1: new USB bus registered, assigned bus number 3
[   73.887837] ohci_hcd 0000:0a:01.1: irq 18, io mem 0xf7fe0000
[   73.977610] usb usb3: configuration #1 chosen from 1 choice
[   73.977688] hub 3-0:1.0: USB hub found
[   73.977709] hub 3-0:1.0: 2 ports detected
[   74.037322] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   74.094040] tg3.c:v3.77 (May 31, 2007)
[   74.094084] ACPI: PCI Interrupt 0000:0a:02.0[A] -> GSI 24 (level, low) -> IRQ 19
[   74.095650] scsi0 : pata_serverworks
[   74.095806] scsi1 : pata_serverworks
[   74.095885] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012000 irq 14
[   74.095896] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012008 irq 15
[   74.274914] usb 1-3: configuration #1 chosen from 1 choice
[   74.277834] hub 1-3:1.0: USB hub found
[   74.280717] hub 1-3:1.0: 4 ports detected
[   74.297604] Attempting manual resume
[   74.297612] swsusp: Resume From Partition 104:1
[   74.297616] PM: Checking swsusp image.
[   74.297781] PM: Resume from disk failed.
[   74.340551] kjournald starting.  Commit interval 5 seconds
[   74.340575] EXT3-fs: mounted filesystem with ordered data mode.
[   74.427098] ata1.00: ATAPI: CD-224E, 9.9A, max MWDMA2
[   74.626813] ata1.00: configured for MWDMA2
[   74.648121] usb 1-3.1: new low speed USB device using ohci_hcd and address 3
[   74.788120] scsi 0:0:0:0: CD-ROM            TEAC     CD-224E          9.9A PQ: 0 ANSI: 5
[   74.789040] usb 1-3.1: configuration #1 chosen from 1 choice
[   75.814851] Uhhuh. NMI received for unknown reason 31 on CPU 0.
[   75.814920] Do you have a strange power saving mode enabled?
[   75.814982] Dazed and confused, but trying to continue
[   75.818882] tg3_test_dma() Write the buffer failed -19
[   75.818969] tg3: DMA engine test failed, aborting.
[   75.819122] ACPI: PCI interrupt for device 0000:0a:02.0 disabled
[   75.819651] ACPI: PCI Interrupt 0000:0a:01.2[C] -> GSI 26 (level, low) -> IRQ 16
[   75.819682] ehci_hcd 0000:0a:01.2: EHCI Host Controller
[   75.819770] ehci_hcd 0000:0a:01.2: new USB bus registered, assigned bus number 4
[   75.844703] ehci_hcd 0000:0a:01.2: irq 16, io mem 0xf7fd0000
[   75.844720] ehci_hcd 0000:0a:01.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   75.844986] usb usb4: configuration #1 chosen from 1 choice
[   75.845071] hub 4-0:1.0: USB hub found
[   75.845092] hub 4-0:1.0: 5 ports detected
[   79.116381] input: PC Speaker as /class/input/input2
[   79.411886] Linux agpgart interface v0.102 (c) Dave Jones
[   79.537139] input: PS/2 Generic Mouse as /class/input/input3
[   79.586484] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   79.617547] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
[   79.617723] ACPI: PCI Interrupt 0000:02:1e.0[A] -> GSI 32 (level, low) -> IRQ 20
[   79.617751] cpqphp: Hot Plug Subsystem Device ID: a2fe
[   79.617767] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 2
[   79.617787] PCI: Using BIOS Interrupt Routing Table
[   79.617891] PCI: Using BIOS Interrupt Routing Table
[   79.682034] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   79.691556] usbcore: registered new interface driver hiddev
[   79.703694] input: Logitech USB Receiver as /class/input/input4
[   79.703777] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0f.2-3.1
[   79.729905] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[   79.731072] input: Logitech USB Receiver as /class/input/input5
[   79.731254] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0f.2-3.1
[   79.731287] usbcore: registered new interface driver usbhid
[   79.731293] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   79.854374] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   79.854397] Uniform CD-ROM driver Revision: 3.20
[   79.854574] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   79.877418] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   80.627802] ACPI: PCI Interrupt 0000:06:1e.0[A] -> GSI 33 (level, low) -> IRQ 21
[   80.627822] cpqphp: Hot Plug Subsystem Device ID: a2fe
[   80.627828] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 6
[   80.627854] PCI: Using BIOS Interrupt Routing Table
[   81.952212] loop: module loaded
[   82.012704] lp: driver loaded but no devices found
[   82.199092] Adding 3903784k swap on /dev/cciss/c0d0p1.  Priority:-1 extents:1 across:3903784k
[   82.541821] EXT3 FS on cciss/c0d0p2, internal journal
[   85.365332] NET: Registered protocol family 10
[   85.365689] lo: Disabled Privacy Extensions
[  344.464529] usb 4-1: new high speed USB device using ehci_hcd and address 2
[  344.626830] usb 4-1: configuration #1 chosen from 1 choice
[  344.720645] usbcore: registered new interface driver libusual
[  344.762795] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  344.762807] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  344.770134] Initializing USB Mass Storage driver...
[  344.770569] scsi2 : SCSI emulation for USB Mass Storage devices
[  344.770743] usb-storage: device found at 2
[  344.770756] usb-storage: waiting for device to settle before scanning
[  344.770767] usbcore: registered new interface driver usb-storage
[  344.770781] USB Mass Storage support registered.
[  349.757123] usb-storage: device scan complete
[  349.757982] scsi 2:0:0:0: Direct-Access     Memorex  TD 2C            1.04 PQ: 0 ANSI: 0 CCS
[  349.758900] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[  350.282416] sd 2:0:0:0: [sda] 501760 512-byte hardware sectors (257 MB)
[  350.283091] sd 2:0:0:0: [sda] Write Protect is off
[  350.283102] sd 2:0:0:0: [sda] Mode Sense: 23 00 00 00
[  350.283112] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  350.286102] sd 2:0:0:0: [sda] 501760 512-byte hardware sectors (257 MB)
[  350.286708] sd 2:0:0:0: [sda] Write Protect is off
[  350.286724] sd 2:0:0:0: [sda] Mode Sense: 23 00 00 00
[  350.286735] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  350.286830]  sda: sda1
[  350.287985] sd 2:0:0:0: [sda] Attached SCSI removable disk

---

### Post by faulkes on 2008-02-10
```

cd /lib/modules/<kernel-version>

ls -l kernel/drivers/net/tg3.ko

```

That should output what it listing for the kernel module on disk, also did you change the IRQ related to the NIC?

From what I can see, there are alot of things taking up address space, i.e. like com ports and the such.  One option is to disable everything in the BIOS you know you won't be using.  Another option to investigate is to ensure you have the current/latest BIOS revision.  There are a few things I'm not sure of in the dmesg output, such as a failure on DSDT.

Faulkes

---

### Post by NateMan on 2008-02-10
Yes I did change the irq for the nic. Very odd. The bios is almost up to date, but I lack a floppy drive to update it with. Do you think this may be unfixable? Seems like it should be doable, due to this server supposidly supporting linux. 
Here is the driver page that is on HP's website:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=316533&prodNameId=3288116&swEnvOID=1025&swLang=8&mode=2&taskId=135&swItem=MTX-UNITY-I21112](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=316533&prodNameId=3288116&swEnvOID=1025&swLang=8&mode=2&taskId=135&swItem=MTX-UNITY-I21112)

I'm not really sure what to do to with the rpm and xml. I am sure it is the same driver that is on the broadcom website, since the card is actually a broadcom card.

---

### Post by faulkes on 2008-02-10
I wouldn't say unfixable but I am running out of options (for my own knowledge).

The rpm is contains the source of the driver, you would need the rpm utilities installed to pull the files out of it.  There is a good possibility that it could have been tweaked or otherwise by HP but I couldn't say for sure.

Ok, hmmm, interesting, reading through the xml file suggests that the NIC is an e1000, not a broadcom.  Is there an onboard NIC in this machine in addition to the broadcom NIC? The e1000 is supported already by default on 2.6+ kernels.

(the xml file is just test, you can read through it)
Faulkes

---

### Post by NateMan on 2008-02-11
Well there are two nics, but the first onboard nic is a iLO (integrated Lights Out) port. It is for some kind of built-in management. Perhaps it is seeing this and not seeing the second one? Maybe I should try reseating the card and seeing if that works. I only found out about the broadcom cause of the lspci.  I don't see a e1000 on the lspci either. I'm looking in the bios now and the name of the raid card is a Compaq NC7770 gigabit server adaptor.

here's a page about it:

[http://h18000.www1.hp.com/products/quickspecs/11051_div/11051_div.html](http://h18000.www1.hp.com/products/quickspecs/11051_div/11051_div.html)

---

### Post by faulkes on 2008-02-11
I would try removing the card and letting it boot to see what it finds (i.e. do another lspci).  

If lspci sees the broadcom card, that should mean it is seated properly, otherwise it wouldn't be recognized or the system wouldn't boot (in typical situations).

So, boot it up without the broadcom card in there and send back another lspci, lets see what it thinks then.  

Faulkes

---

### Post by NateMan on 2008-02-11
Ok the card is seated correctly. After doing some more research, I found this page:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=261183&prodTypeId=329290&prodSeriesId=331490&swLang=8&taskId=135&swEnvOID=4006](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=261183&prodTypeId=329290&prodSeriesId=331490&swLang=8&taskId=135&swEnvOID=4006)

I think that I might have to convert the rpm and attempt that. Not really sure how to get the rpm to a form usable by ubuntu though.

---

### Post by faulkes on 2008-02-11
If you install the rpm tools as well as the rpm development tools you should be able to use the supplied rpm.

The download is source, it will typically unpack itself to /usr/src somewhere.  Once it is unpacked you need the rpm development tools, which itself will build another rpm (the actual driver/module) which can then be installed.  

Faulkes
--note because ubuntu is not natively an rpm system there may be issues.

---

### Post by NateMan on 2008-02-11
Ok I'm gonna start fresh on this server and try to use the .rpm to install the drivers. I talked to our *NIX system admin at work today and he said that the kernal should support that card. Our linux clusters all have those same cards he said. He mentioned that maybe there is a problem with the drivers and ubuntu (or perhaps debian?) itself? The distros there are drivers for seem to be all RPM based. I'll have to try out those solutions when I get done with my labwork tonight. I was told that broadcom was particularly good about getting the source out on the web.

---

