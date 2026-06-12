---
title: "Direct3D 10/11 Is Now Natively Implemented On Linux!"
date: 2010-09-22
forum: Wine
---

### Post by newbie2 on 2010-09-22
> Luca Barbieri made a rather significant commit today that adds a state tracker dubbed "d3d1x", which implements the Direct3D 10/11 COM API in Gallium3D. Luca says this is just the initial version, but it's already working and can run a few DirectX 10/11 texturing demos on Linux at the moment. This is not a matter of simply translating the Direct3D calls and converting them to OpenGL like how Wine currently handles it, but is natively implemented within Gallium3D and TGSI to speak directly to the underlying graphics driver and hardware. Thanks to Gallium3D's architecture, this Direct3D support essentially becomes "free" to all Linux drivers with little to no work required.
[http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1](http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1)
:popcorn:

---

### Post by dardack on 2010-09-22
> **newbie2 said:**
> [http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1](http://www.phoronix.com/scan.php?page=article&item=mesa_gallium3d_d3d11&num=1)
:popcorn:


Take what phoronix says with a grain of salt at this time.  They tend to hype things way too much.  First off, IIRC, there was an IRC chat with wine-dev peeps and also a mailing list on wine-devel regarding all this.  Way it seems wine will not be able to just hook into this, the binary from nvidia won't be able to make use of it, and basically it isn't just that simple.

---

### Post by cwwilson721 on 2010-09-22
I am in agreement on "grain of salt". I'd wait for wine to say "Hey! Look! We got it to work! Here's the NEW wine with REAL D3D!"

Until then, it's vaporware.

Hmm, vaporware based on a closed-source, virus and security infested OS...What could go wrong?

---

### Post by AllRadioisDead on 2010-09-22
> **cwwilson721 said:**
> I am in agreement on "grain of salt". I'd wait for wine to say "Hey! Look! We got it to work! Here's the NEW wine with REAL D3D!"

Until then, it's vaporware.

Hmm, vaporware based on a closed-source, virus and security infested OS...What could go wrong?

Windows isn't a virus infested OS, you just don't know how to manage your system properly.

---

### Post by cwwilson721 on 2010-09-22
> **AllRadioisDead said:**
> Windows isn't a virus infested OS, you just don't know how to manage your system properly.
As compared to what? A dead chicken? In that case, you are correct.
STAY ON TOPIC.

---

### Post by oedipuss on 2010-09-23
Follow-up on phoronix : [Wine Devs Have Mixed Feelings Over Direct3D In Gallium3D]("http://www.phoronix.com/scan.php?page=news_item&px=ODYyNw")

What I don't understand is would this work (if it actually gets implemented) on every card, or just those with gallium3d drivers ? So, since nouveau isn't quite game ready yet, is nvidia basically out?

Edit: Nevermind I just noticed the answer above.

---

