---
title: "I had a few curiosities regarding Ubuntu and Debian"
date: 2013-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by impinball on 2013-07-31
I almost started this post in the "Recurring Discussions" subforum for its nature, but I was wondering about what the main differences between them are.

I haven't used Debian even a single time, but I have read all over the place that the two distros are extremely similar in several areas, especially in the inner workings of it (albeit not exact in either). I was wondering what the main differences were (beyond just the preference of less commercialization).

---

### Post by craig10x on 2013-08-01
Each new version of ubuntu is based on Debian sid as i believe it is called...the development channel of debian....then ubuntu smooths it all out...it is kind of a rather refined version of debian...
I have worked with direct debian based distros and came to the conclusion that (for me anyway) ubuntu is more my "cup of tea" :)

---

### Post by malspa on 2013-08-01
Ubuntu's quicker and easier to install. It has Unity and Debian doesn't. Ubuntu has the PPA system, comes in handy sometimes. Ubuntu has sudo set up by default; with Debian, it's su.

Debian Stable and Ubuntu LTS are both quite nice for long-term usage, both very stable and trouble-free. But probably nothing is as rock-solid as Debian Stable.

Ubuntu also has has the six-month releases, according to schedule. Debian has nothing like that; each Stable release comes out "when it's ready." Debian's "Sid to Testing to Stable" approach results in an excellent final product.

Debian Stable takes a little more work at first, but once it's all set up, you can just forget about it, it's just gonna keep working fine. It's kinda like this: Ubuntu is more user-friendly at the beginning, but Debian Stable is more user-friendly over the long-term. IMHO, that is.

Both are great. I like having Debian Stable as well as Ubuntu LTS installations here, and have done so for several years now. For me, that's a better deal than choosing one or the other.

---

### Post by MadmanRB on 2013-08-01
Both Debian and Ubuntu are very simular, but different as each one has its own goals and objective.
Though the old joke about Ubuntu being an african word for I cant install debian is debunked as debian is just as easy to install as Ubuntu these days.

---

### Post by Cheesemill on 2013-08-05
> **malspa said:**
> Ubuntu has sudo set up by default; with Debian, it's su.

Debian will install with the exact same sudo setup as Ubuntu if you leave the root password blank in the installer :)

---

### Post by lykwydchykyn on 2013-08-05
Here's a good summary for you:

[http://www.alandmoore.com/blog/2012/05/17/debian-for-ubuntu-people/](http://www.alandmoore.com/blog/2012/05/17/debian-for-ubuntu-people/)

---

### Post by malspa on 2013-08-06
> **Cheesemill said:**
> Debian will install with the exact same sudo setup as Ubuntu if you leave the root password blank in the installer :)

Didn't know that! I knew that there was a way to do it, but I never looked into it. Anyway, in the typical default set-up, in Debian it's su and in Ubuntu it's sudo. That is, if there is such a thing as a "typical default set-up." :)

---

### Post by impinball on 2013-08-20
They both support both versions, though.

---

### Post by mamamia88 on 2013-08-20
Debian has 3 branches stable,testing, and sid.   Packages flow down from sid to eventually form the next stable release.  Basically ubuntu takes the most up to date version of debian,freezes it at a point in time, smoothes out the rough edges, adds some customization to make stuff easier ,like front ends for stuff that doesn't normally have front ends ,as well as adding some stuff like device drivers back that debian removes to keep it purely open source. Basically it's a difference in philoshies.  Debian's goal is to make stuff as technically sound and bug free as possible while using only open source softare. While ubuntu aims to make a system that is easy to use as possible for a newcomer.  Because debian is so technically sound it makes a great base for other distros.

---

### Post by monkeybrain20122 on 2013-08-21
> **Cheesemill said:**
> Debian will install with the exact same sudo setup as Ubuntu if you leave the root password blank in the installer :)

Or add yourself as a soder after installation. I never use su except to add myself.

---

### Post by monkeybrain20122 on 2013-08-21
Debian has 4 versions: stable, testing, unstable and experimental. 

My opinion (which others may disagree) is that Debian is a great distro to build other distros on (like Ubuntu) and for maybe businesses and individuals who are very conservative about upgrading and don't venture out of a few core applications, but IMO it is not great for everyday desktop use. 

