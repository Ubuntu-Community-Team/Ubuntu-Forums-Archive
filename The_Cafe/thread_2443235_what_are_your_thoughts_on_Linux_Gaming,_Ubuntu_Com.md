---
title: "what are your thoughts on Linux Gaming, Ubuntu Community?"
date: 2020-05-13
forum: The Cafe
---

### Post by linuxloverforever on 2020-05-13
I think it's doing all right ;)

---

### Post by Perfect Storm on 2020-05-13
With steam and proton, it have become a lot easier to game on linux. Though I only buy games that runs natively and I make small videos about it: [https://youtu.be/75YQ_cwxnUM](https://youtu.be/75YQ_cwxnUM)

---

### Post by EuclideanCoffee on 2020-05-13
I have been using wine for years, but now wine comes preconfigured in various projects, and it's a lot easier. With steam pushing for Linux gaming, I haven't had an issue moving over my old video games to the newer systems. Earlier on this account, I provided a lot of wine support, but now it seems like very few people simply use wine, which is a good thing. :)

---

### Post by TheFu on 2020-05-13
I have about 20 purchased games from the 1990s and early 2000s.  Getting those working under Linux has proven to be non-trivial.

Around 2008, a friend game me a game on Steam. Guess it was a link or a 1-time offer. Never installed it anywhere. In 2008, I was still using a PS2 console and enjoying SOCOM or Ace Combat or GTA or MGS.  Never finished MGS, GTA or all the SOCOM games. 

I'd love to play a few games again, under Wine.  For a few years, I was part of the WINE volunteer support for Quicken.
[LIST]
[*]Real War (4 Generals on a LAN controlling their parts of the "world", using current, modern, military HW)
[*]Real Flight - this is an RC aircraft simulator with RC controller hardware.
[*]C&C 13-titlesReal War
[*]Half Life 5-titles
[*]MSFT Flight Sim 2002
[/LIST]

In the 2000s, I used to run a Half Life server and hosted a few LAN parties at home. This was the time of 802.11b wifi.
I've seen that different WINE front-ends have been released, but never understood them enough to see the point.  I do keep a Win7 and WinXP VM around just for fun, but haven't attempted to game in either.  The Win7 VM is for some proprietary negative scanning software, Quicken, Quickbooks, Tax and investment software. It has extremely restricted network access.

I would enjoy playing a few hours of Starflight again, from time to time, I suppose. That is a tiny MS-Dos game.  Tried to get that working 4 months ago. Before I got it working, life got in the way. That's pretty typical for most people, I suppose.  Need to try getting that working again.

---

### Post by Hwæt on 2020-05-13
It's going well. There's quite a few native releases in Steam. I haven't used Proton. DXVK almost singlehandedly makes WoW playable.

Though, I think I'd be better serviced by buying an AMD card that supports GPU passthrough and setting something up with QEMU.

---

### Post by CatKiller on 2020-05-13
> **TheFu said:**
> I'd love to play a few games again, under Wine.
[LIST]
[*]Half Life 5-titles  
[/LIST]


With the exception of the new VR one (which is due to come to Linux at some point) all the Half Life games (and the Portal games) are Linux-native.

> I've seen that different WINE front-ends have been released, but never understood them enough to see the point.

Convenience.

There are only really two that are particularly important at the moment: Lutris and Proton.

Lutris puts each application in its own prefix rather than having one big (potentially conflicted) prefix with everything in and, rather than having to find out for yourself how to make a particular thing work you can reuse the work of others: you pick whichever thing you're trying to install from a list and it automatically downloads everything you need and applies *that one weird quirk*. There's nothing that Lutris does that you *couldn't* do yourself, if you were willing to throw a bunch of time and research into every application, but you'd just be redoing work that someone else has already done.

Proton is integrated into Steam. It's open source, so you don't have to use Steam to use Proton, but they've made it part of their application so that you can buy, download, and run Windows-native games exactly as if they were Linux-native. And they've put a lot of effort into developing Mesa, Wine, DXVK, and so on. Some titles are whitelisted, so they'll show up in the store as a Linux game and Valve handles the support for them, but you can chance your arm on trying any game with Proton. [ProtonDB](https://www.protondb.com/) has everyone's compatibility reports. If you've had a game less than two weeks and played it less than two hours you can get a full refund, so there's no harm in taking a punt on something that you're interested in; if it doesn't work straight away, you can just get your money back.

---

### Post by CatKiller on 2020-05-13
> **Hwæt said:**
> Though, I think I'd be better serviced by buying an AMD card that supports GPU passthrough and setting something up with QEMU.

Things that don't work in Proton (because anti-cheat) also don't work in a VM (because anti-cheat).

---

