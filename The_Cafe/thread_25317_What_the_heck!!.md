---
title: "What the heck!?!?"
date: 2005-04-09
forum: The Cafe
---

### Post by telmo on 2005-04-09
I have Windows XP Pro and Ubuntu Hoary installed in my laptop. Previously i was running Warty and Windows. And i found out something that really sucks. Ubuntu is much slower than Windows! And i mean... a lot!

Why is this so? I have a P4 3.06Ghz 768Mb RAM and a 80Gb 5400RPM HD... everything runs pretty smooth in Windows, even with my antivirus/antispyware/firewall/etc. eating my memory out. But in Ubuntu whatever task i do... openening a window or opening... everything (And OpenOffice!?!? ! It takes forever!) it just starts to 'think' or something, before actually doing it! I hate it! Not the O.S. itself, don't get me wrong. I LOVE Ubuntu, and i'm pretty sure that i want to stick to Hoary for a while, but what is happening? Is there something i can do about it?

I tried every performance tweak i saw in this forum, and i've even managed to get my 3D acceleration in my ATI 9600 going... but it's just not enough! Everything is just damn slow! :(

---

### Post by edubarr on 2005-04-09
Have you tried to improve your disk access time with hdparm? Maybe this can help you out.
[http://www.ubuntuforums.org/showthread.php?t=24416&highlight=hdparm](http://www.ubuntuforums.org/showthread.php?t=24416&highlight=hdparm)

Another thing you could try is a custom kernel, one that is optimized for your P4.

---

### Post by KiwiNZ on 2005-04-09
Some details might help folks help you .
eg whatprocesses are running including background , what mem usage , what is your partition setup, 
Also some  benchmarks would be usefull

---

### Post by jdong on 2005-04-09
Ok... First off, please tone down your language a bit. Some members of our forum may be offended. Also keep in mind that this is the primary end-user support outlet for Canonical, Ltd's product. Treat us like you'd treat tech support officials (err, **NOT** like AOL support... ;))

Can you please elaborate on exactly what's slow? 
[list]
[*]If you minimize/maximize/minimize/maximize, is the redraw  slow [X/GUI configuration issue]?   
[*]If you start a new program, is it slow to load, with lots of hard disk activity?  Does it start significantly faster the second time around? (DMA/hdparm tweaking) 
[/list] 
If you feel it's a disk issue, please issue the following command at a console, then post the output:

```

time dd if=/dev/zero of=/tmp/bigtestfile bs=1M count=500

rm /tmp/bigtestfile

```

This will write a 500MB file full of zero's and time how long it took to do so.




NOTE: Openoffice.org is a behemoth. It's gonna be slow to load, whether it's on Windows or Linux. It takes 20 seconds to start on my AMD64+RAID0 machine; it's not abnormal for it to take 45 seconds to start the first time! There are quickstart applets to keep a copy preloaded, but I find it pointless. Just start off a copy and minimize it at the beginning of the day. Shove it off to Workspace4 if it gets in your way. Any subsequent Openoffice apps will launch in an instant. Linux's superb memory management will be able to efficiently and responsively swap out Openoffice.org when you don't use it. :)

---

### Post by telmo on 2005-04-09
[QUOTE=edubarr]Have you tried to improve your disk access time with hdparm? Maybe this can help you out.
[http://www.ubuntuforums.org/showthread.php?t=24416&highlight=hdparm](http://www.ubuntuforums.org/showthread.php?t=24416&highlight=hdparm)

Another thing you could try is a custom kernel, one that is optimized for your P4.[/QUOTE]

Yep! I tried it! Actually it's the best performance tweak i've done so far. (as i said on that thread.) :)

[QUOTE=kiwiNZ]Some details might help folks help you .
eg whatprocesses are running including background , what mem usage , what is your partition setup,
Also some benchmarks would be usefull[/QUOTE]

thx. I'll see if i can post some pictures here...

---

### Post by telmo on 2005-04-09
> **jdong]Ok... First off, please tone down your language a bit. Some members of our forum may be offended. Also keep in mind that this is the primary end-user support outlet for Canonical, Ltd's product. Treat us like you'd treat tech support officials (err, **NOT** like AOL support...  said:**
> 
[*]If you minimize/maximize/minimize/maximize, is the redraw  slow [X/GUI configuration issue]?   
[*]If you start a new program, is it slow to load, with lots of hard disk activity?  Does it start significantly faster the second time around? (DMA/hdparm tweaking) 
[/list] 
If you feel it's a disk issue, please issue the following command at a console, then post the output:

```

time dd if=/dev/zero of=/tmp/bigtestfile bs=1M count=500

rm /tmp/bigtestfile

```

This will write a 500MB file full of zero's and time how long it took to do so.



Sorry about the language thing!  I didn't really know that is was somekind of an insult. I'm from far away kingdom.  O:) 

