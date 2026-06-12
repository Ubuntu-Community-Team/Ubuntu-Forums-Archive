---
title: "Wine doesn't work for me"
date: 2010-07-18
forum: Wine
---

### Post by Xntrick on 2010-07-18
So I did a clean install of wine-1.2 following the install instructions on the site. However, the program just doesn't seem to work; any link from the wine menu returns nothing. When I try opening .exe files a windows appears "opening..." but subsequently closes. I tried running winecfg in a terminal but I receive,

wine: '/home/*usr*' is not owned by you, refusing to create a configuration directory there. 

If it helps, /home is a separate ntfs partition.

I tried reinstalling wine packages via synaptic but still the same problem persists.

---

### Post by cogadh on 2010-07-18
Looks like you probably ran wine using "sudo" which screws up the permissions on Wine (never run wine with sudo or a root account). You'll probably need to delete your .wine directory and start over.

---

### Post by asdfoo on 2010-07-18
running wine on NTFS is *not supported* - the linux ntfs driver lacks the features Wine requires.

Setup a ext3fs mount for your wine prefix and programs.

---

