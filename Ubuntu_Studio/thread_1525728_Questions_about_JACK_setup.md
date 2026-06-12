---
title: "Questions about JACK setup"
date: 2010-07-07
forum: Ubuntu Studio
---

### Post by raymondvillain on 2010-07-07
Running Ubuntu Studio 64 bit, just installed Rosegarden and so I "have to start JACK" (in the words of the Rosegarden tutorial).

In the JACK setup window, the Server Path drop down box has several options.  I cannot get JACK to start if I select jackstart.  All the others work, that is, JACK will start with the server path set to jackd, jackd-realtime, or jackdmp.

What is going on with these different server paths?  If my server path is not jackstart, which is recommended in the tutorial, what am I losing?

---

### Post by thorgal on 2010-07-07
"jackstart" is a remnant of the 2.4 kernel era. At the time, "jackd" could only be started by root. jackstart was a wrokaround so that non root users could use JACK as well. I remember quite some hackish stuff to get these things to work (kernel patch for rtlimits, etc).

You can safely ignore jackstart :)

---

### Post by raymondvillain on 2010-07-07
Thanks very much, Thorgal.  I am pressing ahead.

---

