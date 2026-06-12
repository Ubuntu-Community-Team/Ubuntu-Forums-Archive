---
title: "Dell dual monitor issue"
date: 2007-10-30
forum: Windows
---

### Post by DouglasAWh on 2007-10-30
I'm familiar with dual monitor issues in Linux, but having these problems in Windows is new to me.  Of course, I think Vista is mostly a piece of crap, so this just furthers that comparison with XP.  Anyway....

I have an Optiplex 755 with an ATI Radeon HD 2400 Pro.  My ATI Catalyst version is 2007.0928.*  My Video BIOS is 113-B17002-108.  My overall BIOS is A3.  My driver version is 8.421.* and the driver date is 9/28/07 and the Digital siger is "microsoft windows hardware compatibility publish..."  The name runs off the window.  I have an Acer Monitor and a Dell monitor. The Dell is running on the DVI from a DVI/VGA splitter and the Acer is on the VGA side.  I have tried two different splitters.  I have looked in the BIOS configuration.  Nothing seems to help.  Are there any known issues with driver/BIOS issues or this video card and DVI/VGA splitters?  Would more information on the monitors be helpful?

Thanks!

---

### Post by dca on 2007-10-30
Do these monitors work together in Linux?  If I'm thinking of the same card I think it has two DVI outs on the card itself?  If that's the case than each of the flat panel monitors need to support DVI in, not VGA D-SUB15...  Not sure if even splitters would work on that card...  sorry...

---

### Post by DouglasAWh on 2007-10-30
This has DVI and S-video and that's it.  Not sure about Linux.  I haven't tried it.

---

### Post by mechakisc on 2008-03-28
> **DouglasAWh said:**
> This has DVI and S-video and that's it.  Not sure about Linux.  I haven't tried it.

ACTUALLY

The video card has a DVI-I connector and an S-video connector. The DVI-I connector pushes both (either?) digital signal or analog signal. See the [relevant]("http://en.wikipedia.org/wiki/Dvi") Wikipedia page (or any number of other resources) for more information.

I spite of Dell's claims, I'm not confident this card can run two monitors under Vista. Certainly it will not run two DVI monitors. Based on my experience, it ought to run one DVI and one SVGA monitor with no problem, but that doesn't seem to be the case.

My 755 and 2400 came with a Y adapter, with DVI-I male that plugs into the card, a DVI-D female and an SVGA female out to monitors. Either works fine; both do not seem to work. I've tried various drivers - including the latest from both ATI and Dell's web sites - and contacted Dell tech support, to no avail.

You didn't ever happen to find an answer to this problem elsewhere, did you? Because I've just started working on it.

Incidentally, if you plug and of DVI-D, DVI-A, or DVI-I into the back of this video card, assuming that your monitor supports it on the other end, you'll be able to run A monitor. That's Digital, Analog, and Integrated (both a digital and an analog signal).

My apologies if any part of this is very basic information - I've just had a need to learn it today, and regurgitating it is pretty inevitable. :)

---

