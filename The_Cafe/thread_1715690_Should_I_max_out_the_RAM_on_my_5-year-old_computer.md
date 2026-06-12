---
title: "Should I max out the RAM on my 5-year-old computer?"
date: 2011-03-27
forum: The Cafe
---

### Post by jhsu802701 on 2011-03-27
I have a 5-year-old HP DC7600 desktop computer (dual-core 3.4 GHz processor) that I bought used last fall.  This computer originally had four 256 MB RAM cards (for a total of 1 GB), but I just replaced one card with a 1 GB unit, boosting my total RAM to 1.75 GB.  The maximum RAM possible is 4 GB (four 1GB RAM cards).

I'm considering replacing at least two of the remaining 256 MB RAM cards with 1 GB cards.  (I understand that a 32-bit OS can only use up to about 3 GB, so I probably don't need that last 1 GB card.)  Is this something I should be doing now?  Are the RAM cards as cheap as they'll ever get?  Will the RAM cards become scarcer in the years ahead?

I intend to keep this computer for a LONG time.  Even with Ubuntu, Mint, Fedora, or other heavy distro, this computer could be good for another 10 years.  With a lightweight distro like Swift Linux, antiX Linux, or Puppy Linux, this computer could be good for another 20 years.

---

### Post by Dlambert on 2011-03-27
Might as well upgrade to the maximum you can, are you sure you cant run 64-bit?

---

### Post by jhsu802701 on 2011-03-27
> **Dlambert said:**
> Might as well upgrade to the maximum you can, are you sure you cant run 64-bit?

How important is it that I be able to run a 64-bit OS?  My computer maxes out at 4 GB of RAM, and I'm seriously doubting that the difference between 4 GB and 3.25 GB of RAM will ever be that significant.  Upgrading from 3.25 GB to 4 GB of RAM is an increase of only 23%, while the upgrade from 1.0 to 1.75 GB was an increase of 75%.  I think it will be a long time before even Ubuntu/Mint/Fedora actually need 3-4 GB of RAM and an even longer time before Swift/antiX/Puppy Linux do.

---

### Post by wizard10000 on 2011-03-27
> **Dlambert said:**
> Might as well upgrade to the maximum you can, are you sure you cant run 64-bit?

Five years old?  That's a single-core hyperthreading chip.  32-bit only.

edit:  It could be either a hyperthreading P4 or dual core Pentium D in that model, both at 3.4GHz.  The Pentium D is a 64-bit chip, the P4 isn't.

---

### Post by t4thfavor on 2011-03-27
If you can run 64 bit, you can run 8 or 16 GB probably. I have a Compaq from 2004/5 AMD 64 3500+ that will take 2x 4GB DDR2 dimms, and run perfectly. Seems like they just rate them at whatever size ram chips are out at the time times however many slots are there. I think this one says (on Crucial.com) Max 2GB.

---

### Post by tgm4883 on 2011-03-27
Even if it's 32-bit only, you could use the pae kernel to address 4GB of ram. The question I would have though is do you do anything on that system that will require that much memory?

---

### Post by d3v1150m471c on 2011-03-27
i'm using 3gb's of ram. i've never seen the usage get higher than a gb unless i'm running a vm simultaneously. actually i've tried by running multiple apps, got up to 800. i mean it wouldn't hurt but you might not use it. also because you have ram doesn't mean your hardware with ubuntu can use it. I'm not hardware savvy when it comes down to the grit of how things communicate but some processors and the like can only use so much ram.

---

### Post by t4thfavor on 2011-03-27
Just for clarity, I do video editing on the ancient desktop, as well as play SC2 and it uses lots more than the standard 3GB. I also have a 64 bit toshiba laptop that can't use more than 3GB so it's hit or miss for sure.

I usually borrow memory from a friend, or possibly from work before I buy to test for compatibility.

---

### Post by tgm4883 on 2011-03-27
> **d3v1150m471c said:**
> i'm using 3gb's of ram. i've never seen the usage get higher than a gb unless i'm running a vm simultaneously. actually i've tried by running multiple apps, got up to 800. i mean it wouldn't hurt but you might not use it. also because you have ram doesn't mean your hardware with ubuntu can use it. I'm not hardware savvy when it comes down to the grit of how things communicate but **some processors and the like can only use so much ram.**

Link?

---

### Post by Legendary_Bibo on 2011-03-27
My laptop has 4gb, and sometimes I'll have music playing, Firefox open, and the Gimp open as well as some other programs. It's enough RAM, but things get a bit slow once things start going into swap.

