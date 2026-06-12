---
title: "'tiptop' won't run"
date: 2017-05-12
forum: Virtualisation
---

### Post by bariumbitmap on 2017-05-12
I'm running Ubuntu 16.04.1 LTS in a virtual machine. When I install 'tiptop' and run it, I just get this message on stderr:

```

syscall: Operation not permitted
Could not perform syscall.
Don't know why...

```

Any suggestions?

---

### Post by howefield on 2017-05-12
Thread moved to the "*Virtualisation*" forum.

---

### Post by bariumbitmap on 2017-05-12
> **howefield said:**
> Thread moved to the "*Virtualisation*" forum.

Ok, but I would be interested in seeing if this happens when 'tiptop' is run natively also.

---

### Post by howefield on 2017-05-13
> **bariumbitmap said:**
> Ok, but I would be interested in seeing if this happens when 'tiptop' is run natively also.

Same issue actually unless run with sudo.

---

### Post by bariumbitmap on 2017-05-15
Problem solved. Workaround for posterity:

echo 2 | sudo tee /proc/sys/kernel/perf_event_paranoid

Also, "tiptop" doesn't seem to work in virtual machines.

Fuller explanation:

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=862461](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=862461)

[URL="https://lkml.org/lkml/2016/1/11/587"]https://lkml.org/lkml/2016/1/11/587
[/URL]

---

