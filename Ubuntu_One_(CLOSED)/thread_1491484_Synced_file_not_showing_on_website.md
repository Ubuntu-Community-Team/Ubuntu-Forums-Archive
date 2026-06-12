---
title: "Synced file not showing on website"
date: 2010-05-23
forum: Ubuntu One (CLOSED)
---

### Post by Vincent Vermeulen on 2010-05-23
I'm using Lucid 64 bit, with encrypted home dir. I put a 4 KB file into the Ubuntu One folder in my home dir, but after 2 hours it is still not visible on the one.ubuntu.com website. Am I impatient or am I missing something?

The file is marked with a green checkmark, so it should be synced. Right? I just put in this single file, and even after clearing browser cache, new login etc. the website is showing no files, no folders.

I checked that everything is working with `u1sdtool -s`, and seems to be okay:

> State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Appreciate your thoughts on this .

---

### Post by Zemblan on 2010-05-23
I had a similar problem, I think ubuntu one is just working very slowly and with odd glitches at the moment. They are adding new servers etc to deal with the increased load from new users.

---

### Post by Vincent Vermeulen on 2010-05-24
Thanks Zemblan. After 8 hours the file showed up on the webpage, so I  was indeed impatient (or spoiled with expectations).

---

