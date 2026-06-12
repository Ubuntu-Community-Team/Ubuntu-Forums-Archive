---
title: "Which log files to backup?"
date: 2010-09-07
forum: Server Platforms
---

### Post by karmic-koala on 2010-09-07
Hi all, I somehow convinced my manager to let me handle administration of a dell poweredge 2950 server some time back and so far everything's gone well.

I was asked by the system admin team to backup log files for compliance reasons.

My question, which log files should I backup? Currently I tar the whole /var/log folder every night and keep it safe. Is that how its supposed to be done? How do seasoned system admins do it?

---

### Post by Bachstelze on 2010-09-07
You'd probably be better off asking your sys admin team... Maybe which log files you should save is company policy.

---

### Post by chrisbay90 on 2010-09-07
Also keep in mind that log files rotate very rapidly, especially on busy machines. So you may need to hold onto those files for a good period of time.

---

