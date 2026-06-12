---
title: "World of Warcraft problems, list of fixes i found so far..."
date: 2009-11-18
forum: Wine
---

### Post by Alatar1 on 2009-11-18
I wanted to make this in effort to prevent the millions of "OMFG HELP WITH WOW" threads i keep seeing pop up in this forum

First off before posting complaining about WoW problems check [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111) read it!!

So on with the list...

*These are all relevant as of the Time/Day of me posting this, things might change!, Also this is not an "official" post in any way, I am not an ubuntu or wine devoloper, I am a WoW player that's been using the game on Ubuntu for over a year,and have ran into the majority of these problems myself THAT IS ALL*

***Problem:***EULA "accept" button wont work when installing

***Solution:*** Update Wine FULLY , Should fix that right up, refer to [www.winehq.org](www.winehq.org) on how to do that, 
also try google/searching forums, I'm 100% sure there's about a thousand threads on how to do that floating around...

***Problem***"Permission Denied" error when attempting to run the game. OR When the WoW Launcher comes up, the "play" button is greyed out and cant be used. (both are stemming from the same problem)

***Solution*** The easiest and least technical way to fix this would be to first browse on over to /home/<yourusername>/.wine/drive_c/Program Files/World of Warcraft ,
 There will more than likely be an X on the world of warcraft folder, simply right click on it,go to properties, click the "permissions" tab, right under where it says owner: username-group, change the drop down box to "create and delete files".
    Now that that is set, In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".
    DO NOT USE THE LAUNCHER! it WILL lock you out again!!! this should fix this issue.

IF while working on the issue above, you cannot change file permissions due to it telling you the owner is "root"... 
you will need to change the permissions as root,
     the way i know how to do this is go to terminal and enter ```
sudo nautilus
``` or whatever file browser you use (nautilus is the default for ubuntu) this will allow you browse files as root,
         BE VERY CAREFUL HOWEVER, Tinkering with files as root can have very bad consequences and compromise your machine possibly, that being said...
     simply browse to the directy as stated above and change the permissions that way...there are also console commands to do it manually, but for the sake of the not so savvy, I've omitted those.

***Problem:***Installer/Updater sits at 0% and says "waiting for files to close" and won't Install or Patch

       ***Solution***This is caused by WoW related programs running in the background, thusly the installer or updater will NOT change any of the game files....
       To remedy this you will need to check if there are any wow related processes running in the background such as...
/home/username/.wine/drive_c/Program Files/World of Warcraft/Launcher.exe
/home/username/.wine/drive_c/Program Files/World of Warcraft/Wow.exe
/home/username/.wine/drive_c/Program Files/World of Warcraft/Wowerror.exe
/home/username/.wine/drive_c/Program Files/World of Warcraft/Backgrouddownloader.exe
/home/username/.wine/drive_c/Program Files/World of Warcraft/Repair.exe 

           to check running processes i use a program call htop ```
sudo apt-get install htop
```
              after its installed simply type ```
htop
``` in terminal and see if any of those listed, or any other WoW related processes are running when you DON'T have the game or installer/updater running and simply terminate them. should fix that...

***Problem:***World Of Warcraft crashes on the opening cinematic, or has video problems(this does not work for ALL video problems, but it is a very favored thing to do for WoW)

***Solution:*** Run WoW in openGL mode! The way i know how to do this is... Browse on over to /home/yourusrname/.wine/c_drive/program files/world of warcraft/wtf and open the config.wtf to edit and this with its OWN line ```
SET gxApi "opengl"
```

**still a work in progress, will add more shortly!! please anyone feel free to contribute, I'm just tryin to help with the wave of people posting about this particualar game, I've repeated myself at least a few times now trying to fix the same issues with different people...**

---

### Post by clim2f88j on 2009-11-19
> **Alatar1 said:**
> 
    Now that that is set, In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".


when i click the 'Wow.exe' file i get this error: 

