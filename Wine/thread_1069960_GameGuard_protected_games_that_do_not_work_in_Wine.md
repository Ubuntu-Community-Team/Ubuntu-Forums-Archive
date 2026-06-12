---
title: "GameGuard protected games that do not work in Wine"
date: 2009-02-14
forum: Wine
---

### Post by cogadh on 2009-02-14
nProtect GameGuard from INCA Internet is an anti-cheating application that is included in many online games (see list below). It accomplishes its protection features by use of a Windows device driver. Since [Windows drivers do not work in wine]("http://wiki.winehq.org/FAQ#head-8021e00ae87d4fbfb607739af82bdb621b9d9366"), GameGuard cannot function with the games it is designed to protect and the game itself will not run in Wine without it. 

PC Games that are known to use GameGuard protection:
[list]
[*]2Moons
[*]9Dragons
[*]Albatross18
[*]Asda Story
[*]BOTS
[*]Cabal Online
[*]Cal Ripken's Real Baseball
[*]Counter-Strike Online (Asian market only)
[*]Cronous
[*]Dance! Online
[*]Darkeden
[*]Digimon RPG
[*]Dragonica Online
[*]Drift City
[*]Dungeon & Fighter
[*]Emil Chronicle Online
[*]Exteel
[*]FlyFF
[*]GameCampus.com - All games from this site use GameGuard
[*]Gersang
[*]Grand Chase
[*]GunBound
[*]Gunster
[*]GunZ: The Duel
[*]Heat Project
[*]Hyper Relay
[*]Legend of Mir 3
[*]Lineage II
[*]Lunia
[*]Monster Hunter Frontier
[*]Mu Online
[*]Navy Field
[*]OZ World
[*]Pangya
[*]Phantasy Star Online Blue Burst
[*]Phantasy Star Universe
[*]Priston Tale
[*]Ragnarok Online
[*]Rakion
[*]Rappelz
[*]Ran Online
[*]Rohan Online
[*]ROSE Online
[*]Seal Online
[*]Shot Online
[*]Soldier Front
[*]Sudden Attack
[*]Tales Runner
[*]The Chronicles of Spellborn
[*]Trickster
[*]Twelve Sky
[*]WolfTeam
[*]WonderKing Online (non-English versions)
[*]Xiah online
[/list]

Hackshield from AhnLab is an anti-cheat application similar to GameGuard. As such, it also does not work in Wine (though for [technically different reasons]("http://bugs.winehq.org/show_bug.cgi?id=4666")) which prevents the games it protects from also working in Wine.

PC Games that are known to use Hackshield protection:
[list]
[*]Alliance of Valiant Arms
[*]Combat Arms
[*]Crossfire
[*]Elsworld Taiwan
[*]Gunz: The Duel
[*]KalOnline
[*]Mabinogi
[*]MapleStory
[*]Point Blank
[*]Rappelz
[*]Requiem: Bloodmare/Requiem Online
[*]RF Online
[*]S4 League
[*]Shot Online
[*]Vindictus
[*]WonderKing Online (English version) NOTE - As of June, 2010 this game has been reported to work in Wine, despite still having HackShield. If anyone can confirm that it is indeed working, please reply in this thread.
[*]Warrock
[/list]

You may be able to get some of these games running using a virtual machine like VMWare or VirtualBox, but they will likely never work in Wine as long as they continue to use GameGuard and Hackshield. If anyone knows of any other games that may be using GameGuard and/or Hackshield, please let me know and I will update the list. Additionally, if anyone knows of games currently on the list that no longer use these protection schemes and now do work in Wine, also let me know so that I can remove them.

**NOTE: Due to the questionable legality of private servers, please do not bring them up in this thread.** The information in this post really only applies to the use of these games on official servers.

---

### Post by Ferrat on 2009-02-14
Well this list is wrong according to the appdb 
[Silkroad Online]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5391") is platinum status so there are only some GameGuard games that doesn't work....

---

