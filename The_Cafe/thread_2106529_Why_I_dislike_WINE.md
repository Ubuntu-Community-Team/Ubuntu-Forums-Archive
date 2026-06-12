---
title: "Why I dislike WINE"
date: 2013-01-19
forum: The Cafe
---

### Post by Beardedturtle on 2013-01-19
It lags the computer due to memory hogging it takes 6Gb of memory out of 8Gb of memory when I try to launch it. >_< And I have to restart my comp to fix it.

---

### Post by mörgæs on 2013-01-19
Not a support question. 
Moved to the cafe.

---

### Post by Jakin on 2013-01-19
When you launch *it* or when launching a WINE application?

Wine takes little cpu effort or ram usage when i use it.

---

### Post by ajgreeny on 2013-01-19
You must surely mean when you are running a windows app through wine.

The only thing I have ever done using just wine alone is to configure it with ```
winecfg
``` in terminal which takes very little computer resource.

What application are you trying to run? Perhaps that is a memory/cpu hog.

---

### Post by mJayk on 2013-01-19
Wine doesn't take alot of resources on its own, I believe you're doing it wrong :D.

---

### Post by forrestcupp on 2013-01-19
> **mJayk said:**
> Wine doesn't take alot of resources on its own, I believe you're doing it wrong :D.

[IMG]http://funnyasduck.net/wp-content/uploads/2012/11/funny-doing-it-wrong-truck-in-water-boat-pics.jpg[/IMG]

---

### Post by Copper Bezel on 2013-01-19
I don't *like* Wine, because it took me two hours in my latest attempt to install MS Office with proper font smoothing enabled. There's always the possibility that something's going to go awry, and it's not a perfect fix even for the apps that work best with it; it would be much, much better to have supported software in the first place. But the task of creating an execution environment for apps designed for another OS, and doing so to such an extent that they're essentially running native, not under emulation, but never even know that they're on the wrong OS, is absurdly complex, and the fact that it ever works at all seems miraculous to me.

I haven't noticed any memory problems, but Office is the only Wine app I use, since it's the only Windows app I use.

---

### Post by sffvba[e0rt on 2013-01-19
Wine is awesome.  What it makes possible under Linux is incredible.


404

---

### Post by mreq on 2013-01-19
I like Wine. It enables me to use heidisql, which is awesome. Haven't found a better MySQL admin tool yet.

As for MS Office: when i really do need to use it, I load it in virtualbox and print as a PDF which I open in evince. Prefer LaTeX or libreoffice.

---

### Post by MadmanRB on 2013-01-19
> **Copper Bezel said:**
> I don't *like* Wine, because it took me two hours in my latest attempt to install MS Office with proper font smoothing enabled. There's always the possibility that something's going to go awry, and it's not a perfect fix even for the apps that work best with it; it would be much, much better to have supported software in the first place. But the task of creating an execution environment for apps designed for another OS, and doing so to such an extent that they're essentially running native, not under emulation, but never even know that they're on the wrong OS, is absurdly complex, and the fact that it ever works at all seems miraculous to me.

I haven't noticed any memory problems, but Office is the only Wine app I use, since it's the only Windows app I use.

Playonlinux might of helped here, as it has tools that cant patch office better then a standard wine install.
Or Crossover, while not being free it is a very good app.

---

### Post by jerome1232 on 2013-01-19
> **not found said:**
> Wine is awesome.  What it makes possible under Linux is incredible.


404

Times like this are the times I miss the "thanks" button on these forums.

---

### Post by odiseo77 on 2013-01-19
Wine runs fine on my system (C2D @ 2.93 Ghz with 4 GB of ram). With the games it works, obviously... I can even play some old games on Wine that for some reason don't work on my WinXP install anymore.

---

### Post by jeehyun on 2013-01-19
I prefer to use vmware player.
Unity makes me feel that program is really installed on ubuntu.
And there is no error message.
):P

---

### Post by Copper Bezel on 2013-01-20
If you have the system requirements for painless virtualization, it's certainly the better option, no question.

