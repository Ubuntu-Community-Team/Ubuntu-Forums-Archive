---
title: "World of Warcraft + Wine = No dualcore support?"
date: 2009-02-17
forum: Ubuntu Gamers Arena
---

### Post by gotsanity on 2009-02-17
I know a couple months back blizzard added multi cpu support to wow and wine has had it all along... but for some reason my wow install is giving me 100& utilization in only one core... the other core is kicking around 15% Any thoughts?

---

### Post by gotsanity on 2009-02-17
For the record I am running Intrepid, wine 1.0.1, WoW 3.0.9 on a nforce mobo with an amd 1.9 dual core with 3gig ddr2 and a geforce 7500 series

---

### Post by EvinK on 2009-02-19
From some Blizzard post, I will try to dig it up, is that it isn't truly dual core support.  I think they sound the sound part and a few others actually take advantage, but not the whole game itself.  I will try to find that post as I could be wrong.

Here is a [link]("http://forums.wow-europe.com/thread.html;jsessionid=1112A77033802BF8B28541EDD4EBC075.app06_08?topicId=3190959942&sid=1") (although not the one I wanted).    I am not sure what he means by "doubt there will be 100% support".

[QUOTE=Gelmkar]
World of Warcraft was optimised to support Dual-Core processes in a previous patch, while I doubt there will be 100% support, the game should balance the numerous threads the game uses over the core's available which should offer a slight improvement, providing you have your system correctly configured.

First of all make sure that you have installed all the latest updates available for your operating system, especially the ones geared towards fixing or improving dual-core support.

The following post contains some updates to Windows XP/Vista geared towards improving system performance.

[http://forums.wow-europe.com/thread.html?topicId=2405449567&sid=1#4](http://forums.wow-europe.com/thread.html?topicId=2405449567&sid=1#4)

Also check that you have the latest system drivers installed for your motherboard as well as any driver updates available for your CPU. 
[/QUOTE]

---

### Post by ethanay on 2009-02-22
I have this problem with a completely different program:  Pianoteq is a virtual piano that is modeled and synthesized in real time.

It has built-in dual core support.  You pull down a menu and click "enable dual core support"

When I do this, CPU usage skyrockets from about 15-30% to 50-100%.

This is the exact opposite of the intended effect the option is supposed to have.  I posted the issue on the pianoteq forums:
[http://www.forum-pianoteq.com/viewtopic.php?id=282]("http://www.forum-pianoteq.com/viewtopic.php?id=282")

So the problem is basically this:  Under Wine, selecting dual-core rendering doubles the CPU load.  Which means it's a Wine bug that is not correctly interpreting the dual core rendering instructions, resulting in overloading one of the CPUs where both should be sharing the load.

---

### Post by Bram van der Heijden on 2009-03-27
Guys,

World of Warcraft supports it, so does Wine. Check your Config.wtf file in the World of Warcraft WTF folder. If you add the following lines you can change the amount of cores WoW should use. From 1 to 4 cores at once, unlucky for me, cause i run dual quadcores ! :)
Change the setting and it might boost you some fps.

SET processAffinityMask = "15"

Check this WoW forum post

[http://forums.worldofwarcraft.com/thread.html?topicId=1778043427&pageNo=2&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=1778043427&pageNo=2&sid=1)

It is actually meant for the game to run on certain cores you specify, but this way you can force it to run on 4 cores, instead of 1 or 2.

Regards,[PHP][/PHP]

---

### Post by toopi on 2009-04-07
Multi-threading in wine is a bit more complicated than we'd like.  Refer to this [page]("http://www.winehq.org/docs/winedev-guide/threading") for more information.

Now, I don't believe WoW, even on Windows, cannot utilize more than 2 cores.  I've tested it extensively.  As Bram in the post #5 noted, you can make it run on certain cores, but no more than 2 cores.  And it's only if you're running WoW on Windows.

On Linux, WoW with wine does make use of 2 cores.  However, setting process affinity doesn't change a thing, i.e.  wine will pick any 2 cores that it likes.

Edit:  Wine may not even be using 2 cores for WoW.  Usage of the 2nd core could be for other processes.  Wine internal workings are obviously beyond my knowledge.

---

### Post by GCoffee on 2009-04-25
Hmm.. Sounds interesting :-)

---

