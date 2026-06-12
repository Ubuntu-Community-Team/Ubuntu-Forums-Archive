---
title: "No audio output from JACK"
date: 2011-07-20
forum: Ubuntu Studio
---

### Post by Jordii on 2011-07-20
I can't manage to get sound from JACK. It didn't work using the default settings, and neither did it with my USB audio interface selected as "interface", "input device" and "output device". I unticked the Realtime option. 
I was able to start JACK, untill I chose my interface (TASCAM US-122L) as output device.
The error message I'm getting when I try to start JACK is the following:
> Copyright 2001-2005 Paul Davis and others.
10:04:27.478 Patchbay deactivated.
10:04:27.478 Statistics reset.
10:04:27.485 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:04:27.494 ALSA connection graph change.
10:04:28.730 JACK is starting...
10:04:28.731 /usr/bin/jackd -r -dalsa -r44100 -p1024 -n2 -D -Chw:1 -Phw:1
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:04:28.753 JACK was started with PID=3090.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
Cannot lock down memory area (Cannot allocate memory)
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
Using ALSA driver USB US-122L running on card 1 - TASCAM US-122L (644:800e if 0 at 002/004)
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
10:04:28.833 JACK was stopped with exit status=255.
10:04:30.898 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
I'd really like to record using Ubuntu, but I'm affraid I've to switch back to Windows, unless I can get it working thanks to your help.

---

### Post by jeebustrain on 2011-07-20
is your user acct in the Audio group?

---

### Post by Pablo_F on 2011-07-20
Did you search the forums and/or the internet about that particular audio card and alsa/jack? It works for some people at least but they had to hack an alsa conf file.

PS: This alone won't solve the issue but anyway: Run jack in realtime mode (you need to gain rtprio and memlock privileges so you (i.e., the user who executes jack) have to be a member of the audio group at least, as jeebustrain points out)

---

### Post by Jordii on 2011-07-21
@ jeebustrain
I'm not sure how to check that.

@ Pablo_F
I did search for it and tried a few solutions, but they turned out to be aimed at a slightly different problem, and therefore didn't work. To get JACK working in real time mode in combination with my soundcard requires an additional tweak I believe. I'll try that immediately.

---

### Post by Jordii on 2011-07-21
I have just enabled the use audio devices option, and made my USB interface compatible with real time. By the way, this particular problem not only occurs with my Tascam US-122L, it also occurs with my internal laptop speakers. I just can't seem to get sound from JACK.

---

### Post by Jordii on 2011-07-21
The current error message:
> [COLOR=#999999]11:39:36.688 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:39:36.689 Statistics reset.[/COLOR]
 [COLOR=#cccc99]11:39:36.702 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]11:39:36.709 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]11:40:04.899 JACK is starting...[/COLOR]
 [COLOR=#990099]11:40:04.900 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1 -Phw:1[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]11:40:04.926 JACK was started with PID=3958.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:1
 control device hw:1
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:1
 Using ALSA driver USB US-122L running on card 1 - TASCAM US-122L (644:800e if 0 at 002/003)
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]11:40:05.059 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]11:40:07.027 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
Obviously, "Cannot initialize driver" seems to point out the problem, or am I wrong?

---

### Post by Jordii on 2011-07-21
Seems that an essential part of this [guide]("http://wiki.briata.org/doku.php") is malfunctioning: the screenshot included, showing all JACK settings needed to get it work. I have followed the rest of the guide that was necessary for me to do (step 3 and 4).

---

### Post by Jordii on 2011-07-21
> [COLOR=#999999]18:36:54.891 JACK is starting...[/COLOR]
 [COLOR=#990099]18:36:54.892 /usr/bin/jackd -p128 -dalsa -dhw:1 -r44100 -p256 -n2[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]18:36:54.910 JACK was started with PID=3676.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:1
 control device hw:1
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... hw:1|hw:1|256|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:1
 Using ALSA driver USB US-122L running on card 1 - TASCAM US-122L (644:800e if 0 at 002/005)
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]18:36:55.002 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]18:36:57.084 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
That's what it looks like right now.

---

### Post by Pablo_F on 2011-07-22
Hi, 

I don't have one of these, just trying to help, based on the link you gave and this thread in linuxmusicians [1].

So let us take a look at your system. What is the terminal output of these commands?
```

lsusb

cat /proc/asound/cards /proc/asound/modules /proc/asound/version ~/.asoundrc

arecord -l && aplay -l

jackd -dalsa -dusb_stream:1
 
```

Cheers, Pablo

[1]: [http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073&start=0&st=0&sk=t&sd=a&hilit=US122L](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073&start=0&st=0&sk=t&sd=a&hilit=US122L)

EDIT: Please, could you edit the thread title so it is more specific to the problem? (at least mention the card model)

---

### Post by Jordii on 2011-07-22
This is the output:
> jordi@ubuntu:/$ lsusb
Bus 002 Device 003: ID 0644:800e TEAC Corp. TASCAM US-122L
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jordi@ubuntu:/$ 
jordi@ubuntu:/$ cat /proc/asound/cards /proc/asound/modules /proc/asound/version ~/.asoundrc
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb4400000 irq 43
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 002/003)
 0 snd_hda_intel
 1 snd_usb_us122l