### Post by TheFu on 2020-05-13
Steam tracks your gaming. [https://steamcharts.com/](https://steamcharts.com/)   [https://store.steampowered.com/stats/](https://store.steampowered.com/stats/)  I have ZERO interest in that. I've bought the games. Why must we give up anything else to play them?

Loaded Lutris to get C&C working. Vaguely recall that Lutris was a snap package, yet failed to work. Read lots about setting up C&C, but even with it and my retail CDs with all the license keys, the complications to get it working, assuming it would ever work, where beyond my effort level.  Manually setting up WINE would be easier.  

Heck, I should just spin up a WinXP VM and see what works well now that our PCs are 30x faster than they were in 2002.  Plus, WinXP only needs like 6GB of disk, which is less than a few snap packages.

---

### Post by CatKiller on 2020-05-13
> **TheFu said:**
> Steam tracks your gaming. [https://steamcharts.com/](https://steamcharts.com/)   [https://store.steampowered.com/stats/](https://store.steampowered.com/stats/)  I have ZERO interest in that. I've bought the games. Why must we give up anything else to play them? 

Only if you've got it set to online. You don't have to. You can just set it to offline and just play the games locally without any of the social stuff if that's what you prefer. The stats about playtime are private by default. Personally I *like* game devs knowing that people are playing their games on Linux: it shows that there's demand.

> Vaguely recall that Lutris was a snap package, yet failed to work.

Nope. Well, I'm sure it's *also* available as a snap, but they've got a PPA.

I've only tried Starcraft, and that worked with no problems. It automatically downloaded the version that was released for free and installed it, even with the silly Blizzard launcher thing. Didn't C&C and Red Alert get released for free, too?

---

### Post by TheFu on 2020-05-13
> **CatKiller said:**
> Only if you've got it set to online. You don't have to. You can just set it to offline and just play the games locally without any of the social stuff if that's what you prefer. The stats about playtime are private by default. Personally I *like* game devs knowing that people are playing their games on Linux: it shows that there's demand.

Nope. Well, I'm sure it's *also* available as a snap, but they've got a PPA.

I've only tried Starcraft, and that worked with no problems. It automatically downloaded the version that was released for free and installed it, even with the silly Blizzard launcher thing. Didn't C&C and Red Alert get released for free, too?

My desktops are running 16.04.  That brings all sorts of not-available-here issues.  Yep, 16.04 lutris doesn't have a PPA and the snap doesn't work.  Another one of the 80% of snaps that don't work when attempted.  16.04 supports snaps, just it seems the snaps aren't really self-contained as advertised. 

Feedback to devs?  Game devs know that I bought the game in 2002 or 1998 or 1993. Seems like sufficient feedback to me.  

Found about 5 WinXP CDs/DVDs today.  Just need to find one that will load into a VM. I definitely have a retail license somewhere.

There are a few games I've gotten more than my money's worth from - Starflight is one.  SOCOM, Ace Combat 4-6, definitely.  There are many others where I didn't get anywhere near my money's worth from them.  No fault of the game, at the time.  Just that I'm from the generation when you'd buy a game and have it for 50+ yrs to play, sell, loan.  Sorta like books.  I still have about 100 Atari 2600 game cartridges.  Before our last major move, I gave away the console, but not the games.  They mostly work under the emulators, though some of the keyboard/audio is off.  We are at the point where we need to keep a copy of the OS and all settings to continue playing games and hope that the kernel devs don't remove critical subsystems needed to use those programs.

Alas - definitely 1st world problems.

---

### Post by Hwæt on 2020-05-13
> **CatKiller said:**
> Things that don't work in Proton (because anti-cheat) also don't work in a VM (because anti-cheat).

I wasn't saying for anti-cheat, but rather performance and ease of use. WoW is fairly prone to random errors in WINE from patch to patch.

---

### Post by Perfect Storm on 2020-05-14
Made another gaming video today.

Torchlight 2 ofcause.
[video]https://youtu.be/BGR8qkNYTFg[/video]

---

### Post by mastablasta on 2020-05-14
it's getting better and better. the direction is really good and i hope ridiculous DRm clients are either removed or also made compatible. they are holding back some major titles.


good support for older games. i mean Far Cry 2 - i get stuttering on winxp and lag with everything set on low as well as some additional tweaks. in linux and on same PC it works fluently on medium settings. wow!

many games work out of the box in wine and work just fine with no noticeable performance penalty. so we got quite a few working. and the appetites of the kids have grown :-)

---

### Post by CatKiller on 2020-05-14
> **TheFu said:**
> My desktops are running 16.04.  That brings all sorts of not-available-here issues.  Yep, 16.04 lutris doesn't have a PPA and the snap doesn't work.  

You could start a thread about it in the Gaming & Leisure section if you wanted some help with it. 

> Feedback to devs?  Game devs know that I bought the game in 2002 or 1998 or 1993. Seems like sufficient feedback to me.  

As far as they know, you bought those games for Windows, only play them on Windows, and you are not part of a market for non-Windows games because you like Windows so much. Whereas if you buy games through the Linux Steam client it counts as a Linux sale and the optional playtime statistics show that people are playing the game on Linux.

It's very easy for a game developer to think "there is no market for Linux games, so I shouldn't bother learning how to make one." You can show them that isn't true.

---

### Post by sulton on 2020-05-29
I think steam, Valve are going in the right direction

---

