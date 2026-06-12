---
title: "Synaptic Package Manager doesn't work"
date: 2007-05-15
forum: Repositories &amp; Backports
---

### Post by moisessalum on 2007-05-15
When I start the Synaptic Package Manager, this error pops up:

> 
E: Dynamic MMap ran out of room
E: Error occurred while processing xbubble (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


What can I do?

I already upgraded and updated my system, I don't know what else to do!!!! Help please!!! :confused:

---

### Post by bapoumba on 2007-05-16
[https://bugs.launchpad.net/debian/+source/apt/+bug/24626]("https://bugs.launchpad.net/debian/+source/apt/+bug/24626")

Please run:
```
$ sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by moisessalum on 2007-05-16
It worked, thanks!!!!
:lolflag:

---

### Post by mossgarden on 2007-05-21
I have similar problem... except I don't get any message. SPM just won't open (add/remove I can open but actual installing and removing... nothing happens) :confused:

I tried to run that code but it didn't work. :(

---

### Post by bapoumba on 2007-05-21
Pleaseopen a terminal (>Accessories > Terminal) and paste the output to :
```
sudo aptitude update
```

The previous command was to fix the OP's specific problem, yours might be different :)

---

### Post by smeashy on 2008-05-27
Excellent, thank you!

:)

---

### Post by smeashy on 2008-05-27
Actually, this wasn't as conclusive as i'd hoped.
Having rebooted the same problem is there. Synaptics Package Manager fails to open. This is the case when add/remove and update manager (and multimedia players attempt to retrieve codecs) try to access it too.

That command worked temporarily it seems.

---

