---
title: "Sony digital 8 capture issues"
date: 2009-03-11
forum: Ubuntu Studio
---

### Post by styleruk on 2009-03-11
Hi

I've been through the threads here and have not found anything that can fix my problem.
Using Ubuntu 8.10, and plugging in a firewire card (as USB does not work with capture), I cannot get anything in Kino.
Kino works, I have to fire it up as root otherwise it will not initialise the firewire card.  Kino tends to run the cam then counts down 'waiting for video', then stops.  See output below.

Any ideas?

Card: /dev/dv1394/0
Ubuntu 8.10, using gnome
Kino: 1.3.0
Video device:  Sony Handycam digital 8


Kino output:
>> Starting Capture
>> AV/C Enabled
>>> Using iec61883 capture
rom1394_0 warning: read failed: 0x0000fffff0000414
>>> iec61883Reader::StartThread on port 0
>>> AVC enabled 
>> Constructing File Capture tracker
>>> AVC enabled

---

### Post by inobe on 2009-03-11
let's rule out the hardware not being the cause.


is this firewire card connected to firewire header on the mainboard ?

---

### Post by styleruk on 2009-03-11
The firewire card is a PCI card.  It used to work in windows fine a year or so ago.  It's a pinnacle PCI firewire card.

---

### Post by inobe on 2009-03-11
that may just be the problem

on your mainboard there should be a header for firewire

[http://www.frontx.com/cpx509.html](http://www.frontx.com/cpx509.html)

i have a board here that's five years old with one header and one 1/0 connection....

i don't think a pci firewire card will work' if it did' it would bottleneck.

what's the make and model of your motherboard, i will check to see if it has the headers :)

---

### Post by styleruk on 2009-03-11
I have a MSI P31 Neo

It mounts the firewire ok.  I say ok, I can see it in /dev

---

### Post by inobe on 2009-03-11
i don't see a header

lets make sure you have all the requirements


with certain repos you can search down the requirements in synaptic

[http://www.kinodv.org/article/static/3](http://www.kinodv.org/article/static/3)

---

### Post by styleruk on 2009-03-11
Sorry, I'm not sure what to do with your answer, is there a chance you can explain some more?

Regards
Simon

---

### Post by inobe on 2009-03-11
just make sure you have the listed components and utilities installed, you can search for them in synaptic package manager.

> Here's the list of required components. You can usually install them from your Linux distribution's repository.

    * libglade2
    * gtk 2.6 (and related dependencies)
    * libxml2
    * libdv
    * libsamplerate
    * libasound
    * libXv
    * libpthread
    * ffmpeg, libavformat, and libavcodec
    * libraw1394
    * libiec61883
    * libavc1394

Some optional, but recommended runtime utilities include:

    * ffmpeg2theora
    * sox
    * vorbis-tools
    * lame
    * mjpegtools
    * dvdauthor
    * 'Q' dvdauthor
    * growisofs
    * mencoder


let us know if any where missing

---

### Post by styleruk on 2009-03-12
* libglade2.  **YES**
* gtk 2.6 (and related dependencies)  **Have gtk2-engines-pixbuf v2.14.4**
* libxml2 **YES**
* libdv  **YES**
* libsamplerate **YES**
* libasound **Have libasound2**
* libXv **YES**
* libpthread **NO, closest was libpthread-stubs0.  INSTALLING THAT...It worked! then didn't the second time but will restart after this reply... checking others now...**
* ffmpeg, libavformat, and libavcodec**YES, YES, but they have 51 on the end of each**
* libraw1394 **YES**
* libiec61883 **YES**
* libavc1394 **YES**

Some optional, but recommended runtime utilities include:

* ffmpeg2theora NO....installing
* sox  NO... installing
* vorbis-tools YES
* lameNO...installing
* mjpegtools  NO...installing
* dvdauthor NO...installing
* 'Q' dvdauthor NO...installing
* growisofs, NO, can't find it
* mencoder  NO...installing

These installs flagged up these removes...

blender will be removed
gstreamer0.10-ffmpeg will be removed
libavcodec51 will be removed
libxine1-ffmpeg will be removed
openmovieeditor will be removed

So, after installing libpthread, it worked.  Then I paused the video capture, when I tried to restart it did not work.  I am about to reboot just to check.  Just for clarification, it worked then not worked after the libpthread install not after the other removes that came later.

Will report back it is works or not in a mo and after a coffee....great stuff though...thanks for your help so far.

---

### Post by styleruk on 2009-03-12
OK, it's working...fantastic.  Thanks for your help inobe.  Kino is actually very good indeed.  I have about 4hrs of video footage from my band that I have to get onto youtube, this will do the trick.
Again, thanks for your help.

Regards
Simon
:)

---

### Post by inobe on 2009-03-12
that's great :)


if you ever run into any problems' it's almost always something simple.

---

