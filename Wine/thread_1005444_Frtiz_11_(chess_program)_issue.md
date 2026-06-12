---
title: "Frtiz 11 (chess program) issue"
date: 2008-12-08
forum: Wine
---

### Post by awais_rauf on 2008-12-08
I have been trying to make Fritz 11 running using wine 1.1.6 on Ubuntu Intrepid. I have installed Fritz 11 on wine and can make it run too but when ever i click on a menu Fritz gets unstable and becomes non-responding (zombie).

Command line output is:

```


fixme:win:EnumDisplayDevicesW ((null),0,0x32f674,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x3006c 0x00000000
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -300, std (d/m/y): 1/11/2008, dlt (d/m/y): 1/06/2008
fixme:win:EnumDisplayDevicesW ((null),0,0x32f760,0x00000000), stub!
fixme:xrender:X11DRV_AlphaBlend not a dibsection
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
fixme:dsound:DllCanUnloadNow (void): stub
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
fixme:menu:TrackPopupMenuEx not fully implemented
err:toolbar:TOOLBAR_GetImageListForDrawing bitmap for ID 0, index 0 is not valid, number of bitmaps in imagelist: 0
wine: Unhandled page fault on read access to 0x00000020 at address 0x10077195 (thread 002a), starting debugger...
Unhandled exception: page fault on read access to 0x00000020 in 32-bit code (0x10077195).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:10077195 ESP:0032ea84 EBP:0032eb30 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:0269c050 EDX:782bca20
 ESI:10077190 EDI:0269c050
Stack dump:
0x0032ea84:  10077190 78202cd7 00000002 00000000
0x0032ea94:  08ec89cb 00000121 0269c050 00146758
0x0032eaa4:  0032eb74 00000000 100a1f80 782bdd64
0x0032eab4:  7fffffff 7bc34431 0014c298 0032ec14
0x0032eac4:  7bc26790 7bc33ddf 7bc8a444 00172960
0x0032ead4:  7ffd8000 0032eb74 ed755921 0c6e05d6
Backtrace:
=>1 0x10077195 in sviewnet (+0x77195) (0x0032eb30)
  2 0x782027ad in mfc80 (+0x327ad) (0x0032eb50)
  3 0x78201543 in mfc80 (+0x31543) (0x0032ebb8)
  4 0x78201759 in mfc80 (+0x31759) (0x0032ebdc)
  5 0x781ff883 in mfc80 (+0x2f883) (0x0032ec24)
  6 0x7ed5c42a WINPROC_wrapper+0x1a() in user32 (0x0032ec54)
  7 0x7ed5cb0e WINPROC_wrapper+0x6fe() in user32 (0x0032ec94)
  8 0x7ed61365 in user32 (+0xb1365) (0x0032f164)
  9 0x7ed61f5a in user32 (+0xb1f5a) (0x0032f1a4)
  10 0x7ed24651 in user32 (+0x74651) (0x0032f204)
  11 0x7ed278dd in user32 (+0x778dd) (0x0032f264)
  12 0x7ed27d4a SendMessageW+0x4a() in user32 (0x0032f2a4)
  13 0x7ed20284 in user32 (+0x70284) (0x0032f374)
  14 0x7ed210b3 TrackPopupMenu+0x123() in user32 (0x0032f3b4)
  15 0x7ed2115e TrackPopupMenuEx+0x5e() in user32 (0x0032f3e4)
0x10077195: movl	0x20(%eax),%esi
Modules:
Module	Address			Debug info	Name (142 modules)
PE	  330000-  355000	Deferred        chess32
PE	  360000-  373000	Deferred        device32
PE	  400000-  eaa000	Deferred        chessprogram11
PE	  eb0000- 159c000	Deferred        textures2net
PE	 15a0000- 1646000	Deferred        tbaccessnet
PE	 1650000- 16e1000	Deferred        ode
PE	 2080000- 2468000	Deferred        frameresnet
PE	 2ef0000- 2f90000	Deferred        chessresnet
PE	 34d0000- 3621000	Deferred        fritz 11.engine
PE	10000000-100e7000	Export          sviewnet
PE	39800000-399b2000	Deferred        gdiplus
PE	5d360000-5d36e000	Deferred        mfc80enu
PE	78130000-781cb000	Deferred        msvcr80
PE	781d0000-782df000	Export          mfc80
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c2c5000-7c30f000	Deferred        dsound<elf>
  \-PE	7c2d0000-7c30f000	\               dsound
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7c6b3000-7c71c000	Deferred        libgcrypt.so.11
ELF	7c71c000-7c72e000	Deferred        libtasn1.so.3
ELF	7c72e000-7c760000	Deferred        libcrypt.so.1
ELF	7c760000-7c7fd000	Deferred        libgnutls.so.26
ELF	7c7fd000-7c821000	Deferred        libk5crypto.so.3
ELF	7c821000-7c8b3000	Deferred        libkrb5.so.3
ELF	7c8b3000-7c8dd000	Deferred        libgssapi_krb5.so.2
ELF	7c8dd000-7c913000	Deferred        libcups.so.2
ELF	7c913000-7c948000	Deferred        winspool<elf>
  \-PE	7c920000-7c948000	\               winspool
ELF	7ce7c000-7ce80000	Deferred        libgpg-error.so.0
ELF	7ce80000-7ce89000	Deferred        libkrb5support.so.0
ELF	7d0ba000-7d2ee000	Deferred        sis_dri.so
ELF	7d2ee000-7d34f000	Deferred        libgl.so.1
ELF	7d34f000-7d3e4000	Deferred        opengl32<elf>
  \-PE	7d370000-7d3e4000	\               opengl32
ELF	7d3e4000-7d4f5000	Deferred        wined3d<elf>
  \-PE	7d400000-7d4f5000	\               wined3d
ELF	7de76000-7de85000	Deferred        libgcc_s.so.1
ELF	7de98000-7dea1000	Deferred        libdrm.so.2
ELF	7deb4000-7df0d000	Deferred        ddraw<elf>
  \-PE	7dec0000-7df0d000	\               ddraw
ELF	7df0d000-7df21000	Deferred        wtsapi32<elf>
  \-PE	7df10000-7df21000	\               wtsapi32
ELF	7df48000-7df4c000	Deferred        libkeyutils.so.1
ELF	7df4c000-7df50000	Deferred        libcom_err.so.2
ELF	7df63000-7df77000	Deferred        oleacc<elf>
  \-PE	7df70000-7df77000	\               oleacc
ELF	7dfaa000-7dfdd000	Deferred        uxtheme<elf>
  \-PE	7dfb0000-7dfdd000	\               uxtheme
ELF	7dfdd000-7dff1000	Deferred        midimap<elf>
  \-PE	7dfe0000-7dff1000	\               midimap
ELF	7dff1000-7e008000	Deferred        msacm32<elf>
  \-PE	7e000000-7e008000	\               msacm32
ELF	7e008000-7e00c000	Deferred        libcap.so.1
ELF	7e00c000-7e05c000	Deferred        libpulse.so.0
ELF	7e05c000-7e124000	Deferred        libasound.so.2
ELF	7e134000-7e137000	Deferred        libxdamage.so.1
ELF	7e137000-7e16c000	Deferred        winealsa<elf>
  \-PE	7e140000-7e16c000	\               winealsa
ELF	7e16c000-7e175000	Deferred        libxcursor.so.1
ELF	7e175000-7e17a000	Deferred        libxfixes.so.3
ELF	7e17a000-7e17e000	Deferred        libxcomposite.so.1
ELF	7e17e000-7e185000	Deferred        libxrandr.so.2
ELF	7e185000-7e18f000	Deferred        libxrender.so.1
ELF	7e18f000-7e195000	Deferred        libxxf86vm.so.1
ELF	7e195000-7e198000	Deferred        libxinerama.so.1
ELF	7e198000-7e1b8000	Deferred        imm32<elf>
  \-PE	7e1a0000-7e1b8000	\               imm32
ELF	7e1b8000-7e1bd000	Deferred        libxdmcp.so.6
ELF	7e1bd000-7e1d6000	Deferred        libxcb.so.1
ELF	7e1d6000-7e1d9000	Deferred        libxcb-xlib.so.0
ELF	7e1d9000-7e1dc000	Deferred        libxau.so.6
ELF	7e1dc000-7e2cb000	Deferred        libx11.so.6
ELF	7e2cb000-7e2da000	Deferred        libxext.so.6
ELF	7e2da000-7e2f2000	Deferred        libice.so.6
ELF	7e2f2000-7e2fb000	Deferred        libsm.so.6
ELF	7e2fc000-7e303000	Deferred        libasound_module_pcm_pulse.so
ELF	7e303000-7e30c000	Deferred        librt.so.1
ELF	7e30e000-7e3a6000	Deferred        winex11<elf>
  \-PE	7e320000-7e3a6000	\               winex11
ELF	7e3f8000-7e41f000	Deferred        libexpat.so.1
ELF	7e41f000-7e44c000	Deferred        libfontconfig.so.1
ELF	7e45f000-7e475000	Deferred        libz.so.1
ELF	7e475000-7e4eb000	Deferred        libfreetype.so.6
ELF	7e4fe000-7e52a000	Deferred        ws2_32<elf>
  \-PE	7e510000-7e52a000	\               ws2_32
ELF	7e52a000-7e611000	Deferred        oleaut32<elf>
  \-PE	7e540000-7e611000	\               oleaut32
ELF	7e611000-7e67b000	Deferred        msvcrt<elf>
  \-PE	7e620000-7e67b000	\               msvcrt
ELF	7e67b000-7e795000	Deferred        shell32<elf>
  \-PE	7e690000-7e795000	\               shell32
ELF	7e795000-7e7ef000	Deferred        shlwapi<elf>
  \-PE	7e7a0000-7e7ef000	\               shlwapi
ELF	7e7ef000-7e811000	Deferred        mpr<elf>
  \-PE	7e800000-7e811000	\               mpr
ELF	7e811000-7e860000	Deferred        wininet<elf>
  \-PE	7e820000-7e860000	\               wininet
ELF	7e860000-7e874000	Deferred        avicap32<elf>
  \-PE	7e870000-7e874000	\               avicap32
ELF	7e874000-7e888000	Deferred        libresolv.so.2
ELF	7e888000-7e89b000	Deferred        msimg32<elf>
  \-PE	7e890000-7e89b000	\               msimg32
ELF	7e89b000-7e8ba000	Deferred        iphlpapi<elf>
  \-PE	7e8a0000-7e8ba000	\               iphlpapi
ELF	7e8ba000-7e91f000	Deferred        rpcrt4<elf>
  \-PE	7e8d0000-7e91f000	\               rpcrt4
ELF	7e91f000-7ea28000	Deferred        ole32<elf>
  \-PE	7e940000-7ea28000	\               ole32
ELF	7ea28000-7ea4f000	Deferred        msacm32<elf>
  \-PE	7ea30000-7ea4f000	\               msacm32
ELF	7ea4f000-7ea8a000	Deferred        avifil32<elf>
  \-PE	7ea60000-7ea8a000	\               avifil32
ELF	7ea8a000-7eb4b000	Deferred        comctl32<elf>
  \-PE	7ea90000-7eb4b000	\               comctl32
ELF	7eb4b000-7eb5f000	Deferred        lz32<elf>
  \-PE	7eb50000-7eb5f000	\               lz32
ELF	7eb5f000-7eb78000	Deferred        version<elf>
  \-PE	7eb60000-7eb78000	\               version
ELF	7eb78000-7eba1000	Deferred        msvfw32<elf>
  \-PE	7eb80000-7eba1000	\               msvfw32
ELF	7eba1000-7ebf5000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebf5000	\               advapi32
ELF	7ebf5000-7ec93000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec93000	\               gdi32
ELF	7ec93000-7eddc000	Export          user32<elf>
  \-PE	7ecb0000-7eddc000	\               user32
ELF	7eddc000-7ee6e000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee6e000	\               winmm
ELF	7ef8e000-7ef9a000	Deferred        libnss_files.so.2
ELF	7ef9a000-7efa5000	Deferred        libnss_nis.so.2
ELF	7efa5000-7efbe000	Deferred        libnsl.so.1
ELF	7efbe000-7efc7000	Deferred        libnss_compat.so.2
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	b7c83000-b7c87000	Deferred        libdl.so.2
ELF	b7c87000-b7de5000	Deferred        libc.so.6
ELF	b7de5000-b7dfe000	Deferred        libpthread.so.0
ELF	b7e11000-b7f47000	Deferred        libwine.so.1
ELF	b7f49000-b7f66000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	0000001b    0
	0000001a    0
	00000019    0
	00000009    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000029 (D) C:\Program Files\ChessBase\ChessProgram11\ChessProgram11.exe
	00000035   -1
	00000033   15
	00000031   15
	0000002f    0
	0000002e    0
	0000002b    0
	0000002a    1 <==
Backtrace:
=>1 0x10077195 in sviewnet (+0x77195) (0x0032eb30)
  2 0x782027ad in mfc80 (+0x327ad) (0x0032eb50)
  3 0x78201543 in mfc80 (+0x31543) (0x0032ebb8)
  4 0x78201759 in mfc80 (+0x31759) (0x0032ebdc)
  5 0x781ff883 in mfc80 (+0x2f883) (0x0032ec24)
  6 0x7ed5c42a WINPROC_wrapper+0x1a() in user32 (0x0032ec54)
  7 0x7ed5cb0e WINPROC_wrapper+0x6fe() in user32 (0x0032ec94)
  8 0x7ed61365 in user32 (+0xb1365) (0x0032f164)
  9 0x7ed61f5a in user32 (+0xb1f5a) (0x0032f1a4)
  10 0x7ed24651 in user32 (+0x74651) (0x0032f204)
  11 0x7ed278dd in user32 (+0x778dd) (0x0032f264)
  12 0x7ed27d4a SendMessageW+0x4a() in user32 (0x0032f2a4)
  13 0x7ed20284 in user32 (+0x70284) (0x0032f374)
  14 0x7ed210b3 TrackPopupMenu+0x123() in user32 (0x0032f3b4)
  15 0x7ed2115e TrackPopupMenuEx+0x5e() in user32 (0x0032f3e4)
Terminated


```

Can anyone please help!

---

### Post by carml on 2008-12-15
Hi,me too I tried to install Fritz under Ubuntu using wine,but it didn't install,the solution I found somewhere in the forum (I don't remember who posted it) is to install a SW like VirtualBox,then to create a virtual machine to run a Windows OS.Once you created a virtual machine,you can install there Fritz and all the software for Windows.
There are any prerequisites you have to satisfy:
1. download e.g. Virtualbox for Linux host( from the repository or from the site);
2. you must own a installation CD of the OS you want to install;
3. you must have some free space on your hard disk,where you'll save the virtual hard disk createb by the virtualization software.
Tell me,or the author of the original post if you need more help or explanations. :p

---

### Post by awais_rauf on 2008-12-19
Thanks for reply.

the fritz engine runs perfectly and starts calculating moves
You can perfectly move peaces and play the game

BUT 
Problem arises when you click the main toolbar. This is not only the problem with fritz but also with Chessbase 10. I my opinion this should not be a big issue to fix (for the wine developers).

I don't know about Virtualbox. Can you please tell me how much is the performance difference compared to vmware workstation 6?

---

