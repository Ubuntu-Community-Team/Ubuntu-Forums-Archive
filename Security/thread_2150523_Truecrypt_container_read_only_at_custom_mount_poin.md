---
title: "Truecrypt container read only at custom mount point"
date: 2013-06-01
forum: Security
---

### Post by seul on 2013-06-01
Whenever I want to mount a truecrypt container through tc-gui, it is read-only as long as I pick my custom mount point at /media/DATA and writable when I let truecrypt pick the mount point (/media/truecrypt6 for instance).

I need /media/DATA because I use it on my other machine and want to share files and scripts in between them, some of which depend on the path. On the other machine I have no problems with custom mount points.

I tried sudo chmod 777 /media/DATA, which works as long as tc is unmounted but no longer when mounted, same for chown.

I also tried chmodding the container file, nothing helps and I am at my wit's end now.

Thanks for support!

---

### Post by seul on 2013-06-01
OK, very strange. I renamed tc-container-file and now it works.

---

