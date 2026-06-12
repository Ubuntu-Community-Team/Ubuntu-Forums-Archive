---
title: "vmware: hardy, locking assertion failure"
date: 2008-05-18
forum: Virtualisation
---

### Post by floogy on 2008-05-18
Hi, 
I got this error since I upgraded from gutsy to hardy, I use the any-yany-patch-117a, and followed all steps in 
[http://ubuntuforums.org/showpost.php?p=4862887](http://ubuntuforums.org/showpost.php?p=4862887)

```
$ vmware
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /emul/ia32-linux/usr/lib/libxcb-xlib.so.0 [0xf700d767]
#1 /emul/ia32-linux/usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf700d8b1]
#2 /emul/ia32-linux/usr/lib/libX11.so.6(_XReply+0xfd) [0xf7e841bd]
#3 /usr/local/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d7b969]
#4 /usr/local/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d7bf4c]
#5 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bc1180]
#6 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bc1d2c]
#7 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b91c14]
#8 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b9e24f]
#9 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b91c14]
#10 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b9db34]
#11 /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aa2298]
#12 /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aa2586]
#13 /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aa477e]
#14 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cb7459]
#15 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c9f3a1]
#16 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c9f076]
#17 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cb66eb]
#18 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7cb5d46]
#19 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7cb60b8]
Locking assertion failure.  Backtrace:
#0 /emul/ia32-linux/usr/lib/libxcb-xlib.so.0 [0xf700d767]
#1 /emul/ia32-linux/usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf700d81e]
#2 /emul/ia32-linux/usr/lib/libX11.so.6 [0xf7e83518]
#3 /emul/ia32-linux/usr/lib/libX11.so.6(XAddExtension+0x2c) [0xf7e66c9c]
#4 /usr/local/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d73ed7]
#5 /usr/local/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d728b1]
#6 /usr/local/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d72d39]
#7 /usr/local/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d72ec0]
#8 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bbf9b6]
#9 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bc1d75]
#10 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b91c14]
#11 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b9e24f]
#12 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b91c14]
#13 /usr/local/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b9db34]
#14 /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aa2298]
#15 /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aa2586]
#16 /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aa477e]
#17 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cb7459]
#18 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c9f3a1]
#19 /usr/local/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c9f076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
```

it's similar to: [https://bugs.launchpad.net/xorg-server/+bug/185311](https://bugs.launchpad.net/xorg-server/+bug/185311)
and bug #185311:
hardy, locking assertion failure
[https://bugs.launchpad.net/xorg-server/+bug/185311](https://bugs.launchpad.net/xorg-server/+bug/185311)

```
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
```
seems to be a minor issue, with harmless effects.

How to find a solution similar to the solution fo java described in the bug:
```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun/jre/lib/amd64/xawt/libmawt.so
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/xawt/libmawt.so
export LIBXCB_ALLOW_SLOPPY_LOCK=true
export LIBXCB_ALLOW_SLOPPY_LOCK=1
```

but which applies to vmware.

I'm running ubuntu hardy/amd64

```
 uname -a
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

---

### Post by floogy on 2008-05-31
How can I link against ia32-libs, because this bug is already fixed:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/99385](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/99385)
```
libxcb.so.1 => /emul/ia32-linux/usr/lib/libxcb.so.1 (0xf73c9000)
```
```
$ dpkg -L ia32-libs|grep libxcb.so.1
/usr/lib32/libxcb.so.1.0.0
/usr/lib32/libxcb.so.1
```


I solved some of the issues above:

```
$ dpkg -S /emul/ia32-linux/usr/lib/
dpkg: /emul/ia32-linux/usr/lib/ not found.
```

/usr/lib32/ is a symlink to /emul/ia32-linux/usr/lib/, that's the reason for this behaviour.

I noticed, that vmware missed some libs:

```
$ ldd /usr/lib64/vmware/bin/vmware
   linux-gate.so.1 =>  (0xffffe000)
   libdl.so.2 => /lib32/libdl.so.2 (0xf7f6c000)
   libm.so.6 => /lib32/libm.so.6 (0xf7f46000)
   libX11.so.6 => /emul/ia32-linux/usr/lib/libX11.so.6 (0xf7e5f000)
   libXext.so.6 => /emul/ia32-linux/usr/lib/libXext.so.6 (0xf7e51000)
   libXi.so.6 => /emul/ia32-linux/usr/lib/libXi.so.6 (0xf7e49000)
   libexpat.so.0 => /usr/lib32/libexpat.so.0 (0xf7e28000)
   libfontconfig.so.1 => /emul/ia32-linux/usr/lib/libfontconfig.so.1 (0xf7dfd000)
   libfreetype.so.6 => /emul/ia32-linux/usr/lib/libfreetype.so.6 (0xf7d8d000)
   libXrender.so.1 => /emul/ia32-linux/usr/lib/libXrender.so.1 (0xf7d85000)
   libXft.so.2 => /emul/ia32-linux/usr/lib/libXft.so.2 (0xf7d73000)
   libglib-2.0.so.0 => /emul/ia32-linux/usr/lib/libglib-2.0.so.0 (0xf7cc2000)
   libgmodule-2.0.so.0 => /emul/ia32-linux/usr/lib/libgmodule-2.0.so.0 (0xf7cbe000)
   libgobject-2.0.so.0 => /emul/ia32-linux/usr/lib/libgobject-2.0.so.0 (0xf7c81000)
   libatk-1.0.so.0 => /emul/ia32-linux/usr/lib/libatk-1.0.so.0 (0xf7c67000)
   libpango-1.0.so.0 => /emul/ia32-linux/usr/lib/libpango-1.0.so.0 (0xf7c2a000)
   libpangoft2-1.0.so.0 => /emul/ia32-linux/usr/lib/libpangoft2-1.0.so.0 (0xf7c03000)
   libpangoxft-1.0.so.0 => /emul/ia32-linux/usr/lib/libpangoxft-1.0.so.0 (0xf7bfc000)
   libpangox-1.0.so.0 => /emul/ia32-linux/usr/lib/libpangox-1.0.so.0 (0xf7bf0000)
   libgdk-x11-2.0.so.0 => /emul/ia32-linux/usr/lib/libgdk-x11-2.0.so.0 (0xf7b6c000)
   libgdk_pixbuf-2.0.so.0 => /emul/ia32-linux/usr/lib/libgdk_pixbuf-2.0.so.0 (0xf7b54000)
   libgtk-x11-2.0.so.0 => /emul/ia32-linux/usr/lib/libgtk-x11-2.0.so.0 (0xf77dd000)
   libgcc_s.so.1 => /emul/ia32-linux/usr/lib/libgcc_s.so.1 (0xf77d2000)
   libstdc++.so.5 => /emul/ia32-linux/usr/lib/libstdc++.so.5 (0xf7717000)
   libsigc-2.0.so.0 => /emul/ia32-linux/usr/lib/libsigc-2.0.so.0 (0xf7711000)
   libglibmm-2.4.so.1 => not found
   libglibmm_generate_extra_defs-2.4.so.1 => not found
   libatkmm-1.6.so.1 => not found
   libpangomm-1.4.so.1 => not found
   libgdkmm-2.4.so.1 => not found
   libgtkmm-2.4.so.1 => not found
   libart_lgpl_2.so.2 => /emul/ia32-linux/usr/lib/libart_lgpl_2.so.2 (0xf76fa000)
   libxml2.so.2 => /emul/ia32-linux/usr/lib/libxml2.so.2 (0xf75db000)
   libglade-2.0.so.0 => /emul/ia32-linux/usr/lib/libglade-2.0.so.0 (0xf75c2000)
   libgnomecanvas-2.so.0 => /emul/ia32-linux/usr/lib/libgnomecanvas-2.so.0 (0xf7592000)
   libgnomecanvasmm-2.6.so.1 => not found
   librsvg-2.so.2 => /emul/ia32-linux/usr/lib/librsvg-2.so.2 (0xf7561000)
   libview.so.2 => not found
   libsexy.so.1 => not found
   libsexymm.so.1 => not found
   libpthread.so.0 => /lib32/libpthread.so.0 (0xf7548000)
   libz.so.1 => /emul/ia32-linux/usr/lib/libz.so.1 (0xf7533000)
   libc.so.6 => /lib32/libc.so.6 (0xf73e4000)
   /lib/ld-linux.so.2 (0xf7fa5000)
   libxcb-xlib.so.0 => /emul/ia32-linux/usr/lib/libxcb-xlib.so.0 (0xf73e1000)
   libxcb.so.1 => /emul/ia32-linux/usr/lib/libxcb.so.1 (0xf73c9000)
   libXau.so.6 => /emul/ia32-linux/usr/lib/libXau.so.6 (0xf73c6000)
   libpcre.so.3 => /emul/ia32-linux/usr/lib/libpcre.so.3 (0xf739f000)
   libselinux.so.1 => /lib32/libselinux.so.1 (0xf7386000)
   libpangocairo-1.0.so.0 => /emul/ia32-linux/usr/lib/libpangocairo-1.0.so.0 (0xf737c000)
   libcairo.so.2 => /emul/ia32-linux/usr/lib/libcairo.so.2 (0xf731a000)
   libXinerama.so.1 => /emul/ia32-linux/usr/lib/libXinerama.so.1 (0xf7317000)
   libXrandr.so.2 => /emul/ia32-linux/usr/lib/libXrandr.so.2 (0xf7311000)
   libXcursor.so.1 => /emul/ia32-linux/usr/lib/libXcursor.so.1 (0xf7308000)
   libXcomposite.so.1 => /emul/ia32-linux/usr/lib/libXcomposite.so.1 (0xf7304000)
   libXdamage.so.1 => /emul/ia32-linux/usr/lib/libXdamage.so.1 (0xf7301000)
   libXfixes.so.3 => /emul/ia32-linux/usr/lib/libXfixes.so.3 (0xf72fc000)
   libstdc++.so.6 => /emul/ia32-linux/usr/lib/libstdc++.so.6 (0xf7209000)
   libgailutil.so.18 => /emul/ia32-linux/usr/lib/libgailutil.so.18 (0xf7201000)
   libgsf-1.so.114 => /emul/ia32-linux/usr/lib/libgsf-1.so.114 (0xf71cd000)
   libcroco-0.6.so.3 => /emul/ia32-linux/usr/lib/libcroco-0.6.so.3 (0xf7198000)
   libgio-2.0.so.0 => /emul/ia32-linux/usr/lib/libgio-2.0.so.0 (0xf7137000)
   libXdmcp.so.6 => /emul/ia32-linux/usr/lib/libXdmcp.so.6 (0xf7132000)
   libpng12.so.0 => /emul/ia32-linux/usr/lib/libpng12.so.0 (0xf710e000)
   libpixman-1.so.0 => /emul/ia32-linux/usr/lib/libpixman-1.so.0 (0xf70e5000)
   libbz2.so.1.0 => /emul/ia32-linux/usr/lib/libbz2.so.1.0 (0xf70d5000
)
```

These libs are not in the normal ia-32 ubuntu repos for hardy/amd64 as 32bit version:

```
libglibmm-2.4-1c2a libgtkmm-2.4-1c2a  libview2 libsexy2 libsexymm2
```

But they exist in the normal 64bit versions:
```
~$ locate `dpkg -L libglibmm-2.4-1c2a libgtkmm-2.4-1c2a  libview2 libsexy2 libsexymm2|grep .so`
/usr/lib/libatkmm-1.6.so.1
/usr/lib/libatkmm-1.6.so.1.0.30
/usr/lib/libgdkmm-2.4.so.1
/usr/lib/libgdkmm-2.4.so.1.0.30
/usr/lib/libgiomm-2.4.so.1
/usr/lib/libgiomm-2.4.so.1.0.24
/usr/lib/libglibmm-2.4.so.1
/usr/lib/libglibmm-2.4.so.1.0.24
/usr/lib/libglibmm_generate_extra_defs-2.4.so.1
/usr/lib/libglibmm_generate_extra_defs-2.4.so.1.0.24
/usr/lib/libgtkmm-2.4.so.1
/usr/lib/libgtkmm-2.4.so.1.0.30
/usr/lib/libpangomm-1.4.so.1
/usr/lib/libpangomm-1.4.so.1.0.30
/usr/lib/libsexy.so.2
/usr/lib/libsexy.so.2.0.4
/var/chroot/usr/lib/libatkmm-1.6.so.1
/var/chroot/usr/lib/libatkmm-1.6.so.1.0.30
/var/chroot/usr/lib/libgdkmm-2.4.so.1
/var/chroot/usr/lib/libgdkmm-2.4.so.1.0.30
/var/chroot/usr/lib/libglibmm-2.4.so.1
/var/chroot/usr/lib/libglibmm-2.4.so.1.0.24
/var/chroot/usr/lib/libglibmm_generate_extra_defs-2.4.so.1
/var/chroot/usr/lib/libglibmm_generate_extra_defs-2.4.so.1.0.24
/var/chroot/usr/lib/libgtkmm-2.4.so.1
/var/chroot/usr/lib/libgtkmm-2.4.so.1.0.30
/var/chroot/usr/lib/libpangomm-1.4.so.1
/var/chroot/usr/lib/libpangomm-1.4.so.1.0.30

```


This rises the idea, that I could link the libs from an i386 chroot:


I replaced /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0
from /var/chroot/usr/lib/libgtk-x11-2.0.so.0.1200.9 and /var/chroot/usr/lib/libgtk-x11-2.0.so.0 (from: ia32-libs).

I linked some chroot/i386 libs to /usr/lib32/: 

```
sudo ln -s /var/chroot/usr/lib/libatkmm-1.6.so.1 /usr/lib32/libatkmm-1.6.so.1
sudo ln -s /var/chroot/usr/lib/libatkmm-1.6.so.1.0.30 /usr/lib32/libatkmm-1.6.so.1.0.30
sudo ln -s /var/chroot/usr/lib/libgdkmm-2.4.so.1 /usr/lib32/libgdkmm-2.4.so.1
sudo ln -s /var/chroot/usr/lib/libgdkmm-2.4.so.1.0.30 /usr/lib32/libgdkmm-2.4.so.1.0.30
sudo ln -s /var/chroot/usr/lib/libgiomm-2.4.so.1 /usr/lib32/libgiomm-2.4.so.1
sudo ln -s /var/chroot/usr/lib/libgiomm-2.4.so.1.0.24 /usr/lib32/libgiomm-2.4.so.1.0.24
sudo ln -s /var/chroot/usr/lib/libglibmm-2.4.so.1 /usr/lib32/libglibmm-2.4.so.1
sudo ln -s /var/chroot/usr/lib/libglibmm-2.4.so.1.0.24 /usr/lib32/libglibmm-2.4.so.1.0.24
sudo ln -s /var/chroot/usr/lib/libglibmm_generate_extra_defs-2.4.so.1 /usr/lib32/libglibmm_generate_extra_defs-2.4.so.1
sudo ln -s /var/chroot/usr/lib/libglibmm_generate_extra_defs-2.4.so.1.0.24 /usr/lib32/libglibmm_generate_extra_defs-2.4.so.1.0.24
sudo ln -s /var/chroot/usr/lib/libgtkmm-2.4.so.1 /usr/lib32/libgtkmm-2.4.so.1
sudo ln -s /var/chroot/usr/lib/libgtkmm-2.4.so.1.0.30 /usr/lib32/libgtkmm-2.4.so.1.0.30
sudo ln -s /var/chroot/usr/lib/libpangomm-1.4.so.1 /usr/lib32/libpangomm-1.4.so.
sudo ln -s /var/chroot/usr/lib/libpangomm-1.4.so.1.0.30 /usr/lib32/libpangomm-1.4.so.1.0.30
sudo ln -s /var/chroot/usr/lib/libsexy.so.2 /usr/lib32/libsexy.so.2
sudo ln -s /var/chroot/usr/lib/libsexy.so.2.0.4 /usr/lib32/libsexy.so.2.0.4
sudo ln -s /var/chroot/usr/lib/libsexymm.so.2 /usr/lib32/libsexymm.so.2
sudo ln -s /var/chroot/usr/lib/libsexymm.so.2.0.1 /usr/lib32/libsexymm.so.2.0.1
sudo ln -s /var/chroot/usr/lib/libview.so.2 /usr/lib32/libview.so.
sudo ln -s /var/chroot/usr/lib/libview.so.2.1.1 /usr/lib32/libview.so.2.1.1

sudo ln -s /var/chroot/usr/lib/libhal-storage.so.1 /usr/lib32/libhal-storage.so.1
sudo ln -s /var/chroot/usr/lib/libhal-storage.so.1.0.0 /usr/lib32/libhal-storage.so.1.0.0
sudo ln -s /var/chroot/usr/lib/libhal.so.1 /usr/lib32/libhal.so.1
sudo ln -s /var/chroot/usr/lib/libhal.so.1.0.0  /usr/lib32/libhal.so.1.0.0

```
After these actions I get now only this error:
```
/usr/local/lib/vmware/bin/vmware: symbol lookup error: /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref
```

strace
```

[...]
close(4)                                = 0
read(3, "/usr/local/lib/vmware/lib/libgcc"..., 128) = 128
read(3, "/local/lib/vmware/lib/libglibmm-"..., 128) = 128
read(3, "lib/libatkmm-1.6.so.1:/usr/local"..., 128) = 128
read(3, "mware/lib/libgtkmm-2.4.so.1:/usr"..., 128) = 128
read(3, "l/lib/vmware/lib/libsexymm.so.1:"..., 128) = 72
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 20743
fcntl(3, F_DUPFD, 10)                   = -1 EBADF (Bad file descriptor)
dup2(1, 3)                              = 3
pipe([4, 5])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7ffd71852770) = 20751
close(5)                                = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7ffd71852770) = 20752
close(4)                                = 0
close(4294967295)                       = -1 EBADF (Bad file descriptor)
wait4(4294967295, /usr/local/lib/vmware/bin/vmware: symbol lookup error: /usr/local/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref
[{WIFEXITED(s) && WEXITSTATUS(s) == 1}], 0, NULL) = 20752
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 127}], 0, NULL) = 20751
--- SIGCHLD (Child exited) @ 0 (0) ---
fcntl(3, F_DUPFD, 10)                   = 11
close(3)                                = 0
fcntl(11, F_SETFD, FD_CLOEXEC)          = 0
close(11)                               = 0
exit_group(0)                           = ?
Process 20033 detached
```

May I have a similar Problem to this guy, but I'm not able to solve it:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/120618](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/120618)

---

### Post by floogy on 2008-05-31
Please, could someone do the same on his hardy heron/amd64 box, to find out the differences?

```
$ ldd /usr/lib32/libgtk-x11-2.0.so.0
   linux-gate.so.1 =>  (0xffffe000)
   libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf7b28000)
   libgdk-x11-2.0.so.0 (0xf7aa7000)
   libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf7a9e000)
   libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf7a61000)
   libX11.so.6 => /usr/lib32/libX11.so.6 (0xf797a000)
   libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf7977000)
   libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf7973000)
   libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf796e000)
   libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf7954000)
   libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7918000)
   libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7914000)
   libdl.so.2 => /lib32/libdl.so.2 (0xf7910000)
   libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf785e000)
   libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf77fc000)
   libm.so.6 => /lib32/libm.so.6 (0xf77d7000)
   libc.so.6 => /lib32/libc.so.6 (0xf7688000)
   libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf7661000)
   libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf75f0000)
   libz.so.1 => /usr/lib32/libz.so.1 (0xf75db000)
   libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf75b1000)
   libXext.so.6 => /usr/lib32/libXext.so.6 (0xf75a3000)
   libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf759b000)
   libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7598000)
   libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7591000)
   libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf7588000)
   libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf7586000)
   libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf756e000)
   libselinux.so.1 => /lib32/libselinux.so.1 (0xf7555000)
   /lib/ld-linux.so.2 (0xf7eec000)
   libpcre.so.3 => /usr/lib32/libpcre.so.3 (0xf752d000)
   libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf750a000)
   libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf74e1000)
   libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf73ee000)
   libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf73e3000)
   libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf73c1000)
   libXau.so.6 => /usr/lib32/libXau.so.6 (0xf73be000)
   libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf73b9000)
   libpthread.so.0 => /lib32/libpthread.so.0 (0xf73a1000)
