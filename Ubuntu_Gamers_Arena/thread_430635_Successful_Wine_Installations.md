---
title: "Successful Wine Installations"
date: 2007-05-02
forum: Ubuntu Gamers Arena
---

### Post by compiledkernel on 2007-05-02
Gonna sticky this one. 

Try to keep it clean of discussion. Just post 

1. Game name and manufacturer. 

2. How the installation went. 

3. What you did to get it running.  

4. Glitches you noticed during game play.

5. Wine Version used.

---

### Post by compiledkernel on 2007-05-02
1. Prey - 2kGames
2. Pretty flawless 
3. wine /pathtocdrom/setup.exe to install Prey.
    wine prey.exe in the installation directory to run the game.
4. Nothing that I could detect. 
5. 0.9.34

---

### Post by LordFu on 2007-05-09
1. Fallout 2
2. Fine
3. wine ~/setup.exe
4. None yet. Edit: Keyboard doesn't work, playable.
5. 0.9.36

1. Icewind Dale II
2. Minor hassle, wine has an issue with ejecting discs during some installs. You'll need two cd drives or rip the disks to iso.
3. wine ~/setup.exe
4. None yet.
5. 0.9.36

1. Starfleet Command II
2. Minor hassle, wine has an issue with ejecting discs during some installs. You'll need two cd drives or rip the disks to iso.
3. wine ~/setup.exe
4. None yet.
5. 0.9.36

1. UFO: Alien Defense
2. N/A
3. Copied old windows install to wine "drive_c"
4. It runs too fast. Edit: Keyboard doesn't work, unplayable.
5. 0.9.36

---

### Post by YokoZar on 2007-05-10
> **LordFu said:**
> 
1. Icewind Dale II
2. Minor hassle, wine has an issue with ejecting discs during some installs. You'll need two cd drives or rip the disks to iso.
3. wine ~/setup.exe
4. None yet.
5. 0.9.36

