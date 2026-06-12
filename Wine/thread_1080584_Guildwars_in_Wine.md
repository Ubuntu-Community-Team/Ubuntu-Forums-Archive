---
title: "Guildwars in Wine"
date: 2009-02-25
forum: Wine
---

### Post by Sojurner on 2009-02-25
I may be posting in the wrong forum so if so please forgive me. I feel this is a wine related question tho. I have guildwars installed and running under wine in ubuntu 8.10. However since GW uses direct x and obviously there is no support for directx in GW or Wine (to the best of my knowledge) it is somewhat laggy and choppy. How can i overcome this issue and make the game run alot more smooth.  This is one of my favorite games and it sux not being able to play it like i used to under regular windows XP.

ps: i am not interested in dual booting windows xp if at all possible so please do suggest that. I have already thought of it and wish to stay away from that option if at all possible. 

Thanx in advance.

---

### Post by MasterNetra on 2009-02-25
How much ram do you have?

---

### Post by Sojurner on 2009-02-25
i have 2gig of system ram and 640mb on my video card (8800gts). Im also running an AMD 6000+ cpu.

---

### Post by Toffeeapple on 2009-02-25
I don't know if this will help, but!

In the Graphics tab in wine configuration set 'Emulate a virtual desktop' to what ever you desktop resolution is, mine is 1440x900 but there you go.. and unchecked 'Allow DirecXapps.....' 'Allow the window manager to decorate....' and 'Allow the window manager to control...'

with the above I generally get good playable frame rates, around 60, does drop to 30 odd in highly populated cities though (not that I see many of those these days, not like the good old days anyway.. sniff..) and that's with everything set to max in game on the system you see in my sig.....

edit..

(Just in case... to get to wine configuration.. in a terminal type 'winecfg')

---

### Post by Sugi on 2009-02-25
You got the right section of the threads. :D  No one here should say try dual boxing to solve a game's issues *BUT there are a few games that just won't work in Linux* With that being said, Guild War works flawlessly in Wine.

Notes from APPDB:
Try running Guild Wars from the terminal with wine debug:
$ cd ~/.wine/drive_c/Program\ Files\Guild\ Wars/
$ WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe"

(Note: Make sure the location of wine is correct.)

Troubleshooting:

 - Make sure 3D works in native applications before blaming Wine. 
Terminal: $ glxgears 
 - Use the latest version of Wine, at least 1.0. (Current working version of Wine 1.1.15)
 - Try different versions of Windows in winecfg, such as Windows XP and 98.
Terminal: $ winecfg 
Click on Add and find your Gw.exe file
Then chnge the OS to either Windows XP or Windows 98
 - Turn off Compiz Fusion desktop effects. 
(This usually fixes a lot issues with games running within WINE)


If you are having graphics issues, use regedit to try some registry keys:
Terminal:
$ wine regedit
HKEY_CURRENT_USER/Software/Wine/AppDefaults/Gw.exe/Direct3D/
Add the following:
UseGLSL=disabled
DirectDrawRenderer=opengl
OffscreenRenderingMode=pbuffer or fbo
RenderTargetLockMode=auto

(NOTE:   If you do not see Gw.exe within your AppDefault, you can make one or use winecfg to config one for you:
Terminal: 
$ winecfg
Add > find Gw.exe
Click OK and go back to your regedit *$ wine regedit* and look within the AppDefault, it should be there now.)


These flags may help you run Guild Wars better:

-dx8  *Uses DirectX 8*
-dsound  *Uses DirectSound*
-nosound  *Disables sound*

Example:  
wine Gw.exe -dx8 -dsound
wine Gw.exe -nosound

If you need anymore help just let me know.

PS:  I have never ran Guild wars before, but I have used wine for a long time.  I am using the notes off of APPDB.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Cheers,
Sugi

---

### Post by Sojurner on 2009-02-25
now when u say flawlessly. do u mean all the graphics look right (because they already do) or do u mean with no graphics lag (ie plays just like it does in windows.) because the 2nd is not true so far. It looks very good just like it does in windows however i am getting lag issues. like to say that my card isnt rendering fast enough . so i am getting low fps in gameplay and towns.

EDIT: I will try the rest of that. i have tried some of it but u have more info than i had found on wine apdb. Thanx for the help and if i need more ill let u know. will try tonight when i get home.

---

