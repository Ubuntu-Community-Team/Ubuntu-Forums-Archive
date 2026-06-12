---
title: "I gave up on 64 bit Ubuntu and Installed Arch x86_64 Today"
date: 2009-05-30
forum: Testimonials &amp; Experiences
---

### Post by jeffsa12 on 2009-05-30
I've been using Ubuntu since 7.10 and have been **very** pleased with all my 32 bit installs. Awsome OS!!!

I recently thought I should build an up to date computer to replace my 3 ghz Pentium 4 based workhorse. Hardware is amazingly cheap now, and I'm still making decent money. I thought now is the right time before I get a surprise laid off notice and put it off a few more years.

I started with an Asus M3A78-CM, using the on board ATI 3100 graphics, an AMD quad core 9850, with 4 gig ram and 750gb HD, 23" monitor. I was thinking vbox with several OS's at once capacity. Not cutting edge by any means, but less than $500 for complete system minus the monitor.

I initially loaded Ubuntu 8.10 AMD64. It proved to be kinda buggy.....so I updated to 9.04 just to try it out. No better, so I decided to fall back on my favorite, 8.04 Hardy long term support, but 64 bit this time as dual boot.

64 bit, Hardy wouldn't run Desklets which is a no go for me. I found a hacked version of desklets that broke my system. Reloaded and found a different hack for desklets that ran but was unstable. I ended up removing desklets, but Hardy 64bit still proved quirky.  I wanted the "main" OS on my new computer to be rock solid like my 32 bit Hardy. I tried Debian 5.0 64 for a bit. No Desklets there either. I ended up compromising with a dual boot flashy but quirky Ubuntu 9.04 64 and an 8.10 32, which is relatively stable, pretty much does what I want, but doesn't see all my ram. 

I really prefer and like Debian based distros, but I was willing to try something different if needed. 

I spent most of the day installing Arch 2009.2  i686-x86_64 along side my 2 Ubuntu installs. As much work as that turned out to be, I was just glad to finally log into a familiar gnome desktop. My reason for arch was the package management works with both binary and source. If I learn to build all the packages for it from source along with a custom kernel, I thought possibly:

1) A good linux learning experience 
2) Possibly end up with a more stable 64 bit OS

Time will tell if it proves to work for me as I'd like.

I'd like to feel justified in my new computer purchase with better performance and or stability.....so far I can't as my old Pentium is actually more stable, about as fast, etc.

It seems the hardware is getting so far ahead of the current OS's and applications. Adobe just came out with a "real" 64bit test version of flash....At this point, no comment on the (Suse Linux?) java replacement effort, it's not yet mature. Java 64bit for FF was not available from the repos on a few Ubuntu 64bit OS's. 

So it seems we (Linux) have rock solid support for 32 bit, but not so much for 64 bit. I thought the 64bit architecture had been out long enough to have matured within the desktop computer area but I guess not.
Are the near future 8 processor Intel chips going to completely surpass the OS and apps....well not that we'll want or need them for our desktops!!! Anyone remember thinking that about the dual core processors before they were available???


Anyone have anything to add?

---

### Post by hyperdude111 on 2009-05-30
I use 64bit only and have no problems. I don't use desklets but i used to use google gadgets which is almost the same thing.

I have had no problems with compatibility in 64 and the only program using ia32 libs is google chromium.

---

### Post by DeMus on 2009-05-30
I have used Hardy 8.0.4-64 for a year without any problems, since April of this year switched to Jaunty-64 and also now things work as they should. No problems what so ever.
When you keep having problems with 64 bits OS's there might be something wrong with your computer, maybe some hardware which is not recognized properly, maybe a wrong driver.
But don't say the 64-bits versions are unstable because they are not.

---

### Post by philinux on 2009-05-30
Benn using 8.10, 9.04 and testing 9.10. All 64 bit no probs. Occasional firefox hang but thats all. I blame FF. 

All hardware detected fine. Very low cpu usage on idle, like 5%.

---

### Post by rivenathos on 2009-05-30
Debian 5 "Lenny" has gdesklets.  They are available via Synaptic, the Add/Remove applications, as well as Aptitude.  You may have just overlooked them, but they are there.  They are STABLE, as well.

As for 64-bit, well, I get much better performance and dependability with 64-bit versus 32-bit in regards to my hardware.

If you ever want some suggestions for 64-bit Debian 5, PM me.  I do wish you good luck with Arch if you decide to go that route.

---

### Post by Legace on 2009-05-30
Been using 64-bit Jaunty from April, and it has been very stable. I haven't tested gdesklets, but everything that I have needed has worked for me.. :)

---

