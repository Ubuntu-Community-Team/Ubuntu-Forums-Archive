---
title: "ReadyBoost in Vista? I hear it's good."
date: 2007-03-19
forum: Windows
---

### Post by katabatic on 2007-03-19
Friend says it speeds up opening applications a lot. He said it makes it even faster than Ubuntu. Opinions? Why doesn't Ubuntu have it?

---

### Post by zorkerz on 2007-03-19
Please explain what is readyboost?

---

### Post by insane_alien on 2007-03-19
it varies from computer to computer. BTW has he tried ubuntu on that computer? or at least one with the same hardware. the ready boost is essentially just swap space on a different drive. the only way it can reduce loading times is by eliminating the need for the harddrive to read/write/seek to the swap space.  if you have enough RAM to get rid of the swap space then it will run exactly the same.

---

### Post by Trebuchet on 2007-03-19
Since it appears ReadyBoost is software rather than hardware dependent (not including the flash memory it uses) I'm hoping the Linux equivalent will soon appear. While it's really nothing more than an augmented swap file, flash memory is much faster than any hard drive. For people who don't want to (or can't) add additional RAM, it seems like a clever idea.

Supposedly the new hybrid hard drives recently introduced will vastly increase Vista's speed as well. From early reviews of the technology, I looks like MS is depending on hybrid drives to really give Vista a big performance advantage over XP.

---

### Post by katabatic on 2007-03-19
Yes, he had Ubuntu installed on the same laptop. Laptop has 1 gig ram.

It looks like ReadyBoost is similar to putting swap on Flash, but not quite the same. They have optimized it specifically for this purpose. I guess it mainly caches and prefetches commonly used programs, so they load faster.

I'm surprised Linux hasn't done it first, cause it does work from what I'm hearing. 
It's true that adding more ram would be better, but having the option to just plug in a USB flash drive to speed it up does sound good.

---

### Post by ddaedalus on 2007-03-19
1. Flash is *NOT* faster than a HD. In random reads maybe, but in sequantial access, many HDs do outperform most of the flash drives.

2. Linux already had this feature. Create an additional swapfile/-partition on the flashdrive and assign a priority to it. The only thing that Linux doesn't have, thank god, is a fancy name.

---

### Post by katabatic on 2007-03-19
> **ddaedalus said:**
> 1. Flash is *NOT* faster than a HD. In random reads maybe, but in sequantial access, many HDs do outperform most of the flash drives.


Newer flash is getting fast, and it is indeed faster in random reads. Isn't combining the advantage of the HD + the advantage of Flash = Faster?


> **ddaedalus said:**
> 
2. Linux already had this feature. Create an additional swapfile/-partition on the flashdrive and assign a priority to it. The only thing that Linux doesn't have, thank god, is a fancy name.

Two things here:
1. How are you so sure doing that will be just as good as ReadyBoost? Have you compared them?

2. If it IS just as good, it sure isn't easy to do for 99% of Ubuntu users. It is not included and not done automatically like in Vista.

Having a name is a good thing. A lot of people now know about this cool feature in Vista, ReadyBoost. It's likely that even if it was included in Ubuntu, a lot of people wouldn't know about it. The Joe Average usually doesn't go around looking for settings and features to mess with.

---

### Post by marx2k on 2007-03-19
> **katabatic said:**
> Newer flash is getting fast, and it is indeed faster in random reads. Isn't combining the advantage of the HD + the advantage of Flash = Faster?




Two things here:
1. How are you so sure doing that will be just as good as ReadyBoost? Have you compared them?

2. If it IS just as good, it sure isn't easy to do for 99% of Ubuntu users. It is not included and not done automatically like in Vista.

Having a name is a good thing. A lot of people now know about this cool feature in Vista, ReadyBoost. It's likely that even if it was included in Ubuntu, a lot of people wouldn't know about it. The Joe Average usually doesn't go around looking for settings and features to mess with.

1. It's doing the same thing, why wouldn't it be just as fast?
2. This sounds easily accomplished by a simple bash/puthon script.  You can even give the  script a cool name :D

The thing is, even with 512M of RAM and 1G of HD swap space, how often does that 1G of swap space get used up? On my comp, I have to be doing a LOT to even start using the swap space. Most of the time it's used up for larger programs (like VirtualBox with XP running on it) that are just sitting idle.

