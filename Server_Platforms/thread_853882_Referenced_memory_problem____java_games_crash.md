---
title: "Referenced memory problem    java games crash"
date: 2008-07-09
forum: Server Platforms
---

### Post by Spoonkitty on 2008-07-09
ok i play a java game called Runescape and it always crashes when im in the middle of playing it and im pretty sure its to do with java i debugged it and got this error report if this helps

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0x6d07a302, pid=3060, tid=5332
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b19 mixed mode, sharing windows-x86)
# Problematic frame:
# C  [awt.dll+0x7a302]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x04e2a800):  JavaThread "AWT-Windows" daemon [_thread_in_native, id=5332, stack(0x08340000,0x08440000)]

siginfo: ExceptionCode=0xc0000005, reading address 0x00000044

Registers:
EAX=0x00000000, EBX=0x00000001, ECX=0x00000000, EDX=0x0005037f
ESP=0x0843f714, EBP=0x0843f74c, ESI=0x04e2a8f4, EDI=0x00000000
EIP=0x6d07a302, EFLAGS=0x00010246

Top of Stack: (sp=0x0843f714)
0x0843f714:   00009813 04e2a8f4 6d0a112a 0005037f
0x0843f724:   0843f7b4 6d0a0d50 00000000 04e2b148
0x0843f734:   04e2b514 04e2a8f4 0843f724 0843f7d0
0x0843f744:   6d0b6158 00000001 0843f778 7e418734
0x0843f754:   00bf03ce 00009813 001a0030 0005037f
0x0843f764:   6d0a0d50 dcbaabcd 00000000 0843f7b4
0x0843f774:   6d0a0d50 0843f7e0 7e418816 6d0a0d50
0x0843f784:   00bf03ce 00009813 001a0030 0005037f 

Instructions: (pc=0x6d07a302)
0x6d07a2f2:   ce e8 58 c5 00 00 8b b6 34 01 00 00 85 f6 75 03
0x6d07a302:   8b 77 44 8b 44 24 0c 50 56 e8 60 9a 03 00 5f 5e 


Stack: [0x08340000,0x08440000],  sp=0x0843f714,  free space=1021k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [awt.dll+0x7a302]
C  [USER32.dll+0x8734]
C  [USER32.dll+0x8816]
C  [USER32.dll+0x18ea0]
C  [USER32.dll+0x18eec]
C  [ntdll.dll+0xe453]
C  [USER32.dll+0x9402]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x03e50000 JavaThread "Thread-15" daemon [_thread_blocked, id=4256, stack(0x0a8a0000,0x0a9a0000)]
  0x04dd8400 JavaThread "Thread-14" daemon [_thread_blocked, id=1924, stack(0x08940000,0x08a40000)]
  0x085eb400 JavaThread "Java Sound Event Dispatcher" daemon [_thread_blocked, id=728, stack(0x042c0000,0x043c0000)]
  0x086d5800 JavaThread "Thread-10" daemon [_thread_in_native, id=3180, stack(0x036c0000,0x037c0000)]
  0x04d84400 JavaThread "Thread-9" daemon [_thread_blocked, id=4468, stack(0x034c0000,0x035c0000)]
  0x04d85800 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=1848, stack(0x035c0000,0x036c0000)]
  0x086ccc00 JavaThread "thread applet-loader.class" [_thread_blocked, id=4772, stack(0x08c40000,0x08d40000)]
  0x08555c00 JavaThread "AWT-EventQueue-2" [_thread_in_native, id=4948, stack(0x08b40000,0x08c40000)]
  0x086ddc00 JavaThread "AWT-Shutdown" [_thread_blocked, id=544, stack(0x08a40000,0x08b40000)]
  0x08540400 JavaThread "CacheCleanUpThread" daemon [_thread_blocked, id=5384, stack(0x08740000,0x08840000)]
  0x04e36800 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=5052, stack(0x08440000,0x08540000)]
