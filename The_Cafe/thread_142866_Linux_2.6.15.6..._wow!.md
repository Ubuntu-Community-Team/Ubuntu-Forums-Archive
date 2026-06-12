---
title: "Linux 2.6.15.6... wow!"
date: 2006-03-11
forum: The Cafe
---

### Post by Kimm on 2006-03-11
Today I upgraded my kernel, even though my last kernel was fairly resent (2.6.15 with ck-pack 1) I felt that it was less stable then the Breezy Stock kernel. So I did a compile of the absolutely latest kernel without any patches.

I'm blown away! right now I'm compiling the latest release of GTK2 and I cant feel it. on a 1.7 Ghz Intel Celeron with 256 mb ram. Same thing a minute ago when I compiled Epiphany (think it got updated and I didnt like the new version...).

So, if you want to try to compile your own kernel, sieze the moment and do it!
I'd post my build for everyone to download (i686) if I had somewhere to host it :-k

---

### Post by K.Mandla on 2006-03-11
(Just sort of merging the top two threads right now....)

[http://www.ubuntuforums.org/showthread.php?t=142610](http://www.ubuntuforums.org/showthread.php?t=142610)

---

### Post by Klaidas on 2006-03-11
How big would that be?

---

### Post by BWF89 on 2006-03-11
[QUOTE=Kimm]I'd post my build for everyone to download (i686) if I had somewhere to host it :-k[/QUOTE]
[http://rapidshare.de/](http://rapidshare.de/)

---

### Post by papangul on 2006-03-11
[QUOTE=Kimm]
I'd post my build for everyone to download (i686) if I had somewhere to host it :-k[/QUOTE]
Isn't it tailor made just for yourself or is it meant for public use like stock Ubuntu kernel'?

---

### Post by Kimm on 2006-03-11
[QUOTE=K.Mandla](Just sort of merging the top two threads right now....)

[http://www.ubuntuforums.org/showthread.php?t=142610](http://www.ubuntuforums.org/showthread.php?t=142610)[/QUOTE]

I would have used that service, but the kernel-image package is around 16 MB's so its to big.
The other host seems nice though, here are the links for kernel-image and kernel-headers:

[http://rapidshare.de/files/15246561/kernel-image-2.6.15.6-custom_10.00.Custom_i386.deb.html](http://rapidshare.de/files/15246561/kernel-image-2.6.15.6-custom_10.00.Custom_i386.deb.html)
[http://rapidshare.de/files/15246642/kernel-headers-2.6.15.6-custom_10.00.Custom_i386.deb.html](http://rapidshare.de/files/15246642/kernel-headers-2.6.15.6-custom_10.00.Custom_i386.deb.html)

Some other good news is that this kernel seems to work better with the spca5xx webcam driver. My kernel used to crash while using this driver, not anymore.

Edit:

> 
Isn't it tailor made just for yourself or is it meant for public use like stock Ubuntu kernel'?


Should work for pretty much anybody, Its configured pretty much like the stock kernel (I dont need any special configuration)

---

### Post by bonzodog on 2006-03-11
With Dapper flight 5, you get 2.6.15.18, if you are willing to upgrade. I can confirm that flight 5 is VERY stable, extremely fast, and well worth it.

---

### Post by Kimm on 2006-03-11
is that a later or earlier version of the kernel (than 2.6.15.6) :confused: 
'cos I downloaded this as the latest kernel from kernel.org yesterday

---

### Post by papangul on 2006-03-11
lol..

---

### Post by engla on 2006-03-11
[QUOTE=Kimm]is that a later or earlier version of the kernel (than 2.6.15.6) :confused: 
'cos I downloaded this as the latest kernel from kernel.org yesterday[/QUOTE]
It's hard to tell; the version is reported as 2.6.15-18, but what it really means is that the ubuntu dapper kernel is based on 2.6.15.

Anyway, in some ways it's not newer since it doesn't follow all the 2.6.15.x releases, however much of the changes so far are included.
But the ubuntu kernel has backported _some_ drivers and things from the 2.6.16 release (so far only a release candidates available)

---

### Post by NoWhereMan on 2006-03-11
[QUOTE=Kimm]I'd post my build for everyone to download (i686) if I had somewhere to host it :-k[/QUOTE]

Look here 
[http://acfwiki.pbwiki.com/FreeFileStorage](http://acfwiki.pbwiki.com/FreeFileStorage) :)

---

### Post by liquidtenmillion on 2006-03-12
What were your config options?

What form of preemption did you pick, what scheduler, how many HZ, etc.

---

### Post by kaamos on 2006-03-12
Does pmount (in Gnome) work? So if you plug in a usb stick, does it appear on the desktop?

---

### Post by mstlyevil on 2006-03-12
[QUOTE=kaamos]Does pmount (in Gnome) work? So if you plug in a usb stick, does it appear on the desktop?[/QUOTE]

It sure does work. Just tested it.;)

---

