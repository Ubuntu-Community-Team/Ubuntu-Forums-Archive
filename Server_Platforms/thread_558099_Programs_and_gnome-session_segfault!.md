---
title: "Programs and gnome-session segfault!"
date: 2007-09-23
forum: Server Platforms
---

### Post by gustavosenise on 2007-09-23
I have programs and gnome-session segfault!
I have been told in the #ubuntu channel to change my RAM memory card, so I just did it. But the problem remains.

I don't know what is the path to try to solve this. As I said, none in the #ubuntu channel helped. They said that here is the right place to try to solve this.

I have this problems for about a month, and it is getting worse. Please help me!!

Thank you very much!!

---

### Post by jrib on 2007-09-23
I would see if it happens on a live-cd (the desktop cd).  If it's ok there, then create a new user and see if it happens on that user's account.

---

### Post by gustavosenise on 2007-09-24
I have just created a test user and the problema remains!
What now dude?

:confused::(

---

### Post by jrib on 2007-09-24
did you try the live cd?
[edit] just read your private message that you do not have a live-cd.  Would it be difficult to obtain one?

How far do you get before you get an error message?

---

### Post by gustavosenise on 2007-09-24
I will try to get a live CD in two days wtih a friend!

It happens randomlly! Sometimes it happens when I start firefox ou skype  through a command line! Sometimes it takes a while, so I can even check my email or send this message!

But it is really anoying!!!

---

### Post by gustavosenise on 2007-09-24
Hey _jason!

I have just found a Live CD from version 6.06! Rebooting from it the problem still remains!

Would you tell me what might be your guess!?

Thanks a lot dude!

---

### Post by jrib on 2007-09-24
If you're having the same issue on a live cd, then that suggests a hardware problem.  Have run a memtest?  It's an option in the grub menu.

---

### Post by gustavosenise on 2007-09-24
Thats not the case! This solution was the same offered by the folks at #ubuntu! 

The result of the memtest have always shown errors in different memory addresses, always in test#8! So I changed my memory card, I ran the memtest again! Everything is ok with memory card!

Any other guess?

---

### Post by gustavosenise on 2007-09-25
I have just updated my linux kernel, and it seems to made my life easyer!!

I have been using feirefox for a while this morning and got only 2 crashes! But none of them was segfault! The messages displayed was:

*** glibc detected *** /usr/lib/firefox/firefox-bin: free(): invalid pointer: 0xb4f5cd38 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb769c7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb769fe30]
/usr/lib/libnspr4.so(PR_Free+0x38)[0xb7d590c8]
/usr/lib/firefox/libxpcom_core.so[0xb7e08771]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 03:03 181292     /usr/lib/firefox/firefox-bin
0805b000-0805d000 rw-p 00012000 03:03 181292     /usr/lib/firefox/firefox-bin
0805d000-089a3000 rw-p 0805d000 00:00 0          [heap]
af7c9000-af7ca000 ---p af7c9000 00:00 0 
af7ca000-affca000 rw-p af7ca000 00:00 0 
affca000-afffd000 r-xp 00000000 03:03 1114361    /usr/lib/firefox/components/libmork.so
afffd000-b0000000 rw-p 00032000 03:03 1114361    /usr/lib/firefox/components/libmork.so
b0000000-b00ff000 rw-p b0000000 00:00 0 
b00ff000-b0100000 ---p b00ff000 00:00 0 
b0108000-b0142000 r-xp 00000000 03:03 180821     /usr/lib/firefox/libnssckbi.so
b0142000-b014c000 rw-p 0003a000 03:03 180821     /usr/lib/firefox/libnssckbi.so
b014c000-b018b000 r-xp 00000000 03:03 167201     /usr/lib/libfreebl3.so
b018b000-b018c000 rw-p 0003f000 03:03 167201     /usr/lib/libfreebl3.so
b018c000-b018d000 ---p b018c000 00:00 0 
b018d000-b098d000 rw-p b018d000 00:00 0 
b098d000-b098e000 ---p b098d000 00:00 0 
b098e000-b118e000 rw-p b098e000 00:00 0 
b118e000-b11fb000 r-xp 00000000 03:03 167197     /usr/lib/libnss3.so
b11fb000-b1200000 rw-p 0006d000 03:03 167197     /usr/lib/libnss3.so
b1200000-b12ff000 rw-p b1200000 00:00 0 
b12ff000-b1300000 ---p b12ff000 00:00 0 
b1301000-b1303000 r-xp 00000000 03:03 884824     /lib/libnss_mdns4.so.2
b1303000-b1304000 rw-p 00001000 03:03 884824     /lib/libnss_mdns4.so.2
b1304000-b134f000 r-xp 00000000 03:03 167199     /usr/lib/libsoftokn3.so
b134f000-b1353000 rw-p 0004b000 03:03 167199     /usr/lib/libsoftokn3.so
b1353000-b137b000 r-xp 00000000 03:03 167200     /usr/lib/libssl3.so
b137b000-b137d000 rw-p 00027000 03:03 167200     /usr/lib/libssl3.so
b137d000-b139f000 r-xp 00000000 03:03 167198     /usr/lib/libsmime3.so
b139f000-b13a1000 rw-p 00022000 03:03 167198     /usr/lib/libsmime3.so
b13a1000-b13fc000 r-xp 00000000 03:03 1114517    /usr/lib/firefox/components/libpipnss.so
b13fc000-b1400000 rw-p 0005b000 03:03 1114517    /usr/lib/firefox/components/libpipnss.so
b1400000-b1404000 r-xp 00000000 03:03 918337     /lib/tls/i686/cmov/libnss_dns-2.5.so
b1404000-b1406000 rw-p 00003000 03:03 918337     /lib/tls/i686/cmov/libnss_dns-2.5.so
b1406000-b1408000 r-xp 00000000 03:03 884825     /lib/libnss_mdns4_minimal.so.2
b1408000-b1409000 rw-p 00001000 03:03 884825     /lib/libnss_mdns4_minimal.so.2
b141a000-b1424000 r-xp 00000000 03:03 1114382    /usr/lib/firefox/components/libnecko2.so
b1424000-b1425000 rw-p 0000a000 03:03 1114382    /usr/lib/firefox/components/libnecko2.so
b1425000-b1426000 ---p b1425000 00:00 0 
b1426000-b1c26000 rw-p b1426000 00:00 0 
b1c26000-b1c27000 ---p b1c26000 00:00 0 
b1c27000-b2427000 rw-p b1c27000 00:00 0 
b2427000-b2428000 ---p b2427000 00:00 0 
b2428000-b2c28000 rw-p b2428000 00:00 0 
b2c28000-b2c7f000 r-xp 00000000 03:03 1114363    /usr/lib/firefox/components/libstoragecomps.so
b2c7f000-b2c81000 rw-p 00056000 03:03 1114363    /usr/lib/firefox/components/libstoragecomps.so
b2c81000-b2c94000 r-xp 00000000 03:03 1114461    /usr/lib/firefox/components/libcomposer.so
b2c94000-b2c96000 rw-p 00012000 03:03 1114461    /usr/lib/firefox/components/libcomposer.so
b2c96000-b2ca6000 r-xp 00000000 03:03 1114538    /usr/lib/firefox/components/libspellchecker.so
b2ca6000-b2ca7000 rw-p 0000f000 03:03 1114538    /usr/lib/firefox/components/libspellchecker.so
b2ca7000-b2cac000 r-xp 00000000 03:03 1114458    /usr/lib/firefox/components/libtxmgr.so
b2cac000-b2cad000 rw-p 00004000 03:03 1114458    /usr/lib/firefox/components/libtxmgr.so
b2cad000-b2d48000 r-xp 00000000 03:03 1114457    /usr/lib/firefox/components/libeditor.so
b2d48000-b2d4d000 rw-p 0009a000 03:03 1114457    /usr/lib/firefox/components/libeditor.so
b2d4d000-b2d4e000 ---p *** glibc detected *** /usr/lib/firefox/firefox-bin: realloc(): invalid pointer: 0xb4f631a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(realloc+0x392)[0xb76a0322]
/usr/lib/libglib-2.0.so.0(g_realloc+0x3b)[0xb74df18b]
/usr/lib/libgobject-2.0.so.0(g_object_weak_ref+0x91)[0xb754ddb1]
/usr/lib/libgobject-2.0.so.0(g_object_add_weak_pointer+0x5d)[0xb754dead]
/usr/lib/libgdk-x11-2.0.so.0[0xb7999aeb]
/usr/lib/libgdk-x11-2.0.so.0(_gdk_windowing_window_queue_antiexpose+0x35)[0xb7999c65]
/usr/lib/libgdk-x11-2.0.so.0[0xb798155f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0x97)[0xb7981887]
/usr/lib/libgdk-x11-2.0.so.0[0xb7981905]
/usr/lib/libglib-2.0.so.0[0xb74d6091]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb74d7df2]
/usr/lib/libglib-2.0.so.0[0xb74dadcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb74db179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b16044]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb66fcb22]
/usr/lib/firefox/components/libtoolkitcomps.so[0xb65e2d92]
/usr/lib/firefox/firefox-bin[0x804ea79]
/usr/lib/firefox/firefox-bin[0x804ab8f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb764aebc]
/usr/lib/firefox/firefox-bin[0x804aac1]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 03:03 181292     /usr/lib/firefox/firefox-bin
0805b000-0805d000 rw-p 00012000 03:03 181292     /usr/lib/firefox/firefox-bin
0805d000-089a3000 rw-p 0805d000 00:00 0          [heap]
af7c9000-af7ca000 ---p af7c9000 00:00 0 
af7ca000-affca000 rw-p af7ca000 00:00 0 
affca000-afffd000 r-xp 00000000 03:03 1114361    /usr/lib/firefox/components/libmork.so
afffd000-b0000000 rw-p 00032000 03:03 1114361    /usr/lib/firefox/components/libmork.so
b0000000-b00ff000 rw-p b0000000 00:00 0 
b00ff000-b0100000 ---p b00ff000 00:00 0 
b0108000-b0142000 r-xp 00000000 03:03 180821     /usr/lib/firefox/libnssckbi.so
b0142000-b014c000 rw-p 0003a000 03:03 180821     /usr/lib/firefox/libnssckbi.so
b014c000-b018b000 r-xp 00000000 03:03 167201     /usr/lib/libfreebl3.so
b018b000-b018c000 rw-p 0003f000 03:03 167201     /usr/lib/libfreebl3.so
b018c000-b018d000 ---p b018c000 00:00 0 
b018d000-b098d000 rw-p b018d000 00:00 0 
b098d000-b098e000 ---p b098d000 00:00 0 
b098e000-b118e000 rw-p b098e000 00:00 0 
b118e000-b11fb000 r-xp 00000000 03:03 167197     /usr/lib/libnss3.so
b11fb000-b1200000 rw-p 0006d000 03:03 167197     /usr/lib/libnss3.so
b1200000-b12ff000 rw-p b1200000 00:00 0 
b12ff000-b1300000 ---p b12ff000 00:00 0 
b1301000-b1303000 r-xp 00000000 03:03 884824     /lib/libnss_mdns4.so.2
b1303000-b1304000 rw-p 00001000 03:03 884824     /lib/libnss_mdns4.so.2
b1304000-b134f000 r-xp 00000000 03:03 167199     /usr/lib/libsoftokn3.so
b134f000-b1353000 rw-p 0004b000 03:03 167199     /usr/lib/libsoftokn3.so
b1353000-b137b000 r-xp 00000000 03:03 167200     /usr/lib/libssl3.so
b137b000-b137d000 rw-p 00027000 03:03 167200     /usr/lib/libssl3.so
b137d000-b139f000 r-xp 00000000 03:03 167198     /usr/lib/libsmime3.so
b139f000-b13a1000 rw-p 00022000 03:03 167198     /usr/lib/libsmime3.so
b13a1000-b13fc000 r-xp 00000000 03:03 1114517    /usr/lib/firefox/components/libpipnss.so
b13fc000-b1400000 rw-p 0005b000 03:03 1114517    /usr/lib/firefox/components/libpipnss.so
b1400000-b1404000 r-xp 00000000 03:03 918337     /lib/tls/i686/cmov/libnss_dns-2.5.so
b1404000-b1406000 rw-p 00003000 03:03 918337     /lib/tls/i686/cmov/libnss_dns-2.5.so
b1406000-b1408000 r-xp 00000000 03:03 884825     /lib/libnss_mdns4_minimal.so.2
b1408000-b1409000 rw-p 00001000 03:03 884825     /lib/libnss_mdns4_minimal.so.2
b141a000-b1424000 r-xp 00000000 03:03 1114382    /usr/lib/firefox/components/libnecko2.so
b1424000-b1425000 rw-p 0000a000 03:03 1114382    /usr/lib/firefox/components/libnecko2.so
b1425000-b1426000 ---p b1425000 00:00 0 
b1426000-b1c26000 rw-p b1426000 00:00 0 
b1c26000-b1c27000 ---p b1c26000 00:00 0 
b1c27000-b2427000 rw-p b1c27000 00:00 0 
b2427000-b2428000 ---p b2427000 00:00 0 
b2428000-b2c28000 rw-p b2428000 00:00 0 
b2c28000-b2c7f000 r-xp 00000^[[BCancelado (core dumped)

_______________

Any ideas why?

---

### Post by gustavosenise on 2007-09-25
The segfaults remains!!
Please help!

---

