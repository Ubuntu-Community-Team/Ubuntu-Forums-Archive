---
title: "Problems with Wine directories"
date: 2009-11-25
forum: Wine
---

### Post by purity89 on 2009-11-25
I seem to be having some problems with my Wine directories. Check this out:

Trying to run some winetricks-commands:

```
purity@purity-laptop:~$ wget http://www.kegel.com/wine/winetricks
--2009-11-25 14:41:39--  http://www.kegel.com/wine/winetricks
Resolving www.kegel.com... 216.92.86.126
Connecting to www.kegel.com|216.92.86.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 119052 (116K) [text/plain]
Saving to: `winetricks'

100%[======================================>] 119,052     55.2K/s   in 2.1s    

2009-11-25 14:41:41 (55.2 KB/s) - `winetricks' saved [119052/119052]

purity@purity-laptop:~$ sh winetricks vcrun2008
**Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.**
Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.
drive_c already named harddiskvolume0
Executing wine /home/purity/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe
**Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.**
wine: cannot find '/home/purity/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe'
Note: command 'wine /home/purity/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe' returned status 2.  Aborting.

```

Trying to run a .exe using Wine:
```
purity@purity-laptop:~$ wine vcredist_x86.exe 
**Warning: could not find DOS drive for current working directory '/home/purity', starting in the Windows directory.**
fixme:clusapi:GetNodeClusterState ((null),0x32ec4c,0) stub!
fixme:advapi:DecryptFileA "d:\\ab7187d0b5a2fb298198ec61\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0

```

The the install-window opens, although I get an error stating that "This product is not supported on this operating system".

To me it seems like there's something wrong with my Wine-directories, that keeps me from using winetricks. Anyone heard of this before?

I guess I could fix it by removing the Wine-directories and reconfiguring/installing Wine, but I have some programs installed and I'd rather try and fix this some other way.

---

### Post by 8Kuula on 2009-11-25
In wine config ( $ winecfg ) is Drives tab, check that there is one drive pointed to root ( / ), in default one is created (Z: drive) when winecfg is first time ran.
Or atleast to your home directory ( /home/purity ).

---

### Post by purity89 on 2009-11-25
Wow, this actually seemed like it has solved my problems. Thank you very much!

---

