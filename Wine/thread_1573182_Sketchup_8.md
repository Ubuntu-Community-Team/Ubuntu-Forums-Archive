---
title: "Sketchup 8"
date: 2010-09-12
forum: Wine
---

### Post by KiwiTayl on 2010-09-12
I'm trying to run Sketchup 8. I have been able to download and install the program. It shows up in Applications > Wine > Programs > Google SketchUp 8. When I click Applications > Wine > Programs > Google SketchUp 8 > SketchUp, a "starting SketchUp" box opens in the bottom panel, but closes after a few seconds.

I'm using 
Ubuntu 9.10
Wine 1.3.2


Thanks!

---

### Post by drpjkurian on 2010-09-12
hi
Let me share that with you Wine does not work flawlessly for all windows application. I think for time being it is better to switch over to any native programmes in Linux.

---

### Post by drpjkurian on 2010-09-12
In Ubuntu software centre you browse through the programmes which are present in the Science & Technology -> Engineering

---

### Post by KiwiTayl on 2010-09-12
> **drpjkurian said:**
> hi
Let me share that with you Wine does not work flawlessly for all windows application. I think for time being it is better to switch over to any native programmes in Linux.

Indeed. I was hoping someone has overcome this problem.

Thanks for the reply.

---

### Post by pootle42 on 2010-09-13
I'm running sketchup8 on a standard lucid 32bit build on my laptop under wine with no special settings at all, and it is working pretty well, you can do basic drawing add textures etc. fine.

---

### Post by acidblue on 2010-09-15
Same here using SU 8 on 10.04 64bit in WIN XP mode.
So far no problems

---

### Post by mrbriggs on 2010-09-15
I was able to install Sketechup 8.x on a system running Ubuntu 9.10, Wine 1.2

On the first run I received a crash and the error after choosing a template of:
"unable to initialize OpenGL"

I followed the directions at WineHQ for SketchUp 8.x 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21290](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21290)

This basically says that after the first crash to edit the registry (wine regedit) and change the key to:
HKEY_USERS/S-1-5-4/Software/Google/SketchUp8/GLConfig/Display HW_OK = 1

SketchUp now loads and runs without errors.

---

### Post by KiwiTayl on 2010-09-19
> **acidblue said:**
> Same here using SU 8 on 10.04 64bit in WIN XP mode.
So far no problems

I found that wine was in Windows 7 mode. I changed it to Windows XP and SU 8 openned. I get an error message:

[SketchUp was unable to initialize OpenGL! Please make sure you have installed the correct drivers for your graphics card. Error: ChoosePixelFormat failed]

Any ideas?

Thanks.

---

### Post by larsbjo on 2010-09-20
Just read the comment from "mrbriggs" (above your post) and follow the directions. It should work.

---

### Post by Robert.Thompson on 2010-09-20
Hi:

I am using Ubuntu 10.04 LTS & Wine 1.1.42.

I installed SketchUp 8 and did the reqiured: HKEY_USERS/S-1-5-4/Software/Google/SketchUp8/GLConfig/Display HW_OK = 1

SketchUp started but then soon failed.

I went to Configure Wine --> Applications and switched **from** Windows XP **to** Windows 7  and it works fine now.

Go figure...

Rob.

---

### Post by mark_melvin on 2010-09-28
I've tried everything listed here and SU 8 will not start.  I am using Ubuntu 10.04 (32 bit), the proprietary NVidia driver, manually edited registry, and Wine 1.2.

Has anyone got this to work on Wine 1.2?

---

### Post by acidblue on 2010-09-29
Funny, SU 8 now will no longer work.
It worked fine when I first installed it.

The only thing that has changed was an update to 2.6.32-24-generic via normal update process.

I don't get any error messages, just nothing.
I get the little timer spinner that I usually get when loading programs.
Then it stops and nothing, no window, no error messages.

Kinda stumped on this one, I checked the registry and HW_OK does have a value of 1 (0x00000001).

I did a re-install, didn't help.

This is on 10.04 64 bit.

---

### Post by mark_melvin on 2010-09-29
Hmm...I recently upgraded my kernel as well I believe (but I am running 32 bit).  I'll check the version when I get home.

