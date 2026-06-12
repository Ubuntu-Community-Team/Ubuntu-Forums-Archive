---
title: "Server or Desktop for a server?"
date: 2006-10-31
forum: Server Platforms
---

### Post by sroussey on 2006-10-31
I'm thinking of switching our servers from RHEL 4 to Ubuntu. However, it says in the downloads page that the server install does not have any GUI at all. Usually, we have it installed, but when not logged in locally, its not really running.

I want a kernel version that is optimized for server traffic, but on some rare occasions, want a GUI for dealing with certain settings, etc. So what do I do?

---

### Post by Swab on 2006-10-31
You can install the server version and install GUI afterwards.. it's as simple as:
```
sudo apt-get install ubuntu-desktop
```

or maybe..
```
sudo apt-get install xubuntu-desktop
```
..for something a bit more lightweight

---

### Post by ssalman on 2006-10-31
I was going to post the same thing, with one addition, turn off GDM as you don't need it.

---

