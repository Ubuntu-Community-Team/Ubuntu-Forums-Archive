---
title: "ISOLINUX Install or LiveDVD"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by AshRulez on 2009-11-02
I want to make a DVD containing all Ubuntu 9.10 releases.
Everything works fine but Ubuntu Studio not only is not available as LiveDVD, but also has a different directory structure compared to all other distributions (Ubuntu, Kubuntu, Xubuntu, Mythbuntu, Lubuntu).

Does someone know what changes have to be made to the initrd in order to load it under a subdirectory of the DVD (the root of the Ubuntu Studio ISO contents would not be / but /studio/)?
It is very simple for the other distributions, i.e. Kubuntu, so live and installation mode works for them.
Example changes to /scripts/casper inside initrd:
```
LIVE_MEDIA_PATH=kubuntu/casper
$path/kubuntu/.disk/casper-uuid
```

---

### Post by AshRulez on 2009-11-02
Does someone know if there is an unofficial LiveDVD of Ubuntu Studio 9.10 available?
Or is a Live medium easily creatable with remastersys?
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by Stochastic on 2009-11-05
I moved your posts to their own thread.

Edubuntu isn't listed on your first post, have you considered adding that to your DVD.

Sorry I'm not familiar with creating LiveDVDs, but essentially an Ubuntu live cd would provide the same functionality as an Ubuntu Studio live dvd.  From my understanding, the Ubuntu Studio disks use the standard Ubuntu Alternate installer.

---

