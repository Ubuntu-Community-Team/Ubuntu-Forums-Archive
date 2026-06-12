---
title: "Dungeons &amp; Dragons Online: Eberron Unlimited"
date: 2009-09-10
forum: Wine
---

### Post by Jeek Elemental on 2009-09-10
Free to play mmo (with cash shop and perks for subscribing) based on d&d 3.5, set in Eberron.

As of wine --version 1.3.37 no special settings or native .dlls are needed, use appdb only as reference if any problems occur.

Checklist for problem free running:

-DDO installed in clean .wine/ (no added registry settings, nothing installed)
-pylotro installed and set up (wizard in menu), either linux or windows version
-DDO updated through pylotro (ddo hangs at loading screen if version mismatch)
-OpenGL support, proprietary ATI or Nvidia drivers needed. Hw demands are very modest.
-Wine version 1.3.37 or later

Feel free to ask questions if your setup differs but please detail differences.

Wine 1.4 is now in the official repositories and has no problems running ddo, if theres any glitches try
the latest beta wine ppa at: [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

go to [www.ddo.com](www.ddo.com) for account and download, [http://www.lotrolinux.com/download.php](http://www.lotrolinux.com/download.php)
for launcher (thank you ajackson and SNy for making this!)

---

### Post by Naegling23 on 2009-09-10
thanks for the info, I have been following this release, intending to check it out.  I've never played DDO before, and was unsure how it ran in wine.  I guess I'll have to check it out now.

---

### Post by peacewithall on 2009-09-13
> **Jeek Elemental said:**
> Just a note, this game is free to play now, with cashshop.
Seems to be a love/hate game for most, I prefer it over any mmo out there :)

go to [www.ddo.com](www.ddo.com) for account and download, [http://www.lotrolinux.com/download.php](http://www.lotrolinux.com/download.php)
for launcher.

Perfect fit for ubuntu and wine, I run 3 clients at the same time on my feeble X2 4600/2GB+radeon 4650/512MB.
Cpu-wise its fine actually, but memory is tight.

This is on ubuntu jaunty 64bit, wine 1.29 and catalyst 9.10.
I did run into a crash bug, setting texture quality to very low fixed it for now.

OMG thanks so much for this !!!!.

---

### Post by Tigersmind on 2009-09-13
Thanks for the info!

I have been looking for an MMO and I like this one so far. The launcher is just fantastic :D

---

### Post by uberlube on 2009-09-13
ok so i have the launcher installed, have an account made, and i downloaded the installer. when i try to run it though it gives me this error:
```
$ wine ddostandard.exe 
Log file is being written to C:\windows\temp\ddostandard.exe.log
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x6b0d6b
```

Anyone else getting this or know a workaround?

---

### Post by DamnName on 2009-09-13
I have an identical error.  Any help would be greatly appreciated.

---

### Post by jasonditz on 2009-09-13
> **uberlube said:**
> ok so i have the launcher installed, have an account made, and i downloaded the installer. when i try to run it though it gives me this error:
```
$ wine ddostandard.exe 
Log file is being written to C:\windows\temp\ddostandard.exe.log
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x6b0d6b
```

Anyone else getting this or know a workaround?

I'm getting it as well with ddohigh.exe

The log says:

9/13/2009 16:52:52.604:main:D:Running version 0.9.9.2
9/13/2009 16:52:52.604:main:D:OS is Windows XP ; Architecture is x86
9/13/2009 16:52:52.737:main:D:Loading config from installer.ini
9/13/2009 16:52:52.738:main:D:Could not find file installer.ini
9/13/2009 16:52:52.738:main:D:Loading config from jar

---

### Post by HKJGN on 2009-09-14
im not getting an error but mine says the same thing when i try to install DDO, this happens well before you need LOTRO's program, how do you fix it?

9/14/2009 11:23:27.690:main:D:Running version 0.9.9.2 
9/14/2009 11:23:27.690:main:D:OS is Windows XP ; Architecture is x86 
9/14/2009 11:23:27.872:main:D:Loading config from installer.ini 
9/14/2009 11:23:27.873:main:D:Could not find file installer.ini 
9/14/2009 11:23:27.873:main:D:Loading config from jar

on Wine HQ it looks like it hasnt been tested in 1.29, the WineHQ forums have no info regarding this error, and it looks like noones had a solution yet, could anyone post thier instructions of exactly what they did to get it to operate?

---

### Post by uberlube on 2009-09-14
i agree, pls let us know how u got it working if u did

---

### Post by jasonditz on 2009-09-14
According to another forum this is a known issue with wine, and the only way to successfully install DDO is to use the beta installer (which unfortunately I haven't been able to find anywhere).

---

### Post by Jeek Elemental on 2009-09-14
yes the new installer wont work it seems, I missed that since I updated from an existing install. 
If you have access to a windows box the install directory can simply be copied to your wine drive.

details: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785)

Since the client is free now and can be copied without problems, maybe Turbine will allow a .torrent of the install dir.

---

### Post by uberlube on 2009-09-15
I did copy the dir from a win box but for some reason pylotro is detecting it but says it cant find language files. I copied both the DDO folder and the Turbine one as well but im not sure if there was something else i needed. any ideas?

---

### Post by uberlube on 2009-09-15
ok so looking back on the win box i realized that it hadnt actually finished installing. ill post back later on my progess once its transfered

---

### Post by uberlube on 2009-09-15
ok so i can confirm that the game runs quite well once its copied over. 6.3 gigs in total so be ready if ur gonna do it.

---

### Post by HKJGN on 2009-09-16
awesome ill have to try it

---

### Post by thaswiftness on 2009-09-16
I was wondering if anyone can shed some light on my problem loading this game. 

I can get pylotro to load up, I log in, the game launches, but it won't get past the opening screen with the ESRB notice / copyright info screen. The window just closes and the wine log screen from pylotro just says ***Finished***

What am I missing here? :confused:

---

### Post by phreakyo on 2009-09-16
> **thaswiftness said:**
> I was wondering if anyone can shed some light on my problem loading this game. 

I can get pylotro to load up, I log in, the game launches, but it won't get past the opening screen with the ESRB notice / copyright info screen. The window just closes and the wine log screen from pylotro just says ***Finished***

What am I missing here? :confused:

I have the same problem. Are you using the high definition texture download, by any chance? Maybe the advanced graphics stuff is crashing wine.

---

### Post by thaswiftness on 2009-09-16
Yes, but I've also tried disabling the high res graphics in the pylotro settings. I also found that there was a log created from the dndclient :```

$ cat .wine/drive_c/Program\ Files/DND/dndclient.log 
000000006.624: ----CRASH REPORT START----
000000006.624: Program fault: ACCESS_VIOLATION (0xc0000005) trying to read from 0x0000000C
000000006.624: Detailed report:

Current local time: Wed Sep 16 18:32:30 2009


Version Report generated by CoreVersion : 2.0.99 (0x02000063):
  Language: English
  CompanyName : Turbine, Inc.
  FileDescription : <FileVersion
  FileVersion : 01.09.03.8005
  InternalName : dndclient
  LegalCopyright : Copyright © 1997-2009 Turbine, Inc.
  OriginalFilename : dndclient.exe
  ProductName : dndclient
  ProductVersion : 01.09.03.8005 unlimited
  Comments : compiled Sat Jul 18 07:41:39 2009 : retail
  TurbineBuildVersion : 01.09.03.8005.retail
  TurbineType : Player External



000000006.624: ----CRASH REPORT END----



```

And I changed the winedebug setting in pylotro to winedbg and got :

```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f6a4,0x00000000), stub!

fixme:wbemprox:wbem_locator_ConnectServer 0x140a00, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32fa50)

fixme:wbemprox:wbem_locator_ConnectServer 0x146438, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32fa50)
fixme:wbemprox:wbem_locator_ConnectServer 0x146438, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32faa4)

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!

fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table

fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!

fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table

fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x1485c0) : stub

fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20032 0x00000000

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x5766c28,0x5766b70): stub

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x5766c28,0x5766b70): stub

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x5764b50,0x5764ad8): stub

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x5764b50,0x5764ad8): stub

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:xinput:XInputGetState (3 0x21cea2c)
fixme:xinput:XInputGetState (2 0x21cea2c)
fixme:xinput:XInputGetState (1 0x21cea2c)
fixme:xinput:XInputGetState (0 0x21cea2c)

fixme:faultrep:ReportFault 0x32f558 0x0 stub

*** Finished ***


```

The error code from the dndclient seems to point to a .Net problem from turbine from some searching I did, but I've used winetricks to install it.

:confused:

---

### Post by Tamvolan on 2009-09-17
So, Uberlube:
 
What you're saying is that you need to install the game on the windows box, and copy over the folder where the game has been installed?  Then you can just wine executable name, from the folder?

---

### Post by uberlube on 2009-09-18
> **Tamvolan said:**
> So, Uberlube:
 
What you're saying is that you need to install the game on the windows box, and copy over the folder where the game has been installed?  Then you can just wine executable name, from the folder?

Yes and no. You do need to copy over the FULLY installed game into your wine prefix under Program Files. What I mean by fully is that the game will install about 600mb at first and then the turbine manager will install the rest in the background, so ull have to wait until it is finished to grab the whole thing. Once its copied over you have to install pylotro and use that to launch the game.

---

### Post by Tamvolan on 2009-09-18
Gotcha.  I started the download last night, let it run all night, and it got stuck around 3.4 GB out of the 4.8 or whatever it was...

---

### Post by HKJGN on 2009-09-18
worked perfectly for me.

---

### Post by Jeek Elemental on 2009-09-19
Note that the Wine version in the default repos is pretty old.

If you cant get it to run with wine 1.0 you could try

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

for the latest wine.

For 64bit you may have to use

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by ulyyoung on 2009-09-19
Hi there, I'm having a bit of a different problem, I'm wondering if anyone else sees this error...
I was able to copy windows files over, and install pylotro/lotrolinux, from there I was able to change game settings for DDO, and ran the "check" from tools to update.
After updating I try to log in, however I have been getting this error.

Checking account details...
[E08] Server not found - may be down

Said this for any server I tried.  Anyone know a solution?

---

### Post by evil_urna on 2009-09-22
I got the game to install just fine and run. My problem is it runs like utter crap. It is very, very slow even with low quality and useing the normal installer. My machine is well above system reqs so its not that.

---

### Post by Gylu on 2009-09-26
Hmm with a little work I get a fully installed dir from some one and was able to use the LotR launcher to get logged in but when I log into the game it will not respond to my keyboard and I can move my mouse but I can not click on anything.  Is anyone else having this problem?

---

### Post by hikaricore on 2009-09-26
> **evil_urna said:**
> I got the game to install just fine and run. My problem is it runs like utter crap. It is very, very slow even with low quality and useing the normal installer. My machine is well above system reqs so its not that.

Like most things running under WINE you need way more than the minimum requirements.
I assume you have a high end nvidia card (or ati if you're not lucky) and lots of ram + a fast multicore processor?

---

### Post by Gylu on 2009-09-26
OK with a little trial and error ie smashing the keyboard with my hands I have it working.  For some reason hitting the print screen key will make my keyboard/mouse start working.  I have to hit it every time I log in but then it work till I log out.

---

### Post by ajackson on 2009-09-26
> **Gylu said:**
> OK with a little trial and error ie smashing the keyboard with my hands I have it working.  For some reason hitting the print screen key will make my keyboard/mouse start working.  I have to hit it every time I log in but then it work till I log out.
Or you could just make sure the windows version in wine is set to windows 2000. Saves on damage to keyboards :)

---

### Post by jmervyn on 2009-09-29
Mr. Jackson, you have definitely put together a nice product.   Might I suggest that instead of having three different places where one has to select LotRO or DDO, a single selection?

Sadly, I am unable to get the damn .EXE to get past your program, but I'm trying to run it without recompiling <AND> from a different HDD.

It claims,
"err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element" followed by a Wine Game Error [205] "The game client was passed invalid command-line parameters.[205]"  Chances are if I wasn't trying to be cute and use the same installation for both sides of my dual-boot, I'd be successful.

---

### Post by ajackson on 2009-09-30
> **jmervyn said:**
> Mr. Jackson, you have definitely put together a nice product.   Might I suggest that instead of having three different places where one has to select LotRO or DDO, a single selection?
There are only really two places where you need to select which game you want, in the configuration (either manual or wizard) which once done shouldn't need altering and when selecting a default game or switching between which game to play. Since the whole log in, patch, etc procedures are the same having two separate launchers would be a waste of time.

> **jmervyn said:**
> 
Sadly, I am unable to get the damn .EXE to get past your program, but I'm trying to run it without recompiling <AND> from a different HDD.

It claims,
"err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element" followed by a Wine Game Error [205] "The game client was passed invalid command-line parameters.[205]"  Chances are if I wasn't trying to be cute and use the same installation for both sides of my dual-boot, I'd be successful.
Neither error is to do with the launcher, well the second one is in a way. The first is just a sound error, Ubuntus pulse and wines Alsa don't seem to play nicely (under Karmic they seem more friendly) so for LotRO & DDO it is best to set Wines sound to OSS (use winecfg), you'll lose sound in the cut scenes but that can't be helped.

The second error is because the game isn't patched, it is the game client throwing out that error. With DDO and a non Mines of Moria version of LotRO you need to find a suitable version of [patchclient.dll]("www.lotrolinux.com/LOTRO_EU_Bk13_PatchClient.tar.bz2"), I believe that Eberron Unlimited now has a suitable version of this file but you need to patch to get it (nice chicken & egg situation) so just drop LotROs version into your game directory and try patching.

---

### Post by jackschmidt on 2009-10-11
I figured out how to install DDO without having to copy a Windows install.  You have to use the DDO Stormreach installer instead of Eberron.

Here's the installer I used.
[Download]("http://download.ddo.level3.turbine.com/largecontent/ddo/mod8/downloader/live/standardres/DDO-US-Mod8-Downloader-StandardRes.exe")

This will download the entire 2.9+ GB installer for Stormreach.  Install that and use PyLotRO to update the game up to Eberron.

Hope this helps other players who want to play DDO but don't have a Windows installation.

Cheers!

---

### Post by Artemis3 on 2009-10-16
> **jackschmidt said:**
> Here's the installer I used.
[Download]("http://download.ddo.level3.turbine.com/largecontent/ddo/mod8/downloader/live/standardres/DDO-US-Mod8-Downloader-StandardRes.exe")

This will download the entire 2.9+ GB installer for Stormreach.  Install that and use PyLotRO to update the game up to Eberron.

I just did this, but I'm at a loss of what to do after launching pylotro.

There is a "Patch" inside the "Tools" menu, but all that does is show 3 times this message:

```
err:rundll32:WinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
```

If i launch the game, i get to see a pretty movie, and then a loading screen that never finishes.

---

### Post by ajackson on 2009-10-16
> **Artemis3 said:**
> I just did this, but I'm at a loss of what to do after launching pylotro.

There is a "Patch" inside the "Tools" menu, but all that does is show 3 times this message:

```
err:rundll32:WinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
```

If i launch the game, i get to see a pretty movie, and then a loading screen that never finishes.
Try reading my post (three up) about patching.

---

### Post by Naegling23 on 2009-10-18
Thanks for the install info, the game seems like fun the brief time I have been able to try it out.

However, I keep getting frequent and sporatic crashes of the game.  I tried setting texture detail to very low, but they still happen...are there any other potential fixes.  According to winehq, setting the game to windows 2000 works better...ive already tried that one.

Edit:  I found out I was using the version of wine from the repo's.  Does this make that big of a difference?

Edit-Edit:  upgrading to the latest wine release seems to have fixed the problem.

---

### Post by sabmo on 2009-10-29
Just here to say THANKS AJACKSON!

I couldn't get the current version to work, but I downloaded the previous version and then used the patcher, the patcher didn't work until I updated the patcher.dll but after that it patched then ran properly!

Good work man!

Now just to get Turbine to officially support Linux!

---

### Post by eSilence on 2009-10-30
After using ArchLinux and struggling to get DDO:EU to work over there, I switched to Kubuntu Karmic 64 bit. The game actually works here, unlike Arch. But I also have a problem.

At random points during the gameplay, the game will close without warning and the Output window just says ***Finished***. My game is patched and everything, as I can log on fine. 

Any help?
Thanks,
Echoed.

---

### Post by ajackson on 2009-10-31
> **eSilence said:**
> Any help?
Any information?

---

### Post by eSilence on 2009-11-01
> **ajackson said:**
> Any information?
Like what information? My system specs?

Asus G50vt-X1 Laptop, with 4 gigs of RAM, 320 gig HDD, nVidia 9800 GS, and a 2.5 Ghz Dual Centrino 2, running Kubuntu 9.10 64 bit.

---

### Post by ajackson on 2009-11-02
> **eSilence said:**
> Like what information? My system specs?

Asus G50vt-X1 Laptop, with 4 gigs of RAM, 320 gig HDD, nVidia 9800 GS, and a 2.5 Ghz Dual Centrino 2, running Kubuntu 9.10 64 bit.
How did you install, what else have you installed in the same prefix, have you altered the registry in any way?
How about wine version, you did read the sticky at the top of the forum I take it?

---

### Post by eSilence on 2009-11-02
> **ajackson said:**
> How did you install, what else have you installed in the same prefix, have you altered the registry in any way?
How about wine version, you did read the sticky at the top of the forum I take it?

When you say install, you mean DDO, right? I got DDO from my windows Vista machine. I just copied the folder from Program Files over, and dropped that into my /home/atherion.

For wine, I just grabbed the latest version from the website, which is 1.1.32. And I haven't changed my registry in any way.

---

### Post by ajackson on 2009-11-02
> **eSilence said:**
> I haven't changed my registry in any way.
That could be the problem, you have a pretty new graphics card and wine might not be detecting it right so you end up with the default amount of graphics memory (which isn't much), my guess is the crashes have happened when there has been a huge change in the textures needed (i.e. going inside/outside, switching zones, etc).

The AppDB page has the correct registry entry to change to match your true amount of graphical memory (I can remember part of the name but wouldn't want to guess the full registry path).

---

### Post by Toffeeapple on 2009-11-03
Mine looks like this..

```
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"Multisampling"="enabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="auto"
"VideoMemorySize"="512"
```

and that works just fine on the system in my sig.

---

### Post by eSilence on 2009-11-03
> **Toffeeapple said:**
> Mine looks like this..

```
REGEDIT4

**[HKEY_CURRENT_USER\Software\Wine\Direct3D]**
"DirectDrawRenderer"="opengl"
"Multisampling"="enabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="auto"
"VideoMemorySize"="512"
```and that works just fine on the system in my sig.

Could it be that I don't have that directory? Look:
[http://omploader.org/vMm93cA](http://omploader.org/vMm93cA)

---

### Post by Toffeeapple on 2009-11-04
Yep, that could be it, you need to make a new key under HKEY_CURRENT_USER\Software\Wine\ called Direct3D and then add the string values..

---

### Post by themusicwave on 2009-11-06
Anyone know why I would be getting an error indicating I don't have the current client when I try to run it?

Before upgrading to Karmic everything worked great.  I'm not sure what is missing or what changed during the upgrade.  Any help would be great.  I get this wine output as well:

> err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:widOpen Error open: Input/output error
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error

mmap() failed: Cannot allocate memory

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:widOpen Error open: Input/output error

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:widOpen Error open: Input/output error

*** Finished ***

---

### Post by themusicwave on 2009-11-06
As a followup from my last post, I changed the wine package I am using.  Previously I had the package called wine from teh repo which was version 1.01.  

Now I have wine1.2 which is wine 1.1.31.  It still gives me the same message:

"Connection Failed: You do not have the current version of the client installed"

Also, I get these errors in pylotro's output window:

> wine: configuration in '/home/jon/.wine' has been updated.

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

AL lib: alAuxEffectSlot.c:507: alcDestroyContext(): deleting 1 AuxiliaryEffectSlot(s)

AL lib: alEffect.c:1167: exit(): deleting 1 Effect(s)

*** Finished ***

---

### Post by eSilence on 2009-11-07
Try going to 1.1.32. The wine version that is. It didn't work for me until I moved there, although I didnt have your error. Gonna try that registry fix now.

---

### Post by themusicwave on 2009-11-07
I booted into XP an upgraded the client.  However, it now fails with the following wine output.

> mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

AL lib: ALc.c:1368: exit(): closing 1 Device
AL lib: ALc.c:1345: alcCloseDevice(): destroying 1 Context
AL lib: alAuxEffectSlot.c:507: alcDestroyContext(): deleting 1 AuxiliaryEffectSlot(s)

AL lib: alEffect.c:1167: exit(): deleting 1 Effect(s)

*** Finished ***

It gets to the loading screen and then just quits.  Works fine in XP, so I guess I'll be booting into that to play.

---

### Post by themusicwave on 2009-11-08
I went back to wine 1.01 in Ubuntu Karmic and now the game launches and plays.  The only problem is no sound.

In the in game audio menu, it lists "none" as the only sound option.  Not sure why wine isn;t seeing my card any more.

If I go in to wincfg, and mess with the options and hit sound test it always works.  It just never seems to work in the game.

Any ideas?

---

### Post by evil_urna on 2009-11-17
I am haveing a issue with voice chat. It works great on my windows boot with my USB headset but is does not with ubuntu. I tried just useing a normal mic and that does not work either. In the in game voice chat settings the only option it gives me is "default" I have played around with the Ubuntu sound settings and it does see the USB mic and I can use it with other apps but just not with DDO. 

I read somewhere that you have to use the wine config to point ALSA to 0, whatever that means, but I have no idea where I can do that, if I click on config on ALSA it does nothing.

TIA

---

### Post by Toffeeapple on 2009-11-18
[This]("http://www.wowwiki.com/Wine/Misc#In-Game_Voice_Chat_with_USB_Headsets") may be exactly what you are looking for..

---

### Post by evil_urna on 2009-11-18
Holy crap. This could work. Now my only problem is they are asking me to edit a file called .asoundrc and this file appears not to exist on my system. Any ideas there?

---

### Post by evil_urna on 2009-11-18
> **evil_urna said:**
> Holy crap. This could work. Now my only problem is they are asking me to edit a file called .asoundrc and this file appears not to exist on my system. Any ideas there?

I found a post on the forum that dealt with this, [http://ubuntuforums.org/showthread.php?t=360791](http://ubuntuforums.org/showthread.php?t=360791). I used the sample config and the issue now is it tries to pipe all the audio through the headset instead of through the speakers. I think my problem is with this config file. is there a way to generate one that is more accurate to my system?

---

### Post by evil_urna on 2009-11-18
> **evil_urna said:**
> I found a post on the forum that dealt with this, [http://ubuntuforums.org/showthread.php?t=360791](http://ubuntuforums.org/showthread.php?t=360791). I used the sample config and the issue now is it tries to pipe all the audio through the headset instead of through the speakers. I think my problem is with this config file. is there a way to generate one that is more accurate to my system?

ok I dumped this in a file named .asoundrc in my home folder
```

pcm.headset {
     type hw
     card 1
}
ctl.headset {
     type hw
     card 1
} 

```

My mic now works. horray! But now my audio does not work. In the in-game audio menu the only choice is now "default audio on USB audio" and it does not come through the speakers or the USB headset speaker. I am pretty much lost at this point lol.

---

### Post by Toffeeapple on 2009-11-18
HI,

.asoundrc in your home directory is basically a per user configuration file for alsa. and as far as I know ubuntu uses pulse which 'then' uses alsa and then gets all complicated and I really haven't the faintest idea how it all works, you're on your own : )

Not wanting to go into it all and really I haven't the faintest clue anyway.. but pules as far as I have found from trying it on occasion, where as it does give you more 'bells and whistles' ooh I can set individual volumes for individual apps.. ! and stuff, to fiddle with, at the end of the day it just overcomplicates the issue.

Right now I'm on an arch install with just alsa and my sound is all rather easy to deal with and that link I gave earlier helps me have duel sound cards in all my wine prefixes where needed.

---

### Post by Toffeeapple on 2009-11-18
But!

you are only mentioning one sound source in your .asoundrc file

this is mine.

```
pcm.Audigy2 {
        type hw
        card 0
}

ctl.Audigy2 {
        type hw
        card 0
}

pcm.Live {
        type hw
        card 1
}

ctl.Live {
        type hw
        card 1
}

```


Do this in a terminal to see what you have.

cat /proc/asound/cards

This is what I get.
```
[gaia@Al-Masjid ~]$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 ZS [SB0350]
                      SB Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xb000, irq 20
 1 [Live           ]: EMU10K1 - SB Live! 5.1 [SB0060]
                      SB Live! 5.1 [SB0060] (rev.7, serial:0x80611102) at 0xb800, irq 18

```

Hope that helps, sorry if it doesn't.

---

### Post by evil_urna on 2009-11-18
> **Toffeeapple said:**
> But!

you are only mentioning one sound source in your .asoundrc file

this is mine.

```
pcm.Audigy2 {
        type hw
        card 0
}

