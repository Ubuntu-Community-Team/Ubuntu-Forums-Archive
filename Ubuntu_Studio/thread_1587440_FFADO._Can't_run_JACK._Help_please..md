---
title: "FFADO. Can't run JACK. Help please."
date: 2010-10-03
forum: Ubuntu Studio
---

### Post by sonm on 2010-10-03
Hi, I am new to Ubuntu Studio. Recently decided to switch from Windows, but unfortunately, can't do it completely yet.  So far that is the system conf.
1) Acer Aspire 5715Z laptop 2) PCExpress card FireWire adapter 3) ECHO AudioFire4 soundcard.
I've managed to install FFADO driver, can run FFADO mixer, even can control the soundcard (channel volume etc) but I keep on failing with running JACK. Apparently there are some problems with RT-stuff. That's what I have so far

sonm@ubuntus:~$ uname -a
Linux ubuntus 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux

sonm@ubuntus:~$ lspci | grep FireWire
03:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)

sonm@ubuntus:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.999.0-1903
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0014860a9abe7b4d  0x00001486  0x00000AF4   Echo Digital Audio - AudioFire4
   1       0x0102030400000169  0x00010203  0x00000000   Linux - ohci1394  - 
no message buffer overruns

Whatever parameters I use for JACK it keeps on crashing...
I've tried to play around with the IRQs according to 
[http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)
but discovered that I actually don't have Yenta module...
I dunno whether it should be present for PCExpress card or not... but there is something wrong with the JACK.
I made my user a mamber of audio and disk groups. And again...
sonm@ubuntus:~/ffado-svn/tests$ jackd -d firewire -n 3 -p 2048
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    757122
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
02197275074:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1903 built Sep 22 2010 18:42:37
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
no message buffer overruns

Could anyone make any suggestion?

---

### Post by AutoStatic on 2010-10-03
> **sonm said:**
> 02197275074:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1903 built Sep 22 2010 18:42:37
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driverHello sonm, ffado is in the default repositories so it's not necessary to compile it yourself (apparently you've doen that looking at the version number of ffado). In your case I think it's even better to use the one from the repositories. That's a stable version of ffado, so the least error prone. But for now, just let it be, ffado is probably installed in */usr/local* so if you now install ffado from the default repo's ffado will probably stop working (conflicting versions on one machine).
Could you post the outcome of **cat /proc/interrupts** ? And are you using rtirq?

Best,

Jeremy

---

### Post by bluesscream on 2010-10-03
Hi sonm,
This is my way if ffado/jack don't do their job - distilled out of many howto's:
0. run ffadomixer. If it shows the gliders goto 4.
1. Run ubuntustudio-controls with all options defaults marked
2. control files manually: /lib/udev/rules.d/50(or an other number)-udev-default-rules: is there a line 'KERNEL=="raw1394", GROUP="video"' (mostly near the end of the file)?
ls -l /dev/raw1394 should be like 'crw-rw---- 1 root video 171, 0 2009-11-26 09:56 /dev/raw1394. reboot
3. has user rights for audio and video? (system/administration/users and groups/myuser/properties/user rights). If ffadomixer still shows no device goto 10.a.
4. make sure /etc/security/limits.conf and /etc/security/limits.d/audio.conf both contain identical @audio settings esp. a line '@audio - rtprio 99'
5. does jackd run with alsa? with rt unmarked? with low performance settings? Explicitely the internal soundchip selected? if not at all goto 10 b
6. reset fw device, make sure the same samplerate is selected as in qjackctl.
7. try lower priorities in jack i.E. default(=10)
8. Is cpu frequency set to full speed - 'userspace max' or 'perfomance' for each core?
9. Have a look into system-monitor-applet - are there zombie-processes of jackd or other stopped programmes?
10. If it's still not running, completely remove a. ffado b. jackd, with all configurations, install them new after consulting the howtos.
good luck
bluesscream

