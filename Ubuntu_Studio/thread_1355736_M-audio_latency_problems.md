---
title: "M-audio latency problems"
date: 2009-12-15
forum: Ubuntu Studio
---

### Post by garyed on 2009-12-15
I don't expect any solutions but I'm trying to find out if this is a common problem with my sound card (M-audio Audiophile 2496) & U-studio 9.10.
I used to run U-Studio 7.10 Gusty & set Jack at 5.9ms latency & could do as many audio tracks as I wanted in Ardour with no Xruns. I heard that 8.04 was not as solid as 7.10 so I never upgraded. I finally tried 9.10 & all kinds of xruns at 5.9ms & even at higher latencies. I copied my audio setup from Gusty to be sure. Someone else on the Ardour forums had similar problems with ICE1712 chips & attributed it to the Kernel which I tend to agree with. I tried U-studio 9.10- 64 ext4 & also the standard version on ext3 with the same poor results.
Just wondering if anyone else has had this experience.

---

### Post by tgalati4 on 2009-12-15
No pulseaudio in  gutsy.  I  would try to disable pulse.  Or, use dynebolic live cd for your recording sessions.

---

### Post by garyed on 2009-12-15
I completely removed pulseaudio & it didn't help.
I tried to install 64 Studio to see if it would be any better but it messed up grub where I couldn't boot up at all so I never got to try it.

---

### Post by tgalati4 on 2009-12-18
cat /proc/interrupts

Perhaps you have another device that is sharing the sound card interrupt.  Post the output of the above command.

---

### Post by garyed on 2009-12-18
> **tgalati4 said:**
> cat /proc/interrupts

Perhaps you have another device that is sharing the sound card interrupt.  Post the output of the above command.

I use the ICE1712 (m-audio audiophile 2496) for all my recording
The onboard sound is turned off in the bios but it still shows up.
I also have an SBlive for some midi stuff. 

> 
           CPU0       
  0:        185   IO-APIC-edge      timer
  1:        171   IO-APIC-edge      i8042
  3:          2   IO-APIC-edge    
  4:          2   IO-APIC-edge    
  6:          4   IO-APIC-edge      floppy
  7:          1   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:      22753   IO-APIC-edge      i8042
 14:       7426   IO-APIC-edge      ide0
 15:      19197   IO-APIC-edge      ide1
 16:         44   IO-APIC-fasteoi   firewire_ohci
 17:       3161   IO-APIC-fasteoi   eth0, EMU10K1
 18:          0   IO-APIC-fasteoi   sata_promise, ICE1712
 20:         55   IO-APIC-fasteoi   sata_via
 21:          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5
 22:          0   IO-APIC-fasteoi   VIA8237
NMI:          0   Non-maskable interrupts
LOC:     168291   Local timer interrupts
CNT:          0   Performance counter interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
SPU:          0   Spurious interrupts
ERR:          1
MIS:          0



---

### Post by AutoStatic on 2009-12-18
```
18: 0 IO-APIC-fasteoi sata_promise, ICE1712
```It shares an interrupt with a SATA controller. Do you use that controller? Or do you use the VIA one? Otherwise you could try blacklisting the sata_promise or **modprobe -r** it.

---

### Post by GodLikeCreature on 2009-12-18
> **garyed said:**
> I don't expect any solutions but I'm trying to find out if this is a common problem with my sound card (M-audio Audiophile 2496) & U-studio 9.10.
I used to run U-Studio 7.10 Gusty & set Jack at 5.9ms latency & could do as many audio tracks as I wanted in Ardour with no Xruns. I heard that 8.04 was not as solid as 7.10 so I never upgraded. I finally tried 9.10 & all kinds of xruns at 5.9ms & even at higher latencies. I copied my audio setup from Gusty to be sure. Someone else on the Ardour forums had similar problems with ICE1712 chips & attributed it to the Kernel which I tend to agree with. I tried U-studio 9.10- 64 ext4 & also the standard version on ext3 with the same poor results.
Just wondering if anyone else has had this experience.

