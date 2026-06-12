---
title: "HOWTO: USB Audio device"
date: 2005-04-30
forum: Tutorials
---

### Post by SFN on 2005-04-30
I have a Tascam US-122 and was having trouble getting it to work. I had seen similar posts regarding other USB sound cards. 

This process definitely got my US-122 to work on a number of different machines. Although I haven't tested it on any other devices (because I don't have any) I would think the process would be the same.

First, do

```
sudo apt-get install fxload
```

and download

[http://ccrma.stanford.edu/mirrors/agnula/demudi-apt/pool/local/a/alsa-tools/alsa-tools_1.0.5-2_i386.deb](http://ccrma.stanford.edu/mirrors/agnula/demudi-apt/pool/local/a/alsa-tools/alsa-tools_1.0.5-2_i386.deb)  

Then do

```
sudo dpkg -i alsa-tools_1.0.5-2_i386.deb
```

Now, /usr/share/doc/alsa-tools/README.Debian reveals:

> "The alsa-tools packages is almost useles without the alsa-firmware one!

Awfully alsa-firmware has broken license terms and it's to legally
distributable at the moment. The AGNULA team is trying to solve the
issue." 

There is a link there to the source for alsa-firmware but I downloaded an RPM from

[http://rpm.pbone.net/index.php3/stat/4/idpl/1419735/com/alsa-firmware-1.0.6-1.cvs.rhfc2.ccrma.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1419735/com/alsa-firmware-1.0.6-1.cvs.rhfc2.ccrma.i386.rpm.html) 

then did

```
sudo alien --to-deb alsa-firmware-1.0.6-1.cvs.rhfc2.ccrma.i386.rpm
```

and

```
sudo dpkg -i alsa-firmware_1.0.6-2_i386.deb
```

Once you have your deb installed (or got the install done from source) download 

[http://langerland.de/audio/usx2y/usx2y-fw-0.1b.tar.bz2](http://langerland.de/audio/usx2y/usx2y-fw-0.1b.tar.bz2) 

and extract it.

Do

```
lsusb
```

and make note of the bus and device. In this case:

> Bus 001 Device 005: ID 1604:8005 Tascam US-224 Audio/Midi Controller 

Now do

```
sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/001/005
```

/path/to/ represents the location of your ld2-ezusb.hex file. It was in the archive you downloaded from langerland.de. The /001/005 comes from your lsusb results. 001 = Bus. 005 = Device

Finally, do

```
sudo usx2yloader
```

Lights on the US-122 come on. If you do 

```
cat /proc/asound/cards
```

you will see something like

> 0 [Live ]: EMU10K1 - Sound Blaster Live!
Sound Blaster Live! (rev.10) at 0xd000, irq 18
1 [USX2Y ]: USB US-X2Y - TASCAM US-X2Y
TASCAM US-X2Y (1604:8007 if 0 at 001/006) 

If you already had a sound card(s) installed, as I did, your USB card will be the last in the list.

Should you reboot or disconnect the device, you'll need to do

```
sudo usx2yloader
```

again to initialize the card.

I'd imagine you could even have usx2yloader run on startup, if the card was attached all the time.

Hope this helps.

---

### Post by schdefan on 2005-05-21
Hi SFN!

I really appreciate your description. I have tried a lot of solution through the half last year to get my USB Soundcard working but without success. Now my TASCAM US-122 behaves properly.
Thank you.

schdefan

---

### Post by goye2cz on 2005-06-13
I am stuck at this step:

sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/001/005

/path/to/ represents the location of your ld2-ezusb.hex file. It was in the archive you downloaded from langerland.de. The /001/005 comes from your lsusb results. 001 = Bus. 005 = Device

It keeps giving me this message: unable to open for input.

It's possible that I have the syntax wrong, but I've trid it many different ways.

Any help?

goye2cz

---

### Post by SFN on 2005-06-13
[QUOTE=goye2cz]I am stuck at this step:

sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/ -D /proc/bus/usb/001/005

/path/to/ represents the location of your ld2-ezusb.hex file. It was in the archive you downloaded from langerland.de. The /001/005 comes from your lsusb results. 001 = Bus. 005 = Device

It keeps giving me this message: unable to open for input.

It's possible that I have the syntax wrong, but I've trid it many different ways.

Any help?

goye2cz[/QUOTE]

If you will, do me a favor. Paste the responses from 

```
sudo find / -name ld2-ezusb.hex
``` 

```
sudo find / -name us122fw.ihx
``` 

and 

```
lusb
``` 

here.

---

### Post by goye2cz on 2005-06-14
Actually, I tried really hard this morning and finally got my tascam installed. I still seem to be having trouble with jack.

I get this in the messages after I start jackd (using qjackctl):
17:44:16.741 Statistics reset.
17:44:16.768 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
17:44:24.497 Startup script...
17:44:24.506 artsshell -q terminate
sh: artsshell: command not found
17:44:24.839 Startup script terminated with exit status=32512.
17:44:24.842 JACK is starting...
17:44:24.844 /usr/bin/jackd -dalsa -dhw:1 -r48000 -p4096 -n2
17:44:24.867 JACK was started with PID=13211 (0x339b).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|4096|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 4096 frames, buffer = 2 periods
Couldn't open hw:1 for 32bit samples trying 24bit instead
Couldn't open hw:1 for 32bit samples trying 24bit instead
could not start playback (Broken pipe)
17:44:26.891 Server configuration saved to "/home/goye2cz/.jackdrc".
17:44:26.893 Statistics reset.
17:44:26.911 Client activated.
17:44:26.914 Audio connection change.
17:44:26.957 Audio connection graph change.

I have deactivated realtime and frames/period is set to 4096.

What do you make of it?

goye2cz

---

### Post by goye2cz on 2005-06-15
another strange thing is, every time i connect my us-122, I end up with different results at this step:

lsusb

a while ago when I connected, I got these results:

Bus 001 Device 005: ID 1604:8007 Tascam US-122 Audio/Midi Interface

just now, I got these results:

Bus 001 Device 007: ID 1604:8007 Tascam US-122 Audio/Midi Interface

could this be causing me problems?

---

### Post by satchnut on 2005-06-16
I also own a US-122, but when I enter
*sudo usx2yloader*

I get
*usx2yloader: no US-X2Y-compatible cards found*

$ lsusb
*Bus 003 Device 007: ID 1604:8007 Tascam US-122 Audio/Midi Interface*

Any help would be greatly appreciated, as I've been trying to get this working under Linux for YEARS!  Thanks!

---

### Post by SFN on 2005-06-17
[QUOTE=goye2cz]another strange thing is, every time i connect my us-122, I end up with different results at this step:

lsusb

a while ago when I connected, I got these results:

Bus 001 Device 005: ID 1604:8007 Tascam US-122 Audio/Midi Interface

just now, I got these results:

Bus 001 Device 007: ID 1604:8007 Tascam US-122 Audio/Midi Interface

could this be causing me problems?[/QUOTE]

Well, I'm not Mr. USB but as I understand it, the device ID is assigned when you plug a device in. Let's say the first itme you plug in a USB device, that device gets ID 005. The next device you plug in gets IS 006. The next one, 007 and so on. Now let's say the next time you start up, you plugin the device that got ID 007 first. It would get the first available device ID - in this case 005.

Somebody feel free to crrect me if I'm wrong here.

The way I did mine, I had no USB devices plugged in befoer I plugged in the US-122. From that point on, I always made sure that I plugged in the US-122 first. I got the same ID every time.

---

### Post by SFN on 2005-06-17
[QUOTE=satchnut]I also own a US-122, but when I enter
*sudo usx2yloader*

I get
*usx2yloader: no US-X2Y-compatible cards found*

$ lsusb
*Bus 003 Device 007: ID 1604:8007 Tascam US-122 Audio/Midi Interface*

Any help would be greatly appreciated, as I've been trying to get this working under Linux for YEARS!  Thanks![/QUOTE]


Paste the responses from
```
sudo find / -name ld2-ezusb.hex
``` 
and
```
sudo find / -name us122fw.ihx
``` 
here.

---

### Post by SFN on 2005-06-17
[QUOTE=goye2cz]Actually, I tried really hard this morning and finally got my tascam installed. I still seem to be having trouble with jack.

I get this in the messages after I start jackd (using qjackctl):
17:44:16.741 Statistics reset.
17:44:16.768 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
17:44:24.497 Startup script...
17:44:24.506 artsshell -q terminate
sh: artsshell: command not found
17:44:24.839 Startup script terminated with exit status=32512.
17:44:24.842 JACK is starting...
17:44:24.844 /usr/bin/jackd -dalsa -dhw:1 -r48000 -p4096 -n2
17:44:24.867 JACK was started with PID=13211 (0x339b).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|4096|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 4096 frames, buffer = 2 periods
Couldn't open hw:1 for 32bit samples trying 24bit instead
Couldn't open hw:1 for 32bit samples trying 24bit instead
could not start playback (Broken pipe)
17:44:26.891 Server configuration saved to "/home/goye2cz/.jackdrc".
17:44:26.893 Statistics reset.
17:44:26.911 Client activated.
17:44:26.914 Audio connection change.
17:44:26.957 Audio connection graph change.

I have deactivated realtime and frames/period is set to 4096.

What do you make of it?

goye2cz[/QUOTE]

Just want to double-check. You have two sound cards on your system? Whatever existing card was in the computer and your US-122? Is that right?

---

### Post by schdefan on 2005-06-17
hi satchnut!

Did you follow the steps as described above. Maybe you missed to execute
> sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D 

schdefan

---

### Post by satchnut on 2005-06-18
[QUOTE=schdefan]hi satchnut!

Did you follow the steps as described above. Maybe you missed to execute...

schdefan[/QUOTE]
All *fxload* seems to do is increment the US-122 Device # by 1.

**SFN:**

$ sudo find / -name ld2-ezusb.hex
*/home/aphid/Desktop/usx2y-fw-0.1b/ld2-ezusb.hex*

$ sudo find / -name us122fw.ihx
*/usr/share/alsa/firmware/usx2yloader/us122fw.ihx*

---

### Post by SFN on 2005-06-18
[QUOTE=satchnut]All *fxload* seems to do is increment the US-122 Device # by 1.

**SFN:**

$ sudo find / -name ld2-ezusb.hex
*/home/aphid/Desktop/usx2y-fw-0.1b/ld2-ezusb.hex*

$ sudo find / -name us122fw.ihx
*/usr/share/alsa/firmware/usx2yloader/us122fw.ihx*[/QUOTE]

OK. So right before "sudo usx2yloader", you entered: 

```
sudo fxload -s /home/aphid/Desktop/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/003/007
``` 

Is that correct?

---

### Post by satchnut on 2005-06-19
[QUOTE=SFN]OK. So right before "sudo usx2yloader", you entered: 

```
sudo fxload -s /home/aphid/Desktop/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/003/007
``` 

Is that correct?[/QUOTE]
Yes, correct.

---

### Post by schdefan on 2005-06-19
After running
> sudo fxload -s /home/aphid/Desktop/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/003/007
did you see some lights turning on on the US-122.

Maybe you try it to run as root not as sudo.
And take a look at the last lines of /var/log/syslog or dmesg.

---

### Post by TimTheEnchanter on 2005-06-20
Hi. Brand new here, and to Ubuntu.

I've made it to the same step as Satchnut but I've managed to encounter a brand new error, and was hoping someone might have seen this:

```
can't modify CPUCS: Broken pipe
```

Any ideas on what the problem could be? I've verified that the files are present, and the ID numbers are correct as well.

---

### Post by SFN on 2005-06-21
satchnut,

My next question would have been the same as schdefan's. Any news on that?

---

### Post by SFN on 2005-06-21
[QUOTE=TimTheEnchanter]Hi. Brand new here, and to Ubuntu.

I've made it to the same step as Satchnut but I've managed to encounter a brand new error, and was hoping someone might have seen this:

```
can't modify CPUCS: Broken pipe
```

Any ideas on what the problem could be? I've verified that the files are present, and the ID numbers are correct as well.[/QUOTE]


Greetings, Tim The Enchanter!

I'm going to take a huge leap here and suggest actual hardware failure. Can you make your US-122 work via Windows? That is, have you been able to since you got this error? Try to find a Windows machine and plug the device in. If it gets recognized and installed, we can rule out hardware failure.

---

### Post by satchnut on 2005-06-21
[QUOTE=schdefan]After running

did you see some lights turning on on the US-122.

Maybe you try it to run as root not as sudo.
And take a look at the last lines of /var/log/syslog or dmesg.[/QUOTE]
None of the lights turned on -- same thing in root.
I didn't see any useful information in dmesg, so here is the entire output:

```
Linux version 2.6.10-5-686-smp (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Tue Jun 7 09:34:54 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003ff74000 (usable)
 BIOS-e820: 000000003ff74000 - 000000003ff76000 (ACPI NVS)
 BIOS-e820: 000000003ff76000 - 000000003ff97000 (ACPI data)
 BIOS-e820: 000000003ff97000 - 0000000040000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
 BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
127MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000fe710
On node 0 totalpages: 262004
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 225280 pages, LIFO batch:16
  HighMem zone: 32628 pages, LIFO batch:7
DMI 2.3 present.
ACPI: RSDP (v000 DELL                                  ) @ 0x000feb90
ACPI: RSDT (v001 DELL    8300    0x00000007 ASL  0x00000061) @ 0x000fd1cb
ACPI: FADT (v001 DELL    8300    0x00000007 ASL  0x00000061) @ 0x000fd1ff
ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffc90b3
ACPI: MADT (v001 DELL    8300    0x00000007 ASL  0x00000061) @ 0x000fd273
ACPI: BOOT (v001 DELL    8300    0x00000007 ASL  0x00000061) @ 0x000fd2df
ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Processor #1 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 3192.254 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 1030728k/1048016k available (1604k kernel code, 16652k reserved, 719k data, 192k init, 130512k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 6324.22 BogoMIPS (lpj=3162112)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: L3 cache: 2048K
CPU: Hyper-Threading is disabled
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 05
per-CPU timeslice cutoff: 1462.76 usecs.
task migration cache decay timeout: 2 msecs.
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay loop... 6373.37 BogoMIPS (lpj=3186688)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: L3 cache: 2048K
CPU: Hyper-Threading is disabled
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: Intel P4/Xeon Extended MCE MSRs (12) available
CPU1: Thermal monitoring enabled
CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 05
Total of 2 processors activated (12697.60 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking TSC synchronization across 2 CPUs: passed.
Brought up 2 CPUs
CPU0:
 domain 0: span 01
  groups: 01
  domain 1: span 03
   groups: 01 02
CPU1:
 domain 0: span 02
  groups: 02
  domain 1: span 03
   groups: 02 01
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4536k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfbb31, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:09: ioport range 0x800-0x85f could not be reserved
pnp: 00:09: ioport range 0xc00-0xc7f has been reserved
pnp: 00:09: ioport range 0x860-0x8ff could not be reserved
Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Simple Boot Flag at 0x7a set to 0x1
audit: initializing netlink socket (disabled)
audit(1119371647.294:0): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
VBTN PCI0 USB0 USB1 USB2 USB3 PCI1  KBD
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4536KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 192k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: IC35L080AVVA07-0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 160836480 sectors (82348 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
Probing IDE interface ide1...
hdc: HL-DT-STDVD-ROM GDR8162B, ATAPI CD/DVD-ROM drive
hdd: _NEC DVD+RW ND-2100AD, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (470 pages freed)
Restarting tasks... done
ext3: No journal on filesystem on hda1
Adding 2064312k swap on /dev/hda5.  Priority:-1 extents:1
hdc: ATAPI 48X DVD-ROM drive, 256kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 19
ALSA /usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/emu10k1/emufx.c:1385: Installing spdif_bug patch: Audigy 2 [Unknown]
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
input: PC Speaker
Real Time Clock Driver v1.12
inserting floppy driver for 2.6.10-5-686-smp
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i875 Chipset.
agpgart: Maximum main memory to use for agp memory: 941M
agpgart: AGP aperture is 256M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xff80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xff60
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xff40
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xff20
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 4-2: new full speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xffa80800
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usb 5-8: new high speed USB device using ehci_hcd and address 2
hw_random hardware driver 1.0.0 loaded
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 18
ata2: SATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 18
ata1: dev 0 cfg 49:2f00 82:346b 83:7f01 84:4003 85:3469 86:3e01 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 234375000 sectors: lba48
ata1: dev 0 configured for UDMA/133
scsi1 : ata_piix
ata2: SATA port has no device.
scsi2 : ata_piix
  Vendor: ATA       Model: ST3120026AS       Rev: 8.05
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 234375000 512-byte hdwr sectors (120000 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 234375000 512-byte hdwr sectors (120000 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host1/bus0/target0/lun0: p1
Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:03.2[B] -> GSI 18 (level, low) -> IRQ 18
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe8fa800-fe8fafff]  Max Packet=[2048]
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
e100: eth0: e100_probe: addr 0xfe8fb000, irq 20, MAC addr 00:0C:F1:D3:C0:F4
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c041103c494]
NET: Registered protocol family 17
  Vendor: SanDisk   Model: Cruzer Mini       Rev: 0.1
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sdb: 501759 512-byte hdwr sectors (257 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 501759 512-byte hdwr sectors (257 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 0
usb-storage: device scan complete
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0317e40(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled - APM is not SMP safe.
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.14.13 [Jun  8 2005] on minor 0
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
[fglrx] Kernel AGP support doesn't provide agplock functionality.
[fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 256126976
[fglrx] max   AGP = 256126976
[fglrx] free  LFB = 116387840
[fglrx] max   LFB = 116387840
[fglrx] free  Inv = 134217728
[fglrx] max   Inv = 134217728
[fglrx] total Inv = 134217728
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 65536
eth0: no IPv6 routers present
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
usb 3-2: new full speed USB device using uhci_hcd and address 2
usb 3-2: USB disconnect, address 2
usb 3-2: new full speed USB device using uhci_hcd and address 3
usb 3-2: USB disconnect, address 3
usb 3-2: new full speed USB device using uhci_hcd and address 4
```

---

### Post by SFN on 2005-06-23
[QUOTE=satchnut]None of the lights turned on -- same thing in root.
I didn't see any useful information in dmesg, so here is the entire output:
```

<snip>
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
</snip>

```
[/QUOTE]

It looks like you are using a USB hub plugged in to a USB port on your computer. Is that correct? If so, does the hub have a power supply or at least a jack for one? If it does, are you using the power supply? If not, try plugging in the power supply.

Although USB hubs can theoretically run without external power, a whole lot of USB devices fail through hubs unless the hub has external power.

---

### Post by satchnut on 2005-06-27
[QUOTE=SFN]It looks like you are using a USB hub plugged in to a USB port on your computer. Is that correct? If so, does the hub have a power supply or at least a jack for one? If it does, are you using the power supply? If not, try plugging in the power supply.

Although USB hubs can theoretically run without external power, a whole lot of USB devices fail through hubs unless the hub has external power.[/QUOTE]
Sorry I couldn't get back to you sooner...

The recorder is plugged directly into a USB 2.0 port in the motherboard. Could the fact that I'm running on a Dell desktop (Dimension 8300) be the culprit? Normally I would blame it on the crappy Dell OEM hardware, but the recorder *does* work in a Win environment... Mayby it's because Linux has little support for Dell hardware, or maybe it's because I didn't shower this morning...

---

### Post by schdefan on 2005-06-27
Hi satchnut!
Are you able to connect a digi cam or an USB stick to your USB input?
Maybe its not a problem with your soundcard but with your usb input.
schdefan

---

### Post by SFN on 2005-06-27
[QUOTE=satchnut]Sorry I couldn't get back to you sooner...

The recorder is plugged directly into a USB 2.0 port in the motherboard. Could the fact that I'm running on a Dell desktop (Dimension 8300) be the culprit?[/QUOTE]

I wouldn't think so. I could be wrong though.

>  Normally I would blame it on the crappy Dell OEM hardware, but the recorder *does* work in a Win environment...

If it's working under Windows, I would have to assume that the port is OK but try schdefan's suggestion of plugging some other USB device in. If that works then it's not the port. 

Assuming that is the case, open up a terminal and type in lsmod. Paste the results here.

Again, I'm not Joe USB but I'll see what I can do.

---

### Post by jshafer on 2005-06-30
Hi, all -- 

I have been able to follow the instructions to set up my Tascam US-122 so that I am getting sound.  Thanks for all the great tips.  But there are still two minor problems that I am hoping to resolve:

**(1) Occasional lack of sound** - I am having an intermittent problem where about 25% of the time the sound doesn't work upon bootup.  I can immediately tell there is a problem because there is no sound when arriving at the Ubuntu login screen.  If I reboot the machine the problem usually clears up, though sometimes I need to reboot a second time before the sound returns.  

Note:  I added the command "sudo usx2yloader" as an entry in my Gnome startup programs to automatically reinitialize the card upon reboot.  Not sure if this was the right way to do it...

**(2) Gaming** - I am getting no sound at all when starting the America's Army game; it appears that the application is not recognizing my USB audio device for some reason.  When I exit the game the sound returns.

Any suggestions?  Here is some information about my system:

OS:  Ubuntu Linux 5.04 i686 kernel (dual-boot with Windows XP)
PC:  Dell 4600, P4, 2.6GHz, 1GB RAM

Output from lsusb :
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:0810 Logitech, Inc. QuickCam Pro
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 001 Device 005: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 001: ID 0000:0000

Output from cat /proc/asound/cards :
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with AD1980 at 0xfebffa00, irq 17
1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                     TASCAM US-X2Y (1604:8007 if 0 at 001/005)

---

### Post by SFN on 2005-07-01
> **jshafer]**(1) Occasional lack of sound** - I am having an intermittent problem where about 25% of the time the sound doesn't work upon bootup.  I can immediately tell there is a problem because there is no sound when arriving at the Ubuntu login screen.  If I reboot the machine the problem usually clears up, though sometimes I need to reboot a second time before the sound returns.  

Note:  I added the command "sudo usx2yloader" as an entry in my Gnome startup programs to automatically reinitialize the card upon reboot.  Not sure if this was the right way to do it...[/QUOTE]

I'm assuming you did this by going to System, Preferences, Sessions, choosing the Startup Programs, then adding "sudo usx2yloader" there.

If that's the case, I have one idea. Edit that entry, changing the order to, say, 20. You might have to play with the order. (I should add that this is a guess as it seems to fix other things that I have added to the startup.)

[QUOTE]**(2) Gaming** - I am getting no sound at all when starting the America's Army game said:**
> : ICH4 - Intel ICH5
                     Intel ICH5 with AD1980 at 0xfebffa00, irq 17
1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                     TASCAM US-X2Y (1604:8007 if 0 at 001/005)


I'm clueless on that one. I might try disabling the onboard sound card in the BIOS then starting up. If America's Army plays through the TASCAM that way, there's your answer although it's not a very good one.


As always, if anybody else has better answers (or even just different answers), feel free. I'm just feeling my way through all of this.

---

### Post by schdefan on 2005-07-01
Hi jshafer!

When I disabled the internal soundcard in BIOS my Tascam works fine. 

Important is when you are adding "sudo usx2yloader" to the gnome autostarter that you are a superuser. You add yourself as superuser by editing the file /etc/sudoers with the command visudo (start as root)
> # User privilege specification
root    ALL=(ALL) ALL
<you> ALL=(ALL) ALL

Or you can write a startup skript that contains the command usx2yloader and put that into your /etc/init.d directory. Build a symbolic link with update-rc.d.
The Skript should look like that
```
#!/bin/bash
# file: tascam_US-122
# load usx2yloader at boot time


# some outputs
BUS=`lsusb | grep Tascam | cut -d " " -f 2`
DEVICE=`lsusb | grep Tascam | cut -d " " -f 4 | cut -c 1-3`
US122_IHX=`locate us122fw.ihx`
EZUSB_HEX=` locate ld2-ezusb.hex`

echo "bus: " ${BUS}
echo "device: " ${DEVICE}
echo "us122_ihx: " ${US122_IHX}
echo "ezusb_hex: " ${EZUSB_HEX}

## i think you have to run this command only once not every time you boot 
#/sbin/fxload -s ${EZUSB_HEX} -I ${US122_IHX} -D /proc/bus/usb/${BUS}/${DEVICE}

/usr/bin/usx2yloader

echo "the control LEDs of the tascam US-122 should light up"
cat /proc/asound/cards

``` 

save this skript into /etc/init.d/tascam_US-122

build the startup link
> #update-rc.d tascam_US-122 defaults

Hope this helps
schdefan

---

### Post by jshafer on 2005-07-04
schdefan,

Sorry for the delay in getting back to you... I ended up reinstalling my entire Ubuntu system yesterday for some other reasons.  I finally had the chance tonight to go through the US-122 install procedure again.

I thought that the script you suggested was a great idea, so I tried using it but it doesn't seem to be getting loaded at boot time.  None of the "echo" lines print out during boot up, and I still need to manually run the "sudo usx2yloader" command after logging in.  What is interesting, though, is that the "echo" lines for the tascam_US-122 bash script are in fact printing out when I _shut down_ the system.  

Do you know how I could move the tascam_US-122 bash script up earlier in the sequence so that it would be called during boot-up rather than at shut-down?  (This is actually my first bash script, so I'm learning here...)

Also, some good news:  the sound is working in America's Army and other multimedia apps now.  \\:D/  The only thing I'm missing now is the collection of Gnome desktop sounds (i.e., startup, shutdown, browser links, panel buttons, etc.).  I am hoping that once I get the bash script loaded prior to starting X/Gnome, then maybe those other sounds will start working too.  We'll see.

BTW - I did go ahead and disable my other sound card in BIOS, and the Tascam US-122 still works fine in Windows XP so I think I'll leave it that way.  Should have done that a long time ago, as I've never used that other sound card.

Thanks,
jshafer

---

### Post by schdefan on 2005-07-04
hi jshafer!

Good to hear that the sound is working. 
Do a updatedb as root. That wil locate all files on your harddisc in a db. SO in the bash script from above the locate calls will work may they are empty. 
have a look at the directory /etc/rc5.d/. There has to be a symbolic link 

> ls -lah /etc/rc5.d
S20bootUS_122-->/etc/init.d/boot_US122

That S means start it in Runlevel 5 at boot time. All links starting with K means execute them when you shutdown.


Are you sure that you are sudo?


Recently installed a new ubuntu version and the tascam install procedures after playing music files my system freezes completely! Still have to find out why this happens. On the same machine it was working fine on debian unstable.

schdefan

---

### Post by jshafer on 2005-07-04
schedfan,

I figured out that GDM was getting called at S13, earlier than the tascam_US-122 bash script at S20.  So, obviously I wasn't seeing any screen output because Gnome was already loading prior to the bash script...

I used Boot-up Manager (BUM) to change the sequence of the tascam_US-122 bash script to S12, which was the same sequence # as ALSA.  While experimenting with various combinations of things in the bash script (and rebooting lots of times) I noticed something interesting:  the control LEDs on the Tascam US-122 were actually lighting up much earlier in the bootup process, prior to the tascam_US-122 bash script even getting called.

Apparently my Tascam US-122 is getting initialized during the "Starting hotplug subsystem..." step in the Ubuntu bootup process.  However, even though the lights were coming on, they would then go out again as soon as GDM started loading.

To slow things down a bit and see what was going on, I added a "sleep 5" command at the end of my tascam _US-122 bash script.  After I added this in, the lights were still staying on even after GDM started.  Then I actually commented out the "usx2yloader" command in the bash script, and the lights are still staying on through the entire bootup process!

So, as of right now, my Tascam US-122 is effectively getting initialized automatically at bootup without even running "usx2yloader", just by adding a pause between starting ALSA and starting GDM.  It's kind of bizarre, but my theory is that perhaps ALSA needed some time to get set up with the USB device and then starting GDM immediately afterward (not allowing ALSA to finish) was killing it.

Although the Tascam US-122 now seems to be consistently initializing at bootup, I am still having some sound problems with various applications.  It seems that I have either a choice of running the system sounds (startup, shutdown, panel buttons, etc.) or multimedia apps, but not both at the same time.  I have also seen XMMS and mozilla-mplayer lock-ups, etc.  

At this point I think I need to keep experimenting with my ALSA vs. ESD vs. OSS  configuration to get it all working nicely together.  From other forum posts I've read, I guess that is kind of a "holy grail" that few people have been able to achieve in Linux.

- jshafer

---

### Post by schdefan on 2005-07-05
I think the first lights came up when hotplug is getting loaded.
From man hotplug
> hotplug  is  a  program which is used by the kernel to notify user mode software when some significant (usually hardware-related) events take
       place.  An example is when a USB or Cardbus device has just been plugged in.  This  is  useful  for  automatically  loading  and  setting  up
       drivers, packaged either as kernel modules or as user mode programs.

Later on alsa is running and maybe here the usx2yloader is already integrated?
And that is why the lights light up again?

Still good to hear that someone else is interested in having running a TASCAM US-122 on linux. I will have to fix my problem. After executing usx2yloader the system freezes.

---

### Post by schdefan on 2005-07-07
I installed a new ubuntu system on may harddisc. Before that I had an unstable debian system with a running tascam US122 on my computer.

Now when i try to run the fxload command and then the usx2yloader i get the following output. (my script from previous post)
> root@yoshimi:~ # /etc/init.d/tascam_US-122
bus:  003
device:  004
us122_ihx:  /usr/share/alsa/firmware/usx2yloader/us122fw.ihx
ezusb_hex:  /usr/share/alsa/firmware/usx2yloader/ld2-ezusb.hex
microcontroller type: fx
1st stage:  load 2nd stage loader
open RAM hexfile image /usr/share/alsa/firmware/usx2yloader/ld2-ezusb.hex
stop CPU
** LINE: :03000000020046B5
record too short?
unable to download /usr/share/alsa/firmware/usx2yloader/ld2-ezusb.hex
usx2yloader: no US-X2Y-compatible cards found
the control LEDs of the tascam US-122 should light up
0 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                     TASCAM US-X2Y (1604:8007 if 0 at 003/004)

i don't know what is wrong now. But what is very strange that i have to reconnect the soundcard so that the module will be loaded to the kernel.
Is this dependent on the order of the startup scripts.
I have that order
S20hotplug
S21alsa
S22tascam_US-122

outout from dmesg
> usb 3-2: new full speed USB device using ohci_hcd and address 3
usb 3-2: USB disconnect, address 3
usb 3-2: new full speed USB device using ohci_hcd and address 4
usbcore: registered new driver snd-usb-usx2y
usb 3-2: usx2yloader timed out on ep0out
usb_set_interface error
usb 3-2: usx2yloader timed out on ep0out
usb_set_interface error

SFN: do you have any ideas?

schdefan

---

### Post by SFN on 2005-07-08
The one thing that I can add to this (admittedly, I would have given up before getting as far as you two have) is that I don't have the US-122 start up automatically. I start it manually and don't see any of the issues you're seeing. 

Have all of your problems come about since you set it up to start automatically? I can see why you want it to do so but if you still have the problem when starting it manually, you may be headed in the wrong direction to solve this.

Just a suggestion. Hope you can get it working.

---

### Post by gibbon_ on 2005-10-23
I wanted to use that tascam US-122 not only for PCM but also for MIDI. I use the current AGNULA DeMuDi with kernel 2.6.12-multimedia-k7-smp, Alsa 1.0.9 and used Firmware 0.1b for the tascam. MIDI works great on my iBook,  but if i press a key on the Midi KEyboard under Linux, the MIDI IN Light doesnt react. Neither does the application. 

I can see the midi device in the qjackctl Connect MIDI tab, i can also connect it to other applications but the device doesn#t produce MIDI Events with linux. As already said, the Device, my Keyboard and the cables are proofed to be working. :/
I'm out of ideas. 

Is there anyone, who got it to work? Is there any more information i can provide?

If someone is curious about why i post that here: 2 reasons.

1. I used this howto, to get it to work
2. Agnula DeMuDi and ubuntu are not that different in the nitty gritty parts.

I beg you please! Help!

---

### Post by fp-www.tonepad.com on 2005-12-10
I have a Tascam US-224 and I've tried many of the howto's including the one mentioned at the beginning of the thread (with the changes for 224 instead of 122) and haven't had any success.

The commands I've used are:

lsusb
sudo fxload -s /home/triode/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us224fw.ihx -D /proc/bus/usb/001/003
(the files are in those directories, but I have the us224fw.ihx in two directories, I think)
sudo usx2yloader


The firmware loads with fxload, to verify this I check that the numbers have changed like langerland.de site mentions. Also, before loading the firmware when entering the "lsusb" command I get "without fw" in the device list (in the same line as the tascam us224)

Then, when trying the "sudo usx2yloader" command I get "No US-x2y compatible cards found".

I'm using a dell laptop with onboard sound, this one is working fine, but I can't disable it on the bios.

"cat /proc/asound/cards" command returns:
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with STAC9750,51 at 0xf4fff800, irq 7
1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                     TASCAM US-X2Y (1604:8005 if 0 at 001/004)


So, apparently it's already there, but the USB LED on the tascam doesn't light up. I have yet to try checking if it lights up briefly during boot.

How can I select that card? am I doing something wrong? any experiences with US-224?

---

### Post by fp-www.tonepad.com on 2005-12-10
I got the USB LED on!! (and the other leds blinked!)

All  I did was download the alsa-firmware-1.0.9.tar.bz2 and copy the contents of the /usx2yloader/* folder to the /usr/share/alsa/firmware/usx2yloader/*, then instead of using the "sudo usx2yloader" i used "sudo usx2yloader -c 1" which was the number that had the Tascam in "cat /proc/asound/cards", otherwise it said that no usx2y cards were available.

Note that I think this is how you set it up without disabling the onboard sound on the bios (which I didn't have the option for)

Wow, I hope I really did got this issue solved! I'm off to try some recording/playback experiments on that card.

I'll report soon.
Fp

---

### Post by fp-www.tonepad.com on 2005-12-10
Ok, it worked. I got sound!

We need to have the alsa-firmware package added to the Kubuntu/ubuntu repositories. So that it can support tascam usx2y devices.

---

### Post by schdefan on 2005-12-10
Good to hear that you got it working. I was struggling 6 month with my tascam us-122. On that hard way i found out ubuntu.

schdefan

---

### Post by ITGrooves on 2005-12-11
Hello. I'm writing a paper about Linux for pro-Audio in the framework of an Audio Engineer Education Program. Big thanks to SFN for the installation tips on the Tascam US122. Following the instructions we got it up and more or less running. It's the first device with which I managed to get any audio INTO Linux (connected my Ipod to the line-in of the Tascam, and recorded it with Ardour) ! Still some issues though. 1) The recorded audio is crap : plenty of distortion. Also when playing a .wav file of good quality from within Ardour the resulting sound is horrible. This must be a jack-issue, because playing the same file with aplay through the Tascam gives a very good result. 2) The Tascam doesn't receive MIDI. I loaded a MIDI-file in Rosegarden, selected the TASCAM as MIDI device, pressed 'play' but nothing comes in ! Same configuration from Cubase on a WinXP works, so it is not the TASCAM ! Same configuration with Rosegarden using an M-Audio Audiophile USB interface also works, so it's not Linux ! Then what is it ????
My paper has to be ready this week, I'll be glad to send it out to anyone who's interested.
Thanks and regards,
Ivo Vangerven

---

### Post by ITGrooves on 2005-12-11
[QUOTE=gibbon_]I wanted to use that tascam US-122 not only for PCM but also for MIDI. I use the current AGNULA DeMuDi with kernel 2.6.12-multimedia-k7-smp, Alsa 1.0.9 and used Firmware 0.1b for the tascam. MIDI works great on my iBook,  but if i press a key on the Midi KEyboard under Linux, the MIDI IN Light doesnt react. Neither does the application. 

I can see the midi device in the qjackctl Connect MIDI tab, i can also connect it to other applications but the device doesn#t produce MIDI Events with linux. As already said, the Device, my Keyboard and the cables are proofed to be working. :/
I'm out of ideas. 

Is there anyone, who got it to work? Is there any more information i can provide?

If someone is curious about why i post that here: 2 reasons.

1. I used this howto, to get it to work
2. Agnula DeMuDi and ubuntu are not that different in the nitty gritty parts.

I beg you please! Help![/QUOTE]

IMPORTANT : I was fooled by this too initially ! The MIDI-IN light of the Tascam reacts to whatever MIDI-device is plugged into the MIDI in connection of the Tascam. So if you have your keyboard's MIDI OUT  connected directly to the MIDI IN of the Tascam the red light should be lit. But if you send MIDI data over the USB cable to the Tascam (e.g. from within a MIDI software sequencer) the MIDI IN light of the Tascam will not light up  !

---

### Post by schdefan on 2005-12-12
HiITGrooves!
I am very interested in your paper. Haven't tried MIDI in Linux yet but i will give it a try.
schdefan

---

### Post by bobbyshane on 2006-03-02
Any idea if this would work with a us 428?

---

### Post by schdefan on 2006-03-06
Hi!
Should work as well with a 428 with the same module. 
Have a look here
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Tascam#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Tascam#matrix")

schdefan

---

### Post by martintfd on 2006-04-23
Hi,

Firstly many thanks to SFN for making this information available I'm fairly new to Linux so when things don't work as expected these guides are invaluable!

I'm having trouble downloading [http://langerland.de/audio/usx2y/usx2y-fw-0.1b.tar.bz2](http://langerland.de/audio/usx2y/usx2y-fw-0.1b.tar.bz2), on following the link I'm greeted with "error 404: Datei nicht gefunden!".  Is there anywhere else to get this file?

Thanks

Martin

---

### Post by Matze on 2006-04-30
Anyone has managed to get the Tascam US-122 working in Dapper Drake Beta?
I've tried almost anything but lights wont come up :-(
Any help would be great!
Thanks!

---

### Post by passonno on 2006-05-11
Well, now with a new install of Breezy, I cannot believe the crap I have to go through to deal with this.  

     root@ubuntu:~/Desktop# dpkg -i alsa-tools_1.0.5-2_i386.deb
(Reading database ... 59967 files and directories currently installed.)
Preparing to replace alsa-tools 1.0.5-2 (using alsa-tools_1.0.5-2_i386.deb) ...
Unpacking replacement alsa-tools ...
dpkg: dependency problems prevent configuration of alsa-tools:
 alsa-tools depends on libfltk1.1c102 (>= 1.1.4+1.1.5rc1); however:
  Package libfltk1.1c102 is not installed.
dpkg: error processing alsa-tools (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alsa-tools




Then I tried this:        root@ubuntu:~/Desktop# apt-get install alsa-tools
Reading package lists... Done
Building dependency tree... Done
alsa-tools is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  alsa-tools: Depends: libfltk1.1c102 (>= 1.1.4+1.1.5rc1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


So, essentially I cannot install my US122 because, alsa-tools depends on an older fltk package that I cannot obtain nor install.  

Anyone have any ideas?

---

### Post by passonno on 2006-05-12
So now I am in Dapper, trying to install the us122, and here's what's happening.  I download packages, get all the deps resolved, and this is what happens when is run usx2yloader:

root@anthony-laptop:~/Downloads# usx2yloader
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:1
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:2
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:3
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:4
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:5
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:6
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evalroot@anthony-laptop:~/Downloads# usx2yloader
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:1
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:2
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:3
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:4
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:5
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:6
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:7
usx2yloader: no US-X2Y-compatible cards found
uate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:7
usx2yloader: no US-X2Y-compatible cards found


Any ideas?

---

### Post by schdefan on 2006-05-12
Is your soundcard recognized as usb device?

---

### Post by passonno on 2006-05-13
Yep.  

lsusb lists it as 003/006

---

### Post by passonno on 2006-05-13
Yep.  

lsusb lists it as 003/006


I just might go back to breezy again, maybe Dapper is weird?

---

### Post by schdefan on 2006-05-17
maybe you should try again in breezy. With the first post of this thread you should hear music from US-122.
Try another USB-Port as well!

---

### Post by aldous on 2006-07-12
I'd be interested in knowing if you ever found the source of your crappy/distorted audio problem (us-122).  I've had the loader working for months, but the audio output clips and distorts and generally sounds like poop.  The onboard soundcard sounds fine.  I think it is jack related.  jack zombifies after a period of use with the us-122.

---

### Post by Svictor on 2006-11-20
For anyone interested, once you configure your card, there is a [way to automatically load the appropriate drivers and firmwares]("http://www.astro.caltech.edu/%7Emcs/tascam_us122/index.html"), _**through udev**_ (good for Edgy). I just managed to setup my Tascam us-224, following this thread and that tip. :-D 

Only problem is I can't start us428control: there is no error  message (even with option -v2), just nothing happens. The terminal does not return to a prompt and > ps -ef | grep us428control shows the prog. is running... So maybe this is expected behaviour ? :-k Can anyone shed a light on what us428control is supposed to do ?

[EDIT:]

Foudn out: us428control is for the card's midi controlers. In jack, we get 2 entries: Tascam (blah blah) - which is for the midi entry on the card, and us428control, which represents the faders, knobs, buttons... Loading us428control is necessary for the latter to appear to work.

---

### Post by dpids on 2006-12-30
> **SFN said:**
> I wouldn't think so. I could be wrong though.



If it's working under Windows, I would have to assume that the port is OK but try schdefan's suggestion of plugging some other USB device in. If that works then it's not the port. 

Assuming that is the case, open up a terminal and type in lsmod. Paste the results here.

Again, I'm not Joe USB but I'll see what I can do.

I also have a Tascam US-122 and am getting the "can't modify CPUCS: Broken Pipe" error
when trying to load the firmware. This thread is the best info I've been able to find but it seems to stop here without an answer. Was it the crappy Dell? (I have a Dell and the Tascam works fine under Windows so I can't blame the port), external powered hub?, disabling the internal sound card in BIOS?, ..... I can't see the solution in this thread. If somebody could point me in the right direction.......

---

### Post by i_am_nitrogen on 2007-01-10
A note to everyone experiencing audio distortion with Jack when using a US-x2y: you will need to set the buffer sizes large enough to give 21ms latency or more.  I don't know why Jack can only do 21ms when the Windows drivers can reach 5.33ms.  I think it's a misconfiguration in the Linux driver.  If you are below 21ms, Jack will not report xruns but will still act as though it is having xruns.  If you are below ~15ms, jack will report xruns.

I wrote a simple program that uses the smallest buffer size I can get away with and simply passes audio from the input to the output, and as I recall the results were similar.

---

### Post by i_am_nitrogen on 2007-01-10
I have now successfully managed to get my Tascam US-428 working in Kubuntu.  I ran into every single problem described in this thread ](*,), but I didn't give up because it worked great with Gentoo before I switched to Kubuntu.  Here is a list of solutions to the common problems :

Q. Jack's audio is crunchy/"distorted"
A. Increase buffer sizes to get over 21ms latency, easiest using qjackctl.  -- Note: if anyone is able to use the US-x2y lower latencies (5.33ms?), please add a comment describing the motherboard (and USB interface if not integrated) you are using.

Q. CPUCS: broken pipe error
A. You are most likely using the wrong USB device - double check lsusb

Q. record too short? error
A. There is something wrong with the fxload package in Ubuntu's repositories.  I rebuilt the package, making a few changes to account for missing/moved header files, and the message went away.  I've attached my package to this message.  Though it isn't built right for inclusion in the repository, it might help someone out there.


Edit: I've attached my /etc/udev/rules.d/55-tascam.rules file (in compressed form), which should work for any x2y device (I've only tested it with my 428).  Unfortunately I can't get us428control to detach from the udevd process, so udevd has an extra child hanging around with the US-428.  us428control needs to have self-daemonization implemented.

---

### Post by ronlybonly on 2007-01-25
I just got my very own Tascam US-122 in the mail yesterday! \\:D/  ...unfortunately, I can only playback audio for anywhere between 2 and 20 seconds - the whatever application is playing back the audio pauses. For instance, when I fire up Moby's "Drop a Beat" in xmms or rhythymbox, it will play the first few seconds of the track, the it pauses. Now I can play it from that point again, but after several seconds... it pauses. Has anybody else here had similar problems?
Also, in the gnome volume control app, I can only control the tascam through the OSS mixer, and I would really prefer to use the alsa mixer if at all possible. When I try to run alsamixer -c 1 (which is the number of the Tascam), I get the error message: "No mixer elems found." I don't think this should be happening, but I have no clue how to fix it. I would REALLY appreciate some help!

-Andrew

---

### Post by i_am_nitrogen on 2007-01-25
> **ronlybonly said:**
> I just got my very own Tascam US-122 in the mail yesterday! \\:D/  ...unfortunately, I can only playback audio for anywhere between 2 and 20 seconds - the whatever application is playing back the audio pauses. For instance, when I fire up Moby's "Drop a Beat" in xmms or rhythymbox, it will play the first few seconds of the track, the it pauses. Now I can play it from that point again, but after several seconds... it pauses. Has anybody else here had similar problems?
Also, in the gnome volume control app, I can only control the tascam through the OSS mixer, and I would really prefer to use the alsa mixer if at all possible. When I try to run alsamixer -c 1 (which is the number of the Tascam), I get the error message: "No mixer elems found." I don't think this should be happening, but I have no clue how to fix it. I would REALLY appreciate some help!

-Andrew

To help diagnose your audio pausing problem, can you install mpg321/mpg123 and try playing the song from the command line?  Also try playing a .wav file with aplay from the command line.  I suspect that somehow your computer isn't keeping up with the Tascam's need for audio.

As for your "No mixer elems found" error - the Tascam audio devices don't have a mixer control.  Sure, there is mixing going on when you are listening to the input monitor, but as far as a software-controlled mixer like a traditional sound card has, there isn't one.  Are you sure that Gnome is really controlling the volume of the Tascam?  My US-428 volume can be controlled using the MASTER slider when us428control is running, but I don't know if the 122 has any kind of volume control on it.

---

### Post by ronlybonly on 2007-01-30
> **i_am_nitrogen said:**
> To help diagnose your audio pausing problem, can you install mpg321/mpg123 and try playing the song from the command line?  Also try playing a .wav file with aplay from the command line.  I suspect that somehow your computer isn't keeping up with the Tascam's need for audio.

Okay. I ran aplay, and...
```
meredithas@meredithas-laptop:~$ aplay -D plughw:1,0 ./Desktop/sine.wav 
Playing WAVE './Desktop/sine.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Mono

```
The audio still pauses even though aplay doesn't throw an error. Odd.

Also, when I play an audio file and it freezes, this is what shows up on the output of dmesg:
```
[17179691.160000] ALSA /usr/src/alsa/alsa-driver-1.0.13/usb/usx2y/usbusx2yaudio.c:305: Sequence Error!(hcd_frame=897 ep=8in;wait=889,frame=893).
[17179691.160000] Most propably some urb of usb-frame 889 is still missing.
[17179691.160000] Cause could be too long delays in usb-hcd interrupt handling.
```
Matt from the ALSA-users mailing list suggested that I try applying the attached patch to my kernel and recompile, which I did (manually, since the patch was designed for a different kernel version). I tried this on my Dapper box, and it solved all my problems, but it didn't change a thing on Edgy. I might try to give the kernel compile another go tonight and see if it miraculously changes anything. Otherwise, I'm going to start ripping my hair out of my head. ](*,) I would REALLY appreciate some more help. I just don't want to have to install windows on my new dell just to be able to use the Tascam!

Thanks!
-Andrew

---

### Post by i_am_nitrogen on 2007-01-31
> **ronlybonly said:**
> Also, when I play an audio file and it freezes, this is what shows up on the output of dmesg:
```
[17179691.160000] ALSA /usr/src/alsa/alsa-driver-1.0.13/usb/usx2y/usbusx2yaudio.c:305: Sequence Error!(hcd_frame=897 ep=8in;wait=889,frame=893).
[17179691.160000] Most propably some urb of usb-frame 889 is still missing.
[17179691.160000] Cause could be too long delays in usb-hcd interrupt handling.
```

Okay, this looks familiar.  The snd-usb-usx2y command has a parameter to control the number of messages per USB block (or something like that - I'm not in Linux at the moment).  Use modinfo snd-usb-usx2y to get the details.  Try setting it to 1, and if that doesn't fix the problem (1 allows low latency) try higher numbers, like 3 or 4, or more if it will let you.

The other possible fix is increasing the priority of your USB IRQ handler.  This only works if you've got the full-realtime kernel patches from Ingo Molnar (google for ingo molnar realtime) and you're running with threaded interrupt handlers.  There's a program called chrt (change realtime priority) that's in a package named sched-tools or something similar (apt-cache search sched perhaps).  Find the USB ports' IRQ (cat /proc/interrupts), then do chrt -p -f 80 `pidof "IRQ *nn*"`.

> I would REALLY appreciate some more help. I just don't want to have to install windows on my new dell just to be able to use the Tascam!

I know the feeling.  Tascam support still doesn't seem perfect, but I've finally managed to get mostly-skip-free audio at 2.66ms to 5.33ms latency with 4 channel recording.  I just can't run any other audio programs after jack quits until I power cycle my US-428.

Unfortunately I still have to use Windows for my music software (ACID Pro).  There simply isn't an open source music tool that is as reliable, consistent, and feature-rich as ACID (and I don't have time to write one).  Rosegarden and Muse are both promising, but neither supports loops or beat-sliced time stretching.

---

### Post by ronlybonly on 2007-01-31
Thanks! I'll give it a shot and let you know how it turns out.

---

### Post by ronlybonly on 2007-02-03
Thanks! I ended up using the feisty 2.6.20 kernel, which apparently has all of the bugs worked out (at least as far as the snd-usb-usx2y module). Tho only problem now is very crackly sound in jack, but I can probably figure that one out with a little help from the jack mailing list.

---

### Post by i_am_nitrogen on 2007-02-04
> **ronlybonly said:**
> Thanks! I ended up using the feisty 2.6.20 kernel, which apparently has all of the bugs worked out (at least as far as the snd-usb-usx2y module). Tho only problem now is very crackly sound in jack, but I can probably figure that one out with a little help from the jack mailing list.

My jack sound was crackly until I either increased the buffer sizes to get >20ms latency, or patched my kernel with the realtime patches and increased the priority of my USB port's IRQ handler.  If you're able to work out another way of improving jack's performance, be sure to share the info!

---

### Post by bsalt on 2007-02-07
SFN, awesome How-to! I had to rename the code with us224fw.ihx instead of us122fw.ihx, but other than that, this was awesome! 

You are my hero.

---

### Post by jonobo on 2007-02-12
Hi - thanks for the Howto - it worked good so far and i got my US-122 with a green USB-LED-On hanging on my USB-Port.

After reading through this very informational thread i learned by now that there is no software-mixer for the tascam devices. I simply don't understand how to tell my machine to playback sound through the US-122 instead of my built-in soundchip - can anybody hint-click-kick-my-jazz ?

Some infos on my actual system-status:
```
root@zbox:/# cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC655 at 0x1800, irq 209
 1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                      VIA 82XX modem at 0x1c00, irq 209
 2 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 003/007)
```

```
root@zbox:/# lsusb
Bus 003 Device 007: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

Everything seems green and ready to go - what am i missing ?

---

### Post by bsalt on 2007-02-12
Do this:

sudo apt-get install jackd qjackctl

On your Sound and Video menu, there should appear a Jack Control app. Click it, and then click on Setup. For your input device, you should be able to select Tascam, and the same for output. I'll hook up my US-224 and try it myself. I'll let you know shortly.

---

### Post by jonobo on 2007-02-12
Hi bsalt, thanks for the answer ;)

Jack was already installed, is started it up, hit setup and landed in settings-tab.

Driver: ALSA
Input: hw2 TASCAM US-X2Y
Output: hw2 TASCAM US-X2Y

There was another option choosable: hw2,0 US-X2Y Audio #0 .

So far so good.
I started Ardour and played back a beatloop - the sound still being played over my laptop-chip. 
So i double checked if the Jack-Connections-Window, it shows me... before i write too much - here is a self-explaining screenshot:
[[IMG]http://img504.imageshack.us/img504/7822/shotzjack002ez0.th.png[/IMG]](http://img504.imageshack.us/my.php?image=shotzjack002ez0.png)

So - these settings playback on my onboard-chip - even after restarting Jack. I'll keep tryin... ...is it possible to playback sound over the US-122 without Jack ? 
Okay, not really an important question right now - because i need Jack anyway to record in Ardour, the very moment i cannot try to record, because i'm still waiting for my XLR-Cable - but playback should work anyway. 

Any suggestions ?

[Edit 1: Playback works in Audacity without Jack, i simply choose Settings, Playback -> Device : /dev/dsp2 and i got sound - but still need to solve the Jack issue]

[Edit 2: Standard Sound Playback set - i simply missed to change this: Ubuntu Desktop -> System -> Settings -> Audio -> Playback -> US-X2Y Audio #0 - now it plays back most things through the TASCAM Line-Out - but the Jack-issue is still unsolved, Ardour playback for example still runs through my onboard-chip like described above *wonder* ?]

[Edit 3: Okay, sometimes my normal audio-players don't work, and i have to turn off Jack, or on, and switch around a lot, but i can record with Ardour, Hydrogen, Jamin, ... - so i am happy for now :) ]

---

### Post by ssavelan on 2007-02-18
The langerland link is no longer there



........................

Anyone have a iMic working?

---

### Post by pixeldotz on 2007-03-21
does anyone know how to get a usb mixer working?
i have an alesis multimix 8 that has not drivers because it does not require any under windows and macos.

i have been trying for over a week with no luck. lsusb sees the device fine but alsa aplay -l does not nor does any other type of audio app.

---

### Post by i_am_nitrogen on 2007-03-22
> **pixeldotz said:**
> does anyone know how to get a usb mixer working?
i have an alesis multimix 8 that has not drivers because it does not require any under windows and macos.

i have been trying for over a week with no luck. lsusb sees the device fine but alsa aplay -l does not nor does any other type of audio app.

Try aplaymidi -l and arecordmidi -l -- the USB mixer probably isn't an audio device, but a USB MIDI device.  It should show up under your MIDI routing with alsa-patch-bay or qjackctl.

EDIT: Make sure you are using the USB and not the firewire Multimix 8, and also try searching for information on generic USB audio drivers (snd-usb-audio).  I retract my previous statement about it being a MIDI device.

---

### Post by vvojtek on 2007-04-02
Have any solution 
This my problem [http://www.ubuntuforums.org/showthread.php?t=399594](http://www.ubuntuforums.org/showthread.php?t=399594)


:(

---

### Post by i_am_nitrogen on 2007-04-07
> **ssavelan said:**
> The langerland link is no longer there

You can get the file from the alsa-firmware package at alsa-project.org.

---

### Post by BobboProfondo on 2007-06-20
Here's a question. I got a Tascam US-428, and I've got it quite happily running with Ubuntu Studio (Feisty, of course), to an extent. 

I don't have any problem with xruns in Jack and have recorded 2 channel that I'm really happy with. I'll confess I'm a bit of a Linux noob, so how do I get the 428 to expose all four channels to Jack? Only two appear in the connections box and I noticed someone mentioned that they have been recording on 4 channels...

I'm sure you need more info, so please ask away, or tell me what to punch into the terminal...

TIA

---

### Post by i_am_nitrogen on 2007-06-21
> **BobboProfondo said:**
> Here's a question. I got a Tascam US-428, and I've got it quite happily running with Ubuntu Studio (Feisty, of course), to an extent. 

I don't have any problem with xruns in Jack and have recorded 2 channel that I'm really happy with. I'll confess I'm a bit of a Linux noob, so how do I get the 428 to expose all four channels to Jack? Only two appear in the connections box and I noticed someone mentioned that they have been recording on 4 channels...

I'm sure you need more info, so please ask away, or tell me what to punch into the terminal...

TIA

I have a US-428.  It quit working in Linux when I upgraded from a VIA chipset and Edgy to an nForce 4 mobo and Feisty, but that's another story...  There are two steps to getting 4-channel recording:

1. Add the nr_packs=1 option to the snd_usb_usx2y kernel module (look for howtos on /etc/modules.d/* if you're not sure how).
2. Run jackd with device index 2 on the Tascam.  For example, if the US-428 is at hw:1, you would use hw:1,2 instead (it's been a while, so the syntax may be slightly different).

That should do it.

---

### Post by BobboProfondo on 2007-06-21
> **i_am_nitrogen said:**
> I have a US-428.  It quit working in Linux when I upgraded from a VIA chipset and Edgy to an nForce 4 mobo and Feisty, but that's another story...  There are two steps to getting 4-channel recording:

1. Add the nr_packs=1 option to the snd_usb_usx2y kernel module (look for howtos on /etc/modules.d/* if you're not sure how).
2. Run jackd with device index 2 on the Tascam.  For example, if the US-428 is at hw:1, you would use hw:1,2 instead (it's been a while, so the syntax may be slightly different).

That should do it.

Thanks for that. I'll try it shortly and let you all know how it goes. Much appreciated. :D

---

### Post by BobboProfondo on 2007-06-23
> **i_am_nitrogen said:**
> I have a US-428.  It quit working in Linux when I upgraded from a VIA chipset and Edgy to an nForce 4 mobo and Feisty, but that's another story...  There are two steps to getting 4-channel recording:

1. Add the nr_packs=1 option to the snd_usb_usx2y kernel module (look for howtos on /etc/modules.d/* if you're not sure how).
2. Run jackd with device index 2 on the Tascam.  For example, if the US-428 is at hw:1, you would use hw:1,2 instead (it's been a while, so the syntax may be slightly different).

That should do it.

Well I did a bit of research into the nr_packs option (incidentally what does this change?) but the closest I think I got is described below. 

I may be doing something daft here, but the steps I follow are...

```
sudo modprobe snd_usb_usx2y nrpacks=1 (and password)
```
Plug in the USB
```

usx2yloader
us428control &

```

Once I've run these, start Jack Control, and choose hw:1,2 as my interface (which says 'US-X2Y hwdep Audio' next to it.)

Start the Jack server, and the four inputs are there in the connections list. Yippee! :D

Then, however, when I start Rosegarden, or try to connect Audacity or Meterbridge, Jack stops and last night when I was trying this I got loads of messages about Broken Pipes. 

On trying to replicate this again this morning (probably with different settings) I get the following, but the result is just the same, Jack stops. 

11:04:34.051 MIDI connection graph change.
11:04:37.688 Startup script...
11:04:37.692 artsshell -q terminate
11:04:38.001 Startup script terminated with exit status=256.
11:04:38.004 JACK is starting...
11:04:38.007 /usr/bin/jackd -v -R -dalsa -dhw:1,2 -r44100 -p256 -n8
11:04:38.028 JACK was started with PID=6599 (0x19c7).
11:04:40.129 Server configuration saved to "/home/bob/.jackdrc".
11:04:40.133 Statistics reset.
11:04:40.158 Client activated.
11:04:40.174 Audio connection change.
11:04:40.207 Audio connection graph change.
11:04:53.157 Audio connection graph change.
11:04:53.860 Audio connection graph change.
11:04:53.899 Audio connection change.
11:04:53.999 Audio connection graph change.
11:04:54.027 MIDI connection graph change.
11:04:56.259 MIDI connection change.
11:04:56.263 Shutdown notification.
11:04:56.266 Client deactivated.
11:04:56.274 JACK was stopped successfully.
11:04:56.275 Post-shutdown script...
11:04:56.276 killall jackd
11:04:56.297 MIDI connection graph change.
11:04:56.961 MIDI connection change.
11:04:56.972 Post-shutdown script terminated with exit status=256.
11:04:57.713 MIDI connection graph change.

Any light anyone can shed on this would be much appreciated, but I'll accept I may be doing fundamental things the wrong way round, as Linux is all pretty new. 

Cheers
Bob

---

### Post by Tazio on 2007-07-09
Hi all. I have a US-224 and Ubuntu 7.04. I did all the procedure and everything seems ok, but at the end when I
write 
"usx2yloader c -1"
 
I receive this error message :
 
"usx2yloader: cannot open the index file /lib/firmware/usx2yloader/us224.conf"

this is my setup  :
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1604:8005 Tascam US-224 Audio/Midi Controller
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000


0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC650F at 0xa800, irq 17
1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8005 if 0 at 002/004)

Hey.. I'm a newbie.. so.. help me!!!!

:-)

---

### Post by Tazio on 2007-07-10
Hey don't push so hard! :-)
Anyway leds are on now but nothing happens....no sounds... sigh!

---

### Post by Tazio on 2007-10-03
I renounce.

---

### Post by i_am_nitrogen on 2007-10-04
> **Tazio said:**
> "usx2yloader: cannot open the index file /lib/firmware/usx2yloader/us224.conf"

1. Make sure you're running the commands as root.
2. Check the file listed in the error message - is it there?

> Anyway leds are on now but nothing happens....no sounds... sigh!

Make sure you're using the correct hw: device setting in your sound applications.  ALSA will default to using the first sound card detected, and Ubuntu is also set up to prevent a Tascam device from becoming the primary sound card.  Run 'cat /proc/asound/cards' to find the correct number to use after hw:.

With any luck, Gutsy will support the Tascam devices out of the box or with an update.  I've already submitted patches to the ALSA developer list to make this process automatic with udev, but I need to fix them.

---

### Post by Tazio on 2007-10-06
yeah! now i try... thanks!

---

### Post by bsalt on 2007-11-29
Has anybody successfully used the Tascam faders and click wheel to control software mixers in Ardour or other audio applications? I'm interested in how to do this, and if plugins for music recording apps have been written to do this with this line of mixers.

Thanks guys/gals!

---

### Post by bsalt on 2007-11-29
For the file: **usx2y-fw-0.1b.tar.bz2**, visit here to download now:

[http://langerland.de/linux/usx2y/index.html](http://langerland.de/linux/usx2y/index.html)

---

### Post by Tazio on 2007-12-03
Ok! I got it with this command : 

'us428control &' 

which activates the card's knobs, faders and switches. Run it in a console as root (possibly appending the & character to avoid killing it when you close the console):'

and it works!

yeah

[I][I][I]

-----------------------------------------------------------
Hi all. I have a US-224 and Ubuntu 7.04. I did all the procedure and everything seems ok, but at the end when I
write
"usx2yloader c -1"

I receive this error message :

"usx2yloader: cannot open the index file /lib/firmware/usx2yloader/us224.conf"

this is my setup :
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 1604:8005 Tascam US-224 Audio/Midi Controller
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


0 [SI7012 ]: ICH - SiS SI7012
SiS SI7012 with ALC650F at 0xa800, irq 17
1 [USX2Y ]: USB US-X2Y - TASCAM US-X2Y
TASCAM US-X2Y (1604:8005 if 0 at 002/004)

Hey.. I'm a newbie.. so.. help me!!!!


--------------------------------------------------------------
 Re: HOWTO: USB Audio device
Quote:
Originally Posted by Tazio View Post
"usx2yloader: cannot open the index file /lib/firmware/usx2yloader/us224.conf"
1. Make sure you're running the commands as root.
2. Check the file listed in the error message - is it there?

Quote:
Anyway leds are on now but nothing happens....no sounds... sigh!
Make sure you're using the correct hw: device setting in your sound applications. ALSA will default to using the first sound card detected, and Ubuntu is also set up to prevent a Tascam device from becoming the primary sound card. Run 'cat /proc/asound/cards' to find the correct number to use after hw:.

With any luck, Gutsy will support the Tascam devices out of the box or with an update. I've already submitted patches to the ALSA developer list to make this process automatic with udev, but I need to fix them.
__________________[/I][/I][/I]

---

### Post by bsalt on 2007-12-03
Awesome! That is so cool to hear!

---

### Post by shawn_mcmurdo on 2008-01-03
I am trying to get a Tascam US-122 working on Gutsy 7.10 without much success.
After reading various howtos and postings I did the following.

Installed alsa-tools, alsa-utils, and fxload using the Synaptic Package Manager.

I downloaded alsa-firmware-1.0.15.tar.bz2 from ftp.alsa-project.org and extracted it.

I installed libc6-dev using the package manager.

Then I built and installed the alsa-firmware package by doing:
./configure
make
sudo make install

Then I created the file /etc/udev/rules.d/55-tascam.rules
with the following 2 lines:

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/local/share/alsa/firmware/usx2yloader/tascam_ loader.ihx -I /usr/local/share/alsa/firmware/usx2yloader/us122fw .ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

So now when I plug in the us-122 or boot up it is found but there are still problems.

lsusb shows it is on the usb bus and the product id has been changed to 8007 so I know at least the first stage fxload was successful.

lsusb shows:
Bus 001 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface

cat /proc/asound/cards shows:
1 [USX2Y ]: USB US-X2Y - TASCAM US-X2Y
TASCAM US-X2Y (1604:8007 if 0 at 001/006

I set the default sound card by doing:
asoundconf set-default-card USX2Y

amixer info shows:
Card default 'USX2Y'/'TASCAM US-X2Y (1604:8007 if 0 at 001/006)'
Mixer name : ''
Components : ''
Controls : 0
Simple ctrls : 0

aplay startup.wav gives the following error:
aplay: main:545: audio open error: No such file or directory

Anyone have any suggestions on how to proceed from here or what the problem might be?
Thanks!
Shawn

---

### Post by shawn_mcmurdo on 2008-01-08
I was able to get the Tascam US-122 USB soundcard to work on Ununtu 7.10 Gutsy by downloading the version 1.0.15 sources for alsa-lib, alsa-tools, alsa-utils, and alsa-firmware from [ftp://ftp.alsa-project.org/pub/](ftp://ftp.alsa-project.org/pub/) and building them on my system.
I amstill using the Ubuntu supplied 1.0.14 alsa-driver.
Shawn

---

### Post by scizmeli on 2008-05-13
Hi Shawn,

Excellent news. At least someone succeeded in 7.10. 

One hesitation though. If I use the complete ALSA system that I compiled myself, would not this create dependency problems later if I have to install other alsa software with apt-get?

On the other hand, I never did compile such a big piece of code. Sorry for my ignorance but could you please provide me with some guidance on how to do it?

thanks a bunch from advance
Servet

---

### Post by jonobo on 2008-05-13
Mmh. I don't really know if i can add substantial information - but i can at least try and encourage to don't give up.

My US-122 is running fine, right now on Ubuntu 7.04 - i don't know if it works for 7.10, but it should - or not?

To get it running i followed these steps from a "german"!!!-forum, but the steps can be followed easily anyway - okay - i try to translate:
Link to Original-Posting:
[http://forum.ubuntuusers.de/topic/20341/](http://forum.ubuntuusers.de/topic/20341/)
[Scroll down to User "Matze" Date 31.01.2007, 09:31]

1. Download following packages from [http://www.alsa-project.org/](http://www.alsa-project.org/) :
Alsa Tools: [ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.13.tar.bz2)
Alsa Firmware: [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.13.tar.bz2)


```
   tar xjf alsa-firmware-1.0.13.tar.bz2
   tar xjf alsa-tools-1.0.13.tar.bz2
   cd alsa-firmware-1.0.13
   ./configure --prefix=/usr
   cd usx2yloader
   sudo make install


   cd alsa-tools-1.0.13
   cd usx2yloader
   ./configure --prefix=/usr
   make
   sudo make install

   sudo rm -f /etc/hotplug/usb/tascam*
```


2. Install Package 'fxload' with Synaptic.

3.
```
cd /etc/udev/rules.d
sudo touch 55-tascam.rules
sudo gedit 55-tascam.rules
```


Write the following in the just generated and opened file:
```
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
```


4. System --> Preferences --> Sound choose „Tascam USX2Y“ as Soundcard - Ready!

For me that worked fine. If it doesn't help i am sorry for filling the thread with crap - for me it worked fine - ON 7.04 .

---

### Post by eoalvarez on 2009-01-25
Everything was dandy until configure alsa tools
On check for libasound headers version >= 1.00 not present
New version of libasound is not found....

Under synaptic I only have libasound2 available

---

### Post by MundoMuerto on 2009-01-25
Same here, no libasound available. I tried the same steps with the current alsa-tools package (alsa-tools-1.0.19) and received the same results. 
Would it be possible or wise to install libasound in this case or perhaps configure alsa-tools to recognize libasound2?

---

### Post by smaba on 2009-04-14
Hey guys,

I got a weird problem: My Tascam US-122 works ONLY every second time I start up my laptop, which basically means that I have to restart whenever I wanna use my soundcard. Does anyone else have the same problem or a clue what's going wrong here?

greets

smaba

---

### Post by dvwolfman on 2010-05-22
I had trouble with getting the Tascam US-224 to work with Ubuntu, but these directions, when I followed them exactly (except substituting us-224 in place of us-122), got my us-224 working with and without jack:

[URL="https://help.ubuntu.com/community/TASCAM_US-122"]https://help.ubuntu.com/community/TASCAM_US-122
[/URL]
following the post-installation instructions is very important, as the UDEV instructions make it work more plug n' play

it is a legacy piece of hardware, but when my Presonus Firebox broke, I've been forced to use the US-224 again...

performance of the US-224 in Jack with Ardour, etc, has high latency even at it's best setting, so I recommend using the hardware monitoring features of the US224

Good luck to anyone using this hardware, will post any solutions/links with new hardware I get as it comes...:guitar:

---

### Post by dvwolfman on 2010-05-23
> **dvwolfman said:**
> I had trouble with getting the Tascam US-224 to work with Ubuntu, but these directions, when I followed them exactly (except substituting us-224 in place of us-122), got my us-224 working with and without jack:

[URL="https://help.ubuntu.com/community/TASCAM_US-122"]https://help.ubuntu.com/community/TASCAM_US-122
[/URL]
following the post-installation instructions is very important, as the UDEV instructions make it work more plug n' play

it is a legacy piece of hardware, but when my Presonus Firebox broke, I've been forced to use the US-224 again...

performance of the US-224 in Jack with Ardour, etc, has high latency even at it's best setting, so I recommend using the hardware monitoring features of the US224

Good luck to anyone using this hardware, will post any solutions/links with new hardware I get as it comes...:guitar:
I should also add that in the post-installation instructions, if you are using a us-224 the product id is different than the US-122, check it with the following command:

lsusb

this lists the properties of all available usb devices

and note that you will need to change the UDEV rules to match what you see in lsusb, the Tascam us-224 had a product id of 8004 rather than what was listed in the instructions for us-122

am willing to refine instructions and post to a moderator to see if they are clear for a instruction page which explains how to install the US-224 since it gets complicated...
if that is helpful..
thx

---

### Post by terry.weiss on 2010-08-10
Well, it's time to revive this thread :)

I'm running 10.4 LTS. I have a Tascam US-224. I have followed all directions I could find and it works as a sound card and I can record with it. What is weird is that I can't load the hwdep device from JACK. When I do, I get this:

the playback device "hw:1,2" is already in use. Please stop the application using it and run JACK again

AFAIK, nothing else is using it. This is on a fresh reboot. I have it loading firmware on plugin and nrpacks=1 is set in conf.d. When I load us428control, it finds the device:
ubuntu2:~$ us428control &
us428control: US-X2Y-compatible card found on hwdep hw:1

So, it finds it and I assume that means that from fxload to us428control, the intervening steps were successful. In jackctl, it identifies it as a device. But whenever I try to use it, it gives me the message above. I would like to take advantage of this device for the ability use it as a control surface for ardour as well as reduced latency. If I load JACK with dhw:1 (no subdevice) I can use it to record with ardour, but not as a control surface. 

Does anyone have any pointers to suggest that would help me figure out if there is something using the device?

TIA!!!
t.

---

### Post by compuwatch on 2010-08-31
I use the same sound card for recording. Usually it really is easy in UBUNTU to get it working. Download from MEDIBUNTU.org the Alsa-Firmware once you installed it you go Synaptic and type Tascam you will see three items listed. Install them all reboot and you are ready to go.

---

### Post by edjski on 2010-09-19
> **compuwatch said:**
> I use the same sound card for recording. Usually it really is easy in UBUNTU to get it working. Download from MEDIBUNTU.org the Alsa-Firmware once you installed it you go Synaptic and type Tascam you will see three items listed. Install them all reboot and you are ready to go.

Thanks for posting, it seemed to help me -the computer recognizes the us-122 and it lights up now. 
However, I can only get audio out of the us-122 for about a half second, then audio playback stops. If I unplug the us-122, playback resumes (through the computer's built-in soundcard). If I re-connect the us-122, it lights up, outputs audio for about .5sec and then playback stops.

Any thoughts?
Thanks.

---

### Post by deoanam2002 on 2010-10-17
I'm having the exact same problem. The US-122 plays for a second and stops, then sometimes I can go into my sound preferences and switch output back to the internal sound, and then back again to the US-122. It will play for a few more seconds, and then stops. At this point I usually have to restart the computer to get any sound out of the US-122 at all, but even then it's only for a second before it stops.

I tried a couple different firmware versions in the hopes that this would help, but it hasn't. Any insight would be much appreciated.

Edit: I noticed something interesting that may or may not trigger some ideas. I was using the US-122 for sound output and playing a song through Rhythmbox. When the sound cut out, Rhythmbox didn't appear to stop playing, however the song time counter ceased to progress. With my limited knowledge, I guessed that this means there is some kind of software conflict going on with the driver as it interacts with other software... but others would know better than I.

> **edjski said:**
> However, I can only get audio out of the us-122 for about a half second, then audio playback stops. If I unplug the us-122, playback resumes (through the computer's built-in soundcard). If I re-connect the us-122, it lights up, outputs audio for about .5sec and then playback stops.

---

### Post by smaba on 2010-10-20
exactly the same problem here under kubuntu maverick

---

### Post by smaba on 2010-10-22
Hmm...for some reason whenever I have hangups it says: 

```
lsof | grep pcm
pulseaudi 1737     smaba  mem       CHR             116,14            39098 /dev/snd/pcmC1D0p
pulseaudi 1737     smaba  35u      CHR             116,14      0t0   39098 /dev/snd/pcmC1D0p

```

but there is only amarok running.

I had one session where Amarok was running without any hangups and when I typed in ```
lsof | grep pcm
``` it would only show me Amarok!

so...what is that pulseaudi thing doing and how can I stop it?

smaba

---

### Post by klemi on 2010-11-06
Hallo,

I have a new USB-D/A-converter called Cantarta Music Center.

This device dont need a proprietary driver on Windows.

Now I will play audio-files from Computer to Cantarta Music Center via USB plug in under Linux.

I Have done follows:

```
klemens@klemens-laptop:~$ lsusb
Bus 008 Device 002: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 221f:4d48  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1d74:0002  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
klemens@klemens-laptop:~$ ls -l /proc/asound
insgesamt 0
dr-xr-xr-x 5 root root 0 2010-10-17 13:08 card0
dr-xr-xr-x 3 root root 0 2010-10-17 13:08 card1
-r--r--r-- 1 root root 0 2010-10-17 13:08 cards
lrwxrwxrwx 1 root root 5 2010-10-17 13:08 Center -> card1
-r--r--r-- 1 root root 0 2010-10-17 13:08 devices
-r--r--r-- 1 root root 0 2010-10-17 13:08 hwdep
lrwxrwxrwx 1 root root 5 2010-10-17 13:08 Intel -> card0
-r--r--r-- 1 root root 0 2010-10-17 13:08 modules
dr-xr-xr-x 2 root root 0 2010-10-17 13:08 oss
-r--r--r-- 1 root root 0 2010-10-17 13:08 pcm
dr-xr-xr-x 2 root root 0 2010-10-17 13:08 seq
-r--r--r-- 1 root root 0 2010-10-17 13:08 timers
-r--r--r-- 1 root root 0 2010-10-17 13:08 version
```

"ls -l /proc/asound " show "lrwxrwxrwx 1 root root 5 2010-10-17 13:08 Center -> card1"

I think the Converter were identify as a graphic-card.

Someone friendly user said me I must create a file called asound.conf, put it in the /etc directory 
with:
```
pcm.Center {
    type plug
    slave.pcm "card1"
}
ctl.Center {
    type hw
    card 1
}
pcm.card1 {
    type hw
    card 1
}
```

and reboot

If I use then a simple music programme under Linux like "DeaDBeeF", I can see under "settings - output device" the following:

[http://picpaste.de/5-11-10-Cantata_music-center-JlhSdvTc.png]("http://picpaste.de/5-11-10-Cantata_music-center-JlhSdvTc.png")

I have select any items with Cantarta, but the player don't play some flac-files (no "play signs" appears i n the player. --> Nothing happens.

What can I do?

I think ist must go!

Can someone help me?

Thanks

klemi

---

### Post by bsalt on 2011-07-02
Has anyone had success with getting sound to correctly play out the Tascam US-X2Y device, and if so, can you please post what you had done to make this possible? 

I'm hitting my head against a wall here - and I really want to be off of using Windows 7 for music performance/production.

 I am also MS certified for enterprise desktop support in Windows 7, but the fact is that Linux / Mac OS is much faster at their core. Mac OS did not recognize my video and wifi card, and after trying to install various drivers (30+) times to get my hardware working, I gave up and went with Ubuntu. I'd like this to be a testimony of how good Ubuntu is at various tasks like music production / performance, but I'm stuck with not getting any audio out my Tascam. The lights light up, the rules file correctly works when I plug the Tascam in on the fly, but no sound. If needed, I'll buy some better "Linux compatible" audio / midi hardware to use instead, but I'd like to first see that this works and that I can move off Windows 7 entirely. For now, it is my backup to get life working.



Ok, I'm off my soap box now.

---

### Post by jonobo on 2011-07-04
Just follow these steps - that helped to get my US-122 running on 10.04:
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

This thread might also help:
[http://ubuntuforums.org/showthread.php?t=1497526](http://ubuntuforums.org/showthread.php?t=1497526)

Greets,

;j

---

### Post by tupfzom on 2011-08-16
I just realized that at least since 11.04 all I need to get the Tascam US-122 running is the Universe, Multiverse and Medibuntu repoositories.  The only package I had to install is alsa-firmware, then plugging in the soundcard gives a green LED and I instantly can select it to play back and record.  I just tried it from the live CD to verify that it doesn't depend on something else that I might have installed on my real hard disk installation.

Can anyone replicate this?  If so, the [US-122 community documentation page]("http://help.ubuntu.com/community/TASCAM_US-122/") really needs some updating.  I'm not keen on cleaning up the page (it has a "Style Cleanup Required" sticker), but simply adding a few lines would at least help some people avoiding the trouble.

---

### Post by deoanam2002 on 2011-08-16
Attempt to replicate:
Using 11.04 32bit live CD.
Tascam US-122

Installed Universe, Multiverse, Medibuntu repositories.
Installed alsa-firmware
Installed gnome-alsamixer

Plugged US-122 in via USB.
Green USB light comes on the unit.
In Sound Preferences, US-122 appears in Hardware tab, but not in Input or Output tabs.
US-122 does NOT appear in Gnome Alsa Mixer.
I CAN play an audio file through the US-122 using aplay -D plughw:2,0 /home/ubuntu/Desktop/song.wav
HOWEVER, the song cuts out at arbitrary points and will not play the whole song. This is exactly the same thing that happened when I got the US-122 "working" through Ubuntu 10.4.
So it appears that there is little progress here. I understand that there may be different versions of the US-122. I believe I have the first-gen version, as the model number is simply "US-122"

Thanks for the attempt! I wonder if anyone else will have more luck.

> **tupfzom said:**
> I just realized that at least since 11.04 all I need to get the Tascam US-122 running is the Universe, Multiverse and Medibuntu repoositories.  The only package I had to install is alsa-firmware, then plugging in the soundcard gives a green LED and I instantly can select it to play back and record.  I just tried it from the live CD to verify that it doesn't depend on something else that I might have installed on my real hard disk installation.

Can anyone replicate this?  If so, the [US-122 community documentation page]("http://help.ubuntu.com/community/TASCAM_US-122/") really needs some updating.  I'm not keen on cleaning up the page (it has a "Style Cleanup Required" sticker), but simply adding a few lines would at least help some people avoiding the trouble.

---

### Post by tupfzom on 2011-08-16
> **deoanam2002 said:**
> Attempt to replicate:
HOWEVER, the song cuts out at arbitrary points and will not play the whole song.

That's not a problem for me.  I had music playing quite a while and everything was stable.  I also recorded some shorter bits to control myself while practicing, no problems there.  However, from the live CD I only had a very quick check.  Maybe I should try on another computer as well.
> 
I understand that there may be different versions of the US-122. I believe I have the first-gen version, as the model number is simply "US-122"


That's the one I have, too. It says Model No. US-122 on the back, the UPC is 4907034108565 (left barcode).  But who knows whether some changes were made during production?

---

### Post by tupfzom on 2011-08-17
I didn't try the whole thing on another machine yet, but there is one inconvenience I experience.  For some reason the US-122 isn't activated on startup (you obviously can't try this from the live CD).  I have to unplug and replug it, then everything is fine.  Any ideas why this is so?

---

### Post by tupfzom on 2011-08-18
O.K., so I tried the live CD on my laptop, and I get green lights after
```
sudo usx2yloader
```
but the US-122 doesn't appear in the sound settings.  After logging off with
```
gnome-session-save --kill
```
and logging on again with user name "ubuntu" and empty password, it is listed in the hardware tab, but not in the input and output tabs.

---

### Post by deoanam2002 on 2011-12-20
I gave up on this for quite awhile. I just installed Ubuntu Studio 10.10, and so I thought I'd give it another try. I'm running into the exact same problem I outlined before (sound cutting out).
I was able to make the US-122 appear in my input/output selection (and got it to work there) after creating the /etc/asound.conf file to read the following:

```
pcm.us122 {
    type hw;
    card USX2Y;
}                                                                                                  
pcm.usx {
    type plug;
    slave.pcm us122;
}
```

**Edit: It appears that the us-122 only appears in input/output after I select us122 as the sound output in Audacity and play a file in audacity.**

As for the sound cutting out, it could possibly be one of the following:
1. I believe I updated the on-device firmware (possibly 1.11?) ---however, IIRC, I was having the problem before that, and updated the firmware as an attempted solution.
2. According to the following us-122 manual, certain OHCI USB ports will have problems with the device. I have no idea if this applies to my system or not: [http://tascam.com/content/downloads/products/311/US122_Eng.pdf](http://tascam.com/content/downloads/products/311/US122_Eng.pdf)

> **tupfzom said:**
> O.K., so I tried the live CD on my laptop, and I get green lights after
```
sudo usx2yloader
```
but the US-122 doesn't appear in the sound settings.  After logging off with
```
gnome-session-save --kill
```
and logging on again with user name "ubuntu" and empty password, it is listed in the hardware tab, but not in the input and output tabs.

---

### Post by tupfzom on 2012-03-17
I did another try on another computer with Oneiric: I installed alsa-firmware and the US-122 is displayed in the audio settings.  Unfortunately, I can't select it for output. In Audacity I can, but when I hit play, it gives an error.

Recording in audacity only works for half a second, then the recording hangs.

So, not exactly a lot of good news from my side.

---

### Post by deoanam2002 on 2012-03-19
Sorry, I forgot to update here.
As I posted on this thread [http://ubuntuforums.org/showthread.php?t=1697077](http://ubuntuforums.org/showthread.php?t=1697077) (post #5), the instructions here worked for me. They're a bit different from what you find in the wiki.
[http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick](http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick)

Hope this helps.

> **tupfzom said:**
> I did another try on another computer with Oneiric: I installed alsa-firmware and the US-122 is displayed in the audio settings.  Unfortunately, I can't select it for output. In Audacity I can, but when I hit play, it gives an error.

Recording in audacity only works for half a second, then the recording hangs.

So, not exactly a lot of good news from my side.

---

### Post by tupfzom on 2012-03-19
Thanks, deoanam, but unfortunately, this didn't change anything for me on Oneiric.  You're using Maverick, right?  Maybe I should try a Maverick live CD to see whether it might be the machine's fault or the OS's.

Edit: BTW, I did
```
sudo fxload -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/001/010

```

i.e. /lib/firmware/usx2yloader/tascam_loader.ihx instead of /proc/18234/cwd/tascam_loader.ihx as the latter didn't exist.

---

### Post by deoanam2002 on 2012-03-19
Sorry to hear that didn't work. Please update us if you try it with Maverick.

> **tupfzom said:**
> Thanks, deoanam, but unfortunately, this didn't change anything for me on Oneiric.  You're using Maverick, right?  Maybe I should try a Maverick live CD to see whether it might be the machine's fault or the OS's.

Edit: BTW, I did
```
sudo fxload -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/001/010

```

i.e. /lib/firmware/usx2yloader/tascam_loader.ihx instead of /proc/18234/cwd/tascam_loader.ihx as the latter didn't exist.

---

### Post by tupfzom on 2012-03-29
> **deoanam2002 said:**
> Sorry to hear that didn't work. Please update us if you try it with Maverick.

Good news: I got it to work, both with [S]Maverick[/S] Natty and Oneiric.

Explanation:  I'm running a Thinkpad on a docking station and had the US-122 plugged into the docking station.  It turns out I have to plug it into the notebook itself.  (Unless I'm satisfied with recording snippets of half a second, of course.)

So, the bad news is that for some reason it doesn't work on all USB ports with Ubuntu.  On Windows, it *does* work with the docking station's USB ports.

---

