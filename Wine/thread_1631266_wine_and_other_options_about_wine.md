---
title: "wine and other options about wine"
date: 2010-11-26
forum: Wine
---

### Post by c00lwaterz on 2010-11-26
I heard about wine but have never use it so i don't know much about it.
I just recently try to open ubuntu software center and type in the search "wine".
The following appeared:

1) Wine Microsoft Windows Compatibility Layer(Beta Release)
2) Wine Microsoft Windows Compatibility Layer
3) PlayOnLinux

What are they? what to choose? how it works? what is the difference of the three software?

Im sorry for my ignorance. :D

---

### Post by Red_Steve on 2010-11-26
1) is the newest (relatively stable to be frank) version of wine. I'd recommend that
2) is the latest stable version (I feel wine to be much too conversative about their declaration but this version is tried and true)
3) is a wine frontend to ease the installation of many games and some often used MS-Tools (like office) which will install alongside with needed plugins like .net or directX or gecko web engine. I'd recommend this if you are really planning to use more than one windows game or application as it also eases the management of needed plugins.

---

### Post by c00lwaterz on 2010-11-26
> **Red_Steve said:**
> 1) is the newest (relatively stable to be frank) version of wine. I'd recommend that
2) is the latest stable version (I feel wine to be much too conversative about their declaration but this version is tried and true)
3) is a wine frontend to ease the installation of many games and some often used MS-Tools (like office) which will install alongside with needed plugins like .net or directX or gecko web engine. I'd recommend this if you are really planning to use more than one windows game or application as it also eases the management of needed plugins.

so the option is now 1 and 3, for me that have some games like counter strike source, and command and conquer 4 twilight and also in future want to play diablo 3. what is the best option? i plat games but not that many. :p

---

### Post by Oxwivi on 2010-11-26
Option 3 is basically on top of of 1, it will automatically install 1, won't work without it.

---

### Post by Red_Steve on 2010-11-26
1) and 3), yeah

But don't expect that you can play those games on Day 1

Sometimes wine has to be updated for certain functions newer games require and PlayOnLinux has to be updated with installation scripts for the Games you wan't to install. It usually takes about 2-3 Weeks (sometimes months!) until a script hits the repository.

CS:S will be running fine as will C&C4. Diablo III should also do fine but don't bet on it.

I personally use 1) and 3) for World of Warcraft 4.0.3a which does fine and used it for Steam (TF2, CS:S, Tropico 3, Dragon Age, Mass Effect 1 & 2)

---

### Post by c00lwaterz on 2010-11-26
> **Red_Steve said:**
> 1) and 3), yeah

But don't expect that you can play those games on Day 1

Sometimes wine has to be updated for certain functions newer games require and PlayOnLinux has to be updated with installation scripts for the Games you wan't to install. It usually takes about 2-3 Weeks (sometimes months!) until a script hits the repository.

CS:S will be running fine as will C&C4. Diablo III should also do fine but don't bet on it.

I personally use 1) and 3) for World of Warcraft 4.0.3a which does fine and used it for Steam (TF2, CS:S, Tropico 3, Dragon Age, Mass Effect 1 & 2)

do i need to install 1 and 3? or just 3? :p

---

### Post by Iowan on 2010-11-26
Moved to Wine forum.

---

### Post by Zzl1xndd on 2010-11-26
If you install PlayOnLinux it should install WINE as well.

---

### Post by c00lwaterz on 2010-11-26
> **tweakedenigma said:**
> If you install PlayOnLinux it should install WINE as well.

so the best option i can install is playOnLinux? correct me if i am wrong :p

---

### Post by AngelDE98 on 2010-11-27
Yes , install PlayOnLinux ... 

Then you most likely need some extra-dlls but you will only likely need it ...

---

### Post by c00lwaterz on 2010-11-27
> **AngelDE98 said:**
> Yes , install PlayOnLinux ... 

Then you most likely need some extra-dlls but you will only likely need it ...

what about it?  should i do something else after install of playOnLinux?

thanks :p

---

### Post by Soulcage on 2010-11-28
What you should do is paste these into a terminal:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3

---

### Post by c00lwaterz on 2010-11-28
> **Soulcage said:**
> What you should do is paste these into a terminal:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3

ok so i should add wine on playOnLinux. How about installing software? I saw a list there with games, office etc.. do i need serial key? is this same as ubuntu software center? thanks in advance :p

---

### Post by Soulcage on 2010-11-29
If you do what I pasted you'll have wine installed w/o playonlinux and yeah the packages are the same as the ones in the ubuntu software center.

---

### Post by c00lwaterz on 2010-11-29
i have problem in counter strike source. I installed steam in wine and run properly. I installed counter strike source properly bot not loading. only steam is working. I tried some installer like Gomplayer, winamp. but not working on wine. maybe it is not ready yet. i will wait when wine is much more easier to use. :p

---

### Post by Soulcage on 2010-11-30
You should check out [http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by c00lwaterz on 2010-11-30
> **Soulcage said:**
> You should check out [http://appdb.winehq.org/]("http://appdb.winehq.org/")

thanks for the info

I already check but did not work for me.  only steam is working but the counter strike source is not loading. it's ok if not working. not that matters so much to me.

:D

---

