---
title: "Why I love stack smashing protection..."
date: 2008-10-28
forum: Security
---

### Post by jdong on 2008-10-28
```

[jdong@blackbook:/tmp]$ vlc exploit.mpg                           (10-28 12:44)
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000379] ty demux error: Unsupported SEQ bitmap size in master chunk
*** stack smashing detected ***: vlc terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7eeb558]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7eeb510]
/usr/lib/vlc/demux/libty_plugin.so[0xb44e0bc4]
/usr/lib/vlc/demux/libty_plugin.so[0xb44dc6a6]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:04 1262159    /usr/bin/vlc
0804a000-0804b000 r--p 00001000 08:04 1262159    /usr/bin/vlc
0804b000-0804c000 rw-p 00002000 08:04 1262159    /usr/bin/vlc
09cb4000-09edf000 rw-p 09cb4000 00:00 0          [heap]
ad52d000-ad52e000 ---p ad52d000 00:00 0 
ad52e000-add2e000 rwxp ad52e000 00:00 0 
add2e000-ade59000 rw-p add2e000 00:00 0 
ade59000-ade5a000 ---p ade59000 00:00 0 
ade5a000-ae65a000 rwxp ade5a000 00:00 0 
ae65a000-ae6fc000 rw-p 00000000 08:04 318879     /tmp/exploit.mpg
ae6fc000-ae6fd000 ---p ae6fc000 00:00 0 
ae6fd000-aeefd000 rwxp ae6fd000 00:00 0 
aeefd000-aeefe000 ---p aeefd000 00:00 0 
aeefe000-af6fe000 rwxp aeefe000 00:00 0 
af6fe000-af6ff000 ---p af6fe000 00:00 0 
af6ff000-afeff000 rwxp af6ff000 00:00 0 
afeff000-aff00000 ---p afeff000 00:00 0 
aff00000-b0700000 rwxp aff00000 00:00 0 
b0700000-b0721000 rw-p b0700000 00:00 0 
b0721000-b0800000 ---p b0721000 00:00 0 
b088f000-b0894000 r-xp 00000000 08:04 1292983    /usr/lib/qt4/plugins/inputmethods/libqimsw-multi.so
b0894000-b0895000 r--p 00004000 08:04 1292983    /usr/lib/qt4/plugins/inputmethods/libqimsw-multi.so
b0895000-b0896000 rw-p 00005000 08:04 1292983    /usr/lib/qt4/plugins/inputmethods/libqimsw-multi.so
b0896000-b089c000 r--s 00000000 08:04 294404     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b089c000-b089f000 r--s 00000000 08:04 296089     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b089f000-b08a0000 r--s 00000000 08:04 296088     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b08a0000-b08a3000 r--s 00000000 08:04 295775     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b08a3000-b08a6000 r--s 00000000 08:04 295774     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b08a6000-b08a9000 r--s 00000000 08:04 295773     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b08a9000-b08b1000 r--s 00000000 08:04 295771     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b08b1000-b08bc000 r--s 00000000 08:04 295245     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b08bc000-b08bd000 r--s 00000000 08:04 295613     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b08bd000-b08c0000 r--s 00000000 08:04 295596     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b08c0000-b08c7000 r--s 00000000 08:04 295560     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b08c7000-b08cd000 r--s 00000000 08:04 294398     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b08cd000-b08d5000 r--s 00000000 08:04 294410     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b08d5000-b08e3000 r--s 00000000 08:04 294393     /var/cache/fontconfig/865f88548240fee46819705c6468c165-x86.cache-2
b08e3000-b08e5000 r-xp 00000000 08:04 556206     /usr/lib/gconv/UTF-16.so
b08e5000-b08e6000 r--p 00001000 08:04 556206     /usr/lib/gconv/UTF-16.so
b08e6000-b08e7000 rw-p 00002000 08:04 556206     /usr/lib/gconv/UTF-16.so
b08e7000-b08e8000 ---p b08e7000 00:00 0 
b08e8000-b10e8000 rwxp b08e8000 00:00 0 
b10e8000-b10e9000 ---p b10e8000 00:00 0 
b10e9000-b18e9000 rwxp b10e9000 00:00 0 
b18e9000-b18ea000 ---p b18e9000 00:00 0 
b18ea000-b20ea000 rwxp b18ea000 00:00 0 
b20ea000-b20eb000 ---p b20ea000 00:00 0 
b20eb000-b28eb000 rwxp b20eb000 00:00 0 
b28eb000-b28ec000 ---p b28eb000 00:00 0 
b28ec000-b30ec000 rwxp b28ec000 00:00 0 
b30ec000-b30ed000 ---p b30ec000 00:00 0 
b30ed000-b38ed000 rwxp b30ed000 00:00 0 
b38ed000-b38ee000 ---p b38ed000 00:00 0 
b38ee000-b40ee000 rwxp b38ee000 00:00 0 
b40ee000-b40f0000 r-xp 00000000 08:04 1343185    /usr/lib/vlc/access_filter/libaccess_filter_bandwidth_plugin.so
b40f0000-b40f1000 r--p 00001000 08:04 1343185    /usr/lib/vlc/access_filter/libaccess_filter_bandwidth_plugin.so
b40f1000-b40f2000 rw-p 00002000 08:04 1343185    /usr/lib/vlc/access_filter/libaccess_filter_bandwidth_plugin.so
b40f2000-b40f4000 r-xp 00000000 08:04 1343186    /usr/lib/vlc/access_filter/libaccess_filter_dump_plugin.so
b40f4000-b40f5000 r--p 00001000 08:04 1343186    /usr/lib/vlc/access_filter/libaccess_filter_dump_plugin.so
b40f5000-b40f6000 rw-p 00002000 08:04 1343186    /usr/lib/vlc/access_filter/libaccess_filter_dump_plugin.so
b40f6000-b40f9000 r-xp 00000000 08:04 1343188    /usr/lib/vlc/access_filter/libaccess_filter_timeshift_plugin.so
b40f9000-b40fa000 r--p 00002000 08:04 1343188    /usr/lib/vlc/access_filter/libaccess_filter_timeshift_plugin.so
b40fa000-b40fb000 rw-p 00003000 08:04 1343188    /usr/lib/vlc/access_filter/libaccess_filter_timeshift_plugin.so
b40fb000-b40fd000 r-xp 00000000 08:04 1343187    /usr/lib/vlc/access_filter/libaccess_filter_record_plugin.so
b40fd000-b40fe000 r--p 00001000 08:04 1343187    /usr/lib/vlc/access_filter/libaccess_filter_record_plugin.so
b40fe000-b40ff000 rw-p 00002000 08:04 1343187    /usr/lib/vlc/access_filter/libaccess_filter_record_plugin.so
b40ff000-b4102000 r-xp 00000000 08:04 1431096    /usr/lib/vlc/stream_out/libstream_out_bridge_plugin.so
b4102000-b4103000 r--p 00002000 08:04 1431096    /usr/lib/vlc/stream_out/libstream_out_bridge_plugin.so
b4103000-b4104000 rw-p 00003000 08:04 1431096    /usr/lib/vlc/stream_out/libstream_out_bridge_plugin.so
b4104000-b4106000 r-xp 00000000 08:04 1431098    /usr/lib/vlc/stream_out/libstream_out_autodel_plugin.so
b4106000-b4107000 r--p 00001000 08:04 1431098    /usr/lib/vlc/stream_out/libstream_out_autodel_plugin.so
b4107000-b4108000 rw-p 00002000 08:04 1431098    /usr/lib/vlc/stream_out/libstream_out_autodel_plugin.so
b4108000-b410c000 r-xp 00000000 08:04 1431097    /usr/lib/vlc/stream_out/libstream_out_mosaic_bridge_plugin.so
b410c000-b410d000 r--p 00003000 08:04 1431097    /usr/lib/vlc/stream_out/libstream_out_mosaic_bridge_plugin.so
b410d000-b410e000 rw-p 00004000 08:04 1431097    /usr/lib/vlc/stream_out/libstream_out_mosaic_bridge_plugin.so
b410e000-b4112000 r-xp 00000000 08:04 1431090    /usr/lib/vlc/stream_out/libstream_out_standard_plugin.so
b4112000-b4113000 r--p 00003000 08:04 1431090    /usr/lib/vlc/stream_out/libstream_out_standard_plugin.so
b4113000-b4114000 rw-p 00004000 08:04 1431090    /usr/lib/vlc/stream_out/libstream_out_standard_plugin.so
b4114000-b4116000 r-xp 00000000 08:04 1431092    /usr/lib/vlc/stream_out/libstream_out_duplicate_plugin.so
b4116000-b4117000 r--p 00001000 08:04 1431092    /usr/lib/vlc/stream_out/libstream_out_duplicate_plugin.so
b4117000-b4118000 rw-p 00002000 08:04 1431092    /usr/lib/vlc/stream_out/libstream_out_duplicate_plugin.so
b4118000-b4128000 r-xp 00000000 08:04 1431099    /usr/lib/vlc/stream_out/libstream_out_rtp_plugin.so
b4128000-b4129000 r--p 0000f000 08:04 1431099    /usr/lib/vlc/stream_out/libstream_out_rtp_plugin.so
b4129000-b412a000 rw-p 00010000 08:04 1431099    /usr/lib/vlc/stream_out/libstream_out_rtp_plugin.so
b412a000-b4134000 r-xp 00000000 08:04 1431091    /usr/lib/vlc/stream_out/libstream_out_transcode_plugin.so
b4134000-b4135000 r--p 00009000 08:04 1431091    /usr/lib/vlc/stream_out/libstream_out_transcode_plugin.so
b4135000-b4136000 rw-p 0000a000 08:04 1431091    /usr/lib/vlc/stream_out/libstream_out_transcode_plugin.so
b4136000-b4138000 r-xp 00000000 08:04 1431095    /usr/lib/vlc/stream_out/libstream_out_gather_plugin.so
b4138000-b4139000 r--p 00001000 08:04 1431095    /usr/lib/vlc/stream_out/libstream_out_gather_plugin.so
b4139000-b413a000 rw-p 00002000 08:04 1431095    /usr/lib/vlc/stream_out/libstream_out_gather_plugin.so
b413a000-b413c000 r-xp 00000000 08:04 1431094    /usr/lib/vlc/stream_out/libstream_out_display_plugin.so
b413c000-b413d000 r--p 00001000 08:04 1431094    /usr/lib/vlc/stream_out/libstream_out_display_plugin.so
b413d000-b413e000 rw-p 00002000 08:04 1431094    /usr/lib/vlc/stream_out/libstream_out_display_plugin.so
b413e000-b4140000 r-xp 00000000 08:04 1431093    /usr/lib/vlc/stream_out/libstream_out_es_plugin.so
b4140000-b4141000 r--p 00001000 08:04 1431093    /usr/lib/vlc/stream_out/libstream_out_es_plugin.so
b4141000-b4142000 rw-p 00002000 08:04 1431093    /usr/lib/vlc/stream_out/libstream_out_es_plugin.so
b4142000-b4155000 r-xp 00
[1]    11186 abort      vlc exploit.mpg


```

