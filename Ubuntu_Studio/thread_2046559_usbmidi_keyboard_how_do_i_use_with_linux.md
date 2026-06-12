---
title: "usb/midi keyboard how do i use with linux"
date: 2012-08-23
forum: Ubuntu Studio
---

### Post by rapattack1 on 2012-08-23
Hi i have a keyboard and i got an adapter that is midi to usb. What apps should i use with it and how? I don't want to use jack as i tried so many times with so many apps over the years and it did my head in. I would go through long periods of times not being able to get sound for the simplest things and i don't want to go through that horror again. I do audio and video production and i use Artistx which is a distro from Ubuntu. Thanks would appreciate advice as i have never hooked up anything to the computer other than mics...i have a usb mic and it works fantastic

---

### Post by jejeman on 2012-08-23
Plug everything and give as output from these commands
```
lsusb
```
```
amidi -l
```
Only applications that I know that don't need JACK are Traverso, LMMS, ZynAddSubFX, Audacity.

---

### Post by sgx on 2012-08-25
> **rapattack1 said:**
> Hi i have a keyboard

it did my head in. 

i don't want to go through that horror again.

The trick to using qjackctl gui for jackd, is to visualize the
connections as if they were in real gear instead of software and
computer soundcards.

Start qjackctl, press the main gui Connect button, lower right,
which opens the connections panel, with three tabs, Alsa, midi,
and audio. Each tab has two sides, one for in and one for out.
Instruments and devices will display their available components,
awaiting you to connect them, and some connections are automatic,
but that feature can be turned off in the prefs,
which can be helpful in some cases.

To connect items in qjackctl, highlight the in and out of desired items with a mouseclick, and press the connect button
(the one on the qjackctl connections screen, not the one on
the main qjackctl gui ) 

Alsa tab: your real midi keyboard displays its connector
in qjackctl on the right side, and connects to

zynaddsubfx in the Alsa tab on the left side.

In the Audio tab of qjackctl, are System Capture on the left,
and System Playback on the right. (click the widget by System,
to open up its full list of connectors, so you can see Capture,
and Playback displayed) So zynaddsubfx receives the alsa midi
data input, its connector is on the right, and connects to
System Capture on the left.

The connector for the sounds produced by zynaddsubfx are in the Audio
tab on the left side, and are connected to System Playback on the
right side, so you can hear them. My first time, I put a heavy object on the midi keys to provide ongoing sound, so I would hear when the
right connection was made. Look at the wiki for screenshots of the above, 8 links are available,

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl) 

link 8 is for qjackctl/zynaddsubfx, and link 4 covers setup of jackd.
Youtube? just search videos of hydrogen, zynaddsubfx, rakarrack,
ardour, ubuntu studio, many videos start with the basic connections. You'll get it this time around
:guitar:
Cheers

---

### Post by rapattack1 on 2012-09-11
> **jejeman said:**
> Plug everything and give as output from these commands
```
lsusb
```
```
amidi -l
```
Only applications that I know that don't need JACK are Traverso, LMMS, ZynAddSubFX, Audacity.

$ lsusb
Bus 002 Device 005: ID 1a86:752d Unknown 
Bus 002 Device 004: ID 17a0:0001  
Bus 002 Device 003: ID 0e8f:0021 GreenAsia Inc. 
Bus 002 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 046d:08c9 Logitech, Inc. QuickCam Ultra Vision
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carla@carla-desktop:~$ amidi -l
Dir Device    Name
IO  hw:2,0    Audigy MPU-401 (UART)
IO  hw:2,1    Audigy MPU-401 #2
IO  hw:2,2    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:2,3    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:3,0,0  USB2.0-MIDI MIDI 1
 O  hw:3,0,1  USB2.0-MIDI MIDI 2
carla@carla-desktop:~$ 


Sorry i didn't reply before today. I was in two accidents the day or two before and have been dealing with too much after the hospital stay

---

### Post by rapattack1 on 2012-09-11
> **sgx said:**
> The trick to using qjackctl gui for jackd, is to visualize the
connections as if they were in real gear instead of software and
computer soundcards.

Start qjackctl, press the main gui Connect button, lower right,
which opens the connections panel, with three tabs, Alsa, midi,
and audio. Each tab has two sides, one for in and one for out.
Instruments and devices will display their available components,
awaiting you to connect them, and some connections are automatic,
but that feature can be turned off in the prefs,
which can be helpful in some cases.

To connect items in qjackctl, highlight the in and out of desired items with a mouseclick, and press the connect button
(the one on the qjackctl connections screen, not the one on
the main qjackctl gui ) 

Alsa tab: your real midi keyboard displays its connector
in qjackctl on the right side, and connects to

zynaddsubfx in the Alsa tab on the left side.

In the Audio tab of qjackctl, are System Capture on the left,
and System Playback on the right. (click the widget by System,
to open up its full list of connectors, so you can see Capture,
and Playback displayed) So zynaddsubfx receives the alsa midi
data input, its connector is on the right, and connects to
System Capture on the left.

