---
title: "can i get wine backport?"
date: 2006-12-23
forum: Ubuntu Backports
---

### Post by andsim2 on 2006-12-23
does anyone got wine?:confused:

---

### Post by pay on 2006-12-23
```
sudo nano /etc/apt/sources.list
```and add this at the end of the file```
deb http://wine.budgetdedicated.com/apt edgy main
```Ctrl+X Y to exit and then```
sudo apt-get update
```It will probably be a couple of days before the new version (0.9.28) is in the repo though. If you can't wait you will need to compile it from source.

---

### Post by andsim2 on 2006-12-23
thank u for ur supprt

---

### Post by unfnknblvbl on 2007-01-09
I tried that, but I get this error in Synaptic Package Manager:

> wine:
  Depends: libasound2 (>1.0.11) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgphoto2-2 (>=2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libgphoto2-port0 (>=2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
  Depends: libusb-0.1-4 (>=2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
  Depends: libxml2 (>=2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
  Depends: libxslt1.1 (>=1.1.17) but 1.1.15-1ubuntu1 is to be installed

How do I fix this? ](*,)

---

### Post by bobromeo on 2007-01-14
[QUOTE=pay;1922883]```
deb http://wine.budgetdedicated.com/apt edgy main
```

Did that, reloaded, got 47 updates but this warning and no updates:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by outofnicks on 2007-01-14
I  found this terminal command in my sources.list, which was auto-generated at 
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and the warning disappeared, but I had to quit/restart Synaptic PM and do a new reload first:

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -
```

---

### Post by pay on 2007-01-15
> **unfnknblvbl said:**
> I tried that, but I get this error in Synaptic Package Manager:



How do I fix this? ](*,)If you are using dapper then use this repo```
deb http://wine.budgetdedicated.com/apt dapper main
```

---

### Post by tmalloy on 2007-01-20
> **outofnicks said:**
> I  found this terminal command in my sources.list, which was auto-generated at 
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and the warning disappeared, but I had to quit/restart Synaptic PM and do a new reload first:


Newbie Question: How do i quit/restart Synaptic PM and do a new reload?

---

### Post by tmalloy on 2007-01-21
nvm just logged out and logged back in and it worked

---

