---
title: "Help me help someone with Windows."
date: 2010-10-04
forum: The Cafe
---

### Post by kaldor on 2010-10-04
My father has a 6 year old HP with Windows XP. 512 MB RAM, 2.1 Ghz.

It is slow to a snail's pace and freezes a LOT.

So here's the situation:

1) He needs to get stuff done
2) He won't use a Linux distro 
3) He won't reformat/reinstall XP
4) He won't touch/let me touch the registry
5) He won't get a new computer

Basically he's stuck with a computer that won't work anymore and refuses to fix it out of fear of learning. 

He had to rush to get somewhere today and I'm stuck here trying to get stuff working. His AV is fine, etc.

But what can I do to "clean up" Windows? It's unusable (by my standards, to him it's perfectly fine so he says) and it's the first time I've actually sat down to his PC in a very long time; it's bad! :(

Basically, I need to know... what would you do? Aside from defragging, I don't really have any ideas on what to do. 

If I help, he gets mad at when I change stuff I fixed his screen resolution and he panicked and demanded I put 800x600 back on a 15 inch monitor because he was "used to it". If I *don't* fix something, he blames it on me for "trying to make me look stupid". So either way is a loss. I just want the constant nags for computer help to go away, and it's hard when he won't let me help him. 

I've been out of touch with Windows for so long :(

Note: The annoying part is that I convinced my mother to buy a Mac; she's worse than he is, and she never bothers me with problems anymore unless it's a legitimate one. My dad refuses to use the Mac, insisting it's too hard to adjust to something new. So here we are... see my situation? :)

Edit: No, this isn't FUD or Windows-bashing; it's his own fault. Also, please don't reply with "install Ubuntu and make it look like XP" ;)

---

### Post by mendhak on 2010-10-04
OK - he basically wants the thing he's accustomed to working.  Go to appwiz.cpl (start > run > appwiz.cpl) and look at the list of things installed there.  Remove anything that isn't needed.  If you ask him, he'll say "Oh but I might need xyz at a later point" - if it's a might need or little used, then remove it.  You need to uninstall and try and get it to as few applications as possible.

Next, clean up the temp folder.

Next, look for other services which hog resources - does he have Windows Desktop Search on? You'll also want to disable services that aren't important.  To do this go to services.msc (Start > run > services.msc).  Order by 'status' so that the Started ones are at the top.  Then compare that list with [this list here](http://www.theeldergeek.com/services_guide.htm).  If you scroll down you'll find the names.  For each of those links, you'll find a description and whether it is 'needed' for a general user.  This is a slow process but you'll find that a bunch of services can be turned off and that helps with resources.

Can you disable the XP theme without him complaining?

---

### Post by cascade9 on 2010-10-04
> **kaldor said:**
> My father has a 6 year old HP with Windows XP. 512 MB RAM, 2.1 Ghz.
1) He needs to get stuff done
2) He won't use a Linux distro 
3) He won't reformat/reinstall XP
4) He won't touch/let me touch the registry
5) He won't get a new computer


If it was me, I'd let him deal with it ;) 

But if you really want to help, aside from the usual defragging, I'd remove anything thats not in use anymore (all that cruft wont be helping) and run ccleaner a few times, including the registry cleaner......I've never, ever seen any issues from running the registry cleaner on ccleaner, and I've run it on literally hundreds of computers.   

[http://www.piriform.com/ccleaner](http://www.piriform.com/ccleaner)

Updating the motherboard,. video card, LAN, and sound card drivers would be a good idea as well.

---

### Post by kaldor on 2010-10-04
> Updating the motherboard,. video card, LAN, and sound card drivers would be a good idea as well.

Good luck getting that to work out ;)


I'll check out the registry cleaner.. how well has it worked for you in the past? It feels like speeding this up is out of the question right now :)

As for the unneeded programs, he does a surprisingly good job of weaning those out... no worries there.

---

