---
title: "Unable to mount/read Mac-only game in Basiliskii"
date: 2008-05-28
forum: Virtualisation
---

### Post by Bataille23 on 2008-05-28
Okay, so here's the deal: I have Mac OS running beautifully on BasiliskII, which I installed for the sole purpose of playing this game. However, I am unable to mount (or hmount, for that matter) the CD, and my patience is quickly wearing thin. Does anyone know how one might go about mounting a CD-ROM game on a laptop with AMD x86-64 arch? I'm having no problem with the Mac OS itself, although it should be noted that I did not have to use an HFS-formatted CD-ROM to install the OS itself (the files were all on my HD). I contemplated that possibility that my CD/DVD-ROM hardware was just incapable of reading an HFS CD, but then I found that I was able to get some (very cryptic) ouput from opening /dev/scd0 via xhfs (hfs' GUI). Here's the output, although I doubt it will shine any light on my problem:

```

*** glibc detected *** xhfs: munmap_chunk(): invalid pointer: 0x0000000000883e00 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x7f3f4f021d46]
xhfs[0x4030c9]
xhfs[0x40429d]
/usr/lib/libtcl8.4.so.0(TclInvokeStringCommand+0x77)[0x7f3f4fcd9847]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0[0x7f3f4fd01ff2]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x7f3f4fd0023e]
/usr/lib/libtcl8.4.so.0(TclObjInterpProc+0x202)[0x7f3f4fd30232]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0[0x7f3f4fd01ff2]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x7f3f4fd0023e]
/usr/lib/libtcl8.4.so.0(TclObjInterpProc+0x202)[0x7f3f4fd30232]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0[0x7f3f4fd01ff2]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x7f3f4fd0023e]
/usr/lib/libtcl8.4.so.0(TclObjInterpProc+0x202)[0x7f3f4fd30232]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0[0x7f3f4fd01ff2]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x7f3f4fd0023e]
/usr/lib/libtcl8.4.so.0(Tcl_EvalObjEx+0xeb)[0x7f3f4fcdb92b]
/usr/lib/libtk8.4.so.0[0x7f3f4ffcbcc5]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0(Tcl_EvalObjv+0xdf)[0x7f3f4fcdabff]
/usr/lib/libtcl8.4.so.0(Tcl_EvalObjEx+0x1f9)[0x7f3f4fcdba39]
/usr/lib/libtcl8.4.so.0(Tcl_UplevelObjCmd+0x121)[0x7f3f4fd2fdd1]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0[0x7f3f4fd01ff2]
/usr/lib/libtcl8.4.so.0(TclCompEvalObj+0x9e)[0x7f3f4fd0023e]
/usr/lib/libtcl8.4.so.0(TclObjInterpProc+0x202)[0x7f3f4fd30232]
/usr/lib/libtcl8.4.so.0(TclEvalObjvInternal+0x2f6)[0x7f3f4fcda9b6]
/usr/lib/libtcl8.4.so.0(Tcl_EvalEx+0x39d)[0x7f3f4fcdb5dd]
/usr/lib/libtk8.4.so.0(Tk_BindEvent+0x706)[0x7f3f4ffa2a56]
/usr/lib/libtk8.4.so.0(TkBindEventProc+0x17f)[0x7f3f4ffa856f]
/usr/lib/libtk8.4.so.0(Tk_HandleEvent+0x417)[0x7f3f4ffaf767]
/usr/lib/libtk8.4.so.0[0x7f3f4ffaff7c]
/usr/lib/libtcl8.4.so.0(Tcl_ServiceEvent+0x74)[0x7f3f4fd260a4]
/usr/lib/libtcl8.4.so.0(Tcl_DoOneEvent+0x75)[0x7f3f4fd26315]
/usr/lib/libtk8.4.so.0(Tk_MainLoop+0x18)[0x7f3f4ffb0018]
/usr/lib/libtk8.4.so.0(Tk_MainEx+0x36e)[0x7f3f4ffbbede]
xhfs[0x401dcd]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f3f4efc81c4]
xhfs[0x401ca9]
======= Memory map: ========
00400000-00419000 r-xp 00000000 08:01 12109620                           /usr/bin/xhfs
00618000-00623000 rw-p 00018000 08:01 12109620                           /usr/bin/xhfs
00623000-008cb000 rw-p 00623000 00:00 0                                  [heap]
40d6c000-40d6d000 ---p 40d6c000 00:00 0 
40d6d000-4156d000 rw-p 40d6d000 00:00 0 
7f3f4df61000-7f3f4df6e000 r-xp 00000000 08:01 12435512                   /lib/libgcc_s.so.1
7f3f4df6e000-7f3f4e16e000 ---p 0000d000 08:01 12435512                   /lib/libgcc_s.so.1
7f3f4e16e000-7f3f4e16f000 rw-p 0000d000 08:01 12435512                   /lib/libgcc_s.so.1
7f3f4e16f000-7f3f4e174000 r-xp 00000000 08:01 12109395                   /usr/lib/libXfixes.so.3.1.0
7f3f4e174000-7f3f4e373000 ---p 00005000 08:01 12109395                   /usr/lib/libXfixes.so.3.1.0
7f3f4e373000-7f3f4e374000 rw-p 00004000 08:01 12109395                   /usr/lib/libXfixes.so.3.1.0
7f3f4e374000-7f3f4e37d000 r-xp 00000000 08:01 12108502                   /usr/lib/libXrender.so.1.3.0
7f3f4e37d000-7f3f4e57c000 ---p 00009000 08:01 12108502                   /usr/lib/libXrender.so.1.3.0
7f3f4e57c000-7f3f4e57d000 rw-p 00008000 08:01 12108502                   /usr/lib/libXrender.so.1.3.0
7f3f4e57d000-7f3f4e586000 r-xp 00000000 08:01 12108949                   /usr/lib/libXcursor.so.1.0.2
7f3f4e586000-7f3f4e786000 ---p 00009000 08:01 12108949                   /usr/lib/libXcursor.so.1.0.2
7f3f4e786000-7f3f4e787000 rw-p 00009000 08:01 12108949                   /usr/lib/libXcursor.so.1.0.2
7f3f4e787000-7f3f4e78c000 r-xp 00000000 08:01 12109389                   /usr/lib/libXdmcp.so.6.0.0
7f3f4e78c000-7f3f4e98b000 ---p 00005000 08:01 12109389                   /usr/lib/libXdmcp.so.6.0.0
7f3f4e98b000-7f3f4e98c000 rw-p 00004000 08:01 12109389                   /usr/lib/libXdmcp.so.6.0.0
7f3f4e98c000-7f3f4e98e000 r-xp 00000000 08:01 12109378                   /usr/lib/libXau.so.6.0.0
7f3f4e98e000-7f3f4eb8d000 ---p 00002000 08:01 12109378                   /usr/lib/libXau.so.6.0.0
7f3f4eb8d000-7f3f4eb8e000 rw-p 00001000 08:01 12109378                   /usr/lib/libXau.so.6.0.0
7f3f4eb8e000-7f3f4eba9000 r-xp 00000000 08:01 12108582                   /usr/lib/libxcb.so.1.0.0
7f3f4eba9000-7f3f4eda8000 ---p 0001b000 08:01 12108582                   /usr/lib/libxcb.so.1.0.0
7f3f4eda8000-7f3f4eda9000 rw-p 0001a000 08:01 12108582                   /usr/lib/libxcb.so.1.0.0
7f3f4eda9000-7f3f4edaa000 r-xp 00000000 08:01 12108595                   /usr/lib/libxcb-xlib.so.0.0.0
7f3f4edaa000-7f3f4efa9000 ---p 00001000 08:01 12108595                   /usr/lib/libxcb-xlib.so.0.0.0
7f3f4efa9000-7f3f4efaa000 rw-p 00000000 08:01 12108595                   /usr/lib/libxcb-xlib.so.0.0.0
7f3f4efaa000-7f3f4f102000 r-xp 00000000 08:01 12435523                   /lib/libc-2.7.so
7f3f4f102000-7f3f4f302000 ---p 00158000 08:01 12435523                   /lib/libc-2.7.so
7f3f4f302000-7f3f4f305000 r--p 00158000 08:01 12435523                   /lib/libc-2.7.so
7f3f4f305000-7f3f4f307000 rw-p 0015b000 08:01 12435523                   /lib/libc-2.7.so
7f3f4f307000-7f3f4f30c000 rw-p 7f3f4f307000 00:00 0 
7f3f4f30c000-7f3f4f38c000 r-xp 00000000 08:01 12435534                   /lib/libm-2.7.so
7f3f4f38c000-7f3f4f58b000 ---p 00080000 08:01 12435534                   /lib/libm-2.7.so
7f3f4f58b000-7f3f4f58d000 rw-p 0007f000 08:01 12435534                   /lib/libm-2.7.so
7f3f4f58d000-7f3f4f5a3000 r-xp 00000000 08:01 12435566                   /lib/libpthread-2.7.so
7f3f4f5a3000-7f3f4f7a3000 ---p 00016000 08:01 12435566                   /lib/libpthread-2.7.so
7f3f4f7a3000-7f3f4f7a5000 rw-p 00016000 08:01 12435566                   /lib/libpthread-2.7.so
7f3f4f7a5000-7f3f4f7a9000 rw-p 7f3f4f7a5000 00:00 0 
7f3f4f7a9000-7f3f4f7ab000 r-xp 00000000 08:01 12435530                   /lib/libdl-2.7.so
7f3f4f7ab000-7f3f4f9ab000 ---p 00002000 08:01 12435530                   /lib/libdl-2.7.so
7f3f4f9ab000-7f3f4f9ad000 rw-p 00002000 08:01 12435530                   /lib/libdl-2.7.so
7f3f4f9ad000-7f3f4faac000 r-xp 00000000 08:01 12108600                   /usr/lib/libX11.so.6.2.0
7f3f4faac000-7f3f4fcab000 ---p 000ff000 08:01 12108600                   /usr/lib/libX11.so.6.2.0
7f3f4fcab000-7f3f4fcb0000 rw-p 000fe000 08:01 12108600                   /usr/lib/libX11.so.6.2.0
7f3f4fcb0000-7f3f4fd6a000 r-xp 00000000 08:01 12111184                   /usr/lib/libtcl8.4.so.0
7f3f4fd6a000-7f3f4ff6a000 ---p 000ba000 08:01 12111184                   /usr/lib/libtcl8.4.so.0
7f3f4ff6a000-7f3f4ff77000 rw-p 000ba000 08:01 12111184                   /usr/lib/libtcl8.4.so.0
7f3f4ff77000-7f3f4ff78000 rw-p 7f3f4ff77000 00:00 0 
7f3f4ff78000-7f3f5005f000 r-xp 00000000 08:01 12111186                   /usr/lib/libtk8.4.so.0
7f3f5005f000-7f3f5025f000 ---p 000e7000 08:01 12111186                   /usr/lib/libtk8.4.so.0
7f3f5025f000-7f3f50273000 rw-p 000e7000 08:01 12111186                   /usr/lib/libtk8.4.so.0
7f3f50273000-7f3f50274000 rw-p 7f3f50273000 00:00 0 
7f3f50274000-7f3f50291000 r-xp 00000000 08:01 12435500                   /lib/ld-2.7.so
7f3f50374000-7f3f503a8000 rw-p 7f3f50374000 00:00 0 
7f3f50431000-7f3f50470000 r--p 00000000 08:01 12173315                   /usr/lib/locale/en_US.utf8/LC_CTYPE
7f3f50470000-7f3f50475000 rw-p 7f3f50470000 00:00 0 
7f3f50486000-7f3f50487000 r--p 00000000 08:01 12173837                   /usr/lib/locale/en_US.utf8/LC_TIME
7f3f50487000-7f3f5048e000 r--s 00000000 08:01 12107850                   /usr/lib/gconv/gconv-modules.cache
7f3f5048e000-7f3f50491000 rw-p 7f3f5048e000 00:00 0 
7f3f50491000-7f3f50493000 rw-p 0001d000 08:01 12435500                   /lib/ld-2.7.so
7fff5847d000-7fff58492000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff584bd000-7fff584bf000 r-xp 7fff584bd000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted
```

ANY help would be GREATLY appreciated. I'm desperate to play this rare, out-of-print(!) game, and I'm beginning to worry that it just won't happen. If it helps at all, I'm running a Gateway MT-series with an AMD Athlon processor. If any additional information would be helpful in solving this, don't hesitate to reply. I will get it up as quickly as I can.

Thanks!

---

### Post by fjgaude on 2008-05-28
I do believe what you are doing is illegal... Mac OS is not permitted to run on other than Apple hardware.

---

### Post by Bataille23 on 2008-05-28
Really?  Is Basilisk illegal, too, then?  If so, I don't see why it's offered in the repositories, since it exists solely to emulate the ppc environment which can run Mac OS (which, btw, is available to download on Apple's very own website)...

I don't mean to have a go at you, but the whole thing is rather stressful and the legalities and technicalities (etc., etc.) of what I'm doing don't even figure in.  At this point, I don't really care whether it's legal or not.  I paid money for the game from Amazon -- who didn't even specify that it was Mac only, btw -- it's out-of-print and has a price to prove it, and I just want to play it.  Mac OS isn't even sold anymore last time I checked, so I don't see the harm in emulating the environment.  I just want an answer to my question.

If anyone else has run the game "Freak Show" (produced by the Louisiana avant-garde quartet, the Residents) and knows if there are any special "tricks" to running it, your feedback would be greatly appreciated.

---

### Post by fjgaude on 2008-05-28
If what you are doing is legal, fine. What I do know is Apple doesn't permit any of it products to be run on other than its own hardware. If it's Apple software it must run on Apple hardware. That's it. Good luck in what you are doing.

---

