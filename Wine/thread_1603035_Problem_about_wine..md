---
title: "Problem about wine."
date: 2010-10-22
forum: Wine
---

### Post by Pinejoker on 2010-10-22
I was playing LC - Last Chaos Online for a long time and this is the first time i have this problem. since the latest update of wine or ubuntu 10.04 now i couldn't play it anymore and its give me this error ---> * the program could not run itself.* Every time i click the start. :(

I hope someone can tell me to solve my problem. thanks:(

---

### Post by bobwyajnr on 2010-10-22
@Op

Number #1 : get familiar with your applications AppDB page!!
[Last Chaos @ WINE AppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4394")

What version of WINE are using?

What extras have you installed via Winetricks, etc.?

Have you tried running the game from a console?
```

cd ~/.wine/drive_c

```
Then you need to find the folder where your game is installed (under **Program Files** usually). It's just a clone of the standard MS Windows file system layout...
Then run the program executable, using WINE:
```

wine lc.exe *(or whatever it is called!!)*

```
Post up any useful terminal output here or on the AppDB page...

You haven't really told us anything about your level of ability with Linux/UNIX type systems. Noob or uber-geek? I assumed competent because the instructions could get very verbose if you aren't!! :guitar:

Anything not clear about the above then ask away!!

Bob

---

### Post by Pinejoker on 2010-10-22
at begining was beautiful... 
[IMG]http://i826.photobucket.com/albums/zz190/agentz73/lastchaosusa/Screenshot.png[/IMG]

but when i click START, it goes like this. popup "This program could not be run itself" 
[IMG]http://i826.photobucket.com/albums/zz190/agentz73/lastchaosusa/Screenshot-1.png[/IMG]

I'm not really familiar with linux and i'm just beginner of this OS. I have wine 1.2 the latest version and winetricks.

---

### Post by Pinejoker on 2010-10-24
I would imagine if someone will know the solution to this problem. Please help me to fix this. :(

here what i found and please help me out to work this on Ubuntu OS. [http://forums.aeriagames.com/viewtopic.php?t=927247]("http://forums.aeriagames.com/viewtopic.php?t=927247")

---

### Post by bobwyajnr on 2010-10-24
> **Pinejoker said:**
> I would imagine if someone will know the solution to this problem. Please help me to fix this. :(

here what i found and please help me out to work this on Ubuntu OS. [http://forums.aeriagames.com/viewtopic.php?t=927247]("http://forums.aeriagames.com/viewtopic.php?t=927247")

Might I recommend that calling your thread **'unable to run MMO game: Last Chaos (after most recent update)'** would have been more sensible than: **' Re: Problem about wine. '**. Uhhhm this is the **Ubuntu / WINE** thread after all...

Anyway down to business... I've spent an hour or two looking at this problem today - including about a Gb download (though I had dark glasses on at the time - so it's all good :cool:).

'fraid the long and the short of it is that your little program isn't running in WINE - but it is running in Windows 7. I must say the Aeria Games software is a bit on the flaky side (since the installer doesn't even work properly in Windows - without a bit of fiddling). I even tried copying the installation over from my Windows partition to the Linux partition (once the Windows installation was verified as working). Still getting the same bug as you "the program could not start itself" (very bad grammer I must say)...

I'll post up a bug on WineHQ (since I have corroborated your error message/ problem)...

Bob

---

### Post by Pinejoker on 2010-10-24
I actually change the settings of my wine, I put window 7 instead of window xp and still didn't work out. And Thank you! :KS

---