ctl.Audigy2 {
        type hw
        card 0
}

pcm.Live {
        type hw
        card 1
}

ctl.Live {
        type hw
        card 1
}

```


Do this in a terminal to see what you have.

cat /proc/asound/cards

This is what I get.
```
[gaia@Al-Masjid ~]$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 ZS [SB0350]
                      SB Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xb000, irq 20
 1 [Live           ]: EMU10K1 - SB Live! 5.1 [SB0060]
                      SB Live! 5.1 [SB0060] (rev.7, serial:0x80611102) at 0xb800, irq 18

```

Hope that helps, sorry if it doesn't.

based on what you entered I took my info

```
 
0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                      Intel 82801BA-ICH2 with AD1885 at irq 17
1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1f.4-2.3, full speed

```

and entered this

```

pcm.I82801BAICH2 {
     type hw
     card 0
}
ctl.I82801BAICH2 {
     type hw
     card 0
} 
pcm.headset {
     type hw
     card 1
}
ctl.headset {
     type hw
     card 1
} 

```

and I am still haveing the same problem. do I need a copy of this file in /etc? I am likeing the cut of your jib and I think I am on the right track.

---

### Post by Toffeeapple on 2009-11-19
I don't think it needs to be in /etc

but apart from that but I haven't the faintest idea where you should go from here..

.. you're on your own.

Sorry : )

---

### Post by evil_urna on 2009-11-21
I am to the point now where I dont think voice chat will work at all with my setup. Thanks for the help. excuse me I gotta put a round through my PC

---

### Post by salemboot on 2009-12-08
Just a quick script to install 

#!/bin/bash
################### Install Dungeons and dragons online ##########
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update 
sudo apt-get install wine1.2

wget "http://www.kegel.com/wine/winetricks"
bash winetricks vcrun2005
bash winetricks vcrun2005sp1

wget "http://download.ddo.level3.turbine.com/largecontent/ddo/mod8/downloader/live/standardres/DDO-US-Mod8-Downloader-StandardRes.exe"
wine DDO-US-Mod8-Downloader-StandardRes.exe

wget "http://www.lotrolinux.com/LOTRO_EU_Bk13_PatchClient.tar.bz2"
#tar vxf LOTRO_EU_Bk13_PatchClient.tar.bz2 -C "~/.wine/drive_c/Program Files/Turbine/Dungeons & Dragons Online - Stormreach"
tar vxf LOTRO_EU_Bk13_PatchClient.tar.bz2 -C .wine/drive_c/Program\ Files/Turbine/DDO\ Unlimited/


wget "http://www.lotrolinux.com/ajackson-public.key"
sudo apt-key add ajackson-public.key

sudo add-apt-repository ppa:ajackson-bcs/ppa
sudo apt-get update
sudo apt-get install pylotro

/usr/bin/pylotro

#########################################




References:
This forum post and 
[http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X#Installing_VC.2B.2B_Runtime](http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X#Installing_VC.2B.2B_Runtime)

#[http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu)

---

### Post by zzottt on 2009-12-10
nice script salemboot :)


> **themusicwave said:**
> ....The only problem is no sound.

In the in game audio menu, it lists "none" as the only sound option.  Not sure why wine isn;t seeing my card any more.

If I go in to wincfg, and mess with the options and hit sound test it always works.  It just never seems to work in the game.

Any ideas?

I have the same problem, other Wine apps work fine with sound. 
EDIT: nm its working now. I reinstalled Wine

---

### Post by salemboot on 2009-12-16
i fixed most of the links in the script if it don't work let me know.
Also make sure you:

sudo apt-get update && sudo apt-get upgrade 

first.

---

### Post by Xovan on 2009-12-21
FIXED:See bottom


As this is the place with the most complete thread talking about this I'll ask here. :D

On my slackware64 13 machine I was able to 
get wine running
download and install DDO
download and install pyLotro
patch DDO through pyLotro

However once I put in my credentials and try to start the launcher I get no errors, no messages, it just runs one of my cores like hell and never actually launches the game.  Any ideas on what I might have done wrong?

Don't know if this helps but the visual c++ runtime 2005 is installed through winetricks but it doesn't seem to show up in pylotro's "Check Prefix" menuitem dialog under the tools menu.



Btw here's some basics my machine:
AMD Phenom 1.8ghz Quad Core
1 gig ram
Nvidia Geforce 8400 256MB
Slackware 13 (64-bit)


Fix:
what I did wrong was I installed DDO BEFORE I installed the .net framework version 1.1 So I had to clean my wine prefix and winetricks cache

```
rm -rf .wine
rm -rf .winetrickscache
winecfg

```

And then install visual C++ runtime 2005 and visual C++ runtime 2005 sp1 then .net framework version 1.1 then install DDO

---

### Post by Ferrat on 2009-12-22
The DDO installer worked great for me, I had the 
visual C++ runtime 2005 fix and the regedit hack for .NET
The downloader doesn't work in WINE, ran that in a VMBOX then downloaded highres install, moved it to LInux and ran the install via WINE (in terminal, "normal" double click doesn't work) and it installed just fine, updated OOTB with pyLOTR and played without any problems on high graphics :)

---

### Post by NeoFax on 2009-12-31
OK, I had the game working fine just last night on my laptop and now it starts, switches to the correct resolution displays the hourglass mouse and then dumps back to PyLOTRO.  I have not made any changes from then until now.  I am running Karmic w/ Wine 1.1.35, Intel Mobile 945GM w/ S3TC Texture compression turned on.

---

### Post by Schotty on 2010-01-03
Sorry to be as late to the party as I could have posted day one of the new version of DDO (the addition of F2P).

I have been running this on my iMac and on my Ubuntu 9.10 boxes for some time.  Firstly on my iMac, later after I bought a new lappy on that with 9.10.

On both I am using the same method.

1) Install Crossover Games
2) Download the FULL installation files for the game & Install off of that
3) Download the windows pytlotro, install it, and use that to then patch and load the game

I found that as of day one, that was not possible, but an update somewhere around October 1st give or take has a wine update that fixes the bug that prevents the installation off of the full install blob that was aforementioned.

I am currently running this with no issues on both my iMac (OSX 10.5.the latest) and my Laptop (9.10 x64).

I avoided using vanilla wine due to oddities I have run into on Fedora, CentOS, and RHEL in the past with wine64.  I must be honest, I did Google if Ubuntu had the issues and saw some did, but have no firsthand knowledge if there ARE issues on Ubuntu x64 with wine64 loading apps properly or not.  I just would rather avoid the issues entirely.

Hope this helps someone, and all hail the uberness of the wine devs, and Codeweavers, as they let us all game on linux with non native evile win32 code.  Although I do have a sub with Cedega, Transgaming has been dropping the ball alot lately and hasn't gotten squat working correctly for me in ages.

Founder (and have wayyy too many toons) of Khyber's "Fist to Face Conversationists."  A guildie is making a sister set of guilds on the alt servers, but the main on is on Khyber.  Feel free to find us and run an adventure with us. My main is Zacharaias, lvl 14 FvS duker & nuker.  Hope to see you all :D

PS: And if we get enough REAL linux users join up, I am willing to create a guild that advertises that fact.

---

### Post by Derath on 2010-01-06
On Thelanis, there is a Linux Guild... I can't remember all the names of members right now, but we have about 15 members and growing at the moment
(Derath, Kilreth, and Ranthral are my char names)

---

### Post by Artemis3 on 2010-01-28
Has anyone had issues with double click ie: when buying an item?

I have been playing this game for a couple of months, worked fine at first. Later i noticed having trouble double clicking, needing to do it like 3 or 4 fast clicks in a row to make it work. But today, i found i can no longer double click at all. Also i seem to have lost right click... Anyone else experiencing this? This doesn't happen with other wine apps.

PS: If someone finds this post, i solved it by deleting/renaming the files ddo.keymap and UserPreferences.ini (both of them). These files are normally stored in "My Documents\Dungeons and Dragons Online" which in my case turns to be "~/Dungeons and Dragons Online" (My Documents is symlinked to ~).

---

### Post by b1n4ryb0rn on 2010-01-30
hey i am running the pylorto launcher for ddo i got it all to install but everytime i launch the game it tells me that my account is not active. my wifes win pc can logme in and play but the linux pc cannot, any idea why? any help would be appericated

---

### Post by b1n4ryb0rn on 2010-01-30
> **b1n4ryb0rn said:**
> hey i am running the pylorto launcher for ddo i got it all to install but everytime i launch the game it tells me that my account is not active. my wifes win pc can logme in and play but the linux pc cannot, any idea why? any help would be appericated
i need to correct the previous post i updated wine and created a new account so now i get an error 129 andy ideas please

---

### Post by ajackson on 2010-01-30
> **b1n4ryb0rn said:**
> i need to correct the previous post i updated wine and created a new account so now i get an error 129 andy ideas please

Doesn't anyone read [stickies]("http://ubuntuforums.org/showthread.php?t=885111") any more?

No info = pure guesswork answers or no answers at all (why help someone when it feels like pulling teeth?)

---

### Post by xtracool_protik on 2010-02-01
Hi guys,
 I went through procedure (script) given by salemboot and game installed pretty smooth. However I don't see any update option under tools.
 SO I would consider the game I'm trying to run is previous version and the problem is I just get black window with title as [129]Game Error

 I think b1n4ryb0rn here have same issue. I didn't choose default folder for installation if that matters installed it under /home/DDO/Game. And my system setup is Intel x3100 graphics, 4GB RAM, 2.4 GHz C2D, UBUNTU 9.10 with kernel 2.6.32

 Thank you

---

### Post by ajackson on 2010-02-02
> **xtracool_protik said:**
> Intel x3100 graphics
That is probably your problem, I don't think many people have had any joy with DDO and the Intel drivers.

---

### Post by xtracool_protik on 2010-02-02
As I've thought
 Its really bad to get really good processor and ram but no video card. I couldn't play HoN for same reason. 
 Anyway still if anyone else have any other ideas please let me know or if any work around

 Thanks :)

---

### Post by wigard89 on 2010-02-06
Since the release of update 3 for DDO, I have not been able to update to the new version of DDO through pylotro. The game ran perfectly fine up until the release of update 3. The output from the patching screen is:

err:service:validate_service_config Service L"dxregsvc" is Win32 but has no image path set
err:service:scmdatabase_load_services Invalid configuration of service L"dxregsvc" - skipping

wine: Call from 0x7b843bf2 to unimplemented function msvcr71.dll._vscprintf, aborting

fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100

err:rundll32:WinMain Unable to load L"lotropatcher.dll"

wine: Call from 0x7b843bf2 to unimplemented function msvcr71.dll._vscprintf, aborting

fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100

err:rundll32:WinMain Unable to load L"lotropatcher.dll"

wine: Call from 0x7b843bf2 to unimplemented function msvcr71.dll._vscprintf, aborting

fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:rundll32:WinMain Unable to load L"lotropatcher.dll"

*** Finished ***

lotropatcher.dll is the patchclient.dll from book 13.
Does anyone have any idea why the launcher can't update the game this time?
I am using Ubuntu 9.10 Karmic koala, AMD Athlon X2 5000+ processor, 3 gigs RAM, 512 mb Nvidia 8400 video card.

::SOLVED::  I didn't realize that I had an older version of wine installed on my system, updated to wine v. 1.1.38 fixed my issue.

---

### Post by melinko2003 on 2010-02-18
Hi all,

Ajackson: Im having a specific issue with video for the game as soon as I login screen is black. I have turned off compiz and now it actually shows ubuntu's bars at top and bottum - im running a Intel 915 express, and I know Intel cards are supported by the game by doing a little research. 

I ran across this suggestion on another post from you:

[http://ubuntuforums.org/showthread.php?t=812367](http://ubuntuforums.org/showthread.php?t=812367)

> Run cmsettings.exe and choose OpenGL rather than Direct3D, that works fine for me.

Think this would resolve my issues as well?

Kind Regards,

Mel

Intel P4 3.06ghz 
2GB RAM
Intel 915 express
Karmic 9.10

---

### Post by xtracool_protik on 2010-02-18
Hey melnik thanks,
 I've intel 965 I'll try again the way u suggested and let u guys know how it goes. However I'm suppose to upgrade from stromarch to newest version right?

---

### Post by ajackson on 2010-02-19
> **melinko2003 said:**
> im running a Intel 915 express, and I know Intel cards are supported by the game by doing a little research. 
Then you know more than me.

> **melinko2003 said:**
> 
I ran across this suggestion on another post from you:

[http://ubuntuforums.org/showthread.php?t=812367](http://ubuntuforums.org/showthread.php?t=812367)

Think this would resolve my issues as well?

Since it is impossible to switch DDO into OpenGL mode I can't answer that question.

---

### Post by ajackson on 2010-02-19
Can people not PM me asking for support, all it does is annoy me and get you added to my ignore list. This is a support FORUM not a support PM service.

---

### Post by melinko2003 on 2010-02-19
Yea, as far as the Intel cards go - I did a bit more research on them. Unless linux actually properly utilizes the Graphics Accelerator with the onboard chip its not going to be able to play DirectX games. However in windows land... Apparently it works just fine. I still wouldn't trade Linux though .. The alternative I've found is to Rig in a low profile SLI 1x Nvidia graphics card, and play on that.

Cheer's and thanks for the clarification that OpenGL wasnt supported. I had did some hunting around and came across that as well. Sucks but It seems to be a driver issue that could be resolved by Intel. YAK

Mel

Ps. The question was not intended to piss you off of course, and it was more of a Public message vs a Private one .. Only reason I addressed you specifically was you seem to have some indepth knowledge of this, and obviously your input was valued a bit more.

---

### Post by ajackson on 2010-02-19
> **melinko2003 said:**
> Ps. The question was not intended to piss you off of course, and it was more of a Public message vs a Private one .. Only reason I addressed you specifically was you seem to have some indepth knowledge of this, and obviously your input was valued a bit more.
Oh it wasn't you, I keep getting fairly irregular PMs asking for help with either DDO or LotRO, open questions on the forums I don't mind because once I answer it (if I can) the answer is there for all to see.

---

### Post by melinko2003 on 2010-02-19
Great,

I seem to have come across a few tutorials before I found this thread, which I already went through to get this working before I ran the script provided here. Are they required?

See below:

[http://forums.ddo.com/showthread.php?t=212618](http://forums.ddo.com/showthread.php?t=212618)

> 
Direct3D.reg :
```
REGEDIT4 

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="OpenGL"
"Multisampling"="disabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="readdraw"
"UseGLSL"="disabled"
"VideoMemorySize"="###"


```


Also...

> 
-You will need the fake.net11.reg - [http://pub.kxd.cc/ddo/freebsd/fakeNET11.reg](http://pub.kxd.cc/ddo/freebsd/fakeNET11.reg) (right-click save as)

fakeNET11.reg :
```

REGEDIT4

[HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP\v1.1.4322]
"Install"=dword:00000001
"SP"=dword:00000001

[HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\policy\v1.1]
"4322"="3706-4322"

