---
title: "Ever get the idea software devs don't always TRY their software?"
date: 2008-10-08
forum: The Cafe
---

### Post by SomeGuyDude on 2008-10-08
Honestly, I sometimes get the idea that in their zeal to put out a piece of software, some of these guys don't bother to actually take their creation for a whirl. Yes, I have an example in mind.

I installed Cairo Dock. It's very nice. However, there are some applets that make a little popup, such as the System Tray and Terminal applets. No problem, it's useful. Click on the "systray" applet and you get little bubble with your system tray icons.

Problem: it won't go away without doing a keyboard combination. It's the world's most simple GUI concept. Click an icon to make a popup appear, click it again to make it go away. Or there's an X icon to make it close. Or if you click somewhere else on your screen it goes away. I've never run into a situation where there was no method, via the mouse, to close a window. I cannot fathom that anyone involved in the project could use the thing, come across this feature, and say "why yes, this is perfectly reasonable." 

Anyone else run into things like this in software they've tried out?

---

### Post by LaRoza on 2008-10-08
I've had my own code suffer from that.

Programmers are the worst people to test the software they write.

Users, are the worst people to use it, but they will find any error, even given years of review by the best programmers. Users are like that.

---

### Post by myusername on 2008-10-08
of course they dont...thats what beta testers are for :)

---

### Post by SunnyRabbiera on 2008-10-08
Well the good thing is if its an open soruce app most of the time the developers listen.

---

### Post by onero on 2008-10-09
Yeah, I find the developer of cairo-dock is pretty responsive; he implements new features really quickly. I'm not sure if he creates the applets as well though.

---

### Post by CrazyArcher on 2008-10-09
> **myusername said:**
> of course they dont...thats what beta testers are for :)

...Not to mention the alpha-testers.

---

### Post by bash on 2008-10-09
Reminds me of a bug I filed against gnome-do today. Person A writes the program. Person B writes some fancy localisation. And noone checks if the program still works if you use the non-english version.

---

### Post by phrostbyte on 2008-10-09
In the free software world, the users take on the role of QA. :)

Sad truth. 

Developers make better time spent developing software, not testing or finding bugs. It is very time consuming task and it can be done by other people better. Just keep in mind as a user you can submit bug reports and you are actually helping improve the software this way, because rarely is the developer always aware of issues other people are having. It (imo) feels good to the developer because you know you're software is being used if people send it problems with it. :)

---

### Post by Tomosaur on 2008-10-09
It's a common problem.

During the act of developing software, the developer often develops the UI experience according to whatever they'd naturally do, or whatever the toolkit allows them to do easily. Little things often get overlooked because the developer would simply never think to code in support for something they would never really do. A lot of the time, for example, things like clicking elsewhere on the screen aren't something that the toolkit makes obvious as a possible scenario (for example, in this case the event would be the notification bubble losing focus - not an obvious thing to support when you're the developer!).

So it's not just a case that the developer doesn't test their own code - it's that the things that users expect to be supported, the developer doesn't necessarily notice it's missing since it'd just never occur to them to try it that way. This is why user feedback is so important to developers, otherwise people just think 'oh, this is broken', when in reality the developer would just never notice something was wrong since they'd never use it the way you want to use it!

I speak from experience - it's the same kind of thing as an artist really (and us musicians get it a lot too!). A fresh persepective will illuminate things which the original artist never noticed or intended. Chalk it up to developers only being human too!

---

### Post by fabounet on 2008-10-10
but developpers also write manual and readme for end-users, and in the case of Cairo-Dock, you have a little description of each of the applets in the config panel, just next to the button you use to activate one.
if you had took 10s to read it, you would have notice that the dialog appears or come to foreground with right click, and disappear with a middle click.

and think that if devs had to test any line of their code, they would just spend too much time on it and not on coding
beta-testers are here for that, not to mention users that can fill a bug report easily on the forum (cairo-dock.org in this case)

that's open-source.

---

### Post by viriatus on 2008-10-10
> **phrostbyte said:**
> In the free software world, the users take on the role of QA. :)

Sad truth. 

Developers make better time spent developing software, not testing or finding bugs. 

Developers **should** test and find bugs, it's their job. Yes, this a big problem in the FOSS world and that's why most FOSS sucks balls. And people wonder why everyone is still using expensive proprietary software.

:confused:

---

### Post by LaRoza on 2008-10-10
> **viriatus said:**
> Developers **should** test and find bugs, it's their job. Yes, this a big problem in the FOSS world and that's why most FOSS sucks balls. And people wonder why everyone is still using expensive proprietary software.

:confused:

Oh ye of little experience!

Proprietary software often has more bugs and more drastic ones than open source. Sure, if we go by numbers, open source problems has more bugs total, but that is because of the superior bug tracking and reporting and that anyone can make a free program.

It isn't a problem for the FOSS world, it is just that in the proprietary world people accept it.

---

### Post by GeneralZod on 2008-10-10
> **viriatus said:**
> Developers **should** test and find bugs, it's their job. Yes, this a big problem in the FOSS world and that's why most FOSS sucks balls. And people wonder why everyone is still using expensive proprietary software.

:confused:

Even with well-funded, proprietary software, developers very rarely do anywhere near the majority of testing - it's handed over to the QA department.  Developers develop; QA AQ's.

---

### Post by Irihapeti on 2008-10-10
I imagine (I've never done any) that developing is like writing. Trying to proofread your own writing doesn't work. If you've ever found errors in something that another person has written (and checked), you'll know what I mean.

Another problem that writers have is being too close to their subject. It's very easy to assume, "the reader knows what I'm talking about here", when in fact the reader (or many of them) simply doesn't have a clue what you're on about.

Things, both in coding and in writing, are always going to be discovered by other people, no matter how hard the original creator tries to vet their own work.

---

### Post by shadylookin on 2008-10-10
> **viriatus said:**
> Developers **should** test and find bugs, it's their job. Yes, this a big problem in the FOSS world and that's why most FOSS sucks balls. And people wonder why everyone is still using expensive proprietary software.

:confused:

except that for a lot of FOSS it's not their job but their hobby.

Even in proprietary software there are QA people because QAs are cheaper than developers. 

In the FOSS world users are QA.

---

### Post by Irihapeti on 2008-10-10
I think that users are often QA in the world of proprietary software, too. Crash reports sent back to MS, anyone? Or have I been a Linux-only user for so long that I'm imagining this?

---

### Post by Erdaron on 2008-10-10
I don't think bugs are the issue. I've seen programs that are written correctly - they do what they're supposed to - but controls are extremely obtuse and arcane.

I'm currently working on some older instrument control software, and the thing is almost designed to trick you into doing something wrong. The logic behind the interface is completely byzantine. Though I guess it was written in the day it was assumed that if you're going to use a computer, you're going to read a manual first.

(Oddly, a newer version of software designed to control a similar instrument is much easier to figure out, but doesn't work very well.)

---

