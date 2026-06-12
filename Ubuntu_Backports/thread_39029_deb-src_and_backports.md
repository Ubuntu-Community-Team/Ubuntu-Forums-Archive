---
title: "deb-src and backports"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by 2swift on 2005-06-03
I don't know if this question has already been asked, I checked the forums. I was wondering where the source repositories are so I can do an "apt-get source sompackage"? I was interested in using pbuilder to try to rebuild some backports packages for amd64. Am I just missing something obvious?

Thanks.

---

### Post by Juergen on 2005-06-03
You can find an example for a Hoary configuration (and a link to more mirrors) here:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by ubuntu_demon on 2005-06-03
[QUOTE=2swift]I don't know if this question has already been asked, I checked the forums. I was wondering where the source repositories are so I can do an "apt-get source sompackage"? I was interested in using pbuilder to try to rebuild some backports packages for amd64. Am I just missing something obvious?

Thanks.[/QUOTE]
 you should have the deb-src line of the corresponding repository in your sources.list .. for example :

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb-src doesn't work with backport repositories

But if there are sources available this is the way to go :

$ sudo apt-get source packagename

some backport sources are available here :

[http://backports.ubuntuforums.org/ubp/sources](http://backports.ubuntuforums.org/ubp/sources)

Maybe you can get the breezy sources for your package and try to build them ?

---

### Post by Slo Mo Snail on 2005-06-03
As most packages are backported from breezy (and debian unstable, sometimes experimental) you just have to add their deb-src repositories. The only difference between the backports and the sources in the repos is the version number (for 99.999% of them ;) )

---

### Post by Amaranth on 2005-06-03
[QUOTE=Slo Mo Snail]As most packages are backported from breezy (and debian unstable, sometimes experimental) you just have to add their deb-src repositories. The only difference between the backports and the sources in the repos is the version number (for 99.999% of them ;) )[/QUOTE]
 Aside from that, this is a known issue and one the Ubuntu developers brought up at the meeting. Should no longer be a problem when backports move to ubuntu's buildds and servers.

---

### Post by 2swift on 2005-06-03
Thanks for the replies everyone.

---