```

Maybe I can find the older lib that might be responsible for the problem, if someone compare these libs:
```

$ sudo updatedb
$ md5sum $(locate `ldd /usr/lib32/libgtk-x11-2.0.so.0|awk '{print $1}'`|grep /emul/ia32-linux)
547e9b94a8dbcec03ef0cf0597db7f65  /emul/ia32-linux/usr/lib/libX11.so.6
547e9b94a8dbcec03ef0cf0597db7f65  /emul/ia32-linux/usr/lib/libX11.so.6.2.0
07ac021b6a7c1f9f203a1c2a396aef84  /emul/ia32-linux/usr/lib/libXau.so.6
07ac021b6a7c1f9f203a1c2a396aef84  /emul/ia32-linux/usr/lib/libXau.so.6.0.0
4c0f8a14c5c15e19a19cf534354a3979  /emul/ia32-linux/usr/lib/libXcomposite.so.1
4c0f8a14c5c15e19a19cf534354a3979  /emul/ia32-linux/usr/lib/libXcomposite.so.1.0.0
caf8a0fa5dd90866674d64db512c67f2  /emul/ia32-linux/usr/lib/libXcursor.so.1
caf8a0fa5dd90866674d64db512c67f2  /emul/ia32-linux/usr/lib/libXcursor.so.1.0.2
dd25a9bb8a426cd8d147419fa5feff8f  /emul/ia32-linux/usr/lib/libXdamage.so.1
dd25a9bb8a426cd8d147419fa5feff8f  /emul/ia32-linux/usr/lib/libXdamage.so.1.1.0
7058d789a597e640564d4eb793d340ea  /emul/ia32-linux/usr/lib/libXdmcp.so.6
7058d789a597e640564d4eb793d340ea  /emul/ia32-linux/usr/lib/libXdmcp.so.6.0.0
3d56ad8d291c8abab4131013cb85e8e2  /emul/ia32-linux/usr/lib/libXext.so.6
3d56ad8d291c8abab4131013cb85e8e2  /emul/ia32-linux/usr/lib/libXext.so.6.4.0
a1ad155beb445f8e493deae501fbf523  /emul/ia32-linux/usr/lib/libXfixes.so.3
a1ad155beb445f8e493deae501fbf523  /emul/ia32-linux/usr/lib/libXfixes.so.3.1.0
77dfc30c59dce459ff86c83e3ec3be9c  /emul/ia32-linux/usr/lib/libXinerama.so.1
77dfc30c59dce459ff86c83e3ec3be9c  /emul/ia32-linux/usr/lib/libXinerama.so.1.0.0
ef1ef166a2a1190610f89ae3f60f0d82  /emul/ia32-linux/usr/lib/libXrandr.so.2
ef1ef166a2a1190610f89ae3f60f0d82  /emul/ia32-linux/usr/lib/libXrandr.so.2.1.0
8dd039bb40625047fc35db8f37bbadf2  /emul/ia32-linux/usr/lib/libXrender.so.1
8dd039bb40625047fc35db8f37bbadf2  /emul/ia32-linux/usr/lib/libXrender.so.1.3.0
8fd00a236ce0f87e8b20a65057f582a8  /emul/ia32-linux/usr/lib/libatk-1.0.so.0
8fd00a236ce0f87e8b20a65057f582a8  /emul/ia32-linux/usr/lib/libatk-1.0.so.0.2209.1
c3ea505211cb54aac607ceb4631b0365  /emul/ia32-linux/usr/lib/libcairo.so.2
c3ea505211cb54aac607ceb4631b0365  /emul/ia32-linux/usr/lib/libcairo.so.2.17.3
5439502f8da048ae9fd8bff2c13d9d95  /emul/ia32-linux/usr/lib/libexpat.so.1
5439502f8da048ae9fd8bff2c13d9d95  /emul/ia32-linux/usr/lib/libexpat.so.1.5.2
585625b6700b05c5e4017590dc49ba09  /emul/ia32-linux/usr/lib/libfontconfig.so.1
585625b6700b05c5e4017590dc49ba09  /emul/ia32-linux/usr/lib/libfontconfig.so.1.3.0
a4d063ff81b16554d1dd6cea05d8386d  /emul/ia32-linux/usr/lib/libfreetype.so.6
a4d063ff81b16554d1dd6cea05d8386d  /emul/ia32-linux/usr/lib/libfreetype.so.6.3.16
47884c1645daf2960e5642483aca25a3  /emul/ia32-linux/usr/lib/libgcc_s.so.1
8a50e5cd6549f1936ea9df59a243cf79  /emul/ia32-linux/usr/lib/libgdk-x11-2.0.so.0
8a50e5cd6549f1936ea9df59a243cf79  /emul/ia32-linux/usr/lib/libgdk-x11-2.0.so.0.1200.9
939b3d19b4396e32a0efe132a2e56904  /emul/ia32-linux/usr/lib/libgdk_pixbuf-2.0.so.0
939b3d19b4396e32a0efe132a2e56904  /emul/ia32-linux/usr/lib/libgdk_pixbuf-2.0.so.0.1200.9
58b58a23c8ae567a800d92c207749b69  /emul/ia32-linux/usr/lib/libglib-2.0.so.0
58b58a23c8ae567a800d92c207749b69  /emul/ia32-linux/usr/lib/libglib-2.0.so.0.1600.3
d997e9182cd80ba195909447b6bc72e5  /emul/ia32-linux/usr/lib/libgmodule-2.0.so.0
d997e9182cd80ba195909447b6bc72e5  /emul/ia32-linux/usr/lib/libgmodule-2.0.so.0.1600.3
ddfcb33db7c1c75607094b368603b6d3  /emul/ia32-linux/usr/lib/libgobject-2.0.so.0
ddfcb33db7c1c75607094b368603b6d3  /emul/ia32-linux/usr/lib/libgobject-2.0.so.0.1600.3
a38202bababe75c95edb8402e0e5e4cb  /emul/ia32-linux/usr/lib/libpango-1.0.so.0
a38202bababe75c95edb8402e0e5e4cb  /emul/ia32-linux/usr/lib/libpango-1.0.so.0.2000.1
cebf7b7b8e63036d7e8ff5483505d5d5  /emul/ia32-linux/usr/lib/libpangocairo-1.0.so.0
cebf7b7b8e63036d7e8ff5483505d5d5  /emul/ia32-linux/usr/lib/libpangocairo-1.0.so.0.2000.1
3d83608bef26e4ac3cf038cd3a29b69f  /emul/ia32-linux/usr/lib/libpangoft2-1.0.so.0
3d83608bef26e4ac3cf038cd3a29b69f  /emul/ia32-linux/usr/lib/libpangoft2-1.0.so.0.2000.1
e024901dbb8b7ab1459d443dff47371a  /emul/ia32-linux/usr/lib/libpcre.so.3
e024901dbb8b7ab1459d443dff47371a  /emul/ia32-linux/usr/lib/libpcre.so.3.12.1
54748779d519c5c15f479649f4577031  /emul/ia32-linux/usr/lib/libpixman-1.so.0
54748779d519c5c15f479649f4577031  /emul/ia32-linux/usr/lib/libpixman-1.so.0.10.0
32cb2b7252b5f458cd552abdbcca1f45  /emul/ia32-linux/usr/lib/libpng12.so.0
32cb2b7252b5f458cd552abdbcca1f45  /emul/ia32-linux/usr/lib/libpng12.so.0.15.0
da0a9d2a546d49e9bf72864f88fcdae2  /emul/ia32-linux/usr/lib/libstdc++.so.6
da0a9d2a546d49e9bf72864f88fcdae2  /emul/ia32-linux/usr/lib/libstdc++.so.6.0.9
51043b04aaeefb79dd5edc10d0c70054  /emul/ia32-linux/usr/lib/libxcb-xlib.so.0
51043b04aaeefb79dd5edc10d0c70054  /emul/ia32-linux/usr/lib/libxcb-xlib.so.0.0.0
309ee9a121fe1c4be2c5c1b48ab3fd92  /emul/ia32-linux/usr/lib/libxcb.so.1
309ee9a121fe1c4be2c5c1b48ab3fd92  /emul/ia32-linux/usr/lib/libxcb.so.1.0.0
18b183976d20925da91c3c40e0d0a35b  /emul/ia32-linux/usr/lib/libz.so.1
18b183976d20925da91c3c40e0d0a35b  /emul/ia32-linux/usr/lib/libz.so.1.2.3.3

