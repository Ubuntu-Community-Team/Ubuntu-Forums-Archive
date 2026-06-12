---
title: "External WebCam recommendations"
date: 2009-10-11
forum: The Cafe
---

### Post by kevdog on 2009-10-11
Can anybody recommend an external webcam that would be linux/ubuntu compatible.  I have a MS 2.0Mpix cam right now, but good luck trying to get that to run with Ubuntu.

---

### Post by forkandles on 2009-11-23
I cannot understand why you have had zero replies on this request.

I can recommend the Logitech Quickcam E3500 or E3500 Plus (includes stereo headset) for use with Ubuntu 9.10. The E3500 works out of the box with Skype with one minor tweak.
Make sure the speaker symbol in the Ubuntu top toolbar is not muted.
Also using the same icon, set the Sound Preferences correctly, making sure the Input Volume is also not muted.


[http://www.play.com/Product.aspx?r=P...57&source=9593](http://www.play.com/Product.aspx?r=P...57&source=9593)

---

### Post by kevdog on 2009-11-24
That link is broken - another link perhaps?

---

### Post by Lorac1949 on 2009-11-24
> **forkandles said:**
> I cannot understand why you have had zero replies on this request.

I can recommend the Logitech Quickcam E3500 or E3500 Plus (includes stereo headset) for use with Ubuntu 9.10. The E3500 works out of the box with Skype with one minor tweak.
Make sure the speaker symbol in the Ubuntu top toolbar is not muted.
Also using the same icon, set the Sound Preferences correctly, making sure the Input Volume is also not muted.


[http://www.play.com/Product.aspx?r=P...57&source=9593](http://www.play.com/Product.aspx?r=P...57&source=9593)
The link is broken.

Also, I had the Logitech webcam E3500 working in the version of Skype installed from the Ubuntu repositories; however, it breaks up after only a few seconds and stops working entirely soon after. What can I do to fix the problem?

---

### Post by Excedio on 2009-11-24
Believe it or not, my MS NX-3000 works flawlessly.

---

### Post by forkandles on 2009-11-24
Correct link:

http://www.play.com/PC/PCs/4-/10411757/Logitech-Quickcam-E3500-Plus-Webcam/Product.html?&_$ja=tsid:11518|cc:|prd:10411757|cat:Peripherals

You have probably added this software already but if not, just make sure that you have the Karmic Medibuntu package installed:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)


Open Synaptic Package Manager (give password) > Settings > Repositories > Third Party Software > tick Medibuntu > click on Add

Make sure that the webcam is connected directly to a single USB port, not via a hub.
I can assure you that the E3500 works fine.

---

### Post by Lorac1949 on 2009-11-24
> **forkandles said:**
> Correct link:

http://www.play.com/PC/PCs/4-/10411757/Logitech-Quickcam-E3500-Plus-Webcam/Product.html?&_$ja=tsid:11518|cc:|prd:10411757|cat:Peripherals

You have probably added this software already but if not, just make sure that you have the Karmic Medibuntu package installed:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)


Open Synaptic Package Manager (give password) > Settings > Repositories > Third Party Software > tick Medibuntu > click on Add

Make sure that the webcam is connected directly to a single USB port, not via a hub.
I can assure you that the E3500 works fine.
Sorry. The link still doesn't work. There are smilies in the url. Not!

I have the Medibuntu package. Should I install Skype from Synaptic Manager or from the Internet? I've tried both, but still have had problems with the E3500. This is the pits!

---

### Post by sn0m on 2009-11-24
go for this one, works out of the box

