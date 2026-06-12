---
title: "New Toy Review: Dell Mini 9 Ubuntu"
date: 2009-02-16
forum: The Cafe
---

### Post by jdong on 2009-02-16
Well, I got bored last week and found myself with some "excess cash" and grabbed a refurbished Dell Mini 9. I figured I might do a one-week-later review of it for the curious.

**DISCLAIMER**: Some of you may know I've been pretty cold towards the netbook market and am a fairly outspoken critic of them, so don't take the criticism here too seriously!

I will try to assign a summarizing numerical rating to each category.


** Specs **

Just a regular Mini 9 with 8GB SSD, 512MB RAM, and 1.3MP webcam, Ubuntu Linux. (I do a bit of videoconferencing and thought I'd find that feature useful). Final price with shipping and tax was close to $250USD, which is a reasonable deal for an internet appliance. Shipped with the newest A04 BIOS.

** Default OS / Modifications: 8/10 **

The standard OS is an Ubuntu lpia customization based off Hardy. Dell maintains their own unique repository with packages for this distribution and updates seem to propagate down in a timely manner. Note that the OS does include a fully legal (paid fluendo) video playback stack for common formats and has Flash installed, so it's fairly ready to go out of the box. I disliked that Firefox came with a naggy Yahoo toolbar by default.

The only modification I made to the OS was for security -- I reimaged the default system onto a LUKS+LVM partitioning scheme for full disk encryption, and furthermore added a helper shellscript in my home directory to pull in more sensitive data on tmpfs on demand (i.e. my GPG keyring and more important SSH keys). I turned off the Maximus desktop and ran regular GNOME/Metacity.

Overall the default OS works great and gives a great impression of Ubuntu out of the box. The only complaints I have are: (1) The system shipped with over 200 pending updates that took nearly an hour to patch. It would've been better if Dell could've periodically refreshed the images they used on these systems so step #1 wouldn't be applying an hour's worth of updates! (2) There is some glitchiness, like the audio by default seemed to go to both the speakers and headphones until I fiddled around with the volume mixer a bit, and right now the Battery Status Fn key also triggers the wifi-airport selector thing. Minor nitpicks, I'll give an 8/10. Impressively polished Ubuntu configuration, well done.


**Performance: 5/10**:

Oh I can hear you guys heckling me already: ITS A NETBOOK NOT A 16-CORE WORKSTATION. Yes, I know, and I evaluated performance in terms of what I'd expect from a netbook:


First off, I give it mad props for bootup speed -- the Ubuntu splash just ZIPs to fully done; 15s to GDM by conservative estimates. This is very very well done. Shutdown is equally impressively fast. In addition, looking at the boot system it's just a stripped down set of services that are still being started by the regular sysvinit system; no dirty shellscript hack *looks at Eee Xandros*. The magic sauce seems to be a "triggerlateboot" type of shellscript launched after the user logs in, i.e. all dependencies up to GDM are booted then the boot waits until after the user logs in. Smart idea to cut down on waiting time!

Now the bad news: Desktop/UI performance is not what I'd consider a "smooth flawless" experience and that's where this thing loses points. Firefox redraw is very noticeably laggy; resizing/zooming is like a slideshow. Playing music in Pandora pushes the system to 100% CPU usage and you can feel everything crawling, and a flash video is even more downhill from that. At best I can label this as **usable, slightly above bearable**. Not, say, the liquid-smooth experience one gets from an iPhone's web browser and UI despite having a significantly less powerful processor and graphics chip, and 1/4 the RAM.

**Battery Life: 7/10**

I did 3 drain-charge cycles before beginning to evaluate it to make sure that the discharge curve is as steady-state as possible, and used a combination of some scripts and GNOME-Power-Manager to do some testing. Typical usage with wifi can expect to turn in 4h30m total runtime, heavier typical usage will get you 4h00m or so, and really really really conservative usage might get you 4:45.

Here's the bad news: Playing videos will drop that estimate by around 1/3, turning on Compiz will shave almost an hour off, playing audio will also take a good 30 minutes off, though notably using the CPU heavily doesn't affect things much at all.

Now, that is not terribly surprising, considering a more or less stock 945GM mobo is being used with a highly-efficient Atom CPU. The N280 Atoms are supposed to address this issue with a more Atom-tuned mobo which should make the GPU draw less power than the CPU but for now, this is the prime weakness of these things.

**Portability/Mobility: 8/10**

Really lightweight and effortless one-hand carry, fits well even on tiny lecture hall cramped desks. Not much more I can ask for. The points I took off are for: (1) IMO it's still inexcusably thick for something like this, and (2) The suspend-and-resume action isn't as reliable or snappy as, say, my OS X Macbook. At least on two occasions within the week I've owned it, the system did not enter suspend correctly when I closed the lid and packed it, so I found myself using 30 more minutes of battery than I should have. In addition, resume takes about 2.5 seconds from opening the lid to a screen unlock prompt. On OS X this is INSTANTANEOUS, before I can even get the lid up the login dialog is waiting for me. Fast wakeup is very important to me on the go, and this device simply doesn't offer it.

Other thing I should note is that this thing is entirely passively cooled -- no fear of the fans suddenly leaping into action in a quiet library, having to look up to meet a room of angry glares.

**Bottom Line: Value: 10/10, Cost-Blind Usefulness: 6/10**

So what is the bottom line? Well I am going to look at it two ways:

First off, in terms of bang for the buck, this thing is **fantastic**. Despite my harsh comments I still feel for $250 this is a wonderful device worth every penny.

Now, for a slightly different perspective: For myself and many of the people I know, money isn't the sole driving factor in these things. For the past 5 years I've been looking for the ideal on-the-go system with great portability, same feature parity (processing power/capability, keyboard usability, screen size) as a traditional laptop but with an extremely long forgiving battery life. This Mini 9 doesn't quite cut it for the limitations above. But don't worry -- I still haven't found a device that meets my needs. The closest I've come are the Macbook Air, New Macbook Pro 17" (because of its amazing advertised battery life), and Thinkpad X61s. I really don't mind anything in the $0 to $3500USD price range as long as it well exceeds all of my expectations.


What am I going to do with this Mini 9? Well I am going to carry it in conjunction with my Macbook. I like using the Mini 9 for average e-mail checking, IRC, and light web surfing tasks, but when I need to hammer out a paper or some code I'd like a full keyboard. It's a plus that this thing's weight is completely negligible, and in a crowded lecture hall I don't need to pull out a behemoth hunk of metal and obnoxiously set it down on a desk 1/4 the size of the computer.

---

### Post by jpeddicord on 2009-02-16
> **jdong said:**
> Other thing I should note is that this thing is entirely passively cooled -- no fear of the fans suddenly leaping into action in a quiet library, having to look up to meet a room of angry glares

Is your fan really *that* loud? I don't think I've ever heard of a complaint that my laptop's fans were too loud for a library. The idle shuffling of papers I think would be louder. ;)

I've been thinking about getting a Mini 9 (later this year, so there might be a new model by then) and this definitely helps. Nice review.

---

### Post by jdong on 2009-02-16
> **jacobmp92 said:**
> Is your fan really *that* loud? I don't think I've ever heard of a complaint that my laptop's fans were too loud for a library. The idle shuffling of papers I think would be louder. ;)

I've been thinking about getting a Mini 9 (later this year, so there might be a new model by then) and this definitely helps. Nice review.

You gotta remember how heavily I tend to use my computer -- my Korean buds have joked that they want to use one of those Starcraft actions-per-second counter thingies on my computing sessions!

---

### Post by zmjjmz on 2009-02-16
I haven't had any of those performance issues you've listed :/

---

### Post by earthpigg on 2009-02-16
> **zmjjmz said:**
> I haven't had any of those performance issues you've listed :/

ditto.

---

### Post by CrazyDesi on 2009-02-16
I'v got a Mini 12 and it runs things pretty smoothly.  There is some issues with flash, but for the most part, I use it as my main computer almost.

---

### Post by jespdj on 2009-02-17
Dell finally started selling the Mini 9 and 12 here in the Netherlands... I've been waiting for that since October. I have a Mini 9 on order (black, 1 GB RAM, 16 GB SSD). Unfortunately they only sell the Windows XP version here. :( I intend to put Ubuntu 8.10 on it, as far as I know it runs well and the only thing that might be necessary is a simple fix to make the sound work.

Have a look at [http://mydellmini.com](http://mydellmini.com)

It's very easy and cheap to upgrade the RAM to 2 GB, which I intend to do. You can also buy a third-party SSD for the Dell Mini. RunCore sells 16, 32 and 64 GB SSDs for the Dell Mini 9 which are supposed to be a lot faster than the SSD that you get from Dell - it might be worth it to speed up the Mini 9.

---

### Post by jdong on 2009-02-17
Most of my speed issues on this thing are CPU and GPU bound, not RAM. I mean, things like scrolling through YouTube videos is simply painful. It's no big deal for your average day-to-day tasks, but for someone like me who otherwise uses 2.8GHz core 2 duos and 3.4GHz Xeons, the speed difference is painfully noticeable that this ain't a powerhouse ;-)

---