[QUOTE=MadmanRB]Playonlinux might of helped here, as it has tools that cant patch office better then a standard wine install.
Or Crossover, while not being free it is a very good app.[/QUOTE]
I haven't messed with Crossover. Office installed in PlayonLinux with no fuss, but that's where I ran into the font smoothing problem, which turned out to be a *relatively* easy fix in a normal Wine install, once I got through the mess of actually installing it in regular Wine. The font smoothing made the difference between the application being usable for me and not, so I considered that a point for Wine. = )

---

### Post by forrestcupp on 2013-01-20
Wine sucks because they didn't do a good enough job reverse engineering Microsoft Windows from scratch, so that every Windows app works flawlessly in Linux. It SUCKS!!!  ;)

---

### Post by Paddy Landau on 2013-01-20
I don't have that memory problem when I use Wine (I use it only for Quicken).

Of course Wine doesn't work perfectly — but just try running Linux programs under Windows, and see which system is superior!

---

### Post by greg_ory on 2013-01-20
Used Wine in the past and never had the problems you described but I would look into the application you are using within wine.

-Greg

---

### Post by sdowney717 on 2013-01-20
> **Copper Bezel said:**
> I don't *like* Wine, because it took me two hours in my latest attempt to install MS Office with proper font smoothing enabled. There's always the possibility that something's going to go awry, and it's not a perfect fix even for the apps that work best with it; it would be much, much better to have supported software in the first place. But the task of creating an execution environment for apps designed for another OS, and doing so to such an extent that they're essentially running native, not under emulation, but never even know that they're on the wrong OS, is absurdly complex, and the fact that it ever works at all seems miraculous to me.

I haven't noticed any memory problems, but Office is the only Wine app I use, since it's the only Windows app I use.

Which version of MS office did you install?
I have office XP and I dont think it works under wine.

---

### Post by Copper Bezel on 2013-01-20
MS Office 2010. It didn't work all in one step, but there are guides online for just which DLLs and suchlike have to be installed ahead of time. IIRC, there's serious weirdness with getting the .Net stuff to install properly on 64 bit.

> **forrestcupp said:**
> Wine sucks because they didn't do a good enough job reverse engineering Microsoft Windows from scratch, so that every Windows app works flawlessly in Linux. It SUCKS!!!  ;)
Yeah, my feelings exactly. I think it's crazy that the project exists, and I'd have to wonder if it was a waste of time if not for the few cases where it miraculously works, but when it works, that deserves some serious props.

---

### Post by forrestcupp on 2013-01-21
> **Copper Bezel said:**
> MS Office 2010. It didn't work all in one step, but there are guides online for just which DLLs and suchlike have to be installed ahead of time. IIRC, there's serious weirdness with getting the .Net stuff to install properly on 64 bit.
That's because you need to force wine to run as 32-bit. To do that, you have to remove your .wine directory, then type the commands
```
export WINEARCH=win32
wine

```You're basically deleting everything you have installed in Wine and starting with a fresh wineprefix that is 32-bit. Everything works great when you do that. I honestly think that Wine should set up as 32-bit by default.

Also, it is extremely easy to install MS Office 2010 with PlayOnLinux. It automates everything for you. You just put your disc in, tell it to install MS Office, and it does.

---

### Post by Paddy Landau on 2013-01-21
> **forrestcupp said:**
> … it is extremely easy to install MS Office 2010 with PlayOnLinux…
+1 for PlayOnLinux. I don't even know how to use Wine, but I can use it anyway because of PlayOnLinux.

---

