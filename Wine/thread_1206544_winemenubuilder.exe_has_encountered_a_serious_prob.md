---
title: "winemenubuilder.exe has encountered a serious problem"
date: 2009-07-07
forum: Wine
---

### Post by Melhisedek on 2009-07-07
This pops out everytime I try to start wine program, even regedit. This is what I get in console:


```
wine: Unhandled page fault on read access to 0x001611f8 at address 0xb7e536e8 (thread 000d), starting debugger...
Unhandled exception: page fault on read access to 0x001611f8 in 32-bit code (0xb7e536e8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7e536e8 ESP:0033f820 EBP:0033f828 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:001611f8 EBX:b7f3aff4 ECX:001611f8 EDX:001611f8
 ESI:001615f8 EDI:001611f8
Stack dump:
0x0033f820:  00140950 00000000 0033f868 b7e88492
0x0033f830:  001611f8 00000400 00000000 7ee56ff4
0x0033f840:  0033f850 01158710 0033f820 0033f800
0x0033f850:  00000000 00000000 001611f8 7ee56ff4
0x0033f860:  00140950 00141410 0033f898 7ee46f82
0x0033f870:  001611f8 0014a0c8 00000000 00000000
Backtrace:
=>0 0xb7e536e8 strnlen+0x58() in libc.so.6 (0x0033f828)
  1 0xb7e88492 fnmatch+0x92() in libc.so.6 (0x0033f868)
  2 0x7ee46f82 in winemenubuilder (+0x6f82) (0x0033f898)
  3 0x7ee49f00 in winemenubuilder (+0x9f00) (0x0033f9a8)
  4 0x7ee4e261 WinMain+0x201() in winemenubuilder (0x0033fe58)
  5 0x7ee4f39d main+0xad() in winemenubuilder (0x0033fed8)
  6 0x7ee4f2e4 in winemenubuilder (+0xf2e4) (0x0033ff08)
  7 0x7b878190 in kernel32 (+0x58190) (0x0033ffe8)
  8 0xb7f75e1d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0xb7e536e8 strnlen+0x58 in libc.so.6: movl	0x0(%edx),%eax
Modules:
Module	Address			Debug info	Name (61 modules)
ELF	7b800000-7b954000	Export          kernel32<elf>
  \-PE	7b820000-7b954000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e25a000-7e280000	Deferred        libpng12.so.0
ELF	7e295000-7e2a9000	Deferred        lz32<elf>
ELF	7e2a9000-7e2c4000	Deferred        version<elf>
ELF	7e432000-7e465000	Deferred        uxtheme<elf>
  \-PE	7e440000-7e465000	\               uxtheme
ELF	7e465000-7e46e000	Deferred        libxcursor.so.1
ELF	7e46e000-7e473000	Deferred        libxfixes.so.3
ELF	7e473000-7e477000	Deferred        libxcomposite.so.1
ELF	7e477000-7e47f000	Deferred        libxrandr.so.2
ELF	7e47f000-7e489000	Deferred        libxrender.so.1
ELF	7e489000-7e48f000	Deferred        libxxf86vm.so.1
ELF	7e48f000-7e492000	Deferred        libxinerama.so.1
ELF	7e492000-7e4b3000	Deferred        imm32<elf>
  \-PE	7e4a0000-7e4b3000	\               imm32
ELF	7e4b3000-7e4b8000	Deferred        libxdmcp.so.6
ELF	7e4b8000-7e4d2000	Deferred        libxcb.so.1
ELF	7e4d2000-7e4d6000	Deferred        libxau.so.6
ELF	7e4d6000-7e4db000	Deferred        libuuid.so.1
ELF	7e4db000-7e5ca000	Deferred        libx11.so.6
ELF	7e5ca000-7e5da000	Deferred        libxext.so.6
ELF	7e5da000-7e5f2000	Deferred        libice.so.6
ELF	7e5f2000-7e5fb000	Deferred        libsm.so.6
ELF	7e610000-7e6ac000	Deferred        winex11<elf>
  \-PE	7e620000-7e6ac000	\               winex11
ELF	7e6de000-7e705000	Deferred        libexpat.so.1
ELF	7e705000-7e732000	Deferred        libfontconfig.so.1
ELF	7e747000-7e75d000	Deferred        libz.so.1
ELF	7e75d000-7e7d4000	Deferred        libfreetype.so.6
ELF	7e7d4000-7e841000	Deferred        rpcrt4<elf>
  \-PE	7e7e0000-7e841000	\               rpcrt4
ELF	7e841000-7e93c000	Deferred        ole32<elf>
  \-PE	7e860000-7e93c000	\               ole32
ELF	7e93c000-7ea05000	Deferred        comctl32<elf>
  \-PE	7e940000-7ea05000	\               comctl32
ELF	7ea05000-7ea5b000	Deferred        advapi32<elf>
  \-PE	7ea10000-7ea5b000	\               advapi32
ELF	7ea5b000-7eafd000	Deferred        gdi32<elf>
  \-PE	7ea70000-7eafd000	\               gdi32
ELF	7eafd000-7ec49000	Deferred        user32<elf>
  \-PE	7eb20000-7ec49000	\               user32
ELF	7ec49000-7eca7000	Deferred        shlwapi<elf>
  \-PE	7ec60000-7eca7000	\               shlwapi
ELF	7eca7000-7ee34000	Deferred        shell32<elf>
  \-PE	7ecc0000-7ee34000	\               shell32
ELF	7ee34000-7ee58000	Export          winemenubuilder<elf>
  \-PE	7ee40000-7ee58000	\               winemenubuilder
ELF	7ee58000-7ee64000	Deferred        libnss_files.so.2
ELF	7ee64000-7ee7d000	Deferred        libnsl.so.1
ELF	7ee7d000-7ee86000	Deferred        libnss_compat.so.2
ELF	7efc5000-7efeb000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7dd8000-b7ddc000	Deferred        libdl.so.2
ELF	b7ddc000-b7f3f000	Export          libc.so.6
ELF	b7f40000-b7f59000	Deferred        libpthread.so.0
ELF	b7f6e000-b80aa000	Export          libwine.so.1
ELF	b80ac000-b80ca000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c (D) C:\windows\system32\winemenubuilder.exe
	0000000d    0 <==
0000000e 
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000018    0
	00000017    0
	00000013    0
	00000012    0
0000001b 
	0000001c    0
Backtrace:
=>0 0xb7e536e8 strnlen+0x58() in libc.so.6 (0x0033f828)
  1 0xb7e88492 fnmatch+0x92() in libc.so.6 (0x0033f868)
  2 0x7ee46f82 in winemenubuilder (+0x6f82) (0x0033f898)
  3 0x7ee49f00 in winemenubuilder (+0x9f00) (0x0033f9a8)
  4 0x7ee4e261 WinMain+0x201() in winemenubuilder (0x0033fe58)
  5 0x7ee4f39d main+0xad() in winemenubuilder (0x0033fed8)
  6 0x7ee4f2e4 in winemenubuilder (+0xf2e4) (0x0033ff08)
  7 0x7b878190 in kernel32 (+0x58190) (0x0033ffe8)
  8 0xb7f75e1d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)

```

