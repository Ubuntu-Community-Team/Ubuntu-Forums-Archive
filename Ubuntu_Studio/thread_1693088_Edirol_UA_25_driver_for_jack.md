---
title: "Edirol UA 25 driver for jack"
date: 2011-02-22
forum: Ubuntu Studio
---

### Post by martjan on 2011-02-22
Hello!
I'm trying to set Ubuntu studio with my audio card: Edirol UA-25.
But I can not figure out which driver should I choose from jack setup. Does everyone know? In the UA-25 owner's manual drivers are named: UA-4FX. But nothing similar in jack setup panel...
I thank you sincerly for your interest. Bye!

---

### Post by AutoStatic on 2011-02-22
Hello martjan,

There you go:
[IMG]http://www.autostatic.com/logimages/qjackctl_ua-25.png[/IMG]

So you need the 'alsa' driver.

Best,

Jeremy

---

### Post by sranauta on 2011-02-22
Hello AutoStatic

I notice you have the UA25 same as me.

It works fine for me  with jack altho I don't use it for midi. 

I have a Korg K61P usb midi keyboard

I am having a hard time with Reaper. 

I installed Ubuntu Studio 10.04 , then I installed wine, wineasio and then Reaper

As soon as I run reaper it freezes

On a previous Ubuntu Studio 10.04 install Reaper did recognise my Korg K61p in teh Options>preferences>Audio>Midi Devices

However now Reaper freezez on opening

I use Win7 and Cubase 5 and am trying hard to switch to Linux but its proving to be tough

Can you point my nose in the right direction as to how to get Reaper working properly in Linux

Ideally I would like to use Puppy Studio which comes with Reaper installed but it won't recognise my Korg K61p  

Thanks for any and all advice

---

### Post by martjan on 2011-02-23
Hello AutoStatic!
It's a long time I read your posts about edirol and ubuntu studio, and I'm very happy with your interest in my question!
I read your site too, it's very interesting and well done: my best compliments! (just a short off-topic: the google translation of the page German -> English translates the shell commands too!! I spent many time trying to follow your indications and the answers were always: 'command not found'!!  Might be a good idea to report this problem in the site before other people become crazy as me!!!).
Having said that, unfortunately my problem persist. I set jack exactly as you show me, but when I play it this is what happens...
```
10:28:23.973 Patchbay deactivated.
10:28:23.976 Statistics reset.
10:28:24.011 Startup script...
10:28:24.011 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:28:24.013 ALSA connection graph change.
sh: artsshell: not found
10:28:24.414 Startup script terminated with exit status=32512.
10:28:24.414 JACK is starting...
10:28:24.414 /usr/bin/jackd -P69 -t5000 -dalsa -dhw:1 -r48000 -p128 -n3
10:28:24.417 JACK was started with PID=2986.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 69
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|128|3|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 1 - EDIROL UA-25 at usb-0000:00:1a.0-1.5, full speed
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
ALSA: could not start playback (Broken pipe)
Cannot start driver
JackServer::Start() failed with -1
Released audio card Audio1
audio_reservation_finish
Failed to start server
10:28:24.560 JACK was stopped with exit status=255.
10:28:24.561 Post-shutdown script...
10:28:24.561 killall jackd
10:28:24.615 ALSA connection change.
jackd: no process found
10:28:24.967 Post-shutdown script terminated with exit status=256.
10:28:26.617 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```
The only different thing between my settings and yours is that your "interface" is named: hw:UA25, while mine hw:1. I forgot: I use Ubuntu 10.10. Any suggests?!
Thank you very much for the interest!

---

### Post by AutoStatic on 2011-02-23
Hello martjan, could you give the output of **lspci** and **lsusb** ?

Best,

Jeremy

---

### Post by AutoStatic on 2011-02-23
> **sranauta said:**
> Can you point my nose in the right direction as to how to get Reaper working properly in LinuxHello sranauta, sorry but I don't use Windows programs with JACK so no idea. But forumite sgx knows more about this so if you do a search on this forum for the term reaper and the author sgx you should end up with your nose in the right direction ;)

Best,

Jeremy

---

### Post by cub on 2011-02-23
> **sranauta said:**
> Hello AutoStatic

I notice you have the UA25 same as me.

It works fine for me  with jack altho I don't use it for midi. 

I have a Korg K61P usb midi keyboard

I am having a hard time with Reaper. 

I installed Ubuntu Studio 10.04 , then I installed wine, wineasio and then Reaper

As soon as I run reaper it freezes

On a previous Ubuntu Studio 10.04 install Reaper did recognise my Korg K61p in teh Options>preferences>Audio>Midi Devices