```


Can anyone shed light to as if these steps are still needed? Or if more steps outside of this are required with that script anyone shed light on what page they are on in this thread or provide some assistance as I would like to get something going that provides Linux users I know a complete walk through all on one page so I can introduce people to this great game.

Mel

---

### Post by ajackson on 2010-02-19
> **melinko2003 said:**
> Can anyone shed light to as if these steps are still needed?
The fakeNET part isn't really needed but doesn't really do any harm (the installation of .NET used to blow up during the install phase, the fakeNET just fooled the installer into thinking it didn't need to do it).

As for the first bit, the only one I'd keep is VideoMemorySize, the rest might help certain cards/configurations but they can always be added later if needed.

---

### Post by KMSMD on 2010-02-20
I had to install the Stormreach one to get anything to work for this game, but when the game starts up I get the error message of "Connection Failed: You do not have the current version of the client installed".  Now what?

Update, trying to see if maybe I can run through VirtualBox on Windows.  Anyone know if this works before I get to far into it let me know please.

---

### Post by melinko2003 on 2010-02-22
Just, grabbing the DxDiag off of my virtual machine:

> 
---------------
Display Devices
---------------
        Card name: VirtualBox Graphics Adapter
     Manufacturer: Sun Microsystems, Inc.
        Chip type: VBOX
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_80EE&DEV_BEEF&SUBSYS_00000000&REV_00
   Display Memory: 256.0 MB
     Current Mode: 1664 x 948 (32 bit) (60Hz)
          Monitor: Default Monitor
  Monitor Max Res: 
      Driver Name: VBoxDisp.dll
   Driver Version: 3.00.0010.0000 (English)
      DDI Version: unknown
Driver Attributes: Final Retail
 Driver Date/Size: 10/29/2009 04:55:20, 63696 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: VBoxVideo.sys
    Mini VDD Date: 10/29/2009 04:55:20, 59024 bytes
Device Identifier: {D7B78E0E-FDAF-11CF-B063-0A20AFC2CE35}
        Vendor ID: 0x80EE
        Device ID: 0xBEEF
        SubSys ID: 0x00000000
      Revision ID: 0x0000
      Revision ID: 0x0000
      Video Accel: 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Not Available
       AGP Status: Not Available
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run


Looking over this, it doesn't look like it im sure you need:

> 
D3D Status: Enabled


Can anyone confirm?

---

### Post by melinko2003 on 2010-02-22
I just verified if flipping the 3d acceleration on in virtualbox(3.1.4) wouldn't change D3D Status to "Enabled" , and it didn't. If I remember from all I have read about DDO, its temperamental about video cards. It seems that it only really like Nvidia Cards and rarely ATI cards(Even on windows). Im going to give it a shot tonight on my test machine ill report tomorrow or late tonight what the results are. I would suspect you will get a [192] Texture Error if it doesn't recognize the card.  

-Mel

P.s. You might try Vmware?

---

### Post by KMSMD on 2010-02-22
I have SLi enabled dual Nvidia cards, so if that is the only issue then hopefully I am set.  So far Virtualbox is rolling but still need to get all the drivers in for my rig.

---

### Post by melinko2003 on 2010-02-22
Did you put the patch.dll in for book 13 and try updating again? You might not have to install. Let me hunt up what I mean.

-Mel

---

### Post by melinko2003 on 2010-02-22
> **ajackson said:**
> There are only really two places where you need to select which game you want, in the configuration (either manual or wizard) which once done shouldn't need altering and when selecting a default game or switching between which game to play. Since the whole log in, patch, etc procedures are the same having two separate launchers would be a waste of time.


Neither error is to do with the launcher, well the second one is in a way. The first is just a sound error, Ubuntus pulse and wines Alsa don't seem to play nicely (under Karmic they seem more friendly) so for LotRO & DDO it is best to set Wines sound to OSS (use winecfg), you'll lose sound in the cut scenes but that can't be helped.

The second error is because the game isn't patched, it is the game client throwing out that error. With DDO and a non Mines of Moria version of LotRO you need to find a suitable version of [patchclient.dll]("www.lotrolinux.com/LOTRO_EU_Bk13_PatchClient.tar.bz2"), I believe that Eberron Unlimited now has a suitable version of this file but you need to patch to get it (nice chicken & egg situation) so just drop LotROs version into your game directory and try patching.

This part specifically pertains to what issue I think you might be having mate

> 

The second error is because the game isn't patched, it is the game client throwing out that error. With DDO and a non Mines of Moria version of LotRO you need to find a suitable version of [patchclient.dll]("www.lotrolinux.com/LOTRO_EU_Bk13_PatchClient.tar.bz2"), I believe that Eberron Unlimited now has a suitable version of this file but you need to patch to get it (nice chicken & egg situation) so just drop LotROs version into your game directory and try patching.



This part comes at the end of the PyLotro Script, you have to do it manually. There should be a menu option to patch. Get back to me on this.

-Mel

---

### Post by KMSMD on 2010-02-22
I tried the patch option yesterday I believe and couldn't get anywhere.  Thats why I went to the virtualbox option to see if I can work it on XP that way.

---

### Post by KMSMD on 2010-02-22
Had the game error of 122 on XP through virtualbox.  Will try once more back on Ubuntu (dling the stormreach one now) but for the launcher, does it matter if I do repository or the stand-alone version?

---

### Post by KMSMD on 2010-02-22
Just re-installed the Mod 8 version and the launcher, started the game through the launcher (after patching) and still get the good ol "You do not have the current version of the client installed".  Any other suggestions?

---

### Post by melinko2003 on 2010-02-23
What Method are you using to install? The script im assuming? Are you using Standard Def or High Def? You have set mode to windows 2000 in winecfg right? You have disabled high def in pylotro right?Try Updating/patching again .. there was another update a few days ago it might need to bring that one down too. Ill search there forums but its most likely that its in pylotro version or maybe even the wine version your using. 

Would you be able to provide us screen shots on like flickr or something to view?

---

### Post by KMSMD on 2010-02-23
Wine version is 1.1.39, set on Windows 2000. I found the Mod8 in this forum on an earlier post, someone had a link.  Of course now I am getting a new error of EO4, error accessing GLS data centre.  I appreciate the help but my patience to play this game has grown thin  :(

---

### Post by melinko2003 on 2010-02-23
Um... They are updating currently mate - Check there site. Thats a good sign.

-Mel

---

### Post by KMSMD on 2010-02-23
Ok, so that is what the update day is (i.e. WoW).  So now back to original error of not the current version.  I can't patch it seems or something.  Would it have to do more with have Mod8 version that I had to use to install or the launcher?

---

### Post by melinko2003 on 2010-02-24
Servers are up atm - give it a shot and tell me whats up .. All I know is I was getting the same error yesterday as servers were being moved to a new datacenter on there side. From what I've seen there is no regular patching segments like WoW, they fix to add features or events.

Probably to do maint. here and there on servers too.

---

### Post by KMSMD on 2010-02-24
Back to the same game error I have gotten of "Not current version installed"

---

### Post by KMSMD on 2010-02-27
So, nothing??

OK, well thanks Mel for the attempt to get me up and running but I have given up on trying to get this game to work for me.  Apparently not worth my time and trouble.

---

### Post by DarkHawkPro on 2010-03-02
So.. yay!.. another issue.. hopefully it won't beas bad..  

i got DDO to work fully and install fully and update fully.. with the Crossover Office i have.  now my problem is an easy one..  i can't get it to do anything good..  all the graphics are in low..  i admit, totally playable and haven't crashed on low yet, but.. i want some pretty here.. lol.   i was wondering if anyone had any suggestions on how to fix that..  no rush.

Wanted to add my sys specs.

Ubuntu 9.10                - the Karmic Koala
AMD 3.2ghz Quad
ATI Radeon HD:5770
4gig ram

---

### Post by ajackson on 2010-03-02
> **DarkHawkPro said:**
> i got DDO to work fully and install fully and update fully.. with the Crossover Office i have.
Use Crossover Games instead of Crossover Office/Pro, it is aimed at gaming.

---

### Post by salemboot on 2010-03-05
anyone getting model glitches with the new wine / ati drivers

---

### Post by MightyDJ on 2010-03-09
Hello. I would just like to confirm that with a Radeon X300 chipset that I am unable to avoid the "Hardware texture compression (error 129)" message that prevents me from playing this game. No combination of drivers (normal/bleeding-edge) that I have tried works to remove this error message. 

As far as I've been googling, it seems the issue is the lack of a proprietary video driver for this particular card.

I just want to make sure I haven't forgotten to try something. 

Thanks in advance.

---

### Post by Brando753 on 2010-04-25
> **MightyDJ said:**
> Hello. I would just like to confirm that with a Radeon X300 chipset that I am unable to avoid the "Hardware texture compression (error 129)" message that prevents me from playing this game. No combination of drivers (normal/bleeding-edge) that I have tried works to remove this error message. 

As far as I've been googling, it seems the issue is the lack of a proprietary video driver for this particular card.

I just want to make sure I haven't forgotten to try something. 

Thanks in advance.

I wish to also state that I have this exact same issue when trying to run ddo. A black scrren followed by a "Hardware texture compression (error 129)". If anyone knows of a workaround for this it would be great.

(P.S.Using Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07))

---

### Post by labatts on 2010-05-03
I am also getting the same "compression" error.  Any help would be great. 

Ubuntu Netbook 10.04 on an asus 1005ha.  (people say the game works on these netbooks, but according to the guide on winehq, Ubuntu is SOL.  I am hoping for another solution).

---

### Post by Morten ML on 2010-05-14
> **salemboot said:**
> anyone getting model glitches with the new wine / ati drivers

Is this the same as a black shroud coming and going in game? if so try omitting this from regedit direct3d in wine:
```
"OffscreenRenderingMode"="fbo"
``` 

@Ajackson
Thanks a bunch for making this game playable on linux!

I am running this game on ubuntu 9.10 amd64 on a i7 with ATI 4350 HD 1gb, in 1280*1024, and i cant get the graphics higher than low... if i set it higher everything is kind of turned upside down - so 2 questions:
1) Is this the max my graphics card can support?
2) If not does anybody have any ideas on how to get better graphics? (fps seems to be just fine when on low)

EDIT: Ehm i dont know if my graphics card is X300 if it is let me know and i'll see if i can replicate the "Hardware texture compression (error 129)" error.

---

### Post by upitnik on 2010-05-28
Hi!

i Have Ubuntu 10.04 trying to start DDO on it i did everything from "how to" i did pretty much everything from here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785&iTestingId=50634](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785&iTestingId=50634)
also combine with script from this thread, 
but still have problem witch patching DDO, getting some kind of rundll32.exe error i think.

Here is error code:
Connecting to patch.ddo.com:80

Checking files...
files to patch: 1 bytes to download: 138504
Patching files:

Downloading patchclient.dll.......................
.........................

......................
........................
.............
Decrypting.............................
.....

Connecting to patch.ddo.com:80

Checking files...
files to patch: 0 bytes to download: 0
Patching files:

Connecting to patch.ddo.com:80

checking data...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0072be0a).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0072be0a ESP:0033f654 EBP:0033f680 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:81930001 EBX:00165de8 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x0033f654:  7bc51eed 0033f6cc 00000000 00134b88
0x0033f664:  0033f694 7b869a7c 00000001 ffffffff
0x0033f674:  00000000 7b869a40 00134b88 0033f6cc
0x0033f684:  0072bf4b 0033f6cc 00000000 00000000
0x0033f694:  00000284 0072be00 00134b88 00456164
0x0033f6a4:  7bc753c0 00000000 00000000 00165de8
Backtrace:
=>0 0x0072be0a in ttepatchclient (+0x1be0a) (0x0033f680)
  1 0x0072bf4b in ttepatchclient (+0x1bf4a) (0x0033f6cc)
  2 0x54545f45 (0x81930001)
0x0072be0a: movl    0x0(%ecx),%ecx
Modules:
Module    Address            Debug info    Name (104 modules)
PE      340000-  352000    Deferred        zlib1t
PE      710000-  746000    Export          ttepatchclient
PE    10000000-100b0000    Deferred        ddo_patchclient
ELF    7b800000-7b93c000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93c000    \               kernel32
ELF    7bc00000-7bcb8000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb8000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
PE    7c3a0000-7c41b000    Deferred        msvcp71
ELF    7dc92000-7dd26000    Deferred        crypt32<elf>
  \-PE    7dca0000-7dd26000    \               crypt32
ELF    7dd26000-7dd63000    Deferred        rsaenh<elf>
  \-PE    7dd30000-7dd63000    \               rsaenh
ELF    7dd63000-7dd68000    Deferred        libgpg-error.so.0
ELF    7dd68000-7dd71000    Deferred        librt.so.1
ELF    7dd71000-7ddaa000    Deferred        libdbus-1.so.3
ELF    7ddaa000-7de1d000    Deferred        libgcrypt.so.11
ELF    7de1d000-7de2e000    Deferred        libtasn1.so.3
ELF    7de2e000-7de42000    Deferred        libresolv.so.2
ELF    7de42000-7de46000    Deferred        libkeyutils.so.1
ELF    7de46000-7de4e000    Deferred        libkrb5support.so.0
ELF    7de4e000-7de72000    Deferred        libk5crypto.so.3
ELF    7de72000-7df23000    Deferred        libkrb5.so.3
ELF    7df23000-7df34000    Deferred        libavahi-client.so.3
ELF    7df34000-7df40000    Deferred        libavahi-common.so.3
ELF    7df40000-7dfdb000    Deferred        libgnutls.so.26
ELF    7dfdb000-7e00a000    Deferred        libgssapi_krb5.so.2
ELF    7e00a000-7e050000    Deferred        libcups.so.2
ELF    7e05f000-7e065000    Deferred        libnss_dns.so.2
ELF    7e065000-7e069000    Deferred        libnss_mdns4_minimal.so.2
ELF    7e096000-7e196000    Deferred        ole32<elf>
  \-PE    7e0b0000-7e196000    \               ole32
ELF    7e198000-7e19c000    Deferred        libcom_err.so.2
ELF    7e19c000-7e1d0000    Deferred        uxtheme<elf>
  \-PE    7e1a0000-7e1d0000    \               uxtheme
ELF    7e1d0000-7e207000    Deferred        winspool<elf>
  \-PE    7e1e0000-7e207000    \               winspool
ELF    7e207000-7e2bc000    Deferred        comdlg32<elf>
  \-PE    7e210000-7e2bc000    \               comdlg32
ELF    7e2bc000-7e344000    Deferred        winmm<elf>
  \-PE    7e2c0000-7e344000    \               winmm
ELF    7e344000-7e35d000    Deferred        version<elf>
  \-PE    7e350000-7e35d000    \               version
ELF    7e35d000-7e38a000    Deferred        ws2_32<elf>
  \-PE    7e360000-7e38a000    \               ws2_32
ELF    7e38a000-7e473000    Deferred        comctl32<elf>
  \-PE    7e390000-7e473000    \               comctl32
ELF    7e473000-7e643000    Deferred        shell32<elf>
  \-PE    7e480000-7e643000    \               shell32
ELF    7e643000-7e6a5000    Deferred        shlwapi<elf>
  \-PE    7e650000-7e6a5000    \               shlwapi
ELF    7e6a5000-7e6c9000    Deferred        mpr<elf>
  \-PE    7e6b0000-7e6c9000    \               mpr
ELF    7e6c9000-7e723000    Deferred        wininet<elf>
  \-PE    7e6d0000-7e723000    \               wininet
ELF    7e723000-7e7a4000    Deferred        msvcrt<elf>
  \-PE    7e740000-7e7a4000    \               msvcrt
ELF    7e7a4000-7e7c3000    Deferred        msvcr71<elf>
  \-PE    7e7b0000-7e7c3000    \               msvcr71
ELF    7e7f1000-7e7fb000    Deferred        libxcursor.so.1
ELF    7e7fb000-7e801000    Deferred        libxfixes.so.3
ELF    7e801000-7e805000    Deferred        libxcomposite.so.1
ELF    7e805000-7e80d000    Deferred        libxrandr.so.2
ELF    7e80d000-7e817000    Deferred        libxrender.so.1
ELF    7e817000-7e81d000    Deferred        libxxf86vm.so.1
ELF    7e81d000-7e821000    Deferred        libxinerama.so.1
ELF    7e821000-7e843000    Deferred        imm32<elf>
  \-PE    7e830000-7e843000    \               imm32
ELF    7e843000-7e849000    Deferred        libxdmcp.so.6
ELF    7e849000-7e84d000    Deferred        libxau.so.6
ELF    7e84d000-7e867000    Deferred        libxcb.so.1
ELF    7e867000-7e86c000    Deferred        libuuid.so.1
ELF    7e86c000-7e989000    Deferred        libx11.so.6
ELF    7e989000-7e999000    Deferred        libxext.so.6
ELF    7e999000-7e9b2000    Deferred        libice.so.6
ELF    7e9b2000-7e9bb000    Deferred        libsm.so.6
ELF    7e9be000-7e9d2000    Deferred        lz32<elf>
  \-PE    7e9c0000-7e9d2000    \               lz32
ELF    7e9d4000-7ea76000    Deferred        winex11<elf>
  \-PE    7e9e0000-7ea76000    \               winex11
ELF    7eaa9000-7ead0000    Deferred        libexpat.so.1
ELF    7ead0000-7eb00000    Deferred        libfontconfig.so.1
ELF    7eb00000-7eb15000    Deferred        libz.so.1
ELF    7eb15000-7eb8b000    Deferred        libfreetype.so.6
ELF    7eba4000-7ec18000    Deferred        rpcrt4<elf>
  \-PE    7ebb0000-7ec18000    \               rpcrt4
ELF    7ec18000-7ec72000    Deferred        advapi32<elf>
  \-PE    7ec20000-7ec72000    \               advapi32
ELF    7ec72000-7ecfd000    Deferred        gdi32<elf>
  \-PE    7ec80000-7ecfd000    \               gdi32
ELF    7ecfd000-7ee2d000    Deferred        user32<elf>
  \-PE    7ed10000-7ee2d000    \               user32
ELF    7ee2d000-7ee39000    Deferred        libnss_files.so.2
ELF    7ee39000-7ee43000    Deferred        libnss_nis.so.2
ELF    7ee43000-7ee4b000    Deferred        libnss_compat.so.2
ELF    7ee4f000-7ee64000    Deferred        rundll32<elf>
  \-PE    7ee50000-7ee64000    \               rundll32
ELF    7efc1000-7efe7000    Deferred        libm.so.6
ELF    7efe9000-7f000000    Deferred        libnsl.so.1
ELF    f7430000-f7434000    Deferred        libdl.so.2
ELF    f7434000-f758e000    Deferred        libc.so.6
ELF    f758f000-f75a8000    Deferred        libpthread.so.0
ELF    f75c1000-f7701000    Deferred        libwine.so.1
ELF    f7703000-f7721000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0

00000019 explorer.exe
    0000001a    0
0000001b pylotro.exe
    0000001e    0
    0000001c    0
00000028 (D) C:\windows\system32\rundll32.exe
    0000002a    0
    00000029    0 <==
Backtrace:
=>0 0x0072be0a in ttepatchclient (+0x1be0a) (0x0033f680)
  1 0x0072bf4b in ttepatchclient (+0x1bf4a) (0x0033f6cc)
  2 0x54545f45 (0x81930001)

*** Aborted ***

if any1 have any idea what can i do to solve this problem or any direction ?

Thank you.

---

### Post by Morten ML on 2010-05-28
Hi there.

Never tried it on 10.04. but ill give it a go. 
But first i dont undestand you problem.

Is the program updated? (Did you update the program from windows and copied it to ubuntu)

Or are you trying to update it from ubuntu?

Did you set wine to run win 2000?

And with regards to the patching - Where are you patching from? inside "the lord of the rings online" loader?

---

### Post by upitnik on 2010-05-28
> **Morten ML said:**
> Hi there.

Never tried it on 10.04. but ill give it a go. 
But first i dont undestand you problem.

Is the program updated? (Did you update the program from windows and copied it to ubuntu)

Or are you trying to update it from ubuntu?

Did you set wine to run win 2000?

And with regards to the patching - Where are you patching from? inside "the lord of the rings online" loader?

- i did download ddo on windows before i went on unbuntu (that was 1day ago :) )so i used dose bin file's and installer for install DDO via wine.

- Then i have installed LOTRO_EU_Bk13_PatchClient.tar.bz2 witch i can start via wine or stand alone and inside that PyLotro i traying  to do patching witch fail every time, if i try to start DDO without patching i get msg "You dont have current version of cline installed."

- and if i go to patch it get error msg that i have posted first time ,plus pop up window witch say "The program rundll32.exe has encountered a serious problem and it needs to be closed."



Thank you.

---

### Post by Morten ML on 2010-05-29
Hi again. 

What do you mean by install?
> ...so i used dose bin file's and installer for install DDO via wine.

I just copied the whole turbine folder to the wine c drive (In programs)

And again installed?
> ..Then i have installed LOTRO_EU_Bk13_PatchClient.tar.bz2...

I just copied it (LOTRO_EU_Bk13_PatchClient.tar.bz2 file) to the "Dungeons & Dragons Online - Stormreach" folder (in wine) - and unpacked it there. Then i renamed the "patchclient (2).dll" to pylotro or something else.

and then from the loader - I assume you are using ajacksons lord of the ring loader - go to tools->options and mark advanced options and select the "pylotro.dll" as the patch client dll...

I assume you have setup the loader correctly whit regards to the rest of the things that needs to be done in there.

and again did you switch to win 2000 in wine??

---

### Post by upitnik on 2010-05-29
> **Morten ML said:**
> Hi again. 

What do you mean by install?


I just copied the whole turbine folder to the wine c drive (In programs)

And again installed?


I just copied it (LOTRO_EU_Bk13_PatchClient.tar.bz2 file) to the "Dungeons & Dragons Online - Stormreach" folder (in wine) - and unpacked it there. Then i renamed the "patchclient (2).dll" to pylotro or something else.

and then from the loader - I assume you are using ajacksons lord of the ring loader - go to tools->options and mark advanced options and select the "pylotro.dll" as the patch client dll...

I assume you have setup the loader correctly whit regards to the rest of the things that needs to be done in there.

and again did you switch to win 2000 in wine??

correct i useing  ajacksons lord of the ring loader.

i did also copied LOTRO_EU_Bk13_PatchClient.tar.bz2 into C:\Program Files\Turbine\DDO Unlimited and renamed it to DDO_patchclient.dll

also did selected in wine win 2000.

and with all that i getting message from firs and second post.

sry if i wasnt clear enough at first time :) i save on informations :)

---

### Post by Morten ML on 2010-05-29
> sry if i wasnt clear enough at first time  i save on informations  although this made me laugh it is generally not a good idea to save on info when asking for help ;)

I assume you then also selected the
> and then from the loader - I assume you are using ajacksons lord of the ring loader - go to tools->options and mark advanced options and select the "pylotro.dll" as the patch client dll...

If that is the case then I am not sure what you problem is - BUT I dont mind spending the next hour or so helping you. (I will make a vm and try and replicate your error)

If anybody else has a simple answer please post.

EDIT: are you using 32 or 64 bit?

---

### Post by ajackson on 2010-05-29
Looking at the crash, it has updated the program files/dlls then crashed on the update for data files. That tends to point to a problem with the Visual C++ 2005 run-times (or it would with LotRO, I assume DDO now needs that installed as well).

Also you don't say what version of wine you are using, open a terminal and type
```
wine --version
```

---

### Post by upitnik on 2010-05-29
> **Morten ML said:**
> although this made me laugh it is generally not a good idea to save on info when asking for help ;)

I assume you then also selected the


If that is the case then I am not sure what you problem is - BUT I dont mind spending the next hour or so helping you. (I will make a vm and try and replicate your error)

If anybody else has a simple answer please post.

EDIT: are you using 32 or 64 bit?

this is what i use if this help:
Linux kron-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

ty for any effort  ,coz i realy dont have any expiriance on linux as i said before this will be my second day on it and i still adapting.

---

### Post by upitnik on 2010-05-29
> **ajackson said:**
> Looking at the crash, it has updated the program files/dlls then crashed on the update for data files. That tends to point to a problem with the Visual C++ 2005 run-times (or it would with LotRO, I assume DDO now needs that installed as well).

Also you don't say what version of wine you are using, open a terminal and type
```
wine --version
```

i use Wine 1.2-rcl

i will check for  Visual C++ 2005 run-times if i have it or not coz i did some install yeasterday  from winetricky two was for win2005 dont rermember witch 1 was it ,will let you know.

Thank You

---

### Post by Morten ML on 2010-05-29
Well lets see if i am of any help at all before the thankyouing begins ;)

Looking at:
> Linux kron-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux it seems you are running 64 bit.

I am still a bit (pond intended) confused though. are you trying to update the program from ubuntu/wine ? If so i recommend updating the program from windows before copying the lot to wine. I gave up tryiong to update the program from ubuntu. So for every update i have to copy the program again...

The guide i followed for installing it is this:
[HTML]http://forums.ddo.com/showthread.php?t=212618[/HTML]

And last but not least. "Ajackson" is the guy who made this possible to play in linux - so he overrules my inputs at any time.

---

### Post by ajackson on 2010-05-29
> **Morten ML said:**
> And last but not least. "Ajackson" is the guy who made this possible to play in linux - so he overrules my inputs at any time.
Not really for DDO, it works because it and LotRO do stuff in a very similar way but from what I've learnt there are some differences which can cause problems (both in-game and until fairly recently with patching).

---

### Post by Morten ML on 2010-05-29
Mister Jackson (I hope you dont mind me calling you that)

> Quote:
Not really for DDO, it works because it and LotRO do stuff in a very similar way but from what I've learnt there are some differences which can cause problems (both in-game and until fairly recently with patching).


Unless I have missed something you are just being modest. The way I see it is that nobody could get this game to work if it wasn't for your pylotro loader. So I think you deserve all the credit you can get! (maybe you should have a god char ingame or something ;) )

And if you dont mind clerifying this for me: Is it possible to update the program (DDO) from the pylotro loader?

---

### Post by upitnik on 2010-05-29
> **Morten ML said:**
> Well lets see if i am of any help at all before the thankyouing begins ;)

Looking at:
 it seems you are running 64 bit.

I am still a bit (pond intended) confused though. are you trying to update the program from ubuntu/wine ? If so i recommend updating the program from windows before copying the lot to wine. I gave up tryiong to update the program from ubuntu. So for every update i have to copy the program again...


The guide i followed for installing it is this:
[HTML]http://forums.ddo.com/showthread.php?t=212618[/HTML]And last but not least. "Ajackson" is the guy who made this possible to play in linux - so he overrules my inputs at any time.

i have only unbuntu not windows 
so i can update only form umbuntu
 only thing that left from windows system are Setup Files for DDO witch are located on other none system hard drive .

---

### Post by ajackson on 2010-05-29
> **Morten ML said:**
> Unless I have missed something you are just being modest. The way I see it is that nobody could get this game to work if it wasn't for your pylotro loader. So I think you deserve all the credit you can get! (maybe you should have a god char ingame or something ;) )
Getting LotRO working was a group effort of several people, SNy then produced a working command line launcher and I produced a GUI version, I tend to get all the praise when in truth without the initial grind working out how the login process worked and getting help from an unknown Turbine dev who opened up the patch function for us none of this would be possible. So I don't ming getting praise as long as the others who played a large part don't get ignored or forgotten.

> **Morten ML said:**
> And if you dont mind clerifying this for me: Is it possible to update the program (DDO) from the pylotro loader?
It should be, you might need to drop the patchclient.dll from LotRO in (but don't rename it), the patchclient.dll that DDO then provides does have the patching process exposed **but** it seems some people have been having problems since the Wine 1.2 rc releases, so that might be what is causing problems due to some odd regression. I advocate for Crossover Games so use that for LotRO, that is built on top of Wine 1.1.43 so if you can get a copy of Wine 1.1.43 you might have more joy and it would help confirm the issue is with the changes that have happened since that release.

---

### Post by Morten ML on 2010-05-29
> Getting LotRO working was a group effort of several people, SNy then produced a working command line launcher and I produced a GUI version, I tend to get all the praise when in truth without the initial grind working out how the login process worked and getting help from an unknown Turbine dev who opened up the patch function for us none of this would be possible. So I don't ming getting praise as long as the others who played a large part don't get ignored or forgotten.

I guess i didn't look into this good enough. I was under the (wrong) impression that this was a one man job. Offcourse the rest of the crew deserves credit too. I will see if i can find them when i have time. (Maybe you could pass on some of the praising in the meantime... Or if any of the develepors read this you should know that your work is greatly appreciated!)


And if you dont mind clerifying this for me: Is it possible to update the program (DDO) from the pylotro loader?
> It should be, you might need to drop the patchclient.dll from LotRO in (but don't rename it), the patchclient.dll that DDO then provides does have the patching process exposed but it seems some people have been having problems since the Wine 1.2 rc releases, so that might be what is causing problems due to some odd regression. I advocate for Crossover Games so use that for LotRO, that is built on top of Wine 1.1.43 so if you can get a copy of Wine 1.1.43 you might have more joy and it would help confirm the issue is with the changes that have happened since that release.

Ok. thx for clarifying that. I will look into getting it all to work under ubuntu 10.04. 

@upitnik 
so i cant help you that much right now but if you can update the game from windows (maybe you could install it in vmplayer) I think you can play it. But as stated i will look into it.

---

### Post by upitnik on 2010-05-29
Hi guys,

i have manage to start DOO finally,now have another kind of problem when i try to set in game higher resolution game crash :) but at least can get in .

anyway i did all form :
[http://forums.ddo.com/showthread.php?t=212618](http://forums.ddo.com/showthread.php?t=212618)

 plus : Second option

with that i was still haveing same problem ,then i upgraded wine 1.2rc1 to  wine 1.2rc2

now i dont know was it combination of dose two or just wine update

but after update i was able to patch game and get inside.

Thank you all for make this happen .

---

### Post by Morten ML on 2010-05-29
Your welcome. Hope you enjoy Ubuntu.

Could you play the game in high res on the same computer with windows?

I cant play the game on high res either and i think i should be able to.

---

### Post by upitnik on 2010-05-29
> **Morten ML said:**
> Your welcome. Hope you enjoy Ubuntu.

Could you play the game in high res on the same computer with windows?

I cant play the game on high res either and i think i should be able to.

it was working fine on windows in High-Res.

Now i manage to Change To high-res 1400x1050 this is highest i can get, but DDO chrashes after some time of playing 15-20 min or so.

also have 1 more question : when i start ddo it load screen with lady on  after that start loading character data i think ,usually  at that point in background is picture of pirates and i getting empty screen like it missing somekind of graphical driver ,screen look like net. and after that shows character creation/selection window.

any idea what could that be?

---

### Post by Morten ML on 2010-05-30
Unless it has something to do with post 107 in this thread i have no idea.

---

### Post by upitnik on 2010-05-31
> **Morten ML said:**
> Unless it has something to do with post 107 in this thread i have no idea.

Hi,

dint try that yet, but find out i can play at low Details for hour maybe more, think this will have to satisfied me for some time.

Thank you.

---

### Post by Brando753 on 2010-06-07
Guys Im trying to get DDO to play using the LOTRO Launcher and am now getting a black window which then crashes bringing me back to the desktop. Only info available to me.

#####Pre-Login#####
Initialising, please wait...
Available languages checked.
Fetched details from GLS data centre.
Realm list obtained.
World queue configuration read
#####After Login#####
flushing batchbuffer before/after each draw call
flushing GPU caches before/after each draw call

flushing batchbuffer before/after each draw call
flushing GPU caches before/after each draw call

flushing batchbuffer before/after each draw call

flushing GPU caches before/after each draw call

err:d3d:resource_init Out of adapter memory
err:d3d9:device_parent_CreateRenderTarget (0x14b4bc) CreateRenderTarget failed, returning 0x8876017c

*** Finished ***

What Should I do? Thanks for the help.

---

### Post by ajackson on 2010-06-07
> **Brando753 said:**
> What Should I do? Thanks for the help.
Reading the sticky at the top helps.

Wine version, graphics card/driver, etc.

Looking at the error suggests Wine is trying to use more graphics memory than you have, did you manually set how much memory you have? If so did you enter the right amount, if not try setting how much you have as it could misreporting how much is available.

---

### Post by Nettster on 2010-06-08
hey guys i'm rather a n00b at the whole wine thing same as linux in a way just been fiddling with stuff i read to get what i want to work not doing anything major really i'm only getting two errors when i try to load up DDO. the launcher is working fine, i patched the game fine, everything works that way... but the game wont load! 

i keep getting this error message: 
>  
  *** Finished ***


Any help would be greatly appreciated! thanks guys!

---

### Post by Ellsolan on 2010-06-08
Hey. I have some knowledge on how WINE works, but I keep getting a 105 error (D3D not found). I tried to use winetricks to install the d3d9 dlls, but without a result. I even deleted the .wine directory.

Here's the console output. Can somebody help me?

err:d3d9:device_parent_CreateSwapChain (0x1702a4) CreateAdditionalSwapChain failed, returning 0x8876086a
err:d3d9:device_parent_CreateSwapChain (0x1702a4) CreateAdditionalSwapChain failed, returning 0x8876086a
err:d3d9:device_parent_CreateSwapChain (0x1702a4) CreateAdditionalSwapChain failed, returning 0x8876086a
err:d3d9:device_parent_CreateSwapChain (0x1702a4) CreateAdditionalSwapChain failed, returning 0x8876086a
err:d3d9:device_parent_CreateSwapChain (0x1702a4) CreateAdditionalSwapChain failed, returning 0x8876086a
err:d3d9:device_parent_CreateSwapChain (0x1702a4) CreateAdditionalSwapChain failed, returning 0x8876086a

I'm using Mac OS X (on a macbook), with WineBottler and WINE .44, btw.

Update:
I managed to fix this error by running the game in a Virtual Desktop. But, is there any way to bypass the libgsm dependency for DDO?

Thanks,
Ellsolan

---

### Post by Brando753 on 2010-06-13
Now Im running fedora and compiled LOTRO Launcher. It loaded the video and played it but then it shows the splash screen which freezes with the attached error, 
I also noticed its not letting me patch it using the lotro pachclient giving me a rundll32 error

Ubuntu didnt get this far
Using a laptop with fedora 13 intel graphics

Output of LOTRO laucher:

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1

*** Finished ***

---

### Post by lordyosch on 2010-06-13
Wow some of you guys are brave! Writing about being a DnD player on a Linux forum. My God, in some countries you could be stoned for being so geeky.



<Lordyosch runs away, checks his ranks in hide, rolls a d20 and waits...>

---

### Post by Morten ML on 2010-06-15
> **Brando753 said:**
> Now Im running fedora and compiled LOTRO Launcher. It loaded the video and played it but then it shows the splash screen which freezes with the attached error, 
I also noticed its not letting me patch it using the lotro pachclient giving me a rundll32 error

Ubuntu didnt get this far
Using a laptop with fedora 13 intel graphics

Output of LOTRO laucher:

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
[...]

*** Finished ***

Google and you shall find:
[HTML]http://ubuntuforums.org/archive/index.php/t-457268.html[/HTML]

but for the lazy reader:
> **sparkster666 said:**
> 
I have also tried this


These crashes happens cause of sound (yes...), so :

1) In winecfg :

Tick OSS (only)

Tick "Emulate"

use "Basic" "8000Hz" "8 Bit"

Dont know if it works... Let us now.

---

### Post by Brando753 on 2010-06-16
> Dont know if it works... Let us now.
I dont have an OSS option so I unselected all the options and set all the other settings to no avail. Also need to find a way to patch. the files should be up to date but still that wont last long. Im using a book 13 updater I found on the net.

---

### Post by Mosskins on 2010-06-19
Hello!! Okay 'new person' with linux and wine here. 

After about give or take a week of tinkering and frustration, I've finally got the game and the launcher to work. But I can't seem to get it updated. 

I got my brother, who has just a little more experience than I do, and after a couple hours of tedious work, he gave up. 

We are both sure we followed the 'how to' on WineHQ word for word and then some.... but it will not patch.

We have either of the following errors;

```

 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 *** Finished ***

