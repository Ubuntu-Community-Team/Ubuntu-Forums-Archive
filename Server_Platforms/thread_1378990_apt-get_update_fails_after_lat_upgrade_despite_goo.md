---
title: "apt-get update fails after lat upgrade despite good network"
date: 2010-01-12
forum: Server Platforms
---

### Post by DaiLaughing on 2010-01-12
I have searched for similar problems here with no luck but then I never did get on with the search facility in these forums.

ubuntu 8.04.1 as a LAMP server with no GUI.

apt-get update fails with this while it tries:

> 
0% [Connecting to gb.archive.ubuntu.com (194.169.254.10)] [Connecting to security.ubuntu.com (91.189.88.37)]


then:

> Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

I can ping both IP addresses.  I have two other servers connected to the same ADSL router which are updating fine (although they are different versions).  The server is a file server and the Samba shares are working fine.

Thanks.

---