### Post by pwnst*r on 2010-10-04
> **kaldor said:**
> It's unusable (by my standards, **[COLOR="Red"]to him it's perfectly fine so he says[/COLOR]**) 

This right here should be your answer.  Leave his **** alone.

---

### Post by kaldor on 2010-10-04
> **pwnst*r said:**
> This right here should be your answer.  Leave his **** alone.

So what do I do when he asks me for help on a daily basis? I've done that (leaving sh** alone) for the last few years. Try being more mature.

Edit: The problem isn't directly related to the speed. It's related to performance getting in the way of use/fixing issues. How can he fix something when he needs to reboot every few minutes after a lock up? How am I supposed to fix anything when it just locks up? This isn't a Windows-sucks-use-ubuntu-thread. 

The computer can sit there and it'll be fine. But try getting work done on it, and programs will begin to stop responding, screen will freeze up, etc.

---

### Post by marin123 on 2010-10-04
dont do registry cleaner, i messed my xp with that... especially if the computer is a mess...
second, see apps that run on startup (Start -> Run -> msconfig.exe), and shut down everything thats not needed (like update managers), it will speed up the startup...

or second scenario... save Desktop and His Documents and format the HDD. he will be pissed but only for a few days ;)
just kidding, i know your situation... fix laptop but dont touch anything... :S

---

### Post by kaldor on 2010-10-04
> **marin123 said:**
> dont do registry cleaner, i messed my xp with that... especially if the computer is a mess...
second, see apps that run on startup (Start -> Run -> msconfig.exe), and shut down everything thats not needed (like update managers), it will speed up the startup...

or second scenario... save Desktop and His Documents and format the HDD. he will be pissed but only for a few days ;)
just kidding, i know your situation... fix laptop but dont touch anything... :S

Nothing runs on startup apart from the antivirus stuff/essential Windows stuff. 

And yes... "fix it but don't touch it".

Edit: Holy crap.. over 2000 files in the Temp directory!

---

### Post by roggenschrotbrot on 2010-10-04
you should really upgrade the memory imo. 512mb is not enough with sp3, anti-virus software and maybe a browser running of office suite.
edit: also you might want to check the current memory, it being broken might very well be a reason for the lock ups.

---

### Post by kaldor on 2010-10-04
> **roggenschrotbrot said:**
> you should really upgrade the memory imo. 512mb is not enough with sp3, anti-virus software and maybe a browser running of office suite.

He won't do it. I'm trying to get his computer to the "make-do" point. It's hard when you can't do anything with it.

So far, the cleanup is going alright.

---

### Post by mendhak on 2010-10-04
> **kaldor said:**
> He won't do it. I'm trying to get his computer to the "make-do" point. It's hard when you can't do anything with it.

So far, the cleanup is going alright.
Kaldor, did you have a look at my post, try the things out?

---

### Post by Señor Banana on 2010-10-04
Tuneup Utilities

---

### Post by roggenschrotbrot on 2010-10-04
> **kaldor said:**
> He won't do it. I'm trying to get his computer to the "make-do" point. It's hard when you can't do anything with it.

So far, the cleanup is going alright.
yeah, been there before ;)

but to be honest all xp-setups i supported before migrating them to linux had this problem 512 was fine for text/editing surfing up to sp2, but the installations would slowly become unuseable with sp3, even even using fresh reinstalls. afaik there are minimal xp installations which offer a impressively small memory footprint, so there should be tutorials to resize an allready installed xp.

---

### Post by ronnielsen1 on 2010-10-04
> If it was me, I'd let him deal with it

:P

Sounds like your hands are tied. My father-in-law had a p3 with 256 Meg memory (The real expensive kind) that ran XP real slow but Puppy lightning fast.
I've showed him ubuntu, puppy, knoppix, etc and he's impressed but he doesn't know what to do.
Now he has new computers running windows 7 and he's trying to learn a new operating system

---

