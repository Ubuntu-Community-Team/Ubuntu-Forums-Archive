---
title: "Backup to amazon S3 not working"
date: 2014-04-15
forum: Ubuntu Development Version
---

### Post by keithy on 2014-04-15
Which is a great shame since the demise of Ubuntu One

i get the following error

BackendException: No connection to backend
 
Any clues?

Thanks

Keith

---

### Post by keithy on 2014-04-15
Ok, fixed it

you have to use dconf to tell deja-dup which bucket to use then all is well

HTH

Keith

---

### Post by meaglin on 2014-07-09
Could you give me more details? What exactly did you set via dconf?

---

### Post by Rob-e on 2014-12-01
It seems it autogenerates a bucket name to use for the backup. I made my own bucket and limited the IAM user to it so I needed to edit the bucket with dconf-editor.

Here's post that details how to make it work [http://blog.domenech.org/2013/01/backing-up-ubuntu-using-deja-dup-backup-and-aws-s3.html](http://blog.domenech.org/2013/01/backing-up-ubuntu-using-deja-dup-backup-and-aws-s3.html)

---

### Post by pieceofpeace on 2015-09-05
This workaround seems to work for me, but only if I use a bucket created in US (Standard), not in Frankfurt, nor in Ireland. For these two locations, deja-dup still exits with "BackendException: No connection to backend"

Fedora 22
deja-dup 34.0
duplicity 0.6.25
boto 2.38.0

---

### Post by cariboo on 2015-09-05
Seeing as this problem has already been solved, and has nothing to do with Wily. Thread Closed.

---

