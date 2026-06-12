---
title: "World of Warcraft problems with 9.04"
date: 2009-03-31
forum: Wine
---

### Post by nickgaydos on 2009-03-31
Hello, like many people I play World of Warcraft. I have recently installed Ubuntu 9.04 beta on my computer. After the installation, I pulled out my portable hard drive and copied World of Warcraft over to the hard drive of my computer. When I launched WoW and turned the settings up so that i can see, it was laggy. I got 60-100 Frames Per Second in 8.04.2 but in 9.04 i get around 30 with the resolution turned up to 1440 by 900. I ran the same thing in 8.04.2. Please help me. :) Other information will be provided under this paragraph.
SPECS:
Ubuntu 9.04 beta
HP Slimline s3600f
iNtel Pentium Dual Core @ 2.0Ghz
nVidia-BFG GeForce 8400GS with latest drivers.

WOW config:
 SET locale "enUS"
SET portal "us"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxRefresh "69"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET movie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "177"
SET particleDensity "1.000000"
SET realmName "Arygos"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET environmentDetail "1.5"
SET ffxGlow "0"
SET gameTip "16"
SET VoiceActivationSensitivity "0.39999997615814"
SET EnableVoiceChat "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET shadowLevel "0"

---

### Post by nickgaydos on 2009-03-31
I got the major problem fixed-the lag problem! now the only problem is that when I walk it "studders" a little bit. This is not major, but it can be fixed I'm sure!

[IMG]http://tinypic.com/view.php?pic=jskleg&s=5[/IMG] (Don't mind the bars, just of the screen shot)

---

### Post by n0manarmy on 2009-04-24
I've yet to get logged in. 

I'm running a fresh install of Jaunty 9.04. I updated and installed is WINE, JRE6 and copied over my data from my Windows 7 machine. I'm running a Lenovo T400 with Intel Centrino 2, Intel Integrated Graphics, and Intel Wireless Card.

My Config.wtf only contains

*SET gxApi "opengl"*

But all I get is 
[IMG]http://www.blogbaltimore.com/images/Screenshot.png[/IMG]

---

### Post by ubnutuupgrade on 2009-04-25
I get the exact same thing... All i do is play around with my world of warcraft settings in the options menu... I found that if you take off windowed mode then apply it again it usually works. Hope this helps =):P

---

### Post by sigend on 2009-04-25
Hey nickgaydos..About the walk/run issue,i noticed that it only happens when i use <<w>>(forward or uparrow).When im pressing both clicks simultaneously nothing happened!!So go to system/preferences/keyboard  and uncheck the option <<key presses repeat when key is held down>>.That worked for me m8:D



nomanarmy:  try deleting everything in ur config.wtf(ofc always keep a backup somewhere else) and then run wow..1st time u ll start the game i think the file will be created corectly.


my english  sux..^^:D

---

### Post by H0PE on 2009-04-26
im not even sure how you startit up. I just get a wow freeze when i start up, no login screens at all.
 
I did go through an install manual for wow but dont think that was up to date and it says very little about customizing wine or wow.
 
Any uptodate manuals what to set or how to try to fix if you got problems pls? (yes Im aware of the help on ubuntu forums here but that says very little too)

---

### Post by Haanz on 2009-04-26
Hey guys,
I'm getting a similar problem as n0manarmy. I thought it was because i didn't have any graphics card drivers anymore. maybe not though. does any body have a solution?

---

### Post by windowsareslow on 2009-04-26
Sorry to hijack the thread, but is anyone else having problem with keyboard data not being caught?  My login screen comes up, and my mouse works, but typing goes into the background, like a terminal window if that was the last thing focused.

thanks,
B

---

### Post by sigend on 2009-04-27
Hey windowsareslow,i have the same problem everytime i disable compiz.So I 1st type in terminal  metacity --replace.Then i close the terminal and i open a firefox window.I write something at my search engine(just to see that keyboard is working).Then i close firefox and i start wow.Its not a great solution but at least i can play wow!!!!^^

---

### Post by ianmc74 on 2009-04-29
> **n0manarmy said:**
> I've yet to get logged in. 

I'm running a fresh install of Jaunty 9.04. I updated and installed is WINE, JRE6 and copied over my data from my Windows 7 machine. I'm running a Lenovo T400 with Intel Centrino 2, Intel Integrated Graphics, and Intel Wireless Card.

My Config.wtf only contains

*SET gxApi "opengl"*

But all I get is 
[IMG]http://www.blogbaltimore.com/images/Screenshot.png[/IMG]


Exact same issue.  Please, has anyone figured this out.  Went in and deleted the WTF, Cache, (and some other file) to no avail.  When I did this I went through the previews but ended up with the same screen shot for logging in.  
My Linux experiance is 3 days old now so please hold my hand through any suggested fixes please.  :confused:

