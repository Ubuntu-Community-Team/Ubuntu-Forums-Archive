---
title: "Massive breakage for Xubuntu today!"
date: 2012-08-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by xeizo on 2012-08-24
X went down, and no possibility to downgrade to an older Xorg anymore, proposed disabled of course. Also symlinks stopped working and all harddrives but the sysdrive disapperared. 

Before that mess occured after the last critical upgrade, there was graphical corruption of the xfce desktop gui, no titlebars etc. Too much to fix at once, so i reverted to a working Ubuntu image from 2012-07-31, which I'm back online with.

Reminds oneself of the fun with running bleeding edge software, 12.04 never was this broken during development but that was an LTS ...

edit. later I locked all X11/Xorg-packages in Synaptic, after that I could upgrade everything to todays latest packages. Including Nvidia. Nvidia and Xorg 1.13 play extremely bad together, and even worse with every new build of 1.13.

---

### Post by ventrical on 2012-08-24
And the networking is random and itermittent.

```

gn http://ca.archive.ubuntu.com quantal-backports/universe Translation-en_CA
Fetched 17.6 MB in 1min 38s (178 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
ventrical@ventrical-OptiPlex-GX270:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: The package lists or status file coul

```

So I can't even get synaptic to update  at this point.

---

### Post by ventrical on 2012-08-24
Xubuntu never fails with maximum breakage, even  with LTS. The whole thing is crashing. Apport rendered useless and firefox taking on a mind of it's own.

---

