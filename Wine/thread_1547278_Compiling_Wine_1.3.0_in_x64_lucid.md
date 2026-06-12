---
title: "Compiling Wine 1.3.0 in x64 lucid"
date: 2010-08-06
forum: Wine
---

### Post by thenellt on 2010-08-06
So I've been trying to compile wine 1.3.0 in x64 lucid and am having nothing but problems. I have to compile it by hand because it I want to try to get some games running and wine needs source patches to run them. Anyway, I have downloaded the lib32 libraries (600 MB's) and have a lib32 folder with those libraries in it. When I try to run this 
CC="ccache gcc" LDFLAGS="-L./lib32" ./configure -v
make
sudo make install 
I get errors about gcc not working with the -m32 flag. I have a symlink in my /usr/bin/ to gcc 4.1 and thats the version its using, but it is the x64 version. So do I need to install some 32 bit gcc version?

---

### Post by thenellt on 2010-08-07
Bump.
So nobody around has any experience with 32/64bit gcc and compiling things?

---

### Post by Ferrat on 2010-08-07
why don't you use the wine repos? they have uptodate versions that work good, it's really only if you have problems you need to do it yourself :)

---

### Post by thenellt on 2010-08-07
As I said above, I'm trying to get some games to run which require a patched version of wine and you have to do the patching to the source code.

---

### Post by ajackson on 2010-08-07
Have you tried [this]("http://wiki.winehq.org/WineOn64bit#head-f6a7d1b561fe7ce26bb3a061d96d16380d90d618")?

---

### Post by thenellt on 2010-08-07
Thats what I started with and thats how I got all the correct 32bit libraries but for some reason that doesn't seem to fix the fact that the only versions of gcc on my system are x64 4.1.7 and 4.4. It wants x32 bit gcc and I don't know how to get that or where to put it.

---

