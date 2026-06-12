---
title: "How to mount what?"
date: 2011-07-02
forum: Server Platforms
---

### Post by Beatboxx on 2011-07-02
I got a question how to mount which partition. I'm in a installation of Ubuntu server 11.04. I got 3 partitions:

[LIST=1]
[*]982.5KB ext4
[*]2TB ext4
[*]4GB swap
[/LIST]

I thaugt mount 1 as /boot, 2 as / (so root) and 3 swap. Is this right, or should I do something else?

---

### Post by Beatboxx on 2011-07-02
Ow, 1 as boot is not going to work, I guess. Can I just do 2 as root and 3 as swap, and everything works fine?

---

### Post by volkswagner on 2011-07-02
Yeah, partition one is too small for /boot.

You can do as you suggest... / on 2, and /swap on 3.

---