Advanced Linux Sound Architecture Driver Version 1.0.23.
# The usb_stream plugin configuration
pcm.!usb_stream {
  @args [ CARD ]
  @args.CARD {
    type string
    default "2"
  }
  type usb_stream
  card $CARD
} 
jordi@ubuntu:/$ 
jordi@ubuntu:/$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jordi@ubuntu:/$ 
jordi@ubuntu:/$ jackd -dalsa -dusb_stream:1
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
audio_reservation_init
Acquire audio card Audio-1
creating alsa driver ... usb_stream:1|usb_stream:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
Using ALSA driver  running on card 0 - 
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback

---

### Post by marseille on 2011-07-23
I think we are going thru something similar Jordi. I've been wrestling with qjacktl all day. 

Finally, I came up on a command that seems to work. Dunno if it's relevant for you -- and maybe you already know it -- but this is what I did to output sound to the speakers (not the mixer/audio interface):

First I took a look at what the card was... which is ``1''.

```
**$ cat /proc/asound/cards**


 0 [M1x1 ]: USB-Audio - MidiSport 1x1
                      M-Audio MidiSport 1x1 at usb-0000:00:12.1-1, full speed
 1 [SB ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
```


Then I fired up jackd to access the card with hw:cardNumber

```
**$ jackd -d alsa -d hw:1**


jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 1 - HDA ATI SB at 0xfe024000 irq 16
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
```


I didn't like the 48000 sample rate either and am going to try this command a little later:

```
**$ jackd -d alsa -d hw:1 -r 44100 -p 2048**
```

If you find out a better way or somebody could elaborate, I'd love to hear.

---

### Post by Pablo_F on 2011-07-23
Hi, 


Jordii's .asoundrc is broken. According to the info linked in this thread you have to change your ~/.asoundrc file to read like this:

```
pcm.!usb_stream {
        @args [ CARD ]
        @args.CARD {
                type string
                default "1"
        }

        type usb_stream

        card $CARD
}

ctl.!usb_stream {
        @args [ CARD ]
        @args.CARD {
                type string
                default "1"
        }

        type hw

        card $CARD
}

```

After rebooting, you have to tell jackd to use the interface "usb_stream:1" instead of "hw:1". 

Cheers, Pablo

---

### Post by Pablo_F on 2011-07-23
marseille, 

You are telling jackd to use your card number but the ordering in /proc/asound/cards could change between reboots so it is better if you use the card name (in square brackets). This will do the trick:

jackd -dalsa -dhw:SB

Needless to say, you can change the default sample rate (48000), frames per period (1024), etc. You can also use qjackctl, setup window, to define the complete jackd command.

Jordii's case is special because his audio card needs a hack in ~/.asoundrc. Yours and most audio cards don't need it. That's why I suggested he should change the thread title to refer to his particular card.

Cheers, Pablo

---

### Post by marseille on 2011-07-23
Pablo, thanks for that nice command -- I will make sure I do that. As for qjacktl, fighting with it, is the main reason I went to the command line. I'm not doing something right and can only seem to start jackd from the command line.

---

### Post by Pablo_F on 2011-07-23
Hi, 

In case it helps, you can see the complete jackd command that results from qjackctl setup in the message window. Just below "jack is starting..."  Also, it is normally copied to ~/.jackdrc

See also "man jackd". 

Show a screenshot if you wish.

---

### Post by Jordii on 2011-08-01
After changing my .asoundrc file, rebooting and changing my interface in QjackCtl, it still doesn't work. (I had to enter usb_stream:1 manually in the setup section, because I couldn't select it in the list.)

> [COLOR=#999999]12:20:48.017 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:20:48.018 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:20:48.027 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]12:20:48.039 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]12:20:52.426 JACK is starting...[/COLOR]
 [COLOR=#990099]12:20:52.427 /usr/bin/jackd -p512 -dalsa -dusb_stream:1 -r44100 -p512 -n3[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]12:20:52.454 JACK was started with PID=2020.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... usb_stream:1|usb_stream:1|512|3|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver USB US-122L running on card 1 - TASCAM US-122L (644:800e if 0 at 002/003)
 configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: got smaller periods 2 than 3 for capture
 ALSA: cannot configure capture channel
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]12:20:52.533 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]12:20:54.477 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
Btw, I was on vacation for a week, that's why I didn't reply.

