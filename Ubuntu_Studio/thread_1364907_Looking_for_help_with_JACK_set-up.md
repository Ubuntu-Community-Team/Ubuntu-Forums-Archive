---
title: "Looking for help with JACK set-up"
date: 2009-12-26
forum: Ubuntu Studio
---

### Post by Th3Professor on 2009-12-26
I've referred to:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

and:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

...but no luck so far.

My instrument set-up is:

Guitars, mics, & electronic drumset (as live audio instead of MIDI)
--> Mackie Onyx 1220i FireWire mixer

Mackie mixer
--> computer via firewire

M-Audio Axiom 49 USB/MIDI keyboard
--> computer via USB

Computer = Ubuntu Studio 9.10
(with studio controls enabled, priorities, memory adjusted, etc.)

The computer's running off a 64-bit CPU, though I don't think that matters much.

I'm starting out new on all of this Linux music production software and am currently hitting a roadblock with JACK. There are errors popping up in JACK's message window when I try various settings, including testing different drivers - including firewire, alsa, and freebob drivers. The Mackie mixer is the Onyx, firewire integrated, and a google search showed that it *is* compatible with Linux. I'm thinking it's just an issue with the JACK settings.

I followed the steps in the JACK-related links above but still no luck getting it to work.

Could someone please help with the JACK set-up?

Thank you.

---

### Post by AutoStatic on 2009-12-27
You need to stick to the FFADO driver, that's the 'firewire' driver in QjackCtl. What are your current settings in QjackCtl? Could you post a screenshot? And could you post some of those error messages?

---

### Post by Th3Professor on 2009-12-28
Here are screen shots.

edit-
I'm going to 'gimp'/edit those screenshots try to get better resolutions.
edit2-
okay it won't let me remove the images and replace with new ones. Odd.

---

### Post by Th3Professor on 2009-12-28
Let's try this, I hope this is more legible.

---

### Post by arielon on 2009-12-28
OK, I'm going to post here, because it seems we're having similar setup.

Mine: 
. sound card - Presouns FIREBOX [firewire - works great with ffado, better than in Windows with RT+jackd]
. keyb - KORG K61P
. OS - Ubuntu 64 bits

Setup:
. qjackctl (ffado)
. wineasio
. alsa + jack pcm plugin

Soft:
. Rosegarden (master)
. Propellerheads Reason (slave)

