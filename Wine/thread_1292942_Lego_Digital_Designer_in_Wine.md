---
title: "Lego Digital Designer in Wine"
date: 2009-10-16
forum: Wine
---

### Post by blur xc on 2009-10-16
Hey- I see on WineHQ that this program gets their Gold rating, and there's at least one user on the forums using it in Wine (See lego tower computer case thread)...

First I had issues installing it, but after a quick google search I found I had to be in XP mode to get it to work.  So- I took care of that, and it installed fine.

But- Now when I launch it everything loads ok, but once it's finished loading- it closes.

I ran it with
```
wine LDD.exe 2> error.txt
```from the terminal to save all the terminal junk to a file.

Here's the tail end of that file-
```
tail error.txt
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
wine: Call from 0x7bc48e60 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:ViewObject_SetAdvise (0x3930678)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x3930678)->(0)
fixme:shdocvw:OleObject_Close (0x3930678)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x192530)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x192530)->(31448112)
fixme:shdocvw:OleObject_Close (0x192530)->(1)

```I think the USER32.dll.PrintWindow line might be the cause of my problems.  I would really like to get this running in wine.  My wife and kids would appreciate to not have to reboot into Vista to use it, and it won't run in VBox, probalby due to some 3d graphics issue.

Thanks,
BM

---

### Post by beastrace91 on 2009-10-16
Hey There,

Few questions, first you are using the latest Lego Digital Designer ([2.3.19](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16687)) right? What graphics card, graphics driver version #, and Wine version are you using?

~Jeff

---

### Post by blur xc on 2009-10-16
> **beastrace91 said:**
> Hey There,

Few questions, first you are using the latest Lego Digital Designer ([2.3.19]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16687")) right? What graphics card, graphics driver version #, and Wine version are you using?

~Jeff

I'm not in front of that computer right now, but I think it's version 3.0.9 (I downloaded it last night).  I have a nvidia geforce 9600 gt 512mb card, I don't know the video card driver, but it's from the repositories, and the wine version is the newest from the Wine PPA repository.  

I googled user32.dll, and I wonder, can I just copy it from a functioning windows install?

BM

---

### Post by beastrace91 on 2009-10-16
Yes you can give that a try - but also be sure to open your winecfg and set the user32.dll to "native over ride" for your application.

Also if that does not work try reverting back to Wine version .29 - I know .30 & .31 suffered from some regressions in the 3D department. 

Also the reason I asked about the Lego version is because the latest version with test results in the appdb is 2.3.19 - so if you are using a newer version than this be sure to go make a posting for it in the data base :)

~Jeff

---

### Post by blur xc on 2009-10-16
> **beastrace91 said:**
> Yes you can give that a try - but also be sure to open your winecfg and set the user32.dll to "native over ride" for your application.

Also if that does not work try reverting back to Wine version .29 - I know .30 & .31 suffered from some regressions in the 3D department. 

Also the reason I asked about the Lego version is because the latest version with test results in the appdb is 2.3.19 - so if you are using a newer version than this be sure to go make a posting for it in the data base :)

~Jeff

I tried the latest wine version as a desperate attempt to see if I could get Lightroom to run correctly, but no dice.  At least it gets further before failing though...

How do you revert Wine releases?  Do I axe the wine ppa, uninstall, and reinstall from the official jaunty repository?

I wonder if I can find the older version of LDD somewhere...

Thanks,
BM

---

### Post by beastrace91 on 2009-10-16
Yea, just comment out the Wine ppa from your sources.list for now and then ```
sudo apt-get remove wine
``` (don't worry it will keep your installed applications/settings)

Then you simply go download an older version of Wine from [here](http://wine.budgetdedicated.com/archive/index.html) and install it.

~Jeff

---

### Post by DanFoxDavies on 2009-10-16
Hi, it is he of the lego tower computer case.

I'm using LDD v3.0.9, having upgraded from 2.4. Since the upgrade, I've suffered the same problem as described in the original post. I'm using Ubuntu 9.04 64-bit, using the latest stable and latest beta (1.32?) of WINE and I have a Core 2 duo @ 2.13GHz, 2GB RAM, nVidia 9500GT with 1GB RAM (so shouldn't be a problem).

I need to use this program for my business, so I'm looking into it. And I hope we can get it sorted soon.

Also, older versions of LDD won't connect to the server to check prices or upload

---

### Post by blur xc on 2009-10-16
> **DanFoxDavies said:**
> Hi, it is he of the lego tower computer case.

I'm using LDD v3.0.9, having upgraded from 2.4. Since the upgrade, I've suffered the same problem as described in the original post. I'm using Ubuntu 9.04 64-bit, using the latest stable and latest beta (1.32?) of WINE and I have a Core 2 duo @ 2.13GHz, 2GB RAM, nVidia 9500GT with 1GB RAM (so shouldn't be a problem).

I need to use this program for my business, so I'm looking into it. And I hope we can get it sorted soon.

Also, older versions of LDD won't connect to the server to check prices or upload

