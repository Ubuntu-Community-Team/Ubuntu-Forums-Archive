---
title: "Kernel Panic: init error parsing config, denied, kill init"
date: 2008-04-10
forum: Server Platforms
---

### Post by archgriffin on 2008-04-10
I've seen a few posts in regards to the  same kernel panic:

```
Kernel panic - not syncing: Attempted to kill init!
```

However I can not seem to find anyone with the same text above as mine which is as follows:


```

Starting up ...
Loading, please wait...
[     22.232392] sda: assuming drive cache: write through
[     22.232679] sda: assuming drive cache: write through
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...
init: Error parsing configuration: Permission denied
[     22.390365] Kernel panic - not syncing: Attempted to kill init!
[     22.390516]  

```

This is a Ubuntu Server 7.04 running on a VMware ESX Server. Runs basically as a LAMP install, I didn't set it up, it is something I inherited as I replaced it's implementer, and barely touched in the background, short of apt-get update/upgrades to keep it up to date.

For about the last month, it would randomly have the /var change to read-only. Rebooting would fix it, and it would go on working just fine again for a while (1-6 days). Yesterday I finally had a moment to sit with it. Due to it being /var that switched to read-only, the error logs would stop when the error occurred. I only noticed the error because the MySQL server would die, and the website it hosts would throw errors.Therefore I made a change in /etc/syslog.conf, of which I can't entirely remember but I think I changed /var/log/syslog to /root/logs/syslog.

I've still got some things I am trying, but I am getting a bit frustrated with it at this point. I also do not have full access to the ESX Server, I'm just able to reboot it, my next step was using a live CD to change the one thing I did back.

I have tried using the other listed kernel in GRUB, same problem, same thing for both recovery modes. Kernels are:
2.6.20-16-server
2.6.20-15-server

If there is anything or any similar experiences out there that i have skipped in my searching I'd be happy to hear any thoughts or suggestions.

Certainly if you need any more details from me to help, just ask and I'll see what I can provide.

---

### Post by archgriffin on 2008-04-10
Still working on this, just painfully slow however I have been given a screen shot of from a tech that noticed something wrong with it earlier. They didn't do anything to it, but just now thought it would be useful for me :confused:

```

Buffer I/O error on device sda1, logical block 8785920
Aborting journal on device sda1.
ext3_abort called.
EXT3-fs error (device sda1): ext_journal_start_sb: Detected aborted journal
Remounting filesystem read-only

```

at least now I have another thing to fork ideas from. Could the basis of this entire issue be a journal problem?

---

### Post by warp99 on 2008-04-10
> **archgriffin said:**
> 
at least now I have another thing to fork ideas from. Could the basis of this entire issue be a journal problem?

> init: Error parsing configuration: Permission denied
and
> Remounting filesystem read-only
I believe you just answered your own question.

---

### Post by archgriffin on 2008-04-10
Well thank you for responding, though now I'm just not sure what to do.

I'm not the best at this stuff, and I've been stuck in the windows shop for so long at this point every time I get somewhere where I think I would obviously know the answer, my brain seems to die.

---

### Post by Koybe on 2008-04-10
I think you should boot into some rescue CD and make a fscheck on this sda1 partition. It looks like you have bad sectors. But I don't know much how it would show in ESX Server.

You can use *e2fsck* and *badblocks* to try finding out what's happening.

---

### Post by archgriffin on 2008-04-10
currently home, but this will be the first thing I do in the morning and I'll be reporting what I find.

---

### Post by archgriffin on 2008-04-11
Well I got it booted to Live CD, ran the fsck and badblock. fsck ran through a lot of things it fixed.

Now the error is the same except the init line is

```
init: Error parsing configuration: No such file or directory
```

Of which I have seen more of those errors around so I have to skim my bookmarks and see if I can clear that error up.

Thank you, and any other suggestions are welcomed.

Supposed I should have mentioned that it didn't matter which of the kernels I used, and the same error comes for recovery mode.

---

### Post by archgriffin on 2008-04-11
Alright, so I've booted back up in a live CD, and ran the following:

```

sudo tune2fs /dev/sda1 -O has_journal
  tune2fs 1.40.2
sudo fsck /dev/sda1
  fsck 1.40.2
  e2fsck 1.40.2
  /dev/sda1: clean, 103897/5062656 files, 2646810/10108893 blocks

```

However I'm getting the same error as I mentioned last post. Some of the articles I have seen on the init: Error parsing configuration: No such file or directory, point to /etc being on a separate partition, and most of those were after installs, where as this machine has been working for quite a while, and only recently decided to be a pain.

What would be a good next pointer?

---

### Post by Koybe on 2008-04-11
Well, fsck made it clean. 
What if you boot on this live cd and mount manually your partition? Can you read them?
The I would try chrooting into your root partition and see what I get.

```
mount /dev/sda1 /mnt/recover
ls /mnt/recover
chroot /mnt/recover
```

I don't really know what you will find but hopefully some useful informations.

---

### Post by archgriffin on 2008-04-11
I can mount and read the data from sda1 without any problems,
give me a few more minutes here I should be able to paste in some log files...
The ones I would know to grab are /var/log/messages syslog 
Anything else that would be more helpful to someone with more experince then myself?

---

### Post by Koybe on 2008-04-11
/var/log/dmesg maybe. Anyway I'm not really experienced in kernel panic ;) Just making supposition, trying to help..

---

### Post by archgriffin on 2008-04-14
Sorry this took so long to get back, but here are the logs.

The only change I have made in them is taking out the actual server name and replacing it with Linux Server Name, hopefully I've got them all.

I wasn't sure which would be best to post them as text in the form or not, so for now I have just attached them as .gz files, since as txt files they were just too big for the forum to take them.

If it would be more help to have them directly in a post I'll do that too.

---

### Post by archgriffin on 2008-04-14
Forgot to mention, the syslog file only goes to Apr 3. This is the newest of the syslog files, and there was no syslog, only syslog.[1-4].gz, so I took the newest of them.

It never did write a syslog to the place I changed in the syslog.conf file.

---

### Post by archgriffin on 2008-04-14
I now think I am wrong about the /etc partition.

After looking around more (and paying more attention) there is no etc in the sda1. There is an sda2, however it does not look very happy.

I could not mount /dev/sda2, so my next guess would be fsck which results in:

```

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

```

to which I have been researching this and tried the following with no changes:
```

e2fsck -f -v -c

tune2fs -O ^has_journal /dev/sda2

tune2fs -j /dev/sda2
```

they tend to give the above error or complain they can't find a valid superblock.

I've read there is a last ditch effort of:

```
mke2fs -S
```

But it sounds like I would like to avoid that option.

As I continue to look around any one have any other helpful ideas or hints?

Thanks much.

---

### Post by archgriffin on 2008-04-14
Possibly wrong about that too? 

an fdisk -l gives me the following

```

     Device Boot         Start          End        Blocks           Id       System
/dev/sda1   *                  1        5034     40435573+    83       Linux
/dev/sda2                 5035        5221       1502077+      5       Extended
/dev/sda5                 5035        5221       1502046       82       Linux Swap / Solaris

```

To me, that just says it's extended, for swap. 

So, did the system lose it's entire /etc folder?  Any options someone else can find or think I have here?

---

### Post by archgriffin on 2008-04-15
HA!

I found something, there is a backup of the entire /etc folder, tar.gz'd so through the live CD I brought that over, and uncompressed it. The system boots again!

Somewhat...
If you try to login you get

```
Module is unknown
```

Then kicks you back to a login screen.

It also does not appear to be starting up cleanly. By that I mean normally you see it starting "services...ok" no this is just scrolling text all over the place.

I believe I saw something about /dev/shm/var.run not existing go by, along with something about libctutils.so.0 both saying they don't exisit.

Options? Am I actually making progress or just shooting myself in the foot more?

---

### Post by archgriffin on 2008-04-16
Probably a bad idea, but, is it possible to use apt-get or aptitude to reinstall part of the base OS? 

Apache works, MySQL, partly loads now (complains about broken tables), it just seems to me that part of the OS is missing, like the fsck got rid of things the OS needed. 

I'm asking because normally before I go mucking around and cause a big havoc, someone can normal hand out a one liner or something that is a lot easier to handle.

Or, if there are any other options someone can think of.

The system still gives the same error when you attempt to login, however you can login as root through the recovery mode, so I believe I am closer, to having the system working again.

---

### Post by archgriffin on 2008-04-16
More updates.

I've now copied some of the lib files over from the live CD, this seems to have stopped it from barking about them. (libctutils.so.0, libconsole.so.0, libcap.so.1)

However, mysql is still not fully functioning, and I still can not login normally. Login as root in recovery mode is ok, but the normal login presists with "Module is unknown".

I have no idea what it is talking about, maybe a PAM thing? I have no experince with that. If you SSH to the server you are asked for username/password after you enter password you are just denied, and asked for the password again.

I've also found that the following appear to be missing: 

pam_env.so, pam_group.so, pam_limits.so, pam_lastlog.so, pam_mail.so

From /lib/security

I attempted to copy those from the live cd, and that did not go over very well. It would boot, but when you typed in a username it skipped down 5 lines and said you maxed out the limit of attempts, even though you never even got to type a password. Taking them back out, puts me right back to the Module not found issue. 

There is a complaint about /dev/shm/var.run not being able to be created, well there is no /dev/shm, in recovery mode if i make it, it doesn't seem to stick?

I'm starting to run out of things to try, even just poking around blindly :(

Also here are updated logs:

dmesg
```

[    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
[    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 512MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6cd0
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125984 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
[    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
[    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 3390.981 MHz processor.
[85369.033062] Built 1 zonelists.  Total pages: 130048
[85369.033248] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro single
[85369.034103] mapped APIC to ffffd000 (fee00000)
[85369.034167] mapped IOAPIC to ffffc000 (fec00000)
[85369.034567] Enabling fast FPU save and restore... done.
[85369.034632] Enabling unmasked SIMD FPU exception support... done.
[85369.034941] Initializing CPU#0
[85369.036447] PID hash table entries: 2048 (order: 11, 8192 bytes)
[85369.046643] Console: colour VGA+ 80x25
[85369.046799] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[85369.046955] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[85369.047111] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
[85369.047266] virtual kernel memory layout:
[85369.047272]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
[85369.047274]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[85369.047275]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
[85369.047277]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
[85369.047278]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
[85369.047280]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
[85369.047282]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
[85369.047437] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[85369.195950] Calibrating delay using timer specific routine.. 6808.78 BogoMIPS (lpj=34043937)
[85369.196105] Security Framework v1.0.0 initialized
[85369.196261] SELinux:  Disabled at boot.
[85369.196417] Mount-cache hash table entries: 512
[85369.196573] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
[85369.196728] CPU: Trace cache: 12K uops, L1 D cache: 16K
[85369.196884] CPU: L2 cache: 1024K
[85369.196998] CPU: L3 cache: 16384K
[85369.197154] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
[85369.197310] Compat vDSO mapped to ffffe000.
[85369.197447] Remapping vsyscall page to ffffe000
[85369.197603] Checking 'hlt' instruction... OK.
[85369.235924] SMP alternatives: switching to UP code
[85369.236080] Freeing SMP alternatives: 11k freed
[85369.236236] Early unpacking initramfs... done
[85369.425330] ACPI: Core revision 20060707
[85369.425486] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[85369.426109] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
[85369.426265] Total of 1 processors activated (6808.78 BogoMIPS).
[85369.426421] ENABLING IO-APIC IRQs
[85369.426832] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[85369.644490] Brought up 1 CPUs
[85369.644490] Booting paravirtualized kernel on bare hardware
[85369.644490] Time: 14:50:54  Date: 03/16/108
[85369.644490] NET: Registered protocol family 16
[85369.644490] EISA bus registered
[85369.644490] ACPI: bus type pci registered
[85369.644490] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
[85369.644490] PCI: Using configuration type 1
[85369.644490] Setting up standard PCI resources
[85369.654459] ACPI: Interpreter enabled
[85369.654459] ACPI: Using IOAPIC for interrupt routing
[85369.654459] ACPI: PCI Root Bridge [PCI0] (0000:00)
[85369.654459] PCI: Probing PCI hardware (bus 00)
[85369.654459] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[85369.654459] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[85369.654459] Boot video device is 0000:00:0f.0
[85369.654459] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[85369.654459] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[85369.654459] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[85369.654459] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[85369.654658] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[85369.658929] Linux Plug and Play Support v0.97 (c) Adam Belay
[85369.659084] pnp: PnP ACPI init
[85369.670509] pnp: PnP ACPI: found 12 devices
[85369.670665] PnPBIOS: Disabled by ACPI PNP
[85369.670977] PCI: Using ACPI for IRQ routing
[85369.671133] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[85369.684367] NET: Registered protocol family 8
[85369.684367] NET: Registered protocol family 20
[85369.684367] NetLabel: Initializing
[85369.684367] NetLabel:  domain hash size = 128
[85369.684367] NetLabel:  protocols = UNLABELED CIPSOv4
[85369.684367] NetLabel:  unlabeled traffic allowed by default
[85369.684367] PCI: Bridge: 0000:00:01.0
[85369.684367]   IO window: disabled.
[85369.684367]   MEM window: disabled.
[85369.684367]   PREFETCH window: disabled.
[85369.684367] PCI: Setting latency timer of device 0000:00:01.0 to 64
[85369.684367] NET: Registered protocol family 2
[85369.784290] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[85369.784446] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[85369.784601] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
[85369.784757] TCP: Hash tables configured (established 65536 bind 32768)
[85369.784913] TCP reno registered
[85369.814151] checking if image is initramfs... it is
[85370.222866] Freeing initrd memory: 6642k freed
[85370.223586] Simple Boot Flag at 0x36 set to 0x1
[85370.225257] audit: initializing netlink socket (disabled)
[85370.225413] audit(1208357455.050:1): initialized
[85370.226436] VFS: Disk quotas dquot_6.5.1
[85370.226592] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[85370.226748] io scheduler noop registered
[85370.226904] io scheduler anticipatory registered
[85370.227016] io scheduler deadline registered (default)
[85370.227172] io scheduler cfq registered
[85370.227328] Limiting direct PCI/PCI transfers.
[85370.228021] isapnp: Scanning for PnP cards...
[85370.585757] isapnp: No Plug & Play device found
[85370.624776] Real Time Clock Driver v1.12ac
[85370.625072] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[85370.631451] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[85370.631451] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[85370.631451] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[85370.631451] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[85370.631451] mice: PS/2 mouse device common for all mice
[85370.631451] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[85370.631451] input: Macintosh mouse button emulation as /class/input/input0
[85370.631451] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[85370.631451] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[85370.631451] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[85371.140655] serio: i8042 KBD port at 0x60,0x64 irq 1
[85371.140841] serio: i8042 AUX port at 0x60,0x64 irq 12
[85371.142886] EISA: Probing bus 0 at eisa.0
[85371.143198] Cannot allocate resource for EISA slot 1
[85371.143353] EISA: Detected 0 cards.
[85371.173669] TCP cubic registered
[85371.173796] NET: Registered protocol family 1
[85371.173952] Using IPI No-Shortcut mode
[85371.174596] ACPI: (supports S0 S1 S4 S5)
[85371.174752]   Magic number: 4:461:839
[85371.174908]   hash matches device ptyu5
[85371.179763] Freeing unused kernel memory: 332k freed
[85371.179763] input: AT Translated Set 2 keyboard as /class/input/input1
[85371.179874] Time: tsc clocksource has been installed.
[85371.351042] Capability LSM initialized
[85371.381790] ACPI: Processor [CPU0] (supports 8 throttling states)
[85371.381946] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[85371.382101] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[85371.382257] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[85371.990118] PIIX4: IDE controller at PCI slot 0000:00:07.1
[85371.990274] PIIX4: chipset revision 1
[85371.990425] PIIX4: not 100% native mode: will probe irqs later
[85371.990581]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
[85371.990737] Probing IDE interface ide0...
[85372.010186] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
[85372.038018] SCSI subsystem initialized
[85372.038552] Fusion MPT base driver 3.04.03
[85372.038708] Copyright (c) 1999-2007 LSI Logic Corporation
[85372.039234] Fusion MPT SPI Host driver 3.04.03
[85372.069120] Floppy drive(s): fd0 is 1.44M
[85372.097894] FDC 0 is a post-1991 82077
[85372.884678] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
[85373.263864] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[85373.265834] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
[85373.265989] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
[85373.266301] eth0: registered as PCnet/PCI II 79C970A
[85373.266457] pcnet32: 1 cards_found.
[85373.266934] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
[85373.267090] mptbase: Initiating ioc0 bringup
[85373.522715] ioc0: 53C1030: Capabilities={Initiator}
[85373.981524] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
[85374.369941] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
[85374.369941]  target0:0:0: Beginning Domain Validation
[85374.369941]  target0:0:0: Domain Validation skipping write tests
[85374.369941]  target0:0:0: Ending Domain Validation
[85374.369941]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[85374.384330] libata version 2.20 loaded.
[85374.405281] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
[85374.405437] sda: test WP failed, assume Write Enabled
[85374.405592] sda: cache data unavailable
[85374.405709] sda: assuming drive cache: write through
[85374.405865] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
[85374.406020] sda: test WP failed, assume Write Enabled
[85374.406142] sda: cache data unavailable
[85374.406227] sda: assuming drive cache: write through
[85374.406383]  sda: sda1 sda2 < sda5 >
[85374.411917] sd 0:0:0:0: Attached scsi disk sda
[85374.416399] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
[85374.416555] Uniform CD-ROM driver Revision: 3.20
[85374.443106] sd 0:0:0:0: Attached scsi generic sg0 type 0
[85374.599404] Attempting manual resume
[85374.599528] swsusp: Resume From Partition 8:5
[85374.599554] PM: Checking swsusp image.
[85374.600217] PM: Resume from disk failed.
[85374.616859] kjournald starting.  Commit interval 5 seconds
[85374.617171] EXT3-fs: mounted filesystem with ordered data mode.
[85374.902409] parport: PnPBIOS parport detected.
[85374.902565] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[85374.998466] lp0: using parport0 (interrupt-driven).
[85375.019838] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
[85375.038995] EXT3 FS on sda1, internal journal
[85375.098067] eth0: link up
[85376.314369] NET: Registered protocol family 10
[85376.314525] lo: Disabled Privacy Extensions

```

