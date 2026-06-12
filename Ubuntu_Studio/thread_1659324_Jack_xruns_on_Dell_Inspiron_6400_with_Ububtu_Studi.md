---
title: "Jack xruns on Dell Inspiron 6400 with Ububtu Studio 10.10"
date: 2011-01-03
forum: Ubuntu Studio
---

### Post by Shamus on 2011-01-03
Hi.

I have simple needs: I just want to get Internet DJ Console (IDJC) running on my laptop (a Dell Inspiron 6400 with 1MB RAM, 120GB SATA HD - yes, I know I really need more RAM, hehe) so I can do some Internet DJing again like I used to do a couple of years ago (using Windows and SAM Broadcaster on a different laptop in those days), plus do some simple MP3 manipulation: volume normalization, ID3 tag editing: nothing technical, no rocket science. I just want to be able to stream MP3 audio to a Shoutcast server or two, and have some of the features that SAM Broadcaster had: automatically crossfading between tracks, skipping over any silence that an MP3 contained and allowing voice over music for my announcements and "DJ chatter".

I tried PCLinuxOS (PCLOS) 2010.12 a few days ago and was able to get IDJC and Jack working, but I started having other issues, probably to do with all the crap I'd installed in the course of trying to get these working. Since I needed to reinstall the OS anyway I decided to give Ubuntu a try as it seems to be more popular, and has newer versions of apps in its repositories than PCLOS does. 

I installed Ubuntu 10.10 (with GNOME, the most basic and common Ubuntu version) two days ago. After updating all software I installed jackd and the Jack GUI control panel (qjackctl) plus IJDC, but could never get Jack to start- kept getting xruns. Research suggested that I needed a low-latency realtime kernel, available with Ubuntu Studio, so I installed Studio last night (10.10 Maverick Meerkat). I still get the xruns when trying to start Jack (which won't start), even with frames/period set as low as it will go and periods/buffer up around 100 or so.

I searched the forum and found how to start jackd from the command line:
> jackd -d alsa -P and that worked. My terminal's output showed:
> jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xefebc000 irq 42
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
jack main caught signal 15
Released audio card Audio0
audio_reservation_finish

I then went to the Jack Control GUI and clicked the Start button, with jackd already running in the terminal, and it said Jack was running and the message window had no more xruns. The message just said > 09:37:30.569 Client activated.
09:37:30.674 JACK connection change. 

I stopped Jack in the GUI then went into Configure and set up Jack according to what my terminal showed: hw0, 48000Hz, 1024 frames, buffer = 2, saved, and clicked Start: Jack still wouldn't start and I got xruns galore!

So why does Jack bomb out when starting it via the GUI control panel but work when starting it in a terminal?


FYI, I remember that in PCLOX Jack had three available sound card drivers: HDA Intel, STAX Analog and STAX Digital, and Jack would only work if I chose STAX Digital. Ubuntu Studio only has HDA Intel and STAX Analog to choose from. I'm not sure if that has anything to do with it?

---

### Post by Pablo_F on 2011-01-04
Hi, 

"jackd -dalsa -P" means that you run jack in playback only mode, so there are not capture ports. The minimum jackd command should be:

jackd -dalsa

which means duplex mode (capture and playback at the same time) with the default audio card as the "Interface", default sample rate, frames/period, etc, which are good for starters. However, I recommend you use qjackctl, but then give the content of the message window if something goes wrong.

OTOH, using card numbers (like hw:0, hw:1, etc) is not a good idea. It is much better if you use card names (and subdevice numbers if applicable). I know, this is not obvious. Please give the output of:

**arecord -l && aplay -l**

Cheers, Pablo

---

### Post by Shamus on 2011-01-05
Ah, so that's what the command-line switch meant. Guess I should have read jackd's man page. :)

Using qjack I can start jackd in playback mode only. When I try record mode only, it fails:

> 15:25:00.542 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client


Running "jackd -dalsa" from the command line also fails with xruns:

> JackAudioDriver:: ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery


My "arecord -l && aplay -l" output:

> **** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The only sound cards available in qjack's Interface pick list (clicking the right-arrow button to the right of the dropdown list's arrow) are:
hw:0     HDA Intel
hw:0,0   STAX92xx Analog
(default)

If I click on the Interface dropdown arrow for that pick list I see:
/dev/audio
/dev/dsp
hw:0
hw:0,0
plughw:0
(default)


Trying each of these fails. It says /dev/audio doesn't exist, /dev/dsp "unable to connect to server socket" generic red error message, plughw:0 gives xruns, hw:0 gives xruns, hw:0,0 gives xruns.

