---
title: "no sound WoW wine 1.1.8"
date: 2009-03-28
forum: Wine
---

### Post by dennismoore1 on 2009-03-28
ever since i installed wine 1.1.8 and world of warcraft wrath of the lich king 3.0.9, theres been this no sound problem

i originally thought it was either wine or wow but i went to System -> Preferences -> Sound and found that somehow i didnt have sound AT ALL  i click test and NOTHING HAPPENS a box pops up and i guess im supposed to be hearing a sound

i added to my WTF/Config.wtf

SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

and my winecfg is:

OSS Driver
Hardware Acceleration: Emulation
and driver emulation checked

in the audio tab that is

i cant make sense of any of this

all of my audio, by the way, in my system-preferences-sound program are set to alsa

thanks in advance

---

### Post by Darth Buh on 2009-03-29
Yep, same issue here

---

### Post by dennismoore1 on 2009-03-29
someone please help

---

### Post by dennismoore1 on 2009-03-29
i just tried to compile alsa-driver-1.0.9 for my sound card which rings up as:

I82801DBICH4

and it gave me this error

checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /home/christian/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/christian/Desktop/alsa-driver-1.0.9
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-23-generic/build
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "yes"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "yes"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "no"
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
Removing a dummy linux/workqueue.h.
checking for kernel linux/dma-mapping.h... "yes"
Removing a dummy linux/dma-mapping.h.
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
Removing a dummy linux/device.h.
checking for kernel linux/jiffies.h... "yes"
Removing a dummy linux/jiffies.h.
checking for kernel linux/compat.h... "yes"
Removing a dummy linux/compat.h.
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
Removing a dummy linux/moduleparam.h.
checking for kernel linux/syscalls.h... "yes"
Removing a dummy linux/syscalls.h.
checking for kernel linux/firmware.h... "yes"
checking for exported symbol dump_stack... grep: /lib/modules/2.6.24-23-generic/build/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... i586
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "no"
checking for snprintf... "no"
checking for vsnprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for msleep... "no"
checking for tty->count is the atomic type... "no"
checking for io_remap_pfn_range... "no"
checking for new io_remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
Removing local linux/pnp.h.
checking for driver version... 1.0.9
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... configure: error: Unknown soundcard I82801DBICH4

---

### Post by Darth Buh on 2009-03-29
I found out what was going on with mine-

I had changed the command line to take PulseAudio out!

The way I got it running without having to backup the version was adding 'padsp' without the quotations in the command line prior to wine.

Mine looks like:

env WINEPREFIX="/home/***/.wine" padsp wine "C:\Program Files\World of Warcraft\Wow.exe"

And it runs fine now.

DB

-p.s. This is what I used to do to get Ventrilo and WoW running at the same time and not overlap one another.

---