Archive:  /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe
[/home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe or
          /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe.zip, and cannot find /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe.ZIP, period.

---

### Post by clim2f88j on 2009-11-19
nevermind at that. i right click on wow.exe and the preview for the game starts and then cuts off with an error message

---

### Post by Alatar1 on 2009-11-19
What's the error message? and is WoW set to run in openGL? also make sure your running wow with "wine windows program loader"

---

### Post by clim2f88j on 2009-11-19
> **Alatar1 said:**
> What's the error message? and is WoW set to run in openGL? also make sure your running wow with "wine windows program loader"

i am running wow with wine wpl and the error message is one of those that you can actually send out, didnt really pay attention to it

---

### Post by Alatar1 on 2009-11-19
Browse yourself on over to /home/yourusrname/.wine/drive_c/Program Files/World of Warcraft/WTF and open the config.wtf to edit it

make sure ```
SET gxApi "opengl"
``` is in there in the same way the other SET options are.

---

### Post by akoskm on 2009-11-19
> **clim2f88j said:**
> when i click the 'Wow.exe' file i get this error: 

Archive:  /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe
[/home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe or
          /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe.zip, and cannot find /home/facundo/.wine/drive_c/Program Files/World of Warcraft/Wow.exe.ZIP, period.

Have you tried to run WoW with wine and not with the Archive Manager?

---

### Post by clim2f88j on 2009-11-19
> **Alatar1 said:**
> Browse yourself on over to /home/yourusrname/.wine/drive_c/Program Files/World of Warcraft/WTF and open the config.wtf to edit it

make sure ```
SET gxApi "opengl"
``` is in there in the same way the other SET options are.

i dont have se gxapi on it i have all of this:

SET readTOS "-1" 
SET readEULA "-1" 
SET readTerminationWithoutNotice "-1" 
SET readScanning "-1" 
SET readContest "-1" 
SET checkAddonVersion "1" 
SET locale "enUS" 
SET expansionMovie "1" 
SET movie "1" 
SET showToolsUI "1"

btw the wow error i get when the game trys to start its way too long to copy and paste

---

### Post by Alatar1 on 2009-11-19
Then ADD it to that file! 
SET gxApi "opengl"
give it it's own little line.

---

### Post by DarKnightVIII on 2009-11-20
Alatar1

Thanks for making this thread.  Hope you don't mind if I post a problem I've been having in hopes we can figure this out together.  

I'm playing in full screen mode, and for some reason when I Alt+Tab out to change what channel I'm in on Teamspeak, or to do something else, WoW completely freezes and crashes.  

--------------

Little about me:  Was using Vista 32 bit Home Basic (understandably why I switched to a Linux based platform, besides the fact that I've wanted to do it for a long time anyways).  I had a dickens of a time getting Ubuntu 9.10 installed, then Wine then finally, WoW.  At first I was having sound issues (Pulse Audio conflicts w/ WoW), so I just reinstalled Ubuntu + Wine + WoW completely.  It was a new OS install only a few days previous, so no worries.

I'm fairly tech savvy (at least as it concerns some Computer Hardware and I'm very familiar with Windows), but Linux has thrown me for a loop...steep learning curve for me.

---

### Post by beastrace91 on 2009-11-20
@Darknight Do you have desktop effect enabled? I know for many fullscreen applications and Wine this causes issues (alt-tabbing makes it doubly so). If toggling these off does not fix the issue I would suggest simply running WoW windowed as not all full screen apps through Wine like to "alt-tab" desktop effects or not.

Regards,
~Jeff

---

### Post by Alatar1 on 2009-11-21
Yep i had the exact same thing, run it in windowed mode, but dont click the "maximised" box, and simply just click the maximise button on the window :)

---

### Post by Rody on 2009-11-21
insted of using alt tab use ctrl-alt left arrow or right arrow to use the other desktop, makes life much easer.


> **DarKnightVIII said:**
> Alatar1

Thanks for making this thread.  Hope you don't mind if I post a problem I've been having in hopes we can figure this out together.  

I'm playing in full screen mode, and for some reason when I Alt+Tab out to change what channel I'm in on Teamspeak, or to do something else, WoW completely freezes and crashes.  

--------------

Little about me:  Was using Vista 32 bit Home Basic (understandably why I switched to a Linux based platform, besides the fact that I've wanted to do it for a long time anyways).  I had a dickens of a time getting Ubuntu 9.10 installed, then Wine then finally, WoW.  At first I was having sound issues (Pulse Audio conflicts w/ WoW), so I just reinstalled Ubuntu + Wine + WoW completely.  It was a new OS install only a few days previous, so no worries.

I'm fairly tech savvy (at least as it concerns some Computer Hardware and I'm very familiar with Windows), but Linux has thrown me for a loop...steep learning curve for me.

---

### Post by towline on 2009-11-26
HI there,

I think I've experienced every problem mentionned, from not being able to load the 'WotLK' dvd, to EULA agree button not working, to the one where the permissions keep being reset etc. 

I've overcome each hurdle, but I am still unable to run WoW.

The latest, is that when I run the WoW.exe with wine, all that happens is that a blue window opens for a moment, and then closes.  In Terminal, I get the following error message:

> X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  230
  Current serial number in output stream:  230

Any advice?

---

### Post by Alatar1 on 2009-11-27
Go to the WoW shortcut on your desktop. right click, click properties. At the end of the target path, where it says something like: ""C:\Program Files\World of Warcraft\wow.exe"" change it to this:

"C:\Program Files\World of Warcraft\wow.exe" -opengl 
 
If you don't have a shortcut you can make a custom launcher...

Right click your desktop, go to "create launcher" leave the drop down box on "application", on the "command" line click "browse" then browse on over to /home/yourusername/.wine/drive_c/Program Files/World of Warcraft then click on WoW.exe  and name your launcher and so forth..
Now again on the "command" line make sure it looks like this ```
 /home/yourusername/.wine/drive_c/Program Files/World of Warcraft/WoW.exe -opengl
```

theres a space after wow.exe :)

