---
title: "The 'Your swap should not be three times your RAM' thread."
date: 2007-07-05
forum: The Cafe
---

### Post by cleverselfreferentialname on 2007-07-05
Sorry, I just have to vent a little. A lot of people still believe this.

There is an old metric that still floats around, that the size of your swap partition or files should be three times the size of your RAM, or two times the size of your RAM, or 1.5. This is a very common misconception; I've heard it from every lower-echelon IT guy that hasn't been back to school in a while. It comes from the days of DOS and Windows 9x, when a system could reasonably be expected to have 32MBs of RAM, so you needed that extra buffer on-disk.

This is no longer the case. If you have 1GB of RAM, you will generally never need 3GBs, or 2GBs, or 1.5GBs of swap. I have 512MBs of RAM and 512MBs of swap and have never gone past 1/2 swap usage. I recommend 256MBs for 1GB of physical RAM, but most people tend to cling to "OMGz, I need my 6GBs of swap!" Even if you've got 256MBs of physical memory, 512MB of swap can still be reasonable. The rule does not scale past 512MBs of swap.

I am told that editing ISO images requires a lot of swap, but only a very small number of users will ever do that, and one guide to editing ISO images directly covers making new, _temporary_ swap files in addition to your primary swap partition.

You can all post angry counter-flames now if that's your cup of tea, but remember that even when once this is over, we can still argue about what is the optimal value for swapiness with various system configurations!

---

### Post by moredhel on 2007-07-05
I always have my swap 50% of my RAM, but only going up to 512mb... so basically it's always 512mb xD

EDIT: I remember i used to use 150%, but I notice no difference now using 50% ;)

---

