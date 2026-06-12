---
title: "parse error from apt-get (hoary)"
date: 2005-04-04
forum: Repositories &amp; Backports
---

### Post by maestrocalhoun on 2005-04-04
trying to install packages with apt-get I now get this error

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 22551 package `ubuntu-base':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

The packages seem to be downloading fine with they won't dpkg or install. Trying dpkg on a regular .deb file doesn't work either, any help I can get would be appreciated

---

### Post by ubuntu_demon on 2005-04-04
check whether you have omitted "main" in these lines of your /etc/apt/sources.list and add them if necessary:
```

deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

```

sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install ubuntu-base ubuntu-desktop
sudo apt-get dist-upgrade

---

### Post by primeirocrime on 2005-04-07
I've got a similar problem. Every other operation I do with apt, synaptic or update manager turns that output message. CAn't install or uninstall or update or whatever. I'm totally aptless.

---

### Post by mendicant on 2005-04-08
Well, what's line 22551 of /var/lib/dpkg/status?  It seems like that file may be corrupt.  You can try copying it somewhere safe, and attempting a repair.  Just be sure to back it up before you do anything.  It's fairly easy to edit.  The only trick is knowing what's actually installed, if it's really screwed up.  If only part of a line is screwed up, it's pretty obvious.  You can also try looking at status-old in the same directory.  It may be fine.  Just be sure to back everything up, first.  Oh, and did I mention you should back up those files, first?  And you should definitely copy status-old before you do anything, since status-old may actually be fine.

---

### Post by primeirocrime on 2005-04-08
I tried this from this [thread](http://ubuntuforums.org/showthread.php?t=24608)  and it worked:

```
sudo dpkg --clear-avail
```


backup important stuff though, one never knows the inner workings of them electrical creatures...

---

### Post by ubuntu_demon on 2005-04-09
please read this thread :
[http://www.ubuntuforums.org/showthread.php?t=23624](http://www.ubuntuforums.org/showthread.php?t=23624)

If there are still problems let me know!

---