Here is my 500Mb of 0 writting benchmark:

500+0 records in
500+0 records out
524288000 bytes transferred in 25.764153 seconds (20349514 bytes/sec)

real    0m26.521s
user    0m0.001s
sys     0m1.342s

I don't know if that's slow or fast. I've never tried it before. But i think it's something related to Gnome/Ubuntu itself. Just a guess...

As you asked before, yes... when i open any kind of program the second time it's faster.

Now, i'd really like to post some pictures of the running processes for you to see, but i don't really know how!  :shock: 

And i don't know what kind of benchmark utilities i can use to try on my laptop...! (god... i'm soooo lame! :( )

Maybe if you could only help me with these two (sorry, i don't like to ask this much), i could post something of some interest here...

thx!

---

### Post by Ubunted on 2005-04-09
Not sure if you said you'd done this yet, but try the 686 kernel like I did. It seems to boot faster for me anyway.

[http://www.ubuntuforums.org/showthread.php?t=25038](http://www.ubuntuforums.org/showthread.php?t=25038)

---

### Post by shimon on 2005-04-09
disable powernd

---

### Post by telmo on 2005-04-09
> Not sure if you said you'd done this yet, but try the 686 kernel like I did. It seems to boot faster for me anyway.

I have the 686 kernel.

> disable powernd

 :-? 
I don't really know how to do it, but isn't that supposed to be a nice feature? I don't want to lose functionality.

---

### Post by poofyhairguy on 2005-04-09
[QUOTE=telmo] But in Ubuntu whatever task i do... openening a window or opening... everything (And OpenOffice!?!? ! It takes forever!) it just starts to 'think' or something, before actually doing it! I hate it! Not the O.S. itself, don't get me wrong. I LOVE Ubuntu, and i'm pretty sure that i want to stick to Hoary for a while, but what is happening? Is there something i can do about it?
[/QUOTE]

Have you done this?

[http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink)

---

### Post by bvc on 2005-04-09
The first question is....
what is your chipset?

Everything else makes a minimal diff actually, compared to support in the kernel for your chipset. Newer chipsets (usually) have poor performance. The good news is that this is devel'd in the kernel rather quicky if it is a popular chipset.

But infact, I've always found linux's in general slower than win, especially debians. Sorry, but it's the truth, and I've done over 30 distros in 4 years on 2 pc's. Even now, I can load a webpage 3 times in xp before ubuntu begins to load it. Sometimes I swear my USR5610 External was faster than this braodband in linux ](*,)  ...(not at large downloads of course)

---

### Post by telmo on 2005-04-09
[QUOTE=bvc]The first question is....
what is your chipset?

Everything else makes a minimal diff actually, compared to support in the kernel for your chipset. Newer chipsets (usually) have poor performance. The good news is that this is devel'd in the kernel rather quicky if it is a popular chipset.

But infact, I've always found linux's in general slower than win, especially debians. Sorry, but it's the truth, and I've done over 30 distros in 4 years on 2 pc's. Even now, I can load a webpage 3 times in xp before ubuntu begins to load it. Sometimes I swear my USR5610 External was faster than this braodband in linux ](*,)  ...(not at large downloads of course)[/QUOTE]

That's exactly it! I must say, the first time i tried linux, i dropped it because it was too hard to configure, but... it was very fast! And that's one of the main reasons i chose linux over windows. Now... it's looking nice and sweet, but it's very slow compared to my windows. I also know, that one of these days, i have to loose a hole day defragging my windows and running a few scanners to check for virus and trojans and spyware and stupid cookies, bla bla bla... heck, i might even have to install it again...(i wish i wouldn't have to, anyway) but the speed.... oh, the speed! Where is it gone to???

I teach windows. And i must say... i'm fed up with it! I wish i could only remove it permanentely from my computers. (Of course can't do that until i have counter strike running smooth in my hoary :) ) but... damn it! I NEED speed! And every distro of linux is just getting too 'crowded'.

I'm sorry about all this... but i had to get it off my shoulders. But think about this... everytime someone asks what are the advantages of linux, everyone says speed and security? SPEED! Give me speed please! I read on this forum lots of times that Ubuntu is faster than windows... but it's not so on my laptop and i'm going nuts!  ](*,) 

*I definitelly need to sleep! LOL


edit: Yes! I did that prelink thing... not sure why. Everything's still the same. :(

---

### Post by jobezone on 2005-04-11
Hi
I'm not jobezone, I'm his brother (he *made* me write this, you'll see in a moment why, if you know him), why don't you try kde?

It's a **lot faster*** than Gnome for me, my brother also agrees (but prefers gnome). You can install it in synaptic by installing kubuntu-desktop and other packages that start with kubuntu.

When I say that it is a lot a faster, I mean faster than xp, honest to god, I swear it. I open million pages, load lots of apps, everything is always, always, I mean *always* FAST! I don't understand how it's possible by the way, because previously I agreed that linux was slower than windows, but this time, linux beats xp in terms of speed, stability ( in xp I have to be carefull, not letting a lot of programs to be loaded at the same time, in linux, sometimes I forget apps open, because the system is so good i didn't notice) 

p.s. - The swap size is very important, at least for me, I started with a 128 mega swap but then found that things were slow and I noticed that they started getting slow when the swap was full, so I doubled it, and now it's as I've described.
Dan
Try KDE!!!

---

### Post by kassetra on 2005-04-11
[QUOTE=jobezone]p.s. - The swap size is very important, at least for me, I started with a 128 mega swap but then found that things were slow and I noticed that they started getting slow when the swap was full, so I doubled it, and now it's as I've described.
[/QUOTE]

Typically, you want to make your swap size the same as your ram, or double your ram size.  :)

I always have my swap set to my ram size.

---

### Post by bvc on 2005-04-11
based on telmo's specs ,swap can't be an issue
telmo has more ram than I and mine is only touch when doing heavy graphics rendering and my swap is less than half my ram. Of course on my old box the swap is 3x my ram, so it just depends on your specs and what you are using the box for, as to what the swap should be.
```
free -m
             total       used       free     shared    buffers     cached
Mem:           504        389        115          0         28        212
-/+ buffers/cache:        148        356
Swap:          211          0        211
```

---

### Post by kassetra on 2005-04-11
[QUOTE=bvc]so it just depends on your specs and what you are using the box for, as to what the swap should be.
[/QUOTE]

Right... Which is why I said typically... For me, I need at least double the ram, and also double the swap I have now, because I dig into swap way too often:
 ```
 free -m
             total       used       free     shared    buffers     cached
Mem:          1012        687        324          0        119        310
-/+ buffers/cache:        257        755
Swap:         1027          0       1027
```

---

### Post by 23meg on 2005-04-11
i hear you telmo; i feel the exact same way. whenever i'm using Ubuntu i feel that *something* in there is making the system choke, that there's a horrible bottleneck that everything that should flow has to go through! 

maybe it's just some hardware compatibility problems with our computers, or we need some magic tweak that's hiding too far away to be googled.

---

### Post by telmo on 2005-04-11
This is what i have:

ntfs - 16 Gb
swap - 953 Mb
reiserfs (boot) - 95 Mb
xfs (system) - 20 Gb
fat32 (docs) - 37 Gb

...anything wrong here?

I'm now trying (and glad to) XFCE4. It seems a little faster, but still... only a little...

btw, system-monitor is telling me that swap is barely used (2,7mb of 953)

---

### Post by skoal on 2005-04-11
Just a couple of quick observations:

1. I like Gnome for it's features.  I *love* XFCE 4.2 for it's speed.  Choice on Linux doesn't end with the install.  Someone even suggested trying KDE.
2. You are using an ATI driver on Linux, right?  How many Nvidia Ubuntu users can make these same performance 'claims' (on Ubunutu or elsewhere)?  I for one can't.  ATI drivers for linux are getting better every day.  Stay tuned.
3. Open Office still uses *java* (I think).  A small performance tradeoff for an Open Source and free compatible MS Office suite.
4. Back to item 1 again.  You have the choice (freedom) to shutdown many services or use alternative packages to the default install setup/base.  If you continue your discovery process in these mighty fine and friendly forums, in time, I bet you'll look back on this post and scratch your chin a bit. I think the only option you mentioned for getting back Windows performance was reinstalling that OS.  I hear ya.  I had to do the same every 6 months or so myself.

I haven't used Windows in 7 years, so my observations or opinions here are probably no more 'insightful' than 'Beware of Dog' postings in Police training kennels.  Personally, I have to tell you my observations when installing Ubuntu > warty > hoary were just the *opposite* as yours.  That's quite a compliment to Ubuntu coming from LFS > Gentoo > Arch.  Hang in there Telmo.  These knowledgeable guys around here will get you where you want to be.  I'm pretty impressed by these forums myself, being new to Ubuntu.

---

### Post by skoal on 2005-04-11
[QUOTE=telmo]I'm now trying (and glad to) XFCE4. It seems a little faster, but still... only a little...[/QUOTE]

Sweet...

Telmo, by the way, I haven't installed XFCE 4.2 on Ubuntu yet, but if you haven't tried XFCE 4.2 before check out the plugin packages.  I find their plugins far more beneficial than Gnomes.  I assume those plugins are somewhere in the repos.

---

### Post by telmo on 2005-04-11
Yeah... Ubuntu is really cool!  ;-) 
I've tried others O.S.'s myself (about 30!) and Ubuntu is really great! But... you know... speed is VERY important. That's why 'we' buy ram and fast processors... but, i'm sticking to it! I just need to improve it a bit. Maybe when i'm finished improving Hoary a new version appears... lol

---

### Post by bvc on 2005-04-11
1. specs like telmo's need not be concerned about which de/wm. Fact is, that little wm, or medium de, ends up using the same resources after a few hours anyway, unless you used ALL independent apps that are not dependentent on gnome or kde libs, and very few people can claim such unless you aren't really doing anything with the box ;-)

