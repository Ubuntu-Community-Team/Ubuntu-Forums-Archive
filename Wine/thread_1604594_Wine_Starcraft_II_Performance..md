---
title: "Wine Starcraft II Performance."
date: 2010-10-24
forum: Wine
---

### Post by freddan007 on 2010-10-24
I am playing Starcraft II in Wine from my old windows installation and performace is (as expecten) far from as good as in windows. Thus I am trying to find ways of improving performance. I have added the OpenGL registry Key, but I am wondering if reinstalling on my ubuntu drive will improve my performance?

Also, any other ways of improving performance is appreciated.

---

### Post by freddan007 on 2010-10-25
Bump.

---

### Post by freddan007 on 2010-10-29
bump

---

### Post by almigi on 2010-10-29
Have you tried reading the Starcraft II entry in the Wine AppDB located [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882]("here?")

I don't play StarCraft II, but it seems that for many people the game works great in Wine.

I also would recommend using Wine to run the installer and reinstall the game to your Ubuntu partition as well.

---

### Post by vexorian on 2010-10-29
I followed the instructions in appdb and it works great for performance. The performance is most likely always going to be lower than in windows, but at least in my case it is not much lower.

Key points:
- Use WINE 1.3 from winehq's ppa.
- Have updated graphic cards drivers. In my case, just using the latest nvidia stuff from maverick repos was enough. But you may need to use the latest driver from nvidia's site. (Make sure it is the restricted driver)

- Try running without compiz, for example, you can start a CLI session from gdm instead of using gnome. I use metacity compositing instead of compiz and that is enough.

Since many things are not done with graphics card, CPU requirements are probably higher than for windows.

Anyway, I was able to run SC2 decently (good fps but in low quality) with a 8400gs nvidia and a Core 2 Duo 7500e by following the instructions in winehq's page. If you have something lower than that, then I think it will get unplayable.

Edit :Another thing is that the first time you run SC2, it will try to download a lot of things and that first time the interface will be slower until everything is downloaded, give it patience.

---

### Post by Aydos on 2010-10-29
I see this post come up all the time and it always gets dismissed.

You see a lot of check appdb they get it running on there with good performance and you see a lot of I have it running with great performance her, but the people at the end state in low settings.

The thing is some people, like me for example can run it in Windows in Ultra mode with close to 200 FPS in an epic battle, but in Ubuntu with the latest drivers from Nvidia and my stuff running other games and benchmarks flawlessly have to run the game on low settings in get lag in a large battle.

I do not expect a game to run as well as it does in Windows since it is a Windows client, but you should be able to get a little closer than we currently are.

We need to stop acting like it runs fine and see if as a community we can come up with a solution. I am not a coder, but us players who are not coders can run the game and report bugs and share info to get this running better.

Just my 2 cents.

---

### Post by vexorian on 2010-10-29
> You see a lot of check appdb they get it running on there with good performance and you see a lot of I have it running with great performance her, but the people at the end state in low settings. Strikes me as untrue. I have a very low end card, I can only run in medium at most in windows and fps is low. In Linux with latest WINE (specially WINE), performance is lower but not much lower. Plenty of the guys in winehq actually report higher quality than low. For example: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882&iTestingId=57873](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882&iTestingId=57873) reports that he can run in ultra using a 9600.

Considering my current performance using a low end card. I really think you should be able to run in high if you can run in ultra with 200 fps as you mention.

I think you should really try at least with WINE 1.3 and disabling compiz (I think that's what did the most difference for me)

Another thing, Blizzard is sabootaging us this time and for ABSOLUTELY NO REASON they disabled the opengl mode from the windows version.

[http://us.battle.net/sc2/en/forum/topic/188779410#1](http://us.battle.net/sc2/en/forum/topic/188779410#1)

---

### Post by Tuteh on 2012-05-30
Guys maybe this is a bit old now, but i just found out something. I opened up a terminal and used the following: 
cpufreq-selector -g performance

what this did for me is enable the cpu to run on performance when playing sc2 and not powersave.
i only have this selection (between powersave and perfomance) issue when playing sc2 not wow or diablo 3, im guessing it must be some sort of bug on behalf of SC2 cause i went from 24 fps on medium to 40 on ultra. SC2 was the only game that took a long time to load  and returned low fps.

my system runs a core 2 duo e8400 with nvidia gtx275.

here is the wine bug address

[FONT=monospace]http://bugs.winehq.org/show_bug.cgi?id=24558[/FONT]

---

