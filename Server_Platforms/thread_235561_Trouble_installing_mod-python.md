---
title: "Trouble installing mod-python"
date: 2006-08-13
forum: Server Platforms
---

### Post by succhi on 2006-08-13
I have been struggling nearly all day trying to install libapache2-mod-python2.4

I am running Ubuntu6.06. I have tried online resources and the cd with apt-get. I get the following error in all cases, the only difference is the source of the deb.

```
Unpacking libapache2-mod-python2.4 (from .../libapache2-mod-python2.4_3.1.4-0ubuntu1_i386.deb) ...
dpkg: error processing /cdrom//pool/main/liba/libapache2-mod-python/libapache2-mod-python2.4_3.1.4-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/mod_python/cgihandler.py', which is also in package libapache-mod-python2.4
Errors were encountered while processing:
 /cdrom//pool/main/liba/libapache2-mod-python/libapache2-mod-python2.4_3.1.4-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
It always seems to break at the point "trying to overwrite `/usr/lib/python2.4/site-packages/mod_python/cgihandler.py...`

I have moved /usr/lib/python2.4/site-packages/mod_python/ and renamed it so it is not a physical issue with overwriting and perms are fine. It also mentions "which is also in package libapache-mod-python2.4" but this is not installed and is not in /var/cache/apt/archives/

Can anyone tell me what I might try next to fix this?

TIA,
Stu

---

### Post by neilp85 on 2006-08-13
Are you sure you want to be installing the package from CD. You should try to installing from an online repo.

---

### Post by succhi on 2006-08-13
Hi Neil,

No I don't want to install from CD but as I said I had tried online and cd. I just pasted the error, which is the same, from the CD attempt as I had tried too many times to count with online repos.

It didn't matter what I tried I got the same error about not being able to overwrite because it is also in libapache-mod-python2.4 even though I only want to install libapache2-mod-python2.4

Stuart.

---

### Post by az on 2006-08-13
Remove libapache-mod-python2.4

Remove apache, too, for that matter, you only want to be running apache2 anyway.

---

### Post by succhi on 2006-08-14
Azz. You know it's funny I tried removing libapache-mod-python and libapache-mod-python2.4 last night and it said there was nothing there. After starting up my server again this morning and trying to uninstall them once more, on a chance, they actually uninstalled. Thanks for your advice it confirmed what I had done.

Cheers

---

