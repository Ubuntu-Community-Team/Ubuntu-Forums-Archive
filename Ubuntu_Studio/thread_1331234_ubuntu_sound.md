---
title: "ubuntu sound"
date: 2009-11-19
forum: Ubuntu Studio
---

### Post by morsedelay on 2009-11-19
hi all , 

i have 9.04 . and sound is running only on rythebox 
i tried to use LMMS , MIXXX , and amarok . but after installing all in froums recomended codecs , enable or desable jackd . checking alsamixer,  alsadriver etc . 
it still make no sound :( 
by the way what is actualy the deamon jackd and what it makes , do i neeed this prozess ? 

many thanks 
morsedelay 

AMD athlon 64x2 dual core 5000+
ATA 
NVIDIA GeForce 8200 / ASUS

---

### Post by gorgon on 2009-11-19
Hi,

have you checked the audio settings in the programs that you use, that they are set to 'alsa'? 

> what is actualy the deamon jackd and what it makes
jackd is a audio routing program which quite a few sound production programs use (are depending on). get and install 'qjackclt', if you havent already. It is a graphical front end to jackd. LMMS needs jackd to be running before it starts.

Amarok should work without jackd.

tell us how it goes!

cheers,
g

---

### Post by Acradon on 2009-11-24
This is an old thread, but I am experiencing the same problem. I am running 9.10 and can't get the sound in LMMS and Amarok to go. Has anybody got a solution for this problem.

Greets 

Acradon

---

