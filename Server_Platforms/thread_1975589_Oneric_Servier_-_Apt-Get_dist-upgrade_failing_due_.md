---
title: "Oneric Servier - Apt-Get dist-upgrade failing due to disk space error"
date: 2012-05-07
forum: Server Platforms
---

### Post by Morrighu on 2012-05-07
I'm having a problem when I try to upgrade with "running out disk space" even though there is free space available.  I found this thread - for Lucid Lynx - [http://ubuntuforums.org/showthread.php?t=1454052](http://ubuntuforums.org/showthread.php?t=1454052) which describes the problem exactly.

The EXT4 file space is out of inodes but not free space.  

df -i shows that the partition is at 100% even though a regular df shows it at 83% :/

In order to get rid of the problem, I had to go to /usr/src/ and remove all the old kernels in order to free up enough inodes for the new kernel to install. 

When I went to look at what was burning up all the inodes, there are a  LOT of files in the linux-headers folders that just don't apply to my  machine.  No wonder all the inodes are used up.  It creates all kinds of tiny files & folders that don't even apply to my machine.

**Proposed Solutions:  **


[LIST=1]
[*]Not sure how to fix EXT4 but there should defnintely be an increase in the number of inodes.
[*]Create kernels as a "meta package" so that they are only storing the stuff I actually *need* and not ARM, Mac, etc.
[/LIST]

---

