---
title: "System Shock 2"
date: 2007-04-10
forum: Ubuntu Gamers Arena
---

### Post by Emblem Parade on 2007-04-10
Help me, Ubuntu Gamers' Arena, you're my only hope!

I've done everything in my power to try to get System Shock 2 running on Ubuntu, to no avail. My current error is "Your video hardware is not supported by System Shock 2."

Hardware: Athlon 64 X2, Nvidia GeForce 6200
Software: Edgy Eft, Wine 0.9.34, Nvidia Beta Drivers 1.0.9746

What can I do to convince the game that my hardware is supported? ;)

I've tried to configure Wine to be Windows 98, same error. Installation has not been a problem at all. I just can't run the game itself. I've used both the original CD and the Underdogs "abandonware" downloadables, but they seem to have the same problems. I've followed all the various forums explaining how to get it to run on Windows XP, and those haven't helped either.

For the record, I couldn't get it to run on my Windows XP partition, either, though I didn't try as much as I did for Ubuntu. (And ever since I switched to Ubuntu a month ago, my Windows XP just-to-be-on-the-safe-side partition has been gathering digital dust...) On Windows XP, I can get it to the menu, but it crashes when I try to start a new game. I'm sure it's a different kettle of fish there, though, than on Ubuntu.

If anyone has managed to get this classic game running on Ubuntu, please help!

---

### Post by justin whitaker on 2007-04-10
According to this:

