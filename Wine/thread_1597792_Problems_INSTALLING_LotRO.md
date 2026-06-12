---
title: "Problems INSTALLING LotRO"
date: 2010-10-15
forum: Wine
---

### Post by burg1n on 2010-10-15
I just installed Ubuntu 10.10 on my laptop. 
I would like to install Lord of the Rings Online.
I downloaded the installer from the lotro website, then I tried opening it with wine (my wine version is "1.2.1-0ubuntu1 (wine1.2)"

When I open the installer I get a popup error that says:
Fatal Error In GC
GetThreadContext Failed

Then, when I hit "ok" for that error I get another error:
Wine Program Crash
Internal errors - invalid parameters received

I have looked at many guides online and have tried to follow them but they are all very old and for different versions of lotro,wine, and ubuntu. 

I am also new to Ubuntu, so be nice :P talk slow

(and I know that once lotro is installed I need to use a launcher like pylotro, but my lotro is not installed at all)

---

### Post by burg1n on 2010-10-15
OK I have fixed this problem and have installed LotRO successfully
hopefully this thread helps someone :P

1. The file you get from lotro.com is...kind of useless. When you run this file all it does is download another file that is used to download LotRO...I went to my gf's computer (running windows 7) and copied this file to my computer (mirkwoodsetup.exe) This successfully installed LotRO in the latest version of wine. Then I installed Pylotro, the lotro launcher for linux.

2. I thought I was ready to play the game but I ran into many more problems. At first when I logged into pylotro and clicked launch the game would start to launch but then my screen would turn very pixelated and all different shades of green and lotro would close, leaving my computer unusable because of the resolution and colors until I restarted completely. I tried several suggestions at once (ya ya bad idea) so I'm not sure which one fixed it exactly but I'm pretty sure what fixed the problem was installing direct x 9 through winetricks (./winetricks in terminal and selecting directx9 for fellow noobs) I also (after installing dx9) installed directx10 so I could use that with my game but I can't select it in the game options but that's ok with me

3. When I launched the game now it would start the LotRO loading screen but then say "You do not have the current version of the client installed" and would close. I tried clicking "patch" many times on Pylotro and it said it patched fine even though it did not. It also said there was a problem retrieving the news. This was because I was missing msvcr71.dll in wine (i'm using XP for wine btw) So I went to some dll download website and downloaded it, put it in system 32. Now it actually patches correctly!

I seemed to run into every problem possible during this installation :-( and all of this took a complete day to fix because of my lack of knowledge in linux/ubuntu.


Problems I'm still having:
Can not play in windowed mode
When I go to the options and select windowed mode it's...very hard to explain. It leaves a weird trail behind the game and I can't actually switch to other applications behind it (the game stays on top) Also, when I hold down my left mouse button to adjust the camera it acts like it's quickly moving my mouse to the right (spins my camera in circles very fast) even though my mouse is still, and I have to move my mouse very fast to the left to even have the camera still.

And when I am in full screen if I alt-tab to another application I can not get the game to come up again. I'd really like to find a fix to this, I have the habit of leaving the game run all the time which I can live without doing but I can not switch to a browser really quick to look up something game related or respond to the aim/msn IMs im getting or anything.

any suggestions?

---

### Post by CorsairTrumpet on 2010-10-21
First off your post has been very helpful in my endeavor to install and play lotro.  However i have come across a snag.  I installed the dll file in sys 32 and still I am not able to find any way to patch.  Perhaps I am just missing something, but I cannot find where to patch the file.  


Set Up:

Ubuntu 10.04 (updated with-in the last 24hours)
Asus G60JX

Thanks
CT

---

### Post by CorsairTrumpet on 2010-10-21
figured it out.  Just needed to redefine where the game files were located.  

Tools -> Settings Wizard -> Find Games
(Click top choice) Apply 

Tools-> patch -> start


Hope this helps someone...

---

