---
title: "Security UbuntuServer PaX + SSP in comparison GentooHardened?"
date: 2009-11-30
forum: Security
---

### Post by Corvinian on 2009-11-30
Hello,

does someone know how much Ubuntu 9.10 Server-Edition is hardened?
And why a hardened Gentoo-System scores much better with 'paxtest'?

From my Gentoo-experience I run paxtest on both systems and the
results on GentooServer was not very promising.

Ubuntu Server:


```
PaXtest - Copyright(c) 2003,2004 by Peter Busser <peter@adamantix.org>
Released under the GNU Public Licence version 2 or later

Mode: blackhat
Linux svr1 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

Executable anonymous mapping : Killed
Executable bss : Killed
Executable data : Killed
Executable heap : Killed
Executable stack : Killed
Executable anonymous mapping (mprotect) : Vulnerable
Executable bss (mprotect) : Vulnerable
Executable data (mprotect) : Vulnerable
Executable heap (mprotect) : Vulnerable
Executable shared library bss (mprotect) : Vulnerable
Executable shared library data (mprotect): Vulnerable
Executable stack (mprotect) : Vulnerable
Anonymous mapping randomisation test : 12 bits (guessed)
Heap randomisation test (ET_EXEC) : 13 bits (guessed)
Heap randomisation test (ET_DYN) : 16 bits (guessed)
Main executable randomisation (ET_EXEC) : 10 bits (guessed)
Main executable randomisation (ET_DYN) : 10 bits (guessed)
Shared library randomisation test : 10 bits (guessed)
Stack randomisation test (SEGMEXEC) : 19 bits (guessed)
Stack randomisation test (PAGEEXEC) : 19 bits (guessed)
Return to function (strcpy) : Vulnerable
Return to function (strcpy, RANDEXEC) : Vulnerable
Return to function (memcpy) : Vulnerable
Return to function (memcpy, RANDEXEC) : Vulnerable
Executable shared library bss : Killed
Executable shared library data : Killed
Writable text segments : Vulnerable
```Gentoo:

```
PaXtest - Copyright(c) 2003,2004 by Peter Busser <peter@adamantix.org>
Released under the GNU Public Licence version 2 or later

Mode: blackhat
Linux gentoo1 2.6.20-hardened-r6 #3 SMP Mon Oct 8 15:21:38 UTC 2007 i686 Intel(R) Core(TM)2 Duo CPU T5250 @ 1.50GHz GenuineIntel GNU/Linux

Executable anonymous mapping : Killed
Executable bss : Killed
Executable data : Killed
Executable heap : Killed
Executable stack : Killed
Executable anonymous mapping (mprotect) : Killed
Executable bss (mprotect) : Killed
Executable data (mprotect) : Killed
Executable heap (mprotect) : Killed
Executable stack (mprotect) : Killed
Executable shared library bss (mprotect) : Killed
Executable shared library data (mprotect): Killed
Writable text segments : Killed
Anonymous mapping randomisation test : 17 bits (guessed)
Heap randomisation test (ET_EXEC) : 13 bits (guessed)
Heap randomisation test (ET_DYN) : 23 bits (guessed)
Main executable randomisation (ET_EXEC) : No randomisation
Main executable randomisation (ET_DYN) : 15 bits (guessed)
Shared library randomisation test : 17 bits (guessed)
Stack randomisation test (SEGMEXEC) : 23 bits (guessed)
Stack randomisation test (PAGEEXEC) : 23 bits (guessed)
Return to function (strcpy) : paxtest: bad luck, try different compiler options.
Return to function (memcpy) : Vulnerable
Return to function (strcpy, RANDEXEC) : paxtest: bad luck, try different compiler options.
Return to function (memcpy, RANDEXEC) : Vulnerable
Executable shared library bss : Killed
Executable shared library data : Killed

```I checked these security resources:

