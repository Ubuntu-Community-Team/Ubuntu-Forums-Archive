---
title: "What's up with Xorg.conf?"
date: 2007-03-08
forum: The Cafe
---

### Post by mlissner on 2007-03-08
I don't mean to be too much of a punk, but I have to know. Why is it that xorg.conf is such a monolithic, ridiculously complicated, strange and confusing file?

I've just spent the past couple of hours trying to get an external monitor to work on my laptop. My mouse doesn't fully work. Both seem to be centered around the xorg.conf file, which to me seems to make no sense.

It seems like we've figured just about everything else out, more or less, so why is it that this VITALLY important aspect is SO confusingly difficult? Is there a good reason why, or is this just one of those areas that doesn't really work yet?

Any thoughts?

Not too rant too much...I am mostly curious.

---

### Post by PatrickMay16 on 2007-03-08
Programmers don't care as much about usability, I don't think... just as long as they themselves know how to use it, they're satisfied. Though I heard that they're greatly improving this in the latest version of Xorg.

---

### Post by ~LoKe on 2007-03-08
It's difficult because it's vitally important.

I mean, xorg is a serious thing which has a lot of potential to do a lot of different things.  What do you expect?

---

### Post by DoctorMO on 2007-03-08
One of the main reasons behind the apparent 1990s throw back is that X11 development stalled, and almost died. only when X11 changed is license to something most FLOSS people could handle did it fork into Xorg and we are just starting to see the development improvements such as Beryl/Compiz and the next version I hear doesn't have a comfig file in the same manor of speaking.

---

### Post by mlissner on 2007-03-08
> **~LoKe said:**
> It's difficult because it's vitally important.

I mean, xorg is a serious thing which has a lot of potential to do a lot of different things.  What do you expect?

I don't know what I expect, but most things work without too much trouble. With X, something that I agree is vitally important, I'd think it would work really well, so it detects the resolution of your video cards, it detects if you have external monitors hooked up, it detects if you have a mouse with multiple buttons, or a touchpad with a scroll bar. And for all of these things, allows either an obvious config file (like grub.conf, which you can understand with little or no advance knowledge), OR it allows GUI configuration. 

I guess though it sounds like the answer is licensing. Bad licensing until recently.

---

### Post by watson540 on 2007-03-08
it does detect all of that stuff just fine, you just have to tell it to do so. ever heard the command 'dpkg-reconfigure xserver-xorg'? works wonders :)

---

### Post by karellen on 2007-03-08
I think that it really should be a graphical tool for configuring xorg.conf...:)

---

### Post by jdhore on 2007-03-08
> **mlissner said:**
> I don't mean to be too much of a punk, but I have to know. Why is it that xorg.conf is such a monolithic, ridiculously complicated, strange and confusing file?

I've just spent the past couple of hours trying to get an external monitor to work on my laptop. My mouse doesn't fully work. Both seem to be centered around the xorg.conf file, which to me seems to make no sense.

It seems like we've figured just about everything else out, more or less, so why is it that this VITALLY important aspect is SO confusingly difficult? Is there a good reason why, or is this just one of those areas that doesn't really work yet?

Any thoughts?

Not too rant too much...I am mostly curious.

well...i think this answer is 2 fold and i may be able to help you with that external monitor thing as i was mucking with that stuff earlier today.

firstly, i think xorg.conf is so complicated for the fact as kind of "if this looks confusing to you, you're not smart enough to mess with it correctly."
secondly, i believe much like IRCd configs (which i have a lot of experience with) it CAN be modularized by using include lines, but unlike with an IRCd config, to me, that wouldn't feel right or seem optimal.
thirdly, i don't know why the hell all the configuration for mouse stuff is in there...that just confuses me...
All in all, here's how xorg.conf is organized:
Fonts, Modules and misc. stuff
input device configurations (mouse, tablet, keyboard, etc)
Video card stuff
Monitor information

...also, it's certainly A LOT easier than xfree86.conf

---

### Post by ssam on 2007-03-08
because very soon xorg settings will all be auto detected. Xorg 7.2 (which will be in feisty) contains most of the ground work, and in theory can start X without a conf file.

Monitor and input device hot plugging will also be available soon.

have a look at [http://mirror.linux.org.au/pub/linux.conf.au/2007/video/monday/monday_1450_Debian.ogg](http://mirror.linux.org.au/pub/linux.conf.au/2007/video/monday/monday_1450_Debian.ogg) for some details

it would be a bit of a waste of time to write a GUI for configuring X, if it will obsolete by the end of the year.

---

### Post by TheMono on 2007-03-08
The biggest argument against the xorg.conf GUI is if you don't have a working xorg.conf, you can't use a GUI.

---

### Post by karellen on 2007-03-08
> **TheMono said:**
> The biggest argument against the xorg.conf GUI is if you don't have a working xorg.conf, you can't use a GUI.
you're right, I should have thought at this before :). anyway, I never really had any real problems with my xserver in linux, so I never had to manually edit xorg.conf. I guess I'm lucky to run an old and well-supported system :D

---

