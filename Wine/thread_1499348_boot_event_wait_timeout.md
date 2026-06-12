---
title: "boot event wait timeout"
date: 2010-06-01
forum: Wine
---

### Post by Trizzy on 2010-06-01
1. Wine version - 1.1.42
   2. Terminal output - ```
:~$ sh winetricks
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
Setting Windows version to win2k
Executing wine regedit /home/tpohl/.wine/drive_c/winetrickstmp/set-winver.reg
err:process:__wine_kernel_init boot event wait timed out
Install of win2k done
winetricks done.

```
   3. Wine configuration - So far the OS selected doesn't change the problem in the terminal.
     I haven't manually changed any library overrides.
     Sound and graphic options I don't think have any bearing on this problem, but I will post any if they are asked for.
     I haven't made any registry edits, though I can't be sure some of the fixes I have used in the past have changed them for me.
          
   4. Hardware specs/drivers - Again I don't think this has any bearing on the problem, but I will post if necessary.
   5. Other Wine applications - I have used winetricks quite a bit, as it is often referred to in the forums to assist in getting programs to work. So far as I can remember, I have installed dotnet20, fontfix, msxml3, msxml4, directx9, and allfonts. 


     The problem: In the terminal output section you see 
```
err:process:__wine_kernel_init boot event wait timed out

```

     When I issue a command in the terminal to do with wine, I get this message after about 2 or 3 minutes of waiting. Each time that error message is printed is another 2 or 3 minute wait. Also, any wine program whether it be a game or winecfg also has the same lengthy pause. I can't recall exactly when the problem started, so I'm not for sure what could be the culprit. My best guess is one of the winetricks installs.

     Thanks in advance for any help!

---

### Post by cogadh on 2010-06-01
Try running the ["wineboot"]("http://wiki.jswindle.com/index.php/Wine_Simulate_Windows_Reboot") command to force a reboot action.

---

### Post by Trizzy on 2010-06-01
Along with the posted output, I recieved an error message outside of the terminal saying to reboot the Home Network Manager, or reinstall it. Also, dxdllreg has had a problem and needs to close.


Does the dxdllreg refer to DirectX? If so, it would seem that me installing DirectX9 via winetricks could be (one of) my problem? I realize the stickied post in this forums states not to install directx, but it has helped some of my games run smoother, but if that is the cause of the really sloooow wine than I would remove directx asap.