[https://wiki.ubuntu.com/SecurityTeam/Roadmap/Grsecurity](https://wiki.ubuntu.com/SecurityTeam/Roadmap/Grsecurity)
[https://wiki.ubuntu.com/HardyServerSecurity](https://wiki.ubuntu.com/HardyServerSecurity)
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

- Ubuntu Server Edition uses ASLR:
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)
[https://wiki.ubuntu.com/CompilerFlags](https://wiki.ubuntu.com/CompilerFlags)

---

### Post by __p1n__ on 2009-11-30
Likely the CONFIG_PAX flags in the ubuntu kernel build are different from the gentoo kernel.  If you build your own kernel then you can easily change this at the risk of making some applications not work correctly.  You also need to choose whether to include the grsec and pax kernel modules or not.

The tool might also not fully reflect the current kernel security model implementations but in any event double-check that you're using version 0.9.7 of the paxtest tool (the most recent May 2005 build.)

---

### Post by __p1n__ on 2009-11-30
This is actually very interesting.

I'm going to build a 2.6.32 kernel including exec-shield and grsecurity2 modules and also compiled with the pie flag and boot an ubuntu 9.10 server with it.  I'll post the results with the vanilla paxtest when ready (later this week.)

I have a notion about converting paxtest into a 1-pass, multi-test recon module. It will need it's own thread manager but that's easy.

Thanks again for the topic.

---

### Post by rookcifer on 2009-11-30
It doesn't look like your Ubuntu example is even utilizing PaX based on the number of randomization bits.  Are you sure the kernel was patched with PaX?

---

### Post by Corvinian on 2009-12-02
> **__p1n__ said:**
> This is actually very interesting.

I'm going to build a 2.6.32 kernel including exec-shield and grsecurity2 modules and also compiled with the pie flag and boot an ubuntu 9.10 server with it.  I'll post the results with the vanilla paxtest when ready (later this week.)

I have a notion about converting paxtest into a 1-pass, multi-test recon module. It will need it's own thread manager but that's easy.

Thanks again for the topic.

This sound very interesting! I am curious to hear the results :)
The paxtest is the most recent version, 0.9.7-pre4-2

---

### Post by Corvinian on 2009-12-02
> **rookcifer said:**
> It doesn't look like your Ubuntu example is even utilizing PaX based on the number of randomization bits.  Are you sure the kernel was patched with PaX?

I have not compiled an own kernel, I took the default 9.10 Karmic Koala Server Kernel, and this should have (some of) the Pax-options compiled in.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

Or did I get this wrong from the resources ?
Are there any modules I need to load?

---

### Post by rookcifer on 2009-12-02
> **Corvinian said:**
> I have not compiled an own kernel, I took the default 9.10 Karmic Koala Server Kernel, and this should have (some of) the Pax-options compiled in.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

Or did I get this wrong from the resources ?
Are there any modules I need to load?

No that's not PaX, it's simply built-in features of the kernel itself.  Yes, it does some of the same things as PaX does, but it's not actually PaX.  For instance, PaX's ASLR is stronger than what is provided natively by the kernel.  The native kernel will also enable the NX bit, but it's settings are not as strict or thorough as what PaX enables.  Basically, the native kernel can do some of what PaX does, but PaX does more and does it better.  You can look at PaX's Wikipedia page for more info.

In order to use PaX, you will have to manually patch the kernel yourself.  Personally, I wouldn't worry with it, for I think what Ubuntu has done with utilizing the built in ASLR, NX, RELRO, and binary hardening is enough.

---

### Post by Corvinian on 2009-12-03
Thanks for clarifying this. :)

---

### Post by __p1n__ on 2009-12-03
Update:

1) Generic lenny 2.6.28 test results: only 1 case pass = epic fail
2) Recompiled generic lenny 2.6.28 + grsecurity2 = TBD
3) Ubuntu 9.10 = TBD
4) Recompiled ubuntu 9.10 + grsecurity2 = TBD

I'll finish the lenny test tonight and do the ubuntu tests tomorrow.

---

