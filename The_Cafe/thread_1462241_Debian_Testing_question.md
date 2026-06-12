---
title: "Debian Testing question"
date: 2010-04-25
forum: The Cafe
---

### Post by Ewingo401 on 2010-04-25
Hey guys, I know there may be more appropriate places to ask this question but I knew I'd get a quick and informed response here.  Anyway, I plan on setting up Debian Testing as a rolling release on one of my machines by changing all instances of squeeze to testing in my sources list.  The only question I had was, when I go to run updates should I use apt-get upgrade or apt-get dist-upgrade or some combination of the two?  Thanks in advance!

---

### Post by kevCast on 2010-04-25
Debian developers recommend you use aptitude. It would be a combination of the following:

```
aptitude update
aptitude safe-upgrade
aptitude full-upgrade
```

---

### Post by snowpine on 2010-04-25
I use 'apt-get dist-upgrade' with my Debian testing and unstable boxes (and my Ubuntu too). 'apt-get upgrade' is better suited for very stable releases like Debian Stable. Aptitude probably works well too; I've never tried it.

---