The connector for the sounds produced by zynaddsubfx are in the Audio
tab on the left side, and are connected to System Playback on the
right side, so you can hear them. My first time, I put a heavy object on the midi keys to provide ongoing sound, so I would hear when the
right connection was made. Look at the wiki for screenshots of the above, 8 links are available,

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl) 

link 8 is for qjackctl/zynaddsubfx, and link 4 covers setup of jackd.
Youtube? just search videos of hydrogen, zynaddsubfx, rakarrack,
ardour, ubuntu studio, many videos start with the basic connections. You'll get it this time around
:guitar:
Cheers

Thanks so much but all that sounds really familiar. I could not visualise something i don't know. I don't know a typical setup as i am not a musio in that sense. I have played many instruments as a child which was 30 odd years ago and we never had an amp or a desk. I know what those are now ofcourse but don't have enough working knowledge of them and it just doesn't compute for me. I even learnt some audio engineering at a good studio some years back. For some reason it still doesn't happen for me and i spent way too much valuable time on jack

---

### Post by CrocoDuck on 2012-09-11
Hi. I can't be sure that your keyboard is properly working through the adaptor.

```

IO  hw:3,0,0  USB2.0-MIDI MIDI 1
 O  hw:3,0,1  USB2.0-MIDI MIDI 2
```I *feel* those lines encouraging.
Even if I reccomend open sorce software, I want to link to you some commercial one for linux. They are not free, but have useful free demos: [http://www.pianoteq.com/](http://www.pianoteq.com/) (actually my favourite phisically modelled piano) [http://www.renoise.com/](http://www.renoise.com/) (just tried it). Those programs should work without jack (I'm sure that pianoteq works without jack). Have a try by downloading a free demo from pianteq site, unpacking it and runing it. Try to play around with audio settings until you can hear and play. If you can't, we'll know that keyboard is not working properly. Does your Audigy MPU-401 have a MIDI port?

---

### Post by rapattack1 on 2012-09-13
OK i downloaded that software and made a folder called piano but can't remember how to open/edit conf files.
I can't remember what a midi port looks like but i think there is an extension to my soundcard that has that. I would have to put it back into the box as i took it out some time ago. It looks like a longer serial port and i think is known as a game port? Anyway as i am injured its going to be some time before i can move the computer and locate the thing that attaches to the soundcard as it is buried in a box. Sorry had two accidents and one knee is in a splint.

---

### Post by CrocoDuck on 2012-09-13
Oh! I hope your injuries heal quickly! Game port should be good for MIDI connections (I  have one in my soundblaster 5.1, but I never used it). If the keyboard don't works through the adaptor we could make a try with that port (when you will be ok).

Pianoteq should run just after unpacking it, double click on the  executable file you find in the unpacked folder (if it not runs cause permission issues, right click on it, properties, permissions tab, check on execution parameter). For editing conf files you have to use a text editor. Some conf file can't be edited by a normal user. So you have to open it with sudo, for example:

```
sudo gedit
```

or

```
sudo gedit "path to file"
```

the last command directly opens the file with the editor.

---

### Post by rapattack1 on 2012-09-20
hi sorry i haven't been online...too much to deal with and uncomfortable. just got bluetooth mouse set up and long usb keyboard cable but not in the mood after all the shuffling to now get the music keyboard attached. i dont have a cable to go to a game port. i think i have seen them in the past but anyway i dont have one. i will try to get back on soon but there is too much shuffling around in a small apartment like mine :0)

---

### Post by sgx on 2012-09-20
Sorry to hear of multiple accidents! What midi keyboard are you using?

With a desktop computer, a used m-audio 24/96 pci card is about
$30-$60 dollars, and has 5pin midi 1/0 ports, and works great in
linux, and especially qjackctl/jackd. Local gamers may sell one,
after upgrading. Some usb models also have 5 pin midi ports.
Very useful when bargain hardware rack synthesizers pop up.
Cheers 
Hope you get well soon :guitar:

---

### Post by rapattack1 on 2012-09-28
Sorry it has taken me so long to reply. Caught up with too much right now. Ok the keyboard is a Medeli mc37 [http://www.medeli.com.hk/products/ek/mc-37.htm](http://www.medeli.com.hk/products/ek/mc-37.htm)
Yeah not prepared to really spend more money especially now that the injuries are here and well its expensive being me right now :0) Good to know though as hopefully soon i can get out there and earn a little. I am on a disability pension but sometimes make cash selling second hand technology on ebay :0) As it is i came across the music keyboard for free and most of my tech stuff also...i have a great network of people that reuse...maybe i will attract that card too :0) thanks ooppsss got some lightening/thunder so will have to get off the puter

---

### Post by sgx on 2012-09-29
Hi, if you are good at trading 'up', there are quite a few
gear horders, some from Australia, at the big sound forums.
Becoming a regular at a few of them, might help them find
a jewel, for which a premium would gladly be paid or traded.
I think most have market subforums, as well as allowing
casual mentions in releated topics.
Cheers

---

### Post by rapattack1 on 2012-10-04
Don't know much about trading and no real time. I gotta master one thing before i move to something else. Haven't even played a piano in too many years. Anyway not much time as dealing with injuries from two accidents and too much nerd stuff to do :0)

---

