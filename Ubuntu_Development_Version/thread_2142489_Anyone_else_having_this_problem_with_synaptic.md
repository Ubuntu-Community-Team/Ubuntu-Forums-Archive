---
title: "Anyone else having this problem with synaptic?"
date: 2013-05-05
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2013-05-05
I have three saucy installs with different DEs and all of them have been done using --no-install-recommends on the *-desktop packages, so that I get a fairly basic system.

When I select obsolete packages for removal, or the residual configs for obsolete packages, synaptic locks up completely and I have to kill it using 
```
sudo killall synaptic
```

I see that there's been a bug filed for this, but it's supposed to have been fixed in synaptic v 0.8~exp2, which is what I have installed.

It's possible that the --no-install-recommends is not pulling in a needed package. So, before I go reporting a bug, I'd like to know if anyone else is having the same problem.

---

### Post by cariboo on 2013-05-05
I've had a similar problem with synaptic on my Ubuntu Gnome install, when trying to remove some obsolete packages, synaptic locks up and eventually closes. This install was a fresh beta installation, updated to Saucy.

I did have the problem in Raring, but a fresh installation of the Raring final seems to have fixed the problem.

---

### Post by Irihapeti on 2013-05-06
Thanks. It sounds like it's not just something unique to my unusual installations. I've filed a bug report.

---

### Post by Elfy on 2013-05-07
Could be useful to post the bug here so people can fin dit easier.

As far as the issue - I've not had that.

---

### Post by Irihapeti on 2013-05-07
> **Elfy said:**
> Could be useful to post the bug here so people can fin dit easier.
...

Good idea. The bug report is [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1176700](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1176700)

---

