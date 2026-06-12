---
title: "World of Warcraft  walking stutter/audio trouble/hardware cursor"
date: 2010-02-20
forum: Wine
---

### Post by lacktorium on 2010-02-20
After searching the forums and web for days I've finally been able to get my WoW wotlk working on ubuntu 9.10 x86_64:KS. My audio, Graphics and Hardware cursor problems have been solved. for the most part, the cursor with the hardware patch dosent work quite as well as the D3d enabled one.

So to help those who mite have the same issues i did Here is what i did to save you the headache. I've pulled a lot of different things that other people have done and updated them, i cant find where i pulled them all from now but there in the forums if your inclined to look. If you recognize some thing you put out there please let me know so i can add a link in to your post.

Starting off with i am not a complete noob nor am i any where close to an expert if you find something wrong please post it so myself and others have the benefit by learning from you.

first off my specs.
Ubuntu 9.10 x86_64
AMD Phenom II X4 955 Black Edition Deneb 3.2GHz
3GB ram
integrated Ati radeon HD 3300

Graphics driver almost every tutorial I've seen on troubleshooting wow has upgrading your graphics in there some where. main point being you need to have direct rendering capability.
i have an ati graphics card so im pretty well in the whole as far that goes but there getting better. began by upgraded to the newest driver from ati using this great tutorial [http://help.ubuntu.com/com.....]("http://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Even if you don't have ati graphics, upgrading what u have is good place to start with.

Next i upgraded my kernel. NOT Recommended for every one. However if you do feel the need to do so and not wait until April's release of 10.04 which should have 2.6.33. so I've heard any way. You can follow the tutorial at [http://www.ramoonus.nl/2009... ]("http://www.ramoonus.nl/2009/12/03/linux-kernal-2-6-32-installation-guid-for-ubuntu-linux/"). Just be sure to change the download links to the current stable which i believe is 2.6.32.8

Now for wine. download the latest source wine1.1.39(which is wine1.2) from [WineHQ ]("http://winehq.org"). Extract from tar ball then navigate to it in terminal. ```
cd /path/to/wine-1.1.39
```
[SIZE="1"]*Change /path/to to the directory location i.e. home/<username>/ *[/SIZE]

Then download Doctor Debian awesome cursor patch. Thank you so much we all love you for it. It can be found here along with his tutorial here [http://ubuntuforums.org/....]("http://ubuntuforums.org/showthread.php?p=7643957#post7643957")

now to apply the patch. *need to be in the wine directory in terminal i.e. /home/<username>/wine1.1.39*
```
patch -p1 < path/to/wine-cursor-patch-new.txt
```
[SIZE="1"]*Change /path/to to the directory location i.e. home/<username>/ *[/SIZE]

Now a slight variation to Doctor Debian tutorial 
Enter in terminal ```
./configure
``` 
Now this could take some time. 
Once done you will now have the debian file and are able to edit the changelog file as per Dr. Debian's tutorial.

Next step is to make the package i did this by 
```
 make depend && make
``` Then installed by ```
 ./tools/wineinstall
``` but i don't see any reason why Doctor Debian's method for this wouldn't still work. However i did not to download the gauntlet patch.

next set once wine is installed is to configure it. ```
winecfg
``` may get a pop-up to install some software needed for wine work, go ahead and install it. make sure the audio has ALSA checked and add wow.exe to the applications list be sure to check windows version as XP.
 
now to add a Reg tweak a Great tutorial by Sammi can help you do that [http://ubuntuforums.org/.... ]("http://ubuntuforums.org/showthread.php?t=579378") and finaly editing your WoW wtf/Config.wtf file, sammi's tutorial can also help you hear. and here is what i added to mine 
```

SET UIFaster "2"
SET ffxDeath "0"
SET ffxGlow "0"
SET OffscreenRenderingMode "fbo"
SET shadowLevel "0"
SET M2UseShader "0"

```

Edit: Forgot to mention open wow.exe with -opengl  and env WINE_CURSOR=anything;

so it should look like *env WINE_CURSOR=anything; wine "/path/to/wow/WorldofWarcraft/Wow.exe" -opengl*

I hope this helps you. If not don't be afraid to post.:popcorn:

---

### Post by lacktorium on 2010-02-20
update: compiz will break this. there has been some work to disable and re-enable on exit for those who want it like myself. can be checked out here [http://ubuntuforums.org/...]("http://ubuntuforums.org/showthread.php?t=1119615")

Update: starting wow with rhythmbox playing will break sound. option so far is to start wow then start your music.

---

### Post by BetaguyGZT on 2010-02-20
WoW has always worked fine for me using d3d mode.. no tweakage necessary here.

Only complaint I have is when I log off or exit the game, it hangs for about 3 minutes then finally closes.

Thanks for the tips though.. I'm sure they'll help *someone* out. :popcorn:

---

### Post by Alethenorio on 2010-02-20
Ever since I installed Karmic (9.10) I have had sound stuttering problems in WOW which did not happen on 9.04.

I am using the official repository version (Believe it is 1.1.31). You seem to have had the same problem, how did you get it fixed it if at all?

Also sometimes I get no sound at all but that's mostly when I have spotify up and running I believe (Not always though)

I am currenlty compiling this version with the hardware fix but don't expect it to have any impact in the sound so any tips on how one can get that issue fixed would be appreciated.

---

### Post by lacktorium on 2010-02-20
original i had the same problem no sound or glitchy sound with wine1.1.32 i believe then i found it had something to do with not being able to handle multiple audio channels and there was a patch for wine1.1.3*+pulse audio patch. 
which you can download and add yourself or install for reps. it worked but had trouble with the wine vesions working with my graphics so i tried installing on 1.1.38 but the patch driver wouldnt work. so last night when wine1.1.29 was release i tried it with it while i was installing the hw patchsame issue. happily however my audio is now working with the new wine under ALSA driver

---

### Post by Alethenorio on 2010-02-20
So I guess you're saying you compiled the latest version and it is working fine?

I have now compiled the hardware cursor patch using the instructions by Doctor Debian however I am uncertain how I am able to test whether it is working or not. The mouse still freezes in the loading screen so something tells me it is not working

Thanks for the reply.

Regards
Alex

---

### Post by lacktorium on 2010-02-20
yes, kinda get long winded. what are your comp spec maybe someone can help you out

Edit: since ive been messing around with my windows manager, ive noticed that disabling the cursor patch may work better for some than with it. just simply don't add env WINE_CURSOR=anything; to the line

like to point out that disapling compiz and using metacity can also make a difference

---

### Post by lacktorium on 2010-02-20
> **BetaguyGZT said:**
> WoW has always worked fine for me using d3d mode.. no tweakage necessary here.

Only complaint I have is when I log off or exit the game, it hangs for about 3 minutes then finally closes.

Thanks for the tips though.. I'm sure they'll help *someone* out. :popcorn:

thats cool, could i ask for your comp specs

---

