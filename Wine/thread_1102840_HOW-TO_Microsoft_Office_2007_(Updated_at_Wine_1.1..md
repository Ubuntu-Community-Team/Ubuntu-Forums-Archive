---
title: "HOW-TO: Microsoft Office 2007 (Updated at Wine 1.1.17)"
date: 2009-03-22
forum: Wine
---

### Post by NightMKoder on 2009-03-22
Most, if not all, of this is taken from Wine's AppDB entry for Office 2007 install: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

First, some notes (can skip, but don't say I didn't warn you!):

[LIST=1]
[*]Make sure that you do NOT have any other applications installed/used winetricks. This guide is not designed to account for all the situations of your wine installation, but may still work (give it a shot!). 
If you really need Office 2007, while keeping your normal wine directory intact, you can always change the wine prefix during installation. Simply type
```

WINEPREFIX=~/.wine_office2007

```before any command that starts with *wine* in this guide.
[*]This guide only works for wine versions 1.1.3 or later. This is not the version that is normally in Ubuntu (1.0.1).
[*]**NOTE: THIS IS NO LONGER VALID STARTING WINE 1.1.24!**:
Sadly the 1.1.23 wine version does not allow you to install Office 2007 due to a regression. To remedy this, we will install an earlier version.
[/LIST]

Now to install it:
[LIST=1]
[*]First you need to add the wine development repository. Wine's website has a wonderful guide on how to do this at [http://winehq.org/download/deb](http://winehq.org/download/deb) . You will actually NEED to install wine 1.1.24+ to get office to install correctly
After you add the repository, open your package manager (synaptic/adept) and do an upgrade of wine. Now open a terminal and type ```
wine --version
``` to make sure that wine reports ```
wine-1.1.24
```
[*]Now pop in your Office 2007 CD, open it with your file manager, find the file called Setup.exe, and double click it. The setup should work completely. **NOTE:** Due to some bugs in wine, you cannot go back to the install wizard to change which programs to install, so make sure to get everything on the first go.
For those of you that want to do an alternate prefix install, you would need to mount your cd-rom drive (it will be somewhere in /media), and do:
```

WINEPREFIX=~/.wine_office2007 wine Setup.exe

```
[/LIST]

Now you have Office 2007 installed (and you should be able to run most programs). There are two small tweaks to wine that you need to do to make it run a little better. Open up the wine configuration:
```

winecfg

```(Yes, this means add WINEPREFIX=~/.wine_office2007, if you need to!)

Make sure that the Windows Version is set to Windows XP (Applications Tab).
In the Libraries section, you need to add two overrides: "riched20" and "usp10". To do this, simply type the the names (no quotes) into the dropdown-looking textbox, and click "Add". Repeat this for both of the overrides, and you are done!

This will get you to a point of (almost) Word/Excel perfection. However, several things will not work. Here are the things that don't work and how to solve the problem (if a solution exists):
[LIST]
[*]**Service Pack n doesn't install.** It doesn't. Still working on it.
[*]**Excel crashes on start.** This relates to not being able to open the user name dialog. Just exit excel (and run `wineserver -k` to make sure its gone), then start word, fill in your name and exit word. Start excel again, and it should work. (Thanks Mack1)
[*]**Powerpoint does not start (crashes).** Make sure you set the riched20 override in winecfg.
[*]**Access does not start.** You need to install MSVC2005 Libraries:
Get winetricks:
```

wget http://www.kegel.com/wine/winetricks
chmod +x winetricks

```Run (and change prefix if need be):
```

./winetricks vcrun2005

```
[*]**My fonts look weird/always bold.** If this is about Calibri looking weird - it is a known bug. As for Arial looking bold or not showing up, you need to do
```

./winetricks corefonts

```
[*]**Thesaurus does not work.** You need the windows scripting host. Use winetricks (how to get above) and run:
```

./winetricks wsh56js

``` and also open winecfg and set jscript to native.
[*]**How do I default programs to opening in Office 2007?**
Here is an example of how to do it for word:
[LIST]
[*]**Kubuntu:**
System Settings->Advanced->File Associations->Search for "word"
For each of application/msword, application/vnd.openxmlformats-officedocument.wordprocessingml.document:
Click on it. Click "+ Add" on the right side. Type:
```

wine "C:\Program Files\Microsoft Office 2007\Office12\WINWORD.EXE" "`winepath -w \"%U\"`"

```in the textbox, and click ok. (NOTE: Your path may be different. Just make sure you can start word by doing `wine "C:\Program Files\Microsoft Office 2007\Office12\WINWORD.EXE"`, and otherwise find the correct path by browsing through ~/.wine/drive_c. Thanks sukumade.) Make sure the new entry (it will be called wine) is on top. Feel free to select it and click edit to change the name/icon, etc.
[*]**Ubuntu:**
Someone care to contribute? (I use kubuntu, so I can't test). The command should be the same.
[/LIST]
 
[*]**Bullets don't show/bad stuff relating to.** Install wine 1.1.23 from [http://winehq.org/download/deb](http://winehq.org/download/deb) , or if you have access to a windows installation, copy symbol.ttf to ~/.wine/drive_c/windows/fonts .
[*]**Can't open documents created in Office <=2003 with equations in them.** Known issue. Only the equation ribbon will work.
[*]**{Something from another application embedded in document} does not work/crashes when opened.** Known issue. This relates to charts, equations (not ribbon), and a slew of other features (Insert->Object).
[/LIST]

I hope this helps people, as you most definitely do not need to download/install anything other than wine to get Office installed.

Comments & criticism welcome.


**NOTE: THESE INSTRUCTIONS ARE OUTDATED SINCE WINE 1.1.24, USE THE ABOVE INSTRUCTIONS; THESE ARE HERE FOR REFERENCE.**
> 
[LIST=1]
[*]Office 2007 requires the latest development release of wine. As is noted above however, this will have to be done in 2 steps. First, we download wine version 1.1.16 (links from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) (Note to Jaunty users - there is no 1.1.16 specifically for jaunty, so we use intrepid's. It works fine)
[LIST]
[*]**Intrepid/Jaunty:** [http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16%7Ewinehq0%7Eubuntu%7E8.10-0ubuntu1_i386.deb")
[*]**Hardy:** [http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.16~winehq0~ubuntu~8.04-0ubuntu1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.16%7Ewinehq0%7Eubuntu%7E8.04-0ubuntu1_i386.deb")
[/LIST]
 
[*]Once you downloaded the file (anywhere will do), just double click it, and let it install. **NOTE:** If you already have wine 1.1.17/1.1.18/1.1.19/1.1.20/1.1.21/1.1.22/1.1.23 installed, you will have to uninstall it first (use synaptic/adept)
Now you should have wine 1.1.16 installed. If you want to verify this, open up a terminal and type in
```

wine --version

```which should report: wine-1.1.16
[*]Now pop in your Office 2007 CD, open it with your file manager, find the file called Setup.exe, and double click it. The setup should work completely. **NOTE:** Due to some bugs in wine, you cannot go back to the install wizard to change which programs to install, so make sure to get everything on the first go.
For those of you that want to do an alternate prefix install, you would need to mount your cd-rom drive (it will be somewhere in /media), and do:
```

WINEPREFIX=~/.wine_office2007 wine Setup.exe

```
[*]After you complete the installation, I strongly suggest adding the wine development repository. Wine's website has a wonderful guide on how to do this at [http://winehq.org/download/deb](http://winehq.org/download/deb) . You will actually NEED to install wine 1.1.17+ to get symbols/bullets to work correctly.
After you add the repository, open your package manager (synaptic/adept) and do an upgrade of wine.
[/LIST]


---

### Post by sukumade on 2009-03-23
Thanks for this great HOW-TO. 

I basically followed it from beginning to end, although I did have a bit of an issue when I was setting the default applications to open. My installation of Office was in "C:\Program Files\Microsoft Office\Office12\" instead of "Microsoft Office 2007". It threw me off for a second until I tried to run it via the terminal and it said the path did't exist.

Anyways, thanks for the wonderful write-up. With the regression issue with 1.1.17 I was a bit stumped as to the best solution, but this was it. 

Take care!

---

### Post by NightMKoder on 2009-03-23
Good to see it was (relatively) painless for you. I added the bit about the path being different. Thanks for the tip.

---

### Post by aceplayer97 on 2009-03-25
Thanks! Wouldn't have been able to install anything without this awesome guide :guitar:!

---

### Post by griffter on 2009-03-27
OK, so I got the 2007 suite installed and all the apps launch fine and work fine save for Outlook 2007.

I've been fighting with wine 1.1.15, 1.1.16 and 1.1.17 for the past few days across several distros and in all instances, any app that I try to install that requires network support to function, fails.  

Take Outlook 2007 for example - trying to setup the mapi profile to connect to Exchange fails during the autodiscover process and if I choose to manually configure the settings, the server can't be found.

running iexplore.exe that's included with the wine install works fine and brings up the winehq page however - how frustrating!  I'm so close!!!

Right now I'm running 1.1.16 following this HOW-TO - I haven't upgraded to 1.1.17 yet.  I just installed IE7 and I get the Cannot find "%ws" message.

I copied over pine.exe from my XP install and tried to ping several server name by IP, netbios name and fqdn.  All result in in an Error 5 complaining about no TCP/IP stack!!!!

How can the installed version of IE with wine work to bring up winehq but any other app that needs network support not work?!?!?

~griff

---

### Post by allenreed on 2009-03-27
Thanks dude for helping me out and for the awesome guide cause even tho i run windows on this computer one of my employee on his comp he runs Ubuntu so i got it so that we wouldn't have to mess around with his comp. Thank you so much now we got his computer working with office 2007!

---

### Post by Duds55 on 2009-03-27
Thanks

Just one little thing - In order to get Access working first i installed vcrun2005 with winetricks as stated above however i was still getting errors:


[FONT="Courier New"]Could not find dependent assembly L"AceDAO"
import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\MSACCESS.EXE") not found[/FONT]


I finally hit on this solution:

Amend the manifest file for access msaccess.exe.manifest found in [Your Wine Prefix]../Program Files/Microsoft Office/Office12 and remove the dependency reference to AceDAO, ie amend the file and remove the following lines:

<dependency>
<dependentAssembly>
<assemblyIdentity type="win32" name="AceDAO" version="12.0.0.0" language="*" processorArchitecture="X86">
</assemblyIdentity>
</dependentAssembly>
</dependency>

At least i can run it now - Office version is Office Enterprise

---

### Post by NightMKoder on 2009-03-27
> **griffter said:**
> OK, so I got the 2007 suite installed and all the apps launch fine and work fine save for Outlook 2007.

I've been fighting with wine 1.1.15, 1.1.16 and 1.1.17 for the past few days across several distros and in all instances, any app that I try to install that requires network support to function, fails.  

Take Outlook 2007 for example - trying to setup the mapi profile to connect to Exchange fails during the autodiscover process and if I choose to manually configure the settings, the server can't be found.

running iexplore.exe that's included with the wine install works fine and brings up the winehq page however - how frustrating!  I'm so close!!!

Right now I'm running 1.1.16 following this HOW-TO - I haven't upgraded to 1.1.17 yet.  I just installed IE7 and I get the Cannot find "%ws" message.

I copied over pine.exe from my XP install and tried to ping several server name by IP, netbios name and fqdn.  All result in in an Error 5 complaining about no TCP/IP stack!!!!

How can the installed version of IE with wine work to bring up winehq but any other app that needs network support not work?!?!?

~griff

I'm guessing windows has some sort of layer that it uses to connect to exchange that wine probably doesn't implement. Post the log output of the part when it fails. Also, if you want to run ping, you must do it as root, and then it somewhat works. Sadly you can't use your own wineprefix so you must hack around it:
```

$ sudo -i
# cd your_windows_install_location/system32
# WINEPREFIX=/root/.wine wine ping.exe google.com

```
Wine AppDB shows that outlook just doesn't work, and it doesn't seem like a lot of people are trying to get it to work.

Duds:
It seems like you're still getting the vc runtime files error (msvcr80 is part of the runtime). (If you care to try) do `winetricks vcrun2005sp1` and see if that helps.

---

### Post by griffter on 2009-03-27
> **NightMKoder said:**
> I'm guessing windows has some sort of layer that it uses to connect to exchange that wine probably doesn't implement. Post the log output of the part when it fails.

Here's the output when it fails:
Object
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
fixme:winhttp:receive_response authentication not supported
fixme:winhttp:set_credentials unimplemented authentication scheme 10
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.

It looks like 1.1.18 is going to support RPC over HTTPS which is what the autodiscover service for Outlook uses.  
[http://www.winehq.org/announce/1.1.18](http://www.winehq.org/announce/1.1.18)

---

### Post by NightMKoder on 2009-03-28
> **griffter said:**
> Here's the output when it fails:
Object
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
fixme:winhttp:receive_response authentication not supported
fixme:winhttp:set_credentials unimplemented authentication scheme 10
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.

It looks like 1.1.18 is going to support RPC over HTTPS which is what the autodiscover service for Outlook uses.  
[http://www.winehq.org/announce/1.1.18](http://www.winehq.org/announce/1.1.18)

You seem to be right. That guid corresponds to TF_ThreadMgr, which was implemented in 1.1.18. Tell us how it goes (and report it on appdb too).

---

### Post by griffter on 2009-03-28
> **NightMKoder said:**
> You seem to be right. That guid corresponds to TF_ThreadMgr, which was implemented in 1.1.18. Tell us how it goes (and report it on appdb too).

I'll see what I can do with it here.  The first pass during the ./configure of 1.1.18 led me down a long dependency - libjpeg-devel, libpng-devel, libssl-devel, libxslt-devel and Header Files for OpenGL.  Not fun!

I waded through all that and my first pass at the install of Office 2007 Enterprise errors out.

I'll post back later after I have a chance to fight longer with it.  The good news is that I did see (during compiling) the support for the ntlm_auth and all the required winbind dlls needed to make the mapi process of Outlook work. 

~griff

---

### Post by AndrewTheArt on 2009-04-04
Worked great. You may want to recommend purging the winetrickscache folder (rm -fR /home/username/.winetrickscache) before doing any of this -- it couldn't hurt!

I only wish this guide got more exposure. I literally went through hoops before stumbling across this page.

---

### Post by zpreston on 2009-04-13
Thank you so much for this.  I have spent way too much time trying different ways to get this to work.  So far, this has been the only successful way for me(other than CrossOver, but who wants to pay $40 for something that can be done free?)

Outlook crashes on me whenever I try and open it, it says "Cannot open your default e-mail folders.  The information store could not be opened."  The only option I have is to click OK, and then Outlook closes.  It's strange, but I can live without Outlook if there isn't an easy fix to it.

Thanks again.

---

### Post by NightMKoder on 2009-04-13
> **griffter said:**
> I'll see what I can do with it here.  The first pass during the ./configure of 1.1.18 led me down a long dependency - libjpeg-devel, libpng-devel, libssl-devel, libxslt-devel and Header Files for OpenGL.  Not fun!

I waded through all that and my first pass at the install of Office 2007 Enterprise errors out.

I'll post back later after I have a chance to fight longer with it.  The good news is that I did see (during compiling) the support for the ntlm_auth and all the required winbind dlls needed to make the mapi process of Outlook work. 

~griff

[http://www.codeweavers.com/compatibility/browse/group/?app_id=2841;tips=1](http://www.codeweavers.com/compatibility/browse/group/?app_id=2841;tips=1) I found this while researching outlook. Seems there is a way around the networking problems (not sure if that's what you're getting)

> **zpreston said:**
> Thank you so much for this.  I have spent way too much time trying different ways to get this to work.  So far, this has been the only successful way for me(other than CrossOver, but who wants to pay $40 for something that can be done free?)

Outlook crashes on me whenever I try and open it, it says "Cannot open your default e-mail folders.  The information store could not be opened."  The only option I have is to click OK, and then Outlook closes.  It's strange, but I can live without Outlook if there isn't an easy fix to it.

Thanks again.

It seems most people don't have problems running Outlook 2007 under wine. Would you post console output/wine version? 

On a sidenote, the $40 you pay to crossover goes toward wine development. [http://www.codeweavers.com/about/philosophy/](http://www.codeweavers.com/about/philosophy/) It's more of a donation with something in return. If you don't want to do simple donation, I would consider buying a codeweavers product.

---

### Post by zpreston on 2009-04-14
> **NightMKoder said:**
> 

It seems most people don't have problems running Outlook 2007 under wine. Would you post console output/wine version? 

On a sidenote, the $40 you pay to crossover goes toward wine development. [http://www.codeweavers.com/about/philosophy/](http://www.codeweavers.com/about/philosophy/) It's more of a donation with something in return. If you don't want to do simple donation, I would consider buying a codeweavers product.

I am using wine-1.1.19 and Outlook 2007 Enterprise.  As for the "console output," I am sorry, but I am really new at Ubuntu and don't know how to get that.  I open Outlook 2007 and I have the Terminal open, but nothing happens in the terminal.

Thanks for clarifying the $40 charge/donation thing though!

---

### Post by NightMKoder on 2009-04-14
You're actually very close. The terminal is sort of like Window's command prompt. Since you're running outlook using wine, you would need to type in something like:
```

wine "C:\Program Files\Microsoft Office 2007\Office12\Outlook.exe"

```

Then outlook should start (and crash), but you will get a whole bunch of fixme and maybe some err's in the terminal.

---

### Post by sapito318 on 2009-04-15
Hi,
Thanks for this nice guide. I seem to be having trouble though. I had a previous installation of Wine (1.1.19) which ran fine, but after uninstalling the 1.1.19 and reinstalling version 1.1.16 I seem to be running into some problems installing MS 2007. It looks like it is just hanging up in the install. Any suggestions?

---

### Post by NightMKoder on 2009-04-15
> **sapito318 said:**
> Hi,
Thanks for this nice guide. I seem to be having trouble though. I had a previous installation of Wine (1.1.19) which ran fine, but after uninstalling the 1.1.19 and reinstalling version 1.1.16 I seem to be running into some problems installing MS 2007. It looks like it is just hanging up in the install. Any suggestions?

A few things - 
1. make sure `wine --version` outputs wine-1.1.16.
2. make sure you have no overrides set in winecfg
3. if you're talking about the slight freeze when entering the cd-key, that's normal, just wait.
4. try installing with a fresh wine prefix, ie something like (in terminal)
```

WINEPREFIX=~/.wine_office2007 wine Setup.exe

```
5. if all above fails and it freezes somewhere, post your office version (enterprise/student/etc), what kind of install you used (ie typical,minimal,custom-specify what), and where it froze exactly.

This really shouldn't happen with the original version of Office 2007, but I know that SP1 does not install, so if you have a cd of office with SP1 on it, it might not work. (not sure how to check though)

---

### Post by sapito318 on 2009-04-15
Hi,
I am no longer encountering the aforementioned freeze on install as I was able to successfully install OFfice 07. Seems that there was some problem with winetricks that was previously installed. I removed that and it seemed to work OK after that, although the install bar did not seem to go all the way to the end.

My wine version was 1.1.16 when I installed, I then upgraded to 1.1.19 afterwards adn ran the winecfg instructions as directed.

What is happening now is that if I open Excel, it hangs up and does not do anything, looks to be frozen or something...

---

### Post by zpreston on 2009-04-15
Here is what I get from the Terminal, its quite a bit:

```
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msimtf:DllGetClassObject ({c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} {00000001-0000-0000-c000-000000000046} 0x32f924)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} could be created for context 0x1
fixme:msimtf:DllCanUnloadNow ()
err:ole:CoCreateInstance apartment not initialised
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.0", (null), 0x00000000, 0x00000051, (nil), 0x00000000, (nil), 0x32f57c, 0x0000001e, 0x32f574) stub
fixme:mscoree:GetCORVersion (0x32f57c, 30, 0x32f574): semi-stub!
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterTraceGuidsW 0x38ee62e8 0x441230 0x441238 14 0x4423e0 (null) (null) 0x441248
fixme:process:SetProcessShutdownParameters (00000180, 00000000): partial stub.
fixme:loadperf:InstallPerfDllW ((null), L"C:\\prog~fbu\\micr~hfz\\office12\\1033\\outlperf.ini", 0)
fixme:advapi:RegisterEventSourceA ((null),"Outlook"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Outlook"): stub
fixme:advapi:RegisterEventSourceA ((null),"Outlook"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Outlook"): stub
err:animate:ANIMATE_WindowProc unknown msg 0410 wp=00000000 lp=00000000
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32f5d0 0 0x338 0x3917f380 - stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32e804 0 0x3d4 0x3917f380 - stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32e4c4 0 0x494 0x3917f380 - stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32785)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
err:rpc:I_RpcGetBuffer no binding
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32782)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32781)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32780)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32772)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:hook:IsWinEventHookInstalled (32778)-stub!
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32dbfc 0 0x564 0x3917f380 - stub
fixme:msctf:ThreadMgr_fnActivate STUB:(0x135060)
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32dba4 0 0x570 0x3917f380 - stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x281dab0 0 0x594 0x3917f380 - stub
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:advapi:CheckTokenMembership ((nil) 0x1938d0 0x32c384) stub!
fixme:rpc:RpcMgmtEnableIdleCleanup (): stub
fixme:ole:CoSuspendClassObjects 
fixme:advapi:CheckTokenMembership ((nil) 0x152b50 0x32fdd4) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x152b50 0x32fdd4) stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00001b58,(nil),0x0006,0x00000000,0x32fd34,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

