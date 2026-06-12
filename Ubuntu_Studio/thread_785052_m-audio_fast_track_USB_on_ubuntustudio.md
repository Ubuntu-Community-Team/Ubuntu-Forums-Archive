---
title: "m-audio fast track USB on ubuntustudio"
date: 2008-05-07
forum: Ubuntu Studio
---

### Post by pengrac2 on 2008-05-07
hi everyone. first post, yay. anyway, im a guitar player and im having trouble installing working drivers for my m-audio fasttrack USB. I would like to use Ardour with it too. Any one know how i can go about doing this. any help would be greatly appreciated.

---

### Post by SynthesizersFTW on 2008-05-10
> **pengrac2 said:**
> hi everyone. first post, yay. anyway, im a guitar player and im having trouble installing working drivers for my m-audio fasttrack USB. I would like to use Ardour with it too. Any one know how i can go about doing this. any help would be greatly appreciated.

Welcome!  Hope we can help...

A quick look at the [ALSA M-Audio page]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio") shows a bunch of other USB products, so I'm guessing that it should be supported just fine.

You can find the instructions for generic USB sound support at:

[http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio")

An Ardour user reported:
[INDENT]Check and see how many ALSA devices you have. I have an M-Audio Fast Track Pro that creates two ALSA devices (hw:0,0 and hw:0,1), and all of the inputs are on the second device.
Hope that helps.[/INDENT]

If you already have ALSA going and you see this, you're halfway there.  Of course, you will also need JACK to route everything properly!  Any more specifics, ask away.  Hope you can get up and running soon.

---

### Post by robeast on 2008-05-11
Check this out: [http://ardour.org/node/744](http://ardour.org/node/744)
Basically, it's hit and miss with the Fast Track. ALSA doesn't list it as a compatible device on their website.

---

### Post by ElectricJake on 2009-11-12
If you need confirmation, I can tell you it does work, even on a laptop, and in the 2.9ms range, no additional drivers or anything weird.

as far as performance goes, it's just barely up to snuff. push it too hard and it will disconnect, requiring reboot (alsa force-reload doesn't fix it)

If your kernel, jack, memlock, and permissions are great, that interface will do what you want it to. Maybe it's not officially linux-supported, but it's very compatible.

But to a linux-user looking to buy one: get an Edirol instead and save yourself a lot of headaches.

---

### Post by JC Cheloven on 2009-11-13
> **ElectricJake said:**
> If you need confirmation, I can tell you it does work, even on a laptop, and in the 2.9ms range, no additional drivers or anything weird.

as far as performance goes, it's just barely up to snuff. push it too hard and it will disconnect, requiring reboot (alsa force-reload doesn't fix it)

If your kernel, jack, memlock, and permissions are great, that interface will do what you want it to. Maybe it's not officially linux-supported, but it's very compatible.

But to a linux-user looking to buy one: get an Edirol instead and save yourself a lot of headaches.

Hi, Electric, do you realize you're answering to a post which was inactive since may 2008 ?

Anyway, your info has been useful to me, related to [this thread]("http://ubuntuforums.org/showthread.php?p=8312188#post8312188").

Could you tell which version of ubuntu are you using the Fast Track on? Did you use it with a condenser mic?

---

### Post by ElectricJake on 2009-11-16
yes I realize this is old, but on google old topics die hard. if I'm still finding it, I figured someone else might also

Ubuntu Studio Intrepid, I think? I'm dabbling with another distro right now (64) Really only used for recording though the 1/4" jack, though I have read results are more consistent using the XLR if you have sufficient preamp, as the 1/4" built-in preamp consumes just a bit more power, increasing likelihood of snd-usb module unloading

---

### Post by MeGodzillaUDead on 2011-01-19
[QUOTE=ElectricJake;8326573]yes I realize this is old, but on google old topics die hard. if I'm still finding it, I figured someone else might also

  TRUE!  I'm reading this in 2011 trying to decide wether or not to buy one of these interfaces!  Thanks, MeGodzillaUDead

---

### Post by MeGodzillaUDead on 2011-01-19
[QUOTE=ElectricJake;8326573]yes I realize this is old, but on google old topics die hard. if I'm still finding it, I figured someone else might also

  TRUE!  I'm reading this in 2011 trying to decide wether or not to buy one of these interfaces!  Thanks, MeGodzillaUDead

---

