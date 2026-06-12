---
title: "[Announce] GnuPG does not detect injection of unsigned data"
date: 2006-03-09
forum: Server Platforms
---

### Post by issueperson on 2006-03-09
GnuPG announced a bug today (march 9th).

[http://lists.gnupg.org/pipermail/gnupg-announce/2006q1/000216.html](http://lists.gnupg.org/pipermail/gnupg-announce/2006q1/000216.html)

"This new problem affects the use of *gpg* for verification of
signatures which are _not_ detached signatures.  The problem also
affects verification of signatures embedded in encrypted messages;
i.e. standard use of gpg for mails."

an upgraded package is available on the website.
(GnuPG 1.4.2.1 is compromised - the one installed with Ubuntu.  1.4.2.2 is the new stable release)

---

### Post by maxomai on 2006-03-10
Note that gpg2 -- which is also available for Ubuntu and Kubuntu -- apparently does not suffer from this issue.

---

### Post by Barrakketh on 2006-03-11
GnuPG-2 is the development branch.

---

### Post by issueperson on 2006-04-02
UPDATE:
Ubuntu (Breezy) should now fix this problem for you using the Update Manager.

---

