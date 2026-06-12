---
title: "Daru2 to TV?"
date: 2008-03-09
forum: System76 Support
---

### Post by dldf365 on 2008-03-09
I am currently looking to buy a new laptop and, since I prefer Linux and small companies, would like to go with System76, specifically, the Darter Ultra.

I have one question about the Darter before I make a purchase:

**Does the Darter Ultra currently support output to a TV (for watching movies, mostly)?** I realize it has a VGA out so I am wondering if the card (and Ubuntu) supports a VGA to S-Video or VGA to Composite (RCA) video setup.

I know that this is usually done through a bus on the video card, but that it is not always recognized by Linux.

I did some research on the card and the Darter but couldn't really find anything conclusive.

Thanks a lot for the help!

---

### Post by thomasaaron on 2008-03-10
I'm not sure I follow.

The DarU2 had a vga out, which is supported. A VGA to DVI adapter should work fine. But, as for any onboard hardware (or software) that converts the VGA signal to an authentic DVI signal, I'm not aware of any.

---

### Post by dldf365 on 2008-03-10
Hmmm,

Ok, I guess I am really asking about the Intel GMA X3100 graphics card that is (I think) in the Darter. Does this card support a TV out through the VGA port?

In other words, could I simply use a cable like this:
[http://www.parts4pc.com/ConnectorsandAdapters/ExternalPCCables/SVGA/AUD-2350.html](http://www.parts4pc.com/ConnectorsandAdapters/ExternalPCCables/SVGA/AUD-2350.html)
to connect it to a standard TV, or would I need some sort of converter box?

Thanks again.

---

### Post by thomasaaron on 2008-03-10
I've never tested that, but it *should* work fine.
You'll no doubt have to twiddle with xorg.conf to get it just right, though.

---

### Post by dldf365 on 2008-03-10
Right, these things always take some time with the xorg.conf.

Thanks a lot for the help.

---

### Post by john.ennew on 2008-03-12
Hi,

My mainboard has a X3100 GFX and an SVideo out but I have not been able to get the TV out working.  

If you are sucessful, please let me know how you manged it!

Also, I believe the X3100 has problems with 3D applications as I can't get Compiz to work with it either. This thread has some discussion on these problems:

[http://ubuntuforums.org/showthread.php?t=674643&highlight=x3100](http://ubuntuforums.org/showthread.php?t=674643&highlight=x3100)

---

### Post by thomasaaron on 2008-03-12
This should get your desktop effects working:
[http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

---

### Post by reh4c on 2008-03-12
On Hardy Alpha 5, Compiz with desktop effects was "automagically enabled" with a couple of clicks under desktop appearance.  However, a kernel and package update from last night left me with a black screen after login.  Oh, well!!!  Hopefully, these issues are fixed by the beta release.  Hardy Heron final is scheduled for release at the end of Apr--maybe some of our problems with the Intel card will be fixed by then.  Good luck!

---

