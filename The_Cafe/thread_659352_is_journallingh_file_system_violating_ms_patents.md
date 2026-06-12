---
title: "is journallingh file system violating ms patents"
date: 2008-01-05
forum: The Cafe
---

### Post by articpenguin on 2008-01-05
i searched google patents with ntfs and found transactional file system.

[http://www.google.com/patents?id=g8wVAAAAEBAJ&dq=ntfs+log+file](http://www.google.com/patents?id=g8wVAAAAEBAJ&dq=ntfs+log+file)

since journalling is patented does that mean who ever uses a journalling fs ext3 jfs reiserfs xfs could get sued by ms?

---

### Post by p_quarles on 2008-01-05
I have nowhere near the legal expertise required to understand that patent, but if it *does* refer to journaling file systems in general (which I doubt), they've got a problem: IBM introduced one in 1990. 
[http://en.wikipedia.org/wiki/JFS_file_system](http://en.wikipedia.org/wiki/JFS_file_system)

---

### Post by articpenguin on 2008-01-05
wow its been 15 years and microsoft hasnt created a new filesystem since. Just another idea microsoft copies and patents it.

---

### Post by Sam on 2008-01-05
Happily there is something called [prior art](http://en.wikipedia.org/wiki/Prior_art).

---

### Post by D-EJ915 on 2008-01-05
Funny thing is IBM introduced JFS2 into OS/2 which Micro$haft abandoned, lol.

---

### Post by Methuselah on 2008-01-05
I think Microsoft also patented UAC (use access control)

> 
A computer such as a network appliance executes an administrative security process configured to run under an administrative privilege level. Having an administrative privilege level, the administrative security process can initiate administrative functions in an operating system function library. A user process executing under a non-administrative privilege level can initiate a particular administrative function that the process would not otherwise be able to initiate by requesting that the administrative security process initiate the function. In response to a request to initiate a particular function from a process with a non-administrative privilege level, the administrative security process determines whether the requesting process is authorized to initiate the particular administrative function based on information accessed in a data store. If the requesting process is authorized, the administrative security process initiates the particular administrative function. In this manner, the administrative security process facilitates access to specific administrative functions for a user process having a privilege level that does not permit the user process to access the administrative functions.


Which sounds an awful lot like 'sudo' which linux was doing long before vista.

There are probably quite a few microsoft patents wouldn't stand up to close scrutiny in court. I think they're betting on the fact that smaller enterprises won't exactly be spoiling for a fight with microsoft. However, I doubt the whole linux community and its corproate interests will be put out of commission by microsoft patents without a beiiter fight.

Bottom line, I wouldn't worry about it.

---

