---
title: "Kernel Panic after 5-Jan-2012 Updates"
date: 2012-01-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2012-01-05
Last night...
[LIST]
[*]updated my Precise install
[*]surfed the web for a few hours
[*]shutdown my pc and went to bed
[/LIST]
This morning...
[LIST]
[*]awoke and turned on my pc
[*]boom! kernel panic in Ubu 12.04 (both Linux 3.1 & 3.2)
[*]Ubu 10.10 (Linux 2.6) is working fine
[/LIST]
I don't see any complaints in this forum, so I have a *feeling* it's a matter of "bad timing" on my part, e.g. updates were out of order, in the repos, when I did the update.

Anyone else experiencing this?!?!?

---

### Post by oly on 2012-01-05
yeah i am getting this as well, something along these lines.
init: log.c:291: Assertion failed in log_io_error_handler: err->number == EIO

then soething like this

init: Caught abort, core dumped
init: io.c:1312: Unhandled error from nih_io_destroy:Bad file descriptor

then goes into kernel panic

Kernel Panic - not syncing:attempted to kill init!
Pid: 1, comm: init Tainted: P       C O 3.2.0-7-generic #13 ubuntu
then into call trace 

guessing its something todo with the init system rather than kernel just not sure what may be causing, tried different kernels and recovery mode if i am booting to desktop it fails, but i can get root terminal with networking to work.

---

### Post by VinDSL on 2012-01-05
I looked at the backtrace, while brewing my first pot of "black magic"...  :D

It appears that the kernel panic is taking place when the network manager is started, which would be Wicd, in my case.

Thus, on first blush, it looks like the 5-Jan-2011 updates borked Wicd, or vice-versa (depending on how you look at it).

Developing...

---

### Post by VinDSL on 2012-01-05
> **oly said:**
> yeah i am getting this as well, something along these lines.
init: log.c:291: Assertion failed in log_io_error_handler: err->number == EIO

then soething like this

init: Caught abort, core dumped
init: io.c:1312: Unhandled error from nih_io_destroy:Bad file descriptor

then goes into kernel panic

Kernel Panic - not syncing:attempted to kill init!
Pid: 1, comm: init Tainted: P       C O 3.2.0-7-generic #13 ubuntu
then into call trace
Exactly!  Thank you!

Are you using Wicd as your network manager, too?

---

### Post by oly on 2012-01-05
nope, but i noticed samba init script failed, so i went into /etc/init/ and removed smbd.conf and samba4.conf and now it boot to a black screen \o/ 

guessing thats something todo with ati card, what ever happend to failsafe x though ?

---

### Post by oly on 2012-01-05
actually not so sure, think its still erroring the same but at a later stage so perhaps there is another script, or the init errors are not related to the panic.

what hardware do you have ? i am using a dell studio 1749

---

### Post by VinDSL on 2012-01-05
> **oly said:**
> what hardware do you have ? i am using a dell studio 1749
Top-of-the-line gaming machine, circa 2005. LoL!

See my sig...  ;)

---

### Post by oly on 2012-01-05
the hardware not even slightly similar, so not that likely to be hardware related

---

### Post by oly on 2012-01-05
lol, i found out startx works from terminal, so i tried lightdm that failed so i tried removing and installing gdm, that works better but both result in the mouse not working only the keyboard, and it does not fix normal boot rather strange.

---

### Post by oly on 2012-01-05
Yay i am back up and running, i noticed when removing files the init scripts where not being removed and some should not have been there any longer, so i found the command below, basically it find all the packages that have been removed and runs a purge on them to make sure all settings and files are removed after this my system booted, i did this in recovery terminal not 100% sure it was the init but obviously some rogue file lying around on my system causing the issue for me at least.

```
dpkg -l |awk ‘/^rc/ {print $2}’ |xargs sudo dpkg --purge
```

---

### Post by paul_in_london on 2012-01-05
Just checked - ok here.

Still able to reboot 3.2.0-7 (64 bit) normally after latest updates.

---

### Post by ventrical on 2012-01-05
> **oly said:**
> yeah i am getting this as well, something along these lines.
init: log.c:291: Assertion failed in log_io_error_handler: err->number == EIO

then soething like this

init: Caught abort, core dumped
init: io.c:1312: Unhandled error from nih_io_destroy:Bad file descriptor

then goes into kernel panic

Kernel Panic - not syncing:attempted to kill init!
Pid: 1, comm: init Tainted: P       C O 3.2.0-7-generic #13 ubuntu
then into call trace 

guessing its something todo with the init system rather than kernel just not sure what may be causing, tried different kernels and recovery mode if i am booting to desktop it fails, but i can get root terminal with networking to work.


  My  wired ethernet shut completely down yeterday.  I installed two different drives and  they worked great with Kubuntu .. etc.. but not with Ubuntu 12.04. So what I did was  boot from <recovery mode> from GRUB and then that fixed the problem straightaway. Also I could not boot into GNOME classic and got the kernel panic there.

