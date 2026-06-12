---
title: "How to get this thing working"
date: 2011-01-15
forum: Ubuntu Studio
---

### Post by hgernhardt on 2011-01-15
I hate to admit it, but I'm at my wits' end.  Timidity works on the command line, but only if I haven't started jackd.  I can't get jackd to run properly (continuous xruns), and I can't get clients to connect to it.  I'm sure pulseaudio has something to do with this.

All this frustration comes with a stock install of Ubuntu Studio 10.10.

Does anyone have a step-by-step howto in order to get PulseAudio, Timidity++, and JACK working together like the fine-tuned machine they should be?

Thanks!

---

### Post by Pablo_F on 2011-01-16
Hi, 

You need -Oj option in the command line to "jackify" timidity. Nevertheless, I don't think timidity is a good jack client. I suggest you try qsynth (software center). You have to load a soundfont in qsynth. You probably already have one in */usr/share/sounds/sf2*. 

As for the xruns, we need more info to tell you something. There is a message window. 

Cheers! Pablo

---

### Post by hgernhardt on 2011-01-16
Thanks, Pablo, for the reply.  As it turns out, QSynth was part of the default install.

So, here's what I'm faced with when I attempt to start JACK from qjackctl:

```

sh: artsshell: not found
14:20:52.413 Startup script terminated with exit status=32512.
14:20:52.413 JACK is starting...
14:20:52.414 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
14:20:52.437 JACK was started with PID=3353.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xd2400000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
14:20:59.665 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
14:21:02.427 JACK is stopping...
jack main caught signal 15
JackAudioDriver::ProcessAsync: read error, skip cycle
Released audio card Audio0
audio_reservation_finish
14:21:02.542 JACK was stopped successfully.
14:21:02.543 Post-shutdown script...
14:21:02.543 killall jackd
jackd: no process found
14:21:02.983 Post-shutdown script terminated with exit status=256.

```

As you can see, xruns aside, I can't even *connect* to jackd.  This seems to be happening whether or not I have timidity or pulseaudio running.  My runlevel initialization has pulseaudio starting at S50, and timidity starting at S99.  NOTE:  This is the configuration that shipped with Ubuntu Studio 10.10.

Thanks for any help,

Henry

---

### Post by Pablo_F on 2011-01-16
Hi,

It is possible that your audio card is sharing IRQ number with some other piece of hardware. Take a look at */proc/interrupts*. Also, some onboard cards prefer sample rate 48 kHz. Another thing, as you are running jackd2 (version 1.9.x), try the synchronous mode by appending the -S option to the jackd comand (in the server path field of qjackctl's configuration tab). 

I don't think pulseaudio is to blame for the xruns but just in case try keeping it out of the way by killing it before you launch jackd. You would need to avoid pulseaudio's autospawn:

> echo "autospawn = no" > ~/.pulse/client.conf

Then you can write *pulseaudio -k* to kill pulseaudio as the prestart script in qjackctl's options, instead of the useless *artshell -q terminate*

Cheers! Pablo

---

### Post by hgernhardt on 2011-01-16
Once again, Pablo, thanks.  I've changed qjackctl to kill pulseaudio on startup.  I did, however, discover that I have rather a significant interrupt conflict:

```

16:    1011217     181435   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, hda_intel
19:         73        170   IO-APIC-fasteoi   ehci_hcd:usb2, hda_intel

```

This would explain why it seemed to work every now and again.  With the sound card on the same interrupts as my USB ports, I don't stand a chance of getting this thing up and running.

How, then, do I change what device uses which interrupt?

Thanks again,

Henry

---

### Post by Pablo_F on 2011-01-16
I am not sure if you can change IRQ numbers. Maybe from BIOS... If you install a rt kernel you can give priority to the soundcard even if it is sharing IRQ number, but you can not do that with a generic kernel. The bad news is that there is not an rt kernel available in maverick. There is in lucid and I hope there will be in natty.

By the way, you have two hda-intel soundcards. Make sure jack is using the right one. What is there in */proc/asound/cards* ?

Cheers, Pablo

---

### Post by hgernhardt on 2011-01-17
Okay.  So, for some strange, odd reason that makes no sense to me, jackd is running this morning.  I haven't changed the interrupt mapping (and I don't really know how; my google-fu seems to not be working in this regard).

