---
title: "I keep getting kicked out from remote SSH session (could it be PAM?)"
date: 2007-08-20
forum: Server Platforms
---

### Post by frippz on 2007-08-20
I got this server installed and ready the other week (Ubuntu 7.04) and this problem showed up when I returned to work after the weekend.

I log in via remote SSH from my Mac (using iTerm or Terminal.app makes no difference) and after maybe an hour or so I get kicked out and can't log back in with error message "ssh: connect to host xxx.xx.xx.xx port 22: Connection refused".

I can still ping the server. Incidentally, the web sites we have set up starts to ask for a password, even though no .htaccess rules are in place for it. The browser says "Enter a username and password for 'device' at <domain name>". Very odd indeed.

I had to run over to the server room and log in at the physical terminal (wich seems to work just fine) and then I am able to log back in via remote SSH. Not really sure if there is a connection though between these events.

Here's the output from /var/log/auth.log (usernames and IP adresses changed to <username> and xxx.xx.xx.xxx)

```
Aug 20 14:16:35 develop5 smbd[8650]: (pam_unix) session closed for user <username>           
Aug 20 14:17:01 develop5 CRON[8919]: (pam_unix) session opened for user root by (uid=0)
Aug 20 14:17:01 develop5 CRON[8919]: (pam_unix) session closed for user root
Aug 20 14:31:06 develop5 login[8627]: (pam_unix) session opened for user <username> by (uid=0)
Aug 20 14:31:13 develop5 login[8627]: (pam_unix) session closed for user <username>
Aug 20 14:32:57 develop5 login[8939]: (pam_unix) session opened for user <username> by (uid=0)
Aug 20 14:37:35 develop5 login[8939]: (pam_unix) session closed for user <username>
Aug 20 14:38:42 develop5 login[8957]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=tty1 ruser= rhost=  user=<username>
Aug 20 14:38:45 develop5 login[8957]: FAILED LOGIN (1) on 'tty1' FOR `<username>', Authentication failure
Aug 20 14:38:57 develop5 login[8957]: (pam_unix) check pass; user unknown
Aug 20 14:38:57 develop5 login[8957]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=tty1 ruser= rhost=
Aug 20 14:38:59 develop5 login[8957]: FAILED LOGIN (2) on 'tty1' FOR `UNKNOWN', User not known to the underlying authentication module
Aug 20 14:39:01 develop5 CRON[8958]: (pam_unix) session opened for user root by (uid=0)
Aug 20 14:39:01 develop5 CRON[8958]: (pam_unix) session closed for user root
Aug 20 14:39:06 develop5 login[8957]: (pam_unix) session opened for user <username> by (uid=0)
Aug 20 14:39:29 develop5 sshd[8982]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.15.86.192  user=<username>
Aug 20 14:39:31 develop5 sshd[8982]: Failed password for <username> from 193.xx.xx.192 port 58746 ssh2
Aug 20 14:39:34 develop5 sshd[8982]: Accepted password for <username> from 193.xx.xx.192 port 58746 ssh2
Aug 20 14:39:34 develop5 sshd[8984]: (pam_unix) session opened for user <username> by (uid=0)          
Aug 20 14:39:36 develop5 sshd[8984]: (pam_unix) session closed for user <username>           
Aug 20 14:39:52 develop5 login[8957]: (pam_unix) session closed for user <username>
Aug 20 14:40:05 develop5 sshd[9004]: Accepted password for <username> from 193.xx.xx.192 port 58764 ssh2
Aug 20 14:40:05 develop5 sshd[9006]: (pam_unix) session opened for user <username> by (uid=0)
Aug 20 14:40:06 develop5 sshd[9006]: (pam_unix) session closed for user <username>           
Aug 20 14:41:09 develop5 sshd[9024]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.15.86.40  user=<username>
Aug 20 14:41:12 develop5 sshd[9024]: Failed password for <username> from 193.xx.xx.40 port 50600 ssh2
Aug 20 14:41:23 develop5 sshd[9028]: Accepted password for <username> from 193.xx.xx.40 port 50604 ssh2
Aug 20 14:41:23 develop5 sshd[9030]: (pam_unix) session opened for user <username> by (uid=0)
```

I do believe that some entries are the result of me inputting the password wrong, so please disregard those. I was probably just stressed. :)

Now, from what I can tell, PAM seems to have some sort of problem here, but I can't for the life of me figure out what exactly.

I also checked Apache's logs for clues but couldn't find anything of significance (basically nothing was logged since 11:40 AM).

---

### Post by frippz on 2007-08-21
A little update: I just noticed that my Samba connection to the server gets severed at the same time that I get kicked off the SSH session. Something probably goes completely haywire on the server and revokes all privileges.

