---
title: "how do we poke devs on long-opened bugs?"
date: 2007-04-12
forum: The Cafe
---

### Post by Brunellus on 2007-04-12
My local LUG mailing list has been exercised lately over this bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/9068](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/9068)

and as the Ubuntu kid I've just caught some heat from a user who complains that without serial mouse support, he has no X.  

This isn't your average blinking 12 user, mind you, but it did get me thinking:  this bug has been open for over two years, with no real resolution, and reports of things working properly in Knoppix.  How can we nudge the developers to fix this bug?  Is there some sort of "ancient bug cleanup team?"

---

### Post by bonzodog on 2007-04-12
I would imagine you would need to post to one of the mailing lists about it, though I am not sure which one.

---

### Post by salsafyren on 2007-04-12
Good question.

I think the devs just want to close such bugs, because they do not have the manpower to fix them.

It could be nice if Ubuntu could make updates for old releases but then how would they have time to develop the new release?

I think always focusing on the new releases will hurt Ubuntu in the long run (lower quality releases) but it will advance the OS faster.

Do we need more developers?

---

### Post by Brunellus on 2007-04-12
> **salsafyren said:**
> Good question.

I think the devs just want to close such bugs, because they do not have the manpower to fix them.

It could be nice if Ubuntu could make updates for old releases but then how would they have time to develop the new release?

I think always focusing on the new releases will hurt Ubuntu in the long run (lower quality releases) but it will advance the OS faster.

Do we need more developers?
the bug remains open because it is not fixed in subsequent releases--if you read the comments on the bug, it remains open in Feisty.

---

### Post by koenn on 2007-04-12
The bug will cease to be a bug the moment serial mice become obsolete. Give it another year or so  :)

And I suppose that goes for lots of not-so-critical bugs : given enough time, they'll cease to be a problem

---

### Post by Brunellus on 2007-04-12
> **koenn said:**
> The bug will cease to be a bug the moment serial mice become obsolete. Give it another year or so  :)

And I suppose that goes for lots of not-so-critical bugs : given enough time, they'll cease to be a problem
the fix is already in Knoppix, apparently.  That's what makes it irritating;  there's no developer statement as to *why* they can't or won't fix it--they just haven't gotten around to it.

---

### Post by koenn on 2007-04-12
Well, maybe the think it's just not worth the trouble, since serial mice are obsolete - or so they think. 

I wonder how hard this would actualmly be - what if one could just check how knoppix handlles it (these guys are really good with hardware detection), make a patch, and go "here's a fix for that bug, could you add it to the package ?"
But I wouldn't know where to start looking ...

---

### Post by salsafyren on 2007-04-12
Even though the bug has a patch attached, it does not necessarily mean that the devs will fix it.

If they have other priorities, it would be nice to know so.

---

### Post by az on 2007-04-12
> **Brunellus said:**
> the fix is already in Knoppix, apparently.  That's what makes it irritating;  there's no developer statement as to *why* they can't or won't fix it--they just haven't gotten around to it.

It would seem to me that this is an upstream Xorg problem.  There are only a handful of developers that work on Ubuntu.  Most of the work is done by upstream.

What version of Knoppix was used by the person who left that comment?  Does knoppix still use a 2.4 kernel and Xfree86?  I am not up on the latest version, but it still did last year!

That makes it a completely different operating system.  And I would be interested in knowing if the most current version of Knoppix has a working serial mouse with Xorg.

---

### Post by koenn on 2007-04-12
> **az said:**
> It would seem to me that this is an upstream Xorg problem.  
Don't think so. I had a look at mdetect - the debian tool to detect mice ; I assume Ubuntu uses it too and probably Knoppix as well althoug they've been know to borrow hardware detection tools from RedHat as well.

mdetect can produce "output appropriate for XFree86 4.x configuration" and returns error codes such as 0 (success), 1 (error occurred), 2 (no mouse found) so presumably the output is captured and written to xorg.conf. It should be fairly easy to check for errorcode '2' and start a small "assumeSerialMouseAndDealWithIt" routine
I suppose that sort of stuff is at installer level, so nothing to do with Xorg. Bedides, the comments in the bug report indicate that IF a serial mouse is detected, X is configured accordingly and stuff works. Detecting serial mice is the actual hard part, not dealing with 'no mouse found' is the bug.

