---
title: "Simple Question"
date: 2010-08-17
forum: Server Platforms
---

### Post by baudday on 2010-08-17
Solution may not be so simple...

Today I installed Ubuntu Server 10.04 on a RAID 5 setup. Everything worked great. Followed this guide to set it up so that everything would work with ISPConfig. [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3).

Everything was working great and I was setting up clients and everything when the server just went offline, so I came upstairs to check it out and couldn't really tell what was going on, so I just rebooted.

When it booted up I got the following:

```
fsck from util-linux-ng 2.17.2
/dev/md1: clean, 74060/8724480 files, 965799/34867168 blocks
```

I was a little confused by that, but left it alone for a while thinking it was doing something. It's been a while now and the same thing still shows up. I tried rebooting again, but the same message comes up. 

Does anyone know what this means? Is there something wrong or is it actually doing something? If there is something wrong, how do I fix it? 

Thanks in advance.

---

### Post by baudday on 2010-08-17
If anyone can help me with this, that would be awesome. It's pretty urgent, after Thursday I won't have access to the server.

---

### Post by Bachstelze on 2010-08-17
Try booting in "recovery mode", it's more verbose, so should give you a better idea of what's going on.

---

### Post by baudday on 2010-08-17
okay thanks for the reply! how do i do that?

---

### Post by baudday on 2010-08-17
Okay, for future reference, you hold shift before Ubuntu loads and it brings up a menu where you can choose to boot into recovery mode.

I did this and it ran through what it was doing, basically loading some scripts or something, then suddenly it's either done or just stops and the same two lines (as posted above) show up.

I'm at a complete loss and seeing as this is a new install, if I don't figure this out by tomorrow, I'll probably just reinstall.

---

### Post by Bachstelze on 2010-08-18
Kinda hard to figure out what is going on. Try booting a Live CD and fsck your partitions manually, maybe one of them is not so clean.

---

### Post by baudday on 2010-08-18
I went into the filesystem with the live cd and created /forcefsck which is supposed to execute fsck on the next boot. So then I rebooted and it seems to be running but I'm not exactly sure if it is or not. How can I be sure it's doing anything?

---

### Post by baudday on 2010-08-18
I've decided to reinstall. Just hope this doesn't happen again.

---

### Post by wynand2020 on 2010-08-18
Install Windows

---

### Post by spynappels on 2010-08-18
> **wynand2020 said:**
> Install Windows

Very helpful.

---

### Post by arrrghhh on 2010-08-18
> **wynand2020 said:**
> Install Windows

Seriously?  Go back in your hole.

---

### Post by baudday on 2010-08-18
I reinstalled. Running 3 sites on the server now no problem. Still have no idea what happened, but the server is coming in on its first full day of operation haha.

---

