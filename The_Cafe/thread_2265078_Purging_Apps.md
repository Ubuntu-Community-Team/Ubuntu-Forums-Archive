---
title: "Purging Apps?"
date: 2015-02-12
forum: The Cafe
---

### Post by TheFu on 2015-02-12
I'm curious.  **What applications/programs/tools do you purge from the stock Ubuntu installations?**

Here's my first command on every new Ubuntu machine - desktop/server ... doesn't matter.
```
sudo apt-get purge nano gedit leafpad compiz unity-scope* unity-asset-pool  geoclue-ubuntu-geoip network-manager chrome
```

Why?
[LIST]

[*] It all started with just purging nano - usually the first **visudo** on the machine reminds me to purge it.  It isn't called *nanosudo* for a reason. Don't *need* extra editors myself - though on desktops where programming happens I install **geany**. Don't misunderstand, I'm not against nano being the default editor on a desktop, but servers are completely different.
[*] Pretty GUIs get in the way for me. No "cheese" needed.
[*] Then there is the tracking and social media stuff that I'd rather not have. Nautilus and  brasero are dependent on something in here, so be aware of that if you use those programs. I do not.
[*] I find network-manager gets in the way more than it helps with my networking. For a few years, I'd fight with it trying to get it to do something simple and it failing. Sometime in 2013, I'd had enough.
[/LIST]

I love how flexible Linux is that we can customize our machines - and automate that customization through tools and scripts - to get a system we like, enjoy using, and is 100% mine.

So - what's in your list?

---

### Post by mooreted on 2015-02-12
I don't purge anything, I just turn off the Amazon and Internet search functions.

---

### Post by ian-weisser on 2015-02-12
I remove things I don't use from -desktop as updates to them appear.
I generally don't remove anything from -server.

When I release-upgrade desktop every six months, I restore the removed applications by reinstalling the -desktop metapackage.
I used to remove Amazon, but now I simply check the privacy setting.

---

### Post by CantankRus on 2015-02-13
If you're removing compiz and don't like pretty GUI's, why install the Ubuntu/unity flavour in the first place?
I just turn off online search and remove extra scopes so dash only shows Home, Applications and Files scopes.

---

### Post by Bucky Ball on 2015-02-13
I don't purge anything. Been doing [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") installs for a few years now, so I just add what I want and don't have bloat.

My apt-get install command after the first boot generally includes xfce4, firefox, thunderbird, audacity, vlc, and a not very long list of other stuff. ;)

---

### Post by TheFu on 2015-02-13
> **CantankRus said:**
> If you're removing compiz and don't like pretty GUI's, why install the Ubuntu/unity flavour in the first place?
I just turn off online search and remove extra scopes so dash only shows Home, Applications and Files scopes.

a) this is the cafe - not looking for a specific solution for myself. Wanted to learn what applications others find excessive.
b) don't run a stock Ubuntu desktops here. The question was really for people running stock desktops with applications they don't want/need/desire.
c) setups here are mostly scripted, so leaving packages that aren't actually on the system in the **list to be purged** doesn't hurt anything.  Plus if the package is GONE, there isn't any worry it might accidentally get re-enabled later.

I generally install "server" (minimal was just too minimal), then add openbox for a desktop and the 10-15 applications that are actually desired.  Most of my "desktops" run inside virtual machines over a network, so anything with 3D acceleration is useless.  Real servers don't get a GUI, of course. 

So - what applications do you purge from the normal desktop install?

---

### Post by CantankRus on 2015-02-13
> **TheFu said:**
> 

So - what applications do you purge from the normal desktop install?
None.

---

### Post by Pinoy Tux on 2015-02-14
Thunderbird.  Webmail for me.

---

### Post by pfeiffep on 2015-02-14
> **TheFu said:**
> I'm curious.  **What applications/programs/tools do you purge from the stock Ubuntu installations?**

...

So - what's in your list?Once I decided to use a 'Windows' mentality and remove everything that I didn't need in an effort to save space. I used the software center and agressively removed what I considered not useful to me starting with all the games. When I was through with my "ready - shoot - aim" method I was left with a system that was totally useless and was forced to reinall from scratch. Since then I've kept whatever the default installation brings while restricting some of the functionality. I remove all applications that I install after finding I don't like or use them.

