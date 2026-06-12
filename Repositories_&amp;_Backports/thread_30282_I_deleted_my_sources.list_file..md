---
title: "I deleted my sources.list file."
date: 2005-04-28
forum: Repositories &amp; Backports
---

### Post by raid517 on 2005-04-28
Hi, I accedentally deleted my sources.list file for Kubuntu. Can anyone here be kind enough to supply me with a new one?

GJ

---

### Post by heimo on 2005-04-28
This probably is enough for you to get started? (it's not original, please edit to your tastes)

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb ftp://ftp.nerim.net/debian-marillat/ stable main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

```

---

### Post by az on 2005-04-28
sudo apt-setup 
will give you a skeleton which is localised to your area.  Add universe and multiverse...

---

### Post by raid517 on 2005-04-28
Thanks!

---

