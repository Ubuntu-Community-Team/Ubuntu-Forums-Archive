---
title: "Kernel 3.7 and AMD cpu's"
date: 2012-11-19
forum: Ubuntu Development Version
---

### Post by cariboo on 2012-11-19
Just out of curiosity, how many of us with AMD cpu's are having trouble booting the the latest kernel available in the repositories?

My Intel atom powered netbook runs just fine with the 3.7.0.2 kernel.

---

### Post by P-I H on 2012-11-19
I have no problem to boot.
The installation is an upgrade from 12.04.1 to 12.10 and then with changed source list
```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by jppr on 2012-11-19
I have that problem :( I can´t boot in 3.7 kernel, system immediately freezes and gets stuck in it and not do anything any more after that

My system is... Asus motherboard, AMD Athlon 250 II 3,0 Ghz, 4 Gt DDR2 ram and Nvidia 9400 gt

---

### Post by zenarcher on 2012-11-19
I'm having boot problems with my 64 bit system...AMD processor.

zenarcher

---

### Post by rtalcott on 2012-11-19
Same here...AMD64 and it does not want to boot...however I installed the latest RC of GhostBSD and that boots/installs with no problem.

---

### Post by ronacc on 2012-11-19
AMD 64 here and no boot with the 3.7 kernel either with upgraded Quantal hd install or live cd , 3.5.0-17 boots ok

---

### Post by rtalcott on 2012-11-19
sometimes I get the error "**soft lockup cpu0...**" or something like that...I have never seen this one before....and it hangs...if it will boot I only see one core of 4.

---

### Post by jfernyhough on 2012-11-19
Not that it's a solution, but does installing amd64-microcode make any difference?

---

### Post by P-I H on 2012-11-19
I have the AMD microcode installed and is using the Nvidia 304.43 driver.

---

### Post by jfernyhough on 2012-11-19
What about mainline rc6?

:P

---

### Post by DougieFresh4U on 2012-11-19
> **jfernyhough said:**
> What about mainline rc6?

:P

Using rc6
AMD Athlon 5200 x2
3GB RAM
ATI Radeon HD 3200

very basic install, up to date and all seems well at the moment.

---

### Post by ronacc on 2012-11-19
link for the mainline rc6 please . I tried to pull it up with the link in another thread and it won't  come up with that one .

---

### Post by jfernyhough on 2012-11-19
All builds (scroll to the bottom):
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

rc6:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/)

---

### Post by ronacc on 2012-11-19
thanks .

---

### Post by andrew.46 on 2012-11-19
> **cariboo907 said:**
> Just out of curiosity, how many of us with AMD cpu's are having trouble booting the the latest kernel available in the repositories?

Seems ok here on an amd 8150, but labelled a little oddly:

```

andrew@corinth:~$ uname -a
Linux corinth 3.7.0-2-generic #8-Ubuntu SMP Thu Nov 15 16:20:48 UTC 2012 **[COLOR="Red"]x86_64 x86_64 x86_64 [/COLOR]**GNU/Linux

```

:)

---

### Post by wheeze on 2012-11-19
No problems for me at all, but my CPU is pretty old. Just a single-core Athlon 64, but I am using the 64-bit kernel.

FYI, haven't been able to update for several days due to being under the weather and not able to get to my Raring machine, so this is current info as of last Saturday.

---

### Post by cariboo on 2012-11-19
I tried the rc6 yesterday, and I do have the amd-microcode installed, and still no joy. :(

I should also add that I can't boot the daily live iso either.

---

### Post by ventrical on 2012-11-19
I just did a full upgrade to raring from quantal on my:

```

ventrical@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI Device 7914
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
ventrical@ubuntu:~$ sudo apt-get update

