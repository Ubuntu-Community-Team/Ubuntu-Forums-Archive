---
title: "xviewg memory problem"
date: 2011-02-16
forum: Virtualisation
---

### Post by d.atanasov on 2011-02-16
Hello people,

I have a very unpleasant experience with using program depending on "xviewg". When I run the program it freezes and crash all X server, after that i have to kill it. After killing it the "glibc" says that i have "double free or corruption". 
I saw that some programs doesn`t work until you export the libraries like this : "http://ubuntuforums.org/showthread.php?t=447802&highlight=xviewg". 
What do you think I can do to eliminate this bug? 
As additional info I can paste the "Backtrace" of memory corruption: 

diko@diko-laptop:/media/0D88EBF000AA1675/programs/data_view$ ./data_view
*** glibc detected *** ./data_view: double free or corruption (fasttop): 0x0809e5e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x2bf0d1]
/lib/tls/i686/cmov/libc.so.6[0x2c07d2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x2c38ad]
/usr/lib/libxview.so.3(generic_destroy+0x3a)[0x170eaa]
/usr/lib/libxview.so.3(xv_destroy_status+0x6c)[0x230ddc]
/usr/lib/libxview.so.3(ndet_immediate_destroy+0x6c)[0x17acfc]
/usr/lib/libxview.so.3(ntfy_paranoid_enum_conditions+0xbd)[0x18766d]
/usr/lib/libxview.so.3(notify_die+0x73)[0x17ae13]
/usr/lib/libxview.so.3(notify_start+0xbcd)[0x17ca9d]
/usr/lib/libxview.so.3(xv_main_loop+0xb8)[0x227638]
./data_view[0x80493c9]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x26ab56]
./data_view[0x80490b1]
======= Memory map: ========
00110000-00248000 r-xp 00000000 08:05 415301     /usr/lib/libxview.so.3.2.4
00248000-0024a000 r--p 00137000 08:05 415301     /usr/lib/libxview.so.3.2.4
0024a000-0024e000 rw-p 00139000 08:05 415301     /usr/lib/libxview.so.3.2.4
0024e000-00254000 rw-p 00000000 00:00 0 
00254000-00392000 r-xp 00000000 08:05 15884      /lib/tls/i686/cmov/libc-2.10.1.so
00392000-00393000 ---p 0013e000 08:05 15884      /lib/tls/i686/cmov/libc-2.10.1.so
00393000-00395000 r--p 0013e000 08:05 15884      /lib/tls/i686/cmov/libc-2.10.1.so
00395000-00396000 rw-p 00140000 08:05 15884      /lib/tls/i686/cmov/libc-2.10.1.so
00396000-00399000 rw-p 00000000 00:00 0 
00399000-0039d000 r-xp 00000000 08:05 62111      /usr/lib/libXfixes.so.3.1.0
0039d000-0039e000 r--p 00003000 08:05 62111      /usr/lib/libXfixes.so.3.1.0
0039e000-0039f000 rw-p 00004000 08:05 62111      /usr/lib/libXfixes.so.3.1.0
003fa000-00416000 r-xp 00000000 08:05 6925       /lib/libgcc_s.so.1
00416000-00417000 r--p 0001b000 08:05 6925       /lib/libgcc_s.so.1
00417000-00418000 rw-p 0001c000 08:05 6925       /lib/libgcc_s.so.1
004a0000-004ae000 r-xp 00000000 08:05 59592      /usr/lib/libXext.so.6.4.0
004ae000-004af000 r--p 0000d000 08:05 59592      /usr/lib/libXext.so.6.4.0
004af000-004b0000 rw-p 0000e000 08:05 59592      /usr/lib/libXext.so.6.4.0
0052b000-00533000 r-xp 00000000 08:05 24072      /usr/lib/libXrender.so.1.3.0
00533000-00534000 r--p 00007000 08:05 24072      /usr/lib/libXrender.so.1.3.0
00534000-00535000 rw-p 00008000 08:05 24072      /usr/lib/libXrender.so.1.3.0
006c2000-006de000 r-xp 00000000 08:05 37246      /usr/lib/libxcb.so.1.1.0
006de000-006df000 r--p 0001c000 08:05 37246      /usr/lib/libxcb.so.1.1.0
006df000-006e0000 rw-p 0001d000 08:05 37246      /usr/lib/libxcb.so.1.1.0
00715000-00719000 r-xp 00000000 08:05 9372       /usr/lib/libXdmcp.so.6.0.0
00719000-0071a000 rw-p 00003000 08:05 9372       /usr/lib/libXdmcp.so.6.0.0
007f7000-007f9000 r-xp 00000000 08:05 62869      /lib/tls/i686/cmov/libutil-2.10.1.so
007f9000-007fa000 r--p 00001000 08:05 62869      /lib/tls/i686/cmov/libutil-2.10.1.so
007fa000-007fb000 rw-p 00002000 08:05 62869      /lib/tls/i686/cmov/libutil-2.10.1.so
00904000-00906000 r-xp 00000000 08:05 36763      /usr/lib/libXau.so.6.0.0
00906000-00907000 r--p 00001000 08:05 36763      /usr/lib/libXau.so.6.0.0
00907000-00908000 rw-p 00002000 08:05 36763      /usr/lib/libXau.so.6.0.0
009d9000-009e6000 r-xp 00000000 08:05 415300     /usr/lib/libolgx.so.3.2.4
009e6000-009e7000 r--p 0000c000 08:05 415300     /usr/lib/libolgx.so.3.2.4
009e7000-009e8000 rw-p 0000d000 08:05 415300     /usr/lib/libolgx.so.3.2.4
00a66000-00a81000 r-xp 00000000 08:05 11640      /lib/ld-2.10.1.so
00a81000-00a82000 r--p 0001a000 08:05 11640      /lib/ld-2.10.1.so
00a82000-00a83000 rw-p 0001b000 08:05 11640      /lib/ld-2.10.1.so
00c82000-00dac000 r-xp 00000000 08:05 24027      /usr/lib/libX11.so.6.2.0
00dac000-00dad000 ---p 0012a000 08:05 24027      /usr/lib/libX11.so.6.2.0
00dad000-00dae000 r--p 0012a000 08:05 24027      /usr/lib/libX11.so.6.2.0
00dae000-00db0000 rw-p 0012b000 08:05 24027      /usr/lib/libX11.so.6.2.0
00db0000-00db1000 rw-p 00000000 00:00 0 
00dd2000-00dd4000 r-xp 00000000 08:05 35444      /lib/tls/i686/cmov/libdl-2.10.1.so
00dd4000-00dd5000 r--p 00001000 08:05 35444      /lib/tls/i686/cmov/libdl-2.10.1.so
00dd5000-00dd6000 rw-p 00002000 08:05 35444      /lib/tls/i686/cmov/libdl-2.10.1.so
00eed000-00eee000 r-xp 00000000 00:00 0          [vdso]
00f40000-00f49000 r-xp 00000000 08:05 45920      /usr/lib/libXcursor.so.1.0.2
00f49000-00f4a000 r--p 00008000 08:05 45920      /usr/lib/libXcursor.so.1.0.2
00f4a000-00f4b000 rw-p 00009000 08:05 45920      /usr/lib/libXcursor.so.1.0.2
00fa0000-00fc4000 r-xp 00000000 08:05 35546      /lib/tls/i686/cmov/libm-2.10.1.so
00fc4000-00fc5000 r--p 00023000 08:05 35546      /lib/tls/i686/cmov/libm-2.10.1.so
00fc5000-00fc6000 rw-p 00024000 08:05 35546      /lib/tls/i686/cmov/libm-2.10.1.so
08048000-0806a000 r-xp 00000000 08:03 21728      /media/0D88EBF000AA1675/programs/data_view/data_view
0806a000-0806b000 r--p 00021000 08:03 21728      /media/0D88EBF000AA1675/programs/data_view/data_view
0806b000-0806c000 rw-p 00022000 08:03 21728      /media/0D88EBF000AA1675/programs/data_view/data_view
0806c000-081f1000 rw-p 00000000 00:00 0          [heap]
b7500000-b7521000 rw-p 00000000 00:00 0 
b7521000-b7600000 ---p 00000000 00:00 0 
b76ee000-b76f2000 rw-p 00000000 00:00 0 
b7713000-b7715000 rw-p 00000000 00:00 0 
bfc21000-bfc36000 rw-p 00000000 00:00 0          [stack]
Aborted

So hope you can help me, because I saw that this bug is on some debian based platforms. The program works on Mandriva, but I want to use it on distant ubuntu computer.

---

