---
title: "Pangolin Performance Issues"
date: 2008-12-14
forum: System76 Support
---

### Post by dcajacob on 2008-12-14
My girlfriend just bought a Pangolin Performance laptop (model panp4n).  I have been using Ubuntu for several years and I encouraged her to make the switch.  We decided to try System76 because of the good reviews and competitive price.  We picked an Ubuntu-specific hardware dealer because I felt it would be nice if she had little to no hardware issues out of the box.

Given that System76 ships with a custom-developed driver installer, I assumed that things would work out of the box.  It seems that the webcam does, but my girlfriend wouldn't have figured it out without my help.  Part of the problem is that I can't tell what is actually supported.  Some documentation seems to indicate that the drivers support the fingerprint reader, but I see no support.  I did find instructions on installing it ([http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)), but I didn't want to go forward with them if the driver already had supported it.  Also, it seems like the HDMI port doesn't support audio yet.  Is there work on this?

The biggest issue I have is that there doesn't seem to be much documentation on any of these issues.  For people like my girlfriend, this would be a great help.

---

### Post by thomasaaron on 2008-12-15
> Some documentation seems to indicate that the drivers support the fingerprint reader, but I see no support.

Support for the reader is already built into the driver and works out of the box. Go to Applications > Accessories > Fprint project

Biometrics isn't integrated into Ubuntu very well yet, so the software is beta/experimental.

> Also, it seems like the HDMI port doesn't support audio yet. Is there work on this?

This is being worked on at the Ubuntu level. Seeing as HDMI uses HDCP, Ubuntu developers have found a way to implement the video part of HDMI, but not the audio.

---

### Post by thomasaaron on 2008-12-15
Just got your voice message too. I'll not call since I think I probably answered everything here. Let me know if you need more help.

---

### Post by dcajacob on 2008-12-15
Thanks for the quick response!

I have a few more questions.  I understand that the fingerprint reader is in beta, but is it supposed to work at any level yet?  We just tried it and the app dies every time she tries to enroll a finger.

One thing that may be helpful is that I downloaded the newest driver from [http://planet76.com/repositories/](http://planet76.com/repositories/), 2.2.9 and installed it.  I assume since there is no system-specific tag that your drivers are made to be applied to any system76 machine?

Thanks for your help!

---

### Post by dcajacob on 2008-12-16
She was swiping her finger too fast - a nice easy swipe gets a good image with no crash.  Nice!

---