I have the same with my M-Audio 1010LT (ICE1712 chip).  I use UU 9.04 and I am happy with the results, but I do get Xruns as well.    I am OK with them for the most part, because with the exception of recording drums, I hardly ever record more than two tracks at once.

Having said so, Xruns happen randomly, mostly when starting Hydrogen or Ardour, but hardly when I am using them.  I can record my 16 drum tracks all through a 6 minute song with no Xruns whatsoever, then get Xruns for no reason while I am mixing something...  

STRANGE!

---

### Post by tgalati4 on 2009-12-18
Turn off the parallel port, floppy, serial port in the BIOS.  You need to free up interrupts.  Your sound card needs a dedicated interrupt.

---

### Post by garyed on 2009-12-18
> **AutoStatic said:**
> ```
18: 0 IO-APIC-fasteoi sata_promise, ICE1712
```It shares an interrupt with a SATA controller. Do you use that controller? Or do you use the VIA one? Otherwise you could try blacklisting the sata_promise or **modprobe -r** it.
 
Could you give me the code on how to do it?
Also it shares the same interrupt on U-Studio Gusty but I don't have the problem there. I also don't know how to tell if I using the SATA or VIA controller. One of them I think is for RAID which I don't use. 
I do have one SATA HD on the computer.

---

### Post by garyed on 2009-12-18
> **tgalati4 said:**
> Turn off the parallel port, floppy, serial port in the BIOS.  You need to free up interrupts.  Your sound card needs a dedicated interrupt.
Even if I can free up an interrupt how can I force the Audiophile to use the open one?

---

### Post by tgalati4 on 2009-12-20
The kernel and HAL control interrupt assignment.  You can also dedicate interrupt assignment through tthe BIOS.

---

### Post by AutoStatic on 2009-12-20
> **garyed said:**
> Could you give me the code on how to do it?
Also it shares the same interrupt on U-Studio Gusty but I don't have the problem there. I also don't know how to tell if I using the SATA or VIA controller. One of them I think is for RAID which I don't use. 
I do have one SATA HD on the computer.What's the outcome of **lsmod** ?

---

### Post by tgalati4 on 2009-12-20
Step by step:

Go into BIOS at bootup.  (Del, Esc, F10, F2, whatever is required to get into BIOS)

Turn off serial port, parallel port, floppy

Save changes

Reboot into Ubuntu

Open a terminal 

cat /proc/interrupts

If the M-Audio card still shares an interrupt, shut down the machine.  Physically move the card to a different PCI slot.

Reboot

cat /proc/interrupts

---

### Post by garyed on 2009-12-20
> **AutoStatic said:**
> What's the outcome of **lsmod** ?

Here's the out put of lsmod:

