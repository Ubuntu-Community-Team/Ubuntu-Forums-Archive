---
title: "Dovecot authentication"
date: 2010-01-23
forum: Server Platforms
---

### Post by NIT006.5 on 2010-01-23
I'm looking for a little insight into an issue I had a while back. Ubuntu Server 8.04 running dovecot, didn't seem to have any problems, but I then tried on Server 9.04 and had intermittent authentication problems with dovecot. According to the dovecot documentation, the fix is to increase the number assigned to auth_worker_max_count. This did seem to solve the problem, although someone else did report to me that the fix didn't help them and they have to keep restarting dovecot to get authentication working.

My first question is whether or not anyone knows of another cause for dovecot to stop authenticating after a while?

Secondly, although the dovecot documentation gives that fix, I haven't been able to find an explanation for what it is all about and why the fix is required in the first place. Is there a reason that this "fix" isn't included in dovecot's conf by default, since it seems to be an issue as soon as the server is put under load? And why did this only seem to materialise in Server 9.04 while it seemed to work fine on 8.04?

Would appreciate any thoughts or answers as this has puzzled me for a while now.

---

