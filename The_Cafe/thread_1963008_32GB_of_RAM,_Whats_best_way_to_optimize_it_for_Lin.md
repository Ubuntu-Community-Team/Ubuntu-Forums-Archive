---
title: "32GB of RAM, Whats best way to optimize it for Linux."
date: 2012-04-21
forum: The Cafe
---

### Post by Bandit on 2012-04-21
OK Everyone,
I have decided on purchasing 32GB of DDR3-1600 for my new system. Its going to be Corsair Vengeance 1.35v DRAM. Its going pretty cheap right now for around 100-120 bucks here in the US with tax and all. So I want to take advantage of the low pricing and since the new mobo has Quad Channel support. I wanted to find the best way to make the most use of the RAM. This is something I never tried before since I never had ram to spare. 

Ideas? Suggestions?

Thanks,
Joe

EDIT:
Decided to go with just 16GB for my box, but still would love to here any optimization solutions that you do..
Cheers..

---

### Post by Lightstar on 2012-04-21
Hard question since I never use more than 70% of my 4gb.

I guess if you aren't the type to read error logs, you could always put those in the ram along with internet temporary files, etc.  It can clear out after every reboot, keeps the HDD a bit cleaner.  It's more useful for those who use SSD hard drives though since it will cut down a lot on the read / write to the hard drive.

I heard you can mount the ram memory as ramdisk to use as storage or to keep applications in the RAM so that it loads really quickly.  I would do that for programs you use very often, firefox, nautilus, whatever.

---

### Post by Bandit on 2012-04-21
> **Lightstar said:**
> Hard question since I never use more than 70% of my 4gb............

LOL same here.. I was thinking about allocating 16GB as a RAMDisk, but wonder how much more of a performance boost would this be over a average SATA 6GB/s SSD?

---

### Post by 3rdalbum on 2012-04-21
It's not a bargain if it is useless to you. I couldn't even fill 4GiB on my Ubuntu system, so 32GiB will be sitting dormant for you.

Don't waste your money. Buy less RAM. 4GiB is plenty for most people today and gives extra head room for the future.

---

### Post by Bandit on 2012-04-21
> **3rdalbum said:**
> It's not a bargain if it is useless to you. I couldn't even fill 4GiB on my Ubuntu system, so 32GiB will be sitting dormant for you.

Don't waste your money. Buy less RAM. 4GiB is plenty for most people today and gives extra head room for the future.

Yea thats the question I am facing. On one side I see a bargin and get that voice in the back of my head saying "youll be awesome with that" then I get another voice of reason saying "you dont use the 4gigs you use now!!"... I need help  :confused:

If I can justify the need in boosting performance. I will do it. Otherwise I am thinking of just getting 16GB even that is still overkill.

---

### Post by drawkcab on 2012-04-21
run 10+ virtual operating systems?

---

### Post by CharlesA on 2012-04-21
> **drawkcab said:**
> run 10+ virtual operating systems?
That's the only thing I can think of.

---

### Post by d3v1150m471c on 2012-04-21
[http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux](http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux)

---

### Post by Bandit on 2012-04-22
> **drawkcab said:**
> run 10+ virtual operating systems?

Well I can only hope with that much ram freaking Netflix video will quit suffering from decode lag.

---

### Post by SeijiSensei on 2012-04-22
More memory is good, but it won't speed up your processor.  If you have a slow CPU and want to improve Netflix performance, you might find spending $50-100 on a modern NVIDIA or ATI card with support for on-board graphics decoding a better use of funds.

More RAM will buy you a bigger disk cache and might speed things up some.  The only way to tell is to monitor the system's performance, even with something as simple as top.  How much memory is devoted to caching?  What happens if you load a bunch of applications?  Do some of them get swapped out?  If you can open all of the applications you normally use and don't experience substantial delays switching among them, more memory probably won't make a big difference.

