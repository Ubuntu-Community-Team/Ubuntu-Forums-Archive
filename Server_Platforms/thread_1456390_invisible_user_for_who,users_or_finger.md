---
title: "invisible user for who,users or finger"
date: 2010-04-17
forum: Server Platforms
---

### Post by adoweb on 2010-04-17
Hi, i have ubuntu 9.10 Server i386 version with desktop(gnome) installed and my problem is:
If my friend(using winscp windows app.) log-in with his account a cant see him with (users,finger or who) commands. Only in htop application i can see his account using some processes in system. But if i log-in with his account, i can see the user, no problem. So i'm confused where is problem.
So i create test account a try it and behavior is same. And can't see if my friend is log-in or not.

Thanks for Help

---

### Post by gmargo on 2010-04-17
These commands (users, finger, who) show users who are currently running a "login shell" (usually giving the user a normal interactive shell prompt).  When a "login shell" starts, an entry is written to /var/run/utmp (dont' try to read it - it's a binary format file) which is what "who" etc reads.  An "scp" session (guessing from the "winscp" name) is not a "login shell".  

The difference is "being logged in" vs. "being logged in with an interactive shell".

I've probably explained this poorly, but I think that's the reason.

---

### Post by adoweb on 2010-04-18
Thanks :) SCP is really invisible for "who,finger users"

---

