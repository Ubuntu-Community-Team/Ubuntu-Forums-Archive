---
title: "moving .cache"
date: 2012-11-26
forum: Security
---

### Post by lister171254 on 2012-11-26
Not strictly a security, but more a privacy question, but I have my personal files as well as swap encrypted (Didn't want to encrypt the entire home).

Without being paranoid, the .cache folder still has a fair amount of stuff that I'd prefer to also be encrypted.

Tried to delete .cache  and created a soft link to a folder on the encrypted folder. That worked until I rebooted where it got rid of the link and re-created .cache

Any other suggestions.

---

### Post by SlugSlug on 2012-11-26
bit of a long shot but check fstab and have it mount /home last.

(So your encrypted mount is mounted before home allowing link from home to be created ?)

---

### Post by lister171254 on 2012-11-26
I'm mounting the encrypted files via cryptkeeper manuall after I log in.

Not sure whay I loose the link though

---

### Post by SlugSlug on 2012-11-26
does seem odd is it a sym link your making? 

could try make it then

chattrib +i .cache

not tried that on a folder before tho

---

### Post by lister171254 on 2012-12-08
As ususal the problem is in the chair

My symboloc link was wrong. Once I fixed this, I now have .cache on my encrypted drive, after the reboot.

Thanks

---

