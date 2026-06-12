---
title: "Jack xruns every 3-4 minutes"
date: 2009-01-24
forum: Ubuntu Studio
---

### Post by Ouoertheo on 2009-01-24
Hello,
I'm having xruns in jack every 3-4 minutes, no matter what I'm doing. Has anyone else had this issue? If so what did you do to fix it?

Here are my output messages.

```
13:25:19.679 Patchbay deactivated.
13:25:19.770 Statistics reset.
13:25:20.058 Startup script...
13:25:20.059 artsshell -q terminate
13:25:20.063 ALSA connection graph change.
13:25:20.509 Startup script terminated with exit status=256.
13:25:20.510 JACK is starting...
13:25:20.510 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p128 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
13:25:20.524 JACK was started with PID=6950.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
13:25:20.724 ALSA connection change.
13:25:22.740 Server configuration saved to "/root/.jackdrc".
13:25:22.743 Statistics reset.
13:25:22.801 Client activated.
13:25:22.809 JACK connection change.
13:25:22.834 JACK connection graph change.
Enhanced3DNow! detected
SSE2 detected
13:28:35.791 XRUN callback (1).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:30:34.309 ALSA connection graph change.
13:30:34.320 ALSA connection change.
13:31:58.440 XRUN callback (2).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:35:21.169 XRUN callback (3).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:38:44.246 XRUN callback (4).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:42:00.541 XRUN callback (5).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:42:30.767 ALSA connection graph change.
13:42:30.930 ALSA connection change.
13:45:23.534 XRUN callback (6).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:47:43.569 XRUN callback (7).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:51:06.748 XRUN callback (8).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:54:31.828 XRUN callback (9).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
13:56:09.588 XRUN callback (10).
**** alsa_pcm: xrun of at least 1232822312370.176 msecs
```

---

### Post by tsmithtree on 2009-01-25
I have this exact same problem, and it's really irritating.
Switching to linux-rt gives fewer xruns at the expense of making a bunch of other stuff (3d acceleration in particular) not work.

I never used to have ANY xruns, even when running jack all day. Can someone address this issue?

---

### Post by Stochastic on 2009-01-25
Can you guys provide a little more information, such as which version of Ubuntu you're running, if you've had the same problem with different frames-per-period settings, if you've tried any different jack settings, if the xruns are exactly the same time apart or if they vary but stay in the 3-4min range, etc...

---

### Post by Ouoertheo on 2009-01-25
I'm running Ubuntu Studio 8.10, just upgraded from 8.04. I've had this issue with both versions. I have a SBLive! 5.1 sound card.

It has xruns with different frames-per-second values, same thing with rt enabled or not. I'm gonna keep changing settings, maybe I'll stumble on something.

I remember seeing somewhere that a network manager of sorts causes xruns, but I cant seem to find anything on that anymore

Oh  yeah, it's typically between the 3-4 minute range.

---

### Post by Abu_Dayya on 2009-01-25
To avoid xruns with the "alsa_pcm: xrun of at least blah msecs" error, check the 'soft mode' radio button from jack control. This will ignore xruns reported from alsa

---

### Post by Ouoertheo on 2009-01-25
Upon further inspection, the frames/period setting does affect the xruns. The higher the frames/period, the longer it takes for the xruns to show up, but they are still consistent in the period of time it takes them to happen.
It doesn't seem like any of the other options affect it though.

---

