---
title: "Is WUBI worth it?"
date: 2012-12-12
forum: The Cafe
---

### Post by DuckHook on 2012-12-12
I know the developers don't read this and it's not a Canonical forum, but the topic is Ubuntu-related and I'm curious about the thoughts of forum members.

Soooo many of the posts pleading for help seem to come from new users who have installed with WUBI that I've lost count. WUBI is meant to make it easier for Windows users to try Ubuntu, but does it do more harm than good? What happens when trials turns into tribulations? Are the problems even a representative sample? I've no experience with WUBI so have no idea how well-behaved it is, but looking through the sour experiences on these threads is kind of depressing.:(

---

### Post by vasa1 on 2012-12-12
I can't say why, but I don't like WUBI as a concept.

---

### Post by lykwydchykyn on 2012-12-12
First, I'd say that threads on these forums are never a representative sample.  This is a support forum, and by definition people don't post here until there is a problem.  For every person who posts here reporting a problem, there may be 100, 50, 10 , 2, or 0 people who didn't have that problem; we'd never know.

As for WUBI, there is the concept, and there is the implementation.  Implementations always have problems, and they usually tend to fix those problems over time.  The real question is whether the fundamental concept is worth it.  I'm not sure if it is.

Consider the problem: someone who is not terribly techy, but wants to try Linux on his Windows computer.  His options are:

** Boot to the liveCD or LiveUSB image

The advantage here is that the Windows install isn't touched, there's nothing that needs to be set up, and no commitment to be made.  Downside, of course, is that nothing is saved, there is a limit to what can be installed, proprietary drivers can't be tested, the performance is somewhat slower, and (in the case of the CD) the optical media is tied up.

** Install Dual Boot

The advantage here is that Windows is still there, Ubuntu has native hardware access, programs can be installed, data can be saved, etc.etc.
Disadvantage is that setup is tricky and lots of things can go wrong, including the Windows partition being wiped out or made unavailable.

** Virtual Machine

The advantage is that Windows remains safe and untouched, Ubuntu is easy to remove if it's not wanted, and Ubuntu is considerably easier to install.  Disadvantage is that performance really suffers, and you have to run two OS at the same time.  That, and the very concept of a virtual machine makes a lot of people's heads spin.

I see WUBI as a sort of compromise between all three.  You suffer some performance loss and limitations, but your Windows install is safe, you can install programs and save data, and you aren't running two complete OS at the same time.  I'd never recommend it as a long-term setup, but it seems like a better choice than a liveCD or VM for basic testing.

---

### Post by vasa1 on 2012-12-12
> **lykwydchykyn said:**
> First, I'd say that threads on these forums are never a representative sample.  This is a support forum, and by definition people don't post here until there is a problem.  For every person who posts here reporting a problem, there may be 100, 50, 10 , 2, or 0 people who didn't have that problem; we'd never know. ...
+1.

One more point is that it's possible that, given the perceived ease of a WUBI install, less proficient (or technically competent) users maybe drawn to it thereby increasing the chances of a bad experience.

---

### Post by asifnaz on 2012-12-12
Well if there was no wubi I would not be an Ubuntu user . It provided me the opportunity to try Ubuntu first . Then I formatted windows partition and installed Ubuntu .

---

### Post by DuckHook on 2012-12-12
Thanks for your input @asifnaz. Would you have gotten to the same decision point with a LiveCD trial?

Just learned from a concurrent thread (thanks to @bcbc) that WUBI installs Linux's native ext3/4 file structure on top of NTFS. This has the potential to be awful.

Scenario: I'm a less-techy user newly from Windows. I'm not happy with Windows because my system seems to be slower all the time from fragmentation, crufty registry, service bloat, etc, but of course, as a non-techy, I don't know that those are the causes. I try out Ubuntu because I've heard that it runs faster, is more reliable, etc. But the first thing I do, and totally unbeknownst to me is, I install my Ubuntu system on this horribly fragmented NTFS partition. The file is not only spread and fragmented all over heck's half-acre, but the double-journaling overhead is killing performance still further. One day, Ubuntu doesn't even start, or worse, starts but acts wonky. This is due to file corruption caused by a bad write or shutdown from that new Windows game that crashed on me. But I don't know this. It doesn't occur to me that a Windows issue could affect Ubuntu. Conclusion: Ubuntu/Linux is slow, wonky and totally unreliable. All marketing hooey.

Did I get something wrong? Am I painting an unrealistic scenario? I suspect it's pretty common, especially the slow file-system issues.

---

### Post by asifnaz on 2012-12-12
> **DuckHook said:**
> Thanks for your input @asifnaz. Would you have gotten to the same decision point with a LiveCD trial?



IMHO a Live CD is insufficient to try an operating system as it does not allow to install any apps and live CD gives just a sneak peak . 

I was not impressed by the live CD at all until I went through a wubi installation and downloaded some apps.

---

### Post by Grenage on 2012-12-12
You can install apps with a live CD, it's just not persistent.

---

### Post by deadflowr on 2012-12-12
> **Grenage said:**
> You can install apps with a live CD, it's just not persistent.

Yep, thats how I install boot-repair whenever I totally bork grub.

Wubi is worth it to those who suffer high levels of trepidation about their first install.
If you use wubi, you can see whether you even would want to run Ubuntu. If it works and you don't like it(or if it doesn't work) simply remove it, no harm no foul.
Personally, I don't and wouldn't use it.
And I'd have a hard time recommending it to anyone.
It's just a weird program.

