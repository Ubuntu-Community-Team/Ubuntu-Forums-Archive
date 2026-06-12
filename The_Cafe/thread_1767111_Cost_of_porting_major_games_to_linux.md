---
title: "Cost of porting major games to linux"
date: 2011-05-25
forum: The Cafe
---

### Post by Jagoly on 2011-05-25
Does anyone now roughly how much it would cost a major game studio to port one of their own games to linux? Such as betesda's oblivion. How many digets would we be talking? 4? 5? 7?

I don't have any idsea how much any sort of software development costs:confused:

---

### Post by anaconda on 2011-05-25
A lot.

unfortunately it is very expensive.

---

### Post by NovaAesa on 2011-05-25
Video games are very expensive to develop. The big games obviously cost more, e.g. GTAIV cost 100 million USD to develop while lesser current generation games cost around 10 million USD each.

Porting a game is a feat that is much easier while the game is being created. It's not easy to do after-the-fact. I'm guessing the added cost would be at the very least 5 digits (i.e. two man years work), but that's just a guess.

---

### Post by cespinal on 2011-05-25
> **Jagoly said:**
> Does anyone now roughly how much it would cost a major game studio to port one of their own games to linux? Such as betesda's oblivion. How many digets would we be talking? 4? 5? 7?

I don't have any idsea how much any sort of software development costs:confused:

over 9000 rupees

---

### Post by jhonan on 2011-05-25
> **cespinal said:**
> over 9000 rupees
:lolflag:

---

### Post by eriktheblu on 2011-05-25
I suspect one of the big obstacles is that even if a game company wanted to port it, their tools (engines, libraries, drivers, etc.) are unavailable.

---

### Post by 3Miro on 2011-05-25
> **Jagoly said:**
> Does anyone now roughly how much it would cost a major game studio to port one of their own games to linux? Such as betesda's oblivion. How many digets would we be talking? 4? 5? 7?

I don't have any idsea how much any sort of software development costs:confused:

They should just recompile the entire thing against the wine libraries. Oblivion already works great with wine, recompiling shouldn't be too much work and in the end, they will have a native app.

Alternatively, large gaming studios can contribute to wine to make sure their own games run well. This will take small effort and in the end they can provide their own variations of wine. For example, Blizzard can make contributions to the wine code to make sure their games run well, then they can take that snapshot and release blizwine, which will be fine tuned and adjusted to play all Blizzard games out of the box.

In the late 90's there was a company (Loki games) that used to do something similar. Ultimately they were selling their "Loki installers" so they couldn't stay in business. Nobody wanted to pay 40 - 50 USD for Heroes of Might and Magic III only to then pay another 20 - 30 USD to be able to play it on Linux. Loki Games should have made their money from the game studios for the ability to sell on another platform.

---

### Post by andamaru on 2011-05-25
Double posted like an idiot

---

### Post by andamaru on 2011-05-25
> **NovaAesa said:**
> Video games are very expensive to develop. The big games obviously cost more, e.g. GTAIV cost 100 million USD to develop while lesser current generation games cost around 10 million USD each.

Porting a game is a feat that is much easier while the game is being created. It's not easy to do after-the-fact. I'm guessing the added cost would be at the very least 5 digits (i.e. two man years work), but that's just a guess.

I don't think it's that expensive, Grand theft auto iv had one programmer on cross platform development and UT2004 had one or two people. If a game is already running on console's and windows adding a few more ports aren't as expensive.

---

### Post by frankbooth on 2011-05-25
Wherethere it's expensive or not, I have no idea. But since nobody is doing it, I guess it's not profitable enough.

This makes me want to add a follow up question though...

How much workwould be needed for a company to make their game run smooth through Wine?
And what stops game developers from doing this?

---

### Post by psusi on 2011-05-25
It depends entirely on how it was written.  If it is using Windowsisms like DirectX, then it can be rather expensive.  If it is already using OpenGL, then it can be pretty easy.

> **3Miro said:**
> They should just recompile the entire thing against the wine libraries. Oblivion already works great with wine, recompiling shouldn't be too much work and in the end, they will have a native app.

You don't "compile against the wine libraries".  The wine libraries are the Windows libraries.

---

