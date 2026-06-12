---
title: "Free Realms"
date: 2009-04-20
forum: Wine
---

### Post by Xergantheus on 2009-04-20
I know, I know. Why?  I enjoy playing it.  I am completely new to Linux but can grasp things quickly.  I understand wine can run certain applications better than others.  There is a new game still in beta called Free Realms that I have taken a liking to.  It requires you to login to the client side of the game via their website then the client downloads the game as you venture into new parts of it while you are playing.  Is there a fix for this to operate under linux.  I installed wine and what I think to be the unofficial Flash 10 for x64.  The website tells me that it doesn't see w**doze as my OS so I download User Agent Switcher and now it sees me as a windows user.  But it still doesn't recognize my flash 10.  


My questions are:  Would it be possible to run Firefox or another browser in Wine and login to Free Realms and have it install the neccessary files to my virtual C:.

If this is not even possible please forgive as well as any lack of proper terminolgy.

I am running the latest Jaunty and can switch to anything else that would help me get this working so long as your answer is not w**doze.

---

### Post by skompier on 2009-04-20
Since this is a new game using the latest that Windows has to offer, the simple answer would be just to dual boot.

---

### Post by NightMKoder on 2009-04-20
> **skompier said:**
> Since this is a new game using the latest that Windows has to offer, the simple answer would be just to dual boot.

That doesn't necessarily mean the game won't run. The game may be new but the functions it calls aren't - since it does work on windows.

Back to the topic: the game isn't in appdb, so I can't tell you it will work. You can install firefox/flash player in wine and try it. It's actually rather easy:

```

wget http://www.kegel.com/wine/winetricks
sh winetricks allfonts firefox3 flash

```

See how it works, and possibly add an appdb entry. If something is wrong, post a wine log.

---

### Post by mvidberg on 2009-05-01
I am interested in getting this game working in Linux as well.  Will try experimenting and post here with my results.

---

### Post by Sawta on 2009-05-04
I don't know about other users, but I was able to get as far as the server screen before I encountered an issue.

Basically, I followed the suggested steps and installed both Firefox and the newest flash player onto wine.  I was then able to create a character and view its stats and whatnot.

I can see the button "Play now!" listed in various areas of the site, but when I get to the select your server screen, "Waiting for download complete." area, I do not see the appropriate box appear in the upper left-hand corner.

I've included a screen shot for clarity.

I just wanted to note that I *have* been able to get this to play on my copy of Vista on the same laptop (dual partitions), so it has nothing to do with my hardware.

Would love to hear if anyone has a solution for this.

---

### Post by fromple on 2009-05-20
> **NightMKoder said:**
> That doesn't necessarily mean the game won't run. The game may be new but the functions it calls aren't - since it does work on windows.

Back to the topic: the game isn't in appdb, so I can't tell you it will work. You can install firefox/flash player in wine and try it. It's actually rather easy:

```

wget http://www.kegel.com/wine/winetricks
sh winetricks allfonts firefox3 flash

```See how it works, and possibly add an appdb entry. If something is wrong, post a wine log.

I tried to use this to get FreeRealms to run. Sadly, it not only didn't work, it seems it might have broken WoW. :(