```
~$ wineboot
err:process:__wine_kernel_init boot event wait timed out
err:wineboot:ProcessRunKeys Error running cmd L"Z:\\home\\tpohl\\Desktop\\PUTT~GHT.EXE /r" (2)
tpohl@tpohl:~$ fixme:reg:GetNativeSystemInfo (0x33fb08) using GetSystemInfo()
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.42
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\CenturyTel\\Home Network Manager\\Microsoft.VC80.MFC\\Microsoft.VC80.MFCLOC.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:advapi:SetEntriesInAclA 1 0x33f744 (nil) 0x33f77c
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f734 (nil) 0x33f77c
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f754 (nil) 0x33f79c
fixme:advapi:SetSecurityInfo stub
fixme:shdocvw:PersistStreamInit_InitNew (0x144100)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x335c88:3; TargetFrameName 0x335c98:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
wine: Unhandled page fault on read access to 0x0000000f at address 0x7ed6c137 (thread 003f), starting debugger...
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x334160
fixme:iphlpapi:NotifyAddrChange (Handle 0x261e8d8, overlapped 0x261e8e0): stub
0[14b338]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1441a0)->((null) 1 0x3348a0 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x1441a0)->(0x334868)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:shdocvw:navigate_url Unsupported args (Flags 0x335cb0:3; TargetFrameName 0x335cc0:8)
fixme:advapi:LookupAccountNameW L"" L"everyone" 0x646418 0x335b68 0x283ef50 0x335b6c 0x335b74 - stub
wine: cannot find L"C:\\windows\\system32\\qctray.exe"
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1441a0)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x1441a0)->(0x3349e8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1441a0)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x1441a0)->(0x334938)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1441a0)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1441a0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1441a0)->(L"Done")
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),6,3,(nil),2,(nil)) - stub!
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:wbemprox:wbem_locator_ConnectServer 0x12a568, L"ROOT\\WMI", (null), (null), (null), 0x00000000, (null), (nil), 0x33fc2c)
Could not connect to server - error 0x80041001
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x144100)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1459a8)->((nil))
fixme:shdocvw:OleObject_Close (0x144100)->(1)
Unhandled exception: page fault on read access to 0x0000000f in 32-bit code (0x7ed6c137).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7ed6c137 ESP:0033f44c EBP:0033f7b4 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7edb7ff4 ECX:d5487603 EDX:00000000
 ESI:00000000 EDI:0033fa4c
Stack dump:
0x0033f44c:  000000d8 00410033 0033f4b8 7bc46c2e
0x0033f45c:  002d0036 00320032 00320032 00000080
0x0033f46c:  00110000 7bc99ff4 7bc47961 0980f000
0x0033f47c:  00000002 01049df0 00320032 7bc99ff4
0x0033f48c:  0100f000 0100f028 0033f4e4 7bc47dc7
0x0033f49c:  ffffffff 0033f4c8 0033f4c4 00008000
Backtrace:
=>0 0x7ed6c137 NdrDllRegisterProxy+0x27() in rpcrt4 (0x0033f7b4)
  1 0x358215aa in msvidctl (+0x215a9) (0x0033f7e4)
  2 0x01003180 in dxdllreg (+0x317f) (0x0033fb54)
  3 0x010033f7 in dxdllreg (+0x33f6) (0x0033fd80)
  4 0x01003814 in dxdllreg (+0x3813) (0x0033fea8)
  5 0x7b858a24 in kernel32 (+0x48a23) (0x0033fee8)
  6 0x7bc707f4 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc709c0 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4bb9a in ntdll (+0x3bb99) (0x0033ffe8)
0x7ed6c137 NdrDllRegisterProxy+0x27 in rpcrt4: movzbl	0xf(%esi),%eax
Modules:
Module	Address			Debug info	Name (88 modules)
PE	  470000-  493000	Deferred        devenum
PE	 1000000- 100f000	Export          dxdllreg
PE	35500000-35708000	Deferred        quartz
PE	35800000-35931000	Export          msvidctl
ELF	7b800000-7b93a000	Export          kernel32<elf>
  \-PE	7b810000-7b93a000	\               kernel32
ELF	7bc00000-7bcb6000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb6000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7dfff000-7e032000	Deferred        uxtheme<elf>
  \-PE	7e010000-7e032000	\               uxtheme
ELF	7e032000-7e100000	Deferred        comctl32<elf>
  \-PE	7e040000-7e100000	\               comctl32
ELF	7e100000-7e148000	Deferred        dsound<elf>
  \-PE	7e110000-7e148000	\               dsound
ELF	7e148000-7e1cf000	Deferred        winmm<elf>
  \-PE	7e150000-7e1cf000	\               winmm
ELF	7e1cf000-7e2b5000	Deferred        oleaut32<elf>
  \-PE	7e1f0000-7e2b5000	\               oleaut32
ELF	7e2b5000-7e324000	Deferred        msvcrt<elf>
  \-PE	7e2d0000-7e324000	\               msvcrt
ELF	7e33a000-7e33f000	Deferred        libgpg-error.so.0
ELF	7e33f000-7e348000	Deferred        librt.so.1
ELF	7e348000-7e381000	Deferred        libdbus-1.so.3
ELF	7e381000-7e3f4000	Deferred        libgcrypt.so.11
ELF	7e3f4000-7e405000	Deferred        libtasn1.so.3
ELF	7e405000-7e419000	Deferred        libresolv.so.2
ELF	7e419000-7e41d000	Deferred        libkeyutils.so.1
ELF	7e41d000-7e425000	Deferred        libkrb5support.so.0
ELF	7e425000-7e449000	Deferred        libk5crypto.so.3
ELF	7e449000-7e4fa000	Deferred        libkrb5.so.3
ELF	7e4fa000-7e595000	Deferred        libgnutls.so.26
ELF	7e595000-7e5c4000	Deferred        libgssapi_krb5.so.2
ELF	7e5c4000-7e60a000	Deferred        libcups.so.2
ELF	7e62e000-7e638000	Deferred        libxcursor.so.1
ELF	7e638000-7e63e000	Deferred        libxfixes.so.3
ELF	7e63e000-7e642000	Deferred        libxcomposite.so.1
ELF	7e642000-7e64a000	Deferred        libxrandr.so.2
ELF	7e64a000-7e654000	Deferred        libxrender.so.1
ELF	7e654000-7e65a000	Deferred        libxxf86vm.so.1
ELF	7e65a000-7e65e000	Deferred        libxinerama.so.1
ELF	7e65e000-7e67f000	Deferred        imm32<elf>
  \-PE	7e660000-7e67f000	\               imm32
ELF	7e67f000-7e685000	Deferred        libxdmcp.so.6
ELF	7e685000-7e689000	Deferred        libxau.so.6
ELF	7e689000-7e6a3000	Deferred        libxcb.so.1
ELF	7e6a3000-7e6a8000	Deferred        libuuid.so.1
ELF	7e6a8000-7e7c5000	Deferred        libx11.so.6
ELF	7e7c5000-7e7d5000	Deferred        libxext.so.6
ELF	7e7d5000-7e7ee000	Deferred        libice.so.6
ELF	7e7ee000-7e7f7000	Deferred        libsm.so.6
ELF	7e7f8000-7e7fc000	Deferred        libcom_err.so.2
ELF	7e7fc000-7e80d000	Deferred        libavahi-client.so.3
ELF	7e80d000-7e819000	Deferred        libavahi-common.so.3
ELF	7e81b000-7e8ba000	Deferred        winex11<elf>
  \-PE	7e830000-7e8ba000	\               winex11
ELF	7e90f000-7e936000	Deferred        libexpat.so.1
ELF	7e936000-7e966000	Deferred        libfontconfig.so.1
ELF	7e966000-7e97b000	Deferred        libz.so.1
ELF	7e97b000-7e9f1000	Deferred        libfreetype.so.6
ELF	7ea15000-7eb11000	Deferred        ole32<elf>
  \-PE	7ea30000-7eb11000	\               ole32
ELF	7eb11000-7eb25000	Deferred        lz32<elf>
  \-PE	7eb20000-7eb25000	\               lz32
ELF	7eb25000-7ebaf000	Deferred        gdi32<elf>
  \-PE	7eb30000-7ebaf000	\               gdi32
ELF	7ebaf000-7ecbe000	Deferred        user32<elf>
  \-PE	7ebc0000-7ecbe000	\               user32
ELF	7ecbe000-7ecf4000	Deferred        winspool<elf>
  \-PE	7ecd0000-7ecf4000	\               winspool
ELF	7ecf4000-7ed4d000	Deferred        setupapi<elf>
  \-PE	7ed00000-7ed4d000	\               setupapi
ELF	7ed4d000-7edbe000	Export          rpcrt4<elf>
  \-PE	7ed60000-7edbe000	\               rpcrt4
ELF	7edbe000-7ee17000	Deferred        advapi32<elf>
  \-PE	7edd0000-7ee17000	\               advapi32
ELF	7ee17000-7ee23000	Deferred        libnss_files.so.2
ELF	7ee23000-7ee2d000	Deferred        libnss_nis.so.2
ELF	7ee2d000-7ee35000	Deferred        libnss_compat.so.2
ELF	7ee40000-7ee59000	Deferred        version<elf>
  \-PE	7ee50000-7ee59000	\               version
ELF	7efb6000-7efdc000	Deferred        libm.so.6
ELF	7efe0000-7eff7000	Deferred        libnsl.so.1
ELF	f7435000-f7439000	Deferred        libdl.so.2
ELF	f7439000-f7593000	Deferred        libc.so.6
ELF	f7594000-f75ad000	Deferred        libpthread.so.0
ELF	f75d1000-f770c000	Export          libwine.so.1
ELF	f770e000-f772c000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a wineboot.exe
	0000000b    0
0000000e services.exe
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
0000003e (D) C:\windows\system32\dxdllreg.exe
	0000003f    0 <==
00000040 DWTRIG20.EXE
	00000041    0
00000042 explorer.exe
	00000043    0
Backtrace:
=>0 0x7ed6c137 NdrDllRegisterProxy+0x27() in rpcrt4 (0x0033f7b4)
  1 0x358215aa in msvidctl (+0x215a9) (0x0033f7e4)
  2 0x01003180 in dxdllreg (+0x317f) (0x0033fb54)
  3 0x010033f7 in dxdllreg (+0x33f6) (0x0033fd80)
  4 0x01003814 in dxdllreg (+0x3813) (0x0033fea8)
  5 0x7b858a24 in kernel32 (+0x48a23) (0x0033fee8)
  6 0x7bc707f4 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc709c0 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4bb9a in ntdll (+0x3bb99) (0x0033ffe8)
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\profiles\\tpohl\\Local Settings\\Application Data\\PCHealth\\ErrorRep\\QSignoff" 1 -2147483644 (nil) (nil) 0x1375ec (nil)
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x5

```

     There may be more in the output, but it's sat in this spot for about 10 minutes. I have saved the terminal so far, and will post any additional output it gives me. Thanks for the help so far!