I'm glad I'm not the only one!  What have you tried to get it working?  I'm going to try that dll when I get home...  How long have you had this problem?  Did you just upgrade to the new LDD?

BTW, Your thread, which I ran across by chance, is what got me to try LDD in Wine.  Up until now we've had to reboot, which my wife and I don't like to do, which means our kids haven't been able to play with it very much.

BM

---

### Post by beastrace91 on 2009-10-16
Also worth mentioning but if you cannot get this working under plain old Wine you might want to take a look @ Codeweavers their [last test](http://www.codeweavers.com/compatibility/browse/name/?app_id=1197) for LDD is a bit old - but Codeweavers offers a free demo and some software that fails (or needs lots of tweaking under Wine) sometimes runs via Codeweavers with ease.

I personally have a Codeweavers subscription and feel it is worth every penny - good software & they give back to the Wine project.

EDIT: Also just discovered LDD is a free download... Grabbing it now at work and I'll give it a go at home later and see if I can tinker with it enough to get it working

~Jeff

---

### Post by blur xc on 2009-10-16
Well, I tried a user32.dll from my xp machine, and I tried all the override options, and the best I could do was as far as I have already gotten.  Also, I uninstalled wine, commented out the wine ppa and installed an older wine- same deal, except the terminal output is a bit different.  The same user32.dll abort line is there, but the stuff after it is different.  Don't know if that makes any difference though.


```

wine: Call from 0x4c3053 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fe0a4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fe0a4)->((null) 28 2 0x32f58c (nil))
fixme:shdocvw:ViewObject_SetAdvise (0x22485c8)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x22485c8)->(0)
fixme:shdocvw:OleObject_Close (0x22485c8)->(1)
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
fixme:shdocvw:ViewObject_SetAdvise (0x1fe008)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x1fe008)->(28474712)
fixme:shdocvw:OleObject_Close (0x1fe008)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x2248fd0)->((nil))
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
```

Thanks for all the help,
BM

---

### Post by DanFoxDavies on 2009-10-17
I would appreciate if someone who knows what they're doing with Wine's code could take a little time to look into this themselves, although better still would be if Lego Group would be sensible enough to create a Linux port (how hard can it be?)
EDIT: This is new:
```
danfox@Geneticiser:~$ wine '/home/danfox/.wine/dosdevices/c:/Program Files/LEGO Company/LEGO Digital Designer/LDD.exe' 
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x168930)
fixme:shdocvw:OleObject_Advise (0x168930)->(0x1c8f4e4, 0x1c8f53c)
fixme:shdocvw:ViewObject_SetAdvise (0x168930)->(1 00000000 0x1c8f4e4)
fixme:shdocvw:ViewObject_Draw (0x168930)->(1 -1 (nil) (nil) (nil) 0x500 0x1c8f554 0x1c8f554 (nil) 00000000)
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16be68,0x16bd80): stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x20b560)
fixme:shdocvw:OleObject_Advise (0x20b560)->(0x290efac, 0x290f004)
fixme:shdocvw:ViewObject_SetAdvise (0x20b560)->(1 00000000 0x290efac)
fixme:shdocvw:ViewObject_Draw (0x20b560)->(1 -1 (nil) (nil) (nil) 0x500 0x290f01c 0x290f01c (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
wine: Call from 0x7bc49310 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:ViewObject_SetAdvise (0x20b560)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x20b560)->(0)
fixme:shdocvw:OleObject_Close (0x20b560)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x168930)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x168930)->(31649832)
fixme:shdocvw:OleObject_Close (0x168930)->(1)
danfox@Geneticiser:~$ 

```It's the result of trying to run from terminal in Wine 1.1.31...


AND this:
```

danfox@Geneticiser:~$ wine '/home/danfox/.wine/dosdevices/c:/Program Files/LEGO Company/LEGO Digital Designer/LDD.exe' 
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x168930)
fixme:shdocvw:OleObject_Advise (0x168930)->(0x1c669fc, 0x1c66a54)
fixme:shdocvw:ViewObject_SetAdvise (0x168930)->(1 00000000 0x1c669fc)
fixme:shdocvw:ViewObject_Draw (0x168930)->(1 -1 (nil) (nil) (nil) 0x500 0x1c66a6c 0x1c66a6c (nil) 00000000)
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16be18,0x16bd18): stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x163e98)
fixme:shdocvw:OleObject_Advise (0x163e98)->(0x2911254, 0x29112ac)
fixme:shdocvw:ViewObject_SetAdvise (0x163e98)->(1 00000000 0x2911254)
fixme:shdocvw:ViewObject_Draw (0x163e98)->(1 -1 (nil) (nil) (nil) 0x500 0x29112c4 0x29112c4 (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
wine: Call from 0x7bc49310 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:ViewObject_SetAdvise (0x163e98)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x163e98)->(0)
fixme:shdocvw:OleObject_Close (0x163e98)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x168930)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x168930)->(31503632)
fixme:shdocvw:OleObject_Close (0x168930)->(1)
danfox@Geneticiser:~$ 


```Is the result of placing an overide for user32.dll 'native, builtin' in Wine 1.1.31

EDIT: One more thing!
This is the result of using the 'builtin then native' override in Wine 1.1.31
```

danfox@Geneticiser:~$ wine '/home/danfox/.wine/dosdevices/c:/Program Files/LEGO Company/LEGO Digital Designer/LDD.exe' 
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
wine: Unhandled page fault on read access to 0x7c153600 at address 0x7c153600 (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x7c153600 in 32-bit code (0x7c153600).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7c153600 ESP:0106ea9c EBP:0106eaa8 EFLAGS:00010202(  R- --  I   - - - )
 EAX:7c153600 EBX:7bc95ff4 ECX:1a55abde EDX:ffffffff
 ESI:7ffd4f10 EDI:7ffd41d4
Stack dump:
0x0106ea9c:  7bc6ce64 001623b0 7ffd4f10 0106eb78
0x0106eaac:  7bc6d080 7c153600 001623b0 00000000
0x0106eabc:  00000000 00000000 ffffffff 7bc6f5c0
0x0106eacc:  7b8444e0 7bc95ff4 7ffd4f10 7ffd41d4
0x0106eadc:  0106eb78 9a20612b 1a55abde 00000000
0x0106eaec:  f7e625b1 00000040 00000000 00000000
Backtrace:
=>0 0x7c153600 (0x0106eaa8)
  1 0x7bc6d080 call_thread_entry_point+0x70() in ntdll (0x0106eb78)
  2 0x7bc7542b in ntdll (+0x6542b) (0x0106f3b8)
  3 0xf7e5d4ff start_thread+0xbf() in libpthread.so.0 (0x0106f4b8)
  4 0xf7dd9b9e __clone+0x5e() in libc.so.6 (0x00000000)
0x7c153600: -- no code accessible --
Modules:
Module    Address            Debug info    Name (121 modules)
PE      400000-  c38000    Deferred        ldd
ELF    7b800000-7b972000    Deferred        kernel32<elf>
  \-PE    7b820000-7b972000    \               kernel32
ELF    7bc00000-7bcb2000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb2000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c06d000-7c08f000    Deferred        devenum<elf>
  \-PE    7c070000-7c08f000    \               devenum
ELF    7c0b5000-7c102000    Deferred        dsound<elf>
  \-PE    7c0c0000-7c102000    \               dsound
ELF    7c382000-7c386000    Deferred        libgpg-error.so.0
ELF    7c386000-7c3ef000    Deferred        libgcrypt.so.11
ELF    7c3ef000-7c401000    Deferred        libtasn1.so.3
ELF    7c401000-7c417000    Deferred        libresolv.so.2
ELF    7c417000-7c420000    Deferred        libkrb5support.so.0
ELF    7c420000-7c4b2000    Deferred        libkrb5.so.3
ELF    7c4b2000-7c54f000    Deferred        libgnutls.so.26
ELF    7c54f000-7c57a000    Deferred        libgssapi_krb5.so.2
ELF    7c57a000-7c5b1000    Deferred        libcups.so.2
ELF    7c7b1000-7c7b5000    Deferred        libkeyutils.so.1
ELF    7c7b5000-7c7d9000    Deferred        libk5crypto.so.3
ELF    7c7e0000-7c7f5000    Deferred        avicap32<elf>
  \-PE    7c7f0000-7c7f5000    \               avicap32
ELF    7c7f5000-7c80e000    Deferred        spoolss<elf>
  \-PE    7c800000-7c80e000    \               spoolss
ELF    7c80e000-7c82e000    Deferred        localspl<elf>
  \-PE    7c810000-7c82e000    \               localspl
ELF    7c885000-7c8b9000    Deferred        uxtheme<elf>
  \-PE    7c890000-7c8b9000    \               uxtheme
ELF    7c8b9000-7c8ce000    Deferred        midimap<elf>
  \-PE    7c8c0000-7c8ce000    \               midimap
ELF    7c8ce000-7c8f4000    Deferred        msacm32<elf>
  \-PE    7c8d0000-7c8f4000    \               msacm32
ELF    7c8f4000-7c8fb000    Deferred        libgdbm.so.3
ELF    7c8fb000-7c95a000    Deferred        libpulse.so.0
ELF    7c95a000-7ca22000    Deferred        libasound.so.2
ELF    7ca22000-7ca26000    Deferred        libcom_err.so.2
ELF    7ca26000-7ca3e000    Deferred        msacm32<elf>
  \-PE    7ca30000-7ca3e000    \               msacm32
ELF    7cd9e000-7cda4000    Deferred        libattr.so.1
ELF    7cda4000-7cda9000    Deferred        libcap.so.2
ELF    7cda9000-7cdb0000    Deferred        libasound_module_pcm_pulse.so
ELF    7cdb0000-7cde8000    Deferred        winealsa<elf>
  \-PE    7cdc0000-7cde8000    \               winealsa
ELF    7ce09000-7ce12000    Deferred        libxcursor.so.1
ELF    7ce12000-7ce17000    Deferred        libxfixes.so.3
ELF    7ce17000-7ce1b000    Deferred        libxcomposite.so.1
ELF    7ce1b000-7ce25000    Deferred        libxrender.so.1
ELF    7ce25000-7ce2b000    Deferred        libxxf86vm.so.1
ELF    7ce2e000-7ce37000    Deferred        librt.so.1
ELF    7ce47000-7ce68000    Deferred        imm32<elf>
  \-PE    7ce50000-7ce68000    \               imm32
ELF    7ce68000-7cf07000    Deferred        winex11<elf>
  \-PE    7ce80000-7cf07000    \               winex11
ELF    7cf07000-7de1f000    Deferred        libglcore.so.1
ELF    7dfa9000-7dfb1000    Deferred        libxrandr.so.2
ELF    7e005000-7e02c000    Deferred        libexpat.so.1
ELF    7e02c000-7e059000    Deferred        libfontconfig.so.1
ELF    7e059000-7e06f000    Deferred        libz.so.1
ELF    7e06f000-7e0e6000    Deferred        libfreetype.so.6
ELF    7e0e7000-7e0ea000    Deferred        libxinerama.so.1
ELF    7e102000-7e117000    Deferred        system.drv16.so
PE    7e110000-7e117000    Deferred        system.drv16
ELF    7e117000-7e141000    Deferred        ws2_32<elf>
  \-PE    7e120000-7e141000    \               ws2_32
ELF    7e141000-7e226000    Deferred        oleaut32<elf>
  \-PE    7e160000-7e226000    \               oleaut32
ELF    7e226000-7e323000    Deferred        ole32<elf>
  \-PE    7e240000-7e323000    \               ole32
ELF    7e323000-7e357000    Deferred        winspool<elf>
  \-PE    7e330000-7e357000    \               winspool
ELF    7e357000-7e421000    Deferred        comctl32<elf>
  \-PE    7e360000-7e421000    \               comctl32
ELF    7e421000-7e47e000    Deferred        shlwapi<elf>
  \-PE    7e430000-7e47e000    \               shlwapi
ELF    7e47e000-7e60e000    Deferred        shell32<elf>
  \-PE    7e490000-7e60e000    \               shell32
ELF    7e60e000-7e6c0000    Deferred        comdlg32<elf>
  \-PE    7e620000-7e6c0000    \               comdlg32
ELF    7e6c0000-7e72e000    Deferred        rpcrt4<elf>
  \-PE    7e6d0000-7e72e000    \               rpcrt4
ELF    7e72e000-7e742000    Deferred        lz32<elf>
  \-PE    7e730000-7e742000    \               lz32
ELF    7e742000-7e7de000    Deferred        winmm<elf>
  \-PE    7e750000-7e7de000    \               winmm
ELF    7e7de000-7e801000    Deferred        mpr<elf>
  \-PE    7e7e0000-7e801000    \               mpr
ELF    7e801000-7e89c000    Deferred        opengl32<elf>
  \-PE    7e820000-7e89c000    \               opengl32
ELF    7e89c000-7e8a1000    Deferred        libxdmcp.so.6
ELF    7e8a1000-7e8bb000    Deferred        libxcb.so.1
ELF    7e8bb000-7e8bf000    Deferred        libxau.so.6
ELF    7e8bf000-7e8c4000    Deferred        libuuid.so.1
ELF    7e8c4000-7e8c6000    Deferred        libnvidia-tls.so.1
ELF    7e8c6000-7e8d5000    Deferred        libgcc_s.so.1
ELF    7e9c4000-7eab3000    Deferred        libx11.so.6
ELF    7eab3000-7eac3000    Deferred        libxext.so.6
ELF    7eac3000-7eadb000    Deferred        libice.so.6
ELF    7eadb000-7eae4000    Deferred        libsm.so.6
ELF    7eae4000-7eb9e000    Deferred        libgl.so.1
ELF    7eb9e000-7ec10000    Deferred        libglu.so.1
ELF    7ec10000-7ec2a000    Deferred        version<elf>
  \-PE    7ec20000-7ec2a000    \               version
ELF    7ec2c000-7ec83000    Deferred        advapi32<elf>
  \-PE    7ec40000-7ec83000    \               advapi32
ELF    7ec83000-7ed23000    Deferred        gdi32<elf>
  \-PE    7ec90000-7ed23000    \               gdi32
ELF    7ed23000-7ee6f000    Deferred        user32<elf>
  \-PE    7ed40000-7ee6f000    \               user32
ELF    7ef99000-7efa5000    Deferred        libnss_files.so.2
ELF    7efa5000-7efbe000    Deferred        libnsl.so.1
ELF    7efbe000-7efe4000    Deferred        libm.so.6
ELF    7efe5000-7effc000    Deferred        glu32<elf>
  \-PE    7eff0000-7effc000    \               glu32
ELF    f7ce3000-f7cee000    Deferred        libnss_nis.so.2
ELF    f7cef000-f7cf3000    Deferred        libdl.so.2
ELF    f7cf3000-f7e56000    Export          libc.so.6
ELF    f7e57000-f7e70000    Export          libpthread.so.0
ELF    f7e83000-f7e8c000    Deferred        libnss_compat.so.2
ELF    f7e8c000-f7fc8000    Deferred        libwine.so.1
ELF    f7fca000-f7feb000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\LEGO Company\LEGO Digital Designer\LDD.exe
    0000001f    0
    0000001e    0
    0000001a    0 <==
    00000009    0
0000000e 
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 
    00000019    0
Backtrace:
=>0 0x7c153600 (0x0106eaa8)
  1 0x7bc6d080 call_thread_entry_point+0x70() in ntdll (0x0106eb78)
  2 0x7bc7542b in ntdll (+0x6542b) (0x0106f3b8)
  3 0xf7e5d4ff start_thread+0xbf() in libpthread.so.0 (0x0106f4b8)
  4 0xf7dd9b9e __clone+0x5e() in libc.so.6 (0x00000000)
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x1690d8)
fixme:shdocvw:OleObject_Advise (0x1690d8)->(0x1de373c, 0x1de3794)
fixme:shdocvw:ViewObject_SetAdvise (0x1690d8)->(1 00000000 0x1de373c)
fixme:shdocvw:ViewObject_Draw (0x1690d8)->(1 -1 (nil) (nil) (nil) 0x500 0x1de37ac 0x1de37ac (nil) 00000000)
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16c5c0,0x16c4c0): stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x161180)
fixme:shdocvw:OleObject_Advise (0x161180)->(0x2a0ce2c, 0x2a0ce84)
fixme:shdocvw:ViewObject_SetAdvise (0x161180)->(1 00000000 0x2a0ce2c)
fixme:shdocvw:ViewObject_Draw (0x161180)->(1 -1 (nil) (nil) (nil) 0x500 0x2a0ce9c 0x2a0ce9c (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
wine: Call from 0x7bc49310 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:ViewObject_SetAdvise (0x161180)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x161180)->(0)
fixme:shdocvw:OleObject_Close (0x161180)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x1690d8)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x1690d8)->(32494000)
fixme:shdocvw:OleObject_Close (0x1690d8)->(1)
danfox@Geneticiser:~$ 


```

---

### Post by DanFoxDavies on 2009-10-17
Here's what I get with Wine 1.1.29 using a 'native, builtin' override on user32.dll
```
danfox@Geneticiser:~$ wine '/home/danfox/.wine/dosdevices/c:/Program Files/LEGO Company/LEGO Digital Designer/LDD.exe' 
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x14b920)
fixme:shdocvw:OleObject_Advise (0x14b920)->(0x1d5b0b4, 0x1d5b10c)
fixme:shdocvw:ViewObject_SetAdvise (0x14b920)->(1 00000000 0x1d5b0b4)
fixme:shdocvw:ViewObject_Draw (0x14b920)->(1 -1 (nil) (nil) (nil) 0x320 0x1d5b124 0x1d5b124 (nil) 00000000)
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x14edf0,0x14ed08): stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x146e78)
fixme:shdocvw:OleObject_Advise (0x146e78)->(0x29124cc, 0x2912524)
fixme:shdocvw:ViewObject_SetAdvise (0x146e78)->(1 00000000 0x29124cc)
fixme:shdocvw:ViewObject_Draw (0x146e78)->(1 -1 (nil) (nil) (nil) 0x320 0x291253c 0x291253c (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
wine: Call from 0x7bc49200 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32e4e8
fixme:iphlpapi:NotifyAddrChange (Handle 0x5cbe908, overlapped 0x5cbe910): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
0[3af2950]: IMM32: InitKeyboardLayout, aKeyboardLayout=08090809, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14b9c0)->((null) 1 0x32eab0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14b9c0)->((null) 25 2 0x32eac4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14b9c0)->((null) 26 2 0x32eac4 (nil))
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:ClientSite_GetContainer (0x14b9c0)->(0x32eb00)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14b9c0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32eb8c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14b9c0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32ebb4)
fixme:wininet:InternetLockRequestFile STUB


```(the program freezes but does not automatically disappear)


EDIT: Hang on a sec. LDD is calling for USER32.dll.PrintWindow. Wine has user32.dll - see the difference? *goes back to test more*
edit: it seems the capital/lower case thing means nothing, in the Wine config I can't rename to capitals anyway.

---

### Post by DanFoxDavies on 2009-10-17
OK, I've now tried Wine 1.1.29 patched with [This Patch Here.]("http://bugs.winehq.org/attachment.cgi?id=21566")
I compiled it to run in a separate folder.
Here's the somewhat different output when I run it now. Note that the LDD window now appears and hangs around, but clicking anywhere on it leads to an extensive grey-out. (I'm using Compiz btw - any difference if I switch it off?) When the grey-out ends, it looks usable again until I click again. Whatever I click on, it doesn't change the contents of the window other than to grey.
```
danfox@Geneticiser:~$ $HOME/wine-user32/bin/wine '/home/danfox/.wine/drive_c/Program Files/LEGO Company/LEGO Digital Designer/LDD.exe'
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x14a150)
fixme:shdocvw:OleObject_Advise (0x14a150)->(0x1c898cc, 0x1c89924)
fixme:shdocvw:ViewObject_SetAdvise (0x14a150)->(1 00000000 0x1c898cc)
fixme:shdocvw:ViewObject_Draw (0x14a150)->(1 -1 (nil) (nil) (nil) 0x320 0x1c8993c 0x1c8993c (nil) 00000000)
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x14d620,0x14d538): stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x219bf0)
fixme:shdocvw:OleObject_Advise (0x219bf0)->(0x29091d4, 0x290922c)
fixme:shdocvw:ViewObject_SetAdvise (0x219bf0)->(1 00000000 0x29091d4)
fixme:shdocvw:ViewObject_Draw (0x219bf0)->(1 -1 (nil) (nil) (nil) 0x320 0x2909244 0x2909244 (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32e4e8
fixme:iphlpapi:NotifyAddrChange (Handle 0x64be908, overlapped 0x64be910): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
0[3aea360]: IMM32: InitKeyboardLayout, aKeyboardLayout=08090809, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14a1f0)->((null) 1 0x32eab0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->((null) 25 2 0x32eac4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->((null) 26 2 0x32eac4 (nil))
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:ClientSite_GetContainer (0x14a1f0)->(0x32eb00)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32eb8c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32ebb4)
fixme:wininet:InternetLockRequestFile STUB
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->((null) 29 2 0x32f584 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14a1f0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6295218)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6295fe0)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6296d80)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6297b48)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6298e60)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6299b90)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f494)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x629da40)->(0x32ef8c 0x32ef78 0)
fixme:shdocvw:ClientSite_GetContainer (0x14a1f0)->(0x32f460)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14a1f0)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->((null) 25 2 0x32f394 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a1f0)->((null) 26 2 0x32f394 (nil))
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
err:ntdll:RtlpWaitForCriticalSection section 0x62af898 "?" wait timed out in thread 003a, blocked by 0039, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x62af898 "?" wait timed out in thread 003a, blocked by 0039, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x62af898 "?" wait timed out in thread 003a, blocked by 0039, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x62af898 "?" wait timed out in thread 003a, blocked by 0039, retrying (60 sec)


```
EDIT: could the patch be only designed to work on Wine 1.0.1?