[http://cgi.ebay.co.uk/USB-5-Megapixel-Webcam-for-Ubuntu-9-Linux_W0QQitemZ270474462748QQcmdZViewItemQQptZUK_Computing_ComputerComponents_Webcams?hash=item3ef988c61c](http://cgi.ebay.co.uk/USB-5-Megapixel-Webcam-for-Ubuntu-9-Linux_W0QQitemZ270474462748QQcmdZViewItemQQptZUK_Computing_ComputerComponents_Webcams?hash=item3ef988c61c)

---

### Post by gnomeuser on 2009-11-24
Creative Technology, Ltd Live! Cam Optia AF - works out of the box and it is both very durable (the clip isn't exactly epoxy glue like in it's ability to make it stay put at all times but I have dropped mine maybe a hundred times and the camera is perfect still) and the image quality is very good.

---

### Post by areteichi on 2009-11-24
I'm interested in this topic as I'm also thinking of buying one soon.

Looks like Logitech Quickcam 3000 is getting good reviews from ubuntu users (try searching the Newegg product reviews for 'ubuntu'). It is also one of the few webcams that officially supports Linux in its specification (perhaps more reason to support the product/company?).

[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104253]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826104253")

---

### Post by Arup on 2009-11-24
I would recommend Logitech as well athough I have a Microdia chipset cam thats being supported out of the kernel but the led lights don't work on it for low light conditions.

---

### Post by 3rdalbum on 2009-11-24
Aim for a UVC-compatible device. It's a new standard for video input devices that works plug 'n' play on all modern operating systems, including Linux.

---

### Post by forkandles on 2009-11-25
Lorac1949,

I have no idea what went wrong with those previous links but that is irrelevant since you already have the E3500.

Third attempt at link:

[http://www.play.com/PC/PCs/4-/10411757/Logitech-Quickcam-E3500-Plus-Webcam/Product.html](http://www.play.com/PC/PCs/4-/10411757/Logitech-Quickcam-E3500-Plus-Webcam/Product.html)

Skype is one of the packages included in Karmic's Medibuntu so there is no need to get Skype separately either via the internet or via Synaptic.

I can only suggest you try uninstalling/removing Medibuntu.
Make sure that the existing version of Skype has been removed. Use the following command in Terminal.

sudo apt-get autoremove skype skype-common

Now reinstall Medibuntu (Synaptic > Settings > Repositories > Third party Software) and do not forget to click on the RELOAD button.

I am sorry that you are having all these problems. It is probably of little consolation to you but I spent more than 5 days trying to get a different webcam working in another flavour of Linux (failed) followed by Ubuntu 8.10 (success). Webcams in Linux can be a real pain but the E3500 should work perfectly in Ubuntu 9.04 and 9.10. It does for me.

I can only point you to the following links for further help:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

[http://www.ubuntugeek.com/howto-install-skype-2-1-beta-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-skype-2-1-beta-in-ubuntu.html)

Good luck.

If anybody else has any experiences with the Logitech E3500 in 9.10, please feel free to contribute.

---

### Post by SunnyRabbiera on 2009-11-25
I have had good luck with logitech quick cams.

---

### Post by blueturtl on 2009-11-25
Logitech QuickCam S 7500 here, is UVC standard compatible. I haven't had to do anything to get it to work after 2.6.26.

---

### Post by koleoptero on 2009-11-25
> **sn0m said:**
> go for this one, works out of the box

[http://cgi.ebay.co.uk/USB-5-Megapixel-Webcam-for-Ubuntu-9-Linux_W0QQitemZ270474462748QQcmdZViewItemQQptZUK_Computing_ComputerComponents_Webcams?hash=item3ef988c61c](http://cgi.ebay.co.uk/USB-5-Megapixel-Webcam-for-Ubuntu-9-Linux_W0QQitemZ270474462748QQcmdZViewItemQQptZUK_Computing_ComputerComponents_Webcams?hash=item3ef988c61c)

What is this ubuntu 9 they speak of in this page? :?

---

### Post by mathyou on 2009-11-25
I would also recommend the Logitech Quickcam E3500. I spent ages trying to get my MS Lifecam to work but in the end accepted defeat. The E3500 is UVC compatible so works well, and it's very cheap. 

I use it for skype and picture quality is fine. Not sure about the most recent skype version, I have to use the old one as my system doesn't like pulse-audio.

---

### Post by forkandles on 2009-11-25
They are obviously referring to Ubuntu 9.10. They have heard of Windows 7 so Ubuntu 9 sounds right to them.

---

### Post by koleoptero on 2009-11-25
> **forkandles said:**
> They are obviously referring to Ubuntu 9.10. They have heard of Windows 7 so Ubuntu 9 sounds right to them.

Probably.

And on topic: DO NOT buy an msi starcam.

---

