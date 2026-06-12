---
title: "ubuntu-desktop &amp; yelp install issue..."
date: 2005-09-24
forum: Repositories &amp; Backports
---

### Post by ephman on 2005-09-24
hi,

ok long long story but i removed ubuntu-desktop & yelp and i've been trying to reinstall the packages, and i get an error.

E: /cdrom//pool/main/y/yelp/yelp_2.9.3cvs20050222-0ubuntu4_i386.deb:  subprocess dpkg-split returned error exit status 2
E: /cdrom//pool/main/u/ubuntu-meta/ubuntu-desktop_0.43_i386.deb:  subprocess dpkg-split returned error exit status 2

any help would be greatly appreciated thanks.

thanks for the bandwidth,
ephman

---

### Post by Xian on 2005-09-24
The ubuntu-desktop is just a meta-pkg and does not need to be reinstalled. That one you can just leave as is and no harm done. For the issue as a whole, you need to open your sources.list and comment out the cdrom line. Then do an 'apt-get update' session and you should be fine.

```
$ sudo gedit /etc/apt/sources.list
$ sudo apt-get update
```

---

