---
title: "[SOLVED] Apophysis Linux - possible?"
date: 2008-12-10
forum: Ubuntu Studio
---

### Post by djbushido on 2008-12-10
Is it at all possible to get apophysis to run on linux (not apophysis-j)? Or something like it? I use gnofract4d, but want to get back to flames not mandelbrot and julia. I am open to compiling or installing an alternative, or something else if that comes up.

---

### Post by sleepingdragon on 2008-12-11
Are you referring to what I'm showing in my screenshot? Apophysis 2 seems to work fine under WINE.

---

### Post by djbushido on 2008-12-12
What do i need to do to get it running? I haven't personally tried this, but have had bad experiences previously with WINE, and saw some posts that it didn't work... Also, do you know if i can still use flam3?

EDIT: sorry for all the questions, but can i use the 2.0x betas?

EDIT: that's what the screenshot shows, sorry...
Marking solved

---

### Post by sleepingdragon on 2008-12-13
Glad to see you got it going. I only used the beta because that was the most current version at the time I downloaded Apophysis. I'm not even sure what the latest one is now, but WINE has certainly come a long way since the early days and seems to be a lot more stable.

---

### Post by djbushido on 2008-12-13
Thank you for your help. Also, do you know if there is a way to produce a flam3 batch render script?

---

### Post by sleepingdragon on 2008-12-14
I'm not sure if you've managed to install the flam3 install files, you can find them [here]("http://flam3.com/flam3-2.7.17.tar.gz"). You will need to install the build-essential kit from the repos before you install flam3: [I]

sudo apt-get install build-essential[/I] 

in a terminal. From there, you need to run the configure file from the .tar.gz file you downloaded. Open the .tar.gz file and an archive manager should open. Use the extract facility and extract the folder to a location of your choosing. Open a terminal and cd to that directory and run:

[I]sudo ./configure

[/I]Beyond that I cannot help you. I never ran the flam3 scripts.

---

### Post by djbushido on 2008-12-14
oh, i was using flam3 from the windows version. maybe compiling for linux might work.

---

### Post by matiasw on 2012-07-20
I don't know, apophysis-j works for me.

---

