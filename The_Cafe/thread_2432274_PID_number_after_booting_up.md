---
title: "PID number after booting up"
date: 2019-11-29
forum: The Cafe
---

### Post by Skaperen on 2019-11-29
when you boot up, what is a typical PID number *your* system gets up to?

i rebooted my Xubuntu 18.04 LTS (bionic) system 4 times, this evening.  3 for doing an upgrade (i usually reboot once before the actual upgrade and twice afterward) and 1 more to test a change in some my own custom boot up scripts.  this last boot up got to PID **11868**.

if your boot up starts a terminal (mine starts 47 of them over 8 users) the last one can tell you by doing "echo $$" on the shell in it.

---

