---
title: "Finding the root directory with dd"
date: 2012-09-12
forum: Server Platforms
---

### Post by awacs on 2012-09-12
I have a trashed hd - won't mount, using fsck just barfs more and more errors. Tried various superblocks. 

I'd like to just recover the root directory, so I can figure out what data I need to replace. I guess I'm stuck with dd. Anyone can give me a clue where to look on the disk?

Thanks!

---

### Post by HugoSerrano on 2012-09-12
Suggestion (use it at your own risk): 
do a backup with DD.
After try to use a tool called testdisk to recover/fix something.

Regards!

---

### Post by darkod on 2012-09-12
What do you mean by where to look? 

If you know the root partition (like for example /dev/sda1), that's all you need to dd.

If you don't, and there is no way to find out, I guess the only choice is to dd the whole disk but that can take a while depending on the disk size.

---

