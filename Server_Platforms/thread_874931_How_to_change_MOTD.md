---
title: "How to change MOTD?"
date: 2008-07-30
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-07-30
How do I change the MOTD that is displayed when a user logs in via SSH (using puTTY for example)

I can't log in as root via SSH and I dont seem to be able to set my current users permissions so that I can "vi motd"

Probably a daft newbie question but we all have to start somewhere lol

Paul

---

### Post by Dr Small on 2008-07-30
Try:
```
sudo vim /etc/motd
```

---

### Post by G1ZmO65 on 2008-07-31
Doh! Of course! keep forgetting the sudo thing lol

Thanks

Paul

---

### Post by G1ZmO65 on 2008-08-13
btw every time I reboot the server teh MOTD changes back to the default one. Is this supposed to happen?

---

### Post by /etc/init.d/ on 2008-08-13
The file you want is /etc/motd.tail.  /etc/motd seems to get overwritten by the contents of /etc/motd.tail, at least that's what I saw happening last time I tried to change the SSH banner.

---

### Post by G1ZmO65 on 2008-08-13
Thanks :)

---

