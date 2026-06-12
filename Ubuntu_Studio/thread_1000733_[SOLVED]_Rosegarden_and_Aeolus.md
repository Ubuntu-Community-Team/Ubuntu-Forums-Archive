---
title: "[SOLVED] Rosegarden and Aeolus"
date: 2008-12-03
forum: Ubuntu Studio
---

### Post by djbushido on 2008-12-03
I'm really not getting how to do rosegarden and aeolus. I have jack set up, and each application initialized, but i have no idea how to interface between them. If someone could direct me to a tutorial or give a quick explanation, i would greatly appreciate it. I like the idea of jack over something like FL Studio, but it is a lot more work, and much more complicated. Any help would be appreciated.

---

### Post by thorgal on 2008-12-03
HI, I'll try to help :)

Just a comment : jack is not more complicated, it just implies different habits and more flexibility, that's the learning curve like everything else.

First, I have a question : do you plan to record audio inside rosegarden ? Here, I cannot help you. I only use RG for MIDI sequencing and ardour for audio recording. I will just assume that you will not handle audio in RG, only MIDI. I will also assume you know how to use aeolus (it's quite easy by hand). I don't know about triggering different sound banks from external controllers so I will not be of help here either (linux organists may tell you more).

OK. Fire up rosegarden and aeolus.
Rosegarden comes up with a template full of tracks. Let's start simple : highlight track number 2 and type Ctrl-D until there's only one track left: one MIDI track is what we have left.

The MIDI track needs to be connected to aeolus. SO make sure aeolus is up and running. Now, in the main RG window, clcik on the main menu label called Studio and select Manage MIDI devices.

You will see a bunch of stuff. The upper window frame is for playing devices, the guys that can receive MIDI events and be triggered to do something by them. If you do not see aeolus in the connection tab of this window, then we need to associate it to one of the 'MIDI software device'. Pick one of your choice as RG can show many for some reasons unknown to me, and select aeolus in the tab selection menu in the connection tab, next to the MIDI software device you picked. You can rename it to Aeolus if you want (double click on the device name and rename it).

Once you're done there, go back to the main RG window. RIght click on the track label. There will show up a drop down list of MIDI instruments to choose from. Pick Aeolus. Now your track is connected to Aeolus.

Create a track segment in the track editing window, the toolbar icons are sort of self-explanatory. To draw a segment, you must select the pencil tool. To draw the segment, use the middle mouse button (or scroll wheel). Now, change tool into the selection tool (singlel arrow next to pencil icon). Select the created segement by left clicking on it (it should change color from yellowish to greyish). Now, click on an icon called 'Open in Matrix Editor'. There are tootips popping up if you mouse-over these icons so that helps.

This will open a piano roll editor for the segment. Now, I guess you can continue, draw notes, etc. The View menu of that window has an entry that allows you to show the note velocity window at the bottom of the main piano roll window. This velocity view is hidden by default.

OK, you got some notes drawn, etc ? just play the segment.

Do you hear something coming from aeolus ? if not, but things look like they play OK, check your audio connections in qjackctl.

This setup I just described is one way. There are other ways but this will do the trick. Go to the RG website and read the userguide or tuts, they really help! :)

Good luck.

By the way, I did not talk about connecting your keyboard to RG and record MIDI events into a track. That's something you will get from the tuts on RG's website.

---

### Post by djbushido on 2008-12-03
Thank you, this looks uncomplicated enough to work. Also, thanks for the rosegarden link, i didn't find that on any of my google/yahoo searches. I am just using rosegarden as a midi controller, but will probably use ardour to record. Thank you for your help, and I'll post my results later.

---

### Post by thorgal on 2008-12-03
you're welcome, been through this as well ... ;)

anyway, check this out :

[http://www.rosegardenmusic.com/resources/](http://www.rosegardenmusic.com/resources/)


And just to tease you, I actually put a lame video on youtube where you can see one of my monitor screens and things happening in there. I use a VSTi for my drumming with RG as the MIDI controller. I say nothing in the vid but well, I just wanted to show that VSTi's are usable in linux :) Beware, it IS lame ...

[http://www.youtube.com/watch?v=Ys1s3Dk5sGo](http://www.youtube.com/watch?v=Ys1s3Dk5sGo)

---

### Post by djbushido on 2008-12-03
Okay, I'm quickly finding out I don't know how to use aeolus. I don't know if that is the problem, but would like to find out before i start blaming something else. I tried looking at tutorials on aeolus before, but they were for midi keyboards. I don't have one of those. If you could explain what you were talking about, i would appreciate it.

EDIT: Connections in JACK-aeolus as readable connected to rosegarden, rosegarden as readable connected to system, and system as readable connected to rosegarden. Don't know if this helps.
Also, got zynaddsubfx working using practically this same thing...

---

### Post by djbushido on 2008-12-04
Alright then. Don't know what i did differently, maybe connect aeolus to system out or change midi mappings, or remember to "pull stops," but  it is now working, and I plan on using ardour to record. Thanks for your help!

---

