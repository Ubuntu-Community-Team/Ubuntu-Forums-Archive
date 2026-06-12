---
title: "groups locked down"
date: 2009-04-14
forum: Security
---

### Post by recklessray on 2009-04-14
hi, i have users rj, sam, photos and movies

rj and sam are people and i want to store my photos and movies in the relevent home areas to later share using samba.

the home permissions are 700 for rj and sam 

the home permissions are 770 for photos and movies

i used usermod -a -G rj movies
i used usermod -a -G rj photos

to add rj to the relevent groups to access home areas of picutes and movies ...

it doesnt work. ls /home/movies as user rj just returns a permission denied. 

clearly im missing part of the picture here. i'd be really grateful if someone could prod me in the right direction ;)

thanks so much..

ray

---

### Post by ubuntu27 on 2009-04-14
Yet another SPAM Reported.

---

### Post by recklessray on 2009-04-14
spam???!!! how so??

---

### Post by ubuntu27 on 2009-04-14
> **recklessray said:**
> spam???!!! how so??

No, not yours. :P

There was a post below you promoting some website with huge graphic. I reported it and it was deleted.

---

### Post by cammin on 2009-04-14
usermod -a -G users,photos rj

Makes rj a member of the users and photos group

---

