---
title: "memory upgrade and swap"
date: 2006-07-18
forum: Server Platforms
---

### Post by brownrl on 2006-07-18
I have added more memory to my server, should I change the swap partition to be 3x bigger than the new memory size?

-- Rob

---

### Post by matthew on 2006-07-18
Without specifics on your setup it's hard to give an answer. My rule of thumb is this: make the swap 1.5x the amount of ram in the machine until the swap reaches 1Gb. After that, there really isn't a good reason to make it any larger.

---

