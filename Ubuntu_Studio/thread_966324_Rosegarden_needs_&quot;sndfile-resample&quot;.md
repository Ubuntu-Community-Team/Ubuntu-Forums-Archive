---
title: "Rosegarden needs &quot;sndfile-resample&quot;"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by bolex100 on 2008-11-01
Any idea how I get that?  I tried installing from terminal but:-

 sudo apt-get install sndfile-resample
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sndfile-resample

---

### Post by Capoeira on 2008-11-07
post without intention - please delete

---

### Post by bolex100 on 2008-11-08
"without intention"?
I'm asking a question and waiting for an answer.

---

### Post by thorgal on 2008-11-08
sudo apt-get samplerate-programs

---

### Post by bolex100 on 2008-11-09
Invalid operation samplerate-programs

I was just staring to have hope.

---

### Post by mrhelpman on 2008-11-09
> **thorgal said:**
> sudo apt-get samplerate-programs

Urmm that should have been:

sudo apt-get install samplerate-programs

as in:
>  sudo apt-get install samplerate-programs
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libsamplerate0
The following NEW packages will be installed
  libsamplerate0 samplerate-programs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 122kB of archives.
After unpacking 238kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main libsamplerate0 0.1.2-2 [108kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe samplerate-programs 0.1.2-2 [14.2kB]
Fetched 122kB in 0s (363kB/s)
Selecting previously deselected package libsamplerate0.
(Reading database ... 125988 files and directories currently installed.)
Unpacking libsamplerate0 (from .../libsamplerate0_0.1.2-2_i386.deb) ...
Selecting previously deselected package samplerate-programs.
Unpacking samplerate-programs (from .../samplerate-programs_0.1.2-2_i386.deb) ...
Setting up libsamplerate0 (0.1.2-2) ...

Setting up samplerate-programs (0.1.2-2) ...
johnt@TOM001:~$


JT

---

### Post by thorgal on 2008-11-10
my mistake, I type way too fast sometimes ... 

bolex100, try to get familiar with the debian style system / package maintenance (apt-get, dpkg). It is more than worth it, it can be critical at times.

---

### Post by supapete on 2009-07-31
Well, thorgal. A big thankyou. The only way you could know what to do is if you're some kind of magician. That's good advice about familiarizing oneself with the secrets of the terminal. I'm reading up on Linux like there's no tomorrow and it just doesn't help sometimes- like now. I think there's a secret circle of Linux sourcerers who are admitted only after serving years of zenlike committment in a secret monastery. Thanks again. (I wonder who bolex100 offended against- perhaps the handle ?) regards all, P.S

---

