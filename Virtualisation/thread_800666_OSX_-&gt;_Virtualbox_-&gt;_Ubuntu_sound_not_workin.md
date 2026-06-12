---
title: "OSX -&gt; Virtualbox -&gt; Ubuntu sound not working in ubuntu"
date: 2008-05-20
forum: Virtualisation
---

### Post by Ryan_Singer on 2008-05-20
Hello,

I just installed Ubuntu within Virtualbox on my mac, and I can't get sound to work.  I already installed the Guest OS tools for virtualbox, and am stuck trying to think about a next step.

I'd appreciate any ideas,

--
Ryan Singer

---

### Post by ACGilbert on 2008-05-20
I think you go into Virtualbox settings -- audio and select Alsa.
AC

---

### Post by 00arthuryu on 2008-05-20
If you're using Hardy, then you should change it to pulseaudio

---

### Post by ACGilbert on 2008-05-22
I switched from Alsa, which worked, to PulseAudio and that also works.
AC

---

### Post by 00arthuryu on 2008-05-22
not on mine it doesn't :lolflag:

---

### Post by olavjunior on 2009-04-16
Neither does mine! 

I`m using os x, and there`s no choise to choose alsa in the audiosettings in virtualbox. I`ve tried both pulse and alsa as output in ubuntu, with no success...

---

### Post by Captain_Glen on 2009-04-16
Click on your virtual machine.  Click settings, click audio, click something other than null audio driver.

---

### Post by Cybie257 on 2009-04-16
> **olavjunior said:**
> Neither does mine! 

I`m using os x, and there`s no choise to choose alsa in the audiosettings in virtualbox. I`ve tried both pulse and alsa as output in ubuntu, with no success...

Choosing Alsa or Pulseaudio is for the Host settings. This would be for Ubuntu/Linux rather than a setting for OS X. Might want to check a MAC OS X forum for that answer. 

PulseAudio in an Ubuntu/Linux Host will allow you to play audio in both the VM and Host at the same time, while Alsa will restrict you to one of the other. 

-Cybie

---

### Post by amudman on 2009-04-22
On my Ubuntu Intrepid (IBM T23 laptop with guest win xp guest, I fumbled around until I saw this thread. pulseaudio works for me. and as a 'by the way'--- MediaMonkey is up and running so "I B Happy" and I can't complain about the machine slowing down, but I have 1 gig.

I cannot begin to thank everyone enough who has helped me enjoy my music and Ubuntu.   

(I talked to the boss and he said for you to take the rest of the day off)[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