I started over, configuring qjack according to the instructions at [http://ubuntuforums.org/showthread.php?t=1434555](http://ubuntuforums.org/showthread.php?t=1434555) and when I start jackd via qjack's Start button I get this in the message window:
> 
15:51:33.906 Startup script...
15:51:33.907 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
15:51:34.310 Startup script terminated with exit status=32512.
15:51:34.310 JACK is starting...
15:51:34.311 /usr/bin/jackd -dalsa -dhw:0,0 -r44100 -p256 -n2 -m
15:51:34.317 JACK was started with PID=2374.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0,0|hw:0,0|256|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xefebc000 irq 42
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
AcquireSelfRealTime error
alsa_driver_xrun_recovery
JackAudioDriver:: ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver:: ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver:: ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver:: ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver:: ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver:: ProcessAsync: read error, skip cycle


etc. until I click Stop.

---

### Post by AutoStatic on 2011-01-05
Hello Shamus, you could try installing the **linux-backports-modules-alsa-maverick-generic** package. I have the same onboard soundchip and it won't work with Jack unless I install this backports package.

Best,

Jeremy

---

### Post by Shamus on 2011-01-05
I just installed that, Jeremy, but it didn't make any difference. I just downloaded the ISO image of Ubuntu Studio 10.04.1. If it's a Live CD maybe I'll try it from a cD boot and see if Jack starts. I'm beginning to think that jackd doesn't "just work" on Ubuntu. :(

---

### Post by AutoStatic on 2011-01-05
> **Shamus said:**
> I just installed that, Jeremy, but it didn't make any difference.And after a reboot?

> **Shamus said:**
> I just downloaded the ISO image of Ubuntu Studio 10.04.1. If it's a Live CD maybe I'll try it from a cD boot and see if Jack starts.I'm using 10.04 and my onboard soundcard works ok with Jack, but only after installing the backports package.

> **Shamus said:**
> I'm beginning to think that jackd doesn't "just work" on Ubuntu. :(No it doesn't, it takes some tweaking and configuring to get it to work properly. But that's what this forum is for!

---

### Post by Shamus on 2011-01-05
Oh, yes, I rebooted (figuring those were kernel or module patches, or something similar). 

I'm trying 10.10 Maverick. Just started downloading the Lucid image (I grabbed the regular Ubuntu, not Ubuntu Studio, by mistake) and will try it. I'll definitely take your advice and get those backports the first thing after running the update manager. I'll report back later tonight or tomorrow.

---

### Post by Shamus on 2011-01-05
OK, I ended up installing the regular Ubuntu Lucid then, in Synaptics, installed all the Ubuntu Studio stuff plus the recommended apps and also the linux alsa backports, then added myself to the audio group. Jackd starts, but only if I untick the "Realtime"checkbox: it says I don't have permissions to run in realtime mode.

But now, I can't connect to the Internet in Lucid: the restricted driver for my Broadcom 4311 wifi card won't install. Maybe Lucid installed the realtime kernel? I get no choices of what kernel to use at boot time, so I don't know if that's it or not. So I can either connect to the 'net with Maverick or run jackd/IDJC with Lucid, but not both at the same time? The 'net worked before I installed the Studio stuff.

I guess I'm back to square one, looking for a Linux distro that can run in just 1 meg of RAM, will give me Internet access, run jackd, and has a newer version of IDJC in its distro (or which won't start locking up after I install all the dev libraries required for compiling IDJC from a tarball). I've just about given up on Ubuntu.

I've spent more than three days just trying to get this one app running. This sucks. :mad: (Thanks for trying to help me though.)

---

### Post by AutoStatic on 2011-01-06
> **Shamus said:**
> OK, I ended up installing the regular Ubuntu Lucid then, in Synaptics, installed all the Ubuntu Studio stuff plus the recommended apps and also the linux alsa backports, then added myself to the audio group. Jackd starts, but only if I untick the "Realtime"checkbox: it says I don't have permissions to run in realtime mode.Then you probably forgot to configure Jack to enable users to run it with real-time priviliges. Running **dpkg-reconfigure jackd** might solve this.

> **Shamus said:**
> But now, I can't connect to the Internet in Lucid: the restricted driver for my Broadcom 4311 wifi card won't install.System - Administration - Hardware Drivers doesn't list it?

> **Shamus said:**
> Maybe Lucid installed the realtime kernel?No.

> **Shamus said:**
> I get no choices of what kernel to use at boot time, so I don't know if that's it or not.Did you do a clean install? Then you only have one kernel.

> **Shamus said:**
> So I can either connect to the 'net with Maverick or run jackd/IDJC with Lucid, but not both at the same time? The 'net worked before I installed the Studio stuff.Your Broadcom card should work with Lucid. Try installing the **bcmwl-kernel-source** and **dkms** packages and run System - Administration - Hardware Drivers again.

> **Shamus said:**
> I've spent more than three days just trying to get this one app running. This sucks. :mad: (Thanks for trying to help me though.)The app runs! I don't think it's fair to assume that it sucks then and that you want to give up on Ubuntu just because wifi and Jack don't work properly. That's what this forum is for, to get those things to work!

Best,

Jeremy

---

### Post by blablack on 2011-04-28
Hi guys,

It may seem weird that I would send you a "thank you" out of the blue like that, so let me explain!

2 months ago, I bought a brand new laptop just to record/mix music under Ubuntu with my USB sound card (an Edirol UA-25Ex)....

Anyway...It wasn't working... First of all, thanks to some posts AutoStatic wrote on some forums, I found out that I had the EHCI buggy Intel USB port... So had to switch the ONE XHCI USB 3 port of the laptop...

Then I was getting Xruns every 5 minutes or so.... for 4 weeks I have been trying everything to solve this: recompile the kernel with thousands of options combination, change all the settings in Jack, try Jack 1, try Jack 2, try the internal sound card....But I still had these freaking xruns... I even considered switching to..............Windows (how sad is that!) or considered bying a second new laptop!!!!!!!!

But yesterday, thanks to ONE line you wrote:
> just because wifi and Jack don't work properly

So...why not...I tried turning off the Wifi...
OH JOY IT WORKS!

5ms latency, 6 Yoshimi and 1 SuperLooper, and not a single xrun!

So guys, THANKS A MILLION!

For the ones who sould face the same issue: I run an HP Envy 17 laptop.

---