---

### Post by mark_melvin on 2010-09-29
I'm also running 2.6.32-24-generic.  Interesting...

---

### Post by acidblue on 2010-09-30
Just a guess but I bet there's something about that kernel that broke SU 8.

---

### Post by jmacwill on 2010-10-02
I just tried to install and get sketchup 8 running - I had no issues installing - but I tried to run under windows 7 or windows xp emulation and NO response, just the spinning circles - then nothing.  It does not even get to the point where it sets the registry so I can change that error I was hoping to fix :)

I am running 10.04 and the latest Wine.

Anybody else have any luck?

---

### Post by mark_melvin on 2010-10-03
Nope. I get the same thing as you.  I manually created all the registry entries and it didn't help.

M.

---

### Post by jmacwill on 2010-10-10
Hi everybody

I just upgraded to 10.10 and wine 1.3.4 in an attempt to get Sketchup 8 working.  I was having the same issues with 10.04 and wine 1.2 - the machine would look like it was working - but then just stop and no way was sketchup going to run.

Well, upgrading to the latest version of ubuntu and wine did not remedy that situation.

It seems to crash before it even gets a chance to write to the registry - as I cannot even make the required corrections the registry as that line is not there yet to fix.

Has anybody had any sucess getting this to run?

Thanks

Jonathan

---

### Post by okmat on 2010-10-12
I got it working.

First you have to edit the registry:
```
wine regedit
``` 

go to HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display, and change HW_OK to 1

(This info was taken from [http://wiki.winehq.org/GoogleSketchup]("http://wiki.winehq.org/GoogleSketchup"))

Now, right click on the sketchup's launcher icon (on the desktop). Copy the "command" field and paste it in a terminal. Everything works from there, even the welcome screen, why? I dunno

I'm running maverick (kernel 2.6.35-22-generic) and sketchup 8

hope this works for someone else too

---

### Post by mark_melvin on 2010-10-13
That didn't work for me, but I eventually got it working.  I have no idea how - but here is what I did:

1) Screwed around with winetricks installing various VC runtimes (no luck) eventually hosing my wine installation
2) Uninstall Wine
3) Install wine 1.3 (sudo apt-get install wine1.3) - Sketchup still did not start
4) Tried many times to uninstall Sketchup, all of which failed
5) Ultimately deleted all registry keys, all Google folders, and all cached .msi files in the windows/Installer folder
6) Changed my default OS to Windows 7 in the wine config
7) Removed any existing overrides in the Libraries part of the wine configuration
8) Ran the Sketchup installer again and still could not uninstall it, so I clicked "Repair"
9) Now Sketchup works fine

I'm at a loss to explain which step was the magical one.

---

### Post by jeffreyldavidson on 2010-10-20
I made the change running to Google Sketcup using regedit in Wine and now it works fine. I download sketches from woodworking sites and it works perfect.

---

### Post by rogprov on 2010-10-21
I just downloaded/ran the install then changed the regedit entry as shown and I also changed Wine permissions for this app. to allow read/write/execute. Wine is 1.2.1

... bingo working!

 It originally ended up on the desktop but a moved it to it's own folder in home and added it to applications/graphics

---

### Post by movinginthedark on 2010-11-08
> **mark_melvin said:**
> That didn't work for me, but I eventually got it working.  I have no idea how - but here is what I did:

1) Screwed around with winetricks installing various VC runtimes (no luck) eventually hosing my wine installation
2) Uninstall Wine
3) Install wine 1.3 (sudo apt-get install wine1.3) - Sketchup still did not start
4) Tried many times to uninstall Sketchup, all of which failed
5) Ultimately deleted all registry keys, all Google folders, and all cached .msi files in the windows/Installer folder
6) Changed my default OS to Windows 7 in the wine config
7) Removed any existing overrides in the Libraries part of the wine configuration
8) Ran the Sketchup installer again and still could not uninstall it, so I clicked "Repair"
9) Now Sketchup works fine

I'm at a loss to explain which step was the magical one.


I'm running Ubuntu 10.04, and Wine 1.3.6 in XP Mode.

