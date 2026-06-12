---
title: "Skype and Webcam"
date: 2009-01-18
forum: System76 Support
---

### Post by allegrosails on 2009-01-18
Hi, I am new to Linux and Ubuntu. I want to get Skype up and running then move to ekiga. (My family is mostly on Skype).
I went to the Skype download site and downloaded the Ubuntu 7.04-8.04 package. But when I get "Error wrong archecture" when I try to install. It's not clear to me which other package I should download. My processor is:
Core 2 Duo E7300 2.66 GHz FSB 1066 MHz L2 3 MB

Suggestions?

Also: I purchased a Logitech QuickCam Communicate MP (S 5500) webcam. It comes with only Microsoft software. Where do I find drivers for it: Logitech site or elsewhere?

Thanks

---

### Post by drewbenn on 2009-01-18
Sounds like maybe you are using 64-bit Linux but you downloaded the 32-bit version?  If a "uname -m" in the terminal returns "x86_64," that might be the case.  There is a 64-bit package under the "AMD64" section at [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype), give that a shot.
I don't have a webcam nor have I actually used Skype, so I can't provide any help past that suggestion ;)

---

### Post by thomasaaron on 2009-01-18
If you're using a System76 computer, follow these directions...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by perce on 2009-01-19
> **allegrosails said:**
> 

Also: I purchased a Logitech QuickCam Communicate MP (S 5500) webcam. It comes with only Microsoft software. Where do I find drivers for it: Logitech site or elsewhere?

Thanks

Plug it in: either it works, or it doesn't. If it doesn't the best strategy is often to wait 6 months for the next version of Ubuntu. Supported hardware in Linux is often plug-and-play even if in Windows isn't.
(This is true only in first approximation: if you're expert, you can sometimes do some black magic and make a little more hardware to work)

---

### Post by allegrosails on 2009-01-19
Thanks for the reply, Tom.
I was able to get a version of Skype loaded. (amd64). I now can get that application up, active and I can log on and see my contacts.

I still do not have either webcam or headset working.

I followed the link you provided. Add/Remove>>All available>>Other>>Ubuntu unrestricted extras.
When I applied changes, I got this message:
Cannot install 'ubuntu-restricted-extras'

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

(Note: I installed gstreamer recently on an unrelated problem.)
I don't know about the 'synaptic' package manager. If I remove software, will something else break?

I got my Sable system (SAB-P3 Core 2 Duo E7300) last week with Ubuntu 8.10 and I believe I have 64 bit. I have gone to the Logitech site but am not sure which driver to download. I would rather load from an Ubuntu extra if possible and have it part of my package.

BTW: I found the vendor and product ID: 046d (Logitech) PID: 09a1 (Quickcam S5500)

---

### Post by thomasaaron on 2009-01-19
Perce is right. The web cam probably will either work or it won't. There isn't a driver download for it that I'm aware of.

Here is a website that should get you moving in the right direction, though...
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

If you have a package that conflicts with ubuntu-restricted-extras, though, that's not good. That package contains most of the codecs you need for playing different audio and video formats.

If you go to System > Administration > Synaptic Package Manager and search for ubuntu-restricted-extras and try to install it, it will show you what packages are in conflict. Then you can remove them and start over with that first tutorial.

---

### Post by perce on 2009-01-19
I can add, my webcam used to work until Hardy, but something was changed in the new kernel and now it shows only green garbage. This is a common problem in Inrepid, and there is a proposed fix on the web, which consists on starting skype with a strange option (search the forum for webcam Intrepid and you'll find it). Apparently this hack fixed the problem for most people, but not for me.

---

### Post by oregonbob on 2009-04-22
My Logitech Quickcam S5500 web cam worked just great with Skype, video and audio. All I did was install Skype, then I had to adjust the audio source by simply selecting the logitech audio source.

---

