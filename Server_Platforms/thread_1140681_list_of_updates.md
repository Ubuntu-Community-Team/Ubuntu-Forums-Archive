---
title: "list of updates"
date: 2009-04-27
forum: Server Platforms
---

### Post by Mike V on 2009-04-27
Any one knows how to get the list of software needed to be installed after a:

```

sudo apt-get update

```

I have and offline server (dont want to use aptoncd) and want to update it, I want to download all the updates, copy them to the apt archive directory and then run

```

sudo apt-get upgrade

```

Any ideas?

Mike

---

### Post by Titan8990 on 2009-04-28
just do apt-get upgrade and then say 'no' instead of yes with proceeding.


offline server? Not sure I understand the concept.

---

### Post by EXCiD3 on 2009-04-28
Check out [Keryx]("http://keryxproject.org"). :)

---

### Post by Namtabmai on 2009-04-28
```

sudo apt-get upgrade --print-uris

```

Should do it I think. Then copy the debs into

/var/cache/apt/archives

and run upgrade as normal.

---

### Post by Mike V on 2009-04-28
Thanks Namtabmai, let me check if that works.


Titan8990
By offline I mean that is on a LAN but it can not download the deb files.

---

### Post by EXCiD3 on 2009-04-28
That will not work, your offline machine will have NO access to the latest package lists and will not be able to show you any updates. Just give Keryx a shot, i developed it for exactly your situation. :)

---

### Post by Mike V on 2009-04-28
EXCiD3

you are right, I totally forgot that, thanks

---

### Post by EXCiD3 on 2009-04-29
> **Mike V said:**
> EXCiD3

you are right, I totally forgot that, thanks

No worries, I've got dialup at home so I have plenty of experience. :popcorn: Cheers!

---

