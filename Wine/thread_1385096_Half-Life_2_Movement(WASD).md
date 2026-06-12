---
title: "Half-Life 2 Movement(WASD)"
date: 2010-01-19
forum: Wine
---

### Post by Andrew_Carr on 2010-01-19
Ok, so Half-Life 2 is working perfectly in Wine now(Ubuntu 9.10, Wine 1.01 iirc, Ati 5770, Phenom 920) except one thing...
 
   When I'm walking with the WASD keys it'll slow down until I can't even go forward. I can then move back or side to side, but that slows down too. So then I end up stuck in place. It's really weird. Another time I could alternate between moving forward and moving backwards. I could go forward, get progressively slower until I stopped moving, and then go back, and it'd seem to reset the W key so I could go forwards again. 

   Do you guys think this could be a keyboard issue or is it a common Wine issue?
    I just bought a generic keyboard that I haven't used before in gaming, but I kinda doubt that's it. Or could it be a Ubuntu setting that turns off key input after a certain time?




Unrelated Wine issue: I'm also trying to play the Insurgency Mod and Killing Floor for Steam. Insurgency loads fine and everything, but when I get in game the screen flickers a ton and there's two separate images that alternate being displayed. Sometimes my screen is also blurred and flipped upside down. As for Killing floor, it seems to work ok, but my mouse is restricted to a small box in the top left, so I can't click on most of the buttons. I haven't been able to join a game yet so I can't be sure if it'd just the menu that's messed up.

---

### Post by Andrew_Carr on 2010-01-19
Just played some more. It seemed fine, and then after I hit a save point it went all crazy again. So it seems it works ok until I reach a save point, after which I lost all keyboard input to the game. Downsizing and alt tabbing out gave me movement control, although that resulted in being stuck as described above.

   Killing Floor loads fine and plays fine. The only issue is you can only turn 45 degrees left and right with your mouse. So you can't really turn around or anything. Kinda unplayable because of that. Probably related to the issue with the mouse only working in 1/4 of the menu area.
  

    It seems adding the MouseWarpOverride string in 
HKEY_Current_User_User\Software\Wine\DirectInput
   of the registry and setting it to forced is supposed to fix the Killing Floor issue. Also, apparently setting your resolution to 1024x768 makes it small enough so that the mouse box is the same size and it's no longer an issue. 
(wineconsole --backend=user cmd   To go to registry in wine)

     Neither fixed the issue for me :/   Going down to 640x480 made it somewhat better(the box seemed to move around every now and then, so I could access different bits of the menu at different times, separately).

As this post explains([http://ubuntuforums.org/archive/index.php/t-1159780.html](http://ubuntuforums.org/archive/index.php/t-1159780.html)), it seems adding a dinput.dll.so file will fix the issue. Going to try that tomorrow after my games reinstall. Apparently uninstalling Steam in Wine = deleted games.

---

### Post by beastrace91 on 2010-01-19
Regarding your HL2 issue - I'd recommend installing the latest version of Wine (1.1.36 as of my writing this)

Regarding Killing Floor - yes you need to replace that input file as I described in the post you linked to,. Personally I would encourage anyone wanting to play UT engine games under Linux to spend the few bucks to get [Cedega](http://www.cedega.com/) - it runs UT engine games quite flawlessly.

~Jeff

---

### Post by Andrew_Carr on 2010-01-20
60$ for Cedega is pretty high.  I could just get Windows 7 instead, dual boot it, and it'd(hopefully) work better. 

   And apparently my brand new hard drive failed today as Steam was downloading my games(tip: Don't put hard drives in your checked baggage). So yeah, now I'm pretty sure I can fix the Killing Floor problem(but I thought I already had the latest version of wine, maybe not) but now I have bigger issues atm :(

[Edit:] Not sure if the hard drive failure was due to the drive or Ubuntu. My first Ubuntu install everything seemed fine. Then I reinstalled it(powering it down caused an issue with booting, so I just reinstalled) and the disk checker in Ubuntu said the drive had a lot of bad sectors. I checked the disk with fsck(I believe it was fsck, but anyway, another disk checker) and it reported that nothing was wrong, but who knows. Going to try reinstalling again. It's highly likely the TSA messed up the disk since my other bag was virtually destroyed. Oh well, now I know to budget a few hundred dollars extra for airfare, after I get done replacing all my lost/stolen/destroyed property.

---

### Post by beastrace91 on 2010-01-20
> **Andrew_Carr said:**
> Ok, so Half-Life 2 is working perfectly in Wine now(Ubuntu 9.10, Wine 1.01 iirc

Sorry - I was going off of this for your Wine version.

As for Cedega - its only 15$ for 3 months of updates (after which you get to keep using the software)... Where are you getting 60$ from? Personally I feel its worth my time not to have to reboot to play a game for a short while now and then.

~Jeff

---

### Post by Andrew_Carr on 2010-01-20
Ah, I must've looked up some bad info(didn't say any pricing on the site). Someone said it was 60$/year, and I just assumed that you'd have to keep paying to keep using it. 15$ isn't bad. 

   I'm pretty sure I was using Wine 1.01, but I also thought that was the most up to date version. I must've installed the wrong one or something.

---

### Post by beastrace91 on 2010-01-20
> **Andrew_Carr said:**
> I'm pretty sure I was using Wine 1.01, but I also thought that was the most up to date version.

Thats the latest "stable" version. The beta updates every month or so.

~Jeff

---

