---
title: "Guild Wars problem"
date: 2009-05-25
forum: Wine
---

### Post by gunboat on 2009-05-25
I have installed Wine, then Guild Wars and the install seemed to go just fine. But when I try to start Guild Wars I get the small box that starts the game on the screen and it begins to download stuff from ArenaNet, and then crashes and goes away around the time it downloads 60-90 kb. I have nvidia drivers installed (driver number 173.14.16) and I am using Jaunty. Any ideas? Thanks.

---

### Post by wubiubiubi on 2009-05-25
there are several things that can go wrong. first of all, did you install guild wars from the disk or from the client download on the website? you can, technically, use the disk, but doing it from the download works more often. I don't know why, it just does. Also, try configuring wine to work in windows 2000 mode. On some computers GW doesn't work well or at all under windows XP or vista on wine. Also, if you don't have the correct system requirements to run Guild Wars, then sometimes it'll just show the splash screen, start up, and then shut down. Try also installing the latest version of Wine instead of using the "stable" version in the repositories. I can personally vouch that the latest version works better, faster, and it looks more native than using the old wine client

---

### Post by gunboat on 2009-05-25
> **wubiubiubi said:**
> there are several things that can go wrong. first of all, did you install guild wars from the disk or from the client download on the website? you can, technically, use the disk, but doing it from the download works more often. I don't know why, it just does. Also, try configuring wine to work in windows 2000 mode. On some computers GW doesn't work well or at all under windows XP or vista on wine. Also, if you don't have the correct system requirements to run Guild Wars, then sometimes it'll just show the splash screen, start up, and then shut down. Try also installing the latest version of Wine instead of using the "stable" version in the repositories. I can personally vouch that the latest version works better, faster, and it looks more native than using the old wine client