---

### Post by prizrak on 2007-04-13
I suggest using a pretty big pole. Some bugs are pretty rediculous as far as how long they've been open vs how easy to fix. It took a year to get wacom-tools installed by default (how difficult was that seriously?). I have opened a bug about Acer hotkeys months ago and provided both a link to the kernel module required and the keycodes along with corresponding actions. Yet the package haven't even made it into the repos much less the main kernel free. This bug actually leads to unusable bluetooth because the default is off and to turn it on it needs the driver for the keys. (was also filed).

---

### Post by az on 2007-04-13
> **koenn said:**
> Don't think so. I had a look at mdetect - the debian tool to detect mice ; I assume Ubuntu uses it too and probably Knoppix as well althoug they've been know to borrow hardware detection tools from RedHat as well.

mdetect can produce "output appropriate for XFree86 4.x configuration" and returns error codes such as 0 (success), 1 (error occurred), 2 (no mouse found) so presumably the output is captured and written to xorg.conf. It should be fairly easy to check for errorcode '2' and start a small "assumeSerialMouseAndDealWithIt" routine
I suppose that sort of stuff is at installer level, so nothing to do with Xorg. Bedides, the comments in the bug report indicate that IF a serial mouse is detected, X is configured accordingly and stuff works. Detecting serial mice is the actual hard part, not dealing with 'no mouse found' is the bug.

Ubuntu uses dbus and HAL.  Mdetect is old technology.

> **prizrak said:**
> I suggest using a pretty big pole. Some bugs are pretty rediculous as far as how long they've been open vs how easy to fix. .... Yet the package haven't even made it into the repos much less the main kernel free. This bug actually leads to unusable bluetooth because the default is off and to turn it on it needs the driver for the keys. (was also filed).


You have to realize that not just anything can go into the kernel.  What makes it into the main kernel tree is up to the kernel developers, and not Ubuntu.  What Ubuntu provides on top of that is up to the technical board.  If a kernel module or patch breaks other stuff, changed the kernel's ABI or is not yet stable, it just simply can't go in.

This is probably another reason why tools like automatix, which can bring in these patches, often end up breaking your system.

---

### Post by koenn on 2007-04-13
> **az said:**
> Ubuntu uses dbus and HAL.  Mdetect is old technology.

hm ... I Looked at mdetect because it was referred to in follow up comments to that 2 year old bug report. And is dbus not more oriented to hot-plugged peripherals, where a serial mouse would be screwed tightly on to one of the serial port connectors ?
Anyway, I don't think i understand the debian (/ubuntu) installer well enough to fix this myself. On the other hand, it should be fairely easy for a setup routine to notice that no mouse was detected / is (apparently) present and then assume it must be an undetected serial mouse and act accordingly ?

---

### Post by prizrak on 2007-04-13
> **az said:**
> Ubuntu uses dbus and HAL.  Mdetect is old technology.




You have to realize that not just anything can go into the kernel.  What makes it into the main kernel tree is up to the kernel developers, and not Ubuntu.  What Ubuntu provides on top of that is up to the technical board.  If a kernel module or patch breaks other stuff, changed the kernel's ABI or is not yet stable, it just simply can't go in.

This is probably another reason why tools like automatix, which can bring in these patches, often end up breaking your system.

While I do agree with that, however I am using the driver and it's not screwing anything up. I understand that not everything can be in the kernel but if it were at least in the repos I would be much happier. As it stands now I have to look for a *.deb of it if I'm reinstalling.

---

### Post by 23meg on 2007-04-25
[QUOTE=Brunellus]How can we nudge the developers to fix this bug? Is there some sort of "ancient bug cleanup team?"[/QUOTE]

You can subscribe someone you think will be suitable for the job, or a team who's responsible for the software and/or can fix the bug. Click "Actions / Subscribe someone else" on the left menu.

---

### Post by matthekc on 2007-04-25
how about one of those bug bounties for non current ubuntu developers might draw new people in old people back.

---

