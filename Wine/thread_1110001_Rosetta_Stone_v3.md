---
title: "Rosetta Stone v3"
date: 2009-03-29
forum: Wine
---

### Post by gkaykck on 2009-03-29
Hi
when i try to install rosetta stone 3 it will end up suddenly, but it copies the files needed.
after i try use it ill get some flicks on screen but nothing more
the error is
[COLOR="Sienna"]
gkay@LEVEL7:~$ wine '/home/gkay/.wine/dosdevices/c:/Program Files/Rosetta Stone/Rosetta Stone Version 3/RosettaStoneVersion3.exe' 
err:ole:CoGetClassObject class {56fdf344-fd6d-11d0-958a-006097c9a090} not registered
err:ole:CoGetClassObject no class object {56fdf344-fd6d-11d0-958a-006097c9a090} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000000 at address 0x41d591 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0041d591).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0041d591 ESP:0032fd8c EBP:00000007 EFLAGS:00010282(   - 00      - RIS1)
 EAX:80040154 EBX:00000000 ECX:00000000 EDX:00000071
 ESI:004a50a8 EDI:00000000
Stack dump:
0x0032fd8c:  7b868350 00000000 0032ff08 7b8b7ff4
0x0032fd9c:  004a50a8 0032fdb0 0047d1ad 0000000f
0x0032fdac:  0041d5fc 0032fef8 0047d1ce 00000000
0x0032fdbc:  0041e7e5 00400000 00000000 00491310
0x0032fdcc:  ffffffff 0046b6ef 0046b6ff 00400000
0x0032fddc:  7b8b7ff4 0032ff08 0046bda7 00400000
Backtrace:
=>1 0x0041d591 in rosettastoneversion3 (+0x1d591) (0x00000007)
  2 0x00000000 (0x00000000)
0x0041d591: movl	0x0(%edi),%eax
Modules:
Module	Address			Debug info	Name (95 modules)
PE	  400000-  89d000	Export          rosettastoneversion3
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d63b000-7d6a4000	Deferred        libgcrypt.so.11
ELF	7d6a4000-7d6b6000	Deferred        libtasn1.so.3
ELF	7d6b6000-7d753000	Deferred        libgnutls.so.26
ELF	7df55000-7df59000	Deferred        libgpg-error.so.0
ELF	7df59000-7df62000	Deferred        libkrb5support.so.0
ELF	7df62000-7df94000	Deferred        libcrypt.so.1
ELF	7df94000-7dfb8000	Deferred        libk5crypto.so.3
ELF	7dfb8000-7e04a000	Deferred        libkrb5.so.3
ELF	7e04a000-7e074000	Deferred        libgssapi_krb5.so.2
ELF	7e074000-7e0aa000	Deferred        libcups.so.2
ELF	7e114000-7e13c000	Deferred        msacm32<elf>
  \-PE	7e120000-7e13c000	\               msacm32
ELF	7e13c000-7e155000	Deferred        msacm32<elf>
  \-PE	7e140000-7e155000	\               msacm32
ELF	7e155000-7e1a5000	Deferred        libpulse.so.0
ELF	7e1a5000-7e1ba000	Deferred        midimap<elf>
  \-PE	7e1b0000-7e1ba000	\               midimap
ELF	7e1ba000-7e1c3000	Deferred        librt.so.1
ELF	7e1c3000-7e28b000	Deferred        libasound.so.2
ELF	7e28b000-7e2c2000	Deferred        winealsa<elf>
  \-PE	7e290000-7e2c2000	\               winealsa
ELF	7e2c2000-7e2f5000	Deferred        uxtheme<elf>
  \-PE	7e2d0000-7e2f5000	\               uxtheme
ELF	7e2f5000-7e2fe000	Deferred        libxcursor.so.1
ELF	7e2fe000-7e303000	Deferred        libxfixes.so.3
ELF	7e303000-7e307000	Deferred        libxcomposite.so.1
ELF	7e307000-7e30e000	Deferred        libxrandr.so.2
ELF	7e30e000-7e318000	Deferred        libxrender.so.1
ELF	7e318000-7e31b000	Deferred        libxinerama.so.1
ELF	7e31b000-7e33c000	Deferred        imm32<elf>
  \-PE	7e320000-7e33c000	\               imm32
