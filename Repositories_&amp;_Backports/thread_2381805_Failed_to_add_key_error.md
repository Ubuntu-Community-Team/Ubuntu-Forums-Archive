---
title: "Failed to add key error"
date: 2018-01-05
forum: Repositories &amp; Backports
---

### Post by martin8808 on 2018-01-05
Having an extremely confusing error.

trying to install a python based program onto Ubuntu server 16.04 and receiving this response.

sudo bash server_initial_setup_beagle.sh 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease.
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed InRelease [253 kB]
Fetched 560 kB in 2s (260 kB/s)   
Reading package lists... Done
Adding apt packages list...OK
Executing: /tmp/tmp.kNQFYYya6n/gpg.1.sh --keyserver
keyserver.ubuntu.com
--recv-keys
5BB92C09DB82666C
gpg: requesting key DB82666C from hkp server keyserver.ubuntu.com
gpg: key DB82666C: "Launchpad Old Python Versions" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
gpg: keyring `/tmp/tmpnq80q38d/secring.gpg' created
gpg: keyring `/tmp/tmpnq80q38d/pubring.gpg' created
gpg: "tag:launchpad.net:2008:redacted" not a key ID: skipping
Failed to add key.

Cannot figure this out!

---

