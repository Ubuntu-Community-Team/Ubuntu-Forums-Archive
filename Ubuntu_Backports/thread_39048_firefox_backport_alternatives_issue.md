---
title: "firefox backport: alternatives issue"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by infinito on 2005-06-03
Latest Firefox backport introduced a little problem with Alternatives.
It changed the man pages alternative for x-www-browser from mozilla-firefox to firefox, so it leaves a dangling symlink in /etc/alternatives:
```
/etc/alternatives/x-www-browser.1.gz -> /usr/share/man/man1/mozilla-firefox.1.gz
```
This should point to:
```
/etc/alternatives/x-www-browser.1.gz -> /usr/share/man/man1/firefox.1.gz
```
Or at least, have a symlink in the manpages dir like this:
```
/usr/share/man/man1/mozilla-firefox.1.gz -> /usr/share/man/man1/firefox.1.gz
```
This is very anoying to me 'cause cron is sending me mails everyday by the man-db daily update.

---

### Post by jdong on 2005-06-03
Interesting.... I'd love to see how Breezy handles this.

The problem:

/etc/alternatives is not updated by the firefox package. I'll also push this bug to Ubuntu's Bugzilla as a Hoary-to-Breezy migration bug, and see if I can get a temporary fix.

---