syslog
```

Apr 16 00:09:01 LinuxServerName CRON[3033]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 00:09:01 LinuxServerName CRON[3033]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 00:09:01 LinuxServerName CRON[3033]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 00:09:01 LinuxServerName CRON[3033]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 00:09:01 LinuxServerName CRON[3033]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 00:09:01 LinuxServerName CRON[3033]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 00:09:01 LinuxServerName CRON[3033]: Module is unknown
Apr 16 00:17:01 LinuxServerName CRON[3035]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 00:17:01 LinuxServerName CRON[3035]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 00:17:01 LinuxServerName CRON[3035]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 00:17:01 LinuxServerName CRON[3035]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 00:17:01 LinuxServerName CRON[3035]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 00:17:01 LinuxServerName CRON[3035]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 00:17:01 LinuxServerName CRON[3035]: Module is unknown
Apr 16 00:29:50 LinuxServerName -- MARK --
Apr 16 00:39:01 LinuxServerName CRON[3039]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 00:39:01 LinuxServerName CRON[3039]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 00:39:01 LinuxServerName CRON[3039]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 00:39:01 LinuxServerName CRON[3039]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 00:39:01 LinuxServerName CRON[3039]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 00:39:01 LinuxServerName CRON[3039]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 00:39:01 LinuxServerName CRON[3039]: Module is unknown
Apr 16 00:49:50 LinuxServerName -- MARK --
Apr 16 01:09:01 LinuxServerName CRON[3051]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 01:09:01 LinuxServerName CRON[3051]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 01:09:01 LinuxServerName CRON[3051]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 01:09:01 LinuxServerName CRON[3051]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 01:09:01 LinuxServerName CRON[3051]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 01:09:01 LinuxServerName CRON[3051]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 01:09:01 LinuxServerName CRON[3051]: Module is unknown
Apr 16 01:17:01 LinuxServerName CRON[3056]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 01:17:01 LinuxServerName CRON[3056]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 01:17:01 LinuxServerName CRON[3056]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 01:17:01 LinuxServerName CRON[3056]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 01:17:01 LinuxServerName CRON[3056]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 01:17:01 LinuxServerName CRON[3056]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 01:17:01 LinuxServerName CRON[3056]: Module is unknown
Apr 16 01:29:51 LinuxServerName -- MARK --
Apr 16 01:39:01 LinuxServerName CRON[3060]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 01:39:01 LinuxServerName CRON[3060]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 01:39:01 LinuxServerName CRON[3060]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 01:39:01 LinuxServerName CRON[3060]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 01:39:01 LinuxServerName CRON[3060]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 01:39:01 LinuxServerName CRON[3060]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 01:39:01 LinuxServerName CRON[3060]: Module is unknown
Apr 16 01:49:52 LinuxServerName -- MARK --
Apr 16 02:09:01 LinuxServerName CRON[3064]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 02:09:01 LinuxServerName CRON[3064]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 02:09:01 LinuxServerName CRON[3064]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 02:09:01 LinuxServerName CRON[3064]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 02:09:01 LinuxServerName CRON[3064]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 02:09:01 LinuxServerName CRON[3064]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 02:09:01 LinuxServerName CRON[3064]: Module is unknown
Apr 16 02:17:01 LinuxServerName CRON[3067]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 02:17:01 LinuxServerName CRON[3067]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 02:17:01 LinuxServerName CRON[3067]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 02:17:01 LinuxServerName CRON[3067]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 02:17:01 LinuxServerName CRON[3067]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 02:17:01 LinuxServerName CRON[3067]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 02:17:01 LinuxServerName CRON[3067]: Module is unknown
Apr 16 02:29:53 LinuxServerName -- MARK --
Apr 16 02:39:01 LinuxServerName CRON[3072]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 02:39:01 LinuxServerName CRON[3072]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 02:39:01 LinuxServerName CRON[3072]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 02:39:01 LinuxServerName CRON[3072]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 02:39:01 LinuxServerName CRON[3072]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 02:39:01 LinuxServerName CRON[3072]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 02:39:01 LinuxServerName CRON[3072]: Module is unknown
Apr 16 02:49:54 LinuxServerName -- MARK --
Apr 16 03:00:01 LinuxServerName CRON[3077]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 03:00:01 LinuxServerName CRON[3077]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 03:00:01 LinuxServerName CRON[3077]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 03:00:01 LinuxServerName CRON[3077]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 03:00:01 LinuxServerName CRON[3077]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 03:00:01 LinuxServerName CRON[3077]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 03:00:01 LinuxServerName CRON[3077]: Module is unknown
Apr 16 07:26:29 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 07:26:29 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 07:26:29 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 07:26:29 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 07:26:29 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Detected 3394.991 MHz processor.
Apr 16 07:26:29 LinuxServerName kernel: [73137.259350] Built 1 zonelists.  Total pages: 130048
Apr 16 07:26:29 LinuxServerName kernel: [73137.259529] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 07:26:29 LinuxServerName kernel: [73137.260384] mapped APIC to ffffd000 (fee00000)
Apr 16 07:26:29 LinuxServerName kernel: [73137.260447] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 07:26:29 LinuxServerName kernel: [73137.260826] Enabling fast FPU save and restore... done.
Apr 16 07:26:29 LinuxServerName kernel: [73137.260891] Enabling unmasked SIMD FPU exception support... done.
Apr 16 07:26:29 LinuxServerName kernel: [73137.261180] Initializing CPU#0
Apr 16 07:26:29 LinuxServerName kernel: [73137.262657] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73137.262813] Console: colour VGA+ 80x25
Apr 16 07:26:29 LinuxServerName kernel: [73137.262969] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263125] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263280] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263336] virtual kernel memory layout:
Apr 16 07:26:29 LinuxServerName kernel: [73137.263340]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263342]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263344]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263346]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263347]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263349]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263350]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263404] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 07:26:29 LinuxServerName kernel: [73137.412175] Calibrating delay using timer specific routine.. 6795.64 BogoMIPS (lpj=33978217)
Apr 16 07:26:29 LinuxServerName kernel: [73137.412331] Security Framework v1.0.0 initialized
Apr 16 07:26:29 LinuxServerName kernel: [73137.412487] SELinux:  Disabled at boot.
Apr 16 07:26:29 LinuxServerName kernel: [73137.412642] Mount-cache hash table entries: 512
Apr 16 07:26:29 LinuxServerName kernel: [73137.412798] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 07:26:29 LinuxServerName kernel: [73137.412954] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 07:26:29 LinuxServerName kernel: [73137.413002] CPU: L2 cache: 1024K
Apr 16 07:26:29 LinuxServerName kernel: [73137.413024] CPU: L3 cache: 16384K
Apr 16 07:26:29 LinuxServerName kernel: [73137.413179] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 07:26:29 LinuxServerName kernel: [73137.413335] Compat vDSO mapped to ffffe000.
Apr 16 07:26:29 LinuxServerName kernel: [73137.413391] Remapping vsyscall page to ffffe000
Apr 16 07:26:29 LinuxServerName kernel: [73137.413547] Checking 'hlt' instruction... OK.
Apr 16 07:26:29 LinuxServerName kernel: [73137.452159] SMP alternatives: switching to UP code
Apr 16 07:26:29 LinuxServerName kernel: [73137.452315] Freeing SMP alternatives: 11k freed
Apr 16 07:26:29 LinuxServerName kernel: [73137.452470] Early unpacking initramfs... done
Apr 16 07:26:29 LinuxServerName kernel: [73137.641573] ACPI: Core revision 20060707
Apr 16 07:26:29 LinuxServerName kernel: [73137.641728] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 07:26:29 LinuxServerName kernel: [73137.642351] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 07:26:29 LinuxServerName kernel: [73137.642507] Total of 1 processors activated (6795.64 BogoMIPS).
Apr 16 07:26:29 LinuxServerName kernel: [73137.642663] ENABLING IO-APIC IRQs
Apr 16 07:26:29 LinuxServerName kernel: [73137.643075] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Brought up 1 CPUs
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Booting paravirtualized kernel on bare hardware
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Time: 11:26:23  Date: 03/16/108
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] NET: Registered protocol family 16
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] EISA bus registered
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] ACPI: bus type pci registered
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] PCI: Using configuration type 1
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Setting up standard PCI resources
Apr 16 07:26:29 LinuxServerName kernel: [73137.860887] ACPI: Interpreter enabled
Apr 16 07:26:29 LinuxServerName kernel: [73137.860926] ACPI: Using IOAPIC for interrupt routing
Apr 16 07:26:29 LinuxServerName kernel: [73137.862509] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 07:26:29 LinuxServerName kernel: [73137.862655] PCI: Probing PCI hardware (bus 00)
Apr 16 07:26:29 LinuxServerName kernel: [73137.863257] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 07:26:29 LinuxServerName kernel: [73137.863338] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 07:26:29 LinuxServerName kernel: [73137.863494] Boot video device is 0000:00:0f.0
Apr 16 07:26:29 LinuxServerName kernel: [73137.863887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 07:26:29 LinuxServerName kernel: [73137.866514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.866829] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 07:26:29 LinuxServerName kernel: [73137.867149] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 07:26:29 LinuxServerName kernel: [73137.867458] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.874793] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 07:26:29 LinuxServerName kernel: [73137.874868] pnp: PnP ACPI init
Apr 16 07:26:29 LinuxServerName kernel: [73137.885114] pnp: PnP ACPI: found 12 devices
Apr 16 07:26:29 LinuxServerName kernel: [73137.885270] PnPBIOS: Disabled by ACPI PNP
Apr 16 07:26:29 LinuxServerName kernel: [73137.885585] PCI: Using ACPI for IRQ routing
Apr 16 07:26:29 LinuxServerName kernel: [73137.885695] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NET: Registered protocol family 8
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NET: Registered protocol family 20
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel: Initializing
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel:  domain hash size = 128
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel:  unlabeled traffic allowed by default
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] PCI: Bridge: 0000:00:01.0
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609]   IO window: disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609]   MEM window: disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609]   PREFETCH window: disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NET: Registered protocol family 2
Apr 16 07:26:29 LinuxServerName kernel: [73138.000542] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.000698] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.000854] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.001010] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 07:26:29 LinuxServerName kernel: [73138.001114] TCP reno registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.030414] checking if image is initramfs... it is
Apr 16 07:26:29 LinuxServerName kernel: [73138.439107] Freeing initrd memory: 6642k freed
Apr 16 07:26:29 LinuxServerName kernel: [73138.439789] Simple Boot Flag at 0x36 set to 0x1
Apr 16 07:26:29 LinuxServerName kernel: [73138.441456] audit: initializing netlink socket (disabled)
Apr 16 07:26:29 LinuxServerName kernel: [73138.441612] audit(1208345183.040:1): initialized
Apr 16 07:26:29 LinuxServerName kernel: [73138.442634] VFS: Disk quotas dquot_6.5.1
Apr 16 07:26:29 LinuxServerName kernel: [73138.442776] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.442932] io scheduler noop registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.443018] io scheduler anticipatory registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.443031] io scheduler deadline registered (default)
Apr 16 07:26:29 LinuxServerName kernel: [73138.443145] io scheduler cfq registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.443301] Limiting direct PCI/PCI transfers.
Apr 16 07:26:29 LinuxServerName kernel: [73138.444004] isapnp: Scanning for PnP cards...
Apr 16 07:26:29 LinuxServerName kernel: [73138.802799] isapnp: No Plug & Play device found
Apr 16 07:26:29 LinuxServerName kernel: [73138.841920] Real Time Clock Driver v1.12ac
Apr 16 07:26:29 LinuxServerName kernel: [73138.842143] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 07:26:29 LinuxServerName kernel: [73138.842508] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.842877] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.844257] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.844840] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.845726] mice: PS/2 mouse device common for all mice
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] EISA: Probing bus 0 at eisa.0
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] Cannot allocate resource for EISA slot 1
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] EISA: Detected 0 cards.
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] TCP cubic registered
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] NET: Registered protocol family 1
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] Using IPI No-Shortcut mode
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] ACPI: (supports S0 S1 S4 S5)
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035]   Magic number: 4:728:428
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] Freeing unused kernel memory: 332k freed
Apr 16 07:26:29 LinuxServerName kernel: [73139.386154] Time: tsc clocksource has been installed.
Apr 16 07:26:29 LinuxServerName kernel: [73139.557286] Capability LSM initialized
Apr 16 07:26:29 LinuxServerName kernel: [73139.586929] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 07:26:29 LinuxServerName kernel: [73139.587084] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 07:26:29 LinuxServerName kernel: [73139.587217] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 07:26:29 LinuxServerName kernel: [73139.587259] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 07:26:29 LinuxServerName kernel: [73140.184393] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 07:26:29 LinuxServerName kernel: [73140.184549] PIIX4: chipset revision 1
Apr 16 07:26:29 LinuxServerName kernel: [73140.184616] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 07:26:29 LinuxServerName kernel: [73140.184771]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 07:26:29 LinuxServerName kernel: [73140.184927] Probing IDE interface ide0...
Apr 16 07:26:29 LinuxServerName kernel: [73140.194744] SCSI subsystem initialized
Apr 16 07:26:29 LinuxServerName kernel: [73140.195273] Fusion MPT base driver 3.04.03
Apr 16 07:26:29 LinuxServerName kernel: [73140.195299] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 07:26:29 LinuxServerName kernel: [73140.195821] Fusion MPT SPI Host driver 3.04.03
Apr 16 07:26:29 LinuxServerName kernel: [73140.205877] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 07:26:29 LinuxServerName kernel: [73140.265329] Floppy drive(s): fd0 is 1.44M
Apr 16 07:26:29 LinuxServerName kernel: [73140.294207] FDC 0 is a post-1991 82077
Apr 16 07:26:29 LinuxServerName kernel: [73141.061044] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 07:26:29 LinuxServerName kernel: [73141.440228] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 07:26:29 LinuxServerName kernel: [73141.442172] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 07:26:29 LinuxServerName kernel: [73141.442327] mptbase: Initiating ioc0 bringup
Apr 16 07:26:29 LinuxServerName kernel: [73141.709053] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 07:26:29 LinuxServerName kernel: [73142.177839] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: Beginning Domain Validation
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: Domain Validation skipping write tests
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: Ending Domain Validation
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 07:26:29 LinuxServerName kernel: [73142.534740] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 07:26:29 LinuxServerName kernel: [73142.534896] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 07:26:29 LinuxServerName kernel: [73142.536657] eth0: registered as PCnet/PCI II 79C970A
Apr 16 07:26:29 LinuxServerName kernel: [73142.536813] pcnet32: 1 cards_found.
Apr 16 07:26:29 LinuxServerName kernel: [73142.541543] libata version 2.20 loaded.
Apr 16 07:26:29 LinuxServerName kernel: [73142.561896] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73142.562052] sda: test WP failed, assume Write Enabled
Apr 16 07:26:29 LinuxServerName kernel: [73142.562208] sda: cache data unavailable
Apr 16 07:26:29 LinuxServerName kernel: [73142.562238] sda: assuming drive cache: write through
Apr 16 07:26:29 LinuxServerName kernel: [73142.562394] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73142.562499] sda: test WP failed, assume Write Enabled
Apr 16 07:26:29 LinuxServerName kernel: [73142.562535] sda: cache data unavailable
Apr 16 07:26:29 LinuxServerName kernel: [73142.562538] sda: assuming drive cache: write through
Apr 16 07:26:29 LinuxServerName kernel: [73142.562691]  sda: sda1 sda2 <<6>hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 07:26:29 LinuxServerName kernel: [73142.570141] Uniform CD-ROM driver Revision: 3.20
Apr 16 07:26:29 LinuxServerName kernel: [73142.572771]  sda5 >
Apr 16 07:26:29 LinuxServerName kernel: [73142.573082] sd 0:0:0:0: Attached scsi disk sda
Apr 16 07:26:29 LinuxServerName kernel: [73142.590405] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 07:26:29 LinuxServerName kernel: [73142.742411] Attempting manual resume
Apr 16 07:26:29 LinuxServerName kernel: [73142.742445] swsusp: Resume From Partition 8:5
Apr 16 07:26:29 LinuxServerName kernel: [73142.742471] PM: Checking swsusp image.
Apr 16 07:26:29 LinuxServerName kernel: [73142.743104] PM: Resume from disk failed.
Apr 16 07:26:29 LinuxServerName kernel: [73142.754493] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 16 07:26:29 LinuxServerName kernel: [73142.754524] EXT3-fs: write access will be enabled during recovery.
Apr 16 07:26:29 LinuxServerName kernel: [73143.166008] kjournald starting.  Commit interval 5 seconds
Apr 16 07:26:29 LinuxServerName kernel: [73143.166307] EXT3-fs: recovery complete.
Apr 16 07:26:29 LinuxServerName kernel: [73143.167108] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 07:26:29 LinuxServerName kernel: [73143.644473] parport: PnPBIOS parport detected.
Apr 16 07:26:29 LinuxServerName kernel: [73143.644629] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 07:26:29 LinuxServerName kernel: [73143.743087] lp0: using parport0 (interrupt-driven).
Apr 16 07:26:29 LinuxServerName kernel: [73143.767028] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 07:26:29 LinuxServerName kernel: [73143.789089] EXT3 FS on sda1, internal journal
Apr 16 07:26:29 LinuxServerName kernel: [73143.872378] eth0: link up
Apr 16 07:26:29 LinuxServerName mysqld_safe[2620]: started
Apr 16 07:26:29 LinuxServerName mysqld[2624]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ib78QA4U' (Errcode: 13)
Apr 16 07:26:29 LinuxServerName mysqld[2624]: 080416  7:26:29  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 07:26:29 LinuxServerName mysqld[2624]: 080416  7:26:29 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 07:26:29 LinuxServerName mysqld[2624]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 07:26:39 LinuxServerName /etc/mysql/debian-start[2653]: Upgrading MySQL tables if necessary.
Apr 16 07:26:39 LinuxServerName slapd[2670]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 07:26:41 LinuxServerName kernel: [73146.624127] NET: Registered protocol family 10
Apr 16 07:26:41 LinuxServerName kernel: [73146.624308] lo: Disabled Privacy Extensions
Apr 16 07:26:42 LinuxServerName /etc/mysql/debian-start[2688]: Checking for crashed MySQL tables.
Apr 16 07:26:42 LinuxServerName mysqld[2624]: 080416  7:26:42 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 07:26:42 LinuxServerName mysqld[2624]: 080416  7:26:42 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 07:26:43 LinuxServerName mysqld[2624]: 080416  7:26:43 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 07:26:44 LinuxServerName mysqld[2624]: 080416  7:26:44 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 07:26:44 LinuxServerName mysqld[2624]: 080416  7:26:44 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 07:26:44 LinuxServerName mysqld[2624]: 080416  7:26:44 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 07:26:44 LinuxServerName mysqld[2624]: 080416  7:26:44 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 07:26:44 LinuxServerName mysqld[2624]: 080416  7:26:44 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 07:26:44 LinuxServerName mysqld[2624]: 080416  7:26:44 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 07:26:45 LinuxServerName mysqld[2624]: 080416  7:26:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 07:26:46 LinuxServerName atd[2757]: Error redirecting I/O: Permission denied
Apr 16 07:26:46 LinuxServerName /usr/sbin/cron[2760]: (CRON) INFO (pidfile fd = 3)
Apr 16 07:26:47 LinuxServerName /usr/sbin/cron[2761]: (CRON) STARTUP (fork ok)
Apr 16 07:26:47 LinuxServerName /usr/sbin/cron[2761]: (CRON) INFO (Running @reboot jobs)
Apr 16 07:26:51 LinuxServerName kernel: [73157.998957] eth0: no IPv6 routers present
Apr 16 07:27:47 LinuxServerName init: tty1 main process (2506) terminated with status 1
Apr 16 07:27:47 LinuxServerName init: tty1 main process ended, respawning
Apr 16 07:27:56 LinuxServerName init: tty4 main process (2498) killed by TERM signal
Apr 16 07:27:56 LinuxServerName init: tty5 main process (2499) killed by TERM signal
Apr 16 07:27:56 LinuxServerName init: tty2 main process (2504) killed by TERM signal
Apr 16 07:27:56 LinuxServerName init: tty3 main process (2505) killed by TERM signal
Apr 16 07:27:56 LinuxServerName init: tty6 main process (2507) killed by TERM signal
Apr 16 07:27:56 LinuxServerName init: tty1 main process (2792) killed by TERM signal
Apr 16 07:27:59 LinuxServerName mysqld[2624]: 080416  7:27:59 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 07:27:59 LinuxServerName mysqld[2624]: 
Apr 16 07:27:59 LinuxServerName mysqld[2624]: 080416  7:27:59 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 07:27:59 LinuxServerName mysqld[2624]: 
Apr 16 07:27:59 LinuxServerName mysqld_safe[2868]: ended
Apr 16 07:28:00 LinuxServerName exiting on signal 15
Apr 16 09:53:45 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 09:53:45 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 09:53:45 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 09:53:45 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 09:53:45 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Detected 3390.985 MHz processor.
Apr 16 09:53:45 LinuxServerName kernel: [81871.309511] Built 1 zonelists.  Total pages: 130048
Apr 16 09:53:45 LinuxServerName kernel: [81871.309687] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro single
Apr 16 09:53:45 LinuxServerName kernel: [81871.310542] mapped APIC to ffffd000 (fee00000)
Apr 16 09:53:45 LinuxServerName kernel: [81871.310605] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 09:53:45 LinuxServerName kernel: [81871.311004] Enabling fast FPU save and restore... done.
Apr 16 09:53:45 LinuxServerName kernel: [81871.311069] Enabling unmasked SIMD FPU exception support... done.
Apr 16 09:53:45 LinuxServerName kernel: [81871.311420] Initializing CPU#0
Apr 16 09:53:45 LinuxServerName kernel: [81871.312898] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313054] Console: colour VGA+ 80x25
Apr 16 09:53:45 LinuxServerName kernel: [81871.313209] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313365] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313521] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313677] virtual kernel memory layout:
Apr 16 09:53:45 LinuxServerName kernel: [81871.313683]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313685]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313687]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313689]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313690]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313692]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313693]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313849] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 09:53:45 LinuxServerName kernel: [81871.462424] Calibrating delay using timer specific routine.. 6797.77 BogoMIPS (lpj=33988863)
Apr 16 09:53:45 LinuxServerName kernel: [81871.462579] Security Framework v1.0.0 initialized
Apr 16 09:53:45 LinuxServerName kernel: [81871.462735] SELinux:  Disabled at boot.
Apr 16 09:53:45 LinuxServerName kernel: [81871.462891] Mount-cache hash table entries: 512
Apr 16 09:53:45 LinuxServerName kernel: [81871.463047] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 09:53:45 LinuxServerName kernel: [81871.463202] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 09:53:45 LinuxServerName kernel: [81871.463358] CPU: L2 cache: 1024K
Apr 16 09:53:45 LinuxServerName kernel: [81871.463509] CPU: L3 cache: 16384K
Apr 16 09:53:45 LinuxServerName kernel: [81871.463664] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 09:53:45 LinuxServerName kernel: [81871.463820] Compat vDSO mapped to ffffe000.
Apr 16 09:53:45 LinuxServerName kernel: [81871.463957] Remapping vsyscall page to ffffe000
Apr 16 09:53:45 LinuxServerName kernel: [81871.464112] Checking 'hlt' instruction... OK.
Apr 16 09:53:45 LinuxServerName kernel: [81871.502403] SMP alternatives: switching to UP code
Apr 16 09:53:45 LinuxServerName kernel: [81871.502559] Freeing SMP alternatives: 11k freed
Apr 16 09:53:45 LinuxServerName kernel: [81871.502715] Early unpacking initramfs... done
Apr 16 09:53:45 LinuxServerName kernel: [81871.741665] ACPI: Core revision 20060707
Apr 16 09:53:45 LinuxServerName kernel: [81871.741821] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 09:53:45 LinuxServerName kernel: [81871.742444] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 09:53:45 LinuxServerName kernel: [81871.742600] Total of 1 processors activated (6797.77 BogoMIPS).
Apr 16 09:53:45 LinuxServerName kernel: [81871.742756] ENABLING IO-APIC IRQs
Apr 16 09:53:45 LinuxServerName kernel: [81871.743167] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Brought up 1 CPUs
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Booting paravirtualized kernel on bare hardware
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Time: 13:52:40  Date: 03/16/108
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] NET: Registered protocol family 16
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] EISA bus registered
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] ACPI: bus type pci registered
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] PCI: Using configuration type 1
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Setting up standard PCI resources
Apr 16 09:53:45 LinuxServerName kernel: [81871.970790] ACPI: Interpreter enabled
Apr 16 09:53:45 LinuxServerName kernel: [81871.970790] ACPI: Using IOAPIC for interrupt routing
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] PCI: Probing PCI hardware (bus 00)
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] Boot video device is 0000:00:0f.0
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 09:53:45 LinuxServerName kernel: [81871.971115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 09:53:45 LinuxServerName kernel: [81871.971432] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81871.982585] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 09:53:45 LinuxServerName kernel: [81871.982741] pnp: PnP ACPI init
Apr 16 09:53:45 LinuxServerName kernel: [81871.993228] pnp: PnP ACPI: found 12 devices
Apr 16 09:53:45 LinuxServerName kernel: [81871.993384] PnPBIOS: Disabled by ACPI PNP
Apr 16 09:53:45 LinuxServerName kernel: [81871.993698] PCI: Using ACPI for IRQ routing
Apr 16 09:53:45 LinuxServerName kernel: [81871.993854] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NET: Registered protocol family 8
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NET: Registered protocol family 20
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel: Initializing
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel:  domain hash size = 128
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel:  unlabeled traffic allowed by default
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] PCI: Bridge: 0000:00:01.0
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698]   IO window: disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698]   MEM window: disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698]   PREFETCH window: disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NET: Registered protocol family 2
Apr 16 09:53:45 LinuxServerName kernel: [81872.100577] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.100733] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.100889] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.101044] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 09:53:45 LinuxServerName kernel: [81872.101200] TCP reno registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.130474] checking if image is initramfs... it is
Apr 16 09:53:45 LinuxServerName kernel: [81872.599013] Freeing initrd memory: 6642k freed
Apr 16 09:53:45 LinuxServerName kernel: [81872.599738] Simple Boot Flag at 0x36 set to 0x1
Apr 16 09:53:45 LinuxServerName kernel: [81872.601442] audit: initializing netlink socket (disabled)
Apr 16 09:53:45 LinuxServerName kernel: [81872.601598] audit(1208353960.150:1): initialized
Apr 16 09:53:45 LinuxServerName kernel: [81872.602620] VFS: Disk quotas dquot_6.5.1
Apr 16 09:53:45 LinuxServerName kernel: [81872.602776] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.602932] io scheduler noop registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.603088] io scheduler anticipatory registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.603224] io scheduler deadline registered (default)
Apr 16 09:53:45 LinuxServerName kernel: [81872.603380] io scheduler cfq registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.603535] Limiting direct PCI/PCI transfers.
Apr 16 09:53:45 LinuxServerName kernel: [81872.604230] isapnp: Scanning for PnP cards...
Apr 16 09:53:45 LinuxServerName kernel: [81872.966585] isapnp: No Plug & Play device found
Apr 16 09:53:45 LinuxServerName kernel: [81873.004817] Real Time Clock Driver v1.12ac
Apr 16 09:53:45 LinuxServerName kernel: [81873.005131] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] mice: PS/2 mouse device common for all mice
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 09:53:45 LinuxServerName kernel: [81873.007923] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 09:53:45 LinuxServerName kernel: [81873.008279] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 09:53:45 LinuxServerName kernel: [81873.008434] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 09:53:45 LinuxServerName kernel: [81873.009009] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 09:53:45 LinuxServerName kernel: [81873.517085] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 09:53:45 LinuxServerName kernel: [81873.517258] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 09:53:45 LinuxServerName kernel: [81873.526002] EISA: Probing bus 0 at eisa.0
Apr 16 09:53:45 LinuxServerName kernel: [81873.526002] Cannot allocate resource for EISA slot 1
Apr 16 09:53:45 LinuxServerName kernel: [81873.526002] EISA: Detected 0 cards.
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] TCP cubic registered
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] NET: Registered protocol family 1
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] Using IPI No-Shortcut mode
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] ACPI: (supports S0 S1 S4 S5)
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910]   Magic number: 4:905:887
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910]   hash matches device ptyue
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] Freeing unused kernel memory: 332k freed
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 09:53:45 LinuxServerName kernel: [81873.556039] Time: tsc clocksource has been installed.
Apr 16 09:53:45 LinuxServerName kernel: [81873.746686] Capability LSM initialized
Apr 16 09:53:45 LinuxServerName kernel: [81873.786734] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 09:53:45 LinuxServerName kernel: [81873.786890] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:53:45 LinuxServerName kernel: [81873.787045] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:53:45 LinuxServerName kernel: [81873.787201] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:53:45 LinuxServerName kernel: [81874.396070] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 09:53:45 LinuxServerName kernel: [81874.403613] PIIX4: chipset revision 1
Apr 16 09:53:45 LinuxServerName kernel: [81874.403763] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 09:53:45 LinuxServerName kernel: [81874.403919]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 09:53:45 LinuxServerName kernel: [81874.404075] Probing IDE interface ide0...
Apr 16 09:53:45 LinuxServerName kernel: [81874.426174] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 09:53:45 LinuxServerName kernel: [81874.459307] SCSI subsystem initialized
Apr 16 09:53:45 LinuxServerName kernel: [81874.459849] Fusion MPT base driver 3.04.03
Apr 16 09:53:45 LinuxServerName kernel: [81874.459963] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 09:53:45 LinuxServerName kernel: [81874.460507] Fusion MPT SPI Host driver 3.04.03
Apr 16 09:53:45 LinuxServerName kernel: [81874.477517] Floppy drive(s): fd0 is 1.44M
Apr 16 09:53:45 LinuxServerName kernel: [81874.503928] FDC 0 is a post-1991 82077
Apr 16 09:53:45 LinuxServerName kernel: [81875.310675] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 09:53:45 LinuxServerName kernel: [81875.709810] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 09:53:45 LinuxServerName kernel: [81875.711842] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 09:53:45 LinuxServerName kernel: [81875.711998] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] eth0: registered as PCnet/PCI II 79C970A
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] pcnet32: 1 cards_found.
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] mptbase: Initiating ioc0 bringup
Apr 16 09:53:45 LinuxServerName kernel: [81875.978616] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 09:53:45 LinuxServerName kernel: [81876.457388] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 09:53:45 LinuxServerName kernel: [81876.836488] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 09:53:45 LinuxServerName kernel: [81876.836643]  target0:0:0: Beginning Domain Validation
Apr 16 09:53:45 LinuxServerName kernel: [81876.836799]  target0:0:0: Domain Validation skipping write tests
Apr 16 09:53:45 LinuxServerName kernel: [81876.836955]  target0:0:0: Ending Domain Validation
Apr 16 09:53:45 LinuxServerName kernel: [81876.837111]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 09:53:45 LinuxServerName kernel: [81876.858685] libata version 2.20 loaded.
Apr 16 09:53:45 LinuxServerName kernel: [81876.884438] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 09:53:45 LinuxServerName kernel: [81876.884594] Uniform CD-ROM driver Revision: 3.20
Apr 16 09:53:45 LinuxServerName kernel: [81876.901417] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81876.901572] sda: test WP failed, assume Write Enabled
Apr 16 09:53:45 LinuxServerName kernel: [81876.901728] sda: cache data unavailable
Apr 16 09:53:45 LinuxServerName kernel: [81876.901840] sda: assuming drive cache: write through
Apr 16 09:53:45 LinuxServerName kernel: [81876.901996] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81876.902152] sda: test WP failed, assume Write Enabled
Apr 16 09:53:45 LinuxServerName kernel: [81876.902276] sda: cache data unavailable
Apr 16 09:53:45 LinuxServerName kernel: [81876.902362] sda: assuming drive cache: write through
Apr 16 09:53:45 LinuxServerName kernel: [81876.902518]  sda: sda1 sda2 < sda5 >
Apr 16 09:53:45 LinuxServerName kernel: [81876.906260] sd 0:0:0:0: Attached scsi disk sda
Apr 16 09:53:45 LinuxServerName kernel: [81876.909843] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 09:53:45 LinuxServerName kernel: [81876.995491] Attempting manual resume
Apr 16 09:53:45 LinuxServerName kernel: [81876.995609] swsusp: Resume From Partition 8:5
Apr 16 09:53:45 LinuxServerName kernel: [81876.995634] PM: Checking swsusp image.
Apr 16 09:53:45 LinuxServerName kernel: [81876.996272] PM: Resume from disk failed.
Apr 16 09:53:45 LinuxServerName kernel: [81877.015690] kjournald starting.  Commit interval 5 seconds
Apr 16 09:53:45 LinuxServerName kernel: [81877.016002] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 09:53:45 LinuxServerName kernel: [81877.487035] parport: PnPBIOS parport detected.
Apr 16 09:53:45 LinuxServerName kernel: [81877.487191] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 09:53:45 LinuxServerName kernel: [81877.573975] lp0: using parport0 (interrupt-driven).
Apr 16 09:53:45 LinuxServerName kernel: [81877.599040] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 09:53:45 LinuxServerName kernel: [81877.629210] EXT3 FS on sda1, internal journal
Apr 16 09:53:45 LinuxServerName kernel: [81877.733205] eth0: link up
Apr 16 09:53:46 LinuxServerName mysqld_safe[2733]: started
Apr 16 09:53:46 LinuxServerName mysqld[2737]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ibX43har' (Errcode: 13)
Apr 16 09:53:46 LinuxServerName mysqld[2737]: 080416  9:53:46  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 09:53:46 LinuxServerName mysqld[2737]: 080416  9:53:46 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 09:53:46 LinuxServerName mysqld[2737]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 09:53:47 LinuxServerName /etc/mysql/debian-start[2765]: Upgrading MySQL tables if necessary.
Apr 16 09:53:47 LinuxServerName slapd[2782]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 09:53:48 LinuxServerName kernel: [81933.208469] NET: Registered protocol family 10
Apr 16 09:53:48 LinuxServerName kernel: [81933.211426] lo: Disabled Privacy Extensions
Apr 16 09:53:48 LinuxServerName /etc/mysql/debian-start[2785]: Checking for crashed MySQL tables.
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 09:53:48 LinuxServerName mysqld[2737]: 080416  9:53:48 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 09:53:49 LinuxServerName atd[2879]: Error redirecting I/O: Permission denied
Apr 16 09:53:49 LinuxServerName /usr/sbin/cron[2883]: (CRON) INFO (pidfile fd = 3)
Apr 16 09:53:49 LinuxServerName /usr/sbin/cron[2884]: (CRON) STARTUP (fork ok)
Apr 16 09:53:49 LinuxServerName /usr/sbin/cron[2884]: (CRON) INFO (Running @reboot jobs)
Apr 16 09:53:58 LinuxServerName kernel: [81944.367964] eth0: no IPv6 routers present
Apr 16 09:54:57 LinuxServerName init: tty1 main process (2609) terminated with status 1
Apr 16 09:54:57 LinuxServerName init: tty1 main process ended, respawning
Apr 16 09:55:01 LinuxServerName CRON[2923]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 09:55:01 LinuxServerName CRON[2923]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 09:55:01 LinuxServerName CRON[2923]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 09:55:01 LinuxServerName CRON[2923]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 09:55:01 LinuxServerName CRON[2923]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 09:55:01 LinuxServerName CRON[2923]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 09:55:01 LinuxServerName CRON[2923]: Module is unknown
Apr 16 09:55:01 LinuxServerName CRON[2922]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 09:55:01 LinuxServerName CRON[2922]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 09:55:01 LinuxServerName CRON[2922]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 09:55:01 LinuxServerName CRON[2922]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 09:55:01 LinuxServerName CRON[2922]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 09:55:01 LinuxServerName CRON[2922]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 09:55:01 LinuxServerName CRON[2922]: Module is unknown
Apr 16 09:55:06 LinuxServerName init: tty1 main process (2921) terminated with status 1
Apr 16 09:55:06 LinuxServerName init: tty1 main process ended, respawning
Apr 16 09:55:10 LinuxServerName init: tty4 main process (2602) killed by TERM signal
Apr 16 09:55:10 LinuxServerName init: tty5 main process (2603) killed by TERM signal
Apr 16 09:55:10 LinuxServerName init: tty2 main process (2606) killed by TERM signal
Apr 16 09:55:10 LinuxServerName init: tty3 main process (2608) killed by TERM signal
Apr 16 09:55:10 LinuxServerName init: tty6 main process (2610) killed by TERM signal
Apr 16 09:55:10 LinuxServerName init: tty1 main process (2924) killed by TERM signal
Apr 16 09:55:12 LinuxServerName mysqld[2737]: 080416  9:55:12 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 09:55:12 LinuxServerName mysqld[2737]: 
Apr 16 09:55:12 LinuxServerName mysqld[2737]: 080416  9:55:12 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 09:55:12 LinuxServerName mysqld[2737]: 
Apr 16 09:55:12 LinuxServerName mysqld_safe[3010]: ended
Apr 16 09:55:13 LinuxServerName exiting on signal 15
Apr 16 09:56:10 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 09:56:10 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 09:56:10 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 09:56:10 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 09:56:10 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Detected 3390.952 MHz processor.
Apr 16 09:56:10 LinuxServerName kernel: [82031.560065] Built 1 zonelists.  Total pages: 130048
Apr 16 09:56:10 LinuxServerName kernel: [82031.560249] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro single
Apr 16 09:56:10 LinuxServerName kernel: [82031.561104] mapped APIC to ffffd000 (fee00000)
Apr 16 09:56:10 LinuxServerName kernel: [82031.561169] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 09:56:10 LinuxServerName kernel: [82031.561568] Enabling fast FPU save and restore... done.
Apr 16 09:56:10 LinuxServerName kernel: [82031.561639] Enabling unmasked SIMD FPU exception support... done.
Apr 16 09:56:10 LinuxServerName kernel: [82031.561957] Initializing CPU#0
Apr 16 09:56:10 LinuxServerName kernel: [82031.563561] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82031.563717] Console: colour VGA+ 80x25
Apr 16 09:56:10 LinuxServerName kernel: [82031.563872] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564028] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564184] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564340] virtual kernel memory layout:
Apr 16 09:56:10 LinuxServerName kernel: [82031.564345]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564347]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564349]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564350]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564352]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564354]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564355]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564511] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 09:56:10 LinuxServerName kernel: [82031.713053] Calibrating delay using timer specific routine.. 6795.68 BogoMIPS (lpj=33978424)
Apr 16 09:56:10 LinuxServerName kernel: [82031.713208] Security Framework v1.0.0 initialized
Apr 16 09:56:10 LinuxServerName kernel: [82031.713364] SELinux:  Disabled at boot.
Apr 16 09:56:10 LinuxServerName kernel: [82031.713520] Mount-cache hash table entries: 512
Apr 16 09:56:10 LinuxServerName kernel: [82031.713676] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 09:56:10 LinuxServerName kernel: [82031.713831] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 09:56:10 LinuxServerName kernel: [82031.713987] CPU: L2 cache: 1024K
Apr 16 09:56:10 LinuxServerName kernel: [82031.714088] CPU: L3 cache: 16384K
Apr 16 09:56:10 LinuxServerName kernel: [82031.714244] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 09:56:10 LinuxServerName kernel: [82031.714400] Compat vDSO mapped to ffffe000.
Apr 16 09:56:10 LinuxServerName kernel: [82031.714539] Remapping vsyscall page to ffffe000
Apr 16 09:56:10 LinuxServerName kernel: [82031.714694] Checking 'hlt' instruction... OK.
Apr 16 09:56:10 LinuxServerName kernel: [82031.753045] SMP alternatives: switching to UP code
Apr 16 09:56:10 LinuxServerName kernel: [82031.753200] Freeing SMP alternatives: 11k freed
Apr 16 09:56:10 LinuxServerName kernel: [82031.753356] Early unpacking initramfs... done
Apr 16 09:56:10 LinuxServerName kernel: [82031.942460] ACPI: Core revision 20060707
Apr 16 09:56:10 LinuxServerName kernel: [82031.942616] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 09:56:10 LinuxServerName kernel: [82031.943239] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 09:56:10 LinuxServerName kernel: [82031.943395] Total of 1 processors activated (6795.68 BogoMIPS).
Apr 16 09:56:10 LinuxServerName kernel: [82031.943551] ENABLING IO-APIC IRQs
Apr 16 09:56:10 LinuxServerName kernel: [82031.943963] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Brought up 1 CPUs
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Booting paravirtualized kernel on bare hardware
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Time: 13:55:27  Date: 03/16/108
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] NET: Registered protocol family 16
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] EISA bus registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] ACPI: bus type pci registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] PCI: Using configuration type 1
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Setting up standard PCI resources
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: Interpreter enabled
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: Using IOAPIC for interrupt routing
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] PCI: Probing PCI hardware (bus 00)
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] Boot video device is 0000:00:0f.0
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.171682] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 09:56:10 LinuxServerName kernel: [82032.171995] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 09:56:10 LinuxServerName kernel: [82032.172368] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.183459] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 09:56:10 LinuxServerName kernel: [82032.183615] pnp: PnP ACPI init
Apr 16 09:56:10 LinuxServerName kernel: [82032.194574] pnp: PnP ACPI: found 12 devices
Apr 16 09:56:10 LinuxServerName kernel: [82032.194730] PnPBIOS: Disabled by ACPI PNP
Apr 16 09:56:10 LinuxServerName kernel: [82032.195058] PCI: Using ACPI for IRQ routing
Apr 16 09:56:10 LinuxServerName kernel: [82032.195214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NET: Registered protocol family 8
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NET: Registered protocol family 20
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel: Initializing
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel:  domain hash size = 128
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel:  unlabeled traffic allowed by default
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467] PCI: Bridge: 0000:00:01.0
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467]   IO window: disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467]   MEM window: disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467]   PREFETCH window: disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467] NET: Registered protocol family 2
Apr 16 09:56:10 LinuxServerName kernel: [82032.311488] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.311644] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.311800] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.311956] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 09:56:10 LinuxServerName kernel: [82032.312112] TCP reno registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.341251] checking if image is initramfs... it is
Apr 16 09:56:10 LinuxServerName kernel: [82032.749965] Freeing initrd memory: 6642k freed
Apr 16 09:56:10 LinuxServerName kernel: [82032.750745] Simple Boot Flag at 0x36 set to 0x1
Apr 16 09:56:10 LinuxServerName kernel: [82032.752402] audit: initializing netlink socket (disabled)
Apr 16 09:56:10 LinuxServerName kernel: [82032.752558] audit(1208354128.050:1): initialized
Apr 16 09:56:10 LinuxServerName kernel: [82032.753556] VFS: Disk quotas dquot_6.5.1
Apr 16 09:56:10 LinuxServerName kernel: [82032.753712] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.753868] io scheduler noop registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.754024] io scheduler anticipatory registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.754138] io scheduler deadline registered (default)
Apr 16 09:56:10 LinuxServerName kernel: [82032.754293] io scheduler cfq registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.754449] Limiting direct PCI/PCI transfers.
Apr 16 09:56:10 LinuxServerName kernel: [82032.759873] isapnp: Scanning for PnP cards...
Apr 16 09:56:10 LinuxServerName kernel: [82033.117200] isapnp: No Plug & Play device found
Apr 16 09:56:10 LinuxServerName kernel: [82033.153161] Real Time Clock Driver v1.12ac
Apr 16 09:56:10 LinuxServerName kernel: [82033.153463] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 09:56:10 LinuxServerName kernel: [82033.153828] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158550] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] mice: PS/2 mouse device common for all mice
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 09:56:10 LinuxServerName kernel: [82033.667523] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 09:56:10 LinuxServerName kernel: [82033.667707] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 09:56:10 LinuxServerName kernel: [82033.669603] EISA: Probing bus 0 at eisa.0
Apr 16 09:56:10 LinuxServerName kernel: [82033.669915] Cannot allocate resource for EISA slot 1
Apr 16 09:56:10 LinuxServerName kernel: [82033.670071] EISA: Detected 0 cards.
Apr 16 09:56:10 LinuxServerName kernel: [82033.700379] TCP cubic registered
Apr 16 09:56:10 LinuxServerName kernel: [82033.700504] NET: Registered protocol family 1
Apr 16 09:56:10 LinuxServerName kernel: [82033.700660] Using IPI No-Shortcut mode
Apr 16 09:56:10 LinuxServerName kernel: [82033.701257] ACPI: (supports S0 S1 S4 S5)
Apr 16 09:56:10 LinuxServerName kernel: [82033.706862]   Magic number: 4:458:938
Apr 16 09:56:10 LinuxServerName kernel: [82033.706862] Freeing unused kernel memory: 332k freed
Apr 16 09:56:10 LinuxServerName kernel: [82033.706862] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 09:56:10 LinuxServerName kernel: [82033.706982] Time: tsc clocksource has been installed.
Apr 16 09:56:10 LinuxServerName kernel: [82033.888059] Capability LSM initialized
Apr 16 09:56:10 LinuxServerName kernel: [82033.926848] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 09:56:10 LinuxServerName kernel: [82033.927004] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:56:10 LinuxServerName kernel: [82033.927160] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:56:10 LinuxServerName kernel: [82033.927316] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:56:10 LinuxServerName kernel: [82034.527134] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 09:56:10 LinuxServerName kernel: [82034.527290] PIIX4: chipset revision 1
Apr 16 09:56:10 LinuxServerName kernel: [82034.527439] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 09:56:10 LinuxServerName kernel: [82034.534545]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 09:56:10 LinuxServerName kernel: [82034.534701] Probing IDE interface ide0...
Apr 16 09:56:10 LinuxServerName kernel: [82034.556437] SCSI subsystem initialized
Apr 16 09:56:10 LinuxServerName kernel: [82034.557040] Fusion MPT base driver 3.04.03
Apr 16 09:56:10 LinuxServerName kernel: [82034.557195] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 09:56:10 LinuxServerName kernel: [82034.557759] Fusion MPT SPI Host driver 3.04.03
Apr 16 09:56:10 LinuxServerName kernel: [82034.558443] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 09:56:10 LinuxServerName kernel: [82034.606182] Floppy drive(s): fd0 is 1.44M
Apr 16 09:56:10 LinuxServerName kernel: [82034.634941] FDC 0 is a post-1991 82077
Apr 16 09:56:10 LinuxServerName kernel: [82035.401896] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 09:56:10 LinuxServerName kernel: [82035.800925] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 09:56:10 LinuxServerName kernel: [82035.802842] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 09:56:10 LinuxServerName kernel: [82035.802998] mptbase: Initiating ioc0 bringup
Apr 16 09:56:10 LinuxServerName kernel: [82036.049815] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 09:56:10 LinuxServerName kernel: [82036.498649] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 09:56:10 LinuxServerName kernel: [82036.887713] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 09:56:10 LinuxServerName kernel: [82036.887869]  target0:0:0: Beginning Domain Validation
Apr 16 09:56:10 LinuxServerName kernel: [82036.888024]  target0:0:0: Domain Validation skipping write tests
Apr 16 09:56:10 LinuxServerName kernel: [82036.888171]  target0:0:0: Ending Domain Validation
Apr 16 09:56:10 LinuxServerName kernel: [82036.888327]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 09:56:10 LinuxServerName kernel: [82036.905453] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 09:56:10 LinuxServerName kernel: [82036.905609] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 09:56:10 LinuxServerName kernel: [82036.907334] eth0: registered as PCnet/PCI II 79C970A
Apr 16 09:56:10 LinuxServerName kernel: [82036.907490] pcnet32: 1 cards_found.
Apr 16 09:56:10 LinuxServerName kernel: [82036.913023] libata version 2.20 loaded.
Apr 16 09:56:10 LinuxServerName kernel: [82036.934977] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 09:56:10 LinuxServerName kernel: [82036.935133] Uniform CD-ROM driver Revision: 3.20
Apr 16 09:56:10 LinuxServerName kernel: [82036.952144] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82036.952299] sda: test WP failed, assume Write Enabled
Apr 16 09:56:10 LinuxServerName kernel: [82036.952455] sda: cache data unavailable
Apr 16 09:56:10 LinuxServerName kernel: [82036.952568] sda: assuming drive cache: write through
Apr 16 09:56:10 LinuxServerName kernel: [82036.952724] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82036.952880] sda: test WP failed, assume Write Enabled
Apr 16 09:56:10 LinuxServerName kernel: [82036.952999] sda: cache data unavailable
Apr 16 09:56:10 LinuxServerName kernel: [82036.953083] sda: assuming drive cache: write through
Apr 16 09:56:10 LinuxServerName kernel: [82036.953239]  sda: sda1 sda2 < sda5 >
Apr 16 09:56:10 LinuxServerName kernel: [82036.957504] sd 0:0:0:0: Attached scsi disk sda
Apr 16 09:56:10 LinuxServerName kernel: [82036.961053] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 09:56:10 LinuxServerName kernel: [82037.123907] Attempting manual resume
Apr 16 09:56:10 LinuxServerName kernel: [82037.124031] swsusp: Resume From Partition 8:5
Apr 16 09:56:10 LinuxServerName kernel: [82037.124056] PM: Checking swsusp image.
Apr 16 09:56:10 LinuxServerName kernel: [82037.124686] PM: Resume from disk failed.
Apr 16 09:56:10 LinuxServerName kernel: [82037.141412] kjournald starting.  Commit interval 5 seconds
Apr 16 09:56:10 LinuxServerName kernel: [82037.141724] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 09:56:10 LinuxServerName kernel: [82037.426308] parport: PnPBIOS parport detected.
Apr 16 09:56:10 LinuxServerName kernel: [82037.426464] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 09:56:10 LinuxServerName kernel: [82037.525554] lp0: using parport0 (interrupt-driven).
Apr 16 09:56:10 LinuxServerName kernel: [82037.546964] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 09:56:10 LinuxServerName kernel: [82037.566073] EXT3 FS on sda1, internal journal
Apr 16 09:56:10 LinuxServerName kernel: [82037.627181] eth0: link up
Apr 16 09:56:10 LinuxServerName mysqld_safe[2727]: started
Apr 16 09:56:11 LinuxServerName mysqld[2731]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ibmPihxe' (Errcode: 13)
Apr 16 09:56:11 LinuxServerName mysqld[2731]: 080416  9:56:11  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 09:56:11 LinuxServerName mysqld[2731]: 080416  9:56:11 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 09:56:11 LinuxServerName mysqld[2731]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 09:56:12 LinuxServerName /etc/mysql/debian-start[2759]: Upgrading MySQL tables if necessary.
Apr 16 09:56:12 LinuxServerName slapd[2777]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 09:56:12 LinuxServerName kernel: [82071.371640] NET: Registered protocol family 10
Apr 16 09:56:12 LinuxServerName kernel: [82071.374447] lo: Disabled Privacy Extensions
Apr 16 09:56:12 LinuxServerName /etc/mysql/debian-start[2807]: Checking for crashed MySQL tables.
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 09:56:13 LinuxServerName mysqld[2731]: 080416  9:56:13 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 09:56:13 LinuxServerName ntpd[2866]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Apr 16 09:56:13 LinuxServerName ntpd[2867]: precision = 2.000 usec
Apr 16 09:56:13 LinuxServerName ntpd[2867]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Apr 16 09:56:13 LinuxServerName ntpd[2867]: Listening on interface wildcard, ::#123 Disabled
Apr 16 09:56:13 LinuxServerName ntpd[2867]: Listening on interface lo, ::1#123 Enabled
Apr 16 09:56:13 LinuxServerName ntpd[2867]: bind() fd 19, family 10, port 123, scope 2, addr fe80::250:56ff:fe88:27a, in6_is_addr_multicast=0 flags=1 fails: Cannot assign requested address
Apr 16 09:56:13 LinuxServerName ntpd[2867]: Listening on interface lo, 127.0.0.1#123 Enabled
Apr 16 09:56:13 LinuxServerName ntpd[2867]: Listening on interface eth0, 10.150.46.10#123 Enabled
Apr 16 09:56:13 LinuxServerName ntpd[2867]: kernel time sync status 0040
Apr 16 09:56:13 LinuxServerName ntpd[2867]: frequency initialized -109.250 PPM from /var/lib/ntp/ntp.drift
Apr 16 09:56:13 LinuxServerName atd[2875]: Error redirecting I/O: Permission denied
Apr 16 09:56:13 LinuxServerName /usr/sbin/cron[2879]: (CRON) INFO (pidfile fd = 3)
Apr 16 09:56:13 LinuxServerName /usr/sbin/cron[2881]: (CRON) STARTUP (fork ok)
Apr 16 09:56:13 LinuxServerName /usr/sbin/cron[2881]: (CRON) INFO (Running @reboot jobs)
Apr 16 09:56:15 LinuxServerName ntpd_initres[2880]: host name not found: ah-dc1.na.takatacorp.com
Apr 16 09:56:15 LinuxServerName ntpd_initres[2880]: couldn't resolve `ah-dc1.na.takatacorp.com', giving up on it
Apr 16 09:56:23 LinuxServerName kernel: [82082.257476] eth0: no IPv6 routers present
Apr 16 09:56:32 LinuxServerName init: tty1 main process (2602) terminated with status 1
Apr 16 09:56:32 LinuxServerName init: tty1 main process ended, respawning
Apr 16 10:00:01 LinuxServerName CRON[2920]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:00:01 LinuxServerName CRON[2920]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:00:01 LinuxServerName CRON[2920]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:00:01 LinuxServerName CRON[2920]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:00:01 LinuxServerName CRON[2920]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:00:01 LinuxServerName CRON[2920]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:00:01 LinuxServerName CRON[2920]: Module is unknown
Apr 16 10:00:01 LinuxServerName CRON[2919]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:00:01 LinuxServerName CRON[2919]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:00:01 LinuxServerName CRON[2919]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:00:01 LinuxServerName CRON[2919]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:00:01 LinuxServerName CRON[2919]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:00:01 LinuxServerName CRON[2919]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:00:01 LinuxServerName CRON[2919]: Module is unknown
Apr 16 09:59:55 LinuxServerName ntpd[2867]: synchronized to 10.150.10.5, stratum 4
Apr 16 09:59:55 LinuxServerName ntpd[2867]: time reset -33.609019 s
Apr 16 09:59:55 LinuxServerName ntpd[2867]: kernel time sync enabled 0001
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 080416 10:03:57 - mysqld got signal 11;
Apr 16 10:03:57 LinuxServerName mysqld[2731]: This could be because you hit a bug. It is also possible that this binary
Apr 16 10:03:57 LinuxServerName mysqld[2731]: or one of the libraries it was linked against is corrupt, improperly built,
Apr 16 10:03:57 LinuxServerName mysqld[2731]: or misconfigured. This error can also be caused by malfunctioning hardware.
Apr 16 10:03:57 LinuxServerName mysqld[2731]: We will try our best to scrape up some info that will hopefully help diagnose
Apr 16 10:03:57 LinuxServerName mysqld[2731]: the problem, but since we have already crashed, something is definitely wrong
Apr 16 10:03:57 LinuxServerName mysqld[2731]: and this may fail.
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 
Apr 16 10:03:57 LinuxServerName mysqld[2731]: key_buffer_size=16777216
Apr 16 10:03:57 LinuxServerName mysqld[2731]: read_buffer_size=131072
Apr 16 10:03:57 LinuxServerName mysqld[2731]: max_used_connections=2
Apr 16 10:03:57 LinuxServerName mysqld[2731]: max_connections=100
Apr 16 10:03:57 LinuxServerName mysqld[2731]: threads_connected=1
Apr 16 10:03:57 LinuxServerName mysqld[2731]: It is possible that mysqld could use up to 
Apr 16 10:03:57 LinuxServerName mysqld[2731]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 233983 K
Apr 16 10:03:57 LinuxServerName mysqld[2731]: bytes of memory
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Hope that's ok; if not, decrease some variables in the equation.
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 
Apr 16 10:03:57 LinuxServerName mysqld[2731]: thd=0x8a9c330
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Attempting backtrace. You can use the following information to find out
Apr 16 10:03:57 LinuxServerName mysqld[2731]: where mysqld died. If you see no messages after this, something went
Apr 16 10:03:57 LinuxServerName mysqld[2731]: terribly wrong...
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Cannot determine thread, fp=0xb52277f8, backtrace may not be correct.
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Stack range sanity check OK, backtrace follows:
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x81ea513
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x83222eb
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x829c9a4
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x82d0519
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x82cf3cc
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x824d30a
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x824eced
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x824f53f
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x8201ed3
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x8206be9
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x8207147
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x82084d7
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0x8209010
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0xb7eaae5a
Apr 16 10:03:57 LinuxServerName mysqld[2731]: 0xb7cd791e
Apr 16 10:03:57 LinuxServerName mysqld[2731]: New value of fp=(nil) failed sanity check, terminating stack trace!
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Please read http://dev.mysql.com/doc/mysql/en/using-stack-trace.html and follow instructions on how to resolve the stack trace. Resolved
Apr 16 10:03:57 LinuxServerName mysqld[2731]: stack trace is much more helpful in diagnosing the problem, so please do 
Apr 16 10:03:57 LinuxServerName mysqld[2731]: resolve it
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Trying to get some variables.
Apr 16 10:03:57 LinuxServerName mysqld[2731]: Some pointers may be invalid and cause the dump to abort...
Apr 16 10:03:57 LinuxServerName mysqld[2731]: thd->query at 0x8af79a8 = SHOW STATUS LIKE 'Thread%'
Apr 16 10:03:57 LinuxServerName mysqld[2731]: thd->thread_id=7
Apr 16 10:03:57 LinuxServerName mysqld[2731]: The manual page at http://www.mysql.com/doc/en/Crashing.html contains
Apr 16 10:03:57 LinuxServerName mysqld[2731]: information that should help you find out what is causing the crash.
Apr 16 10:03:57 LinuxServerName mysqld_safe[2930]: Number of processes running now: 0
Apr 16 10:03:57 LinuxServerName mysqld_safe[2932]: restarted
Apr 16 10:03:58 LinuxServerName mysqld[2936]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ibugMl5b' (Errcode: 13)
Apr 16 10:03:58 LinuxServerName mysqld[2936]: 080416 10:03:58  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 10:03:58 LinuxServerName mysqld[2936]: 080416 10:03:58 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 10:03:58 LinuxServerName mysqld[2936]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 10:04:44 LinuxServerName ntpd[2867]: synchronized to 10.150.10.5, stratum 4
Apr 16 10:05:01 LinuxServerName CRON[2938]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:05:01 LinuxServerName CRON[2938]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:05:01 LinuxServerName CRON[2938]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:05:01 LinuxServerName CRON[2938]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:05:01 LinuxServerName CRON[2938]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:05:01 LinuxServerName CRON[2938]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:05:01 LinuxServerName CRON[2938]: Module is unknown
Apr 16 10:05:01 LinuxServerName CRON[2939]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:05:01 LinuxServerName CRON[2939]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:05:01 LinuxServerName CRON[2939]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:05:01 LinuxServerName CRON[2939]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:05:01 LinuxServerName CRON[2939]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:05:01 LinuxServerName CRON[2939]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:05:01 LinuxServerName CRON[2939]: Module is unknown
Apr 16 10:05:50 LinuxServerName init: tty4 main process (2596) killed by TERM signal
Apr 16 10:05:50 LinuxServerName init: tty5 main process (2597) killed by TERM signal
Apr 16 10:05:50 LinuxServerName init: tty3 main process (2601) killed by TERM signal
Apr 16 10:05:50 LinuxServerName init: tty6 main process (2603) killed by TERM signal
Apr 16 10:05:50 LinuxServerName init: tty2 main process (2600) killed by TERM signal
Apr 16 10:05:50 LinuxServerName init: tty1 main process (2918) killed by TERM signal
Apr 16 10:05:52 LinuxServerName mysqld[2936]: 080416 10:05:52 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 10:05:52 LinuxServerName mysqld[2936]: 
Apr 16 10:05:54 LinuxServerName mysqld[2936]: 080416 10:05:54 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 10:05:54 LinuxServerName mysqld[2936]: 
Apr 16 10:05:54 LinuxServerName mysqld_safe[3026]: ended
Apr 16 10:05:55 LinuxServerName exiting on signal 15
Apr 16 10:08:10 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:08:10 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:08:10 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:08:10 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:08:10 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Detected 3390.989 MHz processor.
Apr 16 10:08:10 LinuxServerName kernel: [82806.186403] Built 1 zonelists.  Total pages: 130048
Apr 16 10:08:10 LinuxServerName kernel: [82806.186595] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:08:10 LinuxServerName kernel: [82806.187451] mapped APIC to ffffd000 (fee00000)
Apr 16 10:08:10 LinuxServerName kernel: [82806.187514] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 10:08:10 LinuxServerName kernel: [82806.187906] Enabling fast FPU save and restore... done.
Apr 16 10:08:10 LinuxServerName kernel: [82806.187985] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:08:10 LinuxServerName kernel: [82806.188265] Initializing CPU#0
Apr 16 10:08:10 LinuxServerName kernel: [82806.189770] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.189926] Console: colour VGA+ 80x25
Apr 16 10:08:10 LinuxServerName kernel: [82806.190082] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190237] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190393] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190448] virtual kernel memory layout:
Apr 16 10:08:10 LinuxServerName kernel: [82806.190452]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190454]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190456]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190457]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190459]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190461]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190462]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190520] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:08:10 LinuxServerName kernel: [82806.339301] Calibrating delay using timer specific routine.. 6797.38 BogoMIPS (lpj=33986903)
Apr 16 10:08:10 LinuxServerName kernel: [82806.339457] Security Framework v1.0.0 initialized
Apr 16 10:08:10 LinuxServerName kernel: [82806.339613] SELinux:  Disabled at boot.
Apr 16 10:08:10 LinuxServerName kernel: [82806.339768] Mount-cache hash table entries: 512
Apr 16 10:08:10 LinuxServerName kernel: [82806.339924] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 10:08:10 LinuxServerName kernel: [82806.340080] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:08:10 LinuxServerName kernel: [82806.340128] CPU: L2 cache: 1024K
Apr 16 10:08:10 LinuxServerName kernel: [82806.340150] CPU: L3 cache: 16384K
Apr 16 10:08:10 LinuxServerName kernel: [82806.340306] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 10:08:10 LinuxServerName kernel: [82806.340461] Compat vDSO mapped to ffffe000.
Apr 16 10:08:10 LinuxServerName kernel: [82806.340515] Remapping vsyscall page to ffffe000
Apr 16 10:08:10 LinuxServerName kernel: [82806.340671] Checking 'hlt' instruction... OK.
Apr 16 10:08:10 LinuxServerName kernel: [82806.379267] SMP alternatives: switching to UP code
Apr 16 10:08:10 LinuxServerName kernel: [82806.379423] Freeing SMP alternatives: 11k freed
Apr 16 10:08:10 LinuxServerName kernel: [82806.379578] Early unpacking initramfs... done
Apr 16 10:08:10 LinuxServerName kernel: [82806.568681] ACPI: Core revision 20060707
Apr 16 10:08:10 LinuxServerName kernel: [82806.568837] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:08:10 LinuxServerName kernel: [82806.569460] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:08:10 LinuxServerName kernel: [82806.569616] Total of 1 processors activated (6797.38 BogoMIPS).
Apr 16 10:08:10 LinuxServerName kernel: [82806.569772] ENABLING IO-APIC IRQs
Apr 16 10:08:10 LinuxServerName kernel: [82806.570183] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Brought up 1 CPUs
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Booting paravirtualized kernel on bare hardware
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Time: 14:08:04  Date: 03/16/108
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] NET: Registered protocol family 16
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] EISA bus registered
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] ACPI: bus type pci registered
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] PCI: Using configuration type 1
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Setting up standard PCI resources
Apr 16 10:08:10 LinuxServerName kernel: [82806.787996] ACPI: Interpreter enabled
Apr 16 10:08:10 LinuxServerName kernel: [82806.788036] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:08:10 LinuxServerName kernel: [82806.789681] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:08:10 LinuxServerName kernel: [82806.789837] PCI: Probing PCI hardware (bus 00)
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] Boot video device is 0000:00:0f.0
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.801896] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:08:10 LinuxServerName kernel: [82806.801976] pnp: PnP ACPI init
Apr 16 10:08:10 LinuxServerName kernel: [82806.812409] pnp: PnP ACPI: found 12 devices
Apr 16 10:08:10 LinuxServerName kernel: [82806.812501] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:08:10 LinuxServerName kernel: [82806.812811] PCI: Using ACPI for IRQ routing
Apr 16 10:08:10 LinuxServerName kernel: [82806.812943] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NET: Registered protocol family 8
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NET: Registered protocol family 20
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel: Initializing
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel:  domain hash size = 128
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] PCI: Bridge: 0000:00:01.0
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717]   IO window: disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717]   MEM window: disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717]   PREFETCH window: disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NET: Registered protocol family 2
Apr 16 10:08:10 LinuxServerName kernel: [82806.927631] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.927787] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.927942] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.928098] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:08:10 LinuxServerName kernel: [82806.928197] TCP reno registered
Apr 16 10:08:10 LinuxServerName kernel: [82806.957499] checking if image is initramfs... it is
Apr 16 10:08:10 LinuxServerName kernel: [82807.366220] Freeing initrd memory: 6642k freed
Apr 16 10:08:10 LinuxServerName kernel: [82807.366887] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:08:10 LinuxServerName kernel: [82807.368535] audit: initializing netlink socket (disabled)
Apr 16 10:08:10 LinuxServerName kernel: [82807.368691] audit(1208354885.040:1): initialized
Apr 16 10:08:10 LinuxServerName kernel: [82807.369715] VFS: Disk quotas dquot_6.5.1
Apr 16 10:08:10 LinuxServerName kernel: [82807.369845] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82807.370001] io scheduler noop registered
Apr 16 10:08:10 LinuxServerName kernel: [82807.370088] io scheduler anticipatory registered
Apr 16 10:08:10 LinuxServerName kernel: [82807.370101] io scheduler deadline registered (default)
Apr 16 10:08:10 LinuxServerName kernel: [82807.370217] io scheduler cfq registered
Apr 16 10:08:10 LinuxServerName kernel: [82807.370373] Limiting direct PCI/PCI transfers.
Apr 16 10:08:10 LinuxServerName kernel: [82807.371070] isapnp: Scanning for PnP cards...
Apr 16 10:08:10 LinuxServerName kernel: [82807.728175] isapnp: No Plug & Play device found
Apr 16 10:08:10 LinuxServerName kernel: [82807.767514] Real Time Clock Driver v1.12ac
Apr 16 10:08:10 LinuxServerName kernel: [82807.767735] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:08:10 LinuxServerName kernel: [82807.768100] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.768470] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.769761] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.770348] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.770998] mice: PS/2 mouse device common for all mice
Apr 16 10:08:10 LinuxServerName kernel: [82807.772839] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:08:10 LinuxServerName kernel: [82808.284578] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:08:10 LinuxServerName kernel: [82808.284706] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:08:10 LinuxServerName kernel: [82808.286495] EISA: Probing bus 0 at eisa.0
Apr 16 10:08:10 LinuxServerName kernel: [82808.286780] Cannot allocate resource for EISA slot 1
Apr 16 10:08:10 LinuxServerName kernel: [82808.286935] EISA: Detected 0 cards.
Apr 16 10:08:10 LinuxServerName kernel: [82808.317191] TCP cubic registered
Apr 16 10:08:10 LinuxServerName kernel: [82808.317236] NET: Registered protocol family 1
Apr 16 10:08:10 LinuxServerName kernel: [82808.317391] Using IPI No-Shortcut mode
Apr 16 10:08:10 LinuxServerName kernel: [82808.317963] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:08:10 LinuxServerName kernel: [82808.318118]   Magic number: 4:737:131
Apr 16 10:08:10 LinuxServerName kernel: [82808.323113] Freeing unused kernel memory: 332k freed
Apr 16 10:08:10 LinuxServerName kernel: [82808.323113] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:08:10 LinuxServerName kernel: [82808.323256] Time: tsc clocksource has been installed.
Apr 16 10:08:10 LinuxServerName kernel: [82808.494399] Capability LSM initialized
Apr 16 10:08:10 LinuxServerName kernel: [82808.524050] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:08:10 LinuxServerName kernel: [82808.524205] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:08:10 LinuxServerName kernel: [82808.524355] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:08:10 LinuxServerName kernel: [82808.524398] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:08:10 LinuxServerName kernel: [82809.123447] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:08:10 LinuxServerName kernel: [82809.123603] PIIX4: chipset revision 1
Apr 16 10:08:10 LinuxServerName kernel: [82809.123669] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:08:10 LinuxServerName kernel: [82809.123825]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:08:10 LinuxServerName kernel: [82809.123981] Probing IDE interface ide0...
Apr 16 10:08:10 LinuxServerName kernel: [82809.143560] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:08:10 LinuxServerName kernel: [82809.176888] SCSI subsystem initialized
Apr 16 10:08:10 LinuxServerName kernel: [82809.177469] Fusion MPT base driver 3.04.03
Apr 16 10:08:10 LinuxServerName kernel: [82809.177494] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:08:10 LinuxServerName kernel: [82809.178064] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:08:10 LinuxServerName kernel: [82809.194890] Floppy drive(s): fd0 is 1.44M
Apr 16 10:08:10 LinuxServerName kernel: [82809.221272] FDC 0 is a post-1991 82077
Apr 16 10:08:10 LinuxServerName kernel: [82810.008089] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:08:10 LinuxServerName kernel: [82810.397237] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:08:10 LinuxServerName kernel: [82810.399310] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 10:08:10 LinuxServerName kernel: [82810.399466] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 10:08:10 LinuxServerName kernel: [82810.399777] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:08:10 LinuxServerName kernel: [82810.399933] pcnet32: 1 cards_found.
Apr 16 10:08:10 LinuxServerName kernel: [82810.400336] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 10:08:10 LinuxServerName kernel: [82810.400492] mptbase: Initiating ioc0 bringup
Apr 16 10:08:10 LinuxServerName kernel: [82810.666064] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:08:10 LinuxServerName kernel: [82811.144813] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: Beginning Domain Validation
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: Ending Domain Validation
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:08:10 LinuxServerName kernel: [82811.557546] libata version 2.20 loaded.
Apr 16 10:08:10 LinuxServerName kernel: [82811.578462] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82811.578617] sda: test WP failed, assume Write Enabled
Apr 16 10:08:10 LinuxServerName kernel: [82811.578773] sda: cache data unavailable
Apr 16 10:08:10 LinuxServerName kernel: [82811.578802] sda: assuming drive cache: write through
Apr 16 10:08:10 LinuxServerName kernel: [82811.578958] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82811.579049] sda: test WP failed, assume Write Enabled
Apr 16 10:08:10 LinuxServerName kernel: [82811.579084] sda: cache data unavailable
Apr 16 10:08:10 LinuxServerName kernel: [82811.579087] sda: assuming drive cache: write through
Apr 16 10:08:10 LinuxServerName kernel: [82811.579243]  sda: sda1 sda2 < sda5 >
Apr 16 10:08:10 LinuxServerName kernel: [82811.583644] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:08:10 LinuxServerName kernel: [82811.588073] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:08:10 LinuxServerName kernel: [82811.588229] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:08:10 LinuxServerName kernel: [82811.607070] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:08:10 LinuxServerName kernel: [82811.759279] Attempting manual resume
Apr 16 10:08:10 LinuxServerName kernel: [82811.759314] swsusp: Resume From Partition 8:5
Apr 16 10:08:10 LinuxServerName kernel: [82811.759470] PM: Checking swsusp image.
Apr 16 10:08:10 LinuxServerName kernel: [82811.760126] PM: Resume from disk failed.
Apr 16 10:08:10 LinuxServerName kernel: [82811.775242] kjournald starting.  Commit interval 5 seconds
Apr 16 10:08:10 LinuxServerName kernel: [82811.775534] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:08:10 LinuxServerName kernel: [82812.022477] parport: PnPBIOS parport detected.
Apr 16 10:08:10 LinuxServerName kernel: [82812.022633] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:08:10 LinuxServerName kernel: [82812.121896] lp0: using parport0 (interrupt-driven).
Apr 16 10:08:10 LinuxServerName kernel: [82812.143018] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:08:10 LinuxServerName kernel: [82812.172504] EXT3 FS on sda1, internal journal
Apr 16 10:08:10 LinuxServerName kernel: [82812.241206] eth0: link up
Apr 16 10:08:10 LinuxServerName kernel: [82813.348921] NET: Registered protocol family 10
Apr 16 10:08:10 LinuxServerName kernel: [82813.349077] lo: Disabled Privacy Extensions
Apr 16 10:08:10 LinuxServerName mysqld_safe[2628]: started
Apr 16 10:08:10 LinuxServerName mysqld[2632]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ibclmcOQ' (Errcode: 13)
Apr 16 10:08:10 LinuxServerName mysqld[2632]: 080416 10:08:10  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 10:08:10 LinuxServerName mysqld[2632]: 080416 10:08:10 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 10:08:10 LinuxServerName mysqld[2632]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 10:08:11 LinuxServerName /etc/mysql/debian-start[2659]: Upgrading MySQL tables if necessary.
Apr 16 10:08:11 LinuxServerName slapd[2676]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 10:08:11 LinuxServerName /etc/mysql/debian-start[2678]: Checking for crashed MySQL tables.
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:08:11 LinuxServerName mysqld[2632]: 080416 10:08:11 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:08:12 LinuxServerName mysqld[2632]: 080416 10:08:12 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:08:12 LinuxServerName ntpd[2753]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Apr 16 10:08:12 LinuxServerName ntpd[2754]: precision = 2.000 usec
Apr 16 10:08:12 LinuxServerName ntpd[2754]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Apr 16 10:08:12 LinuxServerName ntpd[2754]: Listening on interface wildcard, ::#123 Disabled
Apr 16 10:08:12 LinuxServerName ntpd[2754]: Listening on interface lo, ::1#123 Enabled
Apr 16 10:08:12 LinuxServerName ntpd[2754]: Listening on interface eth0, fe80::250:56ff:fe88:27a#123 Enabled
Apr 16 10:08:12 LinuxServerName ntpd[2754]: Listening on interface lo, 127.0.0.1#123 Enabled
Apr 16 10:08:12 LinuxServerName ntpd[2754]: Listening on interface eth0, 10.150.46.10#123 Enabled
Apr 16 10:08:12 LinuxServerName ntpd[2754]: kernel time sync status 0040
Apr 16 10:08:12 LinuxServerName ntpd[2754]: frequency initialized -109.201 PPM from /var/lib/ntp/ntp.drift
Apr 16 10:08:12 LinuxServerName atd[2760]: Error redirecting I/O: Permission denied
Apr 16 10:08:12 LinuxServerName /usr/sbin/cron[2764]: (CRON) INFO (pidfile fd = 3)
Apr 16 10:08:12 LinuxServerName /usr/sbin/cron[2765]: (CRON) STARTUP (fork ok)
Apr 16 10:08:12 LinuxServerName /usr/sbin/cron[2765]: (CRON) INFO (Running @reboot jobs)
Apr 16 10:08:14 LinuxServerName ntpd_initres[2761]: host name not found: ah-dc1.na.takatacorp.com
Apr 16 10:08:14 LinuxServerName ntpd_initres[2761]: couldn't resolve `ah-dc1.na.takatacorp.com', giving up on it
Apr 16 10:08:19 LinuxServerName kernel: [82823.775603] eth0: no IPv6 routers present
Apr 16 10:09:01 LinuxServerName CRON[2798]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:09:01 LinuxServerName CRON[2798]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:09:01 LinuxServerName CRON[2798]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:09:01 LinuxServerName CRON[2798]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:09:01 LinuxServerName CRON[2798]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:09:01 LinuxServerName CRON[2798]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:09:01 LinuxServerName CRON[2798]: Module is unknown
Apr 16 10:09:52 LinuxServerName init: tty1 main process (2513) terminated with status 1
Apr 16 10:09:52 LinuxServerName init: tty1 main process ended, respawning
Apr 16 10:10:01 LinuxServerName CRON[2800]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:10:01 LinuxServerName CRON[2800]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:10:01 LinuxServerName CRON[2800]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:10:01 LinuxServerName CRON[2800]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:10:01 LinuxServerName CRON[2800]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:10:01 LinuxServerName CRON[2800]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:10:01 LinuxServerName CRON[2800]: Module is unknown
Apr 16 10:10:01 LinuxServerName CRON[2801]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:10:01 LinuxServerName CRON[2801]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:10:01 LinuxServerName CRON[2801]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:10:01 LinuxServerName CRON[2801]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:10:01 LinuxServerName CRON[2801]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:10:01 LinuxServerName CRON[2801]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:10:01 LinuxServerName CRON[2801]: Module is unknown
Apr 16 10:10:07 LinuxServerName init: tty1 main process (2799) terminated with status 1
Apr 16 10:10:07 LinuxServerName init: tty1 main process ended, respawning
Apr 16 10:10:11 LinuxServerName init: tty1 main process (2802) killed by TERM signal
Apr 16 10:10:11 LinuxServerName init: tty4 main process (2506) killed by TERM signal
Apr 16 10:10:11 LinuxServerName init: tty5 main process (2507) killed by TERM signal
Apr 16 10:10:11 LinuxServerName init: tty2 main process (2510) killed by TERM signal
Apr 16 10:10:11 LinuxServerName init: tty3 main process (2512) killed by TERM signal
Apr 16 10:10:11 LinuxServerName init: tty6 main process (2514) killed by TERM signal
Apr 16 10:10:13 LinuxServerName mysqld[2632]: 080416 10:10:13 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 10:10:13 LinuxServerName mysqld[2632]: 
Apr 16 10:10:13 LinuxServerName mysqld[2632]: 080416 10:10:13 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 10:10:13 LinuxServerName mysqld[2632]: 
Apr 16 10:10:13 LinuxServerName mysqld_safe[2878]: ended
Apr 16 10:10:14 LinuxServerName exiting on signal 15
Apr 16 10:19:04 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:18:58 LinuxServerName ntpdate[2385]: step time server 10.150.10.5 offset -5.618783 sec
Apr 16 10:18:58 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:18:58 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:18:58 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:18:58 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Detected 3390.974 MHz processor.
Apr 16 10:18:58 LinuxServerName kernel: [83452.209685] Built 1 zonelists.  Total pages: 130048
Apr 16 10:18:58 LinuxServerName kernel: [83452.209859] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:18:58 LinuxServerName kernel: [83452.210714] mapped APIC to ffffd000 (fee00000)
Apr 16 10:18:58 LinuxServerName kernel: [83452.210777] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 10:18:58 LinuxServerName kernel: [83452.211149] Enabling fast FPU save and restore... done.
Apr 16 10:18:58 LinuxServerName kernel: [83452.211214] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:18:58 LinuxServerName kernel: [83452.211514] Initializing CPU#0
Apr 16 10:18:58 LinuxServerName kernel: [83452.212989] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213145] Console: colour VGA+ 80x25
Apr 16 10:18:58 LinuxServerName kernel: [83452.213301] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213457] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213613] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213669] virtual kernel memory layout:
Apr 16 10:18:58 LinuxServerName kernel: [83452.213673]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213676]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213677]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213679]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213680]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213682]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213683]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213737] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:18:58 LinuxServerName kernel: [83452.362504] Calibrating delay using timer specific routine.. 6796.41 BogoMIPS (lpj=33982087)
Apr 16 10:18:58 LinuxServerName kernel: [83452.362660] Security Framework v1.0.0 initialized
Apr 16 10:18:58 LinuxServerName kernel: [83452.362816] SELinux:  Disabled at boot.
Apr 16 10:18:58 LinuxServerName kernel: [83452.362972] Mount-cache hash table entries: 512
Apr 16 10:18:58 LinuxServerName kernel: [83452.363127] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 10:18:58 LinuxServerName kernel: [83452.363283] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:18:58 LinuxServerName kernel: [83452.363331] CPU: L2 cache: 1024K
Apr 16 10:18:58 LinuxServerName kernel: [83452.363353] CPU: L3 cache: 16384K
Apr 16 10:18:58 LinuxServerName kernel: [83452.363509] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 10:18:58 LinuxServerName kernel: [83452.363664] Compat vDSO mapped to ffffe000.
Apr 16 10:18:58 LinuxServerName kernel: [83452.363720] Remapping vsyscall page to ffffe000
Apr 16 10:18:58 LinuxServerName kernel: [83452.363875] Checking 'hlt' instruction... OK.
Apr 16 10:18:58 LinuxServerName kernel: [83452.402493] SMP alternatives: switching to UP code
Apr 16 10:18:58 LinuxServerName kernel: [83452.402648] Freeing SMP alternatives: 11k freed
Apr 16 10:18:58 LinuxServerName kernel: [83452.402804] Early unpacking initramfs... done
Apr 16 10:18:58 LinuxServerName kernel: [83452.591905] ACPI: Core revision 20060707
Apr 16 10:18:58 LinuxServerName kernel: [83452.592061] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:18:58 LinuxServerName kernel: [83452.592684] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:18:58 LinuxServerName kernel: [83452.592840] Total of 1 processors activated (6796.41 BogoMIPS).
Apr 16 10:18:58 LinuxServerName kernel: [83452.592995] ENABLING IO-APIC IRQs
Apr 16 10:18:58 LinuxServerName kernel: [83452.593407] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Brought up 1 CPUs
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Booting paravirtualized kernel on bare hardware
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Time: 14:18:51  Date: 03/16/108
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] NET: Registered protocol family 16
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] EISA bus registered
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] ACPI: bus type pci registered
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] PCI: Using configuration type 1
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Setting up standard PCI resources
Apr 16 10:18:58 LinuxServerName kernel: [83452.811219] ACPI: Interpreter enabled
Apr 16 10:18:58 LinuxServerName kernel: [83452.811258] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:18:58 LinuxServerName kernel: [83452.812910] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:18:58 LinuxServerName kernel: [83452.813056] PCI: Probing PCI hardware (bus 00)
Apr 16 10:18:58 LinuxServerName kernel: [83452.813667] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:18:58 LinuxServerName kernel: [83452.813745] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:18:58 LinuxServerName kernel: [83452.813901] Boot video device is 0000:00:0f.0
Apr 16 10:18:58 LinuxServerName kernel: [83452.814304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 10:18:58 LinuxServerName kernel: [83452.817044] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.817364] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:18:58 LinuxServerName kernel: [83452.817685] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:18:58 LinuxServerName kernel: [83452.818004] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.825217] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:18:58 LinuxServerName kernel: [83452.825310] pnp: PnP ACPI init
Apr 16 10:18:58 LinuxServerName kernel: [83452.835511] pnp: PnP ACPI: found 12 devices
Apr 16 10:18:58 LinuxServerName kernel: [83452.835604] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:18:58 LinuxServerName kernel: [83452.835925] PCI: Using ACPI for IRQ routing
Apr 16 10:18:58 LinuxServerName kernel: [83452.836039] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NET: Registered protocol family 8
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NET: Registered protocol family 20
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel: Initializing
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel:  domain hash size = 128
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] PCI: Bridge: 0000:00:01.0
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940]   IO window: disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940]   MEM window: disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940]   PREFETCH window: disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NET: Registered protocol family 2
Apr 16 10:18:58 LinuxServerName kernel: [83452.950864] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951020] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951175] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951331] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951439] TCP reno registered
Apr 16 10:18:58 LinuxServerName kernel: [83452.980715] checking if image is initramfs... it is
Apr 16 10:18:58 LinuxServerName kernel: [83453.379469] Freeing initrd memory: 6642k freed
Apr 16 10:18:58 LinuxServerName kernel: [83453.380146] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:18:58 LinuxServerName kernel: [83453.381779] audit: initializing netlink socket (disabled)
Apr 16 10:18:58 LinuxServerName kernel: [83453.381935] audit(1208355532.030:1): initialized
Apr 16 10:18:58 LinuxServerName kernel: [83453.382941] VFS: Disk quotas dquot_6.5.1
Apr 16 10:18:58 LinuxServerName kernel: [83453.383082] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83453.383238] io scheduler noop registered
Apr 16 10:18:58 LinuxServerName kernel: [83453.383324] io scheduler anticipatory registered
Apr 16 10:18:58 LinuxServerName kernel: [83453.383337] io scheduler deadline registered (default)
Apr 16 10:18:58 LinuxServerName kernel: [83453.383456] io scheduler cfq registered
Apr 16 10:18:58 LinuxServerName kernel: [83453.383612] Limiting direct PCI/PCI transfers.
Apr 16 10:18:58 LinuxServerName kernel: [83453.384318] isapnp: Scanning for PnP cards...
Apr 16 10:18:58 LinuxServerName kernel: [83453.741022] isapnp: No Plug & Play device found
Apr 16 10:18:58 LinuxServerName kernel: [83453.779451] Real Time Clock Driver v1.12ac
Apr 16 10:18:58 LinuxServerName kernel: [83453.779660] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:18:58 LinuxServerName kernel: [83453.780023] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.780392] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.781559] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.782173] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.782836] mice: PS/2 mouse device common for all mice
Apr 16 10:18:58 LinuxServerName kernel: [83453.785034] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:18:58 LinuxServerName kernel: [83454.299887] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:18:58 LinuxServerName kernel: [83454.300014] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:18:58 LinuxServerName kernel: [83454.301846] EISA: Probing bus 0 at eisa.0
Apr 16 10:18:58 LinuxServerName kernel: [83454.302153] Cannot allocate resource for EISA slot 1
Apr 16 10:18:58 LinuxServerName kernel: [83454.302309] EISA: Detected 0 cards.
Apr 16 10:18:58 LinuxServerName kernel: [83454.332560] TCP cubic registered
Apr 16 10:18:58 LinuxServerName kernel: [83454.332605] NET: Registered protocol family 1
Apr 16 10:18:58 LinuxServerName kernel: [83454.332761] Using IPI No-Shortcut mode
Apr 16 10:18:58 LinuxServerName kernel: [83454.333528] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:18:58 LinuxServerName kernel: [83454.333839]   Magic number: 4:943:333
Apr 16 10:18:58 LinuxServerName kernel: [83454.333995]   hash matches device tty54
Apr 16 10:18:58 LinuxServerName kernel: [83454.336367] Freeing unused kernel memory: 332k freed
Apr 16 10:18:58 LinuxServerName kernel: [83454.336367] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:18:58 LinuxServerName kernel: [83454.336492] Time: tsc clocksource has been installed.
Apr 16 10:18:58 LinuxServerName kernel: [83454.507612] Capability LSM initialized
Apr 16 10:18:58 LinuxServerName kernel: [83454.537836] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:18:58 LinuxServerName kernel: [83454.537991] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:18:58 LinuxServerName kernel: [83454.538147] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:18:58 LinuxServerName kernel: [83454.538190] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:18:58 LinuxServerName kernel: [83455.136672] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:18:58 LinuxServerName kernel: [83455.136828] PIIX4: chipset revision 1
Apr 16 10:18:58 LinuxServerName kernel: [83455.136893] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:18:58 LinuxServerName kernel: [83455.137049]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:18:58 LinuxServerName kernel: [83455.137205] Probing IDE interface ide0...
Apr 16 10:18:58 LinuxServerName kernel: [83455.156818] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:18:58 LinuxServerName kernel: [83455.190056] SCSI subsystem initialized
Apr 16 10:18:58 LinuxServerName kernel: [83455.190602] Fusion MPT base driver 3.04.03
Apr 16 10:18:58 LinuxServerName kernel: [83455.190625] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:18:58 LinuxServerName kernel: [83455.191166] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:18:58 LinuxServerName kernel: [83455.207358] Floppy drive(s): fd0 is 1.44M
Apr 16 10:18:58 LinuxServerName kernel: [83455.234540] FDC 0 is a post-1991 82077
Apr 16 10:18:58 LinuxServerName kernel: [83456.041282] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:18:58 LinuxServerName kernel: [83456.440396] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:18:58 LinuxServerName kernel: [83456.442338] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 10:18:58 LinuxServerName kernel: [83456.442493] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 10:18:58 LinuxServerName kernel: [83456.442805] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:18:58 LinuxServerName kernel: [83456.442961] pcnet32: 1 cards_found.
Apr 16 10:18:58 LinuxServerName kernel: [83456.443357] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 10:18:58 LinuxServerName kernel: [83456.443513] mptbase: Initiating ioc0 bringup
Apr 16 10:18:58 LinuxServerName kernel: [83456.709061] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:18:58 LinuxServerName kernel: [83457.178011] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: Beginning Domain Validation
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: Ending Domain Validation
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:18:58 LinuxServerName kernel: [83457.530813] libata version 2.20 loaded.
Apr 16 10:18:58 LinuxServerName kernel: [83457.551907] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83457.552063] sda: test WP failed, assume Write Enabled
Apr 16 10:18:58 LinuxServerName kernel: [83457.552219] sda: cache data unavailable
Apr 16 10:18:58 LinuxServerName kernel: [83457.552247] sda: assuming drive cache: write through
Apr 16 10:18:58 LinuxServerName kernel: [83457.552403] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83457.552493] sda: test WP failed, assume Write Enabled
Apr 16 10:18:58 LinuxServerName kernel: [83457.552524] sda: cache data unavailable
Apr 16 10:18:58 LinuxServerName kernel: [83457.552527] sda: assuming drive cache: write through
Apr 16 10:18:58 LinuxServerName kernel: [83457.552680]  sda: sda1 sda2 < sda5 >
Apr 16 10:18:58 LinuxServerName kernel: [83457.558264] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:18:58 LinuxServerName kernel: [83457.561121] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:18:58 LinuxServerName kernel: [83457.561277] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:18:58 LinuxServerName kernel: [83457.580382] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:18:58 LinuxServerName kernel: [83457.732538] Attempting manual resume
Apr 16 10:18:58 LinuxServerName kernel: [83457.732572] swsusp: Resume From Partition 8:5
Apr 16 10:18:58 LinuxServerName kernel: [83457.732598] PM: Checking swsusp image.
Apr 16 10:18:58 LinuxServerName kernel: [83457.733234] PM: Resume from disk failed.
Apr 16 10:18:58 LinuxServerName kernel: [83457.747055] kjournald starting.  Commit interval 5 seconds
Apr 16 10:18:58 LinuxServerName kernel: [83457.747354] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:18:58 LinuxServerName kernel: [83458.128205] parport: PnPBIOS parport detected.
Apr 16 10:18:58 LinuxServerName kernel: [83458.128361] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:18:58 LinuxServerName kernel: [83458.224832] lp0: using parport0 (interrupt-driven).
Apr 16 10:18:58 LinuxServerName kernel: [83458.285127] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:18:58 LinuxServerName kernel: [83458.310761] EXT3 FS on sda1, internal journal
Apr 16 10:18:58 LinuxServerName kernel: [83458.384061] eth0: link up
Apr 16 10:18:58 LinuxServerName kernel: [83459.500887] NET: Registered protocol family 10
Apr 16 10:18:58 LinuxServerName kernel: [83459.501043] lo: Disabled Privacy Extensions
Apr 16 10:18:58 LinuxServerName mysqld_safe[2629]: started
Apr 16 10:18:58 LinuxServerName mysqld[2633]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ibX4vQH6' (Errcode: 13)
Apr 16 10:18:58 LinuxServerName mysqld[2633]: 080416 10:18:58  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 10:18:58 LinuxServerName mysqld[2633]: 080416 10:18:58 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 10:18:58 LinuxServerName mysqld[2633]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 10:18:59 LinuxServerName /etc/mysql/debian-start[2660]: Upgrading MySQL tables if necessary.
Apr 16 10:18:59 LinuxServerName slapd[2676]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 10:19:00 LinuxServerName /etc/mysql/debian-start[2696]: Checking for crashed MySQL tables.
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:19:00 LinuxServerName mysqld[2633]: 080416 10:19:00 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:19:00 LinuxServerName ntpd[2753]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Apr 16 10:19:00 LinuxServerName ntpd[2754]: precision = 2.000 usec
Apr 16 10:19:00 LinuxServerName ntpd[2754]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Apr 16 10:19:00 LinuxServerName ntpd[2754]: Listening on interface wildcard, ::#123 Disabled
Apr 16 10:19:00 LinuxServerName ntpd[2754]: Listening on interface lo, ::1#123 Enabled
Apr 16 10:19:00 LinuxServerName ntpd[2754]: Listening on interface eth0, fe80::250:56ff:fe88:27a#123 Enabled
Apr 16 10:19:00 LinuxServerName ntpd[2754]: Listening on interface lo, 127.0.0.1#123 Enabled
Apr 16 10:19:00 LinuxServerName ntpd[2754]: Listening on interface eth0, 10.150.46.10#123 Enabled
Apr 16 10:19:00 LinuxServerName ntpd[2754]: kernel time sync status 0040
Apr 16 10:19:00 LinuxServerName ntpd[2754]: frequency initialized -109.201 PPM from /var/lib/ntp/ntp.drift
Apr 16 10:19:00 LinuxServerName atd[2760]: Error redirecting I/O: Permission denied
Apr 16 10:19:00 LinuxServerName /usr/sbin/cron[2764]: (CRON) INFO (pidfile fd = 3)
Apr 16 10:19:00 LinuxServerName /usr/sbin/cron[2765]: (CRON) STARTUP (fork ok)
Apr 16 10:19:00 LinuxServerName /usr/sbin/cron[2765]: (CRON) INFO (Running @reboot jobs)
Apr 16 10:19:02 LinuxServerName ntpd_initres[2761]: host name not found: ah-dc1.na.takatacorp.com
Apr 16 10:19:02 LinuxServerName ntpd_initres[2761]: couldn't resolve `ah-dc1.na.takatacorp.com', giving up on it
Apr 16 10:19:08 LinuxServerName kernel: [83470.367094] eth0: no IPv6 routers present
Apr 16 10:19:37 LinuxServerName init: tty1 main process (2514) terminated with status 1
Apr 16 10:19:37 LinuxServerName init: tty1 main process ended, respawning
Apr 16 10:19:40 LinuxServerName init: tty4 main process (2507) killed by TERM signal
Apr 16 10:19:40 LinuxServerName init: tty5 main process (2508) killed by TERM signal
Apr 16 10:19:40 LinuxServerName init: tty2 main process (2511) killed by TERM signal
Apr 16 10:19:40 LinuxServerName init: tty3 main process (2513) killed by TERM signal
Apr 16 10:19:40 LinuxServerName init: tty6 main process (2515) killed by TERM signal
Apr 16 10:19:40 LinuxServerName init: tty1 main process (2797) killed by TERM signal
Apr 16 10:19:42 LinuxServerName mysqld[2633]: 080416 10:19:42 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 10:19:42 LinuxServerName mysqld[2633]: 
Apr 16 10:19:44 LinuxServerName mysqld[2633]: 080416 10:19:44 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 10:19:44 LinuxServerName mysqld[2633]: 
Apr 16 10:19:44 LinuxServerName mysqld_safe[2873]: ended
Apr 16 10:19:46 LinuxServerName exiting on signal 15
Apr 16 10:24:16 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:24:16 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:24:16 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:24:16 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:24:16 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Detected 3390.917 MHz processor.
Apr 16 10:24:16 LinuxServerName kernel: [83520.999838] Built 1 zonelists.  Total pages: 130048
Apr 16 10:24:16 LinuxServerName kernel: [83521.000020] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:24:16 LinuxServerName kernel: [83521.000875] mapped APIC to ffffd000 (fee00000)
Apr 16 10:24:16 LinuxServerName kernel: [83521.000938] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 10:24:16 LinuxServerName kernel: [83521.001323] Enabling fast FPU save and restore... done.
Apr 16 10:24:16 LinuxServerName kernel: [83521.001388] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:24:16 LinuxServerName kernel: [83521.001677] Initializing CPU#0
Apr 16 10:24:16 LinuxServerName kernel: [83521.003172] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013372] Console: colour VGA+ 80x25
Apr 16 10:24:16 LinuxServerName kernel: [83521.013528] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013683] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013839] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013894] virtual kernel memory layout:
Apr 16 10:24:16 LinuxServerName kernel: [83521.013898]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013900]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013902]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013903]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013905]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013906]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013908]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013962] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:24:16 LinuxServerName kernel: [83521.162680] Calibrating delay using timer specific routine.. 6808.28 BogoMIPS (lpj=34041410)
Apr 16 10:24:16 LinuxServerName kernel: [83521.162836] Security Framework v1.0.0 initialized
Apr 16 10:24:16 LinuxServerName kernel: [83521.162992] SELinux:  Disabled at boot.
Apr 16 10:24:16 LinuxServerName kernel: [83521.163148] Mount-cache hash table entries: 512
Apr 16 10:24:16 LinuxServerName kernel: [83521.163303] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 10:24:16 LinuxServerName kernel: [83521.163459] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:24:16 LinuxServerName kernel: [83521.163506] CPU: L2 cache: 1024K
Apr 16 10:24:16 LinuxServerName kernel: [83521.163528] CPU: L3 cache: 16384K
Apr 16 10:24:16 LinuxServerName kernel: [83521.163684] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 10:24:16 LinuxServerName kernel: [83521.163840] Compat vDSO mapped to ffffe000.
Apr 16 10:24:16 LinuxServerName kernel: [83521.163895] Remapping vsyscall page to ffffe000
Apr 16 10:24:16 LinuxServerName kernel: [83521.164051] Checking 'hlt' instruction... OK.
Apr 16 10:24:16 LinuxServerName kernel: [83521.202643] SMP alternatives: switching to UP code
Apr 16 10:24:16 LinuxServerName kernel: [83521.202798] Freeing SMP alternatives: 11k freed
Apr 16 10:24:16 LinuxServerName kernel: [83521.202954] Early unpacking initramfs... done
Apr 16 10:24:16 LinuxServerName kernel: [83521.412002] ACPI: Core revision 20060707
Apr 16 10:24:16 LinuxServerName kernel: [83521.412157] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:24:16 LinuxServerName kernel: [83521.422581] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:24:16 LinuxServerName kernel: [83521.422736] Total of 1 processors activated (6808.28 BogoMIPS).
Apr 16 10:24:16 LinuxServerName kernel: [83521.422892] ENABLING IO-APIC IRQs
Apr 16 10:24:16 LinuxServerName kernel: [83521.423304] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:24:16 LinuxServerName kernel: [83521.641126] Brought up 1 CPUs
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] Booting paravirtualized kernel on bare hardware
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] Time: 14:20:00  Date: 03/16/108
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] NET: Registered protocol family 16
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] EISA bus registered
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] ACPI: bus type pci registered
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] PCI: Using configuration type 1
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] Setting up standard PCI resources
Apr 16 10:24:16 LinuxServerName kernel: [83521.641282] ACPI: Interpreter enabled
Apr 16 10:24:16 LinuxServerName kernel: [83521.641321] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:24:16 LinuxServerName kernel: [83521.642974] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:24:16 LinuxServerName kernel: [83521.643126] PCI: Probing PCI hardware (bus 00)
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] Boot video device is 0000:00:0f.0
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.655325] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:24:16 LinuxServerName kernel: [83521.655448] pnp: PnP ACPI init
Apr 16 10:24:16 LinuxServerName kernel: [83521.665504] pnp: PnP ACPI: found 12 devices
Apr 16 10:24:16 LinuxServerName kernel: [83521.665593] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:24:16 LinuxServerName kernel: [83521.665907] PCI: Using ACPI for IRQ routing
Apr 16 10:24:16 LinuxServerName kernel: [83521.666013] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NET: Registered protocol family 8
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NET: Registered protocol family 20
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel: Initializing
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel:  domain hash size = 128
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] PCI: Bridge: 0000:00:01.0
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004]   IO window: disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004]   MEM window: disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004]   PREFETCH window: disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NET: Registered protocol family 2
Apr 16 10:24:16 LinuxServerName kernel: [83521.780904] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781060] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781216] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781372] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781470] TCP reno registered
Apr 16 10:24:16 LinuxServerName kernel: [83521.810776] checking if image is initramfs... it is
Apr 16 10:24:16 LinuxServerName kernel: [83522.219502] Freeing initrd memory: 6642k freed
Apr 16 10:24:16 LinuxServerName kernel: [83522.220184] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:24:16 LinuxServerName kernel: [83522.221849] audit: initializing netlink socket (disabled)
Apr 16 10:24:16 LinuxServerName kernel: [83522.222005] audit(1208355601.080:1): initialized
Apr 16 10:24:16 LinuxServerName kernel: [83522.223022] VFS: Disk quotas dquot_6.5.1
Apr 16 10:24:16 LinuxServerName kernel: [83522.223149] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83522.223305] io scheduler noop registered
Apr 16 10:24:16 LinuxServerName kernel: [83522.223405] io scheduler anticipatory registered
Apr 16 10:24:16 LinuxServerName kernel: [83522.223418] io scheduler deadline registered (default)
Apr 16 10:24:16 LinuxServerName kernel: [83522.223544] io scheduler cfq registered
Apr 16 10:24:16 LinuxServerName kernel: [83522.223700] Limiting direct PCI/PCI transfers.
Apr 16 10:24:16 LinuxServerName kernel: [83522.224394] isapnp: Scanning for PnP cards...
Apr 16 10:24:16 LinuxServerName kernel: [83522.581767] isapnp: No Plug & Play device found
Apr 16 10:24:16 LinuxServerName kernel: [83522.620406] Real Time Clock Driver v1.12ac
Apr 16 10:24:16 LinuxServerName kernel: [83522.620627] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:24:16 LinuxServerName kernel: [83522.620992] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.621361] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.622495] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.623018] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.623632] mice: PS/2 mouse device common for all mice
Apr 16 10:24:16 LinuxServerName kernel: [83522.625656] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:24:16 LinuxServerName kernel: [83523.137976] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:24:16 LinuxServerName kernel: [83523.138107] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:24:16 LinuxServerName kernel: [83523.139968] EISA: Probing bus 0 at eisa.0
Apr 16 10:24:16 LinuxServerName kernel: [83523.140279] Cannot allocate resource for EISA slot 1
Apr 16 10:24:16 LinuxServerName kernel: [83523.140435] EISA: Detected 0 cards.
Apr 16 10:24:16 LinuxServerName kernel: [83523.170717] TCP cubic registered
Apr 16 10:24:16 LinuxServerName kernel: [83523.170848] NET: Registered protocol family 1
Apr 16 10:24:16 LinuxServerName kernel: [83523.171004] Using IPI No-Shortcut mode
Apr 16 10:24:16 LinuxServerName kernel: [83523.171438] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:24:16 LinuxServerName kernel: [83523.172229] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:24:16 LinuxServerName kernel: [83523.172384]   Magic number: 4:943:333
Apr 16 10:24:16 LinuxServerName kernel: [83523.172540]   hash matches device tty54
Apr 16 10:24:16 LinuxServerName kernel: [83523.176400] Freeing unused kernel memory: 332k freed
Apr 16 10:24:16 LinuxServerName kernel: [83523.176527] Time: tsc clocksource has been installed.
Apr 16 10:24:16 LinuxServerName kernel: [83523.357650] Capability LSM initialized
Apr 16 10:24:16 LinuxServerName kernel: [83523.397253] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:24:16 LinuxServerName kernel: [83523.397409] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:24:16 LinuxServerName kernel: [83523.397559] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:24:16 LinuxServerName kernel: [83523.397603] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:24:16 LinuxServerName kernel: [83524.015817] SCSI subsystem initialized
Apr 16 10:24:16 LinuxServerName kernel: [83524.016433] Fusion MPT base driver 3.04.03
Apr 16 10:24:16 LinuxServerName kernel: [83524.016454] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:24:16 LinuxServerName kernel: [83524.017021] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:24:16 LinuxServerName kernel: [83524.017176] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 10:24:16 LinuxServerName kernel: [83524.017332] mptbase: Initiating ioc0 bringup
Apr 16 10:24:16 LinuxServerName kernel: [83524.018010] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:24:16 LinuxServerName kernel: [83524.056836] Floppy drive(s): fd0 is 1.44M
Apr 16 10:24:16 LinuxServerName kernel: [83524.084764] FDC 0 is a post-1991 82077
Apr 16 10:24:16 LinuxServerName kernel: [83524.293128] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:24:16 LinuxServerName kernel: [83524.761915] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: Beginning Domain Validation
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: Ending Domain Validation
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:24:16 LinuxServerName kernel: [83525.199501] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 10:24:16 LinuxServerName kernel: [83525.200334] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 10:24:16 LinuxServerName kernel: [83525.200645] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:24:16 LinuxServerName kernel: [83525.200801] pcnet32: 1 cards_found.
Apr 16 10:24:16 LinuxServerName kernel: [83525.201352] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:24:16 LinuxServerName kernel: [83525.201508] PIIX4: chipset revision 1
Apr 16 10:24:16 LinuxServerName kernel: [83525.201587] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:24:16 LinuxServerName kernel: [83525.201743]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:24:16 LinuxServerName kernel: [83525.201898] Probing IDE interface ide0...
Apr 16 10:24:16 LinuxServerName kernel: [83525.232596] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83525.232752] sda: test WP failed, assume Write Enabled
Apr 16 10:24:16 LinuxServerName kernel: [83525.232908] sda: cache data unavailable
Apr 16 10:24:16 LinuxServerName kernel: [83525.232937] sda: assuming drive cache: write through
Apr 16 10:24:16 LinuxServerName kernel: [83525.233092] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83525.233180] sda: test WP failed, assume Write Enabled
Apr 16 10:24:16 LinuxServerName kernel: [83525.233213] sda: cache data unavailable
Apr 16 10:24:16 LinuxServerName kernel: [83525.233216] sda: assuming drive cache: write through
Apr 16 10:24:16 LinuxServerName kernel: [83525.233370]  sda: sda1 sda2 < sda5 >
Apr 16 10:24:16 LinuxServerName kernel: [83525.235594] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:24:16 LinuxServerName kernel: [83525.242231] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:24:16 LinuxServerName kernel: [83525.396169] Attempting manual resume
Apr 16 10:24:16 LinuxServerName kernel: [83525.396207] swsusp: Resume From Partition 8:5
Apr 16 10:24:16 LinuxServerName kernel: [83525.396232] PM: Checking swsusp image.
Apr 16 10:24:16 LinuxServerName kernel: [83525.396874] PM: Resume from disk failed.
Apr 16 10:24:16 LinuxServerName kernel: [83525.410793] kjournald starting.  Commit interval 5 seconds
Apr 16 10:24:16 LinuxServerName kernel: [83525.411091] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:24:16 LinuxServerName kernel: [83525.669481] parport: PnPBIOS parport detected.
Apr 16 10:24:16 LinuxServerName kernel: [83525.669636] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:24:16 LinuxServerName kernel: [83526.067727] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:24:16 LinuxServerName kernel: [83526.446847] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:24:16 LinuxServerName kernel: [83526.447665] lp0: using parport0 (interrupt-driven).
Apr 16 10:24:16 LinuxServerName kernel: [83746.598820] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:24:16 LinuxServerName kernel: [83746.694108] EXT3 FS on sda1, internal journal
Apr 16 10:24:16 LinuxServerName kernel: [83746.943067] eth0: link up
Apr 16 10:24:16 LinuxServerName kernel: [83749.380356] NET: Registered protocol family 10
Apr 16 10:24:16 LinuxServerName kernel: [83749.383210] lo: Disabled Privacy Extensions
Apr 16 10:24:16 LinuxServerName kernel: [83760.223878] eth0: no IPv6 routers present
Apr 16 10:24:16 LinuxServerName mysqld_safe[2553]: started
Apr 16 10:24:17 LinuxServerName mysqld[2557]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ib4JeJGg' (Errcode: 13)
Apr 16 10:24:17 LinuxServerName mysqld[2557]: 080416 10:24:17  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 10:24:17 LinuxServerName mysqld[2557]: 080416 10:24:17 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 10:24:17 LinuxServerName mysqld[2557]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 10:24:18 LinuxServerName /etc/mysql/debian-start[2584]: Upgrading MySQL tables if necessary.
Apr 16 10:24:18 LinuxServerName slapd[2601]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 10:24:18 LinuxServerName /etc/mysql/debian-start[2602]: Checking for crashed MySQL tables.
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:24:18 LinuxServerName mysqld[2557]: 080416 10:24:18 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:24:19 LinuxServerName mysqld[2557]: 080416 10:24:19 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:24:19 LinuxServerName mysqld[2557]: 080416 10:24:19 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:24:19 LinuxServerName ntpd[2678]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Apr 16 10:24:19 LinuxServerName ntpd[2679]: precision = 2.000 usec
Apr 16 10:24:19 LinuxServerName ntpd[2679]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Apr 16 10:24:19 LinuxServerName ntpd[2679]: Listening on interface wildcard, ::#123 Disabled
Apr 16 10:24:19 LinuxServerName ntpd[2679]: Listening on interface lo, ::1#123 Enabled
Apr 16 10:24:19 LinuxServerName ntpd[2679]: Listening on interface eth0, fe80::250:56ff:fe88:27a#123 Enabled
Apr 16 10:24:19 LinuxServerName ntpd[2679]: Listening on interface lo, 127.0.0.1#123 Enabled
Apr 16 10:24:19 LinuxServerName ntpd[2679]: Listening on interface eth0, 10.150.46.10#123 Enabled
Apr 16 10:24:19 LinuxServerName ntpd[2679]: kernel time sync status 0040
Apr 16 10:24:19 LinuxServerName ntpd[2679]: frequency initialized -109.201 PPM from /var/lib/ntp/ntp.drift
Apr 16 10:24:19 LinuxServerName atd[2685]: Error redirecting I/O: Permission denied
Apr 16 10:24:19 LinuxServerName /usr/sbin/cron[2689]: (CRON) INFO (pidfile fd = 3)
Apr 16 10:24:19 LinuxServerName /usr/sbin/cron[2690]: (CRON) STARTUP (fork ok)
Apr 16 10:24:19 LinuxServerName /usr/sbin/cron[2690]: (CRON) INFO (Running @reboot jobs)
Apr 16 10:24:21 LinuxServerName ntpd_initres[2686]: host name not found: ah-dc1.na.takatacorp.com
Apr 16 10:24:21 LinuxServerName ntpd_initres[2686]: couldn't resolve `ah-dc1.na.takatacorp.com', giving up on it
Apr 16 10:24:27 LinuxServerName init: tty4 main process (2429) killed by TERM signal
Apr 16 10:24:27 LinuxServerName init: tty5 main process (2430) killed by TERM signal
Apr 16 10:24:27 LinuxServerName init: tty2 main process (2435) killed by TERM signal
Apr 16 10:24:27 LinuxServerName init: tty3 main process (2436) killed by TERM signal
Apr 16 10:24:27 LinuxServerName init: tty1 main process (2439) killed by TERM signal
Apr 16 10:24:27 LinuxServerName init: tty6 main process (2440) killed by TERM signal
Apr 16 10:24:29 LinuxServerName mysqld[2557]: 080416 10:24:29 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 10:24:29 LinuxServerName mysqld[2557]: 
Apr 16 10:24:29 LinuxServerName mysqld[2557]: 080416 10:24:29 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 10:24:29 LinuxServerName mysqld[2557]: 
Apr 16 10:24:29 LinuxServerName mysqld_safe[2797]: ended
Apr 16 10:24:30 LinuxServerName exiting on signal 15
Apr 16 10:41:38 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:41:30 LinuxServerName ntpdate[2382]: step time server 10.150.10.5 offset -7.598812 sec
Apr 16 10:41:30 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:41:44 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:41:44 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:41:44 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Detected 3390.937 MHz processor.
Apr 16 10:41:44 LinuxServerName kernel: [84800.933047] Built 1 zonelists.  Total pages: 130048
Apr 16 10:41:44 LinuxServerName kernel: [84800.933217] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:41:44 LinuxServerName kernel: [84800.934072] mapped APIC to ffffd000 (fee00000)
Apr 16 10:41:44 LinuxServerName kernel: [84800.934135] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 10:41:44 LinuxServerName kernel: [84800.934501] Enabling fast FPU save and restore... done.
Apr 16 10:41:44 LinuxServerName kernel: [84800.934568] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:41:44 LinuxServerName kernel: [84800.934858] Initializing CPU#0
Apr 16 10:41:44 LinuxServerName kernel: [84800.936331] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84800.936486] Console: colour VGA+ 80x25
Apr 16 10:41:44 LinuxServerName kernel: [84800.936642] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84800.936798] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84800.936954] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937007] virtual kernel memory layout:
Apr 16 10:41:44 LinuxServerName kernel: [84800.937012]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937014]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937016]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937017]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937019]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937020]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937022]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937077] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:41:44 LinuxServerName kernel: [84801.085857] Calibrating delay using timer specific routine.. 6807.20 BogoMIPS (lpj=34036005)
Apr 16 10:41:44 LinuxServerName kernel: [84801.086013] Security Framework v1.0.0 initialized
Apr 16 10:41:44 LinuxServerName kernel: [84801.086169] SELinux:  Disabled at boot.
Apr 16 10:41:44 LinuxServerName kernel: [84801.086325] Mount-cache hash table entries: 512
Apr 16 10:41:44 LinuxServerName kernel: [84801.086480] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 10:41:44 LinuxServerName kernel: [84801.086636] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:41:44 LinuxServerName kernel: [84801.086684] CPU: L2 cache: 1024K
Apr 16 10:41:44 LinuxServerName kernel: [84801.086706] CPU: L3 cache: 16384K
Apr 16 10:41:44 LinuxServerName kernel: [84801.086862] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 10:41:44 LinuxServerName kernel: [84801.087017] Compat vDSO mapped to ffffe000.
Apr 16 10:41:44 LinuxServerName kernel: [84801.087074] Remapping vsyscall page to ffffe000
Apr 16 10:41:44 LinuxServerName kernel: [84801.087230] Checking 'hlt' instruction... OK.
Apr 16 10:41:44 LinuxServerName kernel: [84801.125836] SMP alternatives: switching to UP code
Apr 16 10:41:44 LinuxServerName kernel: [84801.125992] Freeing SMP alternatives: 11k freed
Apr 16 10:41:44 LinuxServerName kernel: [84801.126147] Early unpacking initramfs... done
Apr 16 10:41:44 LinuxServerName kernel: [84801.335209] ACPI: Core revision 20060707
Apr 16 10:41:44 LinuxServerName kernel: [84801.335365] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:41:44 LinuxServerName kernel: [84801.335988] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:41:44 LinuxServerName kernel: [84801.336144] Total of 1 processors activated (6807.20 BogoMIPS).
Apr 16 10:41:44 LinuxServerName kernel: [84801.336300] ENABLING IO-APIC IRQs
Apr 16 10:41:44 LinuxServerName kernel: [84801.336711] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Brought up 1 CPUs
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Booting paravirtualized kernel on bare hardware
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Time: 14:41:31  Date: 03/16/108
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] NET: Registered protocol family 16
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] EISA bus registered
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] ACPI: bus type pci registered
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] PCI: Using configuration type 1
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Setting up standard PCI resources
Apr 16 10:41:44 LinuxServerName kernel: [84801.554503] ACPI: Interpreter enabled
Apr 16 10:41:44 LinuxServerName kernel: [84801.554543] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:41:44 LinuxServerName kernel: [84801.556235] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:41:44 LinuxServerName kernel: [84801.556384] PCI: Probing PCI hardware (bus 00)
Apr 16 10:41:44 LinuxServerName kernel: [84801.556997] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:41:44 LinuxServerName kernel: [84801.557091] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:41:44 LinuxServerName kernel: [84801.557246] Boot video device is 0000:00:0f.0
Apr 16 10:41:44 LinuxServerName kernel: [84801.557650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 10:41:44 LinuxServerName kernel: [84801.560443] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.560759] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:41:44 LinuxServerName kernel: [84801.561073] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:41:44 LinuxServerName kernel: [84801.561379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.568315] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:41:44 LinuxServerName kernel: [84801.568392] pnp: PnP ACPI init
Apr 16 10:41:44 LinuxServerName kernel: [84801.578738] pnp: PnP ACPI: found 12 devices
Apr 16 10:41:44 LinuxServerName kernel: [84801.578828] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:41:44 LinuxServerName kernel: [84801.579137] PCI: Using ACPI for IRQ routing
Apr 16 10:41:44 LinuxServerName kernel: [84801.579250] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NET: Registered protocol family 8
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NET: Registered protocol family 20
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel: Initializing
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel:  domain hash size = 128
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] PCI: Bridge: 0000:00:01.0
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224]   IO window: disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224]   MEM window: disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224]   PREFETCH window: disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NET: Registered protocol family 2
Apr 16 10:41:44 LinuxServerName kernel: [84801.694129] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694285] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694441] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694596] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694704] TCP reno registered
Apr 16 10:41:44 LinuxServerName kernel: [84801.724003] checking if image is initramfs... it is
Apr 16 10:41:44 LinuxServerName kernel: [84802.122753] Freeing initrd memory: 6642k freed
Apr 16 10:41:44 LinuxServerName kernel: [84802.123427] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:41:44 LinuxServerName kernel: [84802.125113] audit: initializing netlink socket (disabled)
Apr 16 10:41:44 LinuxServerName kernel: [84802.125269] audit(1208356892.050:1): initialized
Apr 16 10:41:44 LinuxServerName kernel: [84802.126267] VFS: Disk quotas dquot_6.5.1
Apr 16 10:41:44 LinuxServerName kernel: [84802.126394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84802.126550] io scheduler noop registered
Apr 16 10:41:44 LinuxServerName kernel: [84802.126636] io scheduler anticipatory registered
Apr 16 10:41:44 LinuxServerName kernel: [84802.126649] io scheduler deadline registered (default)
Apr 16 10:41:44 LinuxServerName kernel: [84802.126760] io scheduler cfq registered
Apr 16 10:41:44 LinuxServerName kernel: [84802.126916] Limiting direct PCI/PCI transfers.
Apr 16 10:41:44 LinuxServerName kernel: [84802.127610] isapnp: Scanning for PnP cards...
Apr 16 10:41:44 LinuxServerName kernel: [84802.484809] isapnp: No Plug & Play device found
Apr 16 10:41:44 LinuxServerName kernel: [84802.524898] Real Time Clock Driver v1.12ac
Apr 16 10:41:44 LinuxServerName kernel: [84802.525253] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:41:44 LinuxServerName kernel: [84802.525621] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.525998] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.527156] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.527690] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.528315] mice: PS/2 mouse device common for all mice
Apr 16 10:41:44 LinuxServerName kernel: [84802.530476] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:41:44 LinuxServerName kernel: [84803.038043] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.038177] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:41:44 LinuxServerName kernel: [84803.039773] EISA: Probing bus 0 at eisa.0
Apr 16 10:41:44 LinuxServerName kernel: [84803.039773] Cannot allocate resource for EISA slot 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.039773] EISA: Detected 0 cards.
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] TCP cubic registered
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] NET: Registered protocol family 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] Using IPI No-Shortcut mode
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681]   Magic number: 4:805:687
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681]   hash matches device 0000:00:0f.0
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] Freeing unused kernel memory: 332k freed
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:41:44 LinuxServerName kernel: [84803.069797] Time: tsc clocksource has been installed.
Apr 16 10:41:44 LinuxServerName kernel: [84803.250921] Capability LSM initialized
Apr 16 10:41:44 LinuxServerName kernel: [84803.280576] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:41:44 LinuxServerName kernel: [84803.280732] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:41:44 LinuxServerName kernel: [84803.280862] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:41:44 LinuxServerName kernel: [84803.280905] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:41:44 LinuxServerName kernel: [84803.880158] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:41:44 LinuxServerName kernel: [84803.880314] PIIX4: chipset revision 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.880392] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:41:44 LinuxServerName kernel: [84803.880548]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:41:44 LinuxServerName kernel: [84803.880704] Probing IDE interface ide0...
Apr 16 10:41:44 LinuxServerName kernel: [84803.900081] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:41:44 LinuxServerName kernel: [84803.929187] SCSI subsystem initialized
Apr 16 10:41:44 LinuxServerName kernel: [84803.929726] Fusion MPT base driver 3.04.03
Apr 16 10:41:44 LinuxServerName kernel: [84803.929748] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:41:44 LinuxServerName kernel: [84803.930273] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:41:44 LinuxServerName kernel: [84803.957573] Floppy drive(s): fd0 is 1.44M
Apr 16 10:41:44 LinuxServerName kernel: [84803.987809] FDC 0 is a post-1991 82077
Apr 16 10:41:44 LinuxServerName kernel: [84804.764628] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:41:44 LinuxServerName kernel: [84805.143806] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:41:44 LinuxServerName kernel: [84805.145761] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 10:41:44 LinuxServerName kernel: [84805.145917] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 10:41:44 LinuxServerName kernel: [84805.146229] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:41:44 LinuxServerName kernel: [84805.146384] pcnet32: 1 cards_found.
Apr 16 10:41:44 LinuxServerName kernel: [84805.146785] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 10:41:44 LinuxServerName kernel: [84805.146941] mptbase: Initiating ioc0 bringup
Apr 16 10:41:44 LinuxServerName kernel: [84805.402665] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:41:44 LinuxServerName kernel: [84805.811628] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 10:41:44 LinuxServerName kernel: [84806.160814] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:41:44 LinuxServerName kernel: [84806.160970]  target0:0:0: Beginning Domain Validation
Apr 16 10:41:44 LinuxServerName kernel: [84806.161125]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:41:44 LinuxServerName kernel: [84806.161177]  target0:0:0: Ending Domain Validation
Apr 16 10:41:44 LinuxServerName kernel: [84806.161333]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:41:44 LinuxServerName kernel: [84806.170976] libata version 2.20 loaded.
Apr 16 10:41:44 LinuxServerName kernel: [84806.177775] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:41:44 LinuxServerName kernel: [84806.177931] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:41:44 LinuxServerName kernel: [84806.200971] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84806.201127] sda: test WP failed, assume Write Enabled
Apr 16 10:41:44 LinuxServerName kernel: [84806.201283] sda: cache data unavailable
Apr 16 10:41:44 LinuxServerName kernel: [84806.201311] sda: assuming drive cache: write through
Apr 16 10:41:44 LinuxServerName kernel: [84806.201467] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84806.201558] sda: test WP failed, assume Write Enabled
Apr 16 10:41:44 LinuxServerName kernel: [84806.201591] sda: cache data unavailable
Apr 16 10:41:44 LinuxServerName kernel: [84806.201594] sda: assuming drive cache: write through
Apr 16 10:41:44 LinuxServerName kernel: [84806.201749]  sda: sda1 sda2 < sda5 >
Apr 16 10:41:44 LinuxServerName kernel: [84806.206582] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:41:44 LinuxServerName kernel: [84806.210504] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:41:44 LinuxServerName kernel: [84806.366080] Attempting manual resume
Apr 16 10:41:44 LinuxServerName kernel: [84806.366116] swsusp: Resume From Partition 8:5
Apr 16 10:41:44 LinuxServerName kernel: [84806.366142] PM: Checking swsusp image.
Apr 16 10:41:44 LinuxServerName kernel: [84806.366794] PM: Resume from disk failed.
Apr 16 10:41:44 LinuxServerName kernel: [84806.382024] kjournald starting.  Commit interval 5 seconds
Apr 16 10:41:44 LinuxServerName kernel: [84806.382323] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:41:44 LinuxServerName kernel: [84806.623591] parport: PnPBIOS parport detected.
Apr 16 10:41:44 LinuxServerName kernel: [84806.623747] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:41:44 LinuxServerName kernel: [84806.718891] lp0: using parport0 (interrupt-driven).
Apr 16 10:41:44 LinuxServerName kernel: [84806.740018] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:41:44 LinuxServerName kernel: [84806.753558] EXT3 FS on sda1, internal journal
Apr 16 10:41:44 LinuxServerName kernel: [84806.818354] eth0: link up
Apr 16 10:41:44 LinuxServerName kernel: [84808.024839] NET: Registered protocol family 10
Apr 16 10:41:44 LinuxServerName kernel: [84808.024995] lo: Disabled Privacy Extensions
Apr 16 10:41:44 LinuxServerName mysqld_safe[2652]: started
Apr 16 10:41:44 LinuxServerName mysqld[2656]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ib26RzNr' (Errcode: 13)
Apr 16 10:41:44 LinuxServerName mysqld[2656]: 080416 10:41:44  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 10:41:44 LinuxServerName mysqld[2656]: 080416 10:41:44 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 10:41:44 LinuxServerName mysqld[2656]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 10:41:45 LinuxServerName /etc/mysql/debian-start[2683]: Upgrading MySQL tables if necessary.
Apr 16 10:41:45 LinuxServerName slapd[2700]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 10:41:45 LinuxServerName /etc/mysql/debian-start[2724]: Checking for crashed MySQL tables.
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:41:45 LinuxServerName mysqld[2656]: 080416 10:41:45 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:41:45 LinuxServerName ntpd[2777]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Apr 16 10:41:45 LinuxServerName ntpd[2779]: precision = 2.000 usec
Apr 16 10:41:45 LinuxServerName ntpd[2779]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Apr 16 10:41:45 LinuxServerName ntpd[2779]: Listening on interface wildcard, ::#123 Disabled
Apr 16 10:41:45 LinuxServerName ntpd[2779]: Listening on interface lo, ::1#123 Enabled
Apr 16 10:41:45 LinuxServerName ntpd[2779]: Listening on interface eth0, fe80::250:56ff:fe88:27a#123 Enabled
Apr 16 10:41:45 LinuxServerName ntpd[2779]: Listening on interface lo, 127.0.0.1#123 Enabled
Apr 16 10:41:45 LinuxServerName ntpd[2779]: Listening on interface eth0, 10.150.46.10#123 Enabled
Apr 16 10:41:45 LinuxServerName ntpd[2779]: kernel time sync status 0040
Apr 16 10:41:45 LinuxServerName ntpd[2779]: frequency initialized -109.201 PPM from /var/lib/ntp/ntp.drift
Apr 16 10:41:45 LinuxServerName atd[2785]: Error redirecting I/O: Permission denied
Apr 16 10:41:45 LinuxServerName /usr/sbin/cron[2789]: (CRON) INFO (pidfile fd = 3)
Apr 16 10:41:45 LinuxServerName /usr/sbin/cron[2790]: (CRON) STARTUP (fork ok)
Apr 16 10:41:45 LinuxServerName /usr/sbin/cron[2790]: (CRON) INFO (Running @reboot jobs)
Apr 16 10:41:47 LinuxServerName ntpd_initres[2786]: host name not found: ah-dc1.na.takatacorp.com
Apr 16 10:41:47 LinuxServerName ntpd_initres[2786]: couldn't resolve `ah-dc1.na.takatacorp.com', giving up on it
Apr 16 10:41:54 LinuxServerName kernel: [84819.010686] eth0: no IPv6 routers present
Apr 16 10:42:06 LinuxServerName init: tty1 main process (2533) terminated with status 1
Apr 16 10:42:06 LinuxServerName init: tty1 main process ended, respawning
Apr 16 10:42:11 LinuxServerName init: tty4 main process (2528) killed by TERM signal
Apr 16 10:42:11 LinuxServerName init: tty5 main process (2529) killed by TERM signal
Apr 16 10:42:11 LinuxServerName init: tty2 main process (2531) killed by TERM signal
Apr 16 10:42:11 LinuxServerName init: tty3 main process (2532) killed by TERM signal
Apr 16 10:42:11 LinuxServerName init: tty6 main process (2534) killed by TERM signal
Apr 16 10:42:11 LinuxServerName init: tty1 main process (2821) killed by TERM signal
Apr 16 10:42:13 LinuxServerName mysqld[2656]: 080416 10:42:13 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 10:42:13 LinuxServerName mysqld[2656]: 
Apr 16 10:42:13 LinuxServerName mysqld[2656]: 080416 10:42:13 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 10:42:13 LinuxServerName mysqld[2656]: 
Apr 16 10:42:13 LinuxServerName mysqld_safe[2897]: ended
Apr 16 10:42:15 LinuxServerName exiting on signal 15
Apr 16 10:48:37 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:48:37 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:48:37 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:48:37 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:48:37 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] On node 0 totalpages: 131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6c60
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fefab68
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x1fefef14
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefef88
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fefefd8
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT 0x0100000d) @ 0x00000000
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Detected 3391.040 MHz processor.
Apr 16 10:48:37 LinuxServerName kernel: [85226.667998] Built 1 zonelists.  Total pages: 130048
Apr 16 10:48:37 LinuxServerName kernel: [85226.668177] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:48:37 LinuxServerName kernel: [85226.669033] mapped APIC to ffffd000 (fee00000)
Apr 16 10:48:37 LinuxServerName kernel: [85226.669109] mapped IOAPIC to ffffc000 (fec00000)
Apr 16 10:48:37 LinuxServerName kernel: [85226.669492] Enabling fast FPU save and restore... done.
Apr 16 10:48:37 LinuxServerName kernel: [85226.669561] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:48:37 LinuxServerName kernel: [85226.669885] Initializing CPU#0
Apr 16 10:48:37 LinuxServerName kernel: [85226.671410] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85226.671566] Console: colour VGA+ 80x25
Apr 16 10:48:37 LinuxServerName kernel: [85226.671721] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85226.671877] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681597] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681655] virtual kernel memory layout:
Apr 16 10:48:37 LinuxServerName kernel: [85226.681660]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681663]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681664]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681666]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681667]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681669]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681671]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681727] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:48:37 LinuxServerName kernel: [85226.831025] Calibrating delay using timer specific routine.. 6814.72 BogoMIPS (lpj=34073630)
Apr 16 10:48:37 LinuxServerName kernel: [85226.831180] Security Framework v1.0.0 initialized
Apr 16 10:48:37 LinuxServerName kernel: [85226.831336] SELinux:  Disabled at boot.
Apr 16 10:48:37 LinuxServerName kernel: [85226.831492] Mount-cache hash table entries: 512
Apr 16 10:48:37 LinuxServerName kernel: [85226.831648] CPU: After generic identify, caps: 0febfbff 00100000 00000000 00000000 00000011 00000000 00000000
Apr 16 10:48:37 LinuxServerName kernel: [85226.831803] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:48:37 LinuxServerName kernel: [85226.831853] CPU: L2 cache: 1024K
Apr 16 10:48:37 LinuxServerName kernel: [85226.831875] CPU: L3 cache: 16384K
Apr 16 10:48:37 LinuxServerName kernel: [85226.832031] CPU: After all inits, caps: 0febfbff 00100000 00000000 00003180 00000011 00000000 00000000
Apr 16 10:48:37 LinuxServerName kernel: [85226.832187] Compat vDSO mapped to ffffe000.
Apr 16 10:48:37 LinuxServerName kernel: [85226.832242] Remapping vsyscall page to ffffe000
Apr 16 10:48:37 LinuxServerName kernel: [85226.832398] Checking 'hlt' instruction... OK.
Apr 16 10:48:37 LinuxServerName kernel: [85226.870878] SMP alternatives: switching to UP code
Apr 16 10:48:37 LinuxServerName kernel: [85226.871034] Freeing SMP alternatives: 11k freed
Apr 16 10:48:37 LinuxServerName kernel: [85226.871190] Early unpacking initramfs... done
Apr 16 10:48:37 LinuxServerName kernel: [85227.050317] ACPI: Core revision 20060707
Apr 16 10:48:37 LinuxServerName kernel: [85227.050472] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:48:37 LinuxServerName kernel: [85227.060898] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:48:37 LinuxServerName kernel: [85227.061054] Total of 1 processors activated (6814.72 BogoMIPS).
Apr 16 10:48:37 LinuxServerName kernel: [85227.061210] ENABLING IO-APIC IRQs
Apr 16 10:48:37 LinuxServerName kernel: [85227.061622] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Brought up 1 CPUs
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Booting paravirtualized kernel on bare hardware
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Time: 14:48:50  Date: 03/16/108
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] NET: Registered protocol family 16
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] EISA bus registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] ACPI: bus type pci registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] PCI: Using configuration type 1
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Setting up standard PCI resources
Apr 16 10:48:37 LinuxServerName kernel: [85227.279600] ACPI: Interpreter enabled
Apr 16 10:48:37 LinuxServerName kernel: [85227.279639] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:48:37 LinuxServerName kernel: [85227.281499] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:48:37 LinuxServerName kernel: [85227.281647] PCI: Probing PCI hardware (bus 00)
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] Boot video device is 0000:00:0f.0
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.293588] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:48:37 LinuxServerName kernel: [85227.293670] pnp: PnP ACPI init
Apr 16 10:48:37 LinuxServerName kernel: [85227.310437] pnp: PnP ACPI: found 12 devices
Apr 16 10:48:37 LinuxServerName kernel: [85227.310535] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:48:37 LinuxServerName kernel: [85227.310872] PCI: Using ACPI for IRQ routing
Apr 16 10:48:37 LinuxServerName kernel: [85227.310986] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NET: Registered protocol family 8
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NET: Registered protocol family 20
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel: Initializing
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel:  domain hash size = 128
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] PCI: Bridge: 0000:00:01.0
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321]   IO window: disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321]   MEM window: disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321]   PREFETCH window: disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] PCI: Setting latency timer of device 0000:00:01.0 to 64
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NET: Registered protocol family 2
Apr 16 10:48:37 LinuxServerName kernel: [85227.419242] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419398] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419553] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419709] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419817] TCP reno registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.449097] checking if image is initramfs... it is
Apr 16 10:48:37 LinuxServerName kernel: [85227.857824] Freeing initrd memory: 6642k freed
Apr 16 10:48:37 LinuxServerName kernel: [85227.858528] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:48:37 LinuxServerName kernel: [85227.860206] audit: initializing netlink socket (disabled)
Apr 16 10:48:37 LinuxServerName kernel: [85227.860361] audit(1208357331.050:1): initialized
Apr 16 10:48:37 LinuxServerName kernel: [85227.861393] VFS: Disk quotas dquot_6.5.1
Apr 16 10:48:37 LinuxServerName kernel: [85227.861525] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.861681] io scheduler noop registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.861774] io scheduler anticipatory registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.861787] io scheduler deadline registered (default)
Apr 16 10:48:37 LinuxServerName kernel: [85227.861903] io scheduler cfq registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.862059] Limiting direct PCI/PCI transfers.
Apr 16 10:48:37 LinuxServerName kernel: [85227.862774] isapnp: Scanning for PnP cards...
Apr 16 10:48:37 LinuxServerName kernel: [85228.221555] isapnp: No Plug & Play device found
Apr 16 10:48:37 LinuxServerName kernel: [85228.260852] Real Time Clock Driver v1.12ac
Apr 16 10:48:37 LinuxServerName kernel: [85228.261061] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:48:37 LinuxServerName kernel: [85228.261572] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.262000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.263185] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.263779] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.264449] mice: PS/2 mouse device common for all mice
Apr 16 10:48:37 LinuxServerName kernel: [85228.266405] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:48:37 LinuxServerName kernel: [85228.266405] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:48:37 LinuxServerName kernel: [85228.266406] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:48:37 LinuxServerName kernel: [85228.266406] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:48:37 LinuxServerName kernel: [85228.266406] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] EISA: Probing bus 0 at eisa.0
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] Cannot allocate resource for EISA slot 1
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] EISA: Detected 0 cards.
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] TCP cubic registered
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] NET: Registered protocol family 1
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] Using IPI No-Shortcut mode
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748]   Magic number: 4:461:839
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748]   hash matches device ptyu5
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] Freeing unused kernel memory: 332k freed
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:48:37 LinuxServerName kernel: [85228.804891] Time: tsc clocksource has been installed.
Apr 16 10:48:37 LinuxServerName kernel: [85228.986042] Capability LSM initialized
Apr 16 10:48:37 LinuxServerName kernel: [85229.015637] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:48:37 LinuxServerName kernel: [85229.015792] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:48:37 LinuxServerName kernel: [85229.015926] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:48:37 LinuxServerName kernel: [85229.015968] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:48:37 LinuxServerName kernel: [85229.632926] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:48:37 LinuxServerName kernel: [85229.633082] PIIX4: chipset revision 1
Apr 16 10:48:37 LinuxServerName kernel: [85229.633148] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:48:37 LinuxServerName kernel: [85229.633304]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:48:37 LinuxServerName kernel: [85229.633460] Probing IDE interface ide0...
Apr 16 10:48:37 LinuxServerName kernel: [85229.674111] SCSI subsystem initialized
Apr 16 10:48:37 LinuxServerName kernel: [85229.674637] Fusion MPT base driver 3.04.03
Apr 16 10:48:37 LinuxServerName kernel: [85229.674657] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:48:37 LinuxServerName kernel: [85229.675227] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:48:37 LinuxServerName kernel: [85229.713241] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:48:37 LinuxServerName kernel: [85229.724662] Floppy drive(s): fd0 is 1.44M
Apr 16 10:48:37 LinuxServerName kernel: [85229.752342] FDC 0 is a post-1991 82077
Apr 16 10:48:37 LinuxServerName kernel: [85230.539573] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:48:37 LinuxServerName kernel: [85230.908765] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:48:37 LinuxServerName kernel: [85230.910666] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 10:48:37 LinuxServerName kernel: [85230.910822] mptbase: Initiating ioc0 bringup
Apr 16 10:48:37 LinuxServerName kernel: [85231.177606] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:48:37 LinuxServerName kernel: [85231.636415] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: Beginning Domain Validation
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: Ending Domain Validation
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:48:37 LinuxServerName kernel: [85232.012946] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 10:48:37 LinuxServerName kernel: [85232.013102] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 10:48:37 LinuxServerName kernel: [85232.015184] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:48:37 LinuxServerName kernel: [85232.015340] pcnet32: 1 cards_found.
Apr 16 10:48:37 LinuxServerName kernel: [85232.020488] libata version 2.20 loaded.
Apr 16 10:48:37 LinuxServerName kernel: [85232.040449] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85232.040605] sda: test WP failed, assume Write Enabled
Apr 16 10:48:37 LinuxServerName kernel: [85232.040761] sda: cache data unavailable
Apr 16 10:48:37 LinuxServerName kernel: [85232.040808] sda: assuming drive cache: write through
Apr 16 10:48:37 LinuxServerName kernel: [85232.040964] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85232.041064] sda: test WP failed, assume Write Enabled
Apr 16 10:48:37 LinuxServerName kernel: [85232.041098] sda: cache data unavailable
Apr 16 10:48:37 LinuxServerName kernel: [85232.041101] sda: assuming drive cache: write through
Apr 16 10:48:37 LinuxServerName kernel: [85232.041252]  sda: sda1 sda2 < sda5 >
Apr 16 10:48:37 LinuxServerName kernel: [85232.046678] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:48:37 LinuxServerName kernel: [85232.051055] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:48:37 LinuxServerName kernel: [85232.051211] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:48:37 LinuxServerName kernel: [85232.068502] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:48:37 LinuxServerName kernel: [85232.221303] Attempting manual resume
Apr 16 10:48:37 LinuxServerName kernel: [85232.221354] swsusp: Resume From Partition 8:5
Apr 16 10:48:37 LinuxServerName kernel: [85232.221380] PM: Checking swsusp image.
Apr 16 10:48:37 LinuxServerName kernel: [85232.222017] PM: Resume from disk failed.
Apr 16 10:48:37 LinuxServerName kernel: [85232.236871] kjournald starting.  Commit interval 5 seconds
Apr 16 10:48:37 LinuxServerName kernel: [85232.237162] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:48:37 LinuxServerName kernel: [85232.494304] parport: PnPBIOS parport detected.
Apr 16 10:48:37 LinuxServerName kernel: [85232.494460] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:48:37 LinuxServerName kernel: [85232.593512] lp0: using parport0 (interrupt-driven).
Apr 16 10:48:37 LinuxServerName kernel: [85232.616610] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:48:37 LinuxServerName kernel: [85232.630036] EXT3 FS on sda1, internal journal
Apr 16 10:48:37 LinuxServerName kernel: [85232.693089] eth0: link up
Apr 16 10:48:37 LinuxServerName kernel: [85233.799781] NET: Registered protocol family 10
Apr 16 10:48:37 LinuxServerName kernel: [85233.799936] lo: Disabled Privacy Extensions
Apr 16 10:48:37 LinuxServerName mysqld_safe[2658]: started
Apr 16 10:48:38 LinuxServerName mysqld[2662]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ib0p91Qb' (Errcode: 13)
Apr 16 10:48:38 LinuxServerName mysqld[2662]: 080416 10:48:38  InnoDB: Error: unable to create temporary file; errno: 13
Apr 16 10:48:38 LinuxServerName mysqld[2662]: 080416 10:48:38 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 10:48:38 LinuxServerName mysqld[2662]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Apr 16 10:48:39 LinuxServerName /etc/mysql/debian-start[2689]: Upgrading MySQL tables if necessary.
Apr 16 10:48:39 LinuxServerName slapd[2706]: @(#) $OpenLDAP: slapd 2.3.30 (Mar  5 2008 15:05:23) $ ^Ibuildd@terranova:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd 
Apr 16 10:48:39 LinuxServerName ntpd[2778]: ntpd 4.2.2p4@1.1585-o Wed Mar  7 20:43:30 UTC 2007 (1)
Apr 16 10:48:39 LinuxServerName ntpd[2779]: precision = 2.000 usec
Apr 16 10:48:39 LinuxServerName ntpd[2779]: Listening on interface wildcard, 0.0.0.0#123 Disabled
Apr 16 10:48:39 LinuxServerName ntpd[2779]: Listening on interface wildcard, ::#123 Disabled
Apr 16 10:48:39 LinuxServerName ntpd[2779]: Listening on interface lo, ::1#123 Enabled
Apr 16 10:48:39 LinuxServerName ntpd[2779]: bind() fd 19, family 10, port 123, scope 2, addr fe80::250:56ff:fe88:27a, in6_is_addr_multicast=0 flags=1 fails: Cannot assign requested address
Apr 16 10:48:39 LinuxServerName ntpd[2779]: Listening on interface lo, 127.0.0.1#123 Enabled
Apr 16 10:48:39 LinuxServerName ntpd[2779]: Listening on interface eth0, 10.150.46.10#123 Enabled
Apr 16 10:48:39 LinuxServerName ntpd[2779]: kernel time sync status 0040
Apr 16 10:48:39 LinuxServerName ntpd[2779]: frequency initialized -109.201 PPM from /var/lib/ntp/ntp.drift
Apr 16 10:48:39 LinuxServerName atd[2785]: Error redirecting I/O: Permission denied
Apr 16 10:48:39 LinuxServerName /usr/sbin/cron[2789]: (CRON) INFO (pidfile fd = 3)
Apr 16 10:48:39 LinuxServerName /usr/sbin/cron[2790]: (CRON) STARTUP (fork ok)
Apr 16 10:48:39 LinuxServerName /usr/sbin/cron[2790]: (CRON) INFO (Running @reboot jobs)
Apr 16 10:48:39 LinuxServerName /etc/mysql/debian-start[2805]: Checking for crashed MySQL tables.
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './inventory_staging/auth.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_administration_tools.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_application_logs.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_attached_files.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_comments.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_companies.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_categories.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_config_options.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_repo_attributes.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_file_types.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_im_types.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_message_subscriptions.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_companies.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_file_revisions.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_files.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_folders.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_forms.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_messages.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_milestones.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_task_lists.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_tasks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_project_users.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_projects.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_tags.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_user_im_values.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './projectpier/pp_users.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_archive.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_categorylinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_externallinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_filearchive.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_image.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_imagelinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_interwiki.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_ipblocks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_job.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_langlinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_logging.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_math.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_objectcache.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_oldimage.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_page.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_pagelinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_querycache_info.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_recentchanges.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_revision.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_site_stats.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_templatelinks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_text.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_trackbacks.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_transcache.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_user_groups.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:48:39 LinuxServerName mysqld[2662]: 080416 10:48:39 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './wikidb/mw_watchlist.frm'
Apr 16 10:48:41 LinuxServerName ntpd_initres[2786]: host name not found: ah-dc1.na.takatacorp.com
Apr 16 10:48:41 LinuxServerName ntpd_initres[2786]: couldn't resolve `ah-dc1.na.takatacorp.com', giving up on it
Apr 16 10:48:48 LinuxServerName kernel: [85245.004940] eth0: no IPv6 routers present
Apr 16 10:50:01 LinuxServerName CRON[2827]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:50:01 LinuxServerName CRON[2827]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:50:01 LinuxServerName CRON[2827]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:50:01 LinuxServerName CRON[2828]: PAM unable to dlopen(/lib/security/pam_env.so)
Apr 16 10:50:01 LinuxServerName CRON[2828]: PAM [dlerror: /lib/security/pam_env.so: cannot open shared object file: No such file or directory]
Apr 16 10:50:01 LinuxServerName CRON[2828]: PAM adding faulty module: /lib/security/pam_env.so
Apr 16 10:50:01 LinuxServerName CRON[2827]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:50:01 LinuxServerName CRON[2827]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:50:01 LinuxServerName CRON[2827]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:50:01 LinuxServerName CRON[2828]: PAM unable to dlopen(/lib/security/pam_limits.so)
Apr 16 10:50:01 LinuxServerName CRON[2828]: PAM [dlerror: /lib/security/pam_limits.so: cannot open shared object file: No such file or directory]
Apr 16 10:50:01 LinuxServerName CRON[2828]: PAM adding faulty module: /lib/security/pam_limits.so
Apr 16 10:50:01 LinuxServerName CRON[2827]: Module is unknown
Apr 16 10:50:01 LinuxServerName CRON[2828]: Module is unknown
Apr 16 10:50:25 LinuxServerName init: tty1 main process (2543) terminated with status 1
Apr 16 10:50:25 LinuxServerName init: tty1 main process ended, respawning
Apr 16 10:50:37 LinuxServerName init: tty4 main process (2536) killed by TERM signal
Apr 16 10:50:37 LinuxServerName init: tty5 main process (2537) killed by TERM signal
Apr 16 10:50:37 LinuxServerName init: tty2 main process (2541) killed by TERM signal
Apr 16 10:50:37 LinuxServerName init: tty3 main process (2542) killed by TERM signal
Apr 16 10:50:37 LinuxServerName init: tty6 main process (2545) killed by TERM signal
Apr 16 10:50:37 LinuxServerName init: tty1 main process (2829) killed by TERM signal
Apr 16 10:50:39 LinuxServerName mysqld[2662]: 080416 10:50:39 [Note] /usr/sbin/mysqld: Normal shutdown
Apr 16 10:50:39 LinuxServerName mysqld[2662]: 
Apr 16 10:50:39 LinuxServerName mysqld[2662]: 080416 10:50:39 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 16 10:50:39 LinuxServerName mysqld[2662]: 
Apr 16 10:50:39 LinuxServerName mysqld_safe[2905]: ended
Apr 16 10:50:41 LinuxServerName exiting on signal 15

```


messages
```

Apr 16 02:09:53 LinuxServerName -- MARK --
Apr 16 02:29:53 LinuxServerName -- MARK --
Apr 16 02:49:54 LinuxServerName -- MARK --
Apr 16 07:26:29 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 07:26:29 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 07:26:29 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 07:26:29 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 07:26:29 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 07:26:29 LinuxServerName kernel: [    0.000000] Detected 3394.991 MHz processor.
Apr 16 07:26:29 LinuxServerName kernel: [73137.259350] Built 1 zonelists.  Total pages: 130048
Apr 16 07:26:29 LinuxServerName kernel: [73137.259529] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 07:26:29 LinuxServerName kernel: [73137.260826] Enabling fast FPU save and restore... done.
Apr 16 07:26:29 LinuxServerName kernel: [73137.260891] Enabling unmasked SIMD FPU exception support... done.
Apr 16 07:26:29 LinuxServerName kernel: [73137.261180] Initializing CPU#0
Apr 16 07:26:29 LinuxServerName kernel: [73137.262657] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73137.262813] Console: colour VGA+ 80x25
Apr 16 07:26:29 LinuxServerName kernel: [73137.262969] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263125] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263280] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263336] virtual kernel memory layout:
Apr 16 07:26:29 LinuxServerName kernel: [73137.263340]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263342]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263344]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263346]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263347]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263349]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263350]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 07:26:29 LinuxServerName kernel: [73137.263404] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 07:26:29 LinuxServerName kernel: [73137.412175] Calibrating delay using timer specific routine.. 6795.64 BogoMIPS (lpj=33978217)
Apr 16 07:26:29 LinuxServerName kernel: [73137.412331] Security Framework v1.0.0 initialized
Apr 16 07:26:29 LinuxServerName kernel: [73137.412487] SELinux:  Disabled at boot.
Apr 16 07:26:29 LinuxServerName kernel: [73137.412642] Mount-cache hash table entries: 512
Apr 16 07:26:29 LinuxServerName kernel: [73137.412954] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 07:26:29 LinuxServerName kernel: [73137.413002] CPU: L2 cache: 1024K
Apr 16 07:26:29 LinuxServerName kernel: [73137.413024] CPU: L3 cache: 16384K
Apr 16 07:26:29 LinuxServerName kernel: [73137.413335] Compat vDSO mapped to ffffe000.
Apr 16 07:26:29 LinuxServerName kernel: [73137.413391] Remapping vsyscall page to ffffe000
Apr 16 07:26:29 LinuxServerName kernel: [73137.413547] Checking 'hlt' instruction... OK.
Apr 16 07:26:29 LinuxServerName kernel: [73137.452159] SMP alternatives: switching to UP code
Apr 16 07:26:29 LinuxServerName kernel: [73137.452315] Freeing SMP alternatives: 11k freed
Apr 16 07:26:29 LinuxServerName kernel: [73137.452470] Early unpacking initramfs... done
Apr 16 07:26:29 LinuxServerName kernel: [73137.641573] ACPI: Core revision 20060707
Apr 16 07:26:29 LinuxServerName kernel: [73137.641728] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 07:26:29 LinuxServerName kernel: [73137.642351] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 07:26:29 LinuxServerName kernel: [73137.642507] Total of 1 processors activated (6795.64 BogoMIPS).
Apr 16 07:26:29 LinuxServerName kernel: [73137.642663] ENABLING IO-APIC IRQs
Apr 16 07:26:29 LinuxServerName kernel: [73137.643075] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Brought up 1 CPUs
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Booting paravirtualized kernel on bare hardware
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Time: 11:26:23  Date: 03/16/108
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] NET: Registered protocol family 16
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] EISA bus registered
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] ACPI: bus type pci registered
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] PCI: Using configuration type 1
Apr 16 07:26:29 LinuxServerName kernel: [73137.860731] Setting up standard PCI resources
Apr 16 07:26:29 LinuxServerName kernel: [73137.860887] ACPI: Interpreter enabled
Apr 16 07:26:29 LinuxServerName kernel: [73137.860926] ACPI: Using IOAPIC for interrupt routing
Apr 16 07:26:29 LinuxServerName kernel: [73137.862509] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 07:26:29 LinuxServerName kernel: [73137.863257] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 07:26:29 LinuxServerName kernel: [73137.863338] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 07:26:29 LinuxServerName kernel: [73137.866514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.866829] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 07:26:29 LinuxServerName kernel: [73137.867149] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 07:26:29 LinuxServerName kernel: [73137.867458] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.874793] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 07:26:29 LinuxServerName kernel: [73137.874868] pnp: PnP ACPI init
Apr 16 07:26:29 LinuxServerName kernel: [73137.885114] pnp: PnP ACPI: found 12 devices
Apr 16 07:26:29 LinuxServerName kernel: [73137.885270] PnPBIOS: Disabled by ACPI PNP
Apr 16 07:26:29 LinuxServerName kernel: [73137.885585] PCI: Using ACPI for IRQ routing
Apr 16 07:26:29 LinuxServerName kernel: [73137.885695] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NET: Registered protocol family 8
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NET: Registered protocol family 20
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel: Initializing
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel:  domain hash size = 128
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NetLabel:  unlabeled traffic allowed by default
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] PCI: Bridge: 0000:00:01.0
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609]   IO window: disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609]   MEM window: disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609]   PREFETCH window: disabled.
Apr 16 07:26:29 LinuxServerName kernel: [73137.900609] NET: Registered protocol family 2
Apr 16 07:26:29 LinuxServerName kernel: [73138.000542] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.000698] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.000854] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.001010] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 07:26:29 LinuxServerName kernel: [73138.001114] TCP reno registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.030414] checking if image is initramfs... it is
Apr 16 07:26:29 LinuxServerName kernel: [73138.439107] Freeing initrd memory: 6642k freed
Apr 16 07:26:29 LinuxServerName kernel: [73138.439789] Simple Boot Flag at 0x36 set to 0x1
Apr 16 07:26:29 LinuxServerName kernel: [73138.441456] audit: initializing netlink socket (disabled)
Apr 16 07:26:29 LinuxServerName kernel: [73138.441612] audit(1208345183.040:1): initialized
Apr 16 07:26:29 LinuxServerName kernel: [73138.442634] VFS: Disk quotas dquot_6.5.1
Apr 16 07:26:29 LinuxServerName kernel: [73138.442776] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 07:26:29 LinuxServerName kernel: [73138.442932] io scheduler noop registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.443018] io scheduler anticipatory registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.443031] io scheduler deadline registered (default)
Apr 16 07:26:29 LinuxServerName kernel: [73138.443145] io scheduler cfq registered
Apr 16 07:26:29 LinuxServerName kernel: [73138.443301] Limiting direct PCI/PCI transfers.
Apr 16 07:26:29 LinuxServerName kernel: [73138.444004] isapnp: Scanning for PnP cards...
Apr 16 07:26:29 LinuxServerName kernel: [73138.802799] isapnp: No Plug & Play device found
Apr 16 07:26:29 LinuxServerName kernel: [73138.841920] Real Time Clock Driver v1.12ac
Apr 16 07:26:29 LinuxServerName kernel: [73138.842143] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 07:26:29 LinuxServerName kernel: [73138.842508] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.842877] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.844257] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.844840] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 07:26:29 LinuxServerName kernel: [73138.845726] mice: PS/2 mouse device common for all mice
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 07:26:29 LinuxServerName kernel: [73138.847693] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] EISA: Probing bus 0 at eisa.0
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] Cannot allocate resource for EISA slot 1
Apr 16 07:26:29 LinuxServerName kernel: [73139.356127] EISA: Detected 0 cards.
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] TCP cubic registered
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] NET: Registered protocol family 1
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] Using IPI No-Shortcut mode
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] ACPI: (supports S0 S1 S4 S5)
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035]   Magic number: 4:728:428
Apr 16 07:26:29 LinuxServerName kernel: [73139.386035] Freeing unused kernel memory: 332k freed
Apr 16 07:26:29 LinuxServerName kernel: [73139.386154] Time: tsc clocksource has been installed.
Apr 16 07:26:29 LinuxServerName kernel: [73139.557286] Capability LSM initialized
Apr 16 07:26:29 LinuxServerName kernel: [73139.586929] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 07:26:29 LinuxServerName kernel: [73139.587084] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 07:26:29 LinuxServerName kernel: [73139.587217] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 07:26:29 LinuxServerName kernel: [73139.587259] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 07:26:29 LinuxServerName kernel: [73140.184393] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 07:26:29 LinuxServerName kernel: [73140.184549] PIIX4: chipset revision 1
Apr 16 07:26:29 LinuxServerName kernel: [73140.184616] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 07:26:29 LinuxServerName kernel: [73140.184771]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 07:26:29 LinuxServerName kernel: [73140.194744] SCSI subsystem initialized
Apr 16 07:26:29 LinuxServerName kernel: [73140.195273] Fusion MPT base driver 3.04.03
Apr 16 07:26:29 LinuxServerName kernel: [73140.195299] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 07:26:29 LinuxServerName kernel: [73140.195821] Fusion MPT SPI Host driver 3.04.03
Apr 16 07:26:29 LinuxServerName kernel: [73140.205877] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 07:26:29 LinuxServerName kernel: [73140.265329] Floppy drive(s): fd0 is 1.44M
Apr 16 07:26:29 LinuxServerName kernel: [73140.294207] FDC 0 is a post-1991 82077
Apr 16 07:26:29 LinuxServerName kernel: [73141.061044] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 07:26:29 LinuxServerName kernel: [73141.440228] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 07:26:29 LinuxServerName kernel: [73141.442172] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 07:26:29 LinuxServerName kernel: [73141.442327] mptbase: Initiating ioc0 bringup
Apr 16 07:26:29 LinuxServerName kernel: [73141.709053] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 07:26:29 LinuxServerName kernel: [73142.177839] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: Beginning Domain Validation
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: Domain Validation skipping write tests
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: Ending Domain Validation
Apr 16 07:26:29 LinuxServerName kernel: [73142.526366]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 07:26:29 LinuxServerName kernel: [73142.534740] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 07:26:29 LinuxServerName kernel: [73142.534896] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 07:26:29 LinuxServerName kernel: [73142.536657] eth0: registered as PCnet/PCI II 79C970A
Apr 16 07:26:29 LinuxServerName kernel: [73142.536813] pcnet32: 1 cards_found.
Apr 16 07:26:29 LinuxServerName kernel: [73142.561896] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73142.562052] sda: test WP failed, assume Write Enabled
Apr 16 07:26:29 LinuxServerName kernel: [73142.562208] sda: cache data unavailable
Apr 16 07:26:29 LinuxServerName kernel: [73142.562394] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 07:26:29 LinuxServerName kernel: [73142.562499] sda: test WP failed, assume Write Enabled
Apr 16 07:26:29 LinuxServerName kernel: [73142.562535] sda: cache data unavailable
Apr 16 07:26:29 LinuxServerName kernel: [73142.562691]  sda: sda1 sda2 <<6>hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 07:26:29 LinuxServerName kernel: [73142.570141] Uniform CD-ROM driver Revision: 3.20
Apr 16 07:26:29 LinuxServerName kernel: [73142.572771]  sda5 >
Apr 16 07:26:29 LinuxServerName kernel: [73142.573082] sd 0:0:0:0: Attached scsi disk sda
Apr 16 07:26:29 LinuxServerName kernel: [73142.590405] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 07:26:29 LinuxServerName kernel: [73142.742411] Attempting manual resume
Apr 16 07:26:29 LinuxServerName kernel: [73142.754493] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 16 07:26:29 LinuxServerName kernel: [73142.754524] EXT3-fs: write access will be enabled during recovery.
Apr 16 07:26:29 LinuxServerName kernel: [73143.166008] kjournald starting.  Commit interval 5 seconds
Apr 16 07:26:29 LinuxServerName kernel: [73143.166307] EXT3-fs: recovery complete.
Apr 16 07:26:29 LinuxServerName kernel: [73143.167108] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 07:26:29 LinuxServerName kernel: [73143.644473] parport: PnPBIOS parport detected.
Apr 16 07:26:29 LinuxServerName kernel: [73143.644629] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 07:26:29 LinuxServerName kernel: [73143.743087] lp0: using parport0 (interrupt-driven).
Apr 16 07:26:29 LinuxServerName kernel: [73143.767028] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 07:26:29 LinuxServerName kernel: [73143.789089] EXT3 FS on sda1, internal journal
Apr 16 07:26:29 LinuxServerName kernel: [73143.872378] eth0: link up
Apr 16 07:26:41 LinuxServerName kernel: [73146.624127] NET: Registered protocol family 10
Apr 16 07:26:41 LinuxServerName kernel: [73146.624308] lo: Disabled Privacy Extensions
Apr 16 07:28:00 LinuxServerName exiting on signal 15
Apr 16 09:53:45 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 09:53:45 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 09:53:45 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 09:53:45 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 09:53:45 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 09:53:45 LinuxServerName kernel: [    0.000000] Detected 3390.985 MHz processor.
Apr 16 09:53:45 LinuxServerName kernel: [81871.309511] Built 1 zonelists.  Total pages: 130048
Apr 16 09:53:45 LinuxServerName kernel: [81871.309687] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro single
Apr 16 09:53:45 LinuxServerName kernel: [81871.311004] Enabling fast FPU save and restore... done.
Apr 16 09:53:45 LinuxServerName kernel: [81871.311069] Enabling unmasked SIMD FPU exception support... done.
Apr 16 09:53:45 LinuxServerName kernel: [81871.311420] Initializing CPU#0
Apr 16 09:53:45 LinuxServerName kernel: [81871.312898] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313054] Console: colour VGA+ 80x25
Apr 16 09:53:45 LinuxServerName kernel: [81871.313209] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313365] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313521] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313677] virtual kernel memory layout:
Apr 16 09:53:45 LinuxServerName kernel: [81871.313683]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313685]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313687]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313689]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313690]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313692]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313693]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 09:53:45 LinuxServerName kernel: [81871.313849] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 09:53:45 LinuxServerName kernel: [81871.462424] Calibrating delay using timer specific routine.. 6797.77 BogoMIPS (lpj=33988863)
Apr 16 09:53:45 LinuxServerName kernel: [81871.462579] Security Framework v1.0.0 initialized
Apr 16 09:53:45 LinuxServerName kernel: [81871.462735] SELinux:  Disabled at boot.
Apr 16 09:53:45 LinuxServerName kernel: [81871.462891] Mount-cache hash table entries: 512
Apr 16 09:53:45 LinuxServerName kernel: [81871.463202] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 09:53:45 LinuxServerName kernel: [81871.463358] CPU: L2 cache: 1024K
Apr 16 09:53:45 LinuxServerName kernel: [81871.463509] CPU: L3 cache: 16384K
Apr 16 09:53:45 LinuxServerName kernel: [81871.463820] Compat vDSO mapped to ffffe000.
Apr 16 09:53:45 LinuxServerName kernel: [81871.463957] Remapping vsyscall page to ffffe000
Apr 16 09:53:45 LinuxServerName kernel: [81871.464112] Checking 'hlt' instruction... OK.
Apr 16 09:53:45 LinuxServerName kernel: [81871.502403] SMP alternatives: switching to UP code
Apr 16 09:53:45 LinuxServerName kernel: [81871.502559] Freeing SMP alternatives: 11k freed
Apr 16 09:53:45 LinuxServerName kernel: [81871.502715] Early unpacking initramfs... done
Apr 16 09:53:45 LinuxServerName kernel: [81871.741665] ACPI: Core revision 20060707
Apr 16 09:53:45 LinuxServerName kernel: [81871.741821] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 09:53:45 LinuxServerName kernel: [81871.742444] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 09:53:45 LinuxServerName kernel: [81871.742600] Total of 1 processors activated (6797.77 BogoMIPS).
Apr 16 09:53:45 LinuxServerName kernel: [81871.742756] ENABLING IO-APIC IRQs
Apr 16 09:53:45 LinuxServerName kernel: [81871.743167] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Brought up 1 CPUs
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Booting paravirtualized kernel on bare hardware
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Time: 13:52:40  Date: 03/16/108
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] NET: Registered protocol family 16
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] EISA bus registered
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] ACPI: bus type pci registered
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] PCI: Using configuration type 1
Apr 16 09:53:45 LinuxServerName kernel: [81871.960821] Setting up standard PCI resources
Apr 16 09:53:45 LinuxServerName kernel: [81871.970790] ACPI: Interpreter enabled
Apr 16 09:53:45 LinuxServerName kernel: [81871.970790] ACPI: Using IOAPIC for interrupt routing
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81871.970791] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 09:53:45 LinuxServerName kernel: [81871.971115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 09:53:45 LinuxServerName kernel: [81871.971432] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81871.982585] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 09:53:45 LinuxServerName kernel: [81871.982741] pnp: PnP ACPI init
Apr 16 09:53:45 LinuxServerName kernel: [81871.993228] pnp: PnP ACPI: found 12 devices
Apr 16 09:53:45 LinuxServerName kernel: [81871.993384] PnPBIOS: Disabled by ACPI PNP
Apr 16 09:53:45 LinuxServerName kernel: [81871.993698] PCI: Using ACPI for IRQ routing
Apr 16 09:53:45 LinuxServerName kernel: [81871.993854] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NET: Registered protocol family 8
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NET: Registered protocol family 20
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel: Initializing
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel:  domain hash size = 128
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NetLabel:  unlabeled traffic allowed by default
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] PCI: Bridge: 0000:00:01.0
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698]   IO window: disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698]   MEM window: disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698]   PREFETCH window: disabled.
Apr 16 09:53:45 LinuxServerName kernel: [81872.000698] NET: Registered protocol family 2
Apr 16 09:53:45 LinuxServerName kernel: [81872.100577] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.100733] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.100889] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.101044] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 09:53:45 LinuxServerName kernel: [81872.101200] TCP reno registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.130474] checking if image is initramfs... it is
Apr 16 09:53:45 LinuxServerName kernel: [81872.599013] Freeing initrd memory: 6642k freed
Apr 16 09:53:45 LinuxServerName kernel: [81872.599738] Simple Boot Flag at 0x36 set to 0x1
Apr 16 09:53:45 LinuxServerName kernel: [81872.601442] audit: initializing netlink socket (disabled)
Apr 16 09:53:45 LinuxServerName kernel: [81872.601598] audit(1208353960.150:1): initialized
Apr 16 09:53:45 LinuxServerName kernel: [81872.602620] VFS: Disk quotas dquot_6.5.1
Apr 16 09:53:45 LinuxServerName kernel: [81872.602776] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 09:53:45 LinuxServerName kernel: [81872.602932] io scheduler noop registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.603088] io scheduler anticipatory registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.603224] io scheduler deadline registered (default)
Apr 16 09:53:45 LinuxServerName kernel: [81872.603380] io scheduler cfq registered
Apr 16 09:53:45 LinuxServerName kernel: [81872.603535] Limiting direct PCI/PCI transfers.
Apr 16 09:53:45 LinuxServerName kernel: [81872.604230] isapnp: Scanning for PnP cards...
Apr 16 09:53:45 LinuxServerName kernel: [81872.966585] isapnp: No Plug & Play device found
Apr 16 09:53:45 LinuxServerName kernel: [81873.004817] Real Time Clock Driver v1.12ac
Apr 16 09:53:45 LinuxServerName kernel: [81873.005131] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] mice: PS/2 mouse device common for all mice
Apr 16 09:53:45 LinuxServerName kernel: [81873.007598] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 09:53:45 LinuxServerName kernel: [81873.007923] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 09:53:45 LinuxServerName kernel: [81873.008279] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 09:53:45 LinuxServerName kernel: [81873.008434] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 09:53:45 LinuxServerName kernel: [81873.009009] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 09:53:45 LinuxServerName kernel: [81873.517085] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 09:53:45 LinuxServerName kernel: [81873.517258] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 09:53:45 LinuxServerName kernel: [81873.526002] EISA: Probing bus 0 at eisa.0
Apr 16 09:53:45 LinuxServerName kernel: [81873.526002] Cannot allocate resource for EISA slot 1
Apr 16 09:53:45 LinuxServerName kernel: [81873.526002] EISA: Detected 0 cards.
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] TCP cubic registered
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] NET: Registered protocol family 1
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] Using IPI No-Shortcut mode
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] ACPI: (supports S0 S1 S4 S5)
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910]   Magic number: 4:905:887
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910]   hash matches device ptyue
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] Freeing unused kernel memory: 332k freed
Apr 16 09:53:45 LinuxServerName kernel: [81873.555910] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 09:53:45 LinuxServerName kernel: [81873.556039] Time: tsc clocksource has been installed.
Apr 16 09:53:45 LinuxServerName kernel: [81873.746686] Capability LSM initialized
Apr 16 09:53:45 LinuxServerName kernel: [81873.786734] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 09:53:45 LinuxServerName kernel: [81873.786890] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:53:45 LinuxServerName kernel: [81873.787045] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:53:45 LinuxServerName kernel: [81873.787201] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:53:45 LinuxServerName kernel: [81874.396070] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 09:53:45 LinuxServerName kernel: [81874.403613] PIIX4: chipset revision 1
Apr 16 09:53:45 LinuxServerName kernel: [81874.403763] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 09:53:45 LinuxServerName kernel: [81874.403919]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 09:53:45 LinuxServerName kernel: [81874.426174] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 09:53:45 LinuxServerName kernel: [81874.459307] SCSI subsystem initialized
Apr 16 09:53:45 LinuxServerName kernel: [81874.459849] Fusion MPT base driver 3.04.03
Apr 16 09:53:45 LinuxServerName kernel: [81874.459963] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 09:53:45 LinuxServerName kernel: [81874.460507] Fusion MPT SPI Host driver 3.04.03
Apr 16 09:53:45 LinuxServerName kernel: [81874.477517] Floppy drive(s): fd0 is 1.44M
Apr 16 09:53:45 LinuxServerName kernel: [81874.503928] FDC 0 is a post-1991 82077
Apr 16 09:53:45 LinuxServerName kernel: [81875.310675] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 09:53:45 LinuxServerName kernel: [81875.709810] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 09:53:45 LinuxServerName kernel: [81875.711842] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 09:53:45 LinuxServerName kernel: [81875.711998] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] eth0: registered as PCnet/PCI II 79C970A
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] pcnet32: 1 cards_found.
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 09:53:45 LinuxServerName kernel: [81875.719249] mptbase: Initiating ioc0 bringup
Apr 16 09:53:45 LinuxServerName kernel: [81875.978616] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 09:53:45 LinuxServerName kernel: [81876.457388] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 09:53:45 LinuxServerName kernel: [81876.836488] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 09:53:45 LinuxServerName kernel: [81876.836643]  target0:0:0: Beginning Domain Validation
Apr 16 09:53:45 LinuxServerName kernel: [81876.836799]  target0:0:0: Domain Validation skipping write tests
Apr 16 09:53:45 LinuxServerName kernel: [81876.836955]  target0:0:0: Ending Domain Validation
Apr 16 09:53:45 LinuxServerName kernel: [81876.837111]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 09:53:45 LinuxServerName kernel: [81876.884438] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 09:53:45 LinuxServerName kernel: [81876.884594] Uniform CD-ROM driver Revision: 3.20
Apr 16 09:53:45 LinuxServerName kernel: [81876.901417] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81876.901572] sda: test WP failed, assume Write Enabled
Apr 16 09:53:45 LinuxServerName kernel: [81876.901728] sda: cache data unavailable
Apr 16 09:53:45 LinuxServerName kernel: [81876.901996] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:53:45 LinuxServerName kernel: [81876.902152] sda: test WP failed, assume Write Enabled
Apr 16 09:53:45 LinuxServerName kernel: [81876.902276] sda: cache data unavailable
Apr 16 09:53:45 LinuxServerName kernel: [81876.902518]  sda: sda1 sda2 < sda5 >
Apr 16 09:53:45 LinuxServerName kernel: [81876.906260] sd 0:0:0:0: Attached scsi disk sda
Apr 16 09:53:45 LinuxServerName kernel: [81876.909843] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 09:53:45 LinuxServerName kernel: [81876.995491] Attempting manual resume
Apr 16 09:53:45 LinuxServerName kernel: [81877.015690] kjournald starting.  Commit interval 5 seconds
Apr 16 09:53:45 LinuxServerName kernel: [81877.016002] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 09:53:45 LinuxServerName kernel: [81877.487035] parport: PnPBIOS parport detected.
Apr 16 09:53:45 LinuxServerName kernel: [81877.487191] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 09:53:45 LinuxServerName kernel: [81877.573975] lp0: using parport0 (interrupt-driven).
Apr 16 09:53:45 LinuxServerName kernel: [81877.599040] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 09:53:45 LinuxServerName kernel: [81877.629210] EXT3 FS on sda1, internal journal
Apr 16 09:53:45 LinuxServerName kernel: [81877.733205] eth0: link up
Apr 16 09:53:48 LinuxServerName kernel: [81933.208469] NET: Registered protocol family 10
Apr 16 09:53:48 LinuxServerName kernel: [81933.211426] lo: Disabled Privacy Extensions
Apr 16 09:55:13 LinuxServerName exiting on signal 15
Apr 16 09:56:10 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 09:56:10 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 09:56:10 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 09:56:10 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 09:56:10 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 09:56:10 LinuxServerName kernel: [    0.000000] Detected 3390.952 MHz processor.
Apr 16 09:56:10 LinuxServerName kernel: [82031.560065] Built 1 zonelists.  Total pages: 130048
Apr 16 09:56:10 LinuxServerName kernel: [82031.560249] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro single
Apr 16 09:56:10 LinuxServerName kernel: [82031.561568] Enabling fast FPU save and restore... done.
Apr 16 09:56:10 LinuxServerName kernel: [82031.561639] Enabling unmasked SIMD FPU exception support... done.
Apr 16 09:56:10 LinuxServerName kernel: [82031.561957] Initializing CPU#0
Apr 16 09:56:10 LinuxServerName kernel: [82031.563561] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82031.563717] Console: colour VGA+ 80x25
Apr 16 09:56:10 LinuxServerName kernel: [82031.563872] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564028] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564184] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564340] virtual kernel memory layout:
Apr 16 09:56:10 LinuxServerName kernel: [82031.564345]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564347]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564349]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564350]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564352]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564354]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564355]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 09:56:10 LinuxServerName kernel: [82031.564511] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 09:56:10 LinuxServerName kernel: [82031.713053] Calibrating delay using timer specific routine.. 6795.68 BogoMIPS (lpj=33978424)
Apr 16 09:56:10 LinuxServerName kernel: [82031.713208] Security Framework v1.0.0 initialized
Apr 16 09:56:10 LinuxServerName kernel: [82031.713364] SELinux:  Disabled at boot.
Apr 16 09:56:10 LinuxServerName kernel: [82031.713520] Mount-cache hash table entries: 512
Apr 16 09:56:10 LinuxServerName kernel: [82031.713831] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 09:56:10 LinuxServerName kernel: [82031.713987] CPU: L2 cache: 1024K
Apr 16 09:56:10 LinuxServerName kernel: [82031.714088] CPU: L3 cache: 16384K
Apr 16 09:56:10 LinuxServerName kernel: [82031.714400] Compat vDSO mapped to ffffe000.
Apr 16 09:56:10 LinuxServerName kernel: [82031.714539] Remapping vsyscall page to ffffe000
Apr 16 09:56:10 LinuxServerName kernel: [82031.714694] Checking 'hlt' instruction... OK.
Apr 16 09:56:10 LinuxServerName kernel: [82031.753045] SMP alternatives: switching to UP code
Apr 16 09:56:10 LinuxServerName kernel: [82031.753200] Freeing SMP alternatives: 11k freed
Apr 16 09:56:10 LinuxServerName kernel: [82031.753356] Early unpacking initramfs... done
Apr 16 09:56:10 LinuxServerName kernel: [82031.942460] ACPI: Core revision 20060707
Apr 16 09:56:10 LinuxServerName kernel: [82031.942616] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 09:56:10 LinuxServerName kernel: [82031.943239] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 09:56:10 LinuxServerName kernel: [82031.943395] Total of 1 processors activated (6795.68 BogoMIPS).
Apr 16 09:56:10 LinuxServerName kernel: [82031.943551] ENABLING IO-APIC IRQs
Apr 16 09:56:10 LinuxServerName kernel: [82031.943963] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Brought up 1 CPUs
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Booting paravirtualized kernel on bare hardware
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Time: 13:55:27  Date: 03/16/108
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] NET: Registered protocol family 16
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] EISA bus registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] ACPI: bus type pci registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] PCI: Using configuration type 1
Apr 16 09:56:10 LinuxServerName kernel: [82032.161620] Setting up standard PCI resources
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: Interpreter enabled
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: Using IOAPIC for interrupt routing
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 09:56:10 LinuxServerName kernel: [82032.171589] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.171682] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 09:56:10 LinuxServerName kernel: [82032.171995] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 09:56:10 LinuxServerName kernel: [82032.172368] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.183459] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 09:56:10 LinuxServerName kernel: [82032.183615] pnp: PnP ACPI init
Apr 16 09:56:10 LinuxServerName kernel: [82032.194574] pnp: PnP ACPI: found 12 devices
Apr 16 09:56:10 LinuxServerName kernel: [82032.194730] PnPBIOS: Disabled by ACPI PNP
Apr 16 09:56:10 LinuxServerName kernel: [82032.195058] PCI: Using ACPI for IRQ routing
Apr 16 09:56:10 LinuxServerName kernel: [82032.195214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NET: Registered protocol family 8
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NET: Registered protocol family 20
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel: Initializing
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel:  domain hash size = 128
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 09:56:10 LinuxServerName kernel: [82032.211466] NetLabel:  unlabeled traffic allowed by default
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467] PCI: Bridge: 0000:00:01.0
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467]   IO window: disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467]   MEM window: disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467]   PREFETCH window: disabled.
Apr 16 09:56:10 LinuxServerName kernel: [82032.211467] NET: Registered protocol family 2
Apr 16 09:56:10 LinuxServerName kernel: [82032.311488] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.311644] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.311800] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.311956] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 09:56:10 LinuxServerName kernel: [82032.312112] TCP reno registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.341251] checking if image is initramfs... it is
Apr 16 09:56:10 LinuxServerName kernel: [82032.749965] Freeing initrd memory: 6642k freed
Apr 16 09:56:10 LinuxServerName kernel: [82032.750745] Simple Boot Flag at 0x36 set to 0x1
Apr 16 09:56:10 LinuxServerName kernel: [82032.752402] audit: initializing netlink socket (disabled)
Apr 16 09:56:10 LinuxServerName kernel: [82032.752558] audit(1208354128.050:1): initialized
Apr 16 09:56:10 LinuxServerName kernel: [82032.753556] VFS: Disk quotas dquot_6.5.1
Apr 16 09:56:10 LinuxServerName kernel: [82032.753712] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 09:56:10 LinuxServerName kernel: [82032.753868] io scheduler noop registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.754024] io scheduler anticipatory registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.754138] io scheduler deadline registered (default)
Apr 16 09:56:10 LinuxServerName kernel: [82032.754293] io scheduler cfq registered
Apr 16 09:56:10 LinuxServerName kernel: [82032.754449] Limiting direct PCI/PCI transfers.
Apr 16 09:56:10 LinuxServerName kernel: [82032.759873] isapnp: Scanning for PnP cards...
Apr 16 09:56:10 LinuxServerName kernel: [82033.117200] isapnp: No Plug & Play device found
Apr 16 09:56:10 LinuxServerName kernel: [82033.153161] Real Time Clock Driver v1.12ac
Apr 16 09:56:10 LinuxServerName kernel: [82033.153463] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 09:56:10 LinuxServerName kernel: [82033.153828] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158550] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] mice: PS/2 mouse device common for all mice
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 09:56:10 LinuxServerName kernel: [82033.158551] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 09:56:10 LinuxServerName kernel: [82033.667523] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 09:56:10 LinuxServerName kernel: [82033.667707] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 09:56:10 LinuxServerName kernel: [82033.669603] EISA: Probing bus 0 at eisa.0
Apr 16 09:56:10 LinuxServerName kernel: [82033.669915] Cannot allocate resource for EISA slot 1
Apr 16 09:56:10 LinuxServerName kernel: [82033.670071] EISA: Detected 0 cards.
Apr 16 09:56:10 LinuxServerName kernel: [82033.700379] TCP cubic registered
Apr 16 09:56:10 LinuxServerName kernel: [82033.700504] NET: Registered protocol family 1
Apr 16 09:56:10 LinuxServerName kernel: [82033.700660] Using IPI No-Shortcut mode
Apr 16 09:56:10 LinuxServerName kernel: [82033.701257] ACPI: (supports S0 S1 S4 S5)
Apr 16 09:56:10 LinuxServerName kernel: [82033.706862]   Magic number: 4:458:938
Apr 16 09:56:10 LinuxServerName kernel: [82033.706862] Freeing unused kernel memory: 332k freed
Apr 16 09:56:10 LinuxServerName kernel: [82033.706862] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 09:56:10 LinuxServerName kernel: [82033.706982] Time: tsc clocksource has been installed.
Apr 16 09:56:10 LinuxServerName kernel: [82033.888059] Capability LSM initialized
Apr 16 09:56:10 LinuxServerName kernel: [82033.926848] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 09:56:10 LinuxServerName kernel: [82033.927004] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:56:10 LinuxServerName kernel: [82033.927160] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:56:10 LinuxServerName kernel: [82033.927316] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 09:56:10 LinuxServerName kernel: [82034.527134] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 09:56:10 LinuxServerName kernel: [82034.527290] PIIX4: chipset revision 1
Apr 16 09:56:10 LinuxServerName kernel: [82034.527439] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 09:56:10 LinuxServerName kernel: [82034.534545]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 09:56:10 LinuxServerName kernel: [82034.556437] SCSI subsystem initialized
Apr 16 09:56:10 LinuxServerName kernel: [82034.557040] Fusion MPT base driver 3.04.03
Apr 16 09:56:10 LinuxServerName kernel: [82034.557195] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 09:56:10 LinuxServerName kernel: [82034.557759] Fusion MPT SPI Host driver 3.04.03
Apr 16 09:56:10 LinuxServerName kernel: [82034.558443] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 09:56:10 LinuxServerName kernel: [82034.606182] Floppy drive(s): fd0 is 1.44M
Apr 16 09:56:10 LinuxServerName kernel: [82034.634941] FDC 0 is a post-1991 82077
Apr 16 09:56:10 LinuxServerName kernel: [82035.401896] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 09:56:10 LinuxServerName kernel: [82035.800925] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 09:56:10 LinuxServerName kernel: [82035.802842] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 09:56:10 LinuxServerName kernel: [82035.802998] mptbase: Initiating ioc0 bringup
Apr 16 09:56:10 LinuxServerName kernel: [82036.049815] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 09:56:10 LinuxServerName kernel: [82036.498649] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 09:56:10 LinuxServerName kernel: [82036.887713] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 09:56:10 LinuxServerName kernel: [82036.887869]  target0:0:0: Beginning Domain Validation
Apr 16 09:56:10 LinuxServerName kernel: [82036.888024]  target0:0:0: Domain Validation skipping write tests
Apr 16 09:56:10 LinuxServerName kernel: [82036.888171]  target0:0:0: Ending Domain Validation
Apr 16 09:56:10 LinuxServerName kernel: [82036.888327]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 09:56:10 LinuxServerName kernel: [82036.905453] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 09:56:10 LinuxServerName kernel: [82036.905609] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 09:56:10 LinuxServerName kernel: [82036.907334] eth0: registered as PCnet/PCI II 79C970A
Apr 16 09:56:10 LinuxServerName kernel: [82036.907490] pcnet32: 1 cards_found.
Apr 16 09:56:10 LinuxServerName kernel: [82036.934977] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 09:56:10 LinuxServerName kernel: [82036.935133] Uniform CD-ROM driver Revision: 3.20
Apr 16 09:56:10 LinuxServerName kernel: [82036.952144] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82036.952299] sda: test WP failed, assume Write Enabled
Apr 16 09:56:10 LinuxServerName kernel: [82036.952455] sda: cache data unavailable
Apr 16 09:56:10 LinuxServerName kernel: [82036.952724] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 09:56:10 LinuxServerName kernel: [82036.952880] sda: test WP failed, assume Write Enabled
Apr 16 09:56:10 LinuxServerName kernel: [82036.952999] sda: cache data unavailable
Apr 16 09:56:10 LinuxServerName kernel: [82036.953239]  sda: sda1 sda2 < sda5 >
Apr 16 09:56:10 LinuxServerName kernel: [82036.957504] sd 0:0:0:0: Attached scsi disk sda
Apr 16 09:56:10 LinuxServerName kernel: [82036.961053] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 09:56:10 LinuxServerName kernel: [82037.123907] Attempting manual resume
Apr 16 09:56:10 LinuxServerName kernel: [82037.141412] kjournald starting.  Commit interval 5 seconds
Apr 16 09:56:10 LinuxServerName kernel: [82037.141724] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 09:56:10 LinuxServerName kernel: [82037.426308] parport: PnPBIOS parport detected.
Apr 16 09:56:10 LinuxServerName kernel: [82037.426464] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 09:56:10 LinuxServerName kernel: [82037.525554] lp0: using parport0 (interrupt-driven).
Apr 16 09:56:10 LinuxServerName kernel: [82037.546964] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 09:56:10 LinuxServerName kernel: [82037.566073] EXT3 FS on sda1, internal journal
Apr 16 09:56:10 LinuxServerName kernel: [82037.627181] eth0: link up
Apr 16 09:56:12 LinuxServerName kernel: [82071.371640] NET: Registered protocol family 10
Apr 16 09:56:12 LinuxServerName kernel: [82071.374447] lo: Disabled Privacy Extensions
Apr 16 10:05:55 LinuxServerName exiting on signal 15
Apr 16 10:08:10 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:08:10 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:08:10 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:08:10 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:08:10 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:08:10 LinuxServerName kernel: [    0.000000] Detected 3390.989 MHz processor.
Apr 16 10:08:10 LinuxServerName kernel: [82806.186403] Built 1 zonelists.  Total pages: 130048
Apr 16 10:08:10 LinuxServerName kernel: [82806.186595] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:08:10 LinuxServerName kernel: [82806.187906] Enabling fast FPU save and restore... done.
Apr 16 10:08:10 LinuxServerName kernel: [82806.187985] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:08:10 LinuxServerName kernel: [82806.188265] Initializing CPU#0
Apr 16 10:08:10 LinuxServerName kernel: [82806.189770] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.189926] Console: colour VGA+ 80x25
Apr 16 10:08:10 LinuxServerName kernel: [82806.190082] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190237] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190393] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190448] virtual kernel memory layout:
Apr 16 10:08:10 LinuxServerName kernel: [82806.190452]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190454]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190456]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190457]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190459]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190461]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190462]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:08:10 LinuxServerName kernel: [82806.190520] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:08:10 LinuxServerName kernel: [82806.339301] Calibrating delay using timer specific routine.. 6797.38 BogoMIPS (lpj=33986903)
Apr 16 10:08:10 LinuxServerName kernel: [82806.339457] Security Framework v1.0.0 initialized
Apr 16 10:08:10 LinuxServerName kernel: [82806.339613] SELinux:  Disabled at boot.
Apr 16 10:08:10 LinuxServerName kernel: [82806.339768] Mount-cache hash table entries: 512
Apr 16 10:08:10 LinuxServerName kernel: [82806.340080] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:08:10 LinuxServerName kernel: [82806.340128] CPU: L2 cache: 1024K
Apr 16 10:08:10 LinuxServerName kernel: [82806.340150] CPU: L3 cache: 16384K
Apr 16 10:08:10 LinuxServerName kernel: [82806.340461] Compat vDSO mapped to ffffe000.
Apr 16 10:08:10 LinuxServerName kernel: [82806.340515] Remapping vsyscall page to ffffe000
Apr 16 10:08:10 LinuxServerName kernel: [82806.340671] Checking 'hlt' instruction... OK.
Apr 16 10:08:10 LinuxServerName kernel: [82806.379267] SMP alternatives: switching to UP code
Apr 16 10:08:10 LinuxServerName kernel: [82806.379423] Freeing SMP alternatives: 11k freed
Apr 16 10:08:10 LinuxServerName kernel: [82806.379578] Early unpacking initramfs... done
Apr 16 10:08:10 LinuxServerName kernel: [82806.568681] ACPI: Core revision 20060707
Apr 16 10:08:10 LinuxServerName kernel: [82806.568837] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:08:10 LinuxServerName kernel: [82806.569460] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:08:10 LinuxServerName kernel: [82806.569616] Total of 1 processors activated (6797.38 BogoMIPS).
Apr 16 10:08:10 LinuxServerName kernel: [82806.569772] ENABLING IO-APIC IRQs
Apr 16 10:08:10 LinuxServerName kernel: [82806.570183] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Brought up 1 CPUs
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Booting paravirtualized kernel on bare hardware
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Time: 14:08:04  Date: 03/16/108
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] NET: Registered protocol family 16
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] EISA bus registered
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] ACPI: bus type pci registered
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] PCI: Using configuration type 1
Apr 16 10:08:10 LinuxServerName kernel: [82806.787840] Setting up standard PCI resources
Apr 16 10:08:10 LinuxServerName kernel: [82806.787996] ACPI: Interpreter enabled
Apr 16 10:08:10 LinuxServerName kernel: [82806.788036] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:08:10 LinuxServerName kernel: [82806.789681] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:08:10 LinuxServerName kernel: [82806.797809] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.801896] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:08:10 LinuxServerName kernel: [82806.801976] pnp: PnP ACPI init
Apr 16 10:08:10 LinuxServerName kernel: [82806.812409] pnp: PnP ACPI: found 12 devices
Apr 16 10:08:10 LinuxServerName kernel: [82806.812501] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:08:10 LinuxServerName kernel: [82806.812811] PCI: Using ACPI for IRQ routing
Apr 16 10:08:10 LinuxServerName kernel: [82806.812943] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NET: Registered protocol family 8
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NET: Registered protocol family 20
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel: Initializing
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel:  domain hash size = 128
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] PCI: Bridge: 0000:00:01.0
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717]   IO window: disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717]   MEM window: disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717]   PREFETCH window: disabled.
Apr 16 10:08:10 LinuxServerName kernel: [82806.827717] NET: Registered protocol family 2
Apr 16 10:08:10 LinuxServerName kernel: [82806.927631] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.927787] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.927942] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82806.928098] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:08:10 LinuxServerName kernel: [82806.928197] TCP reno registered
Apr 16 10:08:10 LinuxServerName kernel: [82806.957499] checking if image is initramfs... it is
Apr 16 10:08:10 LinuxServerName kernel: [82807.366220] Freeing initrd memory: 6642k freed
Apr 16 10:08:10 LinuxServerName kernel: [82807.366887] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:08:10 LinuxServerName kernel: [82807.368535] audit: initializing netlink socket (disabled)
Apr 16 10:08:10 LinuxServerName kernel: [82807.368691] audit(1208354885.040:1): initialized
Apr 16 10:08:10 LinuxServerName kernel: [82807.369715] VFS: Disk quotas dquot_6.5.1
Apr 16 10:08:10 LinuxServerName kernel: [82807.369845] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:08:10 LinuxServerName kernel: [82807.370001] io scheduler noop registered
Apr 16 10:08:10 LinuxServerName kernel: [82807.370088] io scheduler anticipatory registered
Apr 16 10:08:10 LinuxServerName kernel: [82807.370101] io scheduler deadline registered (default)
Apr 16 10:08:10 LinuxServerName kernel: [82807.370217] io scheduler cfq registered
Apr 16 10:08:10 LinuxServerName kernel: [82807.370373] Limiting direct PCI/PCI transfers.
Apr 16 10:08:10 LinuxServerName kernel: [82807.371070] isapnp: Scanning for PnP cards...
Apr 16 10:08:10 LinuxServerName kernel: [82807.728175] isapnp: No Plug & Play device found
Apr 16 10:08:10 LinuxServerName kernel: [82807.767514] Real Time Clock Driver v1.12ac
Apr 16 10:08:10 LinuxServerName kernel: [82807.767735] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:08:10 LinuxServerName kernel: [82807.768100] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.768470] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.769761] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.770348] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:08:10 LinuxServerName kernel: [82807.770998] mice: PS/2 mouse device common for all mice
Apr 16 10:08:10 LinuxServerName kernel: [82807.772839] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:08:10 LinuxServerName kernel: [82807.774801] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:08:10 LinuxServerName kernel: [82808.284578] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:08:10 LinuxServerName kernel: [82808.284706] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:08:10 LinuxServerName kernel: [82808.286495] EISA: Probing bus 0 at eisa.0
Apr 16 10:08:10 LinuxServerName kernel: [82808.286780] Cannot allocate resource for EISA slot 1
Apr 16 10:08:10 LinuxServerName kernel: [82808.286935] EISA: Detected 0 cards.
Apr 16 10:08:10 LinuxServerName kernel: [82808.317191] TCP cubic registered
Apr 16 10:08:10 LinuxServerName kernel: [82808.317236] NET: Registered protocol family 1
Apr 16 10:08:10 LinuxServerName kernel: [82808.317391] Using IPI No-Shortcut mode
Apr 16 10:08:10 LinuxServerName kernel: [82808.317963] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:08:10 LinuxServerName kernel: [82808.318118]   Magic number: 4:737:131
Apr 16 10:08:10 LinuxServerName kernel: [82808.323113] Freeing unused kernel memory: 332k freed
Apr 16 10:08:10 LinuxServerName kernel: [82808.323113] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:08:10 LinuxServerName kernel: [82808.323256] Time: tsc clocksource has been installed.
Apr 16 10:08:10 LinuxServerName kernel: [82808.494399] Capability LSM initialized
Apr 16 10:08:10 LinuxServerName kernel: [82808.524050] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:08:10 LinuxServerName kernel: [82808.524205] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:08:10 LinuxServerName kernel: [82808.524355] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:08:10 LinuxServerName kernel: [82808.524398] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:08:10 LinuxServerName kernel: [82809.123447] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:08:10 LinuxServerName kernel: [82809.123603] PIIX4: chipset revision 1
Apr 16 10:08:10 LinuxServerName kernel: [82809.123669] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:08:10 LinuxServerName kernel: [82809.123825]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:08:10 LinuxServerName kernel: [82809.143560] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:08:10 LinuxServerName kernel: [82809.176888] SCSI subsystem initialized
Apr 16 10:08:10 LinuxServerName kernel: [82809.177469] Fusion MPT base driver 3.04.03
Apr 16 10:08:10 LinuxServerName kernel: [82809.177494] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:08:10 LinuxServerName kernel: [82809.178064] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:08:10 LinuxServerName kernel: [82809.194890] Floppy drive(s): fd0 is 1.44M
Apr 16 10:08:10 LinuxServerName kernel: [82809.221272] FDC 0 is a post-1991 82077
Apr 16 10:08:10 LinuxServerName kernel: [82810.008089] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:08:10 LinuxServerName kernel: [82810.397237] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:08:10 LinuxServerName kernel: [82810.399310] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 10:08:10 LinuxServerName kernel: [82810.399466] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 10:08:10 LinuxServerName kernel: [82810.399777] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:08:10 LinuxServerName kernel: [82810.399933] pcnet32: 1 cards_found.
Apr 16 10:08:10 LinuxServerName kernel: [82810.400336] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 10:08:10 LinuxServerName kernel: [82810.400492] mptbase: Initiating ioc0 bringup
Apr 16 10:08:10 LinuxServerName kernel: [82810.666064] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:08:10 LinuxServerName kernel: [82811.144813] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: Beginning Domain Validation
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: Ending Domain Validation
Apr 16 10:08:10 LinuxServerName kernel: [82811.543199]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:08:10 LinuxServerName kernel: [82811.578462] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82811.578617] sda: test WP failed, assume Write Enabled
Apr 16 10:08:10 LinuxServerName kernel: [82811.578773] sda: cache data unavailable
Apr 16 10:08:10 LinuxServerName kernel: [82811.578958] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:08:10 LinuxServerName kernel: [82811.579049] sda: test WP failed, assume Write Enabled
Apr 16 10:08:10 LinuxServerName kernel: [82811.579084] sda: cache data unavailable
Apr 16 10:08:10 LinuxServerName kernel: [82811.579243]  sda: sda1 sda2 < sda5 >
Apr 16 10:08:10 LinuxServerName kernel: [82811.583644] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:08:10 LinuxServerName kernel: [82811.588073] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:08:10 LinuxServerName kernel: [82811.588229] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:08:10 LinuxServerName kernel: [82811.607070] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:08:10 LinuxServerName kernel: [82811.759279] Attempting manual resume
Apr 16 10:08:10 LinuxServerName kernel: [82811.775242] kjournald starting.  Commit interval 5 seconds
Apr 16 10:08:10 LinuxServerName kernel: [82811.775534] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:08:10 LinuxServerName kernel: [82812.022477] parport: PnPBIOS parport detected.
Apr 16 10:08:10 LinuxServerName kernel: [82812.022633] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:08:10 LinuxServerName kernel: [82812.121896] lp0: using parport0 (interrupt-driven).
Apr 16 10:08:10 LinuxServerName kernel: [82812.143018] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:08:10 LinuxServerName kernel: [82812.172504] EXT3 FS on sda1, internal journal
Apr 16 10:08:10 LinuxServerName kernel: [82812.241206] eth0: link up
Apr 16 10:08:10 LinuxServerName kernel: [82813.348921] NET: Registered protocol family 10
Apr 16 10:08:10 LinuxServerName kernel: [82813.349077] lo: Disabled Privacy Extensions
Apr 16 10:10:14 LinuxServerName exiting on signal 15
Apr 16 10:19:04 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:18:58 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:18:58 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:18:58 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:18:58 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:18:58 LinuxServerName kernel: [    0.000000] Detected 3390.974 MHz processor.
Apr 16 10:18:58 LinuxServerName kernel: [83452.209685] Built 1 zonelists.  Total pages: 130048
Apr 16 10:18:58 LinuxServerName kernel: [83452.209859] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:18:58 LinuxServerName kernel: [83452.211149] Enabling fast FPU save and restore... done.
Apr 16 10:18:58 LinuxServerName kernel: [83452.211214] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:18:58 LinuxServerName kernel: [83452.211514] Initializing CPU#0
Apr 16 10:18:58 LinuxServerName kernel: [83452.212989] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213145] Console: colour VGA+ 80x25
Apr 16 10:18:58 LinuxServerName kernel: [83452.213301] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213457] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213613] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213669] virtual kernel memory layout:
Apr 16 10:18:58 LinuxServerName kernel: [83452.213673]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213676]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213677]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213679]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213680]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213682]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213683]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:18:58 LinuxServerName kernel: [83452.213737] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:18:58 LinuxServerName kernel: [83452.362504] Calibrating delay using timer specific routine.. 6796.41 BogoMIPS (lpj=33982087)
Apr 16 10:18:58 LinuxServerName kernel: [83452.362660] Security Framework v1.0.0 initialized
Apr 16 10:18:58 LinuxServerName kernel: [83452.362816] SELinux:  Disabled at boot.
Apr 16 10:18:58 LinuxServerName kernel: [83452.362972] Mount-cache hash table entries: 512
Apr 16 10:18:58 LinuxServerName kernel: [83452.363283] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:18:58 LinuxServerName kernel: [83452.363331] CPU: L2 cache: 1024K
Apr 16 10:18:58 LinuxServerName kernel: [83452.363353] CPU: L3 cache: 16384K
Apr 16 10:18:58 LinuxServerName kernel: [83452.363664] Compat vDSO mapped to ffffe000.
Apr 16 10:18:58 LinuxServerName kernel: [83452.363720] Remapping vsyscall page to ffffe000
Apr 16 10:18:58 LinuxServerName kernel: [83452.363875] Checking 'hlt' instruction... OK.
Apr 16 10:18:58 LinuxServerName kernel: [83452.402493] SMP alternatives: switching to UP code
Apr 16 10:18:58 LinuxServerName kernel: [83452.402648] Freeing SMP alternatives: 11k freed
Apr 16 10:18:58 LinuxServerName kernel: [83452.402804] Early unpacking initramfs... done
Apr 16 10:18:58 LinuxServerName kernel: [83452.591905] ACPI: Core revision 20060707
Apr 16 10:18:58 LinuxServerName kernel: [83452.592061] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:18:58 LinuxServerName kernel: [83452.592684] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:18:58 LinuxServerName kernel: [83452.592840] Total of 1 processors activated (6796.41 BogoMIPS).
Apr 16 10:18:58 LinuxServerName kernel: [83452.592995] ENABLING IO-APIC IRQs
Apr 16 10:18:58 LinuxServerName kernel: [83452.593407] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Brought up 1 CPUs
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Booting paravirtualized kernel on bare hardware
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Time: 14:18:51  Date: 03/16/108
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] NET: Registered protocol family 16
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] EISA bus registered
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] ACPI: bus type pci registered
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] PCI: Using configuration type 1
Apr 16 10:18:58 LinuxServerName kernel: [83452.811063] Setting up standard PCI resources
Apr 16 10:18:58 LinuxServerName kernel: [83452.811219] ACPI: Interpreter enabled
Apr 16 10:18:58 LinuxServerName kernel: [83452.811258] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:18:58 LinuxServerName kernel: [83452.812910] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:18:58 LinuxServerName kernel: [83452.813667] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:18:58 LinuxServerName kernel: [83452.813745] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:18:58 LinuxServerName kernel: [83452.817044] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.817364] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:18:58 LinuxServerName kernel: [83452.817685] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:18:58 LinuxServerName kernel: [83452.818004] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.825217] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:18:58 LinuxServerName kernel: [83452.825310] pnp: PnP ACPI init
Apr 16 10:18:58 LinuxServerName kernel: [83452.835511] pnp: PnP ACPI: found 12 devices
Apr 16 10:18:58 LinuxServerName kernel: [83452.835604] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:18:58 LinuxServerName kernel: [83452.835925] PCI: Using ACPI for IRQ routing
Apr 16 10:18:58 LinuxServerName kernel: [83452.836039] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NET: Registered protocol family 8
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NET: Registered protocol family 20
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel: Initializing
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel:  domain hash size = 128
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] PCI: Bridge: 0000:00:01.0
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940]   IO window: disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940]   MEM window: disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940]   PREFETCH window: disabled.
Apr 16 10:18:58 LinuxServerName kernel: [83452.850940] NET: Registered protocol family 2
Apr 16 10:18:58 LinuxServerName kernel: [83452.950864] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951020] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951175] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951331] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:18:58 LinuxServerName kernel: [83452.951439] TCP reno registered
Apr 16 10:18:58 LinuxServerName kernel: [83452.980715] checking if image is initramfs... it is
Apr 16 10:18:58 LinuxServerName kernel: [83453.379469] Freeing initrd memory: 6642k freed
Apr 16 10:18:58 LinuxServerName kernel: [83453.380146] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:18:58 LinuxServerName kernel: [83453.381779] audit: initializing netlink socket (disabled)
Apr 16 10:18:58 LinuxServerName kernel: [83453.381935] audit(1208355532.030:1): initialized
Apr 16 10:18:58 LinuxServerName kernel: [83453.382941] VFS: Disk quotas dquot_6.5.1
Apr 16 10:18:58 LinuxServerName kernel: [83453.383082] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:18:58 LinuxServerName kernel: [83453.383238] io scheduler noop registered
Apr 16 10:18:58 LinuxServerName kernel: [83453.383324] io scheduler anticipatory registered
Apr 16 10:18:58 LinuxServerName kernel: [83453.383337] io scheduler deadline registered (default)
Apr 16 10:18:58 LinuxServerName kernel: [83453.383456] io scheduler cfq registered
Apr 16 10:18:58 LinuxServerName kernel: [83453.383612] Limiting direct PCI/PCI transfers.
Apr 16 10:18:58 LinuxServerName kernel: [83453.384318] isapnp: Scanning for PnP cards...
Apr 16 10:18:58 LinuxServerName kernel: [83453.741022] isapnp: No Plug & Play device found
Apr 16 10:18:58 LinuxServerName kernel: [83453.779451] Real Time Clock Driver v1.12ac
Apr 16 10:18:58 LinuxServerName kernel: [83453.779660] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:18:58 LinuxServerName kernel: [83453.780023] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.780392] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.781559] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.782173] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:18:58 LinuxServerName kernel: [83453.782836] mice: PS/2 mouse device common for all mice
Apr 16 10:18:58 LinuxServerName kernel: [83453.785034] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:18:58 LinuxServerName kernel: [83453.788055] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:18:58 LinuxServerName kernel: [83454.299887] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:18:58 LinuxServerName kernel: [83454.300014] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:18:58 LinuxServerName kernel: [83454.301846] EISA: Probing bus 0 at eisa.0
Apr 16 10:18:58 LinuxServerName kernel: [83454.302153] Cannot allocate resource for EISA slot 1
Apr 16 10:18:58 LinuxServerName kernel: [83454.302309] EISA: Detected 0 cards.
Apr 16 10:18:58 LinuxServerName kernel: [83454.332560] TCP cubic registered
Apr 16 10:18:58 LinuxServerName kernel: [83454.332605] NET: Registered protocol family 1
Apr 16 10:18:58 LinuxServerName kernel: [83454.332761] Using IPI No-Shortcut mode
Apr 16 10:18:58 LinuxServerName kernel: [83454.333528] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:18:58 LinuxServerName kernel: [83454.333839]   Magic number: 4:943:333
Apr 16 10:18:58 LinuxServerName kernel: [83454.333995]   hash matches device tty54
Apr 16 10:18:58 LinuxServerName kernel: [83454.336367] Freeing unused kernel memory: 332k freed
Apr 16 10:18:58 LinuxServerName kernel: [83454.336367] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:18:58 LinuxServerName kernel: [83454.336492] Time: tsc clocksource has been installed.
Apr 16 10:18:58 LinuxServerName kernel: [83454.507612] Capability LSM initialized
Apr 16 10:18:58 LinuxServerName kernel: [83454.537836] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:18:58 LinuxServerName kernel: [83454.537991] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:18:58 LinuxServerName kernel: [83454.538147] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:18:58 LinuxServerName kernel: [83454.538190] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:18:58 LinuxServerName kernel: [83455.136672] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:18:58 LinuxServerName kernel: [83455.136828] PIIX4: chipset revision 1
Apr 16 10:18:58 LinuxServerName kernel: [83455.136893] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:18:58 LinuxServerName kernel: [83455.137049]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:18:58 LinuxServerName kernel: [83455.156818] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:18:58 LinuxServerName kernel: [83455.190056] SCSI subsystem initialized
Apr 16 10:18:58 LinuxServerName kernel: [83455.190602] Fusion MPT base driver 3.04.03
Apr 16 10:18:58 LinuxServerName kernel: [83455.190625] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:18:58 LinuxServerName kernel: [83455.191166] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:18:58 LinuxServerName kernel: [83455.207358] Floppy drive(s): fd0 is 1.44M
Apr 16 10:18:58 LinuxServerName kernel: [83455.234540] FDC 0 is a post-1991 82077
Apr 16 10:18:58 LinuxServerName kernel: [83456.041282] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:18:58 LinuxServerName kernel: [83456.440396] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:18:58 LinuxServerName kernel: [83456.442338] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 10:18:58 LinuxServerName kernel: [83456.442493] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 10:18:58 LinuxServerName kernel: [83456.442805] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:18:58 LinuxServerName kernel: [83456.442961] pcnet32: 1 cards_found.
Apr 16 10:18:58 LinuxServerName kernel: [83456.443357] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 10:18:58 LinuxServerName kernel: [83456.443513] mptbase: Initiating ioc0 bringup
Apr 16 10:18:58 LinuxServerName kernel: [83456.709061] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:18:58 LinuxServerName kernel: [83457.178011] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: Beginning Domain Validation
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: Ending Domain Validation
Apr 16 10:18:58 LinuxServerName kernel: [83457.516575]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:18:58 LinuxServerName kernel: [83457.551907] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83457.552063] sda: test WP failed, assume Write Enabled
Apr 16 10:18:58 LinuxServerName kernel: [83457.552219] sda: cache data unavailable
Apr 16 10:18:58 LinuxServerName kernel: [83457.552403] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:18:58 LinuxServerName kernel: [83457.552493] sda: test WP failed, assume Write Enabled
Apr 16 10:18:58 LinuxServerName kernel: [83457.552524] sda: cache data unavailable
Apr 16 10:18:58 LinuxServerName kernel: [83457.552680]  sda: sda1 sda2 < sda5 >
Apr 16 10:18:58 LinuxServerName kernel: [83457.558264] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:18:58 LinuxServerName kernel: [83457.561121] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:18:58 LinuxServerName kernel: [83457.561277] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:18:58 LinuxServerName kernel: [83457.580382] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:18:58 LinuxServerName kernel: [83457.732538] Attempting manual resume
Apr 16 10:18:58 LinuxServerName kernel: [83457.747055] kjournald starting.  Commit interval 5 seconds
Apr 16 10:18:58 LinuxServerName kernel: [83457.747354] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:18:58 LinuxServerName kernel: [83458.128205] parport: PnPBIOS parport detected.
Apr 16 10:18:58 LinuxServerName kernel: [83458.128361] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:18:58 LinuxServerName kernel: [83458.224832] lp0: using parport0 (interrupt-driven).
Apr 16 10:18:58 LinuxServerName kernel: [83458.285127] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:18:58 LinuxServerName kernel: [83458.310761] EXT3 FS on sda1, internal journal
Apr 16 10:18:58 LinuxServerName kernel: [83458.384061] eth0: link up
Apr 16 10:18:58 LinuxServerName kernel: [83459.500887] NET: Registered protocol family 10
Apr 16 10:18:58 LinuxServerName kernel: [83459.501043] lo: Disabled Privacy Extensions
Apr 16 10:19:46 LinuxServerName exiting on signal 15
Apr 16 10:24:16 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:24:16 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:24:16 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:24:16 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:24:16 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:24:16 LinuxServerName kernel: [    0.000000] Detected 3390.917 MHz processor.
Apr 16 10:24:16 LinuxServerName kernel: [83520.999838] Built 1 zonelists.  Total pages: 130048
Apr 16 10:24:16 LinuxServerName kernel: [83521.000020] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:24:16 LinuxServerName kernel: [83521.001323] Enabling fast FPU save and restore... done.
Apr 16 10:24:16 LinuxServerName kernel: [83521.001388] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:24:16 LinuxServerName kernel: [83521.001677] Initializing CPU#0
Apr 16 10:24:16 LinuxServerName kernel: [83521.003172] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013372] Console: colour VGA+ 80x25
Apr 16 10:24:16 LinuxServerName kernel: [83521.013528] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013683] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013839] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013894] virtual kernel memory layout:
Apr 16 10:24:16 LinuxServerName kernel: [83521.013898]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013900]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013902]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013903]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013905]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013906]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013908]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:24:16 LinuxServerName kernel: [83521.013962] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:24:16 LinuxServerName kernel: [83521.162680] Calibrating delay using timer specific routine.. 6808.28 BogoMIPS (lpj=34041410)
Apr 16 10:24:16 LinuxServerName kernel: [83521.162836] Security Framework v1.0.0 initialized
Apr 16 10:24:16 LinuxServerName kernel: [83521.162992] SELinux:  Disabled at boot.
Apr 16 10:24:16 LinuxServerName kernel: [83521.163148] Mount-cache hash table entries: 512
Apr 16 10:24:16 LinuxServerName kernel: [83521.163459] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:24:16 LinuxServerName kernel: [83521.163506] CPU: L2 cache: 1024K
Apr 16 10:24:16 LinuxServerName kernel: [83521.163528] CPU: L3 cache: 16384K
Apr 16 10:24:16 LinuxServerName kernel: [83521.163840] Compat vDSO mapped to ffffe000.
Apr 16 10:24:16 LinuxServerName kernel: [83521.163895] Remapping vsyscall page to ffffe000
Apr 16 10:24:16 LinuxServerName kernel: [83521.164051] Checking 'hlt' instruction... OK.
Apr 16 10:24:16 LinuxServerName kernel: [83521.202643] SMP alternatives: switching to UP code
Apr 16 10:24:16 LinuxServerName kernel: [83521.202798] Freeing SMP alternatives: 11k freed
Apr 16 10:24:16 LinuxServerName kernel: [83521.202954] Early unpacking initramfs... done
Apr 16 10:24:16 LinuxServerName kernel: [83521.412002] ACPI: Core revision 20060707
Apr 16 10:24:16 LinuxServerName kernel: [83521.412157] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:24:16 LinuxServerName kernel: [83521.422581] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:24:16 LinuxServerName kernel: [83521.422736] Total of 1 processors activated (6808.28 BogoMIPS).
Apr 16 10:24:16 LinuxServerName kernel: [83521.422892] ENABLING IO-APIC IRQs
Apr 16 10:24:16 LinuxServerName kernel: [83521.423304] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:24:16 LinuxServerName kernel: [83521.641126] Brought up 1 CPUs
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] Booting paravirtualized kernel on bare hardware
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] Time: 14:20:00  Date: 03/16/108
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] NET: Registered protocol family 16
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] EISA bus registered
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] ACPI: bus type pci registered
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] PCI: Using configuration type 1
Apr 16 10:24:16 LinuxServerName kernel: [83521.641127] Setting up standard PCI resources
Apr 16 10:24:16 LinuxServerName kernel: [83521.641282] ACPI: Interpreter enabled
Apr 16 10:24:16 LinuxServerName kernel: [83521.641321] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:24:16 LinuxServerName kernel: [83521.642974] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:24:16 LinuxServerName kernel: [83521.651096] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.655325] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:24:16 LinuxServerName kernel: [83521.655448] pnp: PnP ACPI init
Apr 16 10:24:16 LinuxServerName kernel: [83521.665504] pnp: PnP ACPI: found 12 devices
Apr 16 10:24:16 LinuxServerName kernel: [83521.665593] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:24:16 LinuxServerName kernel: [83521.665907] PCI: Using ACPI for IRQ routing
Apr 16 10:24:16 LinuxServerName kernel: [83521.666013] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NET: Registered protocol family 8
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NET: Registered protocol family 20
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel: Initializing
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel:  domain hash size = 128
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] PCI: Bridge: 0000:00:01.0
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004]   IO window: disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004]   MEM window: disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004]   PREFETCH window: disabled.
Apr 16 10:24:16 LinuxServerName kernel: [83521.681004] NET: Registered protocol family 2
Apr 16 10:24:16 LinuxServerName kernel: [83521.780904] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781060] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781216] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781372] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:24:16 LinuxServerName kernel: [83521.781470] TCP reno registered
Apr 16 10:24:16 LinuxServerName kernel: [83521.810776] checking if image is initramfs... it is
Apr 16 10:24:16 LinuxServerName kernel: [83522.219502] Freeing initrd memory: 6642k freed
Apr 16 10:24:16 LinuxServerName kernel: [83522.220184] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:24:16 LinuxServerName kernel: [83522.221849] audit: initializing netlink socket (disabled)
Apr 16 10:24:16 LinuxServerName kernel: [83522.222005] audit(1208355601.080:1): initialized
Apr 16 10:24:16 LinuxServerName kernel: [83522.223022] VFS: Disk quotas dquot_6.5.1
Apr 16 10:24:16 LinuxServerName kernel: [83522.223149] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:24:16 LinuxServerName kernel: [83522.223305] io scheduler noop registered
Apr 16 10:24:16 LinuxServerName kernel: [83522.223405] io scheduler anticipatory registered
Apr 16 10:24:16 LinuxServerName kernel: [83522.223418] io scheduler deadline registered (default)
Apr 16 10:24:16 LinuxServerName kernel: [83522.223544] io scheduler cfq registered
Apr 16 10:24:16 LinuxServerName kernel: [83522.223700] Limiting direct PCI/PCI transfers.
Apr 16 10:24:16 LinuxServerName kernel: [83522.224394] isapnp: Scanning for PnP cards...
Apr 16 10:24:16 LinuxServerName kernel: [83522.581767] isapnp: No Plug & Play device found
Apr 16 10:24:16 LinuxServerName kernel: [83522.620406] Real Time Clock Driver v1.12ac
Apr 16 10:24:16 LinuxServerName kernel: [83522.620627] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:24:16 LinuxServerName kernel: [83522.620992] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.621361] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.622495] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.623018] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:24:16 LinuxServerName kernel: [83522.623632] mice: PS/2 mouse device common for all mice
Apr 16 10:24:16 LinuxServerName kernel: [83522.625656] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:24:16 LinuxServerName kernel: [83522.628088] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:24:16 LinuxServerName kernel: [83523.137976] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:24:16 LinuxServerName kernel: [83523.138107] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:24:16 LinuxServerName kernel: [83523.139968] EISA: Probing bus 0 at eisa.0
Apr 16 10:24:16 LinuxServerName kernel: [83523.140279] Cannot allocate resource for EISA slot 1
Apr 16 10:24:16 LinuxServerName kernel: [83523.140435] EISA: Detected 0 cards.
Apr 16 10:24:16 LinuxServerName kernel: [83523.170717] TCP cubic registered
Apr 16 10:24:16 LinuxServerName kernel: [83523.170848] NET: Registered protocol family 1
Apr 16 10:24:16 LinuxServerName kernel: [83523.171004] Using IPI No-Shortcut mode
Apr 16 10:24:16 LinuxServerName kernel: [83523.171438] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:24:16 LinuxServerName kernel: [83523.172229] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:24:16 LinuxServerName kernel: [83523.172384]   Magic number: 4:943:333
Apr 16 10:24:16 LinuxServerName kernel: [83523.172540]   hash matches device tty54
Apr 16 10:24:16 LinuxServerName kernel: [83523.176400] Freeing unused kernel memory: 332k freed
Apr 16 10:24:16 LinuxServerName kernel: [83523.176527] Time: tsc clocksource has been installed.
Apr 16 10:24:16 LinuxServerName kernel: [83523.357650] Capability LSM initialized
Apr 16 10:24:16 LinuxServerName kernel: [83523.397253] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:24:16 LinuxServerName kernel: [83523.397409] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:24:16 LinuxServerName kernel: [83523.397559] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:24:16 LinuxServerName kernel: [83523.397603] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:24:16 LinuxServerName kernel: [83524.015817] SCSI subsystem initialized
Apr 16 10:24:16 LinuxServerName kernel: [83524.016433] Fusion MPT base driver 3.04.03
Apr 16 10:24:16 LinuxServerName kernel: [83524.016454] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:24:16 LinuxServerName kernel: [83524.017021] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:24:16 LinuxServerName kernel: [83524.017176] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 10:24:16 LinuxServerName kernel: [83524.017332] mptbase: Initiating ioc0 bringup
Apr 16 10:24:16 LinuxServerName kernel: [83524.018010] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:24:16 LinuxServerName kernel: [83524.056836] Floppy drive(s): fd0 is 1.44M
Apr 16 10:24:16 LinuxServerName kernel: [83524.084764] FDC 0 is a post-1991 82077
Apr 16 10:24:16 LinuxServerName kernel: [83524.293128] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:24:16 LinuxServerName kernel: [83524.761915] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: Beginning Domain Validation
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: Ending Domain Validation
Apr 16 10:24:16 LinuxServerName kernel: [83525.190199]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:24:16 LinuxServerName kernel: [83525.199501] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 10:24:16 LinuxServerName kernel: [83525.200334] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 10:24:16 LinuxServerName kernel: [83525.200645] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:24:16 LinuxServerName kernel: [83525.200801] pcnet32: 1 cards_found.
Apr 16 10:24:16 LinuxServerName kernel: [83525.201352] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:24:16 LinuxServerName kernel: [83525.201508] PIIX4: chipset revision 1
Apr 16 10:24:16 LinuxServerName kernel: [83525.201587] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:24:16 LinuxServerName kernel: [83525.201743]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:24:16 LinuxServerName kernel: [83525.232596] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83525.232752] sda: test WP failed, assume Write Enabled
Apr 16 10:24:16 LinuxServerName kernel: [83525.232908] sda: cache data unavailable
Apr 16 10:24:16 LinuxServerName kernel: [83525.233092] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:24:16 LinuxServerName kernel: [83525.233180] sda: test WP failed, assume Write Enabled
Apr 16 10:24:16 LinuxServerName kernel: [83525.233213] sda: cache data unavailable
Apr 16 10:24:16 LinuxServerName kernel: [83525.233370]  sda: sda1 sda2 < sda5 >
Apr 16 10:24:16 LinuxServerName kernel: [83525.235594] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:24:16 LinuxServerName kernel: [83525.242231] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:24:16 LinuxServerName kernel: [83525.396169] Attempting manual resume
Apr 16 10:24:16 LinuxServerName kernel: [83525.410793] kjournald starting.  Commit interval 5 seconds
Apr 16 10:24:16 LinuxServerName kernel: [83525.411091] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:24:16 LinuxServerName kernel: [83525.669481] parport: PnPBIOS parport detected.
Apr 16 10:24:16 LinuxServerName kernel: [83525.669636] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:24:16 LinuxServerName kernel: [83526.067727] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:24:16 LinuxServerName kernel: [83526.446847] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:24:16 LinuxServerName kernel: [83526.447665] lp0: using parport0 (interrupt-driven).
Apr 16 10:24:16 LinuxServerName kernel: [83746.598820] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:24:16 LinuxServerName kernel: [83746.694108] EXT3 FS on sda1, internal journal
Apr 16 10:24:16 LinuxServerName kernel: [83746.943067] eth0: link up
Apr 16 10:24:16 LinuxServerName kernel: [83749.380356] NET: Registered protocol family 10
Apr 16 10:24:16 LinuxServerName kernel: [83749.383210] lo: Disabled Privacy Extensions
Apr 16 10:24:30 LinuxServerName exiting on signal 15
Apr 16 10:41:38 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:41:30 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:41:44 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:41:44 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:41:44 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:41:44 LinuxServerName kernel: [    0.000000] Detected 3390.937 MHz processor.
Apr 16 10:41:44 LinuxServerName kernel: [84800.933047] Built 1 zonelists.  Total pages: 130048
Apr 16 10:41:44 LinuxServerName kernel: [84800.933217] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:41:44 LinuxServerName kernel: [84800.934501] Enabling fast FPU save and restore... done.
Apr 16 10:41:44 LinuxServerName kernel: [84800.934568] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:41:44 LinuxServerName kernel: [84800.934858] Initializing CPU#0
Apr 16 10:41:44 LinuxServerName kernel: [84800.936331] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84800.936486] Console: colour VGA+ 80x25
Apr 16 10:41:44 LinuxServerName kernel: [84800.936642] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84800.936798] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84800.936954] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937007] virtual kernel memory layout:
Apr 16 10:41:44 LinuxServerName kernel: [84800.937012]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937014]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937016]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937017]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937019]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937020]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937022]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:41:44 LinuxServerName kernel: [84800.937077] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:41:44 LinuxServerName kernel: [84801.085857] Calibrating delay using timer specific routine.. 6807.20 BogoMIPS (lpj=34036005)
Apr 16 10:41:44 LinuxServerName kernel: [84801.086013] Security Framework v1.0.0 initialized
Apr 16 10:41:44 LinuxServerName kernel: [84801.086169] SELinux:  Disabled at boot.
Apr 16 10:41:44 LinuxServerName kernel: [84801.086325] Mount-cache hash table entries: 512
Apr 16 10:41:44 LinuxServerName kernel: [84801.086636] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:41:44 LinuxServerName kernel: [84801.086684] CPU: L2 cache: 1024K
Apr 16 10:41:44 LinuxServerName kernel: [84801.086706] CPU: L3 cache: 16384K
Apr 16 10:41:44 LinuxServerName kernel: [84801.087017] Compat vDSO mapped to ffffe000.
Apr 16 10:41:44 LinuxServerName kernel: [84801.087074] Remapping vsyscall page to ffffe000
Apr 16 10:41:44 LinuxServerName kernel: [84801.087230] Checking 'hlt' instruction... OK.
Apr 16 10:41:44 LinuxServerName kernel: [84801.125836] SMP alternatives: switching to UP code
Apr 16 10:41:44 LinuxServerName kernel: [84801.125992] Freeing SMP alternatives: 11k freed
Apr 16 10:41:44 LinuxServerName kernel: [84801.126147] Early unpacking initramfs... done
Apr 16 10:41:44 LinuxServerName kernel: [84801.335209] ACPI: Core revision 20060707
Apr 16 10:41:44 LinuxServerName kernel: [84801.335365] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:41:44 LinuxServerName kernel: [84801.335988] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:41:44 LinuxServerName kernel: [84801.336144] Total of 1 processors activated (6807.20 BogoMIPS).
Apr 16 10:41:44 LinuxServerName kernel: [84801.336300] ENABLING IO-APIC IRQs
Apr 16 10:41:44 LinuxServerName kernel: [84801.336711] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Brought up 1 CPUs
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Booting paravirtualized kernel on bare hardware
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Time: 14:41:31  Date: 03/16/108
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] NET: Registered protocol family 16
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] EISA bus registered
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] ACPI: bus type pci registered
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] PCI: Using configuration type 1
Apr 16 10:41:44 LinuxServerName kernel: [84801.554347] Setting up standard PCI resources
Apr 16 10:41:44 LinuxServerName kernel: [84801.554503] ACPI: Interpreter enabled
Apr 16 10:41:44 LinuxServerName kernel: [84801.554543] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:41:44 LinuxServerName kernel: [84801.556235] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:41:44 LinuxServerName kernel: [84801.556997] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:41:44 LinuxServerName kernel: [84801.557091] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:41:44 LinuxServerName kernel: [84801.560443] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.560759] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:41:44 LinuxServerName kernel: [84801.561073] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:41:44 LinuxServerName kernel: [84801.561379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.568315] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:41:44 LinuxServerName kernel: [84801.568392] pnp: PnP ACPI init
Apr 16 10:41:44 LinuxServerName kernel: [84801.578738] pnp: PnP ACPI: found 12 devices
Apr 16 10:41:44 LinuxServerName kernel: [84801.578828] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:41:44 LinuxServerName kernel: [84801.579137] PCI: Using ACPI for IRQ routing
Apr 16 10:41:44 LinuxServerName kernel: [84801.579250] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NET: Registered protocol family 8
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NET: Registered protocol family 20
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel: Initializing
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel:  domain hash size = 128
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] PCI: Bridge: 0000:00:01.0
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224]   IO window: disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224]   MEM window: disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224]   PREFETCH window: disabled.
Apr 16 10:41:44 LinuxServerName kernel: [84801.594224] NET: Registered protocol family 2
Apr 16 10:41:44 LinuxServerName kernel: [84801.694129] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694285] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694441] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694596] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:41:44 LinuxServerName kernel: [84801.694704] TCP reno registered
Apr 16 10:41:44 LinuxServerName kernel: [84801.724003] checking if image is initramfs... it is
Apr 16 10:41:44 LinuxServerName kernel: [84802.122753] Freeing initrd memory: 6642k freed
Apr 16 10:41:44 LinuxServerName kernel: [84802.123427] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:41:44 LinuxServerName kernel: [84802.125113] audit: initializing netlink socket (disabled)
Apr 16 10:41:44 LinuxServerName kernel: [84802.125269] audit(1208356892.050:1): initialized
Apr 16 10:41:44 LinuxServerName kernel: [84802.126267] VFS: Disk quotas dquot_6.5.1
Apr 16 10:41:44 LinuxServerName kernel: [84802.126394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:41:44 LinuxServerName kernel: [84802.126550] io scheduler noop registered
Apr 16 10:41:44 LinuxServerName kernel: [84802.126636] io scheduler anticipatory registered
Apr 16 10:41:44 LinuxServerName kernel: [84802.126649] io scheduler deadline registered (default)
Apr 16 10:41:44 LinuxServerName kernel: [84802.126760] io scheduler cfq registered
Apr 16 10:41:44 LinuxServerName kernel: [84802.126916] Limiting direct PCI/PCI transfers.
Apr 16 10:41:44 LinuxServerName kernel: [84802.127610] isapnp: Scanning for PnP cards...
Apr 16 10:41:44 LinuxServerName kernel: [84802.484809] isapnp: No Plug & Play device found
Apr 16 10:41:44 LinuxServerName kernel: [84802.524898] Real Time Clock Driver v1.12ac
Apr 16 10:41:44 LinuxServerName kernel: [84802.525253] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:41:44 LinuxServerName kernel: [84802.525621] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.525998] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.527156] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.527690] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:41:44 LinuxServerName kernel: [84802.528315] mice: PS/2 mouse device common for all mice
Apr 16 10:41:44 LinuxServerName kernel: [84802.530476] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:41:44 LinuxServerName kernel: [84802.531339] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:41:44 LinuxServerName kernel: [84803.038043] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.038177] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:41:44 LinuxServerName kernel: [84803.039773] EISA: Probing bus 0 at eisa.0
Apr 16 10:41:44 LinuxServerName kernel: [84803.039773] Cannot allocate resource for EISA slot 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.039773] EISA: Detected 0 cards.
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] TCP cubic registered
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] NET: Registered protocol family 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] Using IPI No-Shortcut mode
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681]   Magic number: 4:805:687
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681]   hash matches device 0000:00:0f.0
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] Freeing unused kernel memory: 332k freed
Apr 16 10:41:44 LinuxServerName kernel: [84803.069681] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:41:44 LinuxServerName kernel: [84803.069797] Time: tsc clocksource has been installed.
Apr 16 10:41:44 LinuxServerName kernel: [84803.250921] Capability LSM initialized
Apr 16 10:41:44 LinuxServerName kernel: [84803.280576] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:41:44 LinuxServerName kernel: [84803.280732] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:41:44 LinuxServerName kernel: [84803.280862] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:41:44 LinuxServerName kernel: [84803.280905] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:41:44 LinuxServerName kernel: [84803.880158] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:41:44 LinuxServerName kernel: [84803.880314] PIIX4: chipset revision 1
Apr 16 10:41:44 LinuxServerName kernel: [84803.880392] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:41:44 LinuxServerName kernel: [84803.880548]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:41:44 LinuxServerName kernel: [84803.900081] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:41:44 LinuxServerName kernel: [84803.929187] SCSI subsystem initialized
Apr 16 10:41:44 LinuxServerName kernel: [84803.929726] Fusion MPT base driver 3.04.03
Apr 16 10:41:44 LinuxServerName kernel: [84803.929748] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:41:44 LinuxServerName kernel: [84803.930273] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:41:44 LinuxServerName kernel: [84803.957573] Floppy drive(s): fd0 is 1.44M
Apr 16 10:41:44 LinuxServerName kernel: [84803.987809] FDC 0 is a post-1991 82077
Apr 16 10:41:44 LinuxServerName kernel: [84804.764628] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:41:44 LinuxServerName kernel: [84805.143806] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:41:44 LinuxServerName kernel: [84805.145761] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
Apr 16 10:41:44 LinuxServerName kernel: [84805.145917] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 16.
Apr 16 10:41:44 LinuxServerName kernel: [84805.146229] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:41:44 LinuxServerName kernel: [84805.146384] pcnet32: 1 cards_found.
Apr 16 10:41:44 LinuxServerName kernel: [84805.146785] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 16 10:41:44 LinuxServerName kernel: [84805.146941] mptbase: Initiating ioc0 bringup
Apr 16 10:41:44 LinuxServerName kernel: [84805.402665] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:41:44 LinuxServerName kernel: [84805.811628] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
Apr 16 10:41:44 LinuxServerName kernel: [84806.160814] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:41:44 LinuxServerName kernel: [84806.160970]  target0:0:0: Beginning Domain Validation
Apr 16 10:41:44 LinuxServerName kernel: [84806.161125]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:41:44 LinuxServerName kernel: [84806.161177]  target0:0:0: Ending Domain Validation
Apr 16 10:41:44 LinuxServerName kernel: [84806.161333]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:41:44 LinuxServerName kernel: [84806.177775] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:41:44 LinuxServerName kernel: [84806.177931] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:41:44 LinuxServerName kernel: [84806.200971] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84806.201127] sda: test WP failed, assume Write Enabled
Apr 16 10:41:44 LinuxServerName kernel: [84806.201283] sda: cache data unavailable
Apr 16 10:41:44 LinuxServerName kernel: [84806.201467] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:41:44 LinuxServerName kernel: [84806.201558] sda: test WP failed, assume Write Enabled
Apr 16 10:41:44 LinuxServerName kernel: [84806.201591] sda: cache data unavailable
Apr 16 10:41:44 LinuxServerName kernel: [84806.201749]  sda: sda1 sda2 < sda5 >
Apr 16 10:41:44 LinuxServerName kernel: [84806.206582] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:41:44 LinuxServerName kernel: [84806.210504] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:41:44 LinuxServerName kernel: [84806.366080] Attempting manual resume
Apr 16 10:41:44 LinuxServerName kernel: [84806.382024] kjournald starting.  Commit interval 5 seconds
Apr 16 10:41:44 LinuxServerName kernel: [84806.382323] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:41:44 LinuxServerName kernel: [84806.623591] parport: PnPBIOS parport detected.
Apr 16 10:41:44 LinuxServerName kernel: [84806.623747] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:41:44 LinuxServerName kernel: [84806.718891] lp0: using parport0 (interrupt-driven).
Apr 16 10:41:44 LinuxServerName kernel: [84806.740018] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:41:44 LinuxServerName kernel: [84806.753558] EXT3 FS on sda1, internal journal
Apr 16 10:41:44 LinuxServerName kernel: [84806.818354] eth0: link up
Apr 16 10:41:44 LinuxServerName kernel: [84808.024839] NET: Registered protocol family 10
Apr 16 10:41:44 LinuxServerName kernel: [84808.024995] lo: Disabled Privacy Extensions
Apr 16 10:42:15 LinuxServerName exiting on signal 15
Apr 16 10:48:37 LinuxServerName syslogd 1.4.1#20ubuntu4: restart.
Apr 16 10:48:37 LinuxServerName kernel: Inspecting /boot/System.map-2.6.20-16-server
Apr 16 10:48:37 LinuxServerName kernel: Loaded 25139 symbols from /boot/System.map-2.6.20-16-server.
Apr 16 10:48:37 LinuxServerName kernel: Symbols match kernel version 2.6.20.
Apr 16 10:48:37 LinuxServerName kernel: No module symbols loaded - kernel modules not enabled. 
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Linux version 2.6.20-16-server (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:48:21 UTC 2008 (Ubuntu 2.6.20-16.35-server)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] sanitize start
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] sanitize end
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000ca000 size: 0000000000002000 end: 00000000000cc000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001fef0000 size: 000000000000f000 end: 000000001feff000 type: 3
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001feff000 size: 0000000000001000 end: 000000001ff00000 type: 4
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 1
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] 0MB HIGHMEM available.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] 512MB LOWMEM available.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] found SMP MP-table at 000f6cd0
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Zone PFN ranges:
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   DMA             0 ->     4096
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   Normal       4096 ->   131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]   HighMem    131072 ->   131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000]     0:        0 ->   131072
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] DMI present.
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Processor #0 15:6 APIC version 17
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Apr 16 10:48:37 LinuxServerName kernel: [    0.000000] Detected 3391.040 MHz processor.
Apr 16 10:48:37 LinuxServerName kernel: [85226.667998] Built 1 zonelists.  Total pages: 130048
Apr 16 10:48:37 LinuxServerName kernel: [85226.668177] Kernel command line: root=UUID=b51e92b2-eb34-45e2-849c-beee4a1e0383 ro quiet splash
Apr 16 10:48:37 LinuxServerName kernel: [85226.669492] Enabling fast FPU save and restore... done.
Apr 16 10:48:37 LinuxServerName kernel: [85226.669561] Enabling unmasked SIMD FPU exception support... done.
Apr 16 10:48:37 LinuxServerName kernel: [85226.669885] Initializing CPU#0
Apr 16 10:48:37 LinuxServerName kernel: [85226.671410] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85226.671566] Console: colour VGA+ 80x25
Apr 16 10:48:37 LinuxServerName kernel: [85226.671721] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85226.671877] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681597] Memory: 508816k/524288k available (2020k kernel code, 14876k reserved, 901k data, 332k init, 0k highmem)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681655] virtual kernel memory layout:
Apr 16 10:48:37 LinuxServerName kernel: [85226.681660]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681663]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681664]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681666]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681667]       .init : 0xc03e1000 - 0xc0434000   ( 332 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681669]       .data : 0xc02f9319 - 0xc03da754   ( 901 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681671]       .text : 0xc0100000 - 0xc02f9319   (2020 kB)
Apr 16 10:48:37 LinuxServerName kernel: [85226.681727] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 16 10:48:37 LinuxServerName kernel: [85226.831025] Calibrating delay using timer specific routine.. 6814.72 BogoMIPS (lpj=34073630)
Apr 16 10:48:37 LinuxServerName kernel: [85226.831180] Security Framework v1.0.0 initialized
Apr 16 10:48:37 LinuxServerName kernel: [85226.831336] SELinux:  Disabled at boot.
Apr 16 10:48:37 LinuxServerName kernel: [85226.831492] Mount-cache hash table entries: 512
Apr 16 10:48:37 LinuxServerName kernel: [85226.831803] CPU: Trace cache: 12K uops, L1 D cache: 16K
Apr 16 10:48:37 LinuxServerName kernel: [85226.831853] CPU: L2 cache: 1024K
Apr 16 10:48:37 LinuxServerName kernel: [85226.831875] CPU: L3 cache: 16384K
Apr 16 10:48:37 LinuxServerName kernel: [85226.832187] Compat vDSO mapped to ffffe000.
Apr 16 10:48:37 LinuxServerName kernel: [85226.832242] Remapping vsyscall page to ffffe000
Apr 16 10:48:37 LinuxServerName kernel: [85226.832398] Checking 'hlt' instruction... OK.
Apr 16 10:48:37 LinuxServerName kernel: [85226.870878] SMP alternatives: switching to UP code
Apr 16 10:48:37 LinuxServerName kernel: [85226.871034] Freeing SMP alternatives: 11k freed
Apr 16 10:48:37 LinuxServerName kernel: [85226.871190] Early unpacking initramfs... done
Apr 16 10:48:37 LinuxServerName kernel: [85227.050317] ACPI: Core revision 20060707
Apr 16 10:48:37 LinuxServerName kernel: [85227.050472] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 16 10:48:37 LinuxServerName kernel: [85227.060898] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 08
Apr 16 10:48:37 LinuxServerName kernel: [85227.061054] Total of 1 processors activated (6814.72 BogoMIPS).
Apr 16 10:48:37 LinuxServerName kernel: [85227.061210] ENABLING IO-APIC IRQs
Apr 16 10:48:37 LinuxServerName kernel: [85227.061622] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Brought up 1 CPUs
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Booting paravirtualized kernel on bare hardware
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Time: 14:48:50  Date: 03/16/108
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] NET: Registered protocol family 16
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] EISA bus registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] ACPI: bus type pci registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] PCI: Using configuration type 1
Apr 16 10:48:37 LinuxServerName kernel: [85227.279444] Setting up standard PCI resources
Apr 16 10:48:37 LinuxServerName kernel: [85227.279600] ACPI: Interpreter enabled
Apr 16 10:48:37 LinuxServerName kernel: [85227.279639] ACPI: Using IOAPIC for interrupt routing
Apr 16 10:48:37 LinuxServerName kernel: [85227.281499] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] PCI quirk: region 1040-104f claimed by PIIX4 SMB
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Apr 16 10:48:37 LinuxServerName kernel: [85227.289414] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.293588] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 16 10:48:37 LinuxServerName kernel: [85227.293670] pnp: PnP ACPI init
Apr 16 10:48:37 LinuxServerName kernel: [85227.310437] pnp: PnP ACPI: found 12 devices
Apr 16 10:48:37 LinuxServerName kernel: [85227.310535] PnPBIOS: Disabled by ACPI PNP
Apr 16 10:48:37 LinuxServerName kernel: [85227.310872] PCI: Using ACPI for IRQ routing
Apr 16 10:48:37 LinuxServerName kernel: [85227.310986] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NET: Registered protocol family 8
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NET: Registered protocol family 20
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel: Initializing
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel:  domain hash size = 128
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NetLabel:  unlabeled traffic allowed by default
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] PCI: Bridge: 0000:00:01.0
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321]   IO window: disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321]   MEM window: disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321]   PREFETCH window: disabled.
Apr 16 10:48:37 LinuxServerName kernel: [85227.319321] NET: Registered protocol family 2
Apr 16 10:48:37 LinuxServerName kernel: [85227.419242] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419398] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419553] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419709] TCP: Hash tables configured (established 65536 bind 32768)
Apr 16 10:48:37 LinuxServerName kernel: [85227.419817] TCP reno registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.449097] checking if image is initramfs... it is
Apr 16 10:48:37 LinuxServerName kernel: [85227.857824] Freeing initrd memory: 6642k freed
Apr 16 10:48:37 LinuxServerName kernel: [85227.858528] Simple Boot Flag at 0x36 set to 0x1
Apr 16 10:48:37 LinuxServerName kernel: [85227.860206] audit: initializing netlink socket (disabled)
Apr 16 10:48:37 LinuxServerName kernel: [85227.860361] audit(1208357331.050:1): initialized
Apr 16 10:48:37 LinuxServerName kernel: [85227.861393] VFS: Disk quotas dquot_6.5.1
Apr 16 10:48:37 LinuxServerName kernel: [85227.861525] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 16 10:48:37 LinuxServerName kernel: [85227.861681] io scheduler noop registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.861774] io scheduler anticipatory registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.861787] io scheduler deadline registered (default)
Apr 16 10:48:37 LinuxServerName kernel: [85227.861903] io scheduler cfq registered
Apr 16 10:48:37 LinuxServerName kernel: [85227.862059] Limiting direct PCI/PCI transfers.
Apr 16 10:48:37 LinuxServerName kernel: [85227.862774] isapnp: Scanning for PnP cards...
Apr 16 10:48:37 LinuxServerName kernel: [85228.221555] isapnp: No Plug & Play device found
Apr 16 10:48:37 LinuxServerName kernel: [85228.260852] Real Time Clock Driver v1.12ac
Apr 16 10:48:37 LinuxServerName kernel: [85228.261061] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 16 10:48:37 LinuxServerName kernel: [85228.261572] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.262000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.263185] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.263779] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 16 10:48:37 LinuxServerName kernel: [85228.264449] mice: PS/2 mouse device common for all mice
Apr 16 10:48:37 LinuxServerName kernel: [85228.266405] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 16 10:48:37 LinuxServerName kernel: [85228.266405] input: Macintosh mouse button emulation as /class/input/input0
Apr 16 10:48:37 LinuxServerName kernel: [85228.266406] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 16 10:48:37 LinuxServerName kernel: [85228.266406] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 16 10:48:37 LinuxServerName kernel: [85228.266406] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] EISA: Probing bus 0 at eisa.0
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] Cannot allocate resource for EISA slot 1
Apr 16 10:48:37 LinuxServerName kernel: [85228.774840] EISA: Detected 0 cards.
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] TCP cubic registered
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] NET: Registered protocol family 1
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] Using IPI No-Shortcut mode
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] ACPI: (supports S0 S1 S4 S5)
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748]   Magic number: 4:461:839
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748]   hash matches device ptyu5
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] Freeing unused kernel memory: 332k freed
Apr 16 10:48:37 LinuxServerName kernel: [85228.804748] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 16 10:48:37 LinuxServerName kernel: [85228.804891] Time: tsc clocksource has been installed.
Apr 16 10:48:37 LinuxServerName kernel: [85228.986042] Capability LSM initialized
Apr 16 10:48:37 LinuxServerName kernel: [85229.015637] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 16 10:48:37 LinuxServerName kernel: [85229.015792] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:48:37 LinuxServerName kernel: [85229.015926] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:48:37 LinuxServerName kernel: [85229.015968] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Apr 16 10:48:37 LinuxServerName kernel: [85229.632926] PIIX4: IDE controller at PCI slot 0000:00:07.1
Apr 16 10:48:37 LinuxServerName kernel: [85229.633082] PIIX4: chipset revision 1
Apr 16 10:48:37 LinuxServerName kernel: [85229.633148] PIIX4: not 100%% native mode: will probe irqs later
Apr 16 10:48:37 LinuxServerName kernel: [85229.633304]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
Apr 16 10:48:37 LinuxServerName kernel: [85229.674111] SCSI subsystem initialized
Apr 16 10:48:37 LinuxServerName kernel: [85229.674637] Fusion MPT base driver 3.04.03
Apr 16 10:48:37 LinuxServerName kernel: [85229.674657] Copyright (c) 1999-2007 LSI Logic Corporation
Apr 16 10:48:37 LinuxServerName kernel: [85229.675227] Fusion MPT SPI Host driver 3.04.03
Apr 16 10:48:37 LinuxServerName kernel: [85229.713241] pcnet32.c:v1.33 27.Jun.2006 tsbogend@alpha.franken.de
Apr 16 10:48:37 LinuxServerName kernel: [85229.724662] Floppy drive(s): fd0 is 1.44M
Apr 16 10:48:37 LinuxServerName kernel: [85229.752342] FDC 0 is a post-1991 82077
Apr 16 10:48:37 LinuxServerName kernel: [85230.539573] hda: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM drive
Apr 16 10:48:37 LinuxServerName kernel: [85230.908765] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 16 10:48:37 LinuxServerName kernel: [85230.910666] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 16 10:48:37 LinuxServerName kernel: [85230.910822] mptbase: Initiating ioc0 bringup
Apr 16 10:48:37 LinuxServerName kernel: [85231.177606] ioc0: 53C1030: Capabilities={Initiator}
Apr 16 10:48:37 LinuxServerName kernel: [85231.636415] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=16
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895] scsi 0:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: Beginning Domain Validation
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: Domain Validation skipping write tests
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: Ending Domain Validation
Apr 16 10:48:37 LinuxServerName kernel: [85232.004895]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Apr 16 10:48:37 LinuxServerName kernel: [85232.012946] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 17
Apr 16 10:48:37 LinuxServerName kernel: [85232.013102] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 88 02 7a assigned IRQ 17.
Apr 16 10:48:37 LinuxServerName kernel: [85232.015184] eth0: registered as PCnet/PCI II 79C970A
Apr 16 10:48:37 LinuxServerName kernel: [85232.015340] pcnet32: 1 cards_found.
Apr 16 10:48:37 LinuxServerName kernel: [85232.040449] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85232.040605] sda: test WP failed, assume Write Enabled
Apr 16 10:48:37 LinuxServerName kernel: [85232.040761] sda: cache data unavailable
Apr 16 10:48:37 LinuxServerName kernel: [85232.040964] SCSI device sda: 83886080 512-byte hdwr sectors (42950 MB)
Apr 16 10:48:37 LinuxServerName kernel: [85232.041064] sda: test WP failed, assume Write Enabled
Apr 16 10:48:37 LinuxServerName kernel: [85232.041098] sda: cache data unavailable
Apr 16 10:48:37 LinuxServerName kernel: [85232.041252]  sda: sda1 sda2 < sda5 >
Apr 16 10:48:37 LinuxServerName kernel: [85232.046678] sd 0:0:0:0: Attached scsi disk sda
Apr 16 10:48:37 LinuxServerName kernel: [85232.051055] hda: ATAPI 1X CD-ROM drive, 32kB Cache, UDMA(33)
Apr 16 10:48:37 LinuxServerName kernel: [85232.051211] Uniform CD-ROM driver Revision: 3.20
Apr 16 10:48:37 LinuxServerName kernel: [85232.068502] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 10:48:37 LinuxServerName kernel: [85232.221303] Attempting manual resume
Apr 16 10:48:37 LinuxServerName kernel: [85232.236871] kjournald starting.  Commit interval 5 seconds
Apr 16 10:48:37 LinuxServerName kernel: [85232.237162] EXT3-fs: mounted filesystem with ordered data mode.
Apr 16 10:48:37 LinuxServerName kernel: [85232.494304] parport: PnPBIOS parport detected.
Apr 16 10:48:37 LinuxServerName kernel: [85232.494460] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Apr 16 10:48:37 LinuxServerName kernel: [85232.593512] lp0: using parport0 (interrupt-driven).
Apr 16 10:48:37 LinuxServerName kernel: [85232.616610] Adding 1502036k swap on /dev/disk/by-uuid/16a84ef5-c17d-4771-9925-f4cf328e374f.  Priority:-1 extents:1 across:1502036k
Apr 16 10:48:37 LinuxServerName kernel: [85232.630036] EXT3 FS on sda1, internal journal
Apr 16 10:48:37 LinuxServerName kernel: [85232.693089] eth0: link up
Apr 16 10:48:37 LinuxServerName kernel: [85233.799781] NET: Registered protocol family 10
Apr 16 10:48:37 LinuxServerName kernel: [85233.799936] lo: Disabled Privacy Extensions
Apr 16 10:50:41 LinuxServerName exiting on signal 15

```

---