What I *have* done, however, is changed my pre-start, post-start, pre-shutdown, and post-shutdown scripts.  I like the desktop login sound, so I've done the following:

Pre-start: [FONT="Courier New"]echo "autospawn = no" > ~/.pulse/client.conf; pulseaudio -k[/FONT]
Post-start: [FONT="Courier New"]timidity -Oj -iAD[/FONT]
Pre-stop: [FONT="Courier New"]killall timidity[/FONT]
Post-stop: [FONT="Courier New"]killall jackd; pulseaudio --start; rm ~/.pulse/client.conf[/FONT]

I'm using timidity because it sounds better than fluidsynth.  For some reason, fluidsynth is generating evil noise rather than nice sounds (using [FONT="Courier New"]/usr/share/sounds/sf2/FluidR3_GM.sf2[/FONT]) when I run rosegarden through it.

> **Pablo_F said:**
> The bad news is that there is not an rt kernel available in maverick.

I've been hearing that.  Despite this, I have an [FONT="Courier New"]/etc/defaults/rtirq[/FONT] filem abd the “RT” indicator in qjackctl comes on every now and again.  I also seem to remember the installation of jackd2 asking permission for realtime priorities for the audio group.

> **Pablo_F said:**
> By the way, you have two hda-intel soundcards. Make sure jack is using the right one. What is there in */proc/asound/cards*

It's using the correct one.  Interrupt 16 is the analog card, and Interrupt 19 is the HDMI card.  I'm not using the HDMI port.

Overall, I still remain rather a bit confused.  Why will jackd start normally at some times (it did so while I was at church yesterday), yet not others (like it did yesterday afternoon when I posted last)?  Is this, in fact, due to a conflict of shared interrupts?

Pablo, I truly appreciate every iota of assistance you've given me.  I'm hoping that more information will turn up so that some of these other lingering questions will be answered.

Thanks,

Henry

---

### Post by Pablo_F on 2011-01-17
Hi, 

> I have an /etc/defaults/rtirq filem abd the “RT” indicator in qjackctl comes on every now and again. I also seem to remember the installation of jackd2 asking permission for realtime priorities for the audio group.

Yes, jackd is running with realtime priority and that can be perfectly done with a generic kernel but if you don't have a kernel with the PREEMPT_RT patch you cannot raise the priority of the soundcard over other kernel threads. And rtirq is useless with a generic kernel. See [http://jackaudio.org/realtime_vs_realtime_kernel](http://jackaudio.org/realtime_vs_realtime_kernel) and [http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107) 

> It's using the correct one.

Sorry but just in case I tell you that the card order is sometimes messed up, so if you are using (default) or hw:0 in jack, it could be that you are using the wrong card at times. For this reason, it is recommended that you use card names, not numbers. For example "hw:Intel" which you type in the interface field of qjackctl. See the actual name between brackets in /proc/asound/cards.

Other than this, I don't know what happens. Maybe disable wireless or any device that shares IRQ number with the card.

Cheers, Pablo

---

### Post by hgernhardt on 2011-01-18
Pablo—
> **Pablo_F said:**
> 
Yes, jackd is running with realtime priority and that can be perfectly done with a generic kernel[…]

Cool.  Based upon my needs, though, I'm thinking that an RT kernel might be overkill for me.  That, and it seems that I can get jackd to run properly now, whether it be the onboard sound or the USB headset I have.

> **Pablo_F said:**
> 
Sorry but just in case I tell you that the card order is sometimes messed up, so if you are using (default) or hw:0 in jack, it could be that you are using the wrong card at times.

Ah, point well taken.  I've adjusted my qjackctl configs to match this.

> **Pablo_F said:**
> 
Other than this, I don't know what happens. Maybe disable wireless or any device that shares IRQ number with the card.


It's something on the USB port, that much I can say with a small amount of certainty based upon [FONT="Courier New"]/proc/interrupts[/FONT].  If only there were a simple way to give interrupt mapping hints to the PCI bus handler!  Be that as it may, I've been getting consistent runs for the past day.  Pablo, you have been a ***great*** help in this matter, and I appreciate all the time you have taken.

Many thanks,

Henry

---