---

### Post by asifnaz on 2012-12-12
> **Grenage said:**
> You can install apps with a live CD, it's just not persistent.

I didn't known that

---

### Post by monkeybrain2012 on 2012-12-12
> **asifnaz said:**
> IMHO a Live CD is insufficient to try an operating system as it does not allow to install any apps and live CD gives just a sneak peak . 

I was not impressed by the live CD at all until I went through a wubi installation and downloaded some apps.

Make a live usb with persistence. Live CD is good only for installation.

---

### Post by sudodus on 2012-12-12
Wubi might be an alternative, when the Windows installation already occupies all four partitions of an MBR partition table.

Before a new Ubuntu user is ready to wipe one of those partitions to allow for an extended partition, it is a good idea to try wubi. But it is important to let her/him know that it is not as stable or efficient as a standard or dual boot installation of Ubuntu onto a real partition.

Persistent USB is also a good alternative, but wubi is faster. A drawback with persistent USB is that it is slower than standard live sessions due to the very slow reading of many small files via USB. And if you unplug the pendrive too early, it gets corrupted.

---

### Post by verzx on 2012-12-12
I highly recommend using anything but WUBI for the simple reason that every time I try to install using it, there are always problems which then lead to other problems.

---

### Post by mJayk on 2012-12-12
I think WUBI provides the first actual method of somebody with no technical skills installing and trying ubuntu.

Yes Live-on-cd's are brilliant and usb sticks which are boot-able are neat.  But they require some "technical" knowledge to create, can go wrong, and things can get alot more scary for someone who doesn't know what they are doing if they do go wrong.

---

### Post by Frogs Hair on 2012-12-12
I started with Wubi and may not be here without it. I know four people who use it to sample the latest releases without problems. Windows 8 and Wubi has been a problem for computers with preloaded Windows 8. 

My friends use Wubi because using Linux operating systems is not a viable option for work. This is due to company policies about using unapproved software including 3rd party Win software. The bottom line is they don't want to commit to a traditional dual boot, but still want to experiment with Ubuntu.

---

### Post by lykwydchykyn on 2012-12-12
> **DuckHook said:**
> 
Scenario: I'm a less-techy user newly from Windows. I'm not happy with Windows because my system seems to be slower all the time from fragmentation, crufty registry, service bloat, etc, but of course, as a non-techy, I don't know that those are the causes. I try out Ubuntu because I've heard that it runs faster, is more reliable, etc. But the first thing I do, and totally unbeknownst to me is, I install my Ubuntu system on this horribly fragmented NTFS partition. The file is not only spread and fragmented all over heck's half-acre, but the double-journaling overhead is killing performance still further. One day, Ubuntu doesn't even start, or worse, starts but acts wonky. This is due to file corruption caused by a bad write or shutdown from that new Windows game that crashed on me. But I don't know this. It doesn't occur to me that a Windows issue could affect Ubuntu. Conclusion: Ubuntu/Linux is slow, wonky and totally unreliable. All marketing hooey.


