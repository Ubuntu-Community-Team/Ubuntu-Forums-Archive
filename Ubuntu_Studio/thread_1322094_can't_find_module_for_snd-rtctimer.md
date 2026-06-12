---
title: "can't find module for snd-rtctimer"
date: 2009-11-10
forum: Ubuntu Studio
---

### Post by Colorado Newb on 2009-11-10
when i open rosegarden it says it can't find an appropriate low-latency timer and suggests snd-rtctimer.  i can't find this.  any ideas?

---

### Post by bkline on 2010-03-31
I'd like to know the answer to this question, too, please.

---

### Post by thorgal on 2010-03-31
try
```

sudo modprobe snd-hrtimer

```

this is the new high resolution timer module.

and check that it loaded:

```

lsmod | grep timer

```

```

cat /proc/asound/timers

```

---

### Post by bkline on 2010-03-31
> **thorgal said:**
> try
```

sudo modprobe snd-hrtimer

```

this is the new high resolution timer module.  ....

Excellent, thanks!

---

