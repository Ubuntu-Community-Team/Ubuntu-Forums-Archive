---
title: "Finding Drive Space via the Terminal..."
date: 2009-09-12
forum: The Cafe
---

### Post by MikeTheC on 2009-09-12
It's a funny thing how sometimes the simplest tool can be useful. I recently had occasion to need to remotely check available drive space on my server, and that meant checking it via a terminal window. But how to do this? Well...

[indent][font=courier]**df -h**[/font][/indent]

All you need to do is be on whatever box is of interest (your own local computer, a remote system, etc.) and then issue the command. It will return a list similar to the following:

```
Filesystem      Size   Used  Avail Capacity  Mounted on
/dev/disk0s2   233Gi   27Gi  205Gi    12%    /
devfs          110Ki  110Ki    0Bi   100%    /dev
map -hosts       0Bi    0Bi    0Bi   100%    /net
map auto_home    0Bi    0Bi    0Bi   100%    /home
/dev/disk1s2   466Gi  427Mi  465Gi     1%    /Volumes/Time Machine Partition
/dev/disk1s3   465Gi   23Gi  443Gi     5%    /Volumes/Data Storage
mikes-mbpro:~ mike$
```

And, as you can deduce from the last two items on the list above, this command also works perfectly well in Mac OS X.

Anyhow, I just thought I should share this nifty little command with the rest of you wonderful folk.

Enjoy!

---

### Post by bodyharvester on 2009-09-12
cool :)

---

### Post by MikeTheC on 2009-09-13
Yeah, I thought it was pretty cool myself.

The biggest downside I see to CLI is, of course, the lack of intuitiveness involved. It's not like there's an easy way to gain access to all these commands like you can programs in a GUI environment.

Don't get me wrong, I fully understand the concept of a terminal, and I will grant that it can be efficient, but it is only efficient after you've memorized bunches of arbitrary commands for it.

Anyhow, when you uncover a gem, it's great to share it with others.

---

