---
title: "Audacity only lets me record for HALF A SECOND!"
date: 2009-05-02
forum: Ubuntu Studio
---

### Post by fredbird67 on 2009-05-02
I upgraded to Jaunty Jackalope last weekend.  I'm trying to record an old LP to burn to a CD, but I'm running into the most infuriating problem!  Whenever I record, even though I've got oodles of disk space left, Audacity only captures the first HALF A SECOND of audio, and I've got the screenshot to prove it!

Where in Sam Hill do I correct this?  Sheesh!

---

### Post by fredbird67 on 2009-05-02
Never mind!  I completely removed it and reinstalled it and it's working fine now. :-)

---

### Post by Altay_H on 2009-06-03
I have the exact same problem.

> **fredbird67 said:**
> Never mind!  I completely removed it and reinstalled it and it's working fine now. :-)
Unfortunately this did not work for me. I went to Synaptic and completely removed both audacity and audacity-data then installed them again, but the problem still exists.

EDIT:
[Changing the frequency to 48000 solves the problem.]("http://www.linuxquestions.org/questions/ubuntu-63/audacity-records-for-a-half-second-then-stops.-723221/")

---

### Post by igorzwx on 2009-06-03
This might be a universal solution to such problems:
[http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html](http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html)

Some other hint one may find here:
[http://n2.nabble.com/user/UserNodes.jtp?user=126956](http://n2.nabble.com/user/UserNodes.jtp?user=126956)
:)

---

### Post by robert shearer on 2009-06-03
Audacity is a great app:)

Though I prefer gramofile for recording large numbers of lps. (install mctools-lite to get the integrated mixer)

Gnome Wave Cleaner for removing clicks, pops and other noises. (gwc)

and wavebreaker for splitting tracks.

---

### Post by igorzwx on 2009-06-04
Interesting!

GramoFile README:
"To record and play .wav files, modified versions of brec(1) and bplay(1) 
by David Monro are used. These programs provide buffered recording and
playback, so all will go well even on a highly loaded system..."

$ brec
The program 'brec' is currently not installed.  You can install it by typing:
sudo apt-get install bplay
bash: brec: command not found
$ sudo apt-get install bplay

$man brec

brec [-d device] [-B buffersize] [-S] [-s speed] [-b bits] [[-t secs] |
       [-T samples]] [-r|-v|-w] [-D level] [file]


$ brec -d /dev/dsp1 -S -s 44100 -b 16 -w mumu.wav

It works! 
Recording can be stopped with Ctrl+C

Quality is good.

sox mumu.wav mumu-out.wav norm -3 

:)

---

