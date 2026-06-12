---
title: "subdirectory limit"
date: 2005-12-29
forum: Server Platforms
---

### Post by onami on 2005-12-29
Can someone please tell me what is the biggest number of subdirectories in a directory, or where to find this limit ?
I only found this limit for ext2/ext3 partitions which is 32000, but i also need it for reiserfs, reiser4, jfs an so on.
Thank you!

PS

i didn't know where to place this, and since this i need for a backup system, i've placed it here.

---

### Post by LordHunter317 on 2005-12-29
Why do you care?  I'm 99% positive you'll hit the limit on how long a path can be well before you hit the directory limit.

---

### Post by psusi on 2005-12-29
I was wondering why you care as well.  Supposedly reiserfs supports some ungodly number like 2 million, as if 32000 isn't already insanely huge.

---

