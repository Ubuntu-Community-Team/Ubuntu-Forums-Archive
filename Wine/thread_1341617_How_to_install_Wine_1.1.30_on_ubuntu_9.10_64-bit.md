---
title: "How to install Wine 1.1.30 on ubuntu 9.10 64-bit"
date: 2009-11-29
forum: Wine
---

### Post by CT_0000 on 2009-11-29
I'm trying to accomplish this. I have the .tar.bz2 file for that version and want to install it. Version 1.1.33 (current) causes problems but that (and the stable version, which also won't work for me) are the only versions I can get out of the ubuntu software center.

I know I need to get all the 32-bit developmental packages but whats the easiest way to do that?

Thanks.

---

### Post by beastrace91 on 2009-11-30
Extract the .tar.bz2 file and then CD into the directory you extracted it to, once you are there run the following commands in terminal: ```
sudo apt-get build-dep wine
sudo apt-get install checkinstall
./configure
make
sudo checkinstall
```

First line grabs all the dependencies you need to compile Wine, the second installs a program called "checkinstall" which allows you to install an application compiled from source using the package manager (which is better than just running plain **make install**), third line configures the setup, forth line compiles the source, and the final line installs the newly compiled program using apt-get and creates a .deb installer for it in case you want to reinstall it later :D

Cheers,
~Jeff

---

### Post by Allyanora on 2009-12-02
thank you a lot for this info, I didn't manage to install in any other way wine on 9.10

thank you, you helped me a lot!

---