---

### Post by VinDSL on 2012-01-06
So far, no joy...

Worst case:  I'll hang in the +1 threads until alpha 2 arrives (2-Feb-2012 ???) and do a fresh install.

Actually, I've been using Peppermint on my pocket pc lately... and 10.10 on the desktop doesn't look so bad.  LoL!

---

### Post by dino99 on 2012-01-06
seems different of your issue , but can be usefull for other kernel panic with intel issue:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzk](http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzk)

---

### Post by VinDSL on 2012-01-06
> **dino99 said:**
> seems different of your issue , but [...]
Thank you, my friend!

Once again, you pointed me in the right direction -- Google.  LoL!  :D

I did a Google Search for 'Ubuntu kernel panic' and limited the results to the past 24 hours.  This thread was in the #1 slot, however...

There were 420 results.  This one provided the workaround:  [log.c Assert failed - err=>number == EIO]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/912558")

> Whilst booting, init has an issue and causes a core dump -> kernel panic.

**[COLOR="DarkRed"]Appending [COLOR="Blue"][SIZE="+1"]--no-log[/SIZE][/COLOR] to the kernel cmd line allows a successful boot.[/COLOR]**

*(emphasis added by VinDSL)*

I'm logged into Ubu 12.04 now, where I can do some forensics.

Thanks, again!  ;)

---

### Post by dino99 on 2012-01-06
> **VinDSL said:**
> Thank you, my friend!

Once again, you pointed me in the right direction -- Google.  LoL!  :D

This one provided the workaround:  [log.c Assert failed - err=>number == EIO]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/912558")



I'm logged into Ubu 12.04 now, where I can do some forensics.

Thanks, again!  ;)

hey you are a smart guy :)
thats good you point that report :)

---

### Post by Harry33 on 2012-01-06
New version of upstart (1.4-0ubuntu2) might help here:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/912558](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/912558)

This is in Launchpad now:
[https://launchpad.net/ubuntu/precise/+source/upstart/1.4-0ubuntu2](https://launchpad.net/ubuntu/precise/+source/upstart/1.4-0ubuntu2)

---

### Post by VinDSL on 2012-01-06
> **Harry33 said:**
> New version of upstart ([COLOR="Blue"]1.4-0ubuntu2[/COLOR]) might help here:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/912558](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/912558)

This is in Launchpad now:
[https://launchpad.net/ubuntu/precise/+source/upstart/1.4-0ubuntu2](https://launchpad.net/ubuntu/precise/+source/upstart/1.4-0ubuntu2)
It's starting to make more sense now, since hooking-up with James Hunt (James = Upstart Maintainer)...  ;)

> Changelog

upstart ([COLOR="Blue"]1.4-0ubuntu2[/COLOR]) precise; urgency=low

  * init/main.c: Temporarily disable default job logging whilst
    investigating bug 912558 (can be re-enabled with _temporary_ '--log' option).

 -- James Hunt <james.hunt@ubuntu.com>   Fri, 06 Jan 2012 16:11:23 +0000

Extra credit reading:  [&#8220;upstart&#8221; package in Ubuntu - Precise]("https://launchpad.net/ubuntu/+source/upstart")

[QUOTE=James Hunt]@VinDSL: Thanks very much! Your result proves the theory [...][/QUOTE]

More extra credit reading:  [Finish Upstart]("https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-finish-upstart") (James = Assignee)

[QUOTE=James Hunt]@Kaulbach: Thank you for taking the time to transcribe the panic.

**[COLOR="DarkRed"]A full fix for this problem has already been written[/COLOR]** but requires new test cases to be written too (it also requires the full test suite to be run extensively).

Rest assured, **[COLOR="DarkRed"]we intend to put out an updated Upstart package as soon as possible with logging re-enabled[/COLOR]**.[/QUOTE]

I'm on the trot right now, but will give the Launchpad Upstart package a try when I get back to my pc.

The thing is, that Launchpad Upstart package was released 8 hours ago, and James Hunt wrote the above replies 4 hours ago.

Going by the time stamps, and reading between the lines, I have a *feeling* that a permanent fix is still in the works, and may take quite some time to achieve.

[s]In standard "U+1 Tester" fashion, I'll probably just downgrade to a previous version, pin it, and keep on truckin'...[/s]  :)

---

### Post by VinDSL on 2012-01-07
Just got home and updated the Upstart Package from 1.4-0ubuntu1 **->** 1.4-0ubuntu2

No more kernel panic!!!

Thanks, to all, for helping me think through the problem!

Special thanks, to James Hunt for issuing the workaround!

Marked as [Solved]...

---