---

### Post by jakebros1 on 2009-11-27
hey alatar i read your first message and im still having a problem dont know what to do like you said that i need to go to properties of wow folder and permissions but whenever i do that the next time it locks it again and i cant get on to it
when i unlock it i get the launcher running once but when i press play nothing comes up and then when i click on the launcher again an error comes up

Details: Failed to change to directory '/home/sheryl/.wine/dosdevices/c:/Program Files/World of Warcraft/' (Permission denied)

can you plz explain to me how to fix it i asked a lot of ppl and never get it solved

p.s. if you have an aim or aol account it would be much easier to talk then just waiting every post back
thx:)

---

### Post by MacLeod9 on 2009-11-27
Hi,

I have successfully installed both Wine 1.2 and all WoW expansions, but have had continual problems with fps in game. I am currently running the game in opengl and windowed mode at lowest possilbe video settings in game. I have tried numerous settings between wine and my nvidia control panel, but continue to see 3-7 fps with the occasional spike to 9-10 fps in doors. on my winxp machine i averaged about 27-30fps no matter where i was in the map. I have research numerous other posts but have not been able to find any solutions. Any ideas would be greatly appreciate as I was happy to switch from windows and really dont want to switch back.
**System Specs:**
Intel D845EPI board, 2.4Ghz proc, 1.5 Gb DDR RAM, and Nvidia GeForce 6200 512mb Video card with restricted drivers enabled and installed
**OS: **Ubuntu 9.10 Karmic Koala with Wine1.2

---

### Post by bethebunny on 2009-11-27
Perhaps someone can help me;

I'm having the ATI "enter game world crash" problem.

The solution, described here:
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

is to add the following lines to xorg.conf:

```

 Option "Capabilities" "0x00000800"
 Option "UseFastTLS" "off"
 Option "KernelModuleParm" "locked-userpages=0"

```

However, it doesn't fix the problem. I think this has something to do with how Ubuntu handles xorg configuration, as the xorg.conf file seems to be largely archaic in recent releases. Any idea how I fix this in 9.10?

---