---

### Post by Clydtsdk-Rivendare on 2009-04-30
@scrambled-graphics-tos-problem-thing-people:

Any time I have a TOS/EULA problem, I go to config.wtf and if the lines

```

SET readTOS "1"
SET readEULA "1"

```aren't in there, make sure they are.

IDK if this will solve your problem or not but it's worth a shot.

---

### Post by dgsullivan on 2009-05-01
> **Clydtsdk-Rivendare said:**
> @scrambled-graphics-tos-problem-thing-people:

Any time I have a TOS/EULA problem, I go to config.wtf and if the lines

```

SET readTOS "1"
SET readEULA "1"

```aren't in there, make sure they are.

IDK if this will solve your problem or not but it's worth a shot.


I'm experiencing the same problem. Setting the two above just gets me to the login screen, yet it's still scrambled like the previous screen shot.

Here's my Config.wtf

"SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "4"
SET processAffinityMask "3"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET groundEffectDensity "24"
SET ffxGlow "0"
SET ffxDeath "0"
SET ffxSpecial "0"
SET gxApi "OpenGl"
SET M2UseShaders "0" "

I've also tried "SET gxApi "d3d"" and various other fixes.

---

### Post by Clydtsdk-Rivendare on 2009-05-01
Hm.... UI reset?

---

### Post by dgsullivan on 2009-05-01
> **Clydtsdk-Rivendare said:**
> Hm.... UI reset?

UI reset in the game? I can't make it that far. 

UI reset by deleting the WTF and Cache files? After that when I run WoW it starts at the video scene, which runs, although skippy. But then I'm back at the scrambled EULA.

---

### Post by dgsullivan on 2009-05-01
I've also tried to play WoW from another HDD where the game worked before on a Windows partition. I've also tried copying the WoW directory from one HDD to my Wine directory. Finally, I've tried a fresh install of the game. All give me the same problem, so I assume it isn't an issue with game.

But, just in case it was, I also ran the Repair.EXE with no success.

---

### Post by dgsullivan on 2009-05-01
When I run WoW in bash...

$ wine "C:/Program Files/World of Warcraft/WoW.exe"

gives me: 

fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
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
fixme:powrprof:DllMain (0x7d690000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d690000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

---

### Post by Clydtsdk-Rivendare on 2009-05-01
You can see an edit button in the lower right of your post?....

Anyway, I wish I could help but this is out of my league. Unless...

```
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
```

Have any addons?

---

### Post by dgsullivan on 2009-05-01
> **Clydtsdk-Rivendare said:**
> Have any addons?

None, it was a fresh install. I went to double check the folder though and it wasn't there. So I created it, and same results, minus that line.

---

### Post by laraby on 2009-05-04
I too had this issue, but if I remove SET gxAPI "opengl" in my config file it actually runs great, and I'm on a netbook!

---

### Post by Silvercloaks on 2009-05-09
I'm in the same boat as everyone in this thread.  I can get WoW to load up, but I can't see what's on the screen for the life of me.  I get lots of fractals and stuff...

Seems like Linux and my windows games aren't playing too nice. :(

---

### Post by Dimarchi on 2009-05-10
Silvercloaks (and/or dgsullivan), it may be that you need to do some regedit stuff, as described in

[http://www.phoronix.com/forums/showthread.php?t=6134](http://www.phoronix.com/forums/showthread.php?t=6134)

reply #8, the quote part, for example. I know I had to do it if I used SET gxAPI "OpenGL" in config.wtf or --opengl in wine command to unscramble the screen. There is no need to use SET gxAPI "d3d", since it is that by default, I think. The regedit thing can be left there if you remove the opengl parts (SET or --opengl), with no ill effect as far as I can see. Old advice, but may be relevant. Try it and see.

---

### Post by onsetofpurity on 2009-06-02
Im having the same problem as n0manarmy.

I'm thinking it has to do with my Intel Integrated Graphics..
Any fixes for it yet?

I tried the opengl in the WTF/config.txt file it only made it worse.

I, too have only been using Ubuntu for a few days.
I have Ubuntu 9.04 and the latest beta for Wine installed.

---

### Post by Inri on 2009-06-05
Same issue as the screenshot. I have had closer success by adding the original posters SET info into my WoW file. i can actually make out where the login is and CAN log in. but its definitely not playable. unless i wanted to play blind.

The most success i have had is using the World Of Warcraft Trial exe.

Any luck out there?):P

New to the forums. New to Ubuntu. Lovin' it!

---

### Post by onsetofpurity on 2009-06-06
Heres a screen shot of my game after login.. just for kicks :P

[IMG]http://img.photobucket.com/albums/v605/koonkiller/Screenshot.png[/IMG]

Enjoy!

---

### Post by roh8880 on 2009-09-04
I have a completely different problem! 

I upgraded to 9.04 and WoW worked for a little bit, but then I got the patch needed after the login screen and I clicked restart. Like normal, the downloader worked its magic, but it still says patch needed and restart no matter how many times I do it! Is there something wrong with the downloader? It still tries to download the same 397 mb file everytime!

---

### Post by Monkey Brawler on 2009-09-04
> **roh8880 said:**
> I have a completely different problem! 

I upgraded to 9.04 and WoW worked for a little bit, but then I got the patch needed after the login screen and I clicked restart. Like normal, the downloader worked its magic, but it still says patch needed and restart no matter how many times I do it! Is there something wrong with the downloader? It still tries to download the same 397 mb file everytime!

I haven't experienced the same issue, however i have experienced issues like that. I couldn't do a fresh install using the stable release. Once i added wine to my repository and downloaded the beta, that resolved my issues. I was unable to resolve the graphics issue so i broke down and just built me a computer. Now i get 130fps on ultra (NOT AVERAGE). Wow runs like a champ. If you dont know how to put wine in your repository hopefully [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) will be able to help ya out :P.

---

### Post by roh8880 on 2009-09-04
> **Monkey Brawler said:**
> I haven't experienced the same issue, however i have experienced issues like that. I couldn't do a fresh install using the stable release. Once i added wine to my repository and downloaded the beta, that resolved my issues. I was unable to resolve the graphics issue so i broke down and just built me a computer. Now i get 130fps on ultra (NOT AVERAGE). Wow runs like a champ. If you dont know how to put wine in your repository hopefully [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) will be able to help ya out :P.

Deleting the patch folder and the WTF folders and running the icon labled launcher, and then clicking of the updater button worked!

Now as my character runs around on screen, she seems to stutter step instead of showing the animation for running. Any tips?

---

### Post by Monkey Brawler on 2009-09-04
> **roh8880 said:**
> Deleting the patch folder and the WTF folders and running the icon labled launcher, and then clicking of the updater button worked!

Now as my character runs around on screen, she seems to stutter step instead of showing the animation for running. Any tips?

If you haven't yet, you always want to place 
> SET gxApi "opengl"In your WTF config file

If your experience problems and graphical glitches you may want to try placing

> SET ffxDeath "0"
SET ffxGlow "0"If you continue to have little issues this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) has all the help you should need
Disabling compiz or setting your appearance settings to "none" may help as well.

