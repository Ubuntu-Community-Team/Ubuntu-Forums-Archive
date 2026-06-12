---
title: "What wine version does Fallout 3 and Oblivion run best on?"
date: 2010-02-16
forum: Wine
---

### Post by Cakeguy on 2010-02-16
Hey, I've been trying multiple times to get Fallout 3 and Oblivion working on my Ubuntu 9.10 x64 pc... Let's say I haven't had any luck at all. First off, Fallout 3 has been laggy... *_Very_* laggy. And I haven't been able too see body parts on the PC or on any NPC. So on myself I just saw my pipboy, gear and so on. At Oblivion I haven't had any luck neither... You see, right after character creation my game crashes... ](*,) Both of my games are bought so they are no pirate-copies. And now I wonder if *_anyone_* knows what Wine-version Fallout 3 and Oblivion runs best on. ;)

Computer speccs:

ATI Radeon 4830.

6 gb of ram.

Quad-Core Processor.

And some more ofc. 8-)

But I think those 3 I mentioned are the most important. Anyways, if you could answer my question then I would be more than thankful. Thanks. 

:-k

Sorry if my english is bad.

---

### Post by Ferrat on 2010-02-16
have you checked appdb.winehq.org ?

---

### Post by gsmanners on 2010-02-16
> **Cakeguy said:**
> First off, Fallout 3 has been laggy... *_Very_* laggy. And I haven't been able too see body parts on the PC or on any NPC. So on myself I just saw my pipboy, gear and so on. At Oblivion I haven't had any luck neither... You see, right after character creation my game crashes... 

I would suggest the latest beta version of Wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

Fallout 3 is laggy on most Windows systems. Wine makes this situation even worse. Lots of people swear by this Stutter Remover (although YMMV):

