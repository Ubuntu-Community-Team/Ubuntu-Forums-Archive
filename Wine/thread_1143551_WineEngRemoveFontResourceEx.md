---
title: "WineEngRemoveFontResourceEx"
date: 2009-04-30
forum: Wine
---

### Post by Ladgalen on 2009-04-30
Hello

I have just installed Juanty Jackalope.

I am trying to install chemdraw with wine version wine-1.1.20

When I do wine autorun.exe on the cdrom a pop up appears but within the pop up there is nothing. When I close the pop up I get the following message 3 times :

fixme:font:WineEngRemoveFontResourceEx :stub

I will be happy if you can help me !

Thanks

---

### Post by asdfoo on 2009-04-30
> **Ladgalen said:**
> Hello

I have just installed Juanty Jackalope.

I am trying to install chemdraw with wine version wine-1.1.20

When I do wine autorun.exe on the cdrom a pop up appears but within the pop up there is nothing. When I close the pop up I get the following message 3 times :

fixme:font:WineEngRemoveFontResourceEx :stub

I will be happy if you can help me !

Thanks


Hello, the topic you have made for this thread is not related.

According to the AppDB this application uses .NET2, so you should use winetricks to install that before running the installer.

from a terminal:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks dotnet20

Then you may have to run the setup program directly instead of using the autorun program.

---

### Post by Ladgalen on 2009-04-30
Thanks for your help. I did what you say but it does not work

I have several time this message when I execute winetricks :
```
fixme:powrprof:DllMain (0x7e540000, 1, (nil)) not fully implemented
```

Moreover, I do not find an install.exe on the cdrom ... now if I load the autorun.exe with wine I get : 

```
fixme:powrprof:DllMain (0x7e540000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
```

And when I close the pop up :
```
fixme:powrprof:DllMain (0x7e540000, 0, 0x1) not fully implemented
```

I have installed it on windows. If I run it from ubuntu I get that :

```

wine ChemDraw.exe
fixme:powrprof:DllMain (0x7e550000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
err:module:import_dll Library MSVCP70.dll (which is needed by L"Z:\\winXP\\Program Files\\CambridgeSoft\\ChemOffice2004\\ChemDraw\\ChemDraw.exe") not found
err:module:import_dll Library MSVCR70.dll (which is needed by L"Z:\\winXP\\Program Files\\CambridgeSoft\\ChemOffice2004\\ChemDraw\\ChemDraw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\winXP\\Program Files\\CambridgeSoft\\ChemOffice2004\\ChemDraw\\ChemDraw.exe" failed, status c0000135
```

And it does not work.

---

### Post by Ladgalen on 2009-04-30
I add the two missing dll in drive_c/windows/system32 and I run the program installed on the winXP partitions :

