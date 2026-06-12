---
title: "Need for speed world Beta"
date: 2010-06-09
forum: Wine
---

### Post by SeeonX on 2010-06-09
I'm in the Need for Speed World beta, I got the game client to install but when I click the GameLauncher.exe file my mouse turns into the loading icon for about a minute then nothing. 

Trouble shooting steps so far:
Permissions: I changed everything in the folder to Read and Write for Owner and my user name.

Under Wine configuration: I tried Windows version XP and 7. Tried to toggle on and off "Allow Window Manager to control the window and decorate the window"

Kept Direct3D to Hardware and allow pixel shader on.


I have Ubuntu 64bit with latest drivers for 9800GTX, Intel quad core and 4 gigs of ram. 

Any advice would be great! :D I tried searching and looking on google couldn't find anything related to wine. :(

---

### Post by cogadh on 2010-06-09
Giving us Wine's terminal output might be helpful in diagnosing the problem.

---

### Post by SeeonX on 2010-06-09
How do I do that again? I'm still new? I googled it really quick but didn't find anything other than some steps for World of warcraft. lol

---

### Post by cogadh on 2010-06-09
Open a terminal, change directory to the game's installation directory, then "wine" the executable:
```
cd ~/.wine/drive_c/<game installation directory>
wine <game executable>.exe
```
I don't know the actual game installation directory or game executable name, so you'll have to figure that part out and modify the commands as necessary. Wine's error output will appear in the terminal. Copy the output and paste it in a post here using the forum "code" tags (they work just like the "quote" tags and will preserve the output's format). If the output is too lengthy, copy it to a text file and attach it to the post instead or use something like Pastebin to link to it.

---

### Post by asdfoo on 2010-06-10
also make sure you're using the most recent version of wine, which is 1.2-rc2

at a terminal type: wine --version

---

### Post by SeeonX on 2010-06-10
wine: Install the Windows version of Mono to run .NET executables

That is the error it gives.

wine-1.2-rc2-111-g9aa9a12

Is the version of wine I am using! :) Thank you very much!

---