### Post by HoKaze on 2011-05-25
> **psusi said:**
> 
You don't "compile against the wine libraries".  The wine libraries are the Windows libraries.
Uh, not quite: [http://www.winehq.org/site/winelib](http://www.winehq.org/site/winelib)
"Theoretically, any Win32 app should be compilable out of the box under Wine.   This, of course, is not the case. We have incompatible headers, and a bunch   of other problems described in    [Winelib User's Guide]("http://www.winehq.org/docs/winelib-guide/index").   **A good way to fix these is to try to compile applications for which we   have the source under Winelib.**     "

Of course, it's not as simple as simply getting these libraries and re-compiling as at the very least you'll have to make changes to your makefile and in some (rare) cases some of the code will still need to be rewritten.
In theory though it should be fairly trivial to do, but this still won't work as well as if they had been written for Linux in the first place and it also means that the compiled program will only work with one specific version of Wine unless I'm mistaken.

---

### Post by JDShu on 2011-05-25
It depends a lot on the game in question too. Oblivion or other DirectX game would be really expensive since the underlying library is completely different. Something like Starcraft 2, which has already been ported to OpenGL, I am guessing would be cheaper.

---

### Post by speedwell68 on 2011-05-25
Surely it is not only the cost of developing the game to run on a Linux platform, it is the cost of supporting it too and as most Linux distros are very different, support would be an utter minefield.

---

### Post by psusi on 2011-05-25
> **HoKaze said:**
> Uh, not quite: [http://www.winehq.org/site/winelib](http://www.winehq.org/site/winelib)
"Theoretically, any Win32 app should be compilable out of the box under Wine.   This, of course, is not the case. We have incompatible headers, and a bunch   of other problems described in    [Winelib User's Guide]("http://www.winehq.org/docs/winelib-guide/index").   **A good way to fix these is to try to compile applications for which we   have the source under Winelib.**     "

How is that quote at all relevant?  That quote just says their headers are not 100% correct.

> **HoKaze said:**
> Of course, it's not as simple as simply getting these libraries and re-compiling as at the very least you'll have to make changes to your makefile and in some (rare) cases some of the code will still need to be rewritten.
In theory though it should be fairly trivial to do, but this still won't work as well as if they had been written for Linux in the first place and it also means that the compiled program will only work with one specific version of Wine unless I'm mistaken.

This still gives you a Windows .exe that still needs the windows or wine dlls to run, just as if you had compiled it with VS, not a native Linux binary.

---

### Post by 3Miro on 2011-05-25
> **psusi said:**
> How is that quote at all relevant?  That quote just says their headers are not 100% correct.

This still gives you a Windows .exe that still needs the windows or wine dlls to run, just as if you had compiled it with VS, not a native Linux binary.

Compiling with winelib does create a Linux executable that depends on wine Linux libraries. It is not as efficient as writing everything with Linux in mind in the first place, but it beats using a windows executable with wine.

Wine doesn't come with windows .dll files, wine comes with its own implementation of DirectX and the windows API. With wine you can use windows .dll files, but it is recommended that you do that only as a last resort. Default wine doesn't come with windows .dll files and the goal of wine is to make it so that you don't need windows .dll files.

What I think would be the best and cheapest way for companies to do right now: 

Wine has the majority of windows API already implemented. If a program doesn't run with wine, it is usually something small. Companies can contribute to wine with small changes to code and help with testing. In the end, companies can get wine to work with their own games and then they can distribute snapshots of wine that are "officially supported and guaranteed to work". This is the smallest cost to developers, contributes and improves wine (with the contributions all windows programs will run better) and the companies can still sell their games to the Linux community. I have a similar snapshot of wine 1.1.37 that plays Oblivion perfectly with light effects and mods and everything.

---

### Post by psusi on 2011-05-25
> **3Miro said:**
> Compiling with winelib does create a Linux executable that depends on wine Linux libraries.

Are you sure?  I couldn't find anything indicating that.  I suppose that you could do it that way, though I don't see why you would want to, since you are still running a windows program with wine.

> **3Miro said:**
> Wine doesn't come with windows .dll files, wine comes with its own implementation of DirectX and the windows API.

Of course; it is a reimplementation of the windows dlls.  The application does not know or care whether it links to the real windows dll or the wine replacement at run time.  You can link to either one at compile time, and at runtime it will use whichever one is on the system.

---

### Post by forrestcupp on 2011-05-25
> **3Miro said:**
> They should just recompile the entire thing against the wine libraries. Oblivion already works great with wine, recompiling shouldn't be too much work and in the end, they will have a native app.

This is a great idea. But like HoKaze mentioned, you're probably still going to have to do some rewriting. And after that, you're still going to have to do a lot of testing specifically for that port.

Most game companies just don't care enough about Linux to put any work at all into it. They're not going to make much money comparatively, so why take the time to even think about it? The truth is that in most genres, computer gaming is massively declining and shifting to the console. Gaming companies aren't even making as much money in Windows anymore, so why would they invest in Linux? The console is where it's at now, and buying a powerhouse PC specifically for gaming is a huge waste of money nowadays.

---

### Post by 3Miro on 2011-05-25
> **forrestcupp said:**
> 
Most game companies just don't care enough about Linux to put any work at all into it. They're not going to make much money comparatively, so why take the time to even think about it? The truth is that in most genres, computer gaming is massively declining and shifting to the console. Gaming companies aren't even making as much money in Windows anymore, so why would they invest in Linux? The console is where it's at now, and buying a powerhouse PC specifically for gaming is a huge waste of money nowadays.

Have you played Dragon's Age: Origins? They had both console and PC versions, however, the PC version was notably better. Better interface (mouse + keyboard), better resolution, better camera.

It is true that a host of games is made for consoles, however, most of those are what I call "zerg" games, just numbers no quality. There are fewer PC titles, but they are usually much better quality. There is money to be made on the PC market and it will be so for quite some time to come. I don't see consoles really taking over until they start coming with mouse + keyboard in addition to the regular controllers (how would you play Starcraft without a mouse or a keyboard).

---

### Post by forrestcupp on 2011-05-25
> **3Miro said:**
> Have you played Dragon's Age: Origins? They had both console and PC versions, however, the PC version was notably better. Better interface (mouse + keyboard), better resolution, better camera.

It is true that a host of games is made for consoles, however, most of those are what I call "zerg" games, just numbers no quality. There are fewer PC titles, but they are usually much better quality. There is money to be made on the PC market and it will be so for quite some time to come. I don't see consoles really taking over until they start coming with mouse + keyboard in addition to the regular controllers (how would you play Starcraft without a mouse or a keyboard).

For one thing, I said *most* genres. Things like MMORPGs and simulations will always be better on the computer.

Also, I wasn't talking at all about the quality of games. PC games usually are higher resolution and look sharper. After playing Halo: Combat Evolved on my computer, I wasn't that impressed with Halo 3's visuals on the 360. I was talking about sales. Sales are what drives companies to make games. For *most* genres, the sales are shifting massively toward the console and away from the PC.

---

### Post by Legendary_Bibo on 2011-05-25
> **3Miro said:**
> Have you played Dragon's Age: Origins? They had both console and PC versions, however, the PC version was notably better. Better interface (mouse + keyboard), better resolution, better camera.

It is true that a host of games is made for consoles, however, most of those are what I call "zerg" games, just numbers no quality. There are fewer PC titles, but they are usually much better quality. There is money to be made on the PC market and it will be so for quite some time to come. I don't see consoles really taking over until they start coming with mouse + keyboard in addition to the regular controllers (how would you play Starcraft without a mouse or a keyboard).

Consoles have a lot more quality games. I have yet to come across a PC game that I've enjoyed more than any console games. I've only liked one PC version of a game because of KB/M and that was Team Fortress 2. I've never really played a console FPS and thought it would be more fun on a PC.

---

### Post by 3Miro on 2011-05-25
> **forrestcupp said:**
> For one thing, I said *most* genres. Things like MMORPGs and simulations will always be better on the computer.

Also, I wasn't talking at all about the quality of games. PC games usually are higher resolution and look sharper. After playing Halo: Combat Evolved on my computer, I wasn't that impressed with Halo 3's visuals on the 360. I was talking about sales. Sales are what drives companies to make games. For *most* genres, the sales are shifting massively toward the console and away from the PC.

We don't disagree here. My point was that there are good popular games on PC-Windows that generate enough sales. We won't see a massive influx of "zerg" games to PC-Linux, but the big titles should sell well enough. For example, an official Blizzard support for Linux for Starcraft, WoW and Diablo with something like blizwine should be profitable. Those mostly run already, so it is a small expense and they get their foot in a sub-market that is a virtual void of commercial games.

---

### Post by forrestcupp on 2011-05-25
> **3Miro said:**
> For example, an official Blizzard support for Linux for Starcraft, WoW and Diablo with something like blizwine should be profitable. Those mostly run already, so it is a small expense and they get their foot in a sub-market that is a virtual void of commercial games.
One thing I've seen is that Linux users rally to support whoever supports them, and they're willing to pay for it. The problem is just that as gung ho as Linux users are, they still make up a very small percentage. Even if it *would* be profitable, most gaming companies perceive Linux as unprofitable. id Software is the exception to this rule.

I wish Loki were still around. They really did good work. You could get a lot of their installers for free. They weren't always perfect, but it was usually better than wine.

---

### Post by Legendary_Bibo on 2011-05-25
> **3Miro said:**
> We don't disagree here. My point was that there are good popular games on PC-Windows that generate enough sales. We won't see a massive influx of "zerg" games to PC-Linux, but the big titles should sell well enough. For example, an official Blizzard support for Linux for Starcraft, WoW and Diablo with something like blizwine should be profitable. Those mostly run already, so it is a small expense and they get their foot in a sub-market that is a virtual void of commercial games.

I was under the impression that WoW was one of the easiest games to run under Wine. Linux users seem to support themselves pretty well so these companies probably don't see a need to support people on Linux. I do remember hearing about a time when Blizzard's ban hammer banned everyone running the game on Wine (it saw them as trying to cheat), they could've told all the Wine users to get Windows and play the game on there, but instead they patched their servers to not see Wine players as cheaters, and they went through and unbanned all the Wine users. That's kind of support.

---

### Post by Legendary_Bibo on 2011-05-25
> **forrestcupp said:**
> One thing I've seen is that Linux users rally to support whoever supports them, and they're willing to pay for it. The problem is just that as gung ho as Linux users are, they still make up a very small percentage. Even if it *would* be profitable, most gaming companies perceive Linux as unprofitable. id Software is the exception to this rule.

I wish Loki were still around. They really did good work. You could get a lot of their installers for free. They weren't always perfect, but it was usually better than wine.

I remember trying to install UT2K4 under Linux and there were guides that said the same thing to get it installed for the version without the Linux installer (the one I had), it was such a headache then I came across the loki installer for it, and it basically did every step in those guides for you with just a chmod and running the script. I like loki installers.

---

### Post by 3Miro on 2011-05-25
Wow, Oblivion and other games like that do work, but they take some time to get there, i.e. it took months to get Starcraft to give decent performance. With the aid of Blizzard, Diablo III for example can be fully supported at launch.

I actually don't play Wow so I didn't know about Blizzard + wine, but it is good to see Blizzard making a smart decision.

---

### Post by Nerotriple6 on 2011-05-25
Not too expensive to make it impossible.

The bastards are just lazy... ...Sorry..
ID Software ported several of their games over to the Linux platform (Including Doom 3).. I guess it just depends on how much programming they can be bothered to do...

---

### Post by medic2000 on 2011-05-25
Guys it is not about hard to port or anything. It is just nobody knows Linux. Really myriad of people never ever even heard about it.

---

### Post by disabledaccount on 2011-05-25
> **Legendary_Bibo said:**
> I remember trying to install UT2K4 under Linux and there were guides that said the same thing to get it installed for the version without the Linux installer (the one I had), it was such a headache then I came across the loki installer for it, and it basically did every step in those guides for you with just a chmod and running the script. I like loki installers.
I have native linux UT2004 working perfectly on 10.04 64bit - installation was not so hard. The problem is (was) in original GOTY edition that came with both Windows and Linux version of game - Linux installer was broken by accident (?).

LT has LTspice simulation software that has Wine-compatybility mode and works just perfectly under latest WINE.

Game is mainly engine (which is generally platform-independant)+ set of compiled engine scripts + textures, models and sound files. Porting to linux needs rewriting of input handlers and OGL interface. Good engines can work both with OGL and DX with the same performance and set of features.

---

### Post by Legendary_Bibo on 2011-05-25
> **tomazzi said:**
> I have native linux UT2004 working perfectly on 10.04 64bit - installation was not so hard. The problem is (was) in original GOTY edition that came with both Windows and Linux version of game - Linux installer was broken by accident (?).

LT has LTspice simulation software that has Wine-compatybility mode and works just perfectly under latest WINE.

Game is mainly engine (which is generally platform-independant)+ set of compiled engine scripts + textures, models and sound files. Porting to linux needs rewriting of input handlers and OGL interface. Good engines can work both with OGL and DX with the same performance and set of features.

Yeah I have it running natively in Linux, it's just that I bought the GOTY version (with mega map pack), and it was missing the Linux installer, but it was possible to do it manually, or use the Loki installer.

---

### Post by BrokenKingpin on 2011-05-25
The short answer... a lot. Although, it really does depend on the game. If it was done in OpenGL, it would be less than if it was a DirectX game. If the game was already developed for Mac, then it would be event less, as it could just be down to packaging.

---

### Post by Bandit on 2011-05-25
> **JDShu said:**
> It depends a lot on the game in question too. Oblivion or other DirectX game would be really expensive since the underlying library is completely different. Something like Starcraft 2, which has already been ported to OpenGL, I am guessing would be cheaper.

You nailed it directly on the head.

OpenGL stuff like Quake and UT are easy and can be done by one person as most of the files are cross platform independent. Sadly so is WoW, but no dice on a Linux binary.

---

### Post by weasel fierce on 2011-05-25
There's been a few indie developers who've discussed this on blogs before. The opinion generally seems to be "very little effort, if its planned to be ported. Quite a lot, if you decide after the fact"

---

### Post by Jagoly on 2011-05-26
What API does the ps3 use? I know that it doesn't use DirectX.

---

### Post by Legendary_Bibo on 2011-05-26
> **Jagoly said:**
> What API does the ps3 use? I know that it doesn't use DirectX.

They have a OpenGL wrapper, but they have their own API.

---

### Post by medic2000 on 2011-05-29
Also Amnesia: The Dark Descent and previous games have Linux ports. You should try. Awesome game.

---

