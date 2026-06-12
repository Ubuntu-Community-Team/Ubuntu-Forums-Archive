---
title: "Ardour hangs on export"
date: 2011-07-08
forum: Ubuntu Studio
---

### Post by uPilger on 2011-07-08
Hi,
after update to ubuntu studio 10.10, I have problems to export from
Ardour. Also on a fresh installation on ubuntu studio 11.04!

Ardour freezes and can only closed bei killing the process.

In this case, I've found the Error from Jack:
JackPosixSemaphore::TimedWait err = Connection timed out
JackFreewheelDriver::ProcessSync SuspendRefNum error

Now, I've compared my Systems, and find out, that is, perhaps an
Jack-Error in connection with alsa. Then this Error occures not on a
system with ffado.

Here are some Info's:
Dist: 11.04/32bit /also on 64bit
Kernel: 2.6.38-8-generic-pae/
Alsa: 1.0.23
jamin: 0.97.14
Ardour: 2.8.11/7387
jackdmp version 1.9.7 tmpdir /dev/shm protocol 8

When I replace jackd 1.9.7 with 0.119
the export works fine, but the system is not so "smoove" (many xruns)
and can at one machine not be run in RT.

I've also try to install the latest 1.9.7 from Source, but probably this
version is eqal to the ubuntu sources.

What can I dio to fix this issue?

Best regards,
Jörg

---

