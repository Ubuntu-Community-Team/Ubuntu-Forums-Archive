---
title: "Conceptual: can a usb2.0 audio device work at usb2.0 speed?"
date: 2010-05-08
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2010-05-08
Hi, I'm in doubt:

I thought that, in the present lack of a 2.0 standard, usb2.0 audio devices may "work" (or not) in linux, but with the limitation of 1.0 speed.

But recently, a particular user reported to be recording in 5+ tracks at 48kHz/16bit using a usb 2.0 device: [an edirol MX 16DX]("http://www.rolandus.com/products/productdetails.php?ProductId=860"). I think this surpasses the possibilities of 1.0 speed, so I'm confused. 

Anyone able to bring some light on this?

---

### Post by AutoStatic on 2010-05-08
I know of 2 USB2 devices that are reported to work:
[LIST]
[*][Edirol UA-1000]("http://www.roland.com/products/en/UA-1000/")
[*][Edirol UA-101]("http://www.roland.com/products/en/UA-101/")
[/LIST]
And they should work at USB2 speed otherwise there's not enough bandwidth to record more than 2 channels at once.

---

### Post by JC Cheloven on 2010-05-08
Thanks, autostatic! :-)

I always assumed that when usb devices were listed in alsa, it meant that they worked, but on an 1.0 basis, which should be false in view of your comments.

Anyway, the cards you mention are adviced as to be problematic in alsa (chopped playback): 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Edirol)
Also the user that reported about the MX16DX stated that playback didn't work (he had to use another soundcard for that).

I'm affraid that purchasing one of these will be a box of susprises... but the focusrite saffire pro 40 (I'd like this one) never changed from "experimental" in ffado since a year+. That's why I'm wondering whether an usb2 device could fit my needs or not.

---

