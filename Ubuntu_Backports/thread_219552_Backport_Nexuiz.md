---
title: "Backport Nexuiz?"
date: 2006-07-20
forum: Ubuntu Backports
---

### Post by sharperguy on 2006-07-20
I noticed that nexuiz was in the edgy repos, but not dapper, it wouldmake it much easyer to install if it was.

---

### Post by mlind on 2006-07-20
Did you try installing it from Edgy's repositories?

---

### Post by sharperguy on 2006-07-20
Ill try it....

it depends on a newer version of libc6

so i guess thats what needs backported

---

### Post by mlind on 2006-07-20
> **sharperguy said:**
> Ill try it....

it depends on a newer version of libc6

so i guess thats what needs backported

Upgrading libc6 would be like shooting yourself on the foot ;)
Looks like Edgy is not binary compatible anymore..

You can build this it from Edgy's sources (or use sources from Debian upstream).
I tested it and it seems to work fine. I'd upload this too, but nexuiz-data is too big for that.. :(

---

### Post by sharperguy on 2006-07-21
nexuiz-data install fine

So if you could just upload the main package i would be fine

---

### Post by mlind on 2006-07-21
> **sharperguy said:**
> nexuiz-data install fine

So if you could just upload the main package i would be fine

nexuiz-data package from edgy? Okay, I'll upload the nexuiz package then.

---

### Post by mlind on 2006-07-21
I uploaded nexuiz package. Add this as a repository
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main

```

---

### Post by sharperguy on 2006-07-22
cheers installed great, now if only it would work with xgl + metacity

---

### Post by mlind on 2006-07-22
> **sharperguy said:**
> cheers installed great, now if only it would work with xgl + metacity

That's probably issue with xgl. If you fail to run it with gxl, you can always start another xserver without xgl stuff.

There used to be very nice HOWTO for running two different xservers (one was xgl) on Dapper development forums, but I dunno where that thread has moved since..

---

