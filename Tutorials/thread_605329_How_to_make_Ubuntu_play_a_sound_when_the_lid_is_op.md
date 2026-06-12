---
title: "How to make Ubuntu play a sound when the lid is opened or closed"
date: 2007-11-06
forum: Tutorials
---

### Post by weblordpepe on 2007-11-06
Hi there.
Ever wanted Ubuntu to play a sound when the lid is opened? ... It's quite easy.

You need the **aplay** program installed, which is by default in Gutsy.

Find a **wav** file of your choice (mine is a bodily noise) and place it anywhere on your system.
[INDENT]
As root, edit the file **/etc/acpi/lid.sh**:
Right near the top there is the code> #!/bin/bash Put the following code directly beneath it:
**aplay /home/username/common_noise.wav**
Where **username** is your username, and **common_noise.wav** is the wav file.[/INDENT]

And thats it, when you open or close the lid, Ubuntu automatically runs the **lid.sh** script, which you have edited to make **aplay** play your sound clip.

---

### Post by staticvoid on 2007-12-04
another guy did this howto as well. Yours is way simpler :D I've used yours. nice job!

---

### Post by weblordpepe on 2007-12-05
:guitar: Awesomeeee

A funny story if I may:
My laptop plays a rather long 3 second fart sound when the lid is opened or closed. Normally it's not an issue but the other day I was doing stuff outside & the laptop was at maximum volume.

Anyway I was on my lunch break, so I went back into work. All of a sudden I realised something. My laptop was closed, set to maximum volume, and no way to mute it. It was going to make a noise soon but of course if I opened the lid it was going to fart.

So I sneaked into the coffee room where people eat their lunch. I thought nobody was around. I opened the lid and of course the thing was LOUD. I was panicing and trying to log in to mute it. Anyway a whole bunch of people were gathering around while I was frantically trying to log in to mute my farting laptop.

Eventually I logged in and muted it. I then had to explain to about 20 people including bosses and managers etc that I programmed my laptop to fart. Life can be so difficult sometimes.

---

### Post by rzrgenesys187 on 2007-12-05
> **weblordpepe said:**
> :guitar: Awesomeeee

A funny story if I may:
My laptop plays a rather long 3 second fart sound when the lid is opened or closed. Normally it's not an issue but the other day I was doing stuff outside & the laptop was at maximum volume.

Anyway I was on my lunch break, so I went back into work. All of a sudden I realised something. My laptop was closed, set to maximum volume, and no way to mute it. It was going to make a noise soon but of course if I opened the lid it was going to fart.

So I sneaked into the coffee room where people eat their lunch. I thought nobody was around. I opened the lid and of course the thing was LOUD. I was panicing and trying to log in to mute it. Anyway a whole bunch of people were gathering around while I was frantically trying to log in to mute my farting laptop.

Eventually I logged in and muted it. I then had to explain to about 20 people including bosses and managers etc that I programmed my laptop to fart. Life can be so difficult sometimes.

:lolflag:

---

### Post by bimmerd00d on 2007-12-05
> **weblordpepe said:**
> :guitar: Awesomeeee

A funny story if I may:
My laptop plays a rather long 3 second fart sound when the lid is opened or closed. Normally it's not an issue but the other day I was doing stuff outside & the laptop was at maximum volume.

Anyway I was on my lunch break, so I went back into work. All of a sudden I realised something. My laptop was closed, set to maximum volume, and no way to mute it. It was going to make a noise soon but of course if I opened the lid it was going to fart.

So I sneaked into the coffee room where people eat their lunch. I thought nobody was around. I opened the lid and of course the thing was LOUD. I was panicing and trying to log in to mute it. Anyway a whole bunch of people were gathering around while I was frantically trying to log in to mute my farting laptop.

Eventually I logged in and muted it. I then had to explain to about 20 people including bosses and managers etc that I programmed my laptop to fart. Life can be so difficult sometimes.

I must have this for a gag.  Buddy is giving me his laptop to throw 7.10 on, this would be GOLD.  :lolflag:

---

### Post by weblordpepe on 2007-12-06
HEHE
I wonder if you could make a bash script to do it randomly. Or even do it within certain times of the day. Suddenly scripting seems way more fun :P

---

### Post by KIAaze on 2009-09-18
> **staticvoid said:**
> another guy did this howto as well. Yours is way simpler :D I've used yours. nice job!

Yes, that was me! :lolflag:
Here's my "complicated" one: [http://ubuntuforums.org/showthread.php?t=563687](http://ubuntuforums.org/showthread.php?t=563687)

I found this one while trying to find mine again. ^^

---

### Post by majedaly on 2011-09-06
Thanks, I tried to enable system beep. it worked on some servers and on others not. using aplay is much easier than system beep. Thanks a lot

---