### Post by monkeybrain2012 on 2013-01-21
I prefer to use native Linux applications as much as possible.  If one thinks that WIndows applications are so great he/she should be using WIndows. That said, I do use WIne for 3 things: WInbugs (which is not essential as I have jags, but it is still cool to be able to get it running),  pdf-xchange-viewer (for easy form filling, okular sorts of work but sometimes doesn't render the fields properly) and plants vs zombies. For those purposes it works very well but I wouldn't trust it for anything more serious (still hh doesn't render chm files correctly,--links don't work,-- and chmsee which runs natively in Linux is much better) Upgraded to wine1.5.22 via ppa and it is complaining that it needs wine-gecko1.9 and the ppa only provides up to 1.8, oh well.

---

### Post by Copper Bezel on 2013-01-21
I'd prefer it, too, but there are situations where there's only one app that can do the job you need. The fact that MS Office is a very good app suite wouldn't have been enough by itself to get me to futz my way through installing it.

> **forrestcupp said:**
> That's because you need to force wine to run as 32-bit. To do that, you have to remove your .wine directory, then type the commands
```
export WINEARCH=win32
wine

```You're basically deleting everything you have installed in Wine and starting with a fresh wineprefix that is 32-bit. Everything works great when you do that. I honestly think that Wine should set up as 32-bit by default.

Also, it is extremely easy to install MS Office 2010 with PlayOnLinux. It automates everything for you. You just put your disc in, tell it to install MS Office, and it does.

I had no problems installing Office on PlayOnLinux. I just couldn't enable the font smoothing, because I couldn't find a way to tweak the Wine prefixes for apps in PlayOnLinux. PlayOnLinux is supposed to take care of that sort of thing, but they missed a spot, and it was an important one. 

I didn't remember the details of the process for Wine, but yes, you're right, I had to force Wine to run 32-bit to get Office to install there.

---

### Post by TOMBSTONEV2 on 2013-01-21
Fallout, and Fallout 2 run on my HP Mini just fine; Ergo I actually like wine. For some reason they run better on ubuntu 12.04 with wine than they did on windows xp, or windows 7.

Wine uses almost no resources on my machine when I initiate it. Wine is definitely not without its bugs though. I do so enjoy when a program runs flawlessly on Wine.

---

### Post by forrestcupp on 2013-01-21
> **monkeybrain2012 said:**
> I prefer to use native Linux applications as much as possible.  If one thinks that WIndows applications are so great he/she should be using WIndows. That said, I do use WIne for 3 things: WInbugs (which is not essential as I have jags, but it is still cool to be able to get it running),  pdf-xchange-viewer (for easy form filling, okular sorts of work but sometimes doesn't render the fields properly) and plants vs zombies. For those purposes it works very well but I wouldn't trust it for anything more serious (still hh doesn't render chm files correctly,--links don't work,-- and chmsee which runs natively in Linux is much better) Upgraded to wine1.5.22 via ppa and it is complaining that it needs wine-gecko1.9 and the ppa only provides up to 1.8, oh well.Well, you've shown, yourself, why Wine is important. Most people use it to run the one or two Windows apps that they really need, and they *like* using Linux. I think it's great that people can choose to use the Linux that they like, and still be able to use some apps developed for Windows that they need or like.

> **Copper Bezel said:**
> I had no problems installing Office on PlayOnLinux. I just couldn't enable the font smoothing, because I couldn't find a way to tweak the Wine prefixes for apps in PlayOnLinux. PlayOnLinux is supposed to take care of that sort of thing, but they missed a spot, and it was an important one. 

I didn't remember the details of the process for Wine, but yes, you're right, I had to force Wine to run 32-bit to get Office to install there.
So you actually got font smoothing to work in MS Office? I haven't used Office in Wine for a while, but that was the main thing that a lot of people cried about. If it's not already on there, you really should post instructions on how you do that in the Wine subforum. That's a pretty huge fix.

---

### Post by sidzen on 2013-01-21
> **monkeybrain2012 said:**
> I prefer to use native Linux applications as much as possible.  If one thinks that WIndows applications are so great he/she should be using WIndows  . . . 
+1
|=**|< Wine, |>b|_|=**|< Windows !!  
Learn to use the CLI or don't say u know linux.

---

### Post by Paddy Landau on 2013-01-22
> **sidzen said:**
> |=**|< Wine, |>b|_|=**|< Windows !!
:confused: (scratching my head)

---

