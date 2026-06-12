---
title: "Which Realtime Kernel?"
date: 2010-09-13
forum: Ubuntu Studio
---

### Post by siabost on 2010-09-13
Hi,
Compaq Pressario R3000 laptop,
2.8Ghz Celeron Processor, 1.5Gb Memory.

A couple of years ago I used Ubuntu Studio then moved to 64Studio and now I'm back with Ubuntu Studio 10.04 32bit.

In the "olden" days I seem to recall that Ubuntu Studio shipped with an RT kernel or at least an up-to-date RT option was available soon after initial release of the OS. Is this no longer the case?

Currently I'm using the standard 2.6.32-25-generic kernel with Xubuntu-desktop loaded on top of the standard Ubuntu Studio set-up. The set-up works well but would work better with a Realtime kernel.

I notice there are a number of RT kernels available via PPAs - which one is best? And is there an "official" one available or due?

I'm a little wary of installing from a PPA something as fundamental as a kernel without recommendation/advice.

Many thanks.

---

### Post by lykeion on 2010-09-13
The official rt-kernel in Lucid is linux-image-2.6.31-10-rt
I thought that this was installed with UbuntuStudio. Is it not listed in the Grub menu? 
Otherwise you should be able to install it with
```
sudo apt-get install linux-rt
```
Thera are some PPA repos you can use, read more here:
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

---

### Post by AutoStatic on 2010-09-13
> **lykeion said:**
> The official rt-kernel in Lucid is linux-image-2.6.31-10-rt2.6.31-11-rt has been released a while ago. This is a fairly decent realtime kernel and I think it is best to stick with this one.

---

### Post by sosaudio1 on 2010-09-13
> **lykeion said:**
> The official rt-kernel in Lucid is linux-image-2.6.31-10-rt
I thought that this was installed with UbuntuStudio. Is it not listed in the Grub menu? 
Otherwise you should be able to install it with
```
sudo apt-get install linux-rt
```
Thera are some PPA repos you can use, read more here:
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

I added the PPA that was mentioned here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

If there are any better, I would like to know as well.

Rich

---

### Post by sosaudio1 on 2010-09-13
> **AutoStatic said:**
> 2.6.31-11-rt has been released a while ago. This is a fairly decent realtime kernel and I think it is best to stick with this one.


That is the one I am running as well...are there any tweaks needed to get optimal performance out of it, or did you just install it and run...

---

### Post by Pablo_F on 2010-09-13
> are there any tweaks needed to get optimal performance out of it, or did you just install it and run... 

Afaik, with the generic kernel you cannot prioritize the so-called "kernel threads" by means of the chrt command. With the rt kernel, yes you can. And you should in order to take advantage of it.

There is a script by the great Rui Nuno Capela (author of qtractor, qjackctl, qsynth...) that raises the desired hardware priorities automagically at boot. You install the ubuntu package rtirq-init and edit the conf file, "/etc/default/rtirq", depending on your hardware (see "cat /proc/interrupts")

See  [http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107)

(Rui refers to /etc/sysconfig/rtirq as the conf file. It must be so in Fedora, I think)

You can use htop to check the priorities (you need to set it up to not hide kernel threads). Or use the ps command as Trulan suggests.

Cheers! Pablo

---

### Post by sosaudio1 on 2010-09-13
> **Pablo_F said:**
> Afaik, with the generic kernel you cannot prioritize the so-called "kernel threads" by means of the chrt command. With the rt kernel, yes you can. And you should in order to take advantage of it.

There is a script by the great Rui Nuno Capela (author of qtractor, qjackctl, qsynth...) that raises the desired hardware priorities automagically at boot. You install the ubuntu package rtirq-init and edit the conf file, "/etc/default/rtirq", depending on your hardware (see "cat /proc/interrupts")

See  [http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107)

(Rui refers to /etc/sysconfig/rtirq as the conf file. It must be so in Fedora, I think)

You can use htop to check the priorities (you need to set it up to not hide kernel threads). Or use the ps command as Trulan suggests.

Cheers! Pablo

since I use my box for not only audio but video, should I add nvidia to the RTIRQ list?

---

### Post by sosaudio1 on 2010-09-13
Does this look like I am firing on all cylinders?