Do you run virtual machines using something like VirtualBox?  With 8 GB you could create a 4 GB Windows VM and still have 4 GB left over for Ubuntu.  If this were a server on which you wanted to run a number of virtual servers, then you might want 32 GB.  On a desktop machine, I'd say more than 16 GB is overkill, and 8 GB is probably plenty.

---

### Post by Bucky Ball on 2012-04-22
Maybe upgrade the processor instead of buying all that RAM if you're after a speed increase. ;)

---

### Post by Bandit on 2012-04-22
> **SeijiSensei said:**
> More memory is good, but it won't speed up your processor...........

I am all aware. My system I have now isnt lacking, Phenom 9850 2.5GHz Qaud, 4GB DDR2-800 Dual Channel, MSI Cyclone O/C'd nv460GTX, 4x WD Blue 320GB HDD(s) RAID0/1.2TB Stripped Disk Array, MSI 770T-C45 Mobo. 
Half the reason I am building a new system is to give this one to my daughter. 
I am putting together a i7-3930K Linux Box for my new system and its getting all the bells and whistles that most really high end gaming systems would. Just wondering if 32GB will just be wasted or better spent on something else. Hence the question if I could put it to better use. Pretty sure I want need a /swap partition. But may be able to take some caching off the the SSD or HDD and place it in ram. Stuff like that..:D

EDIT:
Better post the specs for the new Linux Box, and yes it will ONLY be running linux.

*_New Gear:_*
Intel i7-3930K 3.2GHz 6 Core CPU (3.8GHz Turbo) Unlocked Processor. Will be OCing this joker.. 
ASUS Sabertooth X79 LGA 2011 Mobo.
Cooler Master 1000watt Pro PSU, Modular, Bronze 80+ Rating
Corsair Vengence DDR3-1600 (16GB or 32GB havent made up my mind, will be in quad channel kits)
Corsair H80 Water Cooler unit. (H100 will not fit in case.. boo!!)
Samsung 830 Series, 256GB SATA-III 6GB/s SSD
Cougar CF-V12HP 120mm Hydro Bearing 70CFM 16db Fans (5x of them)

_*Old Gear using in rig:*_
MSI Cyclone O/C'd nv460GTX (re using this one since just got it last summer, putting older radeon in daughters box)
WD Caviar Blue 320GB HDD (using for my /home drive, system will be place on the SSD).
Cooler Master Storm Scout case. (Wanted a new one but cant find another I like as much.)

There ya have it.. 
Now 32GB or 16GB is the question.. hehe   :D

---

### Post by 1clue on 2012-04-22
I've been running 12g on my system and have some input I consider to be relevant.

If you're just running a desktop system then you're wasting your money.  I can definitely see the advantage to going with 8g if you're a heavy app user, but there's a limit to how much memory normal workstation apps can use.

One thing I noticed is that the "unused" memory slowly gets used as a disk cache.  For me it takes about a month of uptime to use up 11.5g, and then it pretty much stays there.  The most I can get to be used with normal desktop use is 6g.

Now, in order to do that I use a few tmpfs filesystems.  Where and what kinda depends on the distro, but basically you find temp directories that have a lot of data written to them rapidly, then mount a tmpfs filesystem there.  I'm a software developer, so I did it with the directory my compiler uses, and it's much quicker.  Any scratch space that can go away when the system reboots can be done this way.

To really use that much space, you either need to run a few virtual machines (which I also do every now and again) or run a service with a whole lot of data involved, which I also do every now and then.  Mysql for example, with a massive amount of data that you cycle through a lot, will suck up a considerable amount of memory.  That's as it should be.

So you can find ways to use up the memory, but as I understand your situation you haven't bought the memory yet, right?  I don't know that I would just hop out and buy memory you don't need.  I can see doubling what you have if you ran out, but not buying that much just because.

I got my 12g because I had some pretty specific things I wanted to do with it, and occasionally I use most of it.  The entire system was designed around my job requirements.  Even so, I started with 6g just to be safe and when I actually used all of it I went out and bought the other set of sticks.

---

