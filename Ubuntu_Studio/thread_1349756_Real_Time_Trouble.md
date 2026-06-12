---
title: "Real Time Trouble"
date: 2009-12-08
forum: Ubuntu Studio
---

### Post by Royke on 2009-12-08
I haven't been able to use rt for quite a while(feisty fawn) and no matter what (rt-kernel)i try, it always ends up with a sort of system hang. Mouse and keyboard is then responding very slowly. For this i even tried 64studio's multimediakernel and in 9.04 it works reasonable, but in Karmic with a newer multimediakernel or with UbuntuStudio's kernel its just the same as always. I am ready to throw this pc in the garbage, but maybe someone here can provide a sollution or at least some advice.

My pc is a fujitsuSiemens Scaleo p, core2duo 2*1.8GHz, 1gb ram. The motherboard is not really advanced and has not many expansionoptions, but it should be capable of running rt nevertheless.

---

### Post by AutoStatic on 2009-12-09
Hello Royke, could you provide some extra info?
[LIST]
[*]output of **lspci**
[*]output of **lsmod**
[*]what steps did you take to configure your system
[/LIST]

---

### Post by DerickX on 2009-12-09
Your system should be ok for pro audio usage (if the hardware is supported well).

Do you have just plain Ubuntu and installed a RT kernel? Did you some extra configuration? Or did you install Ubuntu Studio?

---

### Post by Royke on 2009-12-09
Hello AutoStatic and DerickX. 
Usually i just install Ubuntu from cd and later on upgrade to UbuntuStudio from the DVD. Every (upgrade-)time i tried just to install UbuntuStudio from dvd but always missed a few important things that are on the ubuntucd. Than i just redo the ubuntuinstallation with a clean partition. 
So if i understand you both: There is an important difference in the system configuration, which of course can be modified.:) Than i can better learn how to set it up rather than buying a new pc with new (kernel-)troubles. 

It maybe nice to know that after starting this thread i managed to setup realtime mode with JACKcontrol under the generic kernel, just by creating a new unprivileged user with access to audioprograms. 

Here is the output of lspci and lsmod from my 9.04 :

royke@RoyComputy:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
04:05.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
:KS
royke@RoyComputy:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
video                  25872  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
saa7134_alsa           20000  0 
tuner_simple           22544  1 
tuner_types            22400  1 tuner_simple
tea5767                14852  0 
tuner                  32836  0 
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
iptable_nat            13700  0 
snd_seq_dummy          10756  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
iptable_mangle         10880  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
saa7134               152020  1 saa7134_alsa
iptable_filter         10752  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              52228  1 saa7134
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
videodev               41600  2 tuner,saa7134
x_tables               23044  2 iptable_nat,ip_tables
snd                    62756  17 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            21764  1 videodev
compat_ioctl32          9344  1 saa7134
v4l2_common            20992  2 tuner,saa7134
videobuf_dma_sg        20484  2 saa7134_alsa,saa7134
videobuf_core          26500  2 saa7134,videobuf_dma_sg
soundcore              15200  1 snd
via_agp                16256  1 
nvidia               7233756  0 
psmouse                61972  0 
tveeprom               20100  1 saa7134
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_viapro             15892  0 
shpchp                 40212  0 
agpgart                42696  2 via_agp,nvidia
serio_raw              13444  0 
pcspkr                 10496  0 
joydev                 18368  0 
ndiswrapper           193436  0 
hid_ezkey               9856  0 
usbhid                 42336  0 
usb_storage            99648  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
via_rhine              30856  0 
mii                    13312  1 via_rhine
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
royke@RoyComputy:~$ thanks for the help!
bash: thanks: command not found
royke@RoyComputy:~$

---

### Post by AutoStatic on 2009-12-10
Hello Royke, thanks for the info! And the current generic kernel is indeed pretty good when it comes to realtime stuff so you could also just stick to that kernel. What soundcard are you using, the onboard card? And are you using a PS/2 mouse and keyboard or USB ones? Did you try disabling the firewall? And I see you're using ndiswrapper, there's no driver available for your wireless device?

