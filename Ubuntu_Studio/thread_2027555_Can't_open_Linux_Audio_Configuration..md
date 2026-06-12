---
title: "Can't open Linux Audio Configuration."
date: 2012-07-16
forum: Ubuntu Studio
---

### Post by TheSeventhChaos on 2012-07-16
So I installed Ubuntu Studio yesterday, this is my first time ever using Linux. I'm completely new to it. Usually I'm a pretty fast learner and I figure things out nicely, but this one's got me. When I try to open **Linux Audio Configuration**, an error pops up saying:

 "JACK can only be configured with a loaded and stopped studio. Please create a new studio or load and stop an existing one."

The main reason I'm even worrying about getting into the Audio Config is that my Microphone isn't being detected or working on any of the sound recording software I've installed. When I try to look up help on Google, most of what I find isn't very clear or doesn't pertain to exactly what I need help with.

So if anybody could help with either of my issues, it would be greatly appreciated. Google isn't doing it for me. Hopefully I'm posting this in the right area.

---

### Post by sgx on 2012-07-16
jackd and its gui, qjackctl, are first things to deal with.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

The 4th and 8th links at the wiki will help
with screenshots and configuration tips. Details of your
setup will help.

Having a constant audio source at your mic,
will help you hear when it is connected in qjackctl.

Press Start  in qjackctl, to start jackd.
Press 'Connect' on the lower left of the qjackctl.
interface, in the tabbed panel that opens, in the
Audio tab, The mic should be labeled System, on the left,
and the soundchip will also labeled System, but on the right.
Select each one with the mouse, then press the 'Connect' button
on this panel, not the one on the main screen.

There is a widget by System to click and expand the view,
and name what is there under the hood, capture, playback,
and other gear and software you add will also have the widget.
 

some commands to use in a terminal, type one in, press enter,
read the output. Items in brackets will be the soundchip

cat /proc/asound/cards   and

arecord -l

aplay -l

aconnect -i

aconnect -o

these will show how linux IDs your sound chip and connections.

There are many youtube videos showing qjackctl with
ardour, hydrogen, zynaddsubfx, rakarrack, and in the
sidebar lists.
Cheers

---

### Post by TheSeventhChaos on 2012-07-17
Some of what you said did help, and to be honest I'm not sure how to find my setup on Linux. I know the headset I'm trying to use is **USB, it's a Turtle Beach X12 headset**. Maybe some of what came out of the terminal will show you what you need to know to sort things out a little bit, I'm not sure what to do with all of this information...: 

```
chaos@chaos-Inspiron-1545:~$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6afc000 irq 47
chaos@chaos-Inspiron-1545:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
chaos@chaos-Inspiron-1545:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chaos@chaos-Inspiron-1545:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
chaos@chaos-Inspiron-1545:~$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
chaos@chaos-Inspiron-1545:~$ 
```

Yet, my Sound Recorder and Audacity still aren't picking up my mic. I'm not sure what's wrong with Sound Recorder, it seems to be acting buggy right now, I really don't know. But Audacity just isn't recording anything when I hit record. I'm really lost in all this right now and I want nothing more than for it to be fixed :\

Sorry I'm so new to this, I really hate feeling like I'm a nuisance. **If there's anything you guys need me to show you from my terminal, just tell me what to type in and I'll copy/paste the results.**

**EDIT:**

I changed some settings in Audacity to make it capture and playback from the right sources. Got that working. As for the Sound Recorder, I'm really not sure what's wrong with it. I'll play around with it and come back if I get any results.

---

### Post by TheSeventhChaos on 2012-07-17
Well, so far, I've fixed all that I care to. However I still have trouble figuring out how to get Screen Recorder working. I need something that can record my screen and my system audio and maybe record my voice (if not I can use Audacity or Screen Recorder if it'll work), but other than that, I think I've done all I need to be done. Thank you for the help. If there's anything else you can recommend to me to set a new Linux user on the right path, it'll be greatly appreciated. Thanks again!

---

### Post by sgx on 2012-07-17
timemachine is a good recorder app, route your final audio
to it, and your souncard, for monitoring. The files can
be played with vlc, and imported/edited/exported with
audacity.

There are many active forums, so most google queries will
provide results. man pages are a common documentation in some
distros, for many commands

man lsmod

will document using the lsmod command, regarding the
listing of kernel modules. linux has a lot of 'shorthand'

ls for list, mod for modules in this case of lsmod.

[http://linux.die.net/man/1/jackd](http://linux.die.net/man/1/jackd)

this is an internet based man page, for jackd

From your command output, in the brackets, is seen HDA Intel
this is your motherboard sound chip

Click Setup on the main qjackctl gui. The entries in the qjackctl setup panel

Input device >
Output device >

(click the > widgets to see the dropdown list that contains
what your kernel has discovered, should include HDA Intel
or similar)
The other one in brackets, STAC92xx Analog, can go to google,
and many pages of topics will be there, to pick up tips,
and become aware of the (sometimes weird) jargon.

Glad things are working
:popcorn:

---

### Post by TheSeventhChaos on 2012-07-17
Thank you so much, I'm really glad there's helpful people on here like you! xP lol

---