### Post by 1clue on 2012-04-22
There are people who put their operating system in a RAM disk.  32g is certainly enough for that.  Not sure what that gets you considering that the normal OS will go ahead and do that anyway.  Just leave your system up for awhile and apps you have used before will load a lot faster than they did the first time.

Memory doesn't inherently speed your system up, as everybody and their dog mentioned already.  However a lot of other things people do won't speed it up much either.  Enhancing system speed needs an understanding of how it works, and a coordinated effort using multiple tools.

An example would be my previous post about adding RAM and then using tmpfs in strategically beneficial places.

---

### Post by Bandit on 2012-04-22
> **1clue said:**
> I've been running 12g on my system and have some input I consider to be relevant............

Good info, I think I will just stick to 16GB since I seem to do many things you do as well and I should never have to think about the ram. 32 would just be wasted in vain.. 
Many thanks.

If anyone else has any pointers on speeding up some programs caching or what not. Please feel free to keep posting.

EDIT:
I remember back when I was running my 486DX-4 100 with 16MB of RAM. Most systems back then only had 4MB at most, only few high end had 8MB. Everyone wondering why the heck I optd for 16MB. LOL it cut a huge chunk of time off from compiling some programs. My best bud at the time had a P60 and my system ran circles around it. Thats the driving force behind this question 16-vs- 32.. But I think its safe to say 16GB should be fine in this case. 16MB to 16GB, feels like we have came full circle..

---

### Post by sandyd on 2012-04-22
> **SeijiSensei said:**
> More memory is good, but it won't speed up your processor.  If you have a slow CPU and want to improve Netflix performance, you might find spending $50-100 on a modern NVIDIA or ATI card with support for on-board graphics decoding a better use of funds.

More RAM will buy you a bigger disk cache and might speed things up some.  The only way to tell is to monitor the system's performance, even with something as simple as top.  How much memory is devoted to caching?  What happens if you load a bunch of applications?  Do some of them get swapped out?  If you can open all of the applications you normally use and don't experience substantial delays switching among them, more memory probably won't make a big difference.

Do you run virtual machines using something like VirtualBox?  With 8 GB you could create a 4 GB Windows VM and still have 4 GB left over for Ubuntu.  If this were a server on which you wanted to run a number of virtual servers, then you might want 32 GB.  On a desktop machine, I'd say more than 16 GB is overkill, and 8 GB is probably plenty.
+1.
I have 32GB of ECC DDR3, and I have never used more than 16G. But then again, its a modified workstation that uses two (it has 4 sockets...) Xeon E3-1245s. Runs Ubuntu 11.10 with Xen. Even If I run several VMs, the RAM usage has never gone above 16G. Once you get to a certain point of RAM, even with all the disk caching, adding more RAM will not make things faster.

Buying 32G of RAM is a waste of money, and the only places where that amount would be used is in datacenters. I can confirm, however, that I do use 32G of RAM. Just not for home usage.

---

### Post by Bandit on 2012-04-22
> **sandyd said:**
> +1.
I have 32GB of ECC DDR3,.........

Many thanks for the heads up Sandyd. Yea think I am just going to stick to 16gb so I can purchase two 8GB Quad Channel kits (4x2GB sticks) and fill all 8 banks on the mobo.

[IMG]http://images.highspeedbackbone.net/skuimages/large/A455-3156-chicklet00-aa.jpg[/IMG]

---

### Post by 1clue on 2012-04-22
If the prices aren't too far apart, you could only fill half your slots so that if you want to upgrade in the future it won't be as much of a hit.

---

### Post by Bandit on 2012-04-22
> **1clue said:**
> If the prices aren't too far apart, you could only fill half your slots so that if you want to upgrade in the future it won't be as much of a hit.

Total upgrade cost is already at 1749.88 USD plus shipping and tax. Its already gonna be a heck of a hit.. hehe :popcorn:
Then again all this is pending some money I am supposed to get sometime over the next few months. So it want be purchased today. The ivy bridge stuff may be out before to long as well and the mobo and cpu could very well change. I tend to plan things out and monitor quality of the product by reading many many reviews over a few months period before making a purchase. So it could be June or July before I can build this, but i hope not that long.. hehe