I'd really like to put this dev server into production status, but as long as this happens, I can't do that. :(

---

### Post by Mr. C. on 2007-08-21
This seems like a network dropping issue.  

Do you have a static IP ?

Have you verified no network problems ?  If not, run a constant ping to the server in question, and watch for a correlation between your disconnects and dropped ping packets.

Have you looked at the status of your NIC ?  Run ifconfig -a and look at the stats.

Any messages in /var/log/messages or /var/log/syslog regarding the network bounces (down / up) ?

Your samba and ssh connections are long-term connections, so will be affected when the network drops.  Your http connections are stateless, so are not affected, so long as the network comes back up.

MrC

---

### Post by frippz on 2007-08-21
I'm not sure it has to do with the network. Eventhough the SSH server refuses connection, I can ping the machine. Apache still responds to HTTP requests, yet it asks for a password. I checked the logs you mentioned but found nothing that says anything about the NIC going down.

This is very peculiar...

---

### Post by Mr. C. on 2007-08-21
You may be able to ping the network *after* it has bounced, but a few pings does not prove the network stable.

Apache will also response *after* the network has bounced.  It is resilient to transient errors where as long-term connection-oriented protocols are not.

The problem could be anything from a duplicate IP address, packet loss, or IP reassignment.

I don't see any stats from the suggestions I made, so I cannot rule out these possibilities.  You must first *prove* the network stable before moving to higher-level protocols and diagnostics.

MrC

---

### Post by frippz on 2007-08-21
Ok, the server just kicked me again (around 10:00 PM). Silly me, not having my regular drink of coffee, I never did check syslog properly. Here are the logs you requested:

/var/log/messages since last reboot the same day
```
Aug 21 13:30:37 develop5 syslogd 1.4.1#20ubuntu4: restart.
Aug 21 13:30:37 develop5 kernel: Inspecting /boot/System.map-2.6.20-15-server
Aug 21 13:30:38 develop5 kernel: Loaded 25134 symbols from /boot/System.map-2.6.20-15-server.
Aug 21 13:30:38 develop5 kernel: Symbols match kernel version 2.6.20.
Aug 21 13:30:38 develop5 kernel: No module symbols loaded - kernel modules not enabled. 
Aug 21 13:30:38 develop5 kernel: [    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
Aug 21 13:30:38 develop5 kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 21 13:30:38 develop5 kernel: [    0.000000] sanitize start
Aug 21 13:30:38 develop5 kernel: [    0.000000] sanitize end
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fefd800 end: 000000001fffd800 type: 1
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 000000001fffd800 size: 0000000000002400 end: 000000001ffffc00 type: 3
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 000000001ffffc00 size: 0000000000000400 end: 0000000020000000 type: 4
Aug 21 13:30:38 develop5 kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffd800 (usable)
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 000000001fffd800 - 000000001ffffc00 (ACPI data)
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 000000001ffffc00 - 0000000020000000 (ACPI NVS)
Aug 21 13:30:38 develop5 kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Aug 21 13:30:38 develop5 kernel: [    0.000000] 0MB HIGHMEM available.
Aug 21 13:30:38 develop5 kernel: [    0.000000] 511MB LOWMEM available.
Aug 21 13:30:38 develop5 kernel: [    0.000000] Zone PFN ranges:
Aug 21 13:30:38 develop5 kernel: [    0.000000]   DMA             0 ->     4096
Aug 21 13:30:38 develop5 kernel: [    0.000000]   Normal       4096 ->   131069
Aug 21 13:30:38 develop5 kernel: [    0.000000]   HighMem    131069 ->   131069
Aug 21 13:30:38 develop5 kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 21 13:30:38 develop5 kernel: [    0.000000]     0:        0 ->   131069
Aug 21 13:30:38 develop5 kernel: [    0.000000] DMI not present or invalid.
Aug 21 13:30:38 develop5 kernel: [    0.000000] ACPI: Disabling ACPI support
Aug 21 13:30:38 develop5 kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
Aug 21 13:30:38 develop5 kernel: [    0.000000] Detected 797.590 MHz processor.
Aug 21 13:30:38 develop5 kernel: [   34.170494] Built 1 zonelists.  Total pages: 130046
Aug 21 13:30:38 develop5 kernel: [   34.170502] Kernel command line: root=UUID=9f7d77bf-fd12-4525-8ab4-a1837ec7c1d8 ro quiet splash
Aug 21 13:30:38 develop5 kernel: [   34.170995] Local APIC disabled by BIOS -- you can enable it with "lapic"
Aug 21 13:30:38 develop5 kernel: [   34.171022] Enabling fast FPU save and restore... done.
Aug 21 13:30:38 develop5 kernel: [   34.171029] Enabling unmasked SIMD FPU exception support... done.
Aug 21 13:30:38 develop5 kernel: [   34.171049] Initializing CPU#0
Aug 21 13:30:38 develop5 kernel: [   34.171139] PID hash table entries: 2048 (order: 11, 8192 bytes)
Aug 21 13:30:38 develop5 kernel: [   34.172629] Console: colour VGA+ 80x25
Aug 21 13:30:38 develop5 kernel: [   34.173612] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 21 13:30:38 develop5 kernel: [   34.174899] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 21 13:30:38 develop5 kernel: [   34.226639] Memory: 508828k/524276k available (2020k kernel code, 14868k reserved, 893k data, 328k init, 0k highmem)
Aug 21 13:30:38 develop5 kernel: [   34.226668] virtual kernel memory layout:
Aug 21 13:30:38 develop5 kernel: [   34.226672]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Aug 21 13:30:38 develop5 kernel: [   34.226676]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Aug 21 13:30:38 develop5 kernel: [   34.226680]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Aug 21 13:30:38 develop5 kernel: [   34.226683]     lowmem  : 0xc0000000 - 0xdfffd000   ( 511 MB)
Aug 21 13:30:38 develop5 kernel: [   34.226687]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
Aug 21 13:30:38 develop5 kernel: [   34.226691]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
Aug 21 13:30:38 develop5 kernel: [   34.226694]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
Aug 21 13:30:38 develop5 kernel: [   34.226704] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 21 13:30:38 develop5 kernel: [   34.371000] Calibrating delay using timer specific routine.. 1596.10 BogoMIPS (lpj=7980506)
Aug 21 13:30:38 develop5 kernel: [   34.371111] Security Framework v1.0.0 initialized
Aug 21 13:30:38 develop5 kernel: [   34.371130] SELinux:  Disabled at boot.
Aug 21 13:30:38 develop5 kernel: [   34.371172] Mount-cache hash table entries: 512
Aug 21 13:30:38 develop5 kernel: [   34.371513] CPU: L1 I cache: 16K, L1 D cache: 16K
Aug 21 13:30:38 develop5 kernel: [   34.371520] CPU: L2 cache: 256K
Aug 21 13:30:38 develop5 kernel: [   34.371554] Compat vDSO mapped to ffffe000.
Aug 21 13:30:38 develop5 kernel: [   34.371572] Remapping vsyscall page to ffffe000
Aug 21 13:30:38 develop5 kernel: [   34.371596] Checking 'hlt' instruction... OK.
Aug 21 13:30:38 develop5 kernel: [   34.411181] SMP alternatives: switching to UP code
Aug 21 13:30:38 develop5 kernel: [   34.411547] Freeing SMP alternatives: 11k freed
Aug 21 13:30:38 develop5 kernel: [   34.411989] Early unpacking initramfs... done
Aug 21 13:30:38 develop5 kernel: [   35.137884] CPU0: Intel Pentium III (Coppermine) stepping 06
Aug 21 13:30:38 develop5 kernel: [   35.137902] SMP motherboard not detected.
Aug 21 13:30:38 develop5 kernel: [   35.137908] Local APIC not detected. Using dummy APIC emulation.
Aug 21 13:30:38 develop5 kernel: [   35.138023] Brought up 1 CPUs
Aug 21 13:30:38 develop5 kernel: [   35.138644] Booting paravirtualized kernel on bare hardware
Aug 21 13:30:38 develop5 kernel: [   35.138822] Time: 11:30:13  Date: 07/21/107
Aug 21 13:30:38 develop5 kernel: [   35.138909] NET: Registered protocol family 16
Aug 21 13:30:38 develop5 kernel: [   35.139164] EISA bus registered
Aug 21 13:30:38 develop5 kernel: [   35.153357] PCI: PCI BIOS revision 2.10 entry at 0xfd994, last bus=1
Aug 21 13:30:38 develop5 kernel: [   35.153364] PCI: Using configuration type 1
Aug 21 13:30:38 develop5 kernel: [   35.153370] Setting up standard PCI resources
Aug 21 13:30:38 develop5 kernel: [   35.157324] ACPI: Interpreter disabled.
Aug 21 13:30:38 develop5 kernel: [   35.157335] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 21 13:30:38 develop5 kernel: [   35.157354] pnp: PnP ACPI: disabled
Aug 21 13:30:38 develop5 kernel: [   35.157361] PnPBIOS: Scanning system for PnP BIOS support...
Aug 21 13:30:38 develop5 kernel: [   35.157413] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6d50
Aug 21 13:30:38 develop5 kernel: [   35.157422] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa178, dseg 0x400
Aug 21 13:30:38 develop5 kernel: [   35.161465] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
Aug 21 13:30:38 develop5 kernel: [   35.161600] PCI: Probing PCI hardware
Aug 21 13:30:38 develop5 kernel: [   35.161952] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
Aug 21 13:30:38 develop5 kernel: [   35.161957] * this clock source is slow. Consider trying other clock sources
Aug 21 13:30:38 develop5 kernel: [   35.162009] PCI quirk: region f0c0-f0ff claimed by PIIX4 ACPI
Aug 21 13:30:38 develop5 kernel: [   35.162018] PCI quirk: region f0b0-f0bf claimed by PIIX4 SMB
Aug 21 13:30:38 develop5 kernel: [   35.162078] PCI: Firmware left 0000:00:0d.0 e100 interrupts enabled, disabling
Aug 21 13:30:38 develop5 kernel: [   35.163392] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
Aug 21 13:30:38 develop5 kernel: [   35.164890] NET: Registered protocol family 8
Aug 21 13:30:38 develop5 kernel: [   35.164897] NET: Registered protocol family 20
Aug 21 13:30:38 develop5 kernel: [   35.164920] NetLabel: Initializing
Aug 21 13:30:38 develop5 kernel: [   35.164925] NetLabel:  domain hash size = 128
Aug 21 13:30:38 develop5 kernel: [   35.164929] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 21 13:30:38 develop5 kernel: [   35.164967] NetLabel:  unlabeled traffic allowed by default
Aug 21 13:30:38 develop5 kernel: [   35.165118] pnp: 00:00: ioport range 0x370-0x371 has been reserved
Aug 21 13:30:38 develop5 kernel: [   35.165157] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Aug 21 13:30:38 develop5 kernel: [   35.165166] pnp: 00:0a: ioport range 0xf0c0-0xf0ff has been reserved
Aug 21 13:30:38 develop5 kernel: [   35.165174] pnp: 00:0a: ioport range 0xf0b0-0xf0bf has been reserved
Aug 21 13:30:38 develop5 kernel: [   35.165981] PCI: Bridge: 0000:00:01.0
Aug 21 13:30:38 develop5 kernel: [   35.165987]   IO window: disabled.
Aug 21 13:30:38 develop5 kernel: [   35.165996]   MEM window: fe000000-febfffff
Aug 21 13:30:38 develop5 kernel: [   35.166005]   PREFETCH window: f6000000-f6ffffff
Aug 21 13:30:38 develop5 kernel: [   35.166078] NET: Registered protocol family 2
Aug 21 13:30:38 develop5 kernel: [   35.250568] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug 21 13:30:38 develop5 kernel: [   35.250783] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug 21 13:30:38 develop5 kernel: [   35.251217] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Aug 21 13:30:38 develop5 kernel: [   35.251490] TCP: Hash tables configured (established 16384 bind 8192)
Aug 21 13:30:38 develop5 kernel: [   35.251498] TCP reno registered
Aug 21 13:30:38 develop5 kernel: [   35.280705] checking if image is initramfs... it is
Aug 21 13:30:38 develop5 kernel: [   36.670943] Freeing initrd memory: 6643k freed
Aug 21 13:30:38 develop5 kernel: [   36.671897] audit: initializing netlink socket (disabled)
Aug 21 13:30:38 develop5 kernel: [   36.671930] audit(1187695815.460:1): initialized
Aug 21 13:30:38 develop5 kernel: [   36.672209] VFS: Disk quotas dquot_6.5.1
Aug 21 13:30:38 develop5 kernel: [   36.672264] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 21 13:30:38 develop5 kernel: [   36.672386] io scheduler noop registered
Aug 21 13:30:38 develop5 kernel: [   36.672394] io scheduler anticipatory registered
Aug 21 13:30:38 develop5 kernel: [   36.672400] io scheduler deadline registered (default)
Aug 21 13:30:38 develop5 kernel: [   36.672430] io scheduler cfq registered
Aug 21 13:30:38 develop5 kernel: [   36.672449] Limiting direct PCI/PCI transfers.
Aug 21 13:30:38 develop5 kernel: [   36.672896] isapnp: Scanning for PnP cards...
Aug 21 13:30:38 develop5 kernel: [   37.029536] isapnp: No Plug & Play device found
Aug 21 13:30:38 develop5 kernel: [   37.108820] Real Time Clock Driver v1.12ac
Aug 21 13:30:38 develop5 kernel: [   37.109001] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 21 13:30:38 develop5 kernel: [   37.109283] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 21 13:30:38 develop5 kernel: [   37.111954] pnp: Device 00:0f activated.
Aug 21 13:30:38 develop5 kernel: [   37.112224] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Aug 21 13:30:38 develop5 kernel: [   37.112808] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 21 13:30:38 develop5 kernel: [   37.113386] mice: PS/2 mouse device common for all mice
Aug 21 13:30:38 develop5 kernel: [   37.114864] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 21 13:30:38 develop5 kernel: [   37.115462] input: Macintosh mouse button emulation as /class/input/input0
Aug 21 13:30:38 develop5 kernel: [   37.115554] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 21 13:30:38 develop5 kernel: [   37.115565] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 21 13:30:38 develop5 kernel: [   37.115981] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
Aug 21 13:30:38 develop5 kernel: [   37.115990] PNP: PS/2 controller doesn't have AUX irq; using default 12
Aug 21 13:30:38 develop5 kernel: [   37.359227] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 21 13:30:38 develop5 kernel: [   37.359635] EISA: Probing bus 0 at eisa.0
Aug 21 13:30:38 develop5 kernel: [   37.359705] EISA: Detected 0 cards.
Aug 21 13:30:38 develop5 kernel: [   37.359901] TCP cubic registered
Aug 21 13:30:38 develop5 kernel: [   37.359922] NET: Registered protocol family 1
Aug 21 13:30:38 develop5 kernel: [   37.359977] Using IPI No-Shortcut mode
Aug 21 13:30:38 develop5 kernel: [   37.360037]   Magic number: 3:234:530
Aug 21 13:30:38 develop5 kernel: [   37.361271] Freeing unused kernel memory: 328k freed
Aug 21 13:30:38 develop5 kernel: [   37.368867] Time: tsc clocksource has been installed.
Aug 21 13:30:38 develop5 kernel: [   37.377265] input: AT Translated Set 2 keyboard as /class/input/input1
Aug 21 13:30:38 develop5 kernel: [   37.782095] Capability LSM initialized
Aug 21 13:30:38 develop5 kernel: [   37.950708] thermal: Unknown symbol acpi_processor_set_thermal_limit
Aug 21 13:30:38 develop5 kernel: [   39.280314] usbcore: registered new interface driver usbfs
Aug 21 13:30:38 develop5 kernel: [   39.280370] usbcore: registered new interface driver hub
Aug 21 13:30:38 develop5 kernel: [   39.280446] usbcore: registered new device driver usb
Aug 21 13:30:38 develop5 kernel: [   39.284444] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
Aug 21 13:30:38 develop5 kernel: [   39.284453] e100: Copyright(c) 1999-2006 Intel Corporation
Aug 21 13:30:38 develop5 kernel: [   39.284544] PCI: Found IRQ 9 for device 0000:00:0d.0
Aug 21 13:30:38 develop5 kernel: [   39.284559] PCI: Sharing IRQ 9 with 0000:00:07.2
Aug 21 13:30:38 develop5 kernel: [   39.306964] e100: eth0: e100_probe: addr 0xfecff000, irq 9, MAC addr 00:30:05:06:6D:B6
Aug 21 13:30:38 develop5 kernel: [   39.310704] USB Universal Host Controller Interface driver v3.0
Aug 21 13:30:38 develop5 kernel: [   39.310791] PCI: Enabling device 0000:00:07.2 (0004 -> 0005)
Aug 21 13:30:38 develop5 kernel: [   39.310808] PCI: Found IRQ 9 for device 0000:00:07.2
Aug 21 13:30:38 develop5 kernel: [   39.310826] PCI: Sharing IRQ 9 with 0000:00:0d.0
Aug 21 13:30:38 develop5 kernel: [   39.310849] uhci_hcd 0000:00:07.2: UHCI Host Controller
Aug 21 13:30:38 develop5 kernel: [   39.311085] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Aug 21 13:30:38 develop5 kernel: [   39.311127] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000f400
Aug 21 13:30:38 develop5 kernel: [   39.311403] usb usb1: configuration #1 chosen from 1 choice
Aug 21 13:30:38 develop5 kernel: [   39.311472] hub 1-0:1.0: USB hub found
Aug 21 13:30:38 develop5 kernel: [   39.311492] hub 1-0:1.0: 2 ports detected
Aug 21 13:30:38 develop5 kernel: [   39.389576] SCSI subsystem initialized
Aug 21 13:30:38 develop5 kernel: [   39.557915] PCI: Found IRQ 10 for device 0000:00:0e.0
Aug 21 13:30:38 develop5 kernel: [   39.707326] sym0: <895a> rev 0x1 at pci 0000:00:0e.0 irq 10
Aug 21 13:30:38 develop5 kernel: [   39.709823] sym0: Symbios NVRAM, ID 7, Fast-40, LVD, parity checking
Aug 21 13:30:38 develop5 kernel: [   39.709832] sym0: open drain IRQ line driver, using on-chip SRAM
Aug 21 13:30:38 develop5 kernel: [   39.709838] sym0: using LOAD/STORE-based firmware.
Aug 21 13:30:38 develop5 kernel: [   39.709843] sym0: handling phase mismatch from SCRIPTS.
Aug 21 13:30:38 develop5 kernel: [   39.716494] sym0: SCSI BUS has been reset.
Aug 21 13:30:38 develop5 kernel: [   39.716502] scsi0 : sym-2.2.3
Aug 21 13:30:38 develop5 kernel: [   39.727868] PIIX4: IDE controller at PCI slot 0000:00:07.1
Aug 21 13:30:38 develop5 kernel: [   39.727901] PIIX4: chipset revision 1
Aug 21 13:30:38 develop5 kernel: [   39.727907] PIIX4: not 100%% native mode: will probe irqs later
Aug 21 13:30:38 develop5 kernel: [   39.727923]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb:pio
Aug 21 13:30:38 develop5 kernel: [   39.727945]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:pio, hdd:pio
Aug 21 13:30:38 develop5 kernel: [   39.968467] Floppy drive(s): fd0 is 1.44M
Aug 21 13:30:38 develop5 kernel: [   40.012083] FDC 0 is a post-1991 82077
Aug 21 13:30:38 develop5 kernel: [   40.546736] hda: LTN483L, ATAPI CD/DVD-ROM drive
Aug 21 13:30:38 develop5 kernel: [   40.906597] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Aug 21 13:30:38 develop5 kernel: [   41.446195] hdd: Maxtor 92049U3, ATA DISK drive
Aug 21 13:30:38 develop5 kernel: [   41.506230] ide1 at 0x170-0x177,0x376 on irq 15
Aug 21 13:30:38 develop5 kernel: [   41.553622] hda: ATAPI 48X CD-ROM drive, 120kB Cache, UDMA(33)
Aug 21 13:30:38 develop5 kernel: [   41.553642] Uniform CD-ROM driver Revision: 3.20
Aug 21 13:30:38 develop5 kernel: [   41.561751] hdd: max request size: 128KiB
Aug 21 13:30:38 develop5 kernel: [   41.584922] hdd: 40010544 sectors (20485 MB) w/2048KiB Cache, CHS=39693/16/63, UDMA(33)
Aug 21 13:30:38 develop5 kernel: [   41.584942] hdd: cache flushes not supported
Aug 21 13:30:38 develop5 kernel: [   41.585041]  hdd: hdd1
Aug 21 13:30:38 develop5 kernel: [   42.707532] scsi 0:0:0:0: Direct-Access     SEAGATE  ST39236LC        3252 PQ: 0 ANSI: 3
Aug 21 13:30:38 develop5 kernel: [   42.707555]  target0:0:0: tagged command queuing enabled, command queue depth 16.
Aug 21 13:30:38 develop5 kernel: [   42.707582]  target0:0:0: Beginning Domain Validation
Aug 21 13:30:38 develop5 kernel: [   42.707910]  target0:0:0: asynchronous
Aug 21 13:30:38 develop5 kernel: [   42.714550]  target0:0:0: wide asynchronous
Aug 21 13:30:38 develop5 kernel: [   42.717285]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 31)
Aug 21 13:30:38 develop5 kernel: [   42.720877]  target0:0:0: Domain Validation skipping write tests
Aug 21 13:30:38 develop5 kernel: [   42.720885]  target0:0:0: Ending Domain Validation
Aug 21 13:30:38 develop5 kernel: [   46.843440] SCSI device sda: 17942584 512-byte hdwr sectors (9187 MB)
Aug 21 13:30:38 develop5 kernel: [   46.845188] sda: Write Protect is off
Aug 21 13:30:38 develop5 kernel: [   46.846895] SCSI device sda: write cache: disabled, read cache: enabled, supports DPO and FUA
Aug 21 13:30:38 develop5 kernel: [   46.848029] SCSI device sda: 17942584 512-byte hdwr sectors (9187 MB)
Aug 21 13:30:38 develop5 kernel: [   46.849780] sda: Write Protect is off
Aug 21 13:30:38 develop5 kernel: [   46.851487] SCSI device sda: write cache: disabled, read cache: enabled, supports DPO and FUA
Aug 21 13:30:38 develop5 kernel: [   46.851496]  sda: sda1 sda2 < sda5 >
Aug 21 13:30:38 develop5 kernel: [   46.879063] sd 0:0:0:0: Attached scsi disk sda
Aug 21 13:30:38 develop5 kernel: [   46.894300] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 21 13:30:38 develop5 kernel: [   47.257163] Attempting manual resume
Aug 21 13:30:38 develop5 kernel: [   47.323538] kjournald starting.  Commit interval 5 seconds
Aug 21 13:30:38 develop5 kernel: [   47.323568] EXT3-fs: mounted filesystem with ordered data mode.
Aug 21 13:30:38 develop5 kernel: [   50.999364] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug 21 13:30:38 develop5 kernel: [   53.048407] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 21 13:30:38 develop5 kernel: [   53.053903] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 21 13:30:38 develop5 kernel: [   53.173699] NET: Registered protocol family 17
Aug 21 13:30:38 develop5 kernel: [   53.982595] Linux agpgart interface v0.102 (c) Dave Jones
Aug 21 13:30:38 develop5 kernel: [   54.773377] agpgart: Detected an Intel 440BX Chipset.
Aug 21 13:30:38 develop5 kernel: [   54.777522] agpgart: AGP aperture is 64M @ 0xf8000000
Aug 21 13:30:38 develop5 kernel: [   54.789788] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
Aug 21 13:30:38 develop5 kernel: [   55.039882] input: PC Speaker as /class/input/input2
Aug 21 13:30:38 develop5 kernel: [   55.360504] pnp: Device 00:13 activated.
Aug 21 13:30:38 develop5 kernel: [   55.360514] parport: PnPBIOS parport detected.
Aug 21 13:30:38 develop5 kernel: [   55.360548] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Aug 21 13:30:38 develop5 kernel: [   55.750941] lp0: using parport0 (interrupt-driven).
Aug 21 13:30:38 develop5 kernel: [   55.999105] Adding 425680k swap on /dev/disk/by-uuid/2938b3b5-1576-4d12-b021-8267d7885090.  Priority:-1 extents:1 across:425680k
Aug 21 13:30:38 develop5 kernel: [   56.175081] EXT3 FS on sda1, internal journal
Aug 21 13:30:38 develop5 kernel: [   56.742355] kjournald starting.  Commit interval 5 seconds
Aug 21 13:30:38 develop5 kernel: [   56.742734] EXT3 FS on hdd1, internal journal
Aug 21 13:30:38 develop5 kernel: [   56.742747] EXT3-fs: mounted filesystem with ordered data mode.
Aug 21 13:30:38 develop5 kernel: [   56.837140] NET: Registered protocol family 10
Aug 21 13:30:38 develop5 kernel: [   56.837382] lo: Disabled Privacy Extensions
Aug 21 13:50:37 develop5 -- MARK --
Aug 21 14:10:37 develop5 -- MARK --
Aug 21 14:30:38 develop5 -- MARK --
Aug 21 14:50:38 develop5 -- MARK --
Aug 21 15:10:39 develop5 -- MARK --
Aug 21 15:30:39 develop5 -- MARK --
Aug 21 15:50:40 develop5 -- MARK --
Aug 21 16:10:40 develop5 -- MARK --
Aug 21 16:30:41 develop5 -- MARK --
Aug 21 16:50:41 develop5 -- MARK --
Aug 21 17:10:42 develop5 -- MARK --
Aug 21 17:30:42 develop5 -- MARK --
Aug 21 17:50:43 develop5 -- MARK --
Aug 21 18:10:43 develop5 -- MARK --
Aug 21 18:30:44 develop5 -- MARK --
Aug 21 18:50:44 develop5 -- MARK --
Aug 21 19:10:44 develop5 -- MARK --
Aug 21 19:30:45 develop5 -- MARK --
Aug 21 19:50:45 develop5 -- MARK --
Aug 21 20:10:46 develop5 -- MARK --
Aug 21 20:30:46 develop5 -- MARK --
Aug 21 20:50:46 develop5 -- MARK --
Aug 21 21:10:47 develop5 -- MARK --
Aug 21 21:30:47 develop5 -- MARK --
Aug 21 21:50:48 develop5 -- MARK --
Aug 21 22:10:48 develop5 -- MARK --
```

Output from tail -f /var/log/syslog (the server took another dive just before I got the chance to fetch it)
```
Aug 21 21:51:01 develop5 /USR/SBIN/CRON[13134]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 21:56:01 develop5 /USR/SBIN/CRON[13295]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 22:01:01 develop5 /USR/SBIN/CRON[13344]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 22:06:01 develop5 /USR/SBIN/CRON[13375]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 22:09:01 develop5 /USR/SBIN/CRON[13405]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug 21 22:11:01 develop5 /USR/SBIN/CRON[13412]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 22:16:01 develop5 /USR/SBIN/CRON[13470]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 22:17:01 develop5 /USR/SBIN/CRON[13500]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 21 22:21:01 develop5 /USR/SBIN/CRON[13515]: (root) CMD (/etc/webmin/status/monitor.pl)
Aug 21 22:26:01 develop5 /USR/SBIN/CRON[13560]: (root) CMD (/etc/webmin/status/monitor.pl)
```

Fire away. ;)

