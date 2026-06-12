---
title: "Is there a way to speed up encryption with pycurl?"
date: 2013-01-25
forum: Security
---

### Post by markseger on 2013-01-25
I've been doing a lot of experiments and timing of uploading large files via a REST interface and while I'm leaning towards pycurl it's using over 90% of my CPU and oprofile confirms 77% of the time is in crypto which feels like a lot considering this is sustained load for almost 30 seconds.

I've tried uploading that same file with a different library and they use less time in crypto but upload rates are also slower.

I did see that pycurl is using libgcrypt.so.11.6.0 while the other library was using libcrypto.so.0.9.8 and wonder if that might be part of the difference.

Might there be a way to tell pycurl to use a different cypto library?  Or in some other way make it use less CPU?

-mark

---

### Post by thnewguy on 2013-01-26
Is your primary concern the CPU load or the amount of time for the transfer? There is likely to be a trade-off there. I don't think you can switch libraries without recompiling Phython, but you could throttle your CPU usage. It would extend the time the process takes while reducing the load from your transfer.

---