---

### Post by NightMKoder on 2009-04-16
Nothing obvious is sticking out to me - I guess it doesn't work entirely yet. The appdb page for outlook seems to have a bunch of bugs that have nasty workarounds, but noone seems to really be fixing them.

I would suggest using something other than outlook for now.

---

### Post by Mack1 on 2009-04-20
> **sapito318 said:**
> Hi,

What is happening now is that if I open Excel, it hangs up and does not do anything, looks to be frozen or something...

Hi, 

This solves your problem:

- kill the excel process through using CTRL + ESC, look for excel.exe

- just open up word, it asks you for your usercredentials just like in windows. Once Word has started, close it.

- Now start excel, voila! Works like a charm. The above only needs to be done once.


And to the topic starter: you're a lifesaver! thanks very much.

The only thing i have not got working is that the normal font in windows, arial is not working. it says it uses it but it isn't available in the font-menu thingy.

Maybe i need to install msttcorefonts, will try that.

Update: ok, you have to install msttcorefonts to get the windows fonts like arial in office2007.
            (sudo apt-get install msttcorefonts)

However, now all letters are shown in bold and i cannot change them.....hmm will have to see how to fix this.

---

### Post by kpatz on 2009-04-20
> **NightMKoder said:**
> 
**Thesaurus does not work.** You need the windows scripting host. Use winetricks (how to get above) and run:
```

./winetricks jscript

```
The correct winetricks command to install WSH jscript is:
```
./winetricks wsh56js
```

