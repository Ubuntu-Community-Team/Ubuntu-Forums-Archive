---
title: "Denying a program access to the Internet"
date: 2014-01-27
forum: Security
---

### Post by augustrigmarole on 2014-01-27
I came across a useful post from a few years ago describing how to run a program but deny it access to the Internet: [http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)

If I'm not mistaken, it involves creating a group that is denied Internet access, placing desired programs in the group, then running the program using the terminal.

I've got 2 questions for anyone who has used this method:
1. Does it still work in Ubuntu 12.04 LTS?
2. If yes, does doing this block programs that are called by the original program? For example, some games ultimately end up a different executable than the one that was initially used to start the game, at least in Windows. If the same game is installed and run via Wine, I can anticipate something similar happening, so I'm interested in how this method handles these types of calls.

---

### Post by ian-weisser on 2014-01-28
1. Yes.

2. Generally yes. But there are exceptions - some services (usually daemons and servers) run as a different user, and that user would need to be part of the group.

---

### Post by Dave_L on 2014-01-28
AppArmor can also do this. But configuring it can be challenging.

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