P.S. For me most frequent ffado failure was result of forgetting to set the sample rate in jack to the same value as selected with the device's knob

---

### Post by trulan on 2010-10-03
For your permissions settings, the firewire devices get assigned to the 'audio' group in Ubuntu 10.04 or newer, and to the 'video' group in 9.10 and older.  Debian assigns them to the 'disk' group.  Running
```
ls -al /dev/raw1394
```will tell you where it is actually assigned.

One question though:  Does your Audiofire4 work under windows?  I don't want to be discouraging, but I struck out trying to run ffado on an express card (and yes, it was a TI firewire chip).  I used to have a Dell Inspiron (e1505 IIRC), one of the first ones to have an express card instead of the older PCMCIA cards.  Firewire audio worked on the internal firewire chip but not on the express card.  The mini plug for the onboard firewire broke, and since the express card was a failure I ended up getting another computer (which I have never regretted BTW).  But on that thing, the express card was a complete failure on Windows too.  I finally concluded that it was a poor implementation of a PCI bridge or something.  So if yours works (even sort of works) on Windows then forget what I said, it should work on Ubuntu too.  But if it's a no-go on Windows, it could be more of a hardware problem.

---

### Post by AutoStatic on 2010-10-04
Hello bluesscream,

> **bluesscream said:**
> 7. try lower priorities in jack i.E. default(=10)Lower JACK's priorities, why would you like to do that? And JACK's default prio is 50, not 10.

> **bluesscream said:**
> 10. If it's still not running, completely remove a. ffado b. jackd, with all configurations, install them new after consulting the howtos.IMHO very time-consuming and unnecessary. It doesn't help troubleshooting the issue either.

Just my 2¢.

And regarding my post, I mixed up error messages, using rtirq is probably not necessary unles you get *DRIVER NT: could not run driver cycle* errors.

---

### Post by sonm on 2010-10-04
Thank you all for your replies. I think I'll get much faster through the problem with your help. So actually my ffado location is /home/sonm/ffado-svn and of course for executable files it is /usr/bin...
Does that make any difference?
Then here what I have for cat /proc/interrupts


sonm@ubuntus:/usr/local$ cat /proc/interrupts 
           CPU0       CPU1       
  0:        135          1   IO-APIC-edge      timer
  1:       2010          4   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:        832      13562   IO-APIC-fasteoi   acpi
 12:         52      31879   IO-APIC-edge      i8042
 14:       2266       2190   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:          1        193   IO-APIC-fasteoi   uhci_hcd:usb3, ohci1394
 18:          0          1   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6, ath
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        132        737   IO-APIC-fasteoi   HDA Intel
 23:          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 28:       8941       1377   PCI-MSI-edge      ahci
 29:       3312         35   PCI-MSI-edge      i915
 30:         23       2987   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     907644     916348   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:        511        333   Rescheduling interrupts
CAL:        735        852   Function call interrupts
TLB:       1533       1627   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          3          3   Machine check polls
ERR:          0
MIS:          0

Am not using rtirq

2 Bluescream... Well I'll try what you've suggested and reply asap.

That's the output for 

sonm@ubuntus:/usr/local$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2010-10-04 12:51 /dev/raw1394

I was actually doing

sonm@ubuntus:/usr/local$ sudo chmod 666 /dev/raw1394
 but that seems to be absolutely irrelevant.
2 Trulan
My ECHO AudioFire perfectly works with Windows and we've played numerous shows with it. Yet the system (Windows) itself pose many problems that's why I'd like to be able to toggle between Windows and Linux with the ultimate switching to Linux in the end.

---

