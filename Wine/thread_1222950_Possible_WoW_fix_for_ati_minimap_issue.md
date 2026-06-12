---
title: "Possible WoW fix for ati minimap issue"
date: 2009-07-25
forum: Wine
---

### Post by DarkenSX on 2009-07-25
I need some people to test this but it should work.
The fix:
If  you have previously ran wow in opengl mode and set your video settings skip to step 5.

Step 1.: Open your WTF Folder in your wines world of warcraft directory and open Config.wtf in a text editor delete all the text and add:
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET ffxSpecial "0"

Step 2.: Save Config.wtf And Start WoW from The wow.exe in world of warcraft main directory. Note: do not run in windowed mode

Step 3.: After WoW starts and you accept EULA  "Click Options > Video" On that screen Set Resolution To "800x600" and uncheck V. Sync Box and Hardware cursor if checked Dont click Apply yet go to step 4. first.

Step 4. : in that same window click the word effects drag the top slider all the way to the left eg. Low Click Apply. Note: Your Game may flash the desktop 2 or more times this is normal. close all settings messages etc. in wow and exit wow.

Step 5. Final Step : Go back and edit config.wtf and change SET gxApi "opengl" to SET gxApi "d3d9"
save and enjoy wow. Note: Dont ever use the launcher.exe or change video settings both will mess up your settings.

---

### Post by DarkenSX on 2009-07-26
> **DarkenSX said:**
> I need some people to test this but it should work.
The fix:
If  you have previously ran wow in opengl mode and set your video settings skip to step 5.

Step 1.: Open your WTF Folder in your wines world of warcraft directory and open Config.wtf in a text editor delete all the text and add:
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET ffxSpecial "0"

Step 2.: Save Config.wtf And Start WoW from The wow.exe in world of warcraft main directory. Note: do not run in windowed mode

Step 3.: After WoW starts and you accept EULA  "Click Options > Video" On that screen Set Resolution To "800x600" and uncheck V. Sync Box and Hardware cursor if checked Dont click Apply yet go to step 4. first.

Step 4. : in that same window click the word effects drag the top slider all the way to the left eg. Low Click Apply. Note: Your Game may flash the desktop 2 or more times this is normal. close all settings messages etc. in wow and exit wow.

Step 5. Final Step : Go back and edit config.wtf and change SET gxApi "opengl" to SET gxApi "d3d9"
save and enjoy wow. Note: Dont ever use the launcher.exe or change video settings both will mess up your settings.

Just incase your wondering what happens if you use launcher or change video settings or if this even works heres the info:

Use launcher.exe: Will reset or modify your config.wtf file.

Change Video Settings in game in direct3d mode: Causes game to crash even with the apply to forehead addon must switch to opengl to change them.

Does this really work?: Yes it does i tested it and it works i get about 64 fps ingame compared to the 15 - 32 i get in windows though yours may vary if you get 1 - 10 or 10 - 22 fps in windows with lowest video settings without even moving in game you proberaly wont do much better in d3d on wine but like i said it varies from machine to machine best to meet these req. for decent play:

Ram: 2GB for 32-bit , 2GB or more for 64-bit
CPU: AMD or Intel 2.0Ghz or faster Single core or 2.0Ghz+ per core for Duel core for 32-bit , For 64-bit Faster than 2.0Ghz 
Video: Nvidia Or ATI Card With A minimum of 128MB Video Ram the more ram the better your game will perform.
Drivers: For ATI the official drivers are better than Open ones Nvidia is the same.

---

