---
title: "Can people with electronics knowledge make their own hardware?"
date: 2007-02-09
forum: The Cafe
---

### Post by presbp on 2007-02-09
I was watching a video that was a parody of the "I'm a PC, I'm a Mac" where the Linux guy who looks [stereotypically] like the nerdy programmer Boris from the Bond movie "Goldeneye" PC and Mac were talking and then he started annoying them by saying how you can run any hardware on Linux.

He then said that if you have enough electronics know-how you can made your own hardware and make a drive for it.  If you have enough electronics hardware can you make your own hardware without spending a fortune.. like buying a circuit board and some capacitors, etc. an d saudering and what-not?

I am currently waiting for a SATA drive so that I can boot and build my own Linux distro from the ground up using Linux From Scratch LiveCD and it would be really cool to be able to make your own hardware.

---

### Post by IYY on 2007-02-09
Depends on the kind of hardware. Modern hardware is very complex in design, and even the best engineer couldn't solder it all together (much of it is done by machines).

---

### Post by presbp on 2007-02-09
what kind of hardware would be possible?

---

### Post by IYY on 2007-02-09
Of the parts inside a PC, I think the very best you could aim for is a network card, and even that won't be easy at all. If you just want to build geeky gadgets --- things like motion sensors, motorized systems controlled by the computer... That's possible and not even too difficult (Linux is a very good OS to write drivers for).

---

### Post by presbp on 2007-02-09
well if I want to build some kind of external mechanism or motion sensor what would be a few cool things I could create?

---

### Post by macogw on 2007-02-09
Watch the security one too.  They're on TrueNuff.tv  "I'm BSD, I'm not Linux!"

---

### Post by Fascination on 2007-02-09
> **presbp said:**
> well if I want to build some kind of external mechanism or motion sensor what would be a few cool things I could create?

Well, you've just listed one - motion sensor :P I guess you could make some form of remote adjustable pivot which you could then mount a webcam on and direct where you look. Its a bit hard to answer the question when we dont know how much you know about electronics :)

---

### Post by slimdog360 on 2007-02-09
Grab a usb interface board and see what you can come up with. We do it at work sometimes, one such design comes to mind when measuring the speed of a drum rolling around (to measure the velocity, acceleration etc). The is an inductive proximity sensor which 'counts' little metal bits on the side of the drum passing by, the sensor is then hooked up to a small circuit with a transistor, acting as a switch. Anyway, each time one of these little metal bits passes the sensor a pulse is now sent to the usb interface board, which sends it to the computer, which a computer program can interpret whats going on.

Of course we have things called 'PLCs' which can do this sort of thing automatically among being able to do other things. But this such instance was a separate design for something a little different so it was just easier to do it this way.

The usb interface boards are heaps easy to use, it will have a few analoge/digital inputs and outputs with a usb port which can be connected to your computer. The board should come wih drivers for it and also some software which can give you an idea how it all works. 

Interfacing with the parallel port (the big purple one on the back of your computer) is extremely easy to program. There should be a few links around somewhere. Thats just a cheaper way of doing things, but not as fun.

So now youve got an idea of how to control things via a pc so go and think up some cool ideas. That motion sensor sounds so easy if you really think about it. ( of course you buy the sensor, no design and build it. If your interested in this sort of thing you should consider a career in electrical engineering, every engineer I have ever met loves their job and gets paid quite nicely for doing it.

Here is what I was talking about with the usb board [http://www.apogeekits.com/usb_interface.htm]("http://www.apogeekits.com/usb_interface.htm")

---

### Post by PatrickMay16 on 2007-02-09
If you had the knowledge, surely you could just buy a microprocessor and put it together with some other stuff on a circuitboard and make something?

---

### Post by slimdog360 on 2007-02-09
> **PatrickMay16 said:**
> If you had the knowledge, surely you could just buy a microprocessor and put it together with some other stuff on a circuitboard and make something?

ah, but you have to know either c or assembly to program the microprocessor. Which is a pain in the ***. But you are right though, it is very possible to do.

---

### Post by presbp on 2007-02-09
I don't really know much about those sort of things but I am starting to learn a variety of stuff specifically computer knowledge, and I would assume that electronics knowledge would fit nicely into that. 

What would I need to learn to do a basic thing like a motion sensor that would control a camera or something of that sort?

---

### Post by slimdog360 on 2007-02-10
go down to your electronics store and pick up a book or two on basic electronics.

---

