---
title: "NICE: Google Earth!!"
date: 2006-06-12
forum: The Cafe
---

### Post by mattisking on 2006-06-12
Ok, so I realize this isn't really about Edgy but I generally only hang out in the development forum... so feel free to move it where-ever.

At any rate, Google Earth has now been released with native support for Linux! It runs great!

[http://slashdot.org/articles/06/06/12/2050255.shtml]("http://slashdot.org/articles/06/06/12/2050255.shtml")
[http://earth.google.com/download-earth.html]("http://earth.google.com/download-earth.html")

---

### Post by nehalem on 2006-06-12
Yes it does.  On this day I love Google.

---

### Post by RS3York on 2006-06-12
Great news!

---

### Post by lexxonnet on 2006-06-13
Yay... been waiting for this for a while now!
Runs great as well...

So... who's making the deb package :D

---

### Post by evil_elman on 2006-06-13
And what do you have to do in order to be able to use a .bin file?

Re-package it?

---

### Post by sumadartson on 2006-06-13
```
chmod +x GoogleEarth.whatever.the.bin.is.called.bin
./GoogleEarth.whatever.the.bin.is.called.bin

```

It then installs itself in a newly created google-earth directory in the current user's home dir.

A .deb would be nice... but this is already fantastic. I can see my house from here!

---

### Post by DeeZiD on 2006-06-13
Yay!!!!!!!!

Great news :KS

---

### Post by DeeZiD on 2006-06-13
It works great here, even with Xgl :D

---

### Post by evil_elman on 2006-06-13
Easiest installation I've ever seen... We should have more of these 'Windows-like' installation if I might say so myself.

All other products I've installed so far has been software which isn't available in repositories and they have been a pain in comparison to this.

---

### Post by DeeZiD on 2006-06-13
[QUOTE=evil_elman]Easiest installation I've ever seen... We should have more of these 'Windows-like' installation if I might say so myself.

All other products I've installed so far has been software which isn't available in repositories and they have been a pain in comparison to this.[/QUOTE]

The installation is great.
Only doubleclick on the .bin file and the setup starts :)

---

### Post by huwshimi on 2006-06-13
Works perfectly on amd64. Thanks google.

---

### Post by henriquemaia on 2006-06-13
[quote=xi0nblue]Works perfectly on amd64. Thanks google.[/quote] 
Very true. Works great here too on my 64bit installation.

---

### Post by aamukahvi on 2006-06-13
[QUOTE=evil_elman]Easiest installation I've ever seen... We should have more of these 'Windows-like' installation if I might say so myself.

All other products I've installed so far has been software which isn't available in repositories and they have been a pain in comparison to this.[/QUOTE]
I'd rather have a deb I can just click on to add it into the package management. It's just as easy but comes with the added benefit of being available to all users and easy removal / update.

---

### Post by Paloseco on 2006-06-13
[QUOTE=aamukahvi]I'd rather have a deb I can just click on to add it into the package management. It's just as easy but comes with the added benefit of being available to all users and easy removal / update.[/QUOTE]

Maybe in a short time or someone will do it... The problem is that bin can be installed on any distro but deb is debian dependant, so I think there will be no deb in the near future.

---

### Post by G Morgan on 2006-06-13
Can't they release an RPM via LSB. We can use the alien command then to install. The bin works fine don't get me wrong but we should encourage people to produce software via the standard methods. Prehaps when it leaves beta they will look at it.

---

### Post by kanem on 2006-06-13
[QUOTE=evil_elman]Easiest installation I've ever seen... We should have more of these 'Windows-like' installation if I might say so myself.

All other products I've installed so far has been software which isn't available in repositories and they have been a pain in comparison to this.[/QUOTE]
Yes, installations like this would make things easier. But the downside is that each program would take up this much room. This one's folder is 42MB which, for a Linux program, is huge. There are whole GNU/Linux operating systems that size. 

The reason Google-earth is this big (and so easy to install) is that it includes all the libraries it could possibly need, even ones that the user already has installed. For example libqt-mt is  included, which is the main (or one of the main) graphical library for KDE programs. If the user already has any KDE programs installed then having this library in the google-earth folder as well is a complete waste of space.

It might be okay for one or two programs to do this, but they can't all do this. Well, they could, but it'd be a lot of wasted space.

---

### Post by kanem on 2006-06-13
Is anyone noticing smoother movement in Windows than in Ubuntu? I sense a jerkyness when rotating the planet as compared to the Windows version. Hopefully I'm just imagining it.

---

### Post by lexxonnet on 2006-06-13
I actually thought movement on ubuntu was smoother... then again... that was when I last had windows, which was close to 7 or 8 months ago...

---

### Post by Cheizzz on 2006-06-13
movement in Ubuntu seems slower than in windows to me too, so kanem, youre not the only one out there! :p

---

### Post by evil_elman on 2006-06-14
It is indeed notably slower than in Windows... :-(

---

### Post by xmastree on 2006-06-14
\\:D/

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=11127[/IMG]

\\:D/

---

### Post by Toxicity999 on 2006-06-14
I get a seg fault after the splash screen...

---

### Post by bruce89 on 2006-06-14
Works alright for me.

---

### Post by &amp;)ky#)^ on 2006-06-16
Keep in mind that Version 4 that supports Linux is still in beta.  Hopefully those problems with jerkiness and slow movement will be fixed by final release.  It does work without a hitch in amd64.  Hooray!  However, I was having problems with networked bookmarks and 3D models from 3D warehouse.

I'd also like it in a deb file.  I figure it may be available in deb soon because Picasa is available in deb.

---

### Post by &amp;)ky#)^ on 2006-06-16
Another weird problem I was finding was with the ruler tool box.  Try opening the ruler tool.  A little options box should appear.  Try moving it by dragging.  Mine flies all around the screen.  Anybody else have that?

---

### Post by easyease on 2006-06-16
It doesnt recognise my graphics card (GeForce4 MX 440)...............wtf? the program loads but i dont see earth just the inky blackness of space where no-one can hear me scream.......aaaaaaaaaaaaaaaaaaaaaaaaaaaargh!

---

### Post by isotonic on 2006-06-16
It crashed first time I ran it but it looks pretty kewl...the zoom in on to houses and streets is pretty impressive!

---

### Post by Ventajou on 2006-06-16
I don't see the earth either, with an i855 chipset... maybe in installed Google Deep Space instead?

---

### Post by Somenoob on 2006-06-16
Great news, i thought they would never release a Linux version for it.

---