---

### Post by Jordii on 2011-08-04
Bump.

---

### Post by Jordii on 2011-08-10
Bump ..

---

### Post by sgx on 2011-08-10
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl), start with the bottom link, and then the articles.

The ps ux  command will show whats running, in case somethings get's
using jackd before you do

killall name-of-process  if anything named pulse is running.
Choosing a named item, instead of it's hw:0,0 or hw:1 etc is not foolproof.
Not every soundcard is supported fully. On my card, the named entry
fails in certain situations. The entries in

Input device >
Output device >  (click the >  for the dropdown list are what your
kernel has discovered. Lookup in google

lsmod name-of-soundcard  others with similar gear and solutions
should be there.


You'll have to make various connections, one, two, or three of the
qjackctl connections panelsand sometimes choose an apps audio system preference, not all of them work alike. Once one of them is functional, the others will also work, but maybe have different connections.

A few minutes reading the jackd manpage, will explain the cryptic
entries in .jackdrc  and you can keep special versions as a text file
to run as a command, for setups you use only occasionally.

Cheers

---

### Post by Jordii on 2011-08-11
I managed to start Jack after I'd killed /usr/bin/pulseaudio, but I still can't hear any music being played through my Tascam US-122L. (I selected the device in the dropdown list now.)
Jack also seems to freeze firefox while I'm watching videos at youtube (to test my sound).

By the way, it might be useful mentioning that the soundcard does run, as soon as I plug it into my Ubuntu laptop and therefore I'm able to hear the music that's being recorded. (Through the monitoring option of the soundcard, which doesn't reguire any actions of my laptop other than powering it.)

---

### Post by jejeman on 2011-08-11
> Jack also seems to freeze firefox while I'm watching videos at youtube (to test my sound).Yes. That is normal. 
Use audacious to test sound.

---

### Post by Jordii on 2011-08-11
Got it working now, thanks a billion! :mrgreen:

---

### Post by sgx on 2011-08-11
> **Jordii said:**
> I managed to start Jack after I'd killed /usr/bin/pulseaudio, but I still can't hear any music being played through my Tascam US-122L. (I selected the device in the dropdown list now.)
Jack also seems to freeze firefox while I'm watching videos at youtube (to test my sound).

By the way, it might be useful mentioning that the soundcard does run, as soon as I plug it into my Ubuntu laptop and therefore I'm able to hear the music that's being recorded. (Through the monitoring option of the soundcard, which doesn't reguire any actions of my laptop other than powering it.)
Glad things are working! You might look at the qjackctl > widgets,
and the lsmod command output, before and after inserting the soundcard, and note any differences.
Cheers

---

### Post by mikeh789 on 2011-08-12
using the tascam us-122l, i am only able to get it working using a line i found at [http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073) , that line is 

jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2

though i usually do -p128 or more... i am on ubuntu 10.04, and i find the tascam performs best with a -generic kernel

---

### Post by sgx on 2011-08-13
Hi, you might want to use -n3 for a usb device, it should work better.

If you are using jack2, the -R50 would mean you are using
non realtime, at a priority of 50. This could be raised to
69 or 70, if I recall correctly.

If you are using an older jackd, -R invokes realtime, and you would
probably not specify a priority (the -R does opposite things, depending which version you use, how intuitive! ;) )

Cheers

---

### Post by astur on 2011-08-18
Hi!

This is the way I make it work in AV Linux 5.0:

1.- Put the asoundrc file in your home directory from Briata's page:

$ wget -c [http://pub.briata.org/us-122l/.asoundrc](http://pub.briata.org/us-122l/.asoundrc) ~/.asoundrc

2.- Install alsa-tools, alsa-firmware-loaders and libasound2-plugins from Sypnaptic Package Manager

3.- Plug in US122L and check if it has been detected

$ cat /proc/asound/modules

0 snd_hda_intel
1 snd_hda_intel 
2 snd_usb_us122l

Sometimes it is necessary to plug in several times the US122L in order to get it detected by the system. I don't know the reason.


4.- Open QjackCtl. Configure setup like this:

Frecuency: 48000Hz
Interface: usb_stream:2  -Write this manually because it is not listed-

If in your system the snd_usb_us122l has another number just replace the '2' with it.

5.- Start JACK

6.- Start ARDOUR, arm an audio track and just record!


Note:

I have just tested this in Ubuntu 11.04 and it also works but you have to disable the Real Time in the setup of QjackCtl.

---