[http://appdb.winehq.org/appview.php?iVersionId=2270](http://appdb.winehq.org/appview.php?iVersionId=2270)

It works. Not 100%, but it looks like some Gentoo folks got this running. 

I know that's not much help.

---

### Post by compiledkernel on 2007-04-10
Ok so following the regular game path that I follow 

1. WineAppDB - [http://appdb.winehq.org/appview.php?iVersionId=2270](http://appdb.winehq.org/appview.php?iVersionId=2270) 

which states  -- 
The game's installer refuses to install if it detects Windows 2k or later.  To work around this, you have two options.  First, you can run winecfg and set the Windows version to Windows 98, and then run setup.exe from the CD as normal.  Alternatively, you can open a terminal, navigate to the CD drive, and run the installer this way: wine "setup.exe" &#8211;lgntforce

I tested a full install. When prompted, install the Intel Codec, but click "stop search" when it begins scanning your folders looking for Netscape.  As recommended, do not install Direct X.

Install the official patch

[http://www.irrationalgames.com/shock2/](http://www.irrationalgames.com/shock2/)

For better looking graphics:

Install the SHTUP texture pack: [http://shtup.home.att.net/](http://shtup.home.att.net/)
Install the Rebirth High-Definition model pack: [http://www.strangebedfellows.de/index.php/topic,8.0.html](http://www.strangebedfellows.de/index.php/topic,8.0.html)

Remove the copy protection

Currently, the latest version of Wine doesn't seem to like the Safedisc copy protection used by the program.  You will have to get around this by finding a no-cd crack.

2. Now then, all that said I then cruise out to the cedega wiki 

which states -- [http://cedegawiki.sweetleafstudios.com/wiki/System_Shock_2](http://cedegawiki.sweetleafstudios.com/wiki/System_Shock_2)

    *  Installer crashes when trying to install the video codec for the cutscenes. This is non-fatal however, and the installer does continue after the crash. Because of this, cutscenes don't play. This is not a big problem, since there are only two cutscenes in the entire game (one at the start, one at the end).
    * To work around a menu animation glitch, turn off Accelerated Interprocess Communication and switch on Decrease WineServer Priority.
    * Graphical performance is much better in Cedega-4.1 and higher.

Now all that be said, additional links to reference to the issue 

Wine
[http://www.winehq.org/pipermail/wine-devel/2003-April/016463.html](http://www.winehq.org/pipermail/wine-devel/2003-April/016463.html)

Any help at all?

---

### Post by crane on 2007-04-10
Just to check, Do you have any other 3d games running? or maybe beryl or compiz?
I don't mean running while you try to play. Just will they run?

---

### Post by Emblem Parade on 2007-04-10
Thanks guys! Of course I checked the Wine database, but the instructions there are irrelevant. As I said, installation wasn't a problem anyway under Ubuntu, and setting Wine to run as Windows 98 didn't change anything.

Compiz and Beryl run just fine on my system, and disabling them doesn't change anything. I also run Half Life 2, which makes me happy! So, 3D is not a problem.

Would the last two entries I get when running it help? They may be related to my error message:

```
fixme:msg:pack_message WM_NCPAINT hdc packing not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```

You know, the best way to help me is to try to get it to run yourselves. :) It's available legally at Underdogs.

[http://www.the-underdogs.info/game.php?gameid=3924](http://www.the-underdogs.info/game.php?gameid=3924)

If you do manage to run it, you'll be happy little gamers!

---

### Post by justin whitaker on 2007-04-10
> **Emblem Parade said:**
> Thanks guys! Of course I checked the Wine database, but the instructions there are irrelevant. As I said, installation wasn't a problem anyway under Ubuntu, and setting Wine to run as Windows 98 didn't change anything.

Compiz and Beryl run just fine on my system, and disabling them doesn't change anything. I also run Half Life 2, which makes me happy! So, 3D is not a problem.

Would the last two entries I get when running it help? They may be related to my error message:

```
fixme:msg:pack_message WM_NCPAINT hdc packing not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```

You know, the best way to help me is to try to get it to run yourselves. :) It's available legally at Underdogs.

[http://www.the-underdogs.info/game.php?gameid=3924](http://www.the-underdogs.info/game.php?gameid=3924)

If you do manage to run it, you'll be happy little gamers!

I'll load this up in Crossover, see if there is a way to get it to go.

---

### Post by Emblem Parade on 2007-04-11
Hey, any news? Does it work with Cedega?

---

### Post by justin whitaker on 2007-04-16
> **Emblem Parade said:**
> Hey, any news? Does it work with Cedega?

The UD download works under Cedega 6.0. It does not install as far as the Cedega UI is concerned, but if you pretend to install it, the game launches, and runs beautifully. Sound is perfect, graphics are fine, even saves and reloads games. 

Run the OGG.exe version, then run the sshock.exe.

---

### Post by claydoh on 2007-04-17
I have not tried in a while, but  for me I believe SS2 had issues with nvidia graphics drivers some time back, and I was never able to install or play the game (My fave game ever!) in wine or cedega in quite some time. I will try again, especially as if there has been some recent success. I had tried in cedega 5, but have since cancelled my long standing subscription, and never tried it in wine versions in over a year.

There is still some question as to the legality of UD's release, but I do have my cd, bought new in 1998(9), though it is mightily scratched.

---

### Post by Emblem Parade on 2007-04-17
Thanks! Because my error is "Your video hardware is not supported by System Shock 2" I strongly suspect that, as you say, it might be driver related, and that Cedega won't be able to solve the problem.

Wouldn't an old game like SS2 use on common-denominator directives? Shouldn't it work on all modern cards? And, if not, wouldn't there be a lot of old games that suffer from the same problem?

AND, if so, isn't there some sort of compatibility or emulation layer that would allow my card to pretend it's an old card for the purpose of running such classics?

I haven't installed Cedega yet -- I'm waiting a few more days for the upgrade to Feisty, and when things settle I'll see about Cedega. But... you give me pause to think that Cedega will still not work for me.

---

### Post by Mikhal on 2007-05-01
I can confirm that the game runs perfectly like Justin said using Cedega 6 for the Underdogs download. I even run nearly the same setup as you, Emblem (Feisty, Athlon 64 X2 3800+, GeForce 6150), so I don't think you'll have any trouble running it. Only problem (like stated earlier) was the video cutscenes not showing.

---

### Post by AndreAPL on 2007-06-28
hi there. Im also trying SS2 from there, but mine runs very slow...  is because of cedega 5.1 ?
(amd 3.0+, 9800se, 1gb mem :) )

---

### Post by Sam Plamondon on 2008-06-07
I've gotten System Shock 2 (the Underdogs version) to run with Wine, but the frame-rate is somewhere between 1 and 5 FPS on the lowest resolution, which makes the game absolutely unplayable.  I can play games such as Half-Life 2 and Doom 3 with 30 or more FPS in Windows Vista, so how come System Shock 2 (a much older game) runs so badly?  Is it because of Wine, or because of Ubuntu in general?  Are their any tweaks that could improve the frame-rate, or should I just give up?

---

