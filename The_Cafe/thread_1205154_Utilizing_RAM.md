---
title: "Utilizing RAM"
date: 2009-07-05
forum: The Cafe
---

### Post by sdlynx on 2009-07-05
Hi everyone,

So I have 4 gigs of RAM and I'm running 9.04 x64 plus 2 gigs swap.  At the moment I'm only using 800MB RAM maximum.  I kinda want to get the best that I can out of the RAM so anybody have any suggestions as to what I can do that would use more RAM lol?

sdlynx

---

### Post by steeleyuk on 2009-07-05
Install preload for starters.

> preload is an adaptive readahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times.

---

### Post by sdlynx on 2009-07-05
alright thanks

---

### Post by monsterstack on 2009-07-05
> **steeleyuk said:**
> Install preload for starters.

This is a great tool. Even if you have the standard amount of RAM.

---

### Post by s3a on 2009-07-05
Yes preload is very effective however, in addition to that, do the following:

sudo gedit /etc/sysctl.conf

then at the bottom of the file add the following:

vm.swappiness=0
vm.vfs_cache_pressure=1

Preload preloads things into your RAM for faster application startup speeds and the second part basically makes your computer use RAM more than swap.

---

### Post by PurposeOfReason on 2009-07-05
Install windows and play prototype. :shifty:

---

### Post by sdlynx on 2009-07-05
> **s3a said:**
> Yes preload is very effective however, in addition to that, do the following:

sudo gedit /etc/sysctl.conf

then at the bottom of the file add the following:

vm.swappiness=0
vm.vfs_cache_pressure=1

Preload preloads things into your RAM for faster application startup speeds and the second part basically makes your computer use RAM more than swap.

Well my swap hasn't been used at all ever so I don't think that'll be necessary lol

> **PurposeOfReason said:**
> Install windows and play prototype. :shifty:

:goes to find torrent: lol

---

### Post by joey-elijah on 2009-07-05
Thanks for the preload tip! Installed it - just wondering if it auto-start's up or do i have to set it to do so?

---

### Post by sdlynx on 2009-07-05
It seems I can only run it as root, so yeah I'm wondering too.

---

### Post by andrewabc on 2009-07-05
preload starts automatically. No need to start it. It is a daemon(?) (service).


[http://ubuntu-unleashed.com/tag/preload-and-prefetch-applications](http://ubuntu-unleashed.com/tag/preload-and-prefetch-applications)


Type in command line to see what it is using:
sudo tail -f /var/log/preload.log

Preload for me is using:
readaheading 2513 files
[Sun Jul  5 21:50:12 2009] 1505350kb available for preloading, using 1503584kb of it

---

### Post by sdlynx on 2009-07-05
oh very cool! thanks

---