=>0x04e2a800 JavaThread "AWT-Windows" daemon [_thread_in_native, id=5332, stack(0x08340000,0x08440000)]
  0x04dce800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=2876, stack(0x08140000,0x08240000)]
  0x04d79c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=5984, stack(0x07f40000,0x08040000)]
  0x04d6c000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=5032, stack(0x07e40000,0x07f40000)]
  0x04d6ac00 JavaThread "Attach Listener" daemon [_thread_blocked, id=5740, stack(0x07d40000,0x07e40000)]
  0x04d69c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=5376, stack(0x07c40000,0x07d40000)]
  0x04d62000 JavaThread "Finalizer" daemon [_thread_blocked, id=5780, stack(0x07b40000,0x07c40000)]
  0x04d61000 JavaThread "Reference Handler" daemon [_thread_blocked, id=5632, stack(0x07a40000,0x07b40000)]
  0x03219800 JavaThread "main" [_thread_in_native, id=2408, stack(0x00030000,0x00130000)]

Other Threads:
  0x04d60000 VMThread [stack: 0x07940000,0x07a40000] [id=5272]
  0x04d8d000 WatcherThread [stack: 0x08040000,0x08140000] [id=2884]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 6016K, used 5794K [0x20960000, 0x20fe0000, 0x210c0000)
  eden space 5376K,  99% used [0x20960000, 0x20e9cf70, 0x20ea0000)
  from space 640K,  67% used [0x20ea0000, 0x20f0ba30, 0x20f40000)
  to   space 640K,   0% used [0x20f40000, 0x20f40000, 0x20fe0000)
 tenured generation   total 79440K, used 44408K [0x210c0000, 0x25e54000, 0x26960000)
   the space 79440K,  55% used [0x210c0000, 0x23c1e1c0, 0x23c1e200, 0x25e54000)
 compacting perm gen  total 12288K, used 5762K [0x26960000, 0x27560000, 0x2a960000)
   the space 12288K,  46% used [0x26960000, 0x26f00880, 0x26f00a00, 0x27560000)
    ro space 8192K,  62% used [0x2a960000, 0x2ae62a28, 0x2ae62c00, 0x2b160000)
    rw space 12288K,  52% used [0x2b160000, 0x2b7a86b8, 0x2b7a8800, 0x2bd60000)

