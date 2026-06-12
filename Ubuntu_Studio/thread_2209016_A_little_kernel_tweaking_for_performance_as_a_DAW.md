---
title: "A little kernel tweaking for performance as a DAW"
date: 2014-03-03
forum: Ubuntu Studio
---

### Post by brianmc on 2014-03-03
:arrow: ***This is not something I'm going to be able to provide support for! I'm just sharing my method and results for anyone brave (or foolhardy?) with similar problems as I experienced.***

I've dabbled with Ubuntu Studio since back at the 9.04 distro, with one of the perennial problems being squeezing enough performance out of the system to reliably avoid overruns. I've contemplated going over to Gentoo, but that is a fairly hardcore approach. Similarly, building a genuinely realtime kernel seems to have become practically-impossible.

However, even the lowlatency kernel is rather '*generic*'; it includes support for Intel and AMD processors, plus a bunch of other stuff you may-well not need.

The system I've done this work on reports its processor as an **AMD Athlon(tm) II X4 620 Processor**. In Ardour I was getting a lot of Xruns using a single Edirol DA2496 card, with QJackCtl reporting RT use as-high as **62%** (low: 51%) when run at a 96kHz sample rate, 128 frames/period, and 3 periods/buffer. By compiling a local kernel image, this figure dropped to an upper value of **31%** (low:28%), and no Xruns.

For comparison, the corresponding load-average figures came out as-follows:[INDENT][FONT=fixedsys]**Vanilla kernel:** 1.62, 1.09, 0.92
[/FONT][/INDENT]
[INDENT][FONT=fixedsys]**Tweaked vers:**  0.66, 0.53, 0.35
[/FONT][/INDENT]

There are a *lot* of How-To documents out there that - supposedly - tell you how to build a custom kernel; but, it's a nasty moving target. I ended up documenting what worked for me, then starting to accumulate tweaks. Discarding cross-platform support is an obvious one, as is building-in ALSA and support for the specific sound card(s) in-use rather than having these as modules. Similarly, compile options for power conservation, suspend to ram or disk, and other less-likely hardware are dropped.

