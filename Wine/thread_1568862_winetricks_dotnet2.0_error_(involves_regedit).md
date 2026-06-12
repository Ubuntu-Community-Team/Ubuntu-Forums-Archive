---
title: "winetricks dotnet2.0 error (involves regedit)"
date: 2010-09-05
forum: Wine
---

### Post by Arcmyst on 2010-09-05
I've got a new installation of Karmic on which I've installed Wine, Tor, Vidalia, Opera, and aMSN. I've also completed the steps for all of the sections of the Comprehensive Multimedia guide. Aside from that, all I've done is transfer over old documents and add a new sound theme and bootsplash screen. Using Wine 1.1.31 with no modifications other than an attempt at installing Winamp that didn't work, (due to the lack of the dotnet framework) which I uninstalled. Emulating Windows XP, but I've also tried 2000 with precisely the same results. This is everything that runs in the terminal:

```
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/xerxes/.cache/winetricks/dotnet20/l_intl.nls /home/xerxes/.wine/dosdevices/c:/windows/system32/
Executing wine reg delete HKLM\Software\Microsoft\.NETFramework\policy
                                                                      2.0 /f
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: The system was unable to find the specified registry key or value
------------------------------------------------------
Note: command 'wine reg delete HKLM\Software\Microsoft\.NETFramework\policy
                                                                           2.0 /f' returned status 1.  Aborting.
------------------------------------------------------
```

What I assume is the relevant part is

```
Executing wine reg delete HKLM\Software\Microsoft\.NETFramework\policy
                                                                      2.0 /f
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: The system was unable to find the specified registry key or value
------------------------------------------------------
Note: command 'wine reg delete HKLM\Software\Microsoft\.NETFramework\policy
                                                                           2.0 /f' returned status 1.  Aborting.
------------------------------------------------------
```

If I open up regedit and add a binary value called (null) in the right key, it will get past this step but then run into another key with the same problem (which I can't manage to figure out, but I think it's not really the point). If I have to do this with every key, even if I could manage it, it'd take all week to do, since I have to start over with every iteration (since it deletes the keys when it works). Any idea what the underlying problem is?

P.S. Yes, I know the first paragraph includes a lot of irrelevant information, but I figured it couldn't hurt to list absolutely everything I'd done to my computer since installing the OS this morning.

---

### Post by jesus-saves on 2010-09-06
im having the same problem.  ive looked everywhere online and I can find no answer.  A few others had the same problem, with no answer.

I'm using Ubunutu 10.04 LTS

Im trying to install Windows software with Wine, I need dotnet20 asap.  Anyone who knows how to solve this problem please help.

---

### Post by jesus-saves on 2010-09-06
try downloading and installing this

