---
title: "Wine 1.1.34 failing to compile from Source on 9.10 64bit"
date: 2009-12-11
forum: Wine
---

### Post by beastrace91 on 2009-12-11
Howdy All,

So I've compiled Wine quite a few times now... and this is the first time I am trying to do it on Karmic 64bit and I am hitting the following error message when I run **make depend && make** ```
make[2]: Leaving directory `/home/jeff/Downloads/wine-1.1.34/dlls/winejoystick.drv'
make[2]: Entering directory `/home/jeff/Downloads/wine-1.1.34/dlls/winemp3.acm'
../../tools/winegcc/winegcc -m32 -B../../tools/winebuild --sysroot=../.. -shared ./winemp3.acm.spec    mpegl3.o        -o winemp3.acm.so  -lwinmm -luser32 -lkernel32  ../../libs/port/libwine_port.a -lmpg123  
mpegl3.o: In function `MPEG3_Reset':
/home/jeff/Downloads/wine-1.1.34/dlls/winemp3.acm/mpegl3.c:401: undefined reference to `mpg123_feedseek'
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winemp3.acm.so] Error 2
make[2]: Leaving directory `/home/jeff/Downloads/wine-1.1.34/dlls/winemp3.acm'
make[1]: *** [winemp3.acm] Error 2
make[1]: Leaving directory `/home/jeff/Downloads/wine-1.1.34/dlls'
make: *** [dlls] Error 2

```

Any suggestions on what I should do? Didn't get any hits on Google pertaining to the issue and I'm not quite sure what the error means off hand. I have the Wine build-dep installed & the build-essential package

Thanks in advance,
~Jeff

---

### Post by Lenlen on 2009-12-12
Not that I want to add a "me too" post, but I'm getting a similar error attempting to compile Wine 1.1.34 from source on 64-bit 9.10.  Been scouring Google for hours and trying different things (such as not applying patches, which is why I'm doing it from source) to no avail.

I've also tried compiling 1.1.33, and run into the same problem.

```
make[2]: Entering directory `/home/len/wine-1.1.34/dlls/winecoreaudio.drv'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/len/wine-1.1.34/dlls/winecoreaudio.drv'
make[2]: Entering directory `/home/len/wine-1.1.34/dlls/wined3d'
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wstrict-prototypes -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o directx.o directx.c
directx.c: In function ‘InitAdapters’:
directx.c:4715: error: ‘struct wined3d_adapter’ has no member named ‘driver’
directx.c:4717: error: ‘struct wined3d_adapter’ has no member named ‘driver’
directx.c:4722: error: ‘struct wined3d_adapter’ has no member named ‘description’
directx.c:4724: error: ‘struct wined3d_adapter’ has no member named ‘description’
make[2]: *** [directx.o] Error 1
make[2]: Leaving directory `/home/len/wine-1.1.34/dlls/wined3d'
make[1]: *** [wined3d] Error 2
make[1]: Leaving directory `/home/len/wine-1.1.34/dlls'
make: *** [dlls] Error 2
```

---

### Post by beastrace91 on 2009-12-12
Ahh alrighty, I figured it was indeed an issue with something that had changed in Karmic. [Throwing up a post](http://forum.winehq.org/viewtopic.php?p=36641#36641) on the Wine boards and see if I get something useful there.

~Jeff

---

### Post by beastrace91 on 2009-12-12
Solution: ```
sudo apt-get remove libmpg123-dev
```

Regards,
~Jeff

---

### Post by Zularan on 2009-12-15
Thanks for the thread, I ran into this issue today compiling a patched WINE on 64bit Ubuntu (albeit Lucid)

Found the bug listed here it has existed since Jaunty from what I can tell.  The good news is /usr/include/mpg123.h can be patched to fix it for now.

[http://bugs.winehq.org/show_bug.cgi?id=20042](http://bugs.winehq.org/show_bug.cgi?id=20042) is the bug thread.

[http://bugs.winehq.org/attachment.cgi?id=24513](http://bugs.winehq.org/attachment.cgi?id=24513) is the patch, copy/paste and save locally.


```
 sudo patch -p1 < [patchfile name]
```

enter ```
/usr/include/mpg123.h
``` when it asks for the file location (I'm sure there's a way to include this in the commandline.)

```
./configure
``` etc



removing mpg123-dev works but will compile WINE without mp3 or something, the bug talk is complicated but it all works for me.

Hope this is helpful.

---

### Post by beastrace91 on 2009-12-15
Thanks for the tips! I'll be giving that patch a go later this week hopefully.

Cheers,
~Jeff

---

