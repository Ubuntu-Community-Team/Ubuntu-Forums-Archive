---
title: "deleted some files, and now can't install screenlets from repo"
date: 2007-03-20
forum: Repositories &amp; Backports
---

### Post by syxbit on 2007-03-20
i installed screenlets from this repo
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) edgy screenlets
with key
[http://hendrik.kaju.pri.ee/ubuntu/619A3D4E.gpg](http://hendrik.kaju.pri.ee/ubuntu/619A3D4E.gpg) -O-

it worked great. I had several widgets up.
Then I added the mail widget, and it started crashing the program.
i uninstalled the program, reinstalled, but the settings were saved, so the same widgets were loaded up by default, and it would just load up and crash.
there was nothing i could do, so i figured i'd try to delete the program settings
i did an slocate for "screenlets" and deleted everything that mentioned it (prob a mistake, i know) and now when in try to install it again i get the following error in synaptic

```
Package screenlets has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

any ideas?


ps. these are the files i deleted, in case that helps
/home/syxbit/.config/autostart/screenlets-tray.desktop
/home/syxbit/.config/Screenlets/screenletsd.ses
/var/lib/dpkg/info/screenlets.list
/var/lib/dpkg/info/screenlets.postrm
/var/cache/apt/archives/screenlets_0.0.7-8pre0.0.8_i386.deb
/usr/lib/python2.5/site-packages/screenlets/
/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_edgy_screenlets_binary-i386_Packages
/usr/local/share/screenlets/

---

### Post by FaceLeg on 2007-03-23
The mail 'let has broken mine as well...

:(

---