### Post by sonm on 2010-10-04
That's what I have for the very first attempt to run the JACK
13:17:13.414 Patchbay deactivated.
13:17:13.465 Statistics reset.
13:17:13.560 Startup script...
13:17:13.561 artsshell -q terminate
sh: artsshell: not found
13:17:13.964 Startup script terminated with exit status=32512.
13:17:13.965 JACK is starting...
13:17:13.966 /usr/bin/jackd -P76 -p128 -dfirewire -dhw:0 -r48000 -p16 -n2 -i4 -o4
13:17:13.989 JACK was started with PID=4704.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    757122
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
01555575426:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1903 built Sep 22 2010 18:42:37
jackd: src/libutil/TimestampedBuffer.cpp:1029: void Util::TimestampedBuffer::incrementFrameCounter(unsigned int, ffado_timestamp_t): Assertion `nbframes == m_update_period' failed.
13:17:15.047 JACK was stopped successfully.
13:17:15.048 Post-shutdown script...
13:17:15.048 killall jackd
13:17:15.049 JACK has crashed.
jackd: no process found
13:17:15.468 Post-shutdown script terminated with exit status=256.
13:17:16.209 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by sonm on 2010-10-04
Well... it seems that my FFADO is oddly installed... at least 
$which ffado gives me nothing... 
and indeed there is nothing in /usr and /usr/local
Can that be the core of the problem? But on the other hand... the ffado mixer works...
Uffa...

---

### Post by Pablo_F on 2010-10-04
Imo, you should use rtirq.

sudo apt-get install rtirq-init

sudo gedit /etc/default/rtirq

Edit the line:

RTIRQ_NAME_LIST="rtc ohci1394"

And reboot the computer.

To locate the ffado libs and bins, use locate instead of which:

sudo updatedb
locate ffado

Increase frames/period. Use default as the interface. I am not sure if you have to specify the number of channels but normally default is more adequate.

Try launching jackd from CLI with a more conservative and mostly default setting, like:

/usr/bin/jackd -dfirewire

And attach the output of the terminal.

Cheers! Pablo

---

### Post by sonm on 2010-10-04
I've installed rtirq. Edited the line with ohci1394, ran 
sudo /etc/init.d/rtirq start
... still the same problem... jack d says

sonm@ubuntus:~$ jackd -d firewire
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    757122
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
01422530065:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1903 built Sep 22 2010 18:42:37
firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver
cannot start driver
no message buffer overruns
====================
Should I post what ffado-dbus-server says?

---

### Post by Pablo_F on 2010-10-04
Sorry, that output is not as verbose as I thought.

A sample rate mismatch? Just trying to guess.

Make sure you have the same sample rate in the card and in jack setting. Maybe try to start jackd with:

jackd -v -dfirewire -r96000

???

Anyway, I suggest you ask in the ffado users mailing list.  

[http://www.ffado.org/](http://www.ffado.org/)

[http://www.ffado.org/?q=node/69](http://www.ffado.org/?q=node/69)

[http://sourceforge.net/mailarchive/forum.php?forum_name=ffado-user](http://sourceforge.net/mailarchive/forum.php?forum_name=ffado-user)

Cheers! Pablo

---

### Post by bluesscream on 2010-10-04
sorry, my workaround is obsolete in some points (I retained old settings after dist-upgrading). I'd suggest to make sure /dev/raw1934 is in group audio and there is a line 
KERNEL=="raw1394", GROUP="audio" 
in /lib/udev/rules.d/50(or an other number)-udev-default-rules.
This works for me with "video" as well as with "audio", but must be the same at both places and user a member of the selected group.
@autostatic: I once, don't remember the kernel and jack version, ran into troubles with high jack priorities - nostart, crashes, xruns...
This remove-and-reinstall behavior is a bad habit which remained from times with an other OS ;)
regards bluesscream

---

### Post by AutoStatic on 2010-10-05
sonm, did you take a look here:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Best,

Jeremy

---

### Post by sonm on 2010-10-09
There is some weird problem, which I can't solve. Definitely. I think I'll install everything in Windows and check the configuration of the ECHO. Joining the m-list must be helpful too.
I'll play around the KERNEL=="raw1394", GROUP="audio" as well!
And after all! I can't beleive the piece of iron can be stronger than the human intelligence!!!:lolflag:

---