Dynamic libraries:
0x00400000 - 0x00448000 	C:\Documents and Settings\Chris\Desktop\runescape.exe
0x7c900000 - 0x7c9af000 	C:\WINDOWS\system32\ntdll.dll
0x7c800000 - 0x7c8f6000 	C:\WINDOWS\system32\kernel32.dll
0x77dd0000 - 0x77e6b000 	C:\WINDOWS\system32\ADVAPI32.dll
0x77e70000 - 0x77f02000 	C:\WINDOWS\system32\RPCRT4.dll
0x77fe0000 - 0x77ff1000 	C:\WINDOWS\system32\Secur32.dll
0x5d090000 - 0x5d12a000 	C:\WINDOWS\system32\COMCTL32.dll
0x77f10000 - 0x77f59000 	C:\WINDOWS\system32\GDI32.dll
0x7e410000 - 0x7e4a1000 	C:\WINDOWS\system32\USER32.dll
0x763b0000 - 0x763f9000 	C:\WINDOWS\system32\comdlg32.dll
0x7c9c0000 - 0x7d1d7000 	C:\WINDOWS\system32\SHELL32.dll
0x77c10000 - 0x77c68000 	C:\WINDOWS\system32\msvcrt.dll
0x77f60000 - 0x77fd6000 	C:\WINDOWS\system32\SHLWAPI.dll
0x774e0000 - 0x7761d000 	C:\WINDOWS\system32\ole32.dll
0x77120000 - 0x771ab000 	C:\WINDOWS\system32\OLEAUT32.dll
0x7df70000 - 0x7df92000 	C:\WINDOWS\system32\oledlg.dll
0x73000000 - 0x73026000 	C:\WINDOWS\system32\WINSPOOL.DRV
0x76390000 - 0x763ad000 	C:\WINDOWS\system32\IMM32.DLL
0x773d0000 - 0x774d3000 	C:\WINDOWS\WinSxS\x86_Microsoft.Windows.Common-Controls_6595b64144ccf1df_6.0.2600.5512_x-ww_35d4ce83\comctl32.dll
0x5ad70000 - 0x5ada8000 	C:\WINDOWS\system32\uxtheme.dll
0x77690000 - 0x776b1000 	C:\WINDOWS\system32\NTMARTA.DLL
0x71bf0000 - 0x71c03000 	C:\WINDOWS\system32\SAMLIB.dll
0x76f60000 - 0x76f8c000 	C:\WINDOWS\system32\WLDAP32.dll
0x74720000 - 0x7476c000 	C:\WINDOWS\system32\MSCTF.dll
0x755c0000 - 0x755ee000 	C:\WINDOWS\system32\msctfime.ime
0x76fd0000 - 0x7704f000 	C:\WINDOWS\system32\CLBCATQ.DLL
0x77050000 - 0x77115000 	C:\WINDOWS\system32\COMRes.dll
0x77c00000 - 0x77c08000 	C:\WINDOWS\system32\VERSION.dll
0x42ef0000 - 0x434bd000 	C:\WINDOWS\system32\ieframe.dll
0x76bf0000 - 0x76bfb000 	C:\WINDOWS\system32\PSAPI.DLL
0x78000000 - 0x78045000 	C:\WINDOWS\system32\iertutil.dll
0x78050000 - 0x78120000 	C:\WINDOWS\system32\WININET.dll
0x00cb0000 - 0x00cb9000 	C:\WINDOWS\system32\Normaliz.dll
0x71ab0000 - 0x71ac7000 	C:\WINDOWS\system32\ws2_32.dll
0x71aa0000 - 0x71aa8000 	C:\WINDOWS\system32\WS2HELP.dll
0x01520000 - 0x01647000 	C:\WINDOWS\system32\urlmon.dll
0x77b40000 - 0x77b62000 	C:\WINDOWS\system32\appHelp.dll
0x435d0000 - 0x43944000 	C:\WINDOWS\system32\mshtml.dll
0x746c0000 - 0x746e9000 	C:\WINDOWS\system32\msls31.dll
0x75cf0000 - 0x75d81000 	C:\WINDOWS\system32\MLANG.dll
0x51860000 - 0x5188f000 	C:\Program Files\Common Files\Microsoft Shared\VS7DEBUG\pdm.dll
0x01b20000 - 0x01de5000 	C:\WINDOWS\system32\xpsp2res.dll
0x51710000 - 0x5173f000 	C:\Program Files\Common Files\Microsoft Shared\VS7DEBUG\msdbg2.dll
0x746f0000 - 0x7471a000 	C:\WINDOWS\system32\msimtf.dll
0x71a50000 - 0x71a8f000 	C:\WINDOWS\system32\mswsock.dll
0x662b0000 - 0x66308000 	C:\WINDOWS\system32\hnetcfg.dll
0x71a90000 - 0x71a98000 	C:\WINDOWS\System32\wshtcpip.dll
0x76ee0000 - 0x76f1c000 	C:\WINDOWS\system32\RASAPI32.dll
0x76e90000 - 0x76ea2000 	C:\WINDOWS\system32\rasman.dll
0x5b860000 - 0x5b8b5000 	C:\WINDOWS\system32\NETAPI32.dll
0x76eb0000 - 0x76edf000 	C:\WINDOWS\system32\TAPI32.dll
0x76e80000 - 0x76e8e000 	C:\WINDOWS\system32\rtutils.dll
0x76b40000 - 0x76b6d000 	C:\WINDOWS\system32\WINMM.dll
0x769c0000 - 0x76a74000 	C:\WINDOWS\system32\USERENV.dll
0x77c70000 - 0x77c94000 	C:\WINDOWS\system32\msv1_0.dll
0x76d60000 - 0x76d79000 	C:\WINDOWS\system32\iphlpapi.dll
0x68000000 - 0x68036000 	C:\WINDOWS\system32\rsaenh.dll
0x722b0000 - 0x722b5000 	C:\WINDOWS\system32\sensapi.dll
0x76fc0000 - 0x76fc6000 	C:\WINDOWS\system32\rasadhlp.dll
0x76f20000 - 0x76f47000 	C:\WINDOWS\system32\DNSAPI.dll
0x16080000 - 0x160a5000 	C:\Program Files\Bonjour\mdnsNSP.dll
0x1b000000 - 0x1b00c000 	C:\WINDOWS\system32\ImgUtil.dll
0x76380000 - 0x76385000 	C:\WINDOWS\system32\msimg32.dll
0x65700000 - 0x65718000 	C:\Program Files\Alwil Software\Avast4\AhAScr.dll
0x65000000 - 0x65037000 	C:\PROGRA~1\ALWILS~1\Avast4\Aavm4h.dll
0x64500000 - 0x64538000 	C:\PROGRA~1\ALWILS~1\Avast4\ashBase.dll
0x71ad0000 - 0x71ad9000 	C:\WINDOWS\system32\WSOCK32.dll
0x7c3a0000 - 0x7c41b000 	C:\WINDOWS\system32\MSVCP71.dll
0x7c340000 - 0x7c396000 	C:\WINDOWS\system32\MSVCR71.dll
0x64000000 - 0x64016000 	C:\PROGRA~1\ALWILS~1\Avast4\aswCmnOS.dll
0x64080000 - 0x6409f000 	C:\PROGRA~1\ALWILS~1\Avast4\aswCmnB.dll
0x64100000 - 0x6412f000 	C:\PROGRA~1\ALWILS~1\Avast4\aswCmnS.dll
0x64800000 - 0x6481c000 	C:\PROGRA~1\ALWILS~1\Avast4\ashTask.dll
0x64580000 - 0x64622000 	C:\PROGRA~1\ALWILS~1\Avast4\aswAux.dll
0x75c50000 - 0x75ccd000 	C:\WINDOWS\system32\jscript.dll
0x7e720000 - 0x7e7d0000 	C:\WINDOWS\system32\SXS.DLL
0x77a80000 - 0x77b15000 	C:\WINDOWS\system32\CRYPT32.dll
0x77b20000 - 0x77b32000 	C:\WINDOWS\system32\MSASN1.dll
0x72d20000 - 0x72d29000 	C:\WINDOWS\system32\wdmaud.drv
0x76c30000 - 0x76c5e000 	C:\WINDOWS\system32\WINTRUST.dll
0x76c90000 - 0x76cb8000 	C:\WINDOWS\system32\IMAGEHLP.dll
0x72d10000 - 0x72d18000 	C:\WINDOWS\system32\msacm32.drv
0x77be0000 - 0x77bf5000 	C:\WINDOWS\system32\MSACM32.dll
0x77bd0000 - 0x77bd7000 	C:\WINDOWS\system32\midimap.dll
0x767f0000 - 0x76817000 	C:\WINDOWS\system32\schannel.dll
0x77920000 - 0x77a13000 	C:\WINDOWS\system32\SETUPAPI.dll
0x6d430000 - 0x6d43a000 	C:\WINDOWS\system32\ddrawex.dll
0x73760000 - 0x737ab000 	C:\WINDOWS\system32\DDRAW.dll
0x73bc0000 - 0x73bc6000 	C:\WINDOWS\system32\DCIMAN32.dll
0x10100000 - 0x10111000 	C:\Program Files\Logitech\SetPoint\lgscroll.dll
0x78130000 - 0x781cb000 	C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.1433_x-ww_5cf844d2\MSVCR80.dll
0x7c420000 - 0x7c4a7000 	C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.1433_x-ww_5cf844d2\MSVCP80.dll
0x6d790000 - 0x6d7ad000 	C:\Program Files\Java\jre1.6.0_05\bin\wsdetect.dll
0x6d6b0000 - 0x6d6d1000 	C:\Program Files\Java\jre1.6.0_05\bin\npjpi160_05.dll
0x02500000 - 0x02556000 	C:\Program Files\Java\jre1.6.0_05\bin\msvcr71.dll
0x6d400000 - 0x6d41b000 	C:\Program Files\Java\jre1.6.0_05\bin\jpiexp.dll
0x6d1b0000 - 0x6d1c1000 	C:\Program Files\Java\jre1.6.0_05\bin\deploy.dll
0x76fb0000 - 0x76fb8000 	C:\WINDOWS\System32\winrnr.dll
0x751d0000 - 0x751ee000 	C:\WINDOWS\system32\wshbth.dll
0x6d450000 - 0x6d474000 	C:\Program Files\Java\jre1.6.0_05\bin\jpishare.dll
0x056f0000 - 0x05940000 	C:\PROGRA~1\Java\JRE16~2.0_0\bin\client\jvm.dll
0x6d270000 - 0x6d278000 	C:\PROGRA~1\Java\JRE16~2.0_0\bin\hpi.dll
0x6d770000 - 0x6d77c000 	C:\PROGRA~1\Java\JRE16~2.0_0\bin\verify.dll
0x6d310000 - 0x6d32f000 	C:\PROGRA~1\Java\JRE16~2.0_0\bin\java.dll
0x6d7b0000 - 0x6d7bf000 	C:\PROGRA~1\Java\JRE16~2.0_0\bin\zip.dll
0x6d000000 - 0x6d12e000 	C:\Program Files\Java\jre1.6.0_05\bin\awt.dll
0x6d210000 - 0x6d263000 	C:\Program Files\Java\jre1.6.0_05\bin\fontmanager.dll
0x6d3e0000 - 0x6d3f8000 	C:\Program Files\Java\jre1.6.0_05\bin\jpicom.dll
0x02e00000 - 0x02e3c000 	C:\Program Files\Java\jre1.6.0_05\bin\regutils.dll
0x7d1e0000 - 0x7d49c000 	C:\WINDOWS\system32\msi.dll
0x6d570000 - 0x6d583000 	C:\Program Files\Java\jre1.6.0_05\bin\net.dll
0x6d590000 - 0x6d599000 	C:\Program Files\Java\jre1.6.0_05\bin\nio.dll
0x6d180000 - 0x6d1a3000 	C:\Program Files\Java\jre1.6.0_05\bin\dcpr.dll
0x6d760000 - 0x6d76f000 	C:\Program Files\Java\jre1.6.0_05\bin\unpack.dll
0x6d480000 - 0x6d4a4000 	C:\Program Files\Java\jre1.6.0_05\bin\jsound.dll
0x6d4b0000 - 0x6d4b8000 	C:\Program Files\Java\jre1.6.0_05\bin\jsoundds.dll
0x73f10000 - 0x73f6c000 	C:\WINDOWS\system32\DSOUND.dll
0x73ee0000 - 0x73ee4000 	C:\WINDOWS\system32\KsUser.dll
0x6d340000 - 0x6d346000 	C:\Program Files\Java\jre1.6.0_05\bin\jawt.dll
0x10000000 - 0x1004d000 	C:\WINDOWS\.jagex_cache_32\runescape\jogl.dll
0x5ed00000 - 0x5edcc000 	C:\WINDOWS\system32\OPENGL32.dll
0x68b20000 - 0x68b40000 	C:\WINDOWS\system32\GLU32.dll
0x02ef0000 - 0x02ef5000 	C:\WINDOWS\.jagex_cache_32\runescape\jogl_awt.dll
0x08d40000 - 0x08f78000 	C:\WINDOWS\system32\iglicd32.dll
0x04530000 - 0x045b2000 	C:\WINDOWS\system32\igldev32.dll
0x42b90000 - 0x42c07000 	C:\WINDOWS\system32\mshtmled.dll

