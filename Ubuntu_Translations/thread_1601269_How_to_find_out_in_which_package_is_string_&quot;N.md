---
title: "How to find out in which package is string &quot;No address associated with hostname&quot;"
date: 2010-10-20
forum: Ubuntu Translations
---

### Post by abcuser on 2010-10-20
Hi,
I am trying to translate PyChess (chess game) and I see some strings are not available in PyChess. I have asked developer if there is some missing string, but he responded that this string comes from Python environment. Is there any way to find out in which source Python file is this translation from, that I could check that string and translate it?
Thanks

---

### Post by dpm on 2010-11-22
If the string is not translatable, there is no easy way to find it.

One thing you can do is to download the PyChess code from [http://pychess.googlecode.com/files/pychess-0.10rc1.tar.gz](http://pychess.googlecode.com/files/pychess-0.10rc1.tar.gz), unpack the archive and do a full text search for that string.

In order for the string to be translatable it should be enclosed in _(). If it's not, I'd recommend getting in touch with the developer again and point him to the string.

---

