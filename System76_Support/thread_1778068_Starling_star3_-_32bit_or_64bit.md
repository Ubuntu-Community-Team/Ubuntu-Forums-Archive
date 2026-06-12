---
title: "Starling star3 - 32bit or 64bit"
date: 2011-06-08
forum: System76 Support
---

### Post by Dave_L on 2011-06-08
My Starling model star3 was shipped with Ubuntu Netbook Remix 10.04, 32-bit edition.

```
$ getconf LONG_BIT
32
```

The CPU seems to be 64-bit:

```
$ sudo lshw | grep "description: CPU" -A 12 | grep width
          width: 64 bits
```

If I upgrade to 11.04, should I use the 32-bit edition or the 64-bit edition?

---

### Post by Jpenguin on 2011-06-08
Are you sure it shipped with 32-bit?  I thought S76 always installed 64-bit...

```
uname -a
```

---

### Post by Dave_L on 2011-06-08
```
$ uname -a
Linux HOSTNAME 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
```

The "i686", I believe, indicates 32-bit, as does the LONG_BIT value posted earlier.

---

### Post by Jpenguin on 2011-06-08
Can't say for sure, but I thought i386 was 32-bit...

My 32-bit mac give--
> josh-dyes-computer-2:~ jpenguin$ uname -a
Darwin josh-dyes-computer-2.local 10.7.0 Darwin Kernel Version 10.7.0: Sat Jan 29 15:17:16 PST 2011; root:xnu-1504.9.37~1/RELEASE_I386 i386



My 64-bit kubuntu box gives
> jpenguin@kubuntu:~$ uname -a
Linux kubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by Dave_L on 2011-06-08
> **Jpenguin said:**
> Can't say for sure, but I thought i386 was 32-bit...

Correct, and so is i686.

---

### Post by isantop on 2011-06-08
We shipped 10.04 Netbook edition in 32-bit because there was no 64-bit version available. Your Starling does have a 64-bit compatible CPU, and we do now recommend 11.04, 64-bit.

---

### Post by Dave_L on 2011-06-08
Thanks :)

---

