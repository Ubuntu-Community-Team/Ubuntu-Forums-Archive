---
title: "High-pitched hissing noise heard in intervals - Problem analysis?"
date: 2015-11-20
forum: Ubuntu Studio
---

### Post by Megadoomer on 2015-11-20
Hello everyone,

I recently switched my little "home studio" from Windows 7 to Ubuntu Studio after using Xubuntu on my laptop for years. I managed to set up most programs to work well, however I'm getting a strange problem that I can not figure out.

Multiple times a day, I'm hearing a very loud high-pitched hissing or clipping noise for maybe half a second. It sounds a bit like white noise or a heavily overdriven signal, but it's hard to make out to be honest, since it is so short. Still, this is very irritating, especially when using headphones, as it seems the sound will always be as loud as the signal can get through my interface.

I have tried to increase buffer size and reveiwed my device settings, but I can not find a solution for this. The noise only seems to appear when there actually is some kind of signal, but regardless of the program or current activity (e.g. in the middle of playing a song while idling). There seems to be no correlation between the noise and interface drop-outs/Xruns, as I do not get any from 256 samples upwards and they will sound differently. I never experienced this issue in Windows, but I also got drop-outs with lower buffer sizes.

My system details are the following:

Ubuntu Studio 15.10
CPU: Intel Xeon E3-1231
RAM: 32 GB DDR3
Interface: M-Audio Fast Track MkII (Motherboard sound device disabled in BIOS)

I have added screenshots of my current Cadence-settings, maybe this could help.

Has anyone ever experienced something similar to this or knows what I could try for a solution or to analyse the problem further?


Best regards!

---

### Post by CrocoDuck on 2015-11-20
Do you hear it only when jack is running?

---

