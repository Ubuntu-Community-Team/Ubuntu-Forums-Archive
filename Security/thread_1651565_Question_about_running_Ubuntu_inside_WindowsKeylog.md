---
title: "Question about running Ubuntu inside Windows/Keylogger detection possibility"
date: 2010-12-23
forum: Security
---

### Post by Cilac on 2010-12-23
Let's say I install Ubuntu in a way that I use VirtualBox with it, so I can run it inside of Windows. 

If you use a Linux-incompatible keylogger such as eBlaster on my   computer, will it still record my keystrokes because I'm running it in   Windows? Or will it be unable to detect anything since I'd be typing in   Ubuntu?
If it can still detect what I type in Ubuntu, is there way to prevent that? (i can't try to boot ubuntu from a dual boot screen though, tried everything)

Yes, I realize I posted this same question in the General Help forum, but no one is replying there. :u I'm sorry.

---

### Post by The Cog on 2010-12-23
If the host (windows) has a keylogger installed, then it will be able to log all keystrokes before they even reach the VirtualBox application. The fact that VB is running a different OS such as Linux inside itself is not relevant - the logging goes on outside of VB.

---

