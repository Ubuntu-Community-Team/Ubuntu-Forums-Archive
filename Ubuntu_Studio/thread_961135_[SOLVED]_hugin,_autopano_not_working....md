---
title: "[SOLVED] hugin, autopano not working..."
date: 2008-10-28
forum: Ubuntu Studio
---

### Post by hardyn on 2008-10-28
does anybody have the autopano component of hugin working correctly?

i cannot seem to get it to work, and the export windows to autopano-sift flashes so quicky i cannot read if there are any errors.

the images do stitch correctly using a commercial program that uses the same UBC technology, but i cannot get the hugin / autopano system to function correctly.

help

---

### Post by hardyn on 2008-10-28
Okey, so autopano-sift is working, when run from the command line it correctly identified the control points.  then it can be manually fed back into hugin for stitching.  suggesting that there is something incorrect in the output arguments, or in hugin its-self (the repos are not the most current version)

I will goof around with it a little after work again tonight, and see if i can make it work.

after that, see if i can get enblend to work, again, i suspect there will be argument problems.

---

### Post by hardyn on 2008-10-28
BLAAAAAAARRRRRGGGG!!!!!!!

no spaces in path names!!!!

(man i hate it when stuff like this happens)

---

### Post by Rhubarb on 2008-10-28
I'm just about to resume some photography myself, after recently discovering my digital camera can take RAW photos (not just jpeg ones).
I've used hugin before, it works quite well, a tripod is very important though.

So the problem you encounted was a silly problem with spaces in file names?

---

### Post by hardyn on 2008-10-29
yes, it works really well out of the box.... assuming you do not have spaces in the PATH names, not just file names.

i didn't use a tripod for any of mine and they have come out quite well.

the hint came from an Apple photo site.

---

### Post by nickpj on 2008-11-30
Thank you!! Removing the spaces from the path names fixed it for me too, autopano-sift was completely broken without this. It would be great if the software would be fixed to work with pathnames with spaces, but at least now I can get the software to do something, by removing those spaces :-)

---

### Post by louisgag on 2011-03-11
I had a similar problem after upgrading to Natty, turned out I had to (re)install the autopano-sift package!

---

### Post by jlpelerin on 2011-06-05
Same for me: I had to (re)install the autopano-sift package after switching to 11.04 Natty Narwhal!

---

