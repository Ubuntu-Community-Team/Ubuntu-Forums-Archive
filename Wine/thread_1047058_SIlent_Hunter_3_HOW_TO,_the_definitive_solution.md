---
title: "SIlent Hunter 3 HOW TO, the definitive solution"
date: 2009-01-22
forum: Wine
---

### Post by Cannaregio on 2009-01-22
Here the necessary steps, if you follow exactly this how to, the game should work BETTER than in windows xp (and of course better as in vista), provided you have all the

[COLOR="Blue"]NECESSARY HARD/SOFT STUFF[/COLOR]
-------------------------------------------------------
[LIST=1]
[*]A good graphic card and the correct drivers for it (compiz working, flxgears speedy enough, etc... I won't go into that here). Note that if your graphic card or your CPU are not top notch [COLOR="Blue"]this simulation might "stutter"[/COLOR] no matter the OS we are using (see [next post]("http://ubuntuforums.org/showpost.php?p=6610951&postcount=2") of mine below)
[*]The MOST RECENT version of wine (I'm using 1.1.13 at the moment), a older point .9 version wont work with the periscopes
[*]A good GNU/Linux distribution (let's assume you use Ubuntu/Intrepid)
[*]The necessary patches and add-ons for the game + the game itself (very cheap to buy and/or very easy to find on the web... should you fail to find a second hand or "reminders" software shop near you)
[/LIST]

[COLOR="#0000ff"]HISTORY/REASON/WHY THE HASSLE OF INSTALLING A 4 YEARS OLD PROPRIETARY GAME?[/COLOR] (jump if you don't care)
-------------------------------------------------------
Silent Hunter 3 (SH3) is imho one of the best tactical simulations of submarine warfare you could find at the moment. In many aspects it surpasses the more recent -and more "hollywoodian"- Silent Hunter 4 (that cares more for the eggplant level "one shooter" morons). This game is very captivating, has prima graphics, tactical überdepth and fascinating naval "atmosphere" and you'll probably enjoy it for [COLOR="#0000ff"]years[/COLOR]... or at least months (not weeks, not days).

Good games released for linux are still next to non-existant, so we must (still) stuck with the proprietary crap and the hassle to install a windows application if we want to satisfy our ludic instincts :-)
One advantage is that so doing we avoid the "guinea pig trap" of all new games being released on the unaware zombieland in a very [COLOR="#0000ff"]expensive[/COLOR] and extremely [COLOR="#0000ff"]buggy[/COLOR] status: only [COLOR="Blue"]after many years[/COLOR] SH3 went mature enough, thanks to all the necessary patches that appeared long AFTER its original buggy release.

The slightly disgusting feeling of having to play as a U-boat commander for nazy germany -there are no other options- can easily be compensated playing (with cedega) the [COLOR="Blue"]strategically and tactically marvelllous[/COLOR] WWII simulation combat mission 2, barbarossa to berlin (CMBB) on the soviet side and blowing up all those nazi tanks in the snow with your strategical and tactical finesse... ...and your glorious KV1s and T34s :-)

The above reasons are good enough to play Silent Hunter 3.

[COLOR="#0000ff"]HOW TO[/COLOR]
-------------------------------------------------------
[LIST=1]
[*] Get a iso of SH3 (buy second hand: 5 euro atm, or find on the web & download: aplenty places).
[*] Get the [COLOR="Blue"]necessary[/COLOR] update patch (probably named [COLOR="#0000ff"]silent_hunter_3_dvd_1.4b_emea.exe[/COLOR])
[*] Get [COLOR="#0000ff"]optionally[/COLOR] the nice add-on for the mediterranean theater (see below)
[*] Mount the SH3 iso with Gmount-iso
[*] Browse the iso and launch [COLOR="#0000ff"]setup.exe[/COLOR] using a recent version of wine ([1.1.13 for instance]("http://www.winehq.org/announce/1.1.13"), with previous .9 versions the periscopes will both crush wine and the simulation)
[*] Install the simulation. 
Towards the end of the install process you might get a request to install that "shadow" crap. 
Don't do that, and -unless you see a "no thanks" option- kill the shadow installer and see if you can finish your installation. 
If necessary [COLOR="Blue"]reinstall[/COLOR] in order to terminate your installation correctly. 
[COLOR="#0000ff"]DO NOT LAUNCH THE GAME YET[/COLOR]. 
[*] Reboot as needed. Perform on a terminal wineboot just in case. 
[COLOR="#0000ff"]DO NOT LAUNCH THE GAME YET[/COLOR].
[*] Find and install the patch (probably named [COLOR="#0000ff"]silent_hunter_3_dvd_1.4b_emea.exe[/COLOR]). 
[COLOR="#0000ff"]DO NOT LAUNCH THE GAME YET[/COLOR].
[*] [COLOR="#0000ff"]Optionally[/COLOR] install a nice add on for the mediterranean theater (probably named [COLOR="#0000ff"]silenthunter3addon.ngr[/COLOR], optionally use acetoneiso2 to transform it into an iso first, showing your disgust for that [COLOR="Blue"]ngr[/COLOR] "nero format"). [COLOR="#0000ff"]DO NOT LAUNCH THE GAME YET[/COLOR].
[*] Even if we have all bought a fully legit copy, having to keep the stupid disk in the stupid drive is a stupid hassle. Get [the necessary files to avoid disk checking]("http://www.google.com/search?hl=en&client=opera&rls=en&q=%22silent+hunter+3%22+%22no+dvd%22&btnG=Search"). 
Copy and paste the five files of the crack... 
[*] [COLOR="#0000ff"][LIST]
[*] MissionEngine.dll
[*] sh3.exe
[*] SimData.dll
[*] StateMachine.dll
[*] Utils.dll[/LIST][/COLOR]...into the folder where you installed SH3. If you wish, before pasting, rename the original dll files and the original exe file to "[COLOR="#0000ff"]ori[/COLOR]" in order to keep them for the posterity.
[*] Play and enjoy the simulation. EVERYTHING will work, methinks even much better than in windows, despite the wine overlayer, because we don't need all those intrusive spying and snuffing applications, nor those norton can of worms, nor those stupid firewall alarms running in the background, popping out indecently and slowing down our CPUs. And this is truly a great tribute to the wine developers... Hip, hip, Hurrah!
[/LIST]
So, uff, this was it... enjoy!

---

### Post by Cannaregio on 2009-01-24
THREE problems I haven't solved.

If anyone knows one (or more) working answer(s), please do post here, else I will do it myself... as soon as I find some solutions :-)

-------------------------[COLOR="#0000ff"]- 1 STUTTERING -[/COLOR]--------------------------------
There are (not always, some times) some 'stuttering' problems when the time compression is bigger than 64 and you have a lot of traffic (down from 12-14 FPS to 3-4 FPS).
This happens in windows XP as well and it is due to the relatively high graphic requirements of this simulation.

[COLOR="DimGray"]Some solution attempts:[/COLOR]
Even at a moderate 1280 x 1024 resolution with a mid-range NVIDIA card  you shoul be able to enable 2x FSAA and still find a very playable game with few frame rate hiccups. Unfortunately my Geforce 6200 does not seem to be up to the task :-(
At 1280 x 1024 or greater, a 256MB graphics card is required to ensure a playable experience, particularly with high-quality textures turned on. 
Those with ATI Radeon 96xx-series cards or NVIDIA GeForce 62xx-series cards will want to keep the lighting options turned off, unless playing at 1280 x 1024 or below. 
If you're running the game with a CPU in the minimum range - a 2GHz Intel Pentium 4 or AMD Athlon equivalent - then [COLOR="Blue"]turning down Particle Density and turning off Environmental Effects will increase the frame rate[/COLOR].

I turned down particle density to [COLOR="Blue"]47[/COLOR] and this solved the most annoying stuttering problems. 
With older (less than 256) graphic cards be careful and when there's a lot of traffic around DO NOT choose [COLOR="Blue"]excessive time compression rates[/COLOR] (remain under 256 even with low particle settings)... [COLOR="#0000ff"]...else the simulation will crash[/COLOR].

-------------------------[COLOR="#0000ff"]- 2 SCREEN SIZE -[/COLOR]--------------------------------
I haven't solved the problem of going beyond the 4:3 1024*768 hardcoded screen size. Would love to have it running on my 16:10 22' 1680*1050 monitor (as in windows xp, where this is possible), but didn't manage yet, no matter what parameters I changed.
Of course higher resolution will necessarily require an even faster graphic card... and will therefore increase the stuttering problems discussed above :-)

-------------------------[COLOR="#0000ff"]- 3 GWX3 ADDON -[/COLOR]--------------------------------
[GWX3 gold]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=yYW&q=GWX3+gold+%22silent+hunter%22&btnG=Search") does NOT seem to work :-(
[COLOR="Blue"]Clean[/COLOR] install "ex-novo" with or without "mediterranean extension" and then "gwx3 gold" install: it does install indeed, and it even starts, but as soon as you begin a career, or a mission, it loads until 80% and then after a long while wine dies out.

Otoh, [sh3 commander]("http://hosted.filefront.com/Realjambo/") (a very useful standalone application, updated on 23 JAN 2009, that you run before playing SH3) works perfectly. 


[COLOR="DimGray"]My rig: Ubuntu Intrepid, 2.6.27-7-generic, Geforce 6200 SE, Samsung Syncmaster 1680*1050 - glxgears gives around 720 FPS[/COLOR]

---

### Post by vauss on 2009-02-02
Cannaregio, I solved the problem 1 and 3 by creating (in the registry) the key *HKEY_CURRENT_USER\Software\Wine\DirectSound* , and in that key creating a string *MaxShadowSize* with value [I]0

[/I]I hope it will help you.

---

