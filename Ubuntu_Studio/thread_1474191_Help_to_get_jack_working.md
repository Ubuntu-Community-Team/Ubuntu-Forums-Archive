---
title: "Help to get jack working"
date: 2010-05-05
forum: Ubuntu Studio
---

### Post by risotto77 on 2010-05-05
Hi

I have installed Ubuntustudio over a regular Ubuntu 10.04 installation. But can not get jack sound working. Jackd starts but nothing will connect to it. I have tried with the 2.6.31 rt kernel and with the 2.6.32 preemtive kernel. Allso I have updated jack to jack2 from here [https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/). I have an EWS88MT card using the ice1712 driver. Sound is working with pulseaudio or alsa-only, but have no luck with jackd. 

Have in /etc/security/limits.conf:
> @audio - rtprio 99
@audio - memlock unlimited

Message from qjackctl:
> 02:51:17.223 JACK was started with PID=5044.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver ICE1712 running on card 0 - TerraTec EWS88MT at 0xbc00, irq 18
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
02:51:19.339 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
no message buffer overruns
no message buffer overruns
unknown option character l

Looks like it is a problem to connect to the server. I need help.

---

### Post by AutoStatic on 2010-05-06
Hello risotto77,

Try raising the priority for JACK. Default is 60, but in your case it's running with prio 10. And could you post your JACK settings? Fastest way is to open a terminal, enter **cat ~/.jackdrc** and copy and paste the output.

---

### Post by risotto77 on 2010-05-09
Tried with priority 60 for jackd, but no difference.


~$ cat ~/.jackdrc
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0

---

### Post by risotto77 on 2010-05-11
bump

---

### Post by maliStfn on 2010-05-11
Did you try to change 48kHz to 44.1kHz and to use 16bit instead of 32bit?

---

### Post by risotto77 on 2010-05-11
> **maliStfn said:**
> Did you try to change 48kHz to 44.1kHz and to use 16bit instead of 32bit?


Tried now. Same "Could not connect to JACK server as client..." message

---

### Post by grtyvr on 2010-05-11
Hi,
 
I just installed Ubuntu Studio 10.04 and installed the rt kernel.  Jackd now uses the file
 
/etc/security/limits.d/audio.conf
 
rather than
 
/etc/security/limits.conf
 
I deleted the @audio lines in the /etc/security/limits.conf  and Jack started fine after that.  (I rebooted too, just to be paranoid.)
 
--
Guy
 
 
> **risotto77 said:**
> Hi
 
I have installed Ubuntustudio over a regular Ubuntu 10.04 installation. But can not get jack sound working. Jackd starts but nothing will connect to it. I have tried with the 2.6.31 rt kernel and with the 2.6.32 preemtive kernel. Allso I have updated jack to jack2 from here [https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/). I have an EWS88MT card using the ice1712 driver. Sound is working with pulseaudio or alsa-only, but have no luck with jackd. 
 
Have in /etc/security/limits.conf:
 
 
Message from qjackctl:
 
 
Looks like it is a problem to connect to the server. I need help.

---

### Post by sgx on 2010-05-12
Thanks for posting this. I doubt its printed on the cover of the box :)
I would never have guessed.
Cheers

---

### Post by risotto77 on 2010-05-12
Deleted the lines in /etc/security/limits.conf,rebooted, but no difference here. The jack daemon is starting, but looks like no client will connect to it.

---

### Post by thorgal on 2010-05-12
why do you start jack with the -T option (temporary jack server IIRC) ?

I also think you should try

```

jackd -h

```

to get some help. I think (but I may be misleading here) that the -R option is now reversed to what it used to be: it now disables RT mode! so when you check the RT mode option in qjackctl and save your options, have a look in $HOME/.jackdrc and see if the -R option is in there ;)

---

### Post by risotto77 on 2010-05-12
Not sure if this has anything to do with anything, but to me it looks like jackd do not get the settings from qjackctl. In qjackctl I have ticked the "Force 16bit", I have set Sample Rate to 44100, and have ticked the save JACK audio configuration to: .jackdrc. But these settings are not showing in .jackdrc:


~$ cat ~/.jackdrc
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0

---

### Post by thorgal on 2010-05-12
> **risotto77 said:**
> Not sure if this has anything to do with anything, but to me it looks like jackd do not get the settings from qjackctl. In qjackctl I have ticked the "Force 16bit", I have set Sample Rate to 44100, and have ticked the save JACK audio configuration to: .jackdrc. But these settings are not showing in .jackdrc:


~$ cat ~/.jackdrc
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0

IIRC, you have to run your new config once in qjackctl before it is saved. So if you save a new set of options, run it via qjackctl and then, check .jackdrc after you stop the jack server via qjackctl.

---

### Post by risotto77 on 2010-05-12
> **thorgal said:**
> why do you start jack with the -T option (temporary jack server IIRC) ?


Because it was there by default. Not my idea. I do not understand the jackd options and really thought I could control it from qjackctl. Now I am not sure.

---

### Post by thorgal on 2010-05-12
could be you have a 'jackdbus' installation and you are not controlling the jackd options yourself. The jackdbus options are saved in an entirely different place.

Qjackctl 0.3.6 can now control jackdbus. You may have an unlucky combination of s/w versions and capabilities. I personally cannot help you more as my DAW system is not running ubuntu and I compile jackd myself (don't want to rely on prepackaged stuff for this important component of my studio).

---

### Post by risotto77 on 2010-05-12
> **thorgal said:**
> IIRC, you have to run your new config once in qjackctl before it is saved. So if you save a new set of options, run it via qjackctl and then, check .jackdrc after you stop the jack server via qjackctl.


Qjackctl are writing to .jackdrc (I tried to manually edit the .qjackrc and qjackctl did write over it) but it do not give the options I give in qjackctl "settings". For instance I set Sample Rate to 44100 but qjackctl insist to write 48000 to .jackdrc

~$ cat ~/.jackdrc
/usr/bin/jackd -p 128 -R -P 60 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0

---

### Post by risotto77 on 2010-05-12
> **thorgal said:**
> could be you have a 'jackdbus' installation and you are not controlling the jackd options yourself. The jackdbus options are saved in an entirely different place.

Qjackctl 0.3.6 can now control jackdbus. You may have an unlucky combination of s/w versions and capabilities. I personally cannot help you more as my DAW system is not running ubuntu and I compile jackd myself (don't want to rely on prepackaged stuff for this important component of my studio).


Thanks for pointer. I will look for how to handle jackdbus then. (I have version 0.3.6)

---

### Post by risotto77 on 2010-05-15
I have problem solved now. I am not sure how it got working, but I have reinstalled a lot of software, removed the ubuntu-desktop and ubuntustudio-desktop, and installed the audio and video production software with tasksel.

---