### Post by brim4brim on 2007-07-05
I had spare space at the end of my partition after I deleted my windows swap partition that I had setup to see would it make a difference (it dosn't, windows still gets badly fragmented without a swap file on the C:\).

Anyway I find it makes feck all difference what size your swap is as long as its over 256MB, you are generally alright.  I have 512MB of ram and use feck all swap space.

---

### Post by kerry_s on 2007-07-05
i always use 1 gig of swap, i do alot of multi tasking and often have alot of apps open an i use several desktops, sometimes they will be open for long periods of time/days.

my main system has 1 gig ram(it's down right now)
the laptop i'm using now has 256 ram.

---

### Post by Polygon on 2007-07-05
your swap NEEDS to be at least equal to your ram, (or is highly recommended that it is)

i believe this is because that when you go to hibernate, it saves everything that is in ram onto the hard drive (the  swap if i remember correctly), and if there is not enough swap space to accommodate everything that is in ram, then when you resume things will be screwed up.

i have mine set at twice my ram (so its 2 gb). if you have like at least 1 gb you will almost never need it, but it does help on slower computers that dont have much ram.

---

### Post by Rui Pais on 2007-07-05
Yes, thats right.
I keep see that been advise constantly, some times got so tired of that that i don't take time to explain (i think i will point to this threads, to avoid constantly repetitions of the same).
The only reason that one in fact need swap if it got more then 0.5G is for suspend. A 

Btw, just look at Ubuntu documentation:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
special the [How much space i need]("https://help.ubuntu.com/community/SwapFaq#head-190211a884ef581b07a51ca8ecd8fbf68c93b88e") here it cames again the 2*n formula...

luckily HDs are bigger too :lol:


edit:
@Polygon... not necessarily. Linux manage RAM in a way that it seems it's all used. It will save only the used-cached, i think. 
I used to have a swap of 600m and 1G of ram and in more then a year never see a problem...

---

### Post by smoker on 2007-07-05
i think i tend to agree with the OP, i have 2GB ram, and a 1GB swap, which was basically a 'pick a convenient number' size when i was setting up my partitions. i couldn't say the last time it was used, though i don't tend to monitor these things so much!

as a matter of interest, would it be possible, without problems, to dispense with a swap partition altogether?

---

### Post by brim4brim on 2007-07-05
> **smoker said:**
> i think i tend to agree with the OP, i have 2GB ram, and a 1GB swap, which was basically a 'pick a convenient number' size when i was setting up my partitions. i couldn't say the last time it was used, though i don't tend to monitor these things so much!

as a matter of interest, would it be possible, without problems, to dispense with a swap partition altogether?

I think you can but that its not a good idea.  For example, windows uses a page file and if your HDD free space goes below the Swap file max size then it can cause windows to become very unstable

---

### Post by Rui Pais on 2007-07-05
> **smoker said:**
> i think i tend to agree with the OP, i have 2GB ram, and a 1GB swap, which was basically a 'pick a convenient number' size when i was setting up my partitions. i couldn't say the last time it was used, though i don't tend to monitor these things so much!

as a matter of interest, would it be possible, without problems, to dispense with a swap partition altogether?

if you don't suspend to disk (hibernation) i think that yes... 
imagine a user with 256k of ram that apply the 3*n formula. He will have 1G for memory... still lower they yours ;)

---

### Post by Lord Illidan on 2007-07-05
I have 2 gb RAM. How much swap do I need?

---

### Post by M$LOL on 2007-07-05
> **smoker said:**
> i think i tend to agree with the OP, i have 2GB ram, and a 1GB swap, which was basically a 'pick a convenient number' size when i was setting up my partitions. i couldn't say the last time it was used, though i don't tend to monitor these things so much!

as a matter of interest, would it be possible, without problems, to dispense with a swap partition altogether?

I'm trying that now with a Debian base system on a 500MB HD :P

---

### Post by Rui Pais on 2007-07-05
> **Lord Illidan said:**
> I have 2 gb RAM. How much swap do I need?

open your file manager, 20 or 30 tabs on FF, gimp with some big images, watch a movie, and what ever more you remember or you commonly do with your computer. With all that running open a terminal and run: 
```
free -m
```
that will tell you how much ram and how swap is used. It's a nice general starting point.

---

### Post by eentonig on 2007-07-05
I have 2G RAM and 3G Swap.

Allthough I removed the swap partition from fstab for a while (so basically ran without swap) and I didn't notice any negative impact. So, granted you have enough RAM, swap isn't really needed anymore.

That said. Since disks get larger and larger. I see no point in giving up the x1.5 rule of thumb. If one were to start editing ISO's, Movies, photoediting, ...at the same time,  it will still be usefull.

---

### Post by v8YKxgHe on 2007-07-05
I normally set it to 1GB ... most probably because if I do double my physical memory I will have an 8gb swap space!

---

### Post by Erunno on 2007-07-05
On notebooks having a swap partition equal to the RAM size is needed for hibernating. If you need more than this highly depends on how much RAM you already have and what applications you use. Photo editing software and IDEs for instance can use quite a lot of RAM. So with 512 MB at one point it will have to swap data out of memory. With 2 GB of RAM its highly unlikely that you will need a swap partition other than for hibernating, especially if you are using computers for web browsing / chatting / email solely.

As far as I know the kernel kills the largest process if it runs out of RAM without prior warning.

In my opinion there's no general answer to this question. I'm not sure how Ubuntu handles automatic partitioning but it's probably algorithmic depending on your RAM size with a minimum size.

---

### Post by reclusivemonkey on 2007-07-05
> **kerry_s said:**
> i always use 1 gig of swap, i do alot of multi tasking and often have alot of apps open an i use several desktops, sometimes they will be open for long periods of time/days.

my main system has 1 gig ram(it's down right now)
the laptop i'm using now has 256 ram.

You need to buy more RAM dude...

---

### Post by az on 2007-07-05
> **Erunno said:**
> On notebooks having a swap partition equal to the RAM size is needed for hibernating....

Actually, I think you need at least 25 percent more than your physical ram to suspend-to-disk.

> **Erunno said:**
> 
As far as I know the kernel kills the largest process if it runs out of RAM without prior warning.

Yep.  That's usually X.  It is *not* a good idea to go without swap space.

> **Erunno said:**
> 
In my opinion there's no general answer to this question. I'm not sure how Ubuntu handles automatic partitioning but it's probably algorithmic depending on your RAM size with a minimum size.

It's funny how people get upset about this.  It's funny how some people proclaim how much swap everybody else needs.  It's prudent to have enough swap around so that your box doesn't crash.  The install does a good job of taking into acound your needs as well as the available space.

I don't see any problems here.  Just take the default and move on.  People shouldn't even be doing manual partitioning unless they have very special needs anyway.

---

### Post by Bavo on 2007-07-05
I usually use these rules
RAM > 512Mb => SWAP == RAM  (at least)
128 Mb < RAM < 512Mb => SWAP == 2x RAM 
RAM < 128Mb => get yourself a new computer :)

Your swap should _at least_ equal your RAM, otherwise you won't be able to hibernate.

---

### Post by argie on 2007-07-05
I use very few applications at a time. The 256 MB RAM desktop has 700MB swap (what was left over, after my sizing, so I just dumped it in there), the 1GB RAM laptop doesn't have any swap because I never go over 400 MB usage.

---

### Post by nocturn on 2007-07-05
The old myth is 2 times the RAM and comes from quite old Sun OS versions where this used to be true.

---

### Post by josys36 on 2007-07-05
I haven't used swap for three releases now. I have a T60 with 2 Gig of RAM and never even get close to using it. This is even true when I ran VMWare.

Jason

---

### Post by FoolsGold_MKII on 2007-07-05
I have 2GB RAM, with a swap partition of 1.4GB.

So far it's using 33MB of swap. I highly doubt it's ever gonna hit the upper limit, but I like to be prepared.

---

### Post by Erunno on 2007-07-05
> **az said:**
> Actually, I think you need at least 25 percent more than your physical ram to suspend-to-disk.

There's something new to learn every day :-)

EDIT:

If you're dead set on avoiding swapping as far as possible you can modify how aggressively the kernel swaps pages out of memory via /proc/sys/vm/swappiness. With this you can avoid swapping without losing the safety net that is a swap partition.

---

### Post by cleverselfreferentialname on 2007-07-05
> **reclusivemonkey said:**
> You need to buy more RAM dude...

Why are people always all "Bigger, better, faster, more!" I don't need any more than the 512MBs of RAM I have, and I don't see any reason why I'd need any more. Because....I use fluxbox :D

---

### Post by reclusivemonkey on 2007-07-05
> **cleverselfreferentialname said:**
> Why are people always all "Bigger, better, faster, more!" I don't need any more than the 512MBs of RAM I have, and I don't see any reason why I'd need any more. Because....I use fluxbox :D

The poster I replied to gave me the impression he was regularly running out of RAM. If this is the case, you need more RAM, simple. Its cheap and no one wants to be running for any length of time in swap its S - L - O - W. Swap is for emergencies, not for regular usage.

---

### Post by kerry_s on 2007-07-05
> **reclusivemonkey said:**
> You need to buy more RAM dude...

I would but 256 is the max, this laptop is old. ;) > [http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=14552&DL](http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=14552&DL)