I did the steps from the guild wars on wine page on the guild wars wiki ([http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine#Running_Guild_Wars](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine#Running_Guild_Wars)). I installed the most recent wine I think, the version is 1.1.22. Not sure how to configure wine to work in windows 2000 mode, will look into that. thanks for the tips.

EDIT - uninstalled GW, downloaded the GwSetup.exe file, set Wine to emulate windows2000, and tried to reinstall - but the setup crashes during the install.

---

### Post by wubiubiubi on 2009-05-25
> **gunboat said:**
> I did the steps from the guild wars on wine page on the guild wars wiki ([http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine#Running_Guild_Wars](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine#Running_Guild_Wars)). I installed the most recent wine I think, the version is 1.1.22. Not sure how to configure wine to work in windows 2000 mode, will look into that. thanks for the tips.

k all you gotta do is go to applications->wine->Configure Wine. there should be a drop-down menu under the big white area showing Windows Version: and then your current version. change that to windows 2000.
you should note, however, that this may cause a couple problems when you run guild wars. running in windows 2000 can cause clipping, especially with the wintery graphics associated with eye of the north. this can be fixed by manually installing directx 9. this is easiest done using winetricks or these directions: [http://wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)

---

### Post by wubiubiubi on 2009-05-25
alright... try doing this. run guild wars from the terminal. run
```
Wine "C:\\Program Files\Guild Wars\Gw.exe"
```

When it crashes, it should return an error. post the output here and i'll take a look at it.
also, try running in win98 mode.

---

### Post by gunboat on 2009-05-25
> **wubiubiubi said:**
> alright... try doing this. run guild wars from the terminal. run
```
Wine "C:\\Program Files\Guild Wars\Gw.exe"
```When it crashes, it should return an error. post the output here and i'll take a look at it.
also, try running in win98 mode.


will try (and thanks for being willing to help) but I am now having problems installing, but will give it a go

edit - trying installing , just would not work. terminal ended with this message:


err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

---

### Post by wubiubiubi on 2009-05-25
try cleaning out everything to do with guild wars. browse the C drive and look in program files. if there's still a folder with the guild wars name, delete it. 
by the way, you said that the setup program crashes when you run it. at what point does it crash? on the first bit, when you're choosing the directory for install? or past that?

also, instead of following the directions on the wiki, try doing a manual setup. delete the setup file you have, and the zip file it came from. go to guildwars.com and download the client directly from there. just search for download client, then click the download. it will put a raw GWsetup.exe on your desktop instead of giving you a zip file. run it using wine.

---

### Post by gunboat on 2009-05-26
> **wubiubiubi said:**
> try cleaning out everything to do with guild wars. browse the C drive and look in program files. if there's still a folder with the guild wars name, delete it. 
by the way, you said that the setup program crashes when you run it. at what point does it crash? on the first bit, when you're choosing the directory for install? or past that?

also, instead of following the directions on the wiki, try doing a manual setup. delete the setup file you have, and the zip file it came from. go to guildwars.com and download the client directly from there. just search for download client, then click the download. it will put a raw GWsetup.exe on your desktop instead of giving you a zip file. run it using wine.

I will try that tomorrow night. (eastern time zone) Thanks for the help.

---

### Post by betrunkenaffe on 2009-05-26
I have this exact same issue, it started with wine 1.1.21, -dx8 doesn't solve. Changing drivers hasn't solved, disabling compiz hasn't solved. I tried reinstalling Guild Wars (full uninstall, deletion of directory, etc) and it continuously restarts the downloading of information from Arenanet.

It worked perfectly fine in 1.1.20 so this is definitely something that wine changed.

---

### Post by gunboat on 2009-05-26
> **betrunkenaffe said:**
> I have this exact same issue, it started with wine 1.1.21, -dx8 doesn't solve. Changing drivers hasn't solved, disabling compiz hasn't solved. I tried reinstalling Guild Wars (full uninstall, deletion of directory, etc) and it continuously restarts the downloading of information from Arenanet.
 
It worked perfectly fine in 1.1.20 so this is definitely something that wine changed.
 
Did you uninstall wine and then re-install 1.1.20?

---

### Post by wubiubiubi on 2009-05-26
> **betrunkenaffe said:**
> I have this exact same issue, it started with wine 1.1.21, -dx8 doesn't solve. Changing drivers hasn't solved, disabling compiz hasn't solved. I tried reinstalling Guild Wars (full uninstall, deletion of directory, etc) and it continuously restarts the downloading of information from Arenanet.

It worked perfectly fine in 1.1.20 so this is definitely something that wine changed.


The wine version shouldn't have anything to do with it. the OP said he has 1.1.22, and his is not working. I have 1.1.22, and mine is working. there has to be a factor outside wine.

---

### Post by betrunkenaffe on 2009-05-26
Yes, I uninstalled wine and reinstall 1.1.20 and it worked perfectly fine.

Do you have Jaunty and nVidia?

---

### Post by gunboat on 2009-05-26
> **betrunkenaffe said:**
> Yes, I uninstalled wine and reinstall 1.1.20 and it worked perfectly fine.

Do you have Jaunty and nVidia?

yes to both. using the nvidia driver 173 instead of 180 as the 180 driver really messed up the display.

---

### Post by wubiubiubi on 2009-05-26
I don't think the graphics driver/card is the problem, because it's crashing before it even gets to the game.

Try this command:

```
wine "C:\\Program Files\Guild Wars\Gw.exe" -image
```

That command instructs guild wars to install all known updates and all known areas (instances) in the game. it takes an incredibly long time to install, and i'm not suggesting that you do it (you can if you want, it significantly reduces load times later) but the whole point is to see if it crashes or not. Even though this is only any argument, it fundamentally alters the way the program runs. If this works, but the actual game doesn't, then it's the program. If it doesn't, then it can still be the program, or it could be a multitude of other things.

---

### Post by gunboat on 2009-05-27
> **wubiubiubi said:**
> I don't think the graphics driver/card is the problem, because it's crashing before it even gets to the game.

Try this command:

```
wine "C:\\Program Files\Guild Wars\Gw.exe" -image
```That command instructs guild wars to install all known updates and all known areas (instances) in the game. it takes an incredibly long time to install, and i'm not suggesting that you do it (you can if you want, it significantly reduces load times later) but the whole point is to see if it crashes or not. Even though this is only any argument, it fundamentally alters the way the program runs. If this works, but the actual game doesn't, then it's the program. If it doesn't, then it can still be the program, or it could be a multitude of other things.

I am trying your suggestion, and it is taking a long time - it keeps saying "connecting to arenanet" and then going back to DL. It is at 82 mb now and still going. Will update here if it finishes or breaks. thanks.

EDIT - I left it running overnight, when I looked at it this morning the box was still up with a "connecting to arenanet" message, but no activity (no downloading going on) So I closed the box and the terminal and then tried to launch Guild Wars, the box popped up, connected to arenanet and then crashed.

---

### Post by betrunkenaffe on 2009-05-27
Tried that as well, it appears that I get no error message output but it restarts the connection. By that I mean it starts downloading and then every so often gives the connecting to arenanet message and restarts the download.

Are you using Wireless to connect? Maybe it's a connection issue.

I wish I knew what that seg fault meant.

---

### Post by wubiubiubi on 2009-05-27
Very weird happenings going on. I looked on WineHQ and someone is having a very similar problem. He says he got the installer to run alright by removing wine, then removing the winehq repositories from his sources found in "etc/apt/sources.list.d/.list" and then reinstalling the stable version of wine found in the ubuntu repositories. If you can get it to run under the stable version, then there's some compatibility error going on between the current version of wine and your computer. If it doesn't work, I'll keep thinking about it, but this is kind of the last thing I've thought of. Best of luck.

---

### Post by gunboat on 2009-05-27
> **wubiubiubi said:**
> Very weird happenings going on. I looked on WineHQ and someone is having a very similar problem. He says he got the installer to run alright by removing wine, then removing the winehq repositories from his sources found in "etc/apt/sources.list.d/.list" and then reinstalling the stable version of wine found in the ubuntu repositories. If you can get it to run under the stable version, then there's some compatibility error going on between the current version of wine and your computer. If it doesn't work, I'll keep thinking about it, but this is kind of the last thing I've thought of. Best of luck.
 
any advice on how to remove Wine so as to make sure everything is cleaned out? Also, where are the Ubuntu repositories you are speaking of? (sorry for such a simple question)

---

### Post by wubiubiubi on 2009-05-27
> **gunboat said:**
> any advice on how to remove Wine so as to make sure everything is cleaned out? Also, where are the Ubuntu repositories you are speaking of? (sorry for such a simple question)
```
sudo apt-get purge wine
sudo apt-get autoremove
sudo rm -r ~/.wine
```
I'm fairly certain that should remove wine and then delete all the wine files. This may leave a dead link under applications that you can remove later.
Then, run ```
sudo apt-get install wine
```
and that should give you the 1.0.1 version of wine.

---

### Post by betrunkenaffe on 2009-05-27
Anyone here using 64bit?

---

### Post by gunboat on 2009-05-27
> **wubiubiubi said:**
> This may leave a dead link under applications that you can remove later.

How do you do this? I needed to remove the dead link to guild wars after I uninstalled it, but under the wine submenu it was still there. (can you tell I am new to making linux my desktop?)

> **betrunkenaffe said:**
> Anyone here using 64bit?

Yes, my install of wine is 64 bit (it told me the i86 was the wrong match)

---

### Post by wubiubiubi on 2009-05-27
> **gunboat said:**
> How do you do this? I needed to remove the dead link to guild wars after I uninstalled it, but under the wine submenu it was still there. (can you tell I am new to making linux my desktop?)



Yes, my install of wine is 64 bit (it told me the i86 was the wrong match)

Yeah that's a known problem with many Wine applications. After uninstalling, their links remain under wine programs, unrunnable. In order to delete the dead links, go to system->preferences->main menu. go down to wine, and click the arrow next to it. this will expand it. expand then the programs folder. go into the guild wars file, and highlight and check the box next to, or delete, the guild wars icon. this will get rid of it, and make the guild wars file under wine not show up anymore. note that the file will still be there, and you can activate it later, but you won't see it, and that's pretty much the whole point.

---

### Post by betrunkenaffe on 2009-05-27
I highly recommend not deleting anything from your menu, just uncheck it so it isn't visible. Once you've deleted it, you would have to manually add it back in if you reinstall which is more annoying then it is worth.

Wubi: Are you using 32bit? That may be a lead towards the problem. Interestingly when I first opened GW after the upgrade to 22, it said the GW file was corrupt and started "rebuilding" it. Downgrading to 20 had it working (currently running 1.1.20 for compatibility)

---

### Post by gunboat on 2009-05-27
> **wubiubiubi said:**
>   that should give you the 1.0.1 version of wine.

it got me the 1.1.22 version of wine

---

### Post by betrunkenaffe on 2009-05-27
Use this link and try 1.1.20 amd64

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by gunboat on 2009-05-28
Okay, for what it is worth I want to report what the results are for me. I followed the advice to purge wine from the system. Then I installed 1.1.20. then I downloaded the guild wars client from the guild wars website. then I installed. And now it seems to work, but only in a virtual window, not full screen. I created a character and then when I started the game it showed me the load screen for Ascalon city and started downloading over 130mb. Not sure what that is about. Got in the game, a little laggy I think, but it works. Thanks for all the help fellows. I will report back as I play more.

---

### Post by wubiubiubi on 2009-05-28
> **gunboat said:**
> Okay, for what it is worth I want to report what the results are for me. I followed the advice to purge wine from the system. Then I installed 1.1.20. then I downloaded the guild wars client from the guild wars website. then I installed. And now it seems to work, but only in a virtual window, not full screen. I created a character and then when I started the game it showed me the load screen for Ascalon city and started downloading over 130mb. Not sure what that is about. Got in the game, a little laggy I think, but it works. Thanks for all the help fellows. I will report back as I play more.
That's great! to go to full screen, you can't just click the maximize button in the upper-right like on windows. when you get into the game, hit f11, then go to graphics. there should be a fullscreen button. click it. it will change to fullscreen. the game will remember that and should go to fullscreen when you open the program again. by the way, what's your gw name? If you're new to guild wars (i only say this because you said you're in ascalon city, don't be offended if you're not) I can help you with stuff. By the way, the reason it downloaded over 130mb is because whenever you "zone" into a new instance, it will need to download the data to the gw.dat file. the second time you "zone" or log in to the area, you won't have to re-download it, and it will load directly from your computer. It will be MUCH faster the next time.

---

### Post by betrunkenaffe on 2009-05-28
wine GW.exe -image

Run that command and GW will download all the files for it, if you run it overnight then you'll have minimal load times.

---

### Post by gunboat on 2009-05-29
> **wubiubiubi said:**
> That's great! to go to full screen, you can't just click the maximize button in the upper-right like on windows. when you get into the game, hit f11, then go to graphics. there should be a fullscreen button. click it. it will change to fullscreen. the game will remember that and should go to fullscreen when you open the program again. by the way, what's your gw name? If you're new to guild wars (i only say this because you said you're in ascalon city, don't be offended if you're not) I can help you with stuff. By the way, the reason it downloaded over 130mb is because whenever you "zone" into a new instance, it will need to download the data to the gw.dat file. the second time you "zone" or log in to the area, you won't have to re-download it, and it will load directly from your computer. It will be MUCH faster the next time.
 
No offense at all. I have owned GW for a long time, play it very little and set it aside. Then picked it up played a little, set it aside. Now, after being driven over the edge by Vista, I decided to give Linux another try - and installed Ubuntu. And Guild Wars is the best working game it seems under Ubuntu (my HOI2 crashes too often sadly) so decided to play it and see how far I will get. I have played to post-searing before, but I am only pre-searing right now (level 4 I think). I am playing a ranger named "Will Scarletti" [no points for originality I know]. What is your GW name? I am east coast USA time zone. If you are in the same zone/area let me know, I would enjoy the help. Also, are you in a guild?
 
As for the game play - it has been GREAT. I am amazed that a game like GW, so graphics heavy, plays so well in wine. Just amazing.

---

### Post by wubiubiubi on 2009-05-29
> **gunboat said:**
> No offense at all. I have owned GW for a long time, play it very little and set it aside. Then picked it up played a little, set it aside. Now, after being driven over the edge by Vista, I decided to give Linux another try - and installed Ubuntu. And Guild Wars is the best working game it seems under Ubuntu (my HOI2 crashes too often sadly) so decided to play it and see how far I will get. I have played to post-searing before, but I am only pre-searing right now (level 4 I think). I am playing a ranger named "Will Scarletti" [no points for originality I know]. What is your GW name? I am east coast USA time zone. If you are in the same zone/area let me know, I would enjoy the help. Also, are you in a guild?
 
As for the game play - it has been GREAT. I am amazed that a game like GW, so graphics heavy, plays so well in wine. Just amazing.

I'm in east coast as well. Yes I'm in a guild, but get your own, because mine kinda sucks lol. Anyway, if you have only prophecies, that's fine, but if you're getting really into the game I highly recommend the other campaigns. My name is "Collin Kalashnikov" (no, I'm not Russian, just like the name, hehe). I only have one pre-searing character, but once you get to post, I have like 4 characters that I can help you on. If you don't remember much about the game, it will be difficult, and you probably won't understand alot of the terminology that seasoned players use. Fortunately, the community in Guild Wars is much better than that of other MMO's, especially WoW. Ask around if I'm not on to help, you'll most likely get responses.

---

### Post by gunboat on 2009-05-29
> **wubiubiubi said:**
> I'm in east coast as well. Yes I'm in a guild, but get your own, because mine kinda sucks lol. Anyway, if you have only prophecies, that's fine, but if you're getting really into the game I highly recommend the other campaigns. My name is "Collin Kalashnikov" (no, I'm not Russian, just like the name, hehe). I only have one pre-searing character, but once you get to post, I have like 4 characters that I can help you on. If you don't remember much about the game, it will be difficult, and you probably won't understand alot of the terminology that seasoned players use. Fortunately, the community in Guild Wars is much better than that of other MMO's, especially WoW. Ask around if I'm not on to help, you'll most likely get responses.

Cool & thanks.

---