```or


```



err:rundll32:wWinMain Unable to load L"patchclientl.dll"
 
 err:rundll32:wWinMain Unable to load L"patchclientl.dll"
 
 err:rundll32:wWinMain Unable to load L"patchclientl.dll"
 
 *** Finished ***

```
If you could offer any help I would greatly appreciate it. 



I run a ubuntu karmic 9.10 and only that.

---

### Post by ajackson on 2010-06-19
> **Mosskins said:**
> We have either of the following errors;

```

 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 *** Finished ***

```
As you were told in your other thread asking the same question, you need to get a copy of patchclient.dll from LotRO or a later DDO, a link was given [http://www.mediafire.com/?idnitkd5tyw](http://www.mediafire.com/?idnitkd5tyw) and drop that into your game directory. There is no need to rename it as it will get replaced with the newest version anyway.

> **Mosskins said:**
> or
```

err:rundll32:wWinMain Unable to load L"patchclientl.dll"
 err:rundll32:wWinMain Unable to load L"patchclientl.dll"
 err:rundll32:wWinMain Unable to load L"patchclientl.dll"
 *** Finished ***

```

You've typed the name patchclientl.dll into the options box in PyLotRO, the correct name is patchclient.dll.

---

### Post by Mosskins on 2010-06-20
> As you were told in your other thread asking the same question, you need to get a copy of patchclient.dll from LotRO or a later DDO, a link was given [http://www.mediafire.com/?idnitkd5tyw](http://www.mediafire.com/?idnitkd5tyw) and drop that into your game directory. There is no need to rename it as it will get replaced with the newest version anyway.I know that I need to get a copy of the patch client. And I also mentioned in that thread that I used the patchclient and it *still* did not work.

I downloaded the link that you gave me and it's giving me the same 'can't find entry point.' 

At this point, my guess as to what I am doing wrong is that I must be putting it in the wrong place.(Even though I put it where the old patchclient was)

I'm going to spend some more time trying to get it to work... I think that it won't either way because I've thoroughly confused myself. 


> You've typed the name patchclientl.dll into the options box in PyLotRO, the correct name is patchclient.dll.           That's not a typo. I was told to rename it. That's what I chose. 

But you said in your post that I don't need to rename it.. so I won't try that again. (Didn't quite understand why I needed to rename it in the first place)

---

### Post by ajackson on 2010-06-20
> **Mosskins said:**
> I know that I need to get a copy of the patch client. And I also mentioned in that thread that I used the patchclient and it *still* did not work.

I downloaded the link that you gave me and it's giving me the same 'can't find entry point.' 

At this point, my guess as to what I am doing wrong is that I must be putting it in the wrong place.(Even though I put it where the old patchclient was)
The new patchclient.dll goes in the game directory, the one with dndclient.exe in it.

> **Mosskins said:**
> But you said in your post that I don't need to rename it.. so I won't try that again. (Didn't quite understand why I needed to rename it in the first place)
Because up until recently DDOs patchclient didn't have the patch function exposed, so the first thing it did was download a version of patchclient that would no longer patch (using PyLotRO).

---

### Post by Brando753 on 2010-06-23
Im still running into the rundll32 error. Even using the patchclient.dll you provided, anyone know what to do?

Info available from my previous post as none of it has changed.

---

### Post by ajackson on 2010-06-23
> **Brando753 said:**
> Im still running into the rundll32 error. Even using the patchclient.dll you provided, anyone know what to do?

Info available from my previous post as none of it has changed.
I don't see a rundll32 error in your previous posts, I see mention of one but no error also unless you provide specifics about what you've done so far then troubleshooting is virtually impossible.

---

### Post by xurtik on 2010-06-29
my problem is when i try to patch the game in order to play i get this. 


err:rundll32:wWinMain Unable to load L"lotropatcher.dll"

err:rundll32:wWinMain Unable to load L"lotropatcher.dll"

err:rundll32:wWinMain Unable to load L"lotropatcher.dll"

*** Finished ***

any help is welcome

---

### Post by Brando753 on 2010-07-09
Well I recorded the problem and all logs, Both patching and running do not work :( , but i'm getting close.

had to upload them to deposit files since it was to big to upload to the forums sorry.

[http://depositfiles.com/files/klstclfx5](http://depositfiles.com/files/klstclfx5)

---

### Post by ajackson on 2010-07-09
> **Brando753 said:**
> Well I recorded the problem and all logs, Both patching and running do not work :( , but i'm getting close.

had to upload them to deposit files since it was to big to upload to the forums sorry.

[http://depositfiles.com/files/klstclfx5](http://depositfiles.com/files/klstclfx5)

You are using wine 1.1.38, that is a very, very old version and a lot of improvements have happened since then see [http://www.winehq.org/download](http://www.winehq.org/download) for how to get an up to date version for your distro.

---

### Post by Brando753 on 2010-07-09
Almost There, 
After upgrading wine I was able to patch lots of files. When I ran the game it said I wasnt using the current version of the client. Went back to patch and found these few files where running into problems. 

Again want to thank you for all your help
Here is the output:

```
Connecting to patch.ddo.com:80

Checking files...
files to patch: 14 bytes to download: 7158712

Patching files:

Downloading AxInterop.SHDocVw.dll
 Failed!

Failed to download files: E_ACCESSDENIED(0x80070005)

wine client error:1b: write: Bad file descriptor

Connecting to patch.ddo.com:80

Checking files...
files to patch: 14 bytes to download: 7158712

Patching files:

Downloading AxInterop.SHDocVw.dll
 Failed!
Failed to download files: E_ACCESSDENIED(0x80070005)

wine client error:1f: write: Bad file descriptor

Connecting to patch.ddo.com:80

checking data...
data patches: 0 bytes to download: 0

Patching data:



wine client error:23: write: Bad file descriptor

*** Finished ***
```

---

### Post by asdfoo on 2010-07-09
which version of Wine are you using now? open a terminal and type 'wine --version'

it should print wine-1.2-rc7

If the installation failed previously, I suggest you start right from the beginning as it may have confused itself having crashed midway.


All your application data is stored under your wine prefix which is in a folder named '.wine' in your home directory.  To start fresh, you either need to move or remove this.  Removing will delete all your previously installed programs in Wine.

to move:  mv .wine .wine-old

With the latest version of Wine at hand, I suggest you download the latest version of the client and start installing again.

---

### Post by Brando753 on 2010-07-09
> **asdfoo said:**
> which version of Wine are you using now? open a terminal and type 'wine --version'

it should print wine-1.2-rc7

If the installation failed previously, I suggest you start right from the beginning as it may have confused itself having crashed midway.


All your application data is stored under your wine prefix which is in a folder named '.wine' in your home directory.  To start fresh, you either need to move or remove this.  Removing will delete all your previously installed programs in Wine.

to move:  mv .wine .wine-old

With the latest version of Wine at hand, I suggest you download the latest version of the client and start installing again.

[brandon@Brandon-fedora ~]$ wine --version
wine-1.2-rc6


What do you mean download the latest version of the client? ddo I had to copy from a windows user because the installer dosen't work, i just upgraded wine, and pylotro I compiled from the latest source.

---

### Post by Brando753 on 2010-07-11
Sorry to bump but I am so close to getting this working :( Any suggestions?

Thanks, so Much

---

### Post by ajackson on 2010-07-11
I assume you read the error you were getting
```
Failed to download files: E_ACCESSDENIED(0x80070005)

```
And checked the file permissions on the files in the game directory, if you have copied from Windows you could well have made the files read-only, thus when trying to overwrite you get an access denied error message.

---

### Post by Brando753 on 2010-07-11
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256


Well, I got it working
Now I wish to thank ajackson, and everyone else who has helped me get this game running. Now I still cant play it in Ubuntu cause I get a game error 129, However in Fedora 13 it seems to play fine. If any of you play in Agronnessen let me know I just created a new toon "Brandotwo" . I feel linux users should form a guild with at least one toon for this, let me know if there already is one . Thanks once again for all the help.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.10 (GNU/Linux)

iF4EAREIAAYFAkw6iUgACgkQt41FdDFbejP9CgEArpnEuWK2bzt8svIbGIB/ozUp
+10JZaxsabH0BNXQHsUBAKrJR6ICEvtOBf4xNq+I8gsXMi+Lg6os9AFoxuUjYuc3
=mz7A
-----END PGP SIGNATURE-----

---

### Post by d.oberry on 2010-07-13
i have been reading EVERY forum about getting ddo installed and running and have done quite well, thax to the hard work of those answering the questions of us noobs.  however, i have run into something that i have not been able to understand (consequently not been able to look up!) and would like your help.  the following is what i get when i try to start the game (install worked, update worked and everything else too)  i have uploaded it as a .txt file because it is so long.  if you have any questions or need more info, just let me know and i will get it for you!

thx in advance!

---

### Post by Brando753 on 2010-07-13
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256


Alright now im eating my words . So I got the game running, It patches fine, I can play in the safe area's (Harbor, Marketplace) but when I enter a dungeon the second a monster attacks me the game freezes and forces me to restart the computer, Any Ideas on what I can do, and is there a setting to get pylotro to write its logs without me hitting save as once it crashes I can't access it. Any Help much appreciated, I WAS SOOOO CLOSE
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.10 (GNU/Linux)

iF4EAREIAAYFAkw852AACgkQt41FdDFbejMoSQEAlASu3ptPrMd0kSHeviqIQfG4
QashuC1gglNqvls38+4BAKeJzaDQ3Q5ccgsqlqWSGj1PpTvBdrM21gcmnvp+4X0w
=G2sP
-----END PGP SIGNATURE-----

---

### Post by d.oberry on 2010-07-15
ok have found out that pylotro does work on my system but that ddo has a problem with me.  my earlier post is still not answered and i would really like to know what ddo-folks say about it.  please read the attached .txt file to find out what the problem is.  

could there be a problem with the fact that i am using GSM to get into the internet?  would that cause ddo to not want me to connect?  otherwise my system exceeds all the normal parameters needed to run the game.  i am also not using an ATI video card, so i cannot really understand what is happening.  

thx in advance

---

### Post by Brando753 on 2010-07-22
1 week bump, Just checking to see if anyone knows whats wrong.
Thanks ):P

---

### Post by salemboot on 2010-07-25
Mine don't even make it the login screen no more and I pretty much did what I suggested in my script on page 7.

edit : [http://www.mediafire.com/?ljmtw12eun2](http://www.mediafire.com/?ljmtw12eun2)  Need the lastest patchclient.dll

---

### Post by vuroth on 2010-08-01
Followed the winehq entry.  Patched ok the first time.  Fails to run with:

> err:module:import_dll Library umbra.dll (which is needed by L"C:\\Program Files\\Turbine\\Dungeons & Dragons Online - Stormreach\\dndclient.exe") not found

err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Turbine\\Dungeons & Dragons Online - Stormreach\\dndclient.exe" failed, status c0000135

*** Finished ***

Repatching fails with

> rundll32.exe lotropatcher.dll,Patch patch.ddo.com:80 --language ENGLISH --productcode DDO --filesonly
Connecting to patch.ddo.com:80

Checking files...
files to patch: 6 bytes to download: 2565120
Patching files:

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1007241319/all/en/DDO EULA - Turbine.rtf") (-2147467261)

Failed!

 Failed!

Failed to download files: OES_E_HTTP_STATUS_BAD_REQUEST(0x80044190)

Connecting to patch.ddo.com:80

Checking files...
files to patch: 6 bytes to download: 2565120
Patching files:

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1007241319/all/en/DDO EULA - Turbine.rtf") (-2147467261)

Failed!

 Failed!

Failed to download files: OES_E_HTTP_STATUS_BAD_REQUEST(0x80044190)

Connecting to patch.ddo.com:80

checking data...
data patches: 0 bytes to download: 0
Patching data:



*** Finished ***

wine 1.2

---

### Post by BeWop on 2010-08-10
I'm trying to get this to work with my pretty crappy box. I have an intel GMA 3150 card, and so I don't know if it will. I've been searching forums and such for the past four hours, and just can't seem to find what's wrong. I followed many guides, and yet it still just crashes after start. I installed driconf and all that.

Basically, I get a black screen for a few seconds, and then it crashes, the log says ****finished***** 

Can anyone help me with this?

---

### Post by Ferrat on 2010-08-10
> **BeWop said:**
> I'm trying to get this to work with my pretty crappy box. I have an intel GMA 3150 card, and so I don't know if it will. I've been searching forums and such for the past four hours, and just can't seem to find what's wrong. I followed many guides, and yet it still just crashes after start. I installed driconf and all that.

Basically, I get a black screen for a few seconds, and then it crashes, the log says ****finished***** 

Can anyone help me with this?

Intel cards tends to preform extremely bad under Linux, not sure about your card but mostly getting it 3D games running with a Intel card is a real pain and you usually get bad results :/

---

### Post by BeWop on 2010-08-12
> **Ferrat said:**
> Intel cards tends to preform extremely bad under Linux, not sure about your card but mostly getting it 3D games running with a Intel card is a real pain and you usually get bad results :/

Most of the games that I've run have actually been better in linux, which I blame driconf for fixing. Knights of the Old Republic is an example.

I don't really care all too much about performance, as long as it's playable I'm good. I don't want to dual boot anymore.

---

### Post by articanos on 2010-08-24
Ok, great news for all Intel graphics users, there is a workaround for the game error 129 hardware texture compression was not detected. After days of banging my head against a wall I found a solution! Go into your administration => software sources => check multiverse. Now go back into administration => synaptic package manager, once there type in Driconf. Check it and allow it to install. Next open a terminal and type Driconf, a nice gui will appear. Click on the tab labeled image quality, ensure "Enable S3TC texture compression even if software support is not available" is clicked to yes. Then fire up DDO from pylotro and play.

---

### Post by Drakmor on 2010-09-09
> **articanos said:**
> Ok, great news for all Intel graphics users, there is a workaround for the game error 129 hardware texture compression was not detected. After days of banging my head against a wall I found a solution! Go into your administration => software sources => check multiverse. Now go back into administration => synaptic package manager, once there type in Driconf. Check it and allow it to install. Next open a terminal and type Driconf, a nice gui will appear. Click on the tab labeled image quality, ensure "Enable S3TC texture compression even if software support is not available" is clicked to yes. Then fire up DDO from pylotro and play.

So, I stumbled across this earlier today, and was excited to try it! However, once I turn on texture compression, I don't get the error, but DDO still dies after starting, e.g black screen, then end. Anyone?

Edit: got some debug info:

```
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
  
fixme:win:EnumDisplayDevicesW ((null),0,0x33f55c,0x00000000), stub!
  
fixme:wbemprox:wbem_locator_ConnectServer 0x13d540, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x33fa54)
  
fixme:wbemprox:wbem_locator_ConnectServer 0x13d0b8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x33fa54)
  
fixme:wbemprox:wbem_locator_ConnectServer 0x13d0b8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x33faa8)
  
fixme:advapi:RegisterTraceGuidsW (0x36b24d0, 0x36bd6e8, {7c830ece-5fb3-417a-a1bd-508f45277356}, 1, 0x1d6e724, (null), (null), 0x36bd6f0,)
  
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
  
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
 fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
 fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
  
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x149a90) : stub
  
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode Dialogs cannot be disabled yet.
  
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x2005a 0x00000000
  
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x213b98,0x213a98): stub
  
*** Finished ***

