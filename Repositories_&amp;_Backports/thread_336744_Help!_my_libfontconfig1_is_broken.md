---
title: "Help! my libfontconfig1 is broken"
date: 2007-01-12
forum: Repositories &amp; Backports
---

### Post by amihaic on 2007-01-12
I did (what was probably a very) stupid thing.

I tried to upgrade Banshee to a newer version but it's dependencies weren't met, so I wen't to the Debian repositories and started downloading the libraries it depends on.

I installed fontconfig-config 2.4.2-1 and now my libfontconfig1 is broken (it depends on a previous fontconfig-config version in the ubuntu repos). I tried going to synaptec and reinstalling this package but it said I cant install anything until I fix my broken package. Great.

I tried to do it via command line and this is what I got:
```
amihaic@amihai-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I can't use synaptec right now and some fonts in some applications look a bit funky.

... Help.

---

### Post by amihaic on 2007-01-12
OK, I solved it.

The problem was that my libfontconfig1 was dependent on fontconfig-config, which I upgraded from the Debian site. In Synaptec, I went to this package (fontconfig-config) and from the menu I chose "Force Version". There were 2 versions available, the one that I just installed (the newer one, from Debian) and the one from the Ubuntu repo. I selected the one from the Ubuntu repo, installed it and everything went back to the way it used to be.

---

### Post by bucik85 on 2007-01-16
I had the same problem. I solved it.

First download [fontconfig-config_2.3.2-7ubuntu2_all.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Ff%2Ffontconfig%2Ffontconfig-config_2.3.2-7ubuntu2_all.deb&md5sum=dc77c68395a9b77b0449af9a273a389a&arch=all&type=main")

Next: ```
sudo dpkg -i fontconfig-config_2.3.2-7ubuntu2_all.deb
```

It works. :)

---

