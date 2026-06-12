---
title: "security.ubuntu.com GPG errors"
date: 2005-05-01
forum: Repositories &amp; Backports
---

### Post by rivode on 2005-05-01
Immediately after installing Ubuntu, running 'apt-get update' gives this error:
```
W: GPG error: http://security.ubuntu.com hoary-security Release: The following
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic
Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```
Running 'apt-get update' again shows the same message.

I have re-installed Ubuntu, with the same result.  I have been getting this message for more than two weeks.  I have also tried the 'Restore default keys' option in Synaptic, but that doesn't help.

This is happening with an unmodified sources.list.

Others seem to be having this problem, there are several mentions of it on these forums but no answers that work.  How might I be able to get around this?

---