### Post by swornbrother on 2009-01-26
I have been having this problem as well--after getting a new laptop and upgrading to Jaunty (since I can't boot into earlier versions with this hardware configuration.)

On my old laptop, if it was running wireless, it'd get crazy XRUNS.  Fortunately, it had a switch that would shut the wireless down, and stop them.  My new laptop however, has a button for wireless instead of a switch, and the button does nothing.  I don't know if it's the wireless giving me these problems though, since I'm ignorant of a good way to test this.

Also, none of the JACK settings will affect the XRUNS--not even frames/period.

---

### Post by thorgal on 2009-01-26
you will probably have to look into ACPI stuff (power management and such). You can also check how your IRQs are shared by looking into a file called /proc/interrupts
If your sound card shares its IRQ with e.g. the wireless chip, you will easily get that kind of behavior. Except disabling the wireless card from the BIOS, I cannot see an easy fix. Reassigning IRQs in a laptop is mostly impossible (as far as I know, I could be wrong).

---

### Post by swornbrother on 2009-01-26
Ok, here is my /proc/interrupts:

> 
```
           CPU0       CPU1       
  0:        116         11   IO-APIC-edge      timer
  1:         24       3503   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:         25       3504   IO-APIC-fasteoi   acpi
 12:       2476     426918   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 16:        118      30101   IO-APIC-fasteoi   ohci_hcd:usb3, ehci_hcd:usb4
 17:         93      10797   IO-APIC-fasteoi   ohci_hcd:usb1, ehci_hcd:usb2
 19:         11       1902   IO-APIC-fasteoi   nvidia
 20:          7        460   IO-APIC-fasteoi   HDA Intel
 23:        410      69215   IO-APIC-fasteoi   ath
2301:        652     183510   PCI-MSI-edge      eth0
2302:        303      26871   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     153537     159900   Local timer interrupts
RES:      64517      40319   Rescheduling interrupts
CAL:      23547      10897   Function call interrupts
TLB:        745        467   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0
```


Can anyone tell me if the wireless would be sharing an interrupt with audio, or if it might be more of an acpi issue?

---

### Post by thorgal on 2009-01-27
hello.
The good news: you have no shared interrupt for your audio card
The bad news: you have the infamous Intel HDA.
After looking at your original post, I saw that you're using the default jack setting, which implies a number of periods per buffer of 2. Bump it to 3.
The option from the command line is -n 3.
In qjackctl, it is the number of periods/buffer. The number of frames per period depends on the latency you want to achieve. A good number if 128 for this audio chip.
Try that and report. It fixed the issue for a lot of people.

---

### Post by Ouoertheo on 2009-01-27
Where do i go to look for the ACPI stuff, and how would that affect the consistent xruns with jack?

I don't have any shared interrupts with my soundcard, and no wireless chip to worry about.

17:     269067   IO-APIC-fasteoi   EMU10K1 <-- this means there's no shared irq right?

damn... just noticed that they said not to upgrade to 8.10 if you have multiple processors. :(

---

### Post by dodd_alex on 2009-02-20
I am getting instant xruns with newly upgraded from Ubuntu 10 to Ubuntu Studio. I have tried changing many of the settings in the Jack Setup including the Frames/Period, Sample Rate, Periods/Buffer, Realtime and Soft Mode. I also checked /proc but it is totally empty. I'm stumped.

Help?

---

### Post by markbuntu on 2009-02-22
1232822312370.176 msecs

That is more than 1 billion seconds... it is a bogus message, probably from the driver. I don't think you really need to worry too much about that.

---

### Post by Reeman on 2009-02-25
Seeing that irq 3,4and 5 are free try reassigning them to the pci bus in the bios if possible on a laptop. This should do no harm as you are not using a serial port. If there is a serial port try disable in bios. Because you have a reported IRQ error there is something going on here that you should be able to modify in the bios. In the wonderful world of windows irq sharing has become the norm but in the real world of rt audio it sucks!

---

### Post by kakyoism on 2009-02-25
I'm running 8.04 server (to make full use of my 6G RAM)...
And I get tons of problem, should I really switch to rt?
I remember playing with Periods/Buffer can solve certain 
hardware issues, but this time I had a bad luck with that.

See below a dry run (no application connected)
Also when I try to connect Audacious to it, I get
```
ports used in attemped connection are not of the same data type
```
LOL, there's even a typo in the error message...


```
23:17:22.874 Patchbay deactivated.
23:17:22.962 Statistics reset.
23:17:23.036 Startup script...
23:17:23.037 artsshell -q terminate
23:17:23.099 ALSA connection graph change.
23:17:23.452 Startup script terminated with exit status=256.
23:17:23.452 JACK is starting...
23:17:23.452 /usr/bin/jackd -R -P80 -p1024 -t1000 -dalsa -dhw:0 -r48000 -p128 -n8 -D -Phw:1 -m -Xseq
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
23:17:23.462 JACK was started with PID=4317.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:0|128|8|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 8 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 8 periods for capture
port created: in-14-0-Midi-Through-Port-0
port created: out-14-0-Midi-Through-Port-0
port created: out-128-0-TiMidity-port-0
port created: out-128-1-TiMidity-port-1
port created: out-128-2-TiMidity-port-2
port created: out-128-3-TiMidity-port-3
23:17:23.657 ALSA connection change.
ports used in attemped connection are not of the same data type
ports used in attemped connection are not of the same data type
ports used in attemped connection are not of the same data type
ports used in attemped connection are not of the same data type
ports used in attemped connection are not of the same data type
23:17:25.712 Server configuration saved to "/home/kakyo/.jackdrc".
23:17:25.714 Statistics reset.
23:17:25.751 Client activated.
23:17:25.753 JACK connection change.
23:17:25.757 JACK connection graph change.
23:17:32.310 XRUN callback (1).
delay of 2651.000 usecs exceeds estimated spare time of 2634.000; restart ...
delay of 2654.000 usecs exceeds estimated spare time of 2629.000; restart ...
23:17:46.672 XRUN callback (2).
delay of 2654.000 usecs exceeds estimated spare time of 2631.000; restart ...
23:17:56.566 XRUN callback (3).
delay of 2660.000 usecs exceeds estimated spare time of 2617.000; restart ...
23:17:58.643 XRUN callback (4).
23:18:13.010 XRUN callback (5).
delay of 2657.000 usecs exceeds estimated spare time of 2610.000; restart ...
delay of 2638.000 usecs exceeds estimated spare time of 2610.000; restart ...
23:18:14.715 XRUN callback (1 skipped).
delay of 2657.000 usecs exceeds estimated spare time of 2637.000; restart ...
23:18:43.428 XRUN callback (7).
delay of 2653.000 usecs exceeds estimated spare time of 2631.000; restart ...
23:18:45.495 XRUN callback (8).
23:18:55.038 XRUN callback (9).
delay of 2643.000 usecs exceeds estimated spare time of 2630.000; restart ...
delay of 2650.000 usecs exceeds estimated spare time of 2630.000; restart ...
23:18:55.516 XRUN callback (1 skipped).
delay of 2656.000 usecs exceeds estimated spare time of 2622.000; restart ...
23:18:58.524 XRUN callback (11).
delay of 2660.000 usecs exceeds estimated spare time of 2633.000; restart ...
23:18:59.576 XRUN callback (1 skipped).
delay of 2655.000 usecs exceeds estimated spare time of 2633.000; restart ...
```

---

### Post by babarosa on 2009-02-26
Hi folks!

Did you already adjust these settings I recommended? [http://ubuntuforums.org/showthread.php?t=965611&highlight=jack+limits](http://ubuntuforums.org/showthread.php?t=965611&highlight=jack+limits)

These are the only ones (besides giving rights to certain groups) I have to adjust to get a very stable working audio system.

Regards, Michael

P.S. i forgot to mention that I do have an Intel HDA in my notebook working very fine and delivering astonishing audio-quality.

---

### Post by grubby on 2009-02-28
Hi, interesting thread. I, too, have the infamous HDA Intel and it appears to be sharing an interrupt with the SATA drivers if I'm not msitaken:

tom@horse:~$ cat /proc/interrupts 
           CPU0       CPU1       
  0:        373        242   IO-APIC-edge      timer
  1:      11775      11832   IO-APIC-edge      i8042
  4:          3          3   IO-APIC-edge    
  8:         23         25   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 16:    5497243    5494749   IO-APIC-fasteoi   uhci_hcd:usb1, pata_marvell, eth2, nvidia
 18:     127224     127159   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb4, uhci_hcd:usb7
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 21:          5          4   IO-APIC-fasteoi   uhci_hcd:usb2
 22:   10641901   10644416   IO-APIC-fasteoi   ata_piix, ata_piix, HDA Intel
 23:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb8
219:          0          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:   36428097   38636357   Local timer interrupts
RES:    1156930    1052412   Rescheduling interrupts
CAL:     119658     113038   function call interrupts
TLB:      15581      16586   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0


Is it worth buying a new sound card, or is there a way to make this work?

Does someone maintain a list of the best soundcards for use with jack for pro audio?

Cheers

---