### Post by SuperSonic4 on 2009-05-30
> **jeffsa12 said:**
> I really prefer and like Debian based distros, but I was willing to try something different if needed. 

I spent most of the day installing Arch 2009.2  i686-x86_64 along side my 2 Ubuntu installs. As much work as that turned out to be, I was just glad to finally log into a familiar gnome desktop. My reason for arch was the package management works with both binary and source. If I learn to build all the packages for it from source along with a custom kernel, I thought possibly:

1) A good linux learning experience 
2) Possibly end up with a more stable 64 bit OS

Pacman is the best package manager I've ever come across. I also installed yaourt to install from the AUR without compiling. I've been running Arch 2009.02 x64 since it came out and with only one reinstall to remove clutter. 64bit is only weak when it comes to Wine IMO. I have to admit installing arch was a great step to learn more about Linux.


> It seems the hardware is getting so far ahead of the current OS's and applications. Adobe just came out with a "real" 64bit test version of flash....At this point, no comment on the (Suse Linux?) java replacement effort, it's not yet mature. Java 64bit for FF was not available from the repos on a few Ubuntu 64bit OS's. 


Arch is one of the more cutting edge distros that I am aware of and it is also rolling release so it follows that experimental packages will make it into their repos first - flashplugin is in extra and sun java in community. I think ubuntu does have it in the repos now though.

> So it seems we (Linux) have rock solid support for 32 bit, but not so much for 64 bit. I thought the 64bit architecture had been out long enough to have matured within the desktop computer area but I guess not.
Are the near future 8 processor Intel chips going to completely surpass the OS and apps....well not that we'll want or need them for our desktops!!! Anyone remember thinking that about the dual core processors before they were available???


Anyone have anything to add?

I think there is better support for 32 bit because it's been around longer and in some cases like distros geared to old computers will be 32 bit because that's what their target audience have. Also there are distros like debian which pride themselves on stability and reliability at the expense of the cutting edge.

Can't say anything about gnome and Arch but Arch CLI and Arch+KDEmod are lightning fast and the latter gives Kubuntu a kick up the teeth

---

### Post by whoop on 2009-05-30
> **jeffsa12 said:**
> 
Anyone have anything to add?

I could be totally wrong, cause I don't know you. So please try not to see this as being judgemental. If I understand you correctly you could say that you moved from ubuntu to arch because you found ubuntu (too) buggy. Although I could think of various reasons to move from ubuntu to arch, the buggyness of ubuntu wouldn't be one of them. Why ? Ubuntu is considered big, user-friendly, impressive community (just type some technical linux thing in google, you always get ubuntu), up-to-date etc.
So, if you experience bugs that you can't or won't solve in ubuntu, you'll be bound to experience them in arch as well (maybe different ones, but nonetheless). And you'll have a big chance that it will be more challenging to solve there (being more technical or more do it on your own). 
In any case, Arch is good distro IMHO, so you can't really go wrong there.

---

### Post by ActiveFrost on 2009-05-30
64bit version is not buggy by itself - hardware and drivers is the key of all problems !
I hope you understand that not all things can be perfect ? If it would, there would be no need to create new versions and updates ;)

Basically, if you have problems which you can't solve in Ubuntu, you will definitely have more problems in other distros AND it will be harder to solve them ( and it might lead into "do it by yourself - we won't help you" ).

** Ubuntu community is wonderful & peoples are always ready to spend their time to help others - haven't seen such an attitude anywhere else :)

---

### Post by WatchingThePain on 2009-05-30
> **ActiveFrost said:**
> 64bit version is not buggy by itself - hardware and drivers is the key of all problems !
I hope you understand that not all things can be perfect ? If it would, there would be no need to create new versions and updates ;)

Basically, if you have problems which you can't solve in Ubuntu, you will definitely have more problems in other distros AND it will be harder to solve them ( and it might lead into "do it by yourself - we won't help you" ).

** Ubuntu community is wonderful & peoples are always ready to spend their time to help others - haven't seen such an attitude anywhere else :)

I don't think it's always true that other distro's are harder to solve problems on.
As long as the distro has a good support network and documentation (like Arch) that should be fine.

---

### Post by whoop on 2009-05-30
> **WatchingThePain said:**
> I don't think it's always true that other distro's are harder to solve problems on.
As long as the distro has a good support network and documentation (like Arch) that should be fine.

True, but you can't deny ubuntu forums. It's one of the best, if not the best out there.

---

### Post by growled on 2009-05-30
Honestly, I've never been able to tell much different in performance in the 32 bit and the 64 bit. The only difference for me is that the 64 bit recognizes more RAM and takes a little bit more RAM to operate. Otherwise, I don't see the big deal.

---

