---
title: "firewire audio broken after upgrade to 13.10"
date: 2013-11-04
forum: Ubuntu Studio
---

### Post by Bartje on 2013-11-04
Hi all,

seems like the upgrade to 13.10 has broken quite a bit on my system :( .

I have an audiofire12 which stopped working.

Using ffado-diag, I get somthing which says that the new stack is present, but not loaded, nor active. How can I activate it? I've been reading about it and trying out different options, blacklisting old stack things without even knowing which is old or new or even present in ubuntustudio 13.10... Anyhow, I've been busy for half a day now... time to ask for help :-).

This is what ffado-diag tells me:

FFADO diagnostic utility 2.1.9999-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 3.11.0-11-lowlatency
    Preempt (low latency)... True
    RT patched.............. False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... False
  new 1394 stack active..... False
  /dev/raw1394 node present. False
  User IDs:
UID=1000(bart) GID=1000(bart) groepen=1000(bart),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),33(www-data),44(video),46(plugdev),100(users),103(syslog),107(scanner),109(lpadmin),123(sambashare),124(debian-tor),128(vboxusers),65534(nogroup)
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.8.1-10ubuntu8) 4.8.1
   g++ ............... g++ (Ubuntu/Linaro 4.8.1-10ubuntu8) 4.8.1
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.10.3 for Qt version 4.8.4
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags ........... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable                                                                                                           
No package 'libraw1394' found                                                                                                                         
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.                                                                
Perhaps you should add the directory containing `libavc1394.pc'                                                                                       
to the PKG_CONFIG_PATH environment variable                                                                                                           
No package 'libavc1394' found
     flags ........... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags ........... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags ........... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1 ............ 1.6.12
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.7.2-20ubuntu1) 4.7.2
   g++ ............... g++ (Ubuntu/Linaro 4.7.2-20ubuntu1) 4.7.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.9.6 for Qt version 4.8.3
   jackd ............. sh: 1: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.9
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.34.2
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  
   dbus-1 ............ 1.6.8
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 uname -a...
   Linux bart-PC 3.11.0-11-lowlatency #4-Ubuntu SMP PREEMPT Wed Oct 2 22:48:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 Hardware...
   Host controllers:
   CPU info:
Architecture:          x86_64
CPU-modus(sen):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Draden per kern:       2
Kern(en) per voet:     4
Socket(s):             1
NUMA-node(s):          1
Producent-ID:          GenuineIntel
CPU-familie:           6
Model:                 42
Stepping:              7
CPU-frequentie (MHz):  1600.000
BogoMIPS:              6784.27
Virtualisatie:         VT-x
L1d-cache:             32K
L1i-cache:             32K
L2-cache:              256K
L3-cache:              8192K
NUMA node0 CPU(s):     0-7
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [24, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count: [362, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    4: PID:  None, count: [4, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count: [1, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   16: PID:  None, count: [6613, 4599, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['nvidia']
 IRQ   17: PID:  None, count: [179, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['snd_hda_intel']
 IRQ   18: PID:  None, count: [379564, 0, 374, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1']
 IRQ   19: PID:  None, count: [10282, 0, 215002, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ata_piix', 'ata_piix']
 IRQ   23: PID:  None, count: [225, 3100, 0, 38, 0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   42: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   43: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   44: PID:  None, count: [68, 34123, 0, 1815, 0, 0, 0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   45: PID:  None, count: [0, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['ahci']
 IRQ   46: PID:  None, count: [10, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['mei_me']
 IRQ   47: PID:  None, count: [604, 0, 0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['snd_hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

FireWire kernel stack not present. Please compile the kernel with 
FireWire support.

---

### Post by Bartje on 2013-11-06
really, nobody? 
Nobody seems to reply on IRC, nor on the ubuntustudio mailinglist, nor here. Does this mean that there is no solution at all?

I did a fresh install with ubuntustudio 13.10, still the same issue. I guess I'll have to revert back to 13.04!! :-(

---

### Post by CrocoDuck on 2013-11-07
Hi! Sorry for the late reply, but I had a crazy week... I was thinking about some issue with kernel modules loading. Could you repost the output of

```
lsmod
```

```
lsmod | grep firewire
```

My hope is that we just need to load the modules for the firewire hardware.

---

### Post by jejeman on 2013-11-07
Run
```
lspci -knn
```
see if there is firewire controler.

---

### Post by Bartje on 2013-11-10
Hi,

I'm sorry for the late reply too, had work to do too :-)

Thanks for the reply of course. I have tested a bit further, on another computer the devices do work and get connected, which is good, I can't afford another audiofire12 at the moment. It even worked on a live-usb-stick with ubuntustudio 13.10! I tried the same, with the same stick on my machine, and of course it does not work.

But it needs to work on my main machine of course.

I tried loading the modules with modprobe multiple times already, modprobe firewire-core results in nothing, but modprobe firewire-ohci then does show the new firewire stack to be loaded in ffado-diag, but not activated, and qjackctl keeps saying it can't start jack

My guess now is that I kept using the old firewire stack somehow, because I just did upgrades, not reïnstalling a new version of ubuntu from scratch. 
Now I did. 
My conclusion so far is that the new firewire stack doesn't support my firewire ports yet. But perhaps I'm making conclusions to quickly :-), I hope so.

Anyways, here the outputs of the commands you asked:


**output of lsmod:**

Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39815  1 
snd_hrtimer            12744  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               335327  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 38545  0 
bnep                   18036  2 
bluetooth             232685  10 bnep,rfcomm
binfmt_misc            17500  1 
usblp                  18111  0 
joydev                 17377  0 
snd_hda_codec_hdmi     36906  4 
wacom                  57412  0 
snd_usb_audio         140732  2 
snd_usbmidi_lib        24938  1 snd_usb_audio
coretemp               13355  0 
kvm_intel             137039  0 
kvm                   443215  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55440  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  7 
snd_hda_codec         136498  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
mxm_wmi                13021  0 
wmi                    19070  1 mxm_wmi
gpio_ich               13476  0 
snd                    68876  30 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
nvidia               9410995  82 
mac_hid                13205  0 
mei                    41158  0 
lpc_ich                17061  0 
lp                     17759  0 
soundcore              12680  1 snd
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
microcode              22881  0 
pata_acpi              13038  0 
hid_generic            12540  0 
ahci                   25731  0 
libahci                31364  1 ahci
usbhid                 47074  0 
r8169                  67466  0 
hid                   101289  2 hid_generic,usbhid
usb_storage            57204  2 


lsmod | grep firewire: shows nothing

**lspci -knn**

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
        Kernel driver in use: pcieport
00:01.1 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0105] (rev 09)
        Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:1c3a]
        Kernel driver in use: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:5006]
        Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:a102]
        Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
        Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
        Kernel driver in use: pcieport
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b5)
        Kernel driver in use: pcieport
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b5)
        Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:5006]
        Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation P67 Express Chipset Family LPC Controller [8086:1c46] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
        Kernel driver in use: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller [8086:1c00] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:b002]
        Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
00:1f.5 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller [8086:1c08] (rev 05)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:b002]
        Kernel driver in use: ata_piix
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GL [Quadro 600] [10de:0df8] (rev a1)
        Subsystem: NVIDIA Corporation Device [10de:0835]
        Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
        Subsystem: NVIDIA Corporation Device [10de:0835]
        Kernel driver in use: snd_hda_intel
02:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
        Subsystem: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023]
        Kernel driver in use: xhci_hcd
04:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
        Kernel driver in use: xhci_hcd
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
        Kernel driver in use: r8169
06:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE9172 SATA III 6Gb/s RAID Controller [1b4b:917a] (rev 11)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:b000]
        Kernel driver in use: ahci

I hope you can get something out of this.

---

### Post by CrocoDuck on 2013-11-10
I can't see your firewire controller in the output of lspci -knn. If I run it, for example, I found:

```

04:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]
    Subsystem: ASUSTeK Computer Inc. P5W DH Deluxe Motherboard [1043:815b]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

```

The first I think I would check now is your kernel configuration. Repost the output of this guy:

```
cat /boot/config-$(uname -r) | grep 1394
```

We will see if the new kernel includes the firewire support.

---

### Post by Bartje on 2013-11-10
ok,

what I find weird is that0 firewire works on a different computer but not on my main computer using the same live-usb. In this test the kernel used was the same one, so it has to include firewire support, otherwise it wouldn't work on my old machine either.


the output of cat /boot/config-$(uname -r) | grep 1394 is: 

# IEEE 1394 (FireWire) support
# Supported FireWire (IEEE 1394) Adapters
# CONFIG_PROVIDE_OHCI1394_DMA_INIT is not set

grtz,

Bart

---

### Post by jejeman on 2013-11-10
This looks like a hardware problem, not a driver problem. It does not show firewire controler.
Is the firewire card "on board" or as PCI card?
Check the BIOS if it shows the controler or on the POST screen.
I understand that it worked, but it maybe died. Check the PCI slot, pull card out - return it. Change the PCI slot, clean the card, slot etc. Try another firewire card.

Regardless of the driver (firewire stack, kernel config.) every piece of hardware must be shown in lspci.

---

### Post by Bartje on 2013-11-10
It does indeed seem like a hardware issue, though I'm not convinced yet. It's quite a coïncidence that it would break after an upgrade.

I've got an on board firewire port and two ports through a PCI-card. I've tested all ports, it would be an even bigger coïncidence if the on-board firewire port and the PCI-card ports are broken at the same time.

First thing I'm going to try is disable the firewire port on the motherboard in my BIOS, if I can. Perhaps the issue is having multiple ports, which causes a conflict..

---

### Post by CrocoDuck on 2013-11-10
Your kernel seems to include the support, also you have the  drivers and the modules. The device worked, so is compatible... But is  not showed in lspci... Enigmatic! 

> **Bartje said:**
> 
First thing I'm going to try is disable the firewire port on the motherboard in my BIOS, if I can. Perhaps the issue is having multiple ports, which causes a conflict..


Quack! Good idea. Let's see what happens.

---

### Post by Bartje on 2013-11-10
Ok,

I've got some more success here :-D

Changing the BIOS did not result in anything, but, now I removed the PCI-card and connected the cable to the onboard firewire port and guess what, the system now discovers firewire :-D. Jack is up and running!!! Hooraaay!!


My guess is that the broken PCI-card prevented the onboard port to be detected. 
Perhaps that's still something for the kernel-guys, or ffado-guys to fix in the drivers to fix :-p .

Thanks a lot for the help, I guess I can mark this as solved!!!!

---

