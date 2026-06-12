---
title: "/[usr/]sbin/nologin"
date: 2013-07-02
forum: Security
---

### Post by digitalramble on 2013-07-02
I have a question about the nologin shell on Ubuntu/Debian distros.  I'm used to this from FreeBSD and there, you can can edit a file called /etc/nologin.txt to customize the message for accounts with nologin shells trying to log in. (We deactivate accounts by resetting the shell first and archiving the directory, because it's possible we may want to restore things later.)  The idea is to let the person know what's going on, and the standard "This account is currently not available." is pretty terse.

However, I find that in the debian distros, while there's the nologin shell, there does not appear to be any mention of a customized message in conjunction with nologin in any of the man pages (nor did just trying out a nologin.txt file).  That sucks.

So I figured I'd add a short script to /etc/update-motd.d/ that checked for the nologin shell and output a message, only to realize that the SHELL and USER variables are not set at this point o.O
(If it's relevant, authentication is handled via LDAP, not locally.)

Any ideas at this point for a work around (or an equivalent to /etc/nologin.txt that I didn't find in the docs)?

Thanks...
Cindy

---