---

### Post by CharlesA on 2012-04-22
OW! My newest desktop build cost close to a grand (Phenom II x4 965 black, 8GB RAM, GTX560Ti), and my new server build was the same (i7 2600K, 16GB RAM), but the server is running onboard video cuz it's headless 99% of the time.

---

### Post by Bandit on 2012-04-22
> **CharlesA said:**
> OW! My newest desktop build cost close to a grand ............

The CPU is about 600 USD. Which performance wise its twice as fast as a FX-8150 from me best assessment from ready multiple reviews. So I am kewl with that. But what bites is that the motherboards cost about twice as much as their AMD counterparts. The ASUS Sabertooth X79 intel board is ~320USD while the ASUS 990FX AMD board is ~180USD

---

### Post by BrokenKingpin on 2012-04-22
Running VMs if you have the need for it. 32 gigs of RAM is pretty useless for a PC, but for a home server you could potentially do some cool things with VMs.

I am not saying you shouldn't buy the RAM, having that amount is just awesome, you just won't be using most of it 99% of the time (if it is just a PC).

---

### Post by sffvba[e0rt on 2012-04-22
32GB.... hmmm... if you get another 7: CPU's, motherboards, HDD, PSU, screens and some peripherals you could have 8 computers...

:p


404

---

### Post by Bandit on 2012-04-22
> **BrokenKingpin said:**
> Running VMs if you have the need for it. 32 gigs of RAM is pretty useless for a PC, but.........

Yea I was hoping there was something l33t I could have done with the extra 16gigs. But doesn't look like there really is. The kernel should automatically load up everything I run periodicity into upper RAM for faster accessing. But that's only going to go so far.
So instead of 32 I have revised my purchase list to only list 16GB which is Prob more then I need anyway. But I do use VBox often enough and run some FAH. I prob should change the thread to Solved I guess, but hoping some others will post kewl optimization's they have done.

---

### Post by thenixedreport on 2012-04-22
With 32 GB, you might not even need a swap partition.  :lolflag:

It would definitely come in handy for really intensive tasks, especially when it comes to editing huge image files.

---

### Post by arclance on 2012-04-22
> **thenixedreport said:**
> It would definitely come in handy for really intensive tasks, especially when it comes to editing huge image files.
Making panoramas with Hugin can use over 32GB of memory if your source images are of a high enough resolution or you are stitching a multi-row panorama.
It's not fun to discover that by crashing your computer when you run out of swap....
I am thinking of upgrading to 16GB of ram because of how much hugin uses.

---

### Post by CharlesA on 2012-04-22
Won't need swap unless you plan on using hibernation. ;)

---

### Post by sandyd on 2012-04-22
> **Bandit said:**
> The CPU is about 600 USD. Which performance wise its twice as fast as a FX-8150 from me best assessment from ready multiple reviews. So I am kewl with that. But what bites is that the motherboards cost about twice as much as their AMD counterparts. The ASUS Sabertooth X79 intel board is ~320USD while the ASUS 990FX AMD board is ~180USD
*winces*
My graphics card costs $4000 alone....

---

### Post by Artemis3 on 2012-04-22
Unless you use something special such as a large database, or virtualization; very likely that memory will remain unused. I have 8 and barely ever use more than 3; i don't even have swap.

It would be funny to let the installer choose a swap partition size there; 64GiB? very likely ;). Hibernating that should be pathetic...

---

### Post by Bandit on 2012-04-22
> **sandyd said:**
> *winces*
My graphics card costs $4000 alone....

O' dear... :shock:

Does it make coffee and put the kids to bed?

You must be using one of those Quadro cards, we have a few machines at work using them to run [Solidworks]("http://www.solidworks.com/") CAM software, I know it requires like 4GB of VRAM just for it to function at 100%. I am supposed to be training on that soon since I got "0" CAD experience.

