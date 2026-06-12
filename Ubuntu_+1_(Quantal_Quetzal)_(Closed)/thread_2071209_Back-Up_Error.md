---
title: "Back-Up Error"
date: 2012-10-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by victor9098 on 2012-10-14
Hey all,

Since they have added in the legal notice in the dash I have been seeing the following error at the end of each backup;

> Could not back up the following files. Please make sure you are able to open them.
/home/[user]/.cache/unitydashlegalseen

So first is how do I tweak the permissions? Second, is anyone else seeing this?

Thanks!

---

### Post by mc4man on 2012-10-14
> **victor9098 said:**
> Hey all,

Since they have added in the legal notice in the dash I have been seeing the following error at the end of each backup;



So first is how do I tweak the permissions? Second, is anyone else seeing this?

Thanks!
It's just an empty file with no rw permissions that lets the Dash 'know' not to show the text & instead show the icon in bottom right.
So there is nothing to back up except it's existence

I guess you could r. click on it & change it to read or read/write
(there's nothing to read or write - 0 bytes
Or file a bug if it's causing any actual issue with your backing up

---

### Post by victor9098 on 2012-10-14
Found the file and edited the permissions, so hopefully that will be the end of the error at the end of each backup.

But if nobody else is seeing this error then maybe its just something with my system?

---

### Post by victor9098 on 2012-10-14
Just ran a back-up manually and can confirm that changing the permissions fixes the problem.

I have reported [Bug #1066646]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1066646") against this as I do not believe it is 'expected behaviour', though hopefully its just me ;-)

Thanks again

---

