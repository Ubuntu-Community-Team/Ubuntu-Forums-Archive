---
title: "Move SVN repo from broken PC"
date: 2009-07-24
forum: Server Platforms
---

### Post by sipickles on 2009-07-24
Hi,

I have a problem

My Ubuntu svn server PC died. I obviously need to move the svn repos to its replacement, but I cannot run svndump on a broken machine.

I got the Hard drive from the broken machine and have extracted the repo driectory. I naively copied it onto the new machine in the same location as before and started svnserve.

The new svnserver is able to put out log information and provide updates but my problem comes when I try to commit:

Commit failed (details follow):
Can't create directory
'/home/simon/svn/client/db/transactions/200-1.txn': Permission denied

It seems the new system doesn't have write access to the copied folder.

Can anyone suggest how I cure this permission error? I am not so hot on linux permissions!

Thanks

Simon

---