---

### Post by Bandit on 2012-04-22
> **arclance said:**
> Making panoramas with Hugin can use over 32GB of memory .............

You know I have pushed GIMP to the breaking point with a few large files. Like 10000x4000 res PNGs. But seldom do I need that. I just keep the /swap for that. hehe.. Might as well make use of the SSD also.. :biggrin:

---

### Post by sandyd on 2012-04-22
> **Bandit said:**
> O' dear... :shock:

Does it make coffee and put the kids to bed?

You must be using one of those Quadro cards, we have a few machines at work using them to run [Solidworks]("http://www.solidworks.com/") CAM software, I know it requires like 4GB of VRAM just for it to function at 100%. I am supposed to be training on that soon since I got "0" CAD experience.
I'm using one of these babies (_[http://www.amazon.com/PNY-DisplayPort-Profesional-Graphics-VCQ6000-PB/dp/B0044XUD1U](http://www.amazon.com/PNY-DisplayPort-Profesional-Graphics-VCQ6000-PB/dp/B0044XUD1U)_) for video editing, design, and minor rendering. Major rendering is done at the server farms where there are likely stacks of these GPUs:lolflag:

---

### Post by Bandit on 2012-04-22
> **sandyd said:**
> I'm using one of these babies ([http://www.amazon.com/PNY-DisplayPort-Profesional-Graphics-VCQ6000-PB/dp/B0044XUD1U]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133325")) for video editing, design, and minor rendering. Major rendering is done at the server farms where there are likely stacks of these GPUs:lolflag:

Yea that doesnt have enough RAM. We have a few workstations that run Solidworks and it requires that Quadro with 4GB to work correctly. We tried to be cheap and SLI some NV 500 series and that didnt work.. So quadro happened.. Now solidworks works.. Hate it when software is writen around one particular card to function correctly.

---

### Post by arclance on 2012-04-22
> **Bandit said:**
> You know I have pushed GIMP to the breaking point with a few large files. Like 10000x4000 res PNGs. But seldom do I need that. I just keep the /swap for that. hehe.. Might as well make use of the SSD also.. :biggrin:
One of my multirow panoramas came out 10087x5845 using my old 8MP digital SLR and 8bit jpeg source images.  It takes 1.03GB to open it with GIMP.
My new camera is 21.1MP and I have switched to shooting in RAW (losslessly compressed 14bit) which must be converted to 16bit TIFF to load them into hugin.
If I retake that panorama with my new camera I will need 12+GB of swap to make the panorama.

---

### Post by Bandit on 2012-04-22
> **arclance said:**
> One of my multirow panoramas came out 10087x5845 using my old 8MP digital SLR and 8bit jpegs source images.  It takes 1.03GB to open it with GIMP.
My new camera is 21.1MP.............

What Camera you use? My wife likes to shoot photos but the best one I will get her is a Rebel T3i. I dont know much about it, but she likes it. :KS

---

### Post by CharlesA on 2012-04-22
> **arclance said:**
> One of my multirow panoramas came out 10087x5845 using my old 8MP digital SLR and 8bit jpeg source images.  It takes 1.03GB to open it with GIMP.
My new camera is 21.1MP and I have switched to shooting in RAW (losslessly compressed 14bit) which must be converted to 16bit TIFF to load them into hugin.
If I retake that panorama with my new camera I will need 12+GB of swap to make the panorama.

SLR camera, I presume? The best one I have is like 10MP, I believe.

---

### Post by sandyd on 2012-04-22
> **Bandit said:**
> Yea that doesnt have enough RAM. We have a few workstations that run Solidworks and it requires that Quadro with 4GB to work correctly. We tried to be cheap and SLI some NV 500 series and that didnt work.. So quadro happened.. Now solidworks works.. Hate it when software is writen around one particular card to function correctly.
Hmm...
That was the wrong link.
Fixed.

---