---

### Post by reclusivemonkey on 2007-07-05
> **kerry_s said:**
> I would but 256 is the max, this laptop is old. ;) > [http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=14552&DL](http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=14552&DL)

I've not got a (working) laptop, but would one of the card memory options work? I have one in one of the ancient laptops I have lying around...

---

### Post by deepclutch on 2007-07-05
there are some changes in kernel(linux) afaik regarding some memory patch(that means swap too) and con kolivas stops giving his kernel patches as of 2.6.22 :(
**[The end of the CK kernel patch set]("http://artipc10.vub.ac.be/serendipity/archives/32-The-end-of-the-CK-kernel-patch-set.html")**
[http://kernelnewbies.org/Linux_2_6_2...8ceb44681781c9]("http://kernelnewbies.org/Linux_2_6_21#head-1e87824aa4636cc57408ac7b268ceb44681781c9")

---

### Post by kerry_s on 2007-07-05
> **reclusivemonkey said:**
> The poster I replied to gave me the impression he was regularly running out of RAM. If this is the case, you need more RAM, simple. Its cheap and no one wants to be running for any length of time in swap its S - L - O - W. Swap is for emergencies, not for regular usage.

i do but that's what the 1 gig swap is for. i'm running a debian minimal+fluxbox so even on this old laptop there's plenty of room to play. ;)

---

### Post by kerry_s on 2007-07-05
> **reclusivemonkey said:**
> I've not got a (working) laptop, but would one of the card memory options work? I have one in one of the ancient laptops I have lying around...

thanks, but i'm all good.

---

### Post by ThinkBuntu on 2007-07-05
I have 1.5GB RAM and I'll be damned if I ever noticed my system using the swap (unless I'm running Firefox and GNOME together...just kidding), although most installers set aside a 3GB swap partition. From now on, I'm going to manually partition it to 512MB, which should be more than enough.

---

### Post by cleverselfreferentialname on 2007-07-05
> **reclusivemonkey said:**
> The poster I replied to gave me the impression he was regularly running out of RAM. If this is the case, you need more RAM, simple. Its cheap and no one wants to be running for any length of time in swap its S - L - O - W. Swap is for emergencies, not for regular usage.

Oh, hehe, sorry.

---

### Post by FuturePilot on 2007-07-05
Somehow I ended up with 4.8GB of swap:-k
But I think you need all that swap for hibernating.

---

### Post by reacocard on 2007-07-05
I have 1.2 GB swap so that I can hibernate nicely. IMO, for RAM, if you have <512, you should do at least 256mb swap, maybe more. For 1GB and up, it really doesn't matter, almost anything will run comfortably in 1GB. If you need hibernate, RAM + usual swap usage + 128MB is what I'd recommend.

---

### Post by scragar on 2007-07-05
I have 370 MB of ram(1 * 128Mb, 1*256 MB) and a 1.1GiB swap, is this OK (Fx runs slow if I open 10+ tabs, but that's cos I tend to usebit-torrent and something like VLC as well...)

---

### Post by reacocard on 2007-07-05
> **scragar said:**
> I have 370 MB of ram(1 * 128Mb, 1*256 MB) and a 1.1GiB swap, is this OK (Fx runs slow if I open 10+ tabs, but that's cos I tend to usebit-torrent and something like VLC as well...)

that's plenty, if your swap is more than 2x your RAM, it's probably too much (but better too much than too little :p).

---

### Post by deepclutch on 2007-07-05
more:I have seen a guy who shares swap partition btwn windows xp and Linux :lol:
wht he actually does is he made a script running on each boot to do "mkswap /tmp/pagefile.sys" -brains! :D
below:
[http://www.thinkdigit.com/forum/showthread.php?t=28574&highlight=swap](http://www.thinkdigit.com/forum/showthread.php?t=28574&highlight=swap)

---

### Post by forrestcupp on 2007-07-05
Ram is used up before swap even gets touched, so having more swap wouldn't really slow anything down.  So as big and cheap as hard drives are getting today, what negative effect could you possibly have from having 3 or 4 gigs of swap?  I'm never going to use all 120 gigs of my hard drive, so does it really matter?  In this case, I'd rather be safe than sorry.

---

### Post by wolfen69 on 2007-07-05
> **Lord Illidan said:**
> I have 2 gb RAM. How much swap do I need?

if your an everyday average user, probably none. but people will tell you otherwise. i have 2gb. of RAM, and have never used any swap.

---

### Post by PatrickMay16 on 2007-07-05
Perhaps some don't even need swap. I have 1.5 GB (1500MB) of RAM, and I barely ever see swap used. When I do see swap used, it's about 2MB or something tiny.

---

### Post by kevinlyfellow on 2007-07-08
I use the 2x rule as a max for swap needs, you can't go wrong with 2x.  I prefer to drop it down to the minimum amount because I rarely use it except to hibernate (except when I write a bad program, which I'm likely to do).  I also drop down my swappiness to 20, so that my memory is more reluctant to swap out.  3x is *way* too much, especially for modern computers.

---

### Post by bread eyes on 2007-07-08
You only need the swap to equal the ram is when you hibernate with the ram close to full, which is pretty uncommon. 256kib is usually enough if your going to hibernate and not use heavy software.

---

### Post by deepclutch on 2007-07-08
so,2xram=swap rule is good for only hibernate capable systems.and it seems buggy in Linux :-|

---

### Post by bread eyes on 2007-07-08
> **deepclutch said:**
> so,2xram=swap rule is good for only hibernate capable systems.and it seems buggy in Linux :-|

not really

---

### Post by dfreer on 2007-07-08
The whole problem with this:
If you set your swap too low and you end up needing it, it is going to require (in most cases), resizing partitions and juggling data around to increase the swap partition. Which is only going to use a small section of the hard drive anyways. Why not make it safely big enough to begin with (and since hibernation requires at least 1X the amount of RAM, 256 MB's on a 1 GB system is NOT going to cut it)? 

This is absurd and is only going to confuse (and possibly hurt) new users, who do not understand swap and are just looking for a safe amount. Hard drive space is MUCH cheaper than RAM, and modern systems come equipped with more than enough, so why not leave it at least 1.25 X? And as for: 
> You only need the swap to equal the ram is when you hibernate with the ram close to full, which is pretty uncommon. 256kib is usually enough if your going to hibernate and not use heavy software.

What happens when joe blow runs out of battery life on his notebook so it tries to hibernate, and he was in the middle of an important project that made his total RAM usage over 300 MB's and he only has the 256MB of swap?

---

### Post by bread eyes on 2007-07-08
> **dfreer said:**
> The whole problem with this:
If you set your swap too low and you end up needing it, it is going to require (in most cases), resizing partitions and juggling data around to increase the swap partition.

WELL DUH

> **dfreer said:**
> and since hibernation requires at least 1X the amount of RAM 
No, it doesn't.

> **dfreer said:**
> This is absurd and is only going to confuse (and possibly hurt) new users, who do not understand swap and are just looking for a safe amount. Hard drive space is MUCH cheaper than RAM, and modern systems come equipped with more than enough, so why not leave it at least 1.25 X?

Because there is no need.

> **dfreer said:**
> 
What happens when joe blow runs out of battery life on his notebook so it tries to hibernate, and he was in the middle of an important project that made his total RAM usage over 300 MB's and he only has the 256MB of swap?

Then Joe blow should make his swap larger. I'm not saying everyone should have 256MiB of swap. I could also be misgauging the average user.

---

### Post by Compucore on 2007-07-08
I use about the same as the 2X rule for me as well. Even though I have finally brought my linux laptop up to 1 gig of ram. But it also depends on what your working on that you'll eventually go to swap. Typical things like word processing, spreadsheet stuff takes next to nothing with a gig or two of ram. But if your running a database system like Oracle, Teradata, or Sybase RDBM's for example. Then you will be needing that if there is a lot of data to move around and query at on a given workstation or laptop for that matter. 

Compucore

---

### Post by yatt on 2007-07-08
Don't have a swap space. I have 3 GiB of RAM, which has never gone past 600 MiB of usage.

---

### Post by jpkotta on 2007-07-08
> **yatt said:**
> Don't have a swap space. I have 3 GiB of RAM, which has never gone past 600 MiB of usage.

Can I have some, since you're not using it?

I'm not sure if I've seen a 3x recommendation.  Usually I see 2x to 1x.  I usually go for 1x, and it has served me well.  I prefer to have a bunch of swap for the stuff I'm not using, and let the kernel use RAM for disk cache.  BTW, change /proc/sys/vm/swappiness if you think the kernel is too liberal/conservative with swapping.

I'm sure someone has mentioned already that Linux supports swap *files* as well as swap *partitions*, but I'll mention it anyway, because I don't feel like searching the thread.  So if you ever need more, you can just add a file, no need to shuffle partitions.

---

### Post by yatt on 2007-07-09
> **jpkotta said:**
> Can I have some, since you're not using it?
It gets used on Windows. Vista + Oblivion = RAM whore extrodinaire.

---

### Post by dfreer on 2007-07-09
> **bread eyes said:**
> [QUOTE=dfreer;2988073]Why not make it safely big enough to begin with (and since hibernation requires at least 1X the amount of RAM, 256 MB's on a 1 GB system is NOT going to cut it)? No, it doesn't.[/QUOTE]

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
> Hibernation needs swap
    *The hibernation feature (suspend-to-disk) writes out the contents of the memory to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system.

[http://www.ussg.iu.edu/hypermail/linux/kernel/0401.3/1694.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0401.3/1694.html)
> It depends how much swap gets used in your normal activity. A good rule
of thumb is to make sure you have as much swap as RAM, plus a little
more for any genuine swapping the system is doing. Then you'll be able
to save a full image without freeing up any memory... and when you do
resume, your system will be as responsive as it would be if you'd never
suspended.

Older but still relevent:
[http://lists.debian.org/debian-laptop/1999/11/msg00081.html](http://lists.debian.org/debian-laptop/1999/11/msg00081.html)
> And, most importantly, be sure to have enough swap space to hold the
contents of your physical memory *next to* the data already present in the
swap (that is important when you are short of RAM, because then often you
have some data always swapped out, and the available swap space may not be
sufficient). This means that to prevent any failure of the suspend, you
must have at least as much swap space than physical memory, and even a
little more. And remember that the resume occurs on activation of the
first swap space, and thus the suspend data cannot span across several
swap spaces!!

In short, yes it does :P Please get your facts straight. The important thing here is that IF it is needed, the swap should be there. And there should be just enough to safely do the job, otherwise you get OOM and processes start getting killed, which is never good.

---

