---
title: "World Wind fills me with HOPE!"
date: 2005-05-08
forum: The Cafe
---

### Post by DirtDawg on 2005-05-08
So I'm sure many, many people know all about NASA's open-source project "World Wind"( [http://worldwind.arc.nasa.gov/](http://worldwind.arc.nasa.gov/) ) but it was news to me when a friend and I stumbled over it. What an amazing piece of software. I'm not sure why anyone would bother with Google's "Keyhole" when this seems to be a far more advanced system for absolutely no cost. (Well, other than the cost American Taxpayers forked over to develop the system. But this, imho,  is a prime example of a great way to spend government funds.) 

What strikes me too is that I've heard a lot of talk about large corporations and other  entities trying squash Linux by claiming patent infringments or whatever. It seems obvious now that NASA would use Linux almost exclussively, seeing as they probably build most of their software from the ground up anyway, though this hadn't occured to me before visiting their site. To get to the point; with powerhouses such as NASA standing behind open source development, is there any real chance attempts to slow Linux down will be succesfull? 

If you have a good internet connection and a fairly speedy computer, go get World Wind NOW! You'll love it!

EDIT: I just realized the thing only works on Windows XP, so if you're a full Linux convert, I guess you're out of luck. :|

---

### Post by rathel on 2005-06-28
Yeah it is great!, but is there any linux software like this? have you tried Google's new earth program? [http://earth.google.com](http://earth.google.com), it looks pretty good. but not for linux either :(

---

### Post by ltmon on 2005-06-28
[QUOTE=rathel]Yeah it is great!, but is there any linux software like this? have you tried Google's new earth program? [http://earth.google.com](http://earth.google.com), it looks pretty good. but not for linux either :([/QUOTE]

Google Earth is what became of keyhole, and the jury is out on which is better.  Earth seems a little more suited to average joe use, wheras NASA's is probably more useful for scientific reasons.

A good thing about Google Earth is that when they bought it they made an OpenGL backend, so now it renders using DirectX or OpenGL.  This seems to me to be the first step towards a multi-platform Google Earth, so keep your fingers crossed.

L.

---

### Post by rathel on 2005-06-28
Cool, I hope it does it ported over.

---

### Post by DirtDawg on 2005-06-28
Considering NASA is full and Linux nuts and WorldWind is open-source, it's suprising there's no Linux port. But I suppose it has something to do with the networking system (just a guess)? 
WorldWind works great if you live in one of the USGS mapped cities of America, of which I think there's 7 or 12 or some number. (I live in Portland Or. which is mapped) Otherwise the resolution gets only so good. I haven't seen the new Google mapper yet. I thought they were behind the pay-to-play Keyhole project?

---

### Post by sonny on 2005-06-29
Can't it be install just with the source code???

---

### Post by ltmon on 2005-06-29
[QUOTE=sonny]Can't it be install just with the source code???[/QUOTE]

No, it uses some Microsoft libraries which would have to be ported to their Linux equivalent.  Depending on how many of the Microsoft libraries were used then porting could be very time consuming.

L.

---

### Post by sonny on 2005-06-29
[QUOTE=ltmon]No, it uses some Microsoft libraries which would have to be ported to their Linux equivalent.  Depending on how many of the Microsoft libraries were used then porting could be very time consuming.

L.[/QUOTE]
Well in that case we should send emisares to digg into the code...  :grin:. Or wait until they release a Linux installer.

---

### Post by UbuWu on 2005-06-29
There is some discussion about a linux port on their forums, the problem is that there are a lot of people talking about it, but nobody's is doingit yet...

So far this is what comes closest: a 2d version of worldwind which will be crossplatform:
[http://forum.worldwind.arc.nasa.gov/index.php?showtopic=3780](http://forum.worldwind.arc.nasa.gov/index.php?showtopic=3780)

---

### Post by UbuWu on 2005-06-29
Just noticed the screenshot is actually on Ubuntu  :razz:

---

### Post by UbuWu on 2005-07-03
There is a working version now, although still only for windows... the author says he is currently compiling it on linux  :grin:

---

### Post by UbuWu on 2005-08-16
World Wind for Linux!!!   :grin: 

[http://ww2d.berlios.de/](http://ww2d.berlios.de/)
[http://www.gnomefiles.org/app.php?soft_id=1045](http://www.gnomefiles.org/app.php?soft_id=1045)

Now, if someone could make a .deb for it...

---

### Post by macgyver2 on 2005-08-16
[QUOTE=ltmon]A good thing about Google Earth is that when they bought it they made an OpenGL backend, so now it renders using DirectX or OpenGL. This seems to me to be the first step towards a multi-platform Google Earth, so keep your fingers crossed.[/QUOTE]
It seems like it's difficult to read google when it comes to cross-platform support.  They have that image-organization program, Picasa, that looks pretty decent (saw it on a friend's comp) but it's only for windows.  According to some other message boards, fellow Linux users have written Google about offering a version for Linux and Google's reply was that they have no intention to do so (although maybe that'll change).  Yet Google itself runs it's stuff on Linux (Red Hat, last time I checked...wouldn't it be something to get them to switch to Ubuntu...).  So it strikes me as a bit odd that a company that is so Linux-heavy wouldn't release it's software for Linux...even if they didn't want to release the source code, they could still just do binaries...

---

### Post by matthew on 2005-08-16
Read all of the pages at berlios.de and the program looks good. I downloaded the tarball and installed it, but I haven't had any luck getting it to work.

If I try through the gui (using Nautilus to browse to the directory, then clicking the icon) the splash screen comes up and then nothing happens.

So...I ran it from the command line. The splash screen comes up but again didn't run. However, I did get a reason--output was: "Segmentation Fault."

Bummer. Looks cool. I've got some other stuff to do, but hopefully I'll get some time to play around and see if I can figure out what's going on. Maybe someone else will have better luck off the bat.

---

### Post by UbuWu on 2005-08-18
[QUOTE=matthew]
So...I ran it from the command line. The splash screen comes up but again didn't run. However, I did get a reason--output was: "Segmentation Fault."
[/QUOTE]

A newer version (0.99.5) was released quickly after the first one to fix the segfaults, did you try that one? 

Fot me WW still crashes when I zoom in and don't disable the placenames layer. And it can be very unresponsive while it is loading images, but still it is nice to play around with!

---

### Post by matthew on 2005-08-18
[QUOTE=UbuWu]A newer version (0.99.5) was released quickly after the first one to fix the segfaults, did you try that one? [/QUOTE]
Unfortunately, that is the version I have. I just looked to confirm it and test it again.

---

### Post by paulmerchant on 2006-08-10
The developers have announced that version 1.5 of World Wind could be here as early as September 30, 2006. What's the main new feature? It is being completely retooled to be cross platform.

I can't wait. This is one of my favorite applications! My Windows partition is slowly getting smaller and smaller.

---

### Post by Brunellus on 2006-08-10
not native linux, nothing to see here.

---

### Post by nalmeth on 2006-08-10
I have not heard about this. Thanks for the linkup, I will try it at home

---

