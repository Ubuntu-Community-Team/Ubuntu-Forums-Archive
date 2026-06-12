---
title: "How DO I install solidedge v.20 on Ubuntu 8.10 Intrepid"
date: 2009-03-18
forum: Wine
---

### Post by vinodchintalapalli on 2009-03-18
I'm promoting Open sources in our college & trying to install SOLIDEDGE V.20 on Ubuntu Can any one help with wine

---

### Post by cogadh on 2009-03-18
It hasn't been tested in a while, but it appears that SolidEdge doesn't work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6023](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6023)

If you want to try experimenting with it to see if you can get it to work, we can help, but you need to provide more info. What version of Wine are you using? What have you done so far to try and get the app running? What kind of errors have you gotten from the installation? Providing some system specs may also help.

---

### Post by Jenkins1 on 2009-03-18
I am running wine 1.01 on Ubuntu 8.10 64 bit
I would really like to get it installed as it is the only program that I have to go to the dark side to use. I am aware of vmware and other emulators, but because my laptop came with vista pre-installed i don't have any install cds to make a virtual hard drive with.
The first problem is getting microsoft net frame work 2.0 installed. I have installed mono but that doesn't appear to help. I have also tried using crossover Linux which didn't let the install complete. Any help would be much apreciated.

Many thanks in advance

---