```dual core.

All is well but there is some scrambly screen just before plymouth. The white-stripe Unity panel boot is gone and  menu tabs on windows are seamless on this ATI radeon-express1250.

regards

ventrical@ubuntu:~$ uname -a
Linux ubuntu 3.7.0-2-generic #8-Ubuntu SMP Thu Nov 15 16:20:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ubuntu:~$

---

### Post by ronacc on 2012-11-19
installed rc6  , wouldn't boot , added amd 64 microcode still stopping during boot just after attaching my disks , the kernel seems to be alive since I can alt>sysreq>b to reboot and don't need to hard reset , whatever happens right after the disks are attached seems to be the problem . It is the same with the other 3.7 kernels , 3.5 still boots ok .

---

### Post by jfernyhough on 2012-11-19
Same odd naming on an i5, so it's not AMD-specific:

Linux arrandale 3.7.0-2-generic #8-Ubuntu SMP Thu Nov 15 16:20:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by VinDSL on 2012-11-19
I've been following this thread, even though I'm running an Intel P4EE CPU.

I have a gut *feeling* that we're suffering from a similar problem, but, in my case, it doesn't stop me from booting.

Since I installed the 3.7-rcs, I cannot get my drives to mount in "recovery mode".  When I try to go into read/write mode, I get an error dialog saying it cannot mount "/" because it doesn't exist, and so forth, and so on. However, it will boot, during a normal startup.  

As a workaround, I've been going to console from the LightDM login screen, and disabling services, instead of using "recovery mode".

Reading thorough this thread, it sounds like you guys aren't getting that far in the boot process -- that's all.

The 3.7-rcs obviously suffer from a litany of issues.  Hopefully, we'll overcome them soon.

Just saying...

---

### Post by jppr on 2012-11-20
That kernel bug is a weird and strange when the other 3.7 kernel works and others don´t ... and the strange and bizarre situation will also check that it feels like Canonical's developers don´t have the slightest interest begins to produce correct the problem ... because that kernel problem has been around for so long...

---

### Post by dino99 on 2012-11-20
you need to narrow down that booting issue: first remove "splash  quiet" from the boot line to let you see where hang happen.
As some amd cpu does not have trouble, then it means this issue is related to a mb's chipset or an additional card model.

With that info, a little googling might help.

---

### Post by ronacc on 2012-11-20
> **dino99 said:**
> you need to narrow down that booting issue: first remove "splash  quiet" from the boot line to let you see where hang happen.
As some amd cpu does not have trouble, then it means this issue is related to a mb's chipset or an additional card model.

With that info, a little googling might help.

I already did as you suggest . The 3.7 kernels all stop as soon as my disks are attached during the boot .

---

### Post by dino99 on 2012-11-20
> **ronacc said:**
> I already did as you suggest . The 3.7 kernels all stop as soon as my disks are attached during the boot .

so in verbose mode, do you see the fsck lines ? (maybe force a fsck from a booting kernel shutdown)
i've no problem on ext3/4 on i386

is it the same issue in recovery mode too ?

maybe purge that 3.7 kernel, then reinstall (dkms installed ?)
have you tried with an other video driver ? (if available)

---

### Post by philinux on 2012-11-20
> **cariboo907 said:**
> Just out of curiosity, how many of us with AMD cpu's are having trouble booting the the latest kernel available in the repositories?

My Intel atom powered netbook runs just fine with the 3.7.0.2 kernel.

No probs here. Just rebooted to 3.7.0.2 fine and dandy.

AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2 and nVidia 8600GT.

---

### Post by ronacc on 2012-11-20
> **dino99 said:**
> so in verbose mode, do you see the fsck lines ? (maybe force a fsck from a booting kernel shutdown)
i've no problem on ext3/4 on i386

is it the same issue in recovery mode too ?

maybe purge that 3.7 kernel, then reinstall (dkms installed ?)
have you tried with an other video driver ? (if available)

I'm amd 64 here and that seems to have problems with the 3.7 kernel , I keep all my old kernels and I still have 3.5-17 available and that boots ok . In verbose mode ( quiet and splash removed ) I didn't see the fsck line I'll look for it next boot . I don't think an fsck is being called even though when a 3.7 kernel hangs during boot I alt>sysreq>b to reboot .I doubt its a file system problem since the daily lives do the same thing . I'm nvidia graphics and using nouveau as the driver , I can try the proprietary driver .

---

### Post by jppr on 2012-11-21
Today's new kernel 3.7.0.3.9 update didn´t help and didn´t change anything, my system still doesn´t boot...

---

### Post by dino99 on 2012-11-21
> **jppr said:**
> Today's kernel update didn´t help and didn´t change anything, my system still doesn´t boot, even a new kernel 3.7.0.3.9

it should be great to test both 32 & 64 installation to narrow down that issue.

---

### Post by ronacc on 2012-11-21
d/l'd the i386 and zsync'd the amd64 daily's for today neither would boot , on the amd64 held down shift during boot to get the grub screen and then F6 and selected acpi=off then removed quiet and splash , that let it boot to the desktop , attempting an install  it got to the wireless screen and hung  after selecting continue . tried again same result .

---

### Post by fdm on 2012-11-21
I'm running 32bit ubuntu-minimal with an AMD Phenom II X2 555 processor. From the partial stack trace, it looks like it crashes when initializing my sata harddrive. I get the same results from the lastest 3.7.0.3.7 and the stable 3.6.7 mainline kernel. 3.5.0-17 leftover from quantal still works fine though.

Anyone know where to grab the full stacktrace without a null modem cable? No luck finding it in my logs so far.

---

### Post by ronacc on 2012-11-21
I tried adding acpi=off to the boot parameters for rc6 and that let me get a little further  but still no go , it times out waiting for the root device and drops to busybox .

---

### Post by dino99 on 2012-11-21
have you tried the irqpoll boot parameter ?

---

### Post by ronacc on 2012-11-21
no what do I need to add to the boot line on my install ?

---

### Post by fdm on 2012-11-21
Problem still presists for me when using the irqpoll parameter.

---

### Post by dino99 on 2012-11-21
> **ronacc said:**
> no what do I need to add to the boot line on my install ?

cant really tell you which, as i've not that issue (thanks) , but you will know which one works (in case it helps) after testing them (google around "ubuntu boot setting")

---

### Post by cariboo on 2012-11-21
Seeing a logging doesn't work, when the system won't boot, see the crummy cell phone picture. :)

---

### Post by jppr on 2012-11-21
> **cariboo907 said:**
> Seeing a logging doesn't work, when the system won't boot, see the crummy cell phone picture. :)

I have that same screen :(

---

### Post by ronacc on 2012-11-21
same here except I don't have any usb devices connected so I don't have those lines .

---

### Post by zenarcher on 2012-11-21
> **cariboo907 said:**
> Seeing a logging doesn't work, when the system won't boot, see the crummy cell phone picture. :)

I get about the same thing on my KVM switch with 3.7 and an AMD 64 bit system.

---

### Post by Sworddragon on 2012-11-21
Interestingly my AMD Phenom II X6 1045T never had any booting problems on the last kernel releases. But Turbo Core doesn't work for some versions of the Linux kernel.

---

### Post by VinDSL on 2012-11-21
> **cariboo907 said:**
> Seeing a logging doesn't work, when the system won't boot, see the crummy cell phone picture. :)
Yikes!!!

Your system is infected with Microsoft...  LoL!  :D

---

### Post by cariboo on 2012-11-21
> **VinDSL said:**
> Yikes!!!

Your system is infected with Microsoft...  LoL!  :D

Only Microsoft on this system is the hardware. :-D

---

### Post by zika on 2012-11-22
> **cariboo907 said:**
> Only Microsoft on this system is the hardware. :-D
Clever. Taking the best from both worlds...
Still using IBM keyboard (PS/2, DIN-one is in reserve...)...

---

### Post by P-I H on 2012-11-22
My istallation is booting OK.

This is the kernel.log. Perhaps it will give some help.
The same sequence as in cariboo907's picture starts at 1.539166

```
Nov 22 09:52:18 pi-GA-MA770-UD3-xbmc kernel: Kernel logging (proc) stopped.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: imklog 5.8.6, log source = /proc/kmsg started.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Linux version 3.7.0-3-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-5ubuntu7) ) #9-Ubuntu SMP Tue Nov 20 22:38:45 UTC 2012 (Ubuntu 3.7.0-3.9-generic 3.7.0-rc6)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-3-generic root=UUID=0c1c8efd-e8e9-46ea-a96b-5240a305305b ro quiet splash
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] KERNEL supported cpus:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   Intel GenuineIntel
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   AMD AuthenticAMD
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   Centaur CentaurHauls
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x00000000000983ff] usable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000098400-0x000000000009ffff] reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfc90fff] usable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfcf0000-0x00000000cfcf2fff] ACPI NVS
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfcf3000-0x00000000cfcfffff] ACPI data
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfd00000-0x00000000cfdfffff] reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] DMI 2.4 present.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA770-UD3/GA-MA770-UD3, BIOS FKb 07/08/2010
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] No AGP bridge found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: last_pfn = 0x130000 max_arch_pfn = 0x400000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] MTRR default type: uncachable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   00000-9FFFF write-back
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   C0000-C7FFF write-protect
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   C8000-FFFFF uncachable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] MTRR variable ranges enabled:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   3 base 0000CFD00000 mask FFFFFFF00000 uncachable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   4 base 0000CFE00000 mask FFFFFFE00000 uncachable
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   5 base 000100000000 mask FFFFE0000000 write-back
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   6 base 000120000000 mask FFFFF0000000 write-back
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   7 disabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] original variable MTRRs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 3, base: 3325MB, range: 1MB, type UC
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 4, base: 3326MB, range: 2MB, type UC
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 5, base: 4GB, range: 512MB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 6, base: 4608MB, range: 256MB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] total RAM covered: 3325M
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Found optimal setting for mtrr clean up
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 5  	lose cover RAM: 0G
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] New variable MTRRs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 3, base: 3325MB, range: 1MB, type UC
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] reg 4, base: 3326MB, range: 2MB, type UC
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: update [mem 0xcfd00000-0xffffffff] usable ==> reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: last_pfn = 0xcfc91 max_arch_pfn = 0x400000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] found SMP MP-table at [mem 0x000f53d0-0x000f53df] mapped at [ffff8800000f53d0]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Base memory trampoline at [ffff880000092000] 92000 size 24576
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Using GB pages for direct mapping
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0xcfc90fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]  [mem 0xc0000000-0xcfbfffff] page 2M
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]  [mem 0xcfc00000-0xcfc90fff] page 4k
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] kernel direct mapping tables up to 0xcfc90fff @ [mem 0x1fffd000-0x1fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x12fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]  [mem 0x100000000-0x12fffffff] page 2M
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] kernel direct mapping tables up to 0x12fffffff @ [mem 0xcfc8f000-0xcfc90fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] RAMDISK: [mem 0x36184000-0x370b9fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: RSDP 00000000000f6e00 00014 (v00 GBT   )
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: RSDT 00000000cfcf3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: FACP 00000000cfcf3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: DSDT 00000000cfcf30c0 07472 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: FACS 00000000cfcf0000 00040
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: SSDT 00000000cfcfa600 0088C (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: HPET 00000000cfcfaec0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: MCFG 00000000cfcfaf00 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: APIC 00000000cfcfa540 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] No NUMA configuration found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000012fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x12fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   NODE_DATA [mem 0x12fffc000-0x12fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Zone ranges:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   Normal   [mem 0x100000000-0x12fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Movable zone start for each node
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Early memory node ranges
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   node   0: [mem 0x00010000-0x00097fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   node   0: [mem 0x00100000-0xcfc90fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   node   0: [mem 0x100000000-0x12fffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] On node 0 totalpages: 1047577
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA zone: 6 pages reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA zone: 3906 pages, LIFO batch:0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   DMA32 zone: 830673 pages, LIFO batch:31
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] nr_irqs_gsi: 40
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 0000000000098000 - 0000000000099000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 0000000000099000 - 00000000000a0000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfc91000 - 00000000cfcf0000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfcf0000 - 00000000cfcf3000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfcf3000 - 00000000cfd00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfd00000 - 00000000cfe00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000e0000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] e820: [mem 0xcfe00000-0xdfffffff] available for PCI devices
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s84736 r8192 d21760 u262144
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] pcpu-alloc: s84736 r8192 d21760 u262144 alloc=1*2097152
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028115
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Policy zone: Normal
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-3-generic root=UUID=0c1c8efd-e8e9-46ea-a96b-5240a305305b ro quiet splash
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] __ex_table already sorted, skipping sort
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Checking aperture...
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] No AGP bridge found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Node 0: aperture @ c4000000 size 32 MB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] This costs you 64 MB of RAM
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Memory: 3960776k/4980736k available (6868k kernel code, 790428k absent, 229532k reserved, 6343k data, 976k init)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Hierarchical RCU implementation.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] console [tty0] enabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000000] hpet clockevent registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.004000] tsc: Fast TSC calibration using PIT
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.008000] tsc: Detected 2924.697 MHz processor
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5849.39 BogoMIPS (lpj=11698788)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000006] pid_max: default: 32768 minimum: 301
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000030] Security Framework initialized
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000040] AppArmor: AppArmor initialized
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000041] Yama: becoming mindful.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.000302] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.001421] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.001948] Mount-cache hash table entries: 256
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002127] Initializing cgroup subsys cpuacct
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002129] Initializing cgroup subsys memory
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002136] Initializing cgroup subsys devices
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002138] Initializing cgroup subsys freezer
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002139] Initializing cgroup subsys blkio
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002140] Initializing cgroup subsys perf_event
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002142] Initializing cgroup subsys hugetlb
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002162] tseg: 00cfe00000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002163] CPU: Physical Processor ID: 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002164] CPU: Processor Core ID: 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002165] mce: CPU supports 6 MCE banks
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002170] LVT offset 0 assigned for vector 0xf9
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002175] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002175] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002175] tlb_flushall_shift: 4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.002270] Freeing SMP alternatives: 24k freed
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.003501] ACPI: Core revision 20120913
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.043419] ftrace: allocating 25995 entries in 102 pages
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.053574] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.093246] smpboot: CPU0: AMD Athlon(tm) II X4 620 Processor (fam: 10, model: 05, stepping: 02)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199097] Performance Events: AMD PMU driver.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199100] ... version:                0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199101] ... bit width:              48
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199102] ... generic registers:      4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199103] ... value mask:             0000ffffffffffff
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199104] ... max period:             00007fffffffffff
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199104] ... fixed-purpose events:   0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.199105] ... event mask:             000000000000000f
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.200055] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.200123] smpboot: Booting Node   0, Processors  #1 #2 #3
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.239326] Brought up 4 CPUs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.239328] smpboot: Total of 4 processors activated (23397.57 BogoMIPS)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.240140] devtmpfs: initialized
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.241369] EVM: security.selinux
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.241370] EVM: security.SMACK64
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.241371] EVM: security.capability
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.241450] PM: Registering ACPI NVS region [mem 0xcfcf0000-0xcfcf2fff] (12288 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242273] regulator-dummy: no parameters
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242301] RTC time:  8:52:45, date: 11/22/12
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242338] NET: Registered protocol family 16
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242427] node 0 link 0: io port [b000, ffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242429] TOM: 00000000d0000000 aka 3328M
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242431] Fam 10h mmconf [mem 0xe0000000-0xe00fffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242433] node 0 link 0: mmio [a0000, bffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242435] node 0 link 0: mmio [d0000000, dfffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242437] node 0 link 0: mmio [f0000000, fe02ffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242438] node 0 link 0: mmio [e0000000, e04fffff] ==> [e0100000, e04fffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242440] TOM2: 0000000130000000 aka 4864M
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242442] bus: [bus 00-04] on node 0 link 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242443] bus: 00 [io  0x0000-0xffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242444] bus: 00 [mem 0x000a0000-0x000bffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242445] bus: 00 [mem 0xd0000000-0xdfffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242446] bus: 00 [mem 0xe0500000-0xffffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242447] bus: 00 [mem 0xe0100000-0xe04fffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242448] bus: 00 [mem 0x130000000-0xfcffffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242528] ACPI: bus type pci registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242576] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.242578] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.252694] PCI: Using configuration type 1 for base access
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.253545] bio: create slab <bio-0> at 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.253629] ACPI: Added _OSI(Module Device)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.253630] ACPI: Added _OSI(Processor Device)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.253631] ACPI: Added _OSI(3.0 _SCP Extensions)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.253632] ACPI: Added _OSI(Processor Aggregator Device)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.254264] ACPI: EC: Look up EC in DSDT
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.257932] ACPI: Interpreter enabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.257938] ACPI: (supports S0 S3 S4 S5)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.257952] ACPI: Using IOAPIC for interrupt routing
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303038] ACPI: No dock devices found.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303044] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303087] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303166] PCI host bridge to bus 0000:00
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303169] pci_bus 0000:00: root bus resource [bus 00-ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303171] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303173] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303174] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303176] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303178] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xfebfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303187] pci 0000:00:00.0: [1002:5957] type 00 class 0x060000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303198] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303230] pci 0000:00:02.0: [1002:5978] type 01 class 0x060400
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303259] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303272] pci 0000:00:04.0: [1002:597a] type 01 class 0x060400
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303300] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303326] pci 0000:00:0a.0: [1002:597f] type 01 class 0x060400
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303354] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303379] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303397] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303406] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303414] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303423] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303432] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303441] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303496] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303508] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303570] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303582] pci 0000:00:12.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303649] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303667] pci 0000:00:12.2: reg 10: [mem 0xfe02c000-0xfe02c0ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303746] pci 0000:00:12.2: supports D1 D2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303748] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303771] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303783] pci 0000:00:13.0: reg 10: [mem 0xfe02b000-0xfe02bfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303845] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303857] pci 0000:00:13.1: reg 10: [mem 0xfe02a000-0xfe02afff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303924] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.303942] pci 0000:00:13.2: reg 10: [mem 0xfe029000-0xfe0290ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304021] pci 0000:00:13.2: supports D1 D2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304022] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304047] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304142] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304158] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304167] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304175] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304184] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304193] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304248] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304268] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304331] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304346] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304418] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304459] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304472] pci 0000:00:14.5: reg 10: [mem 0xfe028000-0xfe028fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304536] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304550] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304561] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304573] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304586] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304636] pci 0000:01:00.0: [10de:0615] type 00 class 0x030000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304648] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304660] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304672] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304681] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.304689] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311349] pci 0000:00:02.0: PCI bridge to [bus 01]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311355] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311358] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311361] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311398] pci 0000:02:00.0: [168c:0024] type 00 class 0x028000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311415] pci 0000:02:00.0: reg 10: [mem 0xfdaf0000-0xfdafffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311493] pci 0000:02:00.0: supports D1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311495] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311514] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311520] pci 0000:00:04.0: PCI bridge to [bus 02]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311523] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311525] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311528] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311564] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311576] pci 0000:03:00.0: reg 10: [io  0xce00-0xceff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311595] pci 0000:03:00.0: reg 18: [mem 0xfddff000-0xfddfffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311607] pci 0000:03:00.0: reg 20: [mem 0xfdde0000-0xfddeffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311616] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311659] pci 0000:03:00.0: supports D1 D2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.311660] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319347] pci 0000:00:0a.0: PCI bridge to [bus 03]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319353] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319355] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319358] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319396] pci 0000:04:07.0: [1106:3038] type 00 class 0x0c0300
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319456] pci 0000:04:07.0: reg 20: [io  0xbf00-0xbf1f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319511] pci 0000:04:07.0: supports D1 D2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319513] pci 0000:04:07.0: PME# supported from D0 D1 D2 D3hot
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319536] pci 0000:04:07.2: [1106:3104] type 00 class 0x0c0320
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319556] pci 0000:04:07.2: reg 10: [mem 0xfdcff000-0xfdcff0ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319648] pci 0000:04:07.2: supports D1 D2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319650] pci 0000:04:07.2: PME# supported from D0 D1 D2 D3hot
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319701] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319705] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319708] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319712] pci 0000:00:14.4:   bridge window [mem 0xfdb00000-0xfdbfffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319714] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319715] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319717] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319718] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319720] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xfebfffff] (subtractive decode)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.319995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.320015]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.320017]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329792] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329823] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329851] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329878] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329905] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329931] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329958] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.329985] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330088] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330090] vgaarb: loaded
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330091] vgaarb: bridge control possible 0000:01:00.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330227] SCSI subsystem initialized
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330229] ACPI: bus type scsi registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330289] libata version 3.00 loaded.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330305] ACPI: bus type usb registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330320] usbcore: registered new interface driver usbfs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330326] usbcore: registered new interface driver hub
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330343] usbcore: registered new device driver usb
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.330399] PCI: Using ACPI for IRQ routing
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338606] PCI: pci_cache_line_size set to 64 bytes
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338613] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338677] e820: reserve RAM buffer [mem 0x00098400-0x0009ffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338679] e820: reserve RAM buffer [mem 0xcfc91000-0xcfffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338749] NetLabel: Initializing
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338751] NetLabel:  domain hash size = 128
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338751] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338760] NetLabel:  unlabeled traffic allowed by default
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338831] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.338834] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.340863] Switching to clocksource hpet
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345046] AppArmor: AppArmor Filesystem Enabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345072] pnp: PnP ACPI init
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345087] ACPI: bus type pnp registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345165] pnp 00:00: [bus 00-ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345167] pnp 00:00: [io  0x0cf8-0x0cff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345169] pnp 00:00: [io  0x0000-0x0cf7 window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345170] pnp 00:00: [io  0x0d00-0xffff window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345172] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345173] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345174] pnp 00:00: [mem 0xcff00000-0xfebfffff window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345201] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345208] pnp 00:01: [io  0x0010-0x001f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345210] pnp 00:01: [io  0x0022-0x003f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345211] pnp 00:01: [io  0x0044-0x005f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345212] pnp 00:01: [io  0x0062-0x0063]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345213] pnp 00:01: [io  0x0065-0x006f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345214] pnp 00:01: [io  0x0074-0x007f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345216] pnp 00:01: [io  0x0091-0x0093]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345217] pnp 00:01: [io  0x00a2-0x00bf]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345218] pnp 00:01: [io  0x00e0-0x00ef]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345219] pnp 00:01: [io  0x04d0-0x04d1]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345221] pnp 00:01: [io  0x0220-0x0225]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345222] pnp 00:01: [io  0x0290-0x0294]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345262] system 00:01: [io  0x04d0-0x04d1] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345264] system 00:01: [io  0x0220-0x0225] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345265] system 00:01: [io  0x0290-0x0294] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.345268] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369210] pnp 00:02: [io  0x4100-0x411f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369213] pnp 00:02: [io  0x0228-0x022f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369215] pnp 00:02: [io  0x040b]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369216] pnp 00:02: [io  0x04d6]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369217] pnp 00:02: [io  0x0c00-0x0c01]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369218] pnp 00:02: [io  0x0c14]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369220] pnp 00:02: [io  0x0c50-0x0c52]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369221] pnp 00:02: [io  0x0c6c-0x0c6d]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369222] pnp 00:02: [io  0x0c6f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369223] pnp 00:02: [io  0x0cd0-0x0cd1]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369224] pnp 00:02: [io  0x0cd2-0x0cd3]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369225] pnp 00:02: [io  0x0cd4-0x0cdf]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369227] pnp 00:02: [io  0x4000-0x40fe]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369228] pnp 00:02: [io  0x4210-0x4217]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369234] pnp 00:02: [io  0x0b00-0x0b0f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369235] pnp 00:02: [io  0x0b10-0x0b1f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369237] pnp 00:02: [io  0x0b20-0x0b3f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369239] pnp 00:02: [mem 0x00000000-0x00000fff window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369240] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369246] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369268] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369272] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:03:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369305] system 00:02: [io  0x4100-0x411f] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369307] system 00:02: [io  0x0228-0x022f] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369309] system 00:02: [io  0x040b] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369310] system 00:02: [io  0x04d6] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369312] system 00:02: [io  0x0c00-0x0c01] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369313] system 00:02: [io  0x0c14] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369315] system 00:02: [io  0x0c50-0x0c52] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369316] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369318] system 00:02: [io  0x0c6f] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369319] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369321] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369322] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369324] system 00:02: [io  0x4000-0x40fe] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369325] system 00:02: [io  0x4210-0x4217] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369327] system 00:02: [io  0x0b00-0x0b0f] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369329] system 00:02: [io  0x0b10-0x0b1f] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369330] system 00:02: [io  0x0b20-0x0b3f] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369332] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369335] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369406] pnp 00:03: [dma 4]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369407] pnp 00:03: [io  0x0000-0x000f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369409] pnp 00:03: [io  0x0080-0x0090]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369410] pnp 00:03: [io  0x0094-0x009f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369411] pnp 00:03: [io  0x00c0-0x00df]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369427] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369451] pnp 00:04: [irq 0 disabled]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369463] pnp 00:04: [irq 8]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369464] pnp 00:04: [mem 0xfed00000-0xfed003ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369478] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369497] pnp 00:05: [io  0x0070-0x0073]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369512] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369517] pnp 00:06: [io  0x0061]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369529] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369534] pnp 00:07: [io  0x00f0-0x00ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369541] pnp 00:07: [irq 13]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369555] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369765] pnp 00:08: [io  0x03f8-0x03ff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369772] pnp 00:08: [irq 4]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369807] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369948] pnp 00:09: [io  0x0378-0x037f]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369955] pnp 00:09: [irq 7]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.369980] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370063] pnp 00:0a: [mem 0xe0000000-0xefffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370088] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370090] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370186] pnp 00:0b: [mem 0x000d4400-0x000d7fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370187] pnp 00:0b: [mem 0x000f0000-0x000f7fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370188] pnp 00:0b: [mem 0x000f8000-0x000fbfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370190] pnp 00:0b: [mem 0x000fc000-0x000fffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370191] pnp 00:0b: [mem 0xcfcf0000-0xcfcfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370192] pnp 00:0b: [mem 0xffff0000-0xffffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370195] pnp 00:0b: [mem 0x00000000-0x0009ffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370196] pnp 00:0b: [mem 0x00100000-0xcfceffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370197] pnp 00:0b: [mem 0xcfd00000-0xcfdfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370199] pnp 00:0b: [mem 0xcfe00000-0xcfefffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370200] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370201] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370202] pnp 00:0b: [mem 0xfff80000-0xfffeffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370205] pnp 00:0b: disabling [mem 0x000d4400-0x000d7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370207] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370209] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370211] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370213] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370215] pnp 00:0b: disabling [mem 0x00100000-0xcfceffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370247] system 00:0b: [mem 0xcfcf0000-0xcfcfffff] could not be reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370248] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370250] system 00:0b: [mem 0xcfd00000-0xcfdfffff] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370252] system 00:0b: [mem 0xcfe00000-0xcfefffff] could not be reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370253] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370255] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370257] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370259] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370273] pnp: PnP ACPI: found 12 devices
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.370274] ACPI: ACPI bus type pnp unregistered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376472] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376476] pci 0000:00:02.0: PCI bridge to [bus 01]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376478] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376481] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376483] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376486] pci 0000:00:04.0: PCI bridge to [bus 02]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376488] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376490] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376493] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376496] pci 0000:03:00.0: BAR 6: assigned [mem 0xfdd00000-0xfdd0ffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376498] pci 0000:00:0a.0: PCI bridge to [bus 03]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376499] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376502] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376504] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376507] pci 0000:00:14.4: PCI bridge to [bus 04]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376510] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376514] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376518] pci 0000:00:14.4:   bridge window [mem 0xfdb00000-0xfdbfffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376554] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376556] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376557] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376559] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376560] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xfebfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376562] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376564] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376565] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376567] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376568] pci_bus 0000:02: resource 1 [mem 0xfda00000-0xfdafffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376570] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376572] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376573] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376575] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376576] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376578] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376580] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff pref]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376581] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376583] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376584] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376586] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376587] pci_bus 0000:04: resource 8 [mem 0xcff00000-0xfebfffff]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.376621] NET: Registered protocol family 2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.377151] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.379363] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.379639] TCP: Hash tables configured (established 524288 bind 65536)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.379685] TCP: reno registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.379694] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.379719] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.379804] NET: Registered protocol family 1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.740839] pci 0000:01:00.0: Boot video device
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.740951] PCI: CLS 64 bytes, default 64
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.740991] Trying to unpack rootfs image as initramfs...
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.963687] Freeing initrd memory: 15576k freed
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.968389] PCI-DMA: Disabling AGP.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.968478] PCI-DMA: aperture base @ c4000000 size 65536 KB
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.968479] PCI-DMA: using GART IOMMU.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.968481] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.970906] LVT offset 1 assigned for vector 0x400
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.970917] IBS: LVT offset 1 assigned
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.970942] perf: AMD IBS detected (0x0000001f)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.971128] Initialise module verification
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.971173] audit: initializing netlink socket (disabled)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.971184] type=2000 audit(1353574364.832:1): initialized
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.992620] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.993884] VFS: Disk quotas dquot_6.5.2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.993923] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994363] fuse init (API version 7.20)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994424] msgmni has been set to 7895
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994857] Key type asymmetric registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994859] Asymmetric key parser 'x509' registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994883] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994909] io scheduler noop registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994910] io scheduler deadline registered (default)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.994914] io scheduler cfq registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995022] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995074] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995122] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995164] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995178] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995264] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995267] ACPI: Power Button [PWRB]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995300] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    0.995302] ACPI: Power Button [PWRF]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.021547] GHES: HEST is not enabled!
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.021670] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.042131] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.043235] Linux agpgart interface v0.103
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.044408] brd: module loaded
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.044993] loop: module loaded
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045090] ahci 0000:00:11.0: version 3.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045238] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045241] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045724] scsi0 : ahci
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045792] scsi1 : ahci
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045841] scsi2 : ahci
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045889] scsi3 : ahci
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045914] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045916] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045919] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.045921] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.046945] scsi4 : pata_acpi
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047152] scsi5 : pata_acpi
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047332] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047333] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047539] libphy: Fixed MDIO Bus: probed
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047569] tun: Universal TUN/TAP device driver, 1.6
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047570] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047624] PPP generic driver version 2.4.2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.047669] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.048288] ehci_hcd 0000:00:12.2: EHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.048294] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.048300] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.048326] ehci_hcd 0000:00:12.2: debug port 1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.048349] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056705] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056733] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056735] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056737] usb usb1: Product: EHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056738] usb usb1: Manufacturer: Linux 3.7.0-3-generic ehci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056739] usb usb1: SerialNumber: 0000:00:12.2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056862] hub 1-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056865] hub 1-0:1.0: 6 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056989] ehci_hcd 0000:00:13.2: EHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056994] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.056997] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.057023] ehci_hcd 0000:00:13.2: debug port 1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.057048] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068705] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068728] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068729] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068731] usb usb2: Product: EHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068732] usb usb2: Manufacturer: Linux 3.7.0-3-generic ehci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068734] usb usb2: SerialNumber: 0000:00:13.2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068855] hub 2-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.068857] hub 2-0:1.0: 6 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.069006] ehci_hcd 0000:04:07.2: EHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.069010] ehci_hcd 0000:04:07.2: new USB bus registered, assigned bus number 3
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.069066] ehci_hcd 0000:04:07.2: irq 23, io mem 0xfdcff000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080709] ehci_hcd 0000:04:07.2: USB 2.0 started, EHCI 1.00
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080742] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080744] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080746] usb usb3: Product: EHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080747] usb usb3: Manufacturer: Linux 3.7.0-3-generic ehci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080748] usb usb3: SerialNumber: 0000:04:07.2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080843] hub 3-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080846] hub 3-0:1.0: 2 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080930] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080980] ohci_hcd 0000:00:12.0: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.080985] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.081018] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140682] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140685] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140687] usb usb4: Product: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140688] usb usb4: Manufacturer: Linux 3.7.0-3-generic ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140690] usb usb4: SerialNumber: 0000:00:12.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140827] hub 4-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140832] hub 4-0:1.0: 3 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140940] ohci_hcd 0000:00:12.1: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140945] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 5
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.140961] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200661] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200664] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200666] usb usb5: Product: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200667] usb usb5: Manufacturer: Linux 3.7.0-3-generic ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200668] usb usb5: SerialNumber: 0000:00:12.1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200795] hub 5-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200801] hub 5-0:1.0: 3 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200908] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200912] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 6
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.200945] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260686] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260689] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260691] usb usb6: Product: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260692] usb usb6: Manufacturer: Linux 3.7.0-3-generic ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260693] usb usb6: SerialNumber: 0000:00:13.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260819] hub 6-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260827] hub 6-0:1.0: 3 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260930] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260936] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 7
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.260952] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320652] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320655] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320656] usb usb7: Product: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320658] usb usb7: Manufacturer: Linux 3.7.0-3-generic ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320659] usb usb7: SerialNumber: 0000:00:13.1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320786] hub 7-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320792] hub 7-0:1.0: 3 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320899] ohci_hcd 0000:00:14.5: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320904] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 8
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.320920] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.364673] ata3: SATA link down (SStatus 0 SControl 300)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.364713] ata1: SATA link down (SStatus 0 SControl 300)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380607] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380610] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380612] usb usb8: Product: OHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380614] usb usb8: Manufacturer: Linux 3.7.0-3-generic ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380615] usb usb8: SerialNumber: 0000:00:14.5
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380727] hub 8-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380732] hub 8-0:1.0: 2 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380817] uhci_hcd: USB Universal Host Controller Interface driver
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380858] uhci_hcd 0000:04:07.0: UHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380863] uhci_hcd 0000:04:07.0: new USB bus registered, assigned bus number 9
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380907] uhci_hcd 0000:04:07.0: irq 21, io base 0x0000bf00
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380934] usb usb9: New USB device found, idVendor=1d6b, idProduct=0001
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380935] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380937] usb usb9: Product: UHCI Host Controller
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380938] usb usb9: Manufacturer: Linux 3.7.0-3-generic uhci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380939] usb usb9: SerialNumber: 0000:04:07.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380997] hub 9-0:1.0: USB hub found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.380999] hub 9-0:1.0: 2 ports detected
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.381101] i8042: PNP: No PS/2 controller found. Probing ports directly.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.415549] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.415550] i8042: If AUX port is really absent please use the 'i8042.noaux' option
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.536572] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.536603] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.537474] ata2.00: ATA-8: WDC WD6400AAKS-00A7B0, 01.03B01, max UDMA/133
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.537478] ata2.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.537627] ata2.00: failed to get Identify Device Data, Emask 0x1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.538031] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB04, max UDMA/100
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.538734] ata2.00: failed to get Identify Device Data, Emask 0x1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.538737] ata2.00: configured for UDMA/133
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.538914] scsi 1:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-0 01.0 PQ: 0 ANSI: 5
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.539068] sd 1:0:0:0: Attached scsi generic sg0 type 0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.539086] sd 1:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.539166] sd 1:0:0:0: [sda] Write Protect is off
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.539168] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.539216] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.616413]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.617046] sd 1:0:0:0: [sda] Attached SCSI disk
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.664612] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.664755] mousedev: PS/2 mouse device common for all mice
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.664899] rtc_cmos 00:05: RTC can wake from S4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665005] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665036] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665111] device-mapper: uevent: version 1.0.3
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665162] device-mapper: ioctl: 4.23.0-ioctl (2012-07-25) initialised: dm-devel@redhat.com
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665169] cpuidle: using governor ladder
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665169] cpuidle: using governor menu
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665173] ledtrig-cpu: registered to indicate activity on CPUs
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665174] EFI Variables Facility v0.08 2004-May-17
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665365] ashmem: initialized
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665458] TCP: cubic registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665529] NET: Registered protocol family 10
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665655] NET: Registered protocol family 17
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665663] Key type dns_resolver registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665886] PM: Hibernation image not present or could not be loaded.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.665887] Loading module verification certificates
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.666820] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: a300b623a3c0aa45f0b0ebb3fb7580ffecd0e9a8'
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.666829] registered taskstats version 1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.669148] Key type trusted registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.671123] Key type encrypted registered
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.673315]   Magic number: 4:869:877
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.673420] rtc_cmos 00:05: setting system clock to 2012-11-22 08:52:46 UTC (1353574366)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.673451] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.674480] acpi-cpufreq: overriding BIOS provided _PSD data
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.674604] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.674605] EDD information not available.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.892448] usb 4-3: new low-speed USB device number 2 using ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.968426] tsc: Refined TSC clocksource calibration: 2924.794 MHz
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    1.968436] Switching to clocksource tsc
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.067510] usb 4-3: New USB device found, idVendor=049f, idProduct=0051
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.067513] usb 4-3: New USB device strings: Mfr=1, Product=8, SerialNumber=0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.067515] usb 4-3: Product: Compaq USB Keyboard
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.067517] usb 4-3: Manufacturer: CHICONY
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.180357] usb 3-1: new high-speed USB device number 2 using ehci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.313263] usb 3-1: New USB device found, idVendor=2040, idProduct=8400
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.313267] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.313268] usb 3-1: Product: WinTV Nova-DT
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.313270] usb 3-1: Manufacturer: Hauppauge
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.313271] usb 3-1: SerialNumber: 4031668958
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.338563] ata4.00: configured for UDMA/100
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.576225] usb 5-1: new low-speed USB device number 2 using ohci_hcd
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.751336] usb 5-1: New USB device found, idVendor=045e, idProduct=00f0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.751339] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.751341] usb 5-1: Product: Microsoft ® Laser Mouse 6000
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    2.751342] usb 5-1: Manufacturer: Microsoft Corporation
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.140329] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB04 PQ: 0 ANSI: 5
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.143573] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.143577] cdrom: Uniform CD-ROM driver Revision: 3.20
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.143691] sr 3:0:0:0: Attached scsi CD-ROM sr0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.143770] sr 3:0:0:0: Attached scsi generic sg1 type 5
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.312242] Freeing unused kernel memory: 976k freed
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.312467] Write protecting the kernel read-only data: 12288k
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.315666] Freeing unused kernel memory: 1312k freed
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.318564] Freeing unused kernel memory: 1092k freed
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.365748] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.365937] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.366085] r8169 0000:03:00.0 eth0: RTL8168c/8111c at 0xffffc90000664000, 00:24:1d:2f:87:ac, XID 1c4000c0 IRQ 43
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.366087] r8169 0000:03:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.387259] usbcore: registered new interface driver usbhid
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.387262] usbhid: USB HID core driver
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.392414] input: CHICONY Compaq USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/input/input2
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.392681] hid-generic 0003:049F:0051.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY Compaq USB Keyboard] on usb-0000:00:12.0-3/input0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.396218] input: CHICONY Compaq USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.1/input/input3
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.396340] hid-generic 0003:049F:0051.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [CHICONY Compaq USB Keyboard] on usb-0000:00:12.0-3/input1
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.396512] input: Microsoft Corporation Microsoft ® Laser Mouse 6000 as /devices/pci0000:00/0000:00:12.1/usb5/5-1/5-1:1.0/input/input4
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.396599] hid-generic 0003:045E:00F0.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Corporation Microsoft ® Laser Mouse 6000] on usb-0000:00:12.1-1/input0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.838582] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    3.838586] EXT4-fs (sda8): write access will be enabled during recovery
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    5.262787] EXT4-fs (sda8): recovery complete
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    5.267646] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    7.367824] Adding 6032372k swap on /dev/sda5.  Priority:-1 extents:1 across:6032372k 
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    7.403188] Adding 4188156k swap on /dev/sda7.  Priority:-2 extents:1 across:4188156k 
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    7.439294] Adding 4189180k swap on /dev/sda9.  Priority:-3 extents:1 across:4189180k 
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    7.589291] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    8.107946] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.098627] Disabling lock debugging due to kernel taint
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.166305] lp: driver loaded but no devices found
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.243147] FS-Cache: Loaded
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.253538] RPC: Registered named UNIX socket transport module.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.253541] RPC: Registered udp transport module.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.253542] RPC: Registered tcp transport module.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.253543] RPC: Registered tcp NFSv4.1 backchannel transport module.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.323942] FS-Cache: Netfs 'nfs' registered for caching
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [    9.596013] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.064097] parport_pc 00:09: reported by Plug and Play ACPI
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.064154] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.157962] lp0: using parport0 (interrupt-driven).
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.168018] ppdev: user-space parallel port driver
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.186949] wmi: Mapper loaded
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.244724] MCE: In-kernel MCE decoding enabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.265715] microcode: CPU0: patch_level=0x010000c6
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.295605] EDAC MC: Ver: 3.0.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.322859] AMD64 EDAC driver v3.4.0
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.322897] EDAC amd64: DRAM ECC disabled.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.322911] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.322911]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.322911]  (Note that use of the override may cause unknown side effects.)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.346189] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20120913/utaddress-251)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.346197] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.425718] cfg80211: Calling CRDA to update world regulatory domain
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.527459] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.527541] sp5100_tco: mmio address 0xfec000f0 already in use
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718519] microcode: CPU0: new patch_level=0x010000db
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718539] microcode: CPU1: patch_level=0x010000c6
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718549] microcode: CPU1: new patch_level=0x010000db
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718558] microcode: CPU2: patch_level=0x010000c6
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718564] microcode: CPU2: new patch_level=0x010000db
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718570] microcode: CPU3: patch_level=0x010000c6
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718573] microcode: CPU3: new patch_level=0x010000db
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.718645] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.982629] kvm: Nested Virtualization enabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   10.982634] kvm: Nested Paging enabled
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143753] ath: EEPROM regdomain: 0x30
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143756] ath: EEPROM indicates we should expect a direct regpair map
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143758] ath: Country alpha2 being used: AM
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143759] ath: Regpair used: 0x30
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143764] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143765] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143766] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143768] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143770] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143770] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143772] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143773] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143774] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143775] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143776] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143777] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143778] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143779] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143780] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143781] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143782] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143783] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143784] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143785] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143786] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143787] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143788] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.143789] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147099] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147101] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147102] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147103] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147105] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147106] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147107] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147108] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147109] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147110] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147111] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147112] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147113] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147114] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147115] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147117] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147118] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147119] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147120] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147121] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147122] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147123] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147124] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147125] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147126] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147127] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147128] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:55 pi-GA-MA770-UD3-xbmc kernel: [   11.147130] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.209141] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.332071] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.332313] Registered led device: ath9k-phy0
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.332317] ieee80211 phy0: Atheros AR5418 MAC/BB Rev:2 AR2133 RF Rev:81 mem=0xffffc900121a0000, irq=16
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.332323] cfg80211: Pending regulatory request, waiting for it to be processed...
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.422962] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443048] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443132] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443183] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443233] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443285] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443333] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443393] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.443441] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.631190] dib0700: firmware started successfully.
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639098] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639102] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639104] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639105] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639106] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639107] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639108] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639109] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639110] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639111] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639112] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639113] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639114] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639116] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639117] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639118] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639119] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639120] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639121] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639122] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639123] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639124] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639125] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639126] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639127] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639128] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639129] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639130] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639133] cfg80211: World regulatory domain updated:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639134] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639135] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639136] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639137] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639138] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639139] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.639149] cfg80211: Calling CRDA for country: AM
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643050] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643054] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643055] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643056] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643057] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643059] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643060] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643061] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643062] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643063] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643064] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643065] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643066] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643067] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643068] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643069] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643070] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643071] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643072] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643073] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643074] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643075] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643076] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643077] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643078] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643079] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643080] cfg80211: Disabling freq 2484 MHz
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643083] cfg80211: Regulatory domain changed to country: AM
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643084] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643085] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643086] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 1800 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.643087] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.823317] nvidia: module license 'NVIDIA' taints kernel.
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.835171] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   11.835358] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.43  Sun Aug 19 20:14:03 PDT 2012
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   12.133378] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   12.133444] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Nov 22 09:52:56 pi-GA-MA770-UD3-xbmc kernel: [   12.133494] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.192497] type=1400 audit(1353574377.018:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=760 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.192511] type=1400 audit(1353574377.018:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=759 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.192526] type=1400 audit(1353574377.018:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=796 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.192909] type=1400 audit(1353574377.018:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=759 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.192914] type=1400 audit(1353574377.018:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=760 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.192922] type=1400 audit(1353574377.018:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=796 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.193133] type=1400 audit(1353574377.018:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=759 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.193150] type=1400 audit(1353574377.018:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=796 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.193155] type=1400 audit(1353574377.018:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=760 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.371732] usb 3-1: DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.563652] Bluetooth: Core ver 2.16
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.563678] NET: Registered protocol family 31
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.563679] Bluetooth: HCI device and connection manager initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.563689] Bluetooth: HCI socket layer initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.563691] Bluetooth: L2CAP socket layer initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.563696] Bluetooth: SCO socket layer initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.592319] DiB0070: successfully identified
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.592324] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.592423] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.636147] Bluetooth: RFCOMM TTY layer initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.636161] Bluetooth: RFCOMM socket layer initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.636162] Bluetooth: RFCOMM ver 1.11
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.639801] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.639804] Bluetooth: BNEP filters: protocol multicast
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.639813] Bluetooth: BNEP socket layer initialized
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.685545] type=1400 audit(1353574377.514:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=860 comm="apparmor_parser"
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.744051] usb 3-1: DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   12.964137] DiB0070: successfully identified
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.016938] Registered IR keymap rc-dib0700-rc5
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.017052] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:04:07.2/usb3/3-1/rc/rc0/input13
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.017132] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:04:07.2/usb3/3-1/rc/rc0
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.017356] dvb-usb: schedule remote query interval to 50 msecs.
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.017396] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.017652] usbcore: registered new interface driver dvb_usb_dib0700
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.103754] NFS: Registering the id_resolver key type
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.103766] Key type id_resolver registered
Nov 22 09:52:57 pi-GA-MA770-UD3-xbmc kernel: [   13.103767] Key type id_legacy registered
Nov 22 09:52:59 pi-GA-MA770-UD3-xbmc kernel: [   15.118503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 22 09:52:59 pi-GA-MA770-UD3-xbmc kernel: [   15.120184] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 22 09:52:59 pi-GA-MA770-UD3-xbmc kernel: [   15.133565] r8169 0000:03:00.0 eth0: link down
Nov 22 09:52:59 pi-GA-MA770-UD3-xbmc kernel: [   15.133574] r8169 0000:03:00.0 eth0: link down
Nov 22 09:52:59 pi-GA-MA770-UD3-xbmc kernel: [   15.133602] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 22 09:52:59 pi-GA-MA770-UD3-xbmc kernel: [   15.133885] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 22 09:53:01 pi-GA-MA770-UD3-xbmc kernel: [   16.284727] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Nov 22 09:53:02 pi-GA-MA770-UD3-xbmc kernel: [   17.222625] r8169 0000:03:00.0 eth0: link up
Nov 22 09:53:02 pi-GA-MA770-UD3-xbmc kernel: [   17.223659] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 22 09:53:03 pi-GA-MA770-UD3-xbmc kernel: [   19.143025] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov 22 09:53:03 pi-GA-MA770-UD3-xbmc kernel: [   19.143085] ata4.00: failed command: IDENTIFY PACKET DEVICE
Nov 22 09:53:03 pi-GA-MA770-UD3-xbmc kernel: [   19.143142] ata4.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Nov 22 09:53:03 pi-GA-MA770-UD3-xbmc kernel: [   19.143142]          res 50/00:03:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Nov 22 09:53:03 pi-GA-MA770-UD3-xbmc kernel: [   19.143207] ata4.00: status: { DRDY }
Nov 22 09:53:03 pi-GA-MA770-UD3-xbmc kernel: [   19.143260] ata4: hard resetting link
Nov 22 09:53:04 pi-GA-MA770-UD3-xbmc kernel: [   19.634884] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 22 09:53:05 pi-GA-MA770-UD3-xbmc kernel: [   20.437084] ata4.00: configured for UDMA/100
Nov 22 09:53:06 pi-GA-MA770-UD3-xbmc kernel: [   21.250386] ata4: EH complete
Nov 22 09:53:08 pi-GA-MA770-UD3-xbmc kernel: [   23.582425] NVRM: GPU at 0000:01:00: GPU-3b2d72fa-fdfd-930f-446b-d6edcb123f19
```

---

### Post by Doug S on 2012-11-22
> **cariboo907 said:**
> Seeing a logging doesn't work, when the system won't boot, see the crummy cell phone picture. :)Long shot suggestion: Do you have a USB hub? If yes, try without it. I am wondering if there is some different manifestation of the old USB hubs and AMD processors core detection issues. (which yes, seems bizzare.)
 
Reference: [http://ubuntuforums.org/showpost.php?p=12356703&postcount=16](http://ubuntuforums.org/showpost.php?p=12356703&postcount=16)

---

### Post by wnelson on 2012-11-22
I have a Lenovo b575 with AMD E-350. 3.7.0-030700-rc5-generic boot with no problem at all.

Walt

---

### Post by cariboo on 2012-11-22
> **Doug S said:**
> Long shot suggestion: Do you have a USB hub? If yes, try without it. I am wondering if there is some different manifestation of the old USB hubs and AMD processors core detection issues. (which yes, seems bizzare.)
 
Reference: [http://ubuntuforums.org/showpost.php?p=12356703&postcount=16](http://ubuntuforums.org/showpost.php?p=12356703&postcount=16)

No USB hub here, all devices are plugged directly into the motherboard.

---

### Post by ventrical on 2012-11-23
> **cariboo907 said:**
> No USB hub here, all devices are plugged directly into the motherboard.


But for the wireless optical mouse?   Is there a plug-in adapter that sticks into the USB female socket ??

---

### Post by MWisBest on 2012-11-23
I'm not having any issues with my A8-4500M and all the 3.7 kernels that have been released.

---

### Post by cariboo on 2012-11-23
> **ventrical said:**
> But for the wireless optical mouse?   Is there a plug-in adapter that sticks into the USB female socket ??

This is a fairly old mouse, and has a big honking transceiver. :-D

---

### Post by ventrical on 2012-11-23
> **cariboo907 said:**
> This is a fairly old mouse, and has a big honking transceiver. :-D


Yes .. that's a gem alright :)

---

### Post by lompolo on 2012-11-23
Compare your system and this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822)

Do you have same sata/IDE controller? Same usb controller etc. Wild guess is pata_jmicron driver.

Have you tested 3.7-rc4 or rc2 or rc6 etc?

---

### Post by ventrical on 2012-11-23
> **jfernyhough said:**
> All builds (scroll to the bottom):
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

rc6:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/)


These links just spin .. no connect.

---

### Post by cariboo on 2012-11-23
> **lompolo said:**
> Compare your system and this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822)

Do you have same sata/IDE controller? Same usb controller etc. Wild guess is pata_jmicron driver.

Have you tested 3.7-rc4 or rc2 or rc6 etc?

My motherboard uses the Nvidia MCP61 chipset for SATA and USB. I've only tried rc6.

```
sudo lshw
```

```
 product: MS-7309 (To Be Filled By O.E.M.)
    vendor: MSI
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00000000-0000-0000-0000-002421B76949
  *-core
       description: Motherboard
       product: MS-7309
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V9.5
          date: 04/09/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X2 240 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) II X2 240 Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2829MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:4f00(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP61 SMU
          vendor: NVIDIA Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:80000000-8007ffff
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:ded7f000-ded7ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:ded7ec00-ded7ecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:d000(size=4096) memory:dee00000-deefffff
        *-network
             description: Ethernet interface
             product: DGE-530T Gigabit Ethernet Adapter (rev 11)
             vendor: D-Link System Inc
             physical id: 9
             bus info: pci@0000:01:09.0
             logical name: eth0
             version: 11
             serial: 00:1b:11:b2:63:65
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full ip=192.168.0.10 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:19 memory:deefc000-deefffff ioport:df00(size=256) memory:deec0000-deedffff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:ded78000-ded7bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fff0(size=16)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:ce00(size=8) ioport:cd80(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb80(size=16) memory:ded7d000-ded7dfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:e000(size=4096) memory:def00000-dfffffff ioport:c0000000(size=503316480)
        *-display
             description: VGA compatible controller
             product: GT218 [GeForce 210]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ef80(size=128) memory:def80000-deffffff
        *-multimedia
             description: Audio device
             product: High Definition Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:18 memory:def7c000-def7ffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 7
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250310AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 6RY6X9QJ
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00016e1c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: f2a75327-fd7d-4f89-abee-78633cd69dea
                size: 10000MiB
                capacity: 10000MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2012-04-26 16:57:39 filesystem=ext4 lastmountpoint=/ modified=2012-10-20 17:27:02 mounted=2012-11-02 13:27:57 state=clean
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: 0af95ddd-e62a-4494-9ada-02b7b5288e50
                size: 2000MiB
                capacity: 2000MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: 28ab740f-2027-46a2-b6c9-093c0675ded0
                size: 97GiB
                capacity: 97GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2012-04-26 16:57:50 filesystem=ext4 lastmountpoint=/media/cariboo/28ab740f-2027-46a2-b6c9-093c0675ded0 modified=2012-11-10 18:07:45 mounted=2012-11-10 17:12:52 state=clean
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 29GiB
                capacity: 29GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 10000MiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 19GiB
     *-scsi:1
          physical id: a
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250620A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 3.AA
             serial: 6QE10TQ9
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000aa8aa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: 2667a4b4-45bb-4963-9493-9ab73c80e1fe
                size: 9536MiB
                capacity: 9536MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-10-19 14:27:23 filesystem=ext4 lastmountpoint=/ modified=2012-11-23 09:59:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-11-23 09:59:47 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                logical name: /home
                version: 1.0
                serial: ca094542-6fc2-4236-ad87-36f2de997569
                size: 139GiB
                capacity: 139GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-10-19 14:27:27 filesystem=ext4 lastmountpoint=/home modified=2012-11-23 09:59:47 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2012-11-23 09:59:47 state=mounted
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sdb3
                version: 1.0
                serial: 73e94339-887d-4391-be8f-cf629f4ab62f
                size: 9537MiB
                capacity: 9537MiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-10-20 16:43:09 filesystem=ext4 lastmountpoint=/ modified=2012-10-20 19:25:17 mounted=2012-10-20 19:25:17 state=clean
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sdb4
                version: 1.0
                serial: d839fec6-0a4d-4167-a0be-b4a7014b704c
                size: 74GiB
                capacity: 74GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2012-10-20 16:43:23 filesystem=ext4 lastmountpoint=/media/cariboo/d839fec6-0a4d-4167-a0be-b4a7014b704c modified=2012-11-10 18:07:45 mounted=2012-11-10 17:13:09 state=clean
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4167B
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: DL10
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by jppr on 2012-11-24
[https://launchpad.net/ubuntu/raring/+source/libusb/2:0.1.12-23+nmu1ubuntu1](https://launchpad.net/ubuntu/raring/+source/libusb/2:0.1.12-23+nmu1ubuntu1)

Why that update will not be published or bring repos? Could that update change  somehow produce usb problem when the system boot 3.7 kernel...

---

### Post by dino99 on 2012-11-24
> **jppr said:**
> [https://launchpad.net/ubuntu/raring/+source/libusb/2:0.1.12-23+nmu1ubuntu1](https://launchpad.net/ubuntu/raring/+source/libusb/2:0.1.12-23+nmu1ubuntu1)

Why that update will not be published or bring repos? Could that update change  somehow produce usb problem when the system boot 3.7 kernel...

it has been published:
 Colin Watson <cjwatson@ubuntu.com>  Fri, 23 Nov 2012 03:05:34 +0000

---

### Post by jppr on 2012-11-24
If it is in repos, why I can´t update it... 

E. O-Ou = ) I've updated it, my bad = ) That update don´t change anything...

---

### Post by dino99 on 2012-11-24
> **jppr said:**
> If it is in repos, why I can´t update it...

did you got error ? Why are you saying you cannot update it ?

---

### Post by jerrylamos on 2012-11-25
Yesterday's amd64 .iso booted O.K. just now.

Acer Aspire 5253 wide screen notebook, external monitor, hidden wireless network.

AMD E-350 dual processor.  Actual 1.6 gHz, /proc/cpuinfo shows as 800 mHz some of the time like right now.  bogomips 3191.85 whatever that means to Linus.  My 3.3 gHz Celeron 32 bits is about twice as fast somewhere in the 6000's as I remember.

wireless Microsoft mouse with the small usb plugin.

Now a few days ago I was having fits booting the amd64 all kinds of grief, finally zsync'd an iso that worked.

---

### Post by cariboo on 2012-11-25
@jerrylamos, your AMD E-350 is probably throttled back, if you run powertop, you should see something like the screenshot, the screenshot is from my netbook, as I haven't got throttling setup on this system.

---

### Post by jerrylamos on 2012-11-26
> **cariboo907 said:**
> @jerrylamos, your AMD E-350 is probably throttled back, if you run powertop, you should see something like the screenshot, the screenshot is from my netbook, as I haven't got throttling setup on this system.

```

Quantal cpu MHz  1600.000  bogomips 3192.11
Raring  cpu Mhz   800.000  bogomips 3192.18

```

So how does Raring run the same bogomips throttled back to half the MHz?

Jerry

---

### Post by cecilpierce on 2012-11-26
Anybody see this on updates? Is it important, been getting it for a couple days now...:confused:

"update-initramfs: Generating /boot/initrd.img-3.7.0-3-generic
WARNING: could not open /tmp/mkinitramfs_LsW7tC/lib/modules/3.7.0-3-generic/modules.builtin: No such file or directory"

---

### Post by ventrical on 2012-11-26
> **cecilpierce said:**
> Anybody see this on updates? Is it important, been getting it for a couple days now...:confused:

"update-initramfs: Generating /boot/initrd.img-3.7.0-3-generic
WARNING: could not open /tmp/mkinitramfs_LsW7tC/lib/modules/3.7.0-3-generic/modules.builtin: No such file or directory"


 I have been getting that for a few weeks now.... just never mentioned it because it installs ok. I thought it may be an f/p.

---

### Post by cecilpierce on 2012-11-26
It seems to only happen with Plymouth updates and I never see any changes in bootup or shutdown plymouth screen, hmmmm!

---

### Post by ventrical on 2012-11-26
Back in the saddle again! ? :)

---

### Post by Doug S on 2012-11-26
> **cecilpierce said:**
> Anybody see this on updates? Is it important, been getting it for a couple days now...:confused:
 
"update-initramfs: Generating /boot/initrd.img-3.7.0-3-generic
WARNING: could not open /tmp/mkinitramfs_LsW7tC/lib/modules/3.7.0-3-generic/modules.builtin: No such file or directory"Yes. I only started with 13.04 testing a few days ago. I couldn't find any reference to the issue except for [this one]("http://ubuntuforums.org/showpost.php?p=12325147&postcount=1") . As ventrical mentioned things seems to work O.K. and I had (or so I tought) bigger issues to deal with, so I continued.

---

### Post by ventrical on 2012-11-26
I just installed rc6 (all seems to be working well now) and go that message several times.

WARNING: could not open /tmp/mkinitramfs_7qQomG/lib/modules/3.7.0-030700rc6-generic/modules.builtin: No such file or directory


...and now .. reboot.

:)

---

### Post by ventrical on 2012-11-26
Works excellently.

Linux ventrical-PY028AA-ABA-A1106N 3.7.0-030700rc6-generic #201211162135 SMP Sat Nov 17 02:36:34 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$

---

### Post by Doug S on 2012-11-26
> **jerrylamos said:**
> ```

Quantal cpu MHz  1600.000  bogomips 3192.11
Raring  cpu Mhz   800.000  bogomips 3192.18

```
 
So how does Raring run the same bogomips throttled back to half the MHz?
 
JerryI think, but am not sure, that the bogomips number is determined during startup when the CPU's are locked in performance mode (max clock rate), and that it is independent of throttling state (i.e. it is the max for that computer)

---

### Post by jerrylamos on 2012-11-26
> **Doug S said:**
> I think, but am not sure, that the bogomips number is determined during startup when the CPU's are locked in performance mode (max clock rate), and that it is independent of throttling state (i.e. it is the max for that computer)

I don't have a clue on what throttling is or how it is set or invoked or looked at?  Thanks, anyone.

p.s. presumably bogomips is a timing routine Linus put in so linux could have some idea how fast/slow the processor was so some decisions could be made on boot and/or setup?

---

### Post by jppr on 2012-11-28
The same problem and the problem persists with a new kernel 3.7.0-4 public, the system will fail to boot, it still freezes and gives those same usb device notifications

---

### Post by ronacc on 2012-11-28
same here I haven't gotten any 3.7 kernel to boot yet . Very much like quantal was for me , it was almost 2 months in before I was able to get off the  precise kernel .

---

### Post by VinDSL on 2012-11-28
> **ronacc said:**
> same here I haven't gotten any 3.7 kernel to boot yet . Very much like quantal was for me , it was almost 2 months in before I was able to get off the  precise kernel .
You know what?!?!?

I was *thinking* about upgrading my hardware, now that my AGP nVidia card has moved to legacy status.  And, I was *leaning toward* superseding my Intel P4 Extreme Edition CPU with an 8-Core AMD.

*Looks like* I'm going with an Intel Core i7...  LoL!  :D

This thread has been an eye-opener for me.  Thanks!

---

### Post by catlover2 on 2012-11-28
> **VinDSL said:**
> 
*Looks like* I'm going with an Intel Core i7...  LoL!  :D

Is there any good reason to believe this issue won't get fixed? I think I'll see if it works with my hardware now...

---

### Post by ventrical on 2012-11-28
I dunno .. but the daily.iso  works just great here on ATi , Intel and nVidia chipsets.

---

### Post by ventrical on 2012-11-28
> **VinDSL said:**
> You know what?!?!?

I was *thinking* about upgrading my hardware, now that my AGP nVidia card has moved to legacy status.  And, I was *leaning toward* superseding my Intel P4 Extreme Edition CPU with an 8-Core AMD.

*Looks like* I'm going with an Intel Core i7...  LoL!  :D

This thread has been an eye-opener for me.  Thanks!


The Intel video always seems to work with Unity 3D and compiz, even on the Intel 64bit series. I have one AMD dualcore 64 bit and have had no problems (on ATi) with these kernels.

---

### Post by catlover2 on 2012-11-28
Works beautifully at the moment.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood [Radeon HD 5670]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:05.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 5
model name	: AMD Athlon(tm) II X4 640 Processor
stepping	: 3
microcode	: 0x10000b6
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save
bogomips	: 6026.88
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
``` Scaling is working.

```
Linux ubuntu 3.7.0-4-generic #12-Ubuntu SMP Tue Nov 27 23:13:21 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by ronacc on 2012-11-28
> **VinDSL said:**
> You know what?!?!?

I was *thinking* about upgrading my hardware, now that my AGP nVidia card has moved to legacy status.  And, I was *leaning toward* superseding my Intel P4 Extreme Edition CPU with an 8-Core AMD.

*Looks like* I'm going with an Intel Core i7...  LoL!  :D

This thread has been an eye-opener for me.  Thanks!

I've been using the combination of amd and nvidia  for a long time and it is only the last couple of cycles that I have had serious problems .

---

### Post by lompolo on 2012-11-30
Try to narrow in which version this regression started.

Try between known working version (3.5) and known not working (3.7)

Start with 3.6-rc4. If that works try 3.6-rc6. if not, then 3.6-rc2.
Then choose next version again between workin and broken.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by jerrylamos on 2012-12-02
Install amd64 worked on

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 20
model		: 1
model name	: AMD E-350 Processor (dual)
stepping	: 0
microcode	: 0x5000028
cpu MHz		: 800.000

No clue why it says 800 MHz.  On previous releases it said 1600 MHz which is the spec.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"
Linux Aspire-5253 3.7.0-4-generic #12-Ubuntu SMP Tue Nov 27 23:13:21 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I'd been updating every day or so including 02-Dec-2012 and it was stuck at 3.7.0-2 so I tried install using
raring-desktop-amd64.iso  02-Dec-2012
and got 3.7.0-4

?

I've got 2 Gb memory and don't use that heavy applications so I don't specify a swap.  This has got 4 ubuntu partions of various levels of Ubuntu and a Mint.  It's a solid state drive and I'd rather not have all of them hammering one address area.

So install got upset with no swap and kept asking me 
backup or continue
so I selected continue and got
backup or continue backup or continue
so I selected continue and got 
backup or continue backup or continue backup or continue
ad nauseum until the window spilled way off the screen.  
Eventually install got tired of that loop and went on to complete.

---

### Post by andrew.46 on 2012-12-02
> **jerrylamos said:**
> No clue why it says 800 MHz.  On previous releases it said 1600 MHz which is the spec.

Dynamic frequency scaling I suspect....

---

### Post by jerrylamos on 2012-12-03
"> **andrew.46 said:**
> Dynamic frequency scaling I suspect....

What's "dynamic frequency scaling" and how do I turn it off?  

Note, I've tried a cpu intensive pi calculation which is the same results with ringtail "800 mHz" as previous ubuntu 's at "1600 mHz".  

Now gtkperf the screen benchmark is no gem with unity/compiz for me anyway.  I'm for function while others are for "visual effects".

---

### Post by zika on 2012-12-03
> **jerrylamos said:**
> "What's "dynamic frequency scaling" and how do I turn it off? There are several ways, as we have written several times here...
The easiest way is:
```
sudo nano /etc/init.d/ondemand
```comment
```
echo -n ondemand > $CPUFREQ
```and add line right below
```
echo -n performance > $CPUFREQ
```To apply it without restart, after aforementioned changes, You could run
```
sudo /etc/init.d/ondemand stop
sudo /etc/init.d/ondemand start
```or run a script
```
for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
do
[ -f $CPUFREQ ] || continue
echo -n performance > $CPUFREQ
done
```with root privileges... I've made alias for that and I run it in /etc/rc.local since I do not want to change significantly vanilla install...
Or, simply, take ondemand out of that folder or take away its execute attribute...
As far as I know performance is a default state of scaling_governor... Until it is changed with ondemand script in /etc/init.d...

---

### Post by ronacc on 2012-12-03
as of todays daily I still can't get any version of the 3.7 kernel to boot , either on my upgraded from quantal install or the daily live cd's , so I'm still stuck on the 3.5.0-17 kernel .

---

### Post by zenarcher on 2012-12-03
> **ronacc said:**
> as of todays daily I still can't get any version of the 3.7 kernel to boot , either on my upgraded from quantal install or the daily live cd's , so I'm still stuck on the 3.5.0-17 kernel .

Same here.  None of the 3.7 kernels are booting for me, either.  All AMD processors.

---

### Post by ronacc on 2012-12-03
same here AMD 64x2 4600+ .

---

### Post by rtalcott on 2012-12-03
AMD 64 X2...install hangs early....the Download updates while installing step.

---

### Post by ventrical on 2012-12-03
As usual, works excellently in the Live session (todays daily). I already have it hard installed from last Friday's iso daily with 3.7.

---

### Post by ventrical on 2012-12-03
All booted well on the hard install. Just will not let me copy screenshots to desktop.

---

### Post by ventrical on 2012-12-03
I installed the latest 3.7 rc 7 and now I got this thing on bootup called the MP BIOS bug .. but it still boots into Unity , runs ok , will not let me set backgrounds and is much slower.

---

### Post by andrew.46 on 2012-12-03
> **jerrylamos said:**
> What's "dynamic frequency scaling" and how do I turn it off? 

My apologies for drifting off topic a little: Not sure that you should really turn this off. Dynamic frequency scaling adjusts the frequency of your processor according to the load currently placed on it and is a cpu feature rather than a bug. This conserves power and reduces the amount of heat generated and is particularly important for a laptop, and this particular chip is designed for laptops. I have noticed in the past that some utilities quote the lower cpu figure rather than the upper.

You can spend as much time as you want adjusting the figures, putting 'steps' in etc but best to *use* the feature rather than simply turn it off particularly on a laptop.

---

### Post by jerrylamos on 2012-12-03
> **andrew.46 said:**
> 
You can spend as much time as you want adjusting the figures, putting 'steps' in etc but best to *use* the feature rather than simply turn it off particularly on a laptop.Thanks for your reply.  It is an Acer Aspire 5253 amd64 on Kernel 3.7, and benchmarks are running like they did at 1600 mHz, I presumed something in raring was making a mistake in posting 800 mHz.  Now this isn't a showstopper so I'll leave it at that.

BTW, this entry is from an IBM Thinkpad, and cat /proc/cpuinfo shows
model name	: Intel(R) Pentium(R) M processor 1500MHz
stepping	: 5
microcode	: 0x7
cpu MHz		: 600.000
Now that's way off topic since it's running i386.

---

### Post by zika on 2012-12-04
> **andrew.46 said:**
> My apologies for drifting off topic a little: Not sure that you should really turn this off. Dynamic frequency scaling adjusts the frequency of your processor according to the load currently placed on it and is a cpu feature rather than a bug. This conserves power and reduces the amount of heat generated and is particularly important for a laptop, and this particular chip is designed for laptops. I have noticed in the past that some utilities quote the lower cpu figure rather than the upper.

You can spend as much time as you want adjusting the figures, putting 'steps' in etc but best to *use* the feature rather than simply turn it off particularly on a laptop.
I did not notice that there was a laptop involved in this question. Mea culpa. In that case You're right and my effort to clear what does &#8222;dynamic frequency scaling&#8220; mean and explain how to turn it off is (largely) off-topic... I even do not remember that it was mentioned that laptop is what we were talking about... @jerryamos has (I think) more machines involved in this talk than Jerry Pournelle (same name, intentionally) had in his columns... ;)

---

### Post by Harry33 on 2012-12-05
Here is the RR kernel 3.7 rc 8

[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13)

---

### Post by ursoraivoso on 2012-12-05
> **Harry33 said:**
> Here is the RR kernel 3.7 rc 8

[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13)

Does this one work? I've tried up to 3.7.0.999 and still have same error, would you please confirm.

Thanks in advance.

---

### Post by VinDSL on 2012-12-05
> **Harry33 said:**
> Here is the RR kernel 3.7 rc 8

[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13)

> **ursoraivoso said:**
> Does this one work? I've tried up to 3.7.0.999 and still have same error, would you please confirm.

Thanks in advance.

I've been using it, since last night, and haven't had any problems (Intel chipset). ;)