I am totally new to Ubuntu (I'm using 9.04 Jaunty), but....I had WoW running FLAWLESSLY (I was amazed) using Wine. Then after the Blizzard update this past Tuesday....it just stopped.  The game won't open.  It will open the launcher, but if I click on "options" at the bottom...it gives me nothing but a white space in the launcher, and if I hit "play" it says:

[B]Program Error
The program WoW.exe has encountered a serious problem and needs to close. We are sorry for the inconvienience. This can be caused by a problem in the program or a deficiency in Wine.[/B] 

Then it says to go to appdb.winehq.org, which of course tells me nothing of use. I read through all the comments and couldn't find anyone having this problem.

I got this problem after using the "winetricks" fix above, AND the patch, so I'm not sure which is responsible for it.

How do I UNDO the "fix" called winetricks that you posted, just in case that is the problem? 

Please go easy on me, I'm totally just learning here and thank you for your help. :) If you tell me how to post a Wine log....I will.

---

### Post by NightMKoder on 2009-05-21
> **Sawta said:**
> I don't know about other users, but I was able to get as far as the server screen before I encountered an issue.

Basically, I followed the suggested steps and installed both Firefox and the newest flash player onto wine.  I was then able to create a character and view its stats and whatnot.

I can see the button "Play now!" listed in various areas of the site, but when I get to the select your server screen, "Waiting for download complete." area, I do not see the appropriate box appear in the upper left-hand corner.

I've included a screen shot for clarity.

I just wanted to note that I *have* been able to get this to play on my copy of Vista on the same laptop (dual partitions), so it has nothing to do with my hardware.

Would love to hear if anyone has a solution for this.

There's an appdb entry for free realms now: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=16470](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16470) . But there is a bug that prevents it from downloading the client. There is a fix, but you need to download the wine source and compile it. I haven't tried playing since all the servers are down for some reason (tried too much?)

> **fromple said:**
> I tried to use this to get FreeRealms to run. Sadly, it not only didn't work, it seems it might have broken WoW. :(

I am totally new to Ubuntu (I'm using 9.04 Jaunty), but....I had WoW running FLAWLESSLY (I was amazed) using Wine. Then after the Blizzard update this past Tuesday....it just stopped.  The game won't open.  It will open the launcher, but if I click on "options" at the bottom...it gives me nothing but a white space in the launcher, and if I hit "play" it says:

[B]Program Error
The program WoW.exe has encountered a serious problem and needs to close. We are sorry for the inconvienience. This can be caused by a problem in the program or a deficiency in Wine.[/B] 

Then it says to go to appdb.winehq.org, which of course tells me nothing of use. I read through all the comments and couldn't find anyone having this problem.

I got this problem after using the "winetricks" fix above, AND the patch, so I'm not sure which is responsible for it.

How do I UNDO the "fix" called winetricks that you posted, just in case that is the problem? 

Please go easy on me, I'm totally just learning here and thank you for your help. :) If you tell me how to post a Wine log....I will.

There is no way to undo winetricks, but there is a chance that you're not using opengl for WoW. Look on appdb how to run WoW, since those winetricks shouldn't really mess with anything.

---

### Post by Duskao on 2009-05-21
When installing new games and such, it is generally a good idea to use a new prefix so that exact thing doesn't happen. I have had winetricks mess up a bunch of games for me as well. An easy way to do this is to try playonlinux. might like it, might hate it, but you can give it a try. I actually don't use many of their official scripts that come with it, I mostly use it cause it's an easy way to have a new prefix for each game, then even if one goes wonky you don't need to worry about the others being messed up as well. Its kinda like a safety blanket. 

P.S. their forums suck, and half of them seem to have something shoved up their butts so your better off asking questions here or on winehq.

Oh yeah, one more thing. If you do try POL, I would recommend the advancedwineconfiguration plugin for it. It really makes it easy to customize the registry for each game. (all the Direct3D stuff)

---

### Post by fromple on 2009-05-22
Well, I am running WoW using open gl, so that's not it. Either it was winetricks OR....it was Blizzard's patch on Tuesday, because I still can't get it to run.

Oh well. Guess it's time to cancel THAT sub. I was really loving Linux, but I have a feeling that screwing with every single thing on your machine *every* time anyone updates *anything* is going to really get on my nerves.

Thanks for trying to help guys.

Next time someone posts a "fix" that can't be UNdone...it would probably be good to say so, just in CASE it has the potential for messing something up that a newbie can't fix. :) But there's a good chance this could all be a Blizzard thing too.

---

### Post by NightMKoder on 2009-05-22
> **fromple said:**
> Well, I am running WoW using open gl, so that's not it. Either it was winetricks OR....it was Blizzard's patch on Tuesday, because I still can't get it to run.

Oh well. Guess it's time to cancel THAT sub. I was really loving Linux, but I have a feeling that screwing with every single thing on your machine *every* time anyone updates *anything* is going to really get on my nerves.

Thanks for trying to help guys.

Next time someone posts a "fix" that can't be UNdone...it would probably be good to say so, just in CASE it has the potential for messing something up that a newbie can't fix. :) But there's a good chance this could all be a Blizzard thing too.

Suit yourself, I just remember reading somewhere that the latest patch kills the "-opengl" option when launching, so you have to enable opengl in the config file. Thankfully with wine, you can remove your entire prefix and then just start over.

What Duskao is referring to is called bottling, and it is very useful. If you don't like living on the wild side, then bottling your WoW install would fix all possible bugs relating to multiple software install.

