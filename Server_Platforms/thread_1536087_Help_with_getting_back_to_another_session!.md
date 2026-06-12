---
title: "Help with getting back to another session!"
date: 2010-07-21
forum: Server Platforms
---

### Post by ChromoX on 2010-07-21
So I did a do-release-upgrade and my SSH session was broken before I was finished. I logged back into another session, but of course I can't see what was going on in my other session, which was the pick your PHP.ini file. Is it safe to kill all the processes and start over? Or better yet can I switch to those pts/1, pts/2 from my new session? I do not have screen on this box because it was in the middle of updating.

Thanks.

---

### Post by dfreer on 2010-07-22
I don't know about gaining access to your previously running session (which from what I thought I understood of it, would've been terminated when you lost your connection), but you can try using the screen program in the future. That way if you lose your connection you can reattach to the existing screen.

---

