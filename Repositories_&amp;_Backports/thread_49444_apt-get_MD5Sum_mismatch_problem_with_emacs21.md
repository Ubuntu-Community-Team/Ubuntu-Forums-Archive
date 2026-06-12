---
title: "apt-get MD5Sum mismatch problem with emacs21"
date: 2005-07-16
forum: Repositories &amp; Backports
---

### Post by bpilgrim1979 on 2005-07-16
I've had this problem with first Add Programs and then command line apt-get.  What's wrong?

```

# sudo apt-get update
# sudo apt-get upgrade
# sudo apt-get install emacs21

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/emacs21/emacs21-bin-common_21.3+1-8ubuntu7_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

---

### Post by bpilgrim1979 on 2005-07-25
This turned out to a be problem with us.archive.ubuntu.com in /etc/apt/sources.list.  (in another ubuntuforums post.)  I changed to archive.ubuntu.com and everything resolved.

---

