---
title: "Hissing noise - M-audio delta 1010LT"
date: 2015-08-19
forum: Ubuntu Studio
---

### Post by eamner on 2015-08-19
Hi. I've been searching for a solution for this issue but I haven't found any.
I have a M-audio delta 1010LT in a Kubuntu 14.04 system. Actually I have a dual boot Kubuntu/Windows 7.
There seems to be a random annoying hissing noise that I've noticed in both my speakers and my headphones. I was thinking that my headphones were damaged until I noticed it also happened with the speakers.
The noise is not permanent. Only happens sometimes, no matter what I'm doing, watching videos, listening to music, etc. AND I can only hear it on one side (left).
However, this doesn't happen in WIndows. Only in Kubuntu. That's why I think the problem is not the sound card. It has to do something with the drivers, or the system. In windows I get sound on Line 1/2. In kubuntu I get it through DAC/DAC1. Everything else is silenced in Alsamixer.
I was so desperate to fix it, that I took the radical measure of reinstalling the whole Kubuntu. I did. But the issue remains.
After reinstalling I tested the OSS drivers, but I really didn't like it since they seem to limit what I can do. I prefer ALSA. So I reinstalled ALSA before testing if the noise happens with OSS... By the way after installing OSS and uninstalling it again, I had to find out how to go back to ALSA. It took me a while to discover that OSS had blacklisted snd-ice1712 so I had to re-enable it.
Now I haven't installed much in my fresh kubuntu. I still haven't installed Jack or anything related to making music, because I want to fix this before working with music again. I'm not sure when the issue began, probably after I upgraded to 14.04.

Some info:
```

eric@eric-home:~$ cat /proc/asound/cards 
 0 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0xec00, irq 17

```

```

eric@eric-home:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

eric@eric-home:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=M1010LT
    M Audio Delta 1010LT, ICE1712 multi
    Default Audio Device
front:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    Front speakers
surround40:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    Direct sample mixing device
dsnoop:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    Direct sample snooping device
hw:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    Direct hardware device without any conversions
plughw:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    Hardware device with all software conversions

```

Hope somebody can help me.
Thx.

---

### Post by tgalati4 on 2015-08-19
Some hissing could be due to CPU load.  Run *top* in a terminal and see if the CPU load is high during the hissing episodes.  Those M-Audio cards are generally quiet with decent gain performance.  So if the card works correctly in Windows, I would presume it is a linux software issue.  Also uncheck microphone boost.  There could be a signal bleed.

---

### Post by eamner on 2015-08-20
> **tgalati4 said:**
> Some hissing could be due to CPU load.  Run *top* in a terminal and see if the CPU load is high during the hissing episodes.  Those M-Audio cards are generally quiet with decent gain performance.  So if the card works correctly in Windows, I would presume it is a linux software issue.  Also uncheck microphone boost.  There could be a signal bleed.

Hello. This is my top in a 'normal' moment:
```

top - 20:41:42 up 13 min,  3 users,  load average: 0.12, 0.29, 0.28
Tasks: 177 total,   1 running, 175 sleeping,   0 stopped,   1 zombie
%Cpu(s):  1.7 us,  0.4 sy,  0.0 ni, 97.2 id,  0.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   1993472 total,  1636372 used,   357100 free,    62396 buffers
KiB Swap:  5858300 total,        0 used,  5858300 free.   629140 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                  
 2664 eric      20   0  119820  40192  31712 S   3.3  2.0   0:01.10 konsole                  
 1006 root      20   0   96432  72676  35440 S   2.7  3.6   0:21.84 Xorg                     
 1917 eric      20   0  384936 122452  70044 S   1.7  6.1   0:16.72 kwin                     
 2175 eric      20   0  968848 175708  87544 S   1.0  8.8   0:23.22 chrome                   
 2552 eric      20   0  390032 115084  64584 S   1.0  5.8   0:16.05 chrome                   
 1928 eric      20   0  590708 187728  90848 S   0.7  9.4   0:27.23 plasma-desktop           
  935 root      20   0    2200   1484   1356 S   0.3  0.1   0:00.86 acpid                    
 2565 eric      20   0  326508  95584  42868 S   0.3  4.8   0:10.37 chrome                   
    1 root      20   0    4584   3736   2608 S   0.0  0.2   0:01.38 init                     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                 
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.14 ksoftirqd/0              
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H             
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.62 rcu_sched                
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                   
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.04 migration/0              
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0               
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1               

```