```
~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Wed Dec  5 00:29:33 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.0-030700rc8-generic
Unity Release: unity 6.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0.901+git20121123+server-1.13-branch.c0e68f8e-0ubuntu0ricotz~quantal

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

```

---

### Post by ventrical on 2012-12-05
> **Harry33 said:**
> Here is the RR kernel 3.7 rc 8

[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-5.13)

Thanks harry33... and here is the index:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc8-raring/)

---

### Post by aishen on 2012-12-08
Here problem with sempron x3, no problem with AMD64x2
I updated from quantal and as long as I work with 3.5 no problem.
livecd and hdd stopped after USB detection and the only way of rebooting is too shut down with power button.
Any ideas ?

I think I got this kind of problem with ubuntu 10 intel core 2 few years ago
Crucial bug !

---

### Post by dino99 on 2012-12-08
remove the "quiet splash" options from /etc/default/grub then run:

```
sudo update-grub
```

you will see the warnings/errors at boot time to digg around. Maybe update pciids & usbids:

```
sudo update-pciids && update-usbids
```

and/or try with boot option like noacpi or irqpoll or some others
( google around "ubuntu boot option" )

---

### Post by johnnyde94 on 2012-12-08
Have been having same problem with dell dimension c521 with amd 64 live. Having to revert to 3.5 to boot however, downloading 3.7.0-5 kernel and such now and will reply in a few if it works. I also do belive that I have splash off because I could not get It to boot with out it so ill try above commands if first try fails. 
BRB:p