---

### Post by NightMKoder on 2009-04-20
> **Mack1 said:**
> Hi, 

This solves your problem:

- kill the excel process through using CTRL + ESC, look for excel.exe

- just open up word, it asks you for your usercredentials just like in windows. Once Word has started, close it.

- Now start excel, voila! Works like a charm. The above only needs to be done once.


And to the topic starter: you're a lifesaver! thanks very much.

The only thing i have not got working is that the normal font in windows, arial is not working. it says it uses it but it isn't available in the font-menu thingy.

Maybe i need to install msttcorefonts, will try that.

Update: ok, you have to install msttcorefonts to get the windows fonts like arial in office2007.
            (sudo apt-get install msttcorefonts)

However, now all letters are shown in bold and i cannot change them.....hmm will have to see how to fix this.

I'll add that to the tutorial. Try `winetricks allfonts`.

> **kpatz said:**
> The correct winetricks command to install WSH jscript is:
```
./winetricks wsh56js
```

Thanks, I didn't know that. (Just copied from appdb)

---

### Post by JonyBoyct on 2009-04-21
Thanks **NightMKoder**! It worked like a charm. 
Install office 2007 on Ubuntu Studio Both on 8.04 and 8.10!

---

### Post by JonyBoyct on 2009-04-21
Some times Power Point will not start.  But just reboot it and it's good.
And this problem only started after I tried to install WC3.
Thanks again.

