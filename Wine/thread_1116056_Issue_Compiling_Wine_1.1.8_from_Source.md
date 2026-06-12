---
title: "Issue Compiling Wine 1.1.8 from Source"
date: 2009-04-04
forum: Wine
---

### Post by beastrace91 on 2009-04-04
I am trying to compile Wine 1.1.8 from source, when I run ./configure I get this error message in console:

```
jeff@jeff-laptop:~/Desktop/wine-1.1.8$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: in `/home/jeff/Desktop/wine-1.1.8':
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Any ideas how I can resolve this?

~Jeff

---

### Post by albinootje on 2009-04-04
> **beastrace91 said:**
> 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Do this :
```

sudo apt-get install build-essential patch

```
And try again after that.

And .. why are you compiling from source ? 
Do you need a patched Wine binary ?

---

### Post by albinootje on 2009-04-04
Also interested to read (and use) :
[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)
[http://tuxarena.blogspot.com/2008/09/how-to-compile-and-install-wine-114-in.html](http://tuxarena.blogspot.com/2008/09/how-to-compile-and-install-wine-114-in.html)
->
```

sudo apt-get build-dep wine

```

---

### Post by beastrace91 on 2009-04-04
I already have build-essential installed. But should my dependencies be missing wouldn't it throw a different error when running configure? Anywho I'll try running build-dep wine when I get home from work and see if that helps any.

~Jeff

---

### Post by albinootje on 2009-04-04
> **beastrace91 said:**
> I already have build-essential installed. But should my dependencies be missing wouldn't it throw a different error when running configure? Anywho I'll try running build-dep wine when I get home from work and see if that helps any.

It's possible that you also need the kernel header files, but I thought that the build-essential meta-package also installed that.
Which Ubuntu release are you using ?
> 
configure: error: C compiler cannot create executables
See `config.log' for more details.

The config.log should also be able to tell you more.

---

### Post by beastrace91 on 2009-04-04
Running on the Jaunty beta atm, I'll take a peek at the config.log and see what it says.

~Jeff

---

### Post by el-mar01 on 2009-04-05
You don't need to compile WINE .. you can EASILY install it from the official WINE Personal Package Archive !!!

Click on this link to see how to add the official WINE Personal Package Archive from your ubuntu system: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by beastrace91 on 2009-04-05
I'm well aware that Wine runs from the repositories, this is how I currently have it installed. How ever take a peek at [this thread](http://ubuntuforums.org/showthread.php?t=1113311) and you will see why I am recompiling this slightly older version from source.

```
sudo apt-get build-dep wine
``` worked like a charm! Thanks much.

~Jeff

---