1. Starfleet Command II
2. Minor hassle, wine has an issue with ejecting discs during some installs. You'll need two cd drives or rip the disks to iso.
3. wine ~/setup.exe
4. None yet.
5. 0.9.36Try opening a terminal and typing "wine eject" - this command will tell the wineserver to release the wine processes still locking the CD (and therefore you'll probably get better results than just using the eject terminal command or pressing the button on the drive).

---

### Post by LordFu on 2007-05-10
Sweet, thanks for the tip!!! I'll try to install BG II with that. I've been putting it off because I didn't know of a way to deal with the eject issue.

Edit: Didn't work for me.

---

### Post by DoctorMO on 2007-05-15
Game: Imperialism II (Frogcity)
Wine Version: git-12052007 + patches (see below)

to add patches:

```

cd wine-git/
wget -qO - www.winehq.org/pipermail/wine-patches/attachments/20070509/30cd6ce4/123db4b8476ad3b1e3cd945c00be97a70a4fcc72.bin | patch -p1
wget -qO - www.winehq.org/pipermail/wine-patches/attachments/20070509/2a09b994/f25150f3472fe0aab983384d14e8dacc56f595c5.bin | patch -p1
wget -qO - www.winehq.org/pipermail/wine-patches/attachments/20070509/acb0387d/d01ca3642f6f72d5a1589ab07348b1032151c731-0001.bin | patch -p1

```

to install just compile the source in the normal way.

These patches should be added soon to 0.9.38 so no need to patch soon.

---

### Post by Skylara on 2007-05-18
1. Game name and manufacturer: World of Warcraft/Blizzard

2. How the installation went: Almost perfect

3. What you did to get it running: I followed the WoW installation instructions [here]("https://help.ubuntu.com/community/WorldofWarcraft").  Before I even loaded the game, I also did a search on the Ubuntu forums and on the [Wine website]("http://appdb.winehq.org/appview.php?iVersionId=6482") for WoW issues.

4. Glitches you noticed during game play: When I first loaded the game after all of the installs and patches and such, everything worked fine, but I had two mouse pointers and, twice during a raid that evening, I crashed.  After looking into the problem, I realized I forgot to put *-opengl *  at the end of my launch command.  Once I did that, everything was great AND I have double the framerate I had when running in Windows.  As an aside, I made my gaming PC a purely Linux PC when I installed Ubuntu for the first time.

5. Wine Version used: 0.9.30

--------------
Note for Ubuntu newbies: I never even heard of Ubuntu before Wednesday, May 16, 2007 and had NEVER touched a Linux OS.  On Saturday, May 19, I got the Official Book and took the plunge.  If someone as new to Linux and Ubuntu as me can do this, I think most anyone can!

---

### Post by dj3019 on 2007-05-31
1. MOHAA / EA Games
2. Flawlessly (Was even able to insert 2nd disk)
Problems:  Mouse pointer:  Game has trouble locking the mouse pointer to the EXE so it is impossible to turn and manuever in the game.

What I Did: In the file browser I just right-clicked the setup on the disc and chose open with wine.  Installer ran without a hitch and placed in the wine installation directory of /home folder/.wine/drive_c/Program\ Files/EA\ GAMES/MOHAA then I ran the game in both the terminal and from the file browser with no errors other than the one stated above.  Any ideas on how to fix this?

1. Jedi Knight 2 - Jedi Outcast / Lucas Arts
2. Flawlessly
3. Same as MOHAA
4. None.  Works greater if not better than windows

---

### Post by akinwale on 2007-06-01
Hidden & Dangerous Deluxe - Take Two Interactive

It appears there's a problem with InstallShield when you try to install to a fat32 partition. I got an error which read "Unable to set time on file" or something along those lines. Any ideas? No problems whatsoever with an ext3 partition, though.

Ran hddeluxe.exe through the Wine File browser.

Some texturing glitches. Menu audio and music volume okay, but In-game audio too low. But that may be because I had Songbird open.

Wine version 0.9.33

---

### Post by JunySan on 2007-06-01
1. Jedi Knight II :Jedi Outcast /Lucasarts
2.fine
3.runs from .exe in wine directory, only on fullscreen mode.single & multiplayer runs perfect.
4.need to tweak sound settings on wine to get sound working.
5. wine 0.9.33

---

### Post by cro on 2007-06-05
I took a slightly different approach: I installed all my games when logged in to my Windows installation, then I run the games from Ubuntu using wine through an ntfs-3g mount.

1. World of Warcraft
2. N/A
3. wine <path to game>/wow.exe
4. Very occasionally my UI settings fail to load. On the plus side, I seem to get a higher frame rate running WoW with wine under Ubuntu than under Vista (about 5fps extra under Ubuntu) on the same hardware.
5. 0.9.38

1. Need for Speed: Carbon
2. N/A
3. wine <path to game>/nfsc.exe
4. None
5. 0.9.38

1. Zanzarah: The Hidden Portal
2. N/A
3. wine <path to game>/zanzarah.exe
4. Game does not run, no error shown. I'm going to try installing this through Wine at a later stage.
5. 0.9.38

---

### Post by OrbJinzo on 2007-06-07
Hi im new around here 

1. Starsiege Tribes
2. OK
3. wine <path to game>/Tribes.exe
4. The sound doesnt work for some reason i havent figured how to fix that problem yet. The game runs smooth as butter.Mutli player runs well on it. 
5. 0.9.38

---

### Post by hikaricore on 2007-06-09
> **OrbJinzo said:**
> Hi im new around here

Dayton Represent!!!
One of my old stomping grounds ^_^

Welcome to the community.

---

### Post by OrbJinzo on 2007-06-14
> **hikaricore said:**
> Dayton Represent!!!
One of my old stomping grounds ^_^

Welcome to the community.

hehe thank you.

---

### Post by OrbJinzo on 2007-06-14
im gonna add some more to this list

1. Tribes 2
2. OK
3. wine <path to game>/Tribes2.exe -online
4. The sound doesnt work for some reason i havent figured how to fix that problem yet. The game runs smooth as butter.Mutli player runs well on it.
5. 0.9.38


this is non linux version of its runs pretty smooth.
__________________

---

### Post by nutz on 2007-06-25
StarSiege TRIBES

When the game first installs the sound doesn't work but after playing with the settings in Wine I got the game to work with DirectSound. I have the GSI version of TRIBES updated to 1.11 and Wine 0.9.39. All features of the game work perfectly and the performance is every bit as better than Windows.

---

### Post by j.miller565 on 2007-06-25
1. Star Wars Episode 1 Racer
2. Fine
3. wine <pathtogame>/RACER001.EXE
4. Cinematogrophy lags and you can't get stop watching it by pressing Esc, Enter, etc 

Playing the game works like a dream. It even works better on Ubuntu than on Windows :)
5. 0.9.36