---

### Post by JonyBoyct on 2009-04-29
Now that I have my system set up just the way i like it, I'm a little apprehensive about upgrading to 9.04.  Will I have to install Office 2007 again?  If you noticed in one of my earlyer posts I said that your instructions worked for both 8.04 and 8.10.  That is because I tried to upgrade from 8.04 to 8.10 and lost every thing.  NightMKoder, did you have any trouble upgrading from 8.10 to 9.04?  Also does Office 2007 32 bit, work in a 64 bit OS?

---

### Post by zpreston on 2009-04-29
> **JonyBoyct said:**
> Now that I have my system set up just the way i like it, I'm a little apprehensive about upgrading to 9.04.  Will I have to install Office 2007 again?  If you noticed in one of my earlyer posts I said that your instructions worked for both 8.04 and 8.10.  That is because I tried to upgrade from 8.04 to 8.10 and lost every thing.  NightMKoder, did you have any trouble upgrading from 8.10 to 9.04?  Also does Office 2007 32 bit, work in a 64 bit OS?

I upgraded from 8.10 to 9.04, and it worked great!  Everything was still there and worked fine.  I don't know if this will work on a clean install of 9.04, but it does work if you are just upgrading.

---

### Post by least on 2009-05-03
Thank you for this guide!
I've done a fresh setup of Jaunty so I lost my old wine installation and was unable to install Office again. With your guide it was no problem to solve this problem. Just pick the Intrepid version from wine - it's no problem for Jaunty. 

Due my migration from Windows to Linux I've an existing NTFS partition and I noticed, that wine is not able to open the new Office Formats from NTFS with a double click - I had to open Word and open the file through Word - boring!

I find a solution for this problem and I thought this would be a good place to mention.

