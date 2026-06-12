---
title: "Office 2007 - How to completely erase Wine and components to start from scratch?"
date: 2008-12-07
forum: Wine
---

### Post by cisco80211 on 2008-12-07
I used this howto: [http://mediakey.dk/~cc/howto-office-2007-on-linux-with-wine/](http://mediakey.dk/~cc/howto-office-2007-on-linux-with-wine/)

This worked perfect on one of my computers, but I may have missed a step on my second computer. Both running Ubuntu 8.10 with Wine 1.1.10 and Crossover Games  (crossover-games-demo_7.1.0-1_i386.deb)

I've tried uninstalling wine and then re-doing everything on this page, and Office 2007 starts and errors out right away. I do not even get to enter a serial number. I have updated my system from the Ubuntu system update utility before trying to install. I have also deleted the ~/.wine directory before trying to reinstall Wine.

How do I just delete everything and start from the beginning? 


Thanks for any help..

Cisco80211
[email]cserafin@rkon.com[/email]



This is the log from the Office 2007 installer:
===================================================================
PERF: TickCount=530 Name=OBootStrapper::Run Description=Begin function
Operating System version: 5.1.2600 Service Pack 2. Platform ID: 2
Running on a 32-bit operating system.
Command line: setup.exe
No command line arguments given
Verify file signature in "Z:\home\chris\Desktop\office2007\setup.exe"
Verify file signature in "Z:\home\chris\Desktop\office2007\Ultimater.WW\OSETUP.DLL"
Using setup controller dll at [Z:\home\chris\Desktop\office2007\Ultimater.WW\OSETUP.DLL].
PERF: TickCount=1936 Name=OBootStrapper::Run Description=Calling RunSetup
Opening log file C:\windows\temp\SetupExe(200812071719108).log.
=========================================================================

PERF: TickCount=1940 Name=RunSetup Description=Begin function
Catalyst execution began: 12/07/2008 17:19:10.
Setupexe Resiliency Mode is set to [PerformIfApplicable]; thus Resiliency is [disabled] for the [InstallExecutionMode]
Searching for updated versions of resource files under the 'updates' folder [Z:\home\chris\Desktop\office2007\updates].
Found [0] resource files under the update folder.
Searching for default versions of resource files under the folder [Z:\home\chris\Desktop\office2007].
Resource File Manager : Found (CultureTag=en-US) resource file at [Z:\home\chris\Desktop\office2007\Office.en-usOSETUPUI.DLL].
Found [1] resource files under the default folder.
Resource File Manager : Current user's LCID is [1033].
Resource File Manager : Selecting resource file (File=Z:\home\chris\Desktop\office2007\Office.en-us\OSETUPUI.DLL) for CultureTag [en-US].
Running in [InstallExecutionMode]. Run from TEMP folder at [C:\windows\temp\Setup00000008].
Loaded resource file [C:\windows\temp\Setup00000008\OSETUPUI.DLL] (CultureTag=en-US).
Loaded Dll : Z:\home\chris\Desktop\office2007\Ultimater.WW\OSETUP.DLL.
Catalyst version is : 12.0.4518.1014
JobExecutionMode is InstallExecutionMode.
Error: CoCreateInstance failed HResult: 0x80070005. 
Catalyst execution finished: 12/07/2008 17:19:11.  Return code: 30023.  Exception caught: HResultOnly.
PERF: TickCount=2398 Name=RunSetup Description=End function
=========================================================================

---

### Post by binbash on 2008-12-07
rm .wine

Also 1.10 is out

---

### Post by cisco80211 on 2008-12-07
I did fully remove the ~/.wine folder with the same results.


I also did 'sudo aptitude purge wine' and started from scratch, same result.

---

### Post by hikaricore on 2008-12-07
Unless your howto guide had you replacing wine libraries or something the method you used is the correct one to completely remove WINE.
What makes you think WINE was not fully removed when it was?

---

### Post by heheman3000 on 2009-02-02
I'm having the same problem with Gentoo. I don't think that it's a case of wine installed improperly, rather that something is different in the OS.

---

### Post by heheman3000 on 2009-02-02
Ahh, this was fixed when I added overrides for all the libraries per [this guide]("http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/").

---

