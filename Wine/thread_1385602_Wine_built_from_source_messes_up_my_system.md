---
title: "Wine built from source messes up my system"
date: 2010-01-19
forum: Wine
---

### Post by man_bash on 2010-01-19
Well, long story short, since mp3's are not supported with wine/karmic and are needed for some games, I decided to try to build them from source. what i ran

./configure
>>found all of the dev packages needed, except freetype
./configure --without-freetype
>>configured
./make
>>no problems there
sudo make install
>>installed

Then an update comes in for some package, and now I get an error about wine saying "Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal." Wine itself works (with new problems), but I cannot remove it nor can I reinstall it. I tried to rebuild and install the same version of wine, then older, then stable - nothing works! What can I do?

---

### Post by rocky5051 on 2010-01-19
If you forgot to uninstall the wine package that was installed before building wine from source and installing it, you may have botched the deb package installation. The best thing I could recommend is this:

```
sudo apt-get purge wine
```

Assuming you still have the built binaries that you compiled and installed, jump into that directory and then make uninstall wine.

```
sudo make uninstall
```

Once you've done that, delete that folder and re-download, and re-extract the wine source package, preferably to your home directory. Then just grab all the dependencies and build wine:

```
sudo apt-get build-dep wine
./configure
make depend && make
make install
```

If you're trying to build on a 64 bit environment though, look at this tutorial I put together and skip to the step that talks about building wine. There are some tricks you need to perform to get wine to build right.

[http://ubuntuforums.org/showthread.php?t=1344962](http://ubuntuforums.org/showthread.php?t=1344962)

Good luck. :KS

---

### Post by beastrace91 on 2010-01-19
There is a patch for building Wine on 64bit with mp3 support - I use it personally to play Morrowind :)

[http://ubuntuforums.org/showpost.php?p=8503423&postcount=5](http://ubuntuforums.org/showpost.php?p=8503423&postcount=5)

~Jeff

---

### Post by man_bash on 2010-01-20
Unfortunately, I deleted the sources.
So I re-downloaded them (wine 1.1.36), and tried to re-do all the step with ```
sudo make uninstall
``` instead of ```
sudo make install
```
No dice.

This guy:
```
sudo apt-get purge wine
``` does not work either.

What I did prior to building wine from source was:
copy /home/user/.wine to /home/user/.wine.bak
removed wine with SPM - all packages
only then did I try to build wine.

I was not too worried about gcc, I have to use C for school sometimes, so I installed gcc with all the requirements and devs (just in case) via SPM.

I also forgot to add that I did runs "make depend", separately though, instead of "make depend && make" it was "make depend" then "make". Not sure how that would affect anything though.

beastrace91: that is exactly the game I wanted to play! It worked FANTASTIC with 9.04, wine, and my good ol' 8800GT. As a matter of fact, I was getting better FPS than with windows (not sure why....), and much better loading times (ext3 VS ntfs?). Now it is 9.10 + wine + ATi 4870. I was going by instructions from the WineHQ page for Morrowind: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1331](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1331) . I also changed the line:

mpg123_feedseek(aad->mh, 0, SEEK_SET, NULL);
to
mpg123_feedseek_64(aad->mh, 0, SEEK_SET, NULL);

As per instructions.

---

### Post by rocky5051 on 2010-01-20
The part about gcc in that tutorial was to expose a fix in Wine that the current stable gcc does not allow. So that part wasn't necessary.

The only way short of nuking your Ubuntu install and reinstalling it that I could think of for fixing this problem would be to remove wine's files manually and config settings, but I wouldn't have the faintest idea where to start. Not to mention how dangerous that could be...

Also, make depend && make is two different commands, the AND operator is just a way to put things in queue so that's perfectly fine.

As for getting better fps on Ubuntu, I would imagine the Ubuntu environment has less overhead than your Windows setup had. That'd probably be the reason why.

---

### Post by Brebs on 2010-01-21
> **man_bash said:**
> ./make
I'd be surprised if that worked. The command is:

make

Which runs /usr/bin/make (or whatever's first in PATH), rather than the make executable in the current directory.

---

### Post by d3v1150m471c on 2010-01-21
it's not going to do anything unless "make" is an executable file in your home directory

---

### Post by man_bash on 2010-01-21
...and to the last two smartbums I would say, how, if I did not properly "make" (ie compile the bloody thing), would wine install at all using code "sudo make install" from sources?

---

### Post by vhaarr on 2010-01-21
> **man_bash said:**
> ...and to the last two smartbums

What does "smartbum" mean?

---

### Post by beastrace91 on 2010-01-22
Urg. Yes - the only way to remove Wine if you lost the files you installed from is to go and manually remove all the install files - fyi this is why I also use **sudo checkinstall** instead of **sudo make install** so that way any source I compile is installed via the package manager in case I want to remove it later on.

Also - good luck running *anything* 3D under Wine with an ATI card.

~Jeff

---

### Post by padeco on 2010-02-13
hi guys,
i am trying to install an older version on wine, because the latest update stuffed up my system. i installed dependencies etc.
./configure will work fine; when i run
make

i get the following error:

gcc -c -I. -I. -I../../include -I../../include -I/usr/include/freetype2  -D__WINESRC__ -D_GDI32_ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o freetype.o freetype.c
freetype.c:166: error: ‘FT_MulFix’ undeclared here (not in a function)
freetype.c:166: warning: type defaults to ‘int’ in declaration of ‘pFT_MulFix’
freetype.c: In function ‘WineEngGetOutlineTextMetrics’:
freetype.c:5009: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5010: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5012: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5020: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5020: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5024: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5028: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5109: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5110: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5111: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5112: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5113: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5114: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5115: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5116: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5117: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5122: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5123: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5124: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5125: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5126: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5127: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5128: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5129: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5130: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5131: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5136: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5137: error: called object ‘pFT_MulFix’ is not a function
make[2]: *** [freetype.o] Error 1
make[2]: Leaving directory `/home/path/programs/wine-1.0.1/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/path/programs/wine-1.0.1/dlls'
make: *** [dlls] Error 2

any idea of what is wrong?

many thanks,
padeco

---

