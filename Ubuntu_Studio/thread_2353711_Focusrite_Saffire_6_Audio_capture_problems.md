---
title: "Focusrite Saffire 6 Audio capture problems"
date: 2017-02-24
forum: Ubuntu Studio
---

### Post by rw1968 on 2017-02-24
I've just installed ubuntu studio 16.04LTS and tried to get my Focusrite Saffire 6 USB to work with it.
There are a few posts regarding this interface but, none for a while, and there was a suggestion that it used to work in 12.04
It seems to work fine as a playback device - "aplay -l" shows the device as expected, "arecord -l" shows only the internal soundcard.
The record view of alsamixer doesn't show the Saffire.
Its not a surprise, but when I start an Ardour session the Saffire just doesn't appear in the input device list.

Any ideas?

---

### Post by rw1968 on 2017-02-26
Just in case any of this is of use:


rich@Ginetta:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USB [Saffire 6 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rich@Ginetta:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


rich@Ginetta:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7f30000 irq 28
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf7e40000 irq 29
 2 [USB            ]: USB-Audio - Saffire 6 USB
                      Focusrite Saffire 6 USB at usb-0000:00:1a.0-1.4, full speed
rich@Ginetta:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 003: ID 1235:0010 Focusrite-Novation Saffire 6
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by hombrearbol on 2017-02-28
Hello! I recently started in the Linux world, but I'll try to be useful: Maybe it's a silly question but, you're using JACK, right? Do you have everything routed to be able to record with your USB sound card? If not, I recommend reading [this article]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack"), as to begin.

---

### Post by rw1968 on 2017-03-04
Hi hombrearbol - thanks for your reply, but thats not the problem. It doesn't matter whether I use Jack or ALSA - the only input device available is the internal sound card - so the Saffire doesn't show up in QJackctl as an input device - so I can't connect it to anything.
Looking at the audio/MIDI setup in Ardour, the input device drop down list does not include the Saffire - regardless of which audio system I select.
Your are right about that article, though - it is useful - thanks.

---

### Post by CrocoDuck on 2017-03-04
> **rw1968 said:**
> 
It seems to work fine as a playback device - "aplay -l" shows the device as expected, "arecord -l" shows only the internal soundcard.


Weird. I wonder whether the device itself is broken. Do you have another laptop, even with another OS, to test it with?

As for your currently affected computer, boot it up with the card unplugged, open a terminal and enter this command:

```
dmesg -wH
```

this will open an ongoing dmesg session where new logs from the kernel get automatically appended. Plug your card and copy and paste here the messages that will be appended. I suggest to use the code delimiters as above.

---

### Post by rw1968 on 2017-03-05
Hi CrocoDuck,

It certainly used to work - I will dig out a windows machine later today and retest.

I should have though of dmesg myself (I'm a bit rusty).
Here's the output - I'm off to try to work out what that means.
```

[Mar 5 09:43] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[  +0.087038] usb 1-1.4: New USB device found, idVendor=1235, idProduct=0010
[  +0.000003] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  +0.000002] usb 1-1.4: Product: Saffire 6USB
[  +0.000002] usb 1-1.4: Manufacturer: Focusrite Audio Engineering
[  +0.133625] usbcore: registered new interface driver snd-usb-audio
[  +0.978785] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.020784] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.020007] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
...
duplicate lines removed here for brevity. Message occurred 121 times (in case thats relevant)
...
[  +0.021234] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.021002] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.028247] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.019644] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.022011] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.021081] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
[  +0.021972] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
```

---

### Post by CrocoDuck on 2017-03-05
This is no good. Seems like your kernel is struggling to get proper communication:

```

[  +0.978785] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth

```

Let's look at your onboard hardware:

```

lspci -vnn

```

---

### Post by rw1968 on 2017-03-05
Hi Again - first piece of good news. If I connect to a USB3 socket then that error disappears, so dmesg just says:


```
[Mar 5 10:54] usb 3-1: new full-speed USB device number 2 using xhci_hcd
[  +0.176979] usb 3-1: New USB device found, idVendor=1235, idProduct=0010
[  +0.000004] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  +0.000003] usb 3-1: Product: Saffire 6USB
[  +0.000002] usb 3-1: Manufacturer: Focusrite Audio Engineering
[  +0.162073] usbcore: registered new interface driver snd-usb-audio
```


I've also tested on a windows laptop and audio capture works fine.

Still no sign of the audio capture device on linux though.
```
rich@Ginetta:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rich@Ginetta:~$ 

```


lspci says:

```
rich@Ginetta:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [8086:0150] (rev 09)
    Subsystem: Dell Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [1028:0577]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: ivb_uncore
    Kernel modules: ie31200_edac

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1028:0577]
    Flags: bus master, medium devsel, latency 0, IRQ 24
    Memory at f7f20000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Dell 7 Series/C210 Series Chipset Family MEI Controller [1028:0577]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f7f3b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:16.3 Serial controller [0700]: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller [8086:1e3d] (rev 04) (prog-if 02 [16550])
    Subsystem: Dell 7 Series/C210 Series Chipset Family KT Controller [1028:0577]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
    I/O ports at f100 [size=8]
    Memory at f7f39000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    DeviceName:  Onboard LAN
    Subsystem: Dell 82579LM Gigabit Network Connection [1028:052c]
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at f7f00000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7f38000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f020 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell 7 Series/C210 Series Chipset Family USB Enhanced Host Controller [1028:0577]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7f37000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Dell 7 Series/C210 Series Chipset Family High Definition Audio Controller [1028:0577]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f7f30000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 [8086:1e18] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7e00000-f7efffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell 7 Series/C210 Series Chipset Family USB Enhanced Host Controller [1028:0577]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7f36000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge [0601]: Intel Corporation Q77 Express Chipset LPC Controller [8086:1e47] (rev 04)
    Subsystem: Dell Q77 Express Chipset LPC Controller [1028:0577]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 IDE interface [0101]: Intel Corporation 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode] [8086:1e00] (rev 04) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode] [1028:0577]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f0f0 [size=8]
    I/O ports at f0e0 [size=4]
    I/O ports at f0d0 [size=8]
    I/O ports at f0c0 [size=4]
    I/O ports at f0b0 [size=16]
    I/O ports at f0a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Dell 7 Series/C210 Series Chipset Family SMBus Controller [1028:0577]
    Flags: medium devsel, IRQ 5
    Memory at f7f35000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c_i801

00:1f.5 IDE interface [0101]: Intel Corporation 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode] [8086:1e08] (rev 04) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode] [1028:0577]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    I/O ports at f040 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos XT [Radeon HD 7470/8470 / R5 235/310 OEM] [1002:6778] (prog-if 00 [VGA controller])
    Subsystem: Dell Radeon HD 7470 [1028:2120]
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7e20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

02:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series] [1002:aa98]
    Subsystem: Dell Caicos HDMI Audio [Radeon HD 6400 Series] [1028:aa98]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7e40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

rich@Ginetta:~$ 
```

---

### Post by rw1968 on 2017-03-05
I also found an old web cam with a USB microphone built in. If I connect that it shows up as an audio capture device with no problems:
```

rich@Ginetta:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: U0x4710x329 [USB Device 0x471:0x329], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rich@Ginetta:~$
```

Ardour sees it as an input device in the audio / MIDI setup dialog.

---

### Post by CrocoDuck on 2017-03-05
> **rw1968 said:**
> Hi Again - first piece of good news. If I connect to a USB3 socket then that error disappears, so dmesg just says:

I was expecting to see that by switching to an USB hub controlled by the xhci_hcd kernel driver. Good.

So, plug your saffire, check its card number with this:

```
cat /proc/asound/cards
```

and then use the number in the following command:

```
ls /proc/asound/cardX/
```

where X is the number you found above. We could find some info in the files in there.

Are you using a [.asoundrc file]("http://www.alsa-project.org/main/index.php/Asoundrc")? Return the output of the following:

```

cat .asoundrc
cat /etc/asound.conf

```

---

### Post by rw1968 on 2017-03-05
Hi - thanks again for your help on this. Its card 2:
I've had a bit of a poke around in the card2 directory and it looks like there aren't any capture interfaces associated with that device - although I am out of my linux comfort zone here so I might have missed something

```
rich@Ginetta:~$ ls -l /proc/asound/card2/
total 0
-r--r--r-- 1 root root 0 Mar  5 16:41 id
-r--r--r-- 1 root root 0 Mar  5 16:41 midi0
dr-xr-xr-x 3 root root 0 Mar  5 16:41 pcm0p
-r--r--r-- 1 root root 0 Mar  5 16:41 stream0
-r--r--r-- 1 root root 0 Mar  5 16:41 usbbus
-r--r--r-- 1 root root 0 Mar  5 16:41 usbid
rich@Ginetta:~$ 
rich@Ginetta:~$ ls -l /proc/asound/card2/pcm0p/
total 0
-r--r--r-- 1 root root 0 Mar  5 16:41 info
dr-xr-xr-x 2 root root 0 Mar  5 16:41 sub0
rich@Ginetta:~$ cat /proc/asound/card2/stream0 
Focusrite Saffire 6 USB at usb-0000:00:14.0-1, full speed : USB Audio

Playback:
  Status: Stop
  Interface 0
    Altset 1
    Format: S24_3LE
    Channels: 4
    Endpoint: 1 OUT (NONE)
    Rates: 44100, 48000
rich@Ginetta:~$ cat /proc/asound/card2/pcm0p//info 
card: 2
device: 0
subdevice: 0
stream: PLAYBACK
id: USB Audio
name: USB Audio
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1
rich@Ginetta:~$ 


```


I'm not using any conf files:
```
rich@Ginetta:~$ stat /etc/asound.conf
stat: cannot stat '/etc/asound.conf': No such file or directory
rich@Ginetta:~$ stat ~/.asoundrc
stat: cannot stat '/home/rich/.asoundrc': No such file or directory
rich@Ginetta:~$
```

---

### Post by CrocoDuck on 2017-03-05
Uhm... Not sure what could be causing that. The device [should work]("https://focusritedevelopmentteam.wordpress.com/2012/04/23/saffire-6usb-technical-details-for-driver-developers/"). It could be a kernel/ALSA bug. I would suggest to create an [AV Linux]("http://www.bandshed.net/avlinux/") live bootable media and see whether the card works in that environment. Also, check whether there are firmware updates for the soundcard or known firmware version that work on Linux (I couldn't find any info in this regard). Worth to also have a look at [this]("https://github.com/fulup-bzh/AlsaJsonMixer") and see if it expose some advanced functionality that could be blocking the card. We could also try to [blacklist]("https://wiki.archlinux.org/index.php/Kernel_modules#Blacklisting") the onboard and HDMI audio kernel driver (snd_hda_intel) to see whether the issue is caused by some weird conflict (sometimes it happen, especially with video card codecs as you have).

---

### Post by rw1968 on 2017-03-08
I've blacklisted the modules for the other audio devices, but that made no difference.
I've got my bootable media for AVLinx - I'll try that out tonight.
Thanks also for the other ideas - I'll check them out tonight aswell.
I couldn't find any driver information either other than the link you included in your post.
I'm guessing the next step is for me to start digging around in the driver code - but I haven't done any linux work since 2.6, so thats going to be fun.
Thanks again for your help, CrocoDuck.

---

### Post by rw1968 on 2017-03-12
OK - the AVLinux distro was exactly the same - works fine as an playback device - but no capture.
It does look like a kernel / ALSA / driver bug at this point.
I'll start digging around in the code and see what I can find - any hints or tips anyone?
Cheers!

---

### Post by CrocoDuck on 2017-03-12
i wonder whether it is an USB bandwidth problem. Is the behavior the same regardless of the USB port you use?

---

### Post by rw1968 on 2017-03-13
The only difference I have found so far is that I see this:
```
[  +0.021234] usb 1-1.4: cannot submit urb 0, error -28: not enough bandwidth
```
lots of times if I connect to a non-USB3 port. Its a Dell Optiplex with 4 front panel USB sockets - Two with USB3 (i.e. the SS logo), and two USB2 with the normal USB logo.

These will clearly be rounted differently internally but I'm not with the PC at the minute so I'll do some more investigation tonight.

---

### Post by CrocoDuck on 2017-03-14
> **rw1968 said:**
> Its a Dell Optiplex with 4 front panel USB sockets - Two with USB3 (i.e. the SS logo), and two USB2 with the normal USB logo.


Did you also try the USB ports on the back? I am asking cause in the past I had similar problems and it turned out that the front connectors were unable to supply enough current to correctly power the device. Worth to brute force all of the ports as they are not all the same, both for data capabilities (due to hubs and controllers) but also electric power capabilities.

Not sure where to look for ALSA/Kernel troubleshooting, a part maybe see whether there is some support you can reach with ALSA developers. Probably you will have to use a tool like [Wireshark]("https://www.wireshark.org/") and analyze the USB data traffic from/to device. Not really an expert about this...

---

### Post by djembejohn on 2017-03-22
> **rw1968 said:**
> I've just installed ubuntu studio 16.04LTS and tried to get my Focusrite Saffire 6 USB to work with it.
There are a few posts regarding this interface but, none for a while, and there was a suggestion that it used to work in 12.04
It seems to work fine as a playback device - "aplay -l" shows the device as expected, "arecord -l" shows only the internal soundcard.
The record view of alsamixer doesn't show the Saffire.
Its not a surprise, but when I start an Ardour session the Saffire just doesn't appear in the input device list.

Any ideas?

Did you get any further with this? I'm having the same problem.

---

### Post by rw1968 on 2017-06-25
Hi - yes I did.
Sorry - I've been out of action for a while so I've only just managed to get back to this.
I found this patch for 4.8:
[https://gist.github.com/shiona/def87540b87466fff315c4ac805c6766](https://gist.github.com/shiona/def87540b87466fff315c4ac805c6766)

Which I'll try out as soon as I get a build environment set up.
If anyone else out there has any experience with this patch it would be great to hear about it.

Cheers.

Richard.

---

### Post by rw1968 on 2017-06-26
I'm not doing well - anyone know how to get kernel source for studio?

I get this:

```
rich@Ginetta:~$ apt-get source linux-image-$(uname -r)
Reading package lists... Done
Picking 'linux-hwe' as source package instead of 'linux-image-4.8.0-56-lowlatency'
E: Unable to find a source package for linux-hwe
rich@Ginetta:~$ uname -r
4.8.0-56-lowlatency
```

---