---

### Post by johnnyde94 on 2012-12-08
Update: no luck with 3.7.0-5 (on 12.10) but am trying 

sudo update-pciids && update-usbids
then 
sudo update-grub

---

### Post by johnnyde94 on 2012-12-08
No luck with trying to fix it:cry:](*,):-({|=:frown:#-o:confused::guitar::?: lol

---

### Post by johnnyde94 on 2012-12-08
DOW! this is for ringtail can should I (or someone) report it to quantal too? 

PS. sorry for multible short post

---

### Post by cariboo on 2012-12-08
> **johnnyde94 said:**
> DOW! this is for ringtail can should I (or someone) report it to quantal too? 

PS. sorry for multible short post

Unless you can provide enough information in the bug report, you are more than likely to run into the ***Brad Figg ***bot, that will just keep asking you to install the next latest kernel. This problem isn't writing anything to the logs, so there really isn't much to report, except it doesn't work.

---

### Post by johnnyde94 on 2012-12-08
Thank you ill just wait till the next kernel update but, should I remove the invalid ones?

---

### Post by cariboo on 2012-12-08
> **johnnyde94 said:**
> Thank you ill just wait till the next kernel update but, should I remove the invalid ones?

You might just as well, unless you've got a custom grub menu, as the latest kernel is the one selected automagically, and results in a failed boot, if you aren't paying attention.

I keep trying every kernel release, and will do so until it finally works. :-D

---

### Post by anca-emanuel on 2012-12-09
Install 12.10
Is working ? good; note kernel version: 3.5
Upgrade to Raring.
Kernel 3.7-rc8 not working ?
Test 3.5 again.

You must read this: [https://wiki.ubuntu.com/Kernel/KernelBisection](https://wiki.ubuntu.com/Kernel/KernelBisection)

---

### Post by pqwoerituytrueiwoq on 2012-12-09
i am running a AMD Phenom II 965 BE @3.7GHz CPU and it is stable on kernel 3.7 (from xorg edgers)
```
me@Quantal-Desktop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
me@Quantal-Desktop:~$ uname -r
3.7.0-4-generic
me@Quantal-Desktop:~$ nvidia-settings --version

nvidia-settings:  version 310.19  (buildd@litembilla)  Tue Nov 13 23:04:41 UTC
2012
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.
```

---

### Post by VinDSL on 2012-12-09
> **pqwoerituytrueiwoq said:**
> i am running a AMD Phenom II 965 BE @3.7GHz CPU and it is stable on kernel 3.7 (from xorg edgers)
Which mobo are you running?

I'm "in the market"...  :)

---

### Post by pqwoerituytrueiwoq on 2012-12-09
link in my sig, i have a M4A79XTD EVO, there is a USB 3 version, you should go with a AM3+ Board IMO, that was not a option or it was too expense when i built my system

---

### Post by VinDSL on 2012-12-09
> **pqwoerituytrueiwoq said:**
> link in my sig, i have a M4A79XTD EVO, there is a USB 3 version, you should go with a AM3+ Board IMO, that was not a option or it was too expense when i built my system
Doh!  Was that in your sig before?!?!?!?

I've been distracted by putting up a Christmas tree today.

Got the curtains open, and it's so bright in here, I can hardly see the screen.

Maybe Santa will bring me a new mobo, and 128GB DDR3 RAM...  LoL!  :D

---

### Post by ventrical on 2012-12-09
All still working here on this old machine.

---

### Post by pqwoerituytrueiwoq on 2012-12-09
> **VinDSL said:**
> Doh!  Was that in your sig before?!?!?!?

I've been distracted by putting up a Christmas tree today.

Got the curtains open, and it's so bright in here, I can hardly see the screen.

Maybe Santa will bring me a new mobo, and 128GB DDR3 RAM...  LoL!  :Dbeen there for a long time, are you doing serious video editing or running a server
we can't have a tree the cats would destroy it, less hassle to deal with anyway :)

---

### Post by johnnyde94 on 2012-12-11
> **cariboo907 said:**
> Unless you can provide enough information in the bug report, you are more than likely to run into the ***Brad Figg ***bot, that will just keep asking you to install the next latest kernel. This problem isn't writing anything to the logs, so there really isn't much to report, except it doesn't work.

What info do you need?

---

### Post by lompolo on 2012-12-12
> **johnnyde94 said:**
> What info do you need?

according to: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822)

First step: Does the v3.6-rc1 kernel boot?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/)

---

### Post by johnnyde94 on 2012-12-12
> **lompolo said:**
> according to: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822)

