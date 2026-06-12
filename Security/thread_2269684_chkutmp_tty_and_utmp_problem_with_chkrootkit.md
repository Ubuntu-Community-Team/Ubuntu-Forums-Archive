---
title: "chkutmp tty and utmp problem with chkrootkit"
date: 2015-03-17
forum: Security
---

### Post by electric-alchemist on 2015-03-17
Recently did a clean install of an old version of ubuntu (12.04 Lubuntu) because I had a possible rootkit on a previous installtion of 14.04
 however, I still get some odd results from chkrootkit, regarding the tty and utmp;
```

Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! joe          2415 pts/1  /bin/bash
! joe          2470 pts/1  sudo chkrootkit
! root         2471 pts/1  /bin/sh /usr/sbin/chkrootkit
! root         3105 pts/1  ./chkutmp
! root         3107 pts/1  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         3106 pts/1  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
chkutmp: nothing deleted
```
What does this mean?

---

### Post by unspawn on 2015-03-21
The processes are attached to a tty but no audit record was found in /var/run/utmp. Which is normal behaviour for processes that wait for a login to occur. (If you want to run some checks verify package integrity. This essentially means installing 'debsums' right after you installed the OS as your chosen Linux distribution parent itself does not offer other automated finegrained package content integrity checking as far as I'm aware.) Note installing unsupported distribution releases is a recipe for disaster. Also note traditional root kits are rarely seen anymore. So next time if unsure do ask for second opinions from knowledgeable Linux users before performing destructive ops.

---

### Post by electric-alchemist on 2015-03-23
It's fantasitc to acctually get a reply about this problem, no one seemed interested in helping, so thanks very much! But now I just have more questions:

I did some more research and those processes seem to be from chkrootkit itself... so if they are processes which wait for a login to occur, and no login has occured scince they started, does this mean that chkutmp/chkrootkit will detect itself scince no login has occured scince it begins checking for rootkits?

I've also noticed, using task manager, that these processes only appear when using chkrootkit, what do you think that means?

also, why is installing an unsupported distro a recipe for disaster?

---

### Post by unspawn on 2015-03-23
> **electric-alchemist said:**
> (..) does this mean that chkutmp/chkrootkit will detect itself scince no login has occured scince it begins checking for rootkits? No that's not how things work. And you can simply match the hashes of the concerning files against those of a pristine copy to verify it's not been tampered with.   > **electric-alchemist said:**
> I've also noticed, using task manager, that these processes only appear when using chkrootkit, what do you think that means? Not much, really. This happens more often that you think. The only difference is you won't be running chkutmp (or 'sudo utmpdump /var/run/utmp') at that time...   > **electric-alchemist said:**
> also, why is installing an unsupported distro a recipe for disaster? Security and bug fixes are not things one should pass up on (lightly|ever).

---

### Post by electric-alchemist on 2015-03-24
ok, thanks, but I still don't know what those chkutmp results mean.

---

