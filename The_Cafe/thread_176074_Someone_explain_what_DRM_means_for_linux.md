---
title: "Someone explain what DRM means for linux?"
date: 2006-05-14
forum: The Cafe
---

### Post by ade234uk on 2006-05-14
Im a bit behind the times with things. Can someone explain what DRM means, and how this effects Linux?

---

### Post by Sef on 2006-05-14
DRM = Digital Rights Management

You may not be able to play your favorite dvd, or cd at all. Of course, someone could write a hack for it, like DVD Jon did.

---

### Post by Iandefor on 2006-05-14
DRM is pretty much any system of content protection, meaning that it has safeguards to limit how much you can copy content. For instance, in the Sony Rootkit that got a lot of press a while ago, you were allowed to make three backup copies of a CD, and only three. For more detailed information, I refer you to the almighty Wiki:

[http://en.wikipedia.org/wiki/Digital_rights_management]("http://en.wikipedia.org/wiki/Digital_rights_management")

[quote=Wikipedia]**Digital Rights Management** (**DRM**) is the [umbrella term]("http://en.wikipedia.org/wiki/Umbrella_term") referring to any of several technologies used to enforce pre-defined policies controlling access to software, music, movies, or other digital data and hardware. In more technical terms, DRM handles the description, layering, analysis, valuation, trading, monitoring and enforcement of the usage restrictions that accompany a specific instance of a digital work. In the widest possible sense, the term refers to any such management.[/quote]

---

### Post by srunni on 2006-06-06
I doubt the whole DRM thing will affect Linux, since everything is open source, which means that putting an DRM code in a piece of software would be ridiculously easy to reverse. There has been much action recently in the area of DRM and the MPAA/RIAA (arstechnica.com has some articles about this), however this most likely will not affect Linux. Any DRM put on disc drives, TV tuners can be undone by using software like MythTV. Also, DRM is meant to target the average user and sap them of all their fair-use rights. The "average user" doesn't have Linux; they have MS WIN XP, so we're pretty much safe. But the XP that I run Ubuntu as a virtual OS may be in the group of some of the last DRM-free systems, which is why I will probably end up upgrading the hardware repeatedly instead of buying something new if DRM really takes hold.

---

### Post by Seq on 2006-06-06
[QUOTE=ade234uk]Im a bit behind the times with things. Can someone explain what DRM means, and how this effects Linux?[/QUOTE]
Also, within the context of Linux/X11, DRM is also the [Direct Rendering Manager]("http://dri.freedesktop.org/wiki/DRM")

---

### Post by Stormy Eyes on 2006-06-06
[QUOTE=ade234uk]Im a bit behind the times with things. Can someone explain what DRM means, and how this effects Linux?[/QUOTE]

It means that those bootleg porno videos you downloaded via bittorrent might not play on Linux.

---

### Post by SuperMike on 2006-06-06
[QUOTE=srunni]I doubt the whole DRM thing will affect Linux, since everything is open source, which means that putting an DRM code in a piece of software would be ridiculously easy to reverse. There has been much action recently in the area of DRM and the MPAA/RIAA (arstechnica.com has some articles about this), however this most likely will not affect Linux. Any DRM put on disc drives, TV tuners can be undone by using software like MythTV. Also, DRM is meant to target the average user and sap them of all their fair-use rights. The "average user" doesn't have Linux; they have MS WIN XP, so we're pretty much safe. But the XP that I run Ubuntu as a virtual OS may be in the group of some of the last DRM-free systems, which is why I will probably end up upgrading the hardware repeatedly instead of buying something new if DRM really takes hold.[/QUOTE]

It might be an issue. Imagine if you make something on Linux that installs on Windows and Mac as well. Imagine you do not "sign" it under the DRM with the third-party DRM signature holder (of which I'm sure Microsoft will own a huge stake). When your customers go to install it on Windows, it may give all manner of warnings about the risk of installing non-DRM material. Yikes. That sucks. There goes a huge chunk of the Windows market for your new, great idea. 

And what about making a Linux product that interacts on a port with Windows, such as Samba? What if Microsoft decides to put DRM protection on the TCP/IP ports? If so, they could throw up a dialog saying, "A Non-DRM connection is attempting to get in on your Windows Vista PC through your file sharing. Do you wish to trust this connection?" Yikes, again, there goes your marketshare.

DRM is potentially more bad news than many think. It all comes down to the fine details.

---

### Post by Kernel Sanders on 2006-06-06
[QUOTE=Stormy Eyes]It means that those bootleg porno videos you downloaded via bittorrent might not play on Linux.[/QUOTE]

That gives me an idea! :-k 

*Goes off to download some bootleg porn on uTorrent* :cool: 

;) ;)

---

### Post by prizrak on 2006-06-06
DRM doesn't have much effect on Linux as always it has to do with 3rd party. If iTunes is ever ported to Linux it will still have the DRM module that it does on Windows. Basically if 3rd parties develop DRM'ed software for Linux we will have it. If they do not we won't have it, the kernel itself has support for DRM already (despite what RMS wants) so it's up to the developer to use those API's. 
All in all DRM would make it more difficult for users to migrate as it is possible that it would be impossible to play your collection of audio/video on Linux as it doesn't have the licenses. On the other hand if a 3rd party creates a cross platform player you would be able to transfer the licenses. Could also be the same problem as the Sony Rootkit, if the CD can't install something on your computer it won't work.

---

