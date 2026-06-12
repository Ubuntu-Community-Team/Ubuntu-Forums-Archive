---
title: "Help with Counter-Strike Source Lag"
date: 2009-04-08
forum: Wine
---

### Post by MariaRageBoy on 2009-04-08
Im getting lag playing Counter-Strike source which never happened on windows.
Im using latest dev wine and ATI HD 2600 XT 512 ded video memory
2 GB of Computer mem and AMD X2 Processor 1.9
Source is all laggy
Im using Ubuntu 8.10 Intrepid with Proprietary Drivers

---

### Post by shavenlunatic on 2009-04-08
when you say lag.. do you mean network lag or low frames per second?

When in game, bring down the console and type ```
net_graph 1
``` - this will show your FPS, it will go up and down depending on how much activity there is on screen, how high/low is your FPS running?

---

### Post by asdfoo on 2009-04-08
> **MariaRageBoy said:**
> Im getting lag playing Counter-Strike source which never happened on windows.
Im using latest dev wine and ATI HD 2600 XT 512 ded video memory
2 GB of Computer mem and AMD X2 Processor 1.9
Source is all laggy
Im using Ubuntu 8.10 Intrepid with Proprietary Drivers

you don't say which version of Wine you are using?

Upgrade to Wine 1.1.18, it performs better than the version shipped with 8.10 for CS:S

---

### Post by u235sentinel on 2009-04-08
> **asdfoo said:**
> you don't say which version of Wine you are using?

Upgrade to Wine 1.1.18, it performs better than the version shipped with 8.10 for CS:S

I've seen the same thing however it's not a problem with network latency.  I've been checking and it looks ok.  Every now and then the fps drops to like 2-5 for a couple seconds.  Just enough time for me to die.  

I'm running WINE 1.0.1 and Ubuntu 8.04 on a high end system with an NVIDIA 9800GTX+.  Still using the 169 drivers which came with my distro however I'm looking at upgrading to 180.  Found the drivers in another ubuntu thread here.  If that doesn't work then I'm thinking of upgrading WINE to 1.1.18 as suggested.  I have a number of other games that also depend on WINE.  Hoping it doesn't break any of those :D

---

### Post by asdfoo on 2009-04-08
> **u235sentinel said:**
> I've seen the same thing however it's not a problem with network latency.  I've been checking and it looks ok.  Every now and then the fps drops to like 2-5 for a couple seconds.  Just enough time for me to die.  

I'm running Wine 1.0.1 and Ubuntu 8.04 on a high end system with an NVIDIA 9800GTX+.  Still using the 169 drivers which came with my distro however I'm looking at upgrading to 180.  Found the drivers in another ubuntu thread here.  If that doesn't work then I'm thinking of upgrading Wine to 1.1.18 as suggested.  I have a number of other games that also depend on Wine.  Hoping it doesn't break any of those :D

I'm surprised that 169 supports 9xxx series...

180.44 + 1.1.18 works well

---

### Post by MariaRageBoy on 2009-04-08
> **shavenlunatic said:**
> when you say lag.. do you mean network lag or low frames per second?

When in game, bring down the console and type ```
net_graph 1
``` - this will show your FPS, it will go up and down depending on how much activity there is on screen, how high/low is your FPS running?
I get 80- 70 FPS and around 40-50 in firefights. But its not network lag, as Im playing alone. If I lower my Direct x level from +9.0 or 7.0 the game is barely playable. It causes lockups in multiplayer dunno why
> **asdfoo said:**
> you don't say which version of Wine you are using?

Upgrade to Wine 1.1.18, it performs better than the version shipped with 8.10 for CS:S
lol btw I followed WIne instructions and I already have 1.1.18 I checked the the registration info in Wine.
I said I was using latest Development Wine which is 1.1.18 as of now

Ill just play Condition Zero and 1.6 until I can play Source in Ubuntu

---

