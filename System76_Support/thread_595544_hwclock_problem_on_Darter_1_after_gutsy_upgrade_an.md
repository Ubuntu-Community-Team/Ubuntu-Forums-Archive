---
title: "hwclock problem on Darter 1 after gutsy upgrade and fix"
date: 2007-10-28
forum: System76 Support
---

### Post by dnarnold on 2007-10-28
This is to report a problem I encountered on my Darter 1 after
upgrading to gutsy, and a fix to it.

Since the gutsy upgrade I was seeing this message at boot time:

  Unable to set System Clock to: ...

I investigated and found that this was caused by the hwclock command
in /etc/init.d/hwclock.sh because the hwclock command was not working.
For example "sudo hwclock --show" would wait 5 seconds and then
time out with the message "select() to /dev/rtc to wait for clock tick timed out".

With a little research I found that the --directisa option fixed this:
"sudo hwclock --directisa --show" would respond immediately with the time.
So the fix is to add the --directisa option to the calls to hwclock in
/etc/init.d/hwclock.sh and /etc/init.d/hwclockfirst.sh.  There is
a variable hook called HWCLOCKPARS in these script that can be used for this
purpose.  Thus the fix is to change "HWCLOCKPARS=" to "HWCLOCKPARS=--directisa"
in /etc/init.d/hwclock.sh and /etc/init.d/hwclockfirst.sh

---

### Post by thomasaaron on 2007-10-29
Nice work.

I'll file that in our bag 'o tricks.

---

### Post by steveneddy on 2007-11-21
I'm having hwclock issues again. I'm off to try this repair to see how well it works.

Serval Performance Type 1
EDIT: didn't work

---

### Post by maruchan on 2007-12-27
Thanks, this part fixed my issue:

> 
a variable hook called HWCLOCKPARS in these script that can be used for this
purpose. Thus the fix is to change "HWCLOCKPARS=" to "HWCLOCKPARS=--directisa"
in /etc/init.d/hwclock.sh and /etc/init.d/hwclockfirst.sh

---

### Post by steveneddy on 2007-12-28
I have tried this to try and repair the hwclock.

Anyone think this is a battery problem?

I have even thought about going back to Feisty until Heron is released.

I wonder about getting a new battery for the MB and installing it myself.

Thoughts?

Maybe I need to go back to a 32 bit OS?

Banging my head against the counter.

Other than this and suspend stopped working again, everything seems to be working well.

Serval Type 1, Core 2 Duo, Gutsy 64 bit.

---

### Post by thomasaaron on 2007-12-28
Steveneddy,

Please see my most recent post here:
[http://ubuntuforums.org/showthread.php?t=619927&page=2](http://ubuntuforums.org/showthread.php?t=619927&page=2)

---

### Post by steveneddy on 2007-12-29
> **thomasaaron said:**
> Steveneddy,

Please see my most recent post here:
[http://ubuntuforums.org/showthread.php?t=619927&page=2](http://ubuntuforums.org/showthread.php?t=619927&page=2)

I've been down that road. It was definitely good reading, but was looking for another answer before trying a 32 bit hwclock on a 64 bit system.

I am thinking of going back to 32 bit Feisty to solve issues.

---

### Post by thomasaaron on 2007-12-31
Just as a follow-up: Steveneddy fixed the problem by installing the 32-bit hwclock.[http://ubuntuforums.org/showthread.php?t=619927&page=2](http://ubuntuforums.org/showthread.php?t=619927&page=2)

---

### Post by steveneddy on 2008-01-01
My hwclock wouldn't even click when viewing the BIOS.

Installing the 32 bit version of util-linux solved this issue.

I am running a 64 bit version of Ubuntu.

---

