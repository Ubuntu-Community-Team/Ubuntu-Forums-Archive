---
title: "Yikes!  Clean Up did too good a job! :("
date: 2009-07-25
forum: Ubuntu Christian Edition
---

### Post by ElEdwards on 2009-07-25
Just for grins, I ran the "Computer Janitor" and it displayed a ton of DEB files.  I thought, "Ah, these are leftovers from the installation." and I selected them all for cleaning..... BAD, BAD IDEA!! ..... this got rid of Dans Guardian and more stuff than I can remember right now.

I'm going to have to reinstall CE.... which makes me wonder... What's the point of having "Computer Janitor" if it gets rid of apps??

"Computer Janitor" (to me) means to get rid of Junk.  Right?

El

---

### Post by jerrrys on 2009-07-25
what, no backup?

---

### Post by lukjad on 2009-07-25
Computer Janitor is there to reset your computer to "factory defaults" in a manner of speaking. If you like the way your system works, don't use it. :D

---

### Post by david_kt on 2009-07-25
> **ElEdwards said:**
> Just for grins, I ran the "Computer Janitor" and it displayed a ton of DEB files.  I thought, "Ah, these are leftovers from the installation." and I selected them all for cleaning..... BAD, BAD IDEA!! ..... this got rid of Dans Guardian and more stuff than I can remember right now.

I'm going to have to reinstall CE.... which makes me wonder... What's the point of having "Computer Janitor" if it gets rid of apps??

"Computer Janitor" (to me) means to get rid of Junk.  Right?

El

I think that is because the repository of ubuntu ce did not appear so as the janitor would think all ubuntu ce are redundant packages. Please follow instruction below and you will have ubuntu ce back and will not be removed by computer janitor anymore:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

I will make sure the ubuntu ce repo did not disappear on the production release.

DK

---

### Post by david_kt on 2009-07-25
> **lukjad007 said:**
> Computer Janitor is there to reset your computer to "factory defaults" in a manner of speaking. If you like the way your system works, don't use it. :D

Look like the computer janitor would remove even packages that you install manually (no repository for it). Other than that, it is good to have it. But for me, I prefer to use:

"sudo apt-get autoremove --purge"

It will not remove packages you install.

DK

---

