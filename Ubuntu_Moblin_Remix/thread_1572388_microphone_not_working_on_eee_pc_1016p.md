---
title: "microphone not working on eee pc 1016p"
date: 2010-09-11
forum: Ubuntu Moblin Remix
---

### Post by max313 on 2010-09-11
hello 
i instaled ubuntu netbook remix onmy eee pc 1016 but microphone doesnt work i read the insructions for eee pc 1005 on ubuntu wiki but it still not working
i checked alsamixer an unmuted everything but i still have his problem i will be happy if u help me i really need microphone
thanks.

---

### Post by max313 on 2010-09-12
no idea? please i need to use mic i dont want to leave ubuntu because of this problem but i need it

---

### Post by cespinal on 2010-09-13
patience my friend... there's lots of people trying to figure this out

---

### Post by max313 on 2010-09-13
So u guys also hae the same problem?
Why there is no info about this module in wiki ?
But i need to use it the most thing for using a netbook is to work wit internet and it needs microphone for skype and ....

---

### Post by bamboodragonfly on 2010-10-08
Had the same problem with the internal microphone not working on my Asus  1015PED. Not sure if the 1016P uses the same sound card hardware but I fixed my microphone by installing the padevchooser package with the  Package Manager and then using the volume control to unmute the audio  (click on icon that looks like a speaker symbol) in the Input Devices  tab. You may have to play around with the left and right volume control  sliders a bit. I have Ubuntu Netbook Edition 2.6.32-25-generic installed.

---

### Post by BigRedButton on 2010-10-11
bamboodragonfly has the right idea. If you install all of the alsa packages and the gnome alsa mixer and use it to turn up the gain (the left/right sliders) on the PCM the mic should register. if you open up the alsa mixer and the sound preferences to the input tab next to each other, you can see what levels you're getting from your mic. You might also need to mute the channel labeled "Front Mic" since for some reason that pipes it through the main speakers, or it did on my aspire d250.  Either way, it's a volume issue, not a driver issue, so it shouldn't be too difficult to get working

edit: make sure you get Gnome Alsa Mixer, not alsamixergui. the second is horrible and i'm not quite sure why it's still on the software channel

---

### Post by max313 on 2010-10-12
still not working i have been tested pulse and alsa before posting

---

### Post by djtippman on 2010-10-19
I upgraded my 1016p to 10.10 from 10.04 and my Mic now works.

---

### Post by victorius on 2010-10-27
I could at least get my mic working by installing padevchooser and playing around with the volume. I have Eee PC 1001px

---

### Post by phillsky on 2010-11-07
> **victorius said:**
> I could at least get my mic working by installing padevchooser and playing around with the volume. I have Eee PC 1001px

Could you list exactly what you did to get it to work?

I have an EEE PC 1001PX with an out of the box Ubuntu 10.10 netbook installed. But I can't get the mic to work,

---

