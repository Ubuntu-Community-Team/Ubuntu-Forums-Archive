---
title: "New Darter Boot Hangup"
date: 2007-04-05
forum: System76 Support
---

### Post by shaft350x on 2007-04-05
My wife just got her darter a few days ago.  For some reason now when it tries to boot up it gets about halfway done (according to the bar) and freezes.  It did this in the middle of class while she was taking notes.  I wasn't sure if maybe she put it into hibernate or something but she said she did not put it into hibernate.

I tried booting into safe mode and it locks up giving me:
```

[17179594.272000]  BUG: soft lockup detected on CPU#0!

```

I managed to get it running again only after rebooting enough times that it ran an fsck! automatically.

Is this something that I can fix or do we need to send this back in?

It is getting to be crunch time for classes and we really need this laptop working.

Thanks a bunch.

---

### Post by shaft350x on 2007-04-05
Just tried to boot from a LiveCD

```

[17179642.156000]  BUG: soft lockup detected on CPU#0

```

I am not an expert but this seems to indicate to me this may be a hardware issue?

---

### Post by shaft350x on 2007-04-05
Found the problem and a solution.  The wireless switch was off.  Turned it on and was able to boot.

Thread here:
[http://ubuntuforums.org/showthread.php?p=2408189#post2408189](http://ubuntuforums.org/showthread.php?p=2408189#post2408189)

Though I would think the computer should be able to load regardless of the state of the wireless...

---

### Post by thomasaaron on 2007-04-06
There is a bug connected to suspending and the wireless switch, but we've not heard of that manifestation of it. Generally, it seems to be causing issues with Network Manager.

You might want to contact us at support<at>system76.com and report it so that we can help if you have any further problems.

Best,
Tom

---