First step: Does the v3.6-rc1 kernel boot?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc1-quantal/)

No luck booting with 3.6-rc1

---

### Post by pqwoerituytrueiwoq on 2012-12-12
> **johnnyde94 said:**
> No luck booting with 3.6-rc1
what about 3.6.3
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)

---

### Post by lompolo on 2012-12-13
> **johnnyde94 said:**
> No luck booting with 3.6-rc1

This information is now also in bug report. That is good. 

Next step is bisecting between 3.5 and 3.6-rc1. This is regression. Therefore it is much more useful than testing any random kernels or newest.

If you are not familiar with bisecting and kernel compilation let's wait developer response.

---

### Post by Carterclan on 2012-12-16
No problem here

---

### Post by kurt18947 on 2012-12-16
Very similar machine to ventrical above - Athlon II X2 with Nvidia 8400GS video.  Running a live USB install latest daily.  No issues so far except trying the default boot menu choice said I had a corrupt kernel image.    Selecting live session booted and functions fine so I'm pretty sure the kernel image is not corrupt ;).

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.7.0-6-generic #14-Ubuntu SMP Tue Dec 11 13:13:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ronacc on 2012-12-16
still no joy for me as of todays daily . it dies at the same place as any attempt to boot from the hard disk with any kernel later than 3.5 . Its got to be either my MOBO (gigabyte ) or drive setup ( 2 ide 4 SATA ) .

