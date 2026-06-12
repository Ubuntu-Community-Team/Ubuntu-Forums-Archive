---
title: "Which USB/Firewire audio interface?"
date: 2010-10-21
forum: Ubuntu Studio
---

### Post by miggols99 on 2010-10-21
I'm looking to buy an audio interface for use with Ubuntu Studio. I would like one with USB or Firewire for portability, so PCI/PCI-E is out of the question. I'm not sure which ones work well in Ubuntu Studio though.

I'm only recording for myself, so at minimum I'll need one XLR input and a 1/4" input.

My budget is £200. Does anyone have any recommendations?

I am thinking the Focusrite Saffire Pro 14, but I can't find any information about it being compatible with Ubuntu..

---

### Post by AutoStatic on 2010-10-21
Hello miggols99,

The Focusrite Saffire Pro 14 just came out about two months ago, so it is probably unsupported. Its bigger brothers, the 24 and 40, are supported by the FFADO drivers, but support is still in an experimental stage.
Not sure which other FireWire card would fit in your budget, maybe someone else has an idea. The Echo Audiofire 2 could be an option, but that one has no XLR inputs and no pre-amps. When it comes to USB, I think that the Roland/Cakewalk UA-25EX is still the best option. It is fully supported, has two XLR and 1/4" inputs with decent pre-amps.

Best,

Jeremy

---

### Post by miggols99 on 2010-10-21
I thought the Saffire might be supported because the more expensive models are supported..but I guess it's probably not working yet as it has only been two months as you say.

How is the Roland Cakewalk UA-25EX? I hear it's only USB 1.1..will this be a problem with latency? Do you have any experience with it?

Also, I seen the M-Audio Firewire Solo, but the FFADO website says only "reported to work". Do you know anything about this audio interface at all?

---

### Post by AutoStatic on 2010-10-21
> **miggols99 said:**
> I thought the Saffire might be supported because the more expensive models are supported..but I guess it's probably not working yet as it has only been two months as you say.The Pro 14 is not even on the device list of the FFADO site yet. But I'll ask on IRC, the Pro 14 probably has the same DICE chipset as the Pro 24 and Pro 40 so it might just work with a little patch. I've tested both the 24 and 40 and they seem to work well.

> **miggols99 said:**
> How is the Roland Cakewalk UA-25EX? I hear it's only USB 1.1..will this be a problem with latency? Do you have any experience with it?I own its predecessor, the UA-25, which is practically the same. No problems with latency, works well at 4ms and if you really want the most out of it it can even run at 2ms. USB1.1 is not a real issue considering the number of IO's you're looking for. USB1.1 cannot handle more than 2 channels at full duplex and as long as you're ok with that it is a reasonable option.

> **miggols99 said:**
> Also, I seen the M-Audio Firewire Solo, but the FFADO website says only "reported to work". Do you know anything about this audio interface at all?No, I don't know this device but if I read the comments on the FFADO site I think it will work.

---

### Post by sheehanje on 2010-10-22
I recommend the[ ART Tubefire 8]("http://www.artproaudio.com/products.asp?cat=1&type=79&id=130") .  It is EOL already in favor of their ADAT unit, but is still sold in shops, and still serviced.

I have not found a better interface in this price range with Tube Pre-amps ...  I've ran this so far with Ubuntu Studio 9.04 to 10.04 with very good results.

I had one issue when the firewire interface stopped working and ART RMA'd the unit and had it back to be in 4 days working good as new.  I don't think there is a better company to deal with for service.

I also own 2 Presonus FP10's and I will say without a doubt the ART is the superior unit.  I now use the FP10 for all my line in sources, and use the ART for anything that benefits from a tube preamp...  I may actually go with there ADAT unit next if I find a card that works well with studio.

Now that I told you what I prefer, and after looking at your post again :P ..

You may want to look at this device:

[The ART Tube MP]("http://www.artproaudio.com/products.asp?type=86&cat=9&id=124")

This has been known to work with Jackd with great results..

---

### Post by JC Cheloven on 2010-10-24
Many threads about this. For example [http://ubuntuforums.org/showthread.php?t=1324473&page=2](http://ubuntuforums.org/showthread.php?t=1324473&page=2)

Among the mentioned possibilities there (please read the end of the thread), you could consider specially the M-audio fast track, as a really cheap 24bit/48kHz device which may fit _exactly_ your needs. 
My own "ultra-portable-studio" for recording (overdubbing) single instrument parts, consists of this, plus a netbook, plus a behringer mic. Well, plus some small headphones and cables. All fits in a small hand bag :)

Cheers
JC

---