### Post by MooPi on 2010-10-04
Let it die !!!!!
I know it's a brutal approach but if your dad wants to stick his head in the sand let him. If he can see the speed of your computer and he thinks that his is fine by comparison, the so be it. When it does go belly up just let him know that you'd be happy to help build or install Linux on his new computer and gently nudge him towards Linux if he can't maintain his Windows computer.
 I convinced a friend once that a format and reinstall was his only choice because I found numerous virus on his computer. In reality there were only a few but they were nasty and impossible to ferret out completely. he was completely over joyed by the results and all data was saved. Happy ending. Sometimes what they don't know is better.

---

### Post by Zlatan on 2010-10-04
> **kaldor said:**
> My father has a 6 year old HP with Windows XP. 512 MB RAM, 2.1 Ghz.

It is slow to a snail's pace and freezes a LOT.

So here's the situation:

1) He needs to get stuff done
2) He won't use a Linux distro 
3) He won't reformat/reinstall XP
4) He won't touch/let me touch the registry
5) He won't get a new computer

Basically he's stuck with a computer that won't work anymore and refuses to fix it out of fear of learning. 

He had to rush to get somewhere today and I'm stuck here trying to get stuff working. His AV is fine, etc.

But what can I do to "clean up" Windows? It's unusable (by my standards, to him it's perfectly fine so he says) and it's the first time I've actually sat down to his PC in a very long time; it's bad! :(

Basically, I need to know... what would you do? Aside from defragging, I don't really have any ideas on what to do. 

If I help, he gets mad at when I change stuff I fixed his screen resolution and he panicked and demanded I put 800x600 back on a 15 inch monitor because he was "used to it". If I *don't* fix something, he blames it on me for "trying to make me look stupid". So either way is a loss. I just want the constant nags for computer help to go away, and it's hard when he won't let me help him. 

I've been out of touch with Windows for so long :(

Note: The annoying part is that I convinced my mother to buy a Mac; she's worse than he is, and she never bothers me with problems anymore unless it's a legitimate one. My dad refuses to use the Mac, insisting it's too hard to adjust to something new. So here we are... see my situation? :)

Edit: No, this isn't FUD or Windows-bashing; it's his own fault. Also, please don't reply with "install Ubuntu and make it look like XP" ;)

some guys like "give me a hyunday to make me a world rally champion" style stuff... do nothing and make it work. i would help if he would let me do my things...

---

### Post by cascade9 on 2010-10-04
> **kaldor said:**
> Good luck getting that to work out :wink:


I'll check out the registry cleaner.. how well has it worked for you in the past? It feels like speeding this up is out of the question right now :smile:

As for the unneeded programs, he does a surprisingly good job of weaning those out... no worries there.

The registry cleaner has helped me out in the past, quite often. Runnign ccleaner is the 1st or 2nd thing I try when I get old windows machines that need fixing, but I cant teinstall the OS.  

In most cases, any speed improvements from cleaning the regisry have been less than cleaning windows and the applications out, but it helps, and so far its been 100% safe for me. 

> **roggenschrotbrot said:**
> yeah, been there before ;)

but to be honest all xp-setups i supported before migrating them to linux had this problem 512 was fine for text/editing surfing up to sp2, but the installations would slowly become unuseable with sp3, even even using fresh reinstalls. afaik there are minimal xp installations which offer a impressively small memory footprint, so there should be tutorials to resize an allready installed xp.

Those 'minimal XP' versions would have been done with nLite. Its a great tool, if you want to remove a lot of  useless stuff from windows, but you do have to reinstall. 

Persoanlly, I never had any issues with XP SP3 on 512MB machines. Its hardy a speed demon (well, unless you nlite the hell out of it) but its runs fine IMO. My mum is currently using a 512MB XP SP3 install, no problem. 

