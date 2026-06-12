---
title: "Trouble installing Wrath of the Lich King in wine"
date: 2009-10-18
forum: Wine
---

### Post by Wasteload on 2009-10-18
I have been installing wow with my installers off a small hard usb drive up until now but I purchased WOLK on CD so I have to use the disc to install the game.  When I try to put the disc in it will have an X over the installer stating NOREAD and if I attempt to run the Installer.exe file in root it will state that I am not the owner and I cant run it.  
I tried also to get the universal installer off of WoW's website but when I try to run that I try to scroll down to the bottom of the eu agreement to hit accept but accept will never become "clickable"

I am still new to the ubuntu/linux community but I know my way around things so I shouldnt have many problems following code lines. 

Any help with any of this would be greatly appreciated.

Thanks in advance

Edit:  I am using Ubuntu 9.04 and Wine 1.0.1

---

### Post by beastrace91 on 2009-10-18
Upgraded to the newest version of Wine following the instructions [here](http://www.winehq.org/download/deb)

Then try installing WOLK

~Jeff

---

### Post by r4itei on 2009-10-18
im having the same problems as you.....except i can get to the logon screen but it looks like this  =S

[http://photos-d.ak.fbcdn.net/hphotos-ak-snc1/hs279.snc1/10630_168821523304_502678304_2746487_3975248_n.jpg](http://photos-d.ak.fbcdn.net/hphotos-ak-snc1/hs279.snc1/10630_168821523304_502678304_2746487_3975248_n.jpg)

im using ati video card open source drivers

direct rendering is yes
gears work fine, 700fps...

any other info necessary?

for a platinum level program on wine, sure took me the past 2 days to install and to get past the eula and tos

---

### Post by Wasteload on 2009-10-18
Update:  Updated Wine as the person above suggested and I now have gotten the "Agree" button on the eu agreement to come up now so I am running the install there.  

Fortunately I have all the patches saved on a HDD from when I had windows so I should be in good shape.

I'll post again once I have it up and running for the victory

I LOVE THIS OS

---

### Post by r4itei on 2009-10-18
watch out because when i first ran it, it needed the wine update to get to hit agree.
but then i had to revert back to the stable wine ver 1.0 to actually get the game to start.
and now im stick with this semi translucent login page.

i can type on it i just cant see crap.

---

### Post by Wasteload on 2009-10-18
Yea Im already commited there so I have to just hope but I think I will be ok.

---

### Post by r4itei on 2009-10-18
bump. someone reply my question (3rd post) so i dont have to make new thread.

---

### Post by beastrace91 on 2009-10-18
> **r4itei said:**
> bump. someone reply my question (3rd post) so i dont have to make new thread.

What Wine version are you using? If .31 is giving you issues try reverting back to .29 or .28 as I know .31/.30 had some regressions that hurt a few game's performance. Also do native 3D Linux games work? I know the Open Source drivers typically perform much worse than the closed source ones - but I also have not used ATI in a long time as they have horrid Linux support.

Hope this helps some,
~Jeff

---

### Post by r4itei on 2009-10-18
I reverted back to the stable release. because .31 would always give me some fault but the stable doesnt.
i havent even been trying to get games to work. ive had ubuntu since last year but havent tried gaming on it til now.

also my chipset has no restricted drivers so i must use open-source, tho apparently it has better framerate. just my mouse doesnt show and the screen looked like that...the games i had on here work fine, the ones that came with hardy.

---

### Post by beastrace91 on 2009-10-18
Alrighty well each new version of Wine tend to add functionality try one of the newer versions from [here](http://wine.budgetdedicated.com/archive/index.html)

Some work better than others for some games. This is why things like [Crossover](http://www.codeweavers.com/) or if you want to stick to open source [Play on Linux](http://www.playonlinux.com/en/) where created to help keep things both stable and current.

~Jeff

---

### Post by Wasteload on 2009-10-18
Would you advise downloading PlayonLinux to have as an overall.  

I just moved over to Jaunty as a single boot and do have a lot of games that I would like to be able to play

---

### Post by r4itei on 2009-10-18
i just tried .27 - .31 and it always gives me this

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  160
  Current serial number in output stream:  160

```

so right now my only option is either try to go lower until it runs or just stick to 1.0 and find a way to fix the translucent hazy boxes.

---

### Post by Wasteload on 2009-10-18
Does it being translucent cause you to not be able to type anything in?  Or did I understand that you can still type things in (ie your pw) just you cant see what you are doing?

---

### Post by r4itei on 2009-10-18
i saw that i was typing stuff, but it wasnt enough to know what i was typing, i just saw the blinking text thing move as i smashed on the keyboard.

---

### Post by Wasteload on 2009-10-18
Just to let everyone know the install is about 43% done but I cant stay up to see it finish tonight since I have to be up at 5 in the morning.  
Will update in the morning with how things are going

---

### Post by Wasteload on 2009-10-19
Ok this is where I am at now.  I got the download/install finished by using the universal installer and when I went to open the WOLK launcher I got this message in the form of a window popup that looks to be from wine.


 I am using 9.04 Jaunty and
 1.1.31  version of wine that I just updated last night to be able to get WOLK installed.
 

**Error from wine:  **


 Program Error  (In top title bar)

 

 The program Lanucher.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience.
 

 This can be c aused by a problem in the program or a deficiency in Wine.  You may want to check [http://appdb.winehq.org]("http://appdb.winehq.org/") for tips about running this application.
 

 Then has a couple sentences about reporting the bug.
 

 Once that error message has come up I have to force quit the application to get it to close after that as well.
 

 The launcher is showing as the most current WOLK one but it will start to try to download something within the initial launcher, like it is patching the launcher itself so there may be one other launcher patch that I am missing but I dunno.   
 

 I have seen a little bit of talk about reverting back to a previous version but I have not done that yet.


Where should I be heading from here?

---

### Post by beastrace91 on 2009-10-19
> **Wasteload said:**
> 
 I have seen a little bit of talk about reverting back to a previous version but I have not done that yet.

Give it a try or try doing an install through POL (it manages multiple different Wine versions for you.

~Jeff

---

### Post by Wasteload on 2009-10-19
Hey beast.  I just got PlayonLinux installed last night so could you noob it up a bit for me.  How should I go about telling POL to run that launcher to get past the launcher error I am getting.

Also, I am sure it is easy but how do I go about reverting back to a previous version of wine?

---

### Post by beastrace91 on 2009-10-19
Past Wine versions in .deb format can always be found [here](http://wine.budgetdedicated.com/archive/index.html)

As for POL I have not used it terribly much personally as I have Codeweavers, but I installed it a few days ago and the interface seemed pretty straight forward - just click through it and you should be able to figure it out - if not I will get around to playing with it more myself some time later this week hopefully.

For now just try reverting you Wine version using one of the downloads from my above link if you do not feel like tinkering with POL.

~Jeff

---

### Post by Wasteload on 2009-10-19
Ok I am trying to go back to 1.1.28 and I get it and the installer package scans but then says a later version is already installed and the button that is in the top right that you are supposed to click to install that pkg is greyed out so you cannot choose it.

---

### Post by beastrace91 on 2009-10-19
Remove the newer version first (don't worry this will not affect your installed windows programs)

Search for the "wine" package in synaptic (System->Administration->Synaptic) and mark it for removal and hit apply or if you are not afraid of terminal just do ```
sudo apt-get remove wine
```

Then you should be able to install the older version.

~Jeff

---

### Post by Wasteload on 2009-10-19
Okay thanks for that, no I would prefer if you have it to just shoot me lines of code as I prefer command line interface.  I will do this and let you know how it goes.

---

### Post by Wasteload on 2009-10-19
Man your great got me right over that hump.

I'm going to keep running my patches and hopefully I won't have to bother you anymore.

Thanks again for all of your help!!

---

### Post by Wasteload on 2009-10-19
Ok well great news I am in the game now!!  I got it all patched up and am able to log in ok.

What I want to do now is know how to ensure that I get the best possible graphics I can.  It all seems to be going ok but is hanging up, not to the point that I cannot do anything but definately noticeable.

I have an nVidia video card with the Linux nVidia app installed on here and I have driver version 180.44.

Where should I start...

---

### Post by beastrace91 on 2009-10-19
I'd start with the link that is in my signature entitled ["Linux Gaming: Performance Optimizations"](http://jeffhoogland.blogspot.com/2009/10/linux-gaming-performance-optimizations.html) - but thats just me ;)

~Jeff

---

### Post by Wasteload on 2009-10-19
The saddest part about that is I did not even see that in your sig til just now... :)

---

### Post by Wasteload on 2009-10-19
On the tutorial you sent me, I am trying to update my nVidia driver to the newest at the site suggested:
[ftp://download.nvidia.com/XFree86/](ftp://download.nvidia.com/XFree86/)

I tried to download nvidia install but it seems to be all source code, hints?

---

### Post by Wasteload on 2009-10-19
Okay well I have not been able to get WoW running again since my first success.  Everytime I try to start it I can get through the launcher and get to the game "load" and then it crashes and WoWs debug messenger gives me this:



	 	 	 	 	  [FONT=Arial, sans-serif][SIZE=2]World of WarCraft (build 10505)[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]Exe:      C:\World of Warcraft\Wow.exe[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Time:     Oct 19, 2009  7:34:07.788 PM[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]User:     x[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Computer: x-laptop[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]------------------------------------------------------------------------------[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]This application has encountered a critical error:[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]ERROR #132 (0x85100084) Fatal Exception[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Program:	C:\World of Warcraft\Wow.exe[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7C47285D[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]The instruction at "0x7C47285D" referenced memory at "0x630C7C57".[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]The memory could not be "written".[/SIZE][/FONT]
 

 

 [FONT=Arial, sans-serif][SIZE=2]WoWBuild: 10505[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Settings: [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]SET hwDetect "0"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET gxRefresh "54"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET gxMultisampleQuality "0.000000"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET gxFixLag "0"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET farclip "617"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET specular "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET movie "0"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET readTOS "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET readEULA "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET readScanning "-1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET readContest "-1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET realmList "us.logon.worldofwarcraft.com"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET locale "enUS"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET readTerminationWithoutNotice "-1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET coresDetected "2"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET videoOptionsVersion "2"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET showToolsUI "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_OutputDriverName "System Default"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET spellEffectLevel "6"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_VoiceChatInputDriverName "System Default"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_VoiceChatOutputDriverName "System Default"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET realmName "Destromath"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_MasterVolume "0.10000000149012"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_EnableErrorSpeech "0"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET mouseSpeed "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_SFXVolume "0.60000002384186"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_MusicVolume "0.60000002384186"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_AmbienceVolume "0.60000002384186"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET ChatMusicVolume "0.29999998211861"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET ChatSoundVolume "0.39999997615814"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET ChatAmbienceVolume "0.29999998211861"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_ZoneMusicNoDelay "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET gxTripleBuffer "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Gamma "1.000000"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET groundEffectDist "70"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET installType "Retail"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET patchlist "us.version.worldofwarcraft.com"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET gameTip "18"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET VoiceActivationSensitivity "0.39999997615814"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET Sound_EnableMusic "0"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET uiScale "0.83999997377396"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET useUiScale "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET movieSubtitle "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET accounttype "LK"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET projectedTextures "1"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET checkAddonVersion "0"[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]SET lastCharacterIndex "2"[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]----------------------------------------[/SIZE][/FONT]
                [FONT=Arial, sans-serif][SIZE=2]GxInfo[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]----------------------------------------[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]GxApi: Direct3d9[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Adapter Count: 1[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]Adapter 0 (primary):[/SIZE][/FONT]
   [FONT=Arial, sans-serif][SIZE=2]Driver: Display[/SIZE][/FONT]
   [FONT=Arial, sans-serif][SIZE=2]Version: 7.15.0011.8618[/SIZE][/FONT]
   [FONT=Arial, sans-serif][SIZE=2]Description: NVIDIA GeForce 8300 GS[/SIZE][/FONT]
   [FONT=Arial, sans-serif][SIZE=2]DeviceName: \\.\DISPLAY1[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]------------------------------------------------------------------------------[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]----------------------------------------[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]x86 Registers[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]----------------------------------------[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]EAX=630C7C57  EBX=7C55AFF4  ECX=7C958CE0  EDX=FFFFFFFF  ESI=630C7BEF[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]EDI=00000000  EBP=003AD618  ESP=003AD5F0  EIP=7C47285D  FLG=00210202[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]Hardware/Driver Information:[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Processor:              0x0[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Page Size:              4096[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Min App Address:        0x10000[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Max App Address:        0x7ffeffff[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Processor Mask:         0x3[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Number of Processors:   2[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Processor Type:         586[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Allocation Granularity: 65536[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Processor Level:        6[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Processor Revision:     3853[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Os Version:             5.1[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Os Service Pack:        4.0[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]Percent memory used:    10[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Total physical memory:  3964948480[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Free Memory:            3561668608[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Page file:              6209036288[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Total virtual memory:   2147352575[/SIZE][/FONT]


[FONT=Arial, sans-serif][SIZE=2]Lemme know what you think
[/SIZE][/FONT]

---

### Post by hikaricore on 2009-10-19
> **Wasteload said:**
> On the tutorial you sent me, I am trying to update my nVidia driver to the newest at the site suggested:
[ftp://download.nvidia.com/XFree86/](ftp://download.nvidia.com/XFree86/)

I tried to download nvidia install but it seems to be all source code, hints?

The latest nvidia driver is always listed here.

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

The ones you're looking at are dead wrong.
But you shouldn't need to install these if you already have 180.44 installed.
Have you tried any native 3d games to see if they work?

---

### Post by Wasteload on 2009-10-19
May I ask how to get to the Restricted Drive Manager?

Sry big noob here

---

### Post by beastrace91 on 2009-10-20
> **hikaricore said:**
> 
The ones you're looking at are dead wrong.
But you shouldn't need to install these if you already have 180.44 installed.

Or unless you want a better FPS. The 180.44 drivers work but they are dated (Karmic uses 185 even now) I've gotten at least a small FPS boost with almost every successive new release of nVidia drivers released... And that ftp link he posted is the right one - its an archive of all nVidia drivers released up until this point.


Do you have a 32bit or 64bit Ubuntu install? This determines which drivers you want to download.

Also to install from the binary packages on the FTP site you will need to follow the instructions [here](https://help.ubuntu.com/community/NvidiaManual)

~Jeff

---

### Post by Wasteload on 2009-10-20
Got this info with this uname -a

2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

---

### Post by beastrace91 on 2009-10-20
> **Wasteload said:**
> 
2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 **i686** GNU/Linux

Thats the key - its 32bit :)

The 32bit drivers are listed [here](ftp://download.nvidia.com/XFree86/Linux-x86/)

Install the latest 185.xx driver if you want stable or if you want more bleeding edge try the 190.xx drivers (be cause some times these cause system lock ups now and again - thus beta)

~Jeff

---

### Post by justmikeit on 2009-11-02
I was trying to use the stable version of wine but it didnt work for me, had to get the beta wine from the software center to click the accept the terms. Right now it is downloading will take quite awhile to download the file.

---

