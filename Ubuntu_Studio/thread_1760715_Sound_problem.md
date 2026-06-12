---
title: "Sound problem"
date: 2011-05-17
forum: Ubuntu Studio
---

### Post by iet.aruna on 2011-05-17
This is a rather annoying problem. For some reason, when I plug my headphones into the jack on my laptop,  the audio STILL comes out of my main speakers as well as the headphones.  I tried out another pair of headphones just to make sure it wasn't them  that was the problem, but the problem still persisted. I just want to  listen to music through my headphones...:| I tried going through all of the sound settings and reading through the  Ubuntu help files, but couldn't find anything on the subject. My audio  card is an Intel High-Definition Audio Input/Output card. I tried l

---

### Post by dargaud on 2011-05-17
Right-click on the KMix icon (lower right, normally), [Select master channel]. There select [Playback device] and the various options available: internal, headphones, USB, etc...

In Linux you can have the sound coming through one or more sound devices at the same time, which is great if you want to do complicated DJ stuff, but not so great for everyday simple use.

---

### Post by jejeman on 2011-05-17
This is common problem on laptops. You need to see which card you have, and than to set options in alsa for that card, and then maybe you will get what you want.
First you can try options in sound preferences, to set various profiles, but I doubt the sucess.
To determin the card issue this command:
```
cat /proc/asound/card*/codec#0 | grep -i codec
```
than see if its supported in alsa documentation
```
zcat /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```
If you lucky youre find youre model for both card and laptop, if only card is listed than try any reasonable options for it. Copy options to teh bottom of this file: /etc/modprobe.d/alsa-base.conf
the line for option should look something like this
```
options snd-hda-intel model=basic
```
also look in to ubuntu documentation [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

