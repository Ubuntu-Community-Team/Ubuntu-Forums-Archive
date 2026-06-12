---
title: "Halo Combat Evolved Fully Working Single And Multeplayer!"
date: 2009-05-24
forum: Wine
---

### Post by dvl300 on 2009-05-24
I have solved the problem to play online gaming with halo

Here's what you've got to do:
(You will need wine installed before hand!)
[LIST=1]
[*]Download PlayOnLinux
[http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")
[*]Install PlayOnLinux
[*]Run PlayOnLinux(Press Alt+F2 Then Type In playonlinux And Click Run)
[*]Insert your halo disc
[*]Click Install in PlayOnLinux
[*]Click On Games In The Left Sidebar
[*]Scroll Down In the Right Frame Of The Program Until You Find Halo Combat Evolved
[*]Then Click Apply
[*]Click Forward On The Pop Up Window You Now See
[*]Then Click On Where The CD-ROM Is Mounted Primarily Cdrom0 Then Click Forward
[*]Wait While Prefix Is Created Then Setup Of Halo Will Load
[*]Now Leave The Previous Play On Linux Window Alone And Go Through The Halo Setup As Normal
[*]Once Halo Setup Has Finished Do Not Press Play Now Just Click The X In The Top Right Of The Halo Setup Window And Close It
[*]Now Go Back To The PLayOnLinux Window And Click Forward
[*]Then Tick The Box Create A Shortcut On Desktop
[*]Then Click Forward
[*]Do Not Close The Main PlayOnLinux Window Yet
[*]Now Download Halo Combat Evolved 1.08 Patch And Unzip To Desktop
[http://files.filefront.com/halopc108patchzip/;11408693;/fileinfo.html]("http://files.filefront.com/halopc108patchzip/;11408693;/fileinfo.html")
[*]Click Install in PlayOnLinux
[*]Then Look At The Bottom Right Of The Window And Click On install a .pol application or unsupported application
[*]Click On Manual Installation Then Click Next
[*]Click Forward
[*]Click On Edit an application already installed then click forward
[*]Click On Halo Then Click Forward
[*]Then Click No
[*]Now Click Browse
[*]Then Click On Desktop
[*]Then Click On halopc108patch.exe
[*]Then Click Open
[*]Then Click Forward
[*]The Halo Update Program Will Now Run Once Its Done You Will Get A Pop Up And Click OK
[*]Now Go Back To The PLayOnLinux Window And Click Forward
[*]Then Click No
[*]Now Close The Main PLayOnLinux Window
[*]Now Eject Halo Disc As With The Update It Is No Longer Needed
[*]Now Run Halo From Your Desktop
[*]And Use Halo As You Normally Would
[*]As Usual When You Go To Multiplayer You Will Need To Click Refresh List
[/LIST]
Enjoy!
:D

---

### Post by Sef on 2009-05-24
Moved to WINE forum.

---

### Post by SPARTAN-118 on 2009-06-06
Hi, I followed your tutorial, and I must say, It's great. The only thing is, when I start up Halo: CE, it freezes at the logo videos. I think I remember reading something on how to disable them, but I can't remember where. Can you please tell me how to turn them off? 

Thanks, 
SPARTAN-118

---

### Post by Book4567 on 2009-06-06
use  -novideo on the desktop icon to fix halo you might also have to use -vidmode ####,###,## (with the first two  being the display resoltion and the third refresh rate) and maybe for performance reasons -nosound hope this solves your issue :D

---

### Post by SPARTAN-118 on 2009-06-08
> **Book4567 said:**
> use  -novideo on the desktop icon to fix halo you might also have to use -vidmode ####,###,## (with the first two  being the display resoltion and the third refresh rate) and maybe for performance reasons -nosound hope this solves your issue :D

Thanks, I will try that.

By the way, does console/devmode (adding -console) work in Ubuntu? It should work across all platforms, since it's in the game, right?

_**EDIT: **_Well that's just great. Now, it skips the videos, only to freeze on the HALO screen! Grrrr!!! You know what, I think I'll just stick to gaming on WIndows. I hate Windows Vista, especially since my computer doesn't meet the required specs, but since I also have Starcraft on there (download-only, didn't find the "battle pack" until later) I guess I have no choice. Unless either Wine or PlayOnLinux evolves to more than a Windows emulation platform (I know Wine stands for Wine Is Not an Emulator, but that's besides the point), I guess I should stick to Windows for Windows software.

I'm also waiting for the day when Wine can trick Windows installers into thinking you have "genuine Windows....." That'd be awesome, since there is no replacement for WIndows Movie Maker good enough for me. I don't like Kino, looks too complex, and I can't even find the video editor in Blender.

---

### Post by dvl300 on 2009-06-08
> **SPARTAN-118 said:**
> Hi, I followed your tutorial, and I must say, It's great. The only thing is, when I start up Halo: CE, it freezes at the logo videos. I think I remember reading something on how to disable them, but I can't remember where. Can you please tell me how to turn them off? 

Thanks, 
SPARTAN-118
make sure that wine handles the window of the program
also makes sure you have it set at a steady resolution such 1024x768
or have the program windowed

i have not tested Halo CE as i only use my Halo Combat Evolved for online and offline gaming but from what i have heard from others its usually you've set the resolution for the game to high so you may have to edit the game's config file, and this doesent help as wine controls the program window by default and i swear it has a maximum resolution allowed whilst letting wine handle your program windows

best bet! if all else fails just run it windowed you shouldn't have any problems
:D!

---

### Post by SPARTAN-118 on 2009-06-08
> **dvl300 said:**
> make sure that wine handles the window of the program
also makes sure you have it set at a steady resolution such 1024x768
or have the program windowed

i have not tested Halo CE as i only use my Halo Combat Evolved for online and offline gaming but from what i have heard from others its usually you've set the resolution for the game to high so you may have to edit the game's config file, and this doesent help as wine controls the program window by default and i swear it has a maximum resolution allowed whilst letting wine handle your program windows

best bet! if all else fails just run it windowed you shouldn't have any problems
:D!

And how do I run it windowed? By clicking on "properties" and editing it there? I swear, PlayOnLinux is less confusing, but STILL doesn't get the job done! (Would you believe FireFox is marking doesn't as a spelling mistake?) And even if I DID run it windowed, wouldn't it still freeze up as it's loading? What does the resolution have to do with it? True, when I set it to my *ahem* correct resolution, somehow HALO doesn't quite fit, so I'll just take out that part of the command, but really, why would that make it freeze? Yeesh, why can't Microsoft stop being so defending of their software monopoly and make things more open-sourced? Removing the "genuine Windows" check would be a great start. Or Linux users could have campaigns where commercial game/software developers would be forced to take more notice of them, and start making games that work on Linux platforms. For example, the next PC Halo (IF they make Halo 3 a PC game, like they did in Halo 2) could run on Linux, since Bungie is no longer owned by Microsoft (which means they might not make any more Halo games after the Halo 3 expansion pack, ODST - *sniffle* - but might mean great things for those of us who use non-Microsoft stuff, such as Ubuntu). That'd be great, though it *would* be pretty hard, considering a few months ago I'd never heard of Ubuntu.

_**EDIT:**_ Well, I got Halo running as windowed (typing -windowed on the shortcut), but it STILL freezes at the HALO screen. Then it asked me to run it in safe mode, and it got past the Halo screen, only to freeze at a white screen where the main menu should be. When I pressed Esc, it asked me if I was sure I wanted to exit.
That's as far as I got.

---

### Post by dvl300 on 2009-06-15
you need to configure it in wine

---

