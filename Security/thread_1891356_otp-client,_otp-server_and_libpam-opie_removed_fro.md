---
title: "otp-client, otp-server and libpam-opie removed from repository"
date: 2011-12-05
forum: Security
---

### Post by FlameLicker on 2011-12-05
Dear all,

Obviously otp-client, otp-server and libpam-opie were removed from repository in Ubuntu 11.10. I used it on a number of servers and desktops and found it quite handy.

Does anyone know about security issues with otp? If not I would take it from old repositories and save the source code for future use. 

Otherwise I would appreciate any hint to alternatives.

Cheers

---

### Post by FlameLicker on 2012-03-22
For the records:

echo "
 deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
 deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main
" >> /etc/apt/sources.list
apt-get update
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AED4B06F473041FA

solved the problem.

Cheers!

---