```

wine ChemDraw.exe 
fixme:powrprof:DllMain (0x7e540000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
wine: Unhandled page fault on read access to 0x00000000 at address 0x6ba850 (thread 0009), starting debugger...
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x006ba850).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:006ba850 ESP:0032fca4 EBP:7b860e80 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:0084a264 ECX:00000031 EDX:00000001
 ESI:800401f3 EDI:0084a0a8
Stack dump:
0x0032fca4:  00000000 006bb070 0084a0cc 0000000a
0x0032fcb4:  0032fd7c 0032fcf4 006bb5b6 0032fcd0
0x0032fcc4:  0000000a 0032fd7c 00000000 00000000
0x0032fcd4:  00000000 00000000 00000000 00396ebd
0x0032fce4:  003cdfb0 ffffffff 00391194 3b32fb58
0x0032fcf4:  00400000 006bb730 00113ef3 0032fd7c
Backtrace:
=>0 0x006ba850 in chemdraw (+0x2ba850) (0x7b860e80)
  1 0x758938ec (0x83e58955)
  2 0x00000000 (0x00000000)
0x006ba850: movb	0x0(%eax),%cl
Modules:
Module	Address			Debug info	Name (85 modules)
PE	  390000-  3e4000	Deferred        msvcr70
PE	  400000-  979000	Export          chemdraw
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c080000-7c0f7000	Deferred        msvcp70
ELF	7dbc5000-7dbde000	Deferred        spoolss<elf>
  \-PE	7dbd0000-7dbde000	\               spoolss
ELF	7dbde000-7dbfc000	Deferred        localspl<elf>
  \-PE	7dbe0000-7dbfc000	\               localspl
ELF	7dbfc000-7dc65000	Deferred        libgcrypt.so.11
ELF	7dc65000-7dc77000	Deferred        libtasn1.so.3
ELF	7dc77000-7dc8d000	Deferred        libresolv.so.2
ELF	7dc8d000-7dc96000	Deferred        libkrb5support.so.0
ELF	7dc96000-7dd28000	Deferred        libkrb5.so.3
ELF	7e08c000-7e090000	Deferred        libgpg-error.so.0
ELF	7e090000-7e0b4000	Deferred        libk5crypto.so.3
ELF	7e0b4000-7e151000	Deferred        libgnutls.so.26
ELF	7e151000-7e17c000	Deferred        libgssapi_krb5.so.2
ELF	7e17c000-7e1b3000	Deferred        libcups.so.2
ELF	7e1c7000-7e2ae000	Deferred        oleaut32<elf>
  \-PE	7e1e0000-7e2ae000	\               oleaut32
ELF	7e2ae000-7e2e4000	Deferred        winspool<elf>
  \-PE	7e2c0000-7e2e4000	\               winspool
ELF	7e2e4000-7e396000	Deferred        comdlg32<elf>
  \-PE	7e2f0000-7e396000	\               comdlg32
ELF	7e396000-7e3be000	Deferred        oledlg<elf>
  \-PE	7e3a0000-7e3be000	\               oledlg
ELF	7e3e2000-7e44f000	Deferred        rpcrt4<elf>
  \-PE	7e3f0000-7e44f000	\               rpcrt4
ELF	7e44f000-7e548000	Deferred        ole32<elf>
  \-PE	7e470000-7e548000	\               ole32
ELF	7e571000-7e5a4000	Deferred        uxtheme<elf>
  \-PE	7e580000-7e5a4000	\               uxtheme
ELF	7e5a4000-7e5ad000	Deferred        libxcursor.so.1
ELF	7e5ad000-7e5b2000	Deferred        libxfixes.so.3
ELF	7e5b2000-7e5b6000	Deferred        libxcomposite.so.1
ELF	7e5b6000-7e5be000	Deferred        libxrandr.so.2
ELF	7e5be000-7e5c8000	Deferred        libxrender.so.1
ELF	7e5c8000-7e5ce000	Deferred        libxxf86vm.so.1
ELF	7e5ce000-7e5d1000	Deferred        libxinerama.so.1
ELF	7e5d1000-7e5f2000	Deferred        imm32<elf>
  \-PE	7e5e0000-7e5f2000	\               imm32
ELF	7e5f2000-7e5f7000	Deferred        libxdmcp.so.6
ELF	7e5f7000-7e611000	Deferred        libxcb.so.1
ELF	7e611000-7e700000	Deferred        libx11.so.6
ELF	7e700000-7e710000	Deferred        libxext.so.6
ELF	7e710000-7e728000	Deferred        libice.so.6
ELF	7e728000-7e731000	Deferred        libsm.so.6
ELF	7e734000-7e738000	Deferred        libkeyutils.so.1
ELF	7e741000-7e745000	Deferred        libcom_err.so.2
ELF	7e745000-7e7e1000	Deferred        winex11<elf>
  \-PE	7e750000-7e7e1000	\               winex11
ELF	7e839000-7e860000	Deferred        libexpat.so.1
ELF	7e860000-7e88d000	Deferred        libfontconfig.so.1
ELF	7e8a1000-7e8b7000	Deferred        libz.so.1
ELF	7e8b7000-7e92e000	Deferred        libfreetype.so.6
ELF	7e92e000-7e932000	Deferred        libxau.so.6
ELF	7e964000-7ea2d000	Deferred        comctl32<elf>
  \-PE	7e970000-7ea2d000	\               comctl32
ELF	7ea2d000-7ea83000	Deferred        advapi32<elf>
  \-PE	7ea40000-7ea83000	\               advapi32
ELF	7ea83000-7eb24000	Deferred        gdi32<elf>
  \-PE	7ea90000-7eb24000	\               gdi32
ELF	7eb24000-7ec70000	Deferred        user32<elf>
  \-PE	7eb40000-7ec70000	\               user32
ELF	7ec70000-7ecce000	Deferred        shlwapi<elf>
  \-PE	7ec80000-7ecce000	\               shlwapi
ELF	7ecce000-7ee58000	Deferred        shell32<elf>
  \-PE	7ece0000-7ee58000	\               shell32
ELF	7ee58000-7ee6c000	Deferred        shfolder<elf>
  \-PE	7ee60000-7ee6c000	\               shfolder
ELF	7ef96000-7efa2000	Deferred        libnss_files.so.2
ELF	7efa2000-7efad000	Deferred        libnss_nis.so.2
ELF	7efad000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff2000	Deferred        libuuid.so.1
ELF	b7c75000-b7c7e000	Deferred        libnss_compat.so.2
ELF	b7c7f000-b7c83000	Deferred        libdl.so.2
ELF	b7c83000-b7de6000	Deferred        libc.so.6
ELF	b7de7000-b7e00000	Deferred        libpthread.so.0
ELF	b7e14000-b7f4f000	Deferred        libwine.so.1
ELF	b7f51000-b7f6f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\winXP\Program Files\CambridgeSoft\ChemOffice2004\ChemDraw\ChemDraw.exe
	00000020    0
	0000001f    0
	00000009    0 <==
0000000c 
	0000001a    0
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	0000001c    0
	0000001b    0
	00000019    0
	00000018    0
0000001d 
	0000001e    0
00000021 
	00000026    0
	00000025    0
	00000024    0
	00000023    0
	00000022    0
Backtrace:
=>0 0x006ba850 in chemdraw (+0x2ba850) (0x7b860e80)
  1 0x758938ec (0x83e58955)
  2 0x00000000 (0x00000000)

fixme:powrprof:DllMain (0x7e540000, 0, 0x1) not fully implemented

```

---

### Post by asdfoo on 2009-04-30
You should install the application in Wine... by looking further at the contents for the real installer/setup.

installing in Windows is not supported.

---

### Post by Ladgalen on 2009-04-30
Thanks a lot !!!!!!!

It works. The setup in Installers is called Chem3D.exe thus I thought it was not the one I needed.

Thanks again

---

### Post by molder on 2010-02-25
I had to run sh winetricks gdiplus and then ChemDraw 11 worked!

---