```Also, I'm running kubuntu 10.04 with a system that is mid range, other than the sucky graphics card.

---

### Post by casacerian on 2010-10-11
> **d.oberry said:**
> i have been reading EVERY forum about getting ddo installed and running and have done quite well, thax to the hard work of those answering the questions of us noobs.  however, i have run into something that i have not been able to understand (consequently not been able to look up!) and would like your help.  the following is what i get when i try to start the game (install worked, update worked and everything else too)  i have uploaded it as a .txt file because it is so long.  if you have any questions or need more info, just let me know and i will get it for you!

thx in advance!

I am returning to DDO on Ubuntu, and this same issue is popping up for me.

This is said error report...
[HTML]rundll32.exe ddopatchclient.dll,Patch patch.ddo.com:80 --language ENGLISH --productcode DDO --filesonly
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e6b8e65 (thread 0009), starting debugger...

Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e6b8e65).

Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e6b8e65 ESP:0032fca0 EBP:0032fce8 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:7e6fd0f4 EBX:7e6f5ff4 ECX:7e6f5ff4 EDX:00000010
 ESI:00000000 EDI:00000000
Stack dump:

0x0032fca0:  0032fcdc 000000a9 00128e58 00000006
0x0032fcb0:  00000000 7eff7ff4 10000000 0032fcdc
0x0032fcc0:  00128e50 00000000 10000000 00000010
0x0032fcd0:  00000000 00110014 00126358 7eff7ff4
0x0032fce0:  00126358 10004bb0 0032fde0 10004bbb
0x0032fcf0:  10040734 7eff5cd5 0002005a 7eff0000
Backtrace:
=>0 0x7e6b8e65 _wgetenv+0x45() in msvcrt (0x0032fce8)
  1 0x10004bbb in ddopatchclient (+0x4bba) (0x0032fde0)
  2 0x7eff6591 wmain+0xb0() in rundll32 (0x0032fe60)
  3 0x7eff64d2 in rundll32 (+0x64d1) (0x0032fe90)
  4 0x7b8565fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85729f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc726d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75240 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a60a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)

0x7e6b8e65 _wgetenv+0x45 in msvcrt: movl	0x0(%edi),%ecx
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  330000-  342000	Deferred        zlib1t
PE	10000000-100a3000	Export          ddopatchclient
ELF	7b800000-7b976000	Export          kernel32<elf>
  \-PE	7b810000-7b976000	\               kernel32
ELF	7bc00000-7bcba000	Export          ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e065000-7e165000	Deferred        ole32<elf>
  \-PE	7e080000-7e165000	\               ole32
ELF	7e165000-7e199000	Deferred        uxtheme<elf>
  \-PE	7e170000-7e199000	\               uxtheme
ELF	7e199000-7e22e000	Deferred        winmm<elf>
  \-PE	7e1a0000-7e22e000	\               winmm
ELF	7e22e000-7e25e000	Deferred        ws2_32<elf>
  \-PE	7e240000-7e25e000	\               ws2_32
ELF	7e25e000-7e34d000	Deferred        comctl32<elf>
  \-PE	7e270000-7e34d000	\               comctl32
ELF	7e34d000-7e538000	Deferred        shell32<elf>
  \-PE	7e360000-7e538000	\               shell32
ELF	7e538000-7e59a000	Deferred        shlwapi<elf>
  \-PE	7e550000-7e59a000	\               shlwapi
ELF	7e59a000-7e5bd000	Deferred        mpr<elf>
  \-PE	7e5a0000-7e5bd000	\               mpr
ELF	7e5bd000-7e61b000	Deferred        wininet<elf>
  \-PE	7e5d0000-7e61b000	\               wininet
ELF	7e61b000-7e68f000	Deferred        rpcrt4<elf>
  \-PE	7e630000-7e68f000	\               rpcrt4
ELF	7e68f000-7e712000	Export          msvcrt<elf>
  \-PE	7e6a0000-7e712000	\               msvcrt
ELF	7e712000-7e731000	Deferred        msvcr71<elf>
  \-PE	7e720000-7e731000	\               msvcr71
ELF	7e796000-7e7a0000	Deferred        libxcursor.so.1
ELF	7e7a0000-7e7a6000	Deferred        libxfixes.so.3
ELF	7e7a6000-7e7aa000	Deferred        libxcomposite.so.1
ELF	7e7aa000-7e7b2000	Deferred        libxrandr.so.2
ELF	7e7b2000-7e7bc000	Deferred        libxrender.so.1
ELF	7e7bc000-7e7c2000	Deferred        libxxf86vm.so.1
ELF	7e7c2000-7e7c6000	Deferred        libxinerama.so.1
ELF	7e7c6000-7e7e7000	Deferred        imm32<elf>
  \-PE	7e7d0000-7e7e7000	\               imm32
ELF	7e7e7000-7e7ed000	Deferred        libxdmcp.so.6
ELF	7e7ed000-7e7f1000	Deferred        libxau.so.6
ELF	7e7f1000-7e80b000	Deferred        libxcb.so.1
ELF	7e80b000-7e810000	Deferred        libuuid.so.1
ELF	7e810000-7e92d000	Deferred        libx11.so.6
ELF	7e92d000-7e93d000	Deferred        libxext.so.6
ELF	7e93d000-7e956000	Deferred        libice.so.6
ELF	7e956000-7e95f000	Deferred        libsm.so.6
ELF	7e97e000-7ea24000	Deferred        winex11<elf>
  \-PE	7e990000-7ea24000	\               winex11
ELF	7ea59000-7ea80000	Deferred        libexpat.so.1
ELF	7ea80000-7eab0000	Deferred        libfontconfig.so.1
ELF	7eab0000-7eac5000	Deferred        libz.so.1
ELF	7eac5000-7eb3c000	Deferred        libfreetype.so.6
ELF	7eb5b000-7eb74000	Deferred        version<elf>
  \-PE	7eb60000-7eb74000	\               version
ELF	7eb74000-7ebce000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebce000	\               advapi32
ELF	7ebce000-7ec5a000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec5a000	\               gdi32
ELF	7ec5a000-7ed8d000	Deferred        user32<elf>
  \-PE	7ec70000-7ed8d000	\               user32
ELF	7ef8d000-7ef99000	Deferred        libnss_files.so.2
ELF	7ef99000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efe4000-7eff9000	Export          rundll32<elf>
  \-PE	7eff0000-7eff9000	\               rundll32
ELF	f7446000-f744a000	Deferred        libdl.so.2
ELF	f744a000-f75a4000	Deferred        libc.so.6
ELF	f75a5000-f75be000	Deferred        libpthread.so.0
ELF	f75d5000-f75dd000	Deferred        libnss_compat.so.2
ELF	f75dd000-f771d000	Export          libwine.so.1
ELF	f771f000-f773d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\rundll32.exe
	00000009    0 <==
0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
Backtrace:
=>0 0x7e6b8e65 _wgetenv+0x45() in msvcrt (0x0032fce8)
  1 0x10004bbb in ddopatchclient (+0x4bba) (0x0032fde0)
  2 0x7eff6591 wmain+0xb0() in rundll32 (0x0032fe60)
  3 0x7eff64d2 in rundll32 (+0x64d1) (0x0032fe90)
  4 0x7b8565fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85729f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc726d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75240 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a60a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)

wine: Unhandled page fault on read access to 0x00000000 at address 0x7e6bce65 (thread 0020), starting debugger...

Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e6bce65).

Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e6bce65 ESP:0032fca0 EBP:0032fce8 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:7e7010f4 EBX:7e6f9ff4 ECX:7e6f9ff4 EDX:00000010
 ESI:00000000 EDI:00000000
Stack dump:

0x0032fca0:  0032fcdc 000000a9 00128e58 00000006
0x0032fcb0:  00000000 7effeff4 10000000 0032fcdc
0x0032fcc0:  00128e50 00000000 10000000 00000010
0x0032fcd0:  00000000 00110014 00126358 7effeff4
0x0032fce0:  00126358 10004bb0 0032fde0 10004bbb
0x0032fcf0:  10040734 7effccd5 00030028 7eff0000
Backtrace:
=>0 0x7e6bce65 _wgetenv+0x45() in msvcrt (0x0032fce8)
  1 0x10004bbb in ddopatchclient (+0x4bba) (0x0032fde0)
  2 0x7effd591 wmain+0xb0() in rundll32 (0x0032fe60)
  3 0x7effd4d2 in rundll32 (+0xd4d1) (0x0032fe90)
  4 0x7b8565fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85729f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc726d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75240 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a60a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
0x7e6bce65 _wgetenv+0x45 in msvcrt: movl	0x0(%edi),%ecx
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  330000-  342000	Deferred        zlib1t
PE	10000000-100a3000	Export          ddopatchclient
ELF	7b800000-7b976000	Export          kernel32<elf>
  \-PE	7b810000-7b976000	\               kernel32
ELF	7bc00000-7bcba000	Export          ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e069000-7e169000	Deferred        ole32<elf>
  \-PE	7e080000-7e169000	\               ole32
ELF	7e169000-7e19d000	Deferred        uxtheme<elf>
  \-PE	7e170000-7e19d000	\               uxtheme
ELF	7e19d000-7e232000	Deferred        winmm<elf>
  \-PE	7e1a0000-7e232000	\               winmm
ELF	7e232000-7e262000	Deferred        ws2_32<elf>
  \-PE	7e240000-7e262000	\               ws2_32
ELF	7e262000-7e351000	Deferred        comctl32<elf>
  \-PE	7e270000-7e351000	\               comctl32
ELF	7e351000-7e53c000	Deferred        shell32<elf>
  \-PE	7e360000-7e53c000	\               shell32
ELF	7e53c000-7e59e000	Deferred        shlwapi<elf>
  \-PE	7e550000-7e59e000	\               shlwapi
ELF	7e59e000-7e5c1000	Deferred        mpr<elf>
  \-PE	7e5a0000-7e5c1000	\               mpr
ELF	7e5c1000-7e61f000	Deferred        wininet<elf>
  \-PE	7e5d0000-7e61f000	\               wininet
ELF	7e61f000-7e693000	Deferred        rpcrt4<elf>
  \-PE	7e630000-7e693000	\               rpcrt4
ELF	7e693000-7e716000	Export          msvcrt<elf>
  \-PE	7e6a0000-7e716000	\               msvcrt
ELF	7e716000-7e735000	Deferred        msvcr71<elf>
  \-PE	7e720000-7e735000	\               msvcr71
ELF	7e79a000-7e7a4000	Deferred        libxcursor.so.1
ELF	7e7a4000-7e7aa000	Deferred        libxfixes.so.3
ELF	7e7aa000-7e7ae000	Deferred        libxcomposite.so.1
ELF	7e7ae000-7e7b6000	Deferred        libxrandr.so.2
ELF	7e7b6000-7e7c0000	Deferred        libxrender.so.1
ELF	7e7c0000-7e7c6000	Deferred        libxxf86vm.so.1
ELF	7e7c6000-7e7ca000	Deferred        libxinerama.so.1
ELF	7e7ca000-7e7eb000	Deferred        imm32<elf>
  \-PE	7e7d0000-7e7eb000	\               imm32
ELF	7e7eb000-7e7f1000	Deferred        libxdmcp.so.6
ELF	7e7f1000-7e7f5000	Deferred        libxau.so.6
ELF	7e7f5000-7e80f000	Deferred        libxcb.so.1
ELF	7e80f000-7e814000	Deferred        libuuid.so.1
ELF	7e814000-7e931000	Deferred        libx11.so.6
ELF	7e931000-7e941000	Deferred        libxext.so.6
ELF	7e941000-7e95a000	Deferred        libice.so.6
ELF	7e95a000-7e963000	Deferred        libsm.so.6
ELF	7e982000-7ea28000	Deferred        winex11<elf>
  \-PE	7e990000-7ea28000	\               winex11
ELF	7ea59000-7ea80000	Deferred        libexpat.so.1
ELF	7ea80000-7eab0000	Deferred        libfontconfig.so.1
ELF	7eab0000-7eac5000	Deferred        libz.so.1
ELF	7eac5000-7eb3c000	Deferred        libfreetype.so.6
ELF	7eb5b000-7eb74000	Deferred        version<elf>
  \-PE	7eb60000-7eb74000	\               version
ELF	7eb74000-7ebce000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebce000	\               advapi32
ELF	7ebce000-7ec5a000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec5a000	\               gdi32
ELF	7ec5a000-7ed8d000	Deferred        user32<elf>
  \-PE	7ec70000-7ed8d000	\               user32
ELF	7ef8d000-7ef99000	Deferred        libnss_files.so.2
ELF	7ef99000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efeb000-7f000000	Export          rundll32<elf>
  \-PE	7eff0000-7f000000	\               rundll32
ELF	f7409000-f740d000	Deferred        libdl.so.2
ELF	f740d000-f7567000	Deferred        libc.so.6
ELF	f7568000-f7581000	Deferred        libpthread.so.0
ELF	f7588000-f7590000	Deferred        libnss_compat.so.2
ELF	f75a0000-f76e0000	Export          libwine.so.1
ELF	f76e2000-f7700000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0

00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
0000001f (D) C:\windows\system32\rundll32.exe
	00000020    0 <==
Backtrace:
=>0 0x7e6bce65 _wgetenv+0x45() in msvcrt (0x0032fce8)
  1 0x10004bbb in ddopatchclient (+0x4bba) (0x0032fde0)
  2 0x7effd591 wmain+0xb0() in rundll32 (0x0032fe60)
  3 0x7effd4d2 in rundll32 (+0xd4d1) (0x0032fe90)
  4 0x7b8565fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85729f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc726d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75240 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a60a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)

wine: Unhandled page fault on read access to 0x00000000 at address 0x7e6bde65 (thread 0024), starting debugger...

Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e6bde65).

Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e6bde65 ESP:0032fca0 EBP:0032fce8 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:7e7020f4 EBX:7e6faff4 ECX:7e6faff4 EDX:00000010
 ESI:00000000 EDI:00000000
Stack dump:

0x0032fca0:  0032fcdc 000000a9 00128e58 00000006

0x0032fcb0:  00000000 7effeff4 10000000 0032fcdc

0x0032fcc0:  00128e50 00000000 10000000 00000010

0x0032fcd0:  00000000 00110014 00126358 7effeff4

0x0032fce0:  00126358 10004bb0 0032fde0 10004bbb

0x0032fcf0:  10040734 7effccd5 00040020 7eff0000

Backtrace:
=>0 0x7e6bde65 _wgetenv+0x45() in msvcrt (0x0032fce8)
  1 0x10004bbb in ddopatchclient (+0x4bba) (0x0032fde0)
  2 0x7effd591 wmain+0xb0() in rundll32 (0x0032fe60)
  3 0x7effd4d2 in rundll32 (+0xd4d1) (0x0032fe90)
  4 0x7b8565fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85729f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc726d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75240 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a60a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
0x7e6bde65 _wgetenv+0x45 in msvcrt: movl	0x0(%edi),%ecx
Modules:

Module	Address			Debug info	Name (74 modules)
PE	  330000-  342000	Deferred        zlib1t
PE	10000000-100a3000	Export          ddopatchclient
ELF	7b800000-7b976000	Export          kernel32<elf>
  \-PE	7b810000-7b976000	\               kernel32
ELF	7bc00000-7bcba000	Export          ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e06a000-7e16a000	Deferred        ole32<elf>
  \-PE	7e080000-7e16a000	\               ole32
ELF	7e16a000-7e19e000	Deferred        uxtheme<elf>
  \-PE	7e170000-7e19e000	\               uxtheme
ELF	7e19e000-7e233000	Deferred        winmm<elf>
  \-PE	7e1b0000-7e233000	\               winmm
ELF	7e233000-7e263000	Deferred        ws2_32<elf>
  \-PE	7e240000-7e263000	\               ws2_32
ELF	7e263000-7e352000	Deferred        comctl32<elf>
  \-PE	7e270000-7e352000	\               comctl32
ELF	7e352000-7e53d000	Deferred        shell32<elf>
  \-PE	7e360000-7e53d000	\               shell32
ELF	7e53d000-7e59f000	Deferred        shlwapi<elf>
  \-PE	7e550000-7e59f000	\               shlwapi
ELF	7e59f000-7e5c2000	Deferred        mpr<elf>
  \-PE	7e5b0000-7e5c2000	\               mpr
ELF	7e5c2000-7e620000	Deferred        wininet<elf>
  \-PE	7e5d0000-7e620000	\               wininet
ELF	7e620000-7e694000	Deferred        rpcrt4<elf>
  \-PE	7e630000-7e694000	\               rpcrt4
ELF	7e694000-7e717000	Export          msvcrt<elf>
  \-PE	7e6a0000-7e717000	\               msvcrt
ELF	7e717000-7e736000	Deferred        msvcr71<elf>
  \-PE	7e720000-7e736000	\               msvcr71
ELF	7e79b000-7e7a5000	Deferred        libxcursor.so.1
ELF	7e7a5000-7e7ab000	Deferred        libxfixes.so.3
ELF	7e7ab000-7e7af000	Deferred        libxcomposite.so.1
ELF	7e7af000-7e7b7000	Deferred        libxrandr.so.2
ELF	7e7b7000-7e7c1000	Deferred        libxrender.so.1
ELF	7e7c1000-7e7c7000	Deferred        libxxf86vm.so.1
ELF	7e7c7000-7e7cb000	Deferred        libxinerama.so.1
ELF	7e7cb000-7e7ec000	Deferred        imm32<elf>
  \-PE	7e7d0000-7e7ec000	\               imm32
ELF	7e7ec000-7e7f2000	Deferred        libxdmcp.so.6
ELF	7e7f2000-7e7f6000	Deferred        libxau.so.6
ELF	7e7f6000-7e810000	Deferred        libxcb.so.1
ELF	7e810000-7e815000	Deferred        libuuid.so.1
ELF	7e815000-7e932000	Deferred        libx11.so.6
ELF	7e932000-7e942000	Deferred        libxext.so.6
ELF	7e942000-7e95b000	Deferred        libice.so.6
ELF	7e95b000-7e964000	Deferred        libsm.so.6
ELF	7e983000-7ea29000	Deferred        winex11<elf>
  \-PE	7e990000-7ea29000	\               winex11
ELF	7ea59000-7ea80000	Deferred        libexpat.so.1
ELF	7ea80000-7eab0000	Deferred        libfontconfig.so.1
ELF	7eab0000-7eac5000	Deferred        libz.so.1
ELF	7eac5000-7eb3c000	Deferred        libfreetype.so.6
ELF	7eb5b000-7eb74000	Deferred        version<elf>
  \-PE	7eb60000-7eb74000	\               version
ELF	7eb74000-7ebce000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebce000	\               advapi32
ELF	7ebce000-7ec5a000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec5a000	\               gdi32
ELF	7ec5a000-7ed8d000	Deferred        user32<elf>
  \-PE	7ec70000-7ed8d000	\               user32
ELF	7ef8d000-7ef99000	Deferred        libnss_files.so.2
ELF	7ef99000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efeb000-7f000000	Export          rundll32<elf>
  \-PE	7eff0000-7f000000	\               rundll32
ELF	f74da000-f74de000	Deferred        libdl.so.2
ELF	f74de000-f7638000	Deferred        libc.so.6
ELF	f7639000-f7652000	Deferred        libpthread.so.0
ELF	f7658000-f7660000	Deferred        libnss_compat.so.2
ELF	f7671000-f77b1000	Export          libwine.so.1
ELF	f77b3000-f77d1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)

0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
00000023 (D) C:\windows\system32\rundll32.exe
	00000024    0 <==
Backtrace:
=>0 0x7e6bde65 _wgetenv+0x45() in msvcrt (0x0032fce8)
  1 0x10004bbb in ddopatchclient (+0x4bba) (0x0032fde0)
  2 0x7effd591 wmain+0xb0() in rundll32 (0x0032fe60)
  3 0x7effd4d2 in rundll32 (+0xd4d1) (0x0032fe90)
  4 0x7b8565fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85729f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc726d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75240 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a60a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)

*** Finished ***[/HTML]

---

### Post by casacerian on 2010-10-12
Late edit. I should perhaps note some system specs.

AMD 64 X2 4800; 4 GB RAM; Nvidia 9600 GT 512 vid mem

Wine version 1.3 (latest test version)

---

### Post by rotty3000 on 2010-10-21
I'd been playing ddo on 10.04 since June with no problems. Unfortunately the latest update has somehow broken it.

I used pylotro to patch it (as I always have with no problems).

I'm using a dell xps (i7-920, 1GB Nvidea), which rocks btw.

After the update I was getting the MSCVR80.DLL load error again (although I had not changed my env since june).

So, I proceeded to setup a new win prefix, and copied the installed game back to it. All in added was the "winetricks vcrun2005sp1 vcrun2005" which inited the new .wine and installed the required dlls. Lastly I set the os emulation to win2k as suggested elsewhere (although I tried others after).

Now all I get is a completely black screen with the mouse visible near the middle, but it's frozen. Oddly I can escape back to the desktop, and the app closes.

It's a shame since this had been running flawlessly for months.

Thoughts?

---

### Post by taurolyon on 2010-12-04
> **rotty3000 said:**
> I'd been playing ddo on 10.04 since June with no problems. Unfortunately the latest update has somehow broken it.

I used pylotro to patch it (as I always have with no problems).

I'm using a dell xps (i7-920, 1GB Nvidea), which rocks btw.

After the update I was getting the MSCVR80.DLL load error again (although I had not changed my env since june).

So, I proceeded to setup a new win prefix, and copied the installed game back to it. All in added was the "winetricks vcrun2005sp1 vcrun2005" which inited the new .wine and installed the required dlls. Lastly I set the os emulation to win2k as suggested elsewhere (although I tried others after).

Now all I get is a completely black screen with the mouse visible near the middle, but it's frozen. Oddly I can escape back to the desktop, and the app closes.

It's a shame since this had been running flawlessly for months.

Thoughts?

I had a similar issue until I installed d3dx9 and vcrun2005 using winetricks.

---

### Post by taurolyon on 2010-12-04
I'm currently having a lock-up issue where the game will lockup after a few minutes of play, then I must force-quit it to get it to close.

I'm using the Ultra-High graphics setting, which I'm about to attempt turning that down to High and see if that delays the issue.

---

### Post by buzzmandt on 2010-12-04
you need vcrun2008 vcrun2005 and d3dx9 installed through winetricks, been working great on 4 of my 4 systems. kubuntu10.10.

I also highly recomend you be on (k)ubuntu10.10. much better graphics drivers and xorg

---

### Post by BeWop on 2010-12-30
This has probably already been addressed, but I can't find anything on it.

When using the auto-install script, this happens:
Unable to find the entry point L"Patch" in L"patchclient.dll"
When I try to patch, and it doesn't patch.

After installing and patching on windows and copying it over, I can't patch and it gives this message when I try to run it:
[IMG]http://i647.photobucket.com/albums/uu195/BeWop/Screenshot-7.png?t=1293738675[/IMG]


Thanks for the help.

---

### Post by Morten ML on 2011-03-10
> **BeWop said:**
> This has probably already been addressed, but I can't find anything on it.

When using the auto-install script, this happens:
Unable to find the entry point L"Patch" in L"patchclient.dll"
When I try to patch, and it doesn't patch.

After installing and patching on windows and copying it over, I can't patch and it gives this message when I try to run it:

Thanks for the help.

The error r6034 (added for other users to easier find it)

Idk if you allready figured this one out but anyways here is the way to fix it:
You need to copy some files from windows (XP i guess and thats what i did.)
It is all explained here:
[http://wiki.jswindle.com/index.php/General_Wine_Troubleshooting#R6034_An_Application_has_made_an_attempt_to_load_the_C_runtime_library_incorrectly]("http://wiki.jswindle.com/index.php/General_Wine_Troubleshooting#R6034_An_Application_has_made_an_attempt_to_load_the_C_runtime_library_incorrectly")

Hope this helps.

---

### Post by defis on 2011-04-05
I also have the same problem as [taurolyon]("http://ubuntuforums.org/member.php?u=1020146") . I did everything according to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785)   . I have done the easy set up. Windows version of the PyLotro (couldn't find the Linux version) and also installed it both ways (automatically and manually) but the game still crashes after a while. The screen freezes, it goes black and white (like the usual of a crashed ubuntu windows) the music keeps on playing normally,and in the end i have to force quit it.

What can i do about this? Any suggestions?

I think it doesn't matter but to click the buttons I have to click a little bit lower.

Thank you for your time.

---

### Post by defis on 2011-04-06
Hi there!
Is the game working fine for you?cause I have some issues.After a few minutes in the game, it stops and I have to force quit the game, otherwise nothing happens...
I use wine 1.2.2 and have done everything according to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785) and [http://ubuntuforums.org/showthread.php?t=1263191](http://ubuntuforums.org/showthread.php?t=1263191)   .
Thank you very much for your time...

---

### Post by taurolyon on 2011-04-06
DX11 has been spoiling me. -_-  I recently reinstalled Maverick and got the up to date kernel and ATI drivers, and will be making another attempt at this soon. With the game's next update coming out soon (Update 9), I plan to be playing this game more often.

---

### Post by defis on 2011-04-07
Ok I finally get it to play. I had to set graphics to low and very low but it's good jus like that. Now one of my friends has another problem which has already been posted but I'm not quite sure there is a solution. He tries to login, the screen turns black for a few seconds and then the game end with the usual message *finished*


Also we followed this instruction:

articanos says:
> Ok, great news for all Intel graphics users, there is a workaround for  the game error 129 hardware texture compression was not detected. After  days of banging my head against a wall I found a solution! Go into your  administration => software sources => check multiverse. Now go  back into administration => synaptic package manager, once there type  in Driconf. Check it and allow it to install. Next open a terminal and  type Driconf, a nice gui will appear. Click on the tab labeled image  quality, ensure "Enable S3TC texture compression even if software  support is not available" is clicked to yes. Then fire up DDO from  pylotro and play.

and terminal says: libGL is too old
and an error says: XDriInfo returned with non-zero code.

Any guesses would be appreciated. Thank you all...

---

### Post by buzzmandt on 2011-04-22
if it's intel graphics, install driconf
> sudo apt-get install driconf
run driconf
> driconf
2nd tab "image quality"
select yes to enable S3TC texture compression

---

### Post by Artemis3 on 2011-05-01
With update 9 released, pylotro is refusing to update... What now?

```
rundll32.exe patchclient.dll,Patch patch.ddo.com:80 --language ENGLISH --productcode DDO --filesonly --highres
Failed to create PatchClient: E_FAIL(0x80004005)

Failed to create PatchClient: E_FAIL(0x80004005)

Failed to create PatchClient: E_FAIL(0x80004005)

*** Finished ***
``` (Wine 1.3.19)

---

### Post by Morten ML on 2011-05-01
I am running wine 1.2.2 and didn't have any problem.... I named the patchclient file from book 13 patchclient.dll and the old one patchclient_OLD.dll.

Let me know if this helps.

---

### Post by Artemis3 on 2011-05-01
Weird, the update worked in another machine i have with almost identical software... Will have to investigate whats going on on the first machine.

Ok, i overwrote the newer patchclient.dll from 12/13/10 i had there with the one from book 13 again, and the patch process started, and now its working.

If this ever happens again, i'll use a different name for the file in the advanced options. I suppose my other machine had an older patchclient.dll.

BTW: I couldn't make this thing work at all with v1.2, it spitted out some silly errors about msvcr7.1 or such i didn't want to bother.

---

### Post by ajackson on 2011-05-02
> **Artemis3 said:**
> it spitted out some silly errors about msvcr7.1 or such i didn't want to bother.

Well if you don't want to bother with the errors telling where the problem might be then that is fine :)

Chances are you need to make sure that Visual C++ runtimes 2005 and 2008 are installed (probably just the latter if it used to patch ok) as Turbine changed their patching mechanism (which is why an older patchclient works).

---

### Post by Artemis3 on 2011-05-02
Its obviously working with 1.3.19, and i have vcrun 2003, 2005 and 2008 installed.

---

### Post by Morten ML on 2011-05-05
I now get the error i think artemis3 was talking about.

```
rundll32.exe patchclient.dll,Patch patch.ddo.com:80 --language ENGLISH --productcode DDO --filesonly --highres
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.

err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.

err:module:find_forwarded_export function not found for forward 'msvcrt._vscwprintf' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._vscprintf' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.

wine: Call from 0x7bc49f00 to unimplemented function MSVCR71.dll._vscprintf, aborting

err:seh:setup_exception_record stack overflow 1764 bytes in thread 001e eip 68075231 esp 00230c4c stack 0x230000-0x231000-0x330000

