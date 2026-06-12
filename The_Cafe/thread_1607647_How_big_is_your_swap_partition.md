---
title: "How big is your swap partition?"
date: 2010-10-28
forum: The Cafe
---

### Post by oobuntoo on 2010-10-28
I've never noticed my system actually using any of my swap partition. The only time that I can think of that the swap space might get used is when I put the system in hibernation (suspend to disk), which I don't do anymore. The recommended size of swap partition is twice the size of your physical RAM. If you have, say, 6GB of RAM like mine, then 12GB of swap seems like a lot of wasted space. If you set the swap partition size equal to the RAM size, it still seems like a lot, in this case. 
So, anyone here use swap size smaller than RAM size AND experience no problem? I'd like to get a feel of what others set the swap size to relative to their physical RAM size.

Here's mine right now:
RAM: 6GB
SWAP: 12GB

---

### Post by Verbeck on 2010-10-28
if i run windows 7 in virtual box, about >250 mb of swap get used

1 GB RAM
2 GB SWAP

---

### Post by handy on 2010-10-28
Box No.1: 1GB RAM, no /swap
Box No.2: 2GB RAM, no /swap

Unnecessary for my use. 

Box No.3: 256MB RAM, 32MB /swap
It is the IPCop firewall/router box, it very rarely if ever uses any of its tiny little /swap partition.

---

### Post by Spice Weasel on 2010-10-28
512MB (2GB RAM), but that's just in case something goes wrong. I never really use it. No problems at all.

---

### Post by Random_Dude on 2010-10-28
Why isn't anyone doing "comparing sizes" jokes?

Anyway:
RAM 3GB
SWAP 6GB

---

### Post by kerry_s on 2010-10-28
1gb ram
1gb swap

---

### Post by Barrucadu on 2010-10-28
10GB - I've never used it but, then again, I'm not running out of space on my HDD either, so having such a huge amount isn't a problem.

---

### Post by alexandari on 2010-10-28
2 gb ram
3 gb swap

---

### Post by s.fox on 2010-10-28
Up until recently I had this on my one of my laptops:

4GB RAM
11GB SWAP

---

### Post by 3Miro on 2010-10-28
4GB RAM, 10GB Swap. I intend to upgrade the RAM and I don't want to reformat. Swap helps, when I mess up a program and create a huge memory leak, then I don't have to reboot the entire machine, I have enough time to kill the bad process.

---

### Post by szymon_g on 2010-10-28
> **3Miro said:**
> 4GB RAM, 10GB Swap.

lol. i wanted to write "my swap is bigger than yours", but YOU ARE THE KING!!!

---

### Post by philinux on 2010-10-28
2 gig ram

2 gig swap.

Based on this.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by handy on 2010-10-28
On my box.1 & box.2, I just kept an eye on my /swap usage with "htop" for some time & found that I NEVER needed to use it.

So I removed /swap from both machines.

I think that unless you are using Photoshop, Gimp or similar; CAD software (obviously via Wine), or doing other work such as sound & or (especially) video editing; provided that you have at least 1GB RAM, you really don't need to have a /swap partition at all.

I don't care what the experts say about how much /swap we should have. Just use htop, watch your usage & see for yourself if you do actually need any /swap.  Most people have /swap & they really don't EVER need it.

Yeh, I know, hard drive space is cheap. So what? Why waste it if you don't need to?

---

### Post by scinerd on 2010-10-28
I have always gone with a swap partition that is equal to the size of my ram.  Back in the day when ram wasn't cheap I might have used more.  Now with large ram sizes I'm tempted not to have one.  I would say if you not pressed for disk space a ram partition can't hurt.

---

### Post by Grenage on 2010-10-28
I don't really use swap space, but usually add a token amount - around 4GB.  When a desktop has TBs of storage space, it makes so little difference.

---

### Post by Spice Weasel on 2010-10-28
To anyone that owns a SSD, how fast does it swap? Do you find yourself buying less memory because of the SSD?

---

### Post by handy on 2010-10-28
> **Grenage said:**
> I don't really use swap space, but usually add a token amount - around 4GB.  When a desktop has TBs of storage space, it makes so little difference.

I appreciate that argument, BUT, if you never use it, /swap is just another unnecessary complication. 

With the amount of RAM that most people have on their machines these days (1GB has become a tiny amount), I think that there exist very few computers that run a Linux distro that do actually really need to have a /swap partition.

