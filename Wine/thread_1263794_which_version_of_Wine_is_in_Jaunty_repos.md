---
title: "which version of Wine is in Jaunty repos?"
date: 2009-09-11
forum: Wine
---

### Post by MountainX on 2009-09-11
Should I install the latest version of Wine in Jaunty amd64, or just use the version in the repos?

At the moment, the only Windows app I want to run is MS Money 2003 while I transition over to GnuCash.

---

### Post by civillian on 2009-09-11
The version I had before I started using the wine repo was 9.xx i think, the newest is something like 1.1.29 but its less stable I think.
Check in the wine appdb to see whether or not the default jaunty install of wine will be okay.

---

### Post by MountainX on 2009-09-11
> **C!V!NT said:**
> The version I had before I started using the wine repo was 9.xx i think, the newest is something like 1.1.29 but its less stable I think.
Check in the wine appdb to see whether or not the default jaunty install of wine will be okay.

I used the default Jaunty version from the repos. It works great. It is amazing.

---

### Post by andrea000 on 2009-09-12
The one in the repo's is 1.0.1 it's the current 
stable version I run a few windows app's and i
find that i like 1.1.26 better i would start with
the one in the repo's first as it is the stable
version and if your program doesn't work in that
then move up one at a time and see if they have
fixed what was stopping you from running it in the
last version.

---

### Post by MountainX on 2009-09-12
> **andrea000 said:**
> The one in the repo's is 1.0.1 it's the current 
stable version I run a few windows app's and i
find that i like 1.1.26 better i would start with
the one in the repo's first as it is the stable
version and if your program doesn't work in that
then move up one at a time and see if they have
fixed what was stopping you from running it in the
last version.

Thank you. I am trying to run Microsoft Money 2003 Deluxe & Business. It install and runs perfectly except for the online banking. It will not connect to the Internet because it needs the 128 bit encryption from IE 6. I have not been able to resolve that issue yet.

Do you have IE installed in the Wine beta that you are running? Does it offer 128 bit encryption? (I think Help-About might show this.) Was it easy to get IE installed (if you have it)?

Thanks

---

### Post by andrea000 on 2009-09-12
winetricks will install ie6 for you i dont use ie6 
i just know that winetricks has it listed in there.
you can download it from [here]("http://wiki.winehq.org/winetricks")
also check [here]("http://appdb.winehq.org/") to see what others have done
to get it working

---

### Post by MountainX on 2009-09-12
> **andrea000 said:**
> winetricks will install that for you i dont use ie6 
i just know that winetricks has it listed in there.
you can download it from [here]("http://wiki.winehq.org/winetricks")

First I tried ies4linux. Others seem to have had success with that. So far, I haven't. I do have the winetricks script, so maybe I'll try that next. But I would think ies4linux would be better. I'm surprised I haven't been able to get it to work. Maybe it is a small thing (such as my default Windows version in Wine. I have tried both Win98 and WinXp so far).

---

### Post by andrea000 on 2009-09-12
check wine app database from what i see most
have it running they have it listed the
things they did to get it working.

---

### Post by MountainX on 2009-09-12
> **andrea000 said:**
> check wine app database from what i see most
have it running they have it listed the
things they did to get it working.

Thanks again. I agree that the notes there are really good. The best thread I found was this one:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728)
I've been working through the details of the different approaches described there since yesterday, but I can't get it to work yet.

One difference is that this thread is about Money 2004, and I'm using Money 2003 Deluxe + Business. However, I doubt that makes a difference. I think my problem is that I just haven't hit on the right combination of subtle details yet. 
y
So that leads to my next question. What is the best way to start again with a clean Wine install in Juanty?

What I am doing now is uninstalling Wine, deleting all the directories and then reinstalling Wine via Synaptic. Is there a better way? Can I just delete some config files? Or can I just copy an original file (or files) over my modified config files?

While I'm experimenting, I need a good way to start over again each time with a fresh Wine install. I'm having to do this after each trial, and so far I've had lots of trials (and lots of errors).

---

### Post by andrea000 on 2009-09-12
Don't uninstall anything upgrade wine then when
and if you go back to a older one then uninstall
if you uninstall it will place a deleted marker on 
your software and you'll have to get rid of that
every time you reinstall.Do you have gkdebconfig
installed?That will make it easer to install different
version it is really upgrading the wine if you have not
uninstalled it.Try installing gkdebconfig then download
a deb from wine and double click on it.

---