[http://www.microsoft.com/downloads/details.aspx?familyid=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en)

i think its the same thing wine tries to intall.  when u install it, the registry files it cannot find will then be able to be found, and once it launches the installer, it acts as if it is already installed.

I think this does the trick, but not 100%, let me know if it works.

---

### Post by Bausparfuchs on 2010-09-07
I just noticed the same problem. I'm trying to install .NET 2.0 on Gentoo. To install it manually from your link above does not work, too.

---

### Post by SjoerdC on 2010-09-08
same here, that is, on ubuntu 9.04
```

prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/scrijns/.cache/winetricks/dotnet20/l_intl.nls /home/scrijns/.wine/dosdevices/c:/windows/system32/
Executing wine reg delete HKLM\Software\Microsoft\.NETFramework\policy\v2.0 /f
STUB DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
------------------------------------------------------
Note: command 'wine reg delete HKLM\Software\Microsoft\.NETFramework\policy\v2.0 /f' returned status 1.  Aborting.

```
and I don't get why it's setting windows version to win2k

---

### Post by turboladen on 2010-09-09
I was having the exact same problem with my Linux Mint 9 install.  I updated my sources with the info here [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb), refreshed and found a new version of wine and winetricks were available.  I updated, then tried installing dotnet20 again and was home free.

---

### Post by lusiads on 2010-09-23
The error was because winetricks never bother to check existence of two keys it tries to delete.

From the sript of winetricks:
```
    
# Wine tries to help Mono, which breaks .Net. Can't we all just play nice...
    try $WINE reg delete "HKLM\Software\Microsoft\.NETFramework\policy\v2.0" /f
    try $WINE reg delete "HKLM\Software\Microsoft\.NETFramework" /v InstallRoot /f

```
Create two above keys with regedit tool included wine and you'll be able to install dotnet20.

---

### Post by sorpigal on 2010-09-28
In case it's not clear here is how you create the two necessary registry keys. This is required before the installation of each dotnet version, not just once.

```

wine reg add "HKLM\Software\Microsoft\.NETFramework\policy\v2.0"
wine reg add "HKLM\Software\Microsoft\.NETFramework" /v InstallRoot

```

---

### Post by Snortly on 2010-09-28
I simply commented out those lines in the winetricks script for dotnet20.

the script will add the keys as part of the load_mono26 function to install mono26.

If you never installed mono26 and have no keys, you should have no problems with commenting them out.  (ie. insert "#" at the beginning of each line with "try $WINE reg delete "HKLM\Software\Microsoft\.NETFramework .....")

---

### Post by dankegel on 2010-09-29
I think this is fixed in the latest winetricks in svn,
try [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)

The fix was in 
[http://code.google.com/p/winezeug/source/detail?r=1635](http://code.google.com/p/winezeug/source/detail?r=1635)

and should be in the next release of winetricks.

---

### Post by daas88 on 2010-09-30
I'm trying to install dotnet20 to play fifa 11 on ubuntu, but it fails... I downloaded the latest winetricks, and I get this on terminal:

```
$ ./winetricksvo dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/daniel/.winetrickscache/dotnet20/l_intl.nls /home/daniel/.wine/dosdevices/c:/windows/system32/
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: El sistema no pudo encontrar la clave o el valor del Registro especificado
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
Error: El sistema no pudo encontrar la clave o el valor del Registro especificado
Executing wine /home/daniel/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\daniel\\Temp\\IXP012.TMP\\" 00000000
------------------------------------------------------
Note: command 'wine /home/daniel/.winetrickscache/dotnet20/dotnetfx.exe' returned status 43.  Aborting.
------------------------------------------------------
```

And a window with an error, I attached a screenshot of the error... Any clue about how to fix this?

---

### Post by dino99 on 2010-10-01
> **daas88 said:**
> I'm trying to install dotnet20 to play fifa 11 on ubuntu, but it fails... I downloaded the latest winetricks, and I get this on terminal:

```
$ ./winetricksvo dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/daniel/.winetrickscache/dotnet20/l_intl.nls /home/daniel/.wine/dosdevices/c:/windows/system32/
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: El sistema no pudo encontrar la clave o el valor del Registro especificado
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
Error: El sistema no pudo encontrar la clave o el valor del Registro especificado
Executing wine /home/daniel/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\daniel\\Temp\\IXP012.TMP\\" 00000000
------------------------------------------------------
Note: command 'wine /home/daniel/.winetrickscache/dotnet20/dotnetfx.exe' returned status 43.  Aborting.
------------------------------------------------------
```

And a window with an error, I attached a screenshot of the error... Any clue about how to fix this?

report on: [http://code.google.com/p/winezeug/issues/list](http://code.google.com/p/winezeug/issues/list)

---

### Post by Mi*6d@# on 2010-10-03
> **dankegel said:**
> I think this is fixed in the latest winetricks in svn,
try [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)

The fix was in 
[http://code.google.com/p/winezeug/source/detail?r=1635](http://code.google.com/p/winezeug/source/detail?r=1635)

and should be in the next release of winetricks.

I packaged the latest svn version in my ppa

```
sudo add-apt-repository a.karimov/a.karimovppa && sudo apt-get update && sudo apt-get install winetricks
```

---

### Post by tetris9999 on 2010-10-06
> **lusiads said:**
> The error was because winetricks never bother to check existence of two keys it tries to delete.

From the sript of winetricks:
```
    
# Wine tries to help Mono, which breaks .Net. Can't we all just play nice...
    try $WINE reg delete "HKLM\Software\Microsoft\.NETFramework\policy\v2.0" /f
    try $WINE reg delete "HKLM\Software\Microsoft\.NETFramework" /v InstallRoot /f

```Create two above keys with regedit tool included wine and you'll be able to install dotnet20.

That worked for me. Thanks. :)

---

### Post by fabrizioprocopio on 2010-11-09
I pasted the code to create the 2 keys
the I try to installa dotnet20
 Yhe installation starts, crash soon and in termianl I got this

```
fabrizio@notebook-fabros:~$ sh winetricks dotnet20------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/fabrizio/.cache/winetricks/dotnet20/l_intl.nls /home/fabrizio/.wine/dosdevices/c:/windows/system32
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Operazione completata con successo
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
Operazione completata con successo
Executing wine /home/fabrizio/.cache/winetricks/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\fabrizio\\Temp\\IXP002.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f33c,0x00000001,0x33f364) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"fabrizio" (nil) 0x9ede3c (nil) 0x9ede40 0x9ede34 - stub
fixme:advapi:LookupAccountNameW (null) L"fabrizio" 0x150ed0 0x9ede3c 0x16ad78 0x9ede40 0x9ede34 - stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15
err:rpc:I_RpcGetBuffer no binding
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
fixme:imm:ImmDisableIME (-1): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize
------------------------------------------------------
Note: command 'wine /home/fabrizio/.cache/winetricks/dotnet20/dotnetfx.exe' returned status 91.  Aborting.
------------------------------------------------------
fabrizio@notebook-fabros:~$ 
```some help?

---

### Post by apocamix on 2010-11-27
I was having a different problem with installing dotnet 2.0 and managed to get it done by deleting my .wine folder.

WARNING: You will have to re-install all the programs you had in Wine.
Also if you have any file in your "Windows / C" drive you will lose those too.
Backup that folder or perhaps rename it. I'm no Linux genius but this worked for me.

---