That's my view anyway. :)

htop tells the story; anyone who wants to see how much /swap they are using can monitor it with htop & decide for themselves if it is just another unnecessary system complication.

As an Arch user, I'm all for simplification of the system; as in my view it makes the system easier to manage & far more reliable.

I'll be quiet now. :)

---

### Post by slackthumbz on 2010-10-28
And there was me thinking the thread title was a filthy euphemism, how dull!

I usually set aside 1.5x my RAM for swap.

---

### Post by handy on 2010-10-28
> **slackthumbz said:**
> And there was me thinking the thread title was a filthy euphemism, how dull!

I usually set aside 1.5x my RAM for swap.

Do you ever use any of it?

---

### Post by slackthumbz on 2010-10-28
> **handy said:**
> Do you ever use any of it?

occasionally, mostly it's just there as a safety net.

---

### Post by linux-hack on 2010-10-28
4Go RAM
1Go SWAP = don't rely need more if your ram is more then 1Go

---

### Post by wewantutopia on 2010-10-28
4GB Ram
NO swap

Same on my XP partition (no virtual memory)

---

### Post by Paqman on 2010-10-28
4GB RAM, 3GB swap.

Tbh the only reason i've got that much swap is because it's on a disk which is a leftover from and old setup. I don't really need extra space on that disk, soi i've never got down to shrinking it.

Swappiness is zero, btw. The default Ubuntu swappiness of 60 is waaaaaaaaay too conservative IMO. I want my apps in my RAM, not my storage.

> **Spice Weasel said:**
> To anyone that owns a SSD, how fast does it swap? Do you find yourself buying less memory because of the SSD?

I wouldn't ever use swap on an SSD. If you've invested enough money in a machine to have an SSD, you can afford enough RAM so that you don't need swap. My swap is on an old magnetic drive.

---

### Post by Grenage on 2010-10-28
> **handy said:**
> I appreciate that argument, BUT, if you never use it, /swap is just another unnecessary complication. 

With the amount of RAM that most people have on their machines these days (1GB has become a tiny amount), I think that there exist very few computers that run a Linux distro that do actually really need to have a /swap partition.

That's my view anyway. :)

htop tells the story; anyone who wants to see how much /swap they are using can monitor it with htop & decide for themselves if it is just another unnecessary system complication.

As an Arch user, I'm all for simplification of the system; as in my view it makes the system easier to manage & far more reliable.

I'll be quiet now. :)

