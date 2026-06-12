---
title: "Hardy Heron Server overheats and shuts down"
date: 2008-06-08
forum: Server Platforms
---

### Post by dutchie86 on 2008-06-08
Hey all,
I am having a major problem with ubuntu server (HARDY HERON, all updates installed, latest BIOS) that when it gets under heavy load for a minute or two it overheats and has warnings saying it got over 95C and is shutting down.

I am running Ubuntu Hardy Heron server on an samsung X20 laptop (yeah not a real server but i am just a poor uni student :) ), with 1.5 Gb of RAM, 120gig hard disk and it has a 1.5Ghz proccessor.

I have installed lm-sensors but it can't pick up any sensors and I have also installed hdd-temp and it shows the hdd temp as 38C when i check.

Any help will be greatly appreciated.

---

### Post by fozy on 2008-06-08
Sound like a hardware issue to me.  I had the same problem with a linux setup notebook that had failing fans, hence the heat issue.

---

### Post by beefcurry on 2008-06-17
If you are still suffering such problems roll back to using Gutsy, or feisty. What you are describing could be:

[https://bugs.launchpad.net/bugs/223081](https://bugs.launchpad.net/bugs/223081)

---

