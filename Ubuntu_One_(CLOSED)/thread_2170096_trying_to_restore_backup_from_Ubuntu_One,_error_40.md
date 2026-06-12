---
title: "trying to restore backup from Ubuntu One, error 401"
date: 2013-08-24
forum: Ubuntu One (CLOSED)
---

### Post by grizdog on 2013-08-24
Hello,

I had a system crash on my laptop, and used a disc to reinstall 12.04  I had been backing up my home directory to Ubuntu One, using the deja-dup backup tool.  Now I would like to restore it.

When I try , it always gives me error 401.  Just to check, I gave it the wrong encryption password, and then it simply failed by telling me the encryption password is wrong, not with the 401 error.  Then I gave it the right password, and it took quite a bit longer, but it failed with the 401 error.  SO it seems to know it is me, but is having some problem with authentication.

I made the permissions on my home directory 777 but the problem persisted.

I have seen some old posts to the net suggesting it is a server side problem, if so, I have no idea what to do.

I would be happy to download all the files and try to use deja-dup locally, but I don't know how to just download files from Ubuntu One.  Everything is about syncing, and even though it says all files are synced, I can't find the backup anywhere,.  It makes sense that the backup would be treated differently, since if you synced it to your computer you would forever be backing up the backup, but how do I just download it?  Or better, how do I beat the 401 error?

Thanks.

---

### Post by Irihapeti on 2013-08-25
I'm not 100% sure of this, but it may be that the authorisation token on the server no longer matches the one on your laptop because you've reinstalled.

You can try using the method I've described in [http://ubuntuforums.org/showthread.php?t=2164297&p=12743564#post12743564](http://ubuntuforums.org/showthread.php?t=2164297&p=12743564#post12743564) It won't do any harm if that wasn't the problem.

---

### Post by grizdog on 2013-08-25
Thanks, this worked.  The restore has been going for 3 hours now, which seems like a long time for 3 GB with a wired broadband connection, but hey, backups should be efficient, restores not so much.

I hope your answer makes into the FAQ at some point.  Even if I had thought of that, I can't imagine getting all those steps right.

Thanks again.

---