BTW, when I was on XP SP3 I found that the worst thing for slowing the system down was antivirus. So I used to run without AV, and install it just before a format/reinstall to check I wasnt getting nasty viruses (I never got anything major, just a trojan or two, and they couldnt talk to the net anyway cause I didnt use XPs useless 'one way' firewall.).

---

### Post by eriktheblu on 2010-10-04
[http://notalwaysright.com/mission-impossible/175]("http://notalwaysright.com/mission-impossible/175")

---

### Post by kaldor on 2010-10-04
> **mendhak said:**
> Kaldor, did you have a look at my post, try the things out?

Yep, and so far so good. :)

---

### Post by Zlatan on 2010-10-04
> **eriktheblu said:**
> [http://notalwaysright.com/mission-impossible/175]("http://notalwaysright.com/mission-impossible/175")

^this^
;]]

---

### Post by kaldor on 2010-10-04
ccleaner has been doing a good job so far, nothing messed up yet.

It's so much easier to fix things when he isn't looking over my shoulder and freaking out whenever I do something (be it opening Firefox to google a problem even).

6 years of daily use without barely even a defrag, and never a registry cleanup... not fun.

---

### Post by Naiki Muliaina on 2010-10-04
If he nags you to help, take him into a PC world (if your in the UK), point to the Tech Guys area and say 'Look, £400 to clean a PC'. Then either say take it there, or let you do what you want to it. 

I would say if you are out of touch with Windows though, don't do anything to it. I find myself utterly out of touch with Windows nowdays and cant make head nor tail of it. If you touch it and break it more then you will look stupid and it will give him something to moan about.

---

### Post by kaldor on 2010-10-04
> **Naiki Muliaina said:**
> If he nags you to help, take him into a PC world (if your in the UK), point to the Tech Guys area and say 'Look, £400 to clean a PC'. Then either say take it there, or let you do what you want to it. 

I would say if you are out of touch with Windows though, don't do anything to it. I find myself utterly out of touch with Windows nowdays and cant make head nor tail of it. If you touch it and break it more then you will look stupid and it will give him something to moan about.

He's done that before... paid lots of money to remove a virus (didn't trust me to do it).

Update..

-I've cleaned out the TEMP directory.
-Ran a defrag
-Used ccleaner to fix up the registry a bit
-Turned off some eye candy (window shadow, etc)
-Removed a couple of old programs that haven't been seen in years.

Still pretty slow, but slightly improved. What else?

---

### Post by donkyhotay on 2010-10-04
> **MooPi said:**
> Let it die !!!!!
I know it's a brutal approach but if your dad wants to stick his head in the sand let him.

+1

The time will come when it'll finally fail completely and he'll need to learn a new system anyway (like when the HD goes for example). The sooner he realizes it the better. I'd leave the computer alone and wait for it to go out on it's own in the next year or so. He'll have lost everything and probably be incapable of replacing XP (hard to get legit copies anymore). He will then have learned a very valuable lesson about computers. Definitely let him know that when updates occur it's important to learn new systems as the longer he waits the more different things become and the harder it is to learn the new system.

---

### Post by forrestcupp on 2010-10-04
> **cascade9 said:**
> and run ccleaner a few times, including the registry cleaner......+1 for ccleaner.  It's excellent.

> **pwnst*r said:**
> This right here should be your answer.  Leave his **** alone.
It sounds immature, but on the other hand, it's kind of immature for your dad to want you to make his computer work without letting you do the necessary things that will make it work.

I'd run ccleaner a few times, remove all unnecessary software running in the background, and if that doesn't take care of it, tell him there's nothing more you can do within the limitations he has set.  Sometimes you just have to be firm with people.  I once had someone try to get me to fix their ancient desktop when they have a new laptop.  I told them it wasn't worth fixing and they need to throw it to the bin.  That was kind of liberating because up until that point, I just caved in to whatever computer needs anyone had.

---

### Post by kaldor on 2010-10-04
Seems like all is fine now. Maybe now when he calls for help I won't have to make coffee while waiting for Windows Explorer to load up.

