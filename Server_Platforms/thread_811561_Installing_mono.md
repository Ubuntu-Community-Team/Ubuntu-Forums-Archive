---
title: "Installing mono"
date: 2008-05-29
forum: Server Platforms
---

### Post by arshadparvez on 2008-05-29
Hello,

I am using Ubuntu Hardy on a server where I have to test newly developed websites. I have already installed apache2 which is working perfectly fine. Sometimes I have to test sites running ASP scripts as well. I was told by some friends to install "mono" for serving asp pages.

Through tutorials on the net I tried to install mono with:

**sudo aptitude install mono-apache-server2 libapache2-mod-mono**

But before actual installation began I saw the following msg:

[B]The following packages will be REMOVED:
  apache2-mpm-prefork libapache2-mod-php5
[/B]

Does it mean that the server will stop serving php pages? My own site depends greatly on php scripts.

regards

Arshad

---

### Post by gdzsi on 2008-05-29
There'll be no apache php5 module on the server.

I found a bug report:
[https://bugs.launchpad.net/ubuntu/+source/mod-mono/+bug/227781](https://bugs.launchpad.net/ubuntu/+source/mod-mono/+bug/227781)

---

