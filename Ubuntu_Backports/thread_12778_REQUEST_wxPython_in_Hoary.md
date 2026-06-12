---
title: "REQUEST: wxPython in Hoary"
date: 2005-01-26
forum: Ubuntu Backports
---

### Post by Quest-Master on 2005-01-26
Hey, I was just told that the wxPython in Hoary currently uses GTK2, while the wxPython we are left with in Warty still uses the born-to-die GTK1. The package is known as libwxgtk2.4-python in Warty. I don't know what version Hoary has, but I'm guessing 2.5? ;)

---

### Post by jdong on 2005-01-26
Well, it's still version 2.4, just a new version...

Will this backport break any Python progs written for this older version of wxPython?

---

### Post by Quest-Master on 2005-01-26
From what I remember, no. The 2.x wxPython's are all backwards-compatible and so on, and if I'm wrong, I'll be the one to test it and find out. ;)

---

### Post by jdong on 2005-01-26
Ok, then I'll build these when I get a chance... or at least see if Python dependencies would let me.

---

### Post by Quest-Master on 2005-01-26
/me can't wait. :D

Finally get to do some serious work with wxPython and wxGlade. Haven't done any since my Windows days because of my fear of GTK1 on a modern Gnome desktop. :)

---

### Post by jdong on 2005-01-26
It has a dependency on python 2.4, but I forced a build against python 2.3 (Warty's)...

Cross our fingers.... (OOo didn't like it when I did this!)

---

### Post by Quest-Master on 2005-01-26
Has it been put up on the repos. yet?

---

### Post by jdong on 2005-01-26
It's still building.... Rebuilding 20MB of source isn't exactly that quick.

BTW, I'm worried about the rest of wxwindows -- which has to be backported along with wxPython.....

Even if wxpython has backwards compatibility, I'm not sure if the rest of wxwindows can be backwards compatible..... Please test that too.

---

### Post by Quest-Master on 2005-01-26
Ok, from the developers of it that I've talked to, they said everything SHOULD be fine but should be tested first as well.

Your call.

---

### Post by jdong on 2005-01-26
Bad news:

```

h_gauge.o xh_html.o xh_menu.o xh_notbk.o xh_panel.o xh_radbt.o xh_radbx.o xh_sizer.o xh_slidr.o xh_spin.o xh_stbmp.o xh_sttxt.o xh_text.o xh_listb.o xh_toolb.o xh_stlin.o xh_bmp.o xh_unkwn.o xh_bmpbt.o xh_cald.o xh_listc.o xh_scrol.o xh_stbox.o xh_tree.o xh_frame.o xh_gdctl.o xh_scwin.o xh_split.o xh_wizrd.o xh_statbar.o
ranlib ../../../lib/libwx_gtk_xrc-2.4.a
make[2]: Leaving directory `/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1/objs_gtk_st/contrib/src/xrc'
make[1]: Leaving directory `/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1/objs_gtk_st/contrib/src'
touch build-contrib-static-stamp
make[1]: Entering directory `/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1'
cd wxPython \
        && rm -rf licence \
        && rm -rf build \
        && rm -rf contrib/gizmos/contrib \
        && rm -rf contrib/ogl/contrib \
        && rm -rf contrib/stc/contrib \
        && rm -rf contrib/xrc/contrib \
        && rm -rf *.pyc
make[1]: Leaving directory `/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1'
rm -f build-gtk-dbg-py-stamp
dh_testdir
touch docs/lgpl.txt
cd wxPython \
        && python2.4 ./setup.py build IN_CVS_TREE=1 WX_CONFIG='/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1/objs_gtk_sh/wx-config --prefix=/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1 --exec-prefix=/home/jdong/temp-bk/wxwindows2.4-2.4.2.6ubuntu1/objs_gtk_sh'
/bin/sh: line 1: python2.4: command not found
make: *** [build-gtk-py-stamp] Error 127


```

It really wants Python 2.4.....

---

### Post by Quest-Master on 2005-01-26
No way.

:(

---

