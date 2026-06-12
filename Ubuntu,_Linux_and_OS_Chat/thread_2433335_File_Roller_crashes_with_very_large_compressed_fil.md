---
title: "File Roller crashes with very large compressed files"
date: 2019-12-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Alistair George on 2019-12-17
I have been using File Roller for years and it consistently crashes on various OS from Mint through Elementary if the file is large or has many entries eg 100Gb.
For example, I use bash to produce a largefile.tar.gz 
Afterwards, I use FR to open the file it sits there for ~ 10 minutes opening the file then crashes.
When I open FR with terminal: 'sudo file-roller'  here is the error same operation:
(file-roller:7236): GLib-ERROR **: /build/glib2.0-vjeLfL/glib2.0-2.48.2/./glib/gmem.c:165: failed to allocate 134217728 bytes
Trace/breakpoint trap (core dumped)

Clearly some memory error. Any way around this?

file-roller --version
file-roller 3.16.5

---

### Post by mörgæs on 2019-12-23
File-roller 3.16 is from back in the 16.04 days.

As a first step in troubleshooting: Try installing 19.10, for example in a dual boot, and see how today's version 3.32 behaves.

---

### Post by Alistair George on 2019-12-26
OK the plot thickens. Note that the archive is huge, with thousands of files. In the past File Roller has crashed with much smaller though. But moving on...
I will open a new thread as the situation has changed and its not just File Roller playing up....
Here is the new thread [Rsync problems on huge collection of local files]("https://ubuntuforums.org/showthread.php?t=2433857")

---

