---
title: "How do you get Steam + steam games to run decently under Wine using PlayOnLinux?"
date: 2010-08-04
forum: Wine
---

### Post by Lyude on 2010-08-04
I'm assuming this goes on this board since the majority of this depends on wine.
Hello, I recently switched to Ubuntu, and I have noticed Steam and any steam games seem to run like crap on PlayOnLinux under Wine. I mean I can get them to run, but they're much slower and such then they were on Windows. I currently keep windows installed in order to play games simply by rebooting, but I'd like to keep everything in ubuntu. Steam also will glitch when I move the windows (they jump around), and some windows will keep opening back up if I attempt to close them, and when a notification comes up (for like an instant message or the like) if I click it the chat window for the person will not appear, and sometimes if I move the window it will just disappear completely and I won't be able to find it again. I also never hear the sounds that are supposed to play when I receive an instant message.
Does anyone know any tricks to get Steam to run decently (or close to it) along with Steam games? I use Ubuntu 10.4 x86-64. And I have tried appdb, but there doesn't seem to be much on there that helps.

---

### Post by dardack on 2010-08-04
> **Lyude said:**
> I'm assuming this goes on this board since the majority of this depends on wine.
Hello, I recently switched to Ubuntu, and I have noticed Steam and any steam games seem to run like crap on PlayOnLinux under Wine. I mean I can get them to run, but they're much slower and such then they were on Windows. I currently keep windows installed in order to play games simply by rebooting, but I'd like to keep everything in ubuntu. Steam also will glitch when I move the windows (they jump around), and some windows will keep opening back up if I attempt to close them, and when a notification comes up (for like an instant message or the like) if I click it the chat window for the person will not appear, and sometimes if I move the window it will just disappear completely and I won't be able to find it again. I also never hear the sounds that are supposed to play when I receive an instant message.
Does anyone know any tricks to get Steam to run decently (or close to it) along with Steam games? I use Ubuntu 10.4 x86-64. And I have tried appdb, but there doesn't seem to be much on there that helps.

Because steam isn't a native client for linux.  Why do people expect games meant to run on windows to run at same speeds on linux?

---

### Post by cogadh on 2010-08-04
@dardack - That is a really good question and one that we are likely to never know the answer to.

@Lyude - The fact is, as good as Wine has become over the years, it is still not Windows and therefore it does not necessarily run applications as well as those apps would run in their native environment. This is especially true of games, where you often have the extra performance hit from Wine translating Direct3D actions into OpenGL actions, on top of its normal "translation" work. Some games and apps will work better than others and if you have a machine with really high hardware specs it may "hide" some of Wine's performance flaws, but it will never run everything perfectly.

---

### Post by asdfoo on 2010-08-05
> **dardack said:**
> Because steam isn't a native client for linux.  Why do people expect games meant to run on windows to run at same speeds on linux?

Plus every game is different, some work perfectly, others have issues and more so if you have an intel or ati card.

---

### Post by beastrace91 on 2010-08-05
I hate when people lump "steam games" into one group when asking about Wine. For instance both Torchlight and Crysis are on Steam - two very different beasts when it comes to getting them working under Wine technology.

That being said - with proper hardware (nVidia) most Valve games (source engine) perform around 70-80% the speed of on Windows under Wine.

~Jeff

---

### Post by namebrandon on 2010-08-05
> **beastrace91 said:**
> I hate when people lump "steam games" into one group when asking about Wine. For instance both Torchlight and Crysis are on Steam - two very different beasts when it comes to getting them working under Wine technology.

That being said - with proper hardware (nVidia) most Valve games (source engine) perform around 70-80% the speed of on Windows under Wine.

~Jeff

Hey neighbor! Good to hear..! I'm working my way through getting CS:S to run under DX9, and using identical settings, I was getting ~180fps in Windows, and ~12fps under Wine. I think you just confirmed for me that that was not normal Wine behavior. :)

---

### Post by Lyude on 2010-08-05
I apologize xD, it's just when you look this stuff up on the internet you get put under the impression that there is a way to get them to run better. Oh well, thanks anyway.

---

### Post by dardack on 2010-08-05
> **Lyude said:**
> I apologize xD, it's just when you look this stuff up on the internet you get put under the impression that there is a way to get them to run better. Oh well, thanks anyway.

Before I purchase a game, I always check the wine database for that game.  ie, Starcraft 2 came out tuesday.  That wednesday i checked out:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

Enough people said it ran fine (i always buy nvidia graphics cards just because of the drivers for linux and I have supported nvidia for years just because of that), so I put down my $60.00+tax-1 cent, bam up and running 25+ FPS.

Steam for me, Monkey Island worked great with a few wine compiles in (i have about 20+ .wine prefixes for different games, and I always self compile wine).  

The thing to remember, you didn't give specs of your system.  If your talking intel/ati graphics that can be half your problem right there.  (Although I hear catalyst is getting better, it's still not near nvidia drivers yet).

---

### Post by Lyude on 2010-08-05
Sorry about that xD. I'm using a Core 2 Quad Q9550 at 3.35 GHz and a Sapphire ATi Radeon HD 4850 (stock since overclocking in Linux never really worked too well for me)

---

### Post by dardack on 2010-08-05
> **Lyude said:**
> Sorry about that xD. I'm using a Core 2 Quad Q9550 at 3.35 GHz and a Sapphire ATi Radeon HD 4850 (stock since overclocking in Linux never really worked too well for me)

ATI is probably 50-75% of your problem.  Sorry to say.

---