I have issues every now and then with stuttering usually jumping or doing an attack will fix it. I haven't cared to try to fix it. It doesn't bug me all to much. It may just be part of running wow on Linux :P

---

### Post by roh8880 on 2009-09-16
> **Monkey Brawler said:**
> If you haven't yet, you always want to place 
In your WTF config file

SET gxApi "opengl" 

SET ffxDeath "0"
SET ffxGlow "0"





That fixed it! Thank you!

---

### Post by alving on 2009-09-30
hello

i have a toshiba satelite pro 6000 laptop.
i have just installed 9.04 and wine.

i downloaded installer from WoW website.
when i ran the installer it got to 62% and the computer locked up.:(

after restart, i have almost no free space on the hard drive (used up about 16Gig), left me with ~4 Gig.
i cant find any of the temporary install files to delete them.

in another section of this forum i found a few other places that i deleted temp files from,
but, i still only have about 8.5Gig free space and it says i need at least 15.
there is no Worl of Warcraft folder in the Program Files folder.
i have already emptied the trash for both myself and as root.

im completely baffled.:confused:
any help will be greatly appreciated.
im fed up with windows and i just want to play my game.

thanks
alving

---

### Post by zoveress on 2009-10-07
Hey I have exactly the same lagging problem, how did you manage to fix that?
Cheers
Z.

> **nickgaydos said:**
> I got the major problem fixed-the lag problem! now the only problem is that when I walk it "studders" a little bit. This is not major, but it can be fixed I'm sure!

[IMG]http://tinypic.com/view.php?pic=jskleg&s=5[/IMG] (Don't mind the bars, just of the screen shot)

---

### Post by europa on 2010-01-08
I had this issue before but resolved it by installing the ATI drivers that envy installed.  I think it is an issue with the latest drivers.

Envy no longer has compatible drivers with my video card and now im stuck here too.  At the moment i'm working on looking for drivers to downgrade to.

---

### Post by oniea on 2010-03-27
I found the fix to the character / animation stutter problem. Not sure if i like it though. But if does fix the issue.

System > Preferences > Keyboard

General Tab > uncheck Repeat Keys. ( i don't like it disabled for the rest of the OS but, what i noticed in Warcraft while holding a key to cast it keeps highlighting the spell over and over. So i assume that was the issue with moving as well. )

Have a good one...

---

