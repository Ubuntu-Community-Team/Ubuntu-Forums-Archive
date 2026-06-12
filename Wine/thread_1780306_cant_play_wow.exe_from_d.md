---
title: "cant play wow.exe from d:\"
date: 2011-06-11
forum: Wine
---

### Post by japer855 on 2011-06-11
I have just installed Ubuntu 11.40 last night, and have been trying to play world of warcraft from my windows D:/games/World of Warcraftwow.exe
so far, i get an error messeage "Blocked: wine start /unix comes up as wow.exe is not marked as executable... so i tried to run with Wine Core exe, there is no graphic card that supports the game...
when i try and run it through "playOnLinux" i cant add D:/games/world of Warcraft/wow/exe
is there a way to play world of warcraft???

my spec is RF711-S01AU
******[FONT=Arial]Processor  [/FONT]****[FONT=Arial][/FONT]**
  [COLOR=#0D0D0D][FONT=Arial]InIntel® Core i7™ 2630QM Processor (Sandy Bridge)[/FONT][/COLOR]
 [COLOR=#0D0D0D][FONT=Arial](2.00Hz, 6 MB)[/FONT][/COLOR]
   **[FONT=Arial]Memory [/FONT]**
   [COLOR=#0D0D0D][FONT=Arial]6GB (DDR3 / 4GB x 1 + 2GB x 1 )[/FONT][/COLOR]
   **[FONT=Arial]Chipset [/FONT]**
  [COLOR=#0D0D0D][FONT=Arial]Intel® HM65[/FONT][/COLOR]
   **[FONT=Arial]Hard Drive [/FONT]**
  [COLOR=#0D0D0D][FONT=Arial]1TB (5400 rpm S-ATA / 500GB *2)[/FONT][/COLOR]
    **[FONT=Arial]Optical Drive [/FONT]**
 [SIZE=1]BluRay / DVD Combo[/SIZE]   **[FONT=Arial]Display  [/FONT]**
  [COLOR=#0D0D0D][FONT=Arial]17.3" LED LCD HD+ (1600 x 900) 16:9, SuperBright 280nit Screen[/FONT][/COLOR]
   **[FONT=Arial]Graphics[/FONT]**
   [COLOR=#0D0D0D][FONT=Arial]nVIDIA GeForce GT540M  (Optimus) +  Intel® HD Graphics[/FONT][/COLOR]
HDD been changed for Ubuntu (250GB)

---

### Post by jarrah-95 on 2011-06-11
from the error that you are getting, you need to right click on the wow.exe file and go to permissions, make sure that executable is selected. after doing this that .exe file should run in wine, although i cant garentee that the game will work. 
however, it that doesnt help, wine hq has many pages on how to set up wow on linux through wine

---

### Post by Noraphalem on 2011-06-11
World of Warcraft should run fine so far with Wine but it is recommended to use the OpenGL mode.
Therefore run the WoW.exe with the parameter '/opengl'.

For example:

**user@system $ wine ./WoW.exe /opengl**

Important: The linux shell is case sensitive! WoW.exe is not wow.exe.

---

### Post by japer855 on 2011-06-12
ill try that and let u guys know
thx

---

### Post by japer855 on 2011-06-12
> **jarrah-95 said:**
> from the error that you are getting, you need to right click on the wow.exe file and go to permissions, make sure that executable is selected. after doing this that .exe file should run in wine, although i cant garentee that the game will work. 
however, it that doesnt help, wine hq has many pages on how to set up wow on linux through wine

so far, i cant change the permission, when i put the tick on the permission, the tick disappears... i have tried to change to allow to read and write to all, but doing the same thing....

---

### Post by japer855 on 2011-06-12
so far no good, still the same error...

---

### Post by jocko on 2011-06-12
> **japer855 said:**
> I have just installed Ubuntu 11.40 last night, and have been trying to play world of warcraft from my [COLOR=Red]windows D:/games/World of Warcraftwow.exe[/COLOR]
so far, i get an error messeage "Blocked: wine start /unix comes up as wow.exe is not marked as executable... so i tried to run with Wine Core exe, there is no graphic card that supports the game...
when i try and run it through "playOnLinux" i [COLOR=Red]cant add D:/games/world of Warcraft/wow/exe[/COLOR]
is there a way to play world of warcraft???

...

If I'm getting this right you are trying to run a game installed in windows by trying to get wine to run the executable?
Someone correct me if I'm wrong, but I'm pretty sure that you need to actually install the game in wine to be able to run it with wine. Otherwise wine will not get all the registry settings and other things that it needs to run the game.

---

### Post by japer855 on 2011-06-12
> **jocko said:**
> If I'm getting this right you are trying to run a game installed in windows by trying to get wine to run the executable?
Someone correct me if I'm wrong, but I'm pretty sure that you need to actually install the game in wine to be able to run it with wine. Otherwise wine will not get all the registry settings and other things that it needs to run the game.

i was doing this way back in burning crusade days for wow
and worked fine...

also, how come im getting an error with "failed to find a suitable display devices"
i have installed the correct driver for Nvidia...

---

### Post by cwwilson721 on 2011-06-12
What used to work back in the BC DOESN'T ALWAYS WORK NOW in wine, because wine has progressed, and so has WoW.

Your #1 issue is trying to run a Windows *.exe file on a windows drive.

DON'T DO IT

[LIST]
[*]Running wine on a windows drive can not only bork wine ( I shudder to think what is actually hiding on Windows drives), but PERMISSION ISSUES are a royal pain to figure out
[*]Even if it DOES work, the extra processing needed to get info from a NTFS drive slows stuff down. Games + extra slow stuff = NO
[/LIST]

So, how to fix your issue?

Move the WoW directory on your "D:\" drive (my keyboard couldn't even TYPE that HORRIBLE idea...lol) into your ~/.wine/Program Files folder.

Really

It's that simple.

After that, READ THE WoW HOWTO. 

All of the answers for ALL of your issues are in there, already asked, already answered.

Many, many, many, many, many, many, many, many times

---

### Post by japer855 on 2011-06-12
> **cwwilson721 said:**
> What used to work back in the BC DOESN'T ALWAYS WORK NOW in wine, because wine has progressed, and so has WoW.

Your #1 issue is trying to run a Windows *.exe file on a windows drive.

DON'T DO IT

[LIST]
[*]Running wine on a windows drive can not only bork wine ( I shudder to think what is actually hiding on Windows drives), but PERMISSION ISSUES are a royal pain to figure out
[*]Even if it DOES work, the extra processing needed to get info from a NTFS drive slows stuff down. Games + extra slow stuff = NO
[/LIST]

So, how to fix your issue?

Move the WoW directory on your "D:\" drive (my keyboard couldn't even TYPE that HORRIBLE idea...lol) into your ~/.wine/Program Files folder.

Really

It's that simple.

After that, READ THE WoW HOWTO. 

All of the answers for ALL of your issues are in there, already asked, already answered.

Many, many, many, many, many, many, many, many times

just moved the whole folder across to the ubuntu HDD, just poped with another issue....  (bashing head into the keyboard KLJFkl;dfjgkl;dj;djsfg)

there is no graphic card that supports the game????  WTF

---

### Post by cwwilson721 on 2011-06-12
So you read the thread about running/installing WoW?

I guess I'll HAVE to do this AGAIN:
[LIST]
[*]Install wine 1.3. Google "wine ppa 1.3" if you can't figure out how. (OR READ THE STICKIES IN THIS FORUM)
[*]Run winecfg, install Gecko if it asks. Set mode to Windows XP (for sound to work right), and sound driver to ALSA only.
[*]Install your proprietary drivers from System > Administration > Additional Drivers. (If you don't, good luck on getting it to work. You're on your own then)
[*]Copy WoW to `/.wine/Program Files/World of Warcraft
[*]Create a launcher. Make the command read ```
env WINEPREFIX="/home/<USERNAME>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl 
``` Substitute <USERNAME> with your Ubuntu username.
[*]Run the launcher.
[/LIST]

That's it. If you do anything else, you're on your own. This is the SIMPILEST way to install/run WoW/wine with a Nvidia card. No "Play on Linux". No "registry tweaks". Nothing. THIS WILL WORK.

---

### Post by japer855 on 2011-06-30
> **cwwilson721 said:**
> So you read the thread about running/installing WoW?
 

I guess I'll HAVE to do this AGAIN:
[LIST]
[*]Install wine 1.3. Google "wine ppa 1.3" if you can't figure out how. (OR READ THE STICKIES IN THIS FORUM)
[*]Run winecfg, install Gecko if it asks. Set mode to Windows XP (for sound to work right), and sound driver to ALSA only.
[*]Install your proprietary drivers from System > Administration > Additional Drivers. (If you don't, good luck on getting it to work. You're on your own then)
[*]Copy WoW to `/.wine/Program Files/World of Warcraft
[*]Create a launcher. Make the command read ```
env WINEPREFIX="/home/<USERNAME>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl 
``` Substitute <USERNAME> with your Ubuntu username.
[*]Run the launcher.
[/LIST]
That's it. If you do anything else, you're on your own. This is the SIMPILEST way to install/run WoW/wine with a Nvidia card. No "Play on Linux". No "registry tweaks". Nothing. THIS WILL WORK.
 
 
aight, ill do that, didnt have the chance to get to the forum for while...
ill pm u if i have to XD

---