However now Reaper freezez on opening

I use Win7 and Cubase 5 and am trying hard to switch to Linux but its proving to be tough

Can you point my nose in the right direction as to how to get Reaper working properly in Linux

Ideally I would like to use Puppy Studio which comes with Reaper installed but it won't recognise my Korg K61p  

Thanks for any and all advice
I have not tried Reaper on a Linux box, but run it on my Win7. I also got myself a UA25EX card and wanted to switch to Linux entirely. No such luck. It might depend on what pc you connect the Edirol card too. But enough about me. ;)

I'm not sure if you got Jack running ok? If not, have you tried to connect the Edirol card with Advanced driver OFF and 44.1 kHz (with the same settings in Jack)? Does it work then?

Also, when you get Jack running properly I would suggest looking into Ardour before fiddling away with wine and Reaper. I have used both Ardour and Reaper and have no trouble navigating my way around any of the software. Otherwise, it might be just as good staying with Windows for the sound work if you prefer Reaper.

---

### Post by sgx on 2011-02-23
Hello, sranauta

> **cub said:**
> I have not tried Reaper on a Linux box, but run it on my Win7. I also got myself a UA25EX card and wanted to switch to Linux entirely. No such luck. It might depend on what pc you connect the Edirol card too. But enough about me. ;)

I'm not sure if you got Jack running ok? If not, have you tried to connect the Edirol card with Advanced driver OFF and 44.1 kHz (with the same settings in Jack)? Does it work then?

Also, when you get Jack running properly I would suggest looking into Ardour before fiddling away with wine and Reaper. I have used both Ardour and Reaper and have no trouble navigating my way around any of the software. Otherwise, it might be just as good staying with Windows for the sound work if you prefer Reaper.

from a korg manual

'When USB is connected, MIDI OUT jack does not send out MIDI messages from the K-Series&#8217; keyboard and controller.'

If your Korg was purchased second-hand, there is a system reset sequence in the manual

[www.korg.co.uk/downloads/kseries/support/KSeries_OM_EFG2.pdf](www.korg.co.uk/downloads/kseries/support/KSeries_OM_EFG2.pdf)


Also, I have reaper in the /home/username folder, and use 
regsvr32 wineasio.dll to get wineasio recognized.

reaper has a list of actions, click the 'show actions list' in the
Actions menu, and scroll down to  "Reset all MIDI devices".

The Korg may need to be powered by adaptor or batteries when the usb cable is not used. And usb hubs should not be used in music setups.

I would also disable any soundchip using the bios controls.

Hope something helps!

---