Thanks for the help :)

---

### Post by mamamia88 on 2010-10-04
when i clean my parents computer first thing i do is remove all unneeded applications.  then i run malwarebytes and spybot, then i clean the registry with ccleaner about 5 times, and finally i run deep optimize on iobit smart defrag a couple times.  that seems to work pretty well.

---

### Post by marin123 on 2010-10-04
> **mamamia88 said:**
> when i clean my parents computer first thing i do is remove all unneeded applications.  then i run malwarebytes and spybot, then i clean the registry with ccleaner about 5 times, and finally i run deep optimize on iobit smart defrag a couple times.  that seems to work pretty well.

i put ubuntu on my home desktop :) it did the trick ;)

---

### Post by mamamia88 on 2010-10-04
it sure will but the op said his father refuses to use a linux distro

---

### Post by Dustin2128 on 2010-10-04
> **MooPi said:**
> Let it die !!!!!
I know it's a brutal approach but if your dad wants to stick his head in the sand let him. If he can see the speed of your computer and he thinks that his is fine by comparison, the so be it. When it does go belly up just let him know that you'd be happy to help build or install Linux on his new computer and gently nudge him towards Linux if he can't maintain his Windows computer.
 I convinced a friend once that a format and reinstall was his only choice because I found numerous virus on his computer. In reality there were only a few but they were nasty and impossible to ferret out completely. he was completely over joyed by the results and all data was saved. Happy ending. Sometimes what they don't know is better.

This +9001

---

### Post by marin123 on 2010-10-04
> **mamamia88 said:**
> it sure will but the op said his father refuses to use a linux distro

i know, i have read that... unless he uses some specific windows programs, there's no reason why not switching to linux... my mom only uses firefox and IM client and she wants to be able to see photos and maybe maybe listen to music... in ubuntu everything is straightforward, and makes me worry less about spyware, viruses, trojans and stuff...
my dad actually installed a virus named Security center on his xp and it didnt allow him to run any program...  this is not likely to happen on ubuntu, even for someone who doesnt know how to put file on his flash drive :D

---

### Post by kaldor on 2010-10-04
> **marin123 said:**
> i know, i have read that... unless he uses some specific windows programs, there's no reason why not switching to linux... my mom only uses firefox and IM client and she wants to be able to see photos and maybe maybe listen to music... in ubuntu everything is straightforward, and makes me worry less about spyware, viruses, trojans and stuff...
my dad actually installed a virus named Security center on his xp and it didnt allow him to run any program...  this is not likely to happen on ubuntu, even for someone who doesnt know how to put file on his flash drive :D

He doesn't do very much with a PC either (word process, print, web browse) but that doesn't mean I can just wipe his HD against his will and force another OS on him.

---

### Post by Dustin2128 on 2010-10-04
> **kaldor said:**
> He doesn't do very much with a PC either (word process, print, web browse) but that doesn't mean I can just wipe his HD against his will and force another OS on him.
Make a persuasive argument maybe? Like:
"if you let me install linux to your hard drive (it can even be a dual boot) you'll never need me to do this again"

---