### Post by QDR06VV9 on 2015-11-20
Just my 2 cents worth, [COLOR=#000000]The distortion could mean that your levels are set too high, so open alsamixer from a terminal and try lowering your capture levels.[/COLOR]

---

### Post by tgalati4 on 2015-11-20
Carefully inspect the M-Audio board.  Perhaps a capacitor is failing.  Most noise issues are due to a filtering problem and capacitors are the primary filters.  It could also be noise that is leaking from the power supply of the computer.  Again, capacitors tend to be the cause.  Try swapping with a new power supply.  Test for AC leakage on your 5VDC and 12VDC lines.  Anything more than a few millivolts will cause problems.

---

### Post by Megadoomer on 2015-11-21
Hey eveyone, thanks for your quick replies!

> **CrocoDuck said:**
> Do you hear it only when jack is running?

I'm not sure about this to be honest. I will try to disable Jack for now, but testing this may take me a little while, as these noises seem kind of random and uncontrollable.

If you know non-destructive ways to encourage these glitches to happen, please tell me, then I will try that as well.

> **runrickus said:**
> Just my 2 cents worth, [COLOR=#000000]The distortion could mean that your levels are set too high, so open alsamixer from a terminal and try lowering your capture levels.[/COLOR]

The levels actually appear to be fine. This is also not the regular kind of clipping that would happen if there was a loud signal that gets distorted. They are like sudden peaks or sound glitches out of context, which can happen at random moments while playing songs or even when a movie DVD is playing and there is a dynamically silent part, which would normally almost under no circumstances clip at all (especially irritating, as imaginable).

> **tgalati4 said:**
> Carefully inspect the M-Audio board.  Perhaps a capacitor is failing.  Most noise issues are due to a filtering problem and capacitors are the primary filters.  It could also be noise that is leaking from the power supply of the computer.  Again, capacitors tend to be the cause.  Try swapping with a new power supply.

Well, I see no easy way of opening this thing and while I successfully replaced a broken capacitor in my active monitor once that had puked all over the board and almost blew up, I'm not too great with electronics. I can't rule out hardware issues completely of course, but since this problem did not exist before and started right after the OS chance, I rather assume some software issues or incompatibilities might be the reason for this.

> **tgalati4 said:**
> Test for AC leakage on your 5VDC and 12VDC lines.  Anything more than a few millivolts will cause problems.

Can you tell me how extactly this is done or do you have a link about how to test this? The PSU I'm using is a relatively new Seasonic Platinum 660 by the way.

---

### Post by tgalati4 on 2015-11-21
Just take a voltmeter and put it on AC mode.  Plug the leads, carefully, into a spare hard disk power lead and check your voltages.  There are plenty of youtube videos on how to do it.

I presume that this is not a dual-boot system, so that you can't check this behavior back in Windows.

---

### Post by CrocoDuck on 2015-11-21
> **tgalati4 said:**
> Just take a voltmeter and put it on AC mode.  Plug the leads, carefully, into a spare hard disk power lead and check your voltages.

This should work, but AC mode multimeter are not sensible to high frequencies, as they are intended to work mostly to measure power lines (50 - 60 Hz) and not signals. Low frequency hum is expected to be spanned by power sources though, but if you have some weird high frequency coupling you will not notice it with the multimeter. An oscilloscope would be ideal... but they are rather expensive... Make sure to read plenty of tutorials on these sort of things before attempting anything: the power supply will be powered on and pretty dangerous things can happen (for example, capacitor discharge). You must make sure not to touch dangerous parts or short-circuit stuff with the leads/pointers/clips... Personally, I would advice against doing that for the time being, as if you are not a little bit experienced with electronics and electronics safety you might damage your hardware or do dangerous things.

Sometimes, for internal sound-cards, noise can be spanned by other cards depending on how the system uses them. Do you have your sound-card close to the video-card? This could be highly likely a source of high frequency coupling.

Anyway, just to make clear: is the disturbance a noise, i.e. a sound superimposed to the wanted one, or a distortion, i.e. an alteration of the wanted signal?
[URL="http://ubuntuforums.org/showthread.php?t=2291409"]
This is a similar thread.[/URL]

---

### Post by Megadoomer on 2015-11-23
Thanks for your help so far!

> **tgalati4 said:**
> I presume that this is not a dual-boot system,  so that you can't check this behavior back in Windows.

Not  directly, no. As I mentioned, I still had Windows installed about two  weeks ago before I decided to completely switch to Ubuntu and for the  last ~1,5 years that I have used this audio interface, I never had any  problems like this. I would rather not switch back to Windows or  reinstall it in any way though, if avoidable. So unless my hardware did  not break in the mean time, since only the operating system was  reinstalled, which I find  highly unlikely, though not impossible, my guess is that there is more  of a software issue going on here.

> **tgalati4 said:**
> Just  take a voltmeter and put it on AC mode.  Plug the leads, carefully, into  a spare hard disk power lead and check your voltages.  There are plenty  of youtube videos on how to do it.
> **CrocoDuck said:**
> An oscilloscope would be ideal... but they are  rather expensive... Make sure to read plenty of tutorials on these sort  of things before attempting anything: the power supply will be powered  on and pretty dangerous things can happen (for example, capacitor  discharge).

Well, I'd rather not try anything like this,  personally. I have a small cheap mulimeter here for checking my guitar  pots after soldering, but nothing seriously accurate. To buy an  oscilloscope for this would make no financial sense, I could get a new  PSU and interface for that price just to test them back. ;-)

But  no, I don't have that kind of electronic experience or finesse and  unfortunately I can't think of anyone who does at the moment.

> **CrocoDuck said:**
> Do you have your sound-card close to the  video-card? This could be highly likely a source of high frequency  coupling.

This is a small USB audio interface (M-Audio  Fast Track MkII), so no it's not really near any sources of high  frequencies sitting on my desk, but if it was, I think I might have had  heard this noise a few weeks ago while using Windows as well.

> **CrocoDuck said:**
> Anyway, just to make clear: is the disturbance  a noise, i.e. a sound superimposed to the wanted one, or a distortion,  i.e. an alteration of the wanted signal?

Since I just had  a look at the other thread you linked, let me describe the problem once  again more in detail (sorry for my possibly incorrect or inaccurate  choice of words).

This "noise" is indeed more a kind of  distortion and not a "hissing" or a white noise. Like with the other person  in the liked thread, it only appears in intervals and is not always  audible. It sounds like a sudden "crack!" that can take some  milliseconds up to maybe a second (this seems to vary) in which the  normal sound is completely inaudible or at least fully distorted, then  the sound goes back to normal. It does not seem to be connected to a  certain program (it can happen while watching a DVD in VLC player, while  watching a video on Youtube or while listening to music in Amarok),  though I did not hear it without any signal being played in idle, yet.  Like I mentioned, these cracks are apparently not related to Xruns or  latency, as there is no increase in those and changing the sample rate  has not made any difference until now.

I tried to record the  sound while monitoring my output with Audacity while watching a DVD and I  could not record the sound. In fact, the recording was completely free  of this crackling sound, I stopped it right after it happened and  listened back to it in Audacity and the recording was fine - even the  part where I heard the sound live was recorded correctly (there was no  skip to be heard in the recording or anything else for that matter).

I  find it interesting that both the person in the linked thread and I are  using M-Audio interfaces while describing similar (but not identical?)  problems - could this be caused by an incompatibility of my interface  with Ubuntu, some software or the kernel? Is anything in my latest  description pointing towards that?

I also tried to blacklist the  Nvidia HDMI Output driver of my graphics card as I read in one of the  liked threads. I will see if this brings an improvement, but it's too  early for me to say right now.

---

### Post by CrocoDuck on 2015-11-24
> **Megadoomer said:**
> 

I tried to record the  sound while monitoring my output with Audacity while watching a DVD and I  could not record the sound. In fact, the recording was completely free  of this crackling sound, I stopped it right after it happened and  listened back to it in Audacity and the recording was fine - even the  part where I heard the sound live was recorded correctly (there was no  skip to be heard in the recording or anything else for that matter).

I  find it interesting that both the person in the linked thread and I are  using M-Audio interfaces while describing similar (but not identical?)  problems - could this be caused by an incompatibility of my interface  with Ubuntu, some software or the kernel? Is anything in my latest  description pointing towards that?



Very interesting indeed. So you recorded the output in Audacity but distortion did not showed up in the recording... I think that means, as you suggest, that the problem originates at a lower level. Probably the Kernel drivers or the hardware... or the particular way the Kernel drivers handle this hardware... I am wondering whether we are facing some bug. Give us the output of

```
lspci -vnn
```

I would also suggest to have a look at dmesg, I wonder whether the issue might be caused by something going up sometimes.

```

dmesg
dmesg -e

```

The second command will print the time an a human readable way, so that you can check what went on around the time you got distorted.

---

### Post by Megadoomer on 2015-11-25
Unfortunately I still experience the problem after (successfully) blacklisting the Nvidia HDMI Audio Driver.

The output of **lspci -vnn** currently reads as:

```
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v3 Processor DRAM Controller [8086:0c08] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5000]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f4000000-f60fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000ebffffff
    Capabilities: [88] Subsystem: Gigabyte Technology Co., Ltd Device [1458:5000]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] #19
    Kernel driver in use: pcieport

00:14.0 USB controller [0c03]: Intel Corporation 9 Series Chipset Family USB xHCI Controller [8086:8cb1] (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
    Flags: bus master, medium devsel, latency 0, IRQ 25
    Memory at f6200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation 9 Series Chipset Family ME Interface #1 [8086:8cba]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:1c3a]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f6212000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:1c.0 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 [8086:8c90] (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.2 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 [8086:8c94] (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6100000-f61fffff
    Prefetchable memory behind bridge: 00000000ec100000-00000000ec1fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.3 PCI bridge [0604]: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 [8086:8c96] (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1f.0 ISA bridge [0601]: Intel Corporation 9 Series Chipset Family H97 Controller [8086:8cc6]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode] [8086:8c82] (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:b005]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at f6211000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 9 Series Chipset Family SMBus Controller [8086:8ca2]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5001]
    Flags: medium devsel, IRQ 11
    Memory at f6210000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF100GL [Quadro 5000] [10de:06d9] (rev a3) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device [10de:0770]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4000000 (32-bit, non-prefetchable) [size=32M]
    Memory at e0000000 (64-bit, prefetchable) [size=128M]
    Memory at e8000000 (64-bit, prefetchable) [size=64M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f6000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation GF100 High Definition Audio Controller [10de:0be5] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:0770]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at d000 [size=256]
    Memory at f6100000 (64-bit, non-prefetchable) [size=4K]
    Memory at ec100000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169

04:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [90] Power Management version 2
    Capabilities: [a0] Subsystem: Gigabyte Technology Co., Ltd Device [1458:8892]
  

```

When I execute **dmesg**, I constantly get the following output:

```
[  +0,000001] input input4: event field not found
```

This will be echoed a few hunderd times with different digits in the brackets before the command stops and I get a new prompt.

---

### Post by tgalati4 on 2015-11-25
The dmesg error is probably related to a keyboard, mouse, or trackpad issue.

```
xinput --list
```

Since this is a USB device, are you using a USB hub?  If so, remove all USB devices (including the hub) and plug the audio device in by itself and test.

Since inputs are high-frequency interrupts (so we get a responsive system), it's possible that the input error is causing the noise on your USB audio device.

---

### Post by Megadoomer on 2015-11-25
Oh, okay. The output of **xinput --list** is:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; RAPTOR RAPTOR-GAMING M3 PLATINUM            id=9    [slave  pointer  (2)]
&#9116;   &#8627; RAPTOR RAPTOR-GAMING M3 PLATINUM            id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 Pen stylus                id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 Pad pad                   id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 Pen eraser                id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 Pen cursor                id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

```

Though I can't find any sign of error.
I don't use any kind of USB hub. And I've tried to use the interface on different USB ports (including USB3 and USB2) with no changes.

---

### Post by CrocoDuck on 2015-11-25
I had a look at your lspci -vnn output and I see that your system loads the same drivers I use for all the USB controllers. They never gave me this problem so I am kinda clueless. Proprietary video drivers can give issues on lowlatency (and also realtime) kernels. These kind of issues are quirky enough to be originated by apparently unrelated things, so I would give it a go by unloading the nvidea driver and run with the open source one (at least just for test purposes). Also, are you  on a laptop? If so, try to disable all the power saving daemons and software. I don't know which software implements this features under Ubuntu, but in my experience the best one for audio related work is [TLP]("http://linrunner.de/en/tlp/tlp.html"). [This guy]("http://ubuntuforums.org/showthread.php?t=2300575") solved his problems by downgrading the kernel, as often instabilities are due to incompatibility between proprietary drivers and latest kernel versions. Although the problem was unrelated to yours, it could be of some use.

Probably we will never understand in detail what span the issue. So, I suggest to run (just in live should be fine) older versions of Ubuntu or other operating systems, maybe an UStudio LTS: we could find that the issue belongs to a certain kernel version. We could go all the way back to [this]("https://www.dyne.org/software/dynebolic/") as well: 4 years old software.

---

### Post by CrocoDuck on 2015-11-26
> **Megadoomer said:**
> 

When I execute **dmesg**, I constantly get the following output:

```
[  +0,000001] input input4: event field not found
```

This will be echoed a few hunderd times with different digits in the brackets before the command stops and I get a new prompt.

I wonder whether something weird is going on the USB though...

Lets see if these can shed some light:

```

lsusb -tv
cat /proc/interrupts
ps -eLo pid,cls,rtprio,pri,nice,cmd |grep -i "irq"

```

Who knows... maybe something turning on at some point in the same bus is having fun with us...

---

### Post by tgalati4 on 2015-11-26
Do you have a Raptor Gaming mouse and a Wacom tablet connected to this system?  If so, remove and test your audio.

---

### Post by yoshii on 2015-11-28
if this only happens when you are doing DAW work, try and make sure you aren't using DEMO plugins.  
A lot of demo plugins use white noise bursts so that people can't fully use them and will thus buy the full versions instead.

---

### Post by Megadoomer on 2015-11-28
Hi everyone,

actually, I may have found a solution for this.

Because I was suspecting my interface to be maybe not the cause, but one part of the problem, I thought about ordering and testing one of the unofficially supported small USB interfaces, such as the Focusrite Scarlett 2i2/2i4 or iTrack Solo. My thought process was that it would probably be safer any way to use a well supported interface from now on, as the M-Audio Fast Track is kown-to-work as well, but some people apparently also reported problems with it. To make sure the Focusrite would actually work correctly on my distribution, I did a web search for it and ended up in a thread where a commentator described a similar problem like mine using one of the Scarlett devices. He set up a really elaborated formula for how to configure the buffer size and frequency rate of the interface, because he suspected that certain buffers/frequencies combined caused some kind of interference with the CPU (unfortunately I can't find the thread at the moment).

In short: Apparently the person from this thread found out that usually a frequency of 48 kHz works better, because the calculated latency will be more accurate (or a similar explanation). Since I used plugins for 44,1 kHz and I just make music at home with it, I have always used my interface with a set freqency of 44,1 kHz. Just to test it out, without actually expecting any success, I set my interface to 48 kHz while just keeping the same buffer size in Cadence/Jack and for the last 2-3 days, I have had not a single crack or drop out any more. I also have the subjective impression that the sound I'm hearing is "clearer" or more "defined" (this is hard to describe), though I know that probably no human is able to distinguish the differences between those two sample rates, still this is my experience - maybe also an effect of a better performing frequency setting?

I still feel like this is a bit too early to call it a complete success, but I also did not get any distortion or other disturbance while watching a DVD on the past two days, which has been an almost certain way of experiencing this problem. Even while using Windows, I got small lags now and then, not as frequent, but still more than right now (also while using 44,1 kHz as the sample rate).

I hope that someone who may have the same issue is reading this and could confirm this solution, or maybe this solution makes sense by itself, but I did not find it to be obvious. Any way, until I get the same issue again, I will see this as solved.


Thank you all for your suggestions and help with this! :)

---

### Post by tgalati4 on 2015-11-28
Well, that is a simple fix that eluded all of us.  With music production, one normally samples at 48K, 96K, or 192K.  Nobody uses 44.1K unless you have CD's that you want to listen to or sample.  The conversion from 48K (native internal sample frequency for many audio devices) to 44.1K is not trivial.

Thanks for sharing your fix.

---

### Post by CrocoDuck on 2015-11-28
Wow! These are great news! It was the weird interference/beating thing between clocks then. I wonder whether [this]("http://wiki.linuxaudio.org/wiki/list_of_jack_frame_period_settings_ideal_for_usb_interface") is the page you found?

---

### Post by Megadoomer on 2015-11-29
I did not realise that this was such a big deal. The original M-Audio driver on Windows offers options for 44,1 and 48 kHz, none of the above. I figured that since I'm making/listening to music which is distributed digitally, I just set it to 44,1 kHz, since this is the frequency of most compressed audio files. I did not assume that this would have an impact on the performance, if anything I though it would be beneficial because of the lower frequencies. Good to know.

> **CrocoDuck said:**
> I wonder whether [this]("http://wiki.linuxaudio.org/wiki/list_of_jack_frame_period_settings_ideal_for_usb_interface") is the page you found?

No, not directly at least. I think I have seen the board post that is linked in that article though. At least I can remember reading something that was written there, so probably I have seen it while looking around. But this is exactly what I was referring to, I didn't even know that I could just simply enter custom buffer sizes in Jack/Cadence. As I still had no further problems, I can say that the interface worked much better with 48 kHz already, even though I left the buffer size at 256 samples, which resulted in a calculated latency of 10,6&#773;. I set it to 192 now, which means all parts of the equation should be dividable by two, we'll see how that works out now. Thanks again for sharing this site.

What I don't really understand is, the realistic latency is not constant and effectively depends on different aspects that can not really be calculated. Also this seems like another setting in which a dozenal system would have been better than our decimal one, if you divide 12 by 3, you don't get ugly cycling numbers. :p

But it doesn't matter - at least it works now. ;)

---

### Post by CrocoDuck on 2015-11-29
> **Megadoomer said:**
>  I set it to 192 now, which means all parts of the equation should be dividable by two, we'll see how that works out now. Thanks again for sharing this site.


The preference is to have the Period/Buffer a power of 2, isn't it? Divisible by 2 does not mean a power of 2.

> **Megadoomer said:**
> 
What I don't really understand is, the realistic latency is not constant  and effectively depends on different aspects that can not really be  calculated. Also this seems like another setting in which a dozenal  system would have been better than our decimal one, if you divide 12 by  3, you don't get ugly cycling numbers. :razz:


The maths derived latency applies only at the software level and it is the latency introduced by the system's buffering operations. To this value you have to add the hardware latencies. The maths derived latency is not an estimation of the whole round-trip latency, but it is an exact figure of the software latency. The hardware latency depends upon the converters speed and bus/controllers speed. You cannot calculate it, but you can measure it with [jack_iodelay]("http://manpages.ubuntu.com/manpages/precise/man1/jack_iodelay.1.html") (it comes by default in each jack installation). Have a look at [this]("http://apps.linuxaudio.org/wiki/jack_latency_tests") and [this]("http://kxstudio.linuxaudio.org/Documentation:Manual:latency").

---

### Post by Megadoomer on 2015-11-30
> **CrocoDuck said:**
> The preference is to have the Period/Buffer a power of 2, isn't it? Divisible by 2 does not mean a power of 2.

Oh, you're completely correct. Maybe I should have read more carefully or I just misunderstood this, not being a native speaker. Now the bold numbers suddenly make a lot more sense. Okay, so I received an increasing amout of xruns with my newer setting, maybe because of the buffer size or the tighter setting, but I guess I will just try and find out what setting works best for me here, at least I have some kind of a guideline now.

Thanks for the links, I will check that out and see if it works for me as well.

---