ps -e | grep timer
    5 ?        00:00:00 sirq-timer/0
   11 ?        00:00:00 sirq-hrtimer/0

cat /proc/interrupts
           CPU0       
  0:        163   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge    
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:      11062   IO-APIC-edge      ata_piix
 15:       7509   IO-APIC-edge      ata_piix
 16:         58   IO-APIC-fasteoi   uhci_hcd:usb2
 17:      38464   IO-APIC-fasteoi   eth0, Intel 82801DB-ICH4, nvidia
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:       6790   IO-APIC-fasteoi   uhci_hcd:usb3
 23:          4   IO-APIC-fasteoi   ehci_hcd:usb1
NMI:          0   Non-maskable interrupts
LOC:     566597   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          2   Machine check polls
ERR:          0
MIS:          0


I have since changed my rtirq /etc/default to

RTIRQ_NAME_LIST="rtc0 Intel usb i8042"

this was from:

RTIRQ_NAME_LIST="rtc snd usb i8042"

I have also commented out:

# On kernel configurations that support it,
# which services should be NOT threaded 
# (space separated list).
#RTIRQ_NON_THREADED="rtc snd"

since it sounds like this is not necessary...to a point.

Lemmie know if I should change anything.

Yes....I am trying to squeeze as much out of this turnip as possible...LOL

Rich

---

### Post by sosaudio1 on 2010-09-13
Here is my lspci -v

The concern I have is that I am running the nVidia GS8400 which is supposed to be great and I get a slight jitter in applications where things are animating...such as cursor busy for example. Now it is not a big noticeable problem. but in videos and in scrolling of say the terminal windows, it sort of is....it is almost as if something is polling and then letting go....

Any tweaks would be great.....oh and yes, I realize where I am posting this. I want to see if the RT kernel has any affect on video performance..also...dont want to double post. 

Mods feel free to move this to a place that it needs to go and re-title it as you see fit just so we all can benefit from knowledge obtained in both arenas.  

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
	Subsystem: Dell Device 0160
	Flags: bus master, fast devsel, latency 0
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: [e4] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
	Subsystem: Dell Device 0160
	Flags: fast devsel, IRQ 11
	Memory at c0000000 (32-bit, prefetchable) [disabled] [size=128M]
	Memory at feb80000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: [d0] Power Management version 1

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 0160
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 0160
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 0160
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 0160
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: d0000000-efffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 0160
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Dell Device 0160
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Device 0160
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
	Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:05.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at d0000000 (64-bit, prefetchable) [size=64K]
	Bus: primary=01, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-fe8fffff
	Prefetchable memory behind bridge: d0100000-efffffff
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [60] Express PCI/PCI-X to PCI-Express Bridge, MSI 00
	Kernel modules: shpchp

01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
	Subsystem: Dell Device 8127
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at fe9fe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at d0010000 [disabled] [size=16K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: b44
	Kernel modules: b44

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
	Subsystem: Device 196e:05cf
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at df00 [size=128]
	[virtual] Expansion ROM at fe800000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidia-173, nvidiafb


Thanks
Rich

---

### Post by AutoStatic on 2010-09-14
> **sosaudio1 said:**
> That is the one I am running as well...are there any tweaks needed to get optimal performance out of it, or did you just install it and run...[http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)
Especially the items on CPU scaling and priorities.

---

### Post by siabost on 2010-09-14
):P
Thanks for all the help.

I installed 2.6.31-11-rt successfully &, after familiarising myself with Grub2, set it up so I get to see the grub menu at boot and can choose the rt kernel or the generic as required - best of both worlds.

This thread has certainly sprouted: I hadn't realised you could tune the RT kernel's priorities - will investigate.

As an additional question, can anyone recommend a USB or Firewire multi-channel soundcard that works well with Linux but doesn't cost the earth? Or, failing that, a simple mic in/line in/line out type with decent sound quality?

This being a laptop, any extras have to be external.

Thanks.

---

### Post by Pablo_F on 2010-09-15
A friend of mine is using the Edirol FA-66 wit success. But any firewire card tagged with "Full support" in the ffado site[1] should work.

[1] [http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)

Make sure you have a compatible firewire controller.

