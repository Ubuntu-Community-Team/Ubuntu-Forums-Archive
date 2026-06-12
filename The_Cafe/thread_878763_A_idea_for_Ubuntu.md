---
title: "A idea for Ubuntu"
date: 2008-08-03
forum: The Cafe
---

### Post by tom66 on 2008-08-03
Does Ubuntu have a reliable rollback changes feature? I had this problem once and it was bad; the GUI wouldn't get past the cursor. Turned out I had compiled a bad xml library over the original, as part of installing zlib. I had to reinstall. 

I propose a solution; perhaps it is kinda stupid, but what about keeping a copy of each critical library over a 7 day period? (Critical meaning Ubuntu won't boot without it properly; non-critical would be loss of function, such as the compositing manager) Then if there's a problem you could just run a simple application and fix the problem. If there's a problem with loading libraries then the computer could switch to tty1 and present a message offering to restore the backup. 

Comments, ideas, suggestions are welcome.

---

### Post by spupy on 2008-08-03
Backing up all libs every 7 day requires a lot of storage space. Perhaps it will be better if not the file itself is backed up, but it's version. The backup will say something like (in program readable format of course):
```
On 03.08.2008 library libxml.so was version 2.4, it is working ok
```
Then, if you want to roll back to the previous working version, the roll-back program will know that the last working version of this file was version 2.4 and it will download it from the repos.
Really critical files like the kernel and libs required to connect to the internet (so you can roll-back other stuff) are back-upped as whole files.
Whole-file back-up also for config files in /home and /etc.

This is really a good idea in my opinion. It just happened yesterday - i was updating packages on my gentoo installation. A new version of HAL was installed. Unfortunately, the new version wasn't able to put my laptop to hibernation. So I needed to install the latest working version. I had to find the update logs and search through them to find the version that was installed before the upgrade. A tool such as the one you described would have been immensely useful in that situation.

---

### Post by Daveski on 2008-08-03
> **spupy said:**
> Backing up all libs every 7 day requires a lot of storage space. Perhaps it will be better if not the file itself is backed up, but it's version. 

I think solutions like Microsoft's System Restore and Apple's Time Machine use deduplication so that only changes are stored not necessarily whole files.

---

### Post by tom66 on 2008-08-03
Like diff? That would work. Maybe base it on 'keyframes'. Here's an example.

```

Original: Hell-o world
Change: remove Hell-o add heLlo
Change: remove heLlo add Hello
Change: remove world add World
Keyframe: Hello World
Change: remove World add Ubuntu
Change: add to end ' User'
Change: add to end '!'
Keyframe: Hello Ubuntu User!

```

So in case the original is corrupted then keyframes should prevent it. Store an MD5 sum and go back as far as necessary.

---