Also, isn't there something about USB drives faulting after so many read/writes?

---

### Post by airtonix on 2007-03-19
yeah youll end p witha  dead usb flash drive before long...

wonder if some big stalls foresaw this and made sure the "affordable" usb drive stand was right next to the vista showcase....

hoo hum.

---

### Post by katabatic on 2007-03-19
> **marx2k said:**
> 1. It's doing the same thing, why wouldn't it be just as fast?
2. This sounds easily accomplished by a simple bash/puthon script.  You can even give the  script a cool name :D

The thing is, even with 512M of RAM and 1G of HD swap space, how often does that 1G of swap space get used up? On my comp, I have to be doing a LOT to even start using the swap space. Most of the time it's used up for larger programs (like VirtualBox with XP running on it) that are just sitting idle.

Also, isn't there something about USB drives faulting after so many read/writes?

How are you so sure they do the same thing? Have you compared and tested them extensively? Yes or no. I haven't, that's why I'm posting to ask.

> Q. Won't this wear out the flash drive?

A: Absolutely not. ReadyBoost is smart about how and when it writes to the flash device. Research shows that the lifespan of flash devices used for ReadyBoost will have a usable life of ten years or more.  
From Google search. So, is putting swap on Flash in Linux "smart about how and when it writes to the flash device?" I'm assuming no. I'm also assuming it isn't optimized for using this to speed up the OS in this way.

Why all this doubt and bashing? You're comparing it to using swap on your computer, but this isn't the same! How can you compare it, then?

From what I read, this DOES work. Now, adding lots of ram is surely a better idea, but if you already own a USB flash drive, why not plug it in to speed the OS up? Nothing to lose if it will last 10 years.

My friend was honestly surprised at the performance increase, so this raised my interest. I feel like Linux is trailing behind.

---

### Post by rsambuca on 2007-03-19
katabatic,

How much readyboost will actually increase your Vista performance depends a lot on what the system specs are to begin with.  I have 1Gig Ram, and when I use a 1Gig flash drive as readyboost with Vista, there is a performance gain to be sure.  Not enough to worry about in my case, though.

Something to keep in mind is that linux in general, including ubuntu, are MUCH better at utilizing system resources than XP, and MUCH MUCH better than Vista.  Doing the same tasks in ubuntu takes quite a lot less system resources than Vista, and in fact, I don't know the last time my ubuntu set-up has even touched my swap.  Therefore, most people don't have a need for putting linux swap files on a USB stick as the system RAM is way faster and often quite ample for most peoples' needs nowadays.

---

### Post by Kateikyoushi on 2007-03-20
I really want a thumbdrive to be sticking out of my notebook...

---

### Post by 3rdalbum on 2007-03-20
I have 1.2 gigs of RAM.

Ubuntu's Used Swap (with Firefox, GAIM and Gizmo open): 0 bytes.

Windows XP's Pagefile (with Nero open): 422 megabytes.

If Ubuntu's not touching my swap, and I've got 900 megabytes of RAM available for cache, why on earth would I need Readyboost?

---

### Post by Trebuchet on 2007-03-20
> **3rdalbum said:**
> I have 1.2 gigs of RAM.

Ubuntu's Used Swap (with Firefox, GAIM and Gizmo open): 0 bytes.

Windows XP's Pagefile (with Nero open): 422 megabytes.

If Ubuntu's not touching my swap, and I've got 900 megabytes of RAM available for cache, why on earth would I need Readyboost?Hmm. Might that not be better blamed on Nero? Seems to me if you want to compare swap file usage you should at least be using cross-platform apps. Not sure XP isn't just as bad as you're suggesting, but unless you're comparing apples to apples how can we be sure?

Why not try that same OS comparison with OpenOffice 2, Firefox 2, and Thunderbird on both platforms with precisely the same document files and web pages open? Then we can actually make a valid comparison.

---

### Post by katabatic on 2007-03-20
Like I said, friend said Vista + ReadyBoost was faster than Ubuntu when opening programs, such as Firefox.

---

### Post by igknighted on 2007-03-20
> **katabatic said:**
> How are you so sure they do the same thing? Have you compared and tested them extensively? Yes or no. I haven't, that's why I'm posting to ask.

 
From Google search. So, is putting swap on Flash in Linux "smart about how and when it writes to the flash device?" I'm assuming no. I'm also assuming it isn't optimized for using this to speed up the OS in this way.

