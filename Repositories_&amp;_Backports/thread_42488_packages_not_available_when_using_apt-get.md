---
title: "packages not available when using apt-get"
date: 2005-06-17
forum: Repositories &amp; Backports
---

### Post by ssck on 2005-06-17
i have some packages that i don't seem to be able to get :

1) for dvd playback 
$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

2) for sound 
$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs

am i pointing to the wrong server / website in the repositories ? appreciate if anyone could let me know the right websites to add into the repositories.

thanks very much.

---

### Post by Xian on 2005-06-17
I'm fairly certain some of those are available in the [Extra Repos](http://ubuntuguide.org/#extrarepositories).

---

### Post by ssck on 2005-06-17
[QUOTE=Xian]I'm fairly certain some of those are available in the [Extra Repos](http://ubuntuguide.org/#extrarepositories).[/QUOTE]

found it.didn't look hard enough.thanks for your help.

---