### Post by cogadh on 2009-02-14
Hence why asked for people to post corrections to the list. The list is simply all the games I could find that have (or possibly had) GameGuard and should not work because of that. Its entirely possible that the sources I used were inaccurate about whether or not the game still uses GG. According to [GameGuard's own website]("http://gameguard.nprotect.com/company.html"), Silkroad added it back in 2005, but the game has changed a lot since then, so it may not be using it anymore.

---

### Post by hikaricore on 2009-02-14
I've stuck and unlocked this thread.
Do not ask unrelated questions or post useless junk here.
If I see a bunch of you who can't read/follow instructions I will close it again.

That said if you have further info to add which is relevant to this topic please by all means post away.

---

### Post by binbash on 2009-02-15
Thanks for the sticky! 

Lineage II works with ULL Launcher, [http://www.lotrolinux.com/ULL/](http://www.lotrolinux.com/ULL/) , tested with private servers but i don't know the official one.

---

### Post by cogadh on 2009-02-15
I added a note for that, but if anyone can confirm that it will definitely work with the official servers, it would be helpful.

Also, just to repeat what is at the end of the OP, private servers are a legal grey area and shouldn't really be discussed here. Consider them as forbidden on the forums as the discussion of how to obtain and use cracked executables for games or how to obtain pirated copies of games.

---

### Post by d3drocks on 2009-02-21
I played Shaiya about a month ago without issue in wine. but it was installed on a windows partition, and i exicuted it from its partition in ubuntu.

maybe that will cause something different? I dont know, but it worked.

EDIT: im a little confused as to why counter-strike is on the list.
it uses VAC (Valve Anti Cheat) which is included in steam. I'm pretty sure it uses that system world wide. (I also dont see it on the Nprotect website. I may have missed it though.)

---

### Post by Bensky on 2009-02-21
> **d3drocks said:**
> I played Shaiya about a month ago without issue in wine. but it was installed on a windows partition, and i exicuted it from its partition in ubuntu.

maybe that will cause something different? I dont know, but it worked.

EDIT: im a little confused as to why counter-strike is on the list.
it uses VAC (Valve Anti Cheat) which is included in steam. I'm pretty sure it uses that system world wide. (I also dont see it on the Nprotect website. I may have missed it though.)

Notice that it says "asian market only" - I assume the asian version uses GameGuard as opposed to VAC for Steam.

---

### Post by cogadh on 2009-02-21
Counter-Strike Online is basically a remake of Counter-Strike: Condition Zero that is specifically for the Asian market. It does not actually use Steam as you and I know it (it has a custom Steam-based interface) and does definitely have GameGuard protection.

In regards to Shaiya, its inclusion on the list is due to the information on WineHQ's Appdb, which states that you need to use a GameGuard remover to run the game. If that has changed, can someone please confirm that so I can remove it from the list.

---

### Post by d3drocks on 2009-02-22
> **cogadh said:**
> Counter-Strike Online is basically a remake of Counter-Strike: Condition Zero that is specifically for the Asian market. It does not actually use Steam as you and I know it (it has a custom Steam-based interface) and does definitely have GameGuard protection.

In regards to Shaiya, its inclusion on the list is due to the information on WineHQ's Appdb, which states that you need to use a GameGuard remover to run the game. If that has changed, can someone please confirm that so I can remove it from the list.

ok thanks for clearing that up.

---

### Post by Funnnny on 2009-02-24
You should add some game using HackShield, it's similar to GameGuard and Wine can not run them too

---

### Post by cogadh on 2009-02-24
> **Funnnny said:**
> You should add some game using HackShield, it's similar to GameGuard and Wine can not run them too
I know very little about Hackshield and I'm only aware of a handful of games that use it. Do you know of any sources that might help with building the list?

---

### Post by ryuchao009 on 2009-03-07
I don't know a lot about wine, but wouldn't be possible to put copy the .dll files that GG needs from a working windows install and just put them into \Winows in wine?

---

### Post by buldozerceto on 2009-03-16
Does this means that it won't run in virtual pc?

---

### Post by cogadh on 2009-03-16
Not necessarily. Gameguard and Hackshield should have no problems running in a virtual machine, however, since most virtual machine software apps do not support accelerated 3D graphics, the games still might not work.

---

### Post by Chopes on 2009-03-21
> **cogadh said:**
> Not necessarily. Gameguard and Hackshield should have no problems running in a virtual machine, however, since most virtual machine software apps do not support accelerated 3D graphics, the games still might not work.
Do you know which ones do indeed support accelerated 3d graphics? The game I am trying to get to run is Shot-Online which is a very non-graphic intensive game, oldschool even. I was wondering which virtual machine client would be best to use with this game. Also I was wondering is progress able to be made with this gameguard situation or is this the best we can hope for?

---

### Post by hikaricore on 2009-03-21
> **Chopes said:**
> Do you know which ones do indeed support accelerated 3d graphics? The game I am trying to get to run is Shot-Online which is a very non-graphic intensive game, oldschool even. I was wondering which virtual machine client would be best to use with this game. Also I was wondering is progress able to be made with this gameguard situation or is this the best we can hope for?

You can find this information elsewhere without cluttering up this thread.
Please only post if you have something to add to the topic.

---

### Post by HiddenDev on 2009-05-05
Maple Story Is No Longer A Game Guard File. Its HackSheild

---

### Post by cogadh on 2009-05-05
Fixed. Also removed Mabinogi from the GameGuard list, since it also no longer uses it.

---

### Post by Pantalaimon on 2009-06-20
To my knowlege the game Maple Story uses GameGuard protection, and will not work under wine.

---

### Post by prions on 2009-06-20
They recently switched to hackshield.

---

### Post by cogadh on 2009-06-21
Which also doesn't work in Wine (as indicated in the OP)...

---

### Post by CompizDoDo on 2009-07-16
this sucks most good games use gameguard!

---

### Post by 569874123 on 2009-07-21
Same problem with Xtrap...games like Sword of the new world, neosteam, cabal and more r unplayable on linux :(

---

### Post by Darkaiser on 2009-08-06
Special Force are using GameGuard also

---

### Post by kazuya on 2009-08-07
Guys, you are going about it the wrong way. For guys that love those asian rpg games like 2moons, etc. You really should try to play their p-server equivalents.  You can eneter in google: dekaron p-server..

I playe fussion dekaron. It runs fine in linux/ubuntu in my case with wine. Speed could be better, but all works.  Why? There is no gameguad rootkit.


Try and comment.

---

### Post by hikaricore on 2009-08-07
> **kazuya said:**
> Guys, you are going about it the wrong way. For guys that love those asian rpg games like 2moons, etc. You really should try to play their p-server equivalents.  You can eneter in google: dekaron p-server..

I playe fussion dekaron. It runs fine in linux/ubuntu in my case with wine. Speed could be better, but all works.  Why? There is no gameguad rootkit.


Try and comment.

Please don't discuss private servers on UF.
In most cases they're in a legal grey area and we don't need that kind of thing here.
We're all fully aware that most can be hacked and played outside of this standard but lets keep if off the forums.
The games being discussed are in their original form on proper servers.

---

### Post by Book4567 on 2009-08-10
exteel (a ncsoft game) doesnt work on wine and it uses gameguard
EDIT: i see you have it on your list oops

---

### Post by paks.dreamer on 2009-08-20
nProtect GameGuard is definitely hindering Dragonica Online from running correctly in Wine.

I can only get into it through win98 (GG gives an error, but then bypasses and opens the client), but then the sprites are incomplete, and it crashes most of the time.  I feel that replicating a newer version of windows would run the game itself much more effectively, if only I could get past the Guard.. :/

---

### Post by liamiscool on 2009-08-21
what happens if you deleate hack sheild on Maplestory?:confused:

---

### Post by hikaricore on 2009-08-21
> **liamiscool said:**
> what happens if you deleate hack sheild on Maplestory?:confused:

It doesn't work that way.
Please stop using this thread to ask questions, it is here as an information resource not for other nonsense.

---

### Post by hectic1 on 2009-09-07
there are ways too bypass gameguard some pple do this to play games on linux i know this cause quite alot of pple run gunz online on linux and this is what they do but don't ask me how cause i dunoo =_=

---

### Post by rs_man on 2009-10-01
please delete.

---

### Post by jperez on 2009-10-05
Another game that's been out for only a year that uses GameGuard is Tales Runner.  I've tried it and it was a no go.

*sigh*

Jesse~

---

### Post by Dimitree on 2009-10-22
Emil Chronicle Online uses GameGuard also :frown:
I want to switch to Ubuntu 9.10 with free cloud and all other goodies : (((
If only this game worked : (

---

### Post by dazevedo on 2009-11-05
Shaiya no longer uses GameGuard as of last nights patch ( 11-5-09 )

---

### Post by KaoriKandiez on 2009-12-02
Pretty sure Rakion isn't using Gameguard anymore, too. 
:p

---

### Post by yanom on 2009-12-07
Warrock, B/C it uses hackshield

> I want to switch to Ubuntu 9.10 with free cloud and all other goodies : (((
What exactly is a cloud? Have heard a lot about them...

Oh ya, you could dual boot...

---

### Post by Bwathke on 2009-12-15
I ran Rohan for a few days and it worked like a charm but then GameGuard was download an update and everything started messing up on me :/ From then on it dosent work.

---

### Post by Jguy on 2009-12-16
Ragnarok Online (as far as iRO and Private servers go) works. My pserver client works just fine using GameGuard.

---

### Post by Rokit_Armor on 2010-01-05
z8 games Crossfire uses hackshield now

---

### Post by Bwathke on 2010-01-21
Im testing A.V.A right now but its not looking good so far :(

Everything goes fine with ijji reactor/optimizer then GameGuard tries to authenticate and it all crashes. So add A.V.A to the list.. Too bad the game looked pretty neat.

---

### Post by _h_ on 2010-03-25
I really wish GameGuard would get on to possibly get a fix for this, allowing it the ability to run in Wine.

I loved playing FlyFF when I was on Windows, but sadly now I can't play it anymore. Although from the Wine AppDB the private server clients supposedly work, haven't tested it yet.

---

### Post by jaceleon on 2010-03-25
I also wanted to play Elsword Taiwan on Ubuntu, but I can't seem to determine how can I make Hackshield work with this. Is there a way to run the game without virtualization?

---

### Post by _h_ on 2010-03-25
> **jaceleon said:**
> I also wanted to play Elsword Taiwan on Ubuntu, but I can't seem to determine how can I make Hackshield work with this. Is there a way to run the game without virtualization?

Doesn't look like it, only viable solution is dual booting Windows. Maybe we should make a petition to GameGuard about this issue.

---

### Post by Shadow troup on 2010-05-03
[COLOR=DarkOrange]Hackshield is a pain, I wish I could just run Wine and be done with it.   But I have to try a huge proses to start Mabinogi, which I have not figured  out yet.[/COLOR]

---

### Post by jperez on 2010-05-04
-EDITED-

Alrighty then

Jesse~

---

### Post by cogadh on 2010-05-04
> **cogadh said:**
> 
**NOTE: Due to the questionable legality of private servers, please do not bring them up in this thread.** The information in this post really only applies to the use of these games on official servers.
Please do not use this thread to discuss potentially illegal uses of software. Ubuntu doesn't need that kind stuff on their forums.

---

### Post by Zato-1 on 2010-06-16
You can remove WonderKing from the list. I got it to work.
Search it on winehq, i posted it there :)

---

### Post by cogadh on 2010-06-17
Are you using the English version? That's the only one that actually has HackShield.

---

### Post by Zato-1 on 2010-06-18
> **cogadh said:**
> Are you using the English version? That's the only one that actually has HackShield.

Yes, i do. Its European version tho.. And it does have a HackShield

---

### Post by cogadh on 2010-06-19
Then I'd really like to know how you pulled it off (your AppDB entry didn't offer any specifics). HackSHield still doesn't and probably never will work in Wine (due to the nature of how it works), so either the game has stopped using HackShield or you did something to get around it, possibly without realizing it. Are you playing the game on the official public servers, or one of the "less-than-legal" private servers?

---

### Post by Zato-1 on 2010-06-20
> **cogadh said:**
> Then I'd really like to know how you pulled it off (your AppDB entry didn't offer any specifics). HackSHield still doesn't and probably never will work in Wine (due to the nature of how it works), so either the game has stopped using HackShield or you did something to get around it, possibly without realizing it. Are you playing the game on the official public servers, or one of the "less-than-legal" private servers?

I haven't done anything really.. I just installed the game and played it. When i start the game i see the HackShield window pops up and its loading, after that the game starts.
And yes i am playing on official European server. Here is the link to EU site [http://www.wonderking.co.uk/](http://www.wonderking.co.uk/)

---

### Post by Funnnny on 2010-06-20
Look promising, I think the game integrated badly with HackShield. So while HS failed to start, the game still running thou

---

### Post by cogadh on 2010-06-21
I think for now I will leave it on the list, since it does still have HackShield, but I will note that it has been reported to work anyway. If we could get a secondary confirmation that it works, I'd feel more comfortable removing it from the list. If it is just bad HackShield integration, all it might take is a forced client update to correct the issue and the game will be right back where it was.

---

### Post by quequotion on 2010-07-03
Isn't nProtect just a scam anyway?

I find it really odd that there's no detailed documentation on how exactly their software works.

In addition, their wikipedia page is an obvious promo and looks suspicious.

---

### Post by cogadh on 2010-07-04
The company nProtect is not a scam at all and their product GameGuard is no more of a scam than PunkBuster is, or any other "anti-cheat" application. There's no detailed documentation on it because if they told everybody how they prevent cheating, then the cheaters would just find a way to work around it (not that is all that difficult to work around it anyway). Additionally, I think they are well aware that if people actually knew how their software does what it does, they might not be too happy.

---

### Post by pudgypaw on 2010-08-30
CrossFire MMOFPS has switched from GameGuard to XTrap

Does NOT currently work natively under wine or linux, but does under a properly configured VMWare Player.

Configure with:
svga.vramSize = 268435456
monitor_control.restrict_backdoor = "true"
isolation.tools.getPtrLocation.disable = "true"
isolation.tools.setPtrLocation.disable = "true"
isolation.tools.setVersion.disable = "true"
isolation.tools.getVersion.disable = "true"
monitor_control.disable_directexec = "true"

---

### Post by Jinxzs on 2010-09-22
i can play Flyff but not with the Gameguard thing.

Some private servers dont have gameguard...

---

### Post by Shalmainia on 2010-10-04
I wish I would have found this list prior to wasting my time downloading Rohan, Global version.
On a side-note, Requiem: Momento Mori doesn't seem to have a hackguard but it does crash when you log your character into the server, something about microsoft visual c++ runtime library runtime error, quite the pain in the backside.

---

### Post by The_Accursed_One on 2010-11-02
So I know this is probably a stupid question but why can't GameGuard/HackShield be developed to work with Linux/Mac OS? Could Wine be developed some way to emulate the Windows drivers needed to run the said software?



This may be an unrelated question but seems like it might somewhat fit: Is there anyway you could run a virtual box to run these games and get around the problem altogether?

---

### Post by cogadh on 2010-11-02
They probably could be engineered to work with Linux and other OSes, but that is up to INCA Internet and Ahn Labs to decide to do that. As for Wine, the problem is not emulating other drivers, the problem is GameGuard (and to some extent HackShield) actually ARE drivers. Drivers require kernel mode access while Wine only runs in user mode and that is not going to change. Allowing Wine kernel mode access would be potentially very harmful to your system, hence why it is specifically designed to not do that.

A virtual machine running Windows could be used to get around these problems and many people actually do that, but not all virtual machines support the 3D acceleration necessary for some of these games and the ones that do support it are still a bit buggy.

---

### Post by The_Accursed_One on 2010-11-03
Hmm. Okay. Thanks. I was just wondering because it seemed like everyone was addressing the issue of why it wouldn't work instead of how to fix it. If I knew anything about coding I'd offer my help to engineer it to work with Ubuntu but sadly I'm just some random teenager who knows nothing in the slightest about coding besides some exposure to some Visual BASIC.

And I understand now about the drivers. Makes sense to make sure it doesn't access the kernel. And it would be too much of a risk to give it the option to do so in advanced settings too so yeah. All understandable.

And the whole deal about Virtual machines could be interesting to develop upon. Example: Make a virtual box type deal thats built specifically for gamers on systems that do not support certain games. Interesting...

---

### Post by aliasxerog on 2010-11-20
Has anyone tried to make a proper work around for GameGuard?

---

### Post by AngelDE98 on 2011-01-03
S4 League ( Alaplaya ) has HackShield or something ... I do not play it anymore but I remember it used HackShield .

---

### Post by cogadh on 2011-01-03
It does indeed use HackShield. Added to the list.

---

### Post by Bernie Gallagher on 2011-02-06
> **cogadh said:**
> **NOTE: Due to the questionable legality of private servers, please do not bring them up in this thread.** 

I'd just like to comment on the above note.  Private servers may, indeed, be illegal to run, being a form of copyright infringement.  But there's that little thing called the First Amendment.  In the USA, at least, it's perfectly legal to DISCUSS private servers as long as you don't actually run one (other countries, such as Canada, England, Australia, etc. also have similar protections of freedom of speech).  So go ahead and freely discuss private servers, people.

---

### Post by cogadh on 2011-03-13
> **Bernie Gallagher said:**
> I'd just like to comment on the above note.  Private servers may, indeed, be illegal to run, being a form of copyright infringement.  But there's that little thing called the First Amendment.  In the USA, at least, it's perfectly legal to DISCUSS private servers as long as you don't actually run one (other countries, such as Canada, England, Australia, etc. also have similar protections of freedom of speech).  So go ahead and freely discuss private servers, people.
There is no such thing as free speech on a privately owned forum such as this. Free speech on the internet means you are allowed to start your own website and discuss whatever you want there, not discuss whatever you want on someone else's website. Also, the discussion of private servers often leads to telling people where and how to find/use private servers, which opens Ubuntu up to liability they don't need. This is the same reason that other legal grey areas, like copy protection cracks are verboten topics on Ubuntu forums. 

DO NOT "go ahead and freely discuss private servers", the mods will simply delete any posts of that nature anyway.

---

### Post by XsheepX on 2011-03-15
I would like to add that Vindictus also uses Hackshield.

---

### Post by synclicious on 2011-03-17
what about clubaudition / auditionsea / audition ayodance?

---

### Post by cogadh on 2011-03-18
> **XsheepX said:**
> I would like to add that Vindictus also uses Hackshield.
Added, thanks!

> **synclicious said:**
> what about clubaudition / auditionsea / audition ayodance?
Are you asking if those use GameGuard/Hackshield or are you asking why they aren't on the list? The answer to both is the same: I don't know if they use either anti-cheat system.

---

### Post by gnunoob on 2011-04-11
Heroes in the Sky, a gamescampus.com game, should be added to the list. Actually every game from Games Campus is a no go in Wine, even lastest dev version 1.3.17, with standard install, PlayOnLinux, Cedega Winetricks, nothing works. 

Gameguard is actually setup as a service in Windows, I'm assuming that there is a way to install a service in Wine? That will be step 1 to fixing this. That gameguard.des file and I think some other file too need to be registered services to do their jobs so until that can happen, no Gameguard in Linux :(

---

### Post by cogadh on 2011-04-11
> **gnunoob said:**
> Heroes in the Sky, a gamescampus.com game, should be added to the list. Actually every game from Games Campus is a no go in Wine, even lastest dev version 1.3.17, with standard install, PlayOnLinux, Cedega Winetricks, nothing works. 

Gameguard is actually setup as a service in Windows, I'm assuming that there is a way to install a service in Wine? That will be step 1 to fixing this. That gameguard.des file and I think some other file too need to be registered services to do their jobs so until that can happen, no Gameguard in Linux :(
The service thing is only part of the problem. GameGuard itself is actually a device driver in Windows and Windows device drivers will never work in Wine.

Thanks for the list additions, I'll edit them in shortly.

---

### Post by darkflame666 on 2011-05-25
Well, to add to the list and edit the second post in the topic, Silkroad Online (JoyMax) is running Hackshield now and as far as I can tell is no longer supported

---

### Post by Why-Fi on 2011-06-18
AirRivals/Ace Online/Phi Doi (all localized versions of it) use HackShield and do not work in WINE.

4Story/Gates of Andaron also uses HackShield (Pro version).

---

### Post by Elmseeker on 2011-07-01
> **Why-Fi said:**
> AirRivals/Ace Online/Phi Doi (all localized versions of it) use HackShield and do not work in WINE.

4Story/Gates of Andaron also uses HackShield (Pro version).

Actually there is a guide on the Air Rivals forums on getting it working in wine, it does work.

---

### Post by Mr Pleh on 2013-02-18
Hey, thank you very much for this list. I can't tell you the number of sites I've already gone through that were almost no help to me at all in my problem.

You should add pretty much any games made by Nexon to your Hackshield list, since I'm pretty sure they use it in all their online games. 

[LIST]
[*]Dragon Nest
[*]Navy Field 2
[*]MapleStory
[*]Sudden Attack
[*]Combat Arms
[*]Mabinogi
[*]Vindictus
[*]Atlantica
[*]Dungeon Fighter Online
[/LIST]

I know some of these have already been mentioned

---