Also, I found out that I can't transcode videos or anything CPU intensive for a long period unless I leave my laptop open with a fan blowing on it. I leave my laptop closed because it has a VGA (HDMI on my laptop doesn't work with Ubuntu) cable hooked up to my monitor.

I've made that mistake twice, and it freaks me out when my laptop just shuts off in a snap, and then I go and feel my laptop and it's insanely hot.

---

### Post by Dlambert on 2011-03-29
I use 4 gigs of DDR3 1600, and never go over a gig either(Unless gaming), so depends on what you want.

---

### Post by Paqman on 2011-03-29
> **jhsu802701 said:**
> I have a 5-year-old HP DC7600 desktop computer (dual-core 3.4 GHz processor) that I bought used last fall.  This computer originally had four 256 MB RAM cards (for a total of 1 GB), but I just replaced one card with a 1 GB unit, boosting my total RAM to 1.75 GB.  The maximum RAM possible is 4 GB (four 1GB RAM cards).


You should check to see what type of memory controller you've got. If your mobo uses dual channels then you want to use matching pairs. In your current case you'd have 512MB in dual-channel and 1.25GB not. That would mean some of your RAM was significantly faster than other parts.

> 
I'm considering replacing at least two of the remaining 256 MB RAM cards with 1 GB cards.  (I understand that a 32-bit OS can only use up to about 3 GB, so I probably don't need that last 1 GB card.)

To use 3GB in dual-channel you'd want 2x1GB and 2x512MB, not 3x1GB. You need to make sure they're in the right slots, too.

> Will the RAM cards become scarcer in the years ahead?


Yes, older types of RAM can get pretty expensive.

---

### Post by dh04000 on 2011-03-29
> **jhsu802701 said:**
> I have a 5-year-old HP DC7600 desktop computer (dual-core 3.4 GHz processor) that I bought used last fall.  This computer originally had four 256 MB RAM cards (for a total of 1 GB), but I just replaced one card with a 1 GB unit, boosting my total RAM to 1.75 GB.  The maximum RAM possible is 4 GB (four 1GB RAM cards).

I'm considering replacing at least two of the remaining 256 MB RAM cards with 1 GB cards.  (I understand that a 32-bit OS can only use up to about 3 GB, so I probably don't need that last 1 GB card.)  Is this something I should be doing now?  Are the RAM cards as cheap as they'll ever get?  Will the RAM cards become scarcer in the years ahead?

I intend to keep this computer for a LONG time.  Even with Ubuntu, Mint, Fedora, or other heavy distro, this computer could be good for another 10 years.  With a lightweight distro like Swift Linux, antiX Linux, or Puppy Linux, this computer could be good for another 20 years.

Sounds like a good idea to me. Ram(3-4GB that up!), hard-drives, are super cheap these days. Get thee fastest ram and harddrive you can find for it. Then consider getting a better videocard.

Reinstall with Ubuntu 10.04 or later, and it will see 4GB or more. Uses PAE kernel with 3.2 GB or more.

Boom! It should last you for years more to come.

---

### Post by coolbrook on 2011-03-29
It's your duty, soldier!

:mrgreen:

---

### Post by BrokenKingpin on 2011-04-28
Up to 3/4GB is probably fine, it is not like you are playing high end games on an older system like that anyways.

---

### Post by Paqman on 2011-04-28
Tbh, I find 1GB is actually plenty for general browser/office/mail work on Ubuntu. It's really going to depend on what apps you're using, but I suspect throwing lots of money at RAM on an older machine hits severely diminishing returns once you get beyond 2GB. Going all the way to 4GB would probably be a bit of a waste of money.

However, RAM isn't particularly expensive, and it's not like having more than you can use is a *bad* thing.

---

### Post by boldford on 2011-04-28
For what it's likely to cost you now, rather than later, you might as well upgrade and max out. Your type of RAM will only get more expensive.

---

### Post by speedwell68 on 2011-04-28
> **boldford said:**
> For what it's likely to cost you now, rather than later, you might as well upgrade and max out. Your type of RAM will only get more expensive.

^^^This and just run the PAE kernel.

---

### Post by tgm4883 on 2011-04-28
> **speedwell68 said:**
> ^^^This and just run the PAE kernel.

Nah 64-bit if he has the Pentium D in there

---

