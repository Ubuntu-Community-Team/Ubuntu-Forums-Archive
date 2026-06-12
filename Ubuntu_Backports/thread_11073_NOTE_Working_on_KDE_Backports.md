---
title: "NOTE: Working on KDE Backports"
date: 2005-01-13
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-13
I can't stand it. I'm making backports for KDE 3.3.x. Two months is a very long time to wait.

During the process, the kde metapackages may have broken dependencies (i.e. I'm not done yet).


So, use -t warty-backports , or -t warty to restrict yourself from the staging area when installing KDE related stuff.

Package List:

```

`kde_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde_42-4.10ubp1_all.deb'
`kde-amusements_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde-amusements_42-4.10ubp1_all.deb'
`kde-core_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde-core_42-4.10ubp1_all.deb'
`kde-devel_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde-devel_42-4.10ubp1_all.deb'


```

---

### Post by Quest-Master on 2005-01-13
Just curious, do you yourself prefer KDE or GNOME?

---

### Post by jdong on 2005-01-13
I'm a KDE user.

---

### Post by jdong on 2005-01-13
ack, this takes too long

---

### Post by regeya on 2005-01-16
[QUOTE=jdong]I can't stand it. I'm making backports for KDE 3.3.x. Two months is a very long time to wait.

During the process, the kde metapackages may have broken dependencies (i.e. I'm not done yet).


So, use -t warty-backports , or -t warty to restrict yourself from the staging area when installing KDE related stuff.

Package List:

```

`kde_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde_42-4.10ubp1_all.deb'
`kde-amusements_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde-amusements_42-4.10ubp1_all.deb'
`kde-core_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde-core_42-4.10ubp1_all.deb'
`kde-devel_42-4.10ubp1_all.deb' -> `/var/apt/ubuntu/dists/warty-backports-staging/universe/binary-i386/kde-devel_42-4.10ubp1_all.deb'


```[/QUOTE]

Your efforts are greatly appreciated.  :D 

I for one really appreciate the hard work the GNOME team has put into making their system friendly to the lowest common denominator, but I'm itching to get back to KDE.  I'm glad to see Kubuntu come about, because I had feared that I'd have to move away from using Ubuntu.  I may yet.  I had considered switching back to Gentoo, but as you said of backporting KDE, it takes too long.   :D

---

### Post by jdong on 2005-01-16
I've given up. There are too many dependencies that I can't resolve without bringing like 20 Hoary libs into Warty -- against my beliefs.

This close to Hoary's preview, I think I'll spend more time with Hoary and KDE integration, though the Kubuntu team should be helping out.

---

### Post by HiddenWolf on 2005-01-16
[QUOTE=jdong]I've given up. There are too many dependencies that I can't resolve without bringing like 20 Hoary libs into Warty -- against my beliefs.

This close to Hoary's preview, I think I'll spend more time with Hoary and KDE integration, though the Kubuntu team should be helping out.[/QUOTE]
Have dates been set for Hoary?
Preview / Feature Freeze etc?

---