Valid point, but I don't really view it as a complication; it's just something that's there *if* it's needed.  I have 8GB of RAM and 4TB of drive space (it's not all porn), so for the sake of 0.1%...

---

### Post by Frogs Hair on 2010-10-28
Small , I don't hibernate.

---

### Post by CharlesA on 2010-10-28
Didn't bother to change the defaults, so I've got a 12GB swap partition somewhere. Storage is cheap, and it's there if I need it.

---

### Post by handy on 2010-10-28
> **Grenage said:**
> Valid point, but I don't really view it as a complication; it's just something that's there *if* it's needed.  I have 8GB of RAM and 4TB of drive space (it's not all porn), so for the sake of 0.1%...

Yeh, I agree, these days we mostly have lots of RAM & lots of HDD space so why bother even thinking about the our /swap ?

I'm just a bit obsessive compulsive I guess... lol

Though, as I said, I NEVER need to use /swap.

---

### Post by Grenage on 2010-10-28
> **handy said:**
> Yeh, I agree, these days we mostly have lots of RAM & lots of HDD space so why bother even thinking about the our /swap ?

I'm just a bit obsessive compulsive I guess... lol

Though, as I said, I NEVER use need to use it.

It never hurts to strive for efficiency.

---

### Post by CoreyB. on 2010-10-28
I follow the rule that used to be posted here [http://kbase.redhat.com/faq/docs/DOC-15252]("http://kbase.redhat.com/faq/docs/DOC-15252").  But now I see that you have to have an account, which I don't have, so I don't know if the link still works.  What it said was if you have <= 2 GB of Ram, swap should be twice the ram you have, if you have > 2GB, your swap should be amount of ram + 2GB.

---

### Post by handy on 2010-10-28
> **CoreyB. said:**
> I follow the rule that used to be posted here [http://kbase.redhat.com/faq/docs/DOC-15252]("http://kbase.redhat.com/faq/docs/DOC-15252").  But now I see that you have to have an account, which I don't have, so I don't know if the link still works.  What it said was if you have <= 2 GB of Ram, swap should be twice the ram you have, if you have > 2GB, your swap should be amount of ram + 2GB.

That's just not true anymore.

Check your usage with htop & you will probably find that unless you do incredibly memory hungry tasks, you never use /swap.

The proof is in the pudding. :)

---

### Post by Bölvaður on 2010-10-28
Am I the only one that isn't scared of anything :cool:

```
             total       used       free
Swap:            0          0          0
```


but ok I got a swap of about 1.99GiB but I just swapon when I need to... which is only when Im programming with eclipse and the android emulator running... oh god I hate how much ram it eats up.

---

### Post by Bapun007 on 2010-10-28
2gb ram and 5gb swap .

---

### Post by NightwishFan on 2010-10-28
I have 4gb of swap (3gb ram) and sometimes I do need it. I do a lot of heavy virtual machines and open large images with gimp.

Free right now is:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2984       2418        565          0         68       1625
-/+ buffers/cache:        724       2259
Swap:         4000        115       3884

```

---

### Post by cap10Ibraim on 2010-10-28
3.74 GiB ram 
2.01 GiB swap according to conky always 0% used

---

### Post by sydbat on 2010-10-28
> **Random_Dude said:**
> Why isn't anyone doing "comparing sizes" jokes?

> **slackthumbz said:**
> And there was me thinking the thread title was a filthy euphemism, how dull!The ladies like it! There...it is done...

On topic, both of my current boxen run 2GB swap. It is rarely used, but has been accessed occasionally when I do video editing.

---

### Post by chessnerd on 2010-10-28
On my laptop, I don't actually have a swap partition because all of my partitions are used up. Instead I have a swap file. I see no real performance difference, though.

Laptop:
3 GB RAM
1 GB Swapfile

Newer desktop:
1 GB RAM
2 GB Swap

Older desktop:
512 MB RAM
2 GB Swap

You may be thinking: 
Chessnerd, your swapfile is less than your RAM, why would you do that?

1. The swap is rarely, if ever, used
2. I don't hibernate, so I don't need it to hold the contents of my RAM

---

### Post by ubunterooster on 2010-10-28
8GB RAM ( I plan to up the RAM to 16GB)

33GB SWAP

With all of the VMs I'm running, it can be needed.

---

### Post by NightwishFan on 2010-10-28
Serious, 33gb?? That's awesome. If you ever filled up that much.. geez.

---

### Post by ubunterooster on 2010-10-28
Yes, 33 GB SWAP. I set it for a GB more than double the RAM I plan to end up with, Swap is on a SSD with a 750Mbps write and 1.1Gbps read.

I give a VM between 500MB and 2GB RAM and 10 VMs running at once is nothing spectacular to me.

---

### Post by NightwishFan on 2010-10-28
Well, swap can be harmful to a SSD though, so be careful. Though I am not sure if it is a problem anymore.

---

### Post by aysiu on 2010-10-28
I have 2 GB of RAM on my netbook and have used 0 swap for Ubuntu 9.04, 9.10, 10.04, and 10.10 and have never had a problem running it.

---

### Post by ubunterooster on 2010-10-28
> **NightwishFan said:**
> Well, swap can be harmful to a SSD though,  so be careful. Though I am not sure if it is a problem anymore.
This drive automatically takes care of that process itself, independent of the OS telling it to via its own built-in OS. It adds a bit of time waiting for the drive itself to boot but is well worth it once it is finished. Oh, and it has 4 indilux controllers, 4!

---

### Post by fatality_uk on 2010-10-28
total       used       free     shared    buffers     cached
Mem:          3922       1532       2389          0         77        962
-/+ buffers/cache:        493       3429
Swap:         7627          0       7627

---

### Post by NightwishFan on 2010-10-28
> **ubunterooster said:**
> This drive automatically takes care of that process itself, independent of the OS telling it to via its own built-in OS. It adds a bit of time waiting for the drive itself to boot but is well worth it once it is finished. Oh, and it has 4 indilux controllers, 4!

Wear-leveling right?

---

### Post by oobuntoo on 2010-10-28
Wow. Judging from the responses, looks like [SIZE="7"]SIZE[/SIZE] doesn't matter. :lol:

I did notice today, after watching a movie, that 5.2MB of 12GB swap was used. Weird thing is, only 1.3GB of 6GB physical RAM was being used. Any way, I think I'll reduce my swap to 6GB or less.

---

### Post by ubunterooster on 2010-10-28
> **NightwishFan said:**
> Wear-leveling right?
I was thinking of another term but can't remember what it is

---

### Post by philinux on 2010-10-28
I wish people would read this.

[How much swap do I need]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

---

### Post by ratcheer on 2010-10-28
1 GB RAM, 2 - 1 GB swaps. It was a mistake, I did not understand that I could use the same swap partition for both my "production" and testing installations. I have never bothered to try to fix it. It works fine.

Tim

---

### Post by aysiu on 2010-10-28
> **philinux said:**
> I wish people would read this.

[How much swap do I need]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")
I'm high RAM low disk space, but my disk space is even lower than that example. I have a 16 GB SSD. There is no way I'm wasting any of that space on a swap partition. As I said before, I've used four different Ubuntu releases on it with 0 swap and 0 problems.

---

### Post by Schrute Farms on 2010-10-28
On my desktop:  1.5Gb RAM - Somewhere's around 800GB swap.  I'm only using an old 20GB HD for my Ubuntu partition, so I didn't want too big of a swap because of wasted space.  (I don't hibernate).  In normal use, I've only seen it use 100K.  I've seen it using a few MB when I've got a VirtualBox session up, but I rarely do that.

On my laptop:  512Mb RAM - 1 GB swap.  I have seen it use a little more swap, but only a max of like 100Mb.  The most I've had up at one time on that thing would be like Firefox, GIMP and maybe Open Office.

---

### Post by philinux on 2010-10-28
> **aysiu said:**
> I'm high RAM low disk space, but my disk space is even lower than that example. I have a 16 GB SSD. There is no way I'm wasting any of that space on a swap partition. As I said before, I've used four different Ubuntu releases on it with 0 swap and 0 problems.

+1 for small SSD's

---

### Post by darkhelmetchris on 2010-10-28
I too generally use 2x the amount of RAM.

My thoughts are that I want enough swap to support the following:
- suspend to disk (takes the ram size)
- other swap already on disk (while rarely used, and being variable, size of ram is prudent I think)

Some have mentioned that they use little or none, and have no problems.  I certainly agree - if you're not suspending to disk.

Some have brought up the point of possible SSD damage, and I have an OCZ 60GB ssd in my netbook and I do occasionally suspend to disk on that, so my ram/swap is 2GB/4GB.  I am 18 months into using that drive and it is still flawless.

So that's my 2 cents:  I believe that 2x ram is prudent.

---

### Post by NightwishFan on 2010-10-28
If you do not hibernate 512mb-1gb of swap should probably be sufficient. If you need more that for anything other than hibernation you already know why.

---

### Post by philinux on 2010-10-28
> **darkhelmetchris said:**
> I too generally use 2x the amount of RAM.

My thoughts are that I want enough swap to support the following:
- suspend to disk (takes the ram size)
- other swap already on disk (while rarely used, and being variable, size of ram is prudent I think)

Some have mentioned that they use little or none, and have no problems.  I certainly agree - if you're not suspending to disk.

Some have brought up the point of possible SSD damage, and I have an OCZ 60GB ssd in my netbook and I do occasionally suspend to disk on that, so my ram/swap is 2GB/4GB.  I am 18 months into using that drive and it is still flawless.

So that's my 2 cents:  **I believe that 2x ram is prudent.**

.
> Also, it's recommended that the swap space is twice the amount of physical memory (RAM) depending upon the amount of hard disk space available for the system (although this "recommendation" dates back from a time when physical RAM was very expensive and most Unix systems ran with many processes in swap space - a situation that hardly applies in most situations these days, **but ancient Unix/Linux myths like this "recommendation" tend to survive well past their "use by" dates)**


---

### Post by irv on 2010-10-28
I hibernate and suspend a lot, but there is no way to tell how much swap in am using at that point. Can I run htop when I am suspended or hibernated?
I have a 300 GiB HD so I don't worry.
I have 4.72 GiB for swap and 4 GiB Ram

[ATTACH]173784[/ATTACH]   [ATTACH]173785[/ATTACH]

---

### Post by alanmoore78 on 2010-10-28
Well, when running under Windows, my computer has 3GB of RAM, some of it set aside for graphics, and it typically uses 1400-1800MB of that leaving me less than half available.  The page file is usually another 3GB or so and it uses that quite a bit.

I'm now running Ubuntu 10.10 with the same 3GB of RAM.  System Monitor says I'm using 953MB (32.3%) of 2.9GB.  I have Skype, Shutter, Calculator, 3 windows of Chrome (one with 8 tabs open on this forum plus a Gmail tab), Empathy talking to my wife, a Gedit window with a text file, GIMP is open on Workspace 2 with no file open, and I have Rhythmbox and the Contact List open on Workspace 3 plus a couple of filesystem windows for things I am putting away on the Windows partition (it's got 55GB available so I use that instead of the Ubuntu partition).

The swap file is 1.1GB, but I'm using a mere 3.5MB (0.3%) of it.

I am very impressed with memory handling within Ubuntu.  Windows throws stuff all over the place and generally uses more of everything.  Ubuntu seems to use what it needs, and keeps it better organized.  That's just the way I see it.

My daughter's laptop has only 1GB of RAM, and Ubuntu uses the same 1GB of swap and usually is up to 150-200MB of the swap used when I peek at it when my daughter isn't looking.

---

### Post by oobuntoo on 2010-10-28
> **Schrute Farms said:**
> On my desktop:  1.5Gb RAM - **Somewhere's around 800GB swap**.  I'm only using an old 20GB HD for my Ubuntu partition, so I didn't want too big of a swap because of wasted space.  (I don't hibernate).  In normal use, I've only seen it use 100K.  I've seen it using a few MB when I've got a VirtualBox session up, but I rarely do that.

On my laptop:  512Mb RAM - 1 GB swap.  I have seen it use a little more swap, but only a max of like 100Mb.  The most I've had up at one time on that thing would be like Firefox, GIMP and maybe Open Office.

LOL. 800GB swap? That's got to be a typo, ringht?

---

### Post by Finalfantasykid on 2010-10-28
I have roughly 4GB of memory, and I went with 2 GB of swap space.  I rarely ever use more than maybe 10 MB of my swap space, and since I never go into hibernation, I think I chose the right amount.

---

### Post by radar920 on 2010-10-28
4gig ram
4gig swap

---

### Post by ubunterooster on 2010-10-28
> **oobuntoo said:**
> LOL. 800GB swap? That's got to be a typo, ringht?
He replaced "M" with "G"

---

### Post by MooPi on 2010-10-28
> **Random_Dude said:**
> Why isn't anyone doing "comparing sizes" jokes?

Anyway:
RAM 3GB
SWAP 6GB

Cuzz mine is so small...... 512Mb

---

### Post by Schrute Farms on 2010-10-28
> **oobuntoo said:**
> LOL. 800GB swap? That's got to be a typo, ringht?
Yeah, typo.  If I add up all of my HDs together, I don't have 800GB.  :(

---

### Post by Mr Bean on 2010-10-28
8GB RAM, no swap.

It's more than I've ever needed but it was a reasonable price so I went for it.

I see a lot of crazy conjecture about swapfiles and pagefiles. All these weird ratios you hear being thrown around such as 2:1 but nobody ever gives any reasons why they think that. Or the reasons they give are based on scenarios that are a decade old. 

Seems to me that you:

a. determine how much memory you actually need
b. buy more than that (or use a swapfile/partition to top up memory to a level that you actually expect to need)

Job done.

---

### Post by user1397 on 2010-10-29
1gb ram
256mb swap
16gb ssd

having just a gig of ram, i often do end up using some of that precious swap space...

---

### Post by FuturePilot on 2010-10-29
3GB RAM
5.3GB swap

---

### Post by misfitpierce on 2010-10-29
I just used the default
2GB DDR2 ram
5.7GB SWAP

---

### Post by jacrider on 2010-10-29
Ok, how can I tell how much ram I have used over a period of usage?  I run with 4GB of ram and 4GB of swap.

With ram so relatively cheap, if I am consuming all the ram at peak usage, I am happy to add more.  I have htop installed, but it just shows point in time usage.  Is there a way to log the usage?

Thx.

---

### Post by Lightstar on 2010-10-29
4gb ram
1gb swap which is never used.

---

### Post by NightwishFan on 2010-10-29
Yay finally got compcache working!! :)
```
swapon -s
Filename				Type		Size	Used	Priority
/dev/sda1                               partition	4096536	0	-1
/dev/ramzswap0                          partition	764000	12676	100
```

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2984       2218        765          0         64       1538
-/+ buffers/cache:        615       2368
Swap:         4746         12       4734
```

---

