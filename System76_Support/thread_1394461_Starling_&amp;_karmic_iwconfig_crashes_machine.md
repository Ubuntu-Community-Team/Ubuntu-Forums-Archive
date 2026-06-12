---
title: "Starling &amp; karmic: iwconfig crashes machine"
date: 2010-01-30
forum: System76 Support
---

### Post by hoopycat on 2010-01-30
Greetings!

I got my Starling about a week ago, with 9.10 out of the factory.  Life's been overall good, and I love it muchly.

However, every time I run iwconfig (or iwlist; haven't had the guts to try any others), the system locks hard -- the screen goes blank except for a blinking cursor in the upper left, and the caps lock LED blinks ominously.  Getting out of this requires a power-cycle.

I haven't had this problem without using the command line, until today... I received a batch of Ubuntu updates, and in the middle of installing them (I can't remember which one, unfortunately!), it locked hard with the same symptoms.

Unfortunately, on a reboot, my keyboard and mouse didn't work :-(  Since I was already suspicious about the iwconfig problem, I decided to go for a reinstall from the UNR ISO.  All went well, but I am still having the iwconfig hard lock problem.  (Note that I didn't try it before I installed the System76 driver.)

Since it bit turf on normal updates, I'm somewhat nervous now, to say the least :-)

---

### Post by jdb on 2010-01-30
> **hoopycat said:**
> Greetings!

I got my Starling about a week ago, with 9.10 out of the factory.  Life's been overall good, and I love it muchly.

However, every time I run iwconfig (or iwlist; haven't had the guts to try any others), the system locks hard -- the screen goes blank except for a blinking cursor in the upper left, and the caps lock LED blinks ominously.  Getting out of this requires a power-cycle.

I haven't had this problem without using the command line, until today... I received a batch of Ubuntu updates, and in the middle of installing them (I can't remember which one, unfortunately!), it locked hard with the same symptoms.

Unfortunately, on a reboot, my keyboard and mouse didn't work :-(  Since I was already suspicious about the iwconfig problem, I decided to go for a reinstall from the UNR ISO.  All went well, but I am still having the iwconfig hard lock problem.  (Note that I didn't try it before I installed the System76 driver.)

Since it bit turf on normal updates, I'm somewhat nervous now, to say the least :-)

It sounds like a kernel panic.
Bugs in code & bad hardware are the leading causes.
One high runner is bad memory or memory that isn't plugged in all the way.
You might try running a memory test or re-seating the memory.

jdb

---

### Post by cposs on 2010-01-30
I got the lock up while upgrading yesterday morning as well.  I'm pretty sure what happened is that the upgrade of the winbind package failed installing, and somehow knocked out the hal daemon, which is what kills the keyboard and mouse (X uses hal to find your input devices).  When you go to upgrade your packages it might happen again.   If it does, check out this thread:

[**Starling[star1] Mouse/tack pad broken**]("http://ubuntuforums.org/showthread.php?t=1393126")

The way I fixed it is post #12.

---

### Post by hoopycat on 2010-01-30
jdb: Indeed... it does sound like a kernel panic, but I don't know of a way to figure out exactly what's panicking.

I ran memtest86+ before the reinstall today; it passed.  I've also seen no evidence of a general problem that would lead me to suspect dodgy memory.  It can compile a kernel, and that's good enough for me ;-)

---

### Post by hoopycat on 2010-01-30
cposs:  Ah!  Shift!  I forgot about that.  Interestingly, I don't have winbind installed right now on the reinstall, but I am up-to-date as of a few hours ago.  Therefore, I suspect my iwconfig problem and the winbind problem are two different problems.

---

### Post by thomasaaron on 2010-02-01
Yes, they are two different problems.

iwconfig and opening System Monitor will cause a kernel panic. We don't know why, but it has something to with the wireless driver.

We just discovered the bug ourselves, but are considering it fairly low priority for the moment. We're still trying to get the driver put into Ubuntu upstream, and we're hoping that will fix the problem.

---

### Post by hoopycat on 2010-02-01
Thank you, Thomas!  Glad to know I'm not the only one.  :-)

---

