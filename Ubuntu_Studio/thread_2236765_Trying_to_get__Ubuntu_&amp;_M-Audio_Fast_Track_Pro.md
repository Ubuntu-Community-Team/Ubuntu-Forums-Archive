---
title: "Trying to get  Ubuntu &amp; M-Audio Fast Track Pro working as  2x4 or 4x4"
date: 2014-07-28
forum: Ubuntu Studio
---

### Post by davstar on 2014-07-28
I have the M-Audio Fast Track Pro and i'm just wondering if anyone else out there has a way to get it fully functioning with Ubuntu. I have gotten it working somewhat but can't seem to get it to fully function like say for instance in Windows 7. When i say fully functioning i mean to where i can record from the front 2 **inputs** and playback through at least 2 of the back **outputs** so i can hear sound from my monitors at the same time. i have got it working so far as to where i can route sound in jack and record from one input at a time and hear playback sound from headphones plugged into the Fast Track Pro. it shows **_up in jack settings as : _**

Pro hw:1 
usb audio hw:0 
pro hw:1,1

i have hunch that 1,1 means 1 in and  1 out but not sure

**_why doesn't it show up as like say _**

hw:2
or hw:4 ????


i tried editing the modprobe.d/alsa-base.conf but i probly didn't do it right because it didn't work

some help please :guitar:

---

### Post by jejeman on 2014-07-29
"hw" is short for hardware.
"hw:1" number is for card number. So, this is a label for second audio card.
> hw:2
or hw:4 ????That would be third and fifth soundcard.

Now,

How many inputs/outputs does this card has? Are they all recognized by JACK?
Does this card have hardware monitoring?

---

### Post by davstar on 2014-07-29
Yes i think they are all recognized 
and the card is 4x4 
and i'm not sure if it has hrdware monitoring how can i tell?
fast track pro (hw:1)
usb audio (hw:0)
usb audio (hw:1,1)

---

### Post by jejeman on 2014-07-30
Hardware monitoring means that soundcard it self, without software help. can patch thru input signal to output.
Give us
```
aplay -l
cat /proc/asound/cards
```

---

### Post by CrocoDuck on 2014-07-31
Hi! Are you the same davstar of this post: [http://linuxmusicians.com/viewtopic.php?f=6&t=11016](http://linuxmusicians.com/viewtopic.php?f=6&t=11016) ? Have you tried with the asoundrc way: [https://community.ardour.org/node/4934](https://community.ardour.org/node/4934) ?

---

