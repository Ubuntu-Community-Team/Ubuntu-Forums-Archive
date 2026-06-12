---
title: "what is &quot; [jbd2/sda1-8] &quot; writing to my HD?"
date: 2012-11-06
forum: Security
---

### Post by s1baker on 2012-11-06
hi,

when I run 
```
sudo iotop -a
```

I always see something like this being wrote to my HD

```

TID  PRIO  USER   DISK READ  DISK WRITE  SWAPIN  IO>    COMMAND
312  be/3  root   0.00 B     548.00 K    0.00%   0.67%  [jbd2/sda1-8]

```

with the Disk Write quantity constantly being increased.

Does anybody know what the command " [jbd2/sda1-8] " is?

---

### Post by lykwydchykyn on 2012-11-06
JBD2 is the "journaling block device".  It provides the journaling layer for your hard disk.

You can read more here:

[http://en.wikipedia.org/wiki/Journaling_block_device](http://en.wikipedia.org/wiki/Journaling_block_device)

---