What I did was:
1: Install Wine (obviously)
2: Install Sketchup - It asks for Net Framework 2.0 to be installed - so you follow that through, mine just hung, but I left it for about 6 hours and then just rebooted out of boredom.
3: Sketchup still didn't appear - so I ran the installer again - this time I got desktop icons, but it wouldn't load. I would get the spinning circles, start bar icon, but then would cut out without any Sketchup slash screen.
4: Ran the installer a THIRD time - this time selecting repair install.
5: Sketchup gets to splash screen (from what I can tell works fine although haven't tested further as my license information is on my PC)

I'll post more results as and when I get the chance :)

Hope this helps someone.

**EDIT:** After starting for the first time - I received the OpenGL error, as previously stated, open terminal, type "regedit" like you would in the Windows run command and navigate to:

HKEY_USERS/S-1-5-4/Software/Google/SketchUp8/GLConfig/Display HW_OK = 1

By default, the value of this entry is set to 0 - just change to 1 and away you go :D

---

### Post by AlexDS on 2010-11-30
do you have sketchup 8 free or pro ?

---

### Post by AlexDS on 2010-11-30
> **jeffreyldavidson said:**
> I made the change running to Google Sketcup using regedit in Wine and now it works fine. I download sketches from woodworking sites and it works perfect.

jeffreyldavidson, do you have the free or the pro version of sketchup?

---

### Post by AlwaysLearning on 2011-01-22
I just installed SketchUp 8 and didn't have any problems at all - not even the crash on first run - which actually disappointed me because I had a .reg file ready to go. Could it be that people already have something installed/configured under Wine that's causing problems with SketchUp?

Standard practice for me is to install Windows apps in their own wineprefix. It causes a little more disk use, but I'm assured that apps won't clobber each other plus, when I'm done trying out something, I can just blow away its directory and not worry about my other Windows apps.

```
:~/Install/Google SketchUp$ uname -srvo
Linux 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 GNU/Linux

:~/Install/Google SketchUp$ wine --version
wine-1.2

:~/Install/Google SketchUp$ winetricks --version
Winetricks version 20101106.  (C) 2007-2010 Dan Kegel et al.  LGPL.
```

Here was my install script:
```
#!/bin/sh

DOWNLOAD_URL=http://dl.google.com/sketchup/GoogleSketchUpWEN.exe
SETUP_FILE=GoogleSketchUpWEN.exe

wget --continue --timeout=30 --tries=10 "$DOWNLOAD_URL" --output-document="$SETUP_FILE"
export WINEPREFIX="$HOME/.wine-sketchup"
winetricks dotnet20
wine ./$SETUP_FILE
```

When finished I ran SketchUp from the desktop icon that the installer created. No problems at all.

---

### Post by AlexDS on 2011-01-22
> **AlwaysLearning said:**
> I just installed SketchUp 8 and didn't have any problems at all - not even the crash on first run - which actually disappointed me because I had a .reg file ready to go. Could it be that people already have something installed/configured under Wine that's causing problems with SketchUp?

Standard practice for me is to install Windows apps in their own wineprefix. It causes a little more disk use, but I'm assured that apps won't clobber each other plus, when I'm done trying out something, I can just blow away its directory and not worry about my other Windows apps.

```
:~/Install/Google SketchUp$ uname -srvo
Linux 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 GNU/Linux

:~/Install/Google SketchUp$ wine --version
wine-1.2

:~/Install/Google SketchUp$ winetricks --version
Winetricks version 20101106.  (C) 2007-2010 Dan Kegel et al.  LGPL.
```Here was my install script:
```
#!/bin/sh

DOWNLOAD_URL=http://dl.google.com/sketchup/GoogleSketchUpWEN.exe
SETUP_FILE=GoogleSketchUpWEN.exe

wget --continue --timeout=30 --tries=10 &quot;$DOWNLOAD_URL&quot; --output-document=&quot;$SETUP_FILE&quot;
export WINEPREFIX=&quot;$HOME/.wine-sketchup&quot;
winetricks dotnet20
wine ./$SETUP_FILE
```When finished I ran SketchUp from the desktop icon that the installer created. No problems at all.

What about Layout? it comes with the Pro version.  Is it working for you  ? cause for me after launching is crashing at the beginning, don't know  why :(

---

### Post by AlexDS on 2011-01-22
What about Layout? it comes with the Pro version.  Is it working for you   ? cause for me after launching is crashing at the beginning, don't  know  why :sad:

---

### Post by Ric_NYC on 2011-01-28
Hi, I have Sketchup 8 installed and it works perfectly.


This is what I have:

[B]Wine 1.3
[/B][IMG]http://img440.imageshack.us/img440/8573/screenshot4of.png[/IMG]

[B]Windows set as "XP"
[/B][IMG]http://img121.imageshack.us/img121/743/screenshot3oi.png[/IMG]

[B]Sketchp 8
[/B]
[IMG]http://img199.imageshack.us/img199/4056/screenshot5bc.png[/IMG]




**[COLOR="Red"]bug 14045[/COLOR]**: If you get the error "SketchUp was unable to initialize OpenGL!, run regedit, open [HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display], and change "HW_OK" to 1.

[http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)

---

### Post by Guyllfyre on 2011-02-18
> **Ric_NYC said:**
> If you get the error "SketchUp was unable to initialize OpenGL!, run regedit, open [HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConfig\Display], and change "HW_OK" to 1.

I finally got as far as getting the splash screen, select a template, and click start using.
I get the error but I do not have this registry key.

Any ideas?

I'm running 10.04 LTS x64 on a box with on-board Intel graphics of some sort.

---

### Post by AlexDS on 2011-02-24
Does anybody have Sketchup 8 or 7 PRO working in Ubuntu ?

---

### Post by Guyllfyre on 2011-02-25
> **Guyllfyre said:**
> I finally got as far as getting the splash screen, select a template, and click start using.
I get the error but I do not have this registry key.

Any ideas?

I'm running 10.04 LTS x64 on a box with on-board Intel graphics of some sort.

OK, so I installed an nVidia card to see if it would make a difference.
I still do not get the registry key everyone is saying needs to be changed after I've installed Sketchup.

---

### Post by Guyllfyre on 2011-02-25
OK, now this is odd.
By running it from the desktop shortcut it creates, I get the error and do not get registry keys.

So, I ran it from the commandline as root and lo and behold, it loads and runs just fine, creates all the registry entries, and doesn't pop up with any errors.

I haven't tried doing anything with it yet but the desktop icon still doesn't work but running the executable from the commandline does.

Strange.

---

### Post by orsula on 2011-03-16
For me it was the Wine version. Wine 1.2.2 that came with Ubuntu 10.10 would throw a runtime error and completely hang at start up as attached below. I didn't even get to the OpenGL issues. I finally went to Synaptic and installed wine 1.3 as described in above post. Reinstalled SketchUp 8 (only allowed to "repair" during installation). After that SketchUp started just fine from either icon or command line.

System:
[LIST]
[*]Dell Latitude D630
[*]Ubuntu 10.10
[*]kernel 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux
[*]Nvidia accelerated graphics driver (from System > Administration > additional drivers) for Quadro NVS 135M (driver version 260.19.06)
[/LIST]

Hope this helps someone O:)