### Post by andrewabc on 2011-04-28
I assume DDR2 ram?
You could probably find some used 1gb stuff cheap. I got 2x512mb ddr2 I'll probably never use.

Assuming computer is just using onboard graphics and slow HDD, I wouldn't spend more than $50 on the 3x1gb ram sticks you need to max it out.

---

### Post by Old_Grey_Wolf on 2011-04-28
I have a few older computers. The cost of upgrading RAM can be ridiculous when the RAM chips become obsolete; therefore, if you think you need it, do it now.

I have monitored my computers, they normally use around 300MB of RAM for processes; however; they use another 600MB for cache and buffers. It varies depending on the applications I am running. When I do something like upgrading/installing patches, it can get to 500MB for processes plus another 1.5GB for cache and buffers, or about 2GB total.

The use of cache and buffers improves the performance of the OS. The OS will run just fine without very much RAM to use for cache and buffers; however, the performance improves when you have more.

When I run a host OS and a couple of Virtual Machines, I cam max out 4GB of RAM just for the processes. Without something left over for cache and buffers, they are very slow loading applications or transferring data.

If the RAM is within your price range you can upgrade it now and save some money in the future.

Three of my machines are 10 years old or older. :)

---

### Post by handy on 2011-04-28
My iMac is a 2007 model, it came with 1GB of RAM. I decided recently that I should upgrade the RAM now, before it becomes redundant & expensive to buy.

The Oz dollar has been very strong lately, which helped the timing of my purchase.

I did some research, & found that the 4GB limit on this (& some other Apple models) machine, is due to Apple's incorrect understanding of what their hardware could do:

[http://www.maconsteroids.com/blog/imac-2007-2008-6gb-ram-upgrade/](http://www.maconsteroids.com/blog/imac-2007-2008-6gb-ram-upgrade/)

The appropriate controller chips on the motherboard can handle 6GB with no problems at all.

So I put 6GB in it & it has been as reliable as can be.

It is too much RAM I know. 

Who knows what the future may bring?

---

### Post by Artemis3 on 2011-04-29
You should upgrade the memory of this machine in pairs. It was a bad idea to put a single 1g stick with 3 256ones.

The max upgrade for this machine is 4 1g DDR2 667 dimms. You should go with that if you can, else 2 1g sticks in slot 1 and 3. If you plan to keep the older memory, and they are the same speed (667), you could leave a pair in slots 2 and 4 for a total of 2.5g or ram.

Another worth upgrade is to buy a SSD, even a small one for the / partition can make a big difference (remember to place both swap, /home and /var in your mechanical drive, and /tmp /var/tmp in tmpfs (ramdisk) :))

1g DDR2 667 dimms can still be purchased at good price, you should get the 2 pairs now. Consider an intel SSD, like the 40g model; you should have 1 free sata port for it (unless you have 2 HDs).

---

### Post by c2006 on 2011-04-29
If you're not planning on getting a new machine any time soon, I'd do it now. DDR2 isn't really used for new systems anymore, but there are for the time being still enough systems to justify most places having stock. It's gone up a little, but still cheap enough that it's best to buy in bulk.

I recently updated my own Core 2 Quad system to 8GB of memory (it's only 3 or 4 years old although some components are a little older). NOW is the time to upgrade the memory if you have a DDR2 system you plan on sticking with for a while - it'll only get more expensive from here on.

Probably going to make my final transition to Linux full-time over the next 6 months (ditching Windows completely). When I'm ready for the final jump (which I'm probably going to do in line with the jump to 11.10 later this year to make things simple), I'll probably switch out my main (320GB) hard drive for something like a 1TB drive (and keep the old one with windows still on it *just in case*).

---

### Post by Dragonbite on 2011-04-29
If you want to toss it, I'll gladly take it and max out the RAM!  My home desktop is a P4 w/2.5 GB of Ram and it runs things just fine and outside of my Chrome OS notebook from the Pilot Program, my machines are around that same vintage or older (P3, P4 and PMs, no *n*-cores yet).

I find my bandwidth a bigger bottleneck than the machine's capabilities (except when I had Windows 7 on it.. that was not so good).

My work computer is a dual-core but I put up the specs and somebody told me it can handle 64 bit.  It is probably not too far from 4-5 years old at this point (Lenovo T61).

I would Max it out.  Maybe even look at upgrading the video card to make effects run smoothly.

---

### Post by scouser73 on 2011-04-29
Do it, that's my two pence worth of advice.

---