---

### Post by cogadh on 2010-06-02
Yeah, definitely get rid of DirectX, it can and will break Wine. All you should really need from DirectX are the d3dx9_##.dll files, which you can install with winetricks without installing the full DirectX package.

---

### Post by Trizzy on 2010-06-02
Thanks for the information. I will note this problem in any future threads where someone recommends installing driectX9 via winetricks.

---

### Post by damaan on 2010-06-28
@Trizzy: Did you solve or work around this issue? I also have this delay/timeout every time I start a Wine application and it's pretty annoying.

Edit: I have never used winetricks as far as I can recall.

---

### Post by Trizzy on 2010-10-06
Sorry for not getting back to your post in so long! I had removed this from my subscribed threads. 

To fix the issue I completely removed and purged wine from my system, and started to rebuild it. I have so far avoided DirectX of any kind, and it seems to have fixed my problem. Where as before, ANY command issued in wine would result in the 
```
err:process:__wine_kernel_init boot event wait timed out

```

now it seems only certain packages installed via winetricks causes this timeout. Namely, allfonts package. I'm installing that now, so I can post the output it's giving me for future reference.
```
tpohl@tpohl:~$ sh winetricks allfonts
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/arial32.exe
--2010-10-06 17:18:36--  http://downloads.sourceforge.net/corefonts/arial32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2010-10-06 17:18:36--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2010-10-06 17:18:36--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/x-msdos-program]
Saving to: `arial32.exe'