---

### Post by TheFu on 2015-02-14
> **pfeiffep said:**
> Once I decided to use a 'Windows' mentality and remove everything that I didn't need in an effort to save space. I used the software center and agressively removed what I considered not useful to me starting with all the games. When I was through with my "ready - shoot - aim" method I was left with a system that was totally useless and was forced to reinall from scratch. Since then I've kept whatever the default installation brings while restricting some of the functionality. I remove all applications that I install after finding I don't like or use them.

Don't remember software center - does it hide dependencies so the user can't see what is being removed?

---

### Post by pfeiffep on 2015-02-14
> **TheFu said:**
> Don't remember software center - does it hide dependencies so the user can't see what is being removed?Since I stopped using the software center I had to launch it to find out. When selecting more info I didn't notice and warnings about removal of 5 different apps - but I didn't try to remove any of them so I can't say for certain.  I do know that Synaptic does provide dependiences info. I mistakenly assumed that the native software center would not permit removal of REQUIRED packages.

---

### Post by bashiergui on 2015-02-14
> **pfeiffep said:**
>  I mistakenly assumed that the native software center would not permit removal of REQUIRED packages.It warns you. If you choose to uninstall something that will also remove other packages, it will warn you and give you a list of affected software. It won't let you remove something that other packages depend on without also removing those.

---

### Post by oldos2er on 2015-02-15
I don't purge, just remove (from Kubuntu) ```
sudo apt-get remove kmail kontact quassel konversation
```

---

### Post by user1397 on 2015-02-16
> **TheFu said:**
> a) this is the cafe - not looking for a specific solution for myself. Wanted to learn what applications others find excessive.
b) don't run a stock Ubuntu desktops here. The question was really for people running stock desktops with applications they don't want/need/desire.
c) setups here are mostly scripted, so leaving packages that aren't actually on the system in the **list to be purged** doesn't hurt anything.  Plus if the package is GONE, there isn't any worry it might accidentally get re-enabled later.

I generally install "server" (minimal was just too minimal), then add openbox for a desktop and the 10-15 applications that are actually desired.  Most of my "desktops" run inside virtual machines over a network, so anything with 3D acceleration is useless.  Real servers don't get a GUI, of course. 

So - what applications do you purge from the normal desktop install?TheFu, I like you

---

### Post by bashiergui on 2015-02-17
> **ubuntuman001 said:**
> TheFu, I like youThe Ubuntu Forums Cafe. Come for the chitchat, stay for the bromance ;)

---

### Post by Bucky Ball on 2015-02-17
> **bashiergui said:**
> The Ubuntu Forums Cafe. Come for the chitchat, stay for the bromance ;)

How do you know they're both men, despite the ubuntuman username??? I'm actually an neutered anteater. ;)

---

### Post by bashiergui on 2015-02-17
> **Bucky Ball said:**
> How do you know they're both men, despite the ubuntuman username??? I'm actually an neutered anteater. ;)
Rule 29 and 30, of course ;)
[https://archive.org/stream/RulesOfTheInternet/RulesOfTheInternet..txt](https://archive.org/stream/RulesOfTheInternet/RulesOfTheInternet..txt)

29. All girls are men and all kids are undercover FBI agents
30. There are no girls on the internet.

---

### Post by user1397 on 2015-02-18
Nothing wrong with a bromance! haha

I just meant that, TheFu seems like a guy I could get along with that's all lol

---

### Post by TheFu on 2015-02-25
So added another set of packages to be purged today.  ibus*

Those were interfering with keepassx autotype on 1 system, but not all of them.  Tried to use the suggested workarounds using environment variables first, as suggested by google code and AskUbuntu, no joy.  Simply restarting it would lock all input to 1 window, not necessarily the one on top. No keyboard, no mouse inputs worked then.  The problem has to be a fringe issue, since so many other applications aren't having problems.

keepassx is a core application to me. More important than pretty much any other apps.

However, sometimes, firefox got garbage input that didn't seem related to what was being typed at all. Hopefully this purge will clear that extremely seldom issue too.

As to the bromance ... that's nice, I suppose.  I'm definitely opinionated and think I know what I want/like. Feel free to stop by the LUG in ATL sometime.

---

