---
title: "Building wine deb package myself"
date: 2009-12-28
forum: Wine
---

### Post by wiscalico on 2009-12-28
I want to try build the wine package because I want to put pulse audio patches on top of it.

The ppa from Neil Wilson havn't been updated since 1.1.31 thus I would like to try do it myself. I'm running Karmic 64bit.

But before I apply the patches I wanted to make sure I could build the package **without any modifications**.

First I added the repository reference by winehq.com where the newest Wine is ([http://www.winehq.org/download/deb):](http://www.winehq.org/download/deb):)

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
```

And updated my package list:
```
sudo apt-get update
```

Then I fetched the source and its dependencies:

```
apt-get source wine
```

Which fetches:

wine1.2 1.1.35-0ubuntu1

I also fetches the dependencies with:

```
sudo apt-get build-dep wine
```


Now enter the source directory and try to build with the following:

```
dpkg-buildpackage -rfakeroot -uc -b
```

And after a while dies here:

```
make[3]: Entering directory `/home/je/wine1.2-1.1.35/dlls/acledit'
x86_64-linux-gnu-gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wstrict-prototypes -Wwrite-strings -Wtype-limits -Wpointer-arith  -Wall -g -O2  -o main.o main.c
../../tools/winegcc/winegcc -m32 -B../../tools/winebuild --sysroot=../.. -shared ./acledit.spec    main.o        -o acledit.dll.so  -lkernel32  ../../libs/port/libwine_port.a   
Usage: nm {start|stop}
main.o: In function `DllMain':
/home/je/wine1.2-1.1.35/dlls/acledit/main.c:45: undefined reference to `DisableThreadLibraryCalls'
../../dlls/winecrt0/libwinecrt0.a(stub.o): In function `__wine_spec_unimplemented_stub':
/home/je/wine1.2-1.1.35/dlls/winecrt0/stub.c:35: undefined reference to `RaiseException'
/usr/bin/ld: acledit.dll.so: hidden symbol `RaiseException' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
winegcc: x86_64-linux-gnu-gcc failed
make[3]: *** [acledit.dll.so] Error 2
```

I don't really know what to look after... I assumed an unmodified package would build without much trouble :-S
Can't anyone help me understand what is going wrong?

---

### Post by beastrace91 on 2009-12-28
I'm not 100% but you *might* be having the same issue I had [here](http://ubuntuforums.org/showthread.php?t=1352542). Are you running Ubuntu 9.10 64bit?

~Jeff

---

### Post by wiscalico on 2009-12-28
> **beastrace91 said:**
> I'm not 100% but you *might* be having the same issue I had [here](http://ubuntuforums.org/showthread.php?t=1352542).

I don't even have the package libmpg123-dev installed :(

> **beastrace91 said:**
> Are you running Ubuntu 9.10 64bit?

Yes I'm running Karmic 64bit

---

### Post by beastrace91 on 2009-12-28
Just for ***** and giggles why don't you try downloading the Wine source from [here](http://sourceforge.net/projects/wine/files/Source/) instead of getting it through apt and see if it compiles that way.

Regards,
~Jeff

---

### Post by simonckf on 2009-12-29
Try this

sudo apt-build install wine --reinstall

---

