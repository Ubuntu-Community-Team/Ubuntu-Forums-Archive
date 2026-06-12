---
title: "My Ubuntu Studio last release not work with video ultra hd 4k and not recognise sdxc"
date: 2016-08-31
forum: Ubuntu Studio
---

### Post by levideo2 on 2016-08-31
Hello to all,
given that I have always been a user of Windows operating systems, I am intrigued to linux world, and then yesterday I decided to dedicate a PC configured so:


asus motherboard p5qpro
cpu intel Q9550 quad core 3.29 GHz
x2 8gb ram 4 gb corsair pro metal with low c.l
ssd ocz toshiba 240GB
nvidia gt9800
power supply 600w
Chieftec houses


I installed in less than 30 minutes the latest release of ubuntu studio.
I did do all the updates.
my intention 'to evaluate whether Linux is able to guarantee me decent performance in video editing with ultra hd 4k video created with my fantastic lumix gx80 / &#8203;&#8203;85 that records
at 3840 x 2160 25p / 30 mp4 100mb / s


as usual using a sdxc
professional of lexar from 128gb and to download the clips using a small USB 3.0 adapter produced by hama company able to read this format and capacity 'high.
with windows 10 no recognition problem, whereas with the key and ubuntu 'appeared on the desktop but you can not' read the contents to a strange error that can not mount it if I did not see evil.
no matter I copied a few 4k clips on another stick and poured on ubuntu studio desk.
alas I noticed that the sw for video editing ubuntu study are not compatible with the 4k but one that serves to catch only but in fact I do not need to anything-
I tried to install the sw Lightworks and 4k clips are not recognized the wheel spinning endlessly.
What should I do to fix it ??
it would be a pity not to use this wonderful distribution sw for a great way limit.
:confused:
I hope you help my.
sorry about my bad english i use google translate also
 thanks  a lot levideo

---

### Post by levideo2 on 2016-09-01
I remain always waiting for your suggestions.
Meanwhile I wanted to understand the fact that it is playing movies 4k with youtube and with an application that I could find in the study Ubunto distribution ranging in spurts, while Windows 10 is fine.
I assume that the problem is due to the nvidia driver Ubunto in fact not 'been able to manage the installation of these drivers automatically.
How can I fix the problem ??
let me know, thanks levideo

---

### Post by geomcd1949 on 2016-09-27
You must insure that the source material can be used by Lightworks, a professional NLE. I suggest you use the Lightworks documentation and their Forum to understand the requirements for importing video footage into the editor. If you do, you will be rewarded.

---

### Post by Bucky Ball on 2016-09-27
For the card, install exfat-fuse and exfat-utils from Synaptic Package Manager, reboot and you should be able to see and access the sdxc card with no issues.

Incidentally, if you are wanting to do just video editing you probably do not want a full Ubuntu Studio install. That has a LOT of stuff you are never going to need or use for audio and other things.

Easiest and less bloat to just install Xubuntu and then the packages you need, Lightworks or whatever. You can also install 'bundles' from Ubuntu Studio. For instance, ubuntustudio-video is available in Synaptic. Install that and it will install all UStudio video stuff without the rest. 

Just thought I'd mention. I use Blender for video editing myself, syncing audio with video, rendering and rough cuts, then Openshot and Kino for final cuts. Do you have the correct driver installed for that card? Additional Drivers and the 364 or 367 from memory. You should see it there but if you haven't done an update yet, please do one first.

---

