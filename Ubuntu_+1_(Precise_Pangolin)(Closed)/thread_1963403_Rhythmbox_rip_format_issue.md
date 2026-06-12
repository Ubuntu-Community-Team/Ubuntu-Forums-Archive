---
title: "Rhythmbox rip format issue"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-04-22
In Rhythmbox preferences under Music, you can set a preferred format for ripping: ogg, flack, mp3, or mpeg4. However, the "settings" button is greyed out, so you can't tweak the parameters. 

To see what the defaults might be, I ripped a CD to mp3. The bitrate was shown in the song's properties/Details as 32 kbps! That is a bit ridiculous. In Nautilus, the song's properties/Audio showed 72, still low. How can I adjust this? It used to be possible.

---

### Post by mc4man on 2012-04-22
This is being semi addressed.
Rb will need a preset to get off of the gnome default, have tried here & works well
(though attempts to create & have available more that one preset have proved troublesome - I can create more than 1 profile/preset for mp3 but only 1 is choose-able at a time

The preset under consideration will use VBR 2, I think the current bitrate= line should be lowered

If you want to put this in place then see this bug report - 
replace the current .gep in /usr/share/rhythmbox with the last one attached in report

In ~/.gstreamer-0.10/presets place the .gsr 
(- this is the file where you can adjust the parameters, if presets folder doesn't exist then create

I've tried to create the same for ogg/vorbis but can't seem to craft the .psr correctly
(when something is wrong RB will say you need to install codecs which is not the real reason

Edit: gstreamer mp3 parameters can be seen by installing gstreamer-tools & running
```
gst-inspect lamemp3enc
```

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987)

---

