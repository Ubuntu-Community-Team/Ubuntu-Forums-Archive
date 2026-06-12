---
title: "Call of Duty: Modern Warfare 2"
date: 2009-11-13
forum: Wine
---

### Post by hype on 2009-11-13
Hi there,
i'm starting this thread after following this one [http://ubuntuforums.org/showthread.php?t=1319196](http://ubuntuforums.org/showthread.php?t=1319196)

So here is the issue:
i purchased COD: modern warfare 2 and downloaded it through steam using wine 1.1.32.

If i choose to start the game, i get a quite minimalist error message
"Installation incomplete", with the following url: [https://support.steampowered.com/kb_article.php?ref=9851-PFHN-9932&l=french](https://support.steampowered.com/kb_article.php?ref=9851-PFHN-9932&l=french)

I followed this guide, which provides infos about ports to open on your routeur in order to have steam network working properly: same error message.

 Lastly, i tried to start steam in "offline" mode:
after stating the game, i dont get the error about "incomplete installation", some plugins or components are installed, and it then stucks at directX installation.

Anyhow, the game wont start.

Note: i've just finished COD4 modern warfare on this same wine installation a few days ago, and it works like a charm.

---

### Post by hype on 2009-11-14
Good news !

After following these steps
> from console run &#8220;wine regedit&#8221; and then:
- in HKEY_CURRENT_USER-Software-Wine create, if it's doesn't already exists, a new key named Direct3D
- in Direct3D create the following strings with the following values:
string: DirectDrawRenderer          value: opengl
string: OffscreenRenderingMode  	value: fbo
string: RenderTargetLockMode    	value: auto
string: UseGLSL                           value: readtex
string: VideoMemorySize	            	value: (memory size of your graphic card)om winedb COD's page:

and **installing latest wine 1.1.33 **update through wine ppa team, the game works perfectly !

I play at 1680*1050 without issues.

Just small glitch i have noticed, sometimes i get a black screen while videos are playing background (i can hear the sound of the scene): just quickly press alt-tab and click on-screen, you'll get back to the game.

 I didnt test multiplayer yet.

---

### Post by beastrace91 on 2009-11-14
Good to know! I might have to pick this one up then... What is your frame rate like in game? Also be sure to add a post to the [appdb](appdb.winehq.org/) if you haven't already.

~Jeff

---

### Post by BAMF1501 on 2009-11-15
> **hype said:**
> Good news !

After following these steps


and **installing latest wine 1.1.33 **update through wine ppa team, the game works perfectly !

I play at 1680*1050 without issues.

Just small glitch i have noticed, sometimes i get a black screen while videos are playing background (i can hear the sound of the scene): just quickly press alt-tab and click on-screen, you'll get back to the game.

 I didnt test multiplayer yet.

create some registry files that are easy to add

---

### Post by K7522 on 2009-11-16
I attempted all of these solutions without succcess, I am still unable to play this game due to the same error. Any additional insight would be wonderful. Running Ubuntu 9.10 and Wine 1.1.33.

---

### Post by madone1 on 2009-11-16
I get this error when i try to install MW2 (Wine-1.1.33) ```
Runtime Error (at-1;o):
Cannot Import dll:C:\windows\temp\is-65JOQ.tmp\isskin.dll
```

---

### Post by beastrace91 on 2009-11-16
Trying finding a "isskin.dll" from somewhere else and dropping it into your **~/.wine/drive_c/windows/system32** folder and then setting it to a native DLL override in the WineCFG

Regards,
~Jeff

---

### Post by K7522 on 2009-11-16
Going back to the OP, I also just completed an attempt to install the game on a Windows platform and transferred the game over the network with the same error as before.

---

### Post by hnic on 2009-11-16
Can someone write out some clear step by step instruction on how to install this game on ubuntu 9.10 maybe some screenshots to be sure we are installing it correctly. Windows SUCKS!!!

---

### Post by hnic on 2009-11-16
What am I missing?

wine 1.1.33 installed

installation via winetricks of:
corefonts
d3dx9
dotnet20
ie6 
mfc42

DirectDrawRenderer value: opengl
string: OffscreenRenderingMode value: fbo
string: RenderTargetLockMode value: auto
string: UseGLSL value: readtex
string: VideoMemorySize value: (512)
[ATTACH]136542[/ATTACH]

---

### Post by beastrace91 on 2009-11-17
Trying right-clicking on COD:MW2 and selecting properties and tell it to "verify game data" - if that checks out ok and it still does not work try reinstalling the game (I know its a big download but it's worth a shot)

Regards,
~Jeff

---

### Post by K7522 on 2009-11-17
> **beastrace91 said:**
> Trying right-clicking on COD:MW2 and selecting properties and tell it to "verify game data" - if that checks out ok and it still does not work try reinstalling the game (I know its a big download but it's worth a shot)

Regards,
~Jeff

Verify game data does not resolve the issue. I have also installed this game three times; once via CD's, once via steam installer, and once via CD's to a windows computer, checked to ensure it worked there (it does), and then I transferred the files via the network.

The only solution I have found thus far to actually play the game is to download a no-steam mod to the single player. Still, I didn't buy the game to play SP over and over.

> **hnic said:**
> What am I missing?

wine 1.1.33 installed

installation via winetricks of:
corefonts
d3dx9
dotnet20
ie6 
mfc42

DirectDrawRenderer value: opengl
string: OffscreenRenderingMode value: fbo
string: RenderTargetLockMode value: auto
string: UseGLSL value: readtex
string: VideoMemorySize value: (512)
[ATTACH]136542[/ATTACH]

I have attempted all of these as well without success. It's not a game issue since it works with a no-steam mod. It's a Steam issue. I still have not figured out how to get the game working in steam.

---

### Post by hnic on 2009-11-17
I don't understand how others can get this to work but i can't. Either they are making it up or I must be missing something.

---

### Post by K7522 on 2009-11-17
> **hnic said:**
> I don't understand how others can get this to work but i can't. Either they are making it up or I must be missing something.

You can get single player working by installing a no steam crack, but chances are at some point that will get your legit game version banned. I hear that you can get multiplayer working with a crack as well, but I haven't got that one working even with a new empty steam account.

---

### Post by BAMF1501 on 2009-11-18
i still get incomplete installation :(  doesnt make no sense and i got all file sinstalled and checked interagity

---

### Post by griachae on 2009-11-18
Hey i followed your thread and i got a different problem with installing MW2:

When i open the setup.exe file it tells me "failed to run install script"
What does that mean?

---

### Post by hnic on 2009-11-18
UPDATE!!!

Like most said before this game does work ONLY if you have a no steam crack (SKIDROW). The fps SUCK!! but it works. I have a Dell M4300 Core 2 duo, 512 video card (NV), and 3gb of ram.

HAPPY Gaming

---

### Post by koldrakan on 2009-11-18
I'm trying to install the skidrow-version as well. wine won't even start the installation, all I get is a small error message telling me that the installer failed to load isskin.dll.....

the problem ios that I CANNOT FIND this file :P it's totally absent from the system32-catalog on WinXp-installation I checked. I cant find it online either. 
to the best of my google-powers, all I can find is that this .dll is somehow linked to the very design of the installer walkthrough..

Any thoughts anyone?

---

### Post by hype on 2009-11-18
After an update to both single and multi player, the game doesnt start anymore.

Modern warfare 1 still works on my steam install, both were bought, i mean legally and all on steam. I'm quite sure that it's a steam issue as i did play the game with no issues with the same version of wine and registry settings.

---

### Post by hnic on 2009-11-18
I install MW2 with a non hacked version disc then replaced the SP and MP.exe with skidrow files.

---

### Post by K7522 on 2009-11-22
This does not help with multiplayer gaming though, which is why many people purchase these kinds of games. Do we have any playability at all yet with Steam and Multiplayer mode? (Steam did patch the no-cd crack).

It's sad that people who have purchased the game through legit means have to use a crack to even play the game.

---

### Post by yester64 on 2009-11-23
i will try wine now. If i can get this game running (and any other) i can dumb my windows finally.

---

### Post by Fenrir121 on 2009-11-24
Has anyone made any head way on this? I feel like I am taking crazy pills.

I have tried so many things from Wine and Wine Bottler (I am on a Mac), to CrossoverGames which was worthless. Any tips? 

I am running a legit version of steam with a copy of the game I paid for. I have D/L'ed the game files twice so it is unlikely that they are corrupt. But when I click on "Launch" I keep getting the same error: "Incomplete installation of [COD MW2]" and then in parenthesis either a (55), (53) or a (2), and then a link to the support site. Ahhhhhh!

Winetricks options on:

corefonts
d3dx9
dotnet20
ie6 
mfc42

Can anyone shed some light?

---

### Post by Aspras on 2009-11-25
> **madone1 said:**
> I get this error when i try to install MW2 (Wine-1.1.33) ```
Runtime Error (at-1;o):
Cannot Import dll:C:\windows\temp\is-65JOQ.tmp\isskin.dll
```

Same here

---

### Post by Wazupio on 2009-11-26
Having the same error as the user above me.
I have installed all the program's you have to, but still I can't get it to work.

Anyone got any idea's?

//Edit
For people with the same error I got;
```

Runtime Error (at-1;o);
Cannot Import dll:C:\windows\temp\is-65J0Q.tmp\isskin.dll

```Ok, now I found something, which worked for me, not sure what i'm doing but found it on the French ubuntu website.


**Important**
You gotta have winetricks installed!

Step one;
```

sh winetricks mfc42

```Step two;
```

sh winetricks vcrun6

```Step three;
```

cabextract -F mfc42.dll vcredist.exe

```Now I haven't made this up by myself, so all credits go to Bricolojack from [http://forum.ubuntu-fr.org/viewtopic.php?pid=3071729](http://forum.ubuntu-fr.org/viewtopic.php?pid=3071729).

P.S.
If anyone is able to transulate the page it would be nice!

---

### Post by digital-import on 2009-11-26
> **griachae said:**
> Hey i followed your thread and i got a different problem with installing MW2:

When i open the setup.exe file it tells me "failed to run install script"
What does that mean?

Hi Griachae,

This error will occur if you are running the setup.exe file from "/media/cdrom0".

You will need to run setup.exe from the Wine D: drive, which by default is set up as "/home/username/.wine/dosdevices/d:"

Easy way to do this is:

1. Go to Applications>Wine>Browse C:\Drive
2. In the newly opened window, go to location and replace the c: with d:

[IMG]http://www.overclockers.com.au/pix/image.php?id=anzr3&f=1[/IMG]

3. Right click on setup.exe and select "Open with Wine Windows Program Loader"

This should get it running without that error message occuring. Hope it helps ;)

---

### Post by beefcurry on 2009-11-27
Max over at appdb found a nice solution

> Thanks for the creator of this patch. 
Left 4 Dead 2 has the same problem that CoD6, the error message : 
(53) Incomplete Installation. 
appdb.winehq.org/objectManager.php?sClass=version&iId=18408 

So, i compiled wine 1.1.33 and i moved the file patched and it's works. 
Solo + Multiplayer. 

So, download this file : 
hotfile.com/dl/18516885/0d1e877/PatchCod6.zip.html 

And move the file in /usr/lib/wine in root.

I've tried it and it works with the patched file.

---

### Post by DAVVVVE on 2009-11-29
> **beefcurry said:**
> Max over at appdb found a nice solution



I've tried it and it works with the patched file.


And move the file in /usr/lib32 if u have 64 bit a assume 

Thanks

---

### Post by jacebenson on 2009-11-30
How do I apply the patch (ubuntu 9.10 wine 1.1.33)? 

Where do I place the file.  When I run the patch *'patch -p1 < ~/steam_hack.diff'* it says it *'can't find file to patch at input line 5'*, which refers to an *'a/dlls/imagehlp/integrity.c'* and *'b/dlls/imagehlp/integrity.c'*.

---

### Post by unforeseen123 on 2009-12-01
That patched worked for me, I can now run the game.

I now have a new issue with the fonts in the menu (look at attached image)

Anyone got any ideas how to fix it?



**To install the patch:**
You need to download the wine source, apply the patch, make it and install it. (I googled for instructions how to do this). You must use the source for wine1.1.33.

---

### Post by yester64 on 2009-12-01
> **unforeseen123 said:**
> That patched worked for me, I can now run the game.

I now have a new issue with the fonts in the menu (look at attached image)

Anyone got any ideas how to fix it?



**To install the patch:**
You need to download the wine source, apply the patch, make it and install it. (I googled for instructions how to do this). You must use the source for wine1.1.33.

I am actually looking for a patch. Does this patch work for 64bit and also steam?
If you can, just post the link. I tried last time the instruction in the wine wiki and it did not work for me.
thank you.

---

### Post by unforeseen123 on 2009-12-01
> **yester64 said:**
> I am actually looking for a patch. Does this patch work for 64bit and also steam?
If you can, just post the link. I tried last time the instruction in the wine wiki and it did not work for me.
thank you.
[http://bugs2.winehq.org/attachment.cgi?id=24845](http://bugs2.winehq.org/attachment.cgi?id=24845)

I'm on 64bit, I installed from CD but ran from steam.

---

### Post by yester64 on 2009-12-02
> **jacebenson said:**
> How do I apply the patch (ubuntu 9.10 wine 1.1.33)? 

Where do I place the file.  When I run the patch *'patch -p1 < ~/steam_hack.diff'* it says it *'can't find file to patch at input line 5'*, which refers to an *'a/dlls/imagehlp/integrity.c'* and *'b/dlls/imagehlp/integrity.c'*.

Download the source from
[http://sourceforge.net/projects/wine/files/Source/](http://sourceforge.net/projects/wine/files/Source/)

Then unpack it to a folder of your choice. Mine was 'src' in my homefolder
Copy your patches into that folder and do the following.

Open your terminal in that folder or change to it and type this in.

patch -p1 < your patch file name
./configure
make depend && make
sudo make install


There are two patches i used.
Steam Hack is from the wine hq site, the other one is from this thread.
I used them both and have to check out if it does what it supposed to do.

Hope that helps.

---

### Post by hnic on 2009-12-02
NICE!!!

I got the game running smoothly, framerates are ok the sound works great,single player and MP works BUT!!! the in game steam does not. cant invite friends to play. Does anyone have a work around or know how to fix this issues?

---

### Post by unforeseen123 on 2009-12-02
what patches did you use? whats your wine configuration/version?

@yestur64 what does that other patch do? I dont suppose you know anything about my font issue? (installing that other patch didnt help my issue)

---

### Post by yester64 on 2009-12-02
> **unforeseen123 said:**
> what patches did you use? whats your wine configuration/version?

@yestur64 what does that other patch do? I dont suppose you know anything about my font issue? (installing that other patch didnt help my issue)

Nah, i am not a crack really in this. I just try to work it out.

Well, the patch with the name Freetype supposed to solve the problem with crashing. As an example, you start the game and it lets you play for 1 minute or so and then it freezes and boom, its gone. Happened a lot to me with CSS. 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

> Runs well after recompiling wine with small source modifications.  Without this the hl2.exe crashes within seconds of joining a server.  You can view the patch I used at [http://home.comcast.net/~vivnet/freetype.patch]("http://home.comcast.net/%7Evivnet/freetype.patch")

After patching the game runs with no crashes except on some servers after clicking OK on the MOTD screen.

It is possible that this is somehow related to my hardware as I have noticed that users with more recent GFX cards have not mentioned needing changes to avoid constant crashing.

Using Nvidia 180.60 non-distribution drivers as the 185.xx and 190.xx series causes hl2.exe to crash on exit.

Tested on Nvidia 6800 GS in directx 8.1 mode.

Rating Silver generously as the game is Garbage without modifying freetype.
The other patch is also for steam.
[http://bugs2.winehq.org/attachment.cgi?id=24845](http://bugs2.winehq.org/attachment.cgi?id=24845)
but i don't have any comments on it. I just took it too.

Not sure about the font, but i think there is winetricks which could help, i assume. Haven't installed it myself but i know the problem. Some fonts look funny, altough it does not bother me that much.

Hope that helped.

---

### Post by yester64 on 2009-12-02
can tell so far. It did not work for me. I'll have to try again.

---

### Post by hype on 2009-12-06
I just tried to recompile wine using latest version  [http://www.winehq.org/announce/1.1.34](http://www.winehq.org/announce/1.1.34) .

All works fine, even the multi !
No need to patch anymore.

---

### Post by blob84 on 2009-12-23
I have ubuntu 9.04 and wine 1.1.34 and the game start but is very slow!
How works on 9.10?

---

### Post by SwiftNano on 2009-12-30
Hi All, 

I am having a few problems getting this working and wondered if anyone could help. The installation went fine however when I launch the game I get the following error. 

----- Client Initialization Complete ----- 
Attempting 44 kHz 16 bit [Windows default] sound 
ERROR: Couldn't initialize digital driver: DirectSoundCreate() failed in get_system_speaker_configuration() 


Error during initialization: 
Miles sound system initialization failed. 
Make sure you have your sound card's latest drivers and DirectX installed. 

Any help would be greatly appreciated. 

Wine: 1.1.34 
MB: Gigabyte EX58-UD3R 
Sound: Onboard HDA Intel 7.1 
CPU: Core i7 
GPU: Ati (soon to be replaced with a Nvidia)

---

### Post by countervail on 2010-01-01
Hey guys,

I have installed CoD:MW2 through wine (wine-1.1.35) and MP and SP works just fine without any modifications.

The only 2 problems I have are:

1. No true full screen (I can see the top and bottom taskbars)

2. The mouse cursor is the desktop cursor, I can only use the mouse buttons i.e : fire and zoom, but no movements with the mouse.

Update:

3. Sound cluttering, is there anything I can do to get the game sounds smooth?

I am sorry if the information I provided is insufficient, I am new to ubuntu :)

Cheers and happy new year!

---

### Post by SwiftNano on 2010-01-04
> **countervail said:**
> Hey guys,


2. The mouse cursor is the desktop cursor, I can only use the mouse buttons i.e : fire and zoom, but no movements with the mouse.

Cheers and happy new year!

I can help with this point. There appears to be a bug in version .35 revert to .34 and the desktop cursor problem will be fixed. The discussion for this can be found at wineHQ 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18348&iTestingId=47243](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18348&iTestingId=47243)

I have several other problems (see my post above) I am beginning to thinks a lot of the problems are hardware / driver issues as other people are claiming it just works.

Hope this helps.

---

### Post by Lepodo on 2010-01-04
I followed the second persons tactic and it works perfectly. Great game!

---

### Post by SwiftNano on 2010-01-04
> **Lepodo said:**
> I followed the second persons tactic and it works perfectly. Great game!

Can you clarify who you mean by the second persons tactic.

---

### Post by thebigredone on 2010-02-07
Okay ive been surfing all morning and trying to get the installation running. now i managed one thing.

Im installing with the Disk.

Go to terminal and open a windows cmd console.

```
wine cmd
```

now it will be in Z drive, which is your linux file system. cd to your wine install path. (default: /home/.wine) and then to your C: drive which is a folder there.

Now the CMD will show that you are in C:\

now go to your steam installation directory default c:\program files\steam
obs! in windows it's "\" not "/" like in ubuntu.

example:
```
cd c:\program files\steam
```

then run the following:

```
Steam.exe -install "d:"
```

make sure you have configured your physical CD drive to be wines D: drive in winecfg.

This started the install process in steam for me.

When you need to change the disk, open another terminal (the old one is busy with the install) and run:

```
wine eject
```

This opened my physical DVD drive and i swapped the disk.

Now im a noob and this is my first post which is not a question so dont be to harsh.

Ok, now the install is complete, but when i try to run the game steam says that the install is incomplete. Anyone know what to do now?

---

### Post by smithers3628 on 2010-03-10
I am having the same problem as unforseen123. I have the game installed and i can start a single player game, but the game runs very slow and the text is all messed up. Which patches fix what exactly?

I see that some people figured out a way to fix it and was wondering if one of them could do a full step by step instruction. Someone saying "the second person was right!" doesn't help when there are 15 people posting and a second person on every page of a 5 page posting.

Can someone please just post instructions on how to fix the problems they got around? If one person posts the text, one person posts the framerate, one person post the mouse, and one person post the incomplete installation, we will never again have to answer a question already asked!

---

### Post by Zintha on 2010-03-12
> **hype said:**
> Good news !

After following these steps


and **installing latest wine 1.1.33 **update through wine ppa team, the game works perfectly !

I play at 1680*1050 without issues.

Just small glitch i have noticed, sometimes i get a black screen while videos are playing background (i can hear the sound of the scene): just quickly press alt-tab and click on-screen, you'll get back to the game.

 I didnt test multiplayer yet.

That worked! For 20 seconds. 
It loaded up MW2 and I managed to change over the resolution in the options then it minimized and steam "Verified installation" or something like that and game me the same error of "Incomplete installation".

Close though, will continue to work on it.

---

### Post by AcidSoldier on 2010-03-23
Not wanting to bump, but I just wanted to warn everyone that by doing these hacks you do have a high chance of being Valve Anti-Cheat banned from Modern Warfare 2's multiplayer. That's a lifetime ban from all legit servers, for MW2, due to how it's hosted.

---

### Post by 8Kuula on 2010-04-10
Mouse (free look, aim) seems to be little wierd with MW2, is this feature or bug?

Steam has free multiplayer weekend with MW2 atm, so I did download it from steam and works ok but mouse do not work so good (shiet multiplay anyways ;), have tried so far to smooth mouse on/off, and changing sensitivity, but does not change to better.
Sometimes it is "overmoving" like you are chasing your aim, and other times its like you are "dragging" your aim behind. This is middle of game so sensitivity is same whole time.

Anyone know fix to this?

Setup:
 - Ubuntu 9.10 64bit
 - Wine v1.1.41

---

### Post by mrfishjosh on 2010-04-11
Ok I am a noob at Linux so try to explain things well. thx in advance. I have suse, and wine 1.x.39 do i need wine doors? i dont know weither steam is installed or not as i see nothing. How do i get steam installed wine does not support .msi installer package. I have the MW2 disks. I tried to run the installer from the disk using wine and it gets a ways then locks up. I also get an error steam.exe (main exception) unable to load library steam.dll. I have been working on this forever, if anyone knows a nice tutorial you could point me to. I've tried google. or how to get steam on wine that'd be grand. :)

---