The solution is based on the posting from Nick Koch in [http://www.wine-reviews.net/wine-reviews/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html](http://www.wine-reviews.net/wine-reviews/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html)

For me only solution step 2 worked.
```
2. by making sh scripts in your ~/bin folder. ie excel and have
the following code:

#!/bin/bash
wine "C:\\Program Files\\Microsoft Office\\OFFICE12\\EXCEL.EXE" "`winepath -w "$@"`"
```

Then I edited the properties of the *.docx files and choose "Open With" -> "New" -> sh /usr/bin/excel.sh

Reply this procedure for the other programms and extensions.

Now you should be able to open your Office files wherever they are!

---

### Post by Zyren on 2009-05-04
im trying to install wine 1.1.16 from the download provided, but i keep getting an: Error: Wrong architecture 'i386'

how do i fix this so i can install wine?

thanks

---

### Post by NightMKoder on 2009-05-04
> **Zyren said:**
> im trying to install wine 1.1.16 from the download provided, but i keep getting an: Error: Wrong architecture 'i386'

how do i fix this so i can install wine?

thanks

So you're either running x64 or otherwise - go to the website next to the links ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) and wine 1.1.16 for your architecture. (x64 -> amd64)

---

### Post by NewatUbunt on 2009-05-05
I just wanted to thank KnightMKoder for the post.  I had tried a different how-to located elsewhere with no results whatsoever, but the techniques posted here worked great.  In fact all the Office apps seem to run fine now, except that I get a weird error message after OneNote exits (but the message does not appear to injure the data at all).

Thanks again for the great info, this is a big help for me.

---

### Post by atulkakrana on 2009-05-06
please follow the link for my new wiki article.

[http://en.wikipedia.org/wiki/Office_2007_in_ubuntu_8.10](http://en.wikipedia.org/wiki/Office_2007_in_ubuntu_8.10)

It works like a charm and no issue till date:popcorn:

---

### Post by NightMKoder on 2009-05-06
> **atulkakrana said:**
> please follow the link for my new wiki article.

[http://en.wikipedia.org/wiki/Office_2007_in_ubuntu_8.10](http://en.wikipedia.org/wiki/Office_2007_in_ubuntu_8.10)

It works like a charm and no issue till date:popcorn:

```

sh ./winetricks msxml3 vcrun2003 vcrun2005sp1 vcrun2008 gdiplus riched20 riched30 msxml3 msxml4 msxml6 tahoma vb3run vb4run vb5run vb6run vcrun6 msi2 allfonts dotnet11 corefonts wsh56js

```

Is generally not cool and probably majorly messes with wine. In general, the less winetricks you have to install the better.

Also seems like your article is going to be deleted?

---

### Post by atulkakrana on 2009-05-07
Follow the link


[http://ubuntuforums.org/showthread.php?p=7231643#post7231643](http://ubuntuforums.org/showthread.php?p=7231643#post7231643)

---

### Post by atulkakrana on 2009-05-07
To NightNkoder

With all due respect, you may be right.

But winetricks only screws wine with wrong override.

Winetricks works wonder when used carefully, it saves hell lot of time and even noobs can use it.

It is working perfectly with all of the computers I have.

Its 100% when used correctly.

About my article on wikipedia, Please help and edit it...I dont understand there policies....

---

### Post by the8thstar on 2009-05-07
Can you update Office with Service Pack 1 and 2 through Wine?

---

### Post by NightMKoder on 2009-05-07
> **atulkakrana said:**
> To NightNkoder

With all due respect, you may be right.

But winetricks only screws wine with wrong override.

Winetricks works wonder when used carefully, it saves hell lot of time and even noobs can use it.

It is working perfectly with all of the computers I have.

Its 100% when used correctly.

About my article on wikipedia, Please help and edit it...I dont understand there policies....

Fair enough I guess. I looked at the list of winetricks again and I'm only really concerned with two of them: gdiplus and msi2, which is still relatively ok compared to other guides overriding rpcrt4. I'm sorry for lashing out at you, I'm just a little annoyed at older guides.

> **the8thstar said:**
> Can you update Office with Service Pack 1 and 2 through Wine?

Not yet, but I'm working on finding bugs with SP1 (some of the updates install on wine git)

---

### Post by aceplayer97 on 2009-05-25
Okay I need some help with installing lol. I am able to install one Microsoft Office 2007 program but none after that. I first installed Powerpoint 2007 and it works perfectly. Then I proceeded to install Word 2007 and halfway through the install it stopped and said it encountered an error. Does anyone seem to know what the problem is?

---

### Post by NightMKoder on 2009-05-25
Hmm...Probably should've noted in the guide that you can't do that.

You have to install all the programs you want at once. Going back to the installation doesn't work.

So remove your wine prefix (rm -Rf ~/.wine) and try again.

---

### Post by aceplayer97 on 2009-05-25
I know this might sound stupid but how do I install more the one at the same time?

---

### Post by NightMKoder on 2009-05-25
> **aceplayer97 said:**
> I know this might sound stupid but how do I install more the one at the same time?

Errr...then what are you doing? Doesn't your installer look like: [http://samanathon.com/images/microsoft-office-install.png](http://samanathon.com/images/microsoft-office-install.png) ? What do you press after that?

If you just press install now it installs most of it, I think.

---

### Post by aceplayer97 on 2009-05-25
> **NightMKoder said:**
> Errr...then what are you doing? Doesn't your installer look like: [http://samanathon.com/images/microsoft-office-install.png](http://samanathon.com/images/microsoft-office-install.png) ? What do you press after that?

If you just press install now it installs most of it, I think.

It looks like this:

[http://i380.photobucket.com/albums/oo245/aceplayer97/msoinstaller.jpg](http://i380.photobucket.com/albums/oo245/aceplayer97/msoinstaller.jpg)

---

### Post by NightMKoder on 2009-05-25
What edition of office is that?

---

### Post by aceplayer97 on 2009-05-25
> **nightmkoder said:**
> what edition of office is that?

2007

---

### Post by NightMKoder on 2009-05-25
Sorry I mean what edition of office 2007? cause it definitely aint ultimate, or professional or...anything else

---

### Post by aceplayer97 on 2009-05-25
> **NightMKoder said:**
> Sorry I mean what edition of office 2007? cause it definitely aint ultimate, or professional or...anything else

Well its a burned onto a random CD so I'm guessing its the pirated version lol

---

### Post by NightMKoder on 2009-05-25
Riiight, I'm gonna go with we don't support pirated software here & that is NOT office 2007.

---

### Post by aceplayer97 on 2009-05-26
> **NightMKoder said:**
> Riiight, I'm gonna go with we don't support pirated software here & that is NOT office 2007.

Okay looks like using a pirated copy wasn't a good idea lol. It screwed up my computer and I had to reinstall Ubuntu. Then I went out and bought a copy of Microsoft Enterprise which did install everything at once. Looks like I learned my lesson today: Don't use pirated software lol. But I have one question: I install MSVC2005 Libraries but Access still doesn't start. Why is that?

---

### Post by aceplayer97 on 2009-05-26
Sorry for the double-post, but what version of WINE should you upgrade to after installing Microsoft Office 2007? I had upgraded to the latest version (version 1.1.22) but then none of the Microsoft Office 2007 applications would load at all.

---

### Post by jhoeijao on 2009-05-30
NightMKoder, thanks for your great guide. I learned a lot on it together with the comments from the people who visited this guide..I've posted a similar guide like this if you have time please feel free to visit and your comment will be greatly appreciated. If my post is not informative enough then I'm willing to delete it by myself I don't want give other people problems in installing MS OFFICE 2007 using Wine especially the noobs like me because a lot of the tutorials online are not worth trying.

Thanks.

---

### Post by SystemR89 on 2009-06-02
I installed Office 2003 using a different wine prefix but now I don't know how I can set files association with office installed not in the default wine prefix.

What I can do?

Thank You!

---

### Post by NightMKoder on 2009-06-02
> **SystemR89 said:**
> I installed Office 2003 using a different wine prefix but now I don't know how I can set files association with office installed not in the default wine prefix.

What I can do?

Thank You!

same way as you would for the normal one, just put WINEPREFIX=... wine ... instead of just wine ...

---

### Post by arashiko28 on 2009-06-03
=D>=D>=D>=D> You deserve a standing ovation!!! I have been after this since I changed completely to Ubuntu, not that I need it, I do everything with openoffice equally or even better, but I needed to be able to open a pptx without having it messed up or deconfigured.

It works like a charm, I only installed word, power point and excel, I don't need anything more, plus the tools, now. I use Ubuntu and I can't find the application to associate the programs. I have to go do like a dozen clicks before getting to open one program:

/home/arashiko/.wine/dosdevices/c:/Program Files/Microsoft Office/Office12

and then choosing it... any ideas?

Any way, thanks a lot, that was a great job!

---

### Post by jhoeijao on 2009-06-04
NightMKoder, I'm trying to install MSOffice 2007 again using your guide in another computer but after wine (1.1.16) installation I can't install MSOffice 2007. Please give some advice how to fix it, even my guide didn't work with it. Do that mean installing MSOffice through wine depends on your computer hardware?

---

### Post by NightMKoder on 2009-06-05
> **arashiko28 said:**
> =D>=D>=D>=D> You deserve a standing ovation!!! I have been after this since I changed completely to Ubuntu, not that I need it, I do everything with openoffice equally or even better, but I needed to be able to open a pptx without having it messed up or deconfigured.

It works like a charm, I only installed word, power point and excel, I don't need anything more, plus the tools, now. I use Ubuntu and I can't find the application to associate the programs. I have to go do like a dozen clicks before getting to open one program:

/home/arashiko/.wine/dosdevices/c:/Program Files/Microsoft Office/Office12

and then choosing it... any ideas?

Any way, thanks a lot, that was a great job!

Word doesn't appear in the wine menu? that's kind of weird. I put down a little guide on how to associate stuff on kubuntu, but I don't actually know how to do it on ubuntu. In terms of if you want a quick launcher, create a launcher that launches this command:

wine '/home/arashiko/.wine/dosdevices/c:/Program Files/Microsoft Office/Office12/WINWORD.exe'

I think you do it by right clicking on your desktop, but don't quote me on that.

> **jhoeijao said:**
> NightMKoder, I'm trying to install MSOffice 2007 again using your guide in another computer but after wine (1.1.16) installation I can't install MSOffice 2007. Please give some advice how to fix it, even my guide didn't work with it. Do that mean installing MSOffice through wine depends on your computer hardware?

No - it's not. You probably have something in your wine prefix that's messing with it. Try with a clean prefix or by bottling it.

---

### Post by MALeh on 2009-06-06
Hello,
When I'm installing MSO in custom setup (with excel, word, power point) at 1/4 % it stops and ask for a file location. Check the screenshot:

[[IMG]http://img189.imageshack.us/img189/5316/capturaecra.th.png[/IMG]](http://img189.imageshack.us/my.php?image=capturaecra.png)
" The configuration program can't locate Proofing.pt-pt/proof.en/proof.cab. Navigate to a valid instalation source, and press OK." 

Can someone give me a hand?

Thanks.

---

### Post by jhoeijao on 2009-06-06
> **MALeh said:**
> Hello,
When I'm installing MSO in custom setup (with excel, word, power point) at 1/4 % it stops and ask for a file location. Check the screenshot:

[[IMG]http://img189.imageshack.us/img189/5316/capturaecra.th.png[/IMG]]("http://img189.imageshack.us/my.php?image=capturaecra.png")
" The configuration program can't locate Proofing.pt-pt/proof.en/proof.cab. Navigate to a valid instalation source, and press OK." 

Can someone give me a hand?

Thanks.

Are you using CD in installing your MSOffice? If yes, try using a different CD or copy the MSoffice installer on your hard drive then install.

---

### Post by MALeh on 2009-06-06
> **jhoeijao said:**
> Are you using CD in installing your MSOffice? If yes, try using a different CD or copy the MSoffice installer on your hard drive then install.

I've tried with a different CD and now it don't ask me a folder, but give me a direct abort error. I've used this installation CD many times in my other windows machines. 

What can I do next?

---

### Post by jhoeijao on 2009-06-06
> **MALeh said:**
> I've tried with a different CD and now it don't ask me a folder, but give me a direct abort error. I've used this installation CD many times in my other windows machines. 

What can I do next?

It happened to me before and I based my answer through that experienced and that's the only solution I had. The TS can help you for sure.

---

### Post by MALeh on 2009-06-06
Well, don't know what happened, but it worked. Just uninstalled wine, and with the new CD, i succeeded.

Thanks.

EDIT: Ops, forgot to install solver, and analysis toolpak. Is there any way to repair de installation or i need to full reinstall?

---

### Post by jhoeijao on 2009-06-06
> **MALeh said:**
> Well, don't know what happened, but it worked. Just uninstalled wine, and with the new CD, i succeeded.

Thanks.

I'm glad you made it.

---

### Post by MALeh on 2009-06-07
Is there any other way to resolve the excel crash? When i run it it give me an error: Out of memory. Is there any way to solve it? 

Thanks

---

### Post by cjnkns on 2009-06-07
Thanks for the instructions they worked great!

On a side note: It looks like I need to purchase another license to use 2007 on Linux becuase it keeps bugging me to activate it :(

---

### Post by NightMKoder on 2009-06-07
> **MALeh said:**
> Is there any other way to resolve the excel crash? When i run it it give me an error: Out of memory. Is there any way to solve it? 

Thanks

Other than to start any other application and enter your name, no, I don't know of one.

---

### Post by Dimitriid on 2009-06-09
> **Duds55 said:**
> Thanks

Just one little thing - In order to get Access working first i installed vcrun2005 with winetricks as stated above however i was still getting errors:


[FONT="Courier New"]Could not find dependent assembly L"AceDAO"
import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Microsoft Office\\Office12\\MSACCESS.EXE") not found[/FONT]


I finally hit on this solution:

Amend the manifest file for access msaccess.exe.manifest found in [Your Wine Prefix]../Program Files/Microsoft Office/Office12 and remove the dependency reference to AceDAO, ie amend the file and remove the following lines:

<dependency>
<dependentAssembly>
<assemblyIdentity type="win32" name="AceDAO" version="12.0.0.0" language="*" processorArchitecture="X86">
</assemblyIdentity>
</dependentAssembly>
</dependency>

At least i can run it now - Office version is Office Enterprise

I am running into errors trying to start access:

```
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\MSACCESS.EXE" failed, status c0000142
misanthrope@misanthrope-desktop:~/.wine/drive_c/Program Files/Microsoft Office/O
```

Any ideas?

---

### Post by NightMKoder on 2009-06-09
You still need vcrun2005 and vcrun2005sp1

---

### Post by Dimitriid on 2009-06-09
> **NightMKoder said:**
> You still need vcrun2005 and vcrun2005sp1

I was missing sp1, still doing the same thing:

```
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\MSACCESS.EXE" failed, status c0000142
misanthrope@misanthrope-desktop:~/.wine/drive_c/Program Files/Microsoft Office/Office12
```

Does it matters if I tried to do vcrun2008? If so how do I undo that ( short of nuking everything and starting all over again )

---

### Post by Dimitriid on 2009-06-09
On second look, it looks like winetricks is not working for me:

```
Executing wine /home/misanthrope/.winetrickscache/vcrun2005/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"misanthrope" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"misanthrope" 0x145800 0x33f80c 0x145708 0x33f810 0x33f804 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
fixme:mscoree:LoadLibraryShim (0x7ee27a8c L"fusion.dll", (nil), (nil), 0x33f934): semi-stub
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
Install of vcrun2005 done
winetricks done.

```

---

### Post by jhoeijao on 2009-06-10
> **Dimitriid said:**
> On second look, it looks like winetricks is not working for me:

```
Executing wine /home/misanthrope/.winetrickscache/vcrun2005/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"misanthrope" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"misanthrope" 0x145800 0x33f80c 0x145708 0x33f810 0x33f804 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
fixme:mscoree:LoadLibraryShim (0x7ee27a8c L"fusion.dll", (nil), (nil), 0x33f934): semi-stub
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7ee678 0x7ee65c (nil) (nil)
Install of vcrun2005 done
winetricks done.

```
Just continue the steps on this guide the above codes does not mean that you failed to install winetricks.

---

### Post by Dimitriid on 2009-06-11
I did all the steps on the guide and access 2007 still couldn't work. I am virtualizing in the meantime but obviously wine would be much better.

I did try the most up to date version of wine after updating, im not sure if I should try an older version ( 1.18 or 1.19 for example ).

---

### Post by PerfectReign on 2009-06-14
Many thanks! This worked perfectly. I have now Office 2007 (my blue edition) running under Wine. (I never could get it to work under Crossover Office.)

[IMG]http://www.perfectreign.com/stuff/2009/20090614_wine_excel_2007.jpg[/IMG]

---

### Post by PerfectReign on 2009-06-18
Okay, I messed up.

I went ahead and tried my bestest to configure Outlook 2007 to work with my office Exchange (2003) server. It just wouldn't authenticate. 

Being frustrated - and having OOo 3.0 - I deleted wine, this install and everything.

I now realize  - after making a Word document with specific fields completely FUBAR by editing it in OOo - I need Word and possibly Excel at least. 

I went ahead and reinstalled wine, reinstalled Office 2007 and reinstalled the wine upgrade.

All is well, except I have no menu. 

I added icons for the main programs using the Edit menu in Gnome, but I can't get the icons and I'd really like them.

Any way to generate a Windows menu?

---

### Post by ws.venkateswaran on 2009-06-21
hi

thesaurus search doesnt give out any answers
i did run the code ./winetricks wsh56js and it ran successfully
here is the code that comes out

root@wsv-desktop:/home/wsv# ./winetricks wsh56js
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe](http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe)
--2009-06-21 17:19:51--  [http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe](http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe)
Resolving download.microsoft.com... 117.121.249.19
Connecting to download.microsoft.com|117.121.249.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 335912 (328K) [application/octet-stream]
Saving to: `Windows2000-KB917344-56-x86-enu.exe'

100%[======================================>] 3,35,912     180K/s   in 1.8s    

2009-06-21 17:19:53 (180 KB/s) - `Windows2000-KB917344-56-x86-enu.exe' saved [335912/335912]

Executing wine /root/.winetrickscache/Windows2000-KB917344-56-x86-enu.exe
fixme:advpack:set_ldids Need to support changing paths - default will be used
Install of wsh56js done
winetricks done.


i use wine 1.1.16 is that a problem, and i use ubuntu 8.10.
please help am new to ubuntu

thanks

---

### Post by jhoeijao on 2009-06-21
> **ws.venkateswaran said:**
> hi

thesaurus search doesnt give out any answers
i did run the code ./winetricks wsh56js and it ran successfully
here is the code that comes out

root@wsv-desktop:/home/wsv# ./winetricks wsh56js
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe](http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe)
--2009-06-21 17:19:51--  [http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe](http://download.microsoft.com/download/b/c/3/bc3a0c36-fada-497d-a3de-8b0139766f3b/Windows2000-KB917344-56-x86-enu.exe)
Resolving download.microsoft.com... 117.121.249.19
Connecting to download.microsoft.com|117.121.249.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 335912 (328K) [application/octet-stream]
Saving to: `Windows2000-KB917344-56-x86-enu.exe'

100%[======================================>] 3,35,912     180K/s   in 1.8s    

2009-06-21 17:19:53 (180 KB/s) - `Windows2000-KB917344-56-x86-enu.exe' saved [335912/335912]

Executing wine /root/.winetrickscache/Windows2000-KB917344-56-x86-enu.exe
fixme:advpack:set_ldids Need to support changing paths - default will be used
Install of wsh56js done
winetricks done.


i use wine 1.1.16 is that a problem, and i use ubuntu 8.10.
please help am new to ubuntu

thanks

Try "sh winetricks vcrun2005sp1" on your terminal.

---

### Post by ws.venkateswaran on 2009-06-21
hi 
this is what i get after the command


root@wsv-desktop:/home/wsv# sh winetricks vcrun2005sp1
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)
--2009-06-21 17:43:15--  [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)
Resolving download.microsoft.com... failed: Name or service not known.
wget: unable to resolve host address `download.microsoft.com'
Note: command 'wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)' returned status 1.  Aborting.

what to do

---

### Post by jhoeijao on 2009-06-21
> **ws.venkateswaran said:**
> hi 
this is what i get after the command


root@wsv-desktop:/home/wsv# sh winetricks vcrun2005sp1
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)
--2009-06-21 17:43:15--  [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)
Resolving download.microsoft.com... failed: Name or service not known.
wget: unable to resolve host address `download.microsoft.com'
Note: command 'wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)' returned status 1.  Aborting.

what to do

Click this link [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe) and save it. Copy or move this file in your .winetrickscache folder in your home folder Ctrl+H first to unhidden files and run "sh winetricks vcrun2005sp1" again.

---

### Post by ws.venkateswaran on 2009-06-21
still thesaurus doesnt work.. no results found..


this is what i got

root@wsv-desktop:/home/wsv# sh winetricks vcrun2005sp1
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)
--2009-06-21 18:15:11--  [http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe](http://download.microsoft.com/download/e/1/c/e1c773de-73ba-494a-a5ba-f24906ecf088/vcredist_x86.exe)
Resolving download.microsoft.com... 125.252.226.27
Connecting to download.microsoft.com|125.252.226.27|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2723264 (2.6M) [application/octet-stream]
Saving to: `vcredist_x86.exe'

100%[======================================>] 27,23,264    208K/s   in 14s     

2009-06-21 18:15:37 (191 KB/s) - `vcredist_x86.exe' saved [2723264/2723264]

Executing wine /root/.winetrickscache/vcrun2005sp1/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"root" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"root" 0x134bf8 0x33f80c 0x15aab8 0x33f810 0x33f804 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
fixme:mscoree:LoadLibraryShim (0x7ee2c30c L"fusion.dll", (nil), (nil), 0x33f934): semi-stub
Install of vcrun2005sp1 done
winetricks done.

help

---

### Post by jhoeijao on 2009-06-21
These are all the winetricks (sh     winetricks corefonts tahoma vcrun2005sp1 wsh56js) that I have installed on my Ubuntu 9.04 and my thesaurus works fine. Did you override usp10 and riched20 already?

---

### Post by NightMKoder on 2009-06-21
Hmmm didn't test it enough. I assumed right click and selecting synonyms would let the rest of it work, but apparently not. You need to set jscript to native in winecfg.

---

### Post by ws.venkateswaran on 2009-06-21
ya i over rided usp10 and riched20 before i ran these commands. what should i do now..

all winetricks you said  are installed correctly... is it my wine version problem.. i use 1.1.16 and ubuntu 8.10

---

### Post by jhoeijao on 2009-06-21
> **ws.venkateswaran said:**
> ya i over rided usp10 and riched20 before i ran these commands. what should i do now..

all winetricks you said  are installed correctly... is it my wine version problem.. i use 1.1.16 and ubuntu 8.10

The last solution I can give is update your wine using the synaptic package manager. Search for wine, right click on it and click mark for upgrade.

---

### Post by sandman3838 on 2009-06-27
Hello
I know that this thread is betting long but I had to ask....

I would very much like to do a remove and re-install of office2007.
I have some issues and the install here is much better that the one I used.

Would I just use WINE/UNINSTALL WINE SOFTWARE and select MS office 2007.
Or is there a cleaner way?

Thanks

---

### Post by jhoeijao on 2009-06-27
> **sandman3838 said:**
> Hello
I know that this thread is betting long but I had to ask....

I would very much like to do a remove and re-install of office2007.
I have some issues and the install here is much better that the one I used.

Would I just use WINE/UNINSTALL WINE SOFTWARE and select MS office 2007.
Or is there a cleaner way?

Thanks

**Delete         .Wine Folder**

Click Places>Home Folder press CTRL+H to unhide .wine folder and press delete or type 'rm -rf ~./wine' in your terminal window.

Note: Deleting wine folder means deleting all the programs installed through the use of wine.

---

### Post by markdjones82 on 2009-11-03
All,
  I got it installed, but I am getting the crashout "failed to open information store" after I tried configuring my profile.  I have tried deleting the profile settings for outlook to try and reconfigure.   

Any help on how I can have it recreate the profile or manually configure it?

---

### Post by f1r3br4nd on 2009-11-12
My winetricks seems to be failing at installing anything. It downloads okay, but during the extraction part of the install, it complains that...

"Extracting file failed. It is most likely caused by low memory (low disk space for swapping file) or corrupted Cabinet file."

I first witnessed it with dotnet11 and dotnet20, but so far none of the other packages I've tried with winetricks have worked. Clearly there's something weird about my configuration (though every partition has at least 500mb on it, so that should be enough to temporarily unpack the packages winetricks installs, shouldn't it?

Anyway, my question is, what should I do next in order to troubleshoot this problem?

---

### Post by eagle06 on 2009-11-23
thx for this excellent guide

---

### Post by arashiko28 on 2009-11-30
Thanks it worked like a charm, now, how do I remove the dead weight applications that after all I don't need. 
-Access
-One note
-Groove
-Info Path
-Outlook


I have office 2007 Enterprise, this applications installed but some don't work and I don't need them anyway.

---

### Post by anilisikalp on 2009-12-01
When I try to open a file which is named such as "my document.doc" by double click on desktop; word,excel or powerpoint try to gives an error such that " can't find file my.doc" and "can't find file document.doc". When I open file from word, everthing works normal. Have you ever seen a bug like that?

Thx..

---

### Post by Jonners59 on 2009-12-03
I have installed Ubuntu 9.10 with WINE version xxx.31 and MS O 2007

Installed OK, but:
I can not run Outlook. "Can not Open Outlook WIndow"  I did get it to open to the point where I was able to set up an account.  It then shut down and now has this message.

Publisher crashes if opening templates

OneNote crashes when shutting down and sends error reports

Can you help, please?

---

### Post by maekloev on 2009-12-03
> **anilisikalp said:**
> When I try to open a file which is named such as "my document.doc" by double click on desktop; word,excel or powerpoint try to gives an error such that " can't find file my.doc" and "can't find file document.doc". When I open file from word, everthing works normal. Have you ever seen a bug like that?

Thx..

yeah, i had the same problem. but check out least's [advice]("http://ubuntuforums.org/showpost.php?p=7202831&postcount=29") on page 3 of this thread.

works like a charm! thx for the hint, least. and many thanks to the thread-starter. great stuff ;)

---

### Post by bdws1975 on 2010-01-24
oh, thank you!!!!!!!!!!!!!!!!!  you've just made my life SO much easier.

Brett

---

### Post by Petridish on 2010-06-08
:confused: Alright, I'm about wine-guided to death, after a week of various flavors of failure, I'm begging for mercy and assistance.

The current situation: Ubuntu 8.04, Wine 1..1..24 on an Inspiron mini 10v.

I previously had the trial version of Office 2007 Home and Student successfully installed via wine 1.1.16, but I could not activate with my key (yes it's valid). I'd get to the activation wizard, click "convert" and ... crickets.

So I started over as best I could, not knowing how to undo what I'd done. Not properly, anyway.

Installed wine 1.1.24 and downloaded the software from the Install MS Office website. Moved the .exe into the system32 folder, because that's where Wine insists on looking for it. Extracts files, then asks for the product key, but won't let me type anything. 

For what it's worth, before I moved "up" to .24, I managed to get past the product key entry, only to have the install fail shortly thereafter.

Am I cursed?
The DLL overrides I have are (as they appear in the cfg window):
*gdiplus (native)
*msi (native, builtin)
*msiexec.exe (native, builtin)
*msxml3 (native, builtin)
*msxml4 (native, builtin)
riched20 (native)
usp10 (native)

I deleted .wine and tried the install again, to no avail.

Please help!
If you live in the Louisville area, I'd be willing to <strike>throw</strike> hand the machine over to you to just Make It Work.

---

### Post by ShubyDoo on 2010-06-12
Microsoft Office 2007 WORKS! (Thank you SOOOOOOOOO much)
One thing though, to launch a program I have to go to the directory and then find i.e: ONENOTE.EXE then launch it. Is there a way to get the "Program Files" menu in the main menu? Thanksss :)

---

