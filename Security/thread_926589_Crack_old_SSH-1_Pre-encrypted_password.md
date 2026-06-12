---
title: "Crack old SSH-1 Pre-encrypted password"
date: 2008-09-22
forum: Security
---

### Post by Raymond Day on 2008-09-22
I have a old ZapStation and it runs Red Hat, a old Linux on it. I got port 22 open on it and I found it's Pre-encrypted password for root file.

On my ubuntu server I installed Crack and put the Pre-encrypted password SSH-1 in a file named zap-root-pw

I am not sure how to run it for it to find out the password.

I did this command:

**Crack -fmt SSH-1 zap-root-pw**

But it don't work it says things like:

./Crack: 396: SSH-12spf: not found
sort: open failed: +1: No such file or directory

Any one know how to run it to find out what the password would be?

-Raymond Day

---

### Post by aurelieng on 2008-09-22
Not sure I understand correcly, but if you have a physical access to this machine, what about booting with a liveCD or in runlevel 1, then set a new root password ?

---

### Post by Raymond Day on 2008-09-22
If I use a new Password on it then the ZapStation would not work right. So I need it's password that is all ready in it.

-Raymond Day

---