100%[======================================>] 554,208      394K/s   in 1.4s    

2010-10-06 17:18:38 (394 KB/s) - `arial32.exe' saved [554208/554208]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/arialb32.exe
--2010-10-06 17:18:38--  http://downloads.sourceforge.net/corefonts/arialb32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2010-10-06 17:18:38--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2010-10-06 17:18:38--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `arialb32.exe'

100%[======================================>] 168,176      339K/s   in 0.5s    

2010-10-06 17:18:39 (339 KB/s) - `arialb32.exe' saved [168176/168176]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/comic32.exe
--2010-10-06 17:18:39--  http://downloads.sourceforge.net/corefonts/comic32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2010-10-06 17:18:39--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2010-10-06 17:18:39--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/x-msdos-program]
Saving to: `comic32.exe'

100%[======================================>] 246,008      372K/s   in 0.6s    

2010-10-06 17:18:40 (372 KB/s) - `comic32.exe' saved [246008/246008]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/courie32.exe
--2010-10-06 17:18:40--  http://downloads.sourceforge.net/corefonts/courie32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2010-10-06 17:18:40--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2010-10-06 17:18:40--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/x-msdos-program]
Saving to: `courie32.exe'

100%[======================================>] 646,368      407K/s   in 1.6s    

2010-10-06 17:18:42 (407 KB/s) - `courie32.exe' saved [646368/646368]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/georgi32.exe
--2010-10-06 17:18:42--  http://downloads.sourceforge.net/corefonts/georgi32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2010-10-06 17:18:42--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2010-10-06 17:18:42--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `georgi32.exe'

100%[======================================>] 392,440      377K/s   in 1.0s    

2010-10-06 17:18:44 (377 KB/s) - `georgi32.exe' saved [392440/392440]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/impact32.exe
--2010-10-06 17:18:44--  http://downloads.sourceforge.net/corefonts/impact32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following]
--2010-10-06 17:18:44--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following]
--2010-10-06 17:18:44--  http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe
Resolving superb-sea2.dl.sourceforge.net... 209.160.57.180
Connecting to superb-sea2.dl.sourceforge.net|209.160.57.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `impact32.exe'

100%[======================================>] 173,288      114K/s   in 1.5s    

2010-10-06 17:18:46 (114 KB/s) - `impact32.exe' saved [173288/173288]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/times32.exe
--2010-10-06 17:18:46--  http://downloads.sourceforge.net/corefonts/times32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following]
--2010-10-06 17:18:46--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following]
--2010-10-06 17:18:46--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/x-msdos-program]
Saving to: `times32.exe'

100%[======================================>] 661,728      407K/s   in 1.6s    

2010-10-06 17:18:48 (407 KB/s) - `times32.exe' saved [661728/661728]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/trebuc32.exe
--2010-10-06 17:18:48--  http://downloads.sourceforge.net/corefonts/trebuc32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2010-10-06 17:18:48--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2010-10-06 17:18:48--  http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Resolving cdnetworks-us-1.dl.sourceforge.net... 174.35.19.11
Connecting to cdnetworks-us-1.dl.sourceforge.net|174.35.19.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `trebuc32.exe'

100%[======================================>] 357,200      334K/s   in 1.0s    

