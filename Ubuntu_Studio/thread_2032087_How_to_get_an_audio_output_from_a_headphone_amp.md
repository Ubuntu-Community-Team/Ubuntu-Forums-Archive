---
title: "How to get an audio output from a headphone amp"
date: 2012-07-23
forum: Ubuntu Studio
---

### Post by y183 on 2012-07-23
Good Morning,
Iam running Ubuntu studio 12.04
I have a Lehmann Black Cube USB Headphone Amplifier.  When I use this with Windows 7, it works fine, I just toggle between loudspeaker and headphone.  However, using Ubuntu Studio on my laptop, I can not get any audio output from the amplifer.  Does anyone use a headphone amp with Ubuntu, if so what do I need to do to get mine working.  Or whether you have a headphone amp or not, does anyone know how I can get the amp to work on Ubuntu.  Maybe I need a special driver, if so which one.
Many thanks
Regards
John

---

### Post by jejeman on 2012-07-23
Is this amp basicly a usb sound card?

---

### Post by y183 on 2012-07-23
Thank you for your reply.  Yes it is basically an usb sound card.  The amp bi-passes the onboard computer sound card and uses its own.  It is also a DAC.

---

### Post by jejeman on 2012-07-24
Plug in usb card and give us output from
```
aplay -l 
```
```
cat /proc/asound/cards
```

---

### Post by y183 on 2012-07-24
Thank you for the information.  I have a fairly expensive headphone amplifier, do I need to plug this in prior to typing the two pieces on the command line?

---

### Post by gareththered on 2012-07-24
A quick Google doesn't come up with much for you Lehmann Black Cube USB on Linux.  Maybe you're out of luck.  As to your last question, you don't need to plug in your fairly expensive amp.

---

### Post by y183 on 2012-07-24
Thank you for your reply.  There must be many people using headphone amplifiers working with Ubuntu Studio, which is aimed at audio/video people.  There does not seem to be too much information on the web.  Virtually nothing on YouTube.
Thanks again for your reply.
John

---

### Post by gareththered on 2012-07-25
John,

You could become the first person to get a  Lehmann Black Cube USB to work on Linux! Try the commands suggested by jejeman (all these are at the terminal/command shell).  If they don't list anything that remotely resembles you Lehmann then try```
lsusb
``` with the device removed and then again with it connected.  Look for the difference between the two (or post the 'connected' one here).  Also, capture the output of 'dmesg' ```
dmesg > dmesg.txt
``` and post the last few (20-30 or so) lines here.  If these don't help, then you have to decide whether you are willing to open your  Lehmann up to see what the chipset inside it is!  Even then, it's not guaranteed to work if they use a DAC chipset that isn't supported in Linux.

---

### Post by jejeman on 2012-07-25
> **y183 said:**
> do I need to plug this in prior to typing the two pieces on the command line?Yes, as I mentioned.
I'm refering to that headphone amplifier as USB card, which practicly it is.

---

### Post by y183 on 2012-07-25
Thank you to jejeman and to gareththered for your help.  I have been away all day today and it will possibly be the same tomorrow.  However, I will give your advice a try over the weekend.
I also e-mailed Lehmann three days ago, asking for information, at this moment in time I have not received any form of reply.
So, once again thanks for your help and time.  It is very much appreciated.
John

---

### Post by MIJ-VI on 2012-08-12
OP, have you looked in **System Settings** --> **Sound** to see if your USB headphone amp is recognized and selected as the device for sound output?

---

