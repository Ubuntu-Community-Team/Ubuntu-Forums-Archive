---
title: "Digikam - no video thumbnails - Intrepid"
date: 2008-12-11
forum: Ubuntu Studio
---

### Post by timcredible on 2008-12-11
Anybody know how to get thumbnails working in digikam with the intrepid release?  i used to install libart1-xine, but i did that (had to search around for that .deb file), and it still doesn't work.  i also installed kdemultimedia, still doesn't work.

Thanks.

---

### Post by timcredible on 2008-12-16
well, i think i found the problems.  first, i need mplayerthumbs-1.1 now instead of libart1-xine or kdemultimedia.  ok, i found that and installed it (not in the repos).  but i also need exiv2-0.18, which i can't find in .deb form.  so, i may or may not try to compile it and see if this really fixes it.  curse you, kde4!  not really, it just looks like kde4 was rushed a little and broke several things.

---

### Post by timcredible on 2008-12-16
well, installing the new exiv2 allowed konqueror to create thumbnails for video files, but digikam still won't.  i even install xine to see if it could play the file, and it played it with no problems.  i guess that feature of digikam is just plain broke and won't be fixed for a while.

---

### Post by Didjit on 2009-01-03
Had the same issue. I couldn't find an updated deb for mplayerthumbs, so I compiled following the directions here: [http://kubuntuforums.net/forums/index.php?topic=3085626.msg136683#msg136683](http://kubuntuforums.net/forums/index.php?topic=3085626.msg136683#msg136683)

Now I have video previews in Digikam.

HTH

Didjit

---

### Post by timcredible on 2009-01-05
i get an error on the cmake command.  i guess i'll just wait for jaunty and see if it's fixed there - i did read that mplayerthumbs 1.1 is in jaunty.

---

### Post by MightyFlea on 2009-01-21
Hey guys,

[Launchpad bug #277480]("https://bugs.launchpad.net/ubuntu/intrepid/+source/mplayerthumbs/+bug/277480") seems to say there should be a packages for mplayerthumbs 1.1 in intrepid-proposed, but I can not seem to find it.

Am I just too stupid to find it, or is it not there; if so, is there a binary package at some other place or do I have to compile it myself?
(I can do that, but it has been a while and I am kind of rusty.)

Cheers, Michael

---

### Post by timcredible on 2009-01-22
if you're able to compile it, would you post the steps?  i tried compiling mplayerthumbs 1.1, but i always got an error and gave up trying to figure out what the problem/dependency was that i was missing.  i mean, it shouldn't be too difficult, it came with a make script, but i couldn't get it to work.

---

### Post by MightyFlea on 2009-01-22
Well, I did find a precompiled package in a PPA in the end: [https://launchpad.net/~samrog131/+archive](https://launchpad.net/~samrog131/+archive)

I downloaded the .deb directly and did not add the PPA to my sources so I won't pull more unsupported packages than absolutely necessary. It is relatively ancient (from August 2008), but it seems to be working fine: Now I have video thumbnails in digikam.

I think I will just live with that and bide my time until something shows up in intrepid-backports or intrepid-updates. Or until Jaunty is released; whichever is first. ;-)

Btw I did install digikam 0.10 Beta from a PPA ([https://launchpad.net/~digikam-experimental/+archive](https://launchpad.net/~digikam-experimental/+archive)) - I quite like the newer version so far. I have not noticed any problems so far, but I did not do any heavy editing just yet.
(To get it I had to enable two other PPAs (just follow the links), so now I have a ton of unsupported packages in my system. Oh well, I guess there is always a price.)

---

### Post by timcredible on 2009-01-22
thanks for the link for the new mplayerthumbs.  i installed it via synaptic because i have no fear of too many repos ;-)  but it didn't work with 0.9.4 of digikam.  i've got the repos added for the new version of digikam, but i need to wait to try it until i get to a place with a faster internet connection (79mb will take me a couple hours where i am right now).  i'll update this thread later today with results.

---

### Post by timcredible on 2009-01-23
video thumbnails work now - i had to install the new digikam too.  thanks mightyflea!

---