---

### Post by MasterOfTheHat on 2011-04-17
> **orsula said:**
> For me it was the Wine version. Wine 1.2.2 that came with Ubuntu 10.10 would throw a runtime error and completely hang at start up as attached below. I didn't even get to the OpenGL issues. I finally went to Synaptic and installed wine 1.3 as described in above post. Reinstalled SketchUp 8 (only allowed to "repair" during installation). After that SketchUp started just fine from either icon or command line.

System:
[LIST]
[*]Dell Latitude D630
[*]Ubuntu 10.10
[*]kernel 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux
[*]Nvidia accelerated graphics driver (from System > Administration > additional drivers) for Quadro NVS 135M (driver version 260.19.06)
[/LIST]

Hope this helps someone O:)

Agreed. The version of Wine that comes from apt-get/Ubuntu Software Center is usually several versions behind. Follow the directions at [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) to grab the latest stable version, then follow the registry changes given several places in this thread, and see if Sketchup runs for you.

[HKEY_CURRENT_USER\Software\Google\SketchUp8\GLConf ig\Display], and change "HW_OK" to 1

---

### Post by Moonwen on 2011-04-24
I want to thank everybody in this thread for the help given to solve this problem.
For this reason I want to tell what happened to me and what I did.
I followed all the tips regarding the register but I coudlnd get it work.
So, following [AlwaysLearning]("http://ubuntuforums.org/member.php?u=256920") advises I installed it in a new prefix, but since I'm not good at all at codes I used Q4wine, which you can download from the Ubuntu Software Center.
Done that , at least I could go to the introduction page and from there select the template and start a new page, but I could only see the frame of the window, with the commands (working), but the page was unexisting, I had my desktop image at its place or a mix of the last folders that I opened, a mess.
So I tried the last thing, to switch to the 173 drivers instead the current that i was using, didn't try the 96 because the last time I did that i was send to tty1 and had to uninstall the drivers from there.
Anyway, when I opened it everything was working!
Now I haven't tried to use it in all it's features but it seems to work good.

