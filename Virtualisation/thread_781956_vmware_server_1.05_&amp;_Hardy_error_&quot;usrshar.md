---
title: "vmware server 1.05 &amp; Hardy error: &quot;/usr/share/themes/Clearlooks...&quot;"
date: 2008-05-04
forum: Virtualisation
---

### Post by stell86 on 2008-05-04
VMware-server installed according to guides:
 (sticky)[COLOR="Blue"]**[How to VMWare in Ubuntu 8.04]("http://ubuntuforums.org/showthread.php?t=779934")**[/COLOR], and
[COLOR="Blue"]"vmware-server in hardy"[/COLOR] **[COLOR="Blue"][here]("http://ubuntuforums.org/showpost.php?p=4806567#8")[/COLOR]** and **[COLOR="Blue"][here]("http://ubuntuforums.org/showthread.php?t=613976#10")[/COLOR]**.

I still get the same error as **[COLOR="Blue"][here (second frame)]("http://ubuntuforums.org/showpost.php?p=4818385&postcount=11")[/COLOR]**, **[COLOR="Blue"][here (middle of second frame)]("http://ubuntuforums.org/showpost.php?p=4862887&postcount=46")[/COLOR]**, **[COLOR="Blue"][here]("http://ubuntuforums.org/showpost.php?p=4824683&postcount=1")[/COLOR]**,**[COLOR="Blue"][here]("http://ubuntuforums.org/showpost.php?p=4853343&postcount=1")[/COLOR]**.  :(

I've upgraded from 7.10 to 8.04.  I normally use the 'Clearlooks' theme, but have since tried all available themes - the error stays the same.  Does the install take cognizance of the 'theme' used during the install process (specifically when compiling)?
How do I get back to the 'default' Ubuntu-theme, as suggested **[COLOR="Blue"][here]("http://ubuntuforums.org/showpost.php?p=4834576&postcount=28")[/COLOR]**?.

The only way to run vmware-server is by 'sudo' (see **[COLOR="Blue"][here]("http://ubuntuforums.org/showpost.php?p=4853343&postcount=1")[/COLOR]**.
'chown'-ing the "~/.vmware"-folder does not help (**[COLOR="Blue"][as suggested here by Kokopelli]("http://ubuntuforums.org/showpost.php?p=4860757&postcount=2")[/COLOR]**)

I've decided to create a new thread for this error only as this gets caught up in other threads, but never really addressed.  This may be usefull in the sticky **[COLOR="Blue"][How to VMWare in Ubuntu 8.04]("http://ubuntuforums.org/showthread.php?t=779934")[/COLOR]** once it's solved as it seems I'n not the only one struggling with this...

Here is my version of the error:> $ vmware
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:41: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6fd2767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6fd28b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e511bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d41969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d41f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b87180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b87d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b57c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b6424f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b57c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b63b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a68298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a68586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6a77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c7d459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c653a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c65076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c7c6eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c7bd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c7c0b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6fd2767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6fd281e]
#2 /usr/lib32/libX11.so.6 [0xf7e50518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e33c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d39ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d388b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d38d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d38ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b859b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b87d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b57c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b6424f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b57c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b63b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a68298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a68586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a6a77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c7d459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c653a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c65076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.


---

### Post by mogydy on 2008-05-05
Hi, I have exactly the same error on Hardy 64Bit. 

I have tried modifying my gtkrc file and replace all variables (@bg_colour for example) with a fixed value ('#000') and that seems to work (it fails on the next line) but man it is so much work changing it, i have also screwed up my clearlooks theme by changing it, luckily i have made a copy of my gtkrc file.
I will let you know if i get it to work.

---

### Post by baronKarza on 2008-05-05
Same problem. I upgraded from 7.10.
I added libsexy2, libview2 and others since ldd /usr/lib/vmware/bin/vmware said "not found" (also created new links because required names differ).
An ```
ldd -r /usr/lib/vmware/bin/vmware
``` says:

```
	linux-gate.so.1 =>  (0xb7f5b000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f42000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f1d000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e35000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e27000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb7e1f000)
	libexpat.so.0 => /usr/lib/libexpat.so.0 (0xb7dfe000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7dd4000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7d64000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7d5b000)
	libXft.so.2 => /usr/lib/libXft.so.2 (0xb7d49000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7c98000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7c94000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7c58000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7c3e000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7c00000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb7bd9000)
	libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb7bd2000)
	libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb7bc7000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7b43000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7b2a000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb77b3000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb77a8000)
	libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb76ee000)
	libsigc-2.0.so.0 => /usr/lib/libsigc-2.0.so.0 (0xb76e8000)
	libglibmm-2.4.so.1 => /usr/lib/libglibmm-2.4.so.1 (0xb768e000)
	libglibmm_generate_extra_defs-2.4.so.1 => /usr/lib/libglibmm_generate_extra_defs-2.4.so.1 (0xb7687000)
	libatkmm-1.6.so.1 => /usr/lib/libatkmm-1.6.so.1 (0xb7642000)
	libpangomm-1.4.so.1 => /usr/lib/libpangomm-1.4.so.1 (0xb7614000)
	libgdkmm-2.4.so.1 => /usr/lib/libgdkmm-2.4.so.1 (0xb75ca000)
	libgtkmm-2.4.so.1 => /usr/lib/libgtkmm-2.4.so.1 (0xb7289000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7272000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7153000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb713b000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb710b000)
	libgnomecanvasmm-2.6.so.1 => /usr/lib/libgnomecanvasmm-2.6.so.1 (0xb70c5000)
	librsvg-2.so.2 => /usr/lib/librsvg-2.so.2 (0xb7093000)
	libview.so.2 => /usr/lib/libview.so.2 (0xb703a000)
	libsexy.so.1 => /usr/lib/libsexy.so.1 (0xb702b000)
	libsexymm.so.1 => /usr/lib/libsexymm.so.1 (0xb7013000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb6ffb000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6fe6000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6e97000)
	/lib/ld-linux.so.2 (0xb7f5c000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6e94000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6e7c000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6e79000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6e52000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6e39000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6e2f000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb6dcd000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6dca000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6dc4000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6dbb000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6db7000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6db4000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb6daf000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb6cbc000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb6c5b000)
	libcairomm-1.0.so.1 => /usr/lib/libcairomm-1.0.so.1 (0xb6c40000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0xb6c39000)
	libgsf-1.so.114 => /usr/lib/libgsf-1.so.114 (0xb6c05000)
	libcroco-0.6.so.3 => /usr/lib/libcroco-0.6.so.3 (0xb6bd0000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6bca000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6ba7000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb6b7e000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb6b6d000)
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN3Gtk4MainE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN4Glib9InterfaceE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN3Gtk9TreeStoreE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN4Glib10ObjectBaseE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN3Gtk5EntryE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN3Gtk8ComboBoxE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN4Glib6ObjectE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN3Gtk17FileChooserDialogE' has different size in shared object, consider re-linking
/usr/lib/vmware/bin/vmware: Symbol `_ZTIN3Gtk6WidgetE' has different size in shared object, consider re-linking
undefined symbol: _ZN4sigc8internal11signal_impl5eraseESt14_List_iteratorINS_9slot_baseERS3_PS3_E	(/usr/lib/vmware/bin/vmware)

```

I'm still stuck: any idea? thx in advance

---

### Post by baronKarza on 2008-05-13
Finally, I solved by formatting and reinstalling Ubuntu 8.04.
Half an hour and... everything runs perfectly.
It's stupid but it works.

---

### Post by stell86 on 2008-05-15
> **baronKarza said:**
> Finally, I solved by formatting and reinstalling Ubuntu 8.04.
Half an hour and... everything runs perfectly.
It's stupid but it works.
@ baronKarza:
 - did you have your '/home' on a separate partition from '/'

@ anybody:
Is there a way to make a list of all the non-standard apps installed, so that when the new install is finished, I can just type: "now load my other prgms as well" :)
I have a number of items from non-standard repositories, mostly 'medibuntu'-stuff, that I don't want to remember what I have.... ?

Edit: So far I'm running 'vmware' as sudo and it works fine - so our errors must be a permissions issue somewhere.....

---

### Post by haenschen_klein on 2009-02-09
I've got the same Error with vmware server 1.08, installed on an debian 64 Bit lenny system. After installing the package ia32-libs-gtk (may have an other Name for Ubuntu...) everything works fine. Looks like vmware uses it's own Version of libgtk-x11...(or an other lib in that package) if it is missing on your System, and obviously that doesn't work. Hope that helps

---