...and this is when it starts:
```

top - 21:58:58 up  1:31,  3 users,  load average: 0.60, 0.98, 1.66
Tasks: 189 total,   3 running, 185 sleeping,   0 stopped,   1 zombie
%Cpu(s): 16.6 us,  2.6 sy,  0.0 ni, 80.7 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   1993472 total,  1753800 used,   239672 free,    68808 buffers
KiB Swap:  5858300 total,    12084 used,  5846216 free.   538772 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                  
 2964 eric      20   0  469564 203592  96472 S  47.6 10.2   4:04.59 vlc                      
 1006 root      20   0  234960 133956  89836 R  16.0  6.7   3:43.27 Xorg                     
 1917 eric      20   0  480604 115800  54136 R   5.7  5.8   2:18.15 kwin                     
 2650 eric      20   0  361868  92248  55284 S   5.3  4.6   2:53.86 chrome                   
 2664 eric      20   0  120368  36496  27712 S   4.7  1.8   0:09.30 konsole                  
 2013 eric       9 -11  166244   7676   5908 S   2.0  0.4   0:32.51 pulseaudio               
 2210 eric      20   0  353788 136276  53820 S   1.3  6.8   1:40.17 chrome                   
 2175 eric      20   0  681476 147000  51940 S   0.7  7.4   1:36.47 chrome                   
  935 root      20   0    2200    900    800 S   0.3  0.0   0:03.77 acpid                    
 1928 eric      20   0  605388 171004  58472 S   0.3  8.6   2:44.54 plasma-desktop           
 2001 eric      20   0  312040  73192  36496 S   0.3  3.7   0:02.66 krunner                  
 2877 root      20   0       0      0      0 S   0.3  0.0   0:00.01 kworker/3:2              
 2879 root      20   0       0      0      0 S   0.3  0.0   0:00.23 kworker/1:0              
 3010 eric      20   0    5428   2456   2056 R   0.3  0.1   0:02.64 top                      
    1 root      20   0    4584   1528   1252 S   0.0  0.1   0:01.38 init                     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                 
    3 root      20   0       0      0      0 S   0.0  0.0   0:01.44 ksoftirqd/0              


```

(obviously here I had a few more things loaded, like VLC to play a video).

Regarding Mic Boost, I don't see that option in alsamixer. But everything other than DAC/DAC1 is muted. I must mention that I don't have or use any microphone.

---

### Post by tgalati4 on 2015-08-21
Can you record the hiss with *audacity*?  If so, you can run an analysis of it to see what the dominant frequencies are to help determine where it might be coming from.

Try running *mplayer* in a terminal window and see if you get hiss.

```
sudo apt-get install mplayer2
mplayer anymusicfile.mp3
```

Control-C or "q" to quit.

---

### Post by CrocoDuck on 2015-08-21
Good hints from tgalati4. Just a quick though: there is a remote possibility of the issue being caused by some weird beating/intermodulation thing with hardware clocks and timers. Have a look at your [timers status]("http://wiki.linuxaudio.org/wiki/system_configuration#timers").

---

### Post by eamner on 2015-08-21
> **tgalati4 said:**
> Can you record the hiss with *audacity*?  If so, you can run an analysis of it to see what the dominant frequencies are to help determine where it might be coming from.

Try running *mplayer* in a terminal window and see if you get hiss.



Hi. Sorry about the delay.. I work all day and I can only test at night.
I did the recording with mplayer, first using ALSA in audacity, and then I did the same using Jack (I just installed it). After recording, there was some noticeable noise. 
Then, I took the same recorded files to windows. No noise. No hiss. At least not that I noticed. I'll try to upload the recordings to soundcloud tomorrow so you can hear them.
Then I came back to linux, and at first I didn't hear noise but then at the few minutes it started again. As I said before it seems to be random.
This means the noise was not recorded. It's only at playback (output).
Not sure how to do an analysis. I don't know exactly how to do it. Any suggestion?