Why all this doubt and bashing? You're comparing it to using swap on your computer, but this isn't the same! How can you compare it, then?

From what I read, this DOES work. Now, adding lots of ram is surely a better idea, but if you already own a USB flash drive, why not plug it in to speed the OS up? Nothing to lose if it will last 10 years.

My friend was honestly surprised at the performance increase, so this raised my interest. I feel like Linux is trailing behind.

I have tried "readyboost", or attempted to at least.  I used every USB key I could lay my hands on, and none of them were good enough for readyboost.  You need very nice high speed USB keys.  A one GB key that is fast enough will cost me almost the same as 1 GB of ram... and the ram will lead to much better performance... so why?

---

### Post by marx2k on 2007-03-20
> **katabatic said:**
> How are you so sure they do the same thing? Have you compared and tested them extensively? Yes or no. I haven't, that's why I'm posting to ask.


Well, with both technologies, you're offloading SWAP space onto a flash drive. I mean, why would it be different in either OS? That's like asking if harddrive access is faster under a certain OS.
 
> **katabatic said:**
> From Google search. So, is putting swap on Flash in Linux "smart about how and when it writes to the flash device?" I'm assuming no. I'm also assuming it isn't optimized for using this to speed up the OS in this way.

Why all this doubt and bashing? You're comparing it to using swap on your computer, but this isn't the same! How can you compare it, then?

Unless I'm missing something, this is pretty much the same idea. Just a lot slower. 

> **katabatic said:**
> From what I read, this DOES work. Now, adding lots of ram is surely a better idea, but if you already own a USB flash drive, why not plug it in to speed the OS up? Nothing to lose if it will last 10 years.

My friend was honestly surprised at the performance increase, so this raised my interest. I feel like Linux is trailing behind.

Using a [relatively] slow access device (especially slow when compared to actual RAM) should not speed the system up. The USB Bus bottleneck will make sure of that.

It's not that I'm bashing the idea. It's just that the idea is currently handled with swap.

---

### Post by Trebuchet on 2007-03-20
> **marx2k said:**
> Well, with both technologies, you're offloading SWAP space onto a flash drive. I mean, why would it be different in either OS? That's like asking if harddrive access is faster under a certain OS.
 
Unless I'm missing something, this is pretty much the same idea. Just a lot slower. 

Using a [relatively] slow access device (especially slow when compared to actual RAM) should not speed the system up. The USB Bus bottleneck will make sure of that.

It's not that I'm bashing the idea. It's just that the idea is currently handled with swap.Flash memory, especially the highspeed stuff rated for ReadyBoost, is faster than most hard drives.

While adding RAM might in theory be just as good or better, that ignores the fact that many people are incapable of adding additional RAM either because they don't know how or because their system will not support more (especially laptops). While it's usually going to use USB-format flash memory, I understand it can also use compact flash cards such as SD or CF.

---

### Post by Trebuchet on 2007-03-20
> **igknighted said:**
> I have tried "readyboost", or attempted to at least.  I used every USB key I could lay my hands on, and none of them were good enough for readyboost.  You need very nice high speed USB keys.  A one GB key that is fast enough will cost me almost the same as 1 GB of ram... and the ram will lead to much better performance... so why?NewEgg has some ReadyBoost-rated Kingston USB drives for about $25. You can get a gig of RAM for that?

---

### Post by Lord Illidan on 2007-03-20
> **airtonix said:**
> yeah youll end p witha  dead usb flash drive before long...

wonder if some big stalls foresaw this and made sure the "affordable" usb drive stand was right next to the vista showcase....

hoo hum.

IMHO, this thread is full of FUD...and it's not coming from the Windows guys this time.

Readyboost has been tested, and it has been found to work.
Also, it does not kill your usb flash drive...I believe it chooses areas of the disk which haven't been written/read a lot of times...

