---
title: "Crash in program built with address sanitizer"
date: 2019-10-29
forum: Ubuntu Application Development
---

### Post by dankegel on 2019-10-29
I'm getting this on exit of a couple of our unit tests when the library and test are built with asan:

==7297==Processing thread 7180.
==7297==Stack at 0x7ffe6adbe000-0x7ffe6b5be000 (SP = 0x7ffe6b5ba4e8).
==7297==TLS at 0x7f44b8cad4c0-0x7f44b8cae940.
==7297==DTLS 13 at 0x6080000a20000008-0x638000092000000a.
Tracer caught signal 11: addr=0x0 pc=0x7f44bf4d38b8 sp=0x7f44aedb5ce0
==7180==LeakSanitizer has encountered a fatal error.

This happens only on ubuntu 19.04 and on a Hades Canyon so far, and only with gcc-7, gcc-8, or gcc-9... but it's 100% repeatable.

When built with gcc-6, the crash does not happen.

I guess I'll try to keep narrowing it down.

---

### Post by dankegel on 2019-10-31
Still happening.  Reproduced on two Hades but not on a Skull.
It moves around a bit (to different unit test programs entirely) if I change unrelated code, but remains 100% reproducible.
It only happens in 2 out of 260 unit test programs.

I filed
[https://forums.intel.com/s/question/0D50P00004UlJdZSAV/anyone-seen-address-sanitizer-crashes-on-hades-canyon](https://forums.intel.com/s/question/0D50P00004UlJdZSAV/anyone-seen-address-sanitizer-crashes-on-hades-canyon)
since there's a chance it's hardware-specific...

---