2. I use NVIDIA...win is much faster in all areas. Again, 2 boxes 30+ distros in 4 years. Always the same result.

---

### Post by skoal on 2005-04-11
I've also ran across many confusing posts (to me) in Linux forums and here about Firefox taking forever to load.  I don't understand.  Really, I don't.  The first time I load firefox from a cold/warm boot, it takes < 3 seconds.  Every subsequent firefox launch < 2 seconds.  And that's on a old 2 gig Maxtor drive which spits smoke out the rear case fan...

Just my fortunate luck I guess.  I don't know what I'm doing different than anyone else in Linux.  No performance tweaks at all. Nothing.  Someone compare that to windows.

---

### Post by bvc on 2005-04-11
my biggest nag is the slow internet response, and it's not all the time but about 50% of the time in ubuntu and about 25% in mandrake. The other day I booted ubuntu and didn't have internet......booted mandrake and didn't have internet....booted xp and had internet. Now, that could have been a coincidence but lets say it wasn't.....what did xp do that linux didn't? release/renew? Probably, but why didn't linux do that instead of expecting my wife to do it while I'm at work? (it was me and root could have, but you get the point). Speed...time is $

---

### Post by skoal on 2005-04-12
[QUOTE=bvc]Speed...time is $[/QUOTE]

Yes, sir.  Absolutely.  I agree. WRT to browser rendering speed, I must be fortunate in that I have a 100 Mbit pipe to the net.  So any observations I make relative to that really don't apply to most.

