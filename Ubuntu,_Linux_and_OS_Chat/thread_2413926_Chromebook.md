---
title: "Chromebook"
date: 2019-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by mcyber4 on 2019-03-04
Hi, anyone has a Chromebook? I'm thinking about getting one for security reasons. What's holding me back are specs and prices. Newer cb should run Linux apps like X-plane, gcc, Eclipse, java etc.? They usually only have like 32gb hd which wouldn't be enough for xp. Where would X-Plane etc. be installed, in cloud? Thanks

---

### Post by coffeecat on 2019-03-04
The Security sub-forum is for questions about security in Ubuntu and the official Ubuntu flavours. *Thread moved to **Ubuntu, Linux & OS Chat**.*

I've restored the default font properties in your post. Mid to light grey is difficult to read. Please use default font properties unless you wish to highlight a portion of your post.

---

### Post by kc1di on 2019-03-04
[Here is]("https://tutorials.ubuntu.com/tutorial/install-ubuntu-on-chromebook#0") a good little tutorial on converting the chromebook to ubuntu/xubuntu. 
Remember the chromebooks were designed as an on line machine only and most everything was to be done in the cloud. thus very small hard drives were needed. 
you can put a larger SSD in them but that will void any warrenty on them.  But know people that have done that and it worked well for them.  But you may be able to find another machine just as cheap with more HD space also. Good luck in your search.  As far as security goes I would not bet on it being more secure doing everything online.

---

### Post by makitso on 2019-03-04
Personally, I have not had much luck with chromebooks.  

My latest was anattempt to replace my wife&#8217;s aging Dell 15 XPS with one of the new Acer 15&#8217; models. She hated it.  First, it was slower than her Dell,then there was no delete key, and finally the screen was not very bright.

---

### Post by mcyber4 on 2019-03-04
> **kc1di said:**
>  As far as security goes I would not bet on it being more secure doing everything online.

After being hit by a UEFI Rootkit, that's exactly why I'm considering a CB.

@makitso so it downloads all from cloud? Does it take long to load? What about installing large linux apps like x-plane etc.?
Thanks

---

### Post by kc1di on 2019-03-04
It all depends on your Internet connections I don't know anything about x-plane or if it would run on  a CB. 
But most of your work is stored on line and not on the machine.  Only what is needed to connect and run the internet connection is actually on the machine. 
[This is a good tutorial]("https://www.pcworld.com/article/3168062/how-to-use-a-chromebook-10-must-know-tips-tricks-and-tools-for-beginners.html") on the chromebooks.

---

### Post by jdeca57 on 2019-03-04
I've owned a chromebook for some years (still do) and I still think ir was a good choice if you use it in combination with a VPN solution and at the time I bought it there was no direct Linux support. But in my uninformed opinion the Linux side is not a part of the chrome experience: that is simply a browser that offers a great experience in the browser environment.

---

### Post by TheFu on 2019-03-05
I've used chromebooks daily since 2013, but not as "chromebooks."   For me, chromeOS was just not a sufficient OS.  I violated the warranty, opened the machine, removed the write-protect device, swapped out the 16G SSD for a 60-128G SSD, put in a different BIOS that could boot any OS, and loaded Ubuntu. I was careful to pick 
* only the fastest, cheap, chromebooks - those with fast CPUs.  in 2013, that was the Celeron 2950U CPU (1490 passmarks). Most current Chromebooks sold in 2019 are still slower than that amazing CPU.  It was in the Acer C720.  I replaced that in 2015 with an i5-5015U (3000 passmarks), which was about 2x faster ... and about the same as my 15inch Dell with a Core i5 with 3580 passmarks.
* Not all chromebooks come with SSDs. Only the variants with SSDs are likely to allow swapping out the tiny SSD storage for more.
* I missed the Delete key for years.  More importantly, chromebook keyboards are cheap and the primary reason why I've needed a new one. For me, they last about 2 yrs before 6+ keys stop working. Because they use plastic rivets to hold the keyboards in place, replacement is major surgery and usually $120+ in costs.
Just last week, I replace my wonderful Toshiba CB2 - an ultrabook at chromebook prices - for a used, crazy powerful, laptop from ebay for $305.  The new laptop has a delete key, 8G of RAM, a Core i5 with 7700 passmarks, 1TB HDD, 3.6 lbs, 1080p screen and the battery seems to last over 8 hrs per charge.  Did I mention that it has a delete key?!!!  The ebay purchase was amazing. The only flaw is a tiny chip in the plastic which was clearly pointed out by the seller. When it arrived, I could only feel the chip, couldn't see it.  Everything else about it seems new.  It has F11 and F12 too, which chromebooks don't have ... and pgup/dn/home/end keys.

If I want to have the feel of chromeOS, there are ChromiumOS based solutions. These are useful to re-purpose older laptops, as ChromiumOS is light just like ChromeOS. They do the same things.

But you are primarily interested in security.  For that as the primary goal, then I don't think there is any more secure, networked, OS, on the market today. It is the combination of the Chromebook hardware which is tightly coupled to the ChromeOS software.  They follow the BSD upgrade technique of having 2 partitions for the OS stuff A and B. The running OS is mounted read-only. The other partitions aren't generally mounted.
Google pushes out patches whenever they feel like it. There is no way to stop that.  It broke my Ubuntu subsystem back when I was using ChromeOS with a crouton chroot setup multiple times.  Twice when I was travelling overseas.  This was 50% of the reason why I decided to wipe ChromeOS.
The other reason I wiped ChromeOS was because I needed NFS and ChromeOS doesn't support kernel modules that google doesn't provide.

Chromebooks will always be cheap, lower-end systems with limited RAM.  The RAM cannot be upgraded and only the Pixel line of Chromebooks for $1000+ come with sufficient RAM, IMHO.   I wouldn't expect X-plane to run well on any lessor chromebook, if at all.  I doubt a full Linux environment will come with the planned Linux support. It will be approved apps only and probably only light variants. Google will want to manage the experience.

Oh, and google's support for anything software related in their ChromeOS forums sucks.  Every question I asked there was not answered correctly, then closed, and a forum moderator would choose the "best answer" which wasn't actually an answer to the question.  In the end, all their answers were to "powerwash" the system or reload the OS after building a USB boot, using either ChromeOS or Windows.  My questions for how to accomplish that from Linux were closed.  BTW, Linux building of the USB boot drive **is** a supported option, but the arrogance of their support people would close anything with "Linux" in the question at that time.

Got burned with a Nexus cell phone they dropped support on well before end-of-life. I will never give google another penny, if I can help it.

In short, ChromeOS is very secure, assuming you don't care about privacy. Security and privacy are 2 different things in the google world.
Don't buy a Chromebook if you expect HW to last or if your primary goal is to use it for non-ChromeOS tasks.
If you do get a chromebook, I'd stay away from ARM-based CPUs if you need to run Linux general applications. Certain software has not and never will be supported on ARM.  You probably won't notice until that 1 software isn't available, 6 months after the purchase. This aspect was something I didn't really consider, but I got lucky.

Flatpaks and snaps should make running Linux software easier on chromeOS, but those eat up CPU, RAM, and disk storage - the 3 things that are strictly limited on almost all chromebooks under $500.

Anyway, hopefully this provides some other things to consider.  I really do miss the sub-3 lbs of the beautiful i3 Chromebook, but I miss having a working keyboard more.

---