edit: If this is the fault of the network dropping, could a static IP possibly fix it? We're about to ask the responsible tech to assign us a static IP (right now the server recieves an IP via DHCP just lika any other client on the intranet).

edit2: Just got kicked again (it happens more frequently now for some reason) and just thought I'd output what happened in the console:

```
user@develop5:/etc$ Read from remote host 19x.xx.xx.30: Connection reset by peer
Connection to 19x.xx.xx.30 closed.
[admin@MacServer admin] $ ssh -l user 19x.xx.xx.30
ssh: connect to host 19x.xx.xx.30 port 22: Connection refused
```

edit3: Sorry, forgot to post the output of ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:19x.xx.xx.30  Bcast:19x.xx.xx.255  Mask:255.255.255.0
          inet6 addr: xx80::xx0:5xx:xx06:6xxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59914 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16699233 (15.9 MiB)  TX bytes:18319256 (17.4 MiB)
```

---

### Post by HermanAB on 2007-08-21
If you are going through a little NAT router, then that would explain it.  The small embedded devices flush their tables every once in a while.  That will cause a SSH session to terminate.

---

### Post by Mr. C. on 2007-08-21
> **HermanAB said:**
> If you are going through a little NAT router, then that would explain it.  The small embedded devices flush their tables every once in a while.  That will cause a SSH session to terminate.

Hmmm... this sounds like voodoo.  Which "tables" do you supposed are randomly flushed?   The device would be worthless if it randomly closed open connections.  ARP entires are cleared, which is normal, and inactive or abandoned connection entries will be cleared.

Frippz,

I don't see anything suspect in your logs.  You indicated you have a dynamic IP.  There is nothing wrong with this, so long as you are sure the IP address is maintained (which it should be).

What hasn't been demonstrated is that the network stays active for a long duration (eg. longer than your sessions normally last), so we haven't ruled this out.

I would test with:

1) From some other machine on the LAN, maintain a long term ping with:

ping -i 1 SSHserverIP

where SSHserverIP is your SSH server's IP. Let it run for as long as you need to prove that either the connection is maintained, or not.  If it stays alive, when you Control-C to kill the ping, look for the packet loss.

2) Open an SSH connection to the SSH server and maintain a long term ping (like 1 above) to some other LAN client.  Check the packet loss as above.

3) If no problems are found in 1 and 2 above, set ClientAliveInterval to something like 120 or 180 (2 or 3 minutes) and restart sshd.  Re-test your connections.

4) Standard advice... ensure your router's firmware is current.  I've helped other's whose networking issues (including SSH) were caused by firmware bugs.

MrC

---

### Post by HermanAB on 2007-08-21
It is primarily a problem of cheap little home routers with low RAM.  Some routers flush their NAT tables once per hour, others once every 10 minutes.  This breaks SSL sessions.   Do some Googling and you'll find a plethora of references to this most annoying issue.  The only solution is to buy a different brand and model router.

---

### Post by James79 on 2007-08-21
frippz, I've encounted the frustrating problem that HermanAB is describing.

It occured on my older linksys, it would panick when I would join in on some high traffic torrents. Apparently the sheer number of concurrent connections caused it to panick occasionally (sometimes quite often) and it would evidentally reboot itself.

Are you running a lot of traffic thru a "cheaper/older" home router?

---

### Post by frippz on 2007-08-22
[COLOR=Black]> **Mr. C. said:**
> 
1) From some other machine on the LAN, maintain a long term ping with:

ping -i 1 SSHserverIP

where SSHserverIP is your SSH server's IP. Let it run for as long as you need to prove that either the connection is maintained, or not.  If it stays alive, when you Control-C to kill the ping, look for the packet loss.

2) Open an SSH connection to the SSH server and maintain a long term ping (like 1 above) to some other LAN client.  Check the packet loss as above.

I started to ping the Ubuntu server from the older Mac server while I pinged a Windows server from the Ubuntu server at the same time. As expected the Ubuntu server lost the SSH session and kicked me out, effectively ending the ping command. However, the pings from the older Mac server to the Ubuntu server kept running for several minutes without any packet loss at all.

> **Mr. C. said:**
> 
3) If no problems are found in 1 and 2 above, set ClientAliveInterval to something like 120 or 180 (2 or 3 minutes) and restart sshd.  Re-test your connections.

Changed the config as requested and redid the tests.[/COLOR]     [COLOR=DimGray][COLOR=Silver]Same result. SSH connection to Ubuntu server lost, but the other machine could still ping it without any packet loss.[/COLOR] [COLOR=Black]Scratch that, I redid the test and managed to not loose the SSH session. I kept the ping running for maybe 2-3 minutes. The machine that pinged the Ubuntu server had 0 lost packets while the Ubuntu server's ping to another machine had 5% loss (out of about 1000 packets sent).

[/COLOR]  [/COLOR][COLOR=Black] > **Mr. C. said:**
> 
4) Standard advice... ensure your router's firmware is current.  I've helped other's whose networking issues (including SSH) were caused by firmware bugs.

I'm not 100% sure, but I think there's a dedicated machine routing the traffic. This is a medium sized company with about a total of 30-40 employees. While I'm fairly new here, I don't think they would settle for cheap hardware in the intranet.

Besides, no other server on the intranet has ever had this kind of problem. The older Mac server that was to be replaced by the Ubuntu server never even had a hick-up. It ran both Samba and Netatalk along with Apache, MySQL, Ruby on Rails and so on and never failed even once (we're basically replacing it since it get's a little too slow for all those servers running on it :)).

What I find so odd is that every server running on the machine suddenly either stops responding (like sshd which promptly refuses connection and webmin which stops responding altogether) or starts asking for usernames and password which doesn't exist (Apache asking for user and pass for 'device', whatever 'device' means in this case, and Samba who suddenly doesn't approve the credentials that normally works). After this happens it can take anything between 1 and 15 minutes for the server to be reachable again.[/COLOR]

---

### Post by Mr. C. on 2007-08-22
Ok, good info.  Since you hadn't specifically discounted HermanAB's possible small NAT router hypothesis, I assumed you may have one between your Ubuntu server and your companies router.  It sounds like you do not, so this would not be the issue.

I assume you have 7.04 Server edition, not Workstation.  Is this correct?  The important point here is whether or not Network Manager is running (as it does in Workstation, as it attempts to configure the network when you log in to the console - this does correlate to your connection resetting and SSH thaw's when you log into the console).

Isolating and diagnosing this problem will require a little trial and error, as any of several issues can be causing this issue.  Here are your next tests:

1) Disable IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

2)  Read the following links and perform the modifications indicated.  Each link is similar, but describes the problem and solution differently:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
[http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/](http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/)
[http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551)

You'll need to perform these commands as root, so use "sudo" or equivalent to escalate your privileges.

3) Ensure there is no MTU mismatch. This is unlikely though, but possible.  If you get to this step, we'll go further.

MrC

---

### Post by frippz on 2007-08-23
Well, I got past the first point, disabling IPv6. After that, the harddrive failed horribly. I guess the machine was older than I thought. Luckily we have a spare machine (a much faster and more modern one, mind you), unto which I will install a clean system. Let's hope this one doesn't start off by kicking me all the time. :)

Mr. C, I want to thank you for taking the time to help me diagnose this problem, as well as all you other guys. ;) Too bad the machine gave up before I did. :D I did however learn quite a few things that might help in future situation. Cheers!

---

### Post by Mr. C. on 2007-08-23
Bummer.  Best of luck, and post again if the issue reoccurs.

NrC

---

