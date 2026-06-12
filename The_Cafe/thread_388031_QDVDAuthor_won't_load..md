---
title: "QDVDAuthor won't load."
date: 2007-03-19
forum: The Cafe
---

### Post by SZF2001 on 2007-03-19
I can't get this program to open.

In the terminal, I try it normaly and get this:

```
qdvdauthor
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QComboBox::text: (m_pComboFontStyle) Index 0 out of range
QComboBox::setCurrentItem: (m_pComboFontStyle) Index 0 out of range
Segmentation fault

```

Then I give it root access, still can't open:

```
sudo qdvdauthor
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
*** glibc detected *** qdvdauthor: corrupted double-linked list: 0x0867e608 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb748fceb]
/lib/tls/i686/cmov/libc.so.6[0xb7491cd7]
/lib/tls/i686/cmov/libc.so.6(malloc+0x7f)[0xb749383f]
/usr/lib/libstdc++.so.6(_Znwj+0x27)[0xb76424b7]
/usr/lib/libstdc++.so.6(_Znaj+0x1d)[0xb76425ed]
qdvdauthor[0x81f9394]
qdvdauthor[0x81f9ca4]
/usr/lib/libqt-mt.so.3(_ZN15QThreadInstance5startEPv+0xb1)[0xb79da101]
/lib/tls/i686/cmov/libpthread.so.0[0xb7f33504]
/lib/tls/i686/cmov/libc.so.6(__clone+0x5e)[0xb74f851e]
======= Memory map: ========
08048000-084ac000 r-xp 00000000 fe:00 798444     /usr/bin/qdvdauthor
084ac000-084ae000 rw-p 00463000 fe:00 798444     /usr/bin/qdvdauthor
084ae000-08696000 rw-p 084ae000 00:00 0          [heap]
b4700000-b4721000 rw-p b4700000 00:00 0 
b4721000-b4800000 ---p b4721000 00:00 0 
b4804000-b4805000 ---p b4804000 00:00 0 
b4805000-b5005000 rwxp b4805000 00:00 0 
b5005000-b5006000 ---p b5005000 00:00 0 
b5006000-b5806000 rwxp b5006000 00:00 0 
b5806000-b5814000 r-xp 00000000 fe:00 1297959    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xxmc.so
b5814000-b5815000 rw-p 0000d000 fe:00 1297959    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xxmc.so
b5815000-b581b000 r-xp 00000000 fe:00 1297958    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xvmc.so
b581b000-b581c000 rw-p 00005000 fe:00 1297958    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xvmc.so
b581c000-b5830000 r-xp 00000000 fe:00 1297956    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xshm.so
b5830000-b5831000 rw-p 00013000 fe:00 1297956    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xshm.so
b5831000-b586f000 r-xp 00000000 fe:00 1297955    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_vidix.so
b586f000-b587f000 rw-p 0003e000 fe:00 1297955    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_vidix.so
b587f000-b5880000 rw-p b587f000 00:00 0 
b5880000-b588c000 r-xp 00000000 fe:00 789929     /usr/lib/libdirect-0.9.so.24.0.0
b588c000-b588d000 rw-p 0000c000 fe:00 789929     /usr/lib/libdirect-0.9.so.24.0.0
b588d000-b58d9000 r-xp 00000000 fe:00 789937     /usr/lib/libdirectfb-0.9.so.24.0.0
b58d9000-b58db000 rw-p 0004b000 fe:00 789937     /usr/lib/libdirectfb-0.9.so.24.0.0
b58db000-b593f000 r-xp 00000000 fe:00 790630     /usr/lib/libSDL-1.2.so.0.7.3
b593f000-b5941000 rw-p 00064000 fe:00 790630     /usr/lib/libSDL-1.2.so.0.7.3
b5941000-b5969000 rw-p b5941000 00:00 0 
b5969000-b596d000 r-xp 00000000 fe:00 794678     /usr/lib/libXvMCW.so.1.0.0
b596d000-b596e000 rw-p 00003000 fe:00 794678     /usr/lib/libXvMCW.so.1.0.0
b596e000-b5977000 r-xp 00000000 fe:00 1297957    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xv.so
b5977000-b5978000 rw-p 00008000 fe:00 1297957    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_xv.so
b5978000-b597e000 r-xp 00000000 fe:00 789615     /usr/lib/libdrm.so.2.0.0
b597e000-b597f000 rw-p 00005000 fe:00 789615     /usr/lib/libdrm.so.2.0.0
b597f000-b5983000 r-xp 00000000 fe:00 786802     /usr/lib/libXxf86vm.so.1.0.0
b5983000-b5984000 rw-p 00003000 fe:00 786802     /usr/lib/libXxf86vm.so.1.0.0
b5984000-b59fd000 r-xp 00000000 fe:00 786792     /usr/lib/libGLU.so.1.3.060501
b59fd000-b59fe000 rw-p 00079000 fe:00 786792     /usr/lib/libGLU.so.1.3.060501
b59fe000-b5a66000 r-xp 00000000 fe:00 786804     /usr/lib/libGL.so.1.2
b5a66000-b5a6c000 rw-p 00067000 fe:00 786804     /usr/lib/libGL.so.1.2
b5a6c000-b5a6d000 rw-p b5a6c000 00:00 0 
b5a6f000-b5a73000 r-xp 00000000 fe:00 794230     /usr/lib/libXv.so.1.0.0
b5a73000-b5a74000 rw-p 00003000 fe:00 794230     /usr/lib/libXv.so.1.0.0
b5a74000-b5a78000 r-xp 00000000 fe:00 790624     /usr/lib/libfusion-0.9.so.24.0.0
b5a78000-b5a79000 rw-p 00003000 fe:00 790624     /usr/lib/libfusion-0.9.so.24.0.0
b5a79000-b5a7b000 r-xp 00000000 fe:00 1297954    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_sdl.so
b5a7b000-b5a7c000 rw-p 00002000 fe:00 1297954    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_sdl.so
b5a7c000-b5a93000 r-xp 00000000 fe:00 1297953    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_opengl.so
b5a93000-b5a94000 rw-p 00016000 fe:00 1297953    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_opengl.so
b5a94000-b5aa5000 r-xp 00000000 fe:00 1297951    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_fb.so
b5aa5000-b5aa6000 rw-p 00010000 fe:00 1297951    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_fb.so
b5aa6000-b5ab5000 r-xp 00000000 fe:00 1297949    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_caca.so
b5ab5000-b5ab6000 rw-p 0000e000 fe:00 1297949    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_caca.so
b5ab6000-b5aba000 r-xp 00000000 fe:00 787151     /usr/lib/libgpm.so.1.19.6
b5aba000-b5abb000 rw-p 00004000 fe:00 787151     /usr/lib/libgpm.so.1.19.6
b5abb000-b5b44000 r-xp 00000000 fe:00 8962266    /lib/libslang.so.2.0.6
b5b44000-b5b53000 rw-p 00088000 fe:00 8962266    /lib/libslang.so.2.0.6
b5b53000-b5b73000 rw-p b5b53000 00:00 0 
b5b73000-b5baa000 r-xp 00000000 fe:00 8962084    /lib/libncurses.so.5.5
b5baa000-b5bb2000 rw-p 00037000 fe:00 8962084    /lib/libncurses.so.5.5
b5bb2000-b5bb3000 rw-p b5bb2000 00:00 0 
b5bb3000-b5bca000 r-xp 00000000 fe:00 793378     /usr/lib/libaa.so.1.0.4
b5bca000-b5bcc000 rw-p 00017000 fe:00 793378     /usr/lib/libaa.so.1.0.4
b5bcc000-b5bcd000 rw-p b5bcc000 00:00 0 
b5bd0000-b5bdb000 r-xp 00000000 fe:00 1297950    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_dxr3.so
b5bdb000-b5bdc000 rw-p 0000a000 fe:00 1297950    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_dxr3.so
b5bdc000-b5bdf000 r-xp 00000000 fe:00 1297947    /usr/lib/xine/plugins/1.1.2/xineplug_inp_vcdo.so
b5bdf000-b5be0000 rw-p 00002000 fe:00 1297947    /usr/lib/xine/plugins/1.1.2/xineplug_inp_vcdo.so
b5be0000-b5be1000 rw-p b5be0000 00:00 0 
b5be1000-b5c30000 r-xp 00000000 fe:00 1297946    /usr/lib/xine/plugins/1.1.2/xineplug_inp_vcd.so
b5c30000-b5c32000 rw-p 0004e000 fe:00 1297946    /usr/lib/xine/plugins/1.1.2/xineplug_inp_vcd.so
b5c32000-b5c37000 rw-p b5c32000 00:00 0 
b5c37000-b5c4b000 r-xp 00000000 fe:00 787981     /usr/lib/libsasl2.so.2.0.19
b5c4b000-b5c4c000 rw-p 00014000 fe:00 787981     /usr/lib/libsasl2.so.2.0.19
b5c4c000-b5c57000 r-xp 00000000 fe:00 787986     /usr/lib/liblber.so.2.0.130
b5c57000-b5c58000 rw-p 0000b000 fe:00 787986     /usr/lib/liblber.so.2.0.130
b5c58000-b5c8c000 r-xp 00000000 fe:00 787987     /usr/lib/libldap_r.so.2.0.130
b5c8c000-b5c8d000 rw-p 00034000 fe:00 787987     /usr/lib/libldap_r.so.2.0.130
b5c8d000-b5c8f000 r-xp 00000000 fe:00 8962159    /lib/libcom_err.so.2.1
b5c8f000-b5c90000 rw-p 00001000 fe:00 8962159    /lib/libcom_err.so.2.1
b5c90000-b5c94000 r-xp 00000000 fe:00 789519     /usr/lib/libkrb5support.so.0.0
b5c94000-b5c95000 rw-p 00003000 fe:00 789519     /usr/lib/libkrb5support.so.0.0
b5c95000-b5cb9000 r-xp 00000000 fe:00 789516     /usr/lib/libk5crypto.so.3.0
b5cb9000-b5cba000 rw-p 00023000 fe:00 789516     /usr/lib/libk5crypto.so.3.0
b5cba000-b5d34000 r-xp 00000000 fe:00 789518     /usr/lib/libkrb5.so.3.2
b5d34000-b5d36000 rw-p 0007a000 fe:00 789518     /usr/lib/libkrb5.so.3.2
b5d36000-b5d51000 r-xp 00000000 fe:00 789515     /usr/lib/libgssapi_krb5.so.2.2
b5d51000-b5d52000 rw-p 0001b000 fe:00 789515     /usr/lib/libgssapi_krb5.so.2.2
b5d52000-b5d57000 r-xp 00000000 fe:00 8962136    /lib/tls/i686/cmov/libcrypt-2.4.so
b5d57000-b5d59000 rw-p 00004000 fe:00 8962136    /lib/tls/i686/cmov/libcrypt-2.4.so
b5d59000-b5d80000 rw-p b5d59000 00:00 0 
b5d80000-b5f28000 r-xp 00000000 fe:00 787989     /usr/lib/libsmbclient.so.0.1
b5f28000-b5f33000 rw-p 001a7000 fe:00 787989     /usr/lib/libsmbclient.so.0.1
b5f33000-b5f43000 rw-p b5f33000 00:00 0 
b5f43000-b5f45000 r-xp 00000000 fe:00 1297948    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_aa.so
b5f45000-b5f46000 rw-p 00001000 fe:00 1297948    /usr/lib/xine/plugins/1.1.2/xineplug_vo_out_aa.so
b5f46000-b5f4c000 r-xp 00000000 fe:00 1297945    /usr/lib/xine/plugins/1.1.2/xineplug_inp_v4l.so
b5f4c000-b5f4d000 rw-p 00005000 fe:00 1297945    /usr/lib/xine/plugins/1.1.2/xineplug_inp_v4l.so
b5f4d000-b5f51000 r-xp 00000000 fe:00 1297944    /usr/lib/xine/plugins/1.1.2/xineplug_inp_stdin_fifo.so
b5f51000-b5f52000 rw-p 00003000 fe:00 1297944    /usr/lib/xine/plugins/1.1.2/xineplug_inp_stdin_fifo.so
b5f52000-b5f55000 r-xp 00000000 fe:00 1297943    /usr/lib/xine/plugins/1.1.2/xineplug_inp_smb.so
b5f55000-b5f56000 rw-p 00002000 fe:00 1297943    /usr/lib/xine/plugins/1.1.2/xineplug_inp_smb.so
b5f56000-b5f62000 r-xp 00000000 fe:00 1297942    /usr/lib/xine/plugins/1.1.2/xineplug_inp_rtsp.so
b5f62000-b5f63000 rw-p 0000b000 fe:00 1297942    /usr/lib/xine/plugins/1.1.2/xineplug_inp_rtsp.so
b5f63000-b5f67000 r-xp 00000000 fe:00 1297941    /usr/lib/xine/plugins/1.1.2/xineplug_inp_rtp.so
b5f67000-b5f68000 rw-p 00003000 fe:00 1297941    /usr/lib/xine/plugins/1.1.2/xineplug_inp_rtp.so
b5f68000-b5f6d000 r-xp 00000000 fe:00 1297940    /usr/lib/xine/plugins/1.1.2/xineplug_inp_pvr.so
b5f6d000-b5f6e000 rw-p 00004000 fe:00 1297940    /usr/lib/xine/plugins/1.1.2/xineplug_inp_pvr.so
b5f6e000-b5f73000 r-xp 00000000 fe:00 1297939    /usr/lib/xine/plugins/1.1.2/xineplug_inp_pnm.so
b5f73000-b5f74000 rw-p 00004000 fe:00 1297939    /usr/lib/xine/plugins/1.1.2/xineplug_inp_pnm.so
b5f74000-b5f7d000 r-xp 00000000 fe:00 1297937    /usr/lib/xine/plugins/1.1.2/xineplug_inp_mms.so
b5f7d000-b5f7e000 rw-p 00009000 fe:00 1297937    /usr/lib/xine/plugins/1.1.2/xineplug_inp_mms.so
b5f7e000-b5fb0000 r-xp 00000000 fe:00 8962058    /lib/libsepol.so.1
b5fb0000-b5fb1000 rw-p 00031000 fe:00 8962058    /lib/libsepol.so.1
b5fb1000-b5fbb000 rw-p b5fb1000 00:00 0 
b5fbb000-b5fbe000 r-xp 00000000 fe:00 789498     /usr/lib/libgpg-error.so.0.2.0
b5fbe000-b5fbf000 rw-p 00002000 fe:00 789498     /usr/lib/libgpg-error.so.0.2.0
b5fbf000-b600b000 r-xp 00000000 fe:00 788881     /usr/lib/libgcrypt.so.11.2.1
b600b000-b600d000 rw-p 0004b000 fe:00 788881     /usr/lib/libgcrypt.so.11.2.1
b600d000-b601f000 r-xp 00000000 fe:00 788895     /usr/lib/libtasn1.so.3.0.5
b601f000-b6020000 rw-p 00011000 fe:00 788895     /usr/lib/libtasn1.so.3.0.5
b6020000-b6032000 r-xp 00000000 fe:00 8962223    /lib/libselinux.so.1
b6032000-b6034000 rw-p 00011000 fe:00 8962223    /lib/libselinux.so.1
b6034000-b6042000 r-xp 00000000 fe:00 788394     /usr/lib/libavahi-client.so.3.2.0
b6042000-b6043000 rw-p 0000e000 fe:00 788394     /usr/lib/libavahi-client.so.3.2.0
b6043000-b604d000 r-xp 00000000 fe:00 788390     /usr/lib/libavahi-common.so.3.4.2
b604d000-b604e000 rw-p 00009000 fe:00 788390     /usr/lib/libavahi-common.so.3.4.2
b604e000-b6050000 r-xp 00000000 fe:00 789485     /usr/lib/libavahi-glib.so.1.0.1
b6050000-b6051000 rw-p 00002000 fe:00 789485     /usr/lib/libavahi-glib.so.1.0.1
b6051000-b60ba000 r-xp 00000000 fe:00 789506     /usr/lib/libgnutls.so.13.0.5
b60ba000-b60c0000 rw-p 00068000 fe:00 789506     /usr/lib/libgnutls.so.13.0.5
b60c0000-b60ef000 r-xp 00000000 fe:00 788392     /usr/lib/libdbus-1.so.3.0.0
b60ef000-b60f0000 rw-p 0002f000 fe:00 788392     /usr/lib/libdbus-1.so.3.0.0
b60f0000-b610a000 r-xp 00000000 fe:00 787287     /usr/lib/libdbus-glib-1.so.2.0.0
b610a000-b610b000 rw-p 00019000 fe:00 787287     /usr/lib/libdbus-glib-1.so.2.0.0
b610b000-b621e000 r-xp 00000000 fe:00 789440     /usr/lib/libxml2.so.2.6.26
b621e000-b6223000 rw-p 00113000 fe:00 789440     /usr/lib/libxml2.so.2.6.26
b6223000-b6224000 rw-p b6223000 00:00 0 
b6224000-b626b000 r-xp 00000000 fe:00 789436     /usr/lib/libORBit-2.so.0.1.0
b626b000-b6275000 rw-p 00046000 fe:00 789436     /usr/lib/libORBit-2.so.0.1.0
b6275000-b62ae000 r-xp 00000000 fe:00 789379     /usr/lib/libgobject-2.0.so.0.1200.4
b62ae000-b62af000 rw-p 00038000 fe:00 789379     /usr/lib/libgobject-2.0.so.0.1200.4
b62af000-b62dd000 r-xp 00000000 fe:00 789473     /usr/lib/libgconf-2.so.4.1.0
b62dd000-b62e0000 rw-p 0002e000 fe:00 789473     /usr/lib/libgconf-2.so.4.1.0
b62e0000-b6335000 r-xp 00000000 fe:00 787995     /usr/lib/libgnomevfs-2.sAborted

```

Any idea on what to do?

---

