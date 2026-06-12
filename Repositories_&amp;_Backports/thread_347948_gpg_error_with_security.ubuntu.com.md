---
title: "gpg error with security.ubuntu.com"
date: 2007-01-28
forum: Repositories &amp; Backports
---

### Post by Surgeon General on 2007-01-28
hi, i've been searching for a solution to my update problem (sorry if i crosspost).

i initially used the stock sources.list and i thought of using a fresh one. both would give the message:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures 

were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 

<ftpmaster@ubuntu.com>

when i do a "sudo apt-get update".

i've tried doing a:

gpg --keyserver hkp://subkeys.pgp.net --recv-key 437D05B5
gpg --export --armor 437D05B5 | sudo apt-key add -

also. i've searched the forum but i can't seem to find the proper solution to this. i want 

to upgrade to edgy but i'm holding back because i don't want any kinks before the upgrade.

here's my current sources.list:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb-src [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Beryl
#
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main

---

### Post by Surgeon General on 2007-01-28
just want to let those who follow this thread, my problem has been fixed. apparently the gpg key at security.ubuntu.com has been updated judging from the timestamp. so i did a "sudo apt-get update" and no errors!

---