That's certainly a significant downside to wubi; then again, the less-techy user who tries to set up a dual boot and ends up blowing Windows away is none too pleased either.  I know that because we see a fair amount of that happening here too.  Is there a perfect solution?

---

### Post by DuckHook on 2012-12-12
> **lykwydchykyn said:**
> ...the less-techy user who tries to set up a dual boot and ends up blowing Windows away is none too pleased either.

Yes, very valid point.

> Is there a perfect solution?What about a working installation on USB stick/disk? I'm not talking about persistent USB and all its associated restrictions, but a real working install: only with journaling, swap, all write-intensive activity turned off? Just tried one of those (thanks to instructions/recommendations from @oldfred) and it's not bad. In fact, it works pretty well. If the install CD offered such a choice, possibly with caveats about how much slower such a system would be due to USB limitations, etc. I bet lots of people would choose it instead. Also has the advantage of not being blamed on Ubuntu if stick fails.

---

### Post by JKyleOKC on 2012-12-12
> **DuckHook said:**
> Scenario: I'm a less-techy user newly from Windows. I'm not happy with Windows because my system seems to be slower all the time from fragmentation, crufty registry, service bloat, etc, but of course, as a non-techy, I don't know that those are the causes. I try out Ubuntu because I've heard that it runs faster, is more reliable, etc. But the first thing I do, and totally unbeknownst to me is, I install my Ubuntu system on this horribly fragmented NTFS partition. The file is not only spread and fragmented all over heck's half-acre, but the double-journaling overhead is killing performance still further. One day, Ubuntu doesn't even start, or worse, starts but acts wonky. This is due to file corruption caused by a bad write or shutdown from that new Windows game that crashed on me. But I don't know this. It doesn't occur to me that a Windows issue could affect Ubuntu. Conclusion: Ubuntu/Linux is slow, wonky and totally unreliable. All marketing hooey.

Did I get something wrong? Am I painting an unrealistic scenario? I suspect it's pretty common, especially the slow file-system issues.I think you're right on the money. Unfortunately, that user would have had even worse problems had he tried to install alongside Windows, and might easily have wiped out his (not backed up) Windows system and all his precious data. In such a case, wubi seems to be the least of possible evils, with no good solution available.

On my 2005-era HP laptop, I wasn't able to install Xubuntu alongside WinXP Pro even after explicitly making room for it on a second physical drive. For some reason, the box would not read the entire CD although the CD tested okay and installed properly on other boxes. As a compromise, I installed via wubi and that worked. It wasn't noticeably slower than native installs on older, slower boxes, and let me experiment a bit on the laptop. Just before I gave the laptop to a son's family, after cleaning it of all personal files and the wubi installation, I did manage to get a side-by-side installation of 12.04.1 working properly so that they could get a taste of Xubuntu if they desired to do so, and it was not noticeably different in feel from the old wubi 8.04 installation.

I think wubi has a place, despite the problems associated with it. However I don't plan to try it again.

---

### Post by sidzen on 2012-12-12
No.

If dual-boot is too hard, use two hard drives (even in a laptop, time will be used more efficiently than fooling with WUBI)!

---

### Post by monkeybrain2012 on 2012-12-12
> **DuckHook said:**
> Yes, very valid point.

What about a working installation on USB stick/disk? I'm not talking about persistent USB and all its associated restrictions, but a real working install: only with journaling, swap, all write-intensive activity turned off? Just tried one of those (thanks to instructions/recommendations from @oldfred) and it's not bad. In fact, it works pretty well. If the install CD offered such a choice, possibly with caveats about how much slower such a system would be due to USB limitations, etc. I bet lots of people would choose it instead. Also has the advantage of not being blamed on Ubuntu if stick fails.

