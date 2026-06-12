---
title: "dovecot imap very slow after reboot"
date: 2010-05-24
forum: Server Platforms
---

### Post by kamikazebis on 2010-05-24
Hi,

I've been using ubuntu server for one month now without problems
It's running on a dual core atom with 4 GB RAM and SSD harddrive.


Last weekend I did a reboot and since then my imap folders are almost inaccessible through thunderbird. I also have squirrelmail installed, this became als very slow.

Any ideas what could be wrong?

Greetings.

---

### Post by noway2 on 2010-05-24
The first place I would look is in the logs.  See if you can locate anything out of the ordinary that either explains what is happening or what part of the process is taking so long.  Specifically, is the authentication stage, generating the pages (squirrelmail (PHP based), a problem with an SQL backend, etc.

There is a good chance that you will see something indicating a failure or timeout that will give you a clue as to what is wrong.

---