### Post by cogadh on 2009-03-18
For installing .NET, use [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by hikaricore on 2009-03-18
For god's sake, the phrase is HOW DO I, not HOW TO. HOW TO implies that you're telling people how to do it.
I'm getting so sick of people making this mistake and confusing other users.

---

### Post by Jenkins1 on 2009-03-19
Have installed net framework 2.0 and hence solid edge. How ever it will not open solid edge past the "logo" screen. It just grays out just like a program does when it doesn't respond. Any advice on HOW DO I get it to run correctly?

---

### Post by cogadh on 2009-03-19
We will need more information about what it is actually doing. Run it from the terminal and post Wine's output here, it may provide some helpful info.

---

### Post by Jenkins1 on 2009-03-19
The output is as follows

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1


The only bit that makes sense to me is the "not registered" bit. I have assigned the right license file to the program. I know this because if I had not assigned it then solid edge asks for it before it opens. This however many not be referring to the license file it is just a guess.

---

### Post by cogadh on 2009-03-19
Nope, its not referring to the user license at all. An OLE object class is not registered, meaning the program is trying to create or use an object that either doesn't exist or can't be created, according to Wine. Chances are, you need to install the Visual C++ Runtime (with winetricks) to get the correct functionality.

---

### Post by Jenkins1 on 2009-03-20
After installing Visual c++ runtime i go the following error.

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0x7bc932a4 "loader.c: loader_section" wait timed out in thread 002e, blocked by 0009, retrying (60 sec)

after installing all versions of Visual basic runtime and visual c++ the error is.

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Solid Edge V20\\Program\\Edge.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Solid Edge V20\\Program\\Edge.exe" failed, status c0000135

But now no loading screen. Installing all may have been a silly idea.

Thank you very much for you help so far.

---

### Post by keplerspeed on 2009-03-20
I have the same issue, currently working on it. I NEED to run solidedge in wine...

---

### Post by Jenkins1 on 2009-03-21
Also tried another install combination of 

MS Visual Basic 6 Runtime
Ms Visual C++ 2008 libraries
MS Visual J# 2.0 libraries

This is the error that I get.

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0x7bc932a4 "loader.c: loader_section" wait timed out in thread 007a, blocked by 0086, retrying (60 sec)

Any ideas?

---

### Post by Jenkins1 on 2009-03-22
bump

---

### Post by keplerspeed on 2009-06-02
Ok I have a little bit of functionality now...

I installed dotnet20 and corefonts via wine tricks. with the same result as Jenkins1, (error as in post #12).

Installing dcom98 with winetricks allows the solidedge program to start, with the starting window etc. Also, installing the falsh packages seems to help too. I can open pre existing parts for just a few seconds until SE crashed. The terminal output is:
```

fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:shell:DllCanUnloadNow stub
fixme:resource:GetGuiResources (0xffffffff,0): stub


```

The terminal output when SE crashes:
```

fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
wine: Call from 0xf591429 to unimplemented function ntdll.dll.RtlPushFrame, aborting
wine: Call from 0xf591a39 to unimplemented function ntdll.dll.RtlPopFrame, aborting
wine: Call from 0xf5d8b01 to unimplemented function ntdll.dll.RtlPopFrame, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:shell:URL_ParseUrl failed to parse L"SEERStartUp"
fixme:shell:URL_ParseUrl failed to parse L"Interop.SolidEdgeFramework"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic"
fixme:shell:URL_ParseUrl failed to parse L"SEERCommon"
fixme:shell:URL_ParseUrl failed to parse L"Interop.SEInstallDataLib"
err:ole:RPC_StartRemoting Couldn't register endpoint L"\\pipe\\OLE_0000005200000094"
err:ole:marshal_object object doesn't expose interface {b196b28f-bab4-101a-b69c-00aa00341d07}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {b196b283-bab4-101a-b69c-00aa00341d07}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic.resources"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:system:SystemParametersInfoW Unimplemented action: 4114 (SPI_GETMENUFADE)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  46041
  Current serial number in output stream:  46042

```

Where to now?

---

### Post by keplerspeed on 2009-06-04
And I can confirm that installing the c++ runtimes and VB runtimes dont have any effect. The most critical package from wintricks is dcom98, as this allows the program starting window to open instead of just hanging on the programs splash screen.

---

### Post by keplerspeed on 2009-06-05
Virtual box does the job... but it seems silly to run xp just for one program.

---

### Post by NightMKoder on 2009-06-06
Replacing wine's COM implementation is in general, an extremely bad idea. With a clean wine (ie no winetricks) do

WINEDEBUG=ole wine Edge.exe

Also make sure you're using the latest wine (1.1.23).

---

### Post by keplerspeed on 2009-06-07
Oh ok... I am not familiar with COM, .NET etc, just got a grasp from wiki. Cheers.

Ok ill give that a shot now and see what it does.

---

### Post by keplerspeed on 2009-06-07
Right. So a clean install of wine (1.1.23).

Next I try to run the installer on the cd:
```

wine autorun.exe

```

It notifies me that .NET needs to be installed, tries to do that for me but fails, just saying there has been an 'unexpected error'.

With winetricks I can sucessfully install .NET 2.0, and I can run the installer and install SE. Now, when running "WINEDEBUG=ole wine Edge.exe" to run the program, the output is (well, that first line is pretty much the same but repeats about 100 times, so I didnt copy it eh!)
```

trace:ole:__CLSIDFromString L"{FFC9F9AE-E87A-3252-8E25-B22423A40065}" -> 0xe0d804
trace:ole:COMCAT_CLSID_IEnumGUID_Release 
trace:ole:CoRegisterClassObject ({d0679910-7015-11d1-a3ed-00609726c3c7},0xeb8249c,0x00000004,0x00000001,0xeb82474)
trace:ole:CoMarshalInterface (0x197b58, {00000001-0000-0000-c000-000000000046}, 0xeb8249c, 0, (nil), MSHLFLAGS_TABLESTRONG)
trace:ole:CoGetStandardMarshal ({00000001-0000-0000-c000-000000000046},0xeb8249c,0,(nil),1,0xe0e560)
trace:ole:CoMarshalInterface Using standard marshaling
trace:ole:CoMarshalInterface Calling IMarshal::MarshalInterace
trace:ole:StdMarshalImpl_MarshalInterface (...,{00000001-0000-0000-c000-000000000046},...)
trace:ole:CoGetPSClsid () riid={00000001-0000-0000-c000-000000000046}, pclsid=0xe0e46c
trace:ole:__CLSIDFromString L"{00000320-0000-0000-C000-000000000046}" -> 0xe0e46c
trace:ole:CoGetPSClsid () Returning CLSID={00000320-0000-0000-c000-000000000046}
trace:ole:CoGetClassObject 
	CLSID:	{00000320-0000-0000-c000-000000000046},
	IID:	{d5f569d0-593b-101a-b569-08002b2dbf7a}
trace:ole:apartment_getclassobject calling ole32!DllGetClassObject
trace:ole:NdrDllGetClassObject ({00000320-0000-0000-c000-000000000046}, {d5f569d0-593b-101a-b569-08002b2dbf7a}, 0xe0e460, 0x7ea570c4, {00000320-0000-0000-c000-000000000046}, 0x7ea571fc)
trace:ole:CStdPSFactory_QueryInterface (0x7ea571fc)->QueryInterface({d5f569d0-593b-101a-b569-08002b2dbf7a},0xe0e460)
trace:ole:CStdPSFactory_CreateStub (0x7ea571fc)->CreateStub({00000001-0000-0000-c000-000000000046},0xeb8249c,0xe0e468)
trace:ole:FindProxyInfo found: ProxyInfo 0x7ea4f920 Index 0
trace:ole:CStdStubBuffer_Construct (0xeb8249c,0x7ea51e60,0x7ea571fc,0xe0e468) IClassFactory
trace:ole:CStdStubBuffer_Construct iid={00000001-0000-0000-c000-000000000046}
trace:ole:CStdStubBuffer_Construct vtbl=0x7ea51e70
trace:ole:CStdPSFactory_AddRef (0x7ea571fc)->AddRef()
trace:ole:CStdPSFactory_Release (0x7ea571fc)->Release()
trace:ole:get_stub_manager_from_object not found for object 0xeb8249c
trace:ole:marshal_object constructing new stub manager
trace:ole:new_stub_manager Created new stub manager (oid=11) at 0x199028 for object with IUnknown 0xeb8249c
trace:ole:stub_manager_new_ifstub oid=11, stubbuffer=0x171cf8, iptr=0xeb8249c, iid={00000001-0000-0000-c000-000000000046}
trace:ole:CStdStubBuffer_AddRef (0x171cf8)->AddRef()
trace:ole:stub_manager_new_ifstub ifstub 0x171d18 created with ipid {0000000d-0039-0037-a048-25ecb9b8e1ea}
trace:ole:NdrCStdStubBuffer_Release (0x171cf8)->Release()
trace:ole:stub_manager_ext_addref added 1 refs to 0x199028 (oid 11), rc is now 1
trace:ole:RPC_RegisterInterface ({00000001-0000-0000-c000-000000000046})
trace:ole:stub_manager_int_release after 1
trace:ole:CoMarshalInterface completed with hr 0x00000000
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d644 "loader.c: loader_section" wait timed out in thread 0090, blocked by 0039, retrying (60 sec)


```
The programs 'splash screen' now turns grey and hangs.

The WINEDEBUG thing.. what does it do? What does this output mean?

---

### Post by keplerspeed on 2009-06-11
[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

Under section 6.12:

"6.12. My application won't run, and the log shows lots of OLE errors

There's some chance that Wine's COM implementation has a bug or missing feature that's hurting your app. If so, you can sometimes work around this by using native DCOM98. See "How can I get a copy of some runtime library?" above. You can install OLE by running winetricks and selecting dcom98. If it helps, be sure to file a bug report. If it doesn't, you can undo the installation by running winecfg and removing the native library overrides for rpcrt4, ole32, and oleaut32. See also NativeDcom."

Lots of OLE errors is certainly what we are getting. Also, using dcom98 'helped', but not nearly functional. Comments?

I am looking into this [http://wiki.winehq.org/NativeDcom](http://wiki.winehq.org/NativeDcom) atm....

---

### Post by keplerspeed on 2009-06-11
Ok I have entered this:
```

WINEDEBUG="+ole,+olerelay,+rpc,+storage,+typelib,+typelib2,+variant" wine Edge.exe 2>&1 | tee logfile.txt  

```As explained here: [http://wiki.winehq.org/NativeDcom](http://wiki.winehq.org/NativeDcom)

Part of the log is here:
```

trace:ole:__CLSIDFromString L"{FFC9F9AE-E87A-3252-8E25-B22423A40065}" -> 0xe0d804
trace:ole:COMCAT_CLSID_IEnumGUID_Release 
trace:ole:CoRegisterClassObject ({d0679910-7015-11d1-a3ed-00609726c3c7},0xeb8249c,0x00000004,0x00000001,0xeb82474)
trace:ole:CoMarshalInterface (0x197bd0, {00000001-0000-0000-c000-000000000046}, 0xeb8249c, 0, (nil), MSHLFLAGS_TABLESTRONG)
trace:ole:CoGetStandardMarshal ({00000001-0000-0000-c000-000000000046},0xeb8249c,0,(nil),1,0xe0e560)
trace:ole:CoMarshalInterface Using standard marshaling
trace:storage:HGLOBALStreamImpl_Write (0x197bd0, 0xe0e564, 24, (nil))
trace:storage:HGLOBALStreamImpl_SetSize (0x197bd0, 24)
trace:ole:CoMarshalInterface Calling IMarshal::MarshalInterace
trace:ole:StdMarshalImpl_MarshalInterface (...,{00000001-0000-0000-c000-000000000046},...)
trace:ole:CoGetPSClsid () riid={00000001-0000-0000-c000-000000000046}, pclsid=0xe0e46c
trace:ole:__CLSIDFromString L"{00000320-0000-0000-C000-000000000046}" -> 0xe0e46c
trace:ole:CoGetPSClsid () Returning CLSID={00000320-0000-0000-c000-000000000046}
trace:ole:CoGetClassObject 
    CLSID:    {00000320-0000-0000-c000-000000000046},
    IID:    {d5f569d0-593b-101a-b569-08002b2dbf7a}
trace:ole:apartment_getclassobject calling ole32!DllGetClassObject
trace:ole:NdrDllGetClassObject ({00000320-0000-0000-c000-000000000046}, {d5f569d0-593b-101a-b569-08002b2dbf7a}, 0xe0e460, 0x7ea600c4, {00000320-0000-0000-c000-000000000046}, 0x7ea601fc)
trace:ole:CStdPSFactory_QueryInterface (0x7ea601fc)->QueryInterface({d5f569d0-593b-101a-b569-08002b2dbf7a},0xe0e460)
trace:ole:CStdPSFactory_CreateStub (0x7ea601fc)->CreateStub({00000001-0000-0000-c000-000000000046},0xeb8249c,0xe0e468)
trace:ole:FindProxyInfo found: ProxyInfo 0x7ea58920 Index 0
trace:ole:CStdStubBuffer_Construct (0xeb8249c,0x7ea5ae60,0x7ea601fc,0xe0e468) IClassFactory
trace:ole:CStdStubBuffer_Construct iid={00000001-0000-0000-c000-000000000046}
trace:ole:CStdStubBuffer_Construct vtbl=0x7ea5ae70
trace:ole:CStdPSFactory_AddRef (0x7ea601fc)->AddRef()
trace:ole:CStdPSFactory_Release (0x7ea601fc)->Release()
trace:ole:get_stub_manager_from_object not found for object 0xeb8249c
trace:ole:marshal_object constructing new stub manager
trace:ole:new_stub_manager Created new stub manager (oid=11) at 0x1990a0 for object with IUnknown 0xeb8249c
trace:ole:stub_manager_new_ifstub oid=11, stubbuffer=0x171d70, iptr=0xeb8249c, iid={00000001-0000-0000-c000-000000000046}
trace:ole:CStdStubBuffer_AddRef (0x171d70)->AddRef()
trace:rpc:UuidCreate {929c5ef9-819e-4670-9543-0dbcfcf9de30}
trace:ole:stub_manager_new_ifstub ifstub 0x171d90 created with ipid {0000000d-0009-0008-9543-0dbcfcf9de30}
trace:ole:NdrCStdStubBuffer_Release (0x171d70)->Release()
trace:ole:stub_manager_ext_addref added 1 refs to 0x1990a0 (oid 11), rc is now 1
trace:ole:RPC_RegisterInterface ({00000001-0000-0000-c000-000000000046})
trace:ole:stub_manager_int_release after 1
trace:storage:HGLOBALStreamImpl_Write (0x197bd0, 0xe0e4d4, 40, 0xe0e4d0)
trace:storage:HGLOBALStreamImpl_SetSize (0x197bd0, 64)
trace:ole:CoMarshalInterface completed with hr 0x00000000
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9d644 "loader.c: loader_section" wait timed out in thread 002e, blocked by 0009, retrying (60 sec)

```

Should I file a bug report to wine, and can anyone make sense of the log?

---

### Post by Jenkins1 on 2010-01-03
Ok not sure exactly what I have installed but this is my latest error ```
err:heap:HEAP_CreateSystemHeap system heap base address 0x80000000 not available
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!
err:heap:HEAP_GetPtr Invalid heap (nil)!

```

What should I install to fix this?

---

### Post by Jenkins1 on 2010-01-04
Ok if you install dcom98 and mscommoncontrols5.80 you get this error

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Solid Edge V20\\Program\\edge.exe") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"C:\\Program Files\\Solid Edge V20\\Program\\edge.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Solid Edge V20\\Program\\edge.exe" failed, status c0000135
```

Installing ms common controls 6 doesn't help

---