### Post by CharlesA on 2012-04-22
> **sandyd said:**
> Hmm...
That was the wrong link.
Fixed.
I saw [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133347") one (which is the same one in your edited link) and I think my jaw hit the floor.

---

### Post by arclance on 2012-04-22
> **Bandit said:**
> What Camera you use? My wife likes to shoot photos but the best one I will get her is a Rebel T3i. I dont know much about it, but she likes it. :KS
> **CharlesA said:**
> SLR camera, I presume? The best one I have is like 10MP, I believe.
Both camera's are SLRs, the old camera is a [Canon EOS Digital Rebel]("http://www.usa.canon.com/cusa/support/consumer/eos_slr_camera_systems/eos_digital_slr_cameras/eos_digital_rebel").
My new camera is a [Canon EOS 5D Mk.II]("http://usa.canon.com/cusa/consumer/products/cameras/slr_cameras/eos_5d_mark_ii") with a [EF 16-35mm f/2.8L II USM]("http://www.usa.canon.com/cusa/consumer/products/cameras/ef_lens_lineup/ef_16_35mm_f_2_8l_ii_usm?selectedName=Specifications") lens for panoramas/general photography.
The lens cost more than my old camera did when it was new but it was worth it.
Digital Photo Professional works in Wine so I don't need to use Windows to convert the RAW images to something else.
It's too bad there is no 16bit Photoshop equivalent for Linux so I do need to run a Windows VM for advanced touchup and color correction.

---

### Post by CharlesA on 2012-04-22
Nice camera. I've got a cheap point-and-shoot Nikon that works fine for what I need. I do know a couple professional photographers and they have a ton of gear. I cannot recall what camera they use but I'm sure it's one of those expensive ones - I remember them telling me one of the lenses for it was about 5 grand.

---

### Post by sandyd on 2012-04-22
> **CharlesA said:**
> I saw [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133347") one (which is the same one in your edited link) and I think my jaw hit the floor.
Its supposed to be that expensive. Luckily, it didn't cost that much, since I needed it for work. Guys were nice enough to give me a discount.
 
But then again, all the rendering is done on linux ;)

---

### Post by 1clue on 2012-04-22
> **Bandit said:**
> Total upgrade cost is already at 1749.88 USD plus shipping and tax. Its already gonna be a heck of a hit.. hehe :popcorn:
Then again all this is pending some money I am supposed to get sometime over the next few months. So it want be purchased today. The ivy bridge stuff may be out before to long as well and the mobo and cpu could very well change. I tend to plan things out and monitor quality of the product by reading many many reviews over a few months period before making a purchase. So it could be June or July before I can build this, but i hope not that long.. hehe

Back when I bought my i7 I spent about $2800, and then shortly after that went up to about $3500.  Now you can get everything for half that of course.  Mine's just an i7 920.


> **thenixedreport said:**
> With 32 GB, you might not even need a swap partition.  :lolflag:

It would definitely come in handy for really intensive tasks, especially when it comes to editing huge image files.

Speaking from personal experience, with 6g you don't need swap when you're doing normal desktop type things, and with 12g you don't need swap when you're doing relatively hardcore things.  Sizes mentioned map to MY system, not the OP's.

With 32g if you wind up needing swap, you're either doing something phenomenally l33t or you're running some really, really, really poorly written software.

I was going to put a smiley on that but it's not a joke at all.  32g is a boatload of memory for any desktop.  Sucking down that much RAM, you either need to know a lot about what you're doing or you gotta really suck at what you're doing.

---

### Post by arclance on 2012-04-22
> **CharlesA said:**
> Nice camera. I've got a cheap point-and-shoot Nikon that works fine for what I need. I do know a couple professional photographers and they have a ton of gear. I cannot recall what camera they use but I'm sure it's one of those expensive ones - I remember them telling me one of the lenses for it was about 5 grand.
Yes the [fixed focal length lenses over 300mm]("http://www.bhphotovideo.com/c/search?atclk=Fixed+Focal+Lengths_300mm&ci=274&N=4288584247+4294185281+4261208100+4261208101+4261208102+4261208103") usually cost over $3000 the most expensive being $14,000 right now.  
Most photographers I know rent those, I don't own any.  My uncle used to borrow them from his job when he worked at Sports Illustrated.
They used to make a [1200mm lens]("http://www.canon.com/camera-museum/camera/lens/ef/data/super_telephoto/ef_1200_56l_usm.html") that sold for $89,579, I don't think it sold very well since they stopped making it.

---

### Post by CharlesA on 2012-04-22
> **arclance said:**
> Yes the [fixed focal length lenses over 300mm]("http://www.bhphotovideo.com/c/search?atclk=Fixed+Focal+Lengths_300mm&ci=274&N=4288584247+4294185281+4261208100+4261208101+4261208102+4261208103") usually cost over $3000 the most expensive being $14,000 right now.  
Most photographers I know rent those, I don't own any.  My uncle used to borrow them from his job when he worked at Sports Illustrated.
They used to make a [1200mm lens]("http://www.canon.com/camera-museum/camera/lens/ef/data/super_telephoto/ef_1200_56l_usm.html") that sold for $89,579, I don't think it sold very well since they stopped making it.
Yep. Those would be the ones they use. I'm kinda surprised they bought them but they do enough photography where renting a lens would probably be more expensive. Needless to say they are insured. Heh.

---

### Post by wolfen69 on 2012-04-23
If you want 32gb of ram and don't know what to do with it, you are probably wasting your money. You can do a heck of a lot with "only" 8 gigs. With 4 gigs, I can have vbox running with a bunch of apps on the side. But hey, it's *your* money.

---

### Post by Bandit on 2012-04-23
> **wolfen69 said:**
> If you want 32gb of ram and don't know what to do with it, you are probably wasting your money. You can do a heck of a lot with "only" 8 gigs. With 4 gigs, I can have vbox running with a bunch of apps on the side. But hey, it's *your* money.

Yea I am gonna go with just 16gigs. I would use it from time to time and that allows me to also fill all 8 banks of ram into the mobo. It will be Two Corsair Vengeance quad channel kits 2x (4x 2GB) sets. 16GB for about 120 bucks isnt bad at all and since this system upgrade is a major one non the less, I am prob gonna have to be using this same setup for the next 4 maybe 5 years to get my moneys worth. $2000 / 60 months = $33.33 a month. Just over a dollar a day..

---

### Post by cecilpierce on 2012-04-23
Must be nice to be rich   :p

---

### Post by haqking on 2012-04-23
I have 32GB and no optimization.

So cheap these days, i went with Kingston, started out at 16 on my new build then bought some more from Crucial

Great for running various VM's.

Peace

---

### Post by Bandit on 2012-04-23
> **cecilpierce said:**
> Must be nice to be rich   :p

Nah not rich, just work my rear end off. I dont smoke, seldom drink and other the fishing I dont have any other hobbies. Not smoking alone saves me enough money to build the system.

---

### Post by CharlesA on 2012-04-23
> **Bandit said:**
> Nah not rich, just work my rear end off. I dont smoke, seldom drink and other the fishing I dont have any other hobbies. Not smoking alone saves me enough money to build the system.
Seriously. Smoking is a hell of a money sink. Fishing.. not so much (unless you go nuts over lures and reels and gear and stuff...)

---

### Post by pqwoerituytrueiwoq on 2012-04-23
lots of ram disks
definitely make /tmp one
if you make a crap load of virtual machines be sure you have enough video ram to go around when running 5 at once
you could have windows on each side of your cube each playing a netflix film at the same time and run a screen recorder

---

### Post by wolfen69 on 2012-04-24
to be honest, I'm surprised people cared about your "problem"

I'm glad you got it sorted.

---

### Post by Bandit on 2012-04-24
> **wolfen69 said:**
> to be honest, I'm surprised people cared about your "problem"

I'm glad you got it sorted.

Well I really appreciate everyones input. :)