### Post by waperboy on 2011-02-07
Since this was necroed anyway, I'll just say that I got the M-Audio Fast Track ("MKII", the newer USB2 variety, not Pro or Ultra) - to work without hassle on my Ubuntu 10.04, together with Jack, Rakarrack and Ardour.

---

### Post by cptncatholic on 2011-11-09
> **waperboy said:**
> Since this was necroed anyway, I'll just say that I got the M-Audio Fast Track ("MKII", the newer USB2 variety, not Pro or Ultra) - to work without hassle on my Ubuntu 10.04, together with Jack, Rakarrack and Ardour.

This topic is STILL coming up in Google... 

Waperboy, are you able to record each channel to a separate track in your DAW? I use Ardour and I'm considering this unit for home recording. 

Thanks!
tc

---

### Post by sgx on 2011-11-11
That's the way google is supposed to work. Sometimes it pays
to add a few -2009 -2008 -2007 -2006 to your search, when you know
something did not exist in 2005, and has the most usage in 2010
and 2011.

The FastTrack works fine with some kernels, not at all with others.
When it works, it's quiet, and records a nice signal. I would not
go pushing usb device buttons, or hot-plugging cables,
while powered on, since such devices are probably not filled
with exotic circuitry to protect components.
Hurray for Friday :popcorn:

---

### Post by noisemaker? on 2011-11-20
i have also an m audio fast track pro.. forgett it, it is not working... you can only see 2 channels at a time

now i got an focusrite saffire pro 10 and texas instruments firewire... but as lucky as i am this is currently also not working at all

---

### Post by Cergin-Moor on 2011-11-22
This seems quit strange to me. I am running The fast track pro M- Audio in Ubuntu 10.10. 

I know thats not Ubuntu studio, but I am planning to switch in the near future; as I installed it on USB-stick only 8 GB.

But still its strange because the M-audio fast track is working nicely.

---

### Post by sgx on 2011-11-22
> **noisemaker? said:**
> i have also an m audio fast track pro.. forgett it, it is not working... you can only see 2 channels at a time

now i got an focusrite saffire pro 10 and texas instruments firewire... but as lucky as i am this is currently also not working at all
Now that your Focusrite card is working, you might be able
to sell or trade the mAudio device. Some of the big audio websites have gear shifting sub-forums.

[http://www.harmonycentral.com/community/classifieds/for-sale-wanted/recording?view=discussions](http://www.harmonycentral.com/community/classifieds/for-sale-wanted/recording?view=discussions)

[http://www.kvraudio.com/forum/viewforum.php?f=43](http://www.kvraudio.com/forum/viewforum.php?f=43)

[http://www.musicradar.com/forum/forumdisplay.php?f=66](http://www.musicradar.com/forum/forumdisplay.php?f=66)

---

### Post by Bernard_ivo on 2011-12-21
Hei folks,
Happy to find "almost dead" discussions on m-audio and ubuntu, which seem to be alive. I'm using linux (debian and then ubuntu) for almost a decade already, and have no intention to switch to Windows when it comes to playing and recording music. I'm planning to buy myself an external audio card that is compatible with Ubuntu. Moreover I need a card that will be able to support several inputs and outputs and a guitar as well. So far I have looked at M-audio Fast track pro and EMU 0404 but haven't found much comments on their Linux/Ubuntu compatibility (nor a comparison between both of them). However I would be grateful if you can point me where I can read more about good audio cards and Ubuntu(reviews for example). 
Thanks

---

### Post by anairam on 2012-01-24
In case you are interested, here is a guide to fully (24bits) use M-Audio Fast Track Pro in Debian:

[http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html)

In Ubuntu 10.04, an above the sound card runs out-of-the-box in 16bits.
To be able to run it in 24bits you should do some dirty work compiling the kernel. I have tried the above guide in Ubuntu with no luck, but I was not much patient either. I choose to switch to debian.

Good news is taht since kernel 3.1 the patch mentioned in above blog is merged to sound kernel branch, so it will be no need to compile the kernel and the sound card will work on 24-bit/96kHz out of the box :)

 
cheers,

m

---

### Post by Bernard_ivo on 2012-01-26
Thanks will probably give m-audio a try. 
Cheers

---

### Post by prefabSOFT on 2012-12-19
What external interfaces have the best support under Ubuntu?
(or do you personally have good experience with)

---

