---
title: "Using Specto with HellaNZB - possible?"
date: 2007-04-19
forum: The Cafe
---

### Post by Corvo78 on 2007-04-19
I was thinking.
Would it be possible to let Specto make notifications regarding HellaNZB?
I haven't used Specto yet, though I'm quite sure it had a 'filesystem watcher' option.

Since HellaNZB creates new folders when a download is completed, would Specto be able to 'see' this and make a notification about it?
Or perhaps let Specto watch one of HellaNZB's XML files (which might contain status information..)?

Anyways, just an idea.
By the way: As far as I know Specto is in the Feisty Fawn repositories.

*(I hope I posted this in the right forum..)*

---

### Post by Corvo78 on 2007-04-24
**shamefully... bumping topic**

I've installed Specto, and what I've seen and read so far - this should be possible.
However, I cannot seem to get it to work. Has anyone else tried it or something similar?

---

### Post by Beastofomous on 2009-02-04
I know sorry for the epic old bump but I recently installed HellaNZB and am trying to get it to work with specto as well, any luck from anyone?

---

### Post by G|N| on 2009-02-05
I never used hellaNZB before, but i if it creates a new folder when a download is finished, it should be possible to add a "folder watch" and let specto watch the parent directory.

there was a new specto release (0.3) with a new file and folder watch....now you can actually see what changed.

Maybe you should try it out:
[http://code.google.com/p/specto/downloads/list](http://code.google.com/p/specto/downloads/list)

If this doesn't work, post a message here and i will try to find a way to let specto notify you! :)

---

### Post by Beastofomous on 2009-02-05
well I just tried it out to no avail, made it watch the completed downloads directory but for some reason it seems to be constantly updating. If i set specto to check for an update every second, it will tell me every second that its been updated, every minute it will tell me every minute, and so on. could be im just doing something stupid and not thinking, let me know

thanks in advance

---

### Post by G|N| on 2009-02-05
> **Beastofomous said:**
> well I just tried it out to no avail, made it watch the completed downloads directory but for some reason it seems to be constantly updating. If i set specto to check for an update every second, it will tell me every second that its been updated, every minute it will tell me every minute, and so on. could be im just doing something stupid and not thinking, let me know

thanks in advance

are you using specto 0.2?
There was a bug that folders with special characters were always marked as new so you should really upgrade to 0.3

Can you post or pm me the list of the directory names in the downloads directory?

---

### Post by Beastofomous on 2009-02-05
got it going now, you were right one of the directories had a '-' in it but upgrading to 0.3 solved everything for me.

thank you so much for the timely and knowledgeable response, gotta love the ubuntu community!

---

