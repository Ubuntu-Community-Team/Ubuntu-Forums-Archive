---
title: "Howto: The Epic Baldurs Gate Installation"
date: 2010-03-23
forum: Wine
---

### Post by ZarathustraDK on 2010-03-23
**[SIZE=5]Preface:[/SIZE]**
The Baldurs Gate saga, probably one of the most epic stories ever brought to game, blessed by the gaming-gods of Arcadion. It is a HUGE RPG spanning 2 standalone games, each with their own expansion pack; I'm not lying when I say I've spent months in this game, there are so many ways to play, a plethora of spells and abilities and a story that's right up there with Tolkiens "Lord of the Rings".

Speaking of Tolkien, wouldn't it be neat if you could have "The Hobbit", "The Fellowship of the Ring", "The Two Towers" and "The Return of the King" in one bigass book that you could pull out and feel the weight of? Well, I'm not gonna give you just that, instead I'm going to give you "Baldurs Gate", "Baldurs Gate: Tales of the Sword Coast", "Baldurs Gate II: Shadows of Amn" and "Baldurs Gate II: Throne of Bhaal" all weaved into one, one RPG to rule them all...ok let me rephrase that...you get:

[LIST]
[*]To play Baldurs Gate with BGII interface, engine and graphics.
[*]To play from level 1 to level awesome without having to "recreate" the character between games.
[*]To start characters in BG1 using the races, classes and whatnot available from BGII: Throne of Bhaal.
[*]To play the first Baldurs Gate game in resolutions higher than 640x480 (1600xsomething is the max I think).
[*]To do it on Ubuntu!
[*]A ton of other stuff. (Really, as in "a metric ton of ink is necessary to describe all the neat little features of this setup", kudos to the creators of EasyTutu for one awesome project.)
[/LIST]

**[SIZE=5]What you'll need:[/SIZE]**
[LIST]
[*]An Internet-connection
[*]Baldurs Gate
[*]Baldurs Gate: Tales of the Sword Coast
[*]Baldurs Gate II: Shadows of Amn
[*]Baldurs Gate II: Throne of Bhaal
[*]Plenty of space on your harddrive (imagine installing all the games, then multiply by 3, then add some for safety).
[/LIST]

**[SIZE=5]What's going to happen?[/SIZE]**
You're going to install each game with Wine. When that's done you'll patch the second game expansion with it's latest patch, and lastly you'll install Easytutu that'll combine all the games so that you can play through from the beginning of Baldurs Gate to the end of Throne of Bhaal using the Baldurs Gate II interface, in one continuous story, and without annoying cd-swapping. Hey, stop drooling...

**[SIZE=5]Step 1 - Making it easy for yourself[/SIZE]**
Ok you have 4 game-boxes in your hands, that's a lot of cds. Perhaps if you're lucky you got the DVD-versions then you only have 4 DVD's. To make it easy for yourself do the following:

- Create a folder called "BaldursGate" somewhere where you have plenty of space and normal userprivileges (for the sake of this howto let it be /home/joeuser/BaldursGate).

- Inside this folder create 4 other folders, one for each game/expansion (for this tutorial call them "BG", "BGEXP", "BG2" and "BG2EXP").

- Now for the annoyingly tedious thing: backup all the games to their corresponding folders you just created, just go the root of the cd, press CTRL-A and copy the whole thing over, one disc at a time (remember to press CTRL-H to reveal hidden files, just for good measure). Do not worry about overwriting stuff when copying multiple cd's into the same game-folder, they do exactly the same.

- Yep it's a lot of space, don't worry, we'll clean up afterwards.
- If your cd's are scratched then "get it somewhere ;)". I'm not much for piracy of luxury-goods, but you're sitting with 12-14 cd's that are very old, chances are one of them are messed up, soo...wink-wink-nudge-nudge.

**[SIZE=5]Step 2 - Installing the games[/SIZE]**
Now you have to install the games, but they can sometimes be quite picky about having cd's inserted during installation. For me BGII was a royal pain until I figured out how to cheat it. Anyway here's how it goes:

