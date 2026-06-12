---
title: "koffice 1.4.2 for breezy"
date: 2005-11-25
forum: Ubuntu Backports
---

### Post by abandoned_hussam on 2005-11-25
I know it is in [http://kubuntu.org/packages/koffice142/pool-breezy/](http://kubuntu.org/packages/koffice142/pool-breezy/)
but I've been having some problems lately with accessing kubuntu.org
so can this be copied over or ported to breezy-backports? 
I would more than appreciate it if this can be done.

---

### Post by MichaëlVD on 2006-01-19
Does this topic need to be moved to the backport request forum? I would like this to be backported as well.

---

### Post by veloct on 2006-01-20
For breezy:

deb [http://kubuntu.org/packages/koffice142](http://kubuntu.org/packages/koffice142) breezy main 
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/koffice-1.4.2/kubuntu) breezy main 
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/koffice-1.4.2/kubuntu) breezy main 
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/koffice-1.4.2/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/koffice-1.4.2/kubuntu) breezy main 
The packages do not ship with Kexi which is being packaged separately to get the latest Kexi version.


These packages have been digitally signed using Jonathan Riddell's key. You can download and import the key to apt by doing the following:
```

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

---

### Post by MichaëlVD on 2006-01-20
merci beaucoup

---

