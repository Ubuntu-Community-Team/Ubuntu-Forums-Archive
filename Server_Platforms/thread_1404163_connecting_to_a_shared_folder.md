---
title: "connecting to a shared folder ?"
date: 2010-02-11
forum: Server Platforms
---

### Post by whitetimer on 2010-02-11
Hi All

I have Ubuntu karmic as my host OS and Ubuntu Server as a guest on Virtualbox.  I have set a folder on my host as shared with the guest, but how can i connect to it from the terminal on my guest ?

I am also using webmin as i was trying to stay away from install a desktop :KS 

Many Thanks

---

### Post by Morbius1 on 2010-02-11
sudo mount -t vboxsf *share-name* *mount_point*

---

