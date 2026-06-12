---
title: "What happened to php5-clamavlib in 9.04"
date: 2009-07-06
forum: Server Platforms
---

### Post by scotland42 on 2009-07-06
I am in the process of installing a new server.  We put 9.04 server on it.  I am currently trying to install php5-clamavlib, but it doesn't exist in the repositories.  Am I missing something?  Did it get replaced by a different package?  Should I be doing something different?  Any hints from anybody would be much appreciated.

Cheers

---

### Post by freephile on 2009-10-07
ping?

---

### Post by cariboo on 2009-10-08
It seems php5-clamavlib is no longer available in current debian versions either. You can still get the Hardy version [here]("http://packages.ubuntu.com/hardy-backports/php5-clamavlib")

---

### Post by freephile on 2009-10-08
There are MOTU developers packaging php5-clamavlib and other ClamAV packages

I found the PPA at [https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)  Once I added that to my sources, I was able to install ClamAV and related packages

:)

---

