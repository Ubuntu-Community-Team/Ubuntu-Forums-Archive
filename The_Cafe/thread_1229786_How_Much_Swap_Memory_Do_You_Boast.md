---
title: "How Much Swap Memory Do You Boast?"
date: 2009-08-02
forum: The Cafe
---

### Post by coldReactive on 2009-08-02
*cough*

I have an unbelievable amount, since I don't use much harddrive space.

99 GB.

---

### Post by toupeiro on 2009-08-02
um... why?

I have 1.9GB and my system and 0% used because Linux is far more efficient with physical memory usage than windows (where it was sometimes beneficial to have a large swapfile.)   How much of that 99GB are you actually using? (at a console, type gnome-system-monitor and click on the resources tab)

---

### Post by SuperSonic4 on 2009-08-02
I have 2^12 MiB

---

### Post by coldReactive on 2009-08-02
> **toupeiro said:**
> um... why?

Would YOU use up all 500 GB of your hdd? All my musics are on a flash drive, and most of my documents too. They only take up about 1 GB so far.

---

### Post by SuperSonic4 on 2009-08-02
> **coldReactive said:**
> Would YOU use up all 500 GB of your hdd? All my musics are on a flash drive, and most of my documents too. They only take up about 1 GB so far.

I'd just leave it as unallocated space

---

### Post by toupeiro on 2009-08-02
> **coldReactive said:**
> Would YOU use up all 500 GB of your hdd? All my musics are on a flash drive, and most of my documents too. They only take up about 1 GB so far.

haha, I have a few 500GB hard drives full. :P  Everyones hard drive usage is different.  I would still not waste hard drive space on swap that will likely never get used.  You're much more likely to use it as filespace one day than swapspace.

---

### Post by Tipped OuT on 2009-08-02
> **SuperSonic4 said:**
> I'd just leave it as unallocated space

Why? Did you know having a larger partition space actually speeds up your computer slightly?

---

### Post by SuperSonic4 on 2009-08-02
> **Tipped OuT said:**
> Why? Did you know having a larger partition space actually speeds up your computer slightly?

Yes but I'm sure the gain is negligible compared to the ease of subsequent installs of OS/Data Partitions

---

### Post by toupeiro on 2009-08-02
> **Tipped OuT said:**
> Why? Did you know having a larger partition space actually speeds up your computer slightly?

Not really.  Not in Linux, at least.  Before you go out creating 100GB swapfiles, it might do you some good to google around on how linux utilises RAM.  If I have a 2GB swap partition with NOTHING in it whatsoever, a 100GB swap partition buys me nothing.  Linux balances active process, sleeping processes, and killed processes much better than windows.  Have you ever noticed that the second time you start an application is faster than the first time after a reboot?  Even, if that second time is some hours from now?  Thats because Linux will keep recently used files in memory, even after they are terminated, and flush them if the active load needs the additional memory.  Think of it like a last-in/first out scenario.  You will only get significant swap usage if you are paging almost 100% of your physical RAM.  in a 64-bit machine with more than 4GB, thats pretty tough to do on the average desktop.  Even is a 32-bit average desktop with 4GB, this is hard to do.

---

### Post by CharmyBee on 2009-08-02
0MB swap partition, 2GB of RAM. No swap/RAM issues here.

---

### Post by &#32 Greg on 2009-08-02
> **SuperSonic4 said:**
> I have 2^12 MiB

Is it bad that I knew the value of that in under a second?

---

### Post by Tipped OuT on 2009-08-02
13.3 MB of Swap

623 MB's of RAM.

Wow.

---

### Post by Nburnes on 2009-08-02
3.2 GB of SWAP with 4 GB RAM

---

### Post by aysiu on 2009-08-02
I don't have a swap partition.

Space is a commodity on a 16 GB SSD, and I already have 2 GB of RAM, which is plenty for what I do (no games, no design, only very rarely a virtual machine).

---

