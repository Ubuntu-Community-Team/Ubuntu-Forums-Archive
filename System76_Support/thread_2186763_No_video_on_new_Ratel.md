---
title: "No video on new Ratel"
date: 2013-11-08
forum: System76 Support
---

### Post by grizdog on 2013-11-08
Just took my new Ratel out of the box, plugged everything in, and no video.  The computer itself appeared to be coming up - the fan was going and lights were blinking.  But the led on the monitor that indicates a signal didn't even come on.  Without a monitor, it's kind of hard to diagnose much.

One thing that may be of interest, I bought this with an nVidia video card, instead of just using the onboard video.  This is the first time I have ever done that.  Unfortunately, the only monitor I have available at the moment is an old Benq that has an old VGA connector on the end.  There was no VGA port on the nVidia card, so I plugged it into the motherboard.

If that is the problem, can I just find a VGA - DVI cable and plug this monitor into the card?  I know that to take full advantage of the video card I will need something a little newer, but for now, will that work?

Thanks.

Alex

---

### Post by prshah on 2013-11-09
Is the monitor connected to the correct video output? Try switching the monitor input plug between onboard and nvidia output to see if any of the cards give an output.

---

### Post by grizdog on 2013-11-09
OK, it was as we both suspected - I had to connect the monitor to the video card, not the on board video.  I guess those ports are available if I move a jumper or something, but for now they are just not there.

When I turned on the machine, there was no installation script, it just came straight to a login screen.  Just <enter> dropped me into a guest account, and I cannot make an administrative account without giving it an administrative password, and since I haven't set one up, nothing works - including typing in nothing.  I tried dropping into recovery mode but I couldn't set a root password there, either.  Preinstalled Ubuntu is very nice, but I need some way to set up an account.

---

### Post by grizdog on 2013-11-09
I'm marking the thing as solved, since the video problem is solved.  I still can't get the thing to work properly, which is very frustrating for a preloaded machine, but that's life.

---

