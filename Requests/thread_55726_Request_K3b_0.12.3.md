---
title: "Request: K3b 0.12.3"
date: 2005-08-10
forum: Requests
---

### Post by SpEcIeS on 2005-08-10
There seems to be some necessary bug fixes in this version such as:
[b]
Ignore dock config from K3b versions older than 0.12.
Do not delete DVD project iso image if "remove image" is unchecked.
Properly load multisession default settings.
Update device selection boxes when devices are added or removed via HAL.
Properly cancel DVD project writing.
Fixed DVD+RW session import.[/b]

I obtained the 0.12.2 version via ***deb [http://www.planet-moll.de/debian](http://www.planet-moll.de/debian) sarge main*** if anybody else would like to give that version a whirl. ;)

---

### Post by strikeforce on 2005-08-10
Isn't this package in the universe repository?

I remember being able to download it?

---

### Post by SpEcIeS on 2005-08-10
[QUOTE=strikeforce]Isn't this package in the universe repository?

I remember being able to download it?[/QUOTE]
Using apt the only version I could attain is 0.12.1. :)

---

### Post by Kyral on 2005-08-10
I dunno about you guys, but I cannot build it from Breezy Src because it can't grab a library

---

### Post by cricalix on 2005-08-13
As an AMD64 user, I'm stuck on 0.11.23 - I'm currently attempting to build based on the source file for 0.12.2 from [http://www.planet-moll.de/debian](http://www.planet-moll.de/debian) - but I'd love an 'official' backport :)  Already had to edit the control file for .12.2 - it wanted debhelper .32 and Ubuntu(? - the package comes from debian) only has .28 :>

---

