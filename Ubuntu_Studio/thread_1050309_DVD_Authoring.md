---
title: "DVD Authoring"
date: 2009-01-25
forum: Ubuntu Studio
---

### Post by Mbengi Bongi on 2009-01-25
Hi Guys,

I have a selection of home made DVDs and I basically want to compile a DVD of the 'best bits'.

Whats the best solution for extracting them (to Video_ts folder, NOT *.avi, *.mp4 etc) and authoring the clips onto a DVD.

Preferably DVD menus etc could be made as well ;)

Any ideas? :)

---

### Post by paulisdead on 2009-01-25
dvdbackup -M -i /dev/dvd -o /where/you/want/to/save/it

you of course need dvdbackup installed, and make sure that /dev/dvd is your dvd device you want to dump from.  That'll dump the dvd straight over, no conversion.  The only time I did authoring was maybe five years ago, and I think the command line utility was dvdauthor.  It was very complicated and required editing xml files, and making menus in the gimp was tricky.  I'm sure there has to be an easier way by now.

---

### Post by ajgreeny on 2009-01-25
I think **devede** may do what you want, but I have never used it.  You may also need something to chop your tracks up etc etc, and perhaps **avidemux** for that followed by **devede**

---

### Post by Mbengi Bongi on 2009-01-26
OK, thanks very much guys.

I'll give your suggestions a try.

Cheers  :popcorn:

---

### Post by cotcot on 2009-01-26
I can confirm what ajgreeny writes. Extracting your best bits with avidemux (select "copy" for audio and video and mpgeg-PS (A+V) for format. 
Making the dvd with devede is easy as well. I have done this multiple times.

---

