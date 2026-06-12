---
title: "gdb 6.8-debian crashes almost all the time?"
date: 2009-02-20
forum: Ubuntu Dev Link Forum
---

### Post by getcho on 2009-02-20
Hello there,
I was using Debian Etch AMD_X64 for 1 year and I was happy with its gdb. It was nice gdb, rare crashes and stable indeed. However one of my projects required epoll and I had to upgrade to Lenny version. Later I realized I just needed to download the epoll.h file but anyways. So I upgraded to Lenny and with it gdb 6.8 came. URGH! It was awful! When debugging c++ code with a lot of shared objects and dynamic_casts it crashed almost on every 5 minutes! So I went desperate and  I moved to Ubuntu 8.04. Wow! What a great step ahead! I remember Ubuntu 6.x and it was not so impressive. But that 8.04 rocks! Well ... it seems this Ubuntu uses the same crappy gdb as Debian Lenny. So I started to develop my projects and that gdb crashed almost on every 2 minutes! If it does not crash it writes something like that "trapped at siglongjmp" and it switches the thread context. And then I cannot do anything but restart the debugee. The most astonishing thing was - NO ONE was complaining about gdb! No threads about that on gdb forums, neither on gdb irc channel, nothing! Whats the problem there? No developers for Debian or Ubuntu or I am a loser? Well ... today I decided to get a newer version of gdb. I took gdb-weekly-6.8.50.20090217 cvs snapshot and I managed to compile it. And miracle! It works fine! No more siglongjmps, no more core dumps of gdb! It is stable and fully capable for debugging!
All I want to say here is: does gdb 6.8-debian crash at high rate or my system is somewhat crappy?
Thank you for reading :D

---

