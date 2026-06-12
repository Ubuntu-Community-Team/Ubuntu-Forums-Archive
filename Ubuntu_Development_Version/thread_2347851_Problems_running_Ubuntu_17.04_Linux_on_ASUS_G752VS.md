---
title: "Problems running Ubuntu 17.04 Linux on ASUS G752VS Laptop"
date: 2016-12-29
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2016-12-29
*Non-Optimus laptop (without integrated graphic):*
*ASUS G752VS-GC063D-CST256*
*17.3" FHD LED 1920x1080, Intel Core i7-6700HQ (3.50Ghz), 16GB DDR4, 256GB M.2 NVMe SSD + 1TB HDD 7200rpm, DVDRW-DL, Nvidia GTX1070 8GB GDDR5, Wifi 802.11ac+Bluetooth 4.1 (Dual band) 2*2, Gb LAN, HDMI, mDP, Intel WiDi, USB3.0 x4, USB3.1-Type C(Gen2) with Thunderbolt, HD webcam, Illuminated KB, no OS.*

Hi all,
I'm opening this thread now, during the development period, hoping that before its official release in April 2017, Ubuntu 17.04 *(Zesty Zapus)* Linux can become much more compatible with ASUS G752VS laptop.
While my notebook was empty without any OS, I tried Ubuntu 16.04.1, 16.10 and 17.04.
I noticed multiple problems *(AC adapter/battery, Fn keys and touchpad doesn't work,...)*, so I installed Windows 10 on 50% *(125GB)* of my 256GB M.2 NVMe SSD drive and everything works perfectly and very fast.
My intention is to install these days Ubuntu 17.04 alongside Windows 10, and hopefully *(with your help of course)* to remove Windows completely in April.

**PROBLEM NR.1)**
_Installation_

Touchpad doesn't work, but for now I will skip this issue since I can easily connect USB mouse to my laptop. Since we are talking here about installation, I would say that this is the biggest problem of both Ubuntu 16.10 and 17.04: missing mouse pointer! This problem is 100% related to a video driver because if one is capable to install later Nvidia drivers - problem is solved. The fact is that this problem doesn't exist in ASUS G752VS while trying to instal Ubuntu 16.04.1!
Consequently, the question is how can I inform Ubuntu developers about PROBLEM NR.1?

Thanks for any help.

---

### Post by dino99 on 2016-12-30
open a bug against linux

---