Also, for the record, the above winetricks involve installing a bunch of fonts, firefox, and flash player. It's not anything that should be deadly to wine, so I would suspect the patch to be the culprit.

---

### Post by fromple on 2009-05-22
> **NightMKoder said:**
> Suit yourself, I just remember reading somewhere that the latest patch kills the "-opengl" option when launching, so you have to enable opengl in the config file. Thankfully with wine, you can remove your entire prefix and then just start over.

What Duskao is referring to is called bottling, and it is very useful. If you don't like living on the wild side, then bottling your WoW install would fix all possible bugs relating to multiple software install.

Also, for the record, the above winetricks involve installing a bunch of fonts, firefox, and flash player. It's not anything that should be deadly to wine, so I would suspect the patch to be the culprit.

I had already fixed the Blizzard dis to open gl.  And yes, I too think it's the patch.  On the other hand....is anyone ELSE not able to run it, or just me?  If it's just ME...then I have done something wrong.

---

### Post by NightMKoder on 2009-05-24
On another note, I got free realms to at least start (follow the two bugs in the appdb entry). I don't know to what extent it works, since my choice of video cards is either gma945 or ati r350. On gma945 it doesn't load and crashes in mesa, and my ati r350 has gotten to some trees a cursor and a person, but I could not test gameplay (pentium 4 is too old). Here is my setup:

Compile wine with ret = TRUE in dlls/crypt32/chain.c:1877 .
Do winetricks firefox3 flash d3dx9
Make sure ip blockers are off (this on got me for a while)
wine regedit (only do if starting doesn't work for you):
```

   HKCU\Software\Wine\Direct3D:
      OffscreenRenderingMode=fbo (not sure if this matters)
      UseGLSL=disabled (fixed a ton of opengl errors)
```
Use wine's firefox to go to the free realms site. Install the plugin, and the game should start. Seems like there is a problem with the cursor though (not exactly transparent).

Hope this helps someone!

---

### Post by NightMKoder on 2009-05-24
Sorry for the double post, but I found a way to make free realms loading screen work perfectly on intel hardware (and maybe others).

You need to turn on s3tc texture decompression support. The way you do this for intel drivers (and maybe others) is start driconf and in expert mode, go to image quality and make "force s3tc software compression even if software support is not available" "yes". This is *slightly* a hack, and for a full fix see:
[http://homepage.hispeed.ch/~rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/~rscheidegger/dri_experimental/s3tc_index.html)
where you will be told to run and compile the actual s3tc compression support (which you dont need, you just need decompression as above in driconf).

Now it crashes in mesa...great.

---

### Post by NexusZA on 2009-10-13
I have some good news for Free Realms. As of Wine 1.1.30 it runs really well. If you go to the Wine App DB page (for which I am the maintainer) there is a very easy how to to get it working flawlessly.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9620](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9620)

---

### Post by xtracool_protik on 2010-03-17
Hey Nexus I was going through ur method however at the point when I try to install flash player, it gives me an error saying "Operating System Error!" followed by some numbers. Can u please look into it?
My wine version is 1.1.40 and I'm using intel X3100 graphics card(onboard) with Ubuntu 9.10

Thanks

---

### Post by peacewithall on 2010-03-18
Freerealms works almost perfectly now with the last couple of WINE releases.

xtracool, all I do to get flash installed, after installing firefox in WINE, I visit this page (with WINE's firefox),

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

once there I click the install plugin box, and follow the rest of the instructions within the box in firefox that pops up. Within seconds flash installs and the page will refresh with a working demonstration on that page.

Once freerealms installs you might notice that it performs bad, thats the case with me anyway, so turning down the 'graphics quality' one step above zero does the trick once freerealms is restarted, although at this low setting water don't seem to render for me, but as I like racing I dont see much water :D.

---

### Post by xtracool_protik on 2010-03-19
That did a trick thanks peacewithall
For Nexus's way it gave me error for some reason
However now it stuck at downloading lets see if it goes through

---

### Post by xtracool_protik on 2010-03-19
Sorry guys that was my fault I had set my windows to windows 2000 It seems to be working when i changed it back to Windows XP

---

### Post by ericsonlouis on 2012-08-24
I am having problems downloading flashplayer with wine they tell me :

 invalid parameters

---

