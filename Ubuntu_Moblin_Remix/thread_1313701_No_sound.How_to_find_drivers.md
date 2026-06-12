---
title: "No sound.How to find drivers?"
date: 2009-11-03
forum: Ubuntu Moblin Remix
---

### Post by Harshana on 2009-11-03
My netbook is HP mini 110-1001tu an i installed UNR to it.But no sound.Even startup sounds.How do i get rid of this?
And also i want to play mp3.wav.dat........... audio avi,mpeg, mpg............. videos which works with windows.
Will codec files compatible which i used with UBUNTU 7.04?

---

### Post by tony1212 on 2009-11-04
> **Harshana said:**
> My netbook is HP mini 110-1001tu an i installed UNR to it.But no sound.Even startup sounds.How do i get rid of this?
And also i want to play mp3.wav.dat........... audio avi,mpeg, mpg............. videos which works with windows.
Will codec files compatible which i used with UBUNTU 7.04?

I had to change the sound setting in sound preferences/Hardware to get my card working but its fine now. As for multimedia codecs I install the Medibuntu repository ([http://www.medibuntu.org/](http://www.medibuntu.org/)) full instructions given. Then install the Ubuntu restricted extras package, as well as MP3 etc this gives Flash playing for the likes of U Tube videos. if you also want DVD playback you will need libdvdcss2 as well.  You may also have to install some of the GStreamer packages from the 'UGLY' set for some of the video codecs (not supported by Canonical)

I hope this is some help

---