```


These libs are older then the dist-upgrade to hardy date:
```
ls -l /emul/ia32-linux/usr/lib/libpcre.so.3.12.1
-rw-r--r-- 1 root root 157240 2008-02-23 03:23 /emul/ia32-linux/usr/lib/libpcre.so.3.12.1
 ls -l /emul/ia32-linux/usr/lib/libgcc_s.so.1
-rw-r--r-- 1 root root 42700 2008-04-01 21:49 /emul/ia32-linux/usr/lib/libgcc_s.so.1
 ls -l /emul/ia32-linux/usr/lib/libfontconfig.so.1.3.0
-rw-r--r-- 1 root root 172592 2008-02-28 18:22 /emul/ia32-linux/usr/lib/libfontconfig.so.1.3.0
ls -l /emul/ia32-linux/usr/lib/libexpat.so.1.5.2
-rw-r--r-- 1 root root 131652 2007-12-05 18:51 /emul/ia32-linux/usr/lib/libexpat.so.1.5.2
 ls -l /emul/ia32-linux/usr/lib/libXrender.so.1.3.0
-rw-r--r-- 1 root root 30544 2007-10-24 10:31 /emul/ia32-linux/usr/lib/libXrender.so.1.3.0
ls -l /emul/ia32-linux/usr/lib/libXinerama.so.1.0.0
-rw-r--r-- 1 root root 6464 2007-07-25 10:01 /emul/ia32-linux/usr/lib/libXinerama.so.1.0.0
ls -l /emul/ia32-linux/usr/lib/libXfixes.so.3.1.0
-rw-r--r-- 1 root root 14128 2007-04-27 17:59 /emul/ia32-linux/usr/lib/libXfixes.so.3.1.0
ls -l /emul/ia32-linux/usr/lib/libXext.so.6.4.0
-rw-r--r-- 1 root root 56156 2007-07-24 10:00 /emul/ia32-linux/usr/lib/libXext.so.6.4.0
 ls -l /emul/ia32-linux/usr/lib/libXdmcp.so.6.0.0
