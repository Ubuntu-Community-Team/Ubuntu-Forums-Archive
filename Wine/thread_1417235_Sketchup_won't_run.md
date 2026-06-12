---
title: "Sketchup won't run"
date: 2010-02-27
forum: Wine
---

### Post by ferulebezel on 2010-02-27
I installed wine and sketchup.  When I try to run sketchup their but reporter comes up as soon as I hit the start "using sketchup button"  When I hit the send report button it hangs.

I ran it from a terminal window to get this output.


```
mark&#8984; wine .wine/drive_c/Program\ Files/Google/Google\ SketchUp\ 7/SketchUp.exe fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC"
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_RETRIES: STUB

Intrinsic Alchemy  v3.2 Beta-0902 (Dynamic/Release) 
Built by on Wed Sep 2 13:45:53 MDT 2009

fixme:shdocvw:PersistStreamInit_InitNew (0x204ab8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f340:3; TargetFrameName 0x32f350:8)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7df1a9b8, overlapped 0x7df1a99c): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x349ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x204b54)->((null) 1 0x32ea38 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 25 2 0x32ea4c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 26 2 0x32ea4c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x204b54)->(0x32ea90)
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32eb4c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x205430)->(L"" L"" 0 0x32eb84)
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 29 2 0x32f990 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x204b54)
fixme:shdocvw:ClientSite_GetContainer (0x204b54)->(0x32f908)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x204b54)->(0x6003eb71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 25 2 0x32f814 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 26 2 0x32f814 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x204b54)->((null) 28 2 0x32fa84 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:WebBrowser_Stop (0x204ab8)
fixme:shdocvw:OleObject_Close (0x204ab8)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x204ab8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x205c78)->((nil))
fixme:shdocvw:OleObject_Close (0x204ab8)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
mark&#8984; fixme:system:SystemParametersInfoW Unimplemented action: 8192 (SPI_GETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:wininet:InternetAttemptConnect Stub
fixme:wininet:InternetAttemptConnect Stub
wine: Unhandled page fault on read access to 0x6e655665 at address 0x6062a3c1 (thread 0025), starting debugger...
Unhandled exception: page fault on read access to 0x6e655665 in 32-bit code (0x6062a3c1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6062a3c1 ESP:7ed5c3c8 EBP:7ed5c440 EFLAGS:00210206(   - 00      - RIP1)
 EAX:6e655665 EBX:60649ff4 ECX:60650f5c EDX:00006e65
 ESI:7ed5c4c8 EDI:0000000f
Stack dump:
0x7ed5c3c8:  00000000 00000000 00436886 00000001
0x7ed5c3d8:  00134090 00000001 00110000 00000000
0x7ed5c3e8:  7bc435bb 60649ff4 001320d0 00000001
0x7ed5c3f8:  7ed5c448 6062d5b2 00110000 00000020
0x7ed5c408:  60650f5c 60644426 6064347d 00131fd8
0x7ed5c418:  00130998 00134090 001304a8 00000005
Backtrace:
=>1 0x6062a3c1 HttpOpenRequestA+0xb1() in wininet (0x7ed5c440)
  2 0x00410328 in bssndrpt (+0x10328) (0x7ed5cc74)
  3 0x0040ff31 in bssndrpt (+0xff31) (0x7ed5d8b8)
  4 0x0040c5e3 in bssndrpt (+0xc5e3) (0x7ed5d908)
  5 0x0040c0f1 in bssndrpt (+0xc0f1) (0x7ed5d9d8)
  6 0x004123d1 in bssndrpt (+0x123d1) (0x7ed5d9f8)
  7 0x7bc6dac2 in ntdll (+0x5dac2) (0x7ed5da98)
  8 0x7bc6dcbd in ntdll (+0x5dcbd) (0x7ed5e398)
  9 0x6013b80e start_thread+0xbe() in libpthread.so.0 (0x7ed5e498)
  10 0x6021b8de __clone+0x5e() in libc.so.6 (0x00000000)
0x6062a3c1 HttpOpenRequestA+0xb1 in wininet: cmpb	$0x0,0x0(%eax)
Modules:
Module	Address			Debug info	Name (71 modules)
PE	  400000-  444000	Export          bssndrpt
PE	10000000-1000f000	Deferred        bugsplatrc
ELF	60000000-60136000	Deferred        libwine.so.1
ELF	60136000-6014f000	Export          libpthread.so.0
ELF	6014f000-60294000	Export          libc.so.6
ELF	60294000-60298000	Deferred        libdl.so.2
ELF	60298000-602be000	Deferred        libm.so.6
ELF	602be000-602c6000	Deferred        libnss_compat.so.2
ELF	602c6000-602dd000	Deferred        libnsl.so.1
ELF	602dd000-602e9000	Deferred        libnss_files.so.2
ELF	602e9000-60344000	Deferred        shlwapi<elf>
  \-PE	60300000-60344000	\               shlwapi
ELF	60344000-6048f000	Deferred        user32<elf>
  \-PE	60360000-6048f000	\               user32
ELF	6048f000-6052e000	Deferred        gdi32<elf>
  \-PE	604a0000-6052e000	\               gdi32
ELF	6052e000-60580000	Deferred        advapi32<elf>
  \-PE	60540000-60580000	\               advapi32
ELF	60580000-605e3000	Deferred        rpcrt4<elf>
  \-PE	60590000-605e3000	\               rpcrt4
ELF	605e3000-60602000	Deferred        iphlpapi<elf>
  \-PE	605f0000-60602000	\               iphlpapi
ELF	60602000-60652000	Export          wininet<elf>
  \-PE	60610000-60652000	\               wininet
ELF	60652000-60675000	Deferred        mpr<elf>
  \-PE	60660000-60675000	\               mpr
ELF	60675000-60738000	Deferred        comctl32<elf>
  \-PE	60680000-60738000	\               comctl32
ELF	60738000-60765000	Deferred        ws2_32<elf>
  \-PE	60740000-60765000	\               ws2_32
ELF	60765000-6080b000	Deferred        ole32<elf>
  \-PE	60770000-6080b000	\               ole32
ELF	6080b000-608b1000	Deferred        oleaut32<elf>
  \-PE	60820000-608b1000	\               oleaut32
ELF	608b1000-60930000	Deferred        libfreetype.so.6
ELF	60930000-60946000	Deferred        libz.so.1
ELF	60946000-60973000	Deferred        libfontconfig.so.1
ELF	60973000-6099a000	Deferred        libexpat.so.1
ELF	6099a000-60a34000	Deferred        winex11<elf>
  \-PE	609b0000-60a34000	\               winex11
ELF	60a34000-60a3d000	Deferred        libsm.so.6
ELF	60a3d000-60a58000	Deferred        libice.so.6
ELF	60a58000-60a5e000	Deferred        libxxf86vm.so.1
ELF	60a5e000-60a6e000	Deferred        libxext.so.6
ELF	60a6e000-60b9d000	Deferred        libx11.so.6
ELF	60b9d000-60ba2000	Deferred        libuuid.so.1
ELF	60ba2000-60ba6000	Deferred        libxau.so.6
ELF	60ba6000-60bc4000	Deferred        libxcb.so.1
ELF	60bc4000-60bc9000	Deferred        libxdmcp.so.6
ELF	60bc9000-60bea000	Deferred        imm32<elf>
  \-PE	60bd0000-60bea000	\               imm32
ELF	60bea000-60bed000	Deferred        libxinerama.so.1
ELF	60bed000-60bf7000	Deferred        libxrender.so.1
ELF	60bf7000-60c00000	Deferred        libxrandr.so.2
ELF	60c00000-60c04000	Deferred        libxcomposite.so.1
ELF	60c04000-60c0a000	Deferred        libxfixes.so.3
ELF	60c0a000-60c15000	Deferred        libxcursor.so.1
ELF	60c15000-60c48000	Deferred        uxtheme<elf>
  \-PE	60c20000-60c48000	\               uxtheme
ELF	60c48000-60c4c000	Deferred        libnss_mdns4_minimal.so.2
ELF	6db1d000-6db24000	Deferred        libnss_dns.so.2
ELF	72c47000-72c52000	Deferred        libnss_nis.so.2
ELF	75557000-7566b000	Deferred        shell32<elf>
  \-PE	75570000-7566b000	\               shell32
ELF	7a6b8000-7a6d5000	Deferred        ld-linux.so.2
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca7000	Export          ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c260000-7c274000	Deferred        libresolv.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
00000023 (D) Z:\home\mark\.wine\drive_c\Program Files\Google\Google SketchUp 7\BsSndRpt.exe
	00000025    0 <==
	00000024    0
Backtrace:
=>1 0x6062a3c1 HttpOpenRequestA+0xb1() in wininet (0x7ed5c440)
  2 0x00410328 in bssndrpt (+0x10328) (0x7ed5cc74)
  3 0x0040ff31 in bssndrpt (+0xff31) (0x7ed5d8b8)
  4 0x0040c5e3 in bssndrpt (+0xc5e3) (0x7ed5d908)
  5 0x0040c0f1 in bssndrpt (+0xc0f1) (0x7ed5d9d8)
  6 0x004123d1 in bssndrpt (+0x123d1) (0x7ed5d9f8)
  7 0x7bc6dac2 in ntdll (+0x5dac2) (0x7ed5da98)
  8 0x7bc6dcbd in ntdll (+0x5dcbd) (0x7ed5e398)
  9 0x6013b80e start_thread+0xbe() in libpthread.so.0 (0x7ed5e498)
  10 0x6021b8de __clone+0x5e() in libc.so.6 (0x00000000)
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 272 requests (272 known processed) with 0 events remaining.
```

This is where it hung and I killed it.

Can anyone make heads or tails of this?

---

### Post by ferulebezel on 2010-03-05
Just posting a reply, hoping someone will see this.

---