### Post by cogadh on 2010-06-10
Well, that was easy, it actually told you what to do. Easiest way to install Mono or .NET is using [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by SeeonX on 2010-06-12
Thanks again, now when I try to run the program a message window titled Error pops up saying, "The executable is corrupted please reinstall the application again." Only option is an OK button. <,< 

I made sure all files had full permissions after install, Wine is currently in Vista mode, and I'm unable to think of why it's still not working. I'm trying to do the terminal command to start the program but I'm having issue getting to it again.  

**EDIT:** Can you also tell me how to use the CD command to get to /home/seeonx/.wine/dosdevices/c:/Program Files/Electronic Arts/Need For Speed World so I can run the program? It's not getting past .wine/ :(...?

---

### Post by cogadh on 2010-06-12
```
cd ~/.wine/drive_c/Program\ Files/Electronic\ Arts/Need\ For\ Speed\ World
```

---

### Post by SeeonX on 2010-06-13
I hope this is as clear to you as the other error.. o.o 

```

fixme:advapi:RegisterTraceGuidsW (0x79fd471e, 0x111390, {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4}, 9, 0x7a390368, (null), (null), 0x7a38d250,)
fixme:sync:CreateMemoryResourceNotification (0) stub
err:ole:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
seeonx@seeonx-desktop:~/.wine/drive_c/Program Files/Electronic Arts/Need For Speed World$ fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented

```

---

### Post by cogadh on 2010-06-14
Looks like something from .NET is either missing or doesn't work in Wine. Which version(s) of .NET did you try installing in Wine, or did you just install Mono?

EDIT - On second thought, a better question might be what version of .NET does the game require? AFAIK, versions 1.1 and 2.0 will install and work (mostly) but 3.0 and 3.5 do have problems with Wine (I'm pretty sure 3.5 won't even install yet).

---

### Post by SeeonX on 2010-06-14
I have Framework 2.0 installed - 2.0.50727 not sure which version the game requires. :/

EDIT: Do you recommend that I try installing 3.0 or mono? Not sure what Mono is?

EDIT2: I tried to install 3.0 but I get this: 
```

seeonx@seeonx-desktop:~$ sh winetricks
Xlib:  extension "RANDR" missing on display ":0.0".
------------------------------------------------------
Instaling .net 3.0 runtime.  Can take 15-30 minutes.  See http://wiki.winehq.org/MicrosoftDotNet for tips.
------------------------------------------------------
Xlib:  extension "RANDR" missing on display ":0.0".
prerequisite dotnet20 already installed, skipping
Executing wine /home/seeonx/.winetrickscache/dotnet30/dotnetfx3.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec24) stub!
fixme:advapi:DecryptFileA "c:\\975739e1d76502e76137a983a4d64799\\" 00000000
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:LsaOpenPolicy ((null),0x33ef98,0x00000001,0x33efb4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x33e638,0x00000001,0x33e660) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:service:QueryServiceConfig2W Level 6 not implemented
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
fixme:advapi:LsaOpenPolicy ((null),0x33dda8,0x00000001,0x33ddd0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"seeonx" (nil) 0x33aa50 (nil) 0x33aa54 0x33aa48 - stub
fixme:advapi:LookupAccountNameW (null) L"seeonx" 0x200e60 0x33aa50 0x200f48 0x33aa54 0x33aa48 - stub
fixme:msi:MsiGetFeatureValidStatesW 1 L"WAP_1.0_Core" 0x33ab14 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"Servicing_Key" 0x33ab14 stub returning 8
fixme:urlmon:CoInternetSetFeatureEnabled 8, 0x00000002, 0, stub
fixme:service:QueryServiceConfig2W Level 6 not implemented
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is running.
------------------------------------------------------
Note: command 'wine /home/seeonx/.winetrickscache/dotnet30/dotnetfx3.exe' returned status 236.  Aborting.


```

Maybe Mono 2.6?

---

### Post by SeeonX on 2010-06-17
System Requirements:
Processor : Intel Core 2 Duo E2140 at 1.6 GHz / AMD X2 4000 at 2.1 GHz
Video Card : 256 MB VRAM – nVidia GeForce 7800 GTX / ATI Radeon X700 Pro
Memory : 1 GB RAM
Hard Disk : 3 GB of free Hard Drive Space
Operating System : Microsoft Windows XP / Windows Vista
Sound Card :
Direct X : 9.0c
Controls : Keyboard & Mouse
Installation : DVD-ROM Drive

I'll check to make sure I have 9.0c installed when I get home, Vista mode enabled, and mono 2.6 installed.

---

### Post by cogadh on 2010-06-17
Don't install DirectX, it won't help and in fact might break Wine. Wine already has its own implementation of DirectX that should be sufficient for any DX 9 game.

[Mono]("http://www.mono-project.com/Main_Page") is an open source implementation of Microsoft's .NET API. It isn't 100% analogous to .NET, so some things that a .NET application might require aren't fully implemented, though 90-95% of the time it is still good enough.

I'm surprised the game doesn't list its .NET requirements, but, given that this is a new game, it is very likely dependent on .NET 3.5, which might mean the game won't work until Wine matures a bit more.

---

### Post by SeeonX on 2010-06-19
Mono 2.6 doesn't work. :( I guess I'll just have to start up VMware to run the game on XP or something. <,<

---

### Post by haphaeu on 2010-12-30
Hi all,

trying to install NFS World under openSuse 11.3, using wine 1.2.

After a few issues, I managed to install the game, but the game does not launch. 

For info, i have installed mono 2.6.

```

rafael@linux-l5z5:~/.wine/drive_c/Program Files (x86)/Electronic Arts/Need For Speed World> wine GameLauncher.exe
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 21/02/2010, dlt (d/m/y): 17/10/2010

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for GameLauncher.ProdUI.Program ---> System.TypeInitializationException: An exception was thrown by the type initializer for log4net.Core.LoggerManager ---> System.TypeInitializationException: An exception was thrown by the type initializer for log4net.Util.SystemInfo ---> System.TypeInitializationException: An exception was thrown by the type initializer for System.TimeZone ---> System.NotSupportedException: Can't get timezone name.
  at System.CurrentSystemTimeZone..ctor (Int64 lnow) [0x00000] in <filename unknown>:0 
  at System.TimeZone..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.DateTime.get_Now () [0x00000] in <filename unknown>:0 
  at log4net.Util.SystemInfo..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at log4net.Core.LoggerManager.GetVersionInfo () [0x00000] in <filename unknown>:0 
  at log4net.Core.LoggerManager..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at log4net.LogManager.GetLogger (System.Reflection.Assembly repositoryAssembly, System.String name) [0x00000] in <filename unknown>:0 
  at log4net.LogManager.GetLogger (System.Type type) [0x00000] in <filename unknown>:0 
  at GameLauncher.ProdUI.Program..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---


```

since the app doesn't even launch, I know it'll be more difficult to get it to work properly... but anyway, any help would be much appreciated.

Thanks,
Haphaeu

---

### Post by warbleeder on 2011-01-02
trying to get it running under mint 10 i can install but when i go to launch i get a wine erro saying a program crashed... sothis can be runnable in linux just needs wine to be config properly im working on it and will post here p.s dont try play on linux as you cant even install the game

---

### Post by warbleeder on 2011-01-02
ow and p.s its not NFSW that crashes its a program in wine so its looking good

---

### Post by warbleeder on 2011-01-02
im getting netframe erro so time to play around anyone els had luck?

---

### Post by warbleeder on 2011-01-02
i got past framework erro but i also get iso is corrupt i tryed uninstall and reinstall and just corrupt exe... i think its still down to wine and not the game ...play time

---

### Post by cogadh on 2011-01-02
The game has a "garbage" rating with the current Wine. I don't think any amount of messing with Wine configs and such will fix this, the Wine code itself still needs to mature some more before the game will work:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20797](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20797)

---

