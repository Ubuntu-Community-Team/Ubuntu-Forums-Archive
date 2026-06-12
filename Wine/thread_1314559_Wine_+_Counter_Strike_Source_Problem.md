---
title: "Wine + Counter Strike Source Problem"
date: 2009-11-04
forum: Wine
---

### Post by .:Justus:. on 2009-11-04
I succesfully installed Steam through wine, and I finished downloading Counter Strike source as well.
Now when I try to start CSS by double clicking it in steam, steam simply closes and nothing happens.
And when I try to start CSS in the Wine dropdown menu nothing happens either...
What did I do wrong and how can I fix this?

---

### Post by Dooms_day on 2009-11-04
i dont think wine should be used for anything except very simple programs  i dont trust any kind of emulator with so many low level hardware calls and stuff like that, just wont work lol

---

### Post by band-aid on 2009-11-04
Wine actually does a pretty good job of running most things. I have personally run World of Warcraft very well on minimal hardware. I recommend you check the wine application database for program specific tweaks you can try in order to get it working.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

I was bored so I looked it up for you. It appears the game has either a silver or platinum rating so it should run very well.

---

### Post by edin9 on 2009-11-04
> **band-aid said:**
> Wine actually does a pretty good job of running most things. I have personally run World of Warcraft very well on minimal hardware. I recommend you check the wine application database for program specific tweaks you can try in order to get it working.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

I was bored so I looked it up for you. It appears the game has either a silver or platinum rating so it should run very well.

WoW runs better than most things under WINE.

---

### Post by hikaricore on 2009-11-04
> **Dooms_day said:**
> i dont think wine should be used for anything except very simple programs  i dont trust any kind of emulator with so many low level hardware calls and stuff like that, just wont work lol

Please don't post garbage.

---

### Post by beastrace91 on 2009-11-04
> **.:Justus:. said:**
> What did I do wrong and how can I fix this?

Wine Version, graphics card, and driver version installed? CSS runs pretty well using the latest Wine version (1.1.32 as I type this) - also be sure you have the latest drivers for your GFX card to ensure stability and performance.

~Jeff

---

### Post by .:Justus:. on 2009-11-05
Thanks for the quick replies.
@ band-aid
I heard also that it works almost perfectly on most computers. Hope I can get this to work. Thanks for the link aswell, trying to install that patch right now :D
@beast
My drivers should be up-to-date, just got them off of the AMD site a couple days ago.
What else could I be missing?
I have the newest wine, newest drivers... hmm.
I installed steam from the cd though, could that be the problem?
I put the windows cd in, and ran the setup.exe with wine.
Should I try it a different way?

---

### Post by beastrace91 on 2009-11-05
> **.:Justus:. said:**
>  just got them off of the AMD site a couple days ago.

Oh Jeez. ATI card then I'm assuming? 

~Jeff

---

### Post by .:Justus:. on 2009-11-05
> **beastrace91 said:**
> Oh Jeez. ATI card then I'm assuming? 

~Jeff

Yea, well it seems to work a lot better now, i got the new wine version.
But now, when i click on css, the little loading window comes, but after that nothing happens....

---

### Post by beastrace91 on 2009-11-05
Can you load Steam (or CSS) through terminal and post the out put of the dump when it fails to load? Just as a heads up though ATI drivers are a joke at best on Linux - you may not be able to get CSS to work with them.

~Jeff

---

### Post by .:Justus:. on 2009-11-06
> **beastrace91 said:**
> Can you load Steam (or CSS) through terminal and post the out put of the dump when it fails to load? Just as a heads up though ATI drivers are a joke at best on Linux - you may not be able to get CSS to work with them.

~Jeff

Hm,won't work by simply using "~ directory/file"
What command should i be using to start cs from the terminal?

I mean, i know how to launch it from the terminal, just how do i get it to show the output of the dump?

---

### Post by beastrace91 on 2009-11-06
Loading it via terminal will cause it in turn to show all the Wine calls on the in-between in the terminal screen. Just load it via terminal, then post the last bulk of lines after CSS dumps out.

EDIT: Also just so we are on the same page post the output from ```
wine --version
``` as well.

~Jeff

---

### Post by .:Justus:. on 2009-11-06
> **beastrace91 said:**
> Loading it via terminal will cause it in turn to show all the Wine calls on the in-between in the terminal screen. Just load it via terminal, then post the last bulk of lines after CSS dumps out.

EDIT: Also just so we are on the same page post the output from ```
wine --version
``` as well.

~Jeff

Wine version: wine-1.1.31

When I load the game through the terminal, it doesnt say anything, like I dont see any lines or anything like that.
Could you tell me exactly what to put into the terminal in order to load it with the correct info?
thanks a bunch

---

### Post by beastrace91 on 2009-11-06
Just as I thought - your Wine version is out of date (1.1.32 is the current release - in fact .30 and .31 suffered from some regressions that caused CSS to stop working on some systems). Update to the latest version of Wine and then try CSS again.

To run it with Wine from terminal just find where your Steam.exe is located and run **wine Steam.exe** from then on everything in terminal (including messages from games loading) will be from Steam.

~Jeff

---

### Post by .:Justus:. on 2009-11-07
> **beastrace91 said:**
> Just as I thought - your Wine version is out of date (1.1.32 is the current release - in fact .30 and .31 suffered from some regressions that caused CSS to stop working on some systems). Update to the latest version of Wine and then try CSS again.

To run it with Wine from terminal just find where your Steam.exe is located and run **wine Steam.exe** from then on everything in terminal (including messages from games loading) will be from Steam.

~Jeff

Ah, thats weird, first time i tried i got wine straight off of their website, then i got it from the repositories. 
Hmm, ill try again. thanks :]
Ill be back with the output of the lines in a minute.

---

### Post by .:Justus:. on 2009-11-07
> **.:Justus:. said:**
> Ah, thats weird, first time i tried i got wine straight off of their website, then i got it from the repositories. 
Hmm, ill try again. thanks :]
Ill be back with the output of the lines in a minute.

Ah ok, it worked now, i just deleted and reinstalled wine.
Now i've got the newest, lets see if it works :D

edit: Ok, i can finally get into counter strike, almost impossible to read fonts, eventhough i have the tahoma one installed...
But the game crashes either when im at the "sending client info" page or at the motd screen.
Really annoying.

---

### Post by beastrace91 on 2009-11-07
I'd give a couple other Wine versions a try if I where you. If that doesn't work odds are your ATI card is to blame :(

~Jeff

---

### Post by .:Justus:. on 2009-11-07
> **beastrace91 said:**
> I'd give a couple other Wine versions a try if I where you. If that doesn't work odds are your ATI card is to blame :(

~Jeff

Thanks again for your help jeff.

For everyone who has similar problems. Try the following things.

~update graphical drivers
~upgrade/downgrade wine version (recommended for downgrade is 1.1.28 since everything went fine for most people during that version)
~install the patch from this link: [http://home.comcast.net/~vivnet/freetype.patch](http://home.comcast.net/~vivnet/freetype.patch)

---

### Post by beastrace91 on 2009-11-07
w00t! Glad you got it working :D

~Jeff

---