---

### Post by dragonwings on 2007-07-03
battlefield 1942 running with wine
to do it i 
                 :1/ installed on windows
                 
                 2/insalled nocd 

                 3/used a install maker programe (can find free downloads on net)
                     and made an install with the cracked bf1942 from programe files in windows

                 4/ burn newly made installer to disk
                 
                 5/on my ubuntu 7.04 fully updated .use to wine install game from disk

                 new//>>>>  delete movie files to fix sound and for smooth start up

---

### Post by hikaricore on 2007-07-03
@dragonwings: Merged into WINE thread.

---

### Post by Nehvrook on 2007-07-13
1. Dawn of War - Dark Crusade by Relic & THQ

2. Installation worked fine, nothing unusual

3. It worked straight away when I'd installed it

4. Units weren't saying their little sound bites when I clicked on them. Setting drivers to ALSA and ticking driver emulation in the audio settings of winecfg fixed this. The framerate is slightly lower than it was on Windows in the same settings.

5. Wine Version = wine-0.9.40

---

### Post by cogadh on 2007-08-23
First, a couple of things about my default config; these are the settings I use for every game unless otherwise indicated. I always keep OS set to Windows XP. I have registry edits set to enable opengl as the Direct Draw renderer, enable GLSL, make the video memory 256MB, allow direct access to the sound hardware and set Internet Explorer version to IE6SP1 (Gecko engine is installed). I only use a virtual desktop window when running the installation, otherwise games are all run in full screen. My audio is set to ALSA with full hardware acceleration, 48000 sample rate, 16 bits per sample and driver emulation on. I have library overrides set for all of the d3dx9_##.dll files, d3dx10_33.dll and msvcirt.dll. All games are launched in a separate X Session using a launch script.

1. Star Wars: Knight of the Old Republic | LucasArts 
2. Perfect, but patches do have to be manually applied 
3. Cracked exe, turn off hardware mouse in game settings
4. some sound stuttering, mouse rotation is restricted
5. 0.9.43

1. Star Wars: Knight of the Old Republic II - The Sith Lords | LucasArts
2. Perfect, but patches do have to be manually applied
3. Cracked exe, turn off hardware mouse in game settings
4. sound cuts out completely on some games, comes back after a restart; same mouse problem
5. 0.9.43

1. Star Trek: Armada II | Activision
2. Perfect
3. No-CD crack is NOT required, nothing extra required
4. Can't skip opening cutscene, multiplayer crashes
5. 0.9.43

1. X-Com: Interceptor | MicroProse
2. Needed to set OS to Win 98
3. Cracked exe
4. Seems to work fully, didn't try multiplayer or using joystick
5. 0.9.43

1. Hitman II: Silent Assassin | Eidos
2. Perfect
3. Cracked exe, followed instructions [here]("http://appdb.winehq.org/appview.php?iVersionId=1848") for additional config
4. Works perfectly
5. 0.9.43