I want to achieve:
. plausible - Rosegarden (or any other linux native seq, including Ardour[albeit no midi yet]) sending midi to Reason (wine) while playing other samples from within seq.
. best - Live or Cubase [Rewire or Jack Transport] to Reason in Ubuntu (don't want Windows anymore)

So far:
. winecfg / Alsa+jack pcm = lots of Xruns [which means sound stops in Reason]; midi works! [from Rosegarden seq and K61P]
. . ->> [http://mailman.alsa-project.org/pipermail/alsa-devel/2007-May/001107.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-May/001107.html)
. winecfg / Jack = No midi in Reason. Great timing (RT)
. [Wine+Reason] / wineasio = Seems the best conf, but I get xruns with less than 2048 frames/period and then Reason hangs until I shut down the jack server, to be able to respond. I don't get xruns with Jack driver in winecfg and 128 Frames/period. Midi works.

. Why Reason? - Why not? It works completely stable with Jack audio in winecfg, only problem is no MIDI (I haven't find the way yet)
. Why Live? - [www.ableton.com]("http://www.ableton.com") (download demo and you'll see)

---

### Post by raboofje on 2009-12-28
I think the key error message in the 'Messages' window of jack is 'cannot load driver module firewire' - I'm not too familiar with firewire, but [http://ardour.org/node/2375](http://ardour.org/node/2375) seems to suggest this error means you have not installed ffado yet. Could that be?

---

### Post by AutoStatic on 2009-12-28
Hello Th3Professor, I think you don't have raw1394 access enabled. If you open the Ubuntu Studio Controls and tick 'Enable raw1394 access' you should get your Mackie up and running.

---

### Post by AutoStatic on 2009-12-28
> **arielon said:**
> I want to achieve:
. best - Live or Cubase [Rewire or Jack Transport] to Reason in Ubuntu (don't want Windows anymore)Hello Arielon, with what you're trying to achieve I think you're best off with a Windows machine: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Th3Professor on 2009-12-28
> **AutoStatic said:**
> Hello Th3Professor, I think you don't have raw1394 access enabled. If you open the Ubuntu Studio Controls and tick 'Enable raw1394 access' you should get your Mackie up and running.

I think it was before, though double checked this time and it's definitely enabled now. Though here are some new errors.

Edit-

Should I use "firewire" or "freebob"?

I found this on Ardour's site:
> Firewire devices are supported by FFado (freebob changed it's name). Ubuntustudio has these freebob drivers by default for jack. You should be able to configure jack to use freebob via the setup page in qjackctl. Select "freebob" instead of "alsa" as the driver and review the rest of the configuration.  After you get jack running with freebob, Ardour will just work.
 See [http://ardour.org/system_requirements/audio_compatibility](http://ardour.org/system_requirements/audio_compatibility) for how Ardour uses audio devices. Link:
 [http://ardour.org/node/970](http://ardour.org/node/970)

When I try "freebob" it gives this error message:
"[COLOR=#ff0000]16:14:24.307 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]"

 Attached images are screen shots of the current "firewire" driver set-up (not freebob) in JACK and the error messages that are coming up with that.

---

### Post by trulan on 2009-12-28
I think Autostatic is on  the right track.  Sometimes Ubuntu Studio Controls fails to do its job properly.  Can you post the output of
```
ls -al /dev/raw1394
```
and
```
groups
```

---

### Post by Th3Professor on 2009-12-28
I found some hints on Ardour's board, tried adding my user account to "disk" group (and although it shows the user as part of the group in the gui-version of users/groups, the command line "groups" doesn't show "disk" as a group the user is a member of, which is odd), and I haven't tried this yet - chmod 770 /dev/raw1394 - but I'm considering it (if it'll make any difference at all).

Here's ls -la /dev/raw1394 -
crw-rw---- 1 root video 171, 0 2009-12-28 09:09 /dev/raw1394

Here's groups -
music adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare

(user account name is "music")

---

### Post by AutoStatic on 2009-12-28
Looks good, except for that config rom error you are getting, [seen that one before]("http://ubuntuforums.org/showthread.php?t=1361083").
What Firewire chipset is in your PC? What is the output of **lspci**? Did you try different cables? What kind of Firewire port is on your PC, 4-pin or 8-pin? If it's a 4-pin you have to use an external power adapter for your Mackie.
And I'd suggest you stick with one howto, and preferably this one: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by Th3Professor on 2009-12-28
here's lspci -

```
music@delta:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce 750a LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
07:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
music@delta:~$ 

```Someone else provided cat /proc/interrupts in that other thread, here's that -

```
music@delta:~$ cat /proc/interrupts 
            CPU0       CPU1       CPU2       CPU3       
   0:        128          0          0        165   IO-APIC-edge      timer
   1:          0          0          0          2   IO-APIC-edge      i8042
   4:          0          0          0          2   IO-APIC-edge    
   6:          0          0          0          5   IO-APIC-edge      floppy
   7:          1          0          0          0   IO-APIC-edge    
   8:          0          0          0          1   IO-APIC-edge      rtc0
   9:          0          0          0          0   IO-APIC-fasteoi   acpi
  12:          0          0          0          4   IO-APIC-edge      i8042
  14:          0          5       5341     385417   IO-APIC-edge      pata_amd
  15:          0          0          0          0   IO-APIC-edge      pata_amd
  16:          0          2        922    1024515   IO-APIC-fasteoi   pata_marvell, nvidia
  18:          0          0          0        524   IO-APIC-fasteoi   ohci1394
  20:          0          1        392     705014   IO-APIC-fasteoi   ohci_hcd:usb3
  21:          0          0         97     119787   IO-APIC-fasteoi   ehci_hcd:usb2, HDA Intel
  22:          0          9        766    1772379   IO-APIC-fasteoi   ehci_hcd:usb1
  23:          0          0        185     473507   IO-APIC-fasteoi   ohci_hcd:usb4
  27:          0          1        211     197874   PCI-MSI-edge      ahci
  28:          0          0         40      25271   PCI-MSI-edge      eth0
 NMI:          0          0          0          0   Non-maskable interrupts
 LOC:   28688118   28854988   28601674   28561578   Local timer interrupts
 SPU:          0          0          0          0   Spurious interrupts
 CNT:          0          0          0          0   Performance counter interrupts
 PND:          0          0          0          0   Performance pending work
 RES:    2906683    1490679     833955     410441   Rescheduling interrupts
 CAL:       6336       7146       8238       8193   Function call interrupts
 TLB:      10392      11997       8280       8847   TLB shootdowns
 TRM:          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0   Threshold APIC interrupts
 MCE:          0          0          0          0   Machine check exceptions
 MCP:         95         95         95         95   Machine check polls
 ERR:          1
 MIS:          0
music@delta:~$ 

```I'm not sure if the firewire is 4-pin or 8-pin. I unplugged it, checked it out, and plugged it back in, though didn't see any pins, or maybe I wasn't looking at it correctly.

I used the steps in the [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) howto page.

edit- including editing the /etc/default/rtirq file.

edit2- Here's lsusb -
```
music@delta:~$ lsusb 
Bus 003 Device 003: ID 1532:0109 Razer USA, Ltd 
Bus 003 Device 002: ID 09ae:2007 Tripp Lite 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1532:000c Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 058: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
music@delta:~$ 
```edit3- here's lsmod -
```

music@delta:~$ lsmod 
Module                  Size  Used by
dv1394                 21288  0 
nls_iso8859_1           5264  1 
nls_cp437               6960  1 
vfat                   13264  1 
fat                    59696  1 vfat
ecb                     3280  1 
binfmt_misc            10300  1 
ppdev                   8376  0 
sha256_generic         10800  0 
cryptd                  8120  0 
aes_x86_64              8976  5 
aes_generic            28464  1 aes_x86_64
cbc                     4208  2 
xfs                   537088  1 
exportfs                5328  1 xfs
dm_crypt               14744  2 
snd_hda_codec_nvhdmi     6192  1 
snd_hda_codec_analog    80080  1 
snd_hda_intel          31560  4 
snd_hda_codec          88048  3 snd_hda_codec_nvhdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               9560  1 snd_hda_codec
snd_pcm_oss            45024  0 
snd_mixer_oss          19728  1 snd_pcm_oss
snd_pcm                91960  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3540  0 
snd_seq_oss            33920  0 
snd_seq_midi            8448  0 
snd_rawmidi            27232  1 snd_seq_midi
iptable_filter          3856  0 
snd_seq_midi_event      8656  2 snd_seq_oss,snd_seq_midi
nvidia              10321672  27 
snd_seq                61664  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27000  2 snd_pcm,snd_seq
ip_tables              21152  1 iptable_filter
raw1394                29448  0 
lp                     12740  0 
shpchp                 38220  0 
snd_seq_device          8484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             8344  0 
psmouse                57460  0 
amd64_edac_mod         26944  0 
asus_atk0110            9616  0 
snd                    79496  20 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               6772  0 
x_tables               26680  1 ip_tables
soundcore              10080  1 snd
parport                41484  2 ppdev,lp
snd_page_alloc         11072  2 snd_hda_intel,snd_pcm
edac_core              49916  1 amd64_edac_mod
joydev                 13056  0 
raid10                 24624  0 
raid1                  25648  0 
raid0                   8724  0 
multipath               9812  0 
linear                  6068  0 
usbhid                 43872  2 
raid456                57328  1 
raid6_pq               81440  1 raid456
async_xor               4144  1 raid456
async_memcpy            2512  1 raid456
async_tx                4112  3 raid456,async_xor,async_memcpy
xor                     5760  2 raid456,async_xor
usb_storage            65856  1 
ohci1394               34500  1 dv1394
ieee1394              102048  3 dv1394,raw1394,ohci1394
forcedeth              59644  0 
floppy                 66024  0 
video                  23436  0 
output                  3792  1 video
music@delta:~$ 

```and sudo lspci -vvv -

```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [94] HyperTransport: #1a
    Capabilities: [60] HyperTransport: Retry Mode
    Capabilities: [44] HyperTransport: Slave or Primary Interface
        Command: BaseUnitID=0 UnitCnt=0 MastHost- DefDir- DUL-
        Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency 0: [b]
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD+
        Link Frequency 1: 200MHz
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
        Prefetchable memory behind bridge Upper: 00-00
        Bus Number: 00
    Capabilities: [d0] HyperTransport: #1c

00:01.0 ISA bridge: nVidia Corporation nForce 750a LPC Bridge (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 10
    Region 0: I/O ports at fc00 [size=64]
    Region 4: I/O ports at 1c00 [size=64]
    Region 5: I/O ports at 1c40 [size=64]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 7
    Region 0: Memory at fdf80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 22
    Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 21
    Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    Region 4: I/O ports at f000 [size=16]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 82c0
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (500ns min, 1250ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
        Masking: 00000000  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: fdd00000-fddfffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
    Capabilities: [b8] Subsystem: ASUSTeK Computer Inc. Device 82e7
    Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-
        Mapping Address Base: 00000000fee00000

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 27
    Region 0: I/O ports at 09f0 [size=8]
    Region 1: I/O ports at 0bf0 [size=4]
    Region 2: I/O ports at 0970 [size=8]
    Region 3: I/O ports at 0b70 [size=4]
    Region 4: I/O ports at dc00 [size=16]
    Region 5: Memory at fe026000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [8c] SATA HBA <?>
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
        Address: 00000000fee0f00c  Data: 4171
    Capabilities: [ec] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 82e7
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 28
    Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at d800 [size=8]
    Region 2: Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
    Region 3: Memory at fe029000 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/4 Enable+
        Address: 00000000fee0f00c  Data: 4199
        Masking: 0000fffe  Pending: 00000000
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 0000a000-0000bfff
    Memory behind bridge: f6000000-fbffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000efffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 82e7
    Capabilities: [48] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0f00c  Data: 4151
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
        Mapping Address Base: 00000000fee00000
    Capabilities: [80] Express (v2) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
            Slot #  1, PowerLimit 75.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Off, PwrInd On, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet+ LinkState+
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 82e7
    Capabilities: [48] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0f00c  Data: 4159
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
        Mapping Address Base: 00000000fee00000
    Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 256 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #3, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
            Slot #  4, PowerLimit 10.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Off, PwrInd On, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
            Changed: MRL- PresDet+ LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00007000-00008fff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 82e7
    Capabilities: [48] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0f00c  Data: 4161
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
        Mapping Address Base: 00000000fee00000
    Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #4, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
            Slot #  5, PowerLimit 10.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Off, PwrInd On, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet+ LinkState+
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: [80] HyperTransport: Host or Secondary Interface
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL-
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=1 IsocEn- LSEn- ExtCTL- 64b-
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency: [b]
        Link Error: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE-

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 8294
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=02, secondary=03, subordinate=05, sec-latency=0
    I/O behind bridge: 0000a000-0000bfff
    Memory behind bridge: f6000000-fbffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000efffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Express (v2) Upstream Port, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-SlotPowerLimit 0.000000W
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x16, ASPM L0s, Latency L0 <512ns, L1 <4us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [a0] Subsystem: nVidia Corporation Device 0c19
    Kernel modules: shpchp

03:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=03, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f6000000-f9ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Express (v2) Downstream Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x16, ASPM L0s, Latency L0 <512ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
            Slot #  1, PowerLimit 0.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
    Kernel modules: shpchp

03:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=03, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 00000000eff00000-00000000efffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Express (v2) Downstream Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #2, Speed 2.5GT/s, Width x16, ASPM L0s, Latency L0 <512ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
            Slot #  3, PowerLimit 0.000000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
            Changed: MRL- PresDet- LinkState-
    Kernel modules: shpchp

04:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
    Subsystem: eVga.com. Corp. Device 1260
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at f9f80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <1us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

07:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 8c00 [size=8]
    Region 1: I/O ports at 8800 [size=4]
    Region 2: I/O ports at 8400 [size=8]
    Region 3: I/O ports at 8000 [size=4]
    Region 4: I/O ports at 7c00 [size=16]
    Region 5: Memory at fdaff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: 00000000  Data: 0000
    Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr+ NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #4, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 <256ns, L1 unlimited
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel driver in use: pata_marvell
```edit4- I don't know if ffado-test will be effective here but here's sudo ffado-test Discover - 

```
music@delta:~$ sudo ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

29674393534: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
29675443142: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29676494141: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29677545140: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29678596140: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29679647142: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29679650020: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
29679650043: Debug (devicemanager.cpp)[ 376] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
29680700143: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29681751141: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29682802144: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29683853140: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29684904140: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29684906263: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
29684906278: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
29684906284: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
29684906293: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
29684906299: Debug (Element.cpp)[ 121] show: Element DeviceManager
29684906304: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
no message buffer overruns
music@delta:~$ 

```and sudo ffado-test ListDevices -

```
music@delta:~$ sudo ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
29759243265: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
no message buffer overruns
music@delta:~$ 

```and sudo ffado-test diag -
```


FFADO diagnostic utility 0.1
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.31-9-rt
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... True
  new 1394 stack present.... False
  new 1394 stack loaded..... False
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites...
   gcc................ gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
   g++................ sh: g++: not found
   PyQt............... sh: pyuic: not found
   jackd.............. jackd version 0.116.1 tmpdir /dev/shm protocol 24
     path............. /usr/bin/jackd
     flags............ Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394......... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags............ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
   libavc1394......... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
     flags............ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883........ Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags............ Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6....... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags............ Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1............. Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
     flags............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
 Hardware...
   Host controllers:
01:0a.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8294]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2612.089
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5224.17
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2612.089
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5223.63
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2612.089
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5223.63
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2612.089
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5223.64
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [128, 128, 128, 128], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    4: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['']
 IRQ    6: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['floppy']
 IRQ    7: PID:  None, count:       [1, 1, 1, 1], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['pata_amd']
 IRQ   15: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['pata_amd']
 IRQ   16: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['pata_marvell', 'nvidia']
 IRQ   18: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ohci1394']
 IRQ   20: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ohci_hcd:usb3']
 IRQ   21: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'HDA Intel']
 IRQ   22: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1']
 IRQ   23: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ohci_hcd:usb4']
 IRQ   27: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['ahci']
 IRQ   28: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.
```

one more edit for this post-
I didn't have JACK running (during the commands above) since it's not starting anyway, though I don't know if that makes a difference.

---

### Post by Th3Professor on 2009-12-28
A good portion of that output is confusing but these parts from the "ffado-test diag" have me curious if they involve what is not making things work...

"False" RT patch:
```
FIXME: implement test for RT kernel
RT patched............... False
```"False" new 1394 "stack":
```
new 1394 stack present.... False
new 1394 stack loaded..... False
```g++ and PyQt not found:
```
g++................ sh: g++: not found
PyQt............... sh: pyuic: not found
```JACK not found in "pkg-config" search path:
```
Package jack was not found in the pkg-config search path."
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
```"libraw1394" not found in pkg-config path:
```
Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
```"libavc1394" not found in pkg-config path:
```
Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
```"libiec61883" not found in pkg-config path:
```
Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
```"libxml++-2.6" not found in pkg-config path:
```
Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
```"dbus-1" not found in pkg-config path:
```
Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
```I don't know if I really need to do anything with any of that or if it's just not responding to the "ffado-test" program.

edit- Here's "tail -f /var/log/syslog", I entered the command, turned on the mixer, then turned on my midi keyboard just to see how that would respond too...

After turning on the mixer:
```
Dec 28 20:08:54 delta kernel: [39584.292920] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000ff204000005ab]
Dec 28 20:08:54 delta kernel: [39584.292957] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
```

After turning on the usb/midi keyboard:
```
Dec 28 20:09:23 delta kernel: [39613.959258] usb 4-3: new full speed USB device using ohci_hcd and address 4
Dec 28 20:09:24 delta kernel: [39614.148913] usb 4-3: configuration #1 chosen from 1 choice
Dec 28 20:09:24 delta pulseaudio[14326]: module-alsa-card.c: Failed to find a working profile.
Dec 28 20:09:24 delta pulseaudio[14326]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-M-Audio_USB_Axiom_49-00" card_name="alsa_card.usb-M-Audio_USB_Axiom_49-00" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
```

I'm guessing JACK is supposed to be used with MIDI instruments as well as mixers (like the firewire sound board). When I turned on the Mackie Onyx firewire mixer it looked like the syslog just logged that it was turned on, which seems to be fine. (??) Though I see a lot of "failed" in the log of the usb/midi keyboard being turned on. Confusing.

---

### Post by trulan on 2009-12-28
> **Th3Professor said:**
> I found some hints on Ardour's board, tried adding my user account to "disk" group (and although it shows the user as part of the group in the gui-version of users/groups, the command line "groups" doesn't show "disk" as a group the user is a member of, which is odd), and I haven't tried this yet - chmod 770 /dev/raw1394 - but I'm considering it (if it'll make any difference at all).

Here's ls -la /dev/raw1394 -
crw-rw---- 1 root video 171, 0 2009-12-28 09:09 /dev/raw1394

Here's groups -
music adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare

(user account name is "music")
OK, your permissions are good.  I'm afraid I'm pretty much out of ideas.  I need to read through your stuff more thoroughly, I'll post back if I have any more ideas.

The Ardour forums suggested adding your username to the 'disk' group because that's what raw1394 gets assigned to in Debian.  Ubuntu Studio Controls sets it to group 'video' (as you can see, yours is set to video) so that's all good.

---

### Post by Th3Professor on 2009-12-29
Thank you for taking a look at that output/info. Hopefully something in there will help with figuring out things. Also, I do have a converter that came with the Mackie Onyx firewire mixer, it has a larger plug on one side and a much smaller plug on the other side. I'm not using it right now but the normal firewire/1394 cable plugs directly into my desktop computer's motherboard (motherboard has firewire plug on it), using the bigger plug. I think my laptop has the small-sized plug (though I'm not using this w/ my laptop). I don't see a small-sized plug on my desktop computer though.

Here's an image of a converter like mine:
[IMG]http://www.national-tech.com/prodimages/ieee-1394-firewire-6p-4p-coupler.jpg[/IMG]

---

### Post by AutoStatic on 2009-12-29
That image of the small Back plug is a 4-pin plug. The bigger ones you're using are 8-pins.
And all of the things you suspect of not making things work have nothing to do with your problems unfortunately. The source is this:
```
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
29759243265: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
```

And this:
```
29684904140: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29684906263: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
29684906278: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
29684906284: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
```

Did you try different cables? Does the Mackie come with a power adapter and did you try using the Mackie with the adapter? Did you try first switching the Mackie on and then the computer?

---

### Post by Th3Professor on 2009-12-29
> **AutoStatic said:**
> That image of the small Back plug is a 4-pin plug. The bigger ones you're using are 8-pins.
And all of the things you suspect of not making things work have nothing to do with your problems unfortunately. The source is this:
```
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
29759243265: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
```And this:
```
29684904140: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
29684906263: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
29684906278: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
29684906284: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
```Did you try different cables? Does the Mackie come with a power adapter and did you try using the Mackie with the adapter? Did you try first switching the Mackie on and then the computer?

I only have the 1 firewire cable that came with the Mackie. It's brand new, undamaged, and the syslog file recognizes it when I turn the mixer on/off. :confused:

The Mackie came with its own power adapter/plug, I'm using that cable/plug with it.

I haven't tried turning the Mackie on before the computer. I'll go ahead and try that... turning on the Mackie then restarting the computer. I'll post the JACK response to that here real soon.

edit-
Okay. Good new. Sort of. ...I turned on the Mackie and rebooted the computer. I loaded JACK and there are no noticeable errors. However... it defaulted to the last settings I tested, which used "freebob" driver. Should I still use "firewire" driver? (I read on another site that freebob was used for firewire before the firewire driver came out.) Here are a couple screenshots. Okay nevermind, I can't add screenshots to this post. Weird. I'll post them in the next message.

---

### Post by Th3Professor on 2009-12-29
Here are the screenshots where apparently JACK is actually working (though I haven't tested it yet with Ardour or another program).

Also note that this is with "freebob" driver, I don't know if that's a good or bad idea though.

edit-
I'm testing out freebob, seeing what happens. So far Ardour pops up this warning message:
"[WARNING]: no outputs available for auditioner - manual connection required"

edit2-
Yeah, I'm a total noob with Ardour. ;) Not really sure where to start. I think I'm gonna try getting JACK with firewire first, so I went ahead and switched over to "firewire" driver in JACK and received the following:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]12:20:58.407 Startup script...[/COLOR]
 [COLOR=#990099]12:20:58.407 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:20:58.811 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:20:58.811 JACK is starting...[/COLOR]
 [COLOR=#990099]12:20:58.812 /usr/bin/jackd -R -P70 -dfirewire -r44100 -p128 -n2 -i12 -o12[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 [COLOR=#999999]12:20:58.850 JACK was started with PID=4466.[/COLOR]
 Enhanced3DNow! detected
 SSE2 detected
 02229400085:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
 [COLOR=#999933]12:21:00.941 Server configuration saved to "/home/music/.jackdrc".[/COLOR]
 [COLOR=#999999]12:21:00.943 Statistics reset.[/COLOR]
 [COLOR=#999999]12:21:00.946 Client activated.[/COLOR]
 [COLOR=#CC9966]12:21:00.959 JACK connection graph change.[/COLOR]
 Enhanced3DNow! detected
 SSE2 detected
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
...
  p, li { white-space: pre-wrap; }  [COLOR=#999999]12:21:02.325 Client deactivated.[/COLOR]
 cannot continue execution of the pro
 [COLOR=#999999]12:21:02.342 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:21:02.343 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:21:02.343 killall jackd[/COLOR]
 cessing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
...
  p, li { white-space: pre-wrap; }  [COLOR=#999999]12:21:02.763 Post-shutdown script terminated with exit status=256.[/COLOR]
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
...
jackd: no process found
```


I don't know if this will make much difference - but I'll go ahead and shut down the JACK app, turn off the mixer, turn the mixer back on, restart the computer, and restart JACK (with the firewire driver). <I'll post update soon.>

---

### Post by AutoStatic on 2009-12-29
The FFADO 'firewire' driver is the successor of the 'freebob' driver. It's best to use the FFADO driver. Could you try the 'firewire' driver?

---

### Post by Th3Professor on 2009-12-29
Yep. I'm about to do another reboot of the system (with mackie turned on beforehand) and with firewire driver. I did a firewire driver attempt in the copy/pasted code (edit) of my previous message here. I'm hoping it responds better after a fresh boot.

Okay, here's the message window after a fresh reboot and with firewire driver in JACK:

```
[COLOR=#999999] 12:30:02.073 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:30:02.117 Statistics reset.[/COLOR]
 [COLOR=#999999]12:30:02.193 Startup script...[/COLOR]
 [COLOR=#990099]12:30:02.193 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]12:30:02.197 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:30:02.596 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:30:02.596 JACK is starting...[/COLOR]
 [COLOR=#990099]12:30:02.597 /usr/bin/jackd -R -P70 -dfirewire -r44100 -p128 -n2 -i12 -o12[/COLOR]
 [COLOR=#999999]12:30:02.599 JACK was started with PID=3870.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 [COLOR=#cccc99]12:30:02.799 ALSA connection change.[/COLOR]
 loading driver ..
 Enhanced3DNow! detected
 SSE2 detected
 00091254082:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
 [COLOR=#999933]12:30:04.806 Server configuration saved to "/home/music/.jackdrc".[/COLOR]
 [COLOR=#999999]12:30:04.807 Statistics reset.[/COLOR]
 [COLOR=#999999]12:30:05.014 Client activated.[/COLOR]
 [COLOR=#cc9966]12:30:05.021 JACK connection graph change.[/COLOR]
 Enhanced3DNow! detected
 SSE2 detected
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 [COLOR=#999999]12:30:06.365 Client deactivated.[/COLOR]
 cannot continue execution of the processing graph (Broken pipe)
 [COLOR=#999999]12:30:06.382 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:30:06.383 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:30:06.383 killall jackd[/COLOR]
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 [COLOR=#999999]12:30:06.854 Post-shutdown script terminated with exit status=256.[/COLOR]
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 jackd: no process found
```

edit-
This Ardour forum page says use freebob with mackie onyx-
[http://ardour.org/node/970](http://ardour.org/node/970)
...though the user in that page who tried it said they're experiencing noise problems.

---

### Post by AutoStatic on 2009-12-30
Hmmm, weird. You get better results with the freebob driver and according to this thread your Firewire chipset and Mackie devices can work together, only the revision # of his Firewire chipset is different: [http://forums.gentoo.org/viewtopic-t-791132-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-791132-postdays-0-postorder-asc-start-0.html)

So maybe it's better to focus on the freebob driver, to get that thing to work. The quickest fix though would be to get yourself a decent Firewire card, preferably with a Texas Instruments chipset. I can recommend these ones:
[http://www.feedback.nl/computer/belkin/pci-3-port-firewire](http://www.feedback.nl/computer/belkin/pci-3-port-firewire)
[http://www.feedback.nl/computer/belkin/pcie-3-port-firewire](http://www.feedback.nl/computer/belkin/pcie-3-port-firewire)

---

### Post by trulan on 2009-12-30
You appear to have exactly the same firewire chip as I do, Agere FW 322/323.  I have had absolutely no problems with mine - it even worked (mostly) under windoze.

If the mackie does indeed work better with freebob than with ffado, that would seem really odd to me, but that would be a piece of information for the ffado guys.  Anything that worked under freebob should work better under ffado - but this isn't a perfect world...

I guess you could try increasing your frames and buffer sizes - try 256 and 3 instead of 128 and 2.  Bigger means more latency and your system is light years faster than mine but it just might make a difference, who knows?

---

### Post by Th3Professor on 2009-12-30
I just tried 256 and 3 for frames and buffer size, instead of 128 and 2, and no change in results.

Some new questions have come to mind since my previous update...

How do I check to make sure the ffado drivers are installed?

Is there a way to test to see if my current kernel is supporting the firewire chip on my motherboard?

```
uname -r
2.6.31-9-rt
```My motherboard is:
ASUS M3N-HT Deluxe HDMI
It has: "2x 1394a"
I'm not sure how exactly to find out additional details on the actual "chip" itself on the board.

I don't know if this has to do with kernel recognition of motherboard chips but...

```

lsmod | grep 1394
Module                  Size  Used by
dv1394                 21288  0 
raw1394                29448  0 
ohci1394               34500  1 dv1394
ieee1394              102048  3 dv1394,raw1394,ohci1394

```There is a "0" by "raw1394", that made me wonder if I need to - and I might be off with this guess - but maybe need to "modprobe" something?

I think modprobe is a temporary quick fix but forgot if there is something else I need to do to make it permanent change at boot.

---

### Post by trulan on 2009-12-30
Modprobe would be a temporary fix in the event that you were seeing /dev/raw1394 not found when running ls -al /dev/raw1394.  I don't think that's going to change anything.

Your firewire chip itself should also not be a problem as that is the same chip that is in my desktop.  I'll have to look through your earlier posts - is the firewire chip being managed by a pci bridge or some other host controller?  (I'm talking about things I know very little about here - I'll suggest again attempting to contact the ffado guys on this issue.  I think they have a mailing list rather than a forum.)

Search in Synaptic for ffado.  You should see libffado1 installed, along with a few other things.  But if it wasn't installed Jack would be throwing an error about not being able to find driver "firewire".

---

### Post by AutoStatic on 2009-12-30
> **trulan said:**
> If the mackie does indeed work better with freebob than with ffado, that would seem really odd to me, but that would be a piece of information for the ffado guys.  Anything that worked under freebob should work better under ffado - but this isn't a perfect world..You're right. And which Agere chipset is in your PC? The rev. 70 or rev. 61? I should check my own PC, it has an Agere chipset also. BRB :)

---

### Post by trulan on 2009-12-30
I'm in Windows now but it looks like rev61.  The PC is about three years old.

---

### Post by Th3Professor on 2009-12-30
> **trulan said:**
> Modprobe would be a temporary fix in the event that you were seeing /dev/raw1394 not found when running ls -al /dev/raw1394.  I don't think that's going to change anything.
/dev/raw1394 does exist and permissions are set so I can use it.

> **trulan said:**
> Your firewire chip itself should also not be a problem as that is the same chip that is in my desktop.
That's good to know. I have a mixer that's compatible with Linux, and I have a firewire chipset that's compatible with Linux, so maybe I'm doing something wrong with the JACK settings? It's weird that JACK recognizes the mixer with the freebob driver but not the firewire driver.

> **trulan said:**
> I'll have to look through your earlier posts - is the firewire chip being managed by a pci bridge or some other host controller?
I'm not sure how to check if the firewire chip is managed by pci bridge or some other host controller. :(

> **trulan said:**
> (I'm talking about things I know very little about here - I'll suggest again attempting to contact the ffado guys on this issue.  I think they have a mailing list rather than a forum.)
I checked the ffado site, looks like they have a #ffado IRC channel on freenode, I'll check that out for additional ideas.

> **trulan said:**
> Search in Synaptic for ffado.  You should see libffado1 installed, along with a few other things.  But if it wasn't installed Jack would be throwing an error about not being able to find driver "firewire".
I searched, and ffado's definitely installed, all ffado searchable apps are installed except a "dev" application, which I don't think is necessary.

---

### Post by Th3Professor on 2009-12-30
> **AutoStatic said:**
> Hmmm, weird. You get better results with the freebob driver and according to this thread your Firewire chipset and Mackie devices can work together, only the revision # of his Firewire chipset is different: [http://forums.gentoo.org/viewtopic-t-791132-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-791132-postdays-0-postorder-asc-start-0.html)

So maybe it's better to focus on the freebob driver, to get that thing to work. The quickest fix though would be to get yourself a decent Firewire card, preferably with a Texas Instruments chipset. I can recommend these ones:
[http://www.feedback.nl/computer/belkin/pci-3-port-firewire](http://www.feedback.nl/computer/belkin/pci-3-port-firewire)
[http://www.feedback.nl/computer/belkin/pcie-3-port-firewire](http://www.feedback.nl/computer/belkin/pcie-3-port-firewire)

I just now saw your post (quoted above), I don't know how I missed that before. Anyway, I hope I don't have to buy a firewire card. :-/ Are those cards you listed *definitely* compatible <fully supported> with ffado, linux, jack, ardour, etc.? I'll have to do some digging and see what are some inexpensive but also fully-supported firewire cards. It will be a total bummer if I have to get one considering my Mackie has firewire functionality integrated into it. (Edit- more like, considering my motherboard already has a compatible firewire chip/chipset.) :-/

---

### Post by AutoStatic on 2009-12-31
> **trulan said:**
> I'm in Windows now but it looks like rev61.  The PC is about three years old.
Just checked mine:
```
03:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
```
And that chipset works well in my setup. So maybe the rev 70 is the bottleneck?

And Th3Professor, there are cheaper cards with the same Texas Instruments chipset and as far as I know these cards are fully supported. Actually it's not really if a card is fully supported that matters but more if a Firewire card/chipset and a Firewire soundcard work well together, ie are compatible. Firewire devices can be a bit picky when it comes to chipsets they have to work with.

---

### Post by Th3Professor on 2009-12-31
> **AutoStatic said:**
> Just checked mine:
```
03:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
```And that chipset works well in my setup. So maybe the rev 70 is the bottleneck?

And Th3Professor, there are cheaper cards with the same Texas Instruments chipset and as far as I know these cards are fully supported. Actually it's not really if a card is fully supported that matters but more if a Firewire card/chipset and a Firewire soundcard work well together, ie are compatible. Firewire devices can be a bit picky when it comes to chipsets they have to work with.

Do you know how I check the rev# on my chipset?

As far as sound card and firewire card/chipset, I'm currently using all-motherboard, the audio & firewire features that come with the board (asus m3n-ht deluxe hdmi). It's a pretty hefty motherboard. It'd be a bummer if I can't use the features but at least something I'll take into consideration with future computer builds. :-/

Are there any known-matches between both sound card and firewire card/chipset that are compatible/supported in Linux, like a specific sound card and specific firewire card that work well together?

---

### Post by AutoStatic on 2009-12-31
> **Th3Professor said:**
> Do you know how I check the rev# on my chipset?[http://ubuntuforums.org/showpost.php?p=8573069&postcount=13](http://ubuntuforums.org/showpost.php?p=8573069&postcount=13)
```
01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
```

> **Th3Professor said:**
> As far as sound card and firewire card/chipset, I'm currently using all-motherboard, the audio & firewire features that come with the board (asus m3n-ht deluxe hdmi). It's a pretty hefty motherboard. It'd be a bummer if I can't use the features but at least something I'll take into consideration with future computer builds. :-/It could be the Firewire chipset, but I'm not 100% sure. Maybe we're simply overlooking something.

> **Th3Professor said:**
> Are there any known-matches between both sound card and firewire card/chipset that are compatible/supported in Linux, like a specific sound card and specific firewire card that work well together?Yes, the Belkin cards I posted earlier with the Texas Instruments chipsets. They work with practically all external Firewire soundcards, the links I've posted are from a music store.

And another thing, does the Mackie have any firmware? If so, did you fully update the firmware?
You could also try a cheap Firewire card with a Via chipset, on the Mackie site they even recommend it:

> THE FOLLOWING COMPUTER SYSTEMS HAVE BEEN QUALIFIED BY THE MACKIE TEST DEPARTMENT FOR USE WITH ALL MAJOR DAW&#8217;S INCLUDING PRO TOOLS® M-POWERED&#8482; 8. THIS LIST DOES NOT REPRESENT THE ONLY SYSTEMS THAT WILL FUNCTION FAULTLESSLY AND IS INTENDED TO BE A GUIDE, HOWEVER WE CANNOT GUARANTEE OR SUPPORT PROBLEM FREE SYSTEM SETUP OUTSIDE OF THESE QUALIFIED SYSTEMS.
FOR PC

HPdc7700p
Chipset Q963
Intel Core 2 Duo E6400 @ 2.13GHz
2GB RAM
Ultra ULT40109 8 port FireWire / USB 2.0 card (VIA chipset)

You can get those cards for like $10,- and if it doesn't work you could always return it.

---

### Post by AutoStatic on 2010-01-01
Just found a thread on a German forum where someone has the same chipset and uses it with a Firewire device in Linux apparently: [http://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html](http://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html)

---

### Post by Th3Professor on 2010-01-01
> **AutoStatic said:**
> [http://ubuntuforums.org/showpost.php?p=8573069&postcount=13](http://ubuntuforums.org/showpost.php?p=8573069&postcount=13)
```
01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
```It could be the Firewire chipset, but I'm not 100% sure. Maybe we're simply overlooking something.

Yes, the Belkin cards I posted earlier with the Texas Instruments chipsets. They work with practically all external Firewire soundcards, the links I've posted are from a music store.

And another thing, does the Mackie have any firmware? If so, did you fully update the firmware?
You could also try a cheap Firewire card with a Via chipset, on the Mackie site they even recommend it:



You can get those cards for like $10,- and if it doesn't work you could always return it.

I'm guessing I'd have to log into Windows to update the Mackie's firmware? It did come with a cd rom. The mixer just hit the market in I think September, a few months ago, but I have no idea if there are already firmware updates. I'll check into that, hopefully that'll help.

You mentioned the Mackie site's recommended firewire card - I think that's for Windows/etc. computers, right? Would that apply to Linux systems too?

> **AutoStatic said:**
> Just found a thread on a German forum where someone has the same chipset and uses it with a Firewire device in Linux apparently: [http://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html](http://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html)

I'm a bit rusty on my Deutsch. ;) Even though I studied German in college I have totally forgotten it. lol Here's a [google English translation]("http://translate.google.com/translate?hl=en&sl=de&u=http://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html&ei=mps-S56BMsnjnAegna33CA&sa=X&oi=translate&ct=result&resnum=1&ved=0CAkQ7gEwAA&prev=/search%3Fq%3Dhttp://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DoGY").

---

### Post by AutoStatic on 2010-01-02
> **Th3Professor said:**
> I'm guessing I'd have to log into Windows to update the Mackie's firmware? It did come with a cd rom. The mixer just hit the market in I think September, a few months ago, but I have no idea if there are already firmware updates. I'll check into that, hopefully that'll help.I've checked the Mackie site and I don't think there's any firmware update for your mixer/soundcard.

> **Th3Professor said:**
> You mentioned the Mackie site's recommended firewire card - I think that's for Windows/etc. computers, right? Would that apply to Linux systems too?Yes. I have one lying around, I'll check what kind of chipset is on that one. Focusrite also recommends a Via chipset: [http://www.focusrite.com/answerbase/en/var/attachments/Focusrite_IEEE_1394_compatibility.pdf](http://www.focusrite.com/answerbase/en/var/attachments/Focusrite_IEEE_1394_compatibility.pdf)

> **Th3Professor said:**
> I'm a bit rusty on my Deutsch. ;) Even though I studied German in college I have totally forgotten it. lol Here's a [google English translation]("http://translate.google.com/translate?hl=en&sl=de&u=http://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html&ei=mps-S56BMsnjnAegna33CA&sa=X&oi=translate&ct=result&resnum=1&ved=0CAkQ7gEwAA&prev=/search%3Fq%3Dhttp://www.musiker-board.de/vb/pc-technik/362818-interface-auf-agere-firewire-chipsatz.html%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DoGY").The thread unfortunately doesn't explain how to get it running, it's just someone with the exact same Firewire chipset who got it working apparently with a *cough* MOTU device.

---

### Post by Th3Professor on 2010-01-02
The Focusrite PDF says there's an incompatibility with nvidea nforce4. I have nvidia nforce780a (not sure if that's close enough to the nforce4 to be an issue of compatibility).

On a more general note, I am using both motherboard-based audio and motherboard-based firewire. (Well, technically, I think that the motherboard came with a firewire card to plug into it.) It's an "asus m3n-ht deluxe hdmi". Here's a page on it-
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131343](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131343)
(The "specifications" tab on that page has more info.)

I'm a little confused on firewire cards and sound cards, I'm not sure if I need either a new firewire card and a new sound card, or if I need only one of them. There was mention earlier of "firewire soundcards", that confuses me a little, thinking that they are not mutually exclusive devices. The two Belkin cards appear to only be firewire cards. I'm also not sure which would be better - the PCI or PCIe.

I searched for those two (PCI and PCIe) for U.S.-based sales and found:

Belkin PCI:
[http://www.amazon.com/dp/B000E609G0](http://www.amazon.com/dp/B000E609G0)

Belkin PCIe:
[http://www.amazon.com/3-PORT-Firewire-Pci-Express-Card/dp/B000F9Q3PM](http://www.amazon.com/3-PORT-Firewire-Pci-Express-Card/dp/B000F9Q3PM)

I hope those two links work.

After figuring out if I need PCI or PCIe, if I get one of those linked above will my Mackie work with Linux/JACK/Ardour/etc.?

---

### Post by AutoStatic on 2010-01-03
Firewire card/chipset is the part that sits in your PC and the Firewire soundcard is the external device that you hook up to the Firewire card/chipset. Don't worry about the nforce chipset, it's not an nforce4. And did you look for a VIA Firewire card with a VT6306 or a VT6308 chipset? You can get those for around $10,-: [http://www.amazon.com/dp/B000A2813G](http://www.amazon.com/dp/B000A2813G)

---

### Post by Th3Professor on 2010-01-03
Cool thank you. :)

So just checking (before I make a purchase)... if I use the Sabrent SBT-VT6306 PCI card with my Asus M3N-HT Deluxe HDMI motherboard, will it make it so my Mackie Onyx 1220i FireWire Mixer work in Linux/JACK/Ardour (on Ubuntu Studio 9.10)?

(Considering I spent over $600 on a mixer that apparently might not be currently fully compatible I'm hoping to get the next purchase right. lol)

Thank you. :)

Edit-
Hmm, well I'll go ahead and buy the Sabrent. It's fairly inexpensive. Hopefully it'll make everything work.

---

### Post by Th3Professor on 2010-01-05
OKAY so, I got the card (Sabrent) and it is producing the *exact* same results as my original firewire. Great. <sigh>

Well, here's the JACK set-up with the Sabrent firewire card:

Driver: firewire
Checked: Realtime
Priority 70
Frames/Perios: 128
Sample Rate: 44100
Periods/Buffer: 2
Port Max: 256
Timeout: 500msec
Interface: default
Audio: duplex
Input channels: 12
Output channels: 12

And the messages window:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]15:24:41.637 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:24:41.652 Statistics reset.[/COLOR]
 [COLOR=#66cc99]15:24:41.715 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]15:24:41.907 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:24:49.750 Startup script...[/COLOR]
 [COLOR=#990099]15:24:49.751 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:24:50.153 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:24:50.153 JACK is starting...[/COLOR]
 [COLOR=#990099]15:24:50.153 /usr/bin/jackd -R -P70 -dfirewire -r44100 -p128 -n2 -i12 -o12[/COLOR]
 [COLOR=#999999]15:24:50.157 JACK was started with PID=3832.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 Enhanced3DNow! detected
 SSE2 detected
 00059789821:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
 [COLOR=#999933]15:24:52.267 Server configuration saved to "/home/music/.jackdrc".[/COLOR]
 [COLOR=#999999]15:24:52.268 Statistics reset.[/COLOR]
 [COLOR=#999999]15:24:52.489 Client activated.[/COLOR]
 [COLOR=#cc9966]15:24:52.494 JACK connection graph change.[/COLOR]
 Enhanced3DNow! detected
 SSE2 detected
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 [COLOR=#999999]15:24:53.948 Client deactivated.[/COLOR]
 cannot continue execution of the processing graph (Broken pipe
 [COLOR=#999999]15:24:53.965 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]15:24:53.966 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:24:53.966 killall jackd[/COLOR]
 )
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 [COLOR=#999999]15:24:54.437 Post-shutdown script terminated with exit status=256.[/COLOR]
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 cannot continue execution of the processing graph (Broken pipe)
 jackd: no process found
```That looks uncannily familiar. :(


Any ideas what to do?


Here are some recent messages from over on ffado.org:


> 

**Rumors about FFADO and the new firewire stack**

                                                 Submitted by arnonym on Mon, 12/28/2009 - 23:17.
      The last weeks have seen a few rumors and lots of questions: Is ffado running with the new firewire stack?


 The short answer as of this writing: No


 Read on for the longer answer...
 

Running FFADO 2.0 or later on the new stack requires kernel 2.6.32
or later. And a yet unreleased version of libraw1394 (>2.0.4).
Making ffado run on the new stack revealed some bugs and
not-yet-implemented things in the new stack and the libraw1394
compatibility code because audio streaming is using the firewire stack
in more demanding and advanced ways then for example hard-disk access.
 But the good news is that this is actually worked on and working on
the developers machines. Once all the necessary dependencies are
released, its up to the distributions to ship the new versions (and
finally completely disable the old stack).
 And there are also forces at work to implement the streaming in kernel-space. Of course this will be on the new stack only...
 Updates will of course be posted here.

And someone replied to it:

> 
**[Old stack already disabled in ubuntu 9.10]("http://ffado.org/?q=node/1316#comment-430")**

    Submitted by ceztko on Mon, 01/04/2010 - 19:08.
     

This
is bad as everybody that wanted to test ffado can't do it on the latest
version of the distro with the biggest user base. Is there an easy way to reenable it or kernel recompile is the only way to go?
 
     So what's that all about? Is that why my firewire won't work? <confusion>

I'm running kernel version:
2.6.31-9-rt

How do I check my ffado version?

How do I check my libraw1394 version?

Edit-
Will my firewire work if I change out with another version of either kernel, ffado, and/or libraw1394? Which ones work together? How do I change to another version of those?

<this is certainly frustrating>

Edit2-

By the way, I'm currently hooked up to this firewire card (Sabrent), from what lspci shows:
```
01:09.0 FireWire (IEEE 1394):
VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
```

Edit3-

Okay I found my FFADO version:
1.999.43

Since that's not FFADO 2.0 I'm going to assume my FFADO version is okay.

I'm still not sure how to find my libraw1394 version, though since I'm not running FFADO 2.0, I'll guess that my libraw1394 version isn't as much of a concern.

So, unless someone thinks it might actually be a version of one of those things, I'm guessing that it goes back to my original question regarding the new FireWire card (Sabrent) also not working with the mixer:

Any ideas?

<Thank you!>

---

### Post by trulan on 2010-01-05
```
00059789821:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:06:09
```
There's your Ffado version.

You should have the new firewire stack disabled.  Look for this file:
/etc/modprobe.d/blacklist-firewire.conf
Mine looks like this:
```
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
```
Which I interpret to mean it is disabling the new firewire stack in favor of the old one.

---

### Post by Th3Professor on 2010-01-05
My blacklist-firewire.conf shows:
```
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2

```
Maybe I should remove the "#" from the "#blacklist raw1394"? Maybe that's a bad idea. <shrug>

This is pretty frustrating though, still no working solution between Mackie firewire & the system, even with the new firewire card. :( I'm patient though, I just want the mixer to work w/ the computer. :confused:

---

### Post by AutoStatic on 2010-01-06
Don't blacklist raw1394, you need that kernel module.
And could you post the outcome of the following commands again?
**sudo ffado-test ListDevices**
**sudo ffado-test Discover**
**lsmod | grep 1394**
**cat /proc/interrupts**

> **Th3Professor said:**
> How do I check my libraw1394 version?Don't worry about libraw1394, you have a working version.

> **Th3Professor said:**
> Will my firewire work if I change out with another version of either kernel, ffado, and/or libraw1394? Which ones work together? How do I change to another version of those?You could try another kernel, I don't think either FFADO or libraw1394 are the problem. Did you already try with a non-RT generic kernel? The generic Karmic kernel is pretty good for audio production.

> **Th3Professor said:**
> 
```
01:09.0 FireWire (IEEE 1394):
VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
```Looks good, that one should definitely work.

---

### Post by Th3Professor on 2010-01-06
> **AutoStatic said:**
> Don't blacklist raw1394, you need that kernel module.
And could you post the outcome of the following commands again?
**sudo ffado-test ListDevices**
**sudo ffado-test Discover**
**lsmod | grep 1394**
**cat /proc/interrupts**

```
sudo ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0011060000003c77  0x00001106  0x00000000   Linux - ohci1394  - 
=== 1394 PORT 1 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x001e8c000178af12  0x00001E8C  0x00000000   Linux - ohci1394  - 
no message buffer overruns

```

```
sudo ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

58497425847: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
58497425894: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
58497425903: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
58497425906: Debug (Element.cpp)[ 121] show: Element DeviceManager
58497425912: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
58497425927: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  1 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
no message buffer overruns

```

```
lsmod | grep 1394
raw1394                29448  0 
ohci1394               34500  0 
ieee1394              102048  2 raw1394,ohci1394

```

```
cat /proc/interrupts
            CPU0       CPU1       CPU2       CPU3       
   0:        128          0          0        341   IO-APIC-edge      timer
   1:          0          0          0          2   IO-APIC-edge      i8042
   4:          0          0          0          2   IO-APIC-edge    
   6:          0          0          0          5   IO-APIC-edge      floppy
   7:          1          0          0          0   IO-APIC-edge    
   8:          0          0          0          1   IO-APIC-edge      rtc0
   9:          0          0          0          0   IO-APIC-fasteoi   acpi
  12:          0          0          0          4   IO-APIC-edge      i8042
  14:          0          1       3883     525940   IO-APIC-edge      pata_amd
  15:          0          0          0          0   IO-APIC-edge      pata_amd
  16:          0          1        708     843377   IO-APIC-fasteoi   pata_marvell, nvidia
  17:          0          0          0          3   IO-APIC-fasteoi   ohci1394
  18:          0          0          0          3   IO-APIC-fasteoi   ohci1394
  20:          0          4        536    1465731   IO-APIC-fasteoi   ohci_hcd:usb3
  21:          0          0        114      90426   IO-APIC-fasteoi   ehci_hcd:usb2, HDA Intel
  22:          0          5        917    2497881   IO-APIC-fasteoi   ehci_hcd:usb1
  23:          0          1        241     643697   IO-APIC-fasteoi   ohci_hcd:usb4
  27:          0          0        148     124178   PCI-MSI-edge      ahci
  28:          0          0        140     110808   PCI-MSI-edge      eth0
 NMI:          0          0          0          0   Non-maskable interrupts
 LOC:   59278106   59726160   58986838   59189931   Local timer interrupts
 SPU:          0          0          0          0   Spurious interrupts
 CNT:          0          0          0          0   Performance counter interrupts
 PND:          0          0          0          0   Performance pending work
 RES:    3556105    1295486     880394     283831   Rescheduling interrupts
 CAL:       2638       2633       2561       3307   Function call interrupts
 TLB:       6294       5990       3919       5423   TLB shootdowns
 TRM:          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0   Threshold APIC interrupts
 MCE:          0          0          0          0   Machine check exceptions
 MCP:        196        196        196        196   Machine check polls
 ERR:          1
 MIS:          0

```

> **AutoStatic said:**
> Did you already try with a non-RT generic kernel? The generic Karmic kernel is pretty good for audio production.

I haven't tried generic kernel. How do I add it? (Rather than install Ubuntu followed by Ubuntu Studio install I just started out with a fresh Ubuntu Studio install (only comes w/ the realtime.))

---

### Post by AutoStatic on 2010-01-07
Thanks for al the info! But could you repost the outcome of the **ffado-test** commands with the Mackie attached? I don't see the device now. Your IRQ's look good, both Firewire chipsets now have separate IRQ's.
And you can install the generic kernel by opening Synaptic and search for *linux-image-generic*.

---

### Post by Th3Professor on 2010-01-08
Thank you for the info on the generic kernel, I'll try that out.

I totally forgot about the mixer being turned on during the ffado-test. lol Anyway, here's the ffado-test Discover with the mixer turned on...

```
ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

242528941216: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
242529991145: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242531042147: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242532093145: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242533144148: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242534195148: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242534197257: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
242534197270: Debug (devicemanager.cpp)[ 376] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
242535247149: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242536298147: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242537349147: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242538400146: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242539451281: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
242539453665: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
242539453692: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
242539453700: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
242539453713: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
242539453719: Debug (Element.cpp)[ 121] show: Element DeviceManager
242539453731: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
242539453749: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  1 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
no message buffer overruns

```Edit-
I tried turning the mixer off, then turning it back on, then did a reboot/restart of the computer, and the ffado test discover and it looks like the same results:

```
ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

00104061384: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
00104152507: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
00104153038: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
00104153085: Warning (avc_avdevice.cpp)[ 132] discover: Using generic AV/C support for unsupported device 'Loud Technologies Inc. Onyx-i'
00104153514: Debug (avc_audiosubunit.cpp)[  55] discover: Discovering AVC::AudioSubunit...
00104153518: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00104153906: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00104153911: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,0,0)
00104154829: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00104154837: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,0,1)
00104155718: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00104155721: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,1,0)
00104156588: Debug (avc_subunit.cpp)[ 228] initPlugFromDescriptor: plug loading from descriptor not implemented
00104156591: Debug (avc_plug.cpp)[ 182] discover: discover: Could not init plug from descriptor (0,1,0,1,1)
00104157470: Debug (avc_musicsubunit.cpp)[  65] discover: Discovering MusicSubunit...
00104157474: Debug (avc_subunit.cpp)[ 108] discoverPlugs: Discovering plugs...
00107270363: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
00107270377: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
00107291749: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
00107291762: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
00107291773: Error (avc_plug.cpp)[ 324] discoverStreamFormat: stream format command failed
00107291780: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,12,0,1,0)
00107313414: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
00107313427: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
00107335210: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
00107335223: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
00107335235: Error (avc_plug.cpp)[ 324] discoverStreamFormat: stream format command failed
00107335242: Debug (avc_plug.cpp)[ 235] discover: Could not discover stream format (0,12,0,1,1)
00107358260: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
00107358274: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
00107358299: Debug (avc_unit.cpp)[ 366] discoverPlugs: Discovering plugs...
00107398503: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
00107398523: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
00107398528: Error (avc_unit.cpp)[ 378] discoverPlugs: plug info command failed
00107398538: Error (avc_unit.cpp)[ 182] discover: Detecting plugs failed
00107398540: Error (avc_avdevice.cpp)[ 141] discoverGeneric: Could not discover unit
00107398546: Error (devicemanager.cpp)[ 606] discover: could not discover device
00107398611: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
00107398617: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
00107398620: Debug (Element.cpp)[ 121] show: Element DeviceManager
00107398624: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00107398638: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  1 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
no message buffer overruns

```A good portion of that came up in red font:
> 
00104152507: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed

00104153085: Warning (avc_avdevice.cpp)[ 132] discover: Using generic AV/C support for unsupported device 'Loud Technologies Inc. Onyx-i'

00107270363: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries

00107270377: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed

00107291749: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries

00107291762: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed

00107291773: Error (avc_plug.cpp)[ 324] discoverStreamFormat: stream format command failed

00107313414: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries

00107313427: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed

00107335210: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries

00107335223: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed

00107335235: Error (avc_plug.cpp)[ 324] discoverStreamFormat: stream format command failed

00107358260: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries

00107358274: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed

00107398503: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries

00107398523: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed

00107398528: Error (avc_unit.cpp)[ 378] discoverPlugs: plug info command failed

00107398538: Error (avc_unit.cpp)[ 182] discover: Detecting plugs failed

00107398540: Error (avc_avdevice.cpp)[ 141] discoverGeneric: Could not discover unit

00107398546: Error (devicemanager.cpp)[ 606] discover: could not discover device

I'm not sure what "efc_avc_cmd.cpp" is and why it won't "deserialize".
Then the "avc_avdevice.cpp" apparently reverting to a generic "av/c" (?) for "unsupported" Onyx-i.
(My mixer is an "Onyx-i" Mackie.)
Then all of those "ieee1394service.cpp" errors with some "FCP transaction". Confusing.
And it couldn't even "discover generic". :-/ I'm not sure what all of this means but it doesn't look good.

---

### Post by AutoStatic on 2010-01-08
Is it possible to try the Mackie on OSX or Windows just to make sure the unit isn't broken? I had to sent my Focusrite back too, it didn't do any firmware updates and didn't run stable enough. When I got it back (I doubt itw as the same unit though) it worked flawlessly. Or maybe we're really overseeing something but we practically tried out all options possible.

---

### Post by babarosa on 2010-01-08
Hi Professor,

don't hesitate to ask for help (the firewire chip can cause problems, the debug mode, ...) at ffado-list (ffado-user@lists.sourceforge.net - List for FFADO users, intended for support), the programmers themselves and many others help you - visit [http://www.ffado.org/?q=contact](http://www.ffado.org/?q=contact)

In the meantime, some suggestions:

1)
ffado from karmic's repo is version 2.0rc2, maybe your device is better supported with the latest release candidate v2.0 (you have to compile it)

2)
In v9.10 edit (with sudo permissions) /lib/udev/rules.d/50-udev-default.rules and add this line

KERNEL=="raw1394", GROUP="video"

save the file, (make sure you're in the video group) and reboot.

AND/OR (please try, it doesn't damage your system):

Then, you have to give the access right to "/dev/raw1394" to the "video" group:

 sudo gedit /etc/udev/rules.d/65-permission-raw.rules

And make a copy/paste of this into the file:

 KERNEL=="raw1394", OWNER="root", GROUP="video", MODE="660"

Restart the workstation is necessary to get the acces right.

3)
Give both root and your_user all rights
[http://i14.servimg.com/u/f14/12/84/23/35/rights10.png](http://i14.servimg.com/u/f14/12/84/23/35/rights10.png)

and both root and members to the groups
root, your_user, audio, disk, plugdev, video
[http://i14.servimg.com/u/f14/12/84/23/35/groups10.png](http://i14.servimg.com/u/f14/12/84/23/35/groups10.png)

4)
After using xubuntu for 2 years, I made the experience, that almost all problems are solvable in GNU/Linux, but it really needs a lot of patience, tinkering time and trial and error - which is a pitty.

Good luck,
Michael

---

### Post by Th3Professor on 2010-01-09
Before I try those steps, regarding:
> AND/OR (please try, it doesn't damage your system)
Would those changes damage my system?

---

### Post by AutoStatic on 2010-01-09
No they won't. You can try but my guess is all the lines are already in your */lib/udev/rules.d/50-udev-default.rules*, the Ubuntu Studio Controls take care of that. Personally I think it's better to remove these lines from this file and to create a new file, like */etc/udev/rules.d/65-permission-raw.rules* and to add the line babarosa mentioned. Why? Any update to your system that modifies your */lib/udev/rules.d/50-udev-default.rules* may overwrite the changes made by Ubuntu Studio Controls. If you create a new file you will eliminate that possibility.

---

### Post by Th3Professor on 2010-01-09
> **AutoStatic said:**
> Is it possible to try the Mackie on OSX or Windows just to make sure the unit isn't broken? I had to sent my Focusrite back too, it didn't do any firmware updates and didn't run stable enough. When I got it back (I doubt itw as the same unit though) it worked flawlessly. Or maybe we're really overseeing something but we practically tried out all options possible.

I have a Windows system installed, I'll try that. Though I tested the Mackie with headphones and hooking mics/instruments up to the strips/channels and it worked fine. Hopefully the firewire component isn't broken.

---

### Post by Th3Professor on 2010-01-09
I'll try these modified steps and will post an update in here when I've tried them (along with testing the Mackie in Windows)...

1. Create:
[I]/etc/udev/rules.d/65-permission-raw.rules

[/I]2. Add this to it & save it:
 KERNEL=="raw1394", OWNER="root", GROUP="video", MODE="660"

3. Reboot

4. Give root & user all permissions/rights (in "Users and Groups")

5. Add root & user to groups (in "Users and Groups")

Actually, I think I've already done most of that. I didn't create that ".rules" file but I'll be sure to do that, and will update here after that.

Regarding:
> ffado from karmic's repo is version 2.0rc2, maybe your device is better supported with the latest release candidate v2.0 (you have to compile it)
I read on ffado's site that ffado v.2.0 is basically a *bad* idea right now, something about it being incompatible with things. I have ffado 1.999 or something like that right now, have been told that it's okay.

---

### Post by AutoStatic on 2010-01-09
> **Th3Professor said:**
> I read on ffado's site that ffado v.2.0 is basically a *bad* idea right now, something about it being incompatible with things. I have ffado 1.999 or something like that right now, have been told that it's okay.The version you have now *is* version 2, it's a release candidate. The problem is the new kernel Firewire stack, FFADO doesn't yet work well with it. I guess you're referring to this article: [http://ffado.org/?q=node/1316](http://ffado.org/?q=node/1316)
Don't mind the comments on 9.10, Karmic uses the old Firewire stack: [https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-October/005442.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2009-October/005442.html)

---

### Post by Th3Professor on 2010-01-09
I just checked the /etc/udev/rules.d/ directory. The "50-udev-default.rules" file does not exist. I see these:

ls -la /etc/udev/rules.d/
total 20
drwxr-xr-x 2 root root 4096 2009-12-25 17:59 .
drwxr-xr-x 3 root root 4096 2009-12-25 17:59 ..
-rw-r--r-- 1 root root  788 2009-12-25 17:22** 70-persistent-cd.rules**
-rw-r--r-- 1 root root  445 2009-12-25 17:22** 70-persistent-net.rules**
-rw-r--r-- 1 root root 1157 2009-10-16 01:01 README

---

### Post by AutoStatic on 2010-01-10
*50-udev-default-rules* is in /*lib/udev/rules.d/*
*65-permission-raw.rules* has to be created in */etc/udev/rules.d/*
All these files used to be in */etc/udev/rules.d* but from 9.04 they were moved to */lib/udev/rules.d* and the only files that remained in */etc/udev/rules.d* were the dynamic ones (*70-persistent-net.rules* contains the MAC address of your network card for example). Any udev rules you create yourself should be in */etc/udev/rules.d* too.

---

### Post by Th3Professor on 2010-01-11
Okay I made all of those changes/additions, the rules files, permissions, etc.
I turned on the mixer, restarted the computer, loaded JACK (using "freebob", ffado says that's the best bet for right now, as "firewire" driver doesn't work with Onyx-i at all), and loaded Ardour.

This is the "Ardour - log" message that popped up:
```
[WARNING]: no outputs available for auditioner - manual connection required
```I'm not sure how to manually connect.

Right now I have the following hooked up to my mixer:

Strip 1: electric guitar (hi-z)
Strip 2: bass guitar (hi-z)
Strip 3: microphone (left)
Strip 4: microphone (right)
Strip 11-12: electronic drumset (using trs instead of midi for right now)
I'd like to record my USB/MIDI M-Audio as well, though I am guessing Ardour either doesn't support (or doesn't fully support) MIDI at present.

I've tested the instruments on the mixer alone, without the computer, each instrument, and it is all working fine. It's a firewire mixer, so I have the firewire buttons enabled on all of the active strips. I have control room/phones source setup with "main mix" and "fw1-2" both enabled. All levels are adjusted and set.

I'm not sure what to do next. This is all new to me, well this equipment and software is at least. :-\

How do I set up Ardour to record from my mixer?

I've been looking at some Ardour help files online but they're a bit bloated with information. Looking for a simple quick how to for just testing the mics into the mixer into the computer into Ardour, to click "record", and get something to play back. 

On another note, I installed the generic kernel (I tested the above with rt kernel), though with generic kernel it reverted back to basic graphics. It didn't seem to recognize my graphics card. I've never seen that before. Usually it just asks me to use the proprietary drivers but at least gives me my normal screen resolution (1920x1080), though the generic kernel after booting up and logging in had very simple graphics.

---

### Post by Th3Professor on 2010-01-11
Here's an update, a ffado-test Discover -v6 

```

music@delta:~$ ffado-test Discover -v6
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

05760428619: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
05760428641: Debug (StreamProcessorManager.cpp)[1536] setVerboseLevel: Setting verbose level to 6...
05760428648: Debug (devicemanager.cpp)[1179] setVerboseLevel: Setting verbose level to 6...
05760428788: Debug (Configuration.cpp)[  63] openFile: Could not open file: ~/.ffado/configuration
05760429441: Debug (devicemanager.cpp)[ 168] initialize: Found 2 firewire adapters (ports)
05760429461: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760429469: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
05760429476: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
05760429482: Debug (IsoHandlerManager.cpp)[ 531] setThreadParameters: (0xf176e0) switch to: (rt=0, prio=1)...
05760429517: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
05760429537: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase
05760429542: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
05760429553: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
05760429561: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_xmit
05760429567: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
05760429576: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
05760429586: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_recv
05760429588: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
05760429592: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
05760429595: Debug (CycleTimerHelper.cpp)[ 231] setThreadParameters: (0xf17760) switch to: (rt=0, prio=1)...
05760429614: Debug (Watchdog.cpp)[ 200] start: (0xf17950) Starting watchdog...
05760429618: Debug (Watchdog.cpp)[ 201] start: Create hartbeat task/thread for 0xf17950...
05760429623: Debug (Watchdog.cpp)[ 215] start:  hartbeat task: 0xf179b0, thread 0xf17a20...
05760429625: Debug (Watchdog.cpp)[ 217] start: Create check task/thread for 0xf17950...
05760429630: Debug (Watchdog.cpp)[ 231] start:  check task: 0xf17a60, thread 0xf17ad0...
05760429690: Debug (Watchdog.cpp)[ 249] start: (0xf17950) Watchdog running...
05760429740: Debug (ieee1394service.cpp)[ 280] initialize: This system supports the raw1394_read_cycle_timer call, using it.
05760429782: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.min_split_timeout_usecs
05760429796: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.min_split_timeout_usecs
05760429798: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.min_split_timeout_usecs' not found
05760429806: Debug (ieee1394service.cpp)[ 917] getSplitTimeoutUsecs: reading SPLIT_TIMEOUT on node 0x1...
05760429863: Debug (ieee1394service.cpp)[ 924] getSplitTimeoutUsecs:  READ HI: 0x7FFF01000000
05760429890: Debug (ieee1394service.cpp)[ 931] getSplitTimeoutUsecs:  READ LO: 0x7FFF00000000
05760429925: Debug (ieee1394service.cpp)[ 325] initialize: Minimum SPLIT_TIMEOUT: 1000000. Current: 1000000
05760429931: Debug (CycleTimerHelper.cpp)[ 116] Start: Start 0xf17760...
05760429933: Debug (CycleTimerHelper.cpp)[ 149] initValues: (0xf17760) Init values...
05760429938: Debug (CycleTimerHelper.cpp)[ 156] initValues: Read CTR...
05760429944: Debug (CycleTimerHelper.cpp)[ 167] initValues:  read : CTR:  4283488583, local:  1263235976840767
05760429949: Debug (CycleTimerHelper.cpp)[ 173] initValues:   ctr   : 0xFF50D947  3137709383 (127s 5389cy 2375ticks)
05760429952: Debug (CycleTimerHelper.cpp)[ 179] initValues: requesting DLL re-init...
05760431017: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0xf17760) First run
05760431021: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
05760431046: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 140733198303232, m_dll_e2: 4915200.000000
05760431052: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1263235976841839.000000, next: 1263235977041839.000000
05760431061: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 3137735712.000000, next: 3142650912.000000
05760431066: Debug (CycleTimerHelper.cpp)[ 188] initValues: ready...
05760431074: Debug (Watchdog.cpp)[ 281] registerThread: (0xf17950) Adding thread 0xf19fc0
05760431121: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760431145: Debug (IsoHandlerManager.cpp)[ 572] init: Initializing ISO manager 0xf176e0...
05760431132: Debug (CycleTimerHelper.cpp)[ 195] Init: Initialize 0xf17760...
05760431164: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0xf1a130)
05760431174: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
05760431189: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase
05760431192: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
05760431203: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
05760431211: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_xmit
05760431216: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
05760431224: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
05760431234: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_recv
05760431236: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
05760431300: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
05760431309: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
05760431314: Debug (Configuration.cpp)[ 268] getValueForSetting: path 'ieee1394.isomanager.isotask_activity_timeout_usecs' not found
05760431316: Debug (IsoHandlerManager.cpp)[ 593] init: Create iso thread for 0xf176e0 transmit...
05760431320: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760431325: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
05760431330: Debug (IsoHandlerManager.cpp)[ 612] init: Create iso thread for 0xf176e0 receive...
05760431332: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760431337: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
05760431339: Debug (Watchdog.cpp)[ 281] registerThread: (0xf17950) Adding thread 0xf1a390
05760431385: Debug (Watchdog.cpp)[ 281] registerThread: (0xf17950) Adding thread 0xf1a570
05760431390: Debug (PosixThread.cpp)[ 150] Start: (ISOXMT) Create non RT thread 0xf1a390
05760431413: Debug (PosixThread.cpp)[ 150] Start: (ISORCV) Create non RT thread 0xf1a570
05760431422: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISOXMT) ThreadHandler: start 0xf1a390
05760431479: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISORCV) ThreadHandler: start 0xf1a570
05760431177: Debug (CycleTimerHelper.cpp)[ 393] Execute: (0xf17760) have to retry CTR read, diff unrealistic: diff: -7988364, max: +/- 3072 (try: 10) 0
05760431526: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
05760431531: Debug (IsoHandlerManager.cpp)[ 531] setThreadParameters: (0xf176e0) switch to: (rt=0, prio=1)...
05760431548: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
05760431581: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase
05760431588: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
05760431597: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
05760431607: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_xmit
05760431610: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
05760431620: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
05760431629: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_recv
05760431634: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
05760431635: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0xf17760) First run
05760431642: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
05760431649: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 4915200, m_dll_e2: 4915200.000000
05760431656: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1263235976842458.000000, next: 1263235977042458.000000
05760431661: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 3137750926.000000, next: 3142666126.000000
05760431636: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISOXMT, 0xf1a390) Drop realtime
05760431756: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISORCV, 0xf1a570) Drop realtime
05760431774: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
05760431778: Debug (CycleTimerHelper.cpp)[ 231] setThreadParameters: (0xf17760) switch to: (rt=0, prio=1)...
05760431784: Debug (PosixThread.cpp)[ 230] DropRealTime: (CTRHLP, 0xf19fc0) Drop realtime
05760431790: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0xf1a990)
05760431802: Debug (CycleTimerHelper.cpp)[  61] CycleTimerHelper: Create 0xf1aa50...
05760431808: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760431813: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
05760431817: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
05760431822: Debug (IsoHandlerManager.cpp)[ 531] setThreadParameters: (0xf1a9d0) switch to: (rt=0, prio=1)...
05760431833: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
05760431844: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase
05760431846: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
05760431857: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
05760431906: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_xmit
05760431912: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
05760431921: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
05760431932: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_recv
05760431935: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
05760431940: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
05760431942: Debug (CycleTimerHelper.cpp)[ 231] setThreadParameters: (0xf1aa50) switch to: (rt=0, prio=1)...
05760432011: Debug (Watchdog.cpp)[ 200] start: (0xf1ac40) Starting watchdog...
05760432014: Debug (Watchdog.cpp)[ 201] start: Create hartbeat task/thread for 0xf1ac40...
05760432021: Debug (Watchdog.cpp)[ 215] start:  hartbeat task: 0xf19f20, thread 0xf1acc0...
05760432023: Debug (Watchdog.cpp)[ 217] start: Create check task/thread for 0xf1ac40...
05760432028: Debug (Watchdog.cpp)[ 231] start:  check task: 0xf1ad00, thread 0xf1ad70...
05760432030: Debug (PosixThread.cpp)[ 193] AcquireRealTime: (WDGCHK, 0xf1ad70) Aquire realtime, prio 98
05760432035: Debug (PosixThread.cpp)[ 150] Start: (WDGHBT) Create non RT thread 0xf1acc0
05760432064: Debug (PosixThread.cpp)[ 150] Start: (WDGCHK) Create non RT thread 0xf1ad70
05760432140: Debug (Watchdog.cpp)[ 249] start: (0xf1ac40) Watchdog running...
05760432150: Debug (PosixThread.cpp)[  76] ThreadHandler: (WDGCHK) ThreadHandler: start 0xf1ad70
05760432210: Debug (ieee1394service.cpp)[ 280] initialize: This system supports the raw1394_read_cycle_timer call, using it.
05760432143: Debug (PosixThread.cpp)[  76] ThreadHandler: (WDGHBT) ThreadHandler: start 0xf1acc0
05760432244: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.min_split_timeout_usecs
05760432361: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.min_split_timeout_usecs
05760432369: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.min_split_timeout_usecs' not found
05760432374: Debug (ieee1394service.cpp)[ 917] getSplitTimeoutUsecs: reading SPLIT_TIMEOUT on node 0x0...
05760432417: Debug (ieee1394service.cpp)[ 924] getSplitTimeoutUsecs:  READ HI: 0x7FFF01000000
05760432427: Debug (ieee1394service.cpp)[ 931] getSplitTimeoutUsecs:  READ LO: 0x7FFF00000000
05760432432: Debug (ieee1394service.cpp)[ 325] initialize: Minimum SPLIT_TIMEOUT: 1000000. Current: 1000000
05760432434: Debug (CycleTimerHelper.cpp)[ 116] Start: Start 0xf1aa50...
05760432438: Debug (CycleTimerHelper.cpp)[ 149] initValues: (0xf1aa50) Init values...
05760432440: Debug (CycleTimerHelper.cpp)[ 156] initValues: Read CTR...
05760432445: Debug (CycleTimerHelper.cpp)[ 167] initValues:  read : CTR:  4270002550, local:  1263235976843269
05760432448: Debug (CycleTimerHelper.cpp)[ 173] initValues:   ctr   : 0xFE831176  3127594358 (127s 2097cy 0374ticks)
05760432452: Debug (CycleTimerHelper.cpp)[ 179] initValues: requesting DLL re-init...
05760433510: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0xf1aa50) First run
05760433514: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
05760433521: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 140733198303232, m_dll_e2: 4915200.000000
05760433528: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1263235976844332.000000, next: 1263235977044332.000000
05760433532: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 3127620496.000000, next: 3132535696.000000
05760433538: Debug (CycleTimerHelper.cpp)[ 188] initValues: ready...
05760433542: Debug (Watchdog.cpp)[ 281] registerThread: (0xf1ac40) Adding thread 0xf2d8b0
05760433549: Debug (PosixThread.cpp)[ 150] Start: (CTRHLP) Create non RT thread 0xf2d8b0
05760433572: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760433587: Debug (IsoHandlerManager.cpp)[ 572] init: Initializing ISO manager 0xf1a9d0...
05760433580: Debug (CycleTimerHelper.cpp)[ 195] Init: Initialize 0xf1aa50...
05760433599: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0xf2da20)
05760433601: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
05760433613: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase
05760433615: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
05760433626: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
05760433634: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_xmit
05760433639: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
05760433647: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
05760433658: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_recv
05760433660: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
05760433671: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
05760433679: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.isotask_activity_timeout_usecs
05760433685: Debug (Configuration.cpp)[ 268] getValueForSetting: path 'ieee1394.isomanager.isotask_activity_timeout_usecs' not found
05760433687: Debug (IsoHandlerManager.cpp)[ 593] init: Create iso thread for 0xf1a9d0 transmit...
05760433691: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760433694: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
05760433698: Debug (IsoHandlerManager.cpp)[ 612] init: Create iso thread for 0xf1a9d0 receive...
05760433700: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760433704: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
05760433602: Debug (PosixThread.cpp)[  76] ThreadHandler: (CTRHLP) ThreadHandler: start 0xf2d8b0
05760433715: Debug (CycleTimerHelper.cpp)[ 393] Execute: (0xf1aa50) have to retry CTR read, diff unrealistic: diff: -18102452, max: +/- 3072 (try: 10) 0
05760433706: Debug (Watchdog.cpp)[ 281] registerThread: (0xf1ac40) Adding thread 0xf2dc80
05760433815: Debug (Watchdog.cpp)[ 281] registerThread: (0xf1ac40) Adding thread 0xf2de60
05760433818: Debug (PosixThread.cpp)[ 150] Start: (ISOXMT) Create non RT thread 0xf2dc80
05760433837: Debug (PosixThread.cpp)[ 150] Start: (ISORCV) Create non RT thread 0xf2de60
05760433836: Debug (CycleTimerHelper.cpp)[ 308] initDLL:  (0xf1aa50) First run
05760433865: Debug (CycleTimerHelper.cpp)[ 310] initDLL:   DLL bandwidth: 0.500000 Hz (rel: 0.100000)
05760433869: Debug (CycleTimerHelper.cpp)[ 313] initDLL:   usecs/update: 200000, ticks/update: 4915200, m_dll_e2: 4915200.000000
05760433876: Debug (CycleTimerHelper.cpp)[ 316] initDLL:   usecs current: 1263235976844658.000000, next: 1263235977044658.000000
05760433882: Debug (CycleTimerHelper.cpp)[ 319] initDLL:   ticks current: 3127628520.000000, next: 3132543720.000000
05760433904: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISORCV) ThreadHandler: start 0xf2de60
05760433918: Debug (ieee1394service.cpp)[ 377] setThreadParameters: Switching IsoManager to (rt=0, prio=1)
05760433925: Debug (IsoHandlerManager.cpp)[ 531] setThreadParameters: (0xf1a9d0) switch to: (rt=0, prio=1)...
05760433937: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase
05760433948: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase
05760433950: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase' not found
05760433960: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_xmit
05760433968: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_xmit
05760433973: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_xmit' not found
05760433851: Debug (PosixThread.cpp)[  76] ThreadHandler: (ISOXMT) ThreadHandler: start 0xf2dc80
05760434000: Debug (Configuration.cpp)[ 307] getSetting:   temporary has no setting ieee1394.isomanager.prio_increase_recv
05760434010: Debug (Configuration.cpp)[ 307] getSetting:   /usr/share/libffado1//configuration has no setting ieee1394.isomanager.prio_increase_recv
05760434015: Debug (Configuration.cpp)[ 247] getValueForSetting: path 'ieee1394.isomanager.prio_increase_recv' not found
05760434017: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISOXMT, 0xf2dc80) Drop realtime
05760434025: Debug (PosixThread.cpp)[ 230] DropRealTime: (ISORCV, 0xf2de60) Drop realtime
05760434027: Debug (ieee1394service.cpp)[ 383] setThreadParameters: Switching CycleTimerHelper to (rt=0, prio=1)
05760434031: Debug (CycleTimerHelper.cpp)[ 231] setThreadParameters: (0xf1aa50) switch to: (rt=0, prio=1)...
05760434033: Debug (PosixThread.cpp)[ 230] DropRealTime: (CTRHLP, 0xf2d8b0) Drop realtime
05760434043: Debug (ieee1394service.cpp)[1076] addBusResetHandler: Adding busreset handler (0xf2e280)
05760434046: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
05760434051: Debug (StreamProcessorManager.cpp)[1536] setVerboseLevel: Setting verbose level to 6...
05760434053: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
05760434057: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434059: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
05760434062: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434064: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760434068: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
05760434072: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
05760434075: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434077: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
05760434080: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434082: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760434085: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
05760434087: Debug (devicemanager.cpp)[1179] setVerboseLevel: Setting verbose level to 6...
05760434098: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
05760434105: Debug (Element.cpp)[ 129] setVerboseLevel: Setting verbose level to 6...
05760434109: Debug (StreamProcessorManager.cpp)[1536] setVerboseLevel: Setting verbose level to 6...
05760434111: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
05760434149: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434151: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
05760434156: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434157: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760434161: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
05760434163: Debug (Thread.h)[ 124] setVerboseLevel: (ISOXMT) Setting verbose level to 6...
05760434167: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434169: Debug (Thread.h)[ 124] setVerboseLevel: (ISORCV) Setting verbose level to 6...
05760434172: Debug (IsoHandlerManager.cpp)[ 448] setVerboseLevel: Setting verbose level to 6...
05760434174: Debug (IsoHandlerManager.cpp)[1131] setVerboseLevel: Setting verbose level to 6...
05760434177: Debug (ieee1394service.cpp)[1365] setVerboseLevel: Setting verbose level to 6...
05760434179: Debug (devicemanager.cpp)[1179] setVerboseLevel: Setting verbose level to 6...
05760434189: Debug (devicemanager.cpp)[ 359] discover: Probing node 0...
05761484389: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05762535388: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05763586025: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05764637028: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05765688266: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05765690381: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
05765690393: Debug (devicemanager.cpp)[ 376] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
05765690403: Debug (devicemanager.cpp)[ 359] discover: Probing node 1...
05765690405: Debug (devicemanager.cpp)[ 362] discover: Skipping local node (1)...
05765690412: Debug (devicemanager.cpp)[ 359] discover: Probing node 0...
05765690414: Debug (devicemanager.cpp)[ 362] discover: Skipping local node (0)...
05765690420: Debug (DeviceStringParser.cpp)[ 391] show: DeviceStringParser: 0xf16680
05765690429: Debug (devicemanager.cpp)[ 534] discover: Probing node 0...
05766740016: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05767791393: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05768842020: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05769893393: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05770944021: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 1
05770946145: Error (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
05770946164: Debug (devicemanager.cpp)[ 551] discover: Could not read config rom from device (node id 0). Skip device discovering for this node
05770946169: Debug (devicemanager.cpp)[ 534] discover: Probing node 1...
05770946175: Debug (devicemanager.cpp)[ 537] discover: Skipping local node (1)...
05770946178: Debug (devicemanager.cpp)[ 534] discover: Probing node 0...
05770946184: Debug (devicemanager.cpp)[ 537] discover: Skipping local node (0)...
05770946186: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
05770946195: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
05770946201: Debug (Element.cpp)[ 121] show: Element DeviceManager
05770946207: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
05770946213: Debug (ieee1394service.cpp)[1380] show: Port:  0
05770946222: Debug (ieee1394service.cpp)[1381] show:  Name: ohci1394
05770946224: Debug (ieee1394service.cpp)[1383] show:  CycleTimerHelper: 0xf17760, IsoManager: 0xf176e0, WatchDog: 0xf17950
05770946228: Debug (ieee1394service.cpp)[1388] show:  Time: 00250467374 (010s 1532cy 1070ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
05770946239: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  1 ---
05770946243: Debug (ieee1394service.cpp)[1380] show: Port:  1
05770946247: Debug (ieee1394service.cpp)[1381] show:  Name: ohci1394
05770946249: Debug (ieee1394service.cpp)[1383] show:  CycleTimerHelper: 0xf1aa50, IsoManager: 0xf1a9d0, WatchDog: 0xf1ac40
05770946253: Debug (ieee1394service.cpp)[1388] show:  Time: 00240275802 (009s 6214cy 2394ticks)
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
05770946274: Debug (Configuration.cpp)[ 138] save: Not saving temporary config file: temporary
05770946279: Debug (Configuration.cpp)[ 135] save: Not saving readonly config file: /usr/share/libffado1//configuration
05770946303: Debug (IsoHandlerManager.cpp)[1068] stopHandlers: enter...
05770946309: Debug (IsoHandlerManager.cpp)[ 936] pruneHandlers: enter...
05770946315: Debug (PosixThread.cpp)[ 178] Stop: (ISOXMT) Stop 0xf1a390 (thread: 0x7f0810224910)
05770950116: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISOXMT) ThreadHandler: exit 0xf1a390
05770950168: Debug (PosixThread.cpp)[ 182] Stop: (ISOXMT) Stopped 0xf1a390 (thread: 0x7f0810224910)
05770950173: Debug (PosixThread.cpp)[ 178] Stop: (ISORCV) Stop 0xf1a570 (thread: 0x7f080fa23910)
05770950613: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISORCV) ThreadHandler: exit 0xf1a570
05770950625: Debug (PosixThread.cpp)[ 182] Stop: (ISORCV) Stopped 0xf1a570 (thread: 0x7f080fa23910)
05770950646: Debug (PosixThread.cpp)[ 178] Stop: (CTRHLP) Stop 0xf19fc0 (thread: 0x7f0810a25910)
05771031696: Debug (PosixThread.cpp)[  86] ThreadHandler: (CTRHLP) ThreadHandler: exit 0xf19fc0
05771031731: Debug (PosixThread.cpp)[ 182] Stop: (CTRHLP) Stopped 0xf19fc0 (thread: 0x7f0810a25910)
05771031736: Debug (ieee1394service.cpp)[1084] remBusResetHandler: Removing busreset handler (0xf1a130)
05771031741: Debug (ieee1394service.cpp)[1091] remBusResetHandler:  found
05771031865: Debug (PosixThread.cpp)[ 164] Kill: (WDGCHK) Kill 0xf17ad0 (thread: 0x7f0811226910)
05771031984: Debug (PosixThread.cpp)[ 168] Kill: (WDGCHK) Killed 0xf17ad0 (thread: 0x7f0811226910)
05771031991: Debug (PosixThread.cpp)[ 164] Kill: (WDGHBT) Kill 0xf17a20 (thread: 0x7f0811a27910)
05771032040: Debug (PosixThread.cpp)[ 168] Kill: (WDGHBT) Killed 0xf17a20 (thread: 0x7f0811a27910)
05771032061: Debug (IsoHandlerManager.cpp)[1068] stopHandlers: enter...
05771032068: Debug (IsoHandlerManager.cpp)[ 936] pruneHandlers: enter...
05771032070: Debug (PosixThread.cpp)[ 178] Stop: (ISOXMT) Stop 0xf2dc80 (thread: 0x7f080d21e910)
05771041770: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISOXMT) ThreadHandler: exit 0xf2dc80
05771041801: Debug (PosixThread.cpp)[ 182] Stop: (ISOXMT) Stopped 0xf2dc80 (thread: 0x7f080d21e910)
05771041808: Debug (PosixThread.cpp)[ 178] Stop: (ISORCV) Stop 0xf2de60 (thread: 0x7f080ca1d910)
05771045363: Debug (PosixThread.cpp)[  86] ThreadHandler: (ISORCV) ThreadHandler: exit 0xf2de60
05771045408: Debug (PosixThread.cpp)[ 182] Stop: (ISORCV) Stopped 0xf2de60 (thread: 0x7f080ca1d910)
05771045420: Debug (PosixThread.cpp)[ 178] Stop: (CTRHLP) Stop 0xf2d8b0 (thread: 0x7f080da1f910)
05771233885: Debug (PosixThread.cpp)[  86] ThreadHandler: (CTRHLP) ThreadHandler: exit 0xf2d8b0
05771233933: Debug (PosixThread.cpp)[ 182] Stop: (CTRHLP) Stopped 0xf2d8b0 (thread: 0x7f080da1f910)
05771233940: Debug (ieee1394service.cpp)[1084] remBusResetHandler: Removing busreset handler (0xf2da20)
05771233943: Debug (ieee1394service.cpp)[1091] remBusResetHandler:  found
05771234051: Debug (PosixThread.cpp)[ 164] Kill: (WDGCHK) Kill 0xf1ad70 (thread: 0x7f080e220910)
05771234113: Debug (PosixThread.cpp)[ 168] Kill: (WDGCHK) Killed 0xf1ad70 (thread: 0x7f080e220910)
05771234121: Debug (PosixThread.cpp)[ 164] Kill: (WDGHBT) Kill 0xf1acc0 (thread: 0x7f080ea21910)
05771234183: Debug (PosixThread.cpp)[ 168] Kill: (WDGHBT) Killed 0xf1acc0 (thread: 0x7f080ea21910)
05771234213: Debug (test-ffado.cpp)[ 190] exitfunction: Debug output flushed...
no message buffer overruns
music@delta:~$ 

```

EDIT-
Update. I haven't packed it and sent it back yet, but I'm possibly going to soon send the Mackie Onyx 1220i FireWire mixer back to the dealer. While Onyx is supported, it appears that at present Onyx-i is not supported. I have a few more days on the 30-day warranty, so I'll wait another day or two to see if there are any solutions. Otherwise, I'm going to send the board back, get an all analog mixer, and a PCI/PCIe audio interface.

---

### Post by AutoStatic on 2010-01-11
[http://ffado.org/?q=node/85#comment-428](http://ffado.org/?q=node/85#comment-428)
> The Onyx-i mixers are NOT supported at present. They might or might not work, and it might or might not be due to the controller.

A VT6306 based host controller should work, but there are no guarantees.
We tried a VT6306 chipset so I think we're more or less out of options. If it works in Windows then it's most definitely unsupported by FFADO and then you should really consider returning it if you want to continue working with Ubuntu. Which I hope you will because things like this consume a lot of time and energy :(

---

### Post by Th3Professor on 2010-01-12
Well, the 1220i is packed up, it's going back to the dealer tomorrow. :(

I'm doing some fresh digging now on alternative gear:
[http://ubuntuforums.org/showthread.php?t=1378476](http://ubuntuforums.org/showthread.php?t=1378476)

Hopefully I'll find a suitable solution. :)

---