---

### Post by Moonwen on 2011-04-24
nt

---

### Post by Morten ML on 2011-05-02
Hi all

Anyabody else have a problem with exporting as *.dae files? I cannot get it to actually create the *.dae file. I am using merkat running wine 1.2.2 and sketchup ver 8. I found a bugreport here [http://wine.1045685.n5.nabble.com/Bug-22247-New-Sketchup-cannot-export-collada-or-google-earth-files-td1476212.html]("http://wine.1045685.n5.nabble.com/Bug-22247-New-Sketchup-cannot-export-collada-or-google-earth-files-td1476212.html") and direct url to the attached fix: [http://bugs2.winehq.org/attachment.cgi?id=27172]("http://bugs2.winehq.org/attachment.cgi?id=27172").
But now my problem is what to do? If the fix can be useful what should i do to use it? And if the fix cannot be used is there any other way of exporting a file from sketchup to blender? 
Best regards the linux noob.

---

### Post by acidblue on 2011-06-12
> **Morten ML said:**
> Hi all

Anyabody else have a problem with exporting as *.dae files? I cannot get it to actually create the *.dae file. I am using merkat running wine 1.2.2 and sketchup ver 8. I found a bugreport here [http://wine.1045685.n5.nabble.com/Bug-22247-New-Sketchup-cannot-export-collada-or-google-earth-files-td1476212.html]("http://wine.1045685.n5.nabble.com/Bug-22247-New-Sketchup-cannot-export-collada-or-google-earth-files-td1476212.html") and direct url to the attached fix: [http://bugs2.winehq.org/attachment.cgi?id=27172]("http://bugs2.winehq.org/attachment.cgi?id=27172").
But now my problem is what to do? If the fix can be useful what should i do to use it? And if the fix cannot be used is there any other way of exporting a file from sketchup to blender? 
Best regards the linux noob.

I am also having this problem, the progress bar flashes for a second but the file is never saved.
Also exporting a 2d image just gives me a blank white page, am I suppose to add a light source or something?

I installed Kerkythea and the SUKT script and that seems to work fine, but it doesn't transfer any of my dimensions or rule guides
which is what I need.
Anybody got a clue?

EDIT:
Updating Wine to 1.3 seems to help somewhat.
SketchUp will export a .dae file when exporting a 3D image, however Blender does not import the file, it says "import was successful" But it does not load the file, I am faced with a blank view in Blender.

Also exporting a 2d image still doesn't work, still saves a blank image.

---

### Post by Catlike on 2011-07-15
> **mrbriggs said:**
> I was able to install Sketechup 8.x on a system running Ubuntu 9.10, Wine 1.2

...
I followed the directions at WineHQ for SketchUp 8.x 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21290](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21290)

This basically says that after the first crash to edit the registry (wine regedit) and change the key to:
HKEY_USERS/S-1-5-4/Software/Google/SketchUp8/GLConfig/Display HW_OK = 1

SketchUp now loads and runs without errors.

How does one "edit the registry"? I cannot find a registry.

---

### Post by layr on 2011-08-01
> **Catlike said:**
> How does one "edit the registry"? I cannot find a registry.

Open up terminal -> type "wine regedit" ; without the quotation marks obviously.
...aaand onto my problem. I passed the OpenGL error with the registry editing and after switching graphic drivers got the Sketchup running for minute or so. Program crashes with "Segmentation fault" printed in terminal.
Sketchup 7 runs a bit longer, but crashes in the same manner.

HP Compaq 8510w
Ubuntu 10.10
Wine 1.3.25 (tested 1.2.3 too)
Nvidia driver 275.21 (also tried 270.41.06, 270.41.19, 160.19.44)

terminal output:
```
laur@laur-HP-Compaq-8510w:~$ WINEPREFIX="$HOME/.wine-google8" wine '/home/laur/.wine-google8/drive_c/Program Files/Google/Google SketchUp 8/SketchUp.exe' 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 0

Intrinsic Alchemy v3.3 Beta-0702 (Dynamic/Release)
Built by <unknown> on Fri Jul 2 00:00:00 2010

fixme:shdocvw:PersistStreamInit_InitNew (0x151988)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f030:3; TargetFrameName 0x32f040:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Mon, 01-Aug-2011 14:53:57 GMT; Path=/support; HttpOnly")
fixme:wininet:set_cookie httponly not handled (L"HttpOnly")
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x41de85c, overlapped 0x41de840): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32c11c,0x00000000), stub!
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x151a38)->((null) 1 0x32cd38 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x4b531d0)->()
fixme:shdocvw:ClientSite_GetContainer (0x151a38)->(0x32cd08)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x4b531d0)->(0x32a030)
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x151a38)
fixme:shdocvw:ClientSite_GetContainer (0x151a38)->(0x32f288)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x549f098)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x549fc78)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x54a05d8)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x54a0f60)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x54a18e8)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x54a2250)->()
fixme:mshtml:nsChannel_SetResponseHeader (0x4b531d0)->("content-type" "text/html; charset=UTF-8" 1)
fixme:mshtml:nsChannel_SetResponseHeader (0x4b531d0)->("content-style-type" "text/css" 1)
fixme:mshtml:nsChannel_SetResponseHeader (0x4b531d0)->("content-script-type" "text/javascript" 1)
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x549ec88)->(0x32ec94 0x32ec6c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x549f758)->(0x32ec94 0x32ec6c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x54a0148)->(0x32ec94 0x32ec6c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x54a0aa8)->(0x32ec94 0x32ec6c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x54a1438)->(0x32ec94 0x32ec6c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x54a1db8)->(0x32ec94 0x32ec6c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x54a2720)->(0x32ec94 0x32ec6c 0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x549fc78)->(0x32c7f8)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x549eb10)->(0x32c8f4)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x54a0f60)->(0x32c7f8)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x549f098)->(0x32c7f8)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x54a05d8)->(0x32c7f8)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x54a18e8)->(0x32c7f8)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x54a2250)->(0x32c7f8)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x5626c08)->()
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:mshtml:nsURI_GetAsciiHost Use Uri_PUNYCODE_IDN_HOST flag
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5629108)->(0x32ec94 0x32ec6c 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x5626c08)->(0x32c7f8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:DocObjectService_FireDocumentComplete 0x4a6d240 0x4a6c780 0
fixme:mshtml:nsChannel_IsNoCacheResponse (0x4b531d0)->(0x32f190)
fixme:mshtml:HTMLDocument_get_nameProp (0x15c070)->(0x32f064)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32efa0:3; TargetFrameName 0x32efb0:8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x151a38)->(0x32f1e8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x151a38)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:shdocvw:DocObjectService_FireDocumentComplete 0x4a6d240 0x4a6c780 0
fixme:shdocvw:WebBrowser_Stop (0x151988)
fixme:shdocvw:OleObject_Close (0x151988)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x151988)
fixme:shdocvw:ControlSite_OnFocus (0x151a38)->(0)
fixme:shdocvw:InPlaceSite_OnInPlaceDeactivateEx fNoRedraw (1) ignored
fixme:mshtml:HlinkTarget_SetBrowseContext (0x15c070)->((nil))
fixme:shdocvw:OleObject_Close (0x151988)->(1)
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
(eval):3120: warning: parenthesize argument(s) for future version

(eval):3143: warning: parenthesize argument(s) for future version

fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 0
fixme:wininet:InternetCheckConnectionW 
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetCheckConnectionW 
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
Segmentation fault
```
Don't know whether it helps, but crash occurs mostly when selecting the push/pull tool or trying to rotate the object.
Opened a thread also in wineHQ forums; so far no luck.

---

### Post by harrisheatair on 2012-01-07
I am using wine 1.3.35 and when I go to wine regedit I can't find what is in red HKEY_USERS/S-1-5-4/Software/[COLOR=Red]Google/SketchUp8/GLConfig/Display[/COLOR] or HKEY_CURRENT_USER\Software\[COLOR=Red]Google\SketchUp8\GLConf ig\Display [COLOR=Black]Can someone please help
I don't know if it is the version I have or if I'm doing something wrong.  I have tried everything in all the posts and GS8 acts like it is going to start then does nothing.  I am using Ubuntu 10.4.  Thank you in advance.
[/COLOR][/COLOR][IMG]file:///home/gary/Desktop/Screenshot-1.png[/IMG][IMG]file:///home/gary/Desktop/Screenshot-1.png[/IMG]

---

### Post by neorg on 2012-01-31
Forget wine.
Run a windows OS in VirtualBox [https://www.virtualbox.org/](https://www.virtualbox.org/) and than install Sketchup on the WinOS


Install Virtualbox (apt-get install virtualbox)
Start Virtualbox
Install a Windows OS (Vista, Win7 whatever you got)
Start the Virtual OS
Install Sketchup on the virtual OS

Success guaranteed

---

### Post by Abe41 on 2012-07-05
This is the error message from Sketchup pro 8 installer for Ubuntu 12.04  64 bit is anyone not effectively looking to resolve these issues.  Sketchup is really easy to use and less of a learning curve compared to  Blender 3d. Is it possible to get this operational on a 64 bit system or  is 32 bit just going to be the norm for Ubuntu?

System Info:

System information report, generated by Sysinfo: 7/5/2012 12:37:40 AM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 12.04 (precise) release.
    GNOME: unknown (unknown)
    Kernel version: 3.2.0-26-generic (#41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012)
    GCC: 4.6 (x86_64-linux-gnu)
    Xorg: 1.11.3 (07 May 2012  11:43:21PM) (07 May 2012  11:43:21PM)
    Uptime: 0 days 13 h 58 min

CPU INFORMATION
    AuthenticAMD, AMD Athlon(tm) II X2 255 Processor
    Number of CPUs: 2
    CPU clock currently at 3100.000 MHz with 1024 KB cache
    Numbering: family(16) model(6) stepping(3)
    Bogomips: 6200.06
    Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save

MEMORY INFORMATION
    Total memory: 3010 MB
    Total swap: 3069 MB

STORAGE INFORMATION
    SCSI device -  scsi1
        Vendor:  ATA      
        Model:  WDC WD15EARS-00Z 
    SCSI device -  scsi5
        Vendor:  SONY     
        Model:  CDRW/DVD CRX330E 
    SCSI device -  scsi7
        Vendor:  ZTEMT    
        Model:  Mass storage     

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Advanced Micro Devices [AMD] Family 10h Processor Link Control
        Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge
    PCI bridge(s)
        Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
        Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
        Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
        Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
        Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    ISA bridge
        Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
        Subsystem: Biostar Microtech Int'l Corp Device 3700
    IDE interface
        Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Biostar Microtech Int'l Corp Device 3700

GRAPHIC CARD
    VGA controller
        NVIDIA Corporation GF119 [GeForce GT 520] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Device 1529

SOUND CARD
    Multimedia controller
        NVIDIA Corporation HDMI Audio stub (rev a1)
        Subsystem: eVga.com. Corp. Device 1529

NETWORK
    Ethernet controller
        Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Biostar Microtech Int'l Corp Device 2308

NVIDIA GRAPHIC CARD INFORMATION
    Model name: GeForce GT 520
    Card Type: PCIe 16x
    Video RAM: 2048 MB
    GPU Frequency: 270 MHz
    Driver version: NVIDIA UNIX x86_64 Kernel Module  302.17  Tue Jun 12 16:03:22 PDT 2012

Installer Error log:

The following properties have been set: 
Property: [AdminUser] = true {boolean} 
Property: [ProcessorArchitecture] = AMD64 {string} 
Property: [VersionNT] = 6.0.2 {version} 
Running checks for package 'Microsoft Windows', phase BuildList 
The following properties have been set for package 'Microsoft Windows': 
Running checks for command 'SketchUpPrerequisites\NULL' 
Result of running operator 'VersionGreaterThanOrEqualTo' on property 'VersionNT' and value '5.1.2': true 
Result of checks for command 'SketchUpPrerequisites\NULL' is 'Bypass' 
'Microsoft Windows' RunCheck result: No Install Needed 
Running checks for package '.NET Framework 2.0', phase BuildList 
Running external check with command line "C:\users\abe\Temp\VSD1420.tmp\SketchUpDotNetFx\dotnetchk.exe" 
Process exited with code 0 
Setting value '0 {int}' for property 'DotNetInstalled' 
Reading value 'Version' of registry key 'HKLM\Software\Microsoft\Internet Explorer' 
Unable to read registry value 
Not setting value for property 'IEVersion' 
The following properties have been set for package '.NET Framework 2.0': 
Property: [DotNetInstalled] = 0 {int} 
Running checks for command 'SketchUpDotNetFx\dotnetfx.exe' 
Result of running operator 'ValueNotEqualTo' on property 'DotNetInstalled' and value '0': false 
Result of running operator 'ValueNotEqualTo' on property 'ProcessorArchitecture' and value 'Intel': true 
Result of checks for command 'SketchUpDotNetFx\dotnetfx.exe' is 'Bypass' 
Running checks for command 'SketchUpDotNetFx\NetFx64.exe' 
Result of running operator 'ValueNotEqualTo' on property 'DotNetInstalled' and value '0': false 
Result of running operator 'ValueNotEqualTo' on property 'ProcessorArchitecture' and value 'AMD64': false 
Result of running operator 'ValueEqualTo' on property 'AdminUser' and value 'false': false 
Skipping FailIf because Property 'Version9X' was not defined 
Result of running operator 'VersionLessThan' on property 'VersionNT' and value '5.0.3': false 
Result of running operator 'ValueNotExists' on property 'IEVersion': true 
Result of checks for command 'SketchUpDotNetFx\NetFx64.exe' is 'Fail' 
'.NET Framework 2.0' RunCheck result: Fail 
A prerequisite failed for Package ".NET Framework 2.0" 
Package failed with message "Installation of .NET Framework 2.0 requires Internet Explorer 5.01 or greater."

This is the error message from Sketchup pro 8 installer for Ubuntu 12.04 64 bit is anyone not effectively looking to resolve these issues. Sketchup is really easy to use and less of a learning curve compared to Blender 3d. Is it possible to get this operational on a 64 bit system or is 32 bit just going to be the norm for Ubuntu?

---

### Post by BFG on 2013-04-04
Very useful thread!!

I just had problems with Sketchup 8 Pro installing on Crossover Office with the "unable to initialize OpenGL" error.   12.10 64 bit with an AMD FIREPRO™ V4900 PRO card.
Editing the registry worked - sharing in case it's useful.

In crossover it's a bit easier than wine. From the Crossover GUI, click the bottle on the left, choose the "bottle" tab from the right and click "Run command".
Enter regedit

Navigate to the key:

> **mrbriggs said:**
> 

This basically says that after the first crash to edit the registry (wine regedit) and change the key to:
HKEY_USERS/S-1-5-4/Software/Google/SketchUp8/GLConfig/Display HW_OK = 1


Change from 0 to 1 and exit.  Then sketchup ran just fine. :)

---

