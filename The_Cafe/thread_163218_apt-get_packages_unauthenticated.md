---
title: "apt-get packages unauthenticated"
date: 2006-04-20
forum: The Cafe
---

### Post by gymsmoke on 2006-04-20
when i run apt-get install for proftpd on my Ubuntu 5.10 server install, I get added some of the recommended packages, and then I get this after saying 'Y' to install:
WARNING: the following packages cannot be authenticated!
debconf-utils perl-modules perl libterm-readkey-perl libterm-readline-gnu-perl libterm-readline-perl-perl proftpd-common ucf proftpd proftpd-doc
Install without verification ? [y/N] 

when I typed apt-get install proftpd, these were suggested/recommended packages!
why are they not able to be authenticated?  and why would they be suggested/recommended if they cannot be authenticated?
and, is it safe to install them anyway?

---

### Post by WildTangent on 2006-04-20
[QUOTE=gymsmoke]when i run apt-get install for proftpd on my Ubuntu 5.10 server install, I get added some of the recommended packages, and then I get this after saying 'Y' to install:
WARNING: the following packages cannot be authenticated!
debconf-utils perl-modules perl libterm-readkey-perl libterm-readline-gnu-perl libterm-readline-perl-perl proftpd-common ucf proftpd proftpd-doc
Install without verification ? [y/N] 

when I typed apt-get install proftpd, these were suggested/recommended packages!
why are they not able to be authenticated?  and why would they be suggested/recommended if they cannot be authenticated?
and, is it safe to install them anyway?[/QUOTE]
Just means the server's GPG signature is incorrect, or missing. Proceed at your own risk.

-Wild

---

### Post by gymsmoke on 2006-04-20
Wild~
my sources.list doesn't contain anything that I would consider 'off the beaten path' ... 

Would I be better served by using only the strict Ubuntu repo's ?

---

### Post by aysiu on 2006-04-20
[QUOTE=gymsmoke]
and why would they be suggested/recommended if they cannot be authenticated?[/quote] The *packages* themselves are recommended. The *source* from which you're getting the packages is what cannot be authenticated. > and, is it safe to install them anyway? It depends. What does your /etc/apt/sources.list look like?

---

### Post by gymsmoke on 2006-04-20
dep [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubunut.com/ubunut](http://us.archive.ubunut.com/ubunut) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by aysiu on 2006-04-20
Yeah, you're fine.

---

### Post by gymsmoke on 2006-04-20
interesting... after the installation was completed, I ran updatedb and apt-get update...
I got this warning message for all of the repo's in sources.list

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: Could not execute /usr/bin/gpgv to verify signature (is gnupg installed ?)

answer: no...
i installed gnupg gnupg-doc and it's fine now

---