1. Vampire: The Masquerade - Redemption | Activision
2. Perfect
3. No-CD crack is NOT required, options cannot be set in-game (edit the masquerade.ini file manually), OS set to Win 98
4. Some textures are missing on initial launch, cleans up as the game progresses. Mouse cursor has wrong texture
5. 0.9.43

1. Advent Rising | Majesco
2. Install produces an error at the end, but does complete successfully
3. No-CD crack is NOT required, nothing extra required
4. Mouse movement is restricted and tends to jump around 180 degrees, wide screen bars on cut scenes are blue instead of black
5. 0.9.43 
**NOTE: as of Wine 0.9.45, this game does not work at all anymore**
**NOTE2: as of Wine 0.9.50, this game works again, but the mouse movement is still restricted**

1. Freedom Force | EA/Crave/Irrational Games
2. Perfect
3. No-CD crack is NOT required, nothing extra required
4. Single player works perfectly, did not try multiplayer
5. 0.9.45
**NOTE: as of Wine 0.9.46, this game does require a cracked .exe**
**NOTE2: as of Wine 0.9.49, this game does _not_ require a cracked .exe again**

1. Vampire: The Masquerade - Bloodlines
2. You need to use "wine eject" to swap out the first CD, not required for the third
3. No-CD crack is required
4. At launch, the main menu screen and all sub-menus are blank, however the main menu items are visible when the mouse hovers over them. To "un-blank" all the menus, start a new game, then cancel out of the character creation screen when you get the option to distribute attributes.
5. 1.0-rc2

More to come...

---

### Post by joeyea on 2007-08-26
warcraft 3 

- i installed it by clicking install in wine 
- it installed perfectly 
- i had to use a no cd crack because it didnt recognise the disk was in 
- problems: it ran extreemly slowly even with opengl

---

### Post by tsukasa80 on 2007-08-29
reflexive arcade/Thorsten Kuphaldt/ea games/double fine productions/sega

reflexive acrade games are as follows 

jets n guns heavy weapon mutant storm aveyond installation was normal just run in wine. starts from kicker.
aveyond wont show text and sound is buggy

thorsten kuphaldt
typhoon 2001 once again normal install and starts from kicker.

ea games
alice  normal install runs for me with nocd patch

double fine productions
psychonauts normal install runs fine once again nocd patch

sega
sonic riders install went flawless upon running goes to opening load screen and freezes.

they are all running in xp mode and all were installed with virtual desktop and virtual desktop turned off when playing.used wine-doors to install directx 9 runtimes that seems to help. 

gutsy x86_64 
kernel 2.6.22-5 custom compiled 
wine version 9.43 from feisty repo

---

### Post by tsukasa80 on 2007-08-30
two more to add
croteam/interplay

serious sam the install selection was blind they all said install just guessed and clicked the right one install was good sound is good could be better graphics are faithfully reproduced the menu takes a second to grab the mouse but  the game as a whole runs smoothly

kingpin life of crime easy install just click installer and go.

both were as i always do nocd patched 

using wine 9.43 xp mode
gutsy x86_64
custom compiled 2.6.22-5 kernel

---

### Post by cyb3rj on 2007-09-19
> **JunySan said:**
> 1. Jedi Knight II :Jedi Outcast /Lucasarts
2.fine
3.runs from .exe in wine directory, only on fullscreen mode.single & multiplayer runs perfect.
4.need to tweak sound settings on wine to get sound working.
5. wine 0.9.33

What were your sound tweaks?

---

### Post by mr_boo1711 on 2007-09-25
> **Nehvrook said:**
> 1. Dawn of War - Dark Crusade by Relic & THQ

2. Installation worked fine, nothing unusual

3. It worked straight away when I'd installed it

4. Units weren't saying their little sound bites when I clicked on them. Setting drivers to ALSA and ticking driver emulation in the audio settings of winecfg fixed this. The framerate is slightly lower than it was on Windows in the same settings.

5. Wine Version = wine-0.9.40