---

### Post by sarcaman on 2009-10-18
I have same problem in Karmic on 2 PCs one with nvidia the other ATI.

One Pentium 3, the other Pentium 4

Same with or without Compiz

:(

---

### Post by DanFoxDavies on 2009-10-20
I have been working around with various files and the help of the internet.
I'm now wondering whether the problem could be fixed within the user32.spec and painting.c files (located in /home/[user]/wine-1.1.29/wine-1.1.29/dlls/user32).

I've tried several different wordings and codes but to no effect...I also renamed the file to emulate it's disappearance and still got the same error.

The PrintWindow part of painting.c now reads:
```
/*************************************************************************
*              PrintWindow (USER32.@)
*
*/
BOOL WINAPI PrintWindow( HWND hwnd, HDC hdcBlt, UINT nFlags)
{
   UINT flags = PRF_CHILDREN | PRF_CLIENT | PRF_ERASEBKGND | PRF_OWNED;

   !(nFlags & PW_CLIENTONLY)
   return SendMessageW( hwnd, WM_PRINT, (WPARAM)hdcBlt, (LPARAM)flags );

```
But it seems it's not implemented. Anyone know how to?

---

### Post by DanFoxDavies on 2009-10-23
Just another update: yesterday I tried doing as Lego Customer Services (aka. 'Linux? WTF is that?') suggested and updated the graphics driver. First to Nvidia 185 (same results as the 180 driver I had before) and then to 190 beta (a more hefty error with not even an attempt to display LDD's window ensued, which while I can't remember what it is (stupid me not taking a copy/paste of it), I do remember that it boiled down to the attempted use of OpenGL 3.2, which LDD does not support).
I am now sticking with Nvidia's 185 driver unless given reason to switch again.

---

### Post by DanFoxDavies on 2009-10-25
PLEASE can somebody lend a hand here, I'm all out of ideas and really need to get this working.

Also, if anyone can tell me where Wine's builtin DLL libraries are located (i.e. the ones with the .spec files in the folder), I'd be grateful. I seem to have lost them. 

EDIT: found them, sorry.
Still having problems, though.

---

### Post by DanFoxDavies on 2009-11-09
Bump. Sorry, but I'm not shutting up about this until it's solved and working to Platinum standard.

---

### Post by DanFoxDavies on 2009-11-15
Bump.
Would a real Wine programmer please stand up?
I need to get this working, pretty please with a cherry on top, proper icing and chocolate hundreds and thousands. Yes, it has come to this.

---

### Post by DanFoxDavies on 2009-11-22
Just attempted to run LDD3 in a new install of Wine 1.1.33. The bug still occurs.

Output:
```
danfox@Geneticiser:~$ wine '/home/danfox/.wine/dosdevices/c:/Program Files/LEGO Company/LEGO Digital Designer/LDD.exe' 
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x164fc0)
fixme:shdocvw:OleObject_Advise (0x164fc0)->(0x1c4e6a4, 0x1c4e6fc)
fixme:shdocvw:ViewObject_SetAdvise (0x164fc0)->(1 00000000 0x1c4e6a4)
fixme:shdocvw:ViewObject_Draw (0x164fc0)->(1 -1 (nil) (nil) (nil) 0x620 0x1c4e714 0x1c4e714 (nil) 00000000)
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x168590,0x168490): stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:ACMWrapper_ConnectInput acmStreamOpen returned 512
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\LEGO Company\\LEGO Digital Designer\\LDD.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x3a03db8)
fixme:shdocvw:OleObject_Advise (0x3a03db8)->(0x28c35cc, 0x28c3624)
fixme:shdocvw:ViewObject_SetAdvise (0x3a03db8)->(1 00000000 0x28c35cc)
fixme:shdocvw:ViewObject_Draw (0x3a03db8)->(1 -1 (nil) (nil) (nil) 0x620 0x28c363c 0x28c363c (nil) 00000000)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
wine: Call from 0x7bc489f0 to unimplemented function USER32.dll.PrintWindow, aborting
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:ViewObject_SetAdvise (0x3a03db8)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x3a03db8)->(0)
fixme:shdocvw:OleObject_Close (0x3a03db8)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x164fc0)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x164fc0)->(31332864)
fixme:shdocvw:OleObject_Close (0x164fc0)->(1)
danfox@Geneticiser:~$ 

```

---

### Post by Kazade on 2009-11-30
Just to let you know, I just submitted a patch for this that implements a stub for the missing PrintWindow function. 

That fix does make it start, but it crashes with a more obscure error when you try to do anything :(

---

### Post by DanFoxDavies on 2009-11-30
> **Kazade said:**
> Just to let you know, I just submitted a patch for this that implements a stub for the missing PrintWindow function. 

That fix does make it start, but it crashes with a more obscure error when you try to do anything :(

Yes, I have already tried it with said patch myself. Same results. Wine bug #18772 is tracking the Printwindow thing, but I don't know what to do about this other bug.

---

### Post by Kazade on 2009-11-30
> **DanFoxDavies said:**
> Yes, I have already tried it with said patch myself. Same results. Wine bug #18772 is tracking the Printwindow thing, but I don't know what to do about this other bug.

Yeah I saw that patch, but I wasn't sure why it wasn't previously accepted so rather than resend it, I just implemented a simple stub which is top of the queue here: [http://source.winehq.org/patches/](http://source.winehq.org/patches/)

With the stub everything works as long as you don't scroll anything, you can even build a model if you only access the visible blocks without moving the scrollbar.

---

### Post by DanFoxDavies on 2009-11-30
> **Kazade said:**
> Yeah I saw that patch, but I wasn't sure why it wasn't previously accepted so rather than resend it, I just implemented a simple stub which is top of the queue here: [http://source.winehq.org/patches/](http://source.winehq.org/patches/)

With the stub everything works as long as you don't scroll anything, you can even build a model if you only access the visible blocks without moving the scrollbar.
Thanks, this sounds like progress. I was on the phone to Lego about this earlier and they don't seem to have a clue with Linux.

---

### Post by DanFoxDavies on 2009-11-30
[http://source.winehq.org/patches/data/55818](http://source.winehq.org/patches/data/55818)
Is the patch Kazade mentioned above. Having now applied it to Wine 1.1.32, I have what I would class as bronze usability in LDD3 - that is, can use it but with some fairly awkward problems to avoid.
1: like Kazade said, scrolling in the menus is a no-go.
2: The pane on the right for DesignByMe does not work (it's just blacked out).
3: Sound output gets stuck in a loop upon program launch.
4: and a carried-over bug that still needs solving from the LDD2 era: flipping desktops with Compiz causes the program to crash/vanish and become a Zombie process, particularly while loading a model. (Inconvenient if I'm working on something large and am forced to wait while it loads instead of take advantage of Compiz for multi-tasking).

---

### Post by Kazade on 2009-12-02
Just a quick update. My patch was rejected (I realized soon after submitting that there was a problem with it), so I've sent another one, this one actually implements the body of the function rather than stubs it.

The patch can be found here: [http://source.winehq.org/patches/data/55926](http://source.winehq.org/patches/data/55926)

Hopefully it will get in this time, if not I'll have to see if I can find time to fix any issues with it. Once this one is submitted I might take a look at the scrollbar crash - but there is a possibility that the current OpenAL DirectSound rewrite might fix this automatically - so it could well be worth waiting till after the next release.

---

### Post by DanFoxDavies on 2009-12-02
> **Kazade said:**
> Just a quick update. My patch was rejected (I realized soon after submitting that there was a problem with it), so I've sent another one, this one actually implements the body of the function rather than stubs it.

The patch can be found here: [http://source.winehq.org/patches/data/55926](http://source.winehq.org/patches/data/55926)

Hopefully it will get in this time, if not I'll have to see if I can find time to fix any issues with it. Once this one is submitted I might take a look at the scrollbar crash - but there is a possibility that the current OpenAL DirectSound rewrite might fix this automatically - so it could well be worth waiting till after the next release.

Thanks, Kazade. Let's see if we can get this to Platinum level. And BTW, apparently LDD 3.1 will be coming soon in the new year. There may be more problems with that, I don't know. But since it's only one up from 3.0.9, perhaps it's just LEGO fixing a few bugs themselves.

---

### Post by Kazade on 2009-12-02
The patch was just applied to Wine git :)

---

### Post by DanFoxDavies on 2009-12-02
> **Kazade said:**
> The patch was just applied to Wine git :)
Great stuff. Since applying your patch here, I've been able to get working on a design that's been waiting 20 months for my computer to have enough oomph to cope with it. But of course, as soon as I'd upgraded to 4GB of RAM, LDD3 came out. Now I can finally get on with the Council Flats model. [http://vulpinedesignsultd.deviantart.com/](http://vulpinedesignsultd.deviantart.com/) is my business DA page. Note the older Council Flats WIP post; that picture's from 20 months ago, when I hit my computer's ceiling. You can find it in the Gallery. WIP 2 is from just a moment ago.

---

### Post by samjam on 2009-12-17
> **Kazade said:**
> The patch was just applied to Wine git :)

Hurrah. Will this hit anyones ppa soon?

---

### Post by Kazade on 2009-12-17
It already is in the wine ppa:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.2
```

---

### Post by DanFoxDavies on 2009-12-17
> **samjam said:**
> Hurrah. Will this hit anyones ppa soon?
Apparently it was included in 1.1.34, but that doesn't seem to solve LDD3. I think they only implemented a PrintWindow fix, rather than all fixes needed for LDD3?

---

### Post by Kazade on 2009-12-17
> **DanFoxDavies said:**
> Apparently it was included in 1.1.34, but that doesn't seem to solve LDD3. I think they only implemented a PrintWindow fix, rather than all fixes needed for LDD3?

Yeah just the fix to get it running, I haven't had time to look into the other issues (scrolling, black right hand panel etc.)

---

### Post by DanFoxDavies on 2010-01-07
How's it coming along? Anything new to report?

---

### Post by Kazade on 2010-01-07
> **DanFoxDavies said:**
> How's it coming along? Anything new to report?

It's not really. I've been busy with Xmas + other projects. Could you write Wine bug reports for all the issues you know of and link them here? (I guess the scrolling one is the most important) Then when I get a chance I'll go through and see if any of them is something I can fix.

---

### Post by Kazade on 2010-01-07
Wait! Native quartz.dll fixes the scrolling issue!

Download quartz.dll from here: [http://www.dll-files.com/dllindex/dll-files.shtml?quartz](http://www.dll-files.com/dllindex/dll-files.shtml?quartz)

(Windows license required most likely etc. etc.)

Extract the DLL and copy it to ~/.wine/drive_c/Windows/system32
Run: winecfg

Under libraries, type "quartz" and click "Add" then OK.

Run Lego DD in all it's functional glory ;)

EDIT: As a side note, I received an automatic update to LDD just now and it downloaded, ran the update and then ran the application just like native Windows, - Wine rules.

---

### Post by DanFoxDavies on 2010-01-09
Would it be possible to find or create a Wine equivalent of quartz.dll that can be included in the main ppa? Or is this too difficult or beside the point or somesuch?

---

### Post by Kazade on 2010-01-09
> **DanFoxDavies said:**
> Would it be possible to find or create a Wine equivalent of quartz.dll that can be included in the main ppa? Or is this too difficult or beside the point or somesuch?

The reason that scrolling doesn't work under vanilla Wine is there is a bug in the built-in quartz.dll - that's why using the one from Windows works.

What we should do is create a bug report with a traceback of the crash, noting that the native DLL works fine. I'll do that a little later. Unfortunately I don't have the time to track down and fix that actual bug though :(

---

### Post by DanFoxDavies on 2010-01-25
How's it going, any news?

---

### Post by Kazade on 2010-01-25
Nope, I think I've done all I can (I don't have any time to look into it). The state with Wine 1.1.36 is that it works fine with a native quartz.dll but still crashes without.

---

### Post by cepcer on 2010-05-18
Thanks! The quartz.dll makes it work great in 10.04 and I have a happy son!

---

### Post by cwbar_1 on 2010-08-23
I got the designer to work for my grandson by first setting the compatability mode level slider to "0", then un-checking "enable sounds in the application."  (Edit>Preferences)

---

### Post by coolman98 on 2010-08-23
cool maybe I will try this

---