*** Finished ***
```

I have deleted a lot of repetetions of the same error in this post...
This error was given when i tried to  update the program / patch the program from pylotro. any help would be greatly appreciated.
I got the same error using the lates version of wine version 1.3 something. and after having deleted that version and going back to wine 1.2.2 i still get the same error...
Help would be really apreciated as i cannot play my game right now.
Best regards Morten

---

### Post by ajackson on 2011-05-05
Well MSVCR71.dll is part of Visual C++ Runtime 2003, which winetricks can install (it is a bit of a fudge install as there wasn't a redist for 2003). Sticking a real version of MSVCR71.dll into either the game directory or the system32 folder should fix that problem.

---

### Post by Jalathas on 2011-05-13
I'm running Ubuntu 11.04, running the game in wine through pylotro 0.1.14. I've  been able to get into the game, create a character, and play through the  first tutorial dungeon, but now that I'm in the town, the game's been  freezing on random loading screens. I also, despite having been told  that the game only runs in fullscreen at default resolution, managed to  crank it to fullscreen 1680x1050, which was lovely until the freeze, at  which point nothing could get it OFF the screen, up to and including  switching workspaces. Any idea how to stop the freezes, or at least  change the settings such that I don't have to reboot when they happen?

---

### Post by FrogZeke on 2011-05-14
After digging through forums here, on the ddo forums and winehq, I have not found anyone else having this issue.  When attempting interact with in-game menus, like vendor menus and quest reward selections, I am unable to double-check to make selections.

The workaround?  Having someone else buy items for me and trade them to me.

---

### Post by Morten ML on 2011-05-14
> **Jalathas said:**
> I'm running Ubuntu 11.04, running the game in wine through pylotro 0.1.14. I've  been able to get into the game, create a character, and play through the  first tutorial dungeon, but now that I'm in the town, the game's been  freezing on random loading screens. I also, despite having been told  that the game only runs in fullscreen at default resolution, managed to  crank it to fullscreen 1680x1050, which was lovely until the freeze, at  which point nothing could get it OFF the screen, up to and including  switching workspaces. Any idea how to stop the freezes, or at least  change the settings such that I don't have to reboot when they happen?
Did you specify how many rams you graphic card has in regedit?
Before i did that the screen turned blackish every once in a while... hope it helps.
And @ajackson about the error: "MSVCR71.dll is part of Visual C++ Runtime 2003". INstalling vc2003 fixed my error.

---

### Post by Jalathas on 2011-05-14
> **Morten ML said:**
> Did you specify how many rams you graphic card has in regedit?
Before i did that the screen turned blackish every once in a while... hope it helps.

I hadn't, but while that improved load times, it doesn't seem to have helped any with the freezes, unfortunately. Thanks for the suggestion, though.

EDIT: After setting wine to emulate a virtual desktop the size of the  default resolution, I've at least come to the realization that the game  is actually crashing, not freezing. Rather than clogging up the screen,  it goes away and reveals the window that allows me to abort it.

---

### Post by buzzmandt on 2011-05-17
been using wine 1.3 for long time.  got an update for it this morning updated to 1.3.20.  now it has the jumpy jitters.  if i use the mouse to turn and look around moving or not, it jumps like it gets behind.  using keyboard only for directionals doesn't do this.

downgraded to wine 1.2.2 and it's working fine again.

---

### Post by Hellhoundevil on 2011-08-30
hay does anyone have a solution to this problem with DDO  i keep geting this message: p, li { white-space: pre-wrap; }  wine: Call from 0x7b839702 to unimplemented function msvcr80.dll._findfirst32, aborting
i have the PyLot launcher and standard res instaled but i keep geting that message DX librarys and updated?

---

### Post by ElodieHiras on 2011-09-15
Hello!

I have a problem with DDO:

First, I have the last ubuntu version.
Second, I installed the winetricks librairies.
Third, I grabbed the MOD8 DDO version.
Fourth, I use the Pylotro launcher, and the modified patchclient.dll.

And I get an unknown win32 error 10060 while trying to patch my DDO game.

What does that means, and how do I make it go away?

Thanks!

---

### Post by tarahmarie on 2011-09-18
I have the game running, but it's very slow and glitchy.

Natty
Nvidia GeForce 8600 (512 MB)
Core 3 Duo
4GB RAM
Plenty of space.

Wine 1.3

I have used winetricks to install vcrun2005 and vcrun2008, I've patched the game using ajackson's patchclient.dll, and set graphics to 'Very Low'. 

The game loads and runs so slowly that it's unplayable. I tried setting the reg key (VideoMemorySize), but the game wouldn't load at that point--so I deleted that key. 

Any ideas?

---

### Post by Jokerswild2412 on 2011-09-20
Hey everyone, I just installed ddo on my machine and when I go to patch the game through lotro, I am getting the following error:

p, li { white-space: pre-wrap; } rundll32.exe patchclient.dll,Patch patch.ddo.com:80 --language English --productcode DDO --filesonly
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 err:rundll32:wWinMain Unable to find the entry point L"Patch" in L"patchclient.dll"
 
 *** Finished ***

Can any help me out on how to patch this?By the way I followed the instructions on [URL="https://wiki.archlinux.org/index.php/Dungeon_&_Dragons_Online"]https://wiki.archlinux.org/index.php/Dungeon_&_Dragons_Online
[/URL]

---

### Post by ElodieHiras on 2011-09-20
Ok, I found it was a firewall problem. Now I have solved it and patched my DDO game, I can't run it because it gives me an error 105 could not initialise directX3D. It xorked before, but now it just doesn't anymore. I use the pylotro launcher, and followed the how to at [http://forums.ddo.com/showthread.php?t=212618](http://forums.ddo.com/showthread.php?t=212618)  .

Can somebody help me please?

Thanks!

Edit: It tells me that Direct3D9 is not available without openGL, whatever the hell does that means, if you need that info.

---

### Post by zephar123 on 2011-09-26
Well, issue I am having I believe is 11.10 realated, but I figured I would ask jsut incase.

Ironically, If people wondering why I went to 11.10 it was because of issue in 11.04 with QT functions that 11.10 fixed :P. 

Anyways here is the error log.

> 
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e65c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:imm:ImmReleaseContext (0x10074, (nil)): stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32adf4
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:ntdll:RtlpWaitForCriticalSection section 0x7e2552c0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0023, blocked by 0028, retrying (60 sec)
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x328dd4
fixme:msvcr90:__clean_type_info_names_internal (0x1d1b01e4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3e4cbc) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1009c770) stub
fixme:msvcr90:__clean_type_info_names_internal (0x33a694) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e8d7020) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e7ba8c4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e1fc7f8) stub



now this part here is what I think creating the main issue

err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

I found here though 

[http://ubuntuforums.org/showthread.php?t=1836927&highlight=Direct3D9+OpenGL](http://ubuntuforums.org/showthread.php?t=1836927&highlight=Direct3D9+OpenGL)

which makes me think its an issue with 11.10 if anyone has found a work around for this it would be much appreciated thanks in advance.

---

### Post by mediocresavant on 2011-10-29
p, li { white-space: pre-wrap; } Sort of new to Linux here, so looking for as much help as I can get...


Installed everything according to the instructions on the site, but when I go to log in, I get a white screen with the following on it:



err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/joe/.local/share/mime/packages/x-wine-extension-/bzw.xml
 
 err:menubuilder:write_freedesktop_association_entry error writing association file "/home/joe/.local/share/applications/wine-extension-/bzw.desktop"
 
 *** Finished ***


[LEFT]followed by a black screen with error number 129 that disappears a few seconds later.


Thanks for all your help in advance.
[/LEFT]

---

### Post by ElodieHiras on 2011-11-22
Hello!

I recently did a reinstall of Ubuntu 11.04, and DDO works about fine... Except I can't hear anyone talking on the voice chat.

I still use the Pylotro launcher, and it sends me this error (remove all the " ", because if I typed it without it it would type smilies:

ALSA lib pcm.c:2212:" "(snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 
 ALSA lib pcm.c:2212:" "(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212:" "(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957:" "(snd_pcm_dmix_open) 
 The dmix plugin supports only playback stream
 
 
 Cannot connect to server socket err = Aucun fichier ou dossier de ce type (no such file or directory for the non french speakers)
 Cannot connect to server socket
 jack server is not running or cannot be started
 


Can someone help me please? Thank you!

Edit: Found something about pulseaudio causing, trouble removed it, and now I got no sound at all and nothing on audio setting when playing DDO. Can someone help me?

Edit: Reinstalled pulse audio, configured a working jack server, and I'm having no sound on ddo but audio settings are visible, and new messages:

 p, li { white-space: pre-wrap; }  ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) 
 The dmix plugin supports only playback stream
 
 ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) The dmix plugin supports only playback stream
 
 ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) 
 The dmix plugin supports only playback stream
 
 ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) 
 The dmix plugin supports only playback stream
 
 ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) 
 The dmix plugin supports only playback stream
 
 ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
 
 AL lib: alsa.c:587: Could not open playback device 'hw:0,0': PÃ©riphÃ©rique ou ressource occupÃ©
 
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) 
 Unknown PCM cards.pcm.rear
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
 ALSA lib pcm.c:2212: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
 
 ALSA lib pcm_dmix.c:957: (snd_pcm_dmix_open) 
 The dmix plugin supports only playback stream
 ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave

---

### Post by ElodieHiras on 2011-11-30
Alright, I managed to connect pulseaudio to jack server, but I have some random problems with jack server, where I suddenly can't hear anything from the voice chat. I can talk without any problem, but I cannot hear the others. Same errors for wine output. can somebody help me? Please?

Thank you in advance!

---

### Post by Synoc on 2012-01-06
I am trying to log onto DDO, but when I hit logon, it brings me to the output screen and nothing at all happens. any suggestions? this is my firs time installing and running it. 

I copied the files from my windows box, did the patches. Put in account name, and password, select my server and get nothing but the output screen.

---

### Post by Synoc on 2012-01-07
ok new problem, found this...

[http://forums.ddo.com/showthread.php?t=212618](http://forums.ddo.com/showthread.php?t=212618)

used it. I downloaded the d3dx9 prefix and vcrun2005 at the same time...

it gets FURTHER now, but it now it says I need directx9 or higher installed.  what am I missing?

---

### Post by ergo-proxy on 2012-01-09
Are you using pylotro to start ddo?

---

### Post by Synoc on 2012-01-09
> **ergo-proxy said:**
> Are you using pylotro to start ddo?

affirmative. I am not sure I have ALL the required windows dll's and prefixes. those are the only two I have (well the entire D3dx9 sectiion), but I don't have the .NET 1.1 framework, for example. but bout that cause Direct3D to not load?

---

### Post by ergo-proxy on 2012-01-10
I think d3dx9 is no longer required, at least I didnt install it on oneiric, have a look here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24233](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24233)

---

### Post by Synoc on 2012-01-13
sorry it took long to get back... College has started up again. I already have the d3dx9 and the vcrun200x installed, if they are offending problems how do I remove them?

---

### Post by Synoc on 2012-01-18
been four days, so sorry, to bump, but... 

bump.

---

### Post by ergo-proxy on 2012-01-19
You can try with starting the game from a new wineprefix.

---

### Post by Jeek Elemental on 2012-01-19
Easy way to start "fresh" is to rename your .wine (to .winebak or something), run winecfg, then copy/move ddo from .winebak to .wine

When you have it set up its a good idea to rename it again and use WINEPREFIX to run it, to keep it separate from any other things you run with wine.

As of wine 1.3.37 I don't think any native .dlls or settings are required.

---

### Post by Synoc on 2012-01-19
so IF I did this right, I did a "mv .wine/ winebak" then mv winebak/c_drive/Program\ Files/DDO/ ./wine/c_drive/Program| Files/" and reinstall the pylotro.exe, retrain it, then I should be good to go?

cause I tried it, it didn't work, same problem

---

### Post by Jeek Elemental on 2012-01-20
check:
working opengl setup (numerous guides on web)

wine --version is 1.3.37 or newer (there is a ppa available at [www.winehq.org](www.winehq.org))

ddo client updated (do update from menu in pylotro, ddo will stop at loading screen if wrong client version)

Also might be worth deleting /home/you/Dungeons and Dragons Online/userpreferences.ini

---

### Post by Synoc on 2012-01-21
> **Jeek Elemental said:**
> check:
working opengl setup (numerous guides on web)

wine --version is 1.3.37 or newer (there is a ppa available at [www.winehq.org](www.winehq.org))

ddo client updated (do update from menu in pylotro, ddo will stop at loading screen if wrong client version)

Also might be worth deleting /home/you/Dungeons and Dragons Online/userpreferences.ini

ok I went to 
[http://www.opengl.org/wiki/Getting_started#Linux](http://www.opengl.org/wiki/Getting_started#Linux)
and took a look, it in turn sent me to 
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
if I am understanding this correctly it is either asking met o install new video drivers or new extensions for my current drivers. In either case what are the chances it will make my graphics system unstable? Or am I misreading what I am looking at?

and I am using the latest wine (1.3.37) and the current pylotro. If it matters, I installed the windows exe one as opposed to the linux one in an attempt to keep my Linux and my Windows apps completely separate. I was under the impression from the how-to guide on the pylotro site it doesn't matter, but that information could be old.

---

### Post by Jeek Elemental on 2012-01-22
wine pylotro should be fine.

Regarding drivers, the situation is that there are 2 options currently:
open source but lacking features: nouveau
closed but full featured: nvidia

Odds are you need the nvidia driver for ddo.

You can get both through ubuntus package system, theres also a special (don't ask me why) program for "activating" closed drivers (called additional hardware or close in your menu).
Theres a massive amount of information on this with some googling.

---

### Post by Synoc on 2012-01-22
I am using the nvidia drivers. why is it not recognizing my my direct3d, it shows up in the wine registry, These are my settings, is THIS the problem?
```

REGEDIT4 

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="OpenGL"
"Multisampling"="disabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="readdraw"
"UseGLSL"="disabled"
"VideoMemorySize"="256"

```

---

### Post by Jeek Elemental on 2012-01-23
> **Synoc said:**
> I am using the nvidia drivers. why is it not recognizing my my direct3d, it shows up in the wine registry, These are my settings, is THIS the problem?


None of those settings should stop it from running, however they should not be needed either. The Direct3D key is empty in a clean .wine and that should be your start point.
From a clean .wine created by winecfg, no installs or settings should be needed except the game itself, ie don't install directx or anything.

---

### Post by Synoc on 2012-01-23
I am about to give up on using Linux to play it. after a two weeks I'm getting no where. I have followed every guide I've ever seen, they are all the same, more or less, and all lead me right here.

I started with a clean .wine. copied over the DDO files from my windows partition, installed pylotro, updated DDO, installed winetricks, downloaded d3dx9, vcrun2003-8 according to appdb. and I then failed to get it to run. Direct3D is not installed etc... where is my problem?

---

### Post by Jeek Elemental on 2012-01-23
> **Synoc said:**
> I am about to give up on using Linux to play it. after a two weeks I'm getting no where. I have followed every guide I've ever seen, they are all the same, more or less, and all lead me right here.

I started with a clean .wine. copied over the DDO files from my windows partition, installed pylotro, updated DDO, installed winetricks, downloaded d3dx9, vcrun2003-8 according to appdb. and I then failed to get it to run. Direct3D is not installed etc... where is my problem?

Don't install anything from winetricks..

---

### Post by Synoc on 2012-01-23
so wipe everything (again), clean wine install (again) copy DDO folder (again), reinstalled pylotro (again), point it at the DDO folder (again). and play until I puke?

do I need the registry entry at all?

---

### Post by Synoc on 2012-01-26
ok took the ddo folder out of it's home in .wine/drive_c/Program\ Files/ and threw it in the winebak folder...

rm -r /wine

winecfg

placed the registry file back in regedit

put the DDo folder BACK in .wine/drive_c/Program\ Files/ 

reinstalled pylotro

pointed it at DDO 

same error.

---

### Post by Synoc on 2012-01-29
and bump one last time before I give it up

---

### Post by Jeek Elemental on 2012-01-30
> **Synoc said:**
> ok took the ddo folder out of it's home in .wine/drive_c/Program\ Files/ and threw it in the winebak folder...
rm -r /wine
winecfg
placed the registry file back in regedit
put the DDo folder BACK in .wine/drive_c/Program\ Files/ 
reinstalled pylotro
pointed it at DDO 
same error.

What registry file? Just running DDO does not require any registry settings, its (if I remember) just a version string for the turbine updater, which we don't use.

Did you try deleting userpreferences.ini? This will trigger autodetection from the game.

The error is still that DDO can't find a direct3d device?
Try running another 3d game/demo in the same prefix.

---

### Post by Synoc on 2012-01-30
> **Jeek Elemental said:**
> What registry file? Just running DDO does not require any registry settings, its (if I remember) just a version string for the turbine updater, which we don't use.

Did you try deleting userpreferences.ini? This will trigger autodetection from the game.

The error is still that DDO can't find a direct3d device?
Try running another 3d game/demo in the same prefix.

deleted userpreferences.ini (I didn't set them in the first place, however. no effect. should I jsut delete the entire direct3D folder in the registry?

I was considering using playonlinux to install LotRO and seeing if the mere act of setting that up would enable DDO to work... haven't tried yet as I am not familiar with PlayOnLinux.

---

### Post by Jeek Elemental on 2012-01-30
> **Synoc said:**
> deleted userpreferences.ini (I didn't set them in the first place, however. no effect. should I jsut delete the entire direct3D folder in the registry?
I was considering using playonlinux to install LotRO and seeing if the mere act of setting that up would enable DDO to work... haven't tried yet as I am not familiar with PlayOnLinux.

Starting from a clean .wine there should be no direct3d key at all...Do not import, install or change anything, only copy in ddo/pylotro.

If it still fails you must test your opengl setup with some other demo/game.
I'm sure playonlinux etc. is great, but it won't work if your 3d is not set up.

---

### Post by Synoc on 2012-02-01
just for S&G's since I have wipe out wine more times than I can count, I uninstalled it and reinstalled the whole thing. I'm back at wine1.2.3 since the beta version didn't help me with anything

what other programs use opengl so I can set my set up? that won't cost me anything?

---

### Post by Jeek Elemental on 2012-02-03
For old wine versions you'll have to check appdb for settings needed.
There are many guides on 3d setup a google away, extremetuxracer is a linux-native 3d accelerated game you can get from your package manager.

> **Synoc said:**
> just for S&G's since I have wipe out wine more times than I can count, I uninstalled it and reinstalled the whole thing. I'm back at wine1.2.3 since the beta version didn't help me with anything

what other programs use opengl so I can set my set up? that won't cost me anything?

---

### Post by Synoc on 2012-02-05
extremetuxracer works fine.

updated to wine 1.3.37

JUST moved the files from my winebak folder (where I store them after every wine wipe). 

what is next to test?

this is off appdb
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24407](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24407)

---

### Post by Jeek Elemental on 2012-02-06
Try running it then, it should be good now.
Run it from a terminal so you can catch any error messages.
Make sure the client is updated, output (from within pylotro) should be something like

```
Connecting to patch.ddo.com:80

Checking files...
files to patch: 0 bytes to download: 0
Patching files:

Connecting to patch.ddo.com:80

Checking files...
files to patch: 0 bytes to download: 0
Patching files:

Connecting to patch.ddo.com:80

checking data...
data patches: 0 bytes to download: 0
unlock: 0 empty: 0
result code: 0x00000001
Patching data:


*** Finished ***
```




> **Synoc said:**
> extremetuxracer works fine.
updated to wine 1.3.37
JUST moved the files from my winebak folder (where I store them after every wine wipe). 
what is next to test?
this is off appdb
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24407](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24407)

---

### Post by Synoc on 2012-02-07
patched, started from CLI (./.wine/drive_c/Program\ Files/PyLptRO/pylotro.exe) same problem.

output from terminal is as follows:
```


~$ ./.wine/drive_c/Program\ Files/PyLotRO/pylotro.exe 
fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e63c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:ImmReleaseContext (0x20028, (nil)): stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32aa24
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x328a14
fixme:msvcr90:__clean_type_info_names_internal (0x1d1b01e4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3e4cbc) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1009c770) stub
fixme:msvcr90:__clean_type_info_names_internal (0x33a694) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e8d7020) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e7ba8c4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e1fc7f8) stub

```
as far as the display changing, I have never got it running TO change the display.

Here are the User Prefs it gives me by default:
```


[Display]
Resolution=960x600
ForceFakeFullScreen=False
SyncToRefresh=False
Antialiasing=Disabled
WindowedResolution=960x600
TripleBuffering=False
FullScreen=True
AllowDesktopCompositing=False
AllowWindowResizing=True
AllowFakeFullScreen=True
ConfineFullScreenMouseCursor=True
FixedOutputScaling=Default
ShowIntroMovie=True
RefreshRate=Auto
[Render]
GraphicsCore=D3D9
VideoPostEffects=True
AnimationDetail=Medium
AllowGammaChanges=True
HavePromptedForD3D10AtStartup=False
TextureFiltering=Trilinear
Gamma=1.00
AnisotropicQuality=4
AmbientOcclusion=True
MaxHardwareClass=0
BloomIntensity=1.00
LandscapeDrawDistance=High
DisplayAdapter=0
SpecularLighting=True
ObjectDrawDistance=High
Contrast=1.00
Brightness=1.00
AlphaToCoverage=False
PlayerCrowdQuality=1.00
BlobShadows=True
InteractiveWater=Low
FrillDistance=Medium
OverbrightBloomFilter=False
TextureDetail=High
LandscapeShoreEffects=High
MemoryUsage=0.30
ShadowMapQuality=0
LandscapeStaticObjectShadows=Medium
EnablePortraits=True
AspectRatio=Auto
BlurFilterQuality=Medium
ModelDetail=High
MultiPassLighting=True
LandscapeLightingQuality=Low
D3DVersionPromptedForAtStartup=0
StencilShadows=Medium
FarLandscapeNormalMaps=False
MeshCombining=True
GlowMapping=True
MaterialDetail=High
AtmosphericsDetail=Medium
SurfaceReflections=Low
EnvironmentStencilShadows=False
DistantImposters=True
[Net]
ComputeUniquePort=True
BindInterface=
ConnectionSpeed=0.00
UserSpecifiedPort=0
[TDM]
AllowRenderRedetect=True
[WebBrowser]
HttpsProxyPort=0
HttpsProxyHost=
HttpProxyHost=
InitialConfigDone=True
HttpProxyPort=0
[Input]
JoystickDeadZone=0.25
TurnKeySpeed=150.00
InvertMouseLookYAxis=False
PitchKeySpeed=60.00
MouseLookSensitivity=0.10
MouseLookSmoothingAmount=0.00
[Troubleshooting]
MaximumFrameRate=121
EngineSpeed=VeryHigh
[CullSystem]
UseHardwareOcclusion=False
[International]
UseIME=False

```

---

### Post by Jeek Elemental on 2012-02-07
The first (qt) errors are from pylotro and can be ignored, the xrandr ones would seem to be key.

I'm not at all familiar with nvidia, I would look into if its a known driver issue or possibly wrong info from your monitor.

What you can try tho is running ddo in window mode, change 

```
FullScreen=True
```
to
```
FullScreen=False
```

in userpreferences.ini

Alternatively (or together) set "emulate a virtual desktop" in winecfg, and set the resolution there to your normal desktop one.

From within ddo you can check what fullscreen resolutions are available to it, if it looks ok there you should be set.

> **Synoc said:**
> patched, started from CLI (./.wine/drive_c/Program\ Files/PyLptRO/pylotro.exe) same problem.

output from terminal is as follows:
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?


---

### Post by Synoc on 2012-02-07
Started in Windowed Mode 
```

./.wine/drive_c/Program\ Files/PyLotRO/pylotro.exe 
fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e63c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:ImmReleaseContext (0x20028, (nil)): stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32aa24
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
err:winediag:AUDDRV_GetAudioEndpoint PulseAudio "default" -22 without handle_underrun. Audio may hang. Please upgrade to alsa_plugins >= 1.0.24
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x328a14
fixme:msvcr90:__clean_type_info_names_internal (0x1d1b01e4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3e4cbc) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1009c770) stub
fixme:msvcr90:__clean_type_info_names_internal (0x33a694) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e8d7020) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e7ba8c4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e1fc7f8) stub

```

started in windowed mode w/ virtual desktop
```


./.wine/drive_c/Program\ Files/PyLotRO/pylotro.exe 
fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\patrick\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e63c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:ImmReleaseContext (0x20028, (nil)): stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32aa24
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
err:winediag:AUDDRV_GetAudioEndpoint PulseAudio "default" -22 without handle_underrun. Audio may hang. Please upgrade to alsa_plugins >= 1.0.24
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x328ba4
fixme:msvcr90:__clean_type_info_names_internal (0x1d1b01e4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x3e4cbc) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1009c770) stub
fixme:msvcr90:__clean_type_info_names_internal (0x33a694) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e8d7020) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e7ba8c4) stub
fixme:msvcr90:__clean_type_info_names_internal (0x1e1fc7f8) stub

```
The direct 3d error was eliminated in both instances

---

### Post by njrob on 2012-02-16
> **Jeek Elemental said:**
> Try running it then, it should be good now.
Run it from a terminal so you can catch any error messages.
Make sure the client is updated, output (from within pylotro) should be something like

```
Connecting to patch.ddo.com:80

Checking files...
files to patch: 0 bytes to download: 0
Patching files:

Connecting to patch.ddo.com:80

Checking files...
files to patch: 0 bytes to download: 0
Patching files:

Connecting to patch.ddo.com:80

checking data...
data patches: 0 bytes to download: 0
unlock: 0 empty: 0
result code: 0x00000001
Patching data:


