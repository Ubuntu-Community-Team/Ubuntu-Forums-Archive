---
title: "rosegarden woes"
date: 2008-07-12
forum: Ubuntu Studio
---

### Post by ruhtranayr on 2008-07-12
i'm using ubuntu studio 8.04 64-bit

i upgraded not too long ago from 7.10

pretty sure this used to happen before too

i have rosegarden working but sometimes (a lot) it just drops. it doest crash, it just plays one note and hangs. i have to restart jack, hydrogen and zyn every time. :(  very annoying.

ive noticed its not dependent on what synth i have loaded, even does it when i load a midi file in. 

now that i think of it, i usually killall timidity before i go to work in rosegarden because it seemed to make jack a lot less prone on crashing and it makes things easier for me when routing midi in rosegarden.  so maybe it's timidity causing this? problem is i'm messing around with midi files so i need timidity running...

anyone having similar problems?

---

### Post by ruhtranayr on 2008-07-12
I don't know if this will be helpful but here's a screen shot of my settings

[IMG]http://i82.photobucket.com/albums/j246/ruhtranayr/settings.jpg[/IMG]

and the output of transport messages when this happens. 

```
07:56:01.053 Transport stop.
load = 2.4016 max usecs: 579.000, spare = 22640.000
load = 2.2667 max usecs: 495.000, spare = 22724.000
load = 2.1304 max usecs: 463.000, spare = 22756.000
new transport position: 525260, id=0x26
new transport position: 437716, id=0x27
transport command: START
transport Starting, sync poll of 1 clients for 2.000000 secs
new transport position: 437716, id=0x28
transport Rolling, 2.000000 sec left for poll
transport Starting, sync poll of 1 clients for 2.000000 secs
transport Rolling, 2.000000 sec left for poll
load = 1.9653 max usecs: 418.000, spare = 22801.000
07:56:05.273 Transport start.
load = 2.0787 max usecs: 509.000, spare = 22710.000
load = 2.3271 max usecs: 598.000, spare = 22621.000
load = 2.3953 max usecs: 572.000, spare = 22647.000
transport command: STOP
transport Stopped
load = 2.5801 max usecs: 642.000, spare = 22577.000
load = 2.4098 max usecs: 520.000, spare = 22699.000
07:56:09.489 Transport stop.
load = 2.1352 max usecs: 432.000, spare = 22787.000
load = 1.9806 max usecs: 424.000, spare = 22795.000
new transport position: 525260, id=0x29
new transport position: 437716, id=0x2a
transport command: START
transport Starting, sync poll of 1 clients for 2.000000 secs
new transport position: 437716, id=0x2b
transport Rolling, 2.000000 sec left for poll
transport Starting, sync poll of 1 clients for 2.000000 secs
transport Rolling, 2.000000 sec left for poll
load = 2.0972 max usecs: 514.000, spare = 22705.000
load = 2.2566 max usecs: 561.000, spare = 22658.000
07:56:13.721 Transport start.
transport command: STOP
transport Stopped
new transport position: 87542, id=0x2c
load = 2.1469 max usecs: 473.000, spare = 22746.000
transport command: START
transport Starting, sync poll of 1 clients for 2.000000 secs
new transport position: 87542, id=0x2d
transport Rolling, 2.000000 sec left for poll
transport Starting, sync poll of 1 clients for 2.000000 secs
transport Rolling, 2.000000 sec left for poll
load = 8.7051 max usecs: 3544.000, spare = 19675.000
load = 5.5994 max usecs: 579.000, spare = 22640.000
transport command: STOP
transport Stopped
load = 4.0013 max usecs: 558.000, spare = 22661.000
new transport position: 87542, id=0x2e
07:56:17.952 Transport stop.
load = 3.0106 max usecs: 469.000, spare = 22750.000
load = 2.3667 max usecs: 400.000, spare = 22819.000
transport command: START
transport Starting, sync poll of 1 clients for 2.000000 secs
new transport position: 87542, id=0x2f
transport Rolling, 2.000000 sec left for poll
transport Starting, sync poll of 1 clients for 2.000000 secs
transport Rolling, 2.000000 sec left for poll
07:56:20.162 Transport start.
load = 2.3634 max usecs: 548.000, spare = 22671.000
load = 2.1120 max usecs: 432.000, spare = 22787.000
transport command: STOP
transport Stopped
07:56:22.372 Transport stop.
load = 2.0358 max usecs: 455.000, spare = 22764.000
load = 2.1269 max usecs: 515.000, spare = 22704.000
load = 2.0346 max usecs: 451.000, spare = 22768.000
load = 1.9368 max usecs: 427.000, spare = 22792.000
load = 1.8427 max usecs: 406.000, spare = 22813.000
load = 1.7698 max usecs: 394.000, spare = 22825.000
load = 1.9207 max usecs: 481.000, spare = 22738.000
load = 1.9165 max usecs: 444.000, spare = 22775.000
load = 1.9230 max usecs: 448.000, spare = 22771.000
load = 1.9219 max usecs: 446.000, spare = 22773.000
```

That is only the tail end of the messages. Nothing too interesting... And this is after a fresh reboot; the only app launched is Pidgin. I should note that Rosegarden is version 1.6.1

---

### Post by ruhtranayr on 2008-07-15
I think I just confirmed it's timidity causing the drop.

Was just messing with hydrogen and zynaddsubfx through rosegarden and the problem occured; it would only play the first note. I opened terminal, issued killall timidity, went back to rg, pressed play and everything worked fine. ::Shrug::

'timidity -v' outputs TiMidity++ version 2.13.2

I'm going to do some researching on timidity now...

---

### Post by ruhtranayr on 2008-07-15
Double post...

---