I assume you have Wine installed and working, so in a terminal go:
```

cd /home/joeuser/BaldursGate/BG

```Then, once inside your backed up Baldurs Gate folder do:
```
wine Setup.exe
```You will be guided through installation by the installer. When prompted to choose which kind of installation you want choose "Custom" and mark ALL the content. The game should then install allright.
At the end an annoying video-sequence will start; kill it off however you can (as it froze everything on my screen I CTRL-ALT-F1'ed to a terminal, ran "top" and killed the process-id of the video, then CTRL-ALT-F7 back to my desktop.

- Repeat the same procedure for your BGEXP-folder.

- For the BGII-folder we need to trick the installer (at least I had to). If you don't do this the installer will go to 95% then ask for CD 1, you'll try and point it out to it, but it wont work; do this instead:

- In a terminal type:
```
winecfg
```It'll bring up Wines configuration utility.

- Pick the "Drives"-section.

- Add a new drive-map and point it to your BGII-folder.

- In the same window, click Show Advanced"

- Highlight the drive you just added and change "Type" to CD-ROM.

- Click apply. and close down the window.

**IMPORTANT SIDENOTE:** If you ever run into "insert cd X"-problems, then the above is the way to fix it. If you add a drive this way Wine (or rather the game) will think your backed up cd's are the real cd's = no ingame cd-swapping and NO install problems. As far as I know you anly need to add CD 1 from BGII (for the install only) and the BGIIEXP CD (in order to play the game) this way and everything should be peachy.

Anyway after this little detour you can now install BGII and BGIIEXP using the already covered method.

You should now have installed all 4 games/expansions preferably at the installers default location which would be /home/joeuser/.wine/drive_c/Program Files/Black Isle/*.

**[SIZE=5]Step 3 - Stitching the beast together[/SIZE]**
We are now just about ready to create one mean game. First, though, we need to patch up Throne of Bhaal to the latest patch (only one needed), so go to [http://www.bioware.com/games/throne_bhaal/support/patches/](http://www.bioware.com/games/throne_bhaal/support/patches/) and get it. Run it with Wine and let it do it's thing, shouldn't pose any problems.

Now for the interesting part - Easytutu!
- Download Easytutu here : [http://www.usoutpost31.com/easytutu/](http://www.usoutpost31.com/easytutu/) , pick the one called "Easytutu_ToB.exe".
- Run it with Wine.
- During installation it will ask for your game-installation directories; the defaults should work if you went with the defaults when installing the games/expansions, if you didn't then point the installer to them when it asks. By default the installer will install the whole shamoo to /home/henrik/.wine/drive_c/Program Files/BaldursGateTutu, let it do this, generally just go with the defaults unless you have space-problems.

The Easytutu-installer will now work its wonder. It'll copy all the resources and necessary files from the 4 games/expansions into the BaldursGateTutu-folder, stitch the ******* together, and make it so you use the BGII-interface and BGII-engine for playing the WHOLE thing in one seamless game.

After this you should be good to go. Fire up Baldurs Gate Tutu and give it a whirl (either through the new menu-entry in Applications->Wine->Programs or the old fashion way). REMEMBER: if it starts asking for cd's you need to point out the dir in winecfg using the method previously mentioned. If you did this HowTo correctly, then you should now only need a drive that points to your BGIIEXP-directory.

**[SIZE=5]Issues:[/SIZE]**
**The sound is horrible/the sound freezes the game**
So far I've only had sound-issues. Usually this is because of pulseaudio. The fix is thus:
```
gedit /home/joeuser/.pulse/client.conf
```Then add:
```
autospawn = no
```to the blank file and save it.
Open up winecfg and go to the Audio-tab. Make sure Wine uses alsa for sound, not Esound or anything else.
Now, everytime you want to play to game first open up a terminal and do
```
killall pulseaudio
```so it wont interfere with the game-sound. When you're done playing do
```
pulseaudio -D
```to get back your sound.
NOTE: This sound-fix actually fixes sound in a lot of games besides this one, it's good to remember. Sometimes though the fix will turn your volume to zero once you bring back pulseaudio, don't panic and turn it up again :D.

**Equipping a 2-handed-sword or clicking at Khalid's paperdoll crashes the game! SEE UPDATE AT BOTTOM!**
These 2 actions (and probably a plethora of others I havent seen yet) causes the game to crash to desktop IF you've enabled 3d-accelerated graphics in the game-configuration, turn it off and you'll be dandy.

**The Main menu is messed up**
Yep, it's not a showstopper though.

**[SIZE=5]Cleanup-time![/SIZE]**
You safely delete the Baldurs Gate 1-installation in your wine-installation, it's not needed anymore. You can (in theory) also delete the backup "BG", "BGEXP" and "BGII"-folder. In essence, all you need now is the Baldurs Gate Tutu-folder, BG2-installation and the "BGIIEXP"-folder (the game needs it to run, for verification purposes I guess). I keep the backups around though as it's nice and handy and NOT AT ALL LIKE 12-13 FRIGGIN' CD'S WITH SCRATCHES!!!

**[SIZE="5"]UPDATE[/SIZE]**
Apparently running the game now presents you with a nonsensical error, this can be fixed by using winetricks to install Internet Explorer 7 (don't ask why)

Also, with a vanilla install, you'll only be allowed to run the game properly in 800x600 with 3d-acceleration on. Running it at larger resolution would crash the game when you try to equip a 2h sword, and running it without 3d-acceleration looks pitiful. This can be fixed by installing the Widescreen Mod from the Gibberlings Three found here : [http://www.gibberlings3.net/widescreen/](http://www.gibberlings3.net/widescreen/)
Remember to download the windows version as we're doing this thing with Wine and not GemRB. Put the file in your BaldursGateTutu folder, run it, and fill out the resolution questions, and you should be good to go, fullscreen, 3d-accelerated BG1-to-ToB goodness.

---

### Post by _h_ on 2010-03-23
Just a quick typo fix for you:

```
winecfg
```

You forgot the e. :)

---

### Post by ZarathustraDK on 2010-03-23
> **_h_ said:**
> Just a quick typo fix for you:

```
winecfg
```

You forgot the e. :)

Fixed :)

---

### Post by _h_ on 2010-03-23
> **ZarathustraDK said:**
> Fixed :)

:popcorn:

Nice guide too, I may check out the game for kicks later sometime, and will definitely follow this guide. :D

---

### Post by jokei on 2010-03-24
Quick question, I've already installed BG1 + TOTSC and run them with a minor sound issue, having problems with BGSOA - I'd like to follow this howto, but do I need to uninstall/re-install the 1st 2 (dvd) discs and folder them up to get this working - or can I just install SOA as you've described?

Awesome thread, it's good to see people still enjoy this game

---

### Post by ZarathustraDK on 2010-03-24
> **jokei said:**
> Quick question, I've already installed BG1 + TOTSC and run them with a minor sound issue, having problems with BGSOA - I'd like to follow this howto, but do I need to uninstall/re-install the 1st 2 (dvd) discs and folder them up to get this working - or can I just install SOA as you've described?

Awesome thread, it's good to see people still enjoy this game

Easytutu only needs the installed games (as in "have been installed in Wine from cd/dvd or backed up folders"). If you've installed BG1, TotSC and BGII then you should be able to use Easytutu as described. I just like to do the folder-thing because I have the cd-version and it eases the disc-switching; wine also used to have problems properly detecting cd's/dvd's when inserted, which screwed up the process).

Only thing that differs is that you'll need to patch with the latest SoA-patch instead of the ToB-one as this HowTo describes, and use EasyTutu_SoA.exe instead of EasyTutu_ToB.exe when you stitch it together in the end.

---

### Post by Juckiz on 2010-05-24
Hi, 
I managed to install everything just fine.
However the game doesn't work :(
I'm using Ubuntu 10.04 and everything should be fine graphically.
I tried running the game in 800x600 and 1024x768 windows and it sort of worked but crashes if i try to skip the intros... if i get to the main menu it's still not what it's supposed to be, likely to crash or "break graphically" if i click anywhere in the window.
Its definitely possible that my Ubuntu is to blame. This hasn't actually improved from 9.10. :roll:
Full screen doesn't work at all. Desktop resolution just changes to whatever is set in BG config.
I tried with and without Compiz with the same results.
Damn, i was looking forward to playing this after so many years...

---

### Post by ZarathustraDK on 2010-05-27
Hmm not sure about it since I made this how-to for 9.10, not 10.04; in my book it shouldn't make a difference.

Sounds like you've enabled the direct3d acceleration in bgconf or something.

If you run it in terminal what does it say?

---

### Post by Juckiz on 2010-05-28
Hmm, no i shouldn't have anything direct3d going on...

I'm not sure what i'm supposed to run but i ran 

```
wine BGMain.exe 
```

in Baldur's Gate Tutu -folder and i didn't catch the very beginning, but the terminal was filled with
```

err:gdi:alloc_gdi_handle out of GDI object handles, expect a crash
err:gdi:alloc_gdi_handle out of GDI object handles, expect a crash
err:gdi:alloc_gdi_handle out of GDI object handles, expect a crash
err:gdi:alloc_gdi_handle out of GDI object handles, expect a crash

```
and i had to kill the process. My desktop resolution changed to 800x600 which was currently selected in BGTutu conf.

btw, Warcraft 3 runs just fine with Wine so drivers should be ok...

---

### Post by ZarathustraDK on 2011-11-17
> **Juckiz said:**
> Hi, 
I managed to install everything just fine.
However the game doesn't work :(
I'm using Ubuntu 10.04 and everything should be fine graphically.
I tried running the game in 800x600 and 1024x768 windows and it sort of worked but crashes if i try to skip the intros... if i get to the main menu it's still not what it's supposed to be, likely to crash or "break graphically" if i click anywhere in the window.
Its definitely possible that my Ubuntu is to blame. This hasn't actually improved from 9.10. :roll:
Full screen doesn't work at all. Desktop resolution just changes to whatever is set in BG config.
I tried with and without Compiz with the same results.
Damn, i was looking forward to playing this after so many years...

Forgive my necromancy, but the above error is solvable by installing the Widescreen Mod from The Gibberlings Three [http://www.gibberlings3.net/widescreen/](http://www.gibberlings3.net/widescreen/), also, it fixes the 3d-acceleration bug so turn that mofo on.

So there, the full Baldurs Gate saga, now in 3d-accelerated fullscreen and, I guess, HD if your res can handle it. :D I know mine can.

---

### Post by jkavanagh00 on 2011-12-10
Hi, really thankful to you for making this guide but I seem to have come across a problem. I've done everything, installed all the games, backed up the discs (I have the 4 DVD box set), patched ToB, installed Tutu, used Winetricks to set up IE7, installed the Widescreen mod and made sure the 3D acceleration is off.
However...:(
If i run it from the menu I get "Error: File Not Found"
and if I run it from the terminal I get:
"An Assertion failed in ChDimm.cpp at line number 628
Programmer says: Unable to Open BIF:data\Hd0GMosc.bif"
followed by:
"Microsoft Visual C++ Runtime Library
Runtime Error!
Program C:\ProgramFiles\BaldursGateTutu\BGMain.exe
abnormal program termination"
I'm running Mint Ubuntu on a Toshiba Satellite Pro L300, which I'm pretty sure should be able to handle this game. Any advice or possible fixes you could give me would be greatly appreciated. You did a really good job of selling the whole Tutu package and now I REALLY want to play this game! :D

---

### Post by ZarathustraDK on 2011-12-11
> **jkavanagh00 said:**
> Hi, really thankful to you for making this guide but I seem to have come across a problem. I've done everything, installed all the games, backed up the discs (I have the 4 DVD box set), patched ToB, installed Tutu, used Winetricks to set up IE7, installed the Widescreen mod and made sure the 3D acceleration is off.
However...:(
If i run it from the menu I get "Error: File Not Found"
and if I run it from the terminal I get:
"An Assertion failed in ChDimm.cpp at line number 628
Programmer says: Unable to Open BIF:data\Hd0GMosc.bif"
followed by:
"Microsoft Visual C++ Runtime Library
Runtime Error!
Program C:\ProgramFiles\BaldursGateTutu\BGMain.exe
abnormal program termination"
I'm running Mint Ubuntu on a Toshiba Satellite Pro L300, which I'm pretty sure should be able to handle this game. Any advice or possible fixes you could give me would be greatly appreciated. You did a really good job of selling the whole Tutu package and now I REALLY want to play this game! :D

You say you installed Tutu, is that Easytutu or BGTutu? Tutorial is for Easytutu.

The BIF-line is about some game-resource file (BG stores its gamecontents in bif-files, kinda like Doom stores its stuff in .pak-files). See if you can locate the file in your game directory, if it exists, if its permissions (maybe it's read-only or some of the kind).

The aforementioned error could also be tied to the "Visual C++"-line, ie. there's some winecomponent missing. Try winetricks and install anything Visual C++-related.

As you might have guessed I haven't had this particular error, but I'd go for those seeing an error like that. Just a guess on my part.

---

### Post by jkavanagh00 on 2011-12-13
Hey, thanks for getting back to me on this. I got all the updates I could for C++ but I'm pretty sure that wasn't the issue. I'm going to run the install again and just make sure I got the directories right (btw I definitely used Easy Tutu). I guess I'll let the thread know when and how I get it to work :D

---

### Post by Athgardr on 2012-04-29
Hi there !
I don't know if my reply will be read because of the date, but i'll see.
First, thank you for this tuto ! 
A friend of mine made me discover Baldur's Gate games and wonders ! 
As I run a debian so I had to run it via wine. So I did and started with the BG1. Worked correctly, somehow with few bugs seen in tutos (videos sequences crash, wiverns encounters crash, sound bugging ...), but the game worked.

Before arriving in the Baldur's Gate city, because I appreciate the game, decided to upgrade the installation. To do so this friend landed me his old DVDs (set with 4 DVDs, BG1, BG2 and both extensions, edited by "Mindscape" in France - so french version, but propose an english version too). And I searched ways to install correctly the game on linux, with mods.
The installation of the game works, but I have troubles with EasyTutu.

Here technical details:
- I run a eeepc 1000He, Debian Wheezy 3.2.0, lxde 0.5.5.2, wine 1.0.1-3.1
- I install wine programs in differents .wine config, in a dedicated partition with the WINEPREFIX command. Here: /mnt/Wine/BaldursGate
- So, a french edition of DVDs, but to stick with the tuto, I installed the english version of the game (voices and comments are definitly less stupid than the french version !)
- difference with your tuto: I did iso copies of the DVDs to keep them in the pc (eeepc doesn't have CD driver). So I keep ISOs mounted into /media/BG/BG /media/BG/BGEXP etc.

So.
- The install of the two games, english version, and the two extensions worked w/o problem.
- as did the BGII-ThroneOfBhaal 26498 patch.

But the install of the EasyTutu didn't worked:
After reading [the EasyTutu page](http://www.usoutpost31.com/easytutu/), I tried two ways: 
- the last updated EasyTutu stuff, with a .net framework 3.5 installed first in Debian.
the install of the .net (win version) worked correctly. The EasyTutu didn't, here what wine tells me:
> Missing method .ctor in assembly 
Can't find custom attr constructor image: mtoken: 0x0a00000f
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: Could not load type 'EasyTutu_2011.App' from assembly 'EasyTutuManager, Version=1.0.8.0, Culture=neutral, PublicKeyToken=null'.
- then an older version as suggested by this same website:
> Some Installation files are corrupt.
Please download a fresh copy and retry I redownloaded the file, but get the same result.
Any suggestions ? 
To make my strongly armed knocking head dwarf dig all the Coast of the Sword pit a win!

---

### Post by Sarys on 2012-12-12
No I can't install this just because I have 64 bit Ubuntu :sad:

---