>  Module                  Size  Used by
binfmt_misc            10300  1 
snd_ice1712            68292  0 
snd_ice17xx_ak4xxx      4432  1 snd_ice1712
snd_ak4xxx_adda         9456  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_emu10k1_synth       7280  0 
snd_via82xx            28444  0 
snd_emux_synth         39344  1 snd_emu10k1_synth
snd_seq_virmidi         7920  1 snd_emux_synth
snd_seq_midi_emul       8208  1 snd_emux_synth
snd_pcm_oss            45024  0 
snd_via82xx_modem      13948  0 
snd_emu10k1           153696  1 snd_emu10k1_synth
snd_cs8427              9488  1 snd_ice1712
snd_mixer_oss          19728  1 snd_pcm_oss
snd_ac97_codec        125752  4 snd_ice1712,snd_via82xx,snd_via82xx_modem,snd_emu10k1
ac97_bus                2160  1 snd_ac97_codec
snd_util_mem            5264  2 snd_emux_synth,snd_emu10k1
snd_pcm                91960  6 snd_ice1712,snd_via82xx,snd_pcm_oss,snd_via82xx_modem,snd_emu10k1,snd_ac97_codec
snd_i2c                 6704  2 snd_ice1712,snd_cs8427
snd_seq_dummy           3540  0 
snd_hwdep               9560  2 snd_emux_synth,snd_emu10k1
snd_mpu401_uart         8720  2 snd_ice1712,snd_via82xx
snd_seq_oss            33920  0 
snd_seq_midi            8448  0 
snd_rawmidi            27232  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
iptable_filter          3856  0 
snd_seq_midi_event      8656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                61664  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              21152  1 iptable_filter
snd_timer              27000  3 snd_emu10k1,snd_pcm,snd_seq
x_tables               26680  1 ip_tables
snd_seq_device          8484  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
emu10k1_gp              3344  0 
nvidia               8100720  0 
gameport               14400  3 snd_via82xx,emu10k1_gp
ppdev                   8376  0 
snd                    79496  21 snd_ice1712,snd_ak4xxx_adda,snd_via82xx,snd_emux_synth,snd_seq_virmidi,snd_pcm_oss,snd_via82xx_modem,snd_emu10k1,snd_cs8427,snd_mixer_oss,snd_ac97_codec,snd_pcm,snd_i2c,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11072  4 snd_via82xx,snd_via82xx_modem,snd_emu10k1,snd_pcm
i2c_viapro              8904  0 
k8temp                  5712  0 
amd64_edac_mod         26944  0 
lp                     12740  0 
edac_core              49916  3 amd64_edac_mod
shpchp                 38220  0 
parport_pc             37384  1 
soundcore              10080  1 snd
psmouse                57460  0 
serio_raw               6772  0 
parport                41484  3 ppdev,lp,parport_pc
dm_raid45              79032  0 
xor                     5760  1 dm_raid45
ohci1394               34500  0 
skge                   45280  0 
ieee1394              102048  1 ohci1394
sata_via               12244  0 
floppy                 66024  0 



---

### Post by garyed on 2009-12-20
> **tgalati4 said:**
> Step by step:

Go into BIOS at bootup.  (Del, Esc, F10, F2, whatever is required to get into BIOS)

Turn off serial port, parallel port, floppy

Save changes

Reboot into Ubuntu

Open a terminal 

cat /proc/interrupts

If the M-Audio card still shares an interrupt, shut down the machine.  Physically move the card to a different PCI slot.

Reboot

cat /proc/interrupts

I removed serial & paralell ports in the BIOS & rebooted but it still shares an interrupt with my SATA controller.
I had to go through the moving the card in Windows & I've got it where it works perfectly in XP & Ubuntu 7.10(Gusty). In Gusty it shares the same interrupt with no problem on the same drive just a different partition so I think there's something else going on. Someone in the Ardour forum had the same problem with newer versions of U-studio & the same sound chip
(ICE1712) & they narrowed it down to the kernel. Theirs worked fine with older kernels too.

---

### Post by RaumTrug on 2009-12-20
hi! I've got an M2496, too, and get it working < 2ms even with the generic Kernel from a standard ubuntu install and no other tuning than the standard limits.conf stuff relatively "stable" (connecting/unconnecting causes xruns sometimes, as well as expensive effects, of course), and it's a way old pc! -maybe because it's old and 32bit only, the kernel prob. could be connected to the 64bit build, and you might want to try a 32bit version...? or well, eh better not...

I'd still try to give the "irq unsharing" a try, with good mainboards/bioses you can assign irqs to the individual pci slots: look through your bios wether it has such an option, and look onto your mainboard/into your mainboard docs what number the slot has where the card is plugged!

also try turning off compiz (just select no desktop effects in the user preferences).

what can be even more important is that you turn off cpu frequency ondemand scaling - as you've been quite happy with 7.10 and the problems began with 9.10 that could be the sollution, as this "feature" has been improved with 9.10 to make laptop users happy ;). in this forum there's a thread on how to turn it off somewhere...

ultimately I've heard that VIA mainboard chipsets are particularly quirky for realtime performance, but as it worked with 7.10 I doubt that would be the main problem, it's just rumors, you see...

---

