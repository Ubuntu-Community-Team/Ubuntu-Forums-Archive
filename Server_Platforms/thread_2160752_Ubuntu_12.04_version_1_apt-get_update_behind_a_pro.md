---
title: "Ubuntu 12.04 version 1 apt-get update behind a proxy"
date: 2013-07-08
forum: Server Platforms
---

### Post by jwp1 on 2013-07-08
Hi Guys I went to Linux Tag and I am trying to do CMS.
I installed everything on the install CD and via repos and it works great.
I want to add a few things and I think something happened with my Apt config.
I am behind a proxy and everything else but sudo apt-get update works great.

My first link with the error code is here.
[http://ubuntuforums.org/showthread.php?t=2159286&p=12715025#post12715025](http://ubuntuforums.org/showthread.php?t=2159286&p=12715025#post12715025)

But no one answered so I moved it to server.

Thanks

Jwp

---

### Post by jwp1 on 2013-07-08
I fixed it.
It was the apt.conf

I thought I would just make it blank and see if the error became another.
Instead I opened with nano made the file empty did ctrl and O to save.
The sudo apt-get update and it worked.

Interesting indeed.

---

