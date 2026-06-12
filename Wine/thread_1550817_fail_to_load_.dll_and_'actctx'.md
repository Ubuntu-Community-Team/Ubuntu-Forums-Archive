---
title: "fail to load .dll and 'actctx'"
date: 2010-08-11
forum: Wine
---

### Post by beew on 2010-08-11
Hi,

I am trying to run WinBUGS (a Markov Chain Monte Carlo sampler that works with R but only in windows) in Wine.

Basically, it works in Wine1.0 even though there are error messages.

It doesn't run in Wine1.2 and higher. When trying to start WinBUGS in the terminal it gives the same error messages as in Wine1.0 but in the newer wine WinBUGS simply crashes.

The error message is 
> 
fixme:keyboard:RegisterHotKey (0x20056,13,0x00000002,3): stub
err:ole:CoGetClassObject class {0003000a-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject class {0003000a-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {0003000a-0000-0000-c000-000000000046} could be created for context 0x3The fixme line apparently is harmless. It is the others that kill WinBUGS on the start up in wine1.2 and higher.

So I looked around the internet and found out the meaning of the error message. Wine is complaining about a missing DLL. So I searched the registry in a Windows machine and found out the DLL in question is pbrush.dll (print brush, which Windows has stopped using for quite a while) So I scourged the internet to find a copy of pbrush.dll , downloaded it and put in .wine/drive_c/windows/system32
 
I tried to register it with 

```
$ wine regsvr32 pbrush.dll
```But wine says it failed to load .dll.  Any insight?


Now I found on the internet another proposed remedy without manually downloading and activating pbrush.dll. It is to install dcom98 using winetricks. I did that and now WinBUGS doesn't crash in wine1.3 anymore. However, when I tried to run it, it seems to be stuck (it works in  wine1.0 without dcom98 and the error message I got is

> fixme:keyboard:RegisterHotKey (0x1004a,13,0x00000002,3): stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00000001-1000-11cf-adf0-444553540000} 0x61f7b8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {0003000a-0000-0000-c000-000000000046} 0x6190e4
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {0003000a-0000-0000-c000-000000000046} 0x619c64
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {0003000a-0000-0000-c000-000000000046} 0x619c64
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {0003000a-0000-0000-c000-000000000046} 0x6196e4Can anyone tell me what this mean and how to tackle it? 
{0003000a-0000-0000-c000-000000000046} is the clsid of pbrush It seems that I am still stuck and still have to register PBrush.dll.:(

Thanks.

Sorry, the err ':'ole':'  (without quotes) in  the first error message keeps showing up as smiles!

---

### Post by beew on 2010-08-13
BUMP?? Because it has nothing to do with games? :)

---

### Post by beew on 2010-08-25
Still Bump??

---

