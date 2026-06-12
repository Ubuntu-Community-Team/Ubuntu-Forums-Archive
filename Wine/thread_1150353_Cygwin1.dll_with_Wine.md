---
title: "Cygwin1.dll with Wine"
date: 2009-05-06
forum: Wine
---

### Post by abeisgreat on 2009-05-06
Howdy, I'm trying to setup an... unusual compilation environment on my desktop. This would normally not be an issue, but the thing is, the compilers I'm trying to use are designed to run under Cygwin, on a windows box, and I'm trying to cut out the windows part. Anyway, I have my dev stuff set up in /opt/* and my issue is, it compiles fine up to the part when it trys to load cxbe.exe, its looking for cygwin1.dll, I figure it is, theoredically possible to run this dll under wine, any ideas/suggestions.

Here is my exact error
```
err:module:import_dll Library cygwin1.dll (which is needed by L"Z:\\opt\\openxdk\\bin\\cxbe.exe") not found

```

EDIT: Anyway, I grabbed the cygwin1.dll file and through it where wine could see it, just to take a shot in the dark, no luck, make got a bit farther, but inevitably died

---

### Post by WakkiTabakki on 2009-05-06
Did you register the cygwin-dll? Just putting a dll in a folder isn't enough in windows-land. 
In the folder where you put the dll, open a terminal and type:
```
regsvr32 cygwin1.dll
```


Funny setup, btw, cygwin under wine :)

/N

---

### Post by asdfoo on 2009-05-06
> **WakkiTabakki said:**
> Did you register the cygwin-dll? Just putting a dll in a folder isn't enough in windows-land.
/N


That's not always the case.  There are probably tens of thousands of dlls out there that don't need to be registered.

---

### Post by cogadh on 2009-05-06
Where did you put the DLL in Wine? When you ran the app from the terminal, did you change directories to its install location before running it? The error message you are getting often indicates a simple case of the app being run from the wrong directory (Windows "Start in" behavior).

---

### Post by abeisgreat on 2009-05-06
> **WakkiTabakki said:**
> Did you register the cygwin-dll? Just putting a dll in a folder isn't enough in windows-land. 
In the folder where you put the dll, open a terminal and type:
```
regsvr32 cygwin1.dll
```

Thanks for the advice, I tried that command and got

```

abe@zoey-desktop:~/.wine/drive_c/windows/$ regsvr32 cygwin1.dll
fixme:ntdll:NtSetInformationToken 0x5c 4 0x61168988 44
fixme:ntdll:NtSetInformationToken 0x5c 6 0x32f830 4
     10 [main] ? (8) cygheap_user::init: SetTokenInformation (TokenDefaultDacl), Win32 error 1
fixme:advapi:ImpersonateLoggedOnUser ((nil))
fixme:advapi:ImpersonateLoggedOnUser ((nil))
DllRegisterServer not implemented in DLL cygwin1.dll

```

> **cogadh said:**
> Where did you put the DLL in Wine? When you ran the app from the terminal, did you change directories to its install location before running it? The error message you are getting often indicates a simple case of the app being run from the wrong directory (Windows "Start in" behavior).

If you could explain a bit more, that would be great, the cxbe.exe file (the one which needs cygwin1.dll) is called automatically as part of the compilation process, and therefore is being ran from my ~/Desktop/OpenXDK/ folder. The DLL is stored in ~/.wine/drive_c/windows/

---

### Post by cogadh on 2009-05-06
Put the DLL in ~/.wine/drive_c/windows/system32, that's where Wine expects to find most DLLs.

---

### Post by NightMKoder on 2009-05-06
You probably need to actually install cygwin in wine (yes, emulate a linux environment through a windows compatibility layer on linux. Incredibly fun)

[http://blog.cihar.com/archives/2009/01/12/cygwin_in_wine/](http://blog.cihar.com/archives/2009/01/12/cygwin_in_wine/)

---