ELF	7e33c000-7e341000	Deferred        libxdmcp.so.6
ELF	7e341000-7e35a000	Deferred        libxcb.so.1
ELF	7e35a000-7e35d000	Deferred        libxcb-xlib.so.0
ELF	7e35d000-7e44c000	Deferred        libx11.so.6
ELF	7e44c000-7e45b000	Deferred        libxext.so.6
ELF	7e45b000-7e461000	Deferred        libxxf86vm.so.1
ELF	7e461000-7e479000	Deferred        libice.so.6
ELF	7e479000-7e482000	Deferred        libsm.so.6
ELF	7e484000-7e488000	Deferred        libkeyutils.so.1
ELF	7e488000-7e48c000	Deferred        libcom_err.so.2
ELF	7e48c000-7e490000	Deferred        libcap.so.1
ELF	7e490000-7e497000	Deferred        libasound_module_pcm_pulse.so
ELF	7e497000-7e532000	Deferred        winex11<elf>
  \-PE	7e4b0000-7e532000	\               winex11
ELF	7e55b000-7e582000	Deferred        libexpat.so.1
ELF	7e582000-7e5af000	Deferred        libfontconfig.so.1
ELF	7e5af000-7e5c5000	Deferred        libz.so.1
ELF	7e5c5000-7e63b000	Deferred        libfreetype.so.6
ELF	7e63b000-7e6e1000	Deferred        oleaut32<elf>
  \-PE	7e650000-7e6e1000	\               oleaut32
ELF	7e6e1000-7e718000	Deferred        winspool<elf>
  \-PE	7e6f0000-7e718000	\               winspool
ELF	7e718000-7e773000	Deferred        shlwapi<elf>
  \-PE	7e730000-7e773000	\               shlwapi
ELF	7e773000-7e887000	Deferred        shell32<elf>
  \-PE	7e780000-7e887000	\               shell32
ELF	7e887000-7e935000	Deferred        comdlg32<elf>
  \-PE	7e890000-7e935000	\               comdlg32
ELF	7e935000-7e9c9000	Deferred        winmm<elf>
  \-PE	7e940000-7e9c9000	\               winmm
ELF	7e9c9000-7ea8e000	Deferred        comctl32<elf>
  \-PE	7e9d0000-7ea8e000	\               comctl32
ELF	7ea8e000-7eaa2000	Deferred        libresolv.so.2
ELF	7eab7000-7ead6000	Deferred        iphlpapi<elf>
  \-PE	7eac0000-7ead6000	\               iphlpapi
ELF	7ead6000-7eb39000	Deferred        rpcrt4<elf>
  \-PE	7eae0000-7eb39000	\               rpcrt4
ELF	7eb39000-7ebd8000	Deferred        gdi32<elf>
  \-PE	7eb50000-7ebd8000	\               gdi32
ELF	7ebd8000-7ed24000	Deferred        user32<elf>
  \-PE	7ebf0000-7ed24000	\               user32
ELF	7ed24000-7ed77000	Deferred        advapi32<elf>
  \-PE	7ed30000-7ed77000	\               advapi32
ELF	7ed77000-7ee1d000	Deferred        ole32<elf>
  \-PE	7ed90000-7ee1d000	\               ole32
ELF	7ee1d000-7ee75000	Deferred        ddraw<elf>
  \-PE	7ee30000-7ee75000	\               ddraw
ELF	7ef95000-7efa1000	Deferred        libnss_files.so.2
ELF	7efa1000-7efac000	Deferred        libnss_nis.so.2
ELF	7efac000-7efc5000	Deferred        libnsl.so.1
ELF	7efc5000-7efeb000	Deferred        libm.so.6
ELF	b7df2000-b7df5000	Deferred        libxau.so.6
ELF	b7df5000-b7dfe000	Deferred        libnss_compat.so.2
ELF	b7dff000-b7e03000	Deferred        libdl.so.2
ELF	b7e03000-b7f61000	Deferred        libc.so.6
ELF	b7f62000-b7f7b000	Deferred        libpthread.so.0
ELF	b7f90000-b80c7000	Deferred        libwine.so.1
ELF	b80c9000-b80e6000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rosetta Stone\Rosetta Stone Version 3\RosettaStoneVersion3.exe
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x0041d591 in rosettastoneversion3 (+0x1d591) (0x00000007)
  2 0x00000000 (0x00000000)
gkay@LEVEL7:~$ [/COLOR]

i don't know exactly what is it 
thank you for your help
also i am using wine 1.0.1
and selected windows vista for running the program
thanks again

---

### Post by tyle on 2009-03-29
> **gkaykck said:**
> 
also i am using wine 1.0.1
and selected windows vista for running the program
thanks again

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043)

Update to a newer wine version, and you'll probably be fine.

---

