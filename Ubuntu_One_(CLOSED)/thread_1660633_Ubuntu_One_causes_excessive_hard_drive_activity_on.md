---
title: "Ubuntu One causes excessive hard drive activity on startup?"
date: 2011-01-05
forum: Ubuntu One (CLOSED)
---

### Post by tominglis on 2011-01-05
When I have Ubuntu One enabled, it seems to spend a good 4 - 5 minutes intensively scanning my hard drive whenever I startup / restart and am connected to the internet.

During this time, I'm not able to do much else on my computer.

If I disable it, the computer starts up normally.

I have Ubuntu 10.04.1 on a ThinkPad T510 with a Seagate 7200.4 500Gb hard drive. I have my Documents folder synchronised with Ubuntu One, and it's only about 300mb in size.

Does anyone have any suggestions?

---

### Post by Jackson Tan on 2011-01-08
I'd like to add that I'm facing a similar problem, with my laptop effectively bogged down for about two minutes. It was only when I started to probe the high I/O wait before I discovered the culprit (ubuntuone-syncdaemon).

Given that I have the habit of regularly shutting down my laptop (~3 to 4 times a day), this can be quite a frustration.

I'm running on 10.04 too... does anyone else experience this problem? Is it a 10.04-exclusive issue?

---

### Post by claudios on 2011-01-30
I had the same exact problem with 10.04 and 10.10 later.
Didnt find a solution apart of stopping to use ubuntu one (ubuntuone-syncdaemon was responsible).
If you find a solution let me know.

---

### Post by wog on 2011-01-31
So far, the only solution I've seen is to go to:
System >> Preferences >> Broadcast Preferences
and uncheck "Start Services At Login".

Ubuntu One still tries to start up, but it doesn't consume as much ram or CPU.

---

### Post by Jackson Tan on 2011-01-31
I have that option unchecked already, but it is still taking awfully long.

---

### Post by Jackson Tan on 2011-02-01
Hi all,

I've posted this problem in [Ask Ubuntu]("http://askubuntu.com/questions/24074/high-i-o-wait-after-login") as well, and some Ubuntu One staff responded. This is his response:

> It is a known issue in ubuntuone-syncdaemon versions prior to what's  currently in Natty. We're working on getting backports of the fix to  this (and many more) issues backported to 10.04; unfortunately we didn't  make it in time for 10.04.2, but we'll try to get things into a PPA  soon (within a month or so). I'll update this answer when we do that.

So quite possibly we'll see a remedy of the issue in the coming months.

---

### Post by szemy on 2012-05-22
old thread still problem in ubuntu 12.04 :(
if I can help with any detail let me know

---

### Post by goaliedude3919 on 2012-05-23
I had switched over to Ubuntu One after using Dropbox fro a while. But after these problems, I just ended up switching back to Dropbox. Dropbox doesn't have as much storage, but it was definitely worth it. I haven't tried out Google Drive yet, but that I think gives 10 GB for free.

---

