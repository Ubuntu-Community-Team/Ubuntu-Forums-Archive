---
title: "patching and compiling wine OK, but doesn't work after that"
date: 2010-03-31
forum: Wine
---

### Post by cyphaw on 2010-03-31
Hi everybody, here is my problem:

As the title say, I tried to patch and compile wine 1.1.39 the play correctly at Mirror's Edge.
So I downloaded the sources from sourceforge and applied this patch: [http://bugs2.winehq.org/attachment.cgi?id=11303](http://bugs2.winehq.org/attachment.cgi?id=11303) In fact I directly edited the sources since the patch is not exactly for this version.

And after that,
```
apt-get build-dep wine          (as root)
./configure --enable-win64
make depend && make
make install          (as root)
```Everything went perfectly but when I try to lunch the setup of Mirror's Edge, I have this:
```
laurent@ithil ~ % wine /media/mirror/Setup.exe
Trying to load PE image for unsupported architecture (I386)
err:winedevice:ServiceMain driver L"SecDrv" failed to load
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\winhttp.dll" (error=80)
Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/laurent/.wine' has been updated.
Trying to load PE image for unsupported architecture (I386)
Trying to load PE image for unsupported architecture (I386)
wine: Bad EXE format for Z:\media\mirror\Setup.exe

```This is not normal, since I was able to install and run the game with PlayOnLinux and with wine installed from the repositories, and I don't think that the patch is the problem.

I think that the problem may come from the fact that I have a 64bits processor (Intel Core2Duo P7550 on a macbook pro).

I will try with the sources from the repository version, but if you have any idea of why there is a problem / how to correctly compile win on 64 bits comp (couldn't find good up to date documentation).

Thanks

cyphaw

---

### Post by asdfoo on 2010-04-01
> **cyphaw said:**
> Hi everybody, here is my problem:

As the title say, I tried to patch and compile wine 1.1.39 the play correctly at Mirror's Edge.
So I downloaded the sources from sourceforge and applied this patch: [http://bugs2.winehq.org/attachment.cgi?id=11303](http://bugs2.winehq.org/attachment.cgi?id=11303) In fact I directly edited the sources since the patch is not exactly for this version.

And after that,
```
apt-get build-dep wine          (as root)
./configure --enable-win64
make depend && make
make install          (as root)
```Everything went perfectly but when I try to lunch the setup of Mirror's Edge, I have this:
```
laurent@ithil ~ % wine /media/mirror/Setup.exe
Trying to load PE image for unsupported architecture (I386)
err:winedevice:ServiceMain driver L"SecDrv" failed to load
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\winhttp.dll" (error=80)
Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/laurent/.wine' has been updated.
Trying to load PE image for unsupported architecture (I386)
Trying to load PE image for unsupported architecture (I386)
wine: Bad EXE format for Z:\media\mirror\Setup.exe

```This is not normal, since I was able to install and run the game with PlayOnLinux and with wine installed from the repositories, and I don't think that the patch is the problem.

I think that the problem may come from the fact that I have a 64bits processor (Intel Core2Duo P7550 on a macbook pro).

I will try with the sources from the repository version, but if you have any idea of why there is a problem / how to correctly compile win on 64 bits comp (couldn't find good up to date documentation).

Thanks

cyphaw


The problem is that you've supplied this flag "--enable-win64" to configure.

why are you doing this? ok - maybe you don't understand, this is to build a 64bit ONLY version of Wine.  This is currently unstable and only for developers.

You need to build 32bit Wine to run 32bit programs.  Everyone with a 64bit cpu + distro uses 32bit Wine.

---

### Post by cyphaw on 2010-04-01
> **asdfoo said:**
> The problem is that you've supplied this flag "--enable-win64" to configure.

why are you doing this? ok - maybe you don't understand, this is to build a 64bit ONLY version of Wine.  This is currently unstable and only for developers.

You need to build 32bit Wine to run 32bit programs.  Everyone with a 64bit cpu + distro uses 32bit Wine.

I know that I must build a 32 bits wine, but it didn't work without this this flag on my previous tests, certainly because of missing libraries.

Anyway, I finally managed to correctly compile wine 1.1.31 from the sources of the ubuntu repo and build a .deb package. It is not the last one, but it works. When I try to compile a newer version, I still have warning about missing lib32 libraries (that are installed). I suppose that they are too old and upgrading them means upgrading libc6 too, so I'll wait until lucid (or go back to Debian, maybe :þ )

---

### Post by asdfoo on 2010-04-01
Try the instructions here [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

do not use the --enable-win64

---

