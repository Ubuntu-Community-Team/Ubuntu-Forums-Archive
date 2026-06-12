---
title: "Can not access desktop, Ubuntuone is holding things up."
date: 2009-09-05
forum: Ubuntu One (CLOSED)
---

### Post by pyjimbo on 2009-09-05
Since this morning I can not access the desktop after I login. It is just an empty desktop, no GUI, just the background wallpaper. I used to get a notification in the top right right corner that Ubuntuone is updating but I removed the client, and the problem persists. It is not frozen, just seems to want to update files but it is taking forever. ** I had selected for Ubuntuone to start automatically, I think this is the problem.**

I already did, sudo apt-get remove --purge ubuntuone-client

What other packages do I have to remove to get rid of this completely?

What is the daemon name? :confused: I picked up on ubuntuone-syncdaemon via another thread but there is no package by that name.

---

### Post by pyjimbo on 2009-09-06
I am going to reformat my machines after I backup data. Not much on them anyway.

---

### Post by cariboo on 2009-09-06
Why not just start in recovery mode and completely remove ubuntuone, no need to reinstall.

```
apt-get purge ubuntuone*
```

---

### Post by jamesmcm on 2009-09-14
Why is this marked as solved, the original bug has _not_ been solved, just telling those who encounter it to reinstall Ubuntu One or reformat isn't really a solution.

---

### Post by pyjimbo on 2009-09-15
> **jamesmcm said:**
> Why is this marked as solved, the original bug has _not_ been solved, just telling those who encounter it to reinstall Ubuntu One or reformat isn't really a solution.

As the original poster of this thread I agree. I viewed solved as too broad. 

I was not in the mood at the time to have my machine not working. In the long run it was not Ubuntuone after all. **It was another problem I unknowingly created. A regular occurrence for Ubuntu Linux.**

---