Again thanks to everyone for posting. 

I decided on 16G which should still be overkill 98% of the time, but will allow me so optimization's on some program caching, more to VMs and some large image editing.

- Joe

---

### Post by thenixedreport on 2012-04-24
In my personal opinion, I would go ahead and upgrade to 32 GB of RAM while prices are as low as they are.  Even with Ubuntu and other FOSS Operating Systems, requirements are going to get a bit higher as time goes on.  It can't hurt anything in the long run, and you can always upgrade other components, such as the CPU, at a later date (when prices are more favorable).

---

### Post by Bandit on 2012-04-24
> **thenixedreport said:**
> In my personal opinion, I would go ahead and upgrade to 32 GB of RAM while prices are as low as they are.  Even with Ubuntu and other FOSS Operating Systems, requirements are going to get a bit higher as time goes on.  It can't hurt anything in the long run, and you can always upgrade other components, such as the CPU, at a later date (when prices are more favorable).

Speaking of CPU, anyone heard anything about Ivy Bridge release yet? Thought it was supposed to be out now?

EDIT: Err.. Looks like [Anand has a review posted]("http://www.anandtech.com/show/5771/the-intel-ivy-bridge-core-i7-3770k-review")..

---

### Post by ssam on 2012-04-24
install preload. it figures out what files to keep in RAM to help speed up program launching. its worth having if you have more than about 2GB of RAM.

