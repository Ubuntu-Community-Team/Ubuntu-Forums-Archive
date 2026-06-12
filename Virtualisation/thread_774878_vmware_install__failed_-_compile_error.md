---
title: "vmware install  failed - compile error"
date: 2008-04-29
forum: Virtualisation
---

### Post by aroddo on 2008-04-29
I downloaded and extracted VMware-server-1.0.5-80187.tar.gz and installed all necessery packages ([http://ubuntuforums.org/showthread.php?t=770873&highlight=vmware+install](http://ubuntuforums.org/showthread.php?t=770873&highlight=vmware+install))


I entered the directory and launched the installer script.
```

sudo ./vmware-install.pl -d

```

It runs through all the questions but stops at compiling

```
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:159: Fehler: Redefinition des typedef »uintptr_t«
include/linux/types.h:40: Fehler: Vorherige Deklaration von »uintptr_t« war hier
In Datei, eingefügt von /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 von /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: Warnung: »VMW_HAVE_EPOLL« ist nicht definiert
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: Warnung: »VMW_HAVE_EPOLL« ist nicht definiert
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: Fehler: In Konflikt stehende Typen für »poll_initwait«
include/linux/poll.h:65: Fehler: Vorherige Deklaration von »poll_initwait« war hier
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: Warnung: Initialisierung von inkompatiblem Zeigertyp
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: Warnung: Initialisierung von inkompatiblem Zeigertyp
/tmp/vmware-config1/vmmon-only/linux/driver.c: In Funktion »LinuxDriver_Ioctl«:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: Fehler: »struct mm_struct« hat kein Element namens »dumpable«
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Fehler 2
make: Verlasse Verzeichnis '/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

so, what do I do now ?

cheers!

---

### Post by plazo on 2008-04-30
Hi aroddo,

You won'y be able to install vmware on a 2.6.24 kernel without the "vmware-any-any" patch

Download it here 
[http://taltan2.free.fr/dl/vmware/vmware-any-any-update-116.tgz]("http://taltan2.free.fr/dl/vmware/vmware-any-any-update-116.tgz")

You have to first install vmare. You will have an error when you will try to invoke vmware-config

So untar the patch "tar xf vmware-any-any-update-116.tgz"
"cd" inside the directory and run "./runme.pl"
And you'll get a fully working vmware ;-)

Bye

---

### Post by aroddo on 2008-04-30
Thanks, I just found the other thread with a guide saying exactly the same.

But after doing so i get this when starting vmware in a console:

> 
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/console.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/upgrade-hw.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/pvn.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-not.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-new.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-add.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-remove.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-broken.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-new.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-suspended.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-broken.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-broken.png« konnte nicht erkannt werden
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf703b767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf703b8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7eba1bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7daa969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7daaf4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf0180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf0d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc0c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bcd24f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc0c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bccb34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad1298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad1586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad377e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ce6459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cce3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cce076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ce56eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7ce4d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7ce50b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf703b767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf703b81e]
#2 /usr/lib32/libX11.so.6 [0xf7eb9518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e9cc9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7da2ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7da18b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7da1d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7da1ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bee9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf0d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc0c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bcd24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc0c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bccb34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad1298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad1586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad377e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ce6459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cce3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cce076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.


Following that I uninstalled it with sudo /usr/bin/vmware-uninstall.pl .
Tried it again without success. 

Thats a bit weird because i got it running once earlier ... but no such luck now...

---

