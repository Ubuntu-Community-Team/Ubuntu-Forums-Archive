---
title: "Linux Support for new ipods?"
date: 2007-09-30
forum: The Cafe
---

### Post by Ultra Magnus on 2007-09-30
So I read a little while ago about how Apple had stopped Linux users from using the new ipods, then a couple of days latter I read how the encryption had already been cracked - I was just wondering what the current status of this is - Can you use the new ipods on Linux yet? I've had a look around but there doesn't seem to be any new information on this.

---

### Post by kanem on 2007-09-30
So the fix is just a few lines of extra code that goes into libgpod. libgpod is the backend for all Linux software that manages ipods. For the fix to work now, someone would have to put this code into their copy of the libgpod source file themselves and recompile.

Eventually the code will get into the main version, but it seems it hasn't happened yet; I just went to libgpod/gtkpod's website, and the latest version is from a few months ago. When and if they do release a version with the fix you'll still have to either compile it or get it from somewhere like getdeb.net.

Edit: the code is in libgpod SVN right now. So a new version with new ipod support should be out soon.
[http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/](http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/)

---

### Post by neoaddict on 2007-09-30
I took the liberty of updating the blog post as I was missing a few steps.  :)

---

### Post by kanem on 2007-10-01
Quite a popular blog you got there. It was most of the first hits for a search on "libgpod touch". 

And thanks for the info.

---

### Post by Ultra Magnus on 2007-10-01
Awesome - when I have a free moment I'll have a look - says its "unstable" but all my music is backed up so If I lose It i can always put it back on again.

---