The following commands will retrieve (a) packages required to build the kernel, (b) create and go into a directory to build the kernel, and (c) pull down the kernel source of what you're currently running.[SIZE=3]```
[FONT=fixedsys]sudo apt-get update && sudo apt-get install kernel-package libncurses5-dev fakeroot build-essential kernel-wedge
mkdir ~/src; cd ~/src
apt-get source linux-image-$(uname -r)[/FONT]
```
[/SIZE]
Given I'm working with Ubuntu Studio 13.10, the current (not proposed) version is the ***3.11.0-17-lowlatency*** kernel. This is another moving target, and [SIZE=3][FONT=fixedsys]**uname -r**[/FONT][/SIZE] will let you know what kernel you're currently running. If your differs significantly from this, then make liberal use of ***?*** when deciding which options to include, or exclude.

At this point, there should be a linux-lowlatency-3.11.0 directory in ~/src, go into that directory for the following steps - which take you to the point where you can customise the kernel image.
[SIZE=3] ```
[FONT=fixedsys]chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
cp /boot/config-`uname -r` ./.config[/FONT]
```
[/SIZE]
To tweak the kernel configuration, I use [SIZE=3][FONT=fixedsys]**make menuconfig**[/FONT][/SIZE]. There are other ways to edit the configuration; but, as I found with most of my failed attempts, it is best to pick through options a few at a time, disable things you know are unneeded, and switch items you rely on from modules to built-in.

As-best as I can lay this out, here's much of what I change via menuconfig:[FONT=fixedsys]

[SIZE=3]General setup --->
[/SIZE][/FONT][INDENT][SIZE=3][FONT=fixedsys]Arbitrary version signature:    *delete the text in here*
RCU Subsystem --->
[/FONT][/SIZE][/INDENT]
[INDENT=2][SIZE=3][FONT=fixedsys]Accelerate last non-dyntick-idle CPU's grace periods:    [ ] (blank)
Enable RCU priority boosting:    
[*]
[/FONT][/SIZE][/INDENT]
[INDENT][SIZE=3][FONT=fixedsys]Kernel .config support:    
[*]
Enable access to .config through /proc/config.gz:    
[*]
Configure standard kernel features (expert users) --->
[/FONT][/SIZE][/INDENT]
[INDENT=2][SIZE=3][FONT=fixedsys]Enable PC-Speaker support:    [ ] 
[/FONT][/SIZE][/INDENT]
[SIZE=3][FONT=fixedsys]Processor type and features --->    (***Note!** This is the bit you'll want to change if not using an Athlon CPU!*)
[/FONT][/SIZE][INDENT][SIZE=3][FONT=fixedsys]Support for extended (non-PC) x86 platforms:    [ ]
Intel Low Power Subsystem Support:    [ ]
Linux guest support:    [ ] 
Processor family --->
[/FONT][/SIZE][/INDENT]
[INDENT=2][SIZE=3][FONT=fixedsys]Opteron/Athlon64/Hammer/K8:    (X)[/FONT]
[/SIZE][/INDENT]
[INDENT][SIZE=3][FONT=fixedsys]Supported processor vendors --->[/FONT]
[/SIZE][/INDENT]
[INDENT=2][SIZE=3][FONT=fixedsys]Support Intel processors:    [ ] 
Support Centaur processors:    [ ] 
[/FONT][/SIZE][/INDENT]
[INDENT][SIZE=3][FONT=fixedsys]Maximum number of CPUs:    [4]
Intel MCE features:    [ ] 
Dell laptop support:    < > 
Intel microcode loading support:    [ ] 
Allow for memory hot-add:    [ ] [/FONT]
[/SIZE][/INDENT]
[SIZE=3][FONT=fixedsys]Power management and ACPI options --->[/FONT][/SIZE][INDENT][SIZE=3][FONT=fixedsys]Suspend to RAM and standby:    [ ] 
Hibernation (aka 'suspend to disk'):    [ ] 
Power Management Debug Support:    [ ] 
Enable workqueue power-efficient mode by default:    [ ] 
ACPI (Advanced Configuration and Power Interface) Support:    [ ] 
[/FONT][/SIZE][/INDENT]
[SIZE=3][FONT=fixedsys]Bus options (PCI etc.) --->[/FONT][/SIZE][INDENT][SIZE=3][FONT=fixedsys]PCI Stub driver:    < > [/FONT]
[/SIZE][/INDENT]
[SIZE=3][FONT=fixedsys]Networking support --->    (***Note!** I exclude a lot here, check if you need any of these options for your hardware.*)[/FONT][/SIZE][INDENT][SIZE=3][FONT=fixedsys]Amateur Radio support:    [ ] 
CAN bus subsystem support:    < > 
IrDA (infrared) subsystem support:    < > 
Bluetooth subsystem support:    < > 
WiMAX Wireless Broadband support:    < > 
RF switch subsystem support:    < > 
Plan 9 Resource Sharing Support :    < > 
CAIF support:    < > 
NFC subsystem support: < > 
[/FONT][/SIZE][/INDENT]
[SIZE=3]Device Drivers --->
[/SIZE][INDENT][SIZE=3]Parallel port support: < > 
Macintosh device drivers: [ ] 
Character devices --->
[/SIZE][/INDENT]
[INDENT=2][SIZE=3]Cyclades async mux support: < > 
Moxa Intellio support: < > 
Moxa SmartIO support v. 2. 0: < > 
HSDPA Broadband Wireless Data Card - Globe Trotter: < > 
Multi-Tech multiport card support: < > 
Trace data router for MIPI P1149.7 cJTAG standard: < > 
Trace data sink for MIPI P1149.7 cJTAG standard: < > 
Intel HW Random Number Generator support: < > 
Siemens R3964 line discipline: < > 
Applicom intelligent fieldbus card support: < > 
ACP Modem (Mwave) support: < > 
RAW driver (/dev/raw/rawN): <*>
Maximum number of RAW devices to support: [512]
TPM Hardware Support: < > 
Telecom clock driver for ATCA SBC: < > 
[/SIZE][/INDENT]
[INDENT][SIZE=3]Sound card support: <*> (***Note!** Entry duplicated, as set to loaded in-kernel, then sub-menu options tweaked*; likewise for ALSA)
Sound card support ---->
[/SIZE][/INDENT]
[INDENT=2][SIZE=3]Advanced Linux Sound Architecture: <*>
Advanced Linux Sound Architecture --->
[/SIZE][/INDENT]
[INDENT=3][SIZE=3]Sequencer support: <*>
HR-timer backend support: <*>
Max number of sound cards: (8)
Verbose procfs contents: [ ] 
PCI sound devices ---> (***Note!** All I include herein is forcing loading my desired card*)
[/SIZE][/INDENT]
[INDENT=4][SIZE=3]ICEnsemble ICE1712 (Envy24): <*>
[/SIZE][/INDENT]
[INDENT=3][SIZE=3]ALSA for SoC audio support: < > 
[/SIZE][/INDENT]
[INDENT][SIZE=3]HID support --->
[/SIZE][/INDENT]
[INDENT=2][SIZE=3]Battery level reporting for HID devices: [ ] 
User-space I/O driver support for HID subsystem: < > 
[/SIZE][/INDENT]
[INDENT][SIZE=3]Intel Non-Transparent Bridge support: < > 
IndustryPack bus support: < > 
[/SIZE][/INDENT]
[SIZE=3]Firmware Drivers --->
[/SIZE][INDENT][SIZE=3]BIOS update support for DELL systems via sysfs: < > 
DELL Systems Management Base Driver: < > 
[/SIZE][/INDENT]
[SIZE=3]Kernel hacking --->
[/SIZE][INDENT][SIZE=3]Compile-time checks and compiler options --->
[/SIZE][/INDENT]
[INDENT=2][SIZE=3]Compile the kernel with debug info: [ ] 
Strip assembler-generated symbols during link: 
[*]
[/SIZE][/INDENT]
[INDENT][SIZE=3]Verbose BUG() reporting (adds 70K): [ ] 
Allow gcc to uninline functions marked 'inline': [ ] 
[/SIZE][/INDENT]
[SIZE=3]Virtualization --->
[/SIZE][INDENT][SIZE=3]Kernel-based Virtual Machine (KVM) support: < >[/SIZE]
[/INDENT]


[FONT=arial]All Done; exit and save![/FONT]

Next up is actually compiling the kernel, and once you've entered this command you probably want to make a proper cuppa whilst you wait.

The compile command I've used is: [SIZE=3][FONT=fixedsys]**fakeroot make-kpkg -j4 --initrd --append-to-version=-local kernel_image kernel_headers**[/FONT][/SIZE]. If it works for you, there will be two .deb files in the above directory (~/src, assuming you created this and pulled the source into it). Before installing, I'd recommend making sure you get a grub menu displayed on bootup; this is far-safer than relying on Shift to access the menu if - however you may have deviated from the above (or slavishly followed it when you've an Intel CPU) - your new kernel dies when booting.

To install the kernel:[FONT=fixedsys][SIZE=3]
```
cd ~/src
sudo dpkg -i linux-headers-*.deb
sudo dpkg -i linux-image-*.deb
```[/SIZE][/FONT]

I certainly noticed a far-faster bootup with this. That's in-addition to the dramatic performance improvements I was needing for near-realtime audio work. You are, of course, into '*completely unsupported*' territory. ;)

The JACK latency on my chosen parameters (above) is cited as 4ms. What I've found an excellent rule-of-thumb for latency is that 1ms is the time it takes for sound to travel a little over 1 foot (to be more-precise, 34cm). Ardour's signal processing introduces a little extra latency, as-does the physical hardware. Once the JACK latency starts going above 10ms, you're going to notice it - if you've a keen ear. With my Xrun problem, essentially solved, I can trim the periods/buffer from 3 back to 2 - which JACK estimates as 2.67ms latency.

I *really* hope someone else who's had similar problems as myself finds this useful. I've walked through the process whilst composing this post, so I'd hope the only errors it may contain are typos. Prior to successfully building my own kernel, I ended up having to minimise the Ardour main window as-soon as recording started, *and* avoid swapping workspaces when recording; none of these problems are present with the new kernel (not only that, with the lower latency too), and I'd welcome any suggestions on further tweaks.

---

### Post by Jake_Paine on 2014-03-06
Very interesting, I have the same CPU and have struggled a little with projects of around 16-20 channels and the Waves, Guitar Rig + others plugins in Cubase, haven't tried Ardour yet but planning to give it a go and move some of my projects over as long as I can get my VST's working correctly.

May be coming back to this post soon!!

---

### Post by CrocoDuck on 2014-03-06
Cool Stuff! Sooner or later, I'll use this guide somehow!

---

### Post by brianmc on 2014-03-08
VSTs may see you needing to run wine. That'll be a fiddle; I'd suggest trying the various Calf, LADSPA and LV2 plugins before resorting to stuff normally running in Windows.

---

### Post by brianmc on 2014-03-08
Since I'm also building a new system with a Core i5 processor, and that's what my Dell laptop has, I've redone the process taking out AMD specifics. To make redoing the process easier in-future, I'm saving a copy of the config and an [FONT=fixedsys]*i5_config.patch*[/FONT] file for reuse.

```
cd ~/src
apt-get source linux-image-$(uname -r)
# Move into the relevant directory (change 3.11.0 as-appropriate)
cd linux-lowlatency-3.11.0
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
cp /boot/config-`uname -r` ./.config
[B]##  This is a one-off, with the alternate (using patch to tweak config) listed below
#
make menuconfig
[/B]## Save a patchfile and copy of the .config
#
diff -u /boot/config-`uname -r` ./.config > ../i5_config.patch
cp ./.config ../i5_changes.config
## Build the kernel headers and image
#
fakeroot make-kpkg -j4 --initrd --append-to-version=-i5-local kernel_headers kernel_image
cd ~/src
## Install the kernel headers and image
#
sudo dpkg -i linux-headers-*.deb
sudo dpkg -i linux-image-*.deb
```

The above saves the config, and a patch, which can be dropped in and catch most things you'd need to redo for a more-recent kernel. Instead of make menuconfig, the following will apply the saved patch:

```
[B]## Patch kernel .config instead of (or as a prelude to) running make menuconfig
#
patch ./.config < ../i5_config.patch[/B]
```

This system is already running off an SSD, so startup time was already quick. This patch leaves in much of the suspend/resume items, plus VM support. That's down to doing this on a laptop which sees quite a lot of different uses, those would usually come out for a desktop system dedicated to audio work. However, it still sees the startup time visibly-faster (*Plymouth splash? Blink and you miss it*); plus, the system load from running JACK is reduced and kept more-stable.

If rebuilding with a more-recent kernel: then, before installing the latest kernel headers and image, the old need removed. To do so, you want to boot into the current 'official' kernel that you're tweaking the .config of, do the patch and build under it, and list what's in /boot to see which to remove. In my case, that's:

```
## Remove old custom kernel headers and image
#
sudo dpkg -P linux-headers-3.11.10.4-i5-local
sudo dpkg -P linux-image-3.11.10.4-i5-local
```

I've attached a gzipped copy of the patch file for this: [ATTACH]250949[/ATTACH]. This leaves all the sound cards as modules; so, you could run [FONT=fixedsys]**make menuconfig**[/FONT] after applying the patch, further tweak forcing your required soundcard driver(s) be built-in and taking out VM support.

---

### Post by brianmc on 2014-03-08
Here's a patch file for the originally-specified CPU [AMD Athlon(tm) II X4 620 Processor]: [ATTACH]250956[/ATTACH]

Unpacking this in the [FONT=fixedsys]~/src[/FONT] directory would allow the following commands to be used to build a kernel exclusively for use on AMD; but, note this is with only ICE1712 drivers built-in. Almost all other PCI sound card drivers are not being built at-all!

```
 cd ~/src
