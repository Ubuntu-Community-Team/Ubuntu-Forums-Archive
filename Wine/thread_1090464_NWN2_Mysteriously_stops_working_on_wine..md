---
title: "NWN2 Mysteriously stops working on wine."
date: 2009-03-08
forum: Wine
---

### Post by ubersoft on 2009-03-08
I have been able to run Neverwinter Nights 2 with Storm of Zehir on wine without problems, all the way up to patch 1.21.  I have run it successfully on Hardy and Intrepid, and for a while I was able to run it just fine on Jaunty (Kubuntu in all instances).  I have backed up my .wine directory with all working versions of my apps (I always do that in case I hose wine while I'm trying to configure a new one) so I know I'm always starting with something that works.

The big mystery is that one day, Neverwinter Nights 2 stopped working on Jaunty.  It wasn't an update to wine that did it, but a few weeks back this happened:

One day I loaded up Neverwinter Nights 2, clicked "play," and the game loaded fine.

The next day I loaded up Neverwinter Nights 2, click "play," and nothing ever happened.

I've tried loading various neverwinter nights executables from the terminal, and this is what I get:

wine nwn2main.exe
> wrightc@jack:~/.wine/drive_c/Program Files/Neverwinter Nights 2$ wine nwn2main.exe
[email]wrightc@jack:~/.wine[/email]/drive_c/Program Files/Neverwinter Nights 2$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1a9aa0c,0x00000004,0x1a9aa08) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1a997f8): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) >combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1a99744,0x00000000), stub!

wine nwn2.exe
> wrightc@jack:~/.wine/drive_c/Program Files/Neverwinter Nights 2$ wine nwn2.exe
fixme:advapi:SetEntriesInAclA 1 0x33d748 (nil) 0x33d780
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33d714 (nil) 0x33d75c
fixme:advapi:SetSecurityInfo stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7db5a9e8, overlapped 0x7db5a9cc): stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:setupapi:create_fake_dll failed to create L"c:\\windows\\system32\\comctl32.dll" (error=80)
err:setupapi:create_fake_dll failed to create L"c:\\windows\\system32\\quartz.dll" (error=80)
wine: configuration in '/home/wrightc/.wine' has been updated.
[email]wrightc@jack:~/.wine[/email]/drive_c/Program Files/Neverwinter Nights 2$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1a9aa0c,0x00000004,0x1a9aa08) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1a997f8): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) >combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1a99744,0x00000000), stub!


In both cases nothing ever happens.

It's driving me crazy because I can't think of a single thing I did to WINE that would make the programs not load.  I'm wondering if maybe something happened in the Jaunty environment that is making it impossible to load this particular program (it is still alpha, after all, and its state changes from day to day), but that doesn't make much sense to me either -- all of my other wine-run apps load fine, including Oblivion and Civ4.

Anyway, I'm stumped. Does anyone have any suggestions as to what I can do to troubleshoot this? I hate using my windows partition -- the game is more stable under wine.

---

### Post by cogadh on 2009-03-08
Well, these errors would seem to be rather informative:
```
err:setupapi:create_fake_dll failed to create L"c:\\windows\\system32\\comctl32.dll" (error=80)
err:setupapi:create_fake_dll failed to create L"c:\\windows\\system32\\quartz.dll" (error=80)
```
You might try using a native Windows comctl32.dll and quartz.dll in place of the fake ones that Wine seems to have failed to create.

---

### Post by ubersoft on 2009-03-08
Gave that a try, and this is what I got:

> wine nwn2.exe
fixme:advapi:CheckTokenMembership (0x50 0x13d7a0 0x32faf0) stub!
fixme:advapi:CheckTokenMembership (0x9c 0x14ec80 0x1aafaf0) stub!
[email]wrightc@jack:~/.wine[/email]/drive_c/Program Files/Neverwinter Nights 2$ fixme:advapi:CheckTokenMembership (0xa0 0x14ed98 0x1aafaf0) stub!
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1a9aa0c,0x00000004,0x1a9aa08) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1a997f8): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) >combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1a99744,0x00000000), stub!

Essentially the error about the dlls were removed. Program still won't load though.

---

### Post by ubersoft on 2009-03-09
I've solved my own problem and it has nothing to do with Wine at all. I'm posting this here to give any other interested party a heads-up.

If you are using NVIDIA's proprietary drivers, be aware that NIVIDIA-Linux-x86-180.35 had a nasty bug which apparently prevented some programs from running properly. This is referenced in the [release notes of the prerelease of the next version of the driver](http://www.nvnews.net/vbulletin/showthread.php?p=1951107) ("Fixed a problem that caused signals to be blocked in some applications") and using the prerelease driver does, in fact, solve the problem.

---

