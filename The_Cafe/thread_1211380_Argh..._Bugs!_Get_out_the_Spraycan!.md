---
title: "Argh... Bugs! Get out the Spraycan!"
date: 2009-07-12
forum: The Cafe
---

### Post by arture on 2009-07-12
I just went the second time into a bug, where i told Ubuntu to Hibernate and went away. When I came back, the battery was dead empty and the hibernation had not worked.

I need, must, have to and want to work with Ubuntu, but often I run into deadly Bugs like this, that endanger my work, sometimes like here even my hardware. I ask myself first where to rant and scream about it, then who to tell seriously, and third how to fix it.

Maybe a Buglist for things like that would be great? Where we could work out real solutions? I don't see those see those self critical lists... there are just so many ****** up things, and if we don't work on figuring them out and speak about it... how should we overcome them? 

Greets... bring out your deads... eh.. bugs...

---

### Post by moster on 2009-07-12
Well, it is interesting that work is being done in boot speed department BEFORE resolving standby and hibernate. This is probably because linux in general is oriented more on servers rather then desktop.

But, good news! In Carmic Koala this "problem" should be gone. Kernel hackers finally deal with that problem.

---

### Post by arture on 2009-07-13
> Well, it is interesting that work is being done in boot speed department BEFORE resolving standby and hibernate.

What is Boot Department? Is this the things that are being done before shutting down? Aren't this runlevels?

> 
 This is probably because linux in general is oriented more on servers rather then desktop.


Well, I guessed that this is a bug not a feature. Still then some Information would be great, afterwards.

> 
But, good news! In Carmic Koala this "problem" should be gone. Kernel hackers finally deal with that problem. 

How do you see that? Where do you go to look for bugs and how they are solved...?

---

### Post by Redache on 2009-07-13
The focus is trying to improve boot speed to ensure that a Linux Desktop doesn't take long to load. It's like a competition between Distro's to enhance their appeal.

---

### Post by lisati on 2009-07-13
Hypothesis: There's no such things as bugs, only "undesirable features".

---

### Post by 3rdalbum on 2009-07-13
Try suspending instead - it seems to work more reliably.

I don't think anyone knows why suspend and hibernate work so intermittantly on Linux and so comparatively well on Windows. I hear that there's work underway to make a replacement for HAL, which may result in reliable suspend and hibernate.

---

### Post by ThisEndlessFall on 2009-07-13
Karmic is replacing HAL with DeviceKit-power and udev-extras, according to the Alpha 2 page.

[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

---

### Post by moster on 2009-07-13
> **arture said:**
> What is Boot Department? Is this the things that are being done before shutting down? Aren't this runlevels?

Well, I guessed that this is a bug not a feature. Still then some Information would be great, afterwards.

How do you see that? Where do you go to look for bugs and how they are solved...?

I suggest you put your swimming pants on, and surf the internet for answers...

---

### Post by .Maleficus. on 2009-07-13
[Report bugs here.]("https://launchpad.net/ubuntu")

---

### Post by Bölvaður on 2009-07-13
> **arture said:**
> 
Maybe a Buglist for things like that would be great? Where we could work out real solutions?

[https://launchpad.net/]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=ubuntu")

post your bugs there, tell them on which hardware (as this is just your hardware that is failing... so techinically it should be your mother boarder maker that should fix this) and try to help them as much as you can to let the developers fix that problem y9ou are having.

---