Debian stable is certainly "stable" but this is only because it is very old and by the time software gets to stable they are already outdated and the kernel version may not even work with your hardware (Windows 8 laptops?) , testing is by no means latest and greatest as the name may suggest, it is only less old, I laugh when people in Debian forums advise newbies that testing is not as "solid" and needs to be handled with care. It sounds like saying you should always stay home because the street is such a dangerous place. You would like Debian stable if you have that kind of life philosophy  or if you are a business that only uses a few core applications for routine work and never need new features. But it is not for me.

Unstable (sid) is very unstable and a lot of broken dependencies and so on (need to check "Debian weather" before update or you may break your system) and experimental is a complete mess. I triple boot  Debian SId with Ubuntu 13.04 and Fedora 19, Sid is by far the most buggy and most complicated to setup by a huge margin (Fedora, on the other hand is truly bleeding edge. more up to date than Debian experimental yet  has far fewer bugs than sid,--actually I haven't encountered any which is due to Fedora, there are some issues with third party stuffs like google earth but it is google's bug,-- it is as solid as Ubuntu 13.04 but much more up to date, but there is  less software available so have to compile more)

---

### Post by mastablasta on 2013-08-21
> **monkeybrain20122 said:**
> ... testing is by no means latest and greatest as the name may suggest, it is only less old, I laugh when people in Debian forums advise newbies that testing is not as "solid" and needs to be handled with care. It sounds like saying you should always stay home because the street is such a dangerous place. 


i am sure first users of Linux mint debian had a good laugh when their computers stopped working after certain updates. plenty of them didn't know who to fix it without help. so they added a checup of updates before they are let through to users

---

### Post by monkeybrain20122 on 2013-08-21
> **mastablasta said:**
> i am sure first users of Linux mint debian had a good laugh when their computers stopped working after certain updates. plenty of them didn't know who to fix it without help. so they added a checup of updates before they are let through to users

Well I suppose people who can set up Debian would be a bit more knowledgeable than the first users of Mint. :) Anyway, I tried LMDE for two weeks when it came out. I think the bugs were Mint related.I removed it because I didn't see the point. Software was older than Ubuntu's and definitely more ugly (Couldn't stand the Mint menu)

---

### Post by craig10x on 2013-08-21
I ran LMDE for awhile...there was a number of times that i had breakages and it got annoying after a while so i removed it...I ran 13.04 while it was development and had FAR LESS problems on that then i had with LMDE...of the two, i think Ubuntu development (which is now called the unofficial rolling release version of ubuntu...lol) is the better rolling distro of the two...

---

### Post by monkeybrain20122 on 2013-08-21
Well I never use Debian testing, except for two weeks on LMDE (went from stable to Sid with testing only as an upgrade route) but if LMDE bugs are from Debian testing rather than Mint then it means Debian testing is outdated AND unstable, the worst of all worlds. :)  I would hope that whatever bugginess that people experience in LMDE are Mint bugs. :)

---

### Post by rai_shu2 on 2013-08-21
My impression of Debian is that it's like an Ubuntu best-of album (although that does seem a little backward somehow).

---

### Post by malspa on 2013-08-22
For me, Debian Stable is perfect for "everyday desktop use." As long as I'm getting security updates and an updated web browser, I'm good. Older kernels have not been a problem here on any of my computers. But I multi-boot; I like having Stable as my "primary" distro, the one that I know I can count on, but I also like having a cutting-edge, rolling-release distro available -- Sabayon, for example.

I like to move on to the current "Testing" a few months after the Testing freeze, then stay put as Testing goes to Stable, and on until the next Testing freeze. So for most of the cycle, I'm using Stable. Towards the end, Stable gets too long-in-the-tooth for my tastes. Plus, I get kinda anxious to see what's coming next.

I was very interested in Linux Mint Debian at first, but I didn't like that it was based on Testing, and didn't think that the Update Packs system would be a good idea. So I stayed away. Considering the complaints I'm seeing over at the Mint forums, I guess it's good that I did.

I use only LTS versions of Ubuntu (and I did the same with Mint, when I ran that distro).

---

