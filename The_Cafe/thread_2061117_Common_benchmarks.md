---
title: "Common benchmarks?"
date: 2012-09-21
forum: The Cafe
---

### Post by TheGuyWithTheFace on 2012-09-21
I've recently gotten more into tinkering with computers, and I was thinking it'd be cool to have benchmarks before and after.

I'm currently using hardinfo, it looks pretty nice, and it's nice to see the specs as well as the benchmarks. 

Does anyone have a favorite benchmark, or at least a widely used and accepted one they use?

---

### Post by CharlesA on 2012-09-21
I use [Prime95]("http://www.softpedia.com/get/System/Benchmarks/LinX-benchmark.shtml") and [LinX]("http://www.softpedia.com/get/System/Benchmarks/LinX-benchmark.shtml") for stability testing.

Prime95 is crossplatform, but LinX is Windows-only.

---

### Post by TheGuyWithTheFace on 2012-09-21
Wait, linX is windows only? That's a bit of a misnomer...

so, those are for making sure it doesn't overheat and such when used at maximum capacity?

---

### Post by CharlesA on 2012-09-21
> **TheGuyWithTheFace said:**
> so, those are for making sure it doesn't overheat and such when used at maximum capacity?

Yeah, I use them for make sure an overclock is stable or when troubleshooting memory/CPU problems when memtest says the memory is ok.

---

### Post by TheGuyWithTheFace on 2012-09-21
I forgot to mention, I'd love some opinions on GPU benchmarks as well.

---

### Post by pqwoerituytrueiwoq on 2012-09-21
there is this one for GPUs
[http://unigine.com/products/heaven/download/](http://unigine.com/products/heaven/download/)
i had to modify the launcher script for 64bit
```
#!/bin/bash
cd "`dirname $0`"
cd ./bin
if [ "`uname -m`" == "x86_64" ]; then
    ./launcher_x64 -config ../data/launcher/launcher.xml
else
    ./launcher_x86 -config ../data/launcher/launcher.xml
fi

```

---

### Post by MdMax on 2012-09-22
Hello !

You can also try the Phoronix Test Suite:
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)
[http://www.phoronix.com/](http://www.phoronix.com/)

---

### Post by TheGuyWithTheFace on 2012-09-22
Cool, thanks!

---

### Post by grandsatrap on 2012-09-22
> **MdMax said:**
> Hello !

You can also try the Phoronix Test Suite:
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)
[http://www.phoronix.com/](http://www.phoronix.com/)

I'm trying to download and run it. I did 
```
sudo apt-get install phoronix-test-suite
```

This command works ```
phoronix-test-suite
``` , but I can't get the GUI to work
```
phoronix-test-suite gui

The PHP GTK module must be loaded for the GUI.
This module can be found @ http://gtk.php.net/

```
There is no apt-get install for this that I can see.  I tried doing this (I have no idea what it does):
```
svn co http://svn.php.net/repository/gtk/php-gtk/trunk php-gtk
cd php-gtk
./buildconf

``` 
but it gave me an error message which I can't fix.
```
/bin/sh: phpize: not found
make: *** [buildmk.stamp] Error 127

```

How do I get Phoronix GUI to work?

---

### Post by grandsatrap on 2012-09-22
Oh! I just found another thread about this:

[http://ubuntuforums.org/showthread.php?t=1550470](http://ubuntuforums.org/showthread.php?t=1550470)

---