[http://blogs.chron.com/techblog/archives/2006/12/obsession_indulged_more_on_vistas_readyboost.html](http://blogs.chron.com/techblog/archives/2006/12/obsession_indulged_more_on_vistas_readyboost.html)

let's not bash something just because it was made by Microsoft. If the same thing had been invented by the linux community, would we be saying the same things?

---

### Post by saulgoode on 2007-03-20
I think there might be some useful functionality provided by ReadyBoost but its benefits would be somewhat diluted in the Linux environment for two main reasons.

The first is that ReadyBoost's main purpose was to cut down on Vista's reboot times by storing the needed files in a thumbdrive's non-volatile memory for faster access. Rebooting is not so prevalent a practice for Linux user's and therefore not as significant. Laptop users tend to reboot more frequently and RB-type functionality could prove beneficial to them (although, as has been mentioned, having a thumbdrive sticking out of a laptop is not ideal from a mechanical standpoint).

The second reason is that the Linux kernel already provides a way to decrease load times of applications by decreasing the value stored in /proc/sys/vm/swappiness -- the main difference being that the thumbnail would probably retain "swapped" applications during a reboot (I am guessing here). The Linux method should provide better response when switching between applications (system memory is still faster than thumbdrives) and the user retains flexibility in tuning his system suitably to his usage (increasing the value of swappiness provides for more cache space which is beneficial for activities such as editing large files or compiling code). 

I suspect that the kernel's ability to fine tune how swapping is performed will continue to improve. I am not sure that changes would be made in the same direction as ReadyBoost (which is a bit of a kludge) but a way to background swapping of apps to slow write/fast read, non-volatile memory might be in the cards and would free up system memory for I/O caching.

---

### Post by Trebuchet on 2007-03-20
I think you're mixing up ReadyBoost with SuperFetch, another new memory toy in Vista. From the Vista website:

[I]SuperFetch

Windows SuperFetch enables programs and files to load much faster than they would on Windows XP–based PCs.

When you're not actively using your computer, background tasks—including automatic backup programs and antivirus scans—run when they will least disturb you. These background tasks can take up system memory space that your programs had been using. On Windows XP–based PCs, this can slow progress to a crawl when you attempt to resume work.

SuperFetch monitors which applications you use the most and preloads these into your system memory so they'll be ready when you need them. Windows Vista also runs background programs, like disk defragmenting and Windows Defender, at low priority so that they can do their job but your work always comes first.[/I]

So Vista has ReadyBoost, SuperFetch, and is specifically designed to fully use the new hybrid hard drives. It'll be interesting to see what kind of overall performance boost this combination gives Windows over XP and/or Linux. I suspect that along with more optimized hardware drivers it's going to speed things up quite a bit from typical XP capable PCs.

Some people seem inclined to write off Vista already. I think it's too early for that until we've at least seen what their full lineup looks like. Aero may be a yawner for people who've seen Beryl, but will it still be a yawner for people who haven't and if it also runs several times faster than it's early incarnations?

---

### Post by saulgoode on 2007-03-20
> **Trebuchet said:**
> I think you're mixing up ReadyBoost with SuperFetch, another new memory toy in Vista.

Thanks. Would you say, then, that the entire discussion thus far (and particularly load times of applications) has been about SuperFetch?

And do you know whether a reboot and/or removal of the thumbdrive would result in SuperFetch have to "start over" populating the thumbdrive with frequently-used apps?

---

### Post by Trebuchet on 2007-03-20
ReadyBoost is the new Vista tech that uses USB drives. As I understand it, SuperFetch will be using a different type of flash drive, possibly installed in an IDE channel (at least the photo I saw of one was a small card and not a USB device and what was identified as using an IDE connection). It's an actual physical device with supporting software built into the OS. They're clearly related concepts, but both do different things. I'm not sure they've even been released yet.

The thing I'm most interested in seeing is the hybrid hard drives. Supposedly these will speed up any system with one installed, but Vista apparently can fully utilize the technology and I've hear rumors of a two- or three-fold performance increase.

---

### Post by igknighted on 2007-03-22
> **Trebuchet said:**
> NewEgg has some ReadyBoost-rated Kingston USB drives for about $25. You can get a gig of RAM for that?

I got 1GB dual channel for $60, and I don't buy the cheapest RAM.  But still... I buy my flash drives locally and they don't have such a stick available in store.  If I'm going to order from newegg, I'm gonna drop the $60 for more RAM.

It's a good idea, and useful for those with older systems that want to use Vista, so I give MS their due... but on newer machines the additional cost for real RAM is so low that the USB key isn't really worth buying a special one for the task.

---

### Post by Trebuchet on 2007-03-22
> **igknighted said:**
> I got 1GB dual channel for $60, and I don't buy the cheapest RAM.  But still... I buy my flash drives locally and they don't have such a stick available in store.  If I'm going to order from newegg, I'm gonna drop the $60 for more RAM.

It's a good idea, and useful for those with older systems that want to use Vista, so I give MS their due... but on newer machines the additional cost for real RAM is so low that the USB key isn't really worth buying a special one for the task.Maybe not. OTOH, on laptops where performance is typically lower than comparably priced desktops (and often don't even have the option of installing additional RAM), using a USB thumb drive to enhance system performance might be useful. Many users already transport documents and even applications on thumb drives, and ReadyBoost does not automatically use the entire drive - the user can set how much space gets used for ReadyBoost and keep the rest available for other uses.

Given that hard drives are the slowest component in modern systems, anything that can reduce that bottleneck is a good thing. This is a reasonably clever idea even if it isn't optimal, and I suspect other OSs will follow suit.

---

### Post by mysticrider92 on 2007-03-22
> **ddaedalus said:**
> 1. Flash is *NOT* faster than a HD. In random reads maybe, but in sequantial access, many HDs do outperform most of the flash drives.

2. Linux already had this feature. Create an additional swapfile/-partition on the flashdrive and assign a priority to it. The only thing that Linux doesn't have, thank god, is a fancy name.

Flash is a lot safer to use than a hard drive becase of the lack of moving parts, and I think it is actually a good bit faster (unless you are comparing it to a 15k rpm SCSI hard drive). I have actually thought about trying #2 some time.

---

### Post by bonzodog on 2007-03-22
Linux already caches and pre-fetches programs to boost loading times. 
This is why, the longer you leave your linux system booted up, the more memory it appears to be using. It caches commonly used programs in the memory by default. It only starts using the HDD swap if you try to cache more stuff than it can take, or use a very big program which requires more physical RAM than you might have.

Also, Ubuntu has had a pre-fetch utility for a long while, which you set-up to deliberately start large programs at first boot, shut them down again, where-upon they are now cached for faster start times later.

This is also why they say that a linux system performs better if not shut down frequently - A lot of linux distros really aren't designed for a high amount of shutdown and start-up.

I currently do not switch off/reboot my system unless I have a kernel change - I just log out to gdm at night.

---

### Post by igknighted on 2007-03-22
> **bonzodog said:**
> Linux already caches and pre-fetches programs to boost loading times. 
This is why, the longer you leave your linux system booted up, the more memory it appears to be using. It caches commonly used programs in the memory by default. It only starts using the HDD swap if you try to cache more stuff than it can take, or use a very big program which requires more physical RAM than you might have.

Also, Ubuntu has had a pre-fetch utility for a long while, which you set-up to deliberately start large programs at first boot, shut them down again, where-upon they are now cached for faster start times later.

This is also why they say that a linux system performs better if not shut down frequently - A lot of linux distros really aren't designed for a high amount of shutdown and start-up.

I currently do not switch off/reboot my system unless I have a kernel change - I just log out to gdm at night.

If you fool around with some config files you can change the priority of the swap space.  Not really a great idea for a 5400 RPM laptop hd... but if you had a fast USB key formatted with swap, you might want to bump up the priority.  Then swapping would occur more often than just as a bailout for when physical ram is used up.

---

### Post by Trebuchet on 2007-03-22
[quote=ddaedalus]12. Linux already had this feature. Create an additional swapfile/-partition on the flashdrive and assign a priority to it. The only thing that Linux doesn't have, thank god, is a fancy name.[/quote]So you're saying this is actually a good feature; and your only objection is Windows giving it a fancy name?

Why is it when Microsoft does things differently than Linux they get criticized; and when they do things the same as Linux they get criticized?

---

### Post by igknighted on 2007-03-22
> **Trebuchet said:**
> So you're saying this is actually a good feature; and your only objection is Windows giving it a fancy name?

Why is it when Microsoft does things differently than Linux they get criticized; and when they do things the same as Linux they get criticized?

I think its because (a) there is a bias on these forums against MS - shocking - and (b) MS adds this feature, which is free in other OS's, and then jacks the price up and limits your rights to use the OS.  Sure its a good feature, and if there weren't so many strings attached and it didn't cost so much it would be a great OS.  I like Vista a lot, and have defended it a lot on these boards.  ReadyBoost is a quality feature... however, its not something that linux doesn't have, so its not worth accepting all those other strings just to have it.  I think thats why there is so much skepticism.  If it was this new awesome thing that linux didn't have, then there might be a different reaction.

---

### Post by Trebuchet on 2007-03-23
> **igknighted said:**
> I think its because (a) there is a bias on these forums against MS - shocking - and (b) MS adds this feature, which is free in other OS's, and then jacks the price up and limits your rights to use the OS.  Sure its a good feature, and if there weren't so many strings attached and it didn't cost so much it would be a great OS.  I like Vista a lot, and have defended it a lot on these boards.  ReadyBoost is a quality feature... however, its not something that linux doesn't have, so its not worth accepting all those other strings just to have it.  I think thats why there is so much skepticism.  If it was this new awesome thing that linux didn't have, then there might be a different reaction.Look, I'm not a big fan of MS, but they're a business. They have a product they want to sell. Mark Shuttleworth didn't make his fortune giving away his goods and services. He didn't make it giving away an OS.

Microsoft's operating systems have always been reasonably priced. Reasonably, at least to those who think it's reasonable to pay for an OS in the first place. Vista costs the same for the home user version (Home Premium) as the home user version of XP did. (Factoring in inflation, in fact it's *cheaper.*) Anyone ever priced a Unix license in 1985? Check it, then get back to me on how Windows is overpriced. The low cost of Windows is one of the things that brought computing to the masses. I know that appalls some geeks because that means computing isn't just for high priests any more, but most of us consider would consider that a vast improvement.

Part of what's slowing Linux's advancement into mainstream computing is this irrational need to constantly set itself against Windows. Linux has plenty of wonderful features, so why not tout those rather than bash MS? As many politicians have found out, negative campaign ads are counterproductive in the long run. Linux will gain more ground when it stops worrying about what Windows is doing and focuses on what Linux is doing. When you primarily worry about what the other guy is doing, you surrender the initiative. That's how wars get lost.

---

### Post by igknighted on 2007-03-23
> **Trebuchet said:**
> Look, I'm not a big fan of MS, but they're a business. They have a product they want to sell. Mark Shuttleworth didn't make his fortune giving away his goods and services. He didn't make it giving away an OS.

Microsoft's operating systems have always been reasonably priced. Reasonably, at least to those who think it's reasonable to pay for an OS in the first place. Vista costs the same for the home user version (Home Premium) as the home user version of XP did. (Factoring in inflation, in fact it's *cheaper.*) Anyone ever priced a Unix license in 1985? Check it, then get back to me on how Windows is overpriced. The low cost of Windows is one of the things that brought computing to the masses. I know that appalls some geeks because that means computing isn't just for high priests any more, but most of us consider would consider that a vast improvement.

Part of what's slowing Linux's advancement into mainstream computing is this irrational need to constantly set itself against Windows. Linux has plenty of wonderful features, so why not tout those rather than bash MS? As many politicians have found out, negative campaign ads are counterproductive in the long run. Linux will gain more ground when it stops worrying about what Windows is doing and focuses on what Linux is doing. When you primarily worry about what the other guy is doing, you surrender the initiative. That's how wars get lost.

You're preaching to the choir... I've made these same points in many threads on Vista here.  In fact I've got PM's filling my inbox because I called out Vista haters throwing jabs in for no reason when new users asked for help dual booting it.  There are many things on Vista that make me want to use it... however, while ReadyBoost is neat, it is not one of them (for the reasons I mentioned in the above post which you quoted).  DX10, on the other hand, is something that perks my interest.  As does MathCad which I need for school, and Autodesk Inventor which I enjoy fooling around with.  I am willing to pay for an OS to do these things, since linux cannot.  I don't have to thanks to MSDNAA, but I would have dropped the money for an OEM vista license if I had to.

---

### Post by Trebuchet on 2007-03-23
Don't get me wrong - I'm in no hurry to upgrade to Vista despite the fact I can get a full retail version of Vista Ultimate for $45. I've been fairly pleased with XP Pro, and the new features of Vista really don't float my boat. My current system would handle Vista Basic (barely) but not the "gee-whiz" features, so what's the point?

I'll get a new system eventually. It'll probably have Vista pre-installed, although it might even be a Mac. Either way, I'm going to continue to learn about and experiment with Linux. Linux is only going to grow.

---