Right - this is my next project - Using WINE, and in particular with DoW. :)

Nehvrook (Or anyone for that matter) - can you you do LAN gaming ok across platforms (i.e Windoze and inux both running DoW) without any serious problems?  Can't see why not I suppose, but WINE is very alien to me (I've had to overcome my other Ubuntu issues before dealing with this first you see) ;)

---

### Post by Ferrat on 2007-10-09
1. Baldur's Gate + Tales of the Sword Coast - Black Isle

2. Installation is simple just install as you would in windows.

3. Downgrade wine to 0.9.36

4. When looking at some items (only arrows) the game crashes but you can use the arrows even when not identified. (if you still see the mouse arrow over the BG pointer just ALT+F4, then say no the leaving the game and it disappears)

5. 0.9.36 (later versions break the game)
---------------------------------------------------------------------------------------------------


1. Baldur's Gate 2 + Throne of Bhaal  - Black Isle

2. You need to download and install the version 6 install engine from  [consumer.installshield.com/kb.asp?id=Q108322]("consumer.installshield.com/kb.asp?id=Q108322")

3. Download the install shield engine and for playable preformance you best go with 16bit color and software rendering options and not over 800x600 resolution. OpenGL doesn't work the HID doesn't refresh (early wine versions is said to be able to handle this) and 32bit studders and flickers alot.

4. Game freezes sometimes for a few seconds and can get a little choppy at times, mouse pointer flickers a little (if you still see the mouse arrow over the BG pointer just ALT+F4, then say no the leaving the game and it disappears)

5. 0.9.46
----------------------------------------------------------------------------------------------------

1. Guild Wars

2. Installation works fine

3. Get the install scrpit from the "get GW running" thread (installs wine + lightfix for GW and GW)

4. Some 2D rendered sprites are shown with a white,  black or pink box around them cause the alpha channels don't work as they should.

5. 0.9.44 + lightfix

---

### Post by firedrow on 2007-10-18
1. Day of Defeat: Source / Valve
2. Downloaded no problem
3. Had to put the Tahoma.ttf in WINE's Windows/font folder, then typed "msiexec /i SteamInstall.msi" to install Steam, then just waited for it to download.
4. Testing more tonight, but ran just as smooth as Windows runs it.
5. 0.9.45

Joeyea, have you tried tweak W3 any?  I tweaked mine and then played LAN games all weekend with it.

1. Warcraft III: Frozen Throne / Blizzard
2. Installation is flawless.
3. Using no-cd patch, had to do some tweaking to get it to run smoothly.  Just ask if you want my settings.
4. Laggy, LAN games would lock me up.  Several tweaks fixed it.  Also had to back down from 0.9.46 to 0.9.45.
5. 0.9.45

1. Starcraft Broodwar / Blizzard
2. Installation is flawless.
3. Using no-cd patch, just so I don't carry the disc.
4. None yet.
5. 0.9.45

1. Diablo II: Lord of Destruction / Blizzard
2. Installation is flawless.
3. Using no-cd patch, just so I don't carry the disc.
4. None yet, but I'm not very far in yet.
5. 0.9.45

---

### Post by spikeb on 2007-10-27
1. Diablo II: Lord of Destruction

2. Flawless

3. Installed Using Wine. Worked flawlessly.

4. None.

5. 0.9.46

---

### Post by phreakshew on 2007-11-09
1. Truck Dismount

2. 1st time I used Wine; thought it went good at first, but it's not 100% good...

3. Ran winecfg, installed setup.exe file, cd to Desktop and installed it (wine blah/blah/Desktop/TruckDismount101setup.exe)