*** Finished ***
```
I have played DDO in past and loved it, but I am no longer able to play it on my windows os.  That said, it has been one of my hopes since installing Ubuntu to get this game running; I miss it so much!  Despite multiple attempts, I have been unsuccessful as of yet.

I have managed to get this far; this thread has been very helpful.  I can't seem to get DDO to actually start though.  I keep getting the "finished" message whenever I go through the server select/account login;  it's as if it runs the patch instead of the game.  I had this problem last time I installed DDO successfully on Ubuntu; it's the farthest I've ever gotten.  I still need to try changing the windows version of wine to 2000, but if that doesn't work, what next?  I think it might be my unfamiliarity with the new PyLotro launcher, but there's a good chance there's something else I'm overlooking elsewhere.

---

### Post by Jeek Elemental on 2012-02-16
Which Wine version are you using?
Type "wine --version" in a terminal.

If its < 1.3.37 go to [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)
and follow the instructions there, remember to actually update wine after adding the repo.


> **njrob said:**
> I have played DDO in past and loved it, but I am no longer able to play it on my windows os.  That said, it has been one of my hopes since installing Ubuntu to get this game running; I miss it so much!  Despite multiple attempts, I have been unsuccessful as of yet.

I have managed to get this far; this thread has been very helpful.  I can't seem to get DDO to actually start though.  I keep getting the "finished" message whenever I go through the server select/account login;  it's as if it runs the patch instead of the game.  I had this problem last time I installed DDO successfully on Ubuntu; it's the farthest I've ever gotten.  I still need to try changing the windows version of wine to 2000, but if that doesn't work, what next?  I think it might be my unfamiliarity with the new PyLotro launcher, but there's a good chance there's something else I'm overlooking elsewhere.

---

### Post by njrob on 2012-02-16
It appears I was using Wine 1.3.28
I think I'll re-install PlayOnLinux so I can fine-tune wine versions with greater ease.

I think my main issue in past has been space; my Ubuntu partition was no more than 10GB at best until I found some unnecessary iso files I left on my Windows partition.  Now that I have a 32GB Ubuntu disk, I can install DDO no problem.

So, is the wine version likely the only remaining issue, or could something else be wrong?  I suppose I'll get to that once I've done this other.

---

### Post by Jeek Elemental on 2012-02-16
1.3.28 would require some native dlls if I remember, which if not there would cause DDO to halt as you described.

Checklist:

-DDO installed in clean .wine/ (no added registry settings)
-pylotro installed and set up (wizard in menu), either linux or windows version
-DDO updated through pylotro (ddo hangs at loading screen if version mismatch)
-OpenGL support, proprietary ATI or Nvidia drivers needed (I think). Hw demands are very modest.
-Wine version 1.3.37 or later

These are the basic requirements, run wine pylotro.exe from a terminal to catch error messages and post here if not working.

> **njrob said:**
> It appears I was using Wine 1.3.28
I think I'll re-install PlayOnLinux so I can fine-tune wine versions with greater ease.

I think my main issue in past has been space; my Ubuntu partition was no more than 10GB at best until I found some unnecessary iso files I left on my Windows partition.  Now that I have a 32GB Ubuntu disk, I can install DDO no problem.

So, is the wine version likely the only remaining issue, or could something else be wrong?  I suppose I'll get to that once I've done this other.

---

### Post by njrob on 2012-02-16
I want to do this with the latest 1.3 wine using PlayOnLinux to run both the launcher and DDO.
I have PlyOnLinux installed, and I'm commencing a fresh install of DDO and PyLotoro launcher.
I am using (in PlayOnLinux) Wine 1.3.37, and I set the windows version to 2000 as the WineHQ page recommends.
I need to know where I need to place the pylotro files in relation to the DDO ones so the launcher recognizes the game.
I'll let you know how this works. . .
Thank you for your help thus far!
Any additional pointers would be appreciated!

---

### Post by Jeek Elemental on 2012-02-16
I am not familiar with playonlinux, if it interferes with wine in any way you should probably ask in a dedicated forum.
The appdb items are out of date.

Are you using linux or windows pylotro?
Just place the (windows) pylotro dir in the same dir as ddo, I believe it searches C:\Program Files\ at the very least, maybe even from c:\.

Note that you can't "run both the launcher and DDO" as you say, the launcher will run ddo with the obtained login string.


> **njrob said:**
> I want to do this with the latest 1.3 wine using PlayOnLinux to run both the launcher and DDO.
I have PlyOnLinux installed, and I'm commencing a fresh install of DDO and PyLotoro launcher.
I am using (in PlayOnLinux) Wine 1.3.37, and I set the windows version to 2000 as the WineHQ page recommends.
I need to know where I need to place the pylotro files in relation to the DDO ones so the launcher recognizes the game.
I'll let you know how this works. . .
Thank you for your help thus far!
Any additional pointers would be appreciated!

---

### Post by njrob on 2012-02-16
I'm using Windows pylotro.  Thank you for the comment about pylotro's directory search for ddo; that will help immensely. Let's see how this goes!

---

### Post by njrob on 2012-02-16
I have forgone the use of PlayOnLinux, and I'm going to use wine 1.3.28

What dll's or other such file would I need to put together for the launcher to work?

---

### Post by Jeek Elemental on 2012-02-16
I would recommend updating wine, by far the easiest way.
If you must keep .28 then your best bet is to use the instructions on appdb for that version, like
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24407](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24407)
Get Winetricks from your package manager to install the necessary dlls. Possibly you'll need a dll from lotro to update, not sure how that played out.

Note that even though you use the old wine version, the ddo client has been updated many times since then, so theres no guarantee you will get the same results.


> **njrob said:**
> I have forgone the use of PlayOnLinux, and I'm going to use wine 1.3.28

What dll's or other such file would I need to put together for the launcher to work?

---

### Post by njrob on 2012-02-16
How exactly do I update wine to a specific version?  
The Software Center listings are only as specific as: 1.3  
It doesn't list which version completely like: 1.3.??

When I do find out how to update, will updating Wine require me to wipe my Wine folders?

---

### Post by Jeek Elemental on 2012-02-16
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)
Follow the instructions there, and you get the latest beta through software center/update manager afterwards.

Package is still called wine1.3 although its at 1.4.xx now.

No need to wipe anything, wine will update old prefixes first time you use them.

> **njrob said:**
> How exactly do I update wine to a specific version?  
The Software Center listings are only as specific as: 1.3  
It doesn't list which version completely like: 1.3.??

When I do find out how to update, will updating Wine require me to wipe my Wine folders?

---

### Post by njrob on 2012-02-16
Thanks; in the process of updating wine now, using the terminal.
I hope this helps!

I'm also looking for an Ubuntu/Wine friendly download of the LOTRO free client as a Plan B if the DDO-PyLotro combo fails.  Anyplace you could point me to?  Probably a WineHQ page somewhere, right?

---

### Post by njrob on 2012-02-16
> **Jeek Elemental said:**
> I am not familiar with playonlinux, if it interferes with wine in any way you should probably ask in a dedicated forum.
The appdb items are out of date.

Are you using linux or windows pylotro?
Just place the (windows) pylotro dir in the same dir as ddo, I believe it searches C:\Program Files\ at the very least, maybe even from c:\.

Note that you can't "run both the launcher and DDO" as you say, the launcher will run ddo with the obtained login string.

This "login string," is it what I'm missing?

I have followed all of the most instructions for getting this to work, but it still isn't quite there yet.

It's probably my Graphics settings.  Any tips on how to configure and maximize graphics performance?

---

### Post by Jeek Elemental on 2012-02-17
No, that is what pylotro does for you, among other things.
When you log in with pylotro it gets back an authentication string from the ddo server, and then starts ddo with that string as an argument.

You must run the settings wizard in the tools menu of pylotro.

Lotro is basically the same engine.

Go through the checklist in earlier post, run pylotro from terminal and post any error messages here.

> **njrob said:**
> This "login string," is it what I'm missing?

I have followed all of the most instructions for getting this to work, but it still isn't quite there yet.

It's probably my Graphics settings.  Any tips on how to configure and maximize graphics performance?

---

### Post by njrob on 2012-02-17
> **Jeek Elemental said:**
> The first (qt) errors are from pylotro and can be ignored, the xrandr ones would seem to be key.

I'm not at all familiar with nvidia, I would look into if its a known driver issue or possibly wrong info from your monitor.

What you can try tho is running ddo in window mode, change 

```
FullScreen=True
```
to
```
FullScreen=False
```

in userpreferences.ini

Alternatively (or together) set "emulate a virtual desktop" in winecfg, and set the resolution there to your normal desktop one.

From within ddo you can check what fullscreen resolutions are available to it, if it looks ok there you should be set.

I can't find the "userpreferencesw.ini" file; is it something I need to add to my installation, or is there a specific place where I might have missed it?

---

### Post by Jeek Elemental on 2012-02-17
Default path is 
/home/$user/Dungeons and Dragons Online/UserPreferences.ini

with $user being your username.

However ddo will create those directories and files when run first time, so you may not have them yet.

Exactly what happens when you run it?

> **njrob said:**
> I can't find the "userpreferencesw.ini" file; is it something I need to add to my installation, or is there a specific place where I might have missed it?

---

### Post by njrob on 2012-02-17
> **Jeek Elemental said:**
> Default path is 
/home/$user/Dungeons and Dragons Online/UserPreferences.ini

with $user being your username.

However ddo will create those directories and files when run first time, so you may not have them yet.

Exactly what happens when you run it?

I run pylotro, (not in terminal) and it pops up with the patch window displaying "finished"  instead of starting a game display.  I can't get DDO to even run, (using pylotro).

What could be left undone?  I'll run pylotro in the terminal and post the results.

---

### Post by njrob on 2012-02-17
> **Jeek Elemental said:**
> 1.3.28 would require some native dlls if I remember, which if not there would cause DDO to halt as you described.

Checklist:

-DDO installed in clean .wine/ (no added registry settings)
-pylotro installed and set up (wizard in menu), either linux or windows version
-DDO updated through pylotro (ddo hangs at loading screen if version mismatch)
-OpenGL support, proprietary ATI or Nvidia drivers needed (I think). Hw demands are very modest.
-Wine version 1.3.37 or later

These are the basic requirements, run wine pylotro.exe from a terminal to catch error messages and post here if not working.

I tried to run pylotro in the terminal, and this is the result

neal@ubuntu:~$ wine pylotro.exe
wine: cannot find L"C:\\windows\\system32\\pylotro.exe"
neal@ubuntu:~$ wine ./.wine/drive_c/Program\ Files/PyLotRO/pylotro.exe
fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e5ec
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImmReleaseContext (0x10066, 0x2fe57d8): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32ad84
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  891
  Current serial number in output stream:  891
neal@ubuntu:~$ err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x111bf4), expect failure
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x1124fc), expect failure


Sorry if my command line skills are atrocious; I'm just getting used to this sort of thing.  Syntax rules you don't recognize are such a pain!:rolleyes:

From what I can tell by myself, it is either having trouble finding necessary files, or I need to check my graphics drivers, or both.  Can you "translate" this gobbledygook into simpler terms?  I mainly need to know what I need to make visible and what I need to add to what I've got.

---

### Post by Jeek Elemental on 2012-02-17
It seems you don't have opengl support:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 

The other messages can be ignored.

Which driver are you using? You'll need proprietary drivers from ati or nvidia for the time being, these are not installed by default in ubuntu.


> **njrob said:**
> I tried to run pylotro in the terminal, and this is the result

neal@ubuntu:~$ wine pylotro.exe
wine: cannot find L"C:\\windows\\system32\\pylotro.exe"
neal@ubuntu:~$ wine ./.wine/drive_c/Program\ Files/PyLotRO/pylotro.exe
fixme:system:SetProcessDPIAware stub!
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"Z:\\home\\neal\\.wine\\drive_c\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
fixme:win:FlashWindowEx 0x32e5ec
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImmReleaseContext (0x10066, 0x2fe57d8): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32ad84
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  891
  Current serial number in output stream:  891
neal@ubuntu:~$ err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x111bf4), expect failure
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x1124fc), expect failure


Sorry if my command line skills are atrocious; I'm just getting used to this sort of thing.  Syntax rules you don't recognize are such a pain!:rolleyes:

From what I can tell by myself, it is either having trouble finding necessary files, or I need to check my graphics drivers, or both.  Can you "translate" this gobbledygook into simpler terms?  I mainly need to know what I need to make visible and what I need to add to what I've got.

---

### Post by njrob on 2012-02-17
> **Jeek Elemental said:**
> It seems you don't have opengl support:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 

The other messages can be ignored.

Which driver are you using? You'll need proprietary drivers from ati or nvidia for the time being, these are not installed by default in ubuntu.

I am using a Dell Latitude | D810.  The screen has been replaced before, but that shouldn't be affecting this issue, since it seems to be a software problem, (I sincerely hope so).  I have downloaded the ATI Mobility Radeon X300 driver that matches my Dell from the Dell "Drivers and Downloads" site.  I extracted it to my wine drive_c, but none of the several "setup.exe" files will install anything.

I have tried using the proprietary drivers program Ubuntu has in System Settings before, but it never detects anything.

Does the ATI driver need special treatment in Wine, or is it impossible to run Windows drivers in Wine to begin with?

Sorry for this endless stream of questions; I thank you for your patience and the help you've been giving me.:D

But as for the driver. . .?:confused:

---

### Post by njrob on 2012-02-17
It appears I already have some sort of ATI package added in the Software Center, but I don't know if it can fill in for what DDO requires.

---

### Post by njrob on 2012-02-17
Another quick thought: do I need to install only one of the two kinds of drivers?  I mean, if I have a Dell, and it usually uses ATI, does that make it so that nividia won't work?

---

### Post by njrob on 2012-02-17
Okay, I looked closer at my ATI driver in the Software center and I'm currently adding the latest add-on for the AMD Radeon Graphics accellerators.  I [I]think[I] that this driver includes coverage for my system, but I may be wrong.  It has helped me with my everyday display needs, but could it be insufficient for DDO?

> Checklist:

-DDO installed in clean .wine/ (no added registry settings)
-pylotro installed and set up (wizard in menu), either linux or windows version
-DDO updated through pylotro (ddo hangs at loading screen if version mismatch)
-OpenGL support, proprietary ATI or Nvidia drivers needed (I think). Hw demands are very modest.
-Wine version 1.3.37 or later

These are the basic requirements, run wine pylotro.exe from a terminal to catch error messages and post here if not working.

When you say DDO's graphics demands are, "modest," do you mean that DDO is easy or hard to please when it comes to graphics support?  Man, I must be really missing the mark if it's supposed to be simple!

---

### Post by Jeek Elemental on 2012-02-17
Maybe it helps to think of wine as a big switchboard, when a windows exe asks for a function, wine plugs in the equivalent linux function and conjugglifies any differences (what? its a perfectly cromulent word.)

So you don't need windows drivers, but must have opengl capable driver on linux side.

Sadly that is non-trivial for x300 as fglrx (ati's driver) does not support it anymore.
You can try the "Additional Drivers" program, maybe its able to get an old ati driver.

There are numerous guides and threads on that subject tho.

> **njrob said:**
> Another quick thought: do I need to install only one of the two kinds of drivers?  I mean, if I have a Dell, and it usually uses ATI, does that make it so that nividia won't work?

---

### Post by njrob on 2012-02-17
So that means I just need to find a linux/Ubuntu based ATI driver that supports my graphics card?  The Dell Latitude D810 actually uses Mobility Radeon X600, but the Dell site said I could use X300; is X600 still not covered by the driver I have?

---

### Post by Jeek Elemental on 2012-02-17
The problem is this: ati stopped supporting older cards a while back, so the official fglrx driver won't recognize your card (neither x300 or x600).

The open source driver (which you are probably using now) does not have full opengl support yet.

Its possible you could use an old driver (and old x.org that matches) but it would be non-trivial and way beyond this thread.


> **njrob said:**
> So that means I just need to find a linux/Ubuntu based ATI driver that supports my graphics card?  The Dell Latitude D810 actually uses Mobility Radeon X600, but the Dell site said I could use X300; is X600 still not covered by the driver I have?

---

### Post by njrob on 2012-02-17
Thank you for your help!  I will post again once I am finished with the driver issue.

---

### Post by njrob on 2012-02-17
I know this isn't exactly the place for it but, Jeek, I can't be sure my personal messages got to you, so I need to use this as a failsafe method of getting through.

I tried to install emgd to provid OpenGL support for DDO in Wine, but I seem to have turned my Ubuntu booting upsidedown.  I can't get to the login screen or desktop.  there is an error with the system configuration,=; something about a "command already being sent"
I tried removing emgd, but the system can't find the files.  the desktop managers; all the ones available to me, don't work completely; they stop at the loading screen with the orange dots underneath the name Ubuntu.

Well, what's your diagnosis?  I don't want to reinstall Ubuntu if I don't have to, but I don't know how far in over my head this situation is.  Where do I go?

---

### Post by njrob on 2012-02-17
Okay, I'm back on my own computer again; I had an old root disk from my last Wubi-resize that I hadn't deleted (Thank Goodness!)

I need to do the risize over again, and maybe the installation, but now I know what to do and to be more careful!

---

### Post by njrob on 2012-02-17
Now, back to business!

I am making a new 32GB root.disk now, and will then commence reinstalling DDO and pylotro, (I have already updated to Wine1.3.37).

Once all is as it had been before the emgd crisis, I will need to have a plan for how to provide OpenGL support.  Can I use the nvidia driver even though I have an ATI GPU?  If it must be ATI software to be compatible, would I find directions for that on the Forum(s) here?  If so which?

---

### Post by njrob on 2012-02-18
Hi, I'm back.

I am still working on configuring my OpenGL drivers I just installed; they don't exactly have a gui, (yet), and I am trying to figure out how they work.

I wanted to ask about pylotro's needs again.  With wine 1.3.37, do I still need to get the updated patchclient.dll to run DDO, or is it included in the Mod8 installation?
I could be reading this situation wrong, and it's pylotro that's using the patch-client.dll;  I'm just not certain where to go from where I'm at:

- DDO is installed.
- pylotro is installed (windows standalone version in Wine).
- Installed(ish?) OpenGL support software for r600 graphics card.
- Using Ubuntu 11.10 with Wine 1.3.37

Running Status: PyLotro window displays, and the DDO installation is recognized.  However, when I "log in" with my account name and password, (in the realm/server selection field), the window that usually displays when activating pylotro's "patch" function is displayed, and skips directly to the message "finished."

---

### Post by Jeek Elemental on 2012-02-18
No .dlls are needed.

Have a look at
[http://ubuntuforums.org/showthread.php?t=1824881](http://ubuntuforums.org/showthread.php?t=1824881)

and maybe try asking in that forum.

> **njrob said:**
> Hi, I'm back.

I am still working on configuring my OpenGL drivers I just installed; they don't exactly have a gui, (yet), and I am trying to figure out how they work.

I wanted to ask about pylotro's needs again.  With wine 1.3.37, do I still need to get the updated patchclient.dll to run DDO, or is it included in the Mod8 installation?
I could be reading this situation wrong, and it's pylotro that's using the patch-client.dll;  I'm just not certain where to go from where I'm at:

- DDO is installed.
- pylotro is installed (windows standalone version in Wine).
- Installed(ish?) OpenGL support software for r600 graphics card.
- Using Ubuntu 11.10 with Wine 1.3.37

Running Status: PyLotro window displays, and the DDO installation is recognized.  However, when I "log in" with my account name and password, (in the realm/server selection field), the window that usually displays when activating pylotro's "patch" function is displayed, and skips directly to the message "finished."

---

### Post by Puddinhead on 2012-02-25
I've been running DDO on Linux for about 2 years now.  I'm running Linux Mint 11 on a Lenovo Think Pad W520.  If you can't get ths figured out let me know.  I've found it helpful to have a Windows Virtual Machine handy because the pylotro updater breaks every once in a while so I do the update on the Windows Virtual machine and copy the files to my Linux box.

Let me know if you need help, or hit me up on Thelanis if you manage to get everything working.

---

### Post by skulkruncher on 2012-02-27
Hi, Update 13 just came out and now that tried to patch DDO it starts giving me these errors:

rundll32.exe patchclientlotro.dll,Patch patch.ddo.com:80 --language English --productcode DDO --filesonly
Connecting to patch.ddo.com:80

Checking files...
files to patch: 13 bytes to download: 44126496
Patching files:

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1202230715/all/de/DDO TOS.rtf") (-2147467261)

Failed!

 Failed!

Failed to download files: OES_E_HTTP_STATUS_BAD_REQUEST(0x80044190)

Connecting to patch.ddo.com:80

Checking files...
files to patch: 13 bytes to download: 44126496
Patching files:

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1202230715/all/de/DDO TOS.rtf") (-2147467261)

Failed!

 Failed!

Failed to download files: OES_E_HTTP_STATUS_BAD_REQUEST(0x80044190)

Connecting to patch.ddo.com:80

checking data...
data patches: 0 bytes to download: 0
Patching data:



*** Finished ***

Any ideas why it is doing this and if there is a way to fix it. I've been able to patch it successfully for a while now. Don't know why it's doing it now.

---

### Post by Jeek Elemental on 2012-02-27
It patched fine here, I see you're using the lotro patch dll tho, try switch back to the original one (patchclient.dll).

Far as I know, the lotro .dll was a workaround that is no longer needed and may be the problem.

> **skulkruncher said:**
> Hi, Update 13 just came out and now that tried to patch DDO it starts giving me these errors:

rundll32.exe patchclientlotro.dll,Patch patch.ddo.com:80 --language English --productcode DDO --filesonly
Connecting to patch.ddo.com:80


---

### Post by skulkruncher on 2012-02-27
Thank you for the reply. I will try using the old one and hope I get a better result

---

### Post by skulkruncher on 2012-02-27
Using the regular patchclient.dll gave me this: 
> rundll32.exe patchclient.dll,Patch patch.ddo.com:80 --language English --productcode DDO --filesonly
Connecting to patch.ddo.com:80

Checking files...
files to patch: 13 bytes to download: 44126496
Patching files:

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1202230715/all/en/DDO EULA - Turbine.rtf") (-2147467261)

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1202230716/all/fr/DDO EULA - Turbine.rtf") (-2147467261)

Downloading patchclient.dllFile in use. It will be self patched.


err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1202230715/all/en/DDO EULA - Turbine.rtf") (-2147467261)

err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/ddo/patch/1202230715/all/de/DDO EULA - Turbine.rtf") (-2147467261)

Downloading en/DDO EULA - Turbine.rtfFailed!

 Failed!

fixme:faultrep:ReportFault 0x32f6a4 0x0 stub


---

### Post by Jeek Elemental on 2012-02-27
> **skulkruncher said:**
> Using the regular patchclient.dll gave me this:

Are you using any native .dlls?
I assume you're using the linux version of the launcher, maybe worth trying the windows one instead, as that is working here.

---

### Post by skulkruncher on 2012-02-27
I'm not sure which are the native dlls in my ddo files, havent messed with them in a while. Before, all the other patches went fine until this one so I'm getting bummed out its on this one. Also, do you mean for me to use the dndlauncher.exe?

---

### Post by skulkruncher on 2012-02-27
Thinking back, I remember I switched out the patchclient.dll with the one I downloaded from the winehq page; might have messed up and used the one that isn't original when I tried the second time. Not sure where the original is now....

---

### Post by Jeek Elemental on 2012-02-27
By native .dlls I mean windows own dlls as opposed to wine ones. You can check in winecfg under libraries if you are using any.

As for launcher, pylotro comes in 2 flavours, one runs natively in linux and then launches wine+ddo, other runs as a windows exe in the same .wine as ddo.

Which wine version are you using? (type "wine --version" in a terminal).

> **skulkruncher said:**
> I'm not sure which are the native dlls in my ddo files, havent messed with them in a while. Before, all the other patches went fine until this one so I'm getting bummed out its on this one. Also, do you mean for me to use the dndlauncher.exe?

---

### Post by skulkruncher on 2012-02-27
Im using wine 1.2.2

Where can I find the windows version of pylotro so I can check if it works.

---

### Post by Jeek Elemental on 2012-02-27
[http://www.lotrolinux.com/download.php](http://www.lotrolinux.com/download.php)

If no good, check the first page of this thread and follow the steps there (upgrading wine).
Rename your old .wine to .wineold, run winecfg, then move your ddo dir to the newly made .wine and it should work.

> **skulkruncher said:**
> Im using wine 1.2.2

Where can I find the windows version of pylotro so I can check if it works.

---

### Post by skulkruncher on 2012-02-27
Thanks for the help I'll see if I can make it work with these steps. Same thing happens with the window version so I'll try upgrading wine tomorrow.

---

### Post by skulkruncher on 2012-02-28
Got it to work! :D Finished patching and I logged in. Game works good.

---

### Post by njrob on 2012-03-24
Hi, I'm back!

I installed the latest DDO on a friend's computer and transferred the files to my Ubuntu.  It runs fine in Wine, but the graphics remain an issue.  The 3d Acceleration seems to be the only issue now, and I'm seeking help for that elsewhere, but I wanted to give an update on how the help from this thread was working.  Thank you all very much for you help!  I'm almost there!  Please let me know if there is anything I may find helpful to tweak in DDO to help with graphics performance.  It's really slow, choppy, laggy you name it!  I can't move hardly at all, and even the menu takes minutes to click on something, (not to mention copious amounts of patience!).  But, it does run, so I am excited about that success!

---

### Post by Jeek Elemental on 2012-03-24
You can try setting all graphic options to off/minimal in ddo, then upping one at a time to see if theres one in particular that impacts performance.

Also, if using a 3d accelerated desktop it may be worth switching to 2d before running games.

It may run better inside quests than in town, as all the people running around trigger lots of loading and memory usage.

---

### Post by njrob on 2012-03-24
> **Jeek Elemental said:**
> You can try setting all graphic options to off/minimal in ddo, then upping one at a time to see if theres one in particular that impacts performance.

Also, if using a 3d accelerated desktop it may be worth switching to 2d before running games.

It may run better inside quests than in town, as all the people running around trigger lots of loading and memory usage.

Thank you; I will try that.

I can't seem to get past Shipwreck shore on my new character; the movement wasn't working, but that might have been the network latency.  Thank you thank you for the advice!  Very helpful.

---

### Post by njrob on 2012-03-25
> **Jeek Elemental said:**
> You can try setting all graphic options to off/minimal in ddo, then upping one at a time to see if theres one in particular that impacts performance.

Also, if using a 3d accelerated desktop it may be worth switching to 2d before running games.

It may run better inside quests than in town, as all the people running around trigger lots of loading and memory usage.

I have pretty much everything set as low as possible without turning everything into a blob in the fog.  I also am using the plain, "no frills" gnome desktop environment, and despite my dislike for it it seems to have helped a little with loading screen duration and a small amount of lag in the menus and game environment.
Despite all this, I have found that when I do enter the game, it allows me to do everything, (with an expected delay of course), EXCEPT moving my character forward and backward.  I can rotate my character, but it is so slow that I sometimes forget which direction I told it to rotate, and I'm somewhat suspicious that it went the wrong way!  I asked a friend here at school who is a little into Linux, and he said to try using something called "Can You Run It?"  I tried to use it, but I need a Java update that I can't seem to install properly.
One of the main things I think may be affecting the performance is my incomplete updates to my Graphics drivers.  My update manager shows one update every time it opens, but the check-box can't be clicked; I don't know why.  I think it's an important update related to my graphics software, so any advice to point me towards an appropriate forum thread for these issues would be much appreciated.  Sorry if I went a little off topic from the context of DDO, but I though Jeek Elemental might want to know how our efforts together have been developing, and I trust he might have good pointers for me.  Thanks pal!  I owe you one for even getting this installed!

---

### Post by Jeek Elemental on 2012-03-26
type
```

glxinfo |grep direct