-rw-r--r-- 1 root root 16616 2007-04-27 18:01 /emul/ia32-linux/usr/lib/libXdmcp.so.6.0.0
 ls -l /emul/ia32-linux/usr/lib/libXdamage.so.1.1.0
-rw-r--r-- 1 root root 5992 2007-04-27 18:01 /emul/ia32-linux/usr/lib/libXdamage.so.1.1.0
ls -l /emul/ia32-linux/usr/lib/libXcursor.so.1.0.2
-rw-r--r-- 1 root root 33152 2007-10-24 09:39 /emul/ia32-linux/usr/lib/libXcursor.so.1.0.2
ls -l /emul/ia32-linux/usr/lib/libXau.so.6.0.0
-rw-r--r-- 1 root root 6988 2007-04-27 18:03 /emul/ia32-linux/usr/lib/libXau.so.6.0.0
 ls -l /emul/ia32-linux/usr/lib/libX11.so.6.2.0
-rw-r--r-- 1 root root 944876 2008-03-11 21:33 /emul/ia32-linux/usr/lib/libX11.so.6.2.0
```

---

### Post by PingerS on 2008-06-30
Is this what you're after? Having the same trouble - still.

```
$ ldd /usr/lib64/libgtk-x11-2.0.so.0
/usr/lib64/libgtk-x11-2.0.so.0:
	linux-vdso.so.1 =>  (0x00007fff445fe000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f543bccf000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f543ba35000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f543b829000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f543b5e5000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f543b2e2000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f543b0df000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f543aedd000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f543acd8000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f543aab7000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f543a872000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f543a66f000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f543a46a000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f543a1aa000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f5439f3f000)
	libm.so.6 => /lib/libm.so.6 (0x00007f5439cbd000)
	libc.so.6 => /lib/libc.so.6 (0x00007f543995b000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f543972a000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f5439518000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f543930f000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f543910d000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f5438f03000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f5438cfc000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f5438af2000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f54388c5000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f5438646000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f543842f000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f543822d000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f5438012000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007f5437df6000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f543c4d4000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007f5437bcf000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f54379aa000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f543777c000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f5437470000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f5437262000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f543703e000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f5436e3b000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f5436c36000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f5436a19000)
```

---

### Post by Tristan_F on 2008-07-30
I had also the locking assertion failure related to libX problem. I solve it by finding and old version of the library and made a workaround to trick VMWare to use this library. I explain it more [here]("http://tristan.ferroir.free.fr/index.php/2008/07/30/vmware-in-ubuntu-804-and-the-locking-assertion-failure-problem/").

Briefly you have to find an old version of the library and put it into a directory called libX11.so.6 in your VMWare installation and it works afterwards. Hope this helps

---

### Post by gtdaqua on 2008-07-30
I have not experienced lock assertion errors after upgrading to the latest kernel (not referring a 64bit VMware Console though)

See if this helps: 

Lock assertion failure on a 64bit Hardy - VMware Server Console
```

sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server-console /lib/libpng12.so.0/
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware-server-console/lib/libgcc_s.so.1

```

Something similar applies to 64bit Hardy:
```

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

```

---