gunzip amd_config.patch.gz
apt-get source linux-image-$(uname -r)
## Substitute downloaded kernel image version for ***X.XX.X***
#
cd linux-lowlatency-***X.XX.X***
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
cp /boot/config-`uname -r` ./.config
[I][B] ## Patch the kernel config, and backup a copy of it
#
patch ./.config < ../amd_config.patch
cp ./.config ../amd_changes.config
[/B][/I]## All that should need tweaked via menuconfig is enabling the correct PCI driver(s) for your system
#
make menuconfig
[I][B] ## Assuming you've done your own tweaks via menuconfig, save that .config and make a patch file thereof
#
cp ./.config ../amd_changes-local.config
diff /boot/config-`uname -r` ./.config > ../amd_config-local.patch
[/B][/I]## Build the kernel and headers
#
fakeroot make-kpkg -j4 --initrd --append-to-version=-amd-local kernel_headers kernel_image
```

End-result is, as-ever, two [FONT=fixedsys].deb[/FONT] files in the [FONT=fixedsys]~/src[/FONT] directory which you install with **[FONT=fixedsys]sudo dpkg -i[/FONT]**.

To prove that at least Intel/AMD cross-building is supported, I build my AMD64 [FONT=fixedsys].deb[/FONT] files on my i5 laptop, copied them to a USB stick, and successfully installed on the target AMD box. This was whilst running the stock kernel; I've no idea how that particular crossbuild process would go if building without the target CPU support already in the running kernel.

If, for either the i5 or AMD builds, there are any repeated crashes, I would suggest going back to the stock kernel a build is derived from, tweaking the JACK parameters to run reliably (no Xruns, even if the latency is noticable), and work on reproducing the fault there. If unable to reproduce the fault there, something the machine needs is missing in the [FONT=fixedsys].config[/FONT] and you want to go back to ***[FONT=fixedsys]make menuconfig[/FONT]*** with a copy of the stock [FONT=fixedsys].config[/FONT] file.

Don't submit bug reports should Ubuntu keep giving "Unexpected error" messages with a custom kernel. The developers won't thank any of us for that. ;)

---

