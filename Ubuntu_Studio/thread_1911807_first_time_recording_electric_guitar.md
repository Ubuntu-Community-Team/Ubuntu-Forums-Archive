---
title: "first time recording electric guitar"
date: 2012-01-19
forum: Ubuntu Studio
---

### Post by borderblue on 2012-01-19
What's up people!?

I messaged before, but I have a new acct. because it has been so long since I posted, hah. Anyway, my previous question was kind of a generic query about how one records an electric with Studio Ubuntu (LTS 10.04 64bit is my version). It took me awhile to afford an external recording device. Now I have one, yessss!

I still have no clue as to the exact details, so if somebody could give me specifics, man, I owe you. So, here's my setup:

The box reads Presonus Audiobox USB, the kind they sell at Guitar Center, lol.... The box doesn't give any other model name info, altho it does say it is 24-bit/48k. I have the Audiobox plugged in to puter with usb, and my electric guitar is in the second jack marked "instrument, next to the mic jack. Anyway, I really have no idea the step by step operations, but I have (I think) the software that I need installed. I would like to have reverb and maybe some other effects, hopefully without using my amp. Can I do that and hear the effects in realtime through my headphones plugged into (computer?? audiobox??) If somebody help me out, I'd appreciate it.

---

### Post by Sylos on 2012-01-20
Hello there.

The following is a few steps I use to do recording. There are other ways using other software but this is just what I do.

1. Start the jack sound server by clicking on qjackctl in your sound menu. Then click 'start'

2. Start Ardour from the sound menu.

3. Add a track/bus to ardour.

4. Set the input for the new track to the correct in (possibly in2 in your case as the mic may be in1). You can do this by opening the Mixer window.

5. Enable record on the channel. When you play you should now see the levels going up and down on the channel in ardour.

6. Hit record and play and you are away.


I probabbly missed something out but post up here again if you get stuck. 

As far as guitar effects are concerned you could use something like rackarack. I think to do that you would need to go to the qjackctl 'Connections' window and connect you guitar in to racarrack (once you have started it). Then connect the output of racarrack to the input of ardour.

EDIT: For live monitoring you may also want to connect the output of racarrack to 'System' if it isnt already.

Like I said - post up if you hit trouble.

Cheers

---

### Post by CivilizationII on 2012-02-17
LADSPA or LV2 effects are your friends here.

You need very few things, for example for LADSPA plugins:

1/ qjackctl and jackrack

2/ some LADSPA effect, i recommend Steve Harris (SWH) or CAPs ones for guitar

Jackrack will act as VSThost on windows, it will enable plugins to play and mix. Et voila, an amp and effects in less than 3 minutes ;-)

---

### Post by sgx on 2012-02-17
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and 8 at the wiki discuss setup and connections, with screenshots.

Start the computer with the presonus unplugged. Run the commands

aplay -l   and
arecord -l  and save the contents in a text file. Then insert the presonus, and run the commands again, and add the output to the text file.

The different items should be the presonus ports. Items in brackets
can be used in qjackctl setup page, 

Input Device >
Output Device >       click the  >  widgets to open a dropdown list
of your detected sound devices. They may be labelled hw:1  hw:0,0 etc
or by name, or both.

Plugging in usb devices can reorder the hw: ID aspect, so choosing what
is shown as a name, will help insure less fiddling with qjackctl
at startup.

cat /proc/asound/cards  output will have similar names, and mention the irq used by the soundcard, useful in the rare case it might be shared with video or something else.

cat /proc/asound/devices   will list some elements of the sound system.

amb, caps, fil, tap, swh, and vco are ladspa fx, mda, invada, and calf are LV2 plugins, so install all lv2 system items using synaptic. Guitarix2 and rakarrack areseparate ampsim/fx software to be enjoyed, and parts of guitarix also will be in ladspa listings.
Cheers

---

### Post by sgx on 2012-02-18
this weekend, a presidents day GC or zzounds sale should get you a
Fender Mustang 1 amp/usb input device for $85

[http://www.youtube.com/watch?v=Wl2Q8SNVnPU](http://www.youtube.com/watch?v=Wl2Q8SNVnPU)

24 editable presets are on the main dial, a 'typo' is in the video

the simplest and best
guitar bargain for linux users, class compliant plug/play
usb and line connections, and very versatile. A linux editor
for its ampsims and fx, called plug, is a free download.

[http://piorekf.org/plug/](http://piorekf.org/plug/)

Cheers

---