### Post by MountainX on 2009-09-14
**UPDATE**: This is a summary of installing MS Money 2003 Deluxe & Business under Wine in Jaunty amd64 **WITH ies4linux**. The installation works and Money works, but after any Internet access (via ie6 or Money's online banking) wineserver goes up to 100% CPU utilization and has to be killed. Other than that, **everything works, including online banking**.
------------------------------------------------------------
I finally got it to work. I posted my steps at [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2728")

Here is a copy of the steps:

Here is what I did: 
* Create a fresh install of Wine 

* Install IES4linux by doing the following from a terminal window 

wget [ www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz ]("http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz") 
$ tar zxvf ies4linux-latest.tar.gz 
$ cd ies4linux-* 
$./ies4linux -- no-gui 

NB the ies4linux install seems a bit sensitive. Keep running it until it completes installation successfully. It will eventually. 

* Copy it to the default wine bottle 

$ rm -rf ~/.wine/* 
$ cp -r ~/.ies4linux/ie6/* ~/.wine/ 

* get the WINETRICKS Script 

$ wget [ www.kegel.com/wine/winetricks ]("http://www.kegel.com/wine/winetricks") 

* run the following winetricks options to install the msi installer (we have to install one of the MSI's manually) and ensure that msmoney knows the IE6 SP1 is installed 

$ sh winetricks msi2 fakeie6 

* In the Wine Configuration ensure the the default windows version is "Windows 98" 

* run the MSMoney 2003 Setup.exe from the CD files I copied to my HDD 

All Done !

**Ooops**. I hit a major bug with ies4linux and wine.
The bug is that wineserver will consume 100% CPU whenever SSL (HTTPS) protocol is used. wineserver has to be killed manually. 

There are two bug reports here:
[http://bugs.winehq.org/show_bug.cgi?id=11916](http://bugs.winehq.org/show_bug.cgi?id=11916)
[http://bugs.winehq.org/show_bug.cgi?id=13687](http://bugs.winehq.org/show_bug.cgi?id=13687)

This affects both wine 1.0.1 and 1.1.29. (Also happens with either ies4linux 2.99.0 or 2.99.0.1.)

---

### Post by MountainX on 2009-09-16
**UPDATE**: This is a summary of installing MS Money 2003 Deluxe & Business under Wine in Jaunty amd64 **WITHOUT ies4linux**. The installation works and Money mostly works. But online banking does not work.  The 100% CPU utilization bug is not present, but neither is online banking functionality.
------------------------------------------------------------------

The wine people seem to hate ies4linux and it seems that you can't get any support from the people at WineHQ if you mention ies4linux.
[Here]("http://bookmarks.honewatson.com/2008/12/17/ie6-internet-exporer-install-ubuntu-ibex-intrepid-wine-tricks/")'s the way to install ie6 without using ies4linux:
```
sudo apt-get install wine
sudo apt-get install cabextract
wget http://www.kegel.com/wine/winetricks
sh winetricks corefonts tahoma (*optional*)
sh winetricks msi2
sh winetricks ie6
```then 

ie6 runs now, but MS Money fails to connect to online banking.
I tried the following things -- in this order, but it is all trial and error...

$ sh winetricks msi2
 * In the Wine Configuration set the default windows version to "Windows 2000" 
* run ENCPACK.EXE
*in winecfg[FONT=Verdana], set[/FONT] msi and msiexec to Builtin then Native[FONT=monospace]
[/FONT]* run SYSPACK.MSI
 * run the MSMoney 2003 Setup.exe from the CD files I copied to my HDD 

Online banking gives this error:
Runtime Error!
Program: C:\Program Files\Microsoft Money\MSMONEY.EXE
R6025
see [http://support.microsoft.com/default.aspx/kb/240437](http://support.microsoft.com/default.aspx/kb/240437)

[http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)
Reregister all dlls in ***~/.wine/drive_c/windows/system32*** directory. Open any terminal application go to this directory and run this command twice:                                                                                                                                                                                                                                ```
for i in *.dll *.ocx; do regsvr32 /i $i; done
```I also manually registered these (they are mentioned in the R6025 error bulletin at MS)
wine regsvr32 wintrust.dll
wine regsvr32 rsabase.dll 
wine regsvr32 rsaenh.dll
regsvr32 cryptdlg.dll

Still getting the error, so I tried:
* run ENCPACK.EXE (again!)

still getting the same error:
Runtime Error!
Program: C:\Program Files\Microsoft Money\MSMONEY.EXE
R6025

_Next:_
Change preferred owner and organization in ~/.wine/system.reg
Now IE6 shows 128-bit encryption. But the error R6025 persists.

**Bottom line:**
I can get everything except online banking to work when I use this method. There is no "wineserver 100% CPU" bug, but there is no online banking either.

---

### Post by MountainX on 2009-09-17
**UPDATE**: [COLOR=Blue]Thanks [Tyler]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895/comments/61")![/COLOR] This is a summary of installing MS Money 2003 Deluxe & Business under Wine in Jaunty amd64 **WITH ies4linux**. The installation works and Money works (and the 100% CPU utilization bug is **fixed**!) **Everything works, including online banking**.
------------------------------------------------------------------------------------------------

The solution is given in comment 61 [here]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895") by [Tyler Wagner]("https://bugs.launchpad.net/%7Etyler") ```
https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895
```That plus the steps [two posts above]("http://ubuntuforums.org/showpost.php?p=7949999&postcount=11") worked.

I modified ies4linux to register all DLLs (by uncommenting an existing section of code), but I doubt this made any difference.

[Bug reference]("http://bugs.winehq.org/show_bug.cgi?id=13687#c11"): [http://bugs.winehq.org/show_bug.cgi?id=13687#c11](http://bugs.winehq.org/show_bug.cgi?id=13687#c11)

_Steps with detailed output:_

```
removed wine

http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_amd64.deb
A later version is available in a software channel:
You are strongly advised to install the version from the software channel, since it is usually better supported

$ winecfg
wine: created the configuration directory '/home/my-user/.wine'
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/my-user/.wine' has been updated.
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

* Install IES4linux by doing the following from a terminal window

wget www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
$ tar zxvf ies4linux-latest.tar.gz
$ cd ies4linux-*
$ ./ies4linux --no-gui --no-flash
-----------------------------------------------------------------
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install everything at: /home/my-user/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   SCR56EN.CAB
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
  Installing IE 6
  Installing DCOM98
  Registering DLL's
  Installing TTF Fonts
  Installing ActiveX MFC42
  Installing RICHED20
  Installing registry
  Finalizing
[ OK ]

IEs4Linux installations finished!

To run your IEs, type:
 ie6
 -----------------------------

NB the ies4linux install seems a bit sensitive. Keep running it until it completes installation successfully. It will eventually.

* Copy it to the default wine bottle

$ rm -rf ~/.wine/*
$ cp -r ~/.ies4linux/ie6/* ~/.wine/

* get the WINETRICKS Script

$ wget www.kegel.com/wine/winetricks

* run the following winetricks options to install the msi installer (we have to install one of the MSI's manually) and ensure that msmoney knows the IE6 SP1 is installed

$ sh winetricks msi2 fakeie6
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Executing wget -O InstMsiA.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe
--2009-09-17 09:16:16--  http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe
Resolving download.microsoft.com... 68.142.118.173, 68.142.118.181
Connecting to download.microsoft.com|68.142.118.173|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1709160 (1.6M) [application/octet-stream]
Saving to: `InstMsiA.exe'

100%[======================================>] 1,709,160    470K/s   in 3.9s    

2009-09-17 09:16:21 (424 KB/s) - `InstMsiA.exe' saved [1709160/1709160]

Setting Windows version to win98
Executing wine regedit /home/my-user/.wine/drive_c/winetrickstmp/set-winver.reg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Executing wine /home/my-user/.winetrickscache/InstMSIA.exe
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
fixme:mscoree:GetCORSystemDirectory (0x7e7dc7b0, 260, 0x7e7dc9b8): stub!
Using native,builtin override for following DLLs: msi msiexec.exe
Executing wine regedit /home/my-user/.wine/drive_c/winetrickstmp/override-dll.reg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Clearing Windows version back to default
Executing wine regedit /home/my-user/.wine/drive_c/winetrickstmp/unset-winver.reg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Install of msi2 done
Executing wine regedit /home/my-user/.wine/drive_c/winetrickstmp/fakeie6.reg
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000005
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741819
Install of fakeie6 done
winetricks done.


* In the Wine Configuration ensure the the default windows version is "Windows 98"

~/ies4linux/ies4linux-2.99.0.1$ winecfg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet


* run the MSMoney 2003 Setup.exe from the CD files I copied to my HDD 

tried to install ie6 and failed. (This is new - I didn't see this issue with other versions of wine.)

Windows Update:
error: C:\windows\system32\drmclien.dll
"The installation will continue"
(actually installation ended)

no changes made! Just run the MSMoney 2003 Setup.exe again.
success!

Testing:
Money works (including tools menu).
Online banking works.
CPU utilization is normal (low).



```

---

