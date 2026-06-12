---
title: "Gitosis from repo on Jaunty server"
date: 2009-10-17
forum: Server Platforms
---

### Post by dlouwers on 2009-10-17
Hi,

I am currently trying to set-up a git repo on my server. I have done:

apt-get install git-core gitosis

Installation went fine. However, all tutorials I've found so far assume that you are doing a manual installation of Gitosis. Therefore I don't know how far along in the process I am currently.

Does anyone know of a resource I could read to get this working? Also, most tutorials arrange security by installing public certificates of clients. However I would like to grant access to users I create on the server. Is this also possible?

Best,

Dirk Louwers

---

### Post by bzhao on 2010-12-25
> **dlouwers said:**
> Hi,

I am currently trying to set-up a git repo on my server. I have done:

apt-get install git-core gitosis

Installation went fine. However, all tutorials I've found so far assume that you are doing a manual installation of Gitosis. Therefore I don't know how far along in the process I am currently.

Does anyone know of a resource I could read to get this working? Also, most tutorials arrange security by installing public certificates of clients. However I would like to grant access to users I create on the server. Is this also possible?

Best,

Dirk Louwers


Both apt-get install gitosis and manual gitosis tarball method can work. but you cannot use both of them at the same time in case of malfunction happen.

---

