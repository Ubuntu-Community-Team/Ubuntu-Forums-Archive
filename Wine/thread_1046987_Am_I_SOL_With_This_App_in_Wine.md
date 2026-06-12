---
title: "Am I SOL With This App in Wine?"
date: 2009-01-21
forum: Wine
---

### Post by crokett on 2009-01-21
I have an application that I need for work that I am trying to get running under Wine.  At install it was complaining about the MFC classes not being there so I copied the installed directory and my WinSxS directory from my Windows laptop to the appropriate folders under .wine.  Then I tried running the app and got a lot of errors, so I also copied my .NET/Framework directory over.  I still get these errors.  Any help on what is going on and if it can be fixed?  My alternative is a virtual Windows machine but I'd like to avoid that if possible. 

Thanks. 

```

fixme:advapi:SetEntriesInAclA 0 (nil) (nil) 0x33fc68
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:advapi:CheckTokenMembership (0x258 0x164fe8 0x33df98) stub!

Unhandled Exception: System.TypeInitializationException: The type initializer for 'System.Globalization.TextInfo' threw an exception.
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)
wine: Unhandled exception 0xe0434f4d at address 0x7b845450 (thread 0009), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:0033ef54 EBP:0033efb8 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:0033eff0
 ESI:0033eff0 EDI:0014ee68
Stack dump:
0x0033ef54:  0033eff0 00000004 0000003c e0434f4d
0x0033ef64:  00000001 00000000 7b845450 00000001
0x0033ef74:  80131534 02000038 0033ef90 79e7b494
0x0033ef84:  0033ef9c 02000038 00000001 0033efa0
0x0033ef94:  79e7e17f 0000012f 03d20544 0033efb0
0x0033efa4:  79f07282 03d714fc 7b84545a e0434f4d
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0033efb8)
  2 0x79f071ac in mscorwks (+0x971ac) (0x0033f018)
  3 0x79f0a629 in mscorwks (+0x9a629) (0x0033f0dc)
  4 0x03d5363b (0x0033f10c)
  5 0x03d53501 (0x0033f138)
  6 0x03d51845 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (102 modules)
PE	  340000-  3a2000	Deferred        xports
PE	  3b0000-  3ea000	Deferred        resourcebrowser
PE	  3f0000-  3f9000	Deferred        pwc
PE	  400000-  7bb000	Deferred        xgig-tracecontrol
PE	  7c0000-  7d9000	Deferred        tracedbg
PE	  7e0000-  7f2000	Deferred        remoteservices
PE	  800000-  816000	Deferred        tcsapi
PE	  820000-  832000	Deferred        clienttransport
PE	  840000-  868000	Deferred        applicationframework
PE	  870000-  89f000	Deferred        ccomparator
PE	  8a0000-  aa7000	Deferred        allprotocolslib
PE	  ab0000-  ae6000	Deferred        lli
PE	  af0000-  b10000	Deferred        chart
PE	  b10000-  b29000	Deferred        lstctl
PE	  b30000- 127a000	Deferred        commonui
PE	 1280000- 1288000	Deferred        pwp
PE	 1290000- 1297000	Deferred        gc
PE	 12a0000- 12a6000	Deferred        sdfa
PE	10000000-100a1000	Deferred        analyzerdomain
PE	20000000-2019d000	Deferred        tracedataio
PE	5d360000-5d36e000	Deferred        mfc80enu
PE	5e3a0000-5e42d000	Deferred        diasymreader
PE	78130000-781cb000	Deferred        msvcr80
PE	781d0000-782df000	Deferred        mfc80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b6000	Deferred        mscorjit
PE	790c0000-79500000	Deferred        mscorlib
PE	79e70000-7a3ff000	Export          mscorwks
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
PE	7c4c0000-7c53d000	Deferred        msvcm80
PE	7c550000-7c562000	Deferred        mfcm80
ELF	7e380000-7e3b3000	Deferred        uxtheme<elf>
  \-PE	7e390000-7e3b3000	\               uxtheme
ELF	7e3db000-7e3e4000	Deferred        libxcursor.so.1
ELF	7e3e4000-7e3e9000	Deferred        libxfixes.so.3
ELF	7e3e9000-7e3ed000	Deferred        libxcomposite.so.1
ELF	7e3ed000-7e3f4000	Deferred        libxrandr.so.2
ELF	7e3f4000-7e3fe000	Deferred        libxrender.so.1
ELF	7e3fe000-7e401000	Deferred        libxinerama.so.1
ELF	7e401000-7e422000	Deferred        imm32<elf>
  \-PE	7e410000-7e422000	\               imm32
ELF	7e422000-7e427000	Deferred        libxdmcp.so.6
ELF	7e427000-7e440000	Deferred        libxcb.so.1
ELF	7e440000-7e443000	Deferred        libxcb-xlib.so.0
ELF	7e443000-7e446000	Deferred        libxau.so.6
ELF	7e446000-7e535000	Deferred        libx11.so.6
ELF	7e535000-7e544000	Deferred        libxext.so.6
ELF	7e544000-7e54a000	Deferred        libxxf86vm.so.1
ELF	7e54a000-7e562000	Deferred        libice.so.6
ELF	7e562000-7e56b000	Deferred        libsm.so.6
ELF	7e581000-7e61c000	Deferred        winex11<elf>
  \-PE	7e590000-7e61c000	\               winex11
ELF	7e655000-7e67c000	Deferred        libexpat.so.1
ELF	7e67c000-7e6a9000	Deferred        libfontconfig.so.1
ELF	7e6a9000-7e6bf000	Deferred        libz.so.1
ELF	7e6bf000-7e735000	Deferred        libfreetype.so.6
ELF	7e74b000-7e85f000	Deferred        shell32<elf>
  \-PE	7e760000-7e85f000	\               shell32
ELF	7e85f000-7e875000	Deferred        psapi<elf>
  \-PE	7e860000-7e875000	\               psapi
ELF	7e875000-7e93a000	Deferred        comctl32<elf>
  \-PE	7e880000-7e93a000	\               comctl32
ELF	7e93a000-7e995000	Deferred        shlwapi<elf>
  \-PE	7e950000-7e995000	\               shlwapi
ELF	7e995000-7e9b0000	Deferred        version<elf>
  \-PE	7e9a0000-7e9b0000	\               version
ELF	7e9b0000-7e9dd000	Deferred        ws2_32<elf>
  \-PE	7e9c0000-7e9dd000	\               ws2_32
ELF	7e9dd000-7ea49000	Deferred        msvcrt<elf>
  \-PE	7e9f0000-7ea49000	\               msvcrt
ELF	7ea49000-7ea5d000	Deferred        libresolv.so.2
ELF	7ea5e000-7ea73000	Deferred        lz32<elf>
  \-PE	7ea60000-7ea73000	\               lz32
ELF	7ea73000-7ea92000	Deferred        iphlpapi<elf>
  \-PE	7ea80000-7ea92000	\               iphlpapi
ELF	7ea92000-7eaf5000	Deferred        rpcrt4<elf>
  \-PE	7eaa0000-7eaf5000	\               rpcrt4
ELF	7eaf5000-7eb9b000	Deferred        ole32<elf>
  \-PE	7eb00000-7eb9b000	\               ole32
ELF	7eb9b000-7ec41000	Deferred        oleaut32<elf>
  \-PE	7ebb0000-7ec41000	\               oleaut32
ELF	7ec41000-7ec94000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec94000	\               advapi32
ELF	7ec94000-7ed33000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed33000	\               gdi32
ELF	7ed33000-7ee7f000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7f000	\               user32
ELF	7ef9f000-7efab000	Deferred        libnss_files.so.2
ELF	7efab000-7efc4000	Deferred        libnsl.so.1
ELF	7efc4000-7efea000	Deferred        libm.so.6
ELF	7efec000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c25000-b7c29000	Deferred        libdl.so.2
ELF	b7c29000-b7d87000	Deferred        libc.so.6
ELF	b7d88000-b7da1000	Deferred        libpthread.so.0
ELF	b7db7000-b7eee000	Deferred        libwine.so.1
ELF	b7ef0000-b7f0d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\XGig\Xgig-TraceControl.exe
	0000001b    2
	0000001a    0
	00000019    0
	00000009    0 <==
0000000c 
	00000016    0
	00000013    0
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
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0033efb8)
  2 0x79f071ac in mscorwks (+0x971ac) (0x0033f018)
  3 0x79f0a629 in mscorwks (+0x9a629) (0x0033f0dc)
  4 0x03d5363b (0x0033f10c)
  5 0x03d53501 (0x0033f138)
  6 0x03d51845 (0x00000000)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x33eaa4,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.1433 - Fatal Execution Engine Error (79F071BC) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


```

