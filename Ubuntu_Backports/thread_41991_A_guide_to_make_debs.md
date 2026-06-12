---
title: "A guide to make debs?"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-06-15
I was going to post this in ubuntu help forum but I thought it might get seen by more package maintainer's here.  Please move it if inappropriate.

Can someone create a guide in making one's own debs?  I know there is the debian maintainer's guide but it seems a little involved to me (10+ pages) covering all the scenario's.  

I would think there would be a way to automate the process somewhat if the software compiles with ./configure make make install without issue.  I just want that, and ensure the package lists it's dependencies and has a menu icon (if applicable).

In my other install (deb/sid) even though apt is fairly vast, there was lots of software that didn't have debs.  First I'd check apt-get.org/search, then I tried checkinstall which failed numerous times.  In the end I just made sure I had the libs and devs via apt and compiled the software manually.  I haven't done this yet in ubuntu and I'd really like to avoid doing that if I can.  

One niche I thought I might be able to fill eventually is a ubuntu gaming/small app repository.  There are lots of great games from happypenguin which I have installed in my sid install.  I wanted to initially make my own debs, then make my own local repository for the learning experience, and then maybe offer these to others.  

Basically I thought there is still a fair amount of software that's not in breezy or in debian sid which can be compiled cleanly in hoary if all the lib requirements are met.  I realize this is not in the scope of the backports project, maybe a freshstuff project ;)  Anyway, I have the time to put in this right now and would like to tackle it if anyone has any guides/suggestions on making debs.

---

### Post by jdong on 2005-06-15
Checkinstall creates on-the-fly .deb's for packages by issuing "make install" and monitoring for changes.


The packages are just a way to dpkg --remove it later; dependency tracking is nonexistent. You may use this method to make quick debs.


If you already have RPM's to work with, just use alien to convert them over. As far as whether or not this'll work, no guarantee.

If you want to make real debs like the ones you see apt offering you, the Maintainer guide is the way to go. It actually is a fairly simple and fast procedure (10 minutes max) once you get the hang of it.

---

### Post by McQuaid on 2005-06-15
As I mentioned checkinstall failed on me a few times, but that was in sid, maybe it's better now.  And I found the maintainer's guide a little overwhelming but I guess I should give it another go.  I guess I was looking for a quick n dirty guide that works when stuff compiles without issue.  There's just too many utils/small games I want to install and wanted to avoid compiling from source.  When/if I figure this stuff out I'll write a guide myself hopefully it will help others.

---

### Post by tread on 2005-06-15
I have also read that checkinstall isn't the best way to create debs, library management/sharing isn't good. I wish I could help more .. but you since you are trying to learn something new it'd prolly be good to learn it the right way :)

Oh, and write a guide for us :)

---