### Post by martjan on 2011-02-24
Hello Autostatic,
this is the lsusb output:
```
martin@martin-System-Product-Name:~$ lsusb
Bus 002 Device 005: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 004: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 003: ID 152e:1640 LG (HLDS) 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0582:0074 Roland Corp. EDIROL UA-25
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
while this the lspci one:
```
martin@martin-System-Product-Name:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0dc4 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
07:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```
Thank you for the attention!
Best,
Martin

---

### Post by AutoStatic on 2011-02-24
Hello Martin,

```
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
...
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
```Your USB ports are behind a kind of hub and the USB controller chipset on your motherboard has trouble with USB audio devices (known bug). So you can't use USB audio devices at full-duplex (capturing and playback at once) on your current system. You could try using your UA-25 for capturing or playback only, that should work. If you want to be able to use full-duplex you will need an extra PCIe USB2 (so NOT USB3!) controller card. In Windows you will most likely run into the same issues.

Best,

Jeremy

---

### Post by martjan on 2011-02-24
Well Jeremy,
this is not properly a good news...but it's a news!
So the problem, if I understand, is not in my audio device, but in the motherboard configuration. Right? (at least more or less..!!:D).
I thank you very much for the support, I'll try to better understand and resolve the problem. You renew the compliments for your site, and for your availability too.

Best,

Martin

---

### Post by AutoStatic on 2011-02-24
> **martjan said:**
> So the problem, if I understand, is not in my audio device, but in the motherboard configuration. Right? (at least more or less..!!:D).Yes it is. Your USB ports are behind some kind of hub and USB audio devices don't work well behind hubs (with a few exceptions). Also the USB controller on your motherboard is known to have problems with USB audio devices.

Best,

Jeremy

---

### Post by Pablo_F on 2011-02-24
> Your USB ports are behind a kind of hub and the USB controller chipset on your motherboard has trouble with USB audio devices (known bug). So you can't use USB audio devices at full-duplex (capturing and playback at once) on your current system.

IIRC, with this USB controller you can use the UA-25 soundcard for playback/capture at the same time, but only in non-advanced mode (16bit/44,1KHz and no MIDI ports) and only if you don't have any other device (for example, a mouse) in the same USB bus.

Martin, give it a try, if only as a proof of concept.  

Cheers, Pablo

---

### Post by AutoStatic on 2011-02-24
I'll try that too Pablo. I'll take my UA-25 to work where we have workstations with the same controller and USB ports. I did test my UA-25 with those already and got the same result but I didn't test with advanced mode switched off.

---

### Post by cub on 2011-02-24
That might work, which I suggested earlier, as it is what happens on my Sony Vaio. I can run duplex in 16 bit, 44 kHz, Advanced driver OFF. But only capture OR playback if I set it to Advanced driver.

However, the same laptop and settings in Windows 7 I can run Advanced Driver and all kHz settings no problem. Annoying.

---

### Post by Pablo_F on 2011-02-24
> That might work, which I suggested earlier, as it is what happens on my Sony Vaio.

It also worked in my sister's brand new notebook with the same USB chipset. 
> 
However, the same laptop and settings in Windows 7 I can run Advanced Driver and all kHz settings no problem
The same on her laptop. Sad but true.

I took a look at the Intel's data sheets that someone pointed out. I can't remember now where it is. Intel admits some bugs in the hardware but it looks like W7 has a workaround... :-k 

The saddest part is that there must be millions of these buggy chipsets as many people is reporting the issue... In my sister's notebook there is not an expresscard or firewire port either... 

Cheers, Pablo

---

### Post by SundayForever on 2011-02-26
I'm not sure if you got Jack running ok? If not, have you tried to  connect the Edirol card with Advanced driver OFF and 44.1 kHz (with the  same settings in Jack)? Does it work then?

---

### Post by martjan on 2011-02-26
Hello Pablo, Sunday, cub!
I'm trying everything to solve this problem, but nothing seems to work...
I try with Advance mode off but jack doesn't play. The only way is set "Only capture" or "Only playback" mode in jack control panel. 
I thought this could be a possible solution: [http://alsa.opensrc.org/Edirol_UA-25](http://alsa.opensrc.org/Edirol_UA-25)
```
Full-duplex mode
The Edirol UA-25 is a half-duplex device, which means that it cannot play several sounds simultaneously. Fortunately, Alsa is able to play and record in full-duplex over a half-duplex device. This Alsa feature is provided by the asym (i.e. full-duplex) plugin, which is able to combine the dmix (i.e. play) and dsnoop (i.e. record) plug-ins.
The dmix and dsnoop interfaces are already provided by Alsa.
Add the following text to you .asoundrc file:
 #This PCM combining the dmix and dsnoop slaves
pcm.asymed {
      type asym
      playback.pcm "dmix"
      capture.pcm "dsnoop"
}  
#This PCM should be able to convert recording rates automatically
pcm.pasymed {
      type plug
      slave.pcm "asymed"
}
```
But it doesn't work too... Is there something wrong?!...
The last way is to try an extra PCIe USB2, as AutoStatic suggested. 
Thank You!
Best,
Martin

---

### Post by martjan on 2011-06-07
Hi guys!
It's been a long time since we spoken about my troubles...in the meanwhile i searched on the italian forum for a solution. But I had not found...
I made so many attempts that my beloved Edirol left me...She died...
So I thought for a new one, and I bought the Lexicon Omega. Before buy it I asked many times on the italian forum if someone was able to use it with musical editing programs of Ubuntu (and jack especially....). 2 or 3 users said the card is supported out of the box, and so I was satisfied..
But when the card arrived and I tried it: exactly the same problem with the Edirol one. It is supported out of the box for all functions, but jack can't start in Duplex mode...
So the opinion of AutoStatic that > Your USB ports are behind a kind of hub and the USB controller chipset  on your motherboard has trouble with USB audio devices (known bug). So  you can't use USB audio devices at full-duplex (capturing and playback  at once) on your current system. You could try using your UA-25 for  capturing or playback only, that should work. If you want to be able to  use full-duplex you will need an extra PCIe USB2 (so NOT USB3!)  controller card. In Windows you will most likely run into the same  issues.

Best,

Jeremy
it's the right one! The only problem is that with windows (when I used it) and Nuendo 3 I had no problems! And I have no problems with every usb hardware I use (a toshiba hdd, an external cd writer, for instance). It's a sort of misunderstanding between jack and the motherboard...My motherboard is fairly recent: ASUS p7p55d...
Have you got any suggest?
Thank you very much!
Best
Martin

---

