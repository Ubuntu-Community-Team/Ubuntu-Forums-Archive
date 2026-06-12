---
title: "PlayonLinux or Crossover Games?"
date: 2010-07-26
forum: Wine
---

### Post by xpowerfulxx on 2010-07-26
I'm trying to decide which one to get. PlayOnLinux is good since it has a list of built in games to install, but Crossover Games can install them from the .exe. Which should I get, or should I get them both?

---

### Post by Arthur_D on 2010-07-26
Well, PlayonLinux is free, so why not get that and see if it fills your need, and if not, buy the Crossover suite?

---

### Post by Sticky_Bit on 2010-07-26
Crossover is definitely worth it, if you have the money.

---

### Post by hikaricore on 2010-07-26
POL is simply a Wine frontend.
I suggest you use Wine unless you absolutely need Crossover.

---

### Post by cogadh on 2010-07-27
^^ What he said. You don't actually get anything from POL that you can't already get from from Wine itself, but POL does sometimes make it a bit easier (though not much easier, IMO). Crossover is somewhat similar in this respect, except for the fact that the money you pay to Crossover directly supports the further development of Wine and gives you professional technical support (if that is the kind of thing you need).

---

### Post by cwwilson721 on 2010-07-29
> **xpowerfulxx said:**
> I'm trying to decide which one to get.[COLOR=Teal] PlayOnLinux is good since it has a list of built in games to install[/COLOR], but [COLOR=Red]Crossover Games can install them from the .exe[/COLOR]. Which should I get, or should I get them both?

Hmmm...

Let's start with the basics, and then go to the highlighted colors, and why they are SO misleading.

Both PlayOnLinux and Crossover/Cedega uses wine as their engine. wine is updated faster, quicker, and is most stable and well supported. Look at winehq.com for supported games. POL and Crossover/Cedega add stuff on to wine.

1st, PlayOnLinux(POL) is just a GUI installer for wine. POL just adds neat gizmos to a simple "wine install.exe" command line. That's ALL it does, plus adds a "easy" button to start the games. Unfortunately, wine (as installed from the repos) does the easy menu too. It adds a Wine sub menu to Applications. So, forget POL (It also is behind wine in updates)

2nd, Cedega/Crossover have you pay money for basically NOTHING. wine does what they can do, and for free, faster, and did I mention FREE? wine now has DirectX support (slow, but it works).

As for "[COLOR=Teal] PlayOnLinux is good since it has a list of built in games to install"[COLOR=Black], all it does is provide links to downloadable games, or asks you to insert the cd/dvd. You can do the same with wine.

As for "[/COLOR][/COLOR][COLOR=Red]Crossover Games can install them from the .exe"[COLOR=Black], wine does that already. Just make sure the installer file is executable (permissions in properties), open a terminal, cd to the directory, and type "wine installer.exe"(or whatever the file name is)

Neither is a very compelling reason to use those GUIs over plain ol' wine. Unless you like to pay money.
[/COLOR][/COLOR]

---

### Post by Nico0020 on 2010-08-01
POL is useless as it is just a frontend to something that is already simple.  

Crossover Linux is very important to the WINE project.  Without the crossover team, much of what you see in WINE would not exist.  If you have the extra cash to spend and need expert level support, give crossover a try.  I used to have a sub to crossover, great program, but now I am a broke near graduate student who hasn't had a full time job in over a year, so I stick to WINE.

---

### Post by Tweak42 on 2010-11-15
Few distinctions missing:  
[LIST]
[*]Transgaming/Cedega is not Crossover, and has distanced itself from the wine project developing their own codebase.
[*]Codeweavers/Crossover employs some of the wine developers so subscribing does help contribute.
[/LIST]

One feature that PlayOnLinux and Crossover do is create and manage are prefixes.  Prefixes are container environments to run individual programs separately so they don't step on each other.  This because to get many windows programs running under wine you must tweak settings here and there which may drastically affect other programs running in the same prefix.  Good illustration here: [http://www.playonlinux.com/en/dev-documentation-5.html](http://www.playonlinux.com/en/dev-documentation-5.html)

Now you CAN do prefixes manually with just base wine install as well as all the little tweaks to get some programs running, but it will take time digging and tinkering with config files and command lines. In the end POL/Crossover are just tools to make installation simpler, it's your choice to wither use them or not.

Note: I'm using straight wine, but now starting to run into programs clashing and looking for a easy gui solution to containerize them.

---

### Post by handy on 2010-11-15
Crossover has a demo available, so you can check it out, see if it works for you & evaluate whether it is worth the price.

I've been using Crossover for years on OS X, to play Guild Wars. I use the OS X, as opposed to Linux for Guild Wars, because the GPU drivers are still better under OS X, unfortunately.

---

### Post by rykel on 2011-11-11
> **cwwilson721 said:**
> Hmmm...
Let's start with the basics, and then go to the highlighted colors, and why they are SO misleading.
*SNIPPED*
Neither is a very compelling reason to use those GUIs over plain ol' wine. Unless you like to pay money.
[/COLOR][/COLOR]

I would beg to differ. PlayOnLinux is something so user-friendly it helps ex-Windows users. Also, for some people, they do NOT have the games they would like to play in mind (perhaps they have forgotten Windows games for a long time) so the list of installable games displayed in POL is a great overview and refresher.

Last but not least, POL "containerizes" the games so each of them has their own unique operating environments. While WINE can do so, but POL makes the procedure FRIENDLY. Just my 2 cents!

---

### Post by regeya on 2012-03-16
> **cwwilson721 said:**
> 2nd, Cedega/Crossover have you pay money for basically NOTHING. wine does what they can do, and for free, faster, and did I mention FREE? wine now has DirectX support (slow, but it works).
[/COLOR][/COLOR]

I hate to pop in two years later, but that's not entirely true.  First, Cedega and Crossover are two separate products; on both, they not only provide their own DX drivers, but also usually have support for copy protection before the mainstream Wine release.

---

### Post by Cardale on 2012-05-18
Managing multiple versions of Wine is a chore when all you want to do is use some windows software or play a game.

Playonlinux fills a void in the linux community and does a mighty fine job of it.

I bought Diablo 3 and in less then a day I didn't have to fiddle with patching Wine or downloading a custom version.  I just selected which game I want to install and it handled everything for me.

Of course it is built off Wine which does the real work, but it does the configuration work which is brilliant.  It removes the boundaries from the "Leet" user and the new Ubuntu user coming from Windows or Mac.

To me the honestly my first impressions of Crossover was that is was crap just by looking at their website, but I heard it is very good.

PlayonLinux is good enough for me though.  I can install my games even Microcrap Office if I need to.  Now I can easily convince people to switch to Ubuntu.

If you have the cash Crossover might be easier, but Playonlinux is free and honestly it has a step by step wizard.

---

### Post by Dlambert on 2012-05-19
And if your program doesn't have a POL installer, you can install it manually by .exe. Free?, or not to be free? That is the question.

---

### Post by buzzmandt on 2012-05-21
yeah, playonlinux is becoming awesome.  but i highly recommend you add their repo to your list for the most up to date version.

---

### Post by Dlambert on 2012-05-24
> **buzzmandt said:**
> yeah, playonlinux is becoming awesome. But i highly recommend you add their repo to your list for the most up to date version.
 +1

---

