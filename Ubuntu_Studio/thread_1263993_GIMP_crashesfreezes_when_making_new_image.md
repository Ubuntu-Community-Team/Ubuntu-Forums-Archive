---
title: "GIMP crashes/freezes when making new image"
date: 2009-09-11
forum: Ubuntu Studio
---

### Post by Izobalax on 2009-09-11
This problem has only just started. 

When I want to make a new image, the dialogue for my new image settings pops up completely blank and GIMP freezes. Sometimes GIMP even crashes with this.

Running GIMP in a terminal I get either:

```
(script-fu:4810): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault
```
```
(script-fu:4782): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault
```

These are both crashes. This is what I get when it freezes:

```
*** glibc detected *** gimp: free(): invalid size: 0x0af2ed60 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7414604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb74165b6]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7563126]
/usr/lib/gtk-2.0/2.10.0/engines/libcandido.so(option_menu_get_props+0xa9)[0xb6e02689]
/usr/lib/gtk-2.0/2.10.0/engines/libcandido.so[0xb6e00928]
/usr/lib/libgtk-x11-2.0.so.0(gtk_paint_box+0xee)[0xb7b6eece]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c723fd]
/usr/lib/libgtk-x11-2.0.so.0[0xb7af3526]
/usr/lib/libgobject-2.0.so.0[0xb75e23d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb75e3ba8]
/usr/lib/libgobject-2.0.so.0[0xb75f9aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb75fb34f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb75fb936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c0e2ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3)[0xb7a63763]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a63791]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b7b059]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96)[0xb7a64336]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a65a70]
/usr/lib/libgtk-x11-2.0.so.0[0xb7af3526]
/usr/lib/libgobject-2.0.so.0[0xb75e23d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb75e3ba8]
/usr/lib/libgobject-2.0.so.0[0xb75f9aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb75fb34f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb75fb936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c0e2ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3)[0xb7a63763]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a63791]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a30976]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96)[0xb7a64336]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a65a70]
/usr/lib/libgtk-x11-2.0.so.0[0xb7af3526]
/usr/lib/libgobject-2.0.so.0[0xb75e23d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb75e3ba8]
/usr/lib/libgobject-2.0.so.0[0xb75f9aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb75fb34f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb75fb936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c0e2ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3)[0xb7a63763]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a63791]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b7b059]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96)[0xb7a64336]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a65a70]
/usr/lib/libgtk-x11-2.0.so.0[0xb7af3526]
/usr/lib/libgobject-2.0.so.0[0xb75e23d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb75e3ba8]
/usr/lib/libgobject-2.0.so.0[0xb75f9aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb75fb34f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb75fb936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c0e2ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3)[0xb7a63763]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a63791]
/usr/lib/libgtk-x11-2.0.so.0[0xb7aae503]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96)[0xb7a64336]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a65a70]
/usr/lib/libgimpwidgets-2.0.so.0[0xb7de2e88]
/usr/lib/libgtk-x11-2.0.so.0[0xb7af3526]
/usr/lib/libgobject-2.0.so.0[0xb75e23d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8)[0xb75e3ba8]
/usr/lib/libgobject-2.0.so.0[0xb75f9aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb75fb34f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb75fb936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c0e2ae]
======= Memory map: ========
08048000-0845e000 r-xp 00000000 08:11 11599894   /usr/bin/gimp-2.6
0845e000-0845f000 r--p 00416000 08:11 11599894   /usr/bin/gimp-2.6
0845f000-08473000 rw-p 00417000 08:11 11599894   /usr/bin/gimp-2.6
08473000-0849e000 rw-p 08473000 00:00 0 
09f8e000-0b0cb000 rw-p 09f8e000 00:00 0          [heap]
b3af1000-b3afe000 r-xp 00000000 08:11 1269825    /lib/libgcc_s.so.1
b3afe000-b3aff000 r--p 0000c000 08:11 1269825    /lib/libgcc_s.so.1
b3aff000-b3b00000 rw-p 0000d000 08:11 1269825    /lib/libgcc_s.so.1
b3b00000-b3b21000 rw-p b3b00000 00:00 0 
b3b21000-b3c00000 ---p b3b21000 00:00 0 
b3c1f000-b3cb2000 rw-p b3c1f000 00:00 0 
b3cb2000-b3d4a000 r--p 00000000 08:11 11733120   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3d4a000-b3e7f000 r-xp 00000000 08:11 11600715   /usr/lib/libxml2.so.2.6.32
b3e7f000-b3e80000 ---p 00135000 08:11 11600715   /usr/lib/libxml2.so.2.6.32
b3e80000-b3e84000 r--p 00135000 08:11 11600715   /usr/lib/libxml2.so.2.6.32
b3e84000-b3e85000 rw-p 00139000 08:11 11600715   /usr/lib/libxml2.so.2.6.32
b3e85000-b3e86000 rw-p b3e85000 00:00 0 
b3e86000-b3eb7000 r-xp 00000000 08:11 11601619   /usr/lib/libcroco-0.6.so.3.0.1
b3eb7000-b3eba000 rw-p 00030000 08:11 11601619   /usr/lib/libcroco-0.6.so.3.0.1
b3eba000-b3eed000 r-xp 00000000 08:11 11601896   /usr/lib/libgsf-1.so.114.0.11
b3eed000-b3eee000 ---p 00033000 08:11 11601896   /usr/lib/libgsf-1.so.114.0.11
b3eee000-b3ef0000 r--p 00033000 08:11 11601896   /usr/lib/libgsf-1.so.114.0.11
b3ef0000-b3ef1000 rw-p 00035000 08:11 11601896   /usr/lib/libgsf-1.so.114.0.11
b3ef1000-b3ef2000 rw-p b3ef1000 00:00 0 
b3ef2000-b3f23000 r-xp 00000000 08:11 11602274   /usr/lib/librsvg-2.so.2.26.0
b3f23000-b3f24000 r--p 00031000 08:11 11602274   /usr/lib/librsvg-2.so.2.26.0
b3f24000-b3f25000 rw-p 00032000 08:11 11602274   /usr/lib/librsvg-2.so.2.26.0
b3f25000-b3f86000 rw-p b3f25000 00:00 0 
b3f86000-b3f9e000 r--s 00000000 08:11 11682881   /usr/share/mime/mime.cache
b3f9e000-b3fce000 r-xp 00000000 08:11 11602063   /usr/lib/liblcms.so.1.0.18
b3fce000-b3fcf000 r--p 00030000 08:11 11602063   /usr/lib/liblcms.so.1.0.18
b3fcf000-b3fd0000 rw-p 00031000 08:11 11602063   /usr/lib/liblcms.so.1.0.18
b3fd0000-b4009000 rw-p b3fd0000 00:00 0 
b4009000-b44ab000 r--p 00000000 08:11 11815184   /usr/share/icons/hicolor/icon-theme.cache
b44ab000-b494d000 r--p 00000000 08:11 11815184   /usr/share/icons/hicolor/icon-theme.cache
b494d000-b5001000 r--p 00000000 08:11 11815157   /usr/share/icons/gnome/icon-theme.cache
b5001000-b56b5000 r--p 00000000 08:11 11815157   /usr/share/icons/gnome/icon-theme.cache
b56b5000-b56be000 rw-p b56b5000 00:00 0 
b56ca000-b56e2000 r--s 00000000 08:11 11682881   /usr/share/mime/mime.cache
b56e2000-b571c000 rw-p b56e2000 00:00 0 
b5727000-b5736000 r-xp 00000000 08:11 1269802    /lib/libbz2.so.1.0.4
b5736000-b5737000 r--p 0000f000 08:11 1269802    /lib/libbz2.so.1.0.4
b5737000-b5738000 rw-p 00010000 08:11 1269802    /lib/libbz2.so.1.0.4
b5742000-b5748000 rw-p b5742000 00:00 0 
b5748000-b574d000 rw-p b574b000 00:00 0 
b574d000-b575a000 rw-p b574d000 00:00 0 
b575b000-b575d000 rw-p b575b000 00:00 0 
b575d000-b575e000 r-xp 00000000 08:11 11633088   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b575e000-b575f000 r--p 00000000 08:11 11633088   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b575f000-b5760000 rw-p 00001000 08:11 11633088   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5760000-b5765000 rw-p b5760000 00:00 0 
b5765000-b5768000 r-xp 00000000 08:11 11635003   /usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so
b5768000-b5769000 r--p 00002000 08:11 11635003   /usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so
b5769000-b576a000 rw-p 00003000 08:11 11635003   /usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so
b576a000-b5773000 rw-p b576a000 00:00 0 
b5773000-b57c2000 r--p 00000000 08:11 11733122   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b57c2000-b57d4000 r-xp 00000000 08:11 11601243   /usr/lib/libgvfscommon.so.0.0.0
b57d4000-b57d5000 r--p 00012000 08:11 11601243   /usr/lib/libgvfscommon.so.0.0.0
b57d5000-b57d6000 rw-p 00013000 08:11 11601243   /usr/lib/libgvfscommon.so.0.0.0
b57d6000-b57da000 rw-p b57d6000 00:00 0 
b57da000-b57e9000 r-xp 00000000 08:11 11633121   /usr/lib/gio/modules/libgioremote-volume-monitor.so
b57e9000-b57ea000 r--p 0000e000 08:11 11633121   /usr/lib/gio/modules/libgioremote-volume-monitor.so
b57ea000-b57eb000 rw-p 0000f000 08:11 11633121   /usr/lib/gio/modules/libgioremote-volume-monitor.so
b57eb000-b5805000 r-xp 00000000 08:11 11633122   /usr/lib/gio/modules/libgvfsdbus.so
b5805000-b5806000 r--p 00019000 08:11 11633122   /usr/lib/gio/modules/libgvfsdbus.so
b5806000-b5807000 rw-p 0001a000 08:11 11633122   /usr/lib/gio/modules/libgvfsdbus.so
b5807000-b58dc000 rw-p b5807000 00:00 0 
b58dc000-b593c000 rw-s 00000000 00:09 1900555    /SYSV00000000 (deleted)
b593c000-b599c000 rw-s 00000000 00:09 1867786    /SYSV00000000 (deleted)
b599c000-b599e000 r-xp 00000000 08:11 11666563   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b599e000-b599f000 r--p 00001000 08:11 11666563   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b599f000-b59a0000 rw-p 00002000 08:11 11666563   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b59a0000-b59a3000 r--p 00000000 08:11 1868311    /home/hex/.fonts/nu.pcf
b59a3000-b59a9000 r--s 00000000 08:11 4932133    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b59a9000-b59ac000 r--s 00000000 08:11 4932173    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b59ac000-b59af000 r--s 00000000 08:11 4932167    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b59af000-b59b2000 r--s 00000000 08:11 4932166    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b59b2000-b59b3000 r--s 00000000 08:11 4932163    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b59b3000-b59b6000 r--s 00000000 08:11 4932158    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b59b6000-b59b7000 r--s 00000000 08:11 4932156    /var/cache/fontconfig/7ee55724f82591cb35c3d9771e9e69ed-x86.cache-2
b59b7000-b59bb000 r--s 00000000 08:11 4932153    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-x86.cache-2
b59bb000-b59be000 r--s 00000000 08:11 4932152    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b59be000-b59c1000 r--s 00000000 08:11 4932150    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b59c1000-b59c9000 r--s 00000000 08:11 4932148    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b59c9000-b59d4000 r--s 00000000 08:11 4932147    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b59d4000-b59d6000 r--s 00000000 08:11 4932144    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b59d6000-b59d7000 r--s 00000000 08:11 4932143    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b59d7000-b59f9000 r--s 00000000 08:11 4932142    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b59f9000-b59fb000 r--s 00000000 08:11 4932141    /var/cache/fontconfig/27976ef10b7e11dd553c8e28ee05c29a-x86.cache-2
b59gimp: terminated: Aborted
```

Please help me.

/izo\

---

### Post by jerrrys on 2009-09-13
there seems to be a bug going around; could this be it?

[http://www.google.com/search?q=LibGimpBase-WARNING+**%3A+script-fu%3A+gimp_wire_read()%3A+error+Segmentation+fault&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=LibGimpBase-WARNING+**%3A+script-fu%3A+gimp_wire_read()%3A+error+Segmentation+fault&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Izobalax on 2009-09-13
> **jerrrys said:**
> there seems to be a bug going around; could this be it?

[http://www.google.com/search?q=LibGimpBase-WARNING+**%3A+script-fu%3A+gimp_wire_read()%3A+error+Segmentation+fault&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=LibGimpBase-WARNING+**%3A+script-fu%3A+gimp_wire_read()%3A+error+Segmentation+fault&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
It would seem to be the one, yes. Is there a solution?

/izo\

---

