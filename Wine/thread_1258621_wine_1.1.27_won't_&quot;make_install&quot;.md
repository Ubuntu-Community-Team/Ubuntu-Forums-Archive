---
title: "wine 1.1.27 won't &quot;make install&quot;"
date: 2009-09-05
forum: Wine
---

### Post by chris1950 on 2009-09-05
Downloaded the bz2 file. ./configure and make worked fine but  su -c "make install" is run it asks for password when I enter the password it says wrong password try again - yes the cap key is off. How do I get it to install?:confused:

Downloaded deb package and installed.

---

### Post by ackanao on 2009-09-05
I don't know why are you using "su -c"; just use:  ```
sudo make install
``` or ```
sudo checkinstall
``` if you want to create deb package.

---

