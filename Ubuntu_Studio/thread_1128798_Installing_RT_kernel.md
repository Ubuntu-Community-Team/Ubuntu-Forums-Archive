---
title: "Installing RT kernel"
date: 2009-04-17
forum: Ubuntu Studio
---

### Post by translucent juicebox on 2009-04-17
This doesn't have anything directly to do with lmms, but I don't want to start another topic.  How do I install the realtime kernel?  Regardless of how long I set the buffer, I get more pops and skips in the audio on a computer with 1G of RAM, and a 1.6Ghz cpu, than I ever did with FL Studio on a win98 machine. 

I downloaded the linux-rt 2.6.27.3.4 metapackage and installed it but, I still have the same old 2.6.27-11 kernel.  Was there something I was supposed to do after installing besides restarting the computer?

---

### Post by Stochastic on 2009-04-18
Moved post to it's own thread - please keep all issues to their own threads (help people watch/search topics).

You'll find that the 8.10 RT kernel has many well known issues that essentially make it useless.  If you're running an 8.10 version of Ubuntu you probably shouldn't use the RT kernel.

Most audio users refrained from upgrading to 8.10 (staying with 8.04LTS) and some are now happily (myself included) enjoying the RT kernel in 9.04 (which is set for official release on April 23rd).


One note on configuring for the RT, you'll find there's some easy controls in System -> Administration -> Ubuntu Studio Controls that allow you to set a few audio tweaks to help the RT kernel along.

---

### Post by vivichrist on 2009-05-24
I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) and
grabed the 2.6.29-4 source deb and applied the rt16 patch to it from
[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/). then copied across
the /boot/config-2.6.28-12-generic to that kernel source root directory.
did "make gconfig" and opened that config changed to full pre-emtion and
timing to 1000 like Luke Macneil has done. "make-kpkg clean" then
"CONCURRENCY_LEVEL=2 fakeroot make-kpkg --initrd --append-to-
version=-custom kernel_image kernel_headers" installed the resulting
packages headers first. and hey presto. note. CONCURRENCY_LEVEL=2
because my cpu is duel core and this required installation of certain
dev packages. this is amd64 and Jaunty based though. can point you to a few sites if you need more details.

---