### Post by tubezninja on 2009-08-02
On one of my servers, I was a bit dumb and gave it 12GB of swap space, on 4GB of RAM (because you know, swap should equal your RAM x 3, right?). :)

It's been in operation for about 18 months now, and hasn't touched the swap partition once.  I'm just too lazy to resize it, and it hasn't really needed the disk space yet.

---

### Post by bear24rw on 2009-08-02
0GB Swap
6GB RAM

---

### Post by SuperSonic4 on 2009-08-02
> **  Greg said:**
> Is it bad that I knew the value of that in under a second?

About as sad as me actually putting in the value of that when partitioning instead of 5000

---

### Post by NovaAesa on 2009-08-02
4GiB swap... haven't used it yet. I have 4GiB of ram... so the swap was just one of those 'just in case' sort of things.

---

### Post by chris200x9 on 2009-08-02
I thought I read somewhere to much swap can make your system a little SLOWER

oh but 300 mb I never use more than 800MB of my 2GB ram anyway

---

### Post by Grant A. on 2009-08-02
> **scaredpoet said:**
> On one of my servers, I was a bit dumb and gave it 12GB of swap space, on 4GB of RAM (because you know, swap should equal your RAM x 3, right?). :)


Maybe in the mid-nineties :P

I have a 2.8GB swap file, and 2 GB of RAM.

