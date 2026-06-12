---
title: "Ubuntu help installing WINE-1.2-RC1"
date: 2010-06-05
forum: Wine
---

### Post by Michael64 on 2010-06-05
I have a problem installing WINE that I hope you guys can fix.

Code I used:

1. Downloaded wine-1.2-rc1.tar.bz2 off the website
2. sudo tar xvjf wine-1.2-rc1.tar.bz2
3. cd WINE-1.2-rc1
4. ./configure
5. make
6. su -c "make install"

This is the last two lines I get after completing installation:

make[1]: Leaving directory `/home/michael/wine-1.2-rc1/tools/wrc'
michael@michael:~/wine-1.2-rc1$ 

After installation there is no WINE program. I can't go into the applications section head and see WINE. Am I doing something wrong? Its like nothing was ever installed.

---

### Post by cogadh on 2010-06-05
Is there a particular reason you need to compile it from source yourself rather than using the pre-compiled Ubuntu packages?

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by beastrace91 on 2010-06-06
And if you do really want to build Wine from source be sure to install all of it's build dependencies first with the command **sudo apt-get build-dep wine**

~Jeff

---