```

in a terminal and verify that it says "direct rendering: yes"

Switch off any antialiasing, both in the settings program for your card and inside ddo (below screenmode if I remember). You can try a lower screenmode aswell.

Run ddo from a terminal and check the log there after exiting ddo if theres any juicy error messages.

> **njrob said:**
> I have pretty much everything set as low as possible without turning everything into a blob in the fog.  I also am using the plain, "no frills" gnome desktop environment, and despite my dislike for it it seems to have helped a little with loading screen duration and a small amount of lag in the menus and game environment.
Despite all this, I have found that when I do enter the game, it allows me to do everything, (with an expected delay of course), EXCEPT moving my character forward and backward.  I can rotate my character, but it is so slow that I sometimes forget which direction I told it to rotate, and I'm somewhat suspicious that it went the wrong way!  I asked a friend here at school who is a little into Linux, and he said to try using something called "Can You Run It?"  I tried to use it, but I need a Java update that I can't seem to install properly.
One of the main things I think may be affecting the performance is my incomplete updates to my Graphics drivers.  My update manager shows one update every time it opens, but the check-box can't be clicked; I don't know why.  I think it's an important update related to my graphics software, so any advice to point me towards an appropriate forum thread for these issues would be much appreciated.  Sorry if I went a little off topic from the context of DDO, but I though Jeek Elemental might want to know how our efforts together have been developing, and I trust he might have good pointers for me.  Thanks pal!  I owe you one for even getting this installed!

---

### Post by njrob on 2012-04-04
> **Jeek Elemental said:**
> Run ddo from a terminal and check the log there after exiting ddo if theres any juicy error messages.

How do I run ddo in a terminal?  I can't seem to figure out how to ask it to run a file at the command line level.

---

### Post by buzzmandt on 2012-04-04
From command line terminal```
pylotro
```

---

### Post by njrob on 2012-04-05
> **buzzmandt said:**
> From command line terminal```
pylotro
```

```
neal@ubuntu:~$ pylotro
pylotro: command not found
neal@ubuntu:~$ sudo pylotro
[sudo] password for neal: 
sudo: pylotro: command not found
neal@ubuntu:~$
```

I'm not sure I'm doing this right at all!  lol

---

### Post by Jeek Elemental on 2012-04-05
You are probably using the windows version of pylotro, which is fine.
Note that you should never run wine as super user, it won't help anything and can really make a mess of things.

If your ddo install is in the default .wine directory just cd to there:

```
cd /home/$user/.wine/drive_c/Program\ Files/PyLotRO
```

Change this to your actual path.
Then run

```
wine pylotro.exe
```

If you have a separate directory for ddo, you must tell wine to use that:

```
WINEPREFIX=/home/$user/.yourddodir wine pylotro.exe
```



> **njrob said:**
> ```
neal@ubuntu:~$ pylotro
pylotro: command not found
neal@ubuntu:~$ sudo pylotro
[sudo] password for neal: 
sudo: pylotro: command not found
neal@ubuntu:~$
```

I'm not sure I'm doing this right at all!  lol

---

### Post by buzzmandt on 2012-04-08
Hmmm, interesting, i just installed and ran the windows version of pylotro.  once installed i clicked on it and it would not work.  however running it from command line worked and anyway i ran it from that point on worked (clicked or shortcutted from desktop).  But for some reason had to run it from command line first.  cd'd into the directory and the ran wine pylotro.exe.

for me this is:
```
cd ~/.wine/drive_c/Program\ Files/PyLotRO
wine pylotro.exe
```

---

### Post by njrob on 2012-04-09
Okay, thanks to the help you guys gave me, I ran pylotro in a terminal, and I copied the code before exiting.

```
neal@ubuntu:~$ cd ~/.wine/drive_c/Program\ Files/PyLotRO 
neal@ubuntu:~/.wine/drive_c/Program Files/PyLotRO$ wine pylotro.exe 
fixme:system:SetProcessDPIAware stub! 
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found 
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found 
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found 
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found 
fixme:win:FlashWindowEx 0x32e5ec 
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS 
fixme:imm:ImmReleaseContext (0x10066, 0x1c6d40): stub 
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub 
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS 
fixme:win:FlashWindowEx 0x32c54c 
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot 
fixme:toolhelp:Heap32ListFirst : stub 
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS 
fixme:win:FlashWindowEx 0x32ad84 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline 
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5) 
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5) 
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5) 
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5) 
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream 
Cannot connect to server socket err = No such file or directory 
Cannot connect to server socket 
jack server is not running or cannot be started 
err:d3d_surface:surface_modify_location Surface 0x18ee58 does not have any up to date location. 
err:d3d_surface:surface_modify_location Surface 0x18ee58 does not have any up to date location. 
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS 
fixme:win:FlashWindowEx 0x328d84 
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS 
fixme:win:FlashWindowEx 0x328d84 
neal@ubuntu:~/.wine/drive_c/Program Files/PyLotRO$ 
```

Can anyone here translate for me?  Thank you guys so much for getting me so far!

---

### Post by buzzmandt on 2012-04-09
just checking for sure,
You do have proprietary video drivers installed, yes?
you also ran the following in a terminal (or something close to it)
```
winetricks d3dx9 vcrun200{3,5,8}
```

and i looked throught this massive thread but couldn't find your computer specs, graphics card, ram, and cpu to be specific.

---

### Post by Jeek Elemental on 2012-04-09
> **njrob said:**
> 
err:d3d_surface:surface_modify_location Surface 0x18ee58 does not have any up to date location. 
[/CODE]


This sticks out, it was an issue in wine 1.4rc1 it seems.
Which version are you running now?

---

### Post by Jeek Elemental on 2012-04-09
> **buzzmandt said:**
> you also ran the following in a terminal (or something close to it)
```
winetricks d3dx9 vcrun200{3,5,8}
```


No winetricks needed anymore, if using up to date wine (>1.337 approximately).

---

### Post by buzzmandt on 2012-04-09
> **Jeek Elemental said:**
> No winetricks needed anymore, if using up to date wine (>1.337 approximately).

That is awesome. Thank u for this information

---

### Post by njrob on 2012-04-11
Kk, I checked my Wine version, and it is up to date.  I have something that isn't updating or upgrading or whatever when I run 'sudo apt-get update' and 'sudo apt-get upgrade'.  I'm not sure if it's related or not, but my update manager window also shows one Xorg driver update that I can't click the checkbox on, and I think it might be cramping my graphics performance.  Any sage advice with this added information?  Thanks so much for your patience and support!

---

### Post by Jeek Elemental on 2012-04-12
Hard to say, you could try using the Synaptic package manager instead, maybe it gives more information on what the problem is.
Theres also a "repair broken packages" option there you can try.

> **njrob said:**
> Kk, I checked my Wine version, and it is up to date.  I have something that isn't updating or upgrading or whatever when I run 'sudo apt-get update' and 'sudo apt-get upgrade'.  I'm not sure if it's related or not, but my update manager window also shows one Xorg driver update that I can't click the checkbox on, and I think it might be cramping my graphics performance.  Any sage advice with this added information?  Thanks so much for your patience and support!

---

### Post by njrob on 2012-04-14
I installed Synaptic, and fiddled a little with my driver packages and such.  I think what I've discovered is that I am missing a dependency for at least one of the driver programs that may be affecting DDO's performance, but I don't know what package contains the specific dependency I'm missing.  The Synaptic error message kept telling me that to upgrade the Openchrome driver package, I needed a missing dependency for it called xorg-video-abi-10, or something like that.  It's too foreign for me to understand exactly what's wrong, but what I've done seems to have made Tuc Racer perform a bit more smoothly.  I guess I'll just need to wait for more updates from Xorg-Edgers or find out if the network latency in DDO is caused by something else.  Thoughts & suggestions?

---

### Post by Jeek Elemental on 2012-04-14
Synaptic (and update manager) will pull in any dependencies IF it is available.
This is getting far away from DDO tho, I think to keep the thread useful for others we should stop here.

Feel free to pm me and I can google abit for you, include the output from the following commands please:
lspci
glxinfo (top 10 lines)
wine --version
dmesg


> **njrob said:**
> I installed Synaptic, and fiddled a little with my driver packages and such.  I think what I've discovered is that I am missing a dependency for at least one of the driver programs that may be affecting DDO's performance, but I don't know what package contains the specific dependency I'm missing.  The Synaptic error message kept telling me that to upgrade the Openchrome driver package, I needed a missing dependency for it called xorg-video-abi-10, or something like that.  It's too foreign for me to understand exactly what's wrong, but what I've done seems to have made Tuc Racer perform a bit more smoothly.  I guess I'll just need to wait for more updates from Xorg-Edgers or find out if the network latency in DDO is caused by something else.  Thoughts & suggestions?

---

### Post by EEOregonEEDave on 2012-07-18
I am having no problems with making the os take the appropriate changes to run the game.  I am however having an issue with finding "ajackson-public.key" because lotrolinux seems to have breached TOS with his host or something else causing his links to be dead.  If anyone has an ftp, link, copy to email me, or some other solution please let me know!  Much appreciated in advance.  
~Dave

---

### Post by Jeek Elemental on 2012-08-02
I see lotrolinux.com is expired, maybe he forgot to renew or something.
Give it a couple days to see if it pops up again, not seen any posts by ajackson so hopefully nothing serious.

---

### Post by buzzmandt on 2012-08-04
here's a link to a windows version: [http://www.mcgillsociety.org/PyLotRO/index.html#PYLOTRO](http://www.mcgillsociety.org/PyLotRO/index.html#PYLOTRO) which also works in playonlinux/ddo nicely

---

### Post by Jeek Elemental on 2012-08-22
Thanks buzzmandt, putting link in first post, not sure whats going on with lotrolinux.com

Edit: seems first post is too old to edit.

> **buzzmandt said:**
> here's a link to a windows version: [http://www.mcgillsociety.org/PyLotRO/index.html#PYLOTRO](http://www.mcgillsociety.org/PyLotRO/index.html#PYLOTRO) which also works in playonlinux/ddo nicely

---

### Post by peacewithall on 2012-08-29
There is also the pylotro PPA, [https://launchpad.net/~ajackson-bcs/+archive/ppa](https://launchpad.net/~ajackson-bcs/+archive/ppa), if you wanted the current linux native build.

---

### Post by sabersong on 2012-10-19
I'm having problems with Pylotro. I installed it from the ppa this morning, following the instructions at winehq. I set the path to the game directory, but it seems to have trouble with a space in the path. The Wine output screen reads:

 ```
Argument 'Unlimited/client_local_English' unknown
```

The path name includes "DDO Unlimited", and this seems to be where the problem is.

I tried going into the path and adding the backslashes (or forward slashes --- I can never keep the names straight) as escape characters, but then pylotro can't find the game directory at all.

I did find a reference to this exact problem in another post (a very, very long Lord of the Rings Online topic), but no solution was suggested.

I've also tried the Windows version of Pylotro, but it just hangs at a blank output screen.

Any suggestions on how to solve this would be much appreciated.

Wine version 1.4
(K)ubuntu 12.04 x64
Python version 2.73

---

### Post by Jeek Elemental on 2012-11-12
Not sure what the problem is, the path is correct or it wouldn't find the ddo .exe, which the error message suggests it does.

Is it in a clean .wine dir? Windows version of pylotro should run.
You could try moving ddo, and run it through the Z: drive.

---

### Post by sabersong on 2012-11-12
The windows version of pylotro did eventually start working, and I got into the game. No idea why.

---

### Post by Synoc on 2012-11-28
Yesterday, I tried to log onto DDO, worked fine except I couldn't connect to the server after logging into my account (using PyLotRO). So figuring I needed an update, I proceeded to patch. I was right, it did need a patch, except now, since the patch has finished, the DDO client crashes. included is the entire "serious problem" error
```

Unhandled exception: page fault on write access to 0x00000030 in 32-bit code (0x00674622).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00674622 ESP:0033fd1c EBP:0132446c EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:00000000 ECX:00000405 EDX:00000001
 ESI:0177ca78 EDI:0177ca78
Stack dump:
0x0033fd1c:  0177c908 00000405 00000208 00684d5b
0x0033fd2c:  0125e9e4 012452f8 0033fda8 7da4fff4
0x0033fd3c:  00f9a28c 00f9a29f 00000017 0177c908
0x0033fd4c:  0033fe20 0108f98b 00000013 010fda6a
0x0033fd5c:  7d9f70f2 00000000 00000000 00000000
0x0033fd6c:  00000000 00000000 7f22937e 000000b0
Backtrace:
=>0 0x00674622 in dndclient (+0x274622) (0x0132446c)
0x00674622: movl	%ecx,0x30(%eax)
Modules:
Module	Address			Debug info	Name (129 modules)
PE	  340000-  3c7000	Deferred        umbra
PE	  3d0000-  3e5000	Deferred        vorbisfile
PE	  3f0000-  3fd000	Deferred        ogg
PE	  400000- 1940000	Export          dndclient
PE	 1940000- 1a76000	Deferred        vorbis
PE	 1a80000- 2fa7000	Deferred        awesomium
PE	10000000-10012000	Deferred        zlib1t
PE	12000000-121c6000	Deferred        xerces-c_2_6
PE	18000000-18033000	Deferred        binkw32
PE	3b400000-3b41e000	Deferred        steam_api
ELF	7a163000-7b800000	Deferred        libnvidia-glcore.so.260.19.06
ELF	7b800000-7ba16000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba16000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
ELF	7d18a000-7d224000	Deferred        libgnutls.so.26
ELF	7d7b6000-7d7bb000	Deferred        libgpg-error.so.0
ELF	7d7bb000-7d82f000	Deferred        libgcrypt.so.11
ELF	7d82f000-7d840000	Deferred        libtasn1.so.3
ELF	7d91d000-7d951000	Deferred        uxtheme<elf>
  \-PE	7d920000-7d951000	\               uxtheme
ELF	7d957000-7d972000	Deferred        wsock32<elf>
  \-PE	7d960000-7d972000	\               wsock32
ELF	7d972000-7d9a1000	Deferred        msvcr90<elf>
  \-PE	7d980000-7d9a1000	\               msvcr90
ELF	7d9a1000-7d9cc000	Deferred        msvcr80<elf>
  \-PE	7d9b0000-7d9cc000	\               msvcr80
ELF	7d9cc000-7da59000	Deferred        msvcrt<elf>
  \-PE	7d9e0000-7da59000	\               msvcrt
ELF	7da59000-7db3e000	Deferred        msvcp90<elf>
  \-PE	7da80000-7db3e000	\               msvcp90
ELF	7db3e000-7dbe7000	Deferred        msvcp80<elf>
  \-PE	7db50000-7dbe7000	\               msvcp80
ELF	7dbe7000-7dc1f000	Deferred        usp10<elf>
  \-PE	7dbf0000-7dc1f000	\               usp10
ELF	7dc1f000-7dc78000	Deferred        riched20<elf>
  \-PE	7dc30000-7dc78000	\               riched20
ELF	7dc78000-7dc98000	Deferred        oleacc<elf>
  \-PE	7dc80000-7dc98000	\               oleacc
ELF	7dc98000-7dcca000	Deferred        ws2_32<elf>
  \-PE	7dca0000-7dcca000	\               ws2_32
ELF	7dcca000-7dcde000	Deferred        libresolv.so.2
ELF	7dcf1000-7dd13000	Deferred        iphlpapi<elf>
  \-PE	7dd00000-7dd13000	\               iphlpapi
ELF	7dd13000-7dd3e000	Deferred        netapi32<elf>
  \-PE	7dd20000-7dd3e000	\               netapi32
ELF	7dd3e000-7dd6a000	Deferred        secur32<elf>
  \-PE	7dd40000-7dd6a000	\               secur32
ELF	7dd6a000-7dd7e000	Deferred        psapi<elf>
  \-PE	7dd70000-7dd7e000	\               psapi
ELF	7dd7e000-7de47000	Deferred        libgl.so.1
ELF	7de47000-7df00000	Deferred        opengl32<elf>
  \-PE	7de60000-7df00000	\               opengl32
ELF	7df00000-7df4d000	Deferred        libopenal.so.1
ELF	7df60000-7df7b000	Deferred        openal32<elf>
  \-PE	7df70000-7df7b000	\               openal32
ELF	7df7b000-7dfbf000	Deferred        dsound<elf>
  \-PE	7df80000-7dfbf000	\               dsound
ELF	7dfbf000-7dfc9000	Deferred        libxcursor.so.1
ELF	7dfd1000-7dfda000	Deferred        librt.so.1
ELF	7e03c000-7e063000	Deferred        libexpat.so.1
ELF	7e063000-7e093000	Deferred        libfontconfig.so.1
ELF	7e093000-7e0a1000	Deferred        libxi.so.6
ELF	7e0a1000-7e0a7000	Deferred        libxfixes.so.3
ELF	7e0a7000-7e0ab000	Deferred        libxcomposite.so.1
ELF	7e0ab000-7e0b3000	Deferred        libxrandr.so.2
ELF	7e0b3000-7e0bd000	Deferred        libxrender.so.1
ELF	7e0bd000-7e0c3000	Deferred        libxxf86vm.so.1
ELF	7e0c3000-7e0c7000	Deferred        libxinerama.so.1
ELF	7e0c7000-7e0e1000	Deferred        libxcb.so.1
ELF	7e0e1000-7e1fe000	Deferred        libx11.so.6
ELF	7e1fe000-7e20e000	Deferred        libxext.so.6
ELF	7e20e000-7e227000	Deferred        libice.so.6
ELF	7e22b000-7e22d000	Deferred        libnvidia-tls.so.260.19.06
ELF	7e23a000-7e2ce000	Deferred        winex11<elf>
  \-PE	7e240000-7e2ce000	\               winex11
ELF	7e2ce000-7e2e3000	Deferred        libz.so.1
ELF	7e2e3000-7e35a000	Deferred        libfreetype.so.6
ELF	7e35a000-7e380000	Deferred        d3dxof<elf>
  \-PE	7e360000-7e380000	\               d3dxof
ELF	7e380000-7e3d5000	Deferred        d3dcompiler_43<elf>
  \-PE	7e390000-7e3d5000	\               d3dcompiler_43
ELF	7e3d5000-7e43e000	Deferred        d3dx9_36<elf>
  \-PE	7e3e0000-7e43e000	\               d3dx9_36
ELF	7e43e000-7e458000	Deferred        d3dx9_42<elf>
  \-PE	7e440000-7e458000	\               d3dx9_42
ELF	7e458000-7e550000	Deferred        comctl32<elf>
  \-PE	7e460000-7e550000	\               comctl32
ELF	7e550000-7e5ba000	Deferred        shlwapi<elf>
  \-PE	7e560000-7e5ba000	\               shlwapi
ELF	7e5ba000-7e7ca000	Deferred        shell32<elf>
  \-PE	7e5d0000-7e7ca000	\               shell32
ELF	7e7ca000-7e8bc000	Deferred        oleaut32<elf>
  \-PE	7e7e0000-7e8bc000	\               oleaut32
ELF	7e8bc000-7e8de000	Deferred        imm32<elf>
  \-PE	7e8c0000-7e8de000	\               imm32
ELF	7e8de000-7e906000	Deferred        msacm32<elf>
  \-PE	7e8e0000-7e906000	\               msacm32
ELF	7e906000-7e97b000	Deferred        rpcrt4<elf>
  \-PE	7e910000-7e97b000	\               rpcrt4
ELF	7e97b000-7ea81000	Deferred        ole32<elf>
  \-PE	7e990000-7ea81000	\               ole32
ELF	7ea81000-7ea9a000	Deferred        version<elf>
  \-PE	7ea90000-7ea9a000	\               version
ELF	7ea9a000-7eb57000	Deferred        gdi32<elf>
  \-PE	7eab0000-7eb57000	\               gdi32
ELF	7eb57000-7ec97000	Deferred        user32<elf>
  \-PE	7eb70000-7ec97000	\               user32
ELF	7ec97000-7ed44000	Deferred        winmm<elf>
  \-PE	7eca0000-7ed44000	\               winmm
ELF	7ed44000-7eda4000	Deferred        advapi32<elf>
  \-PE	7ed50000-7eda4000	\               advapi32
ELF	7eda4000-7edb0000	Deferred        libnss_files.so.2
ELF	7edb0000-7edc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7efee000-7eff4000	Deferred        libxdmcp.so.6
ELF	7eff4000-7eff9000	Deferred        libuuid.so.1
ELF	b7530000-b7534000	Deferred        libxau.so.6
ELF	b7534000-b753f000	Deferred        libnss_nis.so.2
ELF	b7540000-b7544000	Deferred        libdl.so.2
ELF	b7544000-b76a1000	Deferred        libc.so.6
ELF	b76a2000-b76bc000	Deferred        libpthread.so.0
ELF	b76bd000-b76c6000	Deferred        libsm.so.6
ELF	b76c6000-b76ce000	Deferred        libnss_compat.so.2
ELF	b76cf000-b7810000	Dwarf           libwine.so.1
ELF	b7812000-b7830000	Deferred        ld-linux.so.2
ELF	b7830000-b7831000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001a    0
	00000019    0
	00000014    0
	00000013    0
0000001b plugplay.exe
	00000020    0
	0000001d    0
	0000001c    0
00000021 explorer.exe
	00000022    0
00000023 pylotro.exe
	00000027    0
	00000026    0
	00000024    0
00000036 (D) C:\Program Files\DDO Unlimited\dndclient.exe
	00000038    0
	00000037    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 2.6.35-32-generic-pae

```
once again, before patch it worked (well I got further), after the patch, I get a crash.

---

### Post by Jeek Elemental on 2012-11-29
Yes it happened to everyone, its a known bug(ish) in wine versions <1.5.15 that the ddo patch exposed.
Upgrade to latest wine and it should be fine (see op).

---

### Post by Synoc on 2012-11-29
added the wine ppa. but I can't install wine1.5

could not find any package by regex 'wine1.5'

---

### Post by Jeek Elemental on 2012-11-29
Strange, did you reload package list after adding repo?
Its actually 1.5.18 now but the pack is called wine1.5.

If you use synaptic try the origin view and check that packages are pulled from ubuntu-wine/ppa (shows as LP-PPA-ubuntu-wine/precise in origin, if you use precise ofcourse).

---

### Post by Synoc on 2012-11-29
installed is:

wine 1.3 (which is 1.4-0ubuntu1 installed) wine1.3-gecko, winetricks, ttf-symbol-replacement-wine, and wine (1.2.3-0ubuntu1 installed)

incidently, I have this same problem on 10.10 and 10.04 and wine 1.4  OR wine 1.5 is not an option

---

### Post by Jeek Elemental on 2012-11-30
Support for older ubuntus is spotty from the ppa, check here:
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

You can always compile it yourself, its not hard and plenty of guides available!

---

### Post by Synoc on 2012-11-30
my luck with compiling anything has been horrid to say the least. and if I'm not going to be able to get support going forth it hardly seems worth it to put forth the effort. 10.04 is still a supported OS for a few more months if it's not getting support now from the ppa I might as well scrap it all until I find out which OS I'm going to have to upgrade to. Unity/Gnome3 aren't even in the running for DEs and only mate even stands a chance. But how does using basically gnome 2 affect wine if gnome 2 for all intents and purposes is now defunct?

---

### Post by Jeek Elemental on 2012-12-01
Well give it a try:
[http://wiki.winehq.org/FAQ#compile_wine](http://wiki.winehq.org/FAQ#compile_wine)
Run it from the dir you compiled in instead of doing "make install" and it won't interfere with package systems wine.

As for desktop environment I think its better to discuss elsewhere, you have lots of choices tho.

---

### Post by Synoc on 2012-12-04
well the ```
sudo apt-get build-dep wine1.3
```
doesn't work (step one)it gets worse from there. 
```
./configure
```
I assume works 
```
make
```
does not.
```
make: *** No targets specified and no makefile found.  Stop
```
and ```
 sudo make install
``` 
doesn't work.
```
./tools/wineinstall
``` fails because I don't have flex, I install flex and it says I don't have bison, I install bison and get further before it fails it says I don't have X... which is ironic since I am using it from my terminal window in gnome 2... that's when I gave up

---

### Post by Synoc on 2012-12-10
upgraded to 12.04... Gave up on trying to get DDO to work on 10.10 or even 10.04. After updating to 12.04 it is working. upon reflection, I might have been able to simply change the ubuntu version INSIDE the PPA to say "precise" and it would have worked. Since the wine PPA doesn't offer updates for 10.10 or 10.04 anymore. I may yet try this on my other system just to find out what happens.

---

### Post by jokenkil on 2013-05-14
i have installed ddo on the acer c7 chromebook hoping to be able to play it but when i try to play it through the pylotro it comes up with this "Unhandled exception: page fault on write access to 0x00000030 in 32-bit code (0x00674b92)." anybody can help?

---

### Post by Jeek Elemental on 2013-06-07
> **jokenkil said:**
> i have installed ddo on the acer c7 chromebook hoping to be able to play it but when i try to play it through the pylotro it comes up with this "Unhandled exception: page fault on write access to 0x00000030 in 32-bit code (0x00674b92)." anybody can help?

Quick look at c7 specs, I don't think it will be able to run ddo I'm afraid. You need an amd or nvidia 3d part realistically, with their driver.

---

### Post by DDalton1977 on 2013-11-25
Help. I did what you guys said but it lead me to a site that was written in some type of.........Asian language.

---

### Post by Beren Camlost on 2013-11-26
The lotrolinux.com site is discontinued but you can find the launcher program still at [https://github.com/Lynx3d/pylotro](https://github.com/Lynx3d/pylotro)

---