---

### Post by a2j on 2012-04-24
using all of my 8Gb, need to double that. Various ram-hungry applications. Its all depends on what you're doing. Browsing the web with 32Gb is like driving a school bus while single. Does the job but waste of space/money/etc.

---

### Post by *^kyfds( on 2012-04-24
as soon as i read the title of this thread my jaw hit the floor.

i'm only running on 512mb of ram on my dell 

\\:D/

---

### Post by Ceiber Boy on 2012-04-24
> **3rdalbum said:**
> It's not a bargain if it is useless to you. I couldn't even fill 4GiB on my Ubuntu system, so 32GiB will be sitting dormant for you.

Don't waste your money. Buy less RAM. 4GiB is plenty for most people today and gives extra head room for the future.

+1

However, I get the feeling that the purchase was to do with fulfilling a passion and interest!
So it wasn't a wast of mony from that point of view.

Good luck finding things to do with it.

Regards.

---

### Post by codingman on 2012-04-24
Boy, an X79 board. I was just waiting for IB to get the next sabertooth board ;) to upgrade from an a8n-sli ;)

---

### Post by Bandit on 2012-04-24
> **Thehumorouscheese said:**
> as soon as i read the title of this thread my jaw hit the floor.

i'm only running on 512mb of ram on my dell 

\\:D/
Sounds like its time to upgrade that ram.. 
Sadly I have a great working Sempron system that I have been trying to get up and running for a year now. But so hard to just find old DDR333 or 400, cheaply.. If it could have been at least DDR2 I have a ton of those sticks sitting around.



> **Ceiber Boy said:**
> +1

However, I get the feeling that the purchase was to do with fulfilling a passion and interest!
So it wasn't a wast of mony from that point of view.

Good luck finding things to do with it.

Regards.
Your correct it is. Sort of one of those guys that has OCD. If I look in my case and there is an empty ram slot, It drives me up the wall. It got to be filled. I would buy plain fake plastic RAM cards just for looks if they made them just for show.. hehe.. One reason I like the Vengeance RAM so much.. Its cool looking, and its approved to work with my board.. Thats also #2 reason I wanted 32GB. The 4x4 sets are approved. The 4x2 Quad Channel kits are not.. :( Not saying they will not work, but its not in writing that they do.


> **codingman said:**
> Boy, an X79 board. I was just waiting for IB to get the next sabertooth board ;) to upgrade from an a8n-sli ;)
I am keeping my eyes open. Really hoping that they would release 6 core IBs. But so far only Quads are to released first. So BOO.. I been running a Quad Core for 4 years now.. Me want more core.. hehe.. :lolflag:

---

