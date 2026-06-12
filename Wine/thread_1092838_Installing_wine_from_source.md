---
title: "Installing wine from source"
date: 2009-03-10
forum: Wine
---

### Post by elitenoobboy on 2009-03-10
After patching the latest wine and trying to install from source, I got as far as ./configure --without-freetype and then with make depend, I get an error after a while:
```

gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o window.o window.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o wintab.o wintab.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o x11ddraw.o x11ddraw.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o x11drv_main.o x11drv_main.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xdnd.o xdnd.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xfont.o xfont.c
xfont.c: In function &#8216;XFONT_ReadCachedMetrics&#8217;:
xfont.c:2167: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
xfont.c:2168: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
xfont.c:2175: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
xfont.c:2189: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
xfont.c: In function &#8216;XFONT_WriteCachedMetrics&#8217;:
xfont.c:2303: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
xfont.c:2304: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
xfont.c:2313: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
xfont.c:2343: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xim.o xim.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xinerama.o xinerama.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xrandr.o xrandr.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xrender.o xrender.c
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o xvidmode.o xvidmode.c
../../tools/wrc/wrc --nostdinc -I. -I. -I../../include -I../../include  -D__WINESRC__   -foversion.res version.rc
../../tools/winegcc/winegcc -m32 -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o ime.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o systray.o text.o window.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so -lcomctl32 -luser32 -lgdi32 -ladvapi32 -limm32 -lkernel32 -lntdll -Wb,-dcomctl32 ../../libs/port/libwine_port.a -L/usr/lib  -lXext -lX11   
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/enb/Desktop/1.1.16/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/enb/Desktop/1.1.16/dlls'
make: *** [dlls] Error 2

```

can anybody tell me what to do to fix this?

---

