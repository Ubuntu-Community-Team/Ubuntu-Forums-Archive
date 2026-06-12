---
title: "Aion The tower of eternity"
date: 2009-04-26
forum: Wine
---

### Post by sejml on 2009-04-26
Hello Ubuntufans any1 got aion running at ubuntu?

---

### Post by Grishka on 2009-04-26
> **sejml said:**
> Hello Ubuntufans any1 got aion running at ubuntu?

read the stickies! there's a separate forum for windows-related questions, you know.

---

### Post by europa on 2009-07-13
damn you, Grishka! Now I have to go search for the other thread he made... if any!

---

### Post by Zakhafr on 2009-09-02
There is indeed a sticky about GameGuard but **AION** is not listed in this topic, so, strictly speaking sejml did nothing wrong asking... although it is well known that AION uses **stupid** GameGuard and thus shouldn't work.

Maybe he/she would have liked to ask if someone successfully hacked around GameGuard... which is certainly not very legal and shouldn't be advertised here.
Once GameGuard is hacked, who knows, the game might work as well as games such as Guild Wars.

---

### Post by wakingrufus on 2009-09-17
I heard that NCSoft dropped gameguard from Aion.  Has anyone tested this?

---

### Post by airtonix on 2009-09-19
> **wakingrufus said:**
> I heard that NCSoft dropped gameguard from Aion.  Has anyone tested this?

Yes, tried running the version from my windows partition.

It still bombs out.

commandline log here : 
[http://pastebin.com/f16c14e2a](http://pastebin.com/f16c14e2a)

---

### Post by mangloid on 2009-09-19
I cant get the launcher to work, in order to try and run the game you need to go to the bin32 folder and run wine on AION.bin

Mine now tries to load and gives no more gamegaurd errors, but it still not playable. It crashed after  few moments of trying.

---

### Post by airtonix on 2009-09-20
> **mangloid said:**
> I cant get the launcher to work, in order to try and run the game you need to go to the bin32 folder and run wine on AION.bin

Mine now tries to load and gives no more gamegaurd errors, but it still not playable. It crashed after  few moments of trying.

```
$ wine ./bin32/AION.bin -ip:206.127.153.247 -port:2106 -cc:1 -noauthgg
```

You can also rename AION.bin to AION.exe, which precludes you from having to prefix the command with 'wine'

---

### Post by xanas3712 on 2009-09-20
airtonix, I hope you don't mind that I used your pastebin to report a wine bug on the issue since I'd really like to see the game playable one day soon.   

Also requested creation of a version for the official 1.5.0.6 on the wine appdb.

I'm hoping getting the game playable soon with some testing will give the developers a reason to keep gameguard out permanently, since I think they are more likely to bring it back without a player base who has reason to care about it being there.

---

### Post by elvendude on 2009-09-22
Has anyone tried this now that GameGuard has been removed from the live client?

---

### Post by skadevil on 2009-09-23
One guy gave it Gold Rating after GameGuard Removal at WineHQ.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17876](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17876)

At least I'm not able to run the game...always getting some .dll errors.

---

### Post by ElSlunko on 2009-09-23
Wow. I had no idea that they were getting rid of GG. I have a dual boot waiting for this game (and my paycheck at the end of the month) but am even MORE excited with this news. Maybe after some fixes we can get it running in Ubuntu :

[http://www.incgamers.com/News/18663/aion-gameguard-out-oceanic-server-in?gr_i_ni](http://www.incgamers.com/News/18663/aion-gameguard-out-oceanic-server-in?gr_i_ni)

---

### Post by Isarii on 2009-09-24
As of this moment, they're still planning to reintroduce Gameguard sometime after launch.  I assume everyone knows the problems with gameguard and can see how that would be bad for a launch.

---

### Post by ElSlunko on 2009-09-24
> **Isarii said:**
> As of this moment, they're still planning to reintroduce Gameguard sometime after launch.  I assume everyone knows the problems with gameguard and can see how that would be bad for a launch.

Yeah I read that as well. How long? Who knows. There were certainly many people having issues with it so I don't think it'll be in the immediate future. Oh well, at least for now we can have some success with WINE & Aion.

---

### Post by mac.repair.guy on 2009-09-27
I still seem to get a country code error... (on game startup) for some reason. Not entirely sure why. It could be because the game was installed on a windows machine and then I cloned it to my drive (wine directory). Maybe it is because I did not 'isntall' it in wine... strange.

~mac.repair.guy

---

### Post by ElSlunko on 2009-10-02
Got it to run in WINE with the advice here : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17877)

Installed in a virtual box and transferred the files to Ubuntu via shared folder. Works amazingly well for a new game. I'm getting 30-50fps with everything maxed.

---

