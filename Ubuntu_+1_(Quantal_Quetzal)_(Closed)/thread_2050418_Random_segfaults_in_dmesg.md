---
title: "Random segfaults in dmesg"
date: 2012-08-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-08-30
Is anyone else seeing random segfaults in dmesg?

I've been getting random application crashes, lockups, etc., and in dmesg I'm seeing things like:

[  484.777553] pool[4765]: segfault at 8 ip 00007f65349ddc7d sp 00007f652172e920 error 6 in libsoup-2.4.so.1.5.0[7f653498a000+a0000]

The process is not the same; I've seen pulseaudio, libecal, libc, ...

I've also had a soft lockups in one of my CPUs (CPU0 of the two cores, hyperthreading).

This has happened with each of the -13 kernels.

(Firefox also just died - Lazarus is an excellent extension. :))

---

### Post by jfernyhough on 2012-08-30
Another one:

[ 3574.913316] evince-thumbnai[7465]: segfault at 7f48ffd1749d ip 00007f4842094557 sp 00007fff0011d030 error 4 in ld-2.15.so[7f484208c000+22000]

Plus firefox when run from a terminal (same for Aurora and Nightly):

“firefox-trunk” terminated by signal SIGSEGV (Address boundary error)

---

### Post by dino99 on 2012-08-31
i only get that error since 28 august:

(midori4:3079): libsoup-CRITICAL **: soup_message_headers_append: assertion `value != NULL' failed

---

### Post by jfernyhough on 2012-08-31
Things seem to have settled a little, at least for now. Could be one of two things. First, there was a gvfs update today (there was one two days ago when these problems started). Two, I switched my shell back to zsh from fishfish.

---

