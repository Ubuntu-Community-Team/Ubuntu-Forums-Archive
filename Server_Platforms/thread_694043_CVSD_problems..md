---
title: "CVSD problems."
date: 2008-02-11
forum: Server Platforms
---

### Post by fracturedmorals on 2008-02-11
Hi all. I've been setting up a Gutsy server and have thus far been quite successful. However, I've run into quite a few stumbling blocks with the CVSD chroot jail.

I'm restoring my CVS repository from a backup of the old one, and I'm currently stuck at a point where I can log in to the repository just fine, but can't seem to be able to perform any operations on it (i.e. "cvs co blah") without getting the error:
"setgid failed: Operation not permitted"

I checked the cvsd FAQ and found the problem, but there seems to be no real solution offered.

I was wondering if anyone else might have had the same problem, and if so, how do I get out of this.

I'm beginning to wonder if I shouldn't just do cvs "The old-fashioned xinetd way".

--Ian:confused:

---

### Post by fracturedmorals on 2008-02-11
bump

---

### Post by fracturedmorals on 2008-02-12
anybody?

---

