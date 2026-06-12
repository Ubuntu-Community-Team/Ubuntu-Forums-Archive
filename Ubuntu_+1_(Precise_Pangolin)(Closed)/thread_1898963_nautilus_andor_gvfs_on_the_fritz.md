---
title: "nautilus and/or gvfs on the fritz"
date: 2011-12-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2011-12-22
Anyone else having a problem getting nautilus to connect to a server, e.g. a url?!?!?

Worked fine, until this morning!  I'm assuming a recent update borked it.

When I try to connect to a server, via a bookmark, nautilus says...

```
Nautilus cannot handle "sftp" locations.
```

Choosing File -> "Connect to server" I get...

```
Can't load the supported server method list.
Please check your gvfs installation.
```

gvfs installation looks fine.

Hrm...

---

### Post by cariboo on 2011-12-22
It works fine here using both ip address and hostname.

---

### Post by VinDSL on 2011-12-23
> **cariboo907 said:**
> It works fine here using both ip address and hostname.
Heh!  It's funny how the mind works, no?!?!?  :D

I finally got so time to investigate this issue, e.g. I got home from work, and...

Your response (along with a general lack of other replies) confirmed that I have a unique problem.

Checking into it further, I discovered that sftp support for gvfs is provided by the gvfs-backends package.  And, the gvfs-backends package was missing from my install.

I installed gvfs-backends and now sftp is (once again) working in nautilus.

I'll mark this thread as solved...

Thanks, cariboo!  ;)

---