### Post by Crazedpsyc on 2010-10-04
> **cascade9 said:**
> I've never, ever seen any issues from running the registry cleaner on ccleaner, and I've run it on literally hundreds of computers.   
[http://www.piriform.com/ccleaner](http://www.piriform.com/ccleaner)


I agree very much with this. Ccleaner (crap cleaner) is excellent at removing what I call Sewer Slime from the computer such as cookies, registry bugs, etc. 
Also try Piriform's defraggler to defragment it (very very very very very slow but useful)

---

### Post by t0p on 2010-10-04
OP: why not make sure all your dad's data is backed up, then nudge the machine towards some kind of irretrievable destruction.  It'll cost a few quid to buy a replacement, but you can get some pretty good hardware for not too much money nowadays.  If you *have* to buy a new computer with Windows 7 installed, you can set it up as an Ubuntu dual-boot.  Once the deed is done, maybe your dad will warm to the idea of the New.  And if not... well, I've heard that 7 is a big improvement on XP so it wouldn't be a total loss.

---

### Post by Zlatan on 2010-10-05
> **kaldor said:**
> He doesn't do very much with a PC either (word process, print, web browse) but that doesn't mean I can just wipe his HD against his will and force another OS on him.

Wait for your dad asking for more help with Windows in a month...
I was pretty lucky to convince my parents to put "something better than Windows" on their PC. Now I don't even need a remote connection to their Ubuntu :D Having a glass of beer with my dad instead of messing with Windows:)

---

### Post by zer010 on 2010-10-05
Really, a reinstall of XP is the best bet. It seems that Win* usually needs it every now and then. However, if you don't have an XP CD, this might not be possible.  I've seen some great suggestions that I use personally and for my family. 

1. CCleaner is awesome! Run the cleaner with most of everything checked. Clear freespace if you have time. Use other advanced options at your discretion. Run the Registry cleaner. I never backup the registry as I've never had any issues.

2. Defrag, defrag, defrag. Defraggler is great, but is even better when used in conjunction with the native defragger. Run the XP defragger twice, run the Defraggler's "Defrag Free Space" then run "Defrag Drive". It will leave almost no fragmentation. 

3. Revo Uninstaller. This handy program is a whiz at cleanly uninstalling apps. 

4. msconfig. Personally, I disable EVERYTHING  and enable only those things that are TRULY needed at startup. Usually, I don't have anything enabled. Antivirus might be a must for someone who is not net savvy.

5. Antivirus. Depending on what AV is used, an active AV can hog a LOT of RAM and other resources, especially Nortons. If I were to run an AV, I would go with either Avast! or Avira, both free.

6. My Computer>Properties: Go to the Advanced tab and choose "Performance". In the "Visual Effects" tab,uncheck everything except for the last one, "Visual styles on windows and buttons". "Apply" and go to the "Advanced" tab and 'Change' "Virtual Memory".  Set the minimum at about 756MB and max at about 1512MB. Apply and OK back to the desktop. 

That's about all I can think of for now. Just going through this list makes me love Linux all over again!

---

### Post by oobuntoo on 2010-10-05
Buy a new hard drive, unplug the old hard drive, install the new hard, then install windows xp on the new hard drive. If everything goes well, use the old hard drive as the secondary drive and copy over all his old files to the new one and reinstall all other software that he uses. 

If he still doesn't like it, put the old drive back in as before and tell him to go screw himself :-# Just kidding about the last part :mrgreen:

---

### Post by RainPhantom on 2010-10-05
[http://home.comcast.net/~SupportCD/OptimizeXP.html](http://home.comcast.net/~SupportCD/OptimizeXP.html)

---

### Post by 98cwitr on 2010-10-05
first things first...msconfig the startup apps. Then run ccleaner (which will let you touch the registry), superantispyware, and uninstall whatever antivirus software he's got and install avast (unless he's already got avast).

---

### Post by marin123 on 2010-10-05
> **kaldor said:**
> He doesn't do very much with a PC either (word process, print, web browse) but that doesn't mean I can just wipe his HD against his will and force another OS on him.

why not? thats what windows would do :D haha

---

### Post by whiskeylover on 2010-10-05
Install Hannah Montana linux on his computer.

---

### Post by Spice Weasel on 2010-10-05
[Linux disguised  as XP.]("http://www.gazlap.hu/uhu/s-themes/icewm-theme-silverxp.jpg")

Install icewm and icewm-themes. Style is silverxp. E: There's also a blue one in that package.

Why not? It's a good idea.

---

### Post by Elfy on 2010-10-05
Well I think you got enough help - this is not going anywhere now. Closed.

---