---

### Post by Royke on 2009-12-10
Hello AutoStatic. With your questions i realize that there are a lot of option i can try. The soundcard it that crappy VIA alc888 hd onboard thing for now. I may one time blow it up with a jack-shortcircuit, try bothways connecting VU-meter:D
At first i will test playing guitar with some jackrack effects without the direct inputsound :guitar: , now that jack runs ok in the generic kernel, there should be some improvement in the timing and to me that says more than a running rt with maybe other problems. The 9.04 generic and karmic too are both running well. The wlan is a WG111v3 usb(rtl8187)and works in karmic out of the box now, after the first updates it's ok i found out. The mouse & keyboard are usb. I have connected them through a usb hub which is v1.1. 
I will try some adjustments in the setup this weekend and hopefully i can learn more. It's great to get help this way, at least now i have something to work on, thanks again!

---

### Post by Royke on 2009-12-16
Hello people,
The real time kernel is still not running here. I removed the usb 1.1 hub from my machine and connected mouse and keyboard directly, changed some other settings, but it's still the same. Maybe i should build my own kernel for this machine, but i don't like it. My feeling says that it will just have the same result. And when i'm ready with that it's proberbly almost april next year. I just want to mix my instruments to the line-in and then process the sound with the great ubuntustudio tools. When i finally succeed i want to also use this way for live-performance. Jack is working in rt now under the generic kernel, but the timing is still too slow for it.(maybe i am goïng to destroy this machine, it gave me headache's enough)

@ AutoStatic 

It's great to see an entire website devoted to linux-audio in my language!
I am working through it, step by step. Maybe i will learn enough now. 

I am not goïng to give up on this: real time for everyone!! :guitar:

---

### Post by AutoStatic on 2009-12-16
> **Royke said:**
> Hello people,
The real time kernel is still not running here. I removed the usb 1.1 hub from my machine and connected mouse and keyboard directly, changed some other settings, but it's still the same. Maybe i should build my own kernel for this machine, but i don't like it. My feeling says that it will just have the same result. And when i'm ready with that it's proberbly almost april next year. I just want to mix my instruments to the line-in and then process the sound with the great ubuntustudio tools. When i finally succeed i want to also use this way for live-performance. Jack is working in rt now under the generic kernel, but the timing is still too slow for it.(maybe i am goïng to destroy this machine, it gave me headache's enough)Personally I think there's no need to compile your own kernel. It has to be something else. What do you mean by the way with "it always ends up with a sort of system hang"? What happens exactly when the system supposedly hangs? And the PC has an Intel CPU so CPU frequency scaling is probably enabled. Did you try disabling that service, the Ondemand service? You might need the package **BootUp-Manager** to do so. Be very careful with that one though.

> **Royke said:**
> I am not goïng to give up on this: real time for everyone!! :guitar:It can be done with your current setup, I'm sure!

---

### Post by Royke on 2009-12-19
> What do you mean by the way with "it always ends up with a sort of system hang"? What happens exactly when the system supposedly hangs?

I try to describe it as good as possible: Sometimes after a few minutes, sometimes after a few seconds, but it always happens when i run rt, the mousemovements and keystrokes suddenly responds very slowly in a shocky way. It than ends up with me turning the computer off out of dispare, because there's no way to use the system when this happens. All the other stuff seems to work. I tested this by running programs after this shocky mouse/keyboard movement-thing happens. Even music keeps on playing with jack and without xruns. It seems to be a controller problem(??)

---

### Post by AutoStatic on 2009-12-19
Could you post the outcome of **cat /proc/interrupts** and **lsusb** ? And what if you plug the USB keyboard and mouse in another USB port?

---

### Post by Royke on 2009-12-23
Hello AutoStatic,
Here's the output of cat /proc/interrupts and lsusb:

roy@RoyComputy:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        132          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  6:          2          0   IO-APIC-edge      floppy
  8:          0          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      pata_via
 15:     317637          0   IO-APIC-edge      pata_via
 17:     116820          0   IO-APIC-fasteoi   HDA Intel
 18:        313          0   IO-APIC-fasteoi   saa7134[0], saa7134[0]
 19:          2          0   IO-APIC-fasteoi   ohci1394
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 21:    9396198          0   IO-APIC-fasteoi   sata_via, ehci_hcd:usb1, uhci_hcd:usb4
 22:         66          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:         53          0   IO-APIC-fasteoi   uhci_hcd:usb5
NMI:          0          0   Non-maskable interrupts
LOC:    2780083    2123980   Local timer interrupts
RES:      27027      34464   Rescheduling interrupts
CAL:         46         97   Function call interrupts
TLB:       4161       5807   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

roy@RoyComputy:~$ lsusb
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 003: ID 07b8:e004 D-Link Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0518:0002 EzKEY Corp. EZ-9900C Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
roy@RoyComputy:~$ 

After i started rt again to wait for the shocky mouse/keyboard movement-thing to happen i unplugged the mouse and keyboard and plugged the mouse in an other usb slot. I did try this before but is was when i had them connected through an usb1.1 hub which i now have removed. I can't believe it and don't really understand: it is working!! :guitar: :lolflag: :popcorn:

Only there has rised up a new problem: The soundcard gets crazy. System event sounds keeps repeating endlessly. It looks like the problem has shifted. I understand(hopefully) that it may has something to do with IRQ-settings but am a bit afraid to mess with it. 
I will try to turn the onboard card off and use an older creative card(have plenty) if i have another pci slot with room for card(must check). If this won't work i can easily switch back.

As soon as i tryed out i will report here and i now have the time to work on it more. Thanks so much for your help, AutoStatic.

I still can't believe how simple: plugging mouse in another slot :rolleyes:

---

### Post by AutoStatic on 2009-12-23
Great that it doesn't hang anymore! You don't have to mess around with IRQ settings, the onboard soundcard has an IRQ of it's own so that's not the problem I think. You could try improving the situation on IRQ 21, it is shared by two USB ports and your SATA controller. And on those USB ports (1 and 4) you have a lot of stuff hooked up:
_Port 1_
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 003: ID 07b8:e004 D-Link Corp. Mass Storage Device

_Port 4_
Bus 004 Device 002: ID 0461:4d16 Primax Electronics, Ltd 

So maybe when you plug these devices in other USB ports (like 2 and 5) you could tweak your system a bit more. You can check in which port a device is plugged in by checking with lsusb, Bus 00x = port x = usbx (usbx => cat /proc/interrupts). I have no clue where the stuttering of your system sounds comes from, could be a driver setting, not sure.

---

### Post by Royke on 2010-02-27
Hello,

There is a few reasons why i didn´t respond sooner, but the main reason is that i could not reproduce my error when installing rt. Now i have found it in the bios. It is IOAPIC what is causing my pc to act strange when using rt. If i switch it to enable my soundcard stutters again and the system is very unstable. So i disabled it. When Ubuntu starts to load i can see a little error about APIC, but it works better than ever now!
For the rest i have now my system tuned for audio thanks to AutoStatic's clear explanation on  and i have disconnected my usb wlan which improves performance more than i thought it would. I have a new isp so connect through a cable again.  After some updates, escpecially Hydrogen and using the qjackctl patchbay the programs are pretty stable too! I am now working on automating the whole connection setup. When i put pc on grub loads 9.04 with auto login and qjackctl autostarts with a startupscript for connecting the line-input to other programs. It is getting better every day now that i finally have setup my system the right way. This has made me a more happy person again and it's good to know to have a better latency than a more than average expensive appie; this only took time to learn and now i'm even ready to help some friends to set their system up!

---

