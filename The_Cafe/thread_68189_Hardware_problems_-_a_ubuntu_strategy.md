---
title: "Hardware problems - a ubuntu strategy?"
date: 2005-09-22
forum: The Cafe
---

### Post by petr on 2005-09-22
A proposal: when someone says "the xxxx doesn't work on my machine under ubuntu" I am beginning to suspect that is because the xxxx wasn't plugged in when they ran the install program and so the hardware detect didn't load the module.

Is that true?

If so, perhaps the formal ubuntu response is to re run the hardware detection process.  Is that possible with the current setup?

Petr

---

### Post by mlomker on 2005-09-22
> If so, perhaps the formal ubuntu response is to re run the hardware detection process.  Is that possible with the current setup?


Not really.  At this point in linux's development installing drivers for devices can be very difficult.  If you look at some of the threads regarding people installing 3D video drivers then you'll see that.  Things like webcams are a pain and digital cameras need the right software.

---

### Post by poofyhairguy on 2005-09-22
[QUOTE=petr]A proposal: when someone says "the xxxx doesn't work on my machine under ubuntu" I am beginning to suspect that is because the xxxx wasn't plugged in when they ran the install program and so the hardware detect didn't load the module.

Is that true?
[/QUOTE]

Not always. Most of the time its because the company that made that product refuses to help Linux with drivers (by making them themselves or opening their specs).

Many webcams, wireless cards, other accesories just don't have Linux drivers. Nothing Ubuntu can do about that.

---

### Post by petr on 2005-09-24
OK it won't work all the time - if there is no driver available - sure.   But if the driver is available, surely it is going to resolve all the dependencies.   A one click answer to "can this work without me writing a driver?"

As a worked example,  any ideas why my i.Link port adapter won't give me an external monitor? :-) 

Petr

---

### Post by newbie2 on 2005-10-12
"I'm not trying to knock Novell. Overall, Suse is a great distribution, and Ubuntu -- my other favorite desktop Linux -- has yet to produce a version that will even install on my home PC.
Let's assume, rather, that my hardware is the problem. Where can the average user, let alone IT managers, buy desktop Linux systems that just work? Finding a hardware combination that's fully Linux compatible can be a research project daunting enough to curb the enthusiasm of even the most ardent hobbyist. "
[http://www.cio.com.au/index.php/id;781250180;fp;4;fpid;21](http://www.cio.com.au/index.php/id;781250180;fp;4;fpid;21)

---

### Post by blueturtl on 2005-10-12
> Where can the average user, let alone IT managers, buy desktop Linux systems that just work? Finding a hardware combination that's fully Linux compatible can be a research project daunting enough to curb the enthusiasm of even the most ardent hobbyist.

I don't know about you guys, but this sounds like a gap for a business. ;) 

I've been thinking about starting my own firm at an older age and I would not be selling or for that matter repairing Windows PCs. A completely working desktop Linux system can be accomplished, it just takes knowledge in what components are to be picked. I initially just built my system for top-notch quality, and it shows - Ubuntu has detected and properly configured every single device on my system! It's people using marginal or crappy hardware that have issues (also ones, who'se manufacturer is Linux-hostile have this problem). Sure, I had no way of knowing when I picked an nVidia card that it would prove lucky in my later Linux endevours, but for example's sake, maintaining a list of quality hardware and manufacturers can't be that hard if you're into it eh?

---

### Post by mcduck on 2005-10-12
[QUOTE=blueturtl]I don't know about you guys, but this sounds like a gap for a business. ;) 

I've been thinking about starting my own firm at an older age and I would not be selling or for that matter repairing Windows PCs. A completely working desktop Linux system can be accomplished, it just takes knowledge in what components are to be picked. I initially just built my system for top-notch quality, and it shows - Ubuntu has detected and properly configured every single device on my system! It's people using marginal or crappy hardware that have issues (also ones, who'se manufacturer is Linux-hostile have this problem). Sure, I had no way of knowing when I picked an nVidia card that it would prove lucky in my later Linux endevours, but for example's sake, maintaining a list of quality hardware and manufacturers can't be that hard if you're into it eh?[/QUOTE]You too? I haven't even started yet and already there is a local competitor? :D

No, i suppose i won't start a company of my own, as business sure isn't my thing. But if somebody else would do the boring stuff with money this would probably be a great business plan..

---

### Post by Lord Illidan on 2005-10-12
I'm not sure.. I would backup anyone who made open source sound card drivers.. that's for sure.. which are better than ALSA, and have greater support for surround sound..

However, as regards driver support, I am quite happy in Ubuntu. The only thing which cannot work is the IR connection between an IR dongle and my phone, and I use that so sparingly, if it all, that I can do without it quite happily.

The trick is to use non exotic hardware, and at the same time, no winmodems, lol...

---

### Post by Pablo_Escobar on 2005-10-12
Heh, I've been reading this forum for quite a long time before registering and I thought there must be something wrong with my computer.

Everything is perfectly fine with my Ubuntu, everything is working perfectly, I just did some application tweaking and that's it. Nothing some googling or searching forums can't fix :)

---

### Post by blastus on 2005-10-12
Speaking of modems. The madness of trying to get modems to work on Windows drove me to purchase an expensive PCI Lucent "winmodem" that said it was compatible with various Windows versions and Linux about 5-6 years ago.

---

### Post by thieummm on 2005-10-12
Hi guys,

I have made a new thread which might be of interest:

[http://www.ubuntuforums.org/showthread.php?t=74573](http://www.ubuntuforums.org/showthread.php?t=74573)

This is about making a compatible hardware database application / web-base engine (think [http://hardware.ubuntu.com)](http://hardware.ubuntu.com))...

Of course this will help only when buying new hardware...

---