---

### Post by cogadh on 2009-07-07
Have you installed anything in Wine yet, or did this start before you could do that?

---

### Post by Melhisedek on 2009-07-08
Strange but it stopped from popping out... It started after I installed Warcraft III on my rig, if it starts again I'll let you know :)

---

### Post by LeChacal on 2009-07-11
I am having the same problem and I just did a clean install of ubuntu 9.04 and I had not installed anything under when it started. I have now installed Firefox and tired to install Office2003. Firefox works fine but when I installed Office2003 I got that error int he middle of the install process, wine never built the menu links for Office which it did for Firefox, and it didn't fully install Office even though Office said that the install was complete. 
The first time I saw the error I had opened up the "Wine Configuration" for the first time to check the version and had not installed anything yet. The other strange thing was when I was looking at the version number on the "About" tab where it should have the version number it says "PACKAGE_STRING" instead.

---

### Post by ackanao on 2009-07-11
Which version of Wine you're using? Wine menu bug is almost fixed with Wine 1.1.25 so it's better to uninstall Wine 1.0.1, delete all Wine menus from "applications.menu" file - goto "**~/.config/menus**" folder, open "applications.menu" file, delete everything related to Wine except:

```

	<Menu>
		<Name>wine-wine</Name>
	</Menu>

```

Goto "**applications-merged**" folder and delete everything related to Wine. Install latest version of Wine and try again...

---

### Post by LeChacal on 2009-07-11
I am/was running Wine 1.1.25 from the wine repositories. I run Jaunty 64bit if that matters. And I tired what you said to do ackanao and nothing changed; the menus are still screwed up, version number still gone, and Office2003 still errors out when I try to install or run it after errored installed.

---

### Post by ackanao on 2009-07-11
I'm sorry to hear that - I'll try to install Office 2003 later today and report back my results

---

### Post by 3base on 2009-07-15
ive got the same prob, same wine but running office2007.
all apps generate this error (eg. utorrent, shrink, notepad), 
deleted menu, no diff, still nogo for launch. 

cherio

---

### Post by kumbayo on 2009-07-15
LeChacal:
The PACKAGE_STRING thing should be fixed by
[http://www.winehq.org/pipermail/wine-cvs/2009-July/057219.html](http://www.winehq.org/pipermail/wine-cvs/2009-July/057219.html)

Melhisedek:
The crash in winemenubuilder should be fixed by
[http://thread.gmane.org/gmane.comp.emulators.wine.patches/69394](http://thread.gmane.org/gmane.comp.emulators.wine.patches/69394)
[http://www.winehq.org/pipermail/wine-cvs/2009-July/057319.html](http://www.winehq.org/pipermail/wine-cvs/2009-July/057319.html)
I got a crash at the same function and i hope this fixes it.

Both problems should be fixed in 1.1.26

As a workaround until then it should be possible to manually create links for the files by running
wine winemenubuilder -w ~/.wine/drive_c/windows/profiles/yourname/Start\ Menu/Programs/YourProgram/YourProgram.lnk
But i do not know if this works with broken winemenubuilder that crashes...

---

### Post by 3base on 2009-07-19
with 1.1.26, 
all green,
go for launch,

taa

---

