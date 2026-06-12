---
title: "clamav clamdscan and ExcludePath"
date: 2009-02-13
forum: Security
---

### Post by mohnkern on 2009-02-13
I'm having to run clamdscan on some machines (i know mostly pointless)

I decided to run clamdscan (and clamd) on the machines.

in /etc/clamd.conf I have:

ExcludePath ^/sys/


and I invoke clamdscan with:

clamdscan /

Yet it is still scanning /sys on the machines.  Shouldn't it skip all of the /sys directory?

---

### Post by mohnkern on 2009-02-13
For those that might be reading this...

I spoke with someone, and we hit a bug in version .94 of clamav.

in /etc/clamd.conf ExcludePath directives need to be:

ExcludePath ^//{directory}/

Not

ExcludePath ^/{directory}/

Supposedly a fix will appear in .95

---

