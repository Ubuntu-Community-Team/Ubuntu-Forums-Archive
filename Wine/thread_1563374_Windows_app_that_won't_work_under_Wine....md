---
title: "Windows app that won't work under Wine..."
date: 2010-08-29
forum: Wine
---

### Post by Baldrick_NZ on 2010-08-29
Or PlayOnLinux either...

I'm a radio enthusiast who uses Direttore ([www.mixtime.com](www.mixtime.com)) for radio automation. Once wmp has been successfully installed using Wine, I try to install Direttore. All progresses well until it tries to register, when it hangs for a while then comes back stating that the dll 'amp3dj.ocx' isn't found. I look under syst32 folder (in wine) and its there. I've even copied the amp3dj from and XP os and copied it across into wine, but Direttore still doesn't recognise that amp3dj is actually there.

Any help to sort this would be much appreciated!

It's the only reason Windows still has a presense on my PC, so if I can get this app going under Ubuntu I can reclaim valuable hard drive space... :D Ahhh, to be finally windows free...

Thanks again.

---

### Post by Tony Flury on 2010-08-30
I think for ocx files you need to register them in the Wine registry.

Try using the regsvr command line app.


It appears to be an already reported bug in Wine

Bug Report :
[http://archives.free.net.ph/message/20100622.005803.844a8a9f.en.html](http://archives.free.net.ph/message/20100622.005803.844a8a9f.en.html)

Possible solution : ?
[http://archives.free.net.ph/message/20100818.093023.02c41dd4.en.html](http://archives.free.net.ph/message/20100818.093023.02c41dd4.en.html)

---

### Post by Baldrick_NZ on 2010-08-30
> **Tony Flury said:**
> I think for ocx files you need to register them in the Wine registry.

Try using the regsvr command line app.


thanks for your reply Tony.

So would that be : '$sudo apt-get install regsvr'?
And then how would I register the file using regsvr?

Pardon my ignorance, I'm not much used to working with the command line..
 
Cheers.

EDIT: or would: '$ wine regsvr32 amp3dj.ocx' be more like it in terminal?

---

### Post by dodle on 2010-08-30
Try:
```
regsvr32 amp3dj.ocx
```

If that doesn't work, try:
```
wine regsvr32 amp3dj.ocx
```

---

### Post by Baldrick_NZ on 2010-09-01
> **dodle said:**
> Try:
```
regsvr32 amp3dj.ocx
```

If that doesn't work, try:
```
wine regsvr32 amp3dj.ocx
```

So, this is what I get when I try either of these commands (check supplied image)...

It looks to me like regsvr32 can't see it, but as you can see it's clearly there. 

What am I doing wrong? How can I resolve this?

Thanks again for all your help!

---

### Post by Baldrick_NZ on 2010-09-01
I restarted my PC, and relaunced Direttore, and while the app was hanging (while registering the amp3dj.ocx) I got this... I'm unsure what it all means, but maybe someone else does. I ran the command 3 times while it was hanging..

[HTML]baldrick@baldrick-desktop:~$ wine regsvr32 amp3dj.ocx
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bca27e4 "loader.c: loader_section" wait timed out in thread 0032, blocked by 0031, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34fdd
baldrick@baldrick-desktop:~$ wine regsvr32 amp3dj.ocx
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bca27e4 "loader.c: loader_section" wait timed out in thread 0038, blocked by 0037, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34fdd
baldrick@baldrick-desktop:~$ wine regsvr32 amp3dj.ocx
wine: Unhandled page fault on read access to 0x0045200a at address 0x6830b1c0 (thread 000d), starting debugger...
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bca27e4 "loader.c: loader_section" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)
Unhandled exception: page fault on read access to 0x0045200a in 32-bit code (0x6830b1c0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6830b1c0 ESP:0033f7b0 EBP:0033f848 EFLAGS:00210297(  R- --  I S -A-P-C)
 EAX:00451ffe EBX:68317ff4 ECX:0000f230 EDX:0000fe95
 ESI:000013c4 EDI:00000000
Stack dump:
0x0033f7b0:  00440b54 004470f8 683074d0 0033f824
0x0033f7c0:  0012f480 0000001b 00000000 00000000
0x0033f7d0:  680088cd 68126f65 0033f7f8 6800896e
0x0033f7e0:  00000033 7bc99ff4 0033f848 7bc43de1
0x0033f7f0:  00440b54 0000467f 0012f480 0000b4ad
0x0033f800:  0012f48d 003a0001 0012f3c8 00142210
Backtrace:
=>0 0x6830b1c0 in winemenubuilder (+0xb1c0) (0x0033f848)
  1 0x6830cbd3 in winemenubuilder (+0xcbd2) (0x0033f938)
  2 0x6830e7cc WinMain+0x1cb() in winemenubuilder (0x0033fdd8)
  3 0x6830f8d4 main+0xa3() in winemenubuilder (0x0033fe58)
  4 0x6830f81c in winemenubuilder (+0xf81b) (0x0033fea8)
  5 0x7b858534 in kernel32 (+0x48533) (0x0033fee8)
  6 0x7bc6f584 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc6f750 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4b0aa in ntdll (+0x3b0a9) (0x0033ffe8)
0x6830b1c0: movzwl	0xc(%eax),%edx
Modules:
Module	Address			Debug info	Name (62 modules)
ELF	20000000-20014000	Deferred        lz32<elf>
  \-PE	20010000-20014000	\               lz32
ELF	28830000-28849000	Deferred        version<elf>
  \-PE	28840000-28849000	\               version
ELF	68000000-6813b000	Export          libwine.so.1
ELF	6813b000-68295000	Deferred        libc.so.6
ELF	68295000-68299000	Deferred        libdl.so.2
ELF	68299000-682bf000	Deferred        libm.so.6
ELF	682bf000-682c7000	Deferred        libnss_compat.so.2
ELF	682c7000-682de000	Deferred        libnsl.so.1
ELF	682de000-682e8000	Deferred        libnss_nis.so.2
ELF	682e8000-682f4000	Deferred        libnss_files.so.2
ELF	682f4000-68319000	Export          winemenubuilder<elf>
  \-PE	68300000-68319000	\               winemenubuilder
ELF	68319000-684ad000	Deferred        shell32<elf>
  \-PE	68330000-684ad000	\               shell32
ELF	684ad000-685bc000	Deferred        user32<elf>
  \-PE	684c0000-685bc000	\               user32
ELF	685bc000-6862d000	Deferred        rpcrt4<elf>
  \-PE	685d0000-6862d000	\               rpcrt4
ELF	6862d000-686fb000	Deferred        comctl32<elf>
  \-PE	68640000-686fb000	\               comctl32
ELF	686fb000-687f7000	Deferred        ole32<elf>
  \-PE	68710000-687f7000	\               ole32
ELF	687f7000-6880c000	Deferred        libz.so.1
ELF	6880c000-6883c000	Deferred        libfontconfig.so.1
ELF	6883c000-68863000	Deferred        libexpat.so.1
ELF	68863000-6886c000	Deferred        libsm.so.6
ELF	6886c000-68885000	Deferred        libice.so.6
ELF	68885000-68895000	Deferred        libxext.so.6
ELF	68895000-689b2000	Deferred        libx11.so.6
ELF	689b2000-689b7000	Deferred        libuuid.so.1
ELF	689b7000-689d1000	Deferred        libxcb.so.1
ELF	689d1000-689d5000	Deferred        libxau.so.6
ELF	689d5000-689db000	Deferred        libxdmcp.so.6
ELF	689db000-689fc000	Deferred        imm32<elf>
  \-PE	689e0000-689fc000	\               imm32
ELF	689fc000-68a02000	Deferred        libxxf86vm.so.1
ELF	68a02000-68a0c000	Deferred        libxrender.so.1
ELF	68a0c000-68a14000	Deferred        libxrandr.so.2
ELF	68a14000-68a18000	Deferred        libxcomposite.so.1
ELF	68a18000-68a22000	Deferred        libxcursor.so.1
ELF	68a22000-68a55000	Deferred        uxtheme<elf>
  \-PE	68a30000-68a55000	\               uxtheme
ELF	6af80000-6afdf000	Deferred        shlwapi<elf>
  \-PE	6af90000-6afdf000	\               shlwapi
ELF	70956000-7096f000	Deferred        libpthread.so.0
ELF	70ab5000-70b0e000	Deferred        advapi32<elf>
  \-PE	70ac0000-70b0e000	\               advapi32
ELF	71b6d000-71b71000	Deferred        libxinerama.so.1
ELF	71d22000-71d3f000	Deferred        ld-linux.so.2
ELF	765b3000-765b9000	Deferred        libxfixes.so.3
ELF	79ba6000-79c45000	Deferred        winex11<elf>
  \-PE	79bb0000-79c45000	\               winex11
ELF	7b534000-7b5aa000	Deferred        libfreetype.so.6
ELF	7b800000-7b93a000	Export          kernel32<elf>
  \-PE	7b810000-7b93a000	\               kernel32
ELF	7bc00000-7bcb6000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb6000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c243000-7c2cd000	Deferred        gdi32<elf>
  \-PE	7c250000-7c2cd000	\               gdi32
Threads:
process  tid      prio (all id:s are in hex)
00000008 regsvr32.exe
	0000001f    0
	00000009    0
0000000c (D) C:\windows\system32\winemenubuilder.exe
	0000000d    0 <==
0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
0000001b explorer.exe
	0000001c    0
Backtrace:
=>0 0x6830b1c0 in winemenubuilder (+0xb1c0) (0x0033f848)
  1 0x6830cbd3 in winemenubuilder (+0xcbd2) (0x0033f938)
  2 0x6830e7cc WinMain+0x1cb() in winemenubuilder (0x0033fdd8)
  3 0x6830f8d4 main+0xa3() in winemenubuilder (0x0033fe58)
  4 0x6830f81c in winemenubuilder (+0xf81b) (0x0033fea8)
  5 0x7b858534 in kernel32 (+0x48533) (0x0033fee8)
  6 0x7bc6f584 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc6f750 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4b0aa in ntdll (+0x3b0a9) (0x0033ffe8)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34fdd
baldrick@baldrick-desktop:~$[/HTML]

---

### Post by ronnielsen1 on 2010-09-01
I'm not sure if these will be equivalent to the program you're trying to run but have you tried any of these native apps?

[http://www.rivendellaudio.org/](http://www.rivendellaudio.org/)

[http://6head.blogspot.com/2008/12/radio-edit-start-your-own-open-source_06.html](http://6head.blogspot.com/2008/12/radio-edit-start-your-own-open-source_06.html)

[http://sourceforge.net/projects/rrabuntu/](http://sourceforge.net/projects/rrabuntu/)

---

### Post by Baldrick_NZ on 2010-09-02
> **ronnielsen1 said:**
> I'm not sure if these will be equivalent to the program you're trying to run but have you tried any of these native apps?

[http://www.rivendellaudio.org/](http://www.rivendellaudio.org/)

[http://6head.blogspot.com/2008/12/radio-edit-start-your-own-open-source_06.html](http://6head.blogspot.com/2008/12/radio-edit-start-your-own-open-source_06.html)

[http://sourceforge.net/projects/rrabuntu/](http://sourceforge.net/projects/rrabuntu/)

Thanks for that Ronnie,

I guess I like the simplicity of this app, and to change means having to completely re-educate myself with a new app isn't an attractive proposition. lol

It also helps my education regarding Ubuntu, how to make things work.

---

### Post by Baldrick_NZ on 2010-09-14
Ok, so here's what I get using 
```
wine regsvr32 amp3dj.ocx
```

baldrick@baldrick-desktop:~$ wine regsvr32 amp3dj.ocx
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bca27e4 "loader.c: loader_section" wait timed out in thread 001b, blocked by 0009, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34fdd


Any ideas? Thanks for all your help so far..

---