However, just one last clarification to my original 'observations' to illustrate the original 'comparison' to Windows performance.  Using Nvidia on Linux is different than using ATI on Linux.  Even for 2D applications.  If you use text, fonts, or images on your DE, then 'RenderAccel = True' is your friend.  Even though most associate that option with OpenGL, composite, or the like, it's real benefit (at the moment) is in hardware accelerated 2D drawables using the RENDER extension.  Case in point: When that extension first came out I tried out that option with an early Nvidia release.  I kept getting lockups when it hardware rendered certain fonts.  That option is much more stable now, and the 2D performance increase since is noticeable for me without it.

---

### Post by bvc on 2005-04-12
Option 		"RenderAccel" 		"true"
no diff

---

### Post by poofyhairguy on 2005-04-12
[QUOTE=bvc]Option 		"RenderAccel" 		"true"
no diff[/QUOTE]

Try xcomposite. That speeds up things for me!

---

### Post by bvc on 2005-04-12
got it to
but thx

---

### Post by skoal on 2005-04-12
I'm an old rusty Xlib/Motif programmer so any detailed explanation I provide would be grossly innacurate.  However, Keith Packard has some very interesting literature on the matter which I've been following for a year or two.  I occasionally select those bookmarks just before bedtime, in case a shot of whiskey or a warm milk toddy doesn't do the 'trick'.

From my experience, the benefit of the 'RenderAccel' Nvidia option varies with the hardware.  I have a Ti-4600 and it's served me well.  Some of the older MX guys seem to either have problems using this option, see no benefit to it, or can't use it at all.  I know nothing about ATI's driver and how it relates to this API.

---

### Post by bvc on 2005-04-12
lol
I'm MX 440 64MB AGP but I hardly see why that would matter seeing how that is above average . What do people with 2 year old mx 200's do (like in my old box), have a slow box? or use windows? Next arguement please :razz: I can see you are 'trying' to help so please don't think I'm 'trying' to be rude. I've done lfs a few times as well so this is not my first rodeo. Everyone knows it's lack of devel. Paint over it anyway you want, but devel is spread so thin and has such a hard time keeping up with new hardware that it ditches the mediocre old in order to attempt to keep up with the Jones'. You know?... "You get what you pay for", so how can anyone compain if its free? We can't! We sacrifice speed for security, stability, next to no viruses, and an all around better situation/OS. But I have never, and never will, pretend 'it's all good'. Glad all is cool with you. I built my pc with "linux compat' hardware...so what's up? Lack of devel....bottom line...
..and I still love Linux!!! :grin:

---