That is actually the best solution. I am now typing from  Ubuntu 12.04 installed in an external hard drive actually ( the partition is 150G ext4, the rest of the hard drive for other Linux distros and storage), it is for all intents and purposes my working OS right now(I have Ubuntu 11.04 on my internal drive, haven't get around to update it and plan to do it during the holidays)  It is fast and smooth and performance wise it is as good as an internal install, moreover I can boot it off different machines so it is portable, I even use it at work!

Installation in a flash drive is not as good though because it is a lot slower and flash drives tend to wear out with a lot of writing and rewriting.

If you want to do this just be careful that you install Ubuntu in the right drive and put the bootloader in the same drive (the external one)

To answer your original question, no, I don't think WUBI is worth the troubles for something limited and is essentially just a little more than a demo, the knowledge you gain from trouble shooting WUBI probably doesn't transfer.  I never used it. I started using Ubuntu with a real dual boot on a old machine, I used manual install instead of "Install along side" as I have more control that way. One month later I wiped Windows XP. 6 months later I wiped WIndows from my main machine as well after I have gained enough experience with Ubuntu on the old machine.

---

### Post by KiwiNZ on 2012-12-12
Like most things it has it's plus and minus sides. If Wubi fits your needs use it, if it doesn't fit don't use it.

Worth it? That value is in the hands of the beholder.

---

### Post by mJayk on 2012-12-12
> **sidzen said:**
> No.
 
If dual-boot is too hard, use two hard drives (even in a laptop, time will be used more efficiently than fooling with WUBI)!
 
 
Well thats a silly option for someone with no tech knowlage, don't you think?

---

### Post by monkeybrain2012 on 2012-12-12
> **mJayk said:**
> Well thats a silly option for someone with no tech knowlage, don't you think?

Not really, I had next to no tech knowledge when I started (dual booting with Ubuntu's own partition). I made a full installation in a usb flash drive using a tutorial online in just a few weeks. Then I found it too slow and and bought an external hard drive a few months later. All you need to know actually is where to put the bootloader.

---

### Post by mJayk on 2012-12-12
> **monkeybrain2012 said:**
> Not really, I had next to no tech knowledge when I started (dual booting with Ubuntu's own partition). I made a full installation in a usb flash drive using a tutorial online in just a few weeks. Then I found it too slow and and bought an external hard drive a few months later. All you need to know actually is where to put the bootloader.
 
Well I'd probably say you had some tech knowlage, considering hard drivers are tech and you had knowlage of what to buy and how to install it.
 
Again all you know is some actual tech knowlage.
 
Nobody forces anybody to use WUBI but it fills a gap and allows some people to experience ubuntu, if its useful for them then fine.  Nobody is restricted to it.

---

### Post by monkeybrain2012 on 2012-12-12
> **mJayk said:**
> Well I'd probably say you had some tech knowlage, considering hard drivers are tech and you had knowlage of what to buy and how to install it.
 
Again all you know is some actual tech knowlage.
 
.

Well if you have no tech knowledge even at that level you probably wouldn't know about Ubuntu either.  If you know what an OS is and that computer != Windows you have some tech knowledge too. :)

---

### Post by mJayk on 2012-12-12
> **monkeybrain2012 said:**
> Well if you have no tech knowledge even at that level you probably wouldn't know about Ubuntu either. If you know what an OS is and that computer != Windows you have some tech knowledge too. :)
 
 
I really disagree I think ubuntu is very intuitive different people have different needs and I deffo think wubi serves its purpose very well.
 
Take people who dont really know anything about computers (granted not many of them about) they are just as clueless about windows and wubi gives them a good chance to try something new with very very little risk and with no trouble installing.
 
When I ask people to give it a go WUBI is one of the big sellers for them to at least try it and a month or two later they are duel booting.

---

### Post by bcbc on 2012-12-12
+1

I did a [survey]("http://ubuntuforums.org/showthread.php?t=1982669") on Wubi not too far back, and there was a clear distinction of those who would recommend Wubi.

> Who would recommend Wubi

For those that have never installed Wubi:
7% would recommend Wubi
93% would not.

For those that have installed Wubi, but no longer use it:
67% would recommend Wubi
33% would not.

For those that are currently using Wubi:
100% would recommend it (probably need to consider the sample size, the intention whether to keep using Wubi, and the length of time the users have used Wubi)

---

### Post by weasel fierce on 2012-12-12
THere's a lot of "what about people with no tech knowledge" concerns coming up, but I'm not sure that's terribly important.

If you want to install your own OS, there is no way around some level of tech knowledge, and that usually comes from looking things up.

I know people who have no idea how to reinstall Windows on their machine, and yet, sooner or later they find out how to do it, by trying and by looking things up.


Doesn't mean the barrier to entry should be artificially high, but at some point, you have to assume the user can figure out how to burn a CD.

---

### Post by bcbc on 2012-12-12
> **weasel fierce said:**
> <snip>
If you want to install your own OS, there is no way around some level of tech knowledge, and that usually comes from looking things up. 
<snip>
Doesn't mean the barrier to entry should be artificially high, but at some point, you have to assume the user can figure out how to burn a CD.

There is one way around it... it's called Wubi.

Canonical want market share, and that means going after all levels of users. They don't want any barriers, artificially high or not. What would be the point of creating artificial barriers anyway?

---

### Post by monkeybrain2012 on 2012-12-12
> **bcbc said:**
> There is one way around it... it's called Wubi.

Canonical want market share, and that means going after all levels of users. They don't want any barriers, artificially high or not. What would be the point of creating artificial barriers anyway?
I completely agree with Weaseal.

For someone to have heard about Ubuntu and have the curiosity to check it out would at minimal require some tech interests if not actual knowledge, from there to gain the minimal knowledge for a real dual boot is not difficult, I started off just by googling and nothing more, I didn't even know about UF. 

It is unrealistic to expect any less in terms of tech competence and interest.

WUBI install is not trivial either if your targets are the lowest common denominator users with NO tech knowledge or curiosity whatsoever like my dad (even assume for argument's sake that by some magic they know about Ubuntu and want to try it out). You would be surprised to know how many such users can't even install a Windows program with confidence. I have suggested a friend to install Libreoffice for over a year (in Windows) and he still hasn't done it because he says he is too busy to find out. There is nothing to find out, just download the .exe and click it! I even sent him the link. He has an old copy of MSO 2003 which someone has installed for him years ago and that's all he uses for basic word processing (he publishes in academic journals) . It is unrealistic to try to promote Ubuntu to such users.

Finally, getting WUBI to work can be frustrating as evidenced by the many threads on the support forums. It has its own peculiar bugs and limitations and often it is hard to get help on UF because most people here don't use it (you seem to be the only go to person apparently). So if you are actually spending time to trouble shoot it (thus not barrier free) why not do something more stable and performs better instead?

---

### Post by bcbc on 2012-12-12
The way I look at it, if a user has a problem with Wubi and gets no help, how likely are they to just trust that they'll get help when they have a normal install?

Many problems people have with Wubi will be the same as with Ubuntu, because it's a driver issue or some partitioning errors etc. 

So helping Wubi users also helps them eventually use a normal Ubuntu. That's why they have the ability to migrate a Wubi install to a normal install.

I think it's kind of sad that a Wubi user with a problem gets told repeatedly that Wubi is the problem and a normal dual boot will solve everything. That's just not accurate and gives Ubuntu a bad name. If Wubi should be removed, you should tell Canonical, not the poor user who installed it.

---

### Post by monkeybrain2012 on 2012-12-12
> **bcbc said:**
> 

So helping Wubi users also helps them eventually use a normal Ubuntu. That's why they have the ability to migrate a Wubi install to a normal install.


Yes indeed, I just found out you can migrate WUBI. I read the instructions and in Zeus' name I can't see how that is easier than just doing a dual boot in the first place. :) In fact it sounds a lot more complicated. That is ironic given the intended purpose of Wubi.

---

### Post by bcbc on 2012-12-12
> **monkeybrain2012 said:**
> Yes indeed, I just found out you can migrate WUBI. I read the instructions and in Zeus' name I can't see how that is easier than just doing a dual boot in the first place. :) In fact it sounds a lot more complicated. That is ironic given the intended purpose of Wubi.

Which part is too complicated for you? Partitioning, downloading the script, or entering a single command in the terminal?

---

### Post by monkeybrain2012 on 2012-12-12
> **bcbc said:**
> Which part is too complicated for you? Partitioning, downloading the script, or entering a single command in the terminal?


How is it easier than dual booting?

---

### Post by bcbc on 2012-12-12
How is the ease of dual-booting related?

What you have here is a user who has spent some time using Wubi, installing programs and customizing it, who would have to partition anyway to install a dual boot, but instead of starting from scratch can easily migrate their existing install with a single command.

No one's forcing anyone to migrate. They can do a clean install if they prefer or use alternative techniques to backup settings and data.

So why do you think migrating is complicated again?

---

### Post by monkeybrain2012 on 2012-12-12
> **bcbc said:**
> How is the ease of dual-booting related?

What you have here is a user who has spent some time using Wubi, installing programs and customizing it, who would have to partition anyway to install a dual boot, but instead of starting from scratch can easily migrate their existing install with a single command.

No one's forcing anyone to migrate. They can do a clean install if they prefer or use alternative techniques to backup settings and data.

So why do you think migrating is complicated again?

Well I just go by your tutorial.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

It is not complicated for me, but complicated enough to have to use a few terminal commands, this doesn't back your advertisement that WUBI is barrier free for users without tech knowledge,--at least you don't have to fool with the terminal and command lines with the Ubuntu installer (it is all clicking and checking boxes). 

Since I don't use Wubi I cannot say how well the script works or how long does it take to migrate. Hope it is less trouble prone that distro upgrades.

Wubi just seems to be a very round about way to do things which could have been done much more directly.

---

### Post by bcbc on 2012-12-12
First you argue that anyone wanting Ubuntu should be able to learn the technical know-how beforehand. Now you're arguing that someone who has learned Ubuntu won't be able to run a terminal command.

There's an evolution:
1. User with no Ubuntu knowledge and doesn't want to (or know how to) partition
2. Learns Ubuntu and likes it, wants to make it permanent.
3. Is now able to partition
4. Has to run a terminal command.

---

### Post by leclerc65 on 2012-12-12
Friends and relatives come to me only when their Windows machines get very sick. I usually told them: "I can mail you an Ubuntu CD, boot it up and use option 'Erase and use the entire disc'.:D".

---

### Post by monkeybrain2012 on 2012-12-12
deleted for double posting.

---

### Post by monkeybrain2012 on 2012-12-12
> **bcbc said:**
> First you argue that anyone wanting Ubuntu should be able to learn the technical know-how beforehand. Now you're arguing that someone who has learned Ubuntu won't be able to run a terminal command.

There's an evolution:
1. User with no Ubuntu knowledge and doesn't want to (or know how to) partition
2. Learns Ubuntu and likes it, wants to make it permanent.
3. Is now able to partition
4. Has to run a terminal command.

Having "Ubuntu knowledge" doesn't follow you know  how to do partition, I can't imagine any day to day use of Ubuntu desktop that would require knowledge of partitioning. On the other hand it is not difficult to learn (google and 5 minutes of reading) partitioning without prior knowledge of Ubuntu,

BTW, live usb, installation in usb flash drives or external drives don't require partitioning. Installing with the "installing alongside" option also doesn't require the user to do partition manually.

---

### Post by bcbc on 2012-12-13
> **monkeybrain2012 said:**
> Having "Ubuntu knowledge" doesn't follow you know  how to do partition, I can't imagine any day to day use of Ubuntu desktop that would require knowledge of partitioning. On the other hand it is not difficult to learn (google and 5 minutes of reading) partitioning without prior knowledge of Ubuntu,

BTW, live usb, installation in usb flash drives or external drives don't require partitioning. Installing with the "installing alongside" option also doesn't require the user to do partition manually.

So you're saying that Ubuntu knowledge doesn't mean you know how to partition, but 5 minutes on google is enough to learn. While at the same time saying you don't need to partition to install Ubuntu, but it's the partitioning that makes the migration complex? Did I get everything?

When I said:
*1. User with no Ubuntu knowledge and doesn't want to (or know how to) partition*

I did not say that the lack of Ubuntu knowledge implies the inability to partition. I said that a [Wubi] User may have no ubuntu knowledge, and might also not want to partition to find out about Ubuntu, or in fact might not be able to partition at all.

And when I said:
*3. Is now able to partition*

I did not mean (nor is it reasonable to deduce that I meant) that somehow by way of using Ubuntu with Wubi they have magically come to understand how to partition.

That's what is known as a straw man argument (or at least that's what 5 minutes of google gets you)

---

### Post by KiwiNZ on 2012-12-13
@  monkeybrain2012 and bcbc, agree to disagree. Closed for now

---

