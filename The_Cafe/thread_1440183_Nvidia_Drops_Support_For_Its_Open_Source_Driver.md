---
title: "Nvidia Drops Support For Its Open Source Driver"
date: 2010-03-27
forum: The Cafe
---

### Post by Dayofswords on 2010-03-27
[http://hardware.slashdot.org/article.pl?sid=10/03/26/2240250](http://hardware.slashdot.org/article.pl?sid=10/03/26/2240250)

the slashdot post
> "While Nvidia is not open-source friendly (despite [public outcries]("http://www.opentheblob.com/") over the years), they have traditionally supported the [xf86-video-nv driver]("http://cgit.freedesktop.org/xorg/driver/xf86-video-nv/") to provide basic mode setting support and other basic functionality. However, with the 'Fermi' and future products, even that open-source support will cease to exist. Nvidia has announced they are [dropping this open-source support for future GPUs]("http://www.phoronix.com/vr.php?view=14714") and really ending it altogether. Nvidia's recommendation is to just use the generic X.Org VESA driver to navigate their way to nvidia.com so that they can install the proprietary driver. Fortunately there is the [Nouveau project]("http://nouveau.freedesktop.org/wiki/") that provides a 2D and 3D video driver for Nvidia's hardware, but Nvidia fails to acknowledge it nor support their efforts in any form."

and i was thinking a getting a card someday....

EDIT: not meaning i'm not choosing them because of this, but its kinda of a "aww..." moment
fine with the closed source version(i hear good things on its performance)

---

### Post by gnomeuser on 2010-03-27
Given their stance on open source I think this makes sense for them. They get to focus on their proprietary driver, we focus on obsoleting it with Nouveau.

the nv driver is intentionally obfuscated, only supports very basic 2D functionality (e.g. it doesn't do xv acceleration). It is by and large entirely replaced today by Nouveau which has a wider support range.

I still would avoid nvidia cards if I could, that being said, due to the price/performance my primary machine is powered by their ION product.

---

### Post by Paqman on 2010-03-27
They may not mention it, but i'm sure they're well aware of the state of Nouveau development. Now that it has progressed to the point where major distros like Ubuntu are rolling it out as default, nv becomes a bit pointless.

---

### Post by forcecore on 2010-03-27
i always use nvidia .run installer to install driver, very simple.

---

### Post by FuturePilot on 2010-03-27
> **Dayofswords said:**
> 
and i was thinking a getting a card someday....

So now you're not just because they're dropping support for that crappy obfuscated 2D driver? With Nouveau as mature as it has gotten I don't think dropping the 'nv' driver is that big of a deal. But never mind that Nvidia cards with the proprietary driver still beat the pants off of anything else under Linux in just about every way possible...

---

### Post by themarker0 on 2010-03-27
Does it really matter if its open source, as long as their *is* a driver?

---

### Post by MooPi on 2010-03-27
I'm curious if any of you are using the Nouveau driver and your impressions?My main Linux computer is an Openbox set up and have always used the xorg driver without issue. Am just wondering if the Nouveau driver would be of any benefit ?

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-03-27
I am extremely happy with nouveau. It works perfectly, the only thing that it lacks is 3d(i understand that we will have it soon) and vdpau, but i don't know if that is ever possible with an open source driver.
 I dual boot for some stuff and games, so for me this is the best choice.

---

### Post by sertse on 2010-03-27
And nothing of value is lost.

If you are using nvidia you have 2 options. The real closed driver, which has better performance anyways.

Or you'll be using the nouveau drivers, which is more "floss" to make you purists more giddy, and which distros are already switching to anyway, since it's now to a point that it's better than nv....

---

### Post by swoll1980 on 2010-03-27
I don't see why this is a problem. I use the closed source driver. For all that have a problem with that, they can use the reverse engineered driver.  Which imo is far better then the crappy one NVIDIA put out.

---

### Post by jflaker on 2010-03-27
I don't mind "proprietary" drivers for proprietary hardware...as long as they keep offering a driver for Linux....Open Source would be great in an ideal world, but to protect their intellectual property, keeping the driver closed makes sense....it is a dog eat dog world in electronics, so if the open source would reveal the underlying hardware, closing the source is OK.

---

### Post by JDShu on 2010-03-27
To be perfectly honest, if you really are a FLOSS enthusiast, you shouldn't be using Nvidia anyway. Back when I had an Nvidia card I used to use the proprietary drivers because they were better. When I got a new computer, I stuck to the Intel chipset and I'll buy an ATI card when I can afford it.

---

### Post by swoll1980 on 2010-03-27
> **JDShu said:**
> To be perfectly honest, if you really are a FLOSS enthusiast, you shouldn't be using Nvidia anyway. Back when I had an Nvidia card I used to use the proprietary drivers because they were better. When I got a new computer, I stuck to the Intel chipset and I'll buy an ATI card when I can afford it.

Intel should make a PCI express video card.

---

### Post by MooPi on 2010-03-27
> **JDShu said:**
> To be perfectly honest, if you really are a FLOSS enthusiast, you shouldn't be using Nvidia anyway. Back when I had an Nvidia card I used to use the proprietary drivers because they were better. When I got a new computer, I stuck to the Intel chipset and I'll buy an ATI card when I can afford it.
  Thats all good and well but are the ATI drivers up to snuff? I read snippets that ATI's driver has problems on the forum.

---

### Post by JDShu on 2010-03-27
> **MooPi said:**
> Thats all good and well but are the ATI drivers up to snuff? I read snippets that ATI's driver has problems on the forum.

I've heard its improving rapidly, though that is really besides the point. If you want a graphics card that works well in Linux by all means, get Nvidia. All I'm saying is that getting Nvidia and then using the Nouveau drivers is not really supporting FLOSS. If you're just going for practicality then all power to you.

---

### Post by Dayofswords on 2010-03-28
> **FuturePilot said:**
> So now you're not just because they're dropping support for that crappy obfuscated 2D driver? With Nouveau as mature as it has gotten I don't think dropping the 'nv' driver is that big of a deal. But never mind that Nvidia cards with the proprietary driver still beat the pants off of anything else under Linux in just about every way possible...

no, i wasnt not going to get one i'm still thinking of what to get in the future, and this just could put a small damper on nvidia as a choice

i'm fine wit propriety things if its better (unless it costs something, i'm cheap that way), i go with what works. just becuase they wont work on the driver anymore doesnt mean i'm not considering them, i hear they are quite good

---

### Post by Paqman on 2010-03-28
> **JDShu said:**
> To be perfectly honest, if you really are a FLOSS enthusiast, you shouldn't be using Nvidia anyway.

I think the issue is about there being a driver that distros can include in their build. A LiveCD is only ever going to have access to the open source driver, and even folks who install the proprietary one will want their system running at a decent resolution while they get it installed.

---

### Post by 3rdalbum on 2010-03-28
I'd be surprised if anyone using Ubuntu really notices the difference. We're switching to Nouveau by default, which actually offers more features than Nv.

People will only notice the difference if they attempt to modify their Xorg.conf, or if they go and play a video from the live CD :-)  Or if in future Ubuntu versions, they realise that Compiz is running out-of-the-box.

