---
title: "pm-suspend over ssh"
date: 2010-08-10
forum: Server Platforms
---

### Post by emma_peel on 2010-08-10
Hello dear forum.

I would like to suspend my server remotely. When launched through SSH, the result is not perfect. The session is frozen, and  sometimes it does not work. I have notice this last bug when I use the DNS server from the server I want to suspend.

After a couple of researches on this forum, I found solutions. For example, the command can be launch in the background. Doing this, the server is always suspended, but the session is still frozen.

Does anybody know a way to do this cleanly ?

---

### Post by md81544 on 2011-09-09
```
sudo su -
$(sleep 15 && pm-suspend) &
```

...then log out of root and then your ssh session within 15 seconds

---

### Post by meonkeys on 2012-03-18
Why does that work (as opposed to running pm-suspend from an interactive shell)?

...hmm, never mind, [FONT="Courier New"]sudo pm-suspend[/FONT] over ssh seems to be working fine now, although I was originally seeing symptoms like those described by @emma_peel. Maybe it has something to do with disconnecting a VGA monitor.

---

