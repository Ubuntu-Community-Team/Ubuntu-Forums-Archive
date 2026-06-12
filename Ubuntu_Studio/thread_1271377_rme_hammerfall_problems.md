---
title: "rme hammerfall problems"
date: 2009-09-20
forum: Ubuntu Studio
---

### Post by jaskah on 2009-09-20
hello

i'm trying to get my rme hammerfall going on ubuntu 8.04. it was working before but i tried to upgrade to 9.04 and, with all the realtime kernel / sata disk problems, i decided go to back to 8.04.

anyways...

the card is not recognized on start up (red host light stays on). when i run hdsploader i get the following:

hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : HDA Intel at 0xfbff8000 irq 22

so, does this mean that not even the pci card is being recognized or what?

i've installed the following alsa files by hand from the alsa site:

alsa-driver-1.0.21
alsa-lib-1.0.21a
alsa-firmware-1.0.20

and from synaptic the following:
alsa-firmware-loaders 1.0.15
alsa-tools-gui 1.0.15

this is all running on a pentium machine with asus p5q motherboard.

thanks in advance for any help on this!

---

### Post by thorgal on 2009-09-21
you've got a Multiface and the light indicator is red ?

In this case, power off everything, and remove the power cable from your PC's power supply. Wait a bit and power on everything again. My Multiface II got stuck a few times when I experimented with suspend/resume (which I gave up on a long time ago by the way). It used to put the multiface in some funny state, that a simple rebooting would not fix. I always had to power off and unplug the power cable to get it reset properly.

---

### Post by jaskah on 2009-09-21
thanks for your reply.

> **thorgal said:**
> you've got a Multiface and the light indicator is red ?

right, the classic problem...which i've had (and solved) before.


> **thorgal said:**
> In this case, power off everything, and remove the power cable from your PC's power supply. Wait a bit and power on everything again. My Multiface II got stuck a few times when I experimented with suspend/resume (which I gave up on a long time ago by the way). It used to put the multiface in some funny state, that a simple rebooting would not fix. I always had to power off and unplug the power cable to get it reset properly.

i tried this but it didn't work. this is strange, as i've done a bit of checking and this kernel (2.6.24-24-rt) is reported to be working with the rme. and i've also done everything (re-insalling alsa) which i did before to get the hammerfall to work.

anyone else with this problem?

---

### Post by thorgal on 2009-09-21
check that your card is seen by your ssytem:

```

lspci

```

```

dmesg | grep -i hammer

```

```

lsmod | grep hdsp

```


I also had problems at times with 2.6.24 but that was because of the alsa version of the day. I now run alsa 1.0.21 (I think) and kernel 2.6.31-rt11. I moved away from 2.6.24 about 6 months ago (I ran 2.6.24 for about a year). The 2.6.31 kernel is quite an improvement for the desktop. The RT patch has still a few issues but nothing that screws up performances if you tune your IRQ priorities right.

---

### Post by jaskah on 2009-09-21
thanks for your reply.

> **thorgal said:**
> check that your card is seen by your ssytem:

```

lspci

```


when i run this i get the following:

jason@jason-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:00.0 Multimedia audio controller: Xilinx Corporation RME Hammerfall DSP (rev 35)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
jason@jason-desktop:~$ 

so, it looks as if the pci card is being recognized



> **thorgal said:**
> 
```

dmesg | grep -i hammer

```


here i get the following:

jason@jason-desktop:~$ dmesg | grep -i hammer
[   41.346787] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/rme9652/../../alsa-kernel/pci/rme9652/hdsp.c:5007: Hammerfall-DSP: unable to use IRQ 0
[   41.346812] RME Hammerfall DSP: probe of 0000:05:00.0 failed with error -16
jason@jason-desktop:~$ 

there is some problem here.



[QUOTE=thorgal;7983209]
```

lsmod | grep hdsp

```

and here i get:

jason@jason-desktop:~$ dmesg | grep -i hammer
[   41.346787] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/rme9652/../../alsa-kernel/pci/rme9652/hdsp.c:5007: Hammerfall-DSP: unable to use IRQ 0
[   41.346812] RME Hammerfall DSP: probe of 0000:05:00.0 failed with error -16
jason@jason-desktop:~$ lsmod | grep hdsp
snd_hdsp               52388  0 
snd_rawmidi            25632  2 snd_hdsp,snd_seq_midi
snd_pcm                78724  3 snd_hda_intel,snd_hdsp,snd_pcm_oss
snd_page_alloc         11400  3 snd_hda_intel,snd_hdsp,snd_pcm
snd_hwdep              10628  2 snd_hda_intel,snd_hdsp
snd                    57636  18 snd_hda_intel,snd_hdsp,snd_seq_dummy,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device,snd_hwdep
jason@jason-desktop:~$ 

any idea how i should proceed now? i haven't had these error messages before.

thanks again for your help, i appreciate it.

---

### Post by thorgal on 2009-09-21
try 

```

cat /proc/interrupts

```

and try to spot the IRQ of 'hdsp'

The error from dmesg is weird. IRQ 0 ?? does not look good to me. Chaneg the PCI slot if you want to experiment (hopefully, you have more than one PCI slot).

---

### Post by jaskah on 2009-09-21
> **thorgal said:**
> 
try 
```

cat /proc/interrupts

```
and try to spot the IRQ of 'hdsp'


i ran this and got:

jason@jason-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        447          1   IO-APIC-edge      timer
  1:         25         25   IO-APIC-edge      i8042
  4:          1          1   IO-APIC-edge    
  6:          3          2   IO-APIC-edge      floppy
  8:          2          5   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:       3081       3108   IO-APIC-edge      i8042
 16:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1, libata
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb4, uhci_hcd:usb7
 20:       1622       1613   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb8
 21:          5          8   IO-APIC-fasteoi   uhci_hcd:usb6, ohci1394
 22:        342        364   IO-APIC-fasteoi   HDA Intel
218:        422        417   PCI-MSI-edge      eth0
219:       4721       4681   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     228315     227957   Local timer interrupts
RES:        879        946   Rescheduling interrupts
CAL:       2294       2427   function call interrupts
TLB:        165        264   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
jason@jason-desktop:~$ 

don't see any hdsp indication here.


> **thorgal said:**
> 
The error from dmesg is weird. IRQ 0 ?? does not look good to me. Chaneg the PCI slot if you want to experiment (hopefully, you have more than one PCI slot).


i just tried to card on my laptop and it ran fine. if the card had been locked up (as sometimes has happened in the past) this would've unlocked it.

i will try your suggestion of switching the pci slot.

thanks again for your help.

---

### Post by jaskah on 2009-09-21
hello again

i re-plugged the pci card into its slot and now the rme gets recognized at start-up.

so, i think i must've jostled the pci card when i was changing a hard disc, and somehow knocked a pin from its slot.

thanks again for your help.

---

### Post by thorgal on 2009-09-21
great :)

---

