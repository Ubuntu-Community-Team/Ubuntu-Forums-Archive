---
title: "Best way to promote my program?"
date: 2008-02-18
forum: The Cafe
---

### Post by peabody on 2008-02-18
It seems like my autokey program has been gathering some momentum lately.  I just released 0.26 which should fix the program enough to run on most people's Linux machines, and the lastest subversion just had a rash of new features.

At this point I'd like to get so more testing and feedback done to squash bugs because I'm sure the program is far from perfect and won't work for everyone just yet.  However, I'm unsure of the best method to advertise my program.  Obviously it's inappropriate to post meme's in the support forums.  I'd also like to get the word out to people using other distributions.  And of course, I'd also be interested in gathering some developers.  I'm kind of a novice at this; anyone have any sagely advice?

---

### Post by DoctorMO on 2008-02-18
linky? perhaps you should explain what it does.

---

### Post by hhhhhx on 2008-02-18
unfortunately, advatizer as i am, the best way is to sell the the most people possible, i.e. windows  :(

---

### Post by hhhhhx on 2008-02-18
[http://ohioloco.ubuntuforums.org/showthread.php?t=679612](http://ohioloco.ubuntuforums.org/showthread.php?t=679612)

also DoctorMO, i see that Dohicky is coming along nicely. :)

---

### Post by DoctorMO on 2008-02-18
> unfortunately, advatizer as i am, the best way is to sell the the most people possible, i.e. windows

Sell? you mean like a buying a license for proprietary software? Maybe some information about why Free Software and Open Source works better as a way to make money and software is in order.

As for windows, the more programmers develop for that platform the more people will continue to use windows instead of looking for alternatives; sooner or later the open source world will have to ditch windows if it wants to see ubuntu used.

---

### Post by hhhhhx on 2008-02-18
> **DoctorMO said:**
> Sell? you mean like a buying a license for proprietary software? Maybe some information about why Free Software and Open Source works better as a way to make money and software is in order.

As for windows, the more programmers develop for that platform the more people will continue to use windows instead of looking for alternatives; sooner or later the open source world will have to ditch windows if it wants to see ubuntu used.
from an advatizers standpoint, it is favorable to go with mocrocrap. i dont think thats what should be done though, sorry for not making that clear.

---

### Post by peabody on 2008-02-18
> linky? perhaps you should explain what it does.

The link is in my signature.

> the best way is to sell the the most people possible, i.e. windows

The nature of this program is such that it is explicitly for Linux.  I don't care about money, I'm just interested in popularity and recognition among desktop linux users.

---

### Post by DoctorMO on 2008-02-18
> The link is in my signature.

I see, it looks very cool; I like the date one for sure.

What I'd do is create a way to edit the configuration with a gui, make it in python with gtk and glade, really easy to do.

Next you need to make it _very_ easy to install, this means packaging up your gui and program into a deb package.

You'll then want to submit this package to launchpad for inclusion into universe.

Then you can go on a campaign of letting people know the tool exists.

---

### Post by peabody on 2008-02-18
> **DoctorMO said:**
> I see, it looks very cool;

Thanks.

> I like the date one for sure.

Any shell command can be run.

> 
What I'd do is create a way to edit the configuration with a gui, make it in python with gtk and glade, really easy to do.


The configuration is just a text file that's very easy to work with.  I have an abbreviation that launches a text editor with the file open so I can change abbrevs on the fly.  I'm certainly not against guis for the program, but I'm actually inclined to perhaps make a sockets interface to it so that a gui front end could be written for it in just about language.

> Next you need to make it _very_ easy to install, this means packaging up your gui and program into a deb package. 

This is certainly in the program's future as I approach a 1.0 release.

> 
You'll then want to submit this package to launchpad for inclusion into universe.

Sure, but only after I manage to get it working with international keyboards ;).  

> Then you can go on a campaign of letting people know the tool exists.

Eh, release early, release often :).  I'm after guinea p--err testers at the moment.  I guess that's more of what I'm really after.

---

### Post by DoctorMO on 2008-02-18
> Eh, release early, release often . I'm after guinea p--err testers at the moment. I guess that's more of what I'm really after.

Tests are a net percentage of possible users; the same rules apply. don't wait for version 1.0 for packaging. Do it right now.

The GUI, I'd make one, reason being while there are lots of people who are from the old linux world of editing config files. too many people are scared to break things with a text file. Lowering the barrier to try your program without fear must be one of your goals.

---

