---
title: "wubi.exe md5sum missmatch"
date: 2008-04-24
forum: Security
---

### Post by eyelessfade on 2008-04-24
Now I have downloaded wubi.exe from 4 different mirrors.
MD5SUMS file say:
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

but
$md5sum wubi.exe
a96aa69961f3ed80dd7a88fae1e28196  wubi.exe

---

### Post by eyelessfade on 2008-04-24
$ md5sum -c MD5SUMS
ubuntu-8.04-alternate-amd64.iso: OK
ubuntu-8.04-alternate-i386.iso: OK
ubuntu-8.04-desktop-amd64.iso: OK
ubuntu-8.04-desktop-i386.iso: OK
ubuntu-8.04-server-amd64.iso: OK
ubuntu-8.04-server-i386.iso: OK
wubi.exe: FAILED
md5sum: WARNING: 1 of 7 computed checksums did NOT match

---

### Post by juan@forum on 2008-04-25
you are right

cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe
:~/temp$ md5sum wubi.exe 
a96aa69961f3ed80dd7a88fae1e28196  wubi.exe

---

### Post by eyelessfade on 2008-04-26
I see that a new MD5SUM file has been uploaded with the correct hash

---

### Post by trimeta on 2008-04-27
I'm still seeing the bad hash; where is this updated MD5SUMS file?

---

### Post by eyelessfade on 2008-04-28
I found it on a mirror in norway, but all mirror should get it. Just take some time :)

---

