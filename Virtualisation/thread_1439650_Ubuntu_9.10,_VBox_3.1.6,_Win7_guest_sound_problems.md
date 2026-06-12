---
title: "Ubuntu 9.10, VBox 3.1.6, Win7 guest: sound problems"
date: 2010-03-26
forum: Virtualisation
---

### Post by dartmusic on 2010-03-26
I do see that others have had sound issues with this setup, but the solutions (if they ever get posted) don't seem to work or apply in my situation.

I am running 9.10 32bit, the latest VirtualBox and trying to get Win7 as a guest OS working correctly.  I have a CoreDuo 3.6GHz proc, 4GB of RAM and using the internal Intel HDA sound card.  I have sound set up for ALSA and with the AC97 controller in Vbox.  I loaded the AC97 driver from the Realtak site IN Win7, but the sound is cutting in and out, sort of crackly sounding as if there's a sampling rate mismatch or something similar.  I also tried using the PulseAudio setting, but the results were the same.

If anyone can point me in the right direction to get this working, I would greatly appreciate it!

Thanks.

---

### Post by stuarto on 2010-03-28
I have the same issue with 9.10, WinXP VM, Intel Quadcore 9300, also with Intel HDA card (82801l). Am going through [http://forums.virtualbox.org/viewtopic.php?f=2&t=12112](http://forums.virtualbox.org/viewtopic.php?f=2&t=12112) trying out suggested solutions.

Hopefully this might also help you.


Stuart

---

### Post by stuarto on 2010-03-28
Actually, I've found changing the number of VM processors down to 1 has improved sound performance greatly (at least for the past hour I've been testing it ;).

Of course, ymmv :)


Stuart

---