---

### Post by cogadh on 2009-01-22
Just copying the application directory from another Windows machine or partition is unlikely to work. Most applications write some kind of registry entries when they are installed that are required for the app to run properly. This is especially true for things like .NET.

The first thing you should do is use [winetricks]("http://wiki.winehq.org/winetricks") to install .NET in Wine correctly, then try running the installation for the app again. If the installation fails, post Wine's terminal output from the installation process. It may indicate what the actual problem is and possibly a solution.

Also, it might help to check Wine's [Application Database]("http://appdb.winehq.org/") to see if anyone else has tried using the app with Wine and what, if anything, they needed to do to make it work.

---

### Post by crokett on 2009-01-22
I checked the application database first, and didn't see it listed. It is pretty specific - it is an app that reads fibre channel traces.   

Thanks for the suggestions. I will look at the winetricks link and check out the registry entries.  I forgot about those.  I've read where other folks have gotten apps to work by doing what I am attempting so I figured I'd try it.

---

### Post by crokett on 2009-01-22
Ok, I managed to get the program to install.  I installed winetricks, then installed the .NET, MFC and MFC2005SP1 libraries the program needs.  Then I installed the program.  However now it says this.  I also copied the WinSxS directory over from my Windows XP machine so I know the files are there.

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\XPorts.dll") not found
err:module:import_dll Library XPorts.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\AnalyzerDomain.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\AnalyzerDomain.dll") not found
err:module:import_dll Library AnalyzerDomain.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\XPorts.dll") not found
err:module:import_dll Library XPorts.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\AllProtocolsLib.DLL") not found
err:module:import_dll Library AllProtocolsLib.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CComparator.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CComparator.dll") not found
err:module:import_dll Library CComparator.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\TraceDataIO.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\TraceDataIO.dll") not found
err:module:import_dll Library TraceDataIO.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Chart.dll") not found
err:module:import_dll Library Chart.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\LstCtl.dll") not found
err:module:import_dll Library LstCtl.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\AllProtocolsLib.DLL") not found
err:module:import_dll Library AllProtocolsLib.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CComparator.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CComparator.dll") not found
err:module:import_dll Library CComparator.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\TraceDataIO.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\TraceDataIO.dll") not found
err:module:import_dll Library TraceDataIO.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CommonUI.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CommonUI.dll") not found
err:module:import_dll Library CommonUI.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\AllProtocolsLib.DLL") not found
err:module:import_dll Library AllProtocolsLib.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CComparator.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\CComparator.dll") not found
err:module:import_dll Library CComparator.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
err:module:import_dll Library mfcm80.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\PWP.dll") not found
err:module:import_dll Library PWP.dll (which is needed by L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Finisar\\Xgig Analyzer\\Xgig-TraceControl.exe" failed, status c0000135


```

---

### Post by cogadh on 2009-01-22
Why do you keep copying that WinSxS directory? It doesn't appear to me that any of that is required and copying it from another machine could actually cause problems.

As for the DLLs Wine is saying you are missing, most of them should be found in the system32 directory, if they are actually present. If they are in the application's install directory, it should also work, but in order for them to be properly detected, you will need to change directories to where the app is installed, then "wine" the executable:
```
cd .wine/drive_c/Program\ Files/<installation directory>
wine foo.exe
```

---

### Post by crokett on 2009-01-22
On my Windows machine, that is where the files are located.  That is why I copied them over. None of these DLLs the program is complaining about are located in any other Windows directories than WinSxS.   

Running the executable from the installed directory gave the same list of errors as running it from my home directory with the fully qualified path to the executable.  I am not sure if it is looking in the wrong place or Wine is looking in the wrong place.

---

### Post by cogadh on 2009-01-22
Try putting just those missing DLLs into the program's install directory or Wine's system32 directory. I'm not sure where the app is looking for them, but normally Wine expects DLLs like that to be found in one of those two places.

---

### Post by crokett on 2009-01-22
Thanks. I am going to try thrashing Wine and starting over.  I learned about winetricks after I'd gotten the program installed.  If that doesn't work I can always run it under a virtual machine.

---

