---
title: "Ubuntu One re-uploads songs every time one is played"
date: 2011-07-13
forum: Ubuntu One (CLOSED)
---

### Post by kernelles on 2011-07-13
All my music is already synced, but every time a song finishes playing in Banshee, a notify OSD message appears letting me know that song is being uploaded to my Ubuntu One account. I'm running Ubuntu 11.04 32 bit.

---

### Post by stuartlangridge on 2011-07-13
> **kernelles said:**
> All my music is already synced, but every time a song finishes playing in Banshee, a notify OSD message appears letting me know that song is being uploaded to my Ubuntu One account. I'm running Ubuntu 11.04 32 bit.

In Banshee's *Edit > Preferences*, do you have "Write ratings and play counts to files" set? If you do, then every time you play a song, Banshee will edit the file for that song to record that you've played it one more time; because the file has changed, Ubuntu One will detect that the file has changed and upload it.

---

### Post by kernelles on 2011-07-14
> **stuartlangridge said:**
> In Banshee's *Edit > Preferences*, do you have "Write ratings and play counts to files" set? If you do, then every time you play a song, Banshee will edit the file for that song to record that you've played it one more time; because the file has changed, Ubuntu One will detect that the file has changed and upload it.

Yes, that was it! Thanks!

---