@CrocoDuck I did the changes suggested in your link. Raised the max freq values from 64 to 3072 and rebooted. No change at all.

---

### Post by marseille2 on 2015-08-22
Just a thought, not a solution ... if it's not hardware or ALSA, spot check pulseaudio -- by killing it and just using JACK and ALSA to troubleshoot. There's been a common PA bug that produces evil playback distortion for a while -- at least as far back as 10.04. There's some fixes (like [this]("http://askubuntu.com/questions/476031/sound-distortion-in-ubuntu-14-04")) ... but I found them to be hit or miss.

---

### Post by CrocoDuck on 2015-08-22
> **eamner said:**
> @CrocoDuck I did the changes suggested in your link. Raised the max freq values from 64 to 3072 and rebooted. No change at all.

Dang.

> **eamner said:**
> [COLOR=#000000]Not sure how to do an analysis. I don't know exactly how to do it. Any suggestion?[/COLOR]

I would look at the frequency content. [This]("http://www.baudline.com/") should be helpful. I will look at it as soon as you upload the thing online.

I think the exact source of the problem will be very hard to spot and probably marseille2 is right: try to strip the audio chain and see what happens. Definitely worth to disable pulsaudio for test purposes. Also, this reminds me of a problem I had when a new version of an USB kernel driver was released. Maybe the issue is generated by cards communicating on the same bus of your Delta. You could try to remove/disable other soundcards (if any) and networking cards and in general any piece of hardware you don't need. A section of the page I linked gives instructions about disabling what you don't need. If you give the output of this

```
lspci -vnn
```

we will see the hardware you have and the kernel drivers in use for them.

 Another idea: you could try a live media of an older (or just different) audio distro and see if you still have the problem. If not, by comparing configuration, we could spot the source.

---

### Post by eamner on 2015-08-22
Ok here are a couple mp3s that I recorded. I hope soundcloud doesn't take them down... ;-)
The first one with mplayer/Alsa:
[https://soundcloud.com/eric-m-n-65850882/far](https://soundcloud.com/eric-m-n-65850882/far)

The second one with Jack:
[https://soundcloud.com/eric-m-n-65850882/walking/s-3K0Ew](https://soundcloud.com/eric-m-n-65850882/walking/s-3K0Ew)

@CrokoDuck can you take a listen to it? As I said, I took those files to windows and I didn't notice any noise, but I'm no expert analyzing sound.
> **CrocoDuck said:**
>  If you give the output of this

```
lspci -vnn
```

we will see the hardware you have and the kernel drivers in use for them.


Here it is:
```

eric@eric-home:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 12)
        Subsystem: Biostar Microtech Int'l Corp Device [1565:110b]
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0041] (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fa000000-fbdfffff
        Prefetchable memory behind bridge: 00000000d6000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20 [EHCI])
        Subsystem: Biostar Microtech Int'l Corp Device [1565:3107]
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 7c000000-7c1fffff
        Prefetchable memory behind bridge: 000000007c200000-000000007c3fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fbe00000-fbefffff
        Prefetchable memory behind bridge: 000000007c400000-000000007c5fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fbf00000-fbffffff
        Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20 [EHCI])
        Subsystem: Biostar Microtech Int'l Corp Device [1565:3107]
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f9ffa000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b06] (rev 06)
        Subsystem: Biostar Microtech Int'l Corp Device [1565:3107]
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: lpc_ich

00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Biostar Microtech Int'l Corp Device [1565:5206]
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4
        I/O ports at 0170 [size=8]
        I/O ports at 0374
        I/O ports at ff90 [size=16]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
        Subsystem: Biostar Microtech Int'l Corp Device [1565:3107]
        Flags: medium devsel, IRQ 3
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0400 [size=32]

00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06) (prog-if 85 [Master SecO PriO])
        Subsystem: Biostar Microtech Int'l Corp Device [1565:5206]
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at a880 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at a480 [size=8]
        I/O ports at a400 [size=4]
        I/O ports at a080 [size=16]
        I/O ports at a000 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
        Subsystem: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32]
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at f9ff6000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 660] [10de:11c0] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:354e]
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (64-bit, prefetchable) [size=128M]
        Memory at d6000000 (64-bit, prefetchable) [size=32M]
        I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at fbd80000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation GK106 HDMI Audio Controller [10de:0e0b] (rev a1)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:354e]
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at fbd7c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

03:00.0 IDE interface [0101]: VIA Technologies, Inc. VT6415 PATA IDE Host Controller [1106:0415] (prog-if 85 [Master SecO PriO])
        Subsystem: VIA Technologies, Inc. VT6415 PATA IDE Host Controller [1106:0415]
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at c480 [size=4]
        I/O ports at c400 [size=16]
        Expansion ROM at fbef0000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: pata_via

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
        Subsystem: Biostar Microtech Int'l Corp Device [1565:2309]
        Flags: bus master, fast devsel, latency 0, IRQ 41
        I/O ports at d800 [size=256]
        Memory at f8fff000 (64-bit, prefetchable) [size=4K]
        Memory at f8ff8000 (64-bit, prefetchable) [size=16K]
        Expansion ROM at fbfe0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169

05:06.0 Multimedia audio controller [0401]: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller [1412:1712] (rev 02)
        Subsystem: VIA Technologies Inc. M-Audio Delta 1010LT [1412:d63b]
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at ec00 [size=32]
        I/O ports at e880 [size=16]
        I/O ports at e800 [size=16]
        I/O ports at e480 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: snd_ice1712

```

**Question:** how do I really know I'm using pulseaudio? See, I'm not a technical expert, I just like doing music in the computer... but I did a 'killall pulseaudio' (and prevented it from reloading by changing to 'autospawn=no' in the client configuration) as @marseille2 suggested. Then I played a mp3, with and without jack, and there's no difference...  

I'll try the live media idea tomorrow. I think I have an old 12.04 cd somewhere...

Thanks for your support.

---

### Post by tgalati4 on 2015-08-22
I didn't hear any hiss in either Soundcloud track.  

To analyze the noise, you need to create a blank sound track for 30 seconds--just generate a quiet track in audacity.  Then playback the track using another device like your phone or mp3 player and record it on your computer using a cable into your microphone jack.  Then highlight the track in audacity and use the analysis tools to perform a frequency analysis.  If the hiss is over 17kHz, then it could be computer noise, because mp3's generally cut off at 17 kHz.

So it could be a timing/clock issue, or a *pulseaudio* glitch, but that sounds jittery can causes distortion, not necessarily hiss.

Although it's a pain, it might be helpful to change slots for your M-audio card and rerun your tests.

---

### Post by marseille2 on 2015-08-23
This is where you can see that pulseaudio is on (from your initial output where problem started):

```
2013 eric       9 -11  166244   7676   5908 S   2.0  0.4   0:32.51 pulseaudio
```

But Crocodoc's advice is important ... since it seems others have had [problems]("https://www.google.com/search?q=m-audio+delta+1010LT+ubuntu+crackling+distortion&oq=m-audio+delta+1010LT+ubuntu+crackling+distortion&aqs=chrome..69i57.10113j0j7&sourceid=chrome&es_sm=93&ie=UTF-8") with IRQ sharing for a long time (ardour offered some fixes here > [link]("https://community.ardour.org/node/4325")). Check out this launchpad [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/814426"), too. One person said:

> [COLOR=#333333][FONT=monospace]Also, the current &#8220;best workaround&#8221; is intel_idle.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]max_cstate=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3. The reason nohz=off works is that it disables all cstates, but as long as we limit to c3 there is no apparent problem.[/FONT][/COLOR]...

I think they were blaming the kernel... but read the thread for better context.

Hope you solve this one.

---

### Post by CrocoDuck on 2015-08-23
I see you have an Nvidia audio device with HDMI output. In the past the audio capabilities of soundcards proven to be problematic, especially when using proprietary drivers + lowlatency/realtime kernels. If it is possible, you can try to disable the hdmi output (check your device manual) and/or try the open source video driver. If your videocard is fairly old chances are that the generic driver or the nouveau driver could work good. I will point you to [Arch linux documentation]("https://wiki.archlinux.org/index.php/NVIDIA") as it is more up to date. Still, you may wish to try simpler (and maybe more related) things before, like the ones suggested by tgalati4 and marseille2.

I am listening to your samples and having a look at them. However, I can hardly spot things.

Describe better this hiss: is it a background noise? If so, I couldn't spot anything clearly separable from the background, probably because the audio track covering it. I would suggest, as tgalati4 said, to make a very long silence track with Audacity, and then play it while recording the output. If it is long we have good chances to see noise events and understand its characteristics.

Or, is the hiss a kind of distortion that alters the quality of your playback? If so, I can try to make a higher order statistics analysis with [octave]("https://gnu.org/software/octave/") of your tracks and try to spot interacting frequencies. Regularities in them can point out if we are facing distortion products from hardware or digital errors of some sort. As this requires time, I will do it only if you think the output is distorted. If so, I am not sure about when I will be able to came back with the results, probably few days or a week, as I am very busy...

If I am not wrong, your sound card should have hardware jumpers used to turn on/off pre-amplifiers on the single channels. Make sure they are all turned off, maybe the cause of the hiss, both as background noise or as distortion, could be just because of that. It could happen that you have noticed on Linux only because chance or weird and unknown reasons.

---

### Post by eamner on 2015-08-23
Hi.

I didn't expect you to hear the noise, since I don't hear it under windows either. I only hear it in my kubuntu output.
Perhaps I've not expressed myself correctly. Sorry about that... english is not my native language. 
More than a hiss, it is a distorted sound, like when your speaker is broken. I looked on internet for a sound that (kind of) resembles what I hear. I found this. Not quite exact but very close:
[https://freesound.org/people/komarom/sounds/63407/](https://freesound.org/people/komarom/sounds/63407/)

Listen especially towards the end. But in my case I only hear it on my left speaker and/or headphone. 

Regarding the Nvidia card HDA device, it was disabled in BIOS. I don't even see it in the system settings anymore. 
I will try the useful suggestions you've given me. Not sure if I can change the slot of the soundcard because I don't have much space in my tower, but I'll check. I still haven't tried the live media option. I'll try it later today and come back with the result. 
But again, I long ago discarded the hardware theory, since this definitely does not happen in windows. 
Thanks.

---

### Post by CrocoDuck on 2015-08-23
> **eamner said:**
> But again, I long ago discarded the hardware theory, since this definitely does not happen in windows.

It is most probably a software issue for me as well, but keep a back-door open for the hardware thing: these issues are quirky. In fact, hardware configurations could span issues depending on the software. I am looking at your [soundcard manual]("http://godzilla.kennedykrieger.org/fmri/Delta1010LT.pdf") and seems that the jumper thing sets the input level only... so probably it will have not much to do with the issue, but still probably worth to try the lowest gain setting.

Have you tried to mess around with Envy24? It is a software mixer intended to set devices of this family. It is strange that you have the issue only on one channel and makes me wonder whether you have some kind of booster active on a channel output. [This page]("http://www.alsa-project.org/main/index.php/Delta_1010lt_Mixer") should kinda help you in sorting the controls.

---

### Post by tgalati4 on 2015-08-23
Install *mudita24* (an envy24 replacement) and run it.

```
sudo apt-get install mudita24
mudita24
```

Check the patch tab and experiment with making patches then save a working configuration as a new "profile".  If you have something connected to a noisy source, try muting that channel.

---

### Post by CrocoDuck on 2015-10-26
Hey there! I found [a thread]("http://www.linuxmusicians.com/viewtopic.php?f=6&t=14764") that could be helpful for you.

---