I need to buy some more RAM. What a waste of a 64bit Operating System. :(

---

### Post by .Maleficus. on 2009-08-02
4GB RAM, 2GB swap file if I remember correctly.
> **coldReactive said:**
> Would YOU use up all 500 GB of your hdd? All my musics are on a flash drive, and most of my documents too. They only take up about 1 GB so far.
Currently connected to my main computer - 450GB internal, 500GB external.  Currently connected to my server - 40GB internal, 1.5TB external.

The answer would be yes.

---

### Post by RATM_Owns on 2009-08-02
2GB.

And I only use 2% of it at most.

---

### Post by FuturePilot on 2009-08-02
2GB RAM, 4.7GB swap.

---

### Post by mobilediesel on 2009-08-02
375.22 MiB RAM
854.98 MiB swap, 28% used. Yes I need more RAM.

That's according to conky..
and that reminds me, who the hell made up "MiB" for a unit of measure?

---

### Post by Tipped OuT on 2009-08-02
> **mobilediesel said:**
> 375.22 MiB RAM
854.98 MiB swap, 28% used. Yes I need more RAM.

That's according to conky..
and that reminds me, who the hell made up "MiB" for a unit of measure?

375 MB's of RAM?

If so I use to have that much. *sigh* Those where the days...

---

### Post by mobilediesel on 2009-08-02
> **Tipped OuT said:**
> 375 MB's of RAM?

If so I use to have that much. *sigh* Those where the days...

Well, 384 but the onboard Intel video steals some.

---

### Post by dragos240 on 2009-08-02
I don't use ANY swap.

---

### Post by Tipped OuT on 2009-08-02
> **mobilediesel said:**
> Well, 384 but the onboard Intel video steals some.

Wow. That's a little bit. I had 512 MB's of RAM, but my on board ATI stole 128, so it made it 384 MB's of RAM. I hope you get more RAM soon, I upgraded my RAM to 784 MB's for only 15$ at Ebay.

---

### Post by liamnixon on 2009-08-02
I have a one gigabyte swap partition, but I've never actually used it with two gigabytes of RAM.

---

### Post by K.Mandla on 2009-08-02
> **dragos240 said:**
> I don't use ANY swap.
Me either. And because of that I generally shave swap partitions down to 256 or 128 megabytes. 

The only machine I have that ever touches swap space is a 100Mhz Pentium with only 16Mb of RAM.

---

### Post by PurposeOfReason on 2009-08-02
> **coldReactive said:**
> Would YOU use up all 500 GB of your hdd? All my musics are on a flash drive, and most of my documents too. They only take up about 1 GB so far.
Here is me sitting on over 2TB of data. I don't have a swap partition. 6GB of ram and I only go through that when I compile of bust out emulators/virtual machines.

---

### Post by init1 on 2009-08-02
> **coldReactive said:**
> Would YOU use up all 500 GB of your hdd?
Music and movies. I've nearly filled up my 250GB drive.

---

### Post by kk0sse54 on 2009-08-02
0GB swap
3GB Ram

---

### Post by amitabhishek on 2009-08-03
2gb.

---

### Post by Viva on 2009-08-03
2GB RAM, 5GB Swap

---

### Post by gnuvistawouldbecool on 2009-08-03
1.4GB RAM (128MB for ati x200m)
1.1GB Swap, rarely used.  Infact I think the 9.10 alpha 3 I had didn't detect the swap andc ran fine....

Compaq presario v5000.

---

### Post by Trail on 2009-08-03
2GB RAM, 256Mb Swap.

I figured I wouldn't disable it, since I think I have noticed that at times, when an application is idle for a long time (for example a firefox with a signal-suspend on it) it tends to offload the memory to swap, so I assume it would use more physical RAM as cache/buffers.

---

### Post by ssam on 2009-08-03
depends what you want to happen when a program decides it wants to allocate 10GB of ram.

if you consider this a bug, and you want the OS to quickly kill the program for running out of RAM, then have a small amount of swap.

if you want the program to keep running (maybe at a fraction the speed it would if it had enough RAM), then have lots of swap.

ubuntu will move to swap files soon, so it will be very easy to adjust swap size on the fly [https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-swapfile](https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-swapfile)

---

### Post by Nythain on 2009-08-03
1GB ram, 1GB swap, and i find if im not running awesome or something equally as lightweight, im easily using 500+MB physical and 100+MB swap. i wish i still had my screenshot of KDE running using 925MB ram and all 1GB of swap from the other day

---

### Post by JohnFH on 2009-08-03
> **ssam said:**
> 
ubuntu will move to swap files soon, so it will be very easy to adjust swap size on the fly [https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-swapfile](https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-swapfile)

This is already not that difficult, especially if you don't care about hibernating.  I use a swap file instead of a partition.  If you want hibernation then you need to find the filesystem offset of the swap file using filefrag.

Tutorial link:
[HOWTO: Use swapfile instead of swap partition and have working hibernation]("http://ubuntuforums.org/showthread.php?t=1042946")

---

### Post by t0p on 2009-08-03
My desktop machine at home is a little aged.  It currently has 256 MB of RAM, and I went with what the Ubuntu installer advised for swap.  I'm not at home right now so I can't check, but I expect that's 256 MB x 3.

On the netbook I'm using right now (EeePC 701, 512 MB RAM, 4 GB SSD) I have *no* swap.  This is to reduce the number of writes done to the disk (to hopefully extend the lifespan of the flash) and because storage space is at a premium when you're using a SSD of just 4 GB! (I've also got a 4 GB SDHC card on which my /home is mounted, and I intend to upgrade that to 16 GB when finances allow... but that is still *tiny* compared to most machines.  In such circumstances, swap is a luxury I can well do without.)

---

### Post by MichealH on 2009-08-03
I used to have 20GB but now I have 1GB as I got told 20GB is alot
I have:
1.5GB RAM
1GB SWAP

---

### Post by aaaantoine on 2009-08-03
2 GB Swap
4 GB RAM.

I created the swap partition when I still had 1 GB RAM.
Other than some logical adjustments (moving the swap partition elsewhere on the drive), the swap hasn't changed.

---

### Post by doorknob60 on 2009-08-03
2 GB. I dont' use it, and especially now since I recently upgraded from 2 GB to 4 GB of RAM, I *really* don't need it. But I still have over 150 GB of unallocated space and even more unused space in my partitions so space isn't exactly an issue right now.

---

### Post by RPG Master on 2009-08-03
I have 6 gigs of swap space and 3 gigs of RAM. Are y'all saying I can just delete that partition and nothing bad would happen? 'Cus I could really use the space :D

---

### Post by Tipped OuT on 2009-08-03
> **RPG Master said:**
> I have 6 gigs of swap space and 3 gigs of RAM. Are y'all saying I can just delete that partition and nothing bad would happen? 'Cus I could really use the space :D

Yes, with 3 Gigs of RAM you should be more then fine... unless your using Vista or Windows 7. :P

---

### Post by RPG Master on 2009-08-03
Or I should say, can I just open gParted, delete that partition and then allocate that space to my main partition without anything bad happening?

---

### Post by HappyFeet on 2009-08-03
I only gave myself 300mb of swap. I have 4gb of ram, and never use it anyway. 99gb of swap? Ridiculous. I would create other partitions with that space and install other distros. But I would not waste it.

---

### Post by HappyFeet on 2009-08-03
> **RPG Master said:**
> Or I should say, can I just open gParted, delete that partition and then allocate that space to my main partition without anything bad happening?

I would just resize the swap partition with gparted, and leave yourself about 500mb of swap.

---

### Post by tjwoosta on 2009-08-03
Any more then 2Gb is just wasted space. Even 2GB is a bit overboard for a swap partition.  If you read up about what the swap partition is and how it works you will understand. Most people never even touch their swap partition, at all, because they have plenty of physical ram.  Ubuntu usually uses somewhere between 350MB and 1.3GB, depending on what you are running.  If you have 2GB ram, you will most likely never have enough information in memory to need the swap partition at all. (unless of course your running a bunch of VM's, but in that case you should already know how memory works.)

I have 1GB ram and I hardly ever swap, even with a full fledged compiz fusion environment, and 256MB allocated to a winXP virtualbox. When it does swap it never uses more then 256MB of my 1GB swap partition.

My current environment uses only 80MB of ram at idle, and hardly ever goes up to 800MB and thats only with 512mb dedicated to virtualbox.

So you can see even my 1GB swap partition is almost inane.  Having more then 2GB is asinine.

---

### Post by evermooingcow on 2009-08-03
I have 10MB because I read some where that the kernel operates more efficiently if you have a swap partition even if it never gets used. The guide I was following suggested something in the order of kilobytes of swap if you have enough RAM and don't actually need swap space. Unfortunately I don't remember where I found this guide.

---

### Post by Tipped OuT on 2009-08-03
> **RPG Master said:**
> Or I should say, can I just open gParted, delete that partition and then allocate that space to my main partition without anything bad happening?

As HappyFeet said, I would just re size it, to be on the safe side. Although, I suggest you re size it to something MUCH smaller then 500 MB's if you really don't want your swap anymore. Otherwise it's just wasted space, you have more then enough RAM.

---

### Post by djurny on 2009-08-03
1gib swap, 8gib ram :) bit of a bummer, i don't get to hibernate now :(

---

### Post by MaxIBoy on 2009-08-03
I have *NO* swap (there's an 8 gig swap partition but I've disabled it.)

---

### Post by chucky chuckaluck on 2009-08-03
people boast about swap? isn't that like boasting about who your wife is cheating on you with?

---

### Post by .Maleficus. on 2009-08-03
> **chucky chuckaluck said:**
> people boast about swap? isn't that like boasting about who your wife is cheating on you with?
Or who has the tiniest... hands.

---

### Post by BabakSM on 2009-08-03
2 gb... but currently using none of it, lol. 4 GB of ram suffices for me (and I don't think I've ever even used half of that, at least on Ubuntu).

---

### Post by MasterNetra on 2009-08-03
> **coldReactive said:**
> Would YOU use up all 500 GB of your hdd? All my musics are on a flash drive, and most of my documents too. They only take up about 1 GB so far.

Here is some wisdom: [http://catb.org/~esr/writings/unix-koans/nervous.html](http://catb.org/~esr/writings/unix-koans/nervous.html) :p Hint: Its valid because its about overdoing things. ;)

---

