---
title: "Yoshimi?"
date: 2011-07-29
forum: Ubuntu Studio
---

### Post by psy-man on 2011-07-29
Hi all, I have installed Ubuntu Studio 11.04. I have something strange to report regarding Yoshimi and its virtual keyboard. The notes I hear are not what I am playing. I cannot connect a real keyboard using the QJack Control connection kit. Yoshimi appears on the midi tab but midi hardware is on the Alsa tab..

---

### Post by Pablo_F on 2011-07-29
Regarding the second issue, you need a2jmidid. In qjackctl, setup, options tab, run script after server start, write down:

a2jmidid -e &

This way you will see your midi keyboard as a jack MIDI device and you will be able to connect to yoshimi input. 

Regarding the first issue, what version are you running and does it happen with every instrument?

Cheers, Pablo

---

### Post by jejeman on 2011-07-29
For second issue check program: a2jmidid.

For first explain little more. What are the notes it is playing?

---

### Post by psy-man on 2011-07-29
hi there, thanks for the reply  a2jmidid  solved the second problem, I will have take a bit more time to consider and describe the first problem better since the notes I hear seem so random. back in a while

---

### Post by Pablo_F on 2011-07-29
Hi, 

Read this:

[http://sourceforge.net/mailarchive/message.php?msg_id=27747821](http://sourceforge.net/mailarchive/message.php?msg_id=27747821)

---

### Post by psy-man on 2011-07-29
yes, that thread describes what is happening. I will try updating Yoshimi or compiling the source. Cheers.

Downloaded the yoshimi-0.060.10 source from source forge
used
 sudo apt-get install cmake-curses-gui
to get cmake
ccmake . throws an error
CMake Error at CMakeLists.txt:105 (message):
  libz required but not found:
what and where is libz ?

---

### Post by Pablo_F on 2011-07-30
To compile from the source code you need the development packages of the dependencies. For example, you need zlib1g-dev, but there will be more missing. 

You can launch synaptic and search for yoshimi, right click, properties, dependencies. You will see that zlib1g is a dependency, so search for zlib1g and you will see there is a zlib1g-dev package. Install it. 

The same applies for most of the other dependencies but not always. It is a bit of a hit and miss. For example, you need a package called fluid which is not there, and beware of the jack dependencies. Don't install libjack-dev but libjack-jackd2-dev (well, unless you want to shift to jackd1).

I just tried in 11.04 and I can confirm the problem and the solution.

Cheers, Pablo

---

### Post by psy-man on 2011-07-30
hi all, I'm back again, I have installed all the dependencies, in addition to those shown in synaptic and fluid also required are 
fftw3
boost headers
fontconfig>0.22
I found and installed them and have now compiled yoshimi-0.060.10 
But I do not know how to make it work. The new version is installed to /usr/local/bin and so it does not over write the older version, however having run the sudo make install I guess other files have been over written as the old version no longer runs, should I uninstall the old version prior to running sudo make install? should the menu shortcut now point to the new version? Clearly I have made a mistake

---

### Post by jejeman on 2011-07-30
You can try to run yoshimi localy from the build folder.
Well, usually make install sets shortcuts to run build version. You can uninstall yoshimi package, you can always install it back.

---

### Post by psy-man on 2011-07-30
to run it from the build folder would I open a terminal cd to the build folder and ./yoshimi ?
forgive my ignorance, clicking the executable doesn't seem to work.

as an aside, rakarrack doesn't start at all!  but I have just discovered guitarix :-)

---

### Post by jejeman on 2011-07-30
> to run it from the build folder would I open a terminal cd to the build folder and ./yoshimi ?Yes. Sometimes programs work, sometimes don't.

What is the error for rakarrack?

---

### Post by psy-man on 2011-07-30
Here is the output when I try to start rakarrack from a terminal
```
####@####:~$ rakarrack

rakarrack 0.6.1 - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|256|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
Using ALSA driver EMU10K1 running on card 1 - SB Live! Platinum [CT4760P] (rev.8, serial:0x80401102) at 0xb000, irq 11
configuring for 48000Hz, period = 256 frames (5.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
Illegal instruction
####@####:~$ JackTemporaryException : now quits...
jack main caught signal 2
JackServer::ClientKill ref = 2 cannot be closed
control device hw:1
Released audio card Audio1
audio_reservation_finish
control device hw:1
####@####:~$ 

```
Curiously Illegal instruction is all I get from yoshimi, if I try to start yoshimi as sudo I get nothing.
Jackd starts and runs ok using qjack control.
It also runs fine when started from the terminal

---

### Post by Pablo_F on 2011-07-30
Does yoshimi work now?

yoshimi --version ???

What is the output of 

cat /proc/asound/cards /proc/asound/version ~/.jackdrc

arecord -l && aplay -l

---

### Post by Pablo_F on 2011-07-30
BTW, never run these programs with sudo. Not yoshimi, qjackctl, rakarrack... john started the jack server -> john runs the jack-aware apps. Not root. Root doesn't like music.

---

### Post by psy-man on 2011-07-30
yoshimi-0.060.10

doesn't work at all

```
cat /proc/asound/cards /proc/asound/version ~/.jackdrc
 0 [Live           ]: EMU10K1 - SB Live! Platinum [CT4760P]
                      SB Live! Platinum [CT4760P] (rev.8, serial:0x80401102) at 0xb000, irq 11
 1 [rev50          ]: VIA686A - VIA 82C686A/B rev50
                      VIA 82C686A/B rev50 with ALC200,200P at 0xc400, irq 11
Advanced Linux Sound Architecture Driver Version 1.0.23.
/usr/bin/jackd -dalsa -dhw:1 -r48000 -p256 -n2

```
sound cards have swapped places since last reboot

```
:~$ arecord -l && aplay -l 
**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! Platinum [CT4760P]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

As you can see I have dug my old SB live out from a box in the attic, I last used it on Win98 with CoolEdit  pro. I'm having fun getting to grips with the alsa mixer.

---

### Post by sgx on 2011-07-30
Yoshimi needs a running a2jmidid.

a2jmidid -j default

Yoshimi and rakarrack both need
a libfltk, and can be very choosy about the version. You might need to use the 5.8 version of yoshimi for awhile.
I would purge all that you have, and use synaptic or dpkg to install it.
Cheers

edit 
In the alsa tab I connect soundcard midi on left to midi through on right
In the midi tab, connect a2j-midi-through on the left to yoshimi-in on the right
In the audio tab, on the left side, I connect yoshimi l/r to either rakarrack in 1/2, or playback 1/2 on the right side. If rakarrack is used, connect rakarrack out 1/2 on the left, to playback 1/2 on the right

your setup ins and outs may be different.

---

### Post by Pablo_F on 2011-07-31
> sound cards have swapped places since last reboot

This is the first problem you have to address. More below.

I strongly recommend you launch qjackctl and start the jack server before anything else.  For your convenience, you can add qjackctl to "applications on start up" and configure qjackctl so that it starts minimized on the tray. This way you will start the jack server with just a click. 

In any case, you configured jack so that it used the interface hw:1 (because the SBLive was hw:1) and the next reboot the cards swapped place. Now, you see that instead of the SBLive, jack is working on the onboard now :( 

So, the best thing you can do to avoid this card swapping weirdness is calling the card by name, not by number. In the interface field, write down **hw:Live** (even if it does not appear selectable in the drop down menu). 

This way, you use the device 0 of the SBLive, for capture and playback. If you want to have more playback channels you have to select hw:Live,0 for input and hw:Live,3 for output.

As for yoshimi, I don't know. It works here. Did you launch with the jack server already running? Have you tried running it in a terminal (just type *yoshimi*) and what is the error message?

Yes, a2jmidid is needed to connect alsa midi ports to jack midi ports. But I think the problem has nothing to do with MIDI connections, at least not now.

Cheers, Pablo

---

### Post by psy-man on 2011-08-01
Hi all, thanks for the replies. Yes, I installed A2J and that does work well but reinstalling the repository version of Yoshimi did not recover functionality after my attempts to install a home compiled version. I am afraid to say, and I'm sorry it does not help the bug fixing that I decided to wipe the partition and start again. I will install zynaddsub which worked fine for my needs and I am already familiar with it.  As for Rakarrack,not working I should start a new thread, although I have to say guitarix is great so I'm not missing rakarrack at the moment.
   In the mean time thanks.

---

### Post by sgx on 2011-08-02
Did you try the version at the Autostatic PPA? works fine in my setup.

[https://launchpad.net/~autostatic/+archive/ppa/+packages](https://launchpad.net/~autostatic/+archive/ppa/+packages)

I have noticed that apps don't always set up to run correctly,
when used in conjunction with certain other apps. Rakarrack
and yoshimi can be problematic. I have gotten used to keeping
auto-connect-to-jack off, whenever possible. Adjusting the
Timeout (Msec) control in qjackctl might help. Some apps may need
a kernel with 1000hz midi timer. A brief explanation and a link for
more is here, second post:

[http://ubuntuforums.org/archive/index.php/t-1651629.html](http://ubuntuforums.org/archive/index.php/t-1651629.html)

Cheers

---

### Post by psy-man on 2011-08-05
hi sgx, I have not tried adding autostatic's ppa to my repository list. It say's its for Lucid and Karmic, do you think it will work on my Natty install?

---

### Post by psy-man on 2011-08-05
Did I mention that I have added Zynaddsub and it works ok for what I need, it even loads the patches that ship with yoshimi, the only problem I have is recording Zynaddsub using the same box as then the CPU load gets higher and higher until the system grinds to a halt.
I have now tested out the latest release of AV linux on this rig. AVL has the later build of yoshimi that I failed to build myself.  yoshimi does not run at all producing a different error  but works fine on another machine I have, so maybe this is a hardware related issue.
The machine that I have in my studio is a retired gamer. AMD athlon @ 2Ghz with 1.7gb of ram. I have an install Ubuntu studio 8.04, on it already and have installed 11.04 to a separate partition where I used to have ubu stu 9.1.
After many hours trying to get  nvidia drivers to work on the various RT kernels. I have ditched the idea of having a dual head studio machine.

 I also have in my studio/man-cave one of those ion USB drum kits, it's actually a game controller not a midi device as one might think, and so to use it to drive midi equipment I must use a program that can take game controller input and make midi output. Believe it or not such a program [exists]("http://glovepie.org/glovepie.php") but is windows only, that said I also have a Yamaha SW1000XG sound card I'm rather fond of but it is not supported by Alsa, an Akai s2000 and a korg X5dr, for both of which I use windows based patch librarians. 

AV linux comes as a live DVD so I can test various combinations of old PC bits I have laying around and see how it performs.

---

### Post by bluesscream on 2011-08-05
did you try selecting midi-driver option 'sec' in qjackctl  and start 'yoshimi -a' in a terminal?

have a look at yoshimi --help

a2jmidid inhibits midi in wine|reaper|vst stuff here

---

### Post by sgx on 2011-08-05
> **psy-man said:**
> hi sgx, I have not tried adding autostatic's ppa to my repository list. It say's its for Lucid and Karmic, do you think it will work on my Natty install?
It's sure worth a shot. You don't need the whole ppa, just the yoshimi package   installed with

sudo dpkg -i name-of.deb.

Use synaptic to remove an existing yoshimi

Cheers

---