[http://www.fallout3nexus.com/downloads/file.php?id=8886](http://www.fallout3nexus.com/downloads/file.php?id=8886)

I don't know what to make of missing body parts. Are they missing faces or just arms, legs and torso?

As with all Bethesda games, expect *lots* of bugs, so make sure to read up on the technical forum. In particular, these threads:

[http://www.bethsoft.com/bgsforums/index.php?showtopic=890373](http://www.bethsoft.com/bgsforums/index.php?showtopic=890373)
[http://www.bethsoft.com/bgsforums/index.php?showtopic=892715](http://www.bethsoft.com/bgsforums/index.php?showtopic=892715)

and also check out this guide:

[http://www.tweakguides.com/Fallout3_1.html](http://www.tweakguides.com/Fallout3_1.html)

I would notice in particular this bit of advice:

> Issue 7: Crashing (2+ core CPU)

Solution: Try adding this line to the [General] section of the Fallout.ini.

iNumHWThreads=2

And change the 0 to 1 for this line

bUseThreadedAI=0

from [http://www.bethsoft.com/bgsforums/index.php?showtopic=973552](http://www.bethsoft.com/bgsforums/index.php?showtopic=973552)

---

### Post by Cakeguy on 2010-02-17
> **gsmanners said:**
> I would suggest the latest beta version of Wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

[SIZE=2]**Fallout 3 is laggy on most Windows systems. Wine makes this situation even worse. Lots of people swear by this Stutter Remover (although YMMV):**[/SIZE]

[http://www.fallout3nexus.com/downloads/file.php?id=8886](http://www.fallout3nexus.com/downloads/file.php?id=8886)

[SIZE=2]**I don't know what to make of missing body parts. Are they missing faces or just arms, legs and torso?**[/SIZE]

As with all Bethesda games, expect *lots* of bugs, so make sure to read up on the technical forum. In particular, these threads:

[http://www.bethsoft.com/bgsforums/index.php?showtopic=890373](http://www.bethsoft.com/bgsforums/index.php?showtopic=890373)
[http://www.bethsoft.com/bgsforums/index.php?showtopic=892715](http://www.bethsoft.com/bgsforums/index.php?showtopic=892715)

and also check out this guide:

[http://www.tweakguides.com/Fallout3_1.html](http://www.tweakguides.com/Fallout3_1.html)

I would notice in particular this bit of advice:



from [http://www.bethsoft.com/bgsforums/index.php?showtopic=973552](http://www.bethsoft.com/bgsforums/index.php?showtopic=973552)


1. Fallout 3 ran just fine when I had Windows 7, but I don't know really. Maybe I can try that mod in Linux, yeah.

2. Let's say everything that's skin on the PC or a NPC is missing.

And oh hey, I'll be sure to read the links you wrote down. As for the Wine-versions, I first tried Fallout 3 with Wine 1.1.38 beta, then I tried with the versions they tried on WineHQ. Both got same results, missing skin/body parts, whatever. And I actually read on UESPWiki about Linux and Oblivion ([http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)) and tried a very old Wine-version which they said worked best for Oblivion. Well the results for Oblivion were... Pretty bad. I WAS able to play it, on windowed mode, very low and resolution 640x480. However that's not the way I wan't to play a game. :frown:

So if there's anything that just might work, MIGHT work just tell me already! :D

Thanks.

---

### Post by Cakeguy on 2010-02-17
> **Ferrat said:**
> have you checked appdb.winehq.org ?

Yeah. :mrgreen:

---

### Post by Cakeguy on 2010-02-19
Uh, so I've read around, and I've seen that Linux, Wine and an ATI-card works bad. Cause at another place, there I have a Ubuntu 9.10 x64 pc with a Nvidia-card. And Fallout 3 works awesome there. So do you think it might be cause I have an ATI-card? Thanks. 


And again, sorry for my bad english.

---

### Post by castlefox on 2010-02-20
Are you using the latest driver for your ATI card???

---

### Post by dino99 on 2010-02-20
latest release is out : 1.1.39 :D

---

### Post by Cakeguy on 2010-02-20
> **castlefox said:**
> Are you using the latest driver for your ATI card???

Yes. :)

---

### Post by Cakeguy on 2010-02-20
> **dino99 said:**
> latest release is out : 1.1.39 :D

Hey, I'll try to install Fallout 3 with that version. Thanks.

---

### Post by Cakeguy on 2010-02-20
So I have installed Fallout 3 in Wine 1.1.39 and applied patch 1.7 (I'll install DLC's when i get my game to work). And I also applied the stutter-thingy mod [http://www.fallout3nexus.com/downloads/file.php?id=8886](http://www.fallout3nexus.com/downloads/file.php?id=8886) . But it still lags, and still I can't see any body-parts of NPC's or the PC. :confused:

---

### Post by Progressive on 2010-02-21
There are TONS of tweaks you can do. INI tweaks, driver tweaks, patches, mods, [NIF optimization]("http://cs.elderscrolls.com/constwiki/index.php/Nif_Optimization"), native dlls, killing background processes.

The NIF optimization has no quality penalty and works for both Oblivion and Fallout. They recommended not using niftoaster on your entire mesh directory, but other than it taking a very long time to finish (let it run overnight)... I noticed no problems. I hear it can conflict with some hair mods though.

Make sure all the mods are installed before you try this though, to get best results.

Other good Oblivion performance mods are:

Oblivion Scripts Optimization 
Oblivion Polygone Overhaul 
Optimised Distant Land MAX 

Also the [Quiet Feet MAX]("http://www.tesnexus.com/downloads/file.php?id=12331") mod.

There are similar ones for Fallout... don't just use the stutter remover.

Another thing is you need to make sure you have all the proper native dlls. Different dlls are needed depending on the version of wine you are using and your hardware. At various times I use the following native dlls to get oblivion working with my radeon.

binkw32
dinput8
msvcp60
quartz
d3d8

and of course the
d3dx9_xx series that are included when you install d3dx9 through winetricks

Just install these into your ~/.wine/drive_c/windows/system32 directory and see if it helps, and delete them out if it doesn't help.

As far as INI tweaks go, the most likely tweak to get you up and running is turning off pixel shading, which will have a very significant impact on the visual quality. There are [others]("http://www.uesp.net/wiki/Oblivion:Ini_Settings") though that have a much less impact that could help. Setting the grass view distance and quality down can help quite a bit. There are also Low Poly grass mods that can look nearly identical to the original.

A recent issue with bethsoft games seems to be a change regarding libmpg123 for 64 bit games. Do you run 64 bit by any chance? That could be an issue... hopefully will be resolved soon.

---

### Post by Cakeguy on 2010-02-21
Hey, I'm pretty new to this Ubuntu-thing. Could you tell me directly how I install those DLL's and that? And yes I use a 64-bit system.

---

### Post by Progressive on 2010-02-21
All you have to do is add them to your system32 directory. If you are using a graphical user interface to access the directory, go to the home directory and make sure the "show hidden files" option is on. Then go to the ".wine" folder, then drive_c and then windows and then system32.

You can find the dlls on the internet on sites like dll-files.com

By the way, another possible method for getting Oblivion to work is to use Oldblivion to convert it to directx 8.0  (this should work in addition to all these other tweaks, and shouldn't interfere with them)

You can probably guess that it negatively impacts visual quality though. You should be able to install it normally from the [oldblivion]("http://www.oldblivion.com/") website.

Their website claims they started on a Fallout 3 version... but notice that was back in 2008... they haven't released anything since then, so this is for oblivion only.

---

### Post by Cakeguy on 2010-02-22
Ok, so I've changed back to Faildows XP due to lack of interest. Big thanks anyway! Sorry if your time feels wasted...

---

### Post by gsmanners on 2010-02-24
No problemo. I still use XP for Fallout 3 (and Sims 2) myself.

---

### Post by Jagoly on 2011-03-19
I am a necromancer.

Have oblivion all working, save for one thing. I am experiencing the problem found at [http://www.uesp.net/wiki/Oblivion:Linux#People.27s_faces_do_not_render_properly]("http://www.uesp.net/wiki/Oblivion:Linux#People.27s_faces_do_not_render_properly")
However, I do not have a Nvidia card. I have an ATI Mobility Radeon 56xx card, with the latest catalyst drivers from the ATI website. The game would be better with bodies. I also had already put in the native dlls for everything mentioned earlier. I know that this doesn't happen on my friend's ati 3xxx card.

---

