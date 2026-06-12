---
title: "After the last update i get a black screen"
date: 2014-08-28
forum: Ubuntu Development Version
---

### Post by pixelro on 2014-08-28
so, after the last update (15 min ago) i get a black screen :(

---

### Post by QIII on 2014-08-28
Hello!

You have given us precious little to go on, here.

Which release are you using?

What are your hardware specs?

Were you using any proprietary drivers?

We're all here to help, but we need to know what we're working with.

:)

---

### Post by pixelro on 2014-08-28
oh, sorry :> 

Ubuntu 14.10, proprietary Nvidia drivers, amd64.

---

### Post by pixelro on 2014-08-28
so, since i have nothing better to do (i'm on a live cd, +chroot waiting for updates) how can i debug it? i can't get to tty because the keyboard locks

---

### Post by grahammechanical on 2014-08-28
On my system there is a kernel update waiting to come down. Perhaps you have already had the update. Boot into an earlier kernel. Or use recovery mode>Resume. If that gets you to a desktop then use Additional Drivers to change video drivers. Use recovery mode to update/upgrade. There might be a fix in the next update.

Of course a lot depends on where you get the black screen.  Which you do not tell us. So, all I can add is, thank for the information. I will avoid updating for the next day or two. Actually, it does not matter if I get a blackscreen because I have other installs of Ubuntu to boot into.

Regards.

---

### Post by caryb on 2014-08-28
I too am experiencing this on my laptop (nvidia driver) I have removed nvidia* & purged out all nvidia drivers & now it allows me to logon but then dumps me back to a terminal.

---

### Post by zonum on 2014-08-28
I too have the same issue as pixelro.  14.10 and Nvidia too.

ii  nvidia-304                                           304.123-0ubuntu2                                      amd64        NVIDIA legacy binary driver - version 304.123
ii  nvidia-current                                       304.123-0ubuntu2                                      amd64        Transitional package for nvidia-current

unity --version
unity 7.3.1

All was well this morning but not now after latest upgrade about 20 minutes ago.

---

### Post by ScislaC on 2014-08-28
Same issue here, NVIDIA as well.

After dropping to a root shell and trying startx from there, it refuses to start because "no screen found".

---

### Post by pixelro on 2014-08-28
it's not the kernel, the kernel didn't update because it didn't prompt me to restart. Also i've tried older ones with the same result. The system freezes after the login screen (text) i don't see any graphics. keyboard locks and the screen is black :>

---

### Post by ScislaC on 2014-08-28
Okay... in my Xorg.0.log I'm seeing:

```
[   106.444] (II) LoadModule: "nvidia"
[   106.444] (WW) Warning, couldn't open module nvidia
[   106.444] (II) UnloadModule: "nvidia"
[   106.444] (II) Unloading nvidia
[   106.444] (EE) Failed to load module "nvidia" (module does not exist, 0)
```

Finally this:

```
Fatal server error:
[   106.454] (EE) no screens found(EE)
```

---

### Post by pixelro on 2014-08-28
boot.log

* No suitable module for running kernel found
 * Starting VirtualBox kernel modules                                    [fail] 
 * Starting load fallback graphics devices                               [fail]

---

### Post by caryb on 2014-08-28
Strangely even after removing the Nvidia driver it then borks loading nouveau driver even on older kernels

---

### Post by pixelro on 2014-08-28
same here

---

### Post by ScislaC on 2014-08-28
Also worth noting that the shutdown and reboot commands aren't working for me either.

---

### Post by anca-emanuel on 2014-08-29
> **ScislaC said:**
> Also worth noting that the shutdown and reboot commands aren't working for me either.

I also have the same problem after today update, and I have nvidia drivers.

Tested Caps Lock, nothing.
Tested Alt+SysRq+B = reboot works

Partial list of updated packages:
```
2014-08-29 07:23:44 upgrade libupstart1:amd64 1.13.1-0ubuntu3 1.13.1-0ubuntu4
2014-08-29 07:23:46 upgrade lightdm:amd64 1.11.6-0ubuntu1 1.11.7-0ubuntu1
2014-08-29 07:24:08 upgrade ubuntu-drivers-common:amd64 1:0.2.97 1:0.2.98
2014-08-29 07:24:11 upgrade libcgmanager0:i386 0.30-1ubuntu1 0.30-1ubuntu2
2014-08-29 07:24:12 upgrade libcgmanager0:amd64 0.30-1ubuntu1 0.30-1ubuntu2
2014-08-29 07:24:13 upgrade upstart:amd64 1.13.1-0ubuntu3 1.13.1-0ubuntu4
2014-08-29 07:24:14 upgrade upstart-bin:amd64 1.13.1-0ubuntu3 1.13.1-0ubuntu4
2014-08-29 07:24:17 upgrade update-manager-core:all 1:14.10.3 1:14.10.4
2014-08-29 07:24:18 upgrade update-manager:all 1:14.10.3 1:14.10.4
2014-08-29 07:24:20 upgrade cgmanager:amd64 0.30-1ubuntu1 0.30-1ubuntu2
2014-08-29 07:24:55 upgrade linux-headers-generic:amd64 3.16.0.10.11 3.16.0.11.12
2014-08-29 07:25:09 upgrade linux-image-generic:amd64 3.16.0.10.11 3.16.0.11.12
2014-08-29 07:25:10 upgrade linux-libc-dev:amd64 3.16.0-10.15 3.16.0-11.16
2014-08-29 07:23:48 install linux-image-3.16.0-11-generic:amd64 <none> 3.16.0-11.16
2014-08-29 07:24:35 install linux-headers-3.16.0-11:all <none> 3.16.0-11.16
2014-08-29 07:24:52 install linux-headers-3.16.0-11-generic:amd64 <none> 3.16.0-11.16
2014-08-29 07:24:56 install linux-image-extra-3.16.0-11-generic:amd64 <none> 3.16.0-11.16 
```

---

### Post by Wise Ferret on 2014-08-29
Very similar issues here, with nvidia gtx-770. If I remove every nvidia package I do manage to get Nouveau driver runing, but when the proprietary drivers are installed they fail to load and I can get only extremely low resolution.

---

### Post by Elfy on 2014-08-29
I removed nvidia and reverted to nouveau before rebooting after kernel update. Booted fine to the desktop, reinstalling nvidia afterwards and it's not getting loaded so still using nouveau here (xubuntu)

---

### Post by harry332 on 2014-08-29
Surely this is a kernel module issue.
The installed newest linux kernel (3.16.0-11.16) will cause nvidia kernel module build to fail.
Thus X cannot be started.
Also see the bug reports #1362957 and #1362848.
Purging nvidia drivers will remove all kernel mudules, also from the older kernels.

You should try this.
- cold boot your system, as it does not get to Display manager, press ctrl+alt+F1 to get to the tty1 (console).
- log in
- purge the newest kernel (3.16.0-11.16), all the packages including the meta ones. Do not remove older kernels though! The latest working kernel is 3.16.0-10.15
- purge nvidia drivers, for example nvidia-331
- install nvidia drivers back (nvidia-331)
- reboot your system

---

### Post by fooman on 2014-08-29
i know its no help, but just to add...i did a clean install about a month ago,  and promptly installed the latest development kernel (at the time i think it was 3.16-rc6)  after a few days updated to 3.16-rc7.  when 3.17-rc1 was released,  i installed that and when i confirmed it was working properly i went and removed all default kernels,  keeping only the development rc releases installed.  i also have nvidia card with proprietary drivers installed (331.89)

as such,  i do not have these issues with the latest updates.  everything here is working fine with kernel 3.17-rc1....in fact boot up times are faster then ever with systemd:

```
systemd-analyze
Startup finished in 2.990s (kernel) + 6.565s (userspace) = 9.556s
```

---

### Post by christopher9 on 2014-08-29
Just lucky I guess....I'm not experiencing any issues with my setup after updating to 14.10 and using proprietary Nvidia binary driver 331.89:
```

-Version-
Kernel        : Linux 3.16.0-11-generic (x86_64)
Compiled        : #16-Ubuntu SMP Mon Aug 25 20:03:32 UTC 2014
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.9.1 (Ubuntu 4.9.1-9ubuntu1) 
Distribution        : Ubuntu Utopic Unicorn (development branch)
-Current Session-
Computer Name        : RoadAmerica
User Name        : twowings (Chris)
Home Directory        : /home/twowings
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 2 hours, 13 minutes
Load Average        : 0.44, 0.36, 0.37

*****************************
-PCI Devices-
Host bridge        : Intel Corporation Haswell-ULT DRAM Controller (rev 09)
VGA compatible controller        : Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Audio device        : Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
USB controller        : Intel Corporation 8 Series USB xHCI HC (rev 04) (prog-if 30 [XHCI])
Communication controller        : Intel Corporation 8 Series HECI #0 (rev 04)
Audio device        : Intel Corporation 8 Series HD Audio Controller (rev 04)
PCI bridge        : Intel Corporation 8 Series PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 8 Series PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 8 Series PCI Express Root Port 4 (rev e4) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 8 Series PCI Express Root Port 5 (rev e4) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation 8 Series USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
ISA bridge        : Intel Corporation 8 Series LPC Controller (rev 04)
SATA controller        : Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
SMBus        : Intel Corporation 8 Series SMBus Controller (rev 04)
Network controller        : Intel Corporation Wireless 7260 (rev 73)
Ethernet controller        : Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
3D controller        : NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)

*****************************************

-Loaded Modules-
bbswitch        : Toggle the discrete graphics card
arc4        : ARC4 Cipher Algorithm
nvidia
snd_hda_codec_idt        : IDT/Sigmatel HD-audio codec
snd_hda_codec_generic        : Generic HD-audio codec parser
hid_logitech_dj
snd_hda_codec_hdmi        : HDMI HD-audio codec
mxm_wmi        : MXM WMI Driver
intel_rapl        : Driver for Intel RAPL (Running Average Power Limit)
x86_pkg_temp_thermal        : X86 PKG TEMP Thermal Driver
intel_powerclamp        : Package Level C-state Idle Injection for Intel CPUs
coretemp        : Intel Core temperature monitor
kvm_intel
kvm
crct10dif_pclmul        : T10 DIF CRC calculation accelerated with PCLMULQDQ.
crc32_pclmul
ghash_clmulni_intel        : GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI
iwlmvm        : The new Intel(R) wireless AGN driver for Linux
mac80211        : IEEE 802.11 subsystem
aesni_intel        : Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
aes_x86_64        : Rijndael (AES) Cipher Algorithm, asm optimized
lrw        : LRW block cipher mode
gf128mul        : Functions for multiplying elements of GF(2^128)
glue_helper
ablk_helper
cryptd        : Software async crypto daemon
joydev        : Joystick device interfaces
iwlwifi        : Intel(R) Wireless WiFi driver for Linux
serio_raw        : Raw serio driver
snd_soc_rt5640        : ASoC RT5640/RT5639 driver
snd_soc_rl6231        : RL6231 class device shared support
snd_soc_core        : ALSA SoC Core
snd_compress        : ALSA Compressed offload framework
snd_pcm_dmaengine
btusb        : Generic Bluetooth USB driver ver 0.6
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
rfcomm        : Bluetooth RFCOMM ver 1.11
bnep        : Bluetooth BNEP ver 1.3
bluetooth        : Bluetooth Core ver 2.19
6lowpan_iphc
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_hda_intel        : Intel HDA driver
snd_hda_controller        : Common HDA driver funcitons
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_hda_codec        : HDA codec core
snd_seq_device        : ALSA sequencer device management
usbhid        : USB HID core driver
i915        : Intel Graphics
snd_hwdep        : Hardware dependent layer
cfg80211        : wireless configuration support
keucr        : ENE USB Mass Storage driver for Linux
drm_kms_helper        : DRM KMS helper
lpc_ich        : LPC interface for Intel ICH
shpchp        : Standard Hot Plug PCI Controller Driver
snd_pcm        : Midlevel PCM code for ALSA.
mei_me        : Intel(R) Management Engine Interface
mei        : Intel(R) Management Engine Interface
drm        : DRM shared core routines
snd_timer        : ALSA timer interface
i2c_algo_bit        : I2C-Bus bit-banging algorithm
toshiba_bluetooth        : Toshiba Laptop ACPI Bluetooth Enable Driver
sparse_keymap        : Generic support for sparse keymaps
snd        : Advanced Linux Sound Architecture driver for soundcards.
video        : ACPI Video Driver
soundcore        : Core sound module
dw_dmac        : Synopsys DesignWare DMA Controller platform driver
wmi        : ACPI-WMI Mapping Driver
dw_dmac_core        : Synopsys DesignWare DMA Controller core driver
snd_soc_sst_acpi        : Intel SST loader on ACPI systems
8250_dw        : Synopsys DesignWare 8250 serial port driver
i2c_hid        : HID over I2C core driver
hid
i2c_designware_platform        : Synopsys DesignWare I2C bus adapter
i2c_designware_core        : Synopsys DesignWare I2C bus adapter core
spi_pxa2xx_platform        : PXA2xx SSP SPI Controller
mac_hid
parport_pc        : PC-style parallel port driver
ppdev
lp
parport
nls_iso8859_1
uas
usb_storage        : USB Mass Storage driver for Linux
ahci        : AHCI SATA low-level driver
libahci        : Common AHCI SATA low-level routines
psmouse        : PS/2 mouse driver
alx        : Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
mdio        : Generic support for MDIO-compatible transceivers
sdhci_acpi        : Secure Digital Host Controller Interface ACPI driver
sdhci        : Secure Digital Host Controller Interface core driver
```

---

### Post by ventrical on 2014-08-29
All working well here with:

```

*-display
                description: VGA compatible controller
                product: G71GL [Quadro FX 3500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
               
```

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ uname -a
Linux ventrical-Precision-WorkStation-T3400 3.16.0-11-generic #16-Ubuntu SMP Mon Aug 25 20:03:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Elfy on 2014-08-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by pixelro on 2014-08-29
> **ventrical said:**
> All working well here with:

```

*-display
                description: VGA compatible controller
                product: G71GL [Quadro FX 3500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
               
```

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ uname -a
Linux ventrical-Precision-WorkStation-T3400 3.16.0-11-generic #16-Ubuntu SMP Mon Aug 25 20:03:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

[COLOR=#000000]uname -a[/COLOR]
[COLOR=#000000]Linux pixel 3.16.0-6-generic #11-Ubuntu SMP Mon Jul 28 01:59:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

[COLOR=#000000]are you using ubuntu proposed updates? why i can't see [/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]3.16.0-11 in my updates?[/FONT][/COLOR][/COLOR]

---

### Post by 3vi1 on 2014-08-29
I've been running Utopic since the day the repos opened with no issues until I got bit by this today too.

My Intel HD4000/nVidia 670MX laptop is running bumblebee with nvidia-343 mamarly ppa drivers.  I'm getting a black screen when lightdm should pop up.  If I try failsafe graphics, I also get a black screen, but on the first boot after that I can at least see lightdm (which then goes back to black when the desktop should load).  Every subsequent boot (even after complete power-off) will be black on lightdm screen unless I try failsafe again.

Booting old kernel does not change symptoms.

I think someone must have been in a hurry to get something in before beta1 freeze again, eh?  I've always ridden the +1 repos, and this appears to be a recurring theme.

---

### Post by ventrical on 2014-08-29
> **pixelro said:**
> [COLOR=#000000]uname -a[/COLOR]
[COLOR=#000000]Linux pixel 3.16.0-6-generic #11-Ubuntu SMP Mon Jul 28 01:59:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

[COLOR=#000000]are you using ubuntu proposed updates? why i can't see [/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]3.16.0-11 in my updates?[/FONT][/COLOR][/COLOR]


 No.

 I use:

```

sudo apt-get dist-upgrade

```

from terminal. During development releases this has been a systemic problem where some groups or sets will get updates and other will not , so , the solution is to :

```

sudo apt-get install synaptic

```

and use synaptic package manager to do the updates. It never fails to pull in the kernels .. also check  the server you are using from Software&Updates. I am currently using the server from Canada but I have had to switch to Main on occasions , to get all the updates/upgrades.

---

### Post by ventrical on 2014-08-29
> **3vi1 said:**
> ...

I think someone must have been in a hurry to get something in before beta1 freeze again, eh?  I've always ridden the +1 repos, and this appears to be a recurring theme.



Don't know if this will help:

[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without     booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work     either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings).     

```

          sudo apt-get purge nvidia*  sudo apt-get install nvidia-current


```

---

### Post by pixelro on 2014-08-29
> **ventrical said:**
> No.

 I use:

```

sudo apt-get dist-upgrade

```

from terminal. During development releases this has been a systemic problem where some groups or sets will get updates and other will not , so , the solution is to :

```

sudo apt-get install synaptic

```

and use synaptic package manager to do the updates. It never fails to pull in the kernels .. also check  the server you are using from Software&Updates. I am currently using the server from Canada but I have had to switch to Main on occasions , to get all the updates/upgrades.

thanks!!!! i'm using the main for updates. i'll take a look to synaptic and aptitude

---

### Post by Cavsfan on 2014-08-29
I'm in the same boat as everyone else I guess. This is on Utopic and Utopic Mate; neither boot.
I did see an error about the nvidia driver not successfully installed and it mentioned a log file but it didn't exist.

I'll just wait this one out and boot in then press Alt+Cntl+F1 to login CLI and get the updates that way.
I imagine it'll straighten itself out.

Here is the bug if any one wants to add themselves to it. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257)

---

### Post by ventrical on 2014-08-29
> **Cavsfan said:**
> I'm in the same boat as everyone else I guess. This is on Utopic and Utopic Mate; neither boot.
I did see an error about the nvidia driver not successfully installed and it mentioned a log file but it didn't exist.

I'll just wait this one out and boot in then press Alt+Cntl+F1 to login CLI and get the updates that way.
I imagine it'll straighten itself out.

Here is the bug if any one wants to add themselves to it. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257)


It always does straighten itself out :) lol  I have become wiser throughout the years to be careful about nvidia ppas and nvidia proprietary drivers but I do experiment from time to time .. fact is .. I'll give it a whirl on my Dell Precision right now.. :) lol

edit:

As suspected .. completely broke my desktop!1 Can't even get terminal . Will have to use Grub Recovery mode ... but there is one caveat I would like to post. I am using a KVM switcher and when I switch to another PC I can see a flash of the login screen before it switches to the other machine 0 sit appears to be some kind of 'blank screen mask' of some sort. This bug was infamous during the quantal and saucy devs.

 brb

---

### Post by ventrical on 2014-08-29
Ok.. and now will reboot:

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ sudo apt-get install nvidia-current
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-9 linux-headers-3.16.0-9-generic
  linux-image-3.16.0-9-generic linux-image-extra-3.16.0-9-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dkms lib32gcc1 libc6-i386 libcuda1-304 libvdpau1 nvidia-304
  nvidia-libopencl1-304 nvidia-opencl-icd-304 nvidia-settings
  screen-resolution-extra
Suggested packages:
  debhelper nvidia-vdpau-driver vdpau-driver
The following NEW packages will be installed:
  dkms lib32gcc1 libc6-i386 libcuda1-304 libvdpau1 nvidia-304 nvidia-current
  nvidia-libopencl1-304 nvidia-opencl-icd-304 nvidia-settings
  screen-resolution-extra
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.3 MB of archives.
After this operation, 221 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ utopic/main libvdpau1 amd64 0.7-2 [23.8 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ utopic/main dkms all 2.2.0.3-1.1ubuntu5 [64.4 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ utopic/main libc6-i386 amd64 2.19-4ubuntu2 [2,207 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ utopic/restricted libcuda1-304 amd64 304.123-0ubuntu2 [6,418 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ utopic/main lib32gcc1 amd64 1:4.9.1-9ubuntu1 [48.0 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu/ utopic/restricted nvidia-304 amd64 304.123-0ubuntu2 [35.3 MB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ utopic/restricted nvidia-current amd64 304.123-0ubuntu2 [4,468 B]
Get:8 http://ca.archive.ubuntu.com/ubuntu/ utopic/restricted nvidia-libopencl1-304 amd64 304.123-0ubuntu2 [16.3 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ utopic/restricted nvidia-opencl-icd-304 amd64 304.123-0ubuntu2 [5,412 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ utopic/main screen-resolution-extra all 0.17.1 [11.4 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ utopic/main nvidia-settings amd64 331.20-0ubuntu8 [774 kB]
Fetched 50.3 MB in 3min 19s (252 kB/s)                                         
Selecting previously unselected package libvdpau1:amd64.
(Reading database ... 226727 files and directories currently installed.)
Preparing to unpack .../libvdpau1_0.7-2_amd64.deb ...
Unpacking libvdpau1:amd64 (0.7-2) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package libc6-i386.
Preparing to unpack .../libc6-i386_2.19-4ubuntu2_amd64.deb ...
Unpacking libc6-i386 (2.19-4ubuntu2) ...
Selecting previously unselected package libcuda1-304.
Preparing to unpack .../libcuda1-304_304.123-0ubuntu2_amd64.deb ...
Unpacking libcuda1-304 (304.123-0ubuntu2) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a4.9.1-9ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:4.9.1-9ubuntu1) ...
Selecting previously unselected package nvidia-304.
Preparing to unpack .../nvidia-304_304.123-0ubuntu2_amd64.deb ...
Unpacking nvidia-304 (304.123-0ubuntu2) ...
Selecting previously unselected package nvidia-current.
Preparing to unpack .../nvidia-current_304.123-0ubuntu2_amd64.deb ...
Unpacking nvidia-current (304.123-0ubuntu2) ...
Selecting previously unselected package nvidia-libopencl1-304.
Preparing to unpack .../nvidia-libopencl1-304_304.123-0ubuntu2_amd64.deb ...
Unpacking nvidia-libopencl1-304 (304.123-0ubuntu2) ...
Selecting previously unselected package nvidia-opencl-icd-304.
Preparing to unpack .../nvidia-opencl-icd-304_304.123-0ubuntu2_amd64.deb ...
Unpacking nvidia-opencl-icd-304 (304.123-0ubuntu2) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_331.20-0ubuntu8_amd64.deb ...
Unpacking nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for dbus (1.8.6-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu3) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Setting up libvdpau1:amd64 (0.7-2) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up libc6-i386 (2.19-4ubuntu2) ...
Setting up libcuda1-304 (304.123-0ubuntu2) ...
Setting up lib32gcc1 (1:4.9.1-9ubuntu1) ...
Setting up nvidia-304 (304.123-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-304/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-304/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-304/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-304
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Loading new nvidia-304-304.123 DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-11-generic
Building for architecture x86_64
Building initial module for 3.16.0-11-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-11-generic/updates/dkms/

depmod.......

DKMS: install completed.
Setting up nvidia-current (304.123-0ubuntu2) ...
Setting up nvidia-libopencl1-304 (304.123-0ubuntu2) ...
Setting up nvidia-opencl-icd-304 (304.123-0ubuntu2) ...
Setting up screen-resolution-extra (0.17.1) ...
Processing triggers for dbus (1.8.6-1ubuntu1) ...
Setting up nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for libc-bin (2.19-4ubuntu2) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-11-generic
ventrical@ventrical-Precision-WorkStation-T3400:~$ 

```

---

### Post by ventrical on 2014-08-29
Can't even get to recovery menu!! No Grub.  The boot process takes right over and goes to blanck screen with blinking cursor.

---

### Post by ventrical on 2014-08-29
Ok.. got GRuB and was able to purge nVidia-current and had to do two hard reboots.  On the first hard boot it tries to get you to send a bug report which is an *XORG* problem. It asks for some of your display logs , and says it is sensitive info . When you decline it locks up solid , requiring a hard reboot. After that the bug alert is gone and I have my nouveau drivers working normally again.

 So I think this is xorg and apport  problem , not nVidia or kernel. ..  just my 2 cents worth . 
Thanks

Regards..

---

### Post by P-I H on 2014-08-29
I updated my system last evening. It booted OK this morning, but after updating 7 packages related to sign on, I got no desktop. I am able to get a terminal with Ctrl+Alt+F1 and will wait until the problem is fixed.

---

### Post by 3vi1 on 2014-08-29
> **P-I H said:**
> I updated my system last evening. It booted OK this morning, but after updating 7 packages related to sign on, I got no desktop. I am able to get a terminal with Ctrl+Alt+F1 and will wait until the problem is fixed.

Yeah, I see a lot of people pointing fingers at nvidia but I can't even get to the LightDM screen (running on intel chipset).  My desktop also would be running solely with the intel drivers as I only use primusrun and the nvida drivers to launch a few specific games.  If it were an nvidia driver problem, I would have expected it to have been fixed when I booted to the -10 kernel and purged/reinstalled the nvidia packages (but there were no changes in the symptoms or visible errors).

My Xorg.0 log file shows no errors except for a missing dri3 module, which I think is normal with utopic's current XOrg version.

On the plus side, my "browsing-internet-sites-with-lynx-Fu" is increasing.  :)

---

### Post by bapoumba on 2014-08-29
Not sure this is related. I get the same type of problem. After booting up, I get to a black screen with the mouse cursor (which works).
ctrl-alt-F2 (or other VT) gets to a black screen without anything, not even a blinking cursor. ctrl-alt-F7 gets me back to seeing the login screen. If, before going to the VT, I blindly enter my password, the screen is still black. Going to a VT and back to the graphical session gets me back to my desktop.

Happened already early on Utopic. I tried **sudo dpkg-reconfigure lightdm** which worked at the time, but not now. Intel chipset BTW.
```
*-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0100000-d017ffff ioport:1800(size=8) memory:b0000000-bfffffff memory:d0200000-d023ffff
```

---

### Post by Wise Ferret on 2014-08-29
The kernel was updated now to 3.16.0-12, and I tried to install nvidia drivers over it, but the issue is not solved.

---

### Post by Cavsfan on 2014-08-29
> **ventrical said:**
> It always does straighten itself out :) lol

I know right? :lol: Been here a couple times myself. :) I used to just jump to a clean install but age and experience have told me to just wait it out.
 I booted into recovery and got networking and then root shell. Purged everything nvidia-331 nvidia-331-uvm nvidia-libopencl1-331 nvidia-opencl-icd-331 nvidia-prime nvidia-settings (all from the repos)
Then purged both kernels and of course it took linux-generic linux-headers-generic linux-image-generic along with it.

It got an error removing nvidia-prime and it's neither installed or removed it says. :p

I tried to add the 3.16.0-10-generic first but that pulled in both that and 3.16.0-11-generic. I am able to login to flashback (with compiz) just fine but the cpu usage by compiz and Xorg is horrible and I cannot stay on here very much longer.

I can't add the aforementioned nvidia components because it's whining about nvidia-prime. I've tried everything I can think of to get rid of it.
Synaptic pops up a box with this:
```
E: nvidia-prime: subprocess installed pre-removal script returned error exit status 5
```
And this in details:
```
(synaptic:9183): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 214649 files and directories currently installed.)
Removing nvidia-prime (0.6.6) ...
Failed to issue method call: Unit nvidia-prime.service not loaded.
invoke-rc.d: initscript nvidia-prime, action "stop" failed.
dpkg: error processing package nvidia-prime (--purge):
 subprocess installed pre-removal script returned error exit status 5
Failed to issue method call: Unit nvidia-prime.service failed to load: No such file or directory.
invoke-rc.d: initscript nvidia-prime, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 6
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

Then terminal produces this:
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge nvidia-prime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-prime*
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 104 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 214649 files and directories currently installed.)
Removing nvidia-prime (0.6.6) ...
Failed to issue method call: Unit nvidia-prime.service not loaded.
invoke-rc.d: initscript nvidia-prime, action "stop" failed.
dpkg: error processing package nvidia-prime (--purge):
 subprocess installed pre-removal script returned error exit status 5
Failed to issue method call: Unit nvidia-prime.service failed to load: No such file or directory.
invoke-rc.d: initscript nvidia-prime, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 nvidia-prime
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

So, I can't update anything with this error. It has some vlc updates held back that will not install.

It's the same on Mate too.
I'm outta here before I burn my cpu up. It's constantly using over 50% and the temps are getting up there.
Maybe tomorrow will be a better day.

---

### Post by bapoumba on 2014-08-30
I do not want to pollute this thread if my observations are not related..
I turned the computer on this morning and was distracted by other things. When I came back to it, the login screen was welcoming me. I left it on the black screen and came back about half hour later. Will try to reproduce with a better timing.

---

### Post by frafu on 2014-08-30
Hi, 

I just had a similar issue with Ubuntu Utopic. Switching to the nouveau driver makes the system work again, but the gui is quite slower. 

Cheers

---

### Post by 3vi1 on 2014-08-30
Okay - I think I just got it fixed on my bumblebee setup.  The solution for me was to blacklist nvidia-343 in /etc/modprobe.d/bumblebee.conf

I *believe* Bumblebeed is supposed to unload any loaded nvidia module when it starts... so I really shouldn't have had to do this except as an optimization.  Maybe something's changed with the load order and there's a race condition preventing bbswitch from working properly?  I certainly didn't have nvidia-343 blacklisted before, and everything was working fine (ever since 343 was released).

After blacklisting, I can see everything at boot and log in.  I've just now re-enabled all my desktop effects and tested that primusrun is running fine.  I'm going to do one more clean boot, just to make sure.  **EDIT:**  Still works great after reboot!

I can see where others might workaround the problem by back-leveling their nvidia - to a version that already exist in the blacklist file.  But it's not the older version that's the solution - it just works because its blacklisted and not loaded at boot.

---

### Post by VinDSL on 2014-08-30
Had the same nVidia problem as everyone else.

it appears that the only nVidia version that *somewhat* works for me is nvidia-updates.

Switching to nvidia-updates got me to the desktop, but it appeared that BOTH nVidia AND Nouveau were running, so after an x-number of minutes, my nVidia GPU would lock up.


Video is lagging as_all_get_out, but the nVidia GPU hasn't locked up yet (uptime 46 minutes).A session only lasted after 5 minutes, last night.

Onward and upward...  :)

---

### Post by VinDSL on 2014-08-30
Hrm...

Browsers are locking up now (1 hr 40 min uptime).

How can the following be?!?!?

```
vindsl@Zuul:~$ ps aux | grep nvidia
vindsl   10227  0.0  0.1   4440  1928 pts/3    S+   12:08   0:00 grep --color=auto nvidia
vindsl@Zuul:~$ ps aux | grep nouveau
vindsl   10244  0.0  0.1   4440  1896 pts/3    S+   12:08   0:00 grep --color=auto nouveau
vindsl@Zuul:~$ 
```

Guess I need to blacklist one or the other...

---

### Post by ScislaC on 2014-08-30
> **VinDSL said:**
> Had the same nVidia problem as everyone else.

it appears that the only nVidia version that *somewhat* works for me is nvidia-updates.

I just tried to install nvidia-331-updates and it made no difference.

---

### Post by VinDSL on 2014-08-30
I just blacklisted Nouveau, and that made no difference.  :)

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/ /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor: Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Sat Aug 30 19:37:02 UTC 2014
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.16.0-4-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  3.0 Mesa 10.2.6

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.2.6-1ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-common
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-xephyr
  Installed: 2:1.15.1-0ubuntu9

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor: Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

Guess I''l blacklist nvidia next, and see it I can get Nouveau off the 'crack' pipe...  :)

---

### Post by frafu on 2014-08-30
> **VinDSL said:**
> 
Guess I''l blacklist nvidia next, and see it I can get Nouveau off the 'crack' pipe...  :)


Why not simply remove the nvidia proprietary driver instead of blacklisting it?

---

### Post by VinDSL on 2014-08-30
Okay, I purged & blacklisted nVidia.  Then, I installed firmware support for Nouveau.

Everything seems to be working fine, now.

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/ /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor: Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Sat Aug 30 19:53:23 UTC 2014
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.16.0-4-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.2.6

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
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.2.6-1ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-common
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-xephyr
  Installed: 2:1.15.1-0ubuntu9

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor: Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

Obviously, nVidia is rekt.

Wake me up when nVidia is fixed, plz...  ):P

---

### Post by mc4man on 2014-08-30
> **VinDSL said:**
> Hrm...

Browsers are locking up now (1 hr 40 min uptime).

How can the following be?!?!?

```
vindsl@Zuul:~$ ps aux | grep nvidia
vindsl   10227  0.0  0.1   4440  1928 pts/3    S+   12:08   0:00 grep --color=auto nvidia
vindsl@Zuul:~$ ps aux | grep nouveau
vindsl   10244  0.0  0.1   4440  1896 pts/3    S+   12:08   0:00 grep --color=auto nouveau
vindsl@Zuul:~$ 
```

Guess I need to blacklist one or the other...

Those are just returning grep on grep, are either actually a process? (named

Here I just use intel (Haswell) & there is no real current issue like this (with the older Intel driver),  though 14.10 has continuing issues with graphical shutdowns & restarts

Is the cma kernel issue coming into play here for you?

---

### Post by VinDSL on 2014-08-30
> **Elfy said:**
> I removed nvidia and reverted to nouveau before rebooting after kernel update. Booted fine to the desktop, reinstalling nvidia afterwards and it's not getting loaded so still using nouveau here (xubuntu)

BTW, you were right, Big E!  :cool:

---

### Post by VinDSL on 2014-08-30
> **mc4man said:**
> Those are just returning grep on grep, are either actually a process? (named

Correct!  I realized that about 5 minutes later, and was too lazy to redact it.  ;)



> **mc4man said:**
> Is the cma kernel issue coming into play here for you?

Do tell -- I'm not aware of that issue.

I'm running the Linux 3.16.0-4-generic kernel.

Does 'the cma kernel issue' affect it?!?!?

---

### Post by VinDSL on 2014-08-30
> **mc4man said:**
> Is the cma kernel issue coming into play here for you?

Found this in the LP bugz: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1347088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1347088)  (cma mem leak)

Is that what you're referring to?

---

### Post by VinDSL on 2014-08-30
Nouveau is working quite nicely.

I just installed the 3.17rc2 mainline kernel.  According to the changelog, it fixed a regression -- cma was mentioned.

```
Alexey Kardashevskiy (1):
      PC, KVM, CMA: Fix regression caused by wrong get_order() use

```

CPU usage seems to be a lot higher than Linux 3.16   

We'll see how it goes...

---

### Post by mc4man on 2014-08-30
> **VinDSL said:**
> Found this in the LP bugz: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1347088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1347088)  (cma mem leak)

Is that what you're referring to?Maybe?? Was referring to this thread - [http://ubuntuforums.org/showthread.php?t=2240948](http://ubuntuforums.org/showthread.php?t=2240948)
Which lead to this bit (some interesting comments near the end about enabling cma at all on x86
[http://lists.freedesktop.org/archives/dri-devel/2014-August/065842.html](http://lists.freedesktop.org/archives/dri-devel/2014-August/065842.html)

(My only interest in 14.10 is what can be backported to 14.04, some ex. [here]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6/+packages")

---

### Post by VinDSL on 2014-08-30
~Cool.  Thx for that.

Interesting project you got going there.

I'm trying to get Nitrogen working with Nemo (my C++ is a little rusty).

Anyway, everything has been working okay with the mainline 3.17rc2 / nouveau combo (6 hr 43 min uptime).

Oddly, when I'm using this (Ubu Forums) message editor, my CPUs peg @ 100% usage.  It'll go back to normal after I submit.

EDIT

After submitting the reply, CPU usage dropped to <=6%.

Heh!  Go figure...  :)

---

### Post by Elfy on 2014-08-31
> **VinDSL said:**
> BTW, you were right, Big E!  :cool:

If only I'd left half broken alone ... 

Got one still half-broken which I'll get back to - completely killed the other one :p

---

### Post by Cavsfan on 2014-08-31
I take it is still dead in the water right? I booted into recovery, got networking and then went to root shell and got some updates.
None of which would solve this problem although I don't what the fix would look like really. :p

---

### Post by xeizoo on 2014-08-31
I\m running the below, lets just say everything was muuuch smoother yesterday using the proprietary Nvidia driver, but regressions was expected just wondered why it took so long ...

> ~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: sön 31 aug 2014 17:08:51 UTC
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.16.1-031601-lowlatency
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVE6
OpenGL version string:  3.0 Mesa 10.4.0-devel

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
Installed-Size: 138
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: [http://mesa3d.org/](http://mesa3d.org/)

Package: mesa-common-dev
 Version: 10.4.0~git20140829.6cd0dbc4-0ubuntu0sarvatt

Package: xserver-xorg-core

Package: xserver-common

Package: xserver-xephyr

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 4th Gen Core Processor DRAM Controller
           +-01.0-[01]--+-00.0  NVIDIA Corporation GK106 [GeForce GTX 650 Ti]
           |            \-00.1  NVIDIA Corporation GK106 HDMI Audio Controller
           +-14.0  Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
           +-16.0  Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
           +-1a.0  Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
           +-1b.0  Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
           +-1c.0-[02]--
           +-1c.2-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           +-1c.6-[04-05]----00.0-[05]----01.0  C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
           +-1d.0  Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
           +-1f.0  Intel Corporation Z87 Express LPC Controller
           +-1f.2  Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
           \-1f.3  Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller


---

### Post by xeizoo on 2014-08-31
Oh, I disabled Compton and restarted and now Nouveau/Gallium actually behaves quite smooth, running Xfce as desktop ....

---

### Post by Cavsfan on 2014-08-31
Surely the fix will be coming soon. I mean how many people have Nvidia cards? I'd venture to say more than don't.
I'm not going to do anything special to get it to work. I'll just wait [S]patiently[/S] until the fix is released.

I'm going to pretend I don't know anything about anything which is pretty close to the truth. :p

---

### Post by pixelro on 2014-08-31
> **Cavsfan said:**
> Surely the fix will be coming soon. I mean how many people have Nvidia cards? I'd venture to say more than don't.
I'm not going to do anything special to get it to work. I'll just wait [S]patiently[/S] until the fix is released.

I'm going to pretend I don't know anything about anything which is pretty close to the truth. :p

worst beta ever! :lolflag:

---

### Post by jerrylamos on 2014-08-31
> **pixelro said:**
> worst beta ever! :lolflag:Well, I've been on Ubuntu unstable since Dapper Drake Beta.  From time to time some of them haven't run on the hardware I had at the time.  Lately I just got a refurb Lenovo Intel Core 2 Duo 3 gHz for $150 fastest hardware I've had except for utopic 64 bit since 7/31 - compiz & unity won't start.  Yes there are launchpad bugs filed, just no resolution.

---

### Post by caryb on 2014-08-31
<Rant>Not wanting to seem bitchy but saying I disabled Blah or blacklist blah is not helpful without some explanation. I'm very Linux savy on the server side but some of these posts are not helpful<end Rant>

---

### Post by Cavsfan on 2014-08-31
Breakage is kool! :guitar:

[ATTACH=CONFIG]256023[/ATTACH]

---

### Post by Cavsfan on 2014-08-31
> **caryb said:**
> <Rant>Not wanting to seem bitchy but saying I disabled Blah or blacklist blah is not helpful without some explanation. I'm very Linux savy on the server side but some of these posts are not helpful<end Rant>

Why not just wait it out like most of us? Myself, I don't want to remove the nvidia drivers even if that fixes the problem. I know I'll just have to add them back so I'm just waiting...

---

### Post by caryb on 2014-08-31
My rant was not about patience but more about if your going to offer suggestions full explanation & file locations etc would be helpful.

---

### Post by Alan F on 2014-09-01
> **jerrylamos said:**
> .......................... - compiz & unity won't start.  Yes there are launchpad bugs filed, just no resolution.

And what is even more disturbing is that there appears no acknowledgement of where the problem actually resides.

---

### Post by ventrical on 2014-09-01
> **Alan F said:**
> And what is even more disturbing is that there appears no acknowledgement of where the problem actually resides.

My guess is that  with summer winding down and it being Labour Day in the Americas that some devs could be taking a time out.

All my nVidia DTs are working with nouveau, but I am still experimenting.

---

### Post by ventrical on 2014-09-01
> **Cavsfan said:**
> Why not just wait it out like most of us? Myself, I don't want to remove the nvidia drivers even if that fixes the problem. I know I'll just have to add them back so I'm just waiting...

That's a failsafe approach :) lol  When working here in Development it is always wise to have extra hardware and machines to do other stuff while waiting for the fixes to come in. I have 3 working KVMs and there is tons of stuff to do when a bottle neck occurs with dev nVidia drivers.:)

---

### Post by klim8 on 2014-09-01
Try with:

```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```

---

### Post by zoltan140 on 2014-09-01
ubuntu-drivers-common (Ubuntu): &#8594; Fix Released 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363675](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363675)

---

### Post by jerrylamos on 2014-09-01
> **klim8 said:**
> Try with:

```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```

Thanks for something to try.

Msg was there is only one alternative.......there is nothing to configure.

So no help, didn't change anything, still boots to desktop no unity no compiz

Thanks anyway.

I haven't gotten any hints from launchpad.

---

### Post by Cavsfan on 2014-09-01
> **ventrical said:**
> That's a failsafe approach :) lol  When working here in Development it is always wise to have extra hardware and machines to do other stuff while waiting for the fixes to come in. I have 3 working KVMs and there is tons of stuff to do when a bottle neck occurs with dev nVidia drivers.:)

Indeed! I would not be testing any developmental version if I didn't have other options. (You can tell by my signature.) :)
 I'm sitting here in an LTS version - one of the 6 Linux systems I have installed 2 of which are 14.10 all the rest are LTS.

I'm going to go see if the fix was released now as post #69 stated.

---

### Post by ScislaC on 2014-09-01
> **zoltan140 said:**
> ubuntu-drivers-common (Ubuntu): &#8594; Fix Released 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363675](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363675)

That didn't seem to fix it here unfortunately. Anyone else have luck?

---

### Post by Cavsfan on 2014-09-01
It's fixed here and all is swell :) :guitar:

I just booted to recovery mode, picked up networking then dropped to root shell and got the updates.
I think it was ubuntu-drivers-common that fixed it unless one or more of the lib files that were also installed were involved.

```
ubuntu-drivers-common (1:0.2.98.1) utopic; urgency=medium


  * gpu-manager.c, gpu-manager.py:
    - Avoid false positives with blacklisted modules (LP: #1363675).
    - Add regression test for the bug.


 -- Mon, 01 Sep 2014 18:01:09 +0200
```

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                            331.89-0ubuntu2                            amd64        NVIDIA binary driver - version 331.89
ii  nvidia-331-uvm                                        331.89-0ubuntu2                            amd64        NVIDIA Unified Memory kernel module
ii  nvidia-libopencl1-331                                 331.89-0ubuntu2                            amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.89-0ubuntu2                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.6                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                            amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Cavsfan on 2014-09-01
Fixed here on Utopic Mate as well. I'd mark this thread as resolved.

When in root shell "reboot" would not reboot the machine on either install just a blinking cursor in the top left, I had to press the reset button. 

But it came right back up in systemd at this moment.

---

### Post by Elfy on 2014-09-01
> **Cavsfan said:**
> Fixed here on Utopic Mate as well. I'd mark this thread as resolved.

When in root shell "reboot" would not reboot the machine on either install just a blinking cursor in the top left, I had to press the reset button. 

But it came right back up in systemd at this moment. fixed for you perhaps ;)

> **ScislaC said:**
> That didn't seem to fix it here unfortunately. Anyone else have luck?

---

### Post by caryb on 2014-09-01
Still pooched on Kubuntu with today's updates.

---

### Post by jerrylamos on 2014-09-01
amd64 utopic today's updates no unity, no compiz unless nomodeset is added to the linux boot line.  All I then get is 1024x768 should be 1360x768.
Wierdo is the .iso boots with  unity & compiz but the resulting install doesn't.

i386 utopic today's updates unity/compiz running though they haven't for the last week.

3.17.0-rc3 hangs on boot unless nomodeset is added to the linux boot line.  Degraded resoluton....

Shades of Ubuntu Intrepid.  Months after RC compiz was eventually fixed....

Well this is a development forum....

---

### Post by ScislaC on 2014-09-01
> **ScislaC said:**
> That didn't seem to fix it here unfortunately. Anyone else have luck?

After uninstalling and reinstalling the nvidia packages it seems to be resolved.

---

### Post by caryb on 2014-09-01
Ok seems to be a permissions thing after todays updates, If I from the terminal as root type startx it works fine as root, I have removed the config folder from KDE but still crashes back to black screen.

---

### Post by VinDSL on 2014-09-01
> **ScislaC said:**
> After uninstalling and reinstalling the nvidia packages it seems to be resolved.

Okay.  I'll give it a whirl... 

BRB

---

### Post by jerrylamos on 2014-09-02
I"ve had a similar problem, boots to desktop no unity hence useless since July 31.
Will boot up in video degraded mode (ugly) if nomodeset is added to the linux line when booting.

Booting in nomodeset, then sudo apt-get update, sudo apt-get dist-upgrade brought in linux-image-3.16.0-12 

Booted 3.16.0-12 several times normally O.K. on this Intel Core 2 Duo 3 gHz.

---

### Post by pixelro on 2014-09-02
the last update fixed it for me 3.16.0-12-generic

nvidia proprietary is working again 

):P

---

### Post by Alan F on 2014-09-02
> **jerrylamos said:**
> I"ve had a similar problem, boots to desktop no unity hence useless since July 31.
Will boot up in video degraded mode (ugly) if nomodeset is added to the linux line when booting.

Booting in nomodeset, then sudo apt-get update, sudo apt-get dist-upgrade brought in linux-image-3.16.0-12 

Booted 3.16.0-12 several times normally O.K. on this Intel Core 2 Duo 3 gHz.

Regret  that 3.16.0-12 kernel does NOT resolve the problem on my laptop (Intel graphics). It will be interesting to see how this one pans out.

---

### Post by ventrical on 2014-09-02
Working here now with new updates...

---

### Post by xeizoo on 2014-09-03
Yes, 3.16.0-12 did the trick, it also runs virtualbox successfully(apart from the benefit of actually running so is virtualbox very slow and unresponsive with nouveau/gallium). It means *everything* is working as it should again on my box :-)

> ~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: ons  3 sep 2014 12:40:11 UTC
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.16.0-12-lowlatency
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 650 Ti/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 343.13

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
Installed-Size: 138
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: [http://mesa3d.org/](http://mesa3d.org/)

Package: mesa-common-dev
 Version: 10.4.0~git20140829.6cd0dbc4-0ubuntu0sarvatt

Package: xserver-xorg-core

Package: xserver-common

Package: xserver-xephyr

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 4th Gen Core Processor DRAM Controller
           +-01.0-[01]--+-00.0  NVIDIA Corporation GK106 [GeForce GTX 650 Ti]
           |            \-00.1  NVIDIA Corporation GK106 HDMI Audio Controller
           +-14.0  Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI
           +-16.0  Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1
           +-1a.0  Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2
           +-1b.0  Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller
           +-1c.0-[02]--
           +-1c.2-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           +-1c.6-[04-05]----00.0-[05]----01.0  C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
           +-1d.0  Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1
           +-1f.0  Intel Corporation Z87 Express LPC Controller
           +-1f.2  Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
           \-1f.3  Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller

---

### Post by VinDSL on 2014-09-05
Seems like the proprietary nVidia drivers went belly up again.  :(

Default Nouveau driver is still working for me, but I can't get my machine off the 'pipe'...

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/ /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor: Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Fri Sep  5 16:47:00 UTC 2014
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.17.0-031700rc3-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  3.0 Mesa 10.2.6

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.2.6-1ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-common
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-xephyr
  Installed: 2:1.15.1-0ubuntu9

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor: Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by Elfy on 2014-09-05
working fine here - though we did have something else yesterday [http://ubuntuforums.org/showthread.php?t=2242791](http://ubuntuforums.org/showthread.php?t=2242791)

there is an update gone through - I've had that from the main server an hour or so ago.

---

### Post by VinDSL on 2014-09-05
Thx, Elfy!  I'll try that.

I updated about an hour ago, but I'm using a mirror.  I'll switch to the main server  ;)

---

### Post by Cavsfan on 2014-09-05
Yeah working fine here. I get the DKMS error on the first DKMS build but not on the 2nd. Not sure if that's why I'm good to go or not.
```
Error! Bad return status for module build on kernel: 3.16.0-13-generic (x86_64)
Consult /var/lib/dkms/nvidia-331/331.89/build/make.log for more information.
```

Maybe that is why the log file doesn't exist. IDK

Here is what I have installed:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                            331.89-0ubuntu3                            amd64        NVIDIA binary driver - version 331.89
ii  nvidia-331-uvm                                        331.89-0ubuntu3                            amd64        NVIDIA Unified Memory kernel module
ii  nvidia-libopencl1-331                                 331.89-0ubuntu3                            amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.89-0ubuntu3                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.6                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                            amd64        Tool for configuring the NVIDIA graphics driver


```

It gets the DKMS error with nvidia-331 but not with nvidia-331-uvm.

Here is the bug [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257)

---

### Post by VinDSL on 2014-09-05
> **VinDSL said:**
> Seems like the proprietary nVidia drivers went belly up again.  :(

Default Nouveau driver is still working for me, but I can't get my machine off the 'pipe'...

For the sake of discussion...

Couldn't figure out why this machine wouldn't get off of 'llvmpipe'.

I switched from Linux 3.17 rc -> Linux 3.16 and now the hardware support is working in Nouveau. :p

```
~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Fri Sep  5 18:27:26 UTC 2014
Distro Release: Ubuntu Utopic Unicorn (development branch)
Kernel Release: Linux 3.16.0-4-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.2.6

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
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.2.6-1ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-common
  Installed: 2:1.15.1-0ubuntu9

Package: xserver-xephyr
  Installed: 2:1.15.1-0ubuntu9

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor: Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 
```

---