This is a VLC 0.9.4 vulnerability that would otherwise allow arbitrary code execution when a victim plays an arbitrary .mpg.

only Intrepid has an "affected" version (previous versions have a different MPG demuxer code path that isn't vulnerable), but as you can see above, GCC stack smashing protection catches the error and kills the VLC process before it can carry out its evil.

---

### Post by OpenSourceFuture on 2008-10-28
Very cool.

---

### Post by jdong on 2008-10-28
Very cool indeed, and good news for me as one of the people tending to VLC. This caused me to lose a bit of sleep last night because I've seen on various security lists that I subscribe to, examples of live Windows proof-of-concept hacks based around this vulnerability. They only require luring the user to play with VLC an affected .mpg file and can end up executing any command as the user -- a VERY nasty effect that could easily be used to drop malware, grant further access, and so on. Given this severity, it was almost certainly going to call on us packages to RUSH out a 0.9.5 package into Intrepid at the last minute, probably poorly tested at best.


This countermeasure in Ubuntu means that the worst thing that can happen to the user is that his VLC crashes, or VLC browser plugin crashes. This is an annoyance for sure, and still will be fixed for Intrepid by an updated VLC in the near future, but at least it's not a huge gaping security hole.

EDIT: Just as a side note, I recall once having one of the Ubuntu Security Team guys tell me about how many of the released security patches for Ubuntu are those that stack-protector was able to detect and abort. I believe that number was on the order of 75% (at least 50% for sure). This is a definite win for users and administrators against new or undiscovered threats.

---

### Post by OpenSourceFuture on 2008-10-28
Thats good user transparent security practices in action, and as most users have no idea about any type of exploit, protection like this integrated makes a big real world difference, and obviously has made your job easier.

---

### Post by jdong on 2008-10-28
Yeah, I am a big fan of proactive hardening, such as the GCC stack protector shown above, and also Apparmor / SELinux fine-grained permissions for at-risk services. IMO it's difficult to impossible to guarantee that software is perfect, but it is easier to minimize the impact of a compromise should it happen. We still have plenty to improve in using more of these proactive technologies but I think we're off to a great start.

---