---

### Post by del_diablo on 2010-03-28
Who cares for Nvidia? Nouveau is not getting enough information to get any development, its slow.
We got proper 3D accel out of the box in the radeon driver anyhow by summer, the radeonhd driver has gotten further on actually implenting most of the 3D.

---

### Post by Eclipse. on 2010-03-28
No big deal, nvidia knows that the big distros are now shipping nouveau.Its worth pointing out that nvidia stopped active development on the driver a while ago and were only fixing bugs when they appeared until now.

---

### Post by gnomeuser on 2010-03-28
> **del_diablo said:**
> Who cares for Nvidia? Nouveau is not getting enough information to get any development, its slow.


Nouveau on my ION system begs to differ, I have 3D acceleration. It runs Compiz and is stable. It's even smoother than the proprietary driver for certain every day tasks.

---

### Post by Eclipse. on 2010-03-28
> **gnomeuser said:**
> Nouveau on my ION system begs to differ, I have 3D acceleration. It runs Compiz and is stable. It's even smoother than the proprietary driver for certain every day tasks.

He has got a point though, Nvidia's refusal to release documentation is making things alot harder for the Nouveau guys.

---

### Post by 3rdalbum on 2010-03-28
> **del_diablo said:**
> Who cares for Nvidia? Nouveau is not getting enough information to get any development, its slow.
We got proper 3D accel out of the box in the radeon driver anyhow by summer, the radeonhd driver has gotten further on actually implenting most of the 3D.

What about getting people's Radeon X9600 graphics cards actually, like, working? To a desktop? Can the RadeonHD driver do that yet? We seem to get a lot of people at Ubuntu Forums who can't get this happening.

---

### Post by alexfish on 2010-03-28
> **forcecore said:**
> i always use nvidia .run installer to install driver, very simple.

Not for Newbies, we need desktop solutions to all drivers

however I feel graphic Board Manufactures May in the future force an issue on [B]Integrated graphics solutions 

[http://en.wikipedia.org/wiki/Graphics_processing_unit](http://en.wikipedia.org/wiki/Graphics_processing_unit)
[/B]

---

### Post by del_diablo on 2010-03-28
> **3rdalbum said:**
> What about getting people's Radeon X9600 graphics cards actually, like, working? To a desktop? Can the RadeonHD driver do that yet? We seem to get a lot of people at Ubuntu Forums who can't get this happening.

Huh? Wrong driver, and it is actually suppose to work Out of da box. My sapphire 9800pro runs out of the box, so i dunno what is causing you problems.
ati-driver = everything older than x1300 or something
radeon = everything newer than that

---

### Post by Lightstar on 2010-03-28
As long as there's one type of driver, wether it's open source or closed, and it's free, I'm fine.

---