### Post by Alatar1 on 2009-11-28
@ jakesbro1 :
quote from my first post >  DO NOT USE THE LAUNCHER! it WILL lock you out again!!!  DONE USE THE LAUNCHER IT WILL LOCK YOU OUT EVERYTIME 
ALSO from my first post...
> In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".

---------------------------------------------------
@Macleod9: Running windows games through wine unfortunately pretty much requires that you have nearly twice the computer specs to run in wine as it would windows, you have nearly the same system as me, may i suggest more RAM (it helped me TREMENDOUSLY)
---------------------------------------------------------------------
@bethebunny : I have no idea, my other machine has karmic koala and i can't get editing the xorg.conf to change anything either, just give it time and a fix should surface.

---

### Post by Ugluk on 2009-12-03
Had people affected with Launcher permissions problem submitted Wine bug?

---

### Post by domosplace on 2009-12-04
Hey everyone

Im a complete noobie to Ubuntu 9.10 I love to Ubuntu about 3 weeks ago and been looking for away to fix my wow problem. I have downloaded wow successful with no problem. I know the lancher locks the wow file. My problem is i cant seem to get pass the video. It closes wow completely. I ran it thur terminal here is the following 

lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed54,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39eb44,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39f01c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f264,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3c4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f534,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e4,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "VA Linux Systems, Inc.". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x39f54c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexEnvf(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_COMBINE_EXT); @ context.c / 1310
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x186de8) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39efa4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0e4,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:state_psizemin_w WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
fixme:d3d:state_psizemin_w WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 1.000000
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ state.c / 2443
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ state.c / 2445
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ state.c / 2447
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2449
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2473
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2475
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2477
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2479
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2481
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ state.c / 2483
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2487
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2489
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2491
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2493
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2495
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 2 @ state.c / 2497
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ state.c / 2487
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ state.c / 2489
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ state.c / 2491
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ state.c / 2493
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ state.c / 2495
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 2 @ state.c / 2497
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ state.c / 2916
Error: Rage 128 timed out... exiting

Now i couldnt find the confwtf that everyone was talking about should i put the opengl in the Runonce_WLK.wtf thing or what? I mean i left windows to the dogs and i really dont wanna go back at all. I have configured wine like they said in all the other fourms i have read. Im completely lost and i really wanna play wow. Oh i cant get the patches to download 
I get the following
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Blizzard Updater.exe" 
Missing symbol {InternalArchive}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {InternalArchive}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:ole:OleCreateStaticFromData (not shown), stub!

and when i try to run the background downloader i get following 
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\BackgroundDownloader.exe" -
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

http error code = 404
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

no i know these are problems i can fix i just dont know where to start...

and another thing my monitor is Unknown how do i fix that too

My computer
Dell Dimension 4500
Vid- 32mb Ati Rage 128 Ultra
1 GB ram 
40gb HD 

I really need help i will be on here every day untill i get a reply to fix this. I am also willing to fix this over aim just send me a private message and i will send u my aim or yahoo i also have a msn but dont use it but i will if u have one. thank you very much 

Oh and i forgot since i was reading up up on drivers i didnt download one cause i didnt know how too also this OS really doesnt have one that works with my video card...