4. Under Applications tab in menu bar, Wine- Programs- Truck Dismount- Truck Dismount did not load game properly.  Right clicked Applications and edited menu, re-typing in the path to the game, checked by winefile.  It worked for a time, then stopped.  (After a couple times of opening the game, it wouldn't open that way anymore.)  So then I navigated to the .exe file and selected Properties, then Open With, hit 'Add' button, then 'Use a custom command'.  Typed in wine, then Add, and Close.  Again, the game loaded correctly for a couple tries, then nothing.  It does still load if I click on it from within winefile though. 

Any ideas?

5. Wine Version 0.9.47 on Ubuntu Feisty

---

### Post by vek on 2007-12-22
ThreadSpace: Hyperbol (an indie game) on steam
[LIST=1]
[*]Installed Steam as per all the other guides
[*]Installed ThreadSpace: Hyperbol from steam game browser
[*]Copied D3DX9_32.dll from another place (haha) to the games folder
[*]Edited startup parameters to go my desired resolution and windowed mode
[/LIST]

Well, the developers of the game actulaly put a guide up step by step for ubuntu: 
[http://wiki.hyperbol.com/moin.cgi/LinuxWINEGuide](http://wiki.hyperbol.com/moin.cgi/LinuxWINEGuide)

I know, its cheating cuz I'm one of those devs, haha.  But hey, I use ubuntu, I play it under ubuntu, I figure people would want to know how :) I'm excited about it cuz I just tried it using the latest wine and the pixel shaders, blur, glow, and so on all suddenly work just fine. -glee-

I've heard that copying/installing D3DX9_32.DLL is no longer necessary as of the latest WINE versions.  Can anyone confirm this?

---

### Post by mr_boo1711 on 2007-12-31
> **Nehvrook said:**
> 1. Dawn of War - Dark Crusade by Relic & THQ

2. Installation worked fine, nothing unusual

3. It worked straight away when I'd installed it

4. Units weren't saying their little sound bites when I clicked on them. Setting drivers to ALSA and ticking driver emulation in the audio settings of winecfg fixed this. The framerate is slightly lower than it was on Windows in the same settings.

5. Wine Version = wine-0.9.40

Ok- I'm trying to achieve what's stated above, but alas - no results!  Now I'm getting use to Linux ok, but I'm a WINE novice (If there's such a thing).  I installed the most up-to-date version of WINE, but when I go to the CD and run the setup exe it LOOKS like its about to do something, and then it does nothing?!  Its setup to run all exe's as if it was XP and I cant see any other settings that look not right,  If you run the autorun.exe on the CD then it brings up the menu, and if you click 'install game' it pauses and then closes the virtual windows desktop.

Any ideas? :confused:

---

### Post by Victormd on 2008-01-11
> **cro said:**
> I took a slightly different approach: I installed all my games when logged in to my Windows installation, then I run the games from Ubuntu using wine through an ntfs-3g mount.


How does the "ntfs-3g mount" work? Because I also dual-boot and am trying to install all my games directly under ubuntu - no luck with any need for speed - so after reading your post, I think that's probably the best route for now. Could you explain how to get Ubuntu to recognize the directory under which the game is installed and correctly link all the dlls (not to access the NTFS partition)?
Thanks

---

### Post by Victormd on 2008-01-12
Warcraft III
- Installed from mounted CD image
- It worked straight away
- No graphics or audio issues so far
- Wine Version 0.9.52

Need For Speed High Stakes
- Installed directly from CD
- Still not working... I'm working on this one
- Wine Version 0.9.52

Adobe Photoshop CS
- Installed directly from CD
- Fully functional as far as I've tested it. I'll update as I work more on it.
- Wine Version 0.9.53

---

### Post by davidpeace on 2008-05-29
1. Diablo 2 with Lord of Destruction expansion
2. Wine version that I downloaded with the cd image (amd64)
3. Only two minor glitches: a. pressing alt to show items on the ground and then clicking on it won't pick up the item, but instead brings up a dialog about whether I want the window on top.... My work-around is to just click anywhere and press alt twice (2 times). b. Sometimes, during game transitions, or starting a new game without quitting D2LOD, the sound goes out. My solution: exit the game completely and restart.:)

---

