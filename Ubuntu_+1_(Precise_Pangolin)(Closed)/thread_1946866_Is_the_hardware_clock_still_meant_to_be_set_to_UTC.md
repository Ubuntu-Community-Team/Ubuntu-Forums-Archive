---
title: "Is the hardware clock still meant to be set to UTC?"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Irihapeti on 2012-03-25
Some time ago I had some problems with inconsistent time stamps that was triggering fsck on a multiboot system, to the point where I thought that a brand-new HD might be faulty.

I eventually discovered that it was being caused by the line in /etc/default/rcS which read:

```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=no
```

Changing it to "yes" solved the problems.

The default has been UTC=yes for as long as I've been using Ubuntu, and when you have a multiboot setup, having one of them different is likely to cause confusion.

My question is whether this is something that's been changed in precise. I.e. are we dealing with a bug here or a design decision. Anyone else having problems of this kind?

---

### Post by screaminj3sus on 2012-03-25
Mine says yes by default:

# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes

---

### Post by pressureman on 2012-03-26
Traditionally, most Linux distros set the hardware clock to UTC. Windows however generally sets the hardware clock to local time. Therefore, if the installer detects Windows on your computer (eg. dual boot), it will set hardware clock to local time to ensure compatibility.

---

### Post by Irihapeti on 2012-03-26
I gather now that this is what's been happening. I do have Windows on that machine. But I'd applied a registry fix to get Windows to read from UTC, for compatibility with Lucid, so I don't need the hwclock=local option.

Now that I know about it, I know what to do in future.

---

### Post by SemiExpert on 2012-03-26
Easy answer:  if you're dual booting with Windows, NO you don't want time set to UTC.

---

