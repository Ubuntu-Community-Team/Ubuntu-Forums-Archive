---
title: "Ubuntu LiveCD architecture rules!"
date: 2005-05-22
forum: The Cafe
---

### Post by jdong on 2005-05-22
Hey guys, I just remastered a Ubuntu LiveCD, adding Backports updates, Openoffice 1.9.100, Azureus/Java, GCC, and WINE, but removing the Windows goodies in the process.


I have to praise Ubuntu for how easy customizing a LiveCD is. This was much easier than Knoppix remastering, which I never really got to work correctly! :)

Also, I like how everything is read-write, without the use of Unionfs. (Device-mapper is the magic word)

---

### Post by jdong on 2005-05-22
BTW, you can find my modified LiveCD at:
[http://backports.ubuntuforums.org:6969/](http://backports.ubuntuforums.org:6969/) , named [adambots-livecd-base_20050520.iso]("http://backports.ubuntuforums.org:6969/file?info_hash=%82%B5%B9%FA6%20%9B%2C%81%1DA%3B%08%88%99.%EC%7E%9Cl")

It's going to be the base OS of a LiveCD for US FIRST robotics development, but currently, it's the standard Hoary LiveCD with all stable backports available, plus Openoffice.org 2.0 beta 100, WINE , GCC, Java, and Azureus. It's always good to have an up-to-date LiveCD that isn't affected by numerous security flaws ;)

---