### Post by aljosa2 on 2017-01-01
Thank you, here it is:
[https://bugs.launchpad.net/ubuntu/+bug/1653456](https://bugs.launchpad.net/ubuntu/+bug/1653456)

---

### Post by dino99 on 2017-01-01
Some workarounds for testing:
[https://forums.opensuse.org/showthread.php/521114-Touchpad-not-responding-Asus-Rog-G752VS](https://forums.opensuse.org/showthread.php/521114-Touchpad-not-responding-Asus-Rog-G752VS)
[https://rog.asus.com/forum/showthread.php?88277-G752VS-Lowered-CPU-voltage-in-BIOS-no-more-throttling](https://rog.asus.com/forum/showthread.php?88277-G752VS-Lowered-CPU-voltage-in-BIOS-no-more-throttling)

If you get some positive results after testing/tweaking, then comment your report.

Note: as that hardware is recent, you should also test it with the latest kernel (4.9) and the latest graphic driver. So use ubuntu 17.04 with that rog monster, its very stable..

---

### Post by aljosa2 on 2017-01-23
While I'm waiting for compatibility between kernels 4.10-rc and Nvidia driver in order to see if something changes with the "Touchpad and Fn keys" problem, the situation with battery and charging isn't clear to me even with Windows 10:

[I][https://rog.asus.com/forum/showthread.php?73891-Plugged-in-Not-Charging](https://rog.asus.com/forum/showthread.php?73891-Plugged-in-Not-Charging)
This is 100% normal, standard behaviour for all laptops that I have seen in the past 5 years. What you described in your post sounded more like your battery not charging at all, just discharging. What's actually happening is your computer using a standard method of battery preservation and Windows knows this, which is why it's telling you that it's plugged in but not charging - simply because it does not need to. You should actually worry about your battery being at 100%, not about it being at less than that.
The idea is that once the battery hits around 95-98% charge, charging stops in order to prevent battery life loss as these batteries should not be charged to full. This is controlled by the built-in power/energy controller. Once it hits that point the battery begins being trickle charged, just enough to keep it at a steady level. Otherwise you would see the battery drop to 97, 96, 95 etc as each day passes by. Your battery continues to be charged extremely slowly to keep it at 98% until you actually use the battery.
In order to make sure your battery will last as long as possible, fully discharge it once a month. It'll last years.
You were almost going to try "fixing" your 100% functional battery, heh.
At least you spared yourself the laugh the tech people would have given you at the computer store.
You have nothing to worry about.[/I]

On my laptop with Windows 10 charging sometimes stops at 95% or 97% with the notification "Plugged in, not charging", and sometimes it goes to full 100%.
With Ubuntu Zesty I always have "Battery (estimating...)":

---

### Post by aljosa2 on 2017-02-16
**Just installed from proposed kernel 4.10.0-8.10 and NVIDIA 375.39.**
**Unfortunately both touchpad and Fn keys still doesn't work.**

These are some problematic DMESG lines (does anyone know what it is and how to fix it?):

```
[ 15.103844] fwupd[2761]: segfault at 555900000008 ip 00007f2e80964e78 sp 00007fff7e425360 error 4 in libc-2.24.so[7f2e808e4000+1bd000]

[ 0.320106] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored


[ 0.385567] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[ 0.385634] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM


[ 3.337489] tpm_crb MSFT0101:00: can't request region for resource [mem 0xfed40080-0xfed40fff]
[ 3.337497] tpm_crb: probe of MSFT0101:00 failed with error -16


[ 3.414234] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (0bda:57fa)
[ 3.416168] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[ 3.416731] uvcvideo 1-4:1.0: Entity type for entity Realtek Extended Controls Unit was not initialized!
[ 3.416733] uvcvideo 1-4:1.0: Entity type for entity Extension 4 was not initialized!
[ 3.416733] uvcvideo 1-4:1.0: Entity type for entity Processing 2 was not initialized!
[ 3.416734] uvcvideo 1-4:1.0: Entity type for entity Camera 1 was not initialized!


[ 3.435818] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[ 3.441448] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[ 3.441462] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[ 3.442210] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[ 3.445714] iwlwifi 0000:02:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[ 3.460952] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[ 3.463638] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 3.464644] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled


[ 2.041622] nvidia: loading out-of-tree module taints kernel.
[ 2.041625] nvidia: module license 'NVIDIA' taints kernel.
[ 2.041626] Disabling lock debugging due to kernel taint
[ 2.045391] nvidia: module verification failed: signature and/or required key missing - tainting kernel


[ 5.555023] nvidia-modeset: Allocated GPU:0 (GPU-36946fb5-8d25-dcea-2d69-172acaad0a58) @ PCI:0000:01:00.0
[ 5.557137] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.557198] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.557351] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.557389] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)


[ 3.604560] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[ 3.604572] thermal thermal_zone8: failed to read out thermal zone (-5)


[ 3.836867] input: ASASTeK COMPUTER INC. ROG MacroKey as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.1/0003:0B05:1837.0005/input/input12
[ 3.839504] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839584] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839637] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839688] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839739] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839794] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839846] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839909] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.839947] intel_rapl: Found RAPL domain package
[ 3.839948] intel_rapl: Found RAPL domain core
[ 3.839949] intel_rapl: Found RAPL domain dram
[ 3.839962] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840000] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840041] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840105] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840162] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840218] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840261] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840313] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 3.840354] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)


[ 4.500659] cgroup: new mount options do not match the existing superblock, will be ignored
[ 4.545833] cgroup: new mount options do not match the existing superblock, will be ignored


[ 4.584826] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.


[ 4.998255] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 4.998277] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 4.998289] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 4.998299] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 4.998314] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 4.998324] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 4.998334] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315260] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315345] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315404] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315454] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315504] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315555] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315643] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315701] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315777] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315828] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315876] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315914] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315951] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.315989] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.316026] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.316063] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.316114] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
[ 5.347949] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160930/nsarguments-95)
```

---

### Post by dino99 on 2017-02-16
nvidia-378.13 (graphics-drivers ppa) is better
report kernel issues listed above; (acpi/uvcvideo/wifi)

fwupd also fails on my system (which i dont need, so removed here)

---

### Post by Sophont on 2017-02-18
> **aljosa2 said:**
> **Just installed from proposed kernel 4.10.0-8.10 and NVIDIA 375.39.**
**Unfortunately both touchpad and Fn keys still doesn't work.**


Hi aljosa2,

I'm in a very similar situation having just bought a G752VM (Nvidia 1060).

You mentioned earlier that you run a live system. Does the above message mean that you have installed Ubuntu (17.04?) by now?

I'm asking because I ripped out the original m.2 ssd AND HDD and installed a new NVME SSD (ADATA 256 GB) and a HDD.
I first installed Ubuntu 16.04 on the HDD and it runs mostly fine - except the issues with Fn Keys and Touchpad not working - these are no big deal to me atm.
But when I tried to boot from the new SSD the BIOS doesn't offer it as a boot option. I disabled SecureBoot, run legacy mode (CSM) instead of EFI and and switched SATA mode from RAID to AHCI (as suggested by other owners of various G752 models) - no matter what I change about these and a couple of other settings - the NVME SSD never shows as a boot option.

But when I boot from the HDD Ubuntu has no problems mounting the SSD drive - so it's not a problem for the Kernel - I just can't get there from a cold boot.

I'm on BIOS Version 302 - the newest available for G752VM.

So do you boot from the HDD or the SSD? And if SSD is it a NVME (the original one)? And what BIOS settings have you selected?

Thanks in advance

---

### Post by Sophont on 2017-02-18
> **dino99 said:**
> nvidia-378.13 (graphics-drivers ppa) is better
report kernel issues listed above; (acpi/uvcvideo/wifi)


What do you mean by "is better"?
In general because newer = better - or specifically for G752?
Could you give an example in what way is is better?

---

### Post by dino99 on 2017-02-18
[https://devtalk.nvidia.com/default/topic/994029/-nvidia-378-13-release-a-new-stable-branch-/?offset=8](https://devtalk.nvidia.com/default/topic/994029/-nvidia-378-13-release-a-new-stable-branch-/?offset=8)

---

### Post by aljosa2 on 2017-02-19
Hello Sophont,
I'm writing you from other computer because I'm out of home untill tomorrow.

As a first thing, can you please join the list of people affected by problems:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456)

Regarding our current Elan touchpad problem, I already wrote to the man whose address gave me Kernel developer who in the past solved Elan touchpad issues of my two other Asus notebooks - but for some unknwon reason my email was rejected. Tomorrow I will give you contact details so please ask him to help us.

Unfortunately, I can't install nvidia-378.13 because of compatibility problems with kernel 4.10.
[https://ubuntuforums.org/showthread.php?t=2347666&page=4&p=13608082#post13608082](https://ubuntuforums.org/showthread.php?t=2347666&page=4&p=13608082#post13608082)
Fortunately everything ok with nvidia-375.39.

After experimenting in the beginning with Ubuntu 16.04.1, 16.10 and 17.04, approximately one month ago I installed Windows 10 and Ubuntu 17.04 (dual booting on 256GB M.2 NVMe SSD).
I bought my ASUS G752VS laptop without any OS preinstalled, and later I upgraded BIOS to latest 306 version (I downloaded BIOS for Windows 10 64bit, but I think that in the future I will download BIOS for other OS'es).

All of my hardware is original. I formated both drives choosing GPT partition table. These are my BIOS settings:
- Boot to UEFI Mode (Legacy Boot Mode disabled);
- SecureBoot disabled (there's no fast-startup / fast-boot option);
- switched SATA mode from RAID to AHCI;
- Bluetooth and SD Card Reader disabled.

PS.
My opinion is that there is some kind of problem with Ubuntu installer. While experimenting with installing (trying various options between automatic and manual installing) Ubuntu 16.04.1, 16.10 and 17.04 contemporaneously on ASUS G752VS and Lenovo Y700-17ISK notebooks, I remember that few times I too didn't find any Ubuntu ssd as a boot option. So try to copy all my settings (including GPT partition table and UEFI Mode) and then firstly try to install (few times) automatically without changing deafult options.

---

### Post by aljosa2 on 2017-02-19
Few days ago I received GRUB update. After that I got black screen, laptop didn't want to boot (no GRUB - no Ubuntu - no Windows - no anything). Solved by firstly resetting default BIOS settings and then customizing them. It would be a good thing that you also first delete all your partitions and then reset default BIOS settings and after that customize them before starting experimenting with Zesty installation :)

---

### Post by Sophont on 2017-02-19
> **aljosa2 said:**
> Hello Sophont,

As a first thing, can you please join the list of people affected by problems:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456)


Too late - did that a week ago (I show there as Olaf(tholap) ). ;-)

> **aljosa2 said:**
> Unfortunately, I can't install nvidia-378.13 because of compatibility problems with kernel 4.10.
[https://ubuntuforums.org/showthread.php?t=2347666&page=4&p=13608082#post13608082](https://ubuntuforums.org/showthread.php?t=2347666&page=4&p=13608082#post13608082)
Fortunately everything ok with nvidia-375.39.

I installed 378 yesterday - it does work with the 4.4 Kernel of 16.04.
And it fixed a graphics glitch after screen dimming (dimming after x minutes power setting).

> **aljosa2 said:**
> Unfortunately, I can't install nvidia-378.13 because of compatibility problems with kernel 4.10.
After experimenting in the beginning with Ubuntu 16.04.1, 16.10 and 17.04, approximately one month ago I installed Windows 10 and Ubuntu 17.04 (dual booting on 256GB M.2 NVMe SSD).
I bought my ASUS G752VS laptop without any OS preinstalled, and later I upgraded BIOS to latest 306 version (I downloaded BIOS for Windows 10 64bit, but I think that in the future I will download BIOS for other OS'es).

All of my hardware is original. I formated both drives choosing GPT partition table. These are my BIOS settings:
- Boot to UEFI Mode (Legacy Boot Mode disabled);
- SecureBoot disabled (there's no fast-startup / fast-boot option);
- switched SATA mode from RAID to AHCI;
- Bluetooth and SD Card Reader disabled.


Thanks for providing your settings - that is very helpful.
306 isn't available for the 752VM yet - the 302 it came with is still the newest available on Asus site. So it might be that I just have to wait for 306 to be published (for my *VM model variant).
But this is the 2nd time I read about boot from NVME SSD working on a G752 variant with EFI instead of legacy BIOS.

So I'll now try to add a EFI partition and see whether that makes a difference. Which is a little bit ironic because I had to switch to CSM to be able to boot from HDD (I had a HDD lying around while I had to wait for the SSD to arrive).

> **aljosa2 said:**
> 
PS.
My opinion is that there is some kind of problem with Ubuntu installer. While experimenting with installing (trying various options between automatic and manual installing) Ubuntu 16.04.1, 16.10 and 17.04 contemporaneously on ASUS G752VS and Lenovo Y700-17ISK notebooks, I remember that few times I too didn't find any Ubuntu ssd as a boot option. So try to copy all my settings (including GPT partition table and UEFI Mode) and then firstly try to install (few times) automatically without changing deafult options.

Interesting.
But I'm still at the stage where the Ubuntu installer sn't even relevant as the BIOS itself doesn't list the SSD at all. On the contrary - after I boot from HDD Ubuntu has no problem with the SSD. I copied my previous boot partition over and it shows and mounts fine in file manager, etc.

Anyway - it probably will all be working perfectly within a few months.
I bought the Asus G75 almost 5 years ago - and it had very similar problems at first - but has been running perfectly for over 4 years until the Monitor failed a few weeks ago.

---

### Post by Sophont on 2017-02-20
OK,

SecureBoot off, CSM off, resetting partition table to gpt and installing new EFI partition allowed me to boot after manually creating a boot path to the EFI partition on the NVME SSD.
Happy with that - thanks for the pointers.

Now I just need to get my old bcache backing device HDD (from the G75) to run with the new cache device I created on the NVME SSD and the migration is complete.

---

### Post by Sophont on 2017-02-20
OK,

SecureBoot off, CSM off, resetting partition table to gpt and installing new EFI partition allowed me to boot after manually creating a boot path to the EFI partition on the NVME SSD.
Happy with that - thanks for the pointers.

Now I just need to get my old bcache backing device HDD (from the G75) to run with the new cache device I created on the NVME SSD and the migration is complete.

---

### Post by aljosa2 on 2017-02-20
Good to hear that :)
I think that in the next few days you will receive Zesty 4.10 kernel update, so be careful with the choice of NVIDIA driver (375.39 ok - 378.13 for now not ok).

By the way, I sent you via PM contact details of the developers who can solve our touchpad and Fn keys problems. Please try to ask them to help us - I don't have a clue why my email was rejected by recipient's mail server.

---

### Post by openroad2 on 2017-03-21
> **aljosa2 said:**
> Good to hear that :)
I think that in the next few days you will receive Zesty 4.10 kernel update, so be careful with the choice of NVIDIA driver (375.39 ok - 378.13 for now not ok).

By the way, I sent you via PM contact details of the developers who can solve our touchpad and Fn keys problems. Please try to ask them to help us - I don't have a clue why my email was rejected by recipient's mail server.

Do you think ubuntu 17.04 has any of the issue solved? Such as keyboard backlight, trackpad, anything?
I haven't tried it yet but I don't mind to get a good glance if there's a chance it has some problems solved.
Thank you.

---

### Post by aljosa2 on 2017-03-22
Hi openroad2,
problem(s) has still not been resolved.
You can follow the progress here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456)
I'm still not sure but it seems that we are moving the discussion here:
[https://bugzilla.kernel.org/show_bug.cgi?id=112531](https://bugzilla.kernel.org/show_bug.cgi?id=112531)

---

### Post by aljosa2 on 2017-03-24
My mentioned problems with Asus G752VS are still unsolved.

Today I found an interesting post at Gentoo Forums: ASUS ROG G752 - Touchpad not recognised:
*"With the new Fedora 4.3.3 kernel, I have full use of the touchpad. The reason is actually something I missed/didn't know about the hardware under the hood. In order to get the touchpad working, the i2c_designware bus support must be compiled as a kernel module. I didn't have that in previous builds and thus, I was unable to use the touchpad. _As of tonight, I am using the touchpad, all function keys, and full hardware support on this machine running on Linux_!"*
*[https://forums.gentoo.org/viewtopic-p-7879282.html?sid=7c46b29b613881c3d1fb74091f7de9b6](https://forums.gentoo.org/viewtopic-p-7879282.html?sid=7c46b29b613881c3d1fb74091f7de9b6)*

Can someone please tell me if the i2c_designware bus support is enabled in Zesty kernel?

---

### Post by openroad2 on 2017-03-25
i think their solution worked but the touchpad was different, and so was the keyboard. but don't take my word, I don't understand any of this.

---

### Post by aljosa2 on 2017-03-25
> **aljosa2 said:**
> My mentioned problems with Asus G752VS are still unsolved.

Today I found an interesting post at Gentoo Forums: ASUS ROG G752 - Touchpad not recognised:
"With the new Fedora 4.3.3 kernel, I have full use of the touchpad. The reason is actually something I missed/didn't know about the hardware under the hood. In order to get the touchpad working, the i2c_designware bus support must be compiled as a kernel module. I didn't have that in previous builds and thus, I was unable to use the touchpad. As of tonight, I am using the touchpad, all function keys, and full hardware support on this machine running on Linux!"
[https://forums.gentoo.org/viewtopic-p-7879282.html?sid=7c46b29b613881c3d1fb74091f7de9b6](https://forums.gentoo.org/viewtopic-p-7879282.html?sid=7c46b29b613881c3d1fb74091f7de9b6)

Can someone please tell me if the i2c_designware bus support is enabled in Zesty kernel?
> **openroad2 said:**
> i think their solution worked but the touchpad was different, and so was the keyboard. but don't take my word, I don't understand any of this.

Linux: Find out what kernel drivers (modules) are loaded:

```
~$ lsmod

Module                  Size  Used by

ccm                    20480  1
bnep                   20480  2
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  1
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
bridge                139264  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
hid_multitouch         20480  0
binfmt_misc            20480  1
nls_iso8859_1          16384  1
[B]i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform[/B]
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
arc4                   16384  2
coretemp               16384  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm_intel             200704  0
snd_hda_intel          36864  3
kvm                   593920  1 kvm_intel
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
crct10dif_pclmul       16384  0
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           167936  2
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
iwlmvm                368640  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
glue_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_seq,snd_pcm
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
nvidia_uvm            647168  0
mac80211              782336  1 iwlmvm
intel_rapl_perf        16384  0
serio_raw              16384  0
input_leds             16384  0
snd                    77824  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
joydev                 20480  0
uvcvideo               90112  0
hid_generic            16384  0
iwlwifi               229376  1 iwlmvm
soundcore              16384  1 snd
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
idma64                 20480  0
virt_dma               16384  1 idma64
mei_me                 40960  0
processor_thermal_device    16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_lpss_pci         16384  0
shpchp                 36864  0
mei                   102400  1 mei_me
intel_pch_thermal      16384  0
wmi                    16384  1 asus_wmi
int3403_thermal        16384  0
hci_uart               98304  0
btbcm                  16384  1 hci_uart
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
bluetooth             557056  11 hci_uart,btintel,btqca,bnep,btbcm
acpi_pad              180224  0
int3406_thermal        16384  0
int3402_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
asus_wireless          16384  0
tpm_crb                16384  0
mac_hid                16384  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  23
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  10
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 28672  3 nf_nat_ftp,nf_nat_masquerade_ipv4,nf_nat_ipv4
libcrc32c              16384  1 nf_nat
parport_pc             32768  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
ppdev                  20480  0
nf_conntrack          131072  11 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,ipt_MASQUERADE,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
lp                     20480  0
iptable_filter         16384  1
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               36864  16 xt_LOG,ipt_REJECT,iptable_mangle,ip_tables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_limit,ip6t_REJECT,xt_CHECKSUM,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
autofs4                40960  2
hid_holtek_mouse       16384  0
usbhid                 53248  0
nvidia_drm             49152  1
nvidia_modeset        790528  5 nvidia_drm
nvidia              12136448  83 nvidia_modeset,nvidia_uvm
drm_kms_helper        151552  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
nvme                   28672  2
drm                   352256  4 nvidia_drm,drm_kms_helper
r8169                  81920  0
nvme_core              53248  4 nvme
ahci                   36864  0
mii                    16384  1 r8169
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   114688  5 i2c_hid,hid_generic,hid_holtek_mouse,usbhid,hid_multitouch
pinctrl_sunrisepoint    28672  0
video                  40960  2 asus_wmi,int3406_thermal
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   73728  0
```

MOD_UNLOAD is set when the module is unloaded from the kernel

```
~$ modinfo i2c_designware_core

filename:       /lib/modules/4.10.0-13-generic/kernel/drivers/i2c/busses/i2c-designware-core.ko
license:        GPL
description:    Synopsys DesignWare I2C bus adapter core
srcversion:     44D6249BD17F761F720697B
depends:        
intree:         Y
vermagic:       4.10.0-13-generic SMP mod_unload
```

MOD_UNLOAD is set when the module is unloaded from the kernel

```
~$ modinfo i2c_designware_platform

filename:       /lib/modules/4.10.0-13-generic/kernel/drivers/i2c/busses/i2c-designware-platform.ko
license:        GPL
description:    Synopsys DesignWare I2C bus adapter
author:         Baruch Siach <baruch@tkos.co.il>
alias:          platform:i2c_designware
srcversion:     5D77A70993CEE6F6CA6C16F
alias:          acpi*:APMC0D0F:*
alias:          acpi*:AMDI0510:*
alias:          acpi*:AMDI0010:*
alias:          acpi*:AMD0010:*
alias:          acpi*:808622C1:*
alias:          acpi*:80860F41:*
alias:          acpi*:INT3433:*
alias:          acpi*:INT3432:*
alias:          acpi*:INT33C3:*
alias:          acpi*:INT33C2:*
depends:        i2c-designware-core
intree:         Y
vermagic:       4.10.0-13-generic SMP mod_unload
```

---

### Post by openroad2 on 2017-03-25
&#296;'d done the same, here it is. Shouldn't elan_i2c have been loaded too? Now, I see ASUS was a terrible choice for Linux. I should've tried a different brand because of support, but now I can't return the product.
```
lsmod
Module                  Size  Used by
nls_utf8               16384  0
udf                    90112  0
crc_itu_t              16384  1 udf
uas                    24576  0
usb_storage            73728  1 uas
ccm                    20480  3
bnep                   20480  2
nls_iso8859_1          16384  1
hid_multitouch         20480  0
arc4                   16384  2
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
iwlmvm                360448  0
ghash_clmulni_intel    16384  0
mac80211              761856  1 iwlmvm
aesni_intel           167936  6
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
intel_cstate           16384  0
snd_hda_intel          36864  3
snd_hda_codec         135168  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
intel_rapl_perf        16384  0
snd                    86016  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
iwlwifi               229376  1 iwlmvm
uvcvideo               90112  0
serio_raw              16384  0
soundcore              16384  1 snd
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
idma64                 20480  0
videobuf2_v4l2         24576  1 uvcvideo
virt_dma               16384  1 idma64
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
joydev                 20480  0
cfg80211              581632  3 iwlmvm,iwlwifi,mac80211
media                  40960  2 uvcvideo,videodev
input_leds             16384  0
mei_me                 40960  0
mei                   102400  1 mei_me
btusb                  45056  0
intel_lpss_pci         16384  0
btrtl                  16384  1 btusb
processor_thermal_device    16384  0
shpchp                 36864  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
wmi                    16384  1 asus_wmi
int3403_thermal        16384  0
nvidia_uvm            647168  0
hci_uart               98304  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
bluetooth             557056  13 btrtl,hci_uart,btintel,btqca,bnep,btbcm,btusb
int3402_thermal        16384  0
ip6t_REJECT            16384  1
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
nf_reject_ipv6         16384  1 ip6t_REJECT
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
tpm_crb                16384  0
int3400_thermal        16384  0
int3406_thermal        16384  0
asus_wireless          16384  0
mac_hid                16384  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad               24576  0
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
xt_comment             16384  4
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  22
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          110592  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
coretemp               16384  0
parport_pc             32768  0
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
ppdev                  20480  0
x_tables               36864  14 xt_comment,xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
nvidia_drm             49152  1
nvidia_modeset        790528  4 nvidia_drm
nvidia              12144640  60 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
nvme                   28672  3
r8169                  81920  0
ahci                   36864  0
nvme_core              53248  5 nvme
drm                   368640  4 nvidia_drm,drm_kms_helper
mii                    16384  1 r8169[INDENT]libahci                32768  1 ahci
[/INDENT]
 i2c_hid                20480  0
hid                   122880  4 i2c_hid,hid_generic,usbhid,hid_multitouch
pinctrl_sunrisepoint    28672  0
video                  40960  2 asus_wmi,int3406_thermal
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0

```

```
modinfo i2c-designware-platform 
filename:       /lib/modules/4.8.0-42-generic/kernel/drivers/i2c/busses/i2c-designware-platform.ko
license:        GPL
description:    Synopsys DesignWare I2C bus adapter
author:         Baruch Siach <baruch@tkos.co.il>
alias:          platform:i2c_designware
srcversion:     77AB41FC82FB335B20751AF
alias:          acpi*:APMC0D0F:*
alias:          acpi*:AMDI0510:*
alias:          acpi*:AMDI0010:*
alias:          acpi*:AMD0010:*
alias:          acpi*:808622C1:*
alias:          acpi*:80860F41:*
alias:          acpi*:INT3433:*
alias:          acpi*:INT3432:*
alias:          acpi*:INT33C3:*
alias:          acpi*:INT33C2:*
depends:        i2c-designware-core
intree:         Y
vermagic:       4.8.0-42-generic SMP mod_unload modversions 
```


```
modinfo i2c-designware-platform 
filename:       /lib/modules/4.8.0-42-generic/kernel/drivers/i2c/busses/i2c-designware-platform.ko
license:        GPL
description:    Synopsys DesignWare I2C bus adapter
author:         Baruch Siach <baruch@tkos.co.il>
alias:          platform:i2c_designware
srcversion:     77AB41FC82FB335B20751AF
alias:          acpi*:APMC0D0F:*
alias:          acpi*:AMDI0510:*
alias:          acpi*:AMDI0010:*
alias:          acpi*:AMD0010:*
alias:          acpi*:808622C1:*
alias:          acpi*:80860F41:*
alias:          acpi*:INT3433:*
alias:          acpi*:INT3432:*
alias:          acpi*:INT33C3:*
alias:          acpi*:INT33C2:*
depends:        i2c-designware-core
intree:         Y
vermagic:       4.8.0-42-generic SMP mod_unload modversions 

```

I don't understand what you mean by MOD_UNLOAD, where do I check that?

---

### Post by openroad2 on 2017-03-25
I'm noticing /sys/class/leds/asus is missing for the keyboard backlight, which is referenced by the file /etc/acpi/asus-keyboard-backlight.sh from the asus-wmi module, used to change keyboard brightness.

```

#!/bin/sh

# this directory is a symlink on my machine:
KEYS_DIR=/sys/class/leds/asus\:\:kbd_backlight

test -d $KEYS_DIR || exit 0

MIN=0
MAX=$(cat $KEYS_DIR/max_brightness)
VAL=$(cat $KEYS_DIR/brightness)

if [ "$1" = down ]; then
    VAL=$((VAL-1))
else
    VAL=$((VAL+1))
fi

if [ "$VAL" -lt $MIN ]; then
    VAL=$MIN
elif [ "$VAL" -gt $MAX ]; then
    VAL=$MAX
fi

echo $VAL > $KEYS_DIR/brightness
```

---

### Post by aljosa2 on 2017-03-26
Initially *(few years ago)* I had some big problems with my other two Asus *(optimus)* laptops. After some time, I upgraded their hard drives to SSD. They are very fast now and working lika a charm.

Bear in mind that our Asus G752VS is a brend new model. I'm not sure but I think that our problems are somehow caused by the implementation of new *(very complicated)* power saving technologies: for example, under Windows 10 keyboard backlighting automatically turns off after 20-30 seconds...

That said, here's one hope: "at the last update of xserver-xorg-input-libinput and libinput10 my touchpad (Asus G752VS ELAN1203:00 04F3:3043) is put suddenly to work but after a reboot no longer works...
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=855317](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=855317)

---

### Post by openroad2 on 2017-03-26
Thank you for that information. I saw that bug on Debian but I don't think in Ubuntu we use xserver-xorg-input-libinput, even though we have libinput10.
It's rather complicated for me to discern what may apply in our case, given Hardware Systems it's not at all my area. If it was there might have a workaround we could coin.
Another consideration I shall state, it's that every distribution has a rather different approach to many things and people who use this are split among different distros, so any bug report may not get great spotlight.

---

### Post by dino99 on 2017-03-26
xserver-xorg-input-libinput: 
This package provides the driver for input devices using libinput library.
It can handle keyboards, mice and touchpads, and essentially replaces the
separate -evdev and -synaptics drivers.

note: that package had to be removed on my old desktop using a usb mouse; with latest xserver-xotg 1.19.3 (from canonical-x ppa), compiz goes crazy and the session is unusable.
(that actually block 1.19 to land into ZZ archive)

---

### Post by aljosa2 on 2017-03-26
From that point of view it will be very interesting to try our laptops under Fedora 26 Alpha in the next few days (will be delayed to at least 28 March). By the way, I can't even boot recently released Manjaro 17.0

---

### Post by openroad2 on 2017-03-26
I tried out Fedora 26 and Fedora 25 (gnome) just before yesterday. Both use wayland by default. The feedback I have is, Fedora 25 is unusable because I can't even get my external mouse to work and the keyboard input is completely chaotic, enter t for terminal I get to two t's, delete once, it deletes twice. I tried to bypass this by typing twice of what I want to get 3t's and delete once to have only one t for instance; following this pattern for any input I want to enter.

In the live preview of Fedora 26 I can type in characters but they get shown abominably slow, the external mouse works but it is also very slow. I gather wayland doesn't support NVIDIA out of the box with Nouveau, and the xinput --list doesn't display anything as ASUS because Fedora doesn't use third party drivers or software? My opinion, whatever the reason may be, is that it's rather complicated to work with this cutting-edge versions, even if it's just a collateral of using wayland by default, which from forums feedback doesn't support NVIDIA graphic cards nicely yet.

---

### Post by openroad2 on 2017-03-26
My problem here (I haven't used Linux throughly for a few years) is that I wanted to migrate from macOS to Linux, so I'm still sorting things out and it helped to have the hardware functionality working, though I don't mind to just do work in this pc but it's more complicated having external keyboard, always external mouse, and the shortcuts not being very friendly or device specific.

---

### Post by aljosa2 on 2017-03-28
Here's something interesting:
[I]
Kernel 4.10.7 Stable Review:[/I]
*Input: elan_i2c - add ASUS EeeBook X205TA special touchpad fw*
*drivers/input/mouse/elan_i2c_core.c | 20 +-*
*[https://lkml.org/lkml/2017/3/28/404](https://lkml.org/lkml/2017/3/28/404)*

Hi openroad2,
please click on the link.
Above the new elan_i2c driver for Asus X205TA, there's a developer email address. It would be very useful if you can inform him *(as soon as possible)* via email about our problems.

---

### Post by openroad2 on 2017-03-28
Ok, I sent and email to the one who made that specific commit. Hope it's not detected as SPAM and that he can work it out. Furthermore, I also pointed the other problems but I don't know if they're inherently related with them.

Aljosa2, have you got any news? Multiple reports among Linux distros with the same problem, OpenSuse, Debian, Ubuntu, kernel.bugs, most with 6 or 7 months old, nonetheless not a single stood out with a partial fix, besides that Debian bug previously mentioned.

---

### Post by aljosa2 on 2017-03-30
Hi openroad2, 
I'm out of home today... are you able to send a desciption of our problems (including links to bug reports) at this mailing list:

*HID: asus: Add missing Fn key maps*
*The mapping of a few Fn combo keys seems missing since they are vendor specific usage page...*
*[https://lkml.org/lkml/2017/3/30/234](https://lkml.org/lkml/2017/3/30/234)*

---

### Post by aljosa2 on 2017-04-05
ASUS G752VS non-optimus laptop (Nvidia GTX1070)
Ubuntu 17.04
Linux 4.10.0-15-generic
Xorg-Server-1.19.3

Ubuntu 17.04 doesn't save my brightness settings. I can adjust the screen brightness but after restarting the screen brightness of my laptop resets to maximum. How can I ensure that my brightness preference will persist after reboot?
[https://bugs.launchpad.net/hundredpapercuts/+bug/1270579](https://bugs.launchpad.net/hundredpapercuts/+bug/1270579)

---

### Post by zika on 2017-04-05
Put the appropriate echo command in /etc/rc.local or ~/.xprofile. First in mind comes :  /sys/class/blacklight/acpi?video/brightness, it may vary on Your machine...[COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by aljosa2 on 2017-04-08
Hello,
inside "/sys/class/backlight/" I have two folders: "acpi_video0" and "acpi_video1":

> ~$ systemctl status [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e
&#9679; [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e - Load/Save Screen Backlight B
   Loaded: loaded (/lib/systemd/system/systemd-backlight@.service; static; vendo
   Active: active (exited) since Sat 2017-04-08 13:37:31 CEST; 16min ago
     Docs: man:systemd-backlight@.service(8)
 Main PID: 683 (code=exited, status=0/SUCCESS)

~$ systemctl status [EMAIL="systemd-backlight@backlight:acpi_video1.servic"]systemd-backlight@backlight:acpi_video1.servic[/EMAIL]e
&#9679; [EMAIL="systemd-backlight@backlight:acpi_video1.servic"]systemd-backlight@backlight:acpi_video1.servic[/EMAIL]e - Load/Save Screen Backlight B
   Loaded: loaded (/lib/systemd/system/systemd-backlight@.service; static; vendo
   Active: active (exited) since Sat 2017-04-08 13:37:31 CEST; 22min ago
     Docs: man:systemd-backlight@.service(8)
 Main PID: 684 (code=exited, status=0/SUCCESS)

Today I received many Ubuntu updates (kernel included), and I also installed freshly released Nvidia 381.09 driver (via “Graphics Drivers” team - Proprietary GPU Drivers PPA).
Now brightness settings are correctly saved, but I have a new problem: changing brightness level doesn't produce any effect (both with or without Nvidia driver installed).

---

### Post by aljosa2 on 2017-07-11
*
Ubuntu 17.10 daily build (2017-07-10), kernel 4.10.0-19
Booted from Live USB, without USB mouse connected: ELAN touhpad doesn't work at all, but al least touchpad cursor is visible all the time. I've tried to disable/enable the touchpad via system settings, but nothing changes.
After that, I suspended my Asus G752VS laptop via shutdown/suspend menu and then I disconnected the USB mouse. After waking up from suspend, my ELAN touhpad magically became fully functional - everything works fabulously.


*
Fedora Workstation 26, kernel 4.11.8
Booted from Live USB, without USB mouse connected: ELAN touhpad doesn't work at all, but al least touchpad cursor is visible all the time. With the USB mouse connected, I've tried to disable/enable the touchpad via system settings, but nothing changes.
After that, I pressed the power button to suspend my Asus G752VS laptop and then I disconnected the USB mouse. After pressing once again the power button to wake up from suspend, my ELAN touhpad magically became fully functional - everything works fabulously.


*
As reported here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456/comments/76](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456/comments/76)
the trick should work also with Ubuntu 17.04 but that's not my case. My current Ubuntu 17.04 was installed while it was still in development - so I will perform a new clean installation (without Windows) in the next few days.

---

### Post by nv30over on 2018-02-21
> **aljosa2 said:**
> Now brightness settings are correctly saved, but I have a new problem: changing brightness level doesn't produce any effect (both with or without Nvidia driver installed).
Hi! Problem with brightness is still here. Are you found any possible solution?

---

### Post by cariboo on 2018-02-21
Thread Closed. 17.04 has hit EOL.

---

### Post by nv30over on 2018-02-21
Problem exists in 17.10.1

---

