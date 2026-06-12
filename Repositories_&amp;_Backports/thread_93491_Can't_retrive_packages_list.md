---
title: "Can't retrive packages list"
date: 2005-11-22
forum: Repositories &amp; Backports
---

### Post by djbeppe on 2005-11-22
Has anyone made this repository work:

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) ../project/experimental main

I cant get packages list! When I do a apt-get update, packages
under "experimental" seems not to be present.

Can anyone help me please?
Thanks!

---

### Post by Xian on 2005-11-22
[QUOTE=djbeppe]When I do a apt-get update, packages
under "experimental" seems not to be present.[/QUOTE]
Seems not to be present in what exactly?
Do a pkg search and see if the version is cached.

```
$ sudo apt-cache policy package_name
```

---

### Post by aysiu on 2005-11-22
Why are you using Debian repositories instead of Ubuntu ones?

---

### Post by Xian on 2005-11-22
There are some pkgs in the Deb rep's that Ubuntu doesn't have.
I've got a couple on my system.

Outside of that there is no reason.

---

### Post by aysiu on 2005-11-22
There are--and for those you can add the repository, install the packages, and then take the repository off.

I just worry for some newcomers to Ubuntu that they actually would be able to find the package in the Ubuntu repositories if they looked (or added the Universe repositories).

---

### Post by Xian on 2005-11-22
Hopefully nobody adding the experimental deb repo is all that green. 
If so, they won't be green for very long... :)

---

