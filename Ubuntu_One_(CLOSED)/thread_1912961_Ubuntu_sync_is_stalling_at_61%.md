---
title: "Ubuntu sync is stalling at 61%"
date: 2012-01-21
forum: Ubuntu One (CLOSED)
---

### Post by BeyondtheClouds on 2012-01-21
Ubuntu one***
I know it takes a while to sync and it's 3 gbs, but it's been about an hour an it hasn't budged.

---

### Post by oldos2er on 2012-01-21
Moved to Ubuntu One.

---

### Post by gleedadswell on 2012-01-24
> **BeyondtheClouds said:**
> Ubuntu one***
I know it takes a while to sync and it's 3 gbs, but it's been about an hour an it hasn't budged.

Yeah, the first sync seems to be quite slow.  When I first set it up it was syncing about 4.5 Gb and it took well over a day to do it.  But once it's done that initial sync it seems to be quite fast.  Now I can edit and update a many Mb file in my U1 folder and it syncs almost instantly as soon as I hit save in whatever application I'm working in.

---

### Post by Bobrm2 on 2012-01-24
I'm running Ubuntu 10.10, and have been trying to "Sync" Ubuntu One for three or four days now. What can I do to change this situtation. I have disconnected and restarted twice now.????

---

### Post by SongOfMyself on 2012-01-26
It seems to be entirely random as far as when it does it. It took nearly 2 weeks for it to ever do the first sync of my photos folder. The Ubuntu One folder itself would always sync immediately, however, as soon as anything was changed in it. When it finally got to that first sync, it hung for 3 or 4 hours, but after that, it progressed extremely fast. I guess when it hangs it's still working, it just doesn't update it's status :-\"

---

### Post by duanedesign on 2012-01-26
HI,
I apologize for anyone experiencing slow file sync and or disconnects and reconnects. We have experienced an unexpected increase in users. We are adding servers and making code changes to get things back to normal.

@Beyond the clouds use the Terminal command:

u1sdtool --waiting | wc -l

This will show you the number of items in the queue. If it makes no progress for a long period of time please contact our support so we can further debug you issue.
[https://one.ubuntu.com/help/contact/](https://one.ubuntu.com/help/contact/)

Thanks,
Duane

---

