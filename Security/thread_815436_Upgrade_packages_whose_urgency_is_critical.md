---
title: "Upgrade packages whose urgency is critical?"
date: 2008-06-01
forum: Security
---

### Post by kung fu buntu on 2008-06-01
Is there any way to know which packages have their **urgency** set to a certain level, like critical or high, using apt tools?

My idea is to get a daily list of packages which need to be upgraded ASAP.
This would have been very usefull with the openssh/ssl severe exploit.

I have no idea how this can be done using "apt-cache search"

Thanks

---

### Post by brian_p on 2008-06-01
> **kung fu buntu said:**
> Is there any way to know which packages have their **urgency** set to a certain level, like critical or high, using apt tools?

apt-listchanges, perhaps.

> My idea is to get a daily list of packages which need to be upgraded ASAP.
This would have been very usefull with the openssh/ssl severe exploit.


Why not just upgrade?

---

### Post by kung fu buntu on 2008-06-01
Because I use Debian unstable... and it's not always easy to upgrade every package.
There are things that break and there are bugs (shown by apt-bugs I think).

So I can't keep all packages up to date...

---

### Post by cdenley on 2008-06-02
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I have the RSS feed in my firefox toolbar. I guess this would be the debian equivalent.

[http://www.debian.org/security/#DSAS](http://www.debian.org/security/#DSAS)

On servers, I usually disable everything but the security branch, then upgrade whenever there is a security notice that affects me.

---