VM Arguments:
jvm_args: -Xbootclasspath/a:C:\PROGRA~1\Java\JRE16~2.0_0\lib\deploy.jar;C:\PROGRA~1\Java\JRE16~2.0_0\lib\plugin.jar -Xmx96m -Djavaplugin.maxHeapSize=96m -Xverify:remote -Djavaplugin.version=1.6.0_05 -Djavaplugin.nodotversion=160_05 -Dbrowser=sun.plugin -DtrustProxy=true -Dapplication.home=C:\PROGRA~1\Java\JRE16~2.0_0 -Djavaplugin.vm.options=-Djava.class.path=C:\PROGRA~1\Java\JRE16~2.0_0\classes -Xbootclasspath/a:C:\PROGRA~1\Java\JRE16~2.0_0\lib\deploy.jar;C:\PROGRA~1\Java\JRE16~2.0_0\lib\plugin.jar -Xmx96m -Djavaplugin.maxHeapSize=96m -Xverify:remote -Djavaplugin.version=1.6.0_05 -Djavaplugin.nodotversion=160_05 -Dbrowser=sun.plugin -DtrustProxy=true -Dapplication.home=C:\PROGRA~1\Java\JRE16~2.0_0  
java_command: <unknown>
Launcher Type: generic

Environment Variables:
CLASSPATH=C:\Program Files\Java\jre1.6.0_02\lib\ext\QTJava.zip
PATH=C:\PROGRA~1\Java\JRE16~2.0_0\bin;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\Program Files\QuickTime\QTSystem\;C:\Program Files\Common Files\Nero\Lib\;.
USERNAME=Chris
OS=Windows_NT
PROCESSOR_IDENTIFIER=x86 Family 15 Model 3 Stepping 4, GenuineIntel