[http://www.ffado.org/?q=node/251](http://www.ffado.org/?q=node/251)

---

### Post by siabost on 2010-09-16
Thanks Pablo_F,

lshw throws up this for my Firewire:
>            *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:d0206000-d02067ff memory:d0200000-d0203fff

I will check the links when I get home.

---

### Post by maghoxfr on 2010-09-16
> **AutoStatic said:**
> 2.6.31-11-rt has been released a while ago. This is a fairly decent realtime kernel and I think it is best to stick with this one.

I'm kind of retired from the "civilized world" this days so I'm kind of passive about searching for info.

Great to know that 2.6.31-11-rt is out, I'll give it a try tomorrow. Thanks for the good news ;)

---

### Post by siabost on 2010-09-17
Hiya,

After further investigation I'm not sure whether to go firewire or USB2 re an external soundcard for my laptop - the hardware list below also shows USB1 so I'm a bit confused as to which I've got i.e. USB1.1 or USB2?
The speeds quoted at the ffado indicate that my firewire (1394a-2000) is slower than USB2 which I also appear to have.

How hard is it to find a USB2 standards compliant soundcard for use on Linux?

Currently with my M-audio MIDI keyboard plugged in via USB & playing live I get a crackle/brief interruption in play while controlling Zynaddsubfx 2.4.0. Is this a function of trying to play it via USB? I don't recall this occurring with a direct MIDI connection via soundcard on a Desktop PC.

Thanks.

Edited highlights of ```
lshw
```

>     description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 1381MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.9
          size: 2800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
       *-usb:0
             description: USB Controller
             product: OHCI USB Controller #1
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:d0001000-d0001fff
        *-usb:1
             description: USB Controller
             product: OHCI USB Controller #2
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:d0002000-d0002fff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:d0206000-d02067ff memory:d0200000-d0203fff
   *-generic UNCLAIMED
                description: System peripheral
                product: PCI1620 Firmware Loading Function
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:02:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=7
                resources: ioport:a400(size=64)
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
                resources: irq:16 memory:d0204000-d0204fff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 7.1
                bus info: pci@0000:02:07.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
                resources: irq:18 memory:d0205000-d0205fff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 7.2
                bus info: pci@0000:02:07.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16
                resources: irq:19 memory:d0206c00-d0206cff
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:5 memory:d0003000-d00030ff

---

### Post by AutoStatic on 2010-09-17
> **siabost said:**
> After further investigation I'm not sure whether to go firewire or USB2 re an external soundcard for my laptop - the hardware list below also shows USB1 so I'm a bit confused as to which I've got i.e. USB1.1 or USB2?
The speeds quoted at the ffado indicate that my firewire (1394a-2000) is slower than USB2 which I also appear to have.Go FireWire, really, it's much better for audio related things.

> **siabost said:**
> How hard is it to find a USB2 standards compliant soundcard for use on Linux?Hard. Afaik only 3 or 4 cards are fully supported.

> **siabost said:**
> Currently with my M-audio MIDI keyboard plugged in via USB & playing live I get a crackle/brief interruption in play while controlling Zynaddsubfx 2.4.0. Is this a function of trying to play it via USB?No, that'sthe relatively poor JACK and MIDI support of ZynAddSubFX. You might want to give Yoshimi a try, it's in my PPA. Yoshimi is a ZASFX fork with better JACK support and in the (near) future hopefully better MIDI support too.

---

### Post by siabost on 2010-09-17
Hi AutoStatic,

Downloaded Yoshimi from your PPA but I'm having a few problems.

Got the ZASFX instrument banks loaded into it but it crashes as soon as I try to use it's virtual keyboard - it doesn't react with the QUERTY keyboard either.

Connecting my M-audio MIDI keyboard was difficult too - initially Yoshimi showed only on the "output" side of the Audio Tab in Jack's connection panel. It showed on the "input" side on the MIDI tab & my keyboard on both "input" & "output" sides on the Alsa Tab. Thus I couldn't figure out a way to connect my keyboard to Yoshimi's midi-in.

Then I changed the MIDI driver in Jack settings from "none" to "raw". This allowed my keyboard to show on the "output" side of the MIDI tab under alsa_pcm and I could make a connection from that to Yoshimi's midi-in.

When I did though, Yoshimi crashed as soon as I pressed a key.

Any idea what I'm doing wrong?

Any help much appreciated.

---