Thanks Lee[

---

### Post by Alatar1 on 2009-12-04
quoted from an earlier post on this thread....

Go to the WoW shortcut on your desktop. right click, click properties. At the end of the target path, where it says something like: ""C:\Program Files\World of Warcraft\wow.exe"" change it to this:

"C:\Program Files\World of Warcraft\wow.exe" -opengl

If you don't have a shortcut you can make a custom launcher...

Right click your desktop, go to "create launcher" leave the drop down box on "application", on the "command" line click "browse" then browse on over to /home/yourusername/.wine/drive_c/Program Files/World of Warcraft then click on WoW.exe and name your launcher and so forth..
Now again on the "command" line make sure it looks like this
Code:

 /home/yourusername/.wine/drive_c/Program Files/World of Warcraft/WoW.exe -opengl

theres a space after wow.exe

---

### Post by domosplace on 2009-12-04
i have done that which was another thing i forgot to mention. how do i fix the fixme errors?

---

### Post by domosplace on 2009-12-04
how do i atleast get past the errors?

---

### Post by domosplace on 2009-12-04
i meant video...

---

### Post by dazer26 on 2009-12-05
"My computer
Dell Dimension 4500
Vid- 32mb Ati Rage 128 Ultra
1 GB ram 
40gb HD"

I hate to say it, but that computer might not be good enough for wow.  Thats a really old video card.  It might barely work in windows.  I have 2gigs of ram and a nvidia 8600 256mb vid card and wow still runs a bit slower in linux than it does in windows.  I am running in direct X mode though, mostly cause I need the hardware cursor.

edit: Also I don't think there is good linux support for old ati cards, if you upgraded the video card and ram you could probably run wow.

---

### Post by domosplace on 2009-12-05
thats the thing...i ran wow in win xp pro. i didnt have any problems except the lag which i fixed....

---

### Post by Alatar1 on 2009-12-05
Those fixme errors says 'd3d' in them, so obviosuly, the opengl thing isnt taking.. try this...  

take yourself over to /home/yourusername/.wine/drive_c/Program Files/World of Warcraft/WTF

and open and edit teh config.wtf , if there isnt one, try creating one, and put this in it own line EXACTLY how i have it here

```
SET gxApi "opengl"
```

and also note, just about any game ran through wine, is going to take about twice as much computing power as it would in windows, unfortunate fact about wine.

---

### Post by domosplace on 2009-12-10
hey sorry about the long time to reply....but i cant create the config.wtf it wont let me...everytime i try to change the permission it goes right back....and what do i do about the add on folder that is missing?

---

### Post by Alatar1 on 2009-12-11
Are you using the launcher? (the little window thingie that pops up when you open the game with blizz news on and the little play button thingie) if you are that's probably the problem. DONT EVER USE THE LAUNCHER. 

and this missing addons folder...try making one?, some people get some of the weirdest errors i've never even seen or heard of, its insanity

---

### Post by domosplace on 2009-12-11
no im not it just got worse

```

lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe"
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\Wow.exe" failed, status c0000005

```

what do i have to do to fix this???
or you can hit me up on aim if you like so we can work together...

---

### Post by akoskm on 2009-12-13
Try this:
lee@lee-desktop:~$ env WINEPREFIX="/home/lee/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" **-opengl**

---

### Post by Alatar1 on 2009-12-19
Bump, Bumpety, Bumpers, Bumpy, Bumper-Boo!!

---

### Post by ahorriblemess on 2009-12-20
First of all, Alatar1, nice avatar. "I am a banana!"

Second: I created a thread but I should have just added it to here. I would delete it if we had the ability to do that on this forum. 

So when I launch WoW.exe with OpenGL, I get an error:

Error #132
Exception: 0x000000005(ACCESS_VIOLATION)at 0073:375116DC The memory could not be "read". 

Or something like that. It has nothing to do with permissions either, because I make sure permissions are set correctly first. And if I launch WoW.exe WITHOUT opengl, it starts up but performance is TERRIBLE. When I play in Windows or Mac it's not so bad. So I'm assuming it's either Wine or the Intel GMA driver for Linux. 

But has anyone experience decent performance if they even got it running? I'm getting a new computer some day... but not for several months. It would be nice to get this working.

---

### Post by kjt124 on 2010-01-02
Ok guys - my first post about Linux so be gentle.

Loving Linux and learning well (especially with the magnitude of complication brought about by trying to run WoW through Wine.

I'm running Ubuntu 9.10
wine 2.something (not sure how to check version numbers yet)
AMD X2 3800+ 64 bit
2 GB 800 MHz RAM
NVidia graphics 512 MB RAM (something like a 8600 GT I believe)

So far I ran through Doctor Debian's (not sure if someone else posted the walk through first) about installing and reconfiguring wine.  Wow man - that would have taken me a lifetime to figure out - thanks a ton!

I have the config.wtf set with 

SET gxApi "opengl"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "100"

My command line is

env WINE_CURSOR=anything; wine /home/kt/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl

I am running the hardware cursor as I had the lag from the OpenGL cursor.

I had patch-f.MPQ in my data folder and it took me about 4 days to figure out that it was the culprit preventing me from having a cursor while in WoW - deleted it and my cursor is back. (please tell me that doesn't undo the hardware cursor thing)

I have 2 distinct issues right now and I am hoping the clever folks who frequent these pages can help - especially since I have only about a week experience with ubuntu thus far and these forums have managed to get me all this way already.

Issue the first (and most important):

I start the game, login, and loading screen passes.  I run at roughly 50 fps even in high population areas - which is about 60% better than when I ran in Win XP.  A short while later things start to go awry (pretty much after I got my coffee and actually try to move around).  I have the ingame latency and framerate indicators showing that not much changes with them (small but not very significant drop), but my computer as a whole boggs down hard.  The WoW screen goes grey-scale (still not familiar with what that means exactly, but I know it isn't a sign of good things).  This occurs on a fresh boot with nothing else running but a firefox window with this site and my gmail as the only 2 tabs up.

I can't imagine that it is a lack of resources being that I have tried this with System Monitor running and both cores run at about 15% and RAM usage reads about 600MB while this is going on.

The system goes to the point where I have to click on the 'X' in the corner of wow to close it several times and wait up to a minute to get the 'force close?' dialogue.  Accessing a terminal for 'top' command is not possible and even 'ctrl+alt+F1' takes about 6 minutes to open to a login prompt.  The last possibility I came up with was possibly since I run my desktop at a resolution of 2048x1536 perhaps my video RAM was all used up by the time I loaded the game, but even after I reduced my resolution to 1600x1200 the result was the same.

I run the game in windowed mode at 1280x1024 resolution and far from max settings.  I am using the NVidia 185 driver that you download through the software center.

I am very new to Linux, but I am not uneducated and I follow direction well, but I cannot find any threads that have addressed this specifically yet.  Has anyone run into this before or have any ideas about it?  Any help at all would be greatly appreciated.  Thanks you.

Issue the second (much less important):

I am messing around with the sound buffer size and am nearly dialed in on where it needs to be, however...   The sound does not last.  If I tab out of the game and come back the sound no longer works.  If this business with computer bogging down occurs then the sound breaks up like it were lagging and then goes away entirely.  Occassionally the goes away on its own with no other warning sign.

As I said this is of low priority as I am still playing with the sound buffer and I have not yet tried different audio drivers or modes or whatever they are that you specify in winecfg, but I figured I would throw out a line and see if anyone had a nibble for me  :P

Edit:  Currently using ALSA if that helps /Edit

Thank you for anyone who has read this giant post - I'll try to explain myself more briefly next time.

---

### Post by kjt124 on 2010-01-03
Current update...

I think I have the system bogging down issue mostly solved.  It seems as though I am running near the upper limit of my processing power.  I am trying my best to tweak settings / addons to run with sufficient options, but also actually run.  Is there any way to modify how programs access the processor or anything like that?  With the aid of system monitor it seems that one of my cores runs consistently at about 25% load and the other one is running consistently at 90+%.  I have very little information about how a dual core processor is utilized.  For now at least I think this part is reasonably solved.

My other issue unfortunately still exists.  No Sound (or small periods of very poor sound and then no sound).  I have switched audio modes in winecfg and the only that works a little bit is ALSA.  I've also messed around with audio buffer size and that can sometimes increase my sound quality when I have sound, but having sound is still not reliable.  I'm not even sure which sound card I have as it is an onboard sound (it is a gigabyte mobo if that helps).  Obviously no sound is not the end of the world, but there has to be something I can do here.

---

### Post by kjt124 on 2010-01-03
another quick question - what is the possible range of values for the audio buffer size?

---

### Post by Alatar1 on 2010-01-03
Glad to see you got the bogging down issue solved(for the most part) it does seem that any programs run through wine (well at least games) take about 3x more computer power than it would on windows, seeing as how the OS is being made to run a program thats not mad for it.


As for the sound issue, If you fix that one let me know, tabbing out of the game kills my sound all the time, if you keep tabbing back in and out however, it can make it come back usually. Hope it helps.

---

### Post by Raan03 on 2010-01-04
Hello (bear with me untill the end - first some mumbo jumbo)

I tried to run World of Warcraft the last week trying to configure it. First I had it difficult in D3D with objects not being correctly rendered - The Barrens was 1 big desert with curves, the cities were drawn correctly except the ground. 

I tried the opengl setting, which gave me some major improvement over the D3D on terms of ground rendering, but I wasn't satisfied with how the game handles (choppy sound and Warcraft freezes ten seconds after a gameplay of 5 minutes or so which rendered my spells pretty useless to use).

I decided to upgrade to the newest Wine (1.35), which increased my FPS-rate but not the major problems I've encountered + mouse lag ofcourse. I also re-enabled the Pixel shaders and changed the Vertex shaders to hardware(winecfg-graphics). This removed the issue with the ground not being properly rendered in D3D.

After it I decided to upgrade my kernel (2.6.32-020632-generic
), as it came to my understanding that the kernel tree delivered by Karmic has a bug in his kernel scheduler.

Unfortunately I had to hard reset the computer being crashed after 10 minutes of gameplay in D3D, so I switched back to OpenGL. After this, I could play for hours without getting any kind of freeze. The only problem remains is the choppy sound.

Then it came to my understanding that the problem might lie with PulseAudio, so I killed all services of PulseAudio. This had the result that the sound was back the way it used to be - like it played in Windows. Unfortunately, after a while I had the choppy sound again: so I tried to renice the PulseAudio which had a brief success (again). Right now, I have completely removed PulseAudio from my system but didn't had time yet to test whether this has any results...

Quick summary:
[list]
[*]Make sure you've got wine 1.35 (repository or compiled with hardware mouse support)
[*]Upgrade your kernel to the 2.6.32 series
[/list]
This removed the freezes in OpenGL due to a known 2.6.31 kernel scheduler bug.
The choppy sound *might* (as I don't have any confirmation yet on my system due lack of time) be resolved by going back to Alsa

---

### Post by amenfex on 2010-04-09
K.

First, THANK YOU! 

WoW runs but I have a few issues.

1. It appears BC is already installed. When I tried to run Install WoW.exe, there is no install button, just: "Play Burning Crusade". 

2. When i try to install Linch through InstallWoW.exe, it gives me this prompt.

Sorry, the instillation failed

" The file "Z:\home\andres\WoW_install\World of Warcraft\Logs" is read only and cannot be overwritten. Please try installing to a different location. (ConflictManager::DeleteFolder)"

3. When I log in, it downloads Update and tells me to restart WoW "Patch Required". The program closes and downloads the patch. This prompt also comes up:


"Program Error

The program WoW.exe has ecountered a serious problem and needs to be closed. We are sorry for the inconvinience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check http:appdb.winehq.org for tips about running this application.

If this problem is no present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org."

After that, I just press close.

When the path finishes downloading, it window closes and another Blizzard box pops up with a blank message with a button that says "Ok". 

This happens every time I try to open it WoW.

Hopefully you're not tired of answering all these questions. So far you're thread has helped the most out of the dozens on the Internet. Again, thanks.

---

### Post by roh8880 on 2010-05-19
Ok, hopefully this doesn't count as necro-posting!

I have an issue with WoW on 10.04 and I can't figure this one out!

I have the latest wine, the latest drivers, duo-core 6000+ 3.0 GHz, 2gig ddr2, and not that great of a graphics card. I have the opengl in the Config.wtf file, I'm running metacity (instead of compiz) on my appearance, I have the effects turned down, shaders and all that jazz turned off.

I'm still getting this . . . 
[IMG]http://i615.photobucket.com/albums/tt233/roh8880/runtime.png[/IMG]
[IMG]http://i615.photobucket.com/albums/tt233/roh8880/error.png[/IMG]


Any ideas?

---