### Post by WatchingThePain on 2009-05-30
> **whoop said:**
> True, but you can't deny ubuntu forums. It's one of the best, if not the best out there.

I didn't deny Ubuntu forums.
Most likely Ubuntu forums are best.
My point is that Arch also has excellent forums so the original poster should not be scared that problems will be more difficult to solve.

---

### Post by jeffsa12 on 2009-05-30
Yes, Lenny has gdesklets available in the repos but it doesn't run on 64bit as is... Same as one of the Ubuntu 64bit...forgot which version, it's there but doesn't run at all from the repos.

I haven't ruled out a possible hardware problem, but 32bit runs fine. By buggy I mean for example, FF 3.0.10 right click bug only when on some OS's, but not all. I definitely had an odd, intermittent fglrx driver bug in one instance, but I use it on all my installs w/o problems. I get some occasional strange behavior with graphics, only in FF on my 9.04 64 install. I had lockups requiring hard reboots in 8.04 64.

In all honesty, I'm probably just nit picking on some of the little issues for sure. I think I was just used to absolutely no problems after setup with 32bit. I didn't realize there was that much difference between 32 and 64 bit OS's before playing around with them first hand.

Also keep in mind...this is a hobby for me. What would be considered very usable by 99% of users, I may see a small glitch, which if I can't solve, is a good reason for me to experiment and try something different.

I'm also thinking that different CPU manufacturers architecture, core count, etc are all built to technical specification "standards", but implemented differently, therefore possibly causing some problems with the way some OS's and applications use the hardware. 

Anyone else using an AMD quad core cpu?

---

### Post by HappyFeet on 2009-05-30
> **DeMus said:**
> don't say the 64-bits versions are unstable because they are not.

Exactly. I read from a few sources online (google it) that because of the way 64bit is written, it is actually *more* stable than 32bit. Having said that, I use 64 Ubuntu with no problems. I will never go back to 32bit.

> **jeffsa12 said:**
> 
Anyone else using an AMD quad core cpu?

I am, and love it. I'm using the Phenom 9950@2.8ghz.

---

### Post by WatchingThePain on 2009-05-30
> **jeffsa12 said:**
> Yes, Lenny has gdesklets available in the repos but it doesn't run on 64bit as is... Same as one of the Ubuntu 64bit...forgot which version, it's there but doesn't run at all from the repos.

I haven't ruled out a possible hardware problem, but 32bit runs fine. By buggy I mean for example, FF 3.0.10 right click bug only when on some OS's, but not all. I definitely had an odd, intermittent fglrx driver bug in one instance, but I use it on all my installs w/o problems. I get some occasional strange behavior with graphics, only in FF on my 9.04 64 install. I had lockups requiring hard reboots in 8.04 64.

In all honesty, I'm probably just nit picking on some of the little issues for sure. I think I was just used to absolutely no problems after setup with 32bit. I didn't realize there was that much difference between 32 and 64 bit OS's before playing around with them first hand.

Also keep in mind...this is a hobby for me. What would be considered very usable by 99% of users, I may see a small glitch, which if I can't solve, is a good reason for me to experiment and try something different.

I'm also thinking that different CPU manufacturers architecture, core count, etc are all built to technical specification "standards", but implemented differently, therefore possibly causing some problems with the way some OS's and applications use the hardware. 

Anyone else using an AMD quad core cpu?

Yes I have Phenom I quad and it's really been fine.

---

### Post by jeffsa12 on 2009-06-18
Follow up:

I logged into my Ubuntu 9.04 64bit today (in use now) and was very pleased to see the right click bug had been fixed in the Firefox update in 3.0.11.

This was my biggest issue with Ununtu 9.04 64 bit.

I would like to take the time to thank all the developers and everyone else involved in bringing us Ubuntu and Firefox!!! 

Ubuntu will always be at the top of my favourite Linux distros and is the distro that convinced me to move to Linux full time for all my computer use.

I'd also like to say that getting an Arch 64bit install to do everything Ubuntu does on your desktop would be a great learning experience for anyone who would be interested in learning a bit more about Linux. Great job to all the people making this distro possible!!

In closing I'd like to say LINUX ROCKS and I see GNU/Linux, OSS/FOSS as the greatest example of what can be accomplished by group of individuals that truly benefits all involved. 

It's refreshing for me to see in these economically troubled times, something that obviously works for the benefit of any/all user(s), that's not going to get screwed up or eliminated by greed and $$$$$ as the underlying driving force!!!

---

### Post by ukripper on 2009-06-19
No doubt everything in Arch is well documented and is also a top notch rolling distro. You create your own Arch your way (i like their philosphy). Arch is for experienced linux users only but not for all unlike ubuntu which on other hand is all-size-fit;).

---