---------------  S Y S T E M  ---------------

OS: Windows XP Build 2600 Service Pack 3

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 3 stepping 4, cmov, cx8, fxsr, mmx, sse, sse2, sse3

Memory: 4k page, physical 1039344k(179176k free), swap 2502884k(1665996k free)

vm_info: Java HotSpot(TM) Client VM (10.0-b19) for windows-x86 JRE (1.6.0_05-b13), built on Feb 22 2008 01:16:53 by "java_re" with MS VC++ 7.1

time: Wed Jul 09 13:52:40 2008
elapsed time: 10268 seconds


``` please let me know how i can fix this error it is getting irritating...

---

### Post by windependence on 2008-07-09
Is this on a Windoze box?

> ---------------  S Y S T E M  ---------------

OS: Windows XP Build 2600 Service Pack 3

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 3 stepping 4, cmov, cx8, fxsr, mmx, sse, sse2, sse3

-Tim

---

### Post by Spoonkitty on 2008-07-09
> **windependence said:**
> Is this on a Windoze box?



-Tim

wat do u mean?

---

### Post by windependence on 2008-07-09
The error you posted mentions all kinds of Windoze dlls and say the OS is Windoze XP. I am afraid this is a Linux forum.

-Tim

---

### Post by Spoonkitty on 2008-07-09
> **windependence said:**
> The error you posted mentions all kinds of Windoze dlls and say the OS is Windoze XP. I am afraid this is a Linux forum.

-Tim

oh dam can u revert me to a website that could help me with this problem

---

### Post by windependence on 2008-07-09
[http://forum.runescape.com/forums.ws](http://forum.runescape.com/forums.ws)

-Tim

---