2010-10-06 17:18:50 (334 KB/s) - `trebuc32.exe' saved [357200/357200]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/verdan32.exe
--2010-10-06 17:18:50--  http://downloads.sourceforge.net/corefonts/verdan32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following]
--2010-10-06 17:18:50--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following]
--2010-10-06 17:18:50--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/x-msdos-program]
Saving to: `verdan32.exe'

100%[======================================>] 351,992      388K/s   in 0.9s    

2010-10-06 17:18:51 (388 KB/s) - `verdan32.exe' saved [351992/351992]

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/webdin32.exe
--2010-10-06 17:18:51--  http://downloads.sourceforge.net/corefonts/webdin32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following]
--2010-10-06 17:18:51--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following]
--2010-10-06 17:18:51--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/x-msdos-program]
Saving to: `webdin32.exe'

100%[======================================>] 185,072      161K/s   in 1.1s    

2010-10-06 17:18:53 (161 KB/s) - `webdin32.exe' saved [185072/185072]

Executing cabextract -q --directory=/home/tpohl/.wine/drive_c/winetrickstmp /home/tpohl/.winetrickscache/arial32.exe
/home/tpohl/.winetrickscache/arial32.exe: library not compiled to support large files.
Executing cp -f /home/tpohl/.wine/drive_c/winetrickstmp/Arial.TTF /home/tpohl/.wine/drive_c/winetrickstmp/Arialbd.TTF /home/tpohl/.wine/drive_c/winetrickstmp/Arialbi.TTF /home/tpohl/.wine/drive_c/winetrickstmp/Ariali.TTF /home/tpohl/.wine/drive_c/windows/Fonts
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
Executing cabextract -q --directory=/home/tpohl/.wine/drive_c/winetrickstmp /home/tpohl/.winetrickscache/arialb32.exe
/home/tpohl/.winetrickscache/arialb32.exe: library not compiled to support large files.
Executing cp -f /home/tpohl/.wine/drive_c/winetrickstmp/AriBlk.TTF /home/tpohl/.wine/drive_c/windows/Fonts
err:process:__wine_kernel_init boot event wait timed out
Executing cabextract -q --directory=/home/tpohl/.wine/drive_c/winetrickstmp /home/tpohl/.winetrickscache/comic32.exe
/home/tpohl/.winetrickscache/comic32.exe: library not compiled to support large files.
Executing cp -f /home/tpohl/.wine/drive_c/winetrickstmp/Comic.TTF /home/tpohl/.wine/drive_c/winetrickstmp/Comicbd.TTF /home/tpohl/.wine/drive_c/windows/Fonts
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
Executing cabextract -q --directory=/home/tpohl/.wine/drive_c/winetrickstmp /home/tpohl/.winetrickscache/courie32.exe
/home/tpohl/.winetrickscache/courie32.exe: library not compiled to support large files.
Executing cp -f /home/tpohl/.wine/drive_c/winetrickstmp/cour.ttf /home/tpohl/.wine/drive_c/winetrickstmp/courbd.ttf /home/tpohl/.wine/drive_c/winetrickstmp/courbi.ttf /home/tpohl/.wine/drive_c/winetrickstmp/couri.ttf /home/tpohl/.wine/drive_c/windows/Fonts
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out

```
I issued the command to install allfonts well over 30 minutes ago. Most of the wait time isn't from downloading packages, but from the excessive time outs. I -believe- the culprit might be in this line of code seen before each series of timeouts. 
```
/home/tpohl/.winetrickscache/courie32.exe: library not compiled to support large files.

```
It appears to me that certain *font*.exe files are the cause. Ill continue my search for more answers and post here. 

For future reference, if anyone wants a reply from me the fastest way is a PM. Also, these and other packages are in the effort to install Ultima Online and Razor. UO installs and runs perfectly out of the box, and I **know** razor works because I've ran it before on Ubuntu. For anyone having issues with razor installing/running, I believe most of the causes are dotnet20 and font packages not installed or configured incorrectly.

---

### Post by Trizzy on 2010-10-07
My specific problem was solved by issuing this command. 
```
wineboot --update
``` 

I had the same symptoms as before. After attempting to download the allfonts and fontfix packages via winetricks, many other commands started giving the boot timeout response, and I had to wait several minutes to issue many common commands. The above code completely fixed the problem, where as before it took nearly 45 minutes to try and download allfonts, it now takes 2-3 minutes with download time.

---

### Post by xbartolo on 2010-12-22
I also had a similar problem and I found out that one of the dll that I had overwriten (rpcrt4.dll) did not have executing rights. I changed them and then it worked properly.

The command that i used was the following:

Go to the .wine/drive_c/windows/system32 directory
type "chmod a+x rpcrt4.dll"

Hope it helps

---

