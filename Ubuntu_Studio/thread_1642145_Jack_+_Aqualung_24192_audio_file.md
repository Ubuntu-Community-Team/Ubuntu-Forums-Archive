---
title: "Jack + Aqualung 24/192 audio file"
date: 2010-12-10
forum: Ubuntu Studio
---

### Post by solo16 on 2010-12-10
Hi guys,
 
Just asking if anyone has successfully played 24/192 audio file thru Jack + Aqualung?
 
In Jack i can't even change the bit resolution to 24bit it's greyed out and locked to 16 
 
bit only. 
 
Anyway i'm planning to buy some hi-res auido files, before doing that i just want to 
 
make sure it's supported.
 
Btw, i'm using Ubuntu Studio 10.10 in rt kernel.
 
Cheers!

---

### Post by cchhrriiss121212 on 2010-12-10
Jack uses 32bit float by default. The greyed out options are for OSS, and you will be using ALSA. The ability to play hi res audio will depend on your soundcard as well, so I hope you are not using some on board chipset.

---

### Post by solo16 on 2010-12-10
Hi,

Yes my soundcard  is supported for such res. I'm currently using RME Hdspe AES. 

I've just tried to configure the jack to 96khz, however it refuses to start. Did i missed something ?

Thx!

---

### Post by cchhrriiss121212 on 2010-12-10
First you should set your card to the rate you want, you should be able to do that in hdspconf. Set jack to use the same rate you set your card to. If jack does not start try to post the contents of the message window.

---

### Post by solo16 on 2010-12-10
> **cchhrriiss121212 said:**
> First you should set your card to the rate you want, you should be able to do that in hdspconf. Set jack to use the same rate you set your card to. If jack does not start try to post the contents of the message window.

Hey,

thx for your fast respond!!!! first i'm not able to run hdspconf for some unknown reason. but i use alsamixer to change the target sampling rate, let say 192, then i change the jack setting to 192 as well. quit and start again, it shows that the max_samplerate=96 for jack but it can be changed.

so my question how, how can i configure jack for supporting sample rate larger than 96? also in jack it missed 176.2 sampling rate setting as well.

Many Thx!!!!

---

### Post by cchhrriiss121212 on 2010-12-10
Setting your card to 192KHz requires more resources, so it could be that your card only supports that rate with a limited number of channels. You will have to consult your manual to find out, then set that number manually in the jack setup window. 

Jack does not have a setting for 176.2, that is by design as I'm sure not many people will be using it.

---

