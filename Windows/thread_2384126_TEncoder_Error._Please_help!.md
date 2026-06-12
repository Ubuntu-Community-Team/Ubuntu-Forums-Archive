---
title: "TEncoder Error. Please help!"
date: 2018-02-02
forum: Windows
---

### Post by capestorm on 2018-02-02
I installed TEncoder two days ago and it worked well twice (as I was still learning the software). Today I wanted to use it for an encoding project. Clicking the desktop icon delivered the following message: "An error occured in the application". I uninstalled and reinstalled the software as well as rebooted my laptop. But the error message still appears and I am unable to use the software. 

I'm attaching data from the "bug report". Please guide me through this problem as I am not "tech-savy". 

```
date/time          : 2018-02-02, 10:31:59, 769ms
computer name      : FRANKS-PC
user name          : Franks
operating system   : Windows 8 x64 build 9200
system language    : English
system up time     : 1 day 22 hours
program up time    : 2 seconds
processors         : 4x Intel(R) Core(TM) i3-3217U CPU @ 1.80GHz
physical memory    : 237/3982 MB (free/total)
free disk space    : (C:) 7,32 GB
display mode       : 1366x768, 32 bit
process id         : $4604
allocated memory   : 56,97 MB
largest free block : 1,02 GB
executable         : TEncoder.exe
exec. date/time    : 2014-02-09 14:26
version            : 3.7.0.3964
compiled with      : Delphi XE4
madExcept version  : 4.0.9
callstack crc      : $d277efab, $c16ca2f8, $c16ca2f8
contact name       : Ashley
contact email      : [EMAIL="lightworker.za@gmail.com"]lightworker.za@gmail.com[/EMAIL]
exception number   : 1
exception class    : EAccessViolation
exception message  : Access violation at address 007C7F2D in module 'TEncoder.exe'. Read of address 00000000.

main thread ($15c0):
007c7f2d +036d TEncoder.exe sSkinProvider            TacMinTimer.TimeHandler
00763202 +0002 TEncoder.exe acThdTimer               TacThreadedTimer.TimeEvent
00763173 +000f TEncoder.exe acThdTimer               TacThreadedTimer.Timer
00763220 +0018 TEncoder.exe acThdTimer               TacThreadedTimer.OnTimer2
0063208f +000f TEncoder.exe Vcl.ExtCtrls             TTimer.Timer
00631f73 +002b TEncoder.exe Vcl.ExtCtrls             TTimer.WndProc
0053f228 +0014 TEncoder.exe System.Classes           StdWndProc
778a8c1b +000b user32.dll                            DispatchMessageW
00693287 +00f3 TEncoder.exe Vcl.Forms                TApplication.ProcessMessage
006932b2 +000a TEncoder.exe Vcl.Forms                TApplication.ProcessMessages
00870859 +0105 TEncoder.exe UnitMain        4235 +12 TMainForm.LoadProfiles
0086e5b3 +003b TEncoder.exe UnitMain        3414  +8 TMainForm.FormShow
0081b37c +0070 TEncoder.exe JvFormPlacement          TJvFormPlacement.FormShow
006891d5 +0015 TEncoder.exe Vcl.Forms                TCustomForm.DoShow
0068d81d +00a9 TEncoder.exe Vcl.Forms                TCustomForm.CMShowingChanged
005b5715 +02bd TEncoder.exe Vcl.Controls             TControl.WndProc
005ba1d1 +05c5 TEncoder.exe Vcl.Controls             TWinControl.WndProc
00689bf9 +060d TEncoder.exe Vcl.Forms                TCustomForm.WndProc
007affdf +193f TEncoder.exe sSkinProvider            TsSkinProvider.NewWndProc
005b5350 +0024 TEncoder.exe Vcl.Controls             TControl.Perform
00816880 +00a4 TEncoder.exe JvWndProcHook            TJvHookInfos.WindowProc
005b5350 +0024 TEncoder.exe Vcl.Controls             TControl.Perform
005b95bd +010d TEncoder.exe Vcl.Controls             TWinControl.UpdateShowing
005b96cc +00bc TEncoder.exe Vcl.Controls             TWinControl.UpdateControlState
005bc282 +0026 TEncoder.exe Vcl.Controls             TWinControl.CMVisibleChanged
005b5715 +02bd TEncoder.exe Vcl.Controls             TControl.WndProc
005ba1d1 +05c5 TEncoder.exe Vcl.Controls             TWinControl.WndProc
00689bf9 +060d TEncoder.exe Vcl.Forms                TCustomForm.WndProc
007b314e +4aae TEncoder.exe sSkinProvider            TsSkinProvider.NewWndProc
00816880 +00a4 TEncoder.exe JvWndProcHook            TJvHookInfos.WindowProc
005b5350 +0024 TEncoder.exe Vcl.Controls             TControl.Perform
005b3d42 +0026 TEncoder.exe Vcl.Controls             TControl.SetVisible
00689476 +003a TEncoder.exe Vcl.Forms                TCustomForm.SetVisible
006935ef +00b3 TEncoder.exe Vcl.Forms                TApplication.Run
008c44a9 +0119 TEncoder.exe TEncoder          52 +18 initialization
76628652 +0022 KERNEL32.DLL                          BaseThreadInitThunk

thread $2d00:
77a3ec9d +07d RPCRT4.dll    RpcBindingFree
77a17bb1 +621 RPCRT4.dll    NdrClientCall2
77ec3f62 +0a2 ntdll.dll     bsearch
77ec3f2b +06b ntdll.dll     bsearch
77e9122d +03d ntdll.dll     RtlAppendUnicodeStringToString
77ecc193 +023 ntdll.dll     vswprintf_s
77ecc152 +012 ntdll.dll     swprintf_s
77eb78d7 +027 ntdll.dll     RtlIpv4AddressToStringW
77eb7881 +061 ntdll.dll     RtlIpv4AddressToStringExW
76b2701e +1ae WS2_32.dll    getsockopt
77ecbcc3 +023 ntdll.dll     vsprintf_s
77ecbc82 +012 ntdll.dll     sprintf_s
77ecc193 +023 ntdll.dll     vswprintf_s
77ecc152 +012 ntdll.dll     swprintf_s
77eb78d7 +027 ntdll.dll     RtlIpv4AddressToStringW
77eb7881 +061 ntdll.dll     RtlIpv4AddressToStringExW
6ef2047c +06c mswsock.dll   Tcpip4_WSHAddressToString
76628652 +022 KERNEL32.DLL  BaseThreadInitThunk

thread $46cc:
76628652 +22 KERNEL32.DLL  BaseThreadInitThunk

thread $3358 (TJvHttpUrlGrabberThread):
7639ebe3 +093 KERNELBASE.dll                         WaitForSingleObjectEx
73ecb503 +0f3 wininet.dll                            HttpSendRequestW
0083068e +3ce TEncoder.exe   JvUrlGrabbers    681 +0 TJvHttpUrlGrabberThread.Grab
008353cb +067 TEncoder.exe   JvUrlListGrabber        TJvCustomUrlGrabberThread.Execute
004a8f83 +02b TEncoder.exe   madExcept               HookedTThreadExecute
0053bb1a +042 TEncoder.exe   System.Classes          ThreadProc
00409f10 +028 TEncoder.exe   System           236 +0 ThreadWrapper
004a8e69 +00d TEncoder.exe   madExcept               CallThreadProcSafe
004a8ece +032 TEncoder.exe   madExcept               ThreadExceptFrame
76628652 +022 KERNEL32.DLL                           BaseThreadInitThunk
>> created by thread $3114 at:
0083527f +037 TEncoder.exe   JvUrlListGrabber        TJvCustomUrlGrabberThread.Create

thread $c04:
76628652 +22 KERNEL32.DLL  BaseThreadInitThunk

thread $3e08:
76628652 +22 KERNEL32.DLL  BaseThreadInitThunk

thread $4644:
76628652 +22 KERNEL32.DLL  BaseThreadInitThunk

modules:
00400000 TEncoder.exe                3.7.0.3964          C:\Program Files (x86)\TEncoder Video Converter
10000000 MediaInfo.dll               0.7.61.0            C:\Program Files (x86)\TEncoder Video Converter
51be0000 explorerframe.dll           6.2.16299.98        C:\WINDOWS\system32
591c0000 msvcp110_win.dll            6.2.16299.15        C:\WINDOWS\SYSTEM32
59270000 AEPIC.dll                   6.2.16299.15        C:\WINDOWS\SYSTEM32
593b0000 CLDAPI.dll                  6.2.16299.192       C:\WINDOWS\SYSTEM32
59680000 policymanager.dll           6.2.16299.15        C:\WINDOWS\SYSTEM32
596f0000 thumbcache.dll              6.2.16299.15        C:\Windows\System32
64cd0000 FaultRep.dll                6.2.16299.15        C:\WINDOWS\SYSTEM32
6df10000 dwmapi.dll                  6.2.16299.15        C:\WINDOWS\system32
6e720000 propsys.dll                 7.0.16299.15        C:\WINDOWS\system32
6e8a0000 msiso.dll                   11.0.16299.192      C:\WINDOWS\SYSTEM32
6e900000 urlmon.dll                  11.0.16299.192      C:\WINDOWS\SYSTEM32
6ed20000 ondemandconnroutehelper.dll 6.2.16299.15        C:\WINDOWS\SYSTEM32
6eee0000 rasadhlp.dll                6.2.16299.15        C:\Windows\System32
6eef0000 mswsock.dll                 6.2.16299.15        C:\WINDOWS\system32
6ef50000 iertutil.dll                11.0.16299.192      C:\WINDOWS\SYSTEM32
712a0000 DPAPI.DLL                   6.2.16299.15        C:\WINDOWS\SYSTEM32
712f0000 FLTLIB.DLL                  6.2.16299.15        C:\WINDOWS\SYSTEM32
71470000 olepro32.dll                6.2.16299.15        C:\WINDOWS\SYSTEM32
71920000 WindowsCodecs.dll           6.2.16299.15        C:\WINDOWS\SYSTEM32
71b10000 WINNSI.DLL                  6.2.16299.15        C:\WINDOWS\SYSTEM32
72030000 winspool.drv                6.2.16299.15        C:\WINDOWS\SYSTEM32
722a0000 ntmarta.dll                 6.2.16299.15        C:\WINDOWS\SYSTEM32
722f0000 uxtheme.dll                 6.2.16299.15        C:\WINDOWS\system32
72370000 comctl32.dll                6.10.16299.192      C:\WINDOWS\WinSxS\x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.16299.192_none_5d760485a7e0eb41
72590000 msimg32.dll                 6.2.16299.15        C:\WINDOWS\SYSTEM32
72a80000 mpr.dll                     6.2.16299.15        C:\WINDOWS\SYSTEM32
72aa0000 aswhookx.dll                17.9.3.19960        C:\Program Files\AVAST Software\Avast
73830000 bcrypt.dll                  6.2.16299.125       C:\WINDOWS\SYSTEM32
73880000 cryptsp.dll                 6.2.16299.15        C:\WINDOWS\SYSTEM32
73960000 dbgcore.DLL                 6.2.16299.15        C:\WINDOWS\SYSTEM32
73990000 dbghelp.dll                 6.2.16299.15        C:\WINDOWS\SYSTEM32
73b60000 WINSTA.dll                  6.2.16299.15        C:\WINDOWS\SYSTEM32
73be0000 IPHLPAPI.DLL                6.2.16299.15        C:\WINDOWS\SYSTEM32
73c10000 DNSAPI.dll                  6.2.16299.19        C:\WINDOWS\SYSTEM32
73cb0000 winhttp.dll                 6.2.16299.192       C:\WINDOWS\SYSTEM32
73d70000 wininet.dll                 11.0.16299.192      C:\WINDOWS\SYSTEM32
745d0000 shell32.dll                 6.2.16299.192       C:\WINDOWS\System32
75a00000 version.dll                 6.2.16299.15        C:\WINDOWS\SYSTEM32
75a30000 wsock32.dll                 6.2.16299.15        C:\WINDOWS\SYSTEM32
75b00000 wtsapi32.dll                6.2.16299.15        C:\WINDOWS\SYSTEM32
75ba0000 CRYPTBASE.dll               6.2.16299.15        C:\WINDOWS\System32
75bb0000 SspiCli.dll                 6.2.16299.192       C:\WINDOWS\System32
75bd0000 clbcatq.dll                 2001.12.10941.16384 C:\WINDOWS\System32
76090000 advapi32.dll                6.2.16299.192       C:\WINDOWS\System32
76170000 ole32.dll                   6.2.16299.192       C:\WINDOWS\System32
76270000 cfgmgr32.dll                6.2.16299.15        C:\WINDOWS\System32
762b0000 KERNELBASE.dll              6.2.16299.15        C:\WINDOWS\System32
76490000 IMM32.DLL                   6.2.16299.15        C:\WINDOWS\System32
764c0000 MSCTF.dll                   6.2.16299.19        C:\WINDOWS\System32
76610000 KERNEL32.DLL                6.2.16299.15        C:\WINDOWS\System32
76850000 gdi32full.dll               6.2.16299.98        C:\WINDOWS\System32
769b0000 powrprof.dll                6.2.16299.15        C:\WINDOWS\System32
76a00000 sechost.dll                 6.2.16299.15        C:\WINDOWS\System32
76a50000 msvcrt.dll                  7.0.16299.125       C:\WINDOWS\System32
76b10000 WS2_32.dll                  6.2.16299.15        C:\WINDOWS\System32
76b80000 kernel.appcore.dll          6.2.16299.15        C:\WINDOWS\System32
76ba0000 shlwapi.dll                 6.2.16299.15        C:\WINDOWS\System32
76bf0000 oleaut32.dll                6.2.16299.15        C:\WINDOWS\System32
76c90000 windows.storage.dll         6.2.16299.192       C:\WINDOWS\System32
77270000 GDI32.dll                   6.2.16299.15        C:\WINDOWS\System32
772a0000 comdlg32.dll                6.2.16299.125       C:\WINDOWS\System32
77380000 CRYPT32.dll                 6.2.16299.15        C:\WINDOWS\System32
77510000 imagehlp.dll                6.2.16299.15        C:\WINDOWS\System32
77530000 NSI.dll                     6.2.16299.15        C:\WINDOWS\System32
775a0000 MSASN1.dll                  6.2.16299.15        C:\WINDOWS\System32
77610000 profapi.dll                 6.2.16299.15        C:\WINDOWS\System32
77680000 ucrtbase.dll                6.2.16299.125       C:\WINDOWS\System32
77830000 bcryptPrimitives.dll        6.2.16299.98        C:\WINDOWS\System32
77890000 user32.dll                  6.2.16299.125       C:\WINDOWS\System32
77a10000 RPCRT4.dll                  6.2.16299.192       C:\WINDOWS\System32
77ad0000 shcore.dll                  6.2.16299.15        C:\WINDOWS\System32
77b60000 combase.dll                 6.2.16299.15        C:\WINDOWS\System32
77db0000 win32u.dll                  6.2.16299.15        C:\WINDOWS\System32
77dd0000 msvcp_win.dll               6.2.16299.15        C:\WINDOWS\System32
77e50000 ntdll.dll                   6.2.16299.192       C:\WINDOWS\SYSTEM32

cpu registers:
eax = 00000000
ebx = 0894a400
ecx = 00000000
edx = 00000000
esi = 000002ab
edi = 00000188
eip = 007c7f2d
esp = 0019f3b8
ebp = 0019f438

stack dump:
0019f3b8  20 00 cc 00 3c b1 13 3b - b1 33 85 40 63 27 76 62   ...<..;.3.@c'vb
0019f3c8  27 76 7b 40 43 ca 7e 00 - 80 c4 99 04 00 00 00 00  'v{@C.~.........
0019f3d8  00 00 00 00 00 00 00 00 - df 02 00 00 dc 01 00 00  ................
0019f3e8  ff 00 00 00 80 20 63 00 - 58 0d 99 09 80 20 63 00  ..... c.X.... c.
0019f3f8  00 a4 94 08 05 32 76 00 - 76 31 76 00 00 a4 94 08  .....2v.v1v.....
0019f408  25 32 76 00 10 c9 9e 04 - 92 20 63 00 40 f4 19 00  %2v...... c.@...
0019f418  78 1f 63 00 60 f5 19 00 - 98 93 40 00 38 f4 19 00  x.c.`.....@.8...
0019f428  58 0d 99 09 da 0c 10 00 - 00 00 00 00 10 c9 9e 04  X...............
0019f438  50 f4 19 00 2a f2 53 00 - 13 01 00 00 01 00 00 00  P...*.S.........
0019f448  00 00 00 00 00 00 00 00 - 7c f4 19 00 bb e0 8a 77  ........|......w
0019f458  da 0c 10 00 13 01 00 00 - 01 00 00 00 00 00 00 00  ................
0019f468  da 0c 10 00 cd ab ba dc - 00 00 00 00 58 0d 99 09  ............X...
0019f478  da 0c 10 00 a0 f4 19 00 - 49 88 8b 77 58 0d 99 09  ........I..wX...
0019f488  da 0c 10 00 13 01 00 00 - 01 00 00 00 00 00 00 00  ................
0019f498  00 00 00 00 da 0c 10 00 - 70 f5 19 00 45 b1 8b 77  ........p...E..w
0019f4a8  13 01 00 00 01 00 00 00 - 00 00 00 00 09 07 65 fc  ..............e.
0019f4b8  00 00 00 00 0c f6 19 00 - 60 65 61 03 71 07 65 fc  ........`ea.q.e.
0019f4c8  24 00 00 00 01 00 00 00 - 00 00 00 00 00 00 00 00  $...............
0019f4d8  30 00 00 00 ff ff ff ff - ff ff ff ff 25 b0 8b 77  0...........%..w
0019f4e8  00 00 00 00 00 00 00 00 - c4 f4 19 00 00 00 00 00  ................

disassembling:
00870754      public UnitMain.TMainForm.LoadProfiles:  ; function entry point
00870754 4223   push    ebp
00870755        mov     ebp, esp
00870757        add     esp, -$288
0087075d        push    ebx
0087075e        push    esi
0087075f        xor     ecx, ecx
00870761        mov     [ebp-$288], ecx
00870767        mov     [ebp-$284], ecx
0087076d        mov     [ebp-$27c], ecx
00870773        mov     [ebp-$280], ecx
00870779        mov     [ebp-$274], ecx
0087077f        mov     [ebp-$278], ecx
00870785        mov     ebx, edx
00870787        mov     esi, eax
00870789        lea     eax, [ebp-$270]
0087078f        mov     edx, [$449ed8]
00870795        call    -$464e7a ($40b920)     ; System.@InitializeRecord
00870795
0087079a        xor     eax, eax
0087079c        push    ebp
0087079d        push    $870953                ; System.@HandleFinally
008707a2        push    dword ptr fs:[eax]
008707a5        mov     fs:[eax], esp
008707a8 4225   lea     edx, [ebp-$278]
008707ae        mov     eax, [$8d7108]
008707b3        mov     eax, [eax]
008707b5        call    -$1dc9d2 ($693de8)     ; Vcl.Forms.TApplication.GetExeName
008707b5
008707ba        mov     eax, [ebp-$278]
008707c0        lea     edx, [ebp-$274]
008707c6        call    -$41d4bf ($45330c)     ; System.SysUtils.ExtractFileDir
008707c6
008707cb        lea     eax, [ebp-$274]
008707d1        mov     edx, $87096c
008707d6        call    -$4655cb ($40b210)     ; System.@UStrCat
008707d6
008707db        mov     eax, [ebp-$274]
008707e1        mov     dl, 1
008707e3        call    -$41d9c8 ($452e20)     ; System.SysUtils.DirectoryExists
008707e3
008707e8        test    al, al
008707ea        jz      loc_87090c
008707ea
008707f0 4228   mov     eax, [ebx+$2c4]
008707f6        mov     edx, [eax]
008707f8        call    dword ptr [edx+$48]
008707f8
008707fb 4230   lea     edx, [ebp-$280]
00870801        mov     eax, [$8d7108]
00870806        mov     eax, [eax]
00870808        call    -$1dca25 ($693de8)     ; Vcl.Forms.TApplication.GetExeName
00870808
0087080d        mov     eax, [ebp-$280]
00870813        lea     edx, [ebp-$27c]
00870819        call    -$41d512 ($45330c)     ; System.SysUtils.ExtractFileDir
00870819
0087081e        lea     eax, [ebp-$27c]
00870824        mov     edx, $87096c
00870829        call    -$46561e ($40b210)     ; System.@UStrCat
00870829
0087082e        mov     eax, [ebp-$27c]
00870834        call    -$41ce05 ($453a34)     ; System.SysUtils.SetCurrentDir
00870834
00870839 4232   lea     ecx, [ebp-$270]
0087083f        mov     edx, $1ff
00870844        mov     eax, $87098c
00870849        call    -$41d7f6 ($453058)     ; System.SysUtils.FindFirst
00870849
0087084e        test    eax, eax
00870850        jnz     loc_87089c
00870850
00870852      loc_870852:
00870852 4235   mov     eax, [$8d7108]
00870857        mov     eax, [eax]
00870859      > call    -$1dd5b6 ($6932a8)     ; Vcl.Forms.TApplication.ProcessMessages
00870859
0087085e 4236   lea     ecx, [ebp-$284]
00870864        xor     edx, edx
00870866        mov     eax, [ebp-$25c]
0087086c        call    -$41d645 ($45322c)     ; System.SysUtils.ChangeFileExt
0087086c
00870871        mov     edx, [ebp-$284]
00870877        mov     eax, [ebx+$2c4]
0087087d        mov     ecx, [eax]
0087087f        call    dword ptr [ecx+$3c]
0087087f
00870882 4237   lea     eax, [ebp-$270]
00870888        call    -$41d7e5 ($4530a8)     ; System.SysUtils.FindNext
00870888
0087088d        test    eax, eax
0087088f        jz      loc_870852
0087088f
00870891 4238   lea     eax, [ebp-$270]
00870897        call    -$41d7d0 ($4530cc)     ; System.SysUtils.FindClose
00870897
0087089c      loc_87089c:
0087089c 4241   mov     eax, [esi+$594]
008708a2        call    -$41ce73 ($453a34)     ; System.SysUtils.SetCurrentDir
008708a2
008708a7 4243   lea     ecx, [ebp-$270]
008708ad        mov     edx, $1ff
008708b2        mov     eax, $87098c
008708b7        call    -$41d864 ($453058)     ; System.SysUtils.FindFirst
008708b7
008708bc        test    eax, eax
008708be        jnz     loc_870924
008708be
008708c0      loc_8708c0:
008708c0 4246   mov     eax, [$8d7108]
008708c5        mov     eax, [eax]
008708c7        call    -$1dd624 ($6932a8)     ; Vcl.Forms.TApplication.ProcessMessages
008708c7
008708cc 4247   lea     ecx, [ebp-$288]
008708d2        xor     edx, edx
008708d4        mov     eax, [ebp-$25c]
008708da        call    -$41d6b3 ($45322c)     ; System.SysUtils.ChangeFileExt
008708da
008708df        mov     edx, [ebp-$288]
008708e5        mov     eax, [ebx+$2c4]
008708eb        mov     ecx, [eax]
008708ed        call    dword ptr [ecx+$3c]
008708ed
008708f0 4248   lea     eax, [ebp-$270]
008708f6        call    -$41d853 ($4530a8)     ; System.SysUtils.FindNext
008708f6
008708fb        test    eax, eax
008708fd        jz      loc_8708c0
008708fd
008708ff 4249   lea     eax, [ebp-$270]
00870905        call    -$41d83e ($4530cc)     ; System.SysUtils.FindClose
00870905
0087090a        jmp     loc_870924
0087090a
0087090a      ; ---------------------------------------------------------
0087090a
0087090c      loc_87090c:
0087090c 4255   push    $10
0087090e        mov     ecx, $870998
00870913        mov     edx, $8709a4
00870918        mov     eax, [$8d7108]
0087091d        mov     eax, [eax]
0087091f        call    -$1dd1ac ($693778)     ; Vcl.Forms.TApplication.MessageBox
0087091f
00870924      loc_870924:
00870924 4258   xor     eax, eax
00870926        pop     edx
00870927        pop     ecx
00870928        pop     ecx
00870929        mov     fs:[eax], edx
0087092c        push    $87095a
00870929
00870931      loc_870931:
00870931        lea     eax, [ebp-$288]
00870937        mov     edx, 6
0087093c        call    -$466881 ($40a0c0)     ; System.@UStrArrayClr
0087093c
00870941        lea     eax, [ebp-$270]
00870947        mov     edx, [$449ed8]
0087094d        call    -$464f5a ($40b9f8)     ; System.@FinalizeRecord
0087094d
00870952        ret
00870952
00870952      ; ---------------------------------------------------------
00870952
00870953        jmp     -$467410 ($409548)     ; System.@HandleFinally
00870953
00870958        jmp     loc_870931
00870958
00870958      ; ---------------------------------------------------------
00870958
0087095a        pop     esi
0087095b        pop     ebx
0087095c        mov     esp, ebp
0087095e        pop     ebp
0087095f        ret
```

---

### Post by Yellow Pasque on 2018-02-02
> operating system : Windows 8 x64 build 9200

You're in the wrong place: [https://ubuntuforums.org/forumdisplay.php?f=170](https://ubuntuforums.org/forumdisplay.php?f=170)

---

### Post by wildmanne39 on 2018-02-02
*Thread moved to **Windows, a more appropriate forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mc4man on 2018-02-02
Keep going backwards in versions until you find a stable one, noting that this program has been abandoned so no more fixes..
[https://www.videohelp.com/software/TEncoder/old-versions#downloadold](https://www.videohelp.com/software/TEncoder/old-versions#downloadold)
(- there are much better alternatives to this in linux so certainly there are in windows too.

---