---

### Post by andrew.46 on 2012-12-16
Steady as a rock here...

---

### Post by lompolo on 2012-12-17
Here is some more info about bisecting
[http://wiki.debian.org/DebianKernel/GitBisect](http://wiki.debian.org/DebianKernel/GitBisect)

```
sudo apt-get install git
sudo apt-get build-dep linux-meta
```
install git and packages kernel building will need.

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
```
This will load lot of linux sources. If you save it you can update it later with git pull

```
cd linux-2.6
```
2.6 is just a name.

```
cp /boot/config-3.5 .config
```
choose config from working kernel.

```
git bisect start v3.6-rc1 v3.5
```
We want to test what changed between these versions. It will tell how many builds are needed at worst.

BUILD:

```
sudo fakeroot make deb-pkg
```
```
sudo dpkg -i ../linux-image-something
```
Build new kernel. and install it. (the new version of course)

```
sudo update-grub
```

reboot

Go again to linux directory.
```
git bisect good
```
if that was working or
```
git bisect bad
```
if it was bad

Repeat build until ready.

---

### Post by ronacc on 2012-12-17
A couple of days ago I went as far as the first bisect , the resultant kernel failed to boot I may try another bisect starting with that one . The problem I think is in the way the newer kernels handle mixed IDE and sata drives . The boot stalls after attaching the first 2 drives , which I think are the IDE drives , its hard to tell since the kernel calls everything SD(x) . I took the dvd of yesterdays daily which would not boot in my test box and it boots fine in my "work" box which is also AMD 64x2 and nvidia so that isnt the problem allso that box has only sata drives .

---

### Post by johnnyde94 on 2012-12-17
> **johnnyde94 said:**
> No luck booting with 3.6-rc1

Kernel 3.6-rc1 broke my CPU:( I can put on CPU but when I go to desk top all I see is a black arrow but can got to tty and update

---

### Post by jppr on 2012-12-18
I just tried to install today's Daily-Live, but that is only going to be anything at all. The installation runs just the same notifications of new USB devices than before, and then it freezes. If the problem is not USB 3.7 drivers in the kernel so that where a problem might exist? When the 3.5 kernel works without any problems.

My system is... Asus M2N68-AM PLUS motherboard, AMD Athlon 250 II X 2, 2 x 2 GB Kingston DDR2 and Nvidia 9400 Gt

---

### Post by zenarcher on 2012-12-18
> **jppr said:**
> I just tried to install today's Daily-Live, but that is only going to be anything at all. The installation runs just the same notifications of new USB devices than before, and then it freezes. If the problem is not USB 3.7 drivers in the kernel so that where a problem might exist? When the 3.5 kernel works without any problems.

My system is... Asus M2N68-AM PLUS motherboard, AMD Athlon 250 II X 2, 2 x 2 GHz Kingston DDR2 and Nvidia 9400 Gt

Exactly the same situation I have with my USB KVM switch....freezes when it gets there while loading.  I am also using an AMD X2 processor.  No problems at all with kernel 3.5 nor any previous to that.

zenarcher

---

### Post by pqwoerituytrueiwoq on 2012-12-18
never had any issue with my moms athlon II x2 250 rengor cpu on the 3.7 kernel (qantal+xorg edgers)
but this is on a am3 boards

---

### Post by Lyfang on 2012-12-18
Hi! I found this link: [Install Linux Kernel 3.7.1 On Ubuntu 12.10/12.04 and Linux Mint 14/13]("http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html")

---

### Post by geofb on 2012-12-20
HP-Pavilion AY597AA-ABL HPE-110f/ALOE, BIOS 5.03 09/11/2009
AMD Phenom(tm) II X4 925 

This setup worked with kernels up until 3.6.10
Then it froze on: Loading initial ramdisk...

Same problem with 3.7.0 and 3.7.1

I got the machine to boot on 3.7.1 using: noapic nolapic noacpi

Once the machine was up, I reapplied the AMD microcode:

sudo aptitude reinstall amd64-microcode

Thereafter, machine boots without the need for: noapic nolapic noacpi

Linux hp 3.7.1-030701-generic #201212171620 SMP Mon Dec 17 21:21:30 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by zika on 2012-12-20
> **geofb said:**
> HP-Pavilion AY597AA-ABL HPE-110f/ALOE, BIOS 5.03 09/11/2009
AMD Phenom(tm) II X4 925 

This setup worked with kernels up until 3.6.10
Then it froze on: Loading initial ramdisk...

Same problem with 3.7.0 and 3.7.1

I got the machine to boot on 3.7.1 using: noapic nolapic noacpi

Once the machine was up, I reapplied the AMD microcode:

sudo aptitude reinstall amd64-microcode

Thereafter, machine boots without the need for: noapic nolapic noacpi

Linux hp 3.7.1-030701-generic #201212171620 SMP Mon Dec 17 21:21:30 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
That might be the reason I did not get any problems with 3.7 on AMD.
I've used microcode for quite some time: [http://ubuntuforums.org/showthread.php?t=1945481]("http://ubuntuforums.org/archive/index.php/t-1945481.html")
Remedy I've used is just the same as it is in amd64-microcode with exception of some scripts and documents...
Thank You.
At the time I was trying to solve that problem, I did not notice that a package was available... It is nice to have it now...
(Ater some searching, when time permitted, there is same package for Quantal, emerged after my post given above, and it is also backported later for Precise...)

---

### Post by cariboo on 2012-12-20
I've had the amd84-microcode installed from the beginning, as I was getting a missing microcode error on boot. I didn't notice if there is a newer version available for the 3.7 kernel.

I'm using amd64-microcode (1.20120910-2) unstable.

---

### Post by zika on 2012-12-20
> **cariboo907 said:**
> I've had the amd84-microcode installed from the beginning, as I was getting a missing microcode error on boot. I didn't notice if there is a newer version available for the 3.7 kernel.

I'm using amd64-microcode (1.20120910-2) unstable.
Now Your original question that started this thread should be changed from
> **cariboo907 said:**
> Just out of curiosity, how many of us with  AMD cpu's are having trouble booting the the latest kernel available in  the repositories?

My Intel atom powered netbook runs just fine with the 3.7.0.2 kernel.to

&#8222;Just out of curiosity, how many of us with  AMD cpu's that are having trouble booting the the latest kernel available in  the repositories have amd64-microcode (one way or another) installed?&#8220;

NHF,  just a teaser... ):P

Update&#8321;: To be serious: I've noticed since I've started work today with it that 3.7.0-7-generic #15-Ubuntu is noticeably slower than 999(daily) from mainline... It even seems to be slower that lowlatency of same version...

---

### Post by VinDSL on 2012-12-20
> **zika said:**
> Update&#8321;: To be serious: I've noticed since I've started work today with it that 3.7.0-7-generic #15-Ubuntu is noticeably slower than 999(daily) from mainline... It even seems to be slower that lowlatency of same version...
Heh!  Glad to hear that... in an odd way.

I was using the Ubu 3.7 final from the official PPA (for a few days) and this machine was flying like the wind.  Fast, everything was responsive, and so forth, and so on.

Now, I'm running the 3.7.1-030701 kernel, and it's dogging it, again.

Just saying...

---

### Post by zika on 2012-12-20
> **VinDSL said:**
> Heh!  Glad to hear that... in an odd way.

I was using the Ubu 3.7 final from the official PPA (for a few days) and this machine was flying like the wind.  Fast, everything was responsive, and so forth, and so on.

Now, I'm running the 3.7.1-030701 kernel, and it's dogging it, again.

Just saying...Bad news, 999 just panicked twice on me... I've jinxed it...
It is obviously suffering from pre-3.8 virus...
Trouble is that I was playing with scheduling, latency and such stuff and I might be to blame beside kernel itself...
Update&#8321;: No, it's not my fault, liquorix 3.6 flies...

---

### Post by VinDSL on 2012-12-20
> **zika said:**
> Update&#8321;: No, it's not my fault, liquorix 3.6 flies...
I've always loved Liquorix kernels -- always have it on tap!

Dittos for Ubu 10.10 and trust 2.6.x.

Those are my two fallbacks, when +1 takes a dive...  ;)

---

### Post by zika on 2012-12-20
> **VinDSL said:**
> I've always loved Liquorix kernels -- always have it on tap!

Dittos for Ubu 10.10 and trust 2.6.x.

Those are my two fallbacks, when +1 takes a dive...  ;)Which it does more and more RaRely... (pun intended)...

---

### Post by johnnyde94 on 2012-12-20
3.7.0.7.11 error info...

---

### Post by kevpan815 on 2012-12-20
I won't be able to test today's Nightly Build with my Dell AMD Processor and ATI Radeon Graphics Card Desktop today (due to the Winter Snow Storm hitting the Chicago Area right now as I am right now using my Dell Intel Netbook Only at the moment due to the fact that the lights just flickered and obviously my desktop does NOT have a Battery in the PC like my Dell Netbook has, but I will try Zsyncing tomorrow's Nightly Build assuming that we have power tomorrow morning and let you guys know how it turns out.

---

### Post by kevpan815 on 2012-12-20
> **cariboo907 said:**
> Just out of curiosity, how many of us with AMD cpu's are having trouble booting the the latest kernel available in the repositories?

My Intel atom powered netbook runs just fine with the 3.7.0.2 kernel.

I just tried installing 3.7.1 (on an Intel EM64T Processor running AMD64 13.04, and got an Error saying that I had a Bad Download, don't know why however, unless my WIFI connection is not 100% at the moment, which very well could be a possibility with the Winter Snow Storm affecting us here in the Windy City, my ISP is Verizon Wireless by the way.

---

### Post by pqwoerituytrueiwoq on 2012-12-20
> **kevpan815 said:**
> I just tried installing 3.7.1 (on an Intel EM64T Processor running AMD64 13.04, and got an Error saying that I had a Bad Download, don't know why however, unless my WIFI connection is not 100% at the moment, which very well could be a possibility with the Winter Snow Storm affecting us here in the Windy City, my ISP is Verizon Wireless by the way.
check the md5sum, sometimes data gets damaged in transit, yuo may have a incomplete download

---

### Post by manulemaboul on 2012-12-21
Same as many people here, I've tried all kernels and nothing boot since the 3.6 RC1.
After reading the thread, I've tried installing the amd64-microcode, still hangs.

Tried the noapic noacpi nolapic command lines, still hangs after enumerating my USB peripherals.

My config is an opteron 170 / dfi lanparty nforce 4 ultra D, using x386, not x64.
 
This is driving me crazy, I can't figure out what's going wrong and searching the web didn't helped :(.
I don't want to be stucked with 3.5.7 forever :/.

Downloading latest raring desktop image AMD64, I'll try to see if it boot from USB using x64 and amd64-microcode.

---

### Post by kevpan815 on 2012-12-21
> **manulemaboul said:**
> Same as many people here, I've tried all kernels and nothing boot since the 3.6 RC1.
After reading the thread, I've tried installing the amd64-microcode, still hangs.

Tried the noapic noacpi nolapic command lines, still hangs after enumerating my USB peripherals.

My config is an opteron 170 / dfi lanparty nforce 4 ultra D, using x386, not x64.
 
This is driving me crazy, I can't figure out what's going wrong and searching the web didn't helped :(.
I don't want to be stucked with 3.5.7 forever :/.

Downloading latest raring desktop image AMD64, I'll try to see if it boot from USB using x64 and amd64-microcode.

My problem was different from yours, the first file (the all.deb file) that you are supposed to install first failed to even install. If someone could give me instructions on how to check the MD5 Sum in Ubuntu (I have checked MD5's before, but only in Microsoft Windows) I would be very grateful. I did wipe my system today when I updated to today's Nightly Build through Zsync and Clean Install but I do have the 3.7.1 Bad Download saved on a DVD Disk just in case I need to create some kind of Bug Report.

---

### Post by pqwoerituytrueiwoq on 2012-12-21
in a terminal
md5sum /path/to/file

---

### Post by manulemaboul on 2012-12-21
I know nothing will work, but can I install the x64 version of the 3.7.1 kernel just to test if it'll boot ? 

Is there any risks ?

---

### Post by cariboo on 2012-12-21
There shouldn't be any problem, if you install the 3.7 kernel, just make sure you have something to fallback on, either a running install with the 3.5 kernel, or another stable version.

---

### Post by manulemaboul on 2012-12-21
Still got the 3.5.7 i386 kernel wich is working, using it right now.

I was a bit scared that the x64 one could break some system files or something.
Let's try then, thanks :).

---

### Post by williejones on 2012-12-21
> **kevpan815 said:**
> My problem was different from yours, the first file (the all.deb file) that you are supposed to install first failed to even install. If someone could give me instructions on **how to check the MD5 Sum in Ubuntu **(I have checked MD5's before, but only in Microsoft Windows) I would be very grateful. I did wipe my system today when I updated to today's Nightly Build through Zsync and Clean Install but I do have the 3.7.1 Bad Download saved on a DVD Disk just in case I need to create some kind of Bug Report.

This is how I check the md5 sum.  I download the iso to my desktop.  In a terminal type cd Desktop. type ls (to see the name o f the iso image), then type md5sum (name of iso image)
Note that you can start the name of the iso then hit tab to autocomplete the name.

After I get the md5 sum highlight and copy the answer.  Go to the web page you downloaded the iso from, look for md5sums.  When you are there select edit, find in the browser and paste your md5 sum in the search box.  See if it is found.

---

### Post by ronacc on 2012-12-22
after not being able to get 3.7 to work for me I tried the 3.8 rc1 and it boots right up .

---

### Post by cariboo on 2012-12-22
> **ronacc said:**
> after not being able to get 3.7 to work for me I tried the 3.8 rc1 and it boots right up .

I can finally boot into a newer kernel too. :-D

---

### Post by zika on 2012-12-23
To clarify: I can boot in 3.8 but I can not stay long to work with it: kernel panics (recursive...)...
It panics almost the second it encounters compiz or minutes after it start gnome-session-fallback...
But, I'm not complaining...

---

### Post by sacridex on 2013-01-01
So when will 3.8 land in raring?
I'm yearningly looking forward to test raring on my amd machine. :)

---

### Post by JMB74 on 2013-01-01
> **sacridex said:**
> So when will 3.8 land in raring?
I'm yearningly looking forward to test raring on my amd machine. :)

[https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Raring](https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Raring)

> As noted last week, we will keep the kernel in the Raring archive on a  v3.7 based kernel until a few upstream v3.8-rc# iterations have passed.   We'll then upload a v3.8 based kernel and remain on the v3.8 kernel for  the remainder of the Raring cycle. So by a few, sounds like it may not be until say RC3 or RC4 perhaps?

Meaning it could be several weeks yet.

---

### Post by kansasnoob on 2013-01-04
Just testing Lubuntu i386 20130104 on this hardware:

AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

And no matter if I choose check for defects, try w/o installing, or install I just get this:

[ATTACH]229583[/ATTACH]

Does that seem like the same issue?

If so is there a bug report?

Sorry for not reading every message, but this is a looooong thread ;)

Edit: It works fine (almost) on this hardware:

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

Note: I say almost because check for defects fails to run properly but I know that's common in early development.

---

### Post by kansasnoob on 2013-01-04
Found one bug report:

[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1082673](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1082673)

Looks very similar ....... I think ;)

---

### Post by cariboo on 2013-01-05
@kansasnoob, you screenshot is quite similar to the one I posted earlier in the thread. Boot on my system stops at the same place, the only difference is the peripheral manufacturers name.

---

### Post by kansasnoob on 2013-01-05
> **cariboo907 said:**
> @kansasnoob, you screenshot is quite similar to the one I posted earlier in the thread. Boot on my system stops at the same place, the only difference is the peripheral manufacturers name.

Found it:

[http://ubuntuforums.org/showpost.php?p=12366104&postcount=37](http://ubuntuforums.org/showpost.php?p=12366104&postcount=37)

And maybe this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822)

---

### Post by Gyokuro on 2013-01-05
I'm not an AMD user but I have searched the [www.kernel.org](www.kernel.org) git history tree and until kernel 3.8-rc1 only following patch went in which explicitly mentioning an AMD problem: 

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=787314c35fbb97e02823a1b8eb8cfa58f366cd49](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=787314c35fbb97e02823a1b8eb8cfa58f366cd49)

so it seems that this part is missing in 3.7. Maybe I have overlooked something and the kernel guys have to cook a patch for your AMD problem.

---

### Post by hlewis on 2013-01-11
Have not been able to boot into 3.7 kernel since the upgrade, tried most if not all of the suggested fixes, nothing has worked.   Noting that that the boot sequence appeared to stop at the logitech listing for the mouse... I disconnected the Mouse, that action resulted in the stop appearing at Power Resource to register!  On a whim decided to disable ACPI in bios, didn't think this would do much, because as i recall most linux distros's ignore much the bios settings, could be wrong about that.  I saved the settings and rebooted, and much to my surprise 3.7 booted. 

Here is the output of my boot.log

```

Begin: Loading essential drivers ... FATAL: Error inserting microcode (/lib/modules/3.7.0-7-generic/kernel/arch/x86/kernel/microcode.ko): No such device
done.
Begin: Running /scripts/init-premount ... Begin: Requesting microcode update using per-core interface ... done.
done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux 2.20.1
/dev/sda1: clean, 320549/15073280 files, 2597315/60279552 blocks
modem-manager[687]: <info>  ModemManager (version 0.6.0.0) starting...

modem-manager[687]: <info>  Loaded plugin 'SimTech'

modem-manager[687]: <info>  Loaded plugin 'Option'

modem-manager[687]: <info>  Loaded plugin 'Linktop'

modem-manager[687]: <info>  Loaded plugin 'X22X'

modem-manager[687]: <info>  Loaded plugin 'Option High-Speed'

modem-manager[687]: <info>  Loaded plugin 'Nokia'

modem-manager[687]: <info>  Loaded plugin 'Longcheer'

modem-manager[687]: <info>  Loaded plugin 'ZTE'

modem-manager[687]: <info>  Loaded plugin 'Wavecom'

modem-manager[687]: <info>  Loaded plugin 'Gobi'

modem-manager[687]: <info>  Loaded plugin 'Novatel'

modem-manager[687]: <info>  Loaded plugin 'Samsung'

modem-manager[687]: <info>  Loaded plugin 'MotoC'

modem-manager[687]: <info>  Loaded plugin 'Sierra'

modem-manager[687]: <info>  Loaded plugin 'Huawei'

modem-manager[687]: <info>  Loaded plugin 'Ericsson MBM'

modem-manager[687]: <info>  Loaded plugin 'AnyData'

modem-manager[687]: <info>  Loaded plugin 'Cinterion'

modem-manager[687]: <info>  Loaded plugin 'Iridium'

modem-manager[687]: <info>  Loaded plugin 'Generic'

modem-manager[687]: <info>  Successfully loaded 20 plugins

 * Setting sensors limits                                                [ OK ] 
 * Starting mDNS/DNS-SD daemon                                           [ OK ]
 * Starting bluetooth daemon                                             [ OK ]
 * Starting CUPS printing spooler/server                                 [ OK ]
 * Starting Samba Auto-reload Integration                                [ OK ]
 * Stopping Samba Auto-reload Integration                                [ OK ]
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Stopping System V initialisation compatibility                        [ OK ]
 * VirtualBox Additions disabled, not in a Virtual Machine
saned disabled; edit /etc/default/saned
 * Starting System V runlevel compatibility                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting automatic crash report generation                            [ OK ]
 * Starting                                                              [ OK ]
 * Starting deferred execution scheduler                                 [ OK ]
 * Starting regular background program processing daemon                 [ OK ]
 * Starting anac(h)ronistic cron                                         [ OK ]
 * Starting                                                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting save kernel messages                                         [ OK ]
 * Starting                                                              [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting CPU interrupts balancing daemon                              [ OK ]
 * Starting ACPI daemon                                                  [ OK ]
 * Starting configure virtual network devices                            [ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 * Stopping save kernel messages                                         [ OK ]
 * Stopping anac(h)ronistic cron                                         [ OK ]
 * Starting web server apache2                                           [ OK ] 
 * Stopping cold plug devices                                            [ OK ]
 * Stopping log initial device creation                                  [ OK ]
 * Starting load fallback graphics devices                               [ OK ]
 * Starting enable remaining boot-time encrypted block devices           [ OK ]
 * Starting save udev log and update rules                               [ OK ]
 * Stopping save udev log and update rules                               [ OK ]
 * Stopping enable remaining boot-time encrypted block devices           [ OK ]
 * Starting load fallback graphics devices                               [fail]
 * Starting GNOME Display Manager                                        [ OK ]
 * Starting                         

```
Make of this what you will but it is booting.   Just thought it may be relevant.

---

### Post by kansasnoob on 2013-01-11
> **hlewis said:**
> Have not been able to boot into 3.7 kernel since the upgrade, tried most if not all of the suggested fixes, nothing has worked.   Noting that that the boot sequence appeared to stop at the logitech listing for the mouse... I disconnected the Mouse, that action resulted in the stop appearing at Power Resource to register!  On a whim decided to disable ACPI in bios, didn't think this would do much, because as i recall most linux distros's ignore much the bios settings, could be wrong about that.  I saved the settings and rebooted, and much to my surprise 3.7 booted. 

Here is the output of my boot.log

```

Begin: Loading essential drivers ... FATAL: Error inserting microcode (/lib/modules/3.7.0-7-generic/kernel/arch/x86/kernel/microcode.ko): No such device
done.
Begin: Running /scripts/init-premount ... Begin: Requesting microcode update using per-core interface ... done.
done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux 2.20.1
/dev/sda1: clean, 320549/15073280 files, 2597315/60279552 blocks
modem-manager[687]: <info>  ModemManager (version 0.6.0.0) starting...

modem-manager[687]: <info>  Loaded plugin 'SimTech'

modem-manager[687]: <info>  Loaded plugin 'Option'

modem-manager[687]: <info>  Loaded plugin 'Linktop'

modem-manager[687]: <info>  Loaded plugin 'X22X'

modem-manager[687]: <info>  Loaded plugin 'Option High-Speed'

modem-manager[687]: <info>  Loaded plugin 'Nokia'

modem-manager[687]: <info>  Loaded plugin 'Longcheer'

modem-manager[687]: <info>  Loaded plugin 'ZTE'

modem-manager[687]: <info>  Loaded plugin 'Wavecom'

modem-manager[687]: <info>  Loaded plugin 'Gobi'

modem-manager[687]: <info>  Loaded plugin 'Novatel'

modem-manager[687]: <info>  Loaded plugin 'Samsung'

modem-manager[687]: <info>  Loaded plugin 'MotoC'

modem-manager[687]: <info>  Loaded plugin 'Sierra'

modem-manager[687]: <info>  Loaded plugin 'Huawei'

modem-manager[687]: <info>  Loaded plugin 'Ericsson MBM'

modem-manager[687]: <info>  Loaded plugin 'AnyData'

modem-manager[687]: <info>  Loaded plugin 'Cinterion'

modem-manager[687]: <info>  Loaded plugin 'Iridium'

modem-manager[687]: <info>  Loaded plugin 'Generic'

modem-manager[687]: <info>  Successfully loaded 20 plugins

 * Setting sensors limits                                                [ OK ] 
 * Starting mDNS/DNS-SD daemon                                           [ OK ]
 * Starting bluetooth daemon                                             [ OK ]
 * Starting CUPS printing spooler/server                                 [ OK ]
 * Starting Samba Auto-reload Integration                                [ OK ]
 * Stopping Samba Auto-reload Integration                                [ OK ]
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Stopping System V initialisation compatibility                        [ OK ]
 * VirtualBox Additions disabled, not in a Virtual Machine
saned disabled; edit /etc/default/saned
 * Starting System V runlevel compatibility                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting automatic crash report generation                            [ OK ]
 * Starting                                                              [ OK ]
 * Starting deferred execution scheduler                                 [ OK ]
 * Starting regular background program processing daemon                 [ OK ]
 * Starting anac(h)ronistic cron                                         [ OK ]
 * Starting                                                              [ OK ]
 * Starting                                                              [ OK ]
 * Starting save kernel messages                                         [ OK ]
 * Starting                                                              [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting CPU interrupts balancing daemon                              [ OK ]
 * Starting ACPI daemon                                                  [ OK ]
 * Starting configure virtual network devices                            [ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 * Stopping save kernel messages                                         [ OK ]
 * Stopping anac(h)ronistic cron                                         [ OK ]
 * Starting web server apache2                                           [ OK ] 
 * Stopping cold plug devices                                            [ OK ]
 * Stopping log initial device creation                                  [ OK ]
 * Starting load fallback graphics devices                               [ OK ]
 * Starting enable remaining boot-time encrypted block devices           [ OK ]
 * Starting save udev log and update rules                               [ OK ]
 * Stopping save udev log and update rules                               [ OK ]
 * Stopping enable remaining boot-time encrypted block devices           [ OK ]
 * Starting load fallback graphics devices                               [fail]
 * Starting GNOME Display Manager                                        [ OK ]
 * Starting                         

```
Make of this what you will but it is booting.   Just thought it may be relevant.

Good find! I just tried the same Lubuntu disc that had earlier failed on me and used the acpi=off boot parameter as shown here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Success :D

The screen resolution is too low but that may even be a different issue. It's adequate to allow installation though, after which I could fiddle with the nVidia drivers ;)

---

### Post by ventrical on 2013-01-11
I just booted up the daily (raring-desktop-amd64.iso) last night on my Acer Extensa and it works just fine. 3.7.0-7

---

### Post by sacridex on 2013-01-13
3.8 kernel has landed in raring and now its working fine! :)
(amd 64 x2 6000+, asus m2n sli deluxe)

---

### Post by ronparent on 2013-01-13
> 3.8 kernel has landed in raring and now its working fine! 
(amd 64 x2 6000+, asus m2n sli deluxe)

Same here!!!! Nothing seems to be broken - yet!!!!!!

---

### Post by kuvanito on 2013-02-01
> **cariboo907 said:**
> Just out of curiosity, how many of us with AMD cpu's are having trouble booting the the latest kernel available in the repositories?

My Intel atom powered netbook runs just fine with the 3.7.0.2 kernel.

i was looking for some help but can't find any.
long ago i gave up on installing ubuntu on any amd cpu computer,why? because they gave me nothing but problems....
yesterday someone gave me a dell pc with an amd athlon x2 cpu and nvidia chipset with 2g of ram and inmediatly i downloaded my 64bit iso of the day and proceed to test it,for man sake,this amd's cpu continue to be the crap they have always been,there is no way i could run that daily build in this machine and this is something i do daily on my intel rig.i will never ever use an amd pc for my self with any other os that windows,they are crap to me,my own opinion OK,hehehehe in the other hand i continue to have crashes at all time with 64bit but 32bit runs smooth,so i am giving up on 64bit for now until RR is released and then i'll see.....happy testing....
hey do you need an amd pc? is outside by the curve if you make it before the garbage truck by 6:00 am today 02/01/2013 hehehehehehe....1 hour left...

---

### Post by jerrylamos on 2013-02-01
I've been running Acer Aspire 5253 with amd64 for the last couple of years on a variety of Ubuntu's up to 3.8.0-2, linux mint, debian, ... most of the time running fine, 32 bit and 64 bit.

Biggest difficulty has been installing an ubuntu on a USB hard drive with the Acer.  It will boot and run from the USB where I test Ubuntu's, but attempts to install to the USB screw everything up.  Grub goes into a mess particularly Grub 2.  "Don't install onto USB from the Acer amd64!".

In times past I had a Windows 7 hard drive and installing onto the USB hard drive I couldn't boot anything.  Easy to remove the Windows 7 hard drive to sve it and put in another one for testing.

So I do the installs on USB plugged into intel netbook and tower with no problem whatsoever.  Once installed somewhere else they will run fine on the amd64.

With no USB hard drive, the Acer amd64 installs and runs various 32 bit and 64 bit linux's fine. 

Just nicer on my Intel netbook and tower I can install several linux on USB hard drive for testing etc.

---

### Post by ventrical on 2013-02-02
> **kuvanito said:**
> i was looking for some help but can't find any.
long ago i gave up on installing ubuntu on any amd cpu computer,why? because they gave me nothing but problems....
yesterday someone gave me a dell pc with an amd athlon x2 cpu and nvidia chipset with 2g of ram and inmediatly i downloaded my 64bit iso of the day and proceed to test it,for man sake,this amd's cpu continue to be the crap they have always been,there is no way i could run that daily build in this machine and this is something i do daily on my intel rig.i will never ever use an amd pc for my self with any other os that windows,they are crap to me,my own opinion OK,hehehehe in the other hand i continue to have crashes at all time with 64bit but 32bit runs smooth,so i am giving up on 64bit for now until RR is released and then i'll see.....happy testing....
hey do you need an amd pc? is outside by the curve if you make it before the garbage truck by 6:00 am today 02/01/2013 hehehehehehe....1 hour left...


Dern!!:mad:

---

### Post by zika on 2013-02-02
Yet another AMD discarded too soon...

---

### Post by ventrical on 2013-02-02
> **zika said:**
> Yet another AMD discarded too soon...


I just love taking those roadside tosses and bringing them back from the shredders teeth:)

I have been lucky so far with AMD athlon 2x acer extensa 4420 64bit.  Also an AMD 32 bit 1.2 GHz..

---

### Post by ventrical on 2013-02-02
Just zsynced the daily and got a seamless live USB on:

```

0:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)


```

---

### Post by VinDSL on 2013-02-03
> **cariboo907 said:**
> I tried the rc6 yesterday, and I do have the amd-microcode installed, and still no joy. :(

> **jfernyhough said:**
> Same odd naming on an i5, so it's not AMD-specific
Interesting!

I never realized that AMD & Intel microcode are both available.

I just installed Intel microcode via Synaptic and it seems to be working fine...

```
vindsl@Zuul:~$ cat /proc/cpuinfo | grep 'model name' | cut -c 13-60
 Intel(R) Pentium(R) 4 CPU 3.40GHz
 Intel(R) Pentium(R) 4 CPU 3.40GHz

vindsl@Zuul:~$ dmesg | grep microcode
[    2.020696] microcode: CPU0 sig=0xf25, pf=0x4, revision=0x1b
[    2.021259] microcode: CPU0 updated to revision 0x2b, date = 2004-08-11
[    2.021278] microcode: CPU1 sig=0xf25, pf=0x4, revision=0x1b
[    2.021578] microcode: CPU1 updated to revision 0x2b, date = 2004-08-11
[    2.022487] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba 
```

Learn something new every day.

Just saying...

---

### Post by cariboo on 2013-02-03
> **VinDSL said:**
> Interesting!

I never realized that AMD & Intel microcode are both available.

I just installed Intel microcode via Synaptic and it seems to be working fine...

```
vindsl@Zuul:~$ dmesg | grep microcode
[    2.020696] microcode: CPU0 sig=0xf25, pf=0x4, revision=0x1b
[    2.021259] microcode: CPU0 updated to revision 0x2b, date = 2004-08-11
[    2.021278] microcode: CPU1 sig=0xf25, pf=0x4, revision=0x1b
[    2.021578] microcode: CPU1 updated to revision 0x2b, date = 2004-08-11
[    2.022487] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
vindsl@Zuul:~$ 
```

Learn something new every day.

Just saying...

A couple of days ago, the amd-microcode was replaced by linux-firmware.

---

### Post by VinDSL on 2013-02-03
> **cariboo907 said:**
> A couple of days ago, the amd-microcode was replaced by linux-firmware.
Is the "coast clear", so to speak?

I'd really like to upgrade to an 8-core AMD mobo... ;)

---

### Post by zika on 2013-02-04
> **VinDSL said:**
> Interesting!

I never realized that AMD & Intel microcode are both available.

I just installed Intel microcode via Synaptic and it seems to be working fine...

```
vindsl@Zuul:~$ cat /proc/cpuinfo | grep 'model name' | cut -c 13-60
 Intel(R) Pentium(R) 4 CPU 3.40GHz
 Intel(R) Pentium(R) 4 CPU 3.40GHz

vindsl@Zuul:~$ dmesg | grep microcode
[    2.020696] microcode: CPU0 sig=0xf25, pf=0x4, revision=0x1b
[    2.021259] microcode: CPU0 updated to revision 0x2b, date = 2004-08-11
[    2.021278] microcode: CPU1 sig=0xf25, pf=0x4, revision=0x1b
[    2.021578] microcode: CPU1 updated to revision 0x2b, date = 2004-08-11
[    2.022487] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba 
```Learn something new every day.

Just saying...
[http://ubuntuforums.org/showthread.php?t=1945481](http://ubuntuforums.org/showthread.php?t=1945481)

> **cariboo907 said:**
> A couple of days ago, the amd-microcode was replaced by linux-firmware.
[http://ubuntuforums.org/showthread.php?t=2110366](http://ubuntuforums.org/showthread.php?t=2110366)

---

### Post by killian_ro on 2013-02-04
Please learn your plurals! Its "cpus" in the thread title.

---

### Post by zika on 2013-02-04
> **killian_ro said:**
> Please learn your plurals! **Its** "cpus" in the thread title.No need to shout...
Isn't &#8222;it's&#8220; more proper than &#8222;its&#8220; in Your sentence...?

---

### Post by cariboo on 2013-02-04
> **killian_ro said:**
> Please learn your plurals! Its "cpus" in the thread title.

Thank you for making your first post in 6 years one that criticizes my spelling. :-D

---

### Post by kansasnoob on 2013-02-04
> **cariboo907 said:**
> Thank you for making your first post in 6 years one that criticizes my spelling. :-D

Ain't life grand :lolflag:

---

### Post by VinDSL on 2013-02-04
> **cariboo907 said:**
> Thank you for making your first post in 6 years one that criticizes my spelling. :-D
LoL!  Nice skewer...  :cool:

---

### Post by pqwoerituytrueiwoq on 2013-02-05
> **VinDSL said:**
> I'd really like to upgrade to an 8-core AMD mobo... ;)
what would you do with 8 cores? are you media editing?

---

### Post by VinDSL on 2013-02-05
> **pqwoerituytrueiwoq said:**
> what would you do with 8 cores? are you media editing?
Occasionally...

[INDENT][http://www.youtube.com/watch?v=j5XAEl9dd_s](http://www.youtube.com/watch?v=j5XAEl9dd_s)[/INDENT]

---

### Post by pqwoerituytrueiwoq on 2013-02-05
> **VinDSL said:**
> Occasionally...
[INDENT][http://www.youtube.com/watch?v=j5XAEl9dd_s](http://www.youtube.com/watch?v=j5XAEl9dd_s)[/INDENT]
how wil yu fit 8 cores in your conky script
btw have you checked your launchpad email?

---

### Post by ronacc on 2013-02-11
just a note , it turns out that something Ubuntu was doing ( or not doing) was what was screwing those of us with AMD 64 systems . I just updated my Sabayon 10 install and that included the 3.7.0 kernel , it booted and runs fine . If a small underfunded distro can get it right what excuse does Ubuntu have .

---

### Post by pqwoerituytrueiwoq on 2013-02-12
> **ronacc said:**
> just a note , it turns out that something Ubuntu was doing ( or not doing) was what was screwing those of us with AMD 64 systems . I just updated my Sabayon 10 install and that included the 3.7.0 kernel , it booted and runs fine . If a small underfunded distro can get it right what excuse does Ubuntu have .
was that rhetorical?
this is testing, in testing stuff breaks
it is bigger and has more stuff to deal with
we are on kernel 3.8 rc6/rc7 now

---

### Post by jerrylamos on 2013-02-12
> **pqwoerituytrueiwoq said:**
> was that rhetorical?
this is testing, in testing stuff breaks
it is bigger and has more stuff to deal with
we are on kernel 3.8 rc6/rc7 now
Stuff breaks, some stuff gets fixed, some doesn't.  We testers have no way of knowing what development intends to work on and fix and what they are not interested in.  

One of the areas developers are not at all interested in is WPA encrypted network connecting.  On amd64 Raring automatically "disconnects" on boot.  And just sits there.  Syslog says NM recognizes "secrets" are required, which it has, but refuses to use.  Precise connects just fine.  So I have to manually connect using the "secrets" that NM already has stored.  No action on my lauhchpad bugs.

Ubuntu's primary interest is Unity eye candy directed at smartphones. I would hope for a split, Ubuntu for smartphones much stripped down on function and faster (comparatively Android goes like blazes on my tablets) and full function on the far more capable pc's.

This is linux.  We have choices.  I do look for Raring bugs (whether development is interested or not) and also run 12.04.x to rescue the Raring, and also a amd64 Mint which is directed at pc's not smartphones so it is easier to set up and run for what I do.  Your milage may vary.

---

### Post by ronacc on 2013-02-12
> **pqwoerituytrueiwoq said:**
> was that rhetorical?
this is testing, in testing stuff breaks
it is bigger and has more stuff to deal with
we are on kernel 3.8 rc6/rc7 now

it was more informational . Yes this is testing , I could not test for almost half of the cycle due to the 3.7 kernels not booting on my ( and many others ) system . the problem was ignored there were similar issues with quantal also , being used as a second class participant does not give me a warm fuzzy feeling .

---

### Post by ronacc on 2013-02-12
> **jerrylamos said:**
> 

Ubuntu's primary interest is Unity eye candy directed at smartphones. I would hope for a split, Ubuntu for smartphones much stripped down on function and faster (comparatively Android goes like blazes on my tablets) and full function on the far more capable pc's.


I saw an article ,I couldn't find it again to link it , saying that Ubuntu was hoping for an ubuntu phone this year . While I might buy one , being a collector of lost causes , Ubuntu will be going up against 2 very fierce competitors that own the smart phone field of battle ( android and Ios ) + 2 others that are determined capture a slice their monopoly ( microsoft and blackberry ) + a host of bit players . Mark has chosen a minefield to dance in .

---

### Post by cariboo on 2013-02-12
This thread is starting to stray off topic. For more info on the Ubuntu smartphone, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=2100707](http://ubuntuforums.org/showthread.php?t=2100707)

Since we are now on kernel 3.8.0-6, this thread has outlived it's usefulness. Thread closed.

---

