---
title: "Ubuntu repository doens't contain _all_ debian sid softwares ?"
date: 2004-12-05
forum: Repositories &amp; Backports
---

### Post by M@t on 2004-12-05
I would like to install lilypond software (a program for typesetting sheet music). But there is no package for this software in ubuntu hoary repository (I enabled universe and multiverse).

"apt-cache search lilypond" doesn't find anything.

I do not understand why this software is in the unstable repository of Debian and not in hoary. Is there any other package which doesn't appear in hoary and is in Debian sid ? Is this a bug ?

---

### Post by randy on 2004-12-05
I know there's some packages that don't appear in universe because they weren't rebuilt.  You can try rebuilding the Sid package from source, that will definitely work.

---

### Post by M@t on 2004-12-05
I added the deb-src line for hoary universe in my sources.list and it worked. Thanks a lot.

Do you know why packages were not all rebuilt ?

---

### Post by jdong on 2004-12-05
A certain snapshotted sid package may have had build errors...

---

### Post by az on 2004-12-05
Warty's Universe was frozen some time ago, too...

---

### Post by Hikaru79 on 2004-12-09
In this case, you don't really need it in the repository; lilypond.org offers Debian packages which is really all that the Ubuntu repository is anyway. Go here: [http://www.lilypond.org/web/download/#2.4](http://www.lilypond.org/web/download/#2.4)   and download the Sid/Sarge package. Then, in a command line, cd into the directory where you downloaded the .deb file and type:

```
dpkg -i *packagename*
```

Assuming you have all the neccesary dependancies, you'll be all set to go once that finishes :)

---

