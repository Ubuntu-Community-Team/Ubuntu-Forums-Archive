---
title: "WoW and wine 1.3.20 WARNING!!!"
date: 2011-05-18
forum: Wine
---

### Post by cwwilson721 on 2011-05-18
Today, I ran my updater, and updated wine to 1.3.20 from 1.3.19

When I ran WoW, I started spinning in circles (like 'click to move' was checked in the Mouse options)

Reverting back to 1.3.19 fixed the issue.

I ran into the same issue when updating from Korn's PPA for Pulse Audio support earlier this week, but thought it may have justbeen an error in compilation.

But since 2 different repos (Korn and ubuntu-wine) have the same issue, I will have to assume this is a regression in wine's code.

---

### Post by bobwyajnr on 2011-05-18
> **cwwilson721 said:**
> 
But since 2 different repos (Korn and ubuntu-wine) have the same issue, I will have to assume this is a regression in wine's code.

Yes, there are quite a few games adversely affected by the 1.3.20 'mouse fix' (I subscribe to WINE bugs mailing list).

For the true geeks who like Git and the commandline:
[WINE Bugzilla 1.3.20 mouse control regression]("http://bugs.winehq.org/show_bug.cgi?id=27156")

Bob

---

