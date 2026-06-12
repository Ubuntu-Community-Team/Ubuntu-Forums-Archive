---
title: "No apt-get"
date: 2006-08-17
forum: Repositories &amp; Backports
---

### Post by se-ra on 2006-08-17
Hi there,
I have a big problem. I cannot update my system with apt-get. Synaptic doesn't work eighter.

I have just installed Ubuntu 6.06.1 alternate x64. I also tried the i386 version, it doesn't work eighter.

This is what I get:

root@dragon:/# apt-get update
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Errhttp://security.ubuntu.com dapper-security/main Packages
  Connection failed
Errhttp://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Errhttp://security.ubuntu.com dapper-security/main Sources
  Connection failed
Errhttp://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Errhttp://de.archive.ubuntu.com dapper Release.gpg
  Connection failed
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper Release
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/main Packages
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/restricted Packages
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/main Sources
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) dapper/restricted Sources
Errhttp://de.archive.ubuntu.com dapper/main Packages
  Connection failed
Errhttp://de.archive.ubuntu.com dapper/restricted Packages
  Connection failed
Errhttp://de.archive.ubuntu.com dapper/main Sources
  Connection failed
Errhttp://de.archive.ubuntu.com dapper/restricted Sources
  Connection failed
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://de.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


**This is my sources.list (I just changed it throught synaptic):**

root@dragon:/# cat /etc/apt/sources.list |grep -v ^#

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted



I can manually open the address [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) in firefox and w3c and download archives. I'm also available to manually install the downloaded packages.

Does anybody have an idea?

Thanks for your help!

---

### Post by ciscosurfer on 2006-08-17
EDIT: Solved; I needed to reinstall Apt to get it to work again.  Somehow before, Apt got hosed -- prevented my machine from updating.  But all is well now... :-\"

---

### Post by ciscosurfer on 2006-08-17
@se-ra
Try using completely different mirrors.

---

### Post by CsmcDem on 2006-09-14
i am having the same problem. I do not know how to reinstall apt-get. If you would please explain where i could get the file for apt-get, i would appreciate it.

---

### Post by ciscosurfer on 2006-09-14
Go here ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) and type in apt into the keyword selector, make sure you select the appropriate version of Ubuntu and then hit Enter.  Download apt and all it's dependencies if necessary.

Here's a quick link if you're using Dapper: [http://packages.ubuntu.com/dapper/base/apt](http://packages.ubuntu.com/dapper/base/apt)

---

