---
title: "High I/O Wait After Login"
date: 2011-01-15
forum: Ubuntu One (CLOSED)
---

### Post by Jackson Tan on 2011-01-15
Shortly after logging into Ubuntu (10.04), the System Monitor started to show high I/O wait activity, levelling at about 50% of the graph (presumably because I use a dual-core laptop). At the same time, the hard disk read/write indicator light is lit. The program iotop revealed the Ubuntu One Sync Daemon to be the one responsible. Presumably the Ubuntu One is trying to hash the files (since it occurs even if I'm disconnected).

Now, the problem with this is that this intense hard disk hogging can take up to two or three minutes, which makes Ubuntu insufferably slow. Opening Firefox is okay, but the browser is constantly greyed out and lags horribly. It reminds me of those Windows days when I try to use my computer while a virus scanner is grinding my hard disk.

Given that I often shut down my laptop when I don't use it (about 3 to 4 times a day), this makes Ubuntu lose much of its lustre. So my question: is this normal behaviour, i.e. are other people experiencing such a situation as well?

---

### Post by bonzini on 2011-01-23
Jackson, I experience a similar slow startup.  Mine lasts for about a minute or so.  Kinda reminds me (not so fondly) of those old Windoze days, though I hasten to add that having Ubuntu One watching over my files is WAY preferable to having a bunch of Windoze crapware running in the background.

---

### Post by Jackson Tan on 2011-01-23
True, knowing that it is a program that you use and not a bunch of unknown processes is more reassuring, but nonetheless it is rather dampening to have a Linux system behave like Windows. Furthermore, as some have expressed in other threads, Dropbox does not suffer this issue.

I'm all for Canonical to find ways to sustain their business. That's why I'm willing to use Ubuntu One (paid account) over Dropbox. Nonetheless, I think the product should not have such burdens.

---

### Post by Jackson Tan on 2011-02-01
Hi all,

I've posted this problem in [Ask Ubuntu]("http://askubuntu.com/questions/24074/high-i-o-wait-after-login") as well, and some Ubuntu One staff responded. This is his response:

> It is a known issue in ubuntuone-syncdaemon versions prior to  what's  currently in Natty. We're working on getting backports of the  fix to  this (and many more) issues backported to 10.04; unfortunately  we didn't  make it in time for 10.04.2, but we'll try to get things into  a PPA  soon (within a month or so). I'll update this answer when we do  that.

So quite possibly we'll see a remedy of the issue in the coming months.

---

### Post by markseger on 2011-11-03
Don't get fooled by thinking iowait is an indication of a slow anything.  It's perfectly normal on a system doing a lot of I/O.  All it means is the only thing the cpu was doing during a timeslice was i/o.  If things are slow, it has to be something else!  Run something like collectl and look at what it says is going on.
-mark

---

