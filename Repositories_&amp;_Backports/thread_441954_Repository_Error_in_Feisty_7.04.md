---
title: "Repository Error in Feisty 7.04"
date: 2007-05-13
forum: Repositories &amp; Backports
---

### Post by joep on 2007-05-13
Hi I mucked up my repository list.

E: Type '“deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

:confused:

---

### Post by joep on 2007-05-13
Hi found the answer.

sudo gedit /etc/apt/sources.list

Just went there and found the problem . :)

---

