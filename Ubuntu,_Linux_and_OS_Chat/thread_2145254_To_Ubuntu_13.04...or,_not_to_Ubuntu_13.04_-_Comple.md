---
title: "To Ubuntu 13.04...or, not to Ubuntu 13.04 - Complete Disappointment"
date: 2013-05-14
forum: Ubuntu, Linux and OS Chat
---

### Post by peshko-lnx on 2013-05-14
Let me first start to say that I completely support patching bug #1....by no means! But I think 13.04 was rashed too much...or Ubuntu testing has gone down the hill big time.

I have been a long time Ubuntu user. I started with 9.10 and moved to 10.04. ever since I have been using 10.04 pretty successfully. 9.10 has been great for me. Pretty well bundled. Everything worked, as it is supposed to be running, down to the smallest detail. I customized my gnome d
desktop, nautilus, etc.

recently I got a new laptop, put a larger disk and decided to start fresh with 13.04. What a disappointment that was...I have no problem moving from Gnome to Unity, nor issues with the installation. Installation was flawless.

I am shocked that Canonical would let so many bugs go to their production release...Let me list a couple:

- Suspend hangs my laptop - [https://bugzilla.kernel.org/show_bug.cgi?id=42977](https://bugzilla.kernel.org/show_bug.cgi?id=42977)
- Ethernet card does not work when the laptop works on a battery - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652)
- Screen Lock does not work

etc.

And these are just a couple of MAJOR problems that are currently running out of my Ubuntu deployment. Plain vanilla install, with no other software. Still questioning the feasibility of the move to 13.04 and whether I should move at all...

So here is the rhetorical question - are we trying to build a fix for bug #1, or simply following Microsoft's steps of releasing a release that is not prime time ready...??? Or is Canonical turning into Microsoft's mirror image, pushing things without proper testing and with no care it that really is going to work...??? Should I mention the disaster of Windows Vista?

I think Canonical need to get their act together, before they go downhill....really fast...

In the meantime, I would recommend to everyone that is looking at Ubuntu 13.04 to look at alternatives, test and see if everything would work fine before make the call.

---

### Post by kargool on 2013-05-14
For me, 13.04 seems like a bug-fixed version of 12.10 with a few extra features and changes.
The main reason for me to upgrade was performance and the cloud app monitor.

I use ubuntu on my laptop (Thinkpad E420, i5-2540m, intel HD3000 graphics, 64-bit Linux) and i have noticed a great increase in battery life as unity has been tweaked to give much better performance. There have been far less compiz/unity crashes than a fresh 12.10 install AND i have noticed almost a 20-30% increase in battery life.

I have not yet tested the performance of Unity on disctrete graphics (AMD Radeon HD6630m, fglrx Catalyst 13.4)

I also like the changes to the user interface and style. The new cloud app indicator is useful to me as I use ubuntu one to sync between devices but do not want active syncing to occur when I am working on files as it would sync whenever I saved a file. Now I can easily turn off syncing without having to load the heavy Ubuntu One application.

---

### Post by pqwoerituytrueiwoq on 2013-05-14
I am running xubuntu 13.04 64bit on several machines no issue, i even started switching to it before April was here on production machines (i was running beta full time)
only had 1 bug show up, and it was fixed during iso testing, and it had a easy workaround
about a week before raring was released there was a bugged kernel, bad for nvidia gpus and lots of hdmi audio chips, upgrading to the [mainline kernel](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme) solved this

---

### Post by cariboo on 2013-05-14
> **peshko-lnx said:**
> Let me first start to say that I completely support patching bug #1....by no means! But I think 13.04 was rashed too much...or Ubuntu testing has gone down the hill big time.

I'd suggest if you feel that testing doesn't fix problems with your system, that you take part in testing, either by joining the [Q/A team]("http://qa.ubuntu.com/"), or installing Saucy, and participating in threads in the [U+1 sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=427").

The more people with different hardware testing, the better.

---

### Post by llanitedave on 2013-05-15
I just downloaded Ubuntu 13.04 and gave it a spin for  few days.  Bottom line:  I like it.  I haven't encountered any notable bugs.  There are some nice added touches compared to 12.04, and it does look nice and clean.  I do like the fonts, and if there's a sluggishness, I don't see it on my Toshiba Satellite.

More bottom line:  I also just upgraded my Kubuntu to 13.04, and that has some nice minor improvements as well.  All things considered, I still prefer Kubuntu over Unity.

I've now gotten familiar with the big three -- Xubuntu, Kubuntu, and Ubuntu.  Although I do have a personal favorite, that's just me.  Any one of those DE's is actually a pleasure to use.  None of them has shown any stability issues, or made me regret using them.

---

### Post by pfeiffep on 2013-05-15
> [COLOR=#000000]But I think 13.04 was rashed too much...or Ubuntu testing has gone down the hill big time.[/COLOR]

Possibly stick with a LTS version

---

### Post by mastablasta on 2013-05-16
> **peshko-lnx said:**
> I am shocked that Canonical would let so many bugs go to their production release...Let me list a couple:



if the new laptop on Ubutnu certified list? : [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
 
if not (probably now since mostly old stuff is there), then what is the problem? 

unfortunatelly the procedure in your case is: test, report the bug, wait for it to be sovled.

if everything is ok, then publish it on laptop compatibility list. maybe it will even get Ubuntu Certified.

---

### Post by peshko-lnx on 2013-05-16
> **mastablasta said:**
> if the new laptop on Ubutnu certified list? : [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
 
if not (probably now since mostly old stuff is there), then what is the problem? 

unfortunatelly the procedure in your case is: test, report the bug, wait for it to be sovled.

if everything is ok, then publish it on laptop compatibility list. maybe it will even get Ubuntu Certified.

This is a good point! I just checked, and there is no Toshiba laptop/desktop certified... In my case most of the problems has already been reported...I keep testing, so I will see how everything is going to turn out...

---

### Post by peshko-lnx on 2013-05-16
> **pfeiffep said:**
> Possibly stick with a LTS version

That's what I used to, but decided to check the latest one anyway. Had 10.04 running for a long time...

---

### Post by peshko-lnx on 2013-05-16
> **cariboo907 said:**
> I'd suggest if you feel that testing doesn't fix problems with your system, that you take part in testing, either by joining the [Q/A team]("http://qa.ubuntu.com/"), or installing Saucy, and participating in threads in the [U+1 sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=427").

The more people with different hardware testing, the better.

I will probably go for Saucy. I have no problem doing some testing and support the development.

Thanks!

/Peter

---

### Post by peshko-lnx on 2013-05-16
> **pqwoerituytrueiwoq said:**
> I am running xubuntu 13.04 64bit on several machines no issue, i even started switching to it before April was here on production machines (i was running beta full time)
only had 1 bug show up, and it was fixed during iso testing, and it had a easy workaround
about a week before raring was released there was a bugged kernel, bad for nvidia gpus and lots of hdmi audio chips, upgrading to the [mainline kernel]("https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme") solved this

The kernel bugs are that I encountered are still in Xubuntu, but I like Xuubuntu more than Unity.

---

### Post by peshko-lnx on 2013-05-19
To add to the weird and untested...

My download speed is incredibly slow. Using speedtest.net my download  speed is in the range of 20-30 Mb/s regardless of the server. Upload  speed is pretty good thou. I am using Wireless connection. My router is  Netgear R6300.

My ISP is FiOS and I am at 75/35 plan.

In comparison rebooting in Windows 7 speedtest.net is at 80 Mb/s down and 38 Mb/s up.

Another strange thing I discovered is that when I look at the connection  information of my wireless connection it constantly fluctiates b/w 6  Mb/s and 144 Mb/s. It never goes above 144 Mb/s. In comaprison, my  Windows 7 stays at 300 Mb/s constantly pretty much. Drops to 270 rarely.

I just upgraded to the latest kernel from the repository and took quite a while just to download.

My adapter is Intel(R) Centrino(R) Advanced-N 6230. Attaching both tests - Ubuntu 13.04 (26 Mb/s down and 39 Mb/s up) and Windows 7 (84 Mb/s down and 39 Mb/s up). Both tests in wireless connection. And again, this is pretty much plain Ubuntu installation. I also tested it with a LiveCD, with the same horrible download speeds. OPened a thread in the Networking forum, but so far no replies...

[ATTACH=CONFIG]242763[/ATTACH][ATTACH=CONFIG]242764[/ATTACH]

---

### Post by ARooster on 2013-05-20
> **kargool said:**
> For me, 13.04 seems like a bug-fixed version of 12.10 with a few extra features and changes.

I agree. It seems to run smoother as well. The 3D desktop effects are also nicely done and seem to be quite well optimised as I believe they work faster than the 12.10. The stability issues in 12.10 were too much for me so I went back to 12.04 after less than a month. 13.04 seems to be running well, however. The one issue I had with it, however, was that I was unable to start the 3D desktop right after the installation. It's annoying having to look for solutions to issues while unable to even open the desktop, let alone a web browser. The display driver defaults to Noveau and the 3D Unity just doesn't seem to work on my nVidia with Noveau. However, after switching to a proprietary nVidia driver through terminal everything seems to be fine. The main beef I have with Ubuntu about this is it's been an issue since they started Unity. You could resolve it by going in through Unity2D but the issue was not resolved even though Unity2D has been cancelled.

I think that since you have the option to download updates and proprietary software such as mp3 support and Flash during installation they could add another option to download and install a proprietary display driver.

---

### Post by prusswan on 2013-05-20
Unity was a path of no return, and the primary reason for the mass divide/exodus after 12.04. Many people on the current LTS will have no viable upgrade path and have no choice but to turn to other distros so that their meets can continue to be met adequately. Of course, some have decided to move on right away.

---

### Post by craig10x on 2013-05-20
While initially, when unity was introduced, there was much hue and cry....but many eventually decided to spend some time and give it a chance and completely turned around and really enjoy using it now...so i wouldn't say there was a mass exodus....just an initially "over-reacting negative response"...and others did decide to try other versions of ubuntu or other distros like linux mint, etc...

Also, Unity has greatly improved in each new ubuntu version and some who were lukewarm to it originally now very happy using it... :)

---

### Post by deadflowr on 2013-05-20
> **prusswan said:**
> Unity was a path of no return, and the primary reason for the mass divide/exodus after 12.04. Many people on the current LTS will have no viable upgrade path and have no choice but to turn to other distros so that their meets can continue to be met adequately. Of course, some have decided to move on right away.

Is your brain fried?

Anyone on the current LTS default Ubuntu is already enjoying unity.

I take it you mean after lucid.

And unity can do all the things anyone needs to do, it just takes a different way of looking at how to do them.

---

### Post by prusswan on 2013-05-20
> **deadflowr said:**
> Is your brain fried?

Anyone on the current LTS default Ubuntu is already enjoying unity.

I take it you mean after lucid.

And unity can do all the things anyone needs to do, it just takes a different way of looking at how to do them.

gnome-session-fallback, but what would eunuchs know?

---

### Post by deadflowr on 2013-05-20
gnome fallback ain't the default.

---

### Post by prusswan on 2013-05-20
> **deadflowr said:**
> gnome fallback ain't the default.

I didn't say it is, but it does explain why the exodus has already begun at 12.04

---

### Post by deadflowr on 2013-05-20
> **prusswan said:**
> I didn't say it is, but it does explain why the exodus has already begun at 12.04

Those who switched distros, switched two distros before precise came out.

Some for the bizarre disdain for a quirky desktop.
And far more because the hardware they had couldn't handle unity.
I was one of the latter, for a time.

Personally, if I was to need a classic desktop design, I'd go with xfce over classic gnome.

---

### Post by peshko-lnx on 2013-05-20
Guys, I don't want to poop on the party, but I don't want to make the thread unity vs non-unity. Frankly speaking I was a long time Gnome user, but I don't like Gnome3 and I like xfce. But all this is personal preference...

The idea if the thread was to point the fact that Canonical pasy less and less attention on testing and rather rushes releases out of the door prematurely. I was running 10.04 for years and recently I decided to try 13.04 it for me it was a complete failure!

There are way too many issues that keep out of completely moving to 13.04. I will try 13.10 and see how the development goes...but I just recompiled and installed kernel 3.9.3 and Ubuntu 13.04 looks a bit better. I suspect why they do not put it in mass release, but to me it is questionable...

---

### Post by iamkuriouspurpleoranj on 2013-05-20
Running Xubuntu with zero problems. I actually followed development of 13.04 a little in the Ubuntu +1 section of these pages. There was simply a feeling from quite early on that 13.04 was quite stable and this was indeed my own experience on those occasions when I tried out a development build of Ubuntu (not Xubuntu).

Not sure where this instense criticism of Ubuntu comes from but as someone used to running CentOS and Debian stable, I find the latest Ubuntu to be comparable to say Fedora or openSUSE. In other words, good for a modern desktop. Buggy, bloated and unstable? Yeah, yeah, yeah.

I actually find criticism of Ubuntu getting buggier, more bloated and increasingly unstable with each new release. So maybe its detractors need to pull their finger out, hmm?

---

### Post by Sam Mills on 2013-05-21
> **peshko-lnx said:**
> 
The idea if the thread was to point the fact that Canonical pasy less and less attention on testing and rather rushes releases out of the door prematurely.

Then there are those that do research and prepare for a new release/buy/build linux compatible hardware. It's really a rather old concept. I'm sorry things didn't work out for you, but I have a high end laptop that will run *anything*. Because I did homework instead of running off to BestBuy and buying any old thing. Would you go to System76 if you wanted a Windows computer?

---

### Post by Sam Mills on 2013-05-21
> **iamkuriouspurpleoranj said:**
> 
Not sure where this instense criticism of Ubuntu comes from but as someone used to running CentOS and Debian stable, I find the latest Ubuntu to be comparable to say Fedora or openSUSE. In other words, good for a modern desktop. Buggy, bloated and unstable? Yeah, yeah, yeah.


We all have different experiences based on our hardware. Those with compatible hardware have great experiences, and those who don't, not so much. I realize ubuntu won't work on *every* computer, (nothing will) that's why I choose hardware that's certified for ubuntu/linux. Sure, the average person won't follow that path, but then again ubuntu isn't targeted for my grandmother. Unless I install it for her, and maintain it. But I would have to do that with windows too.

Ubuntu is doing just fine, considering it gets little help from manufacturers. If your computer doesn't work right with Ubuntu, get one that does, or stay with what you know. No big deal. It doesn't really concern me that people *love* windows or mac. If that's your thing, that's cool. 

If you want the best linux experience, buy a pc with linux preinstalled, or buy compatible hardware. Isn't that what windows and mac users do?

Btw, 13.04 has been pretty much perfect so far. For me. Good luck.

---

### Post by ARooster on 2013-05-21
In this day and age there are several computers (in various formats) around any household or workplace. When buying a new computer you can do research and squeeze out a bit of extra money and get a high-end PC, but a lighter weight OS with less bloat will run well on an older PC as well. This is why many people come to Ubuntu. A modern-looking OS without the need for the newest hardware to run it. Unity has removed that. The problem with this, the way I see it, is as soon as your OS requires "new hardware" to run it is competing with Windows and MacOS on their terms.

As far as buying compatible hardware, I would really like to know which graphic card works great out of the box with Ubuntu. Both nVidia and AMD have closed-source drivers, as far as I'm aware, Intel's no better. When Ubuntu doesn't even have the option to start with proprietary drivers (which it could probably download during installation as easily as it does the Fraunhofer mp3 decoder) and defaults to Noveau it forces you into sorting out issues before you're even done logging onto your account for the first time. This doesn't happen with Windows or Mac systems. I guess this is why Ubuntu is loosing out. It still requires some knowledge to install, thus driving away inexperienced users, while at the same time being a "modern OS" with all the bells and whistles that generally does not sit well with the hardcore Linux crowd. 

Having said that, personally I like Unity as a productive desktop environment, it's less gimmicky than say Cairo dock or the Mac dock thing (I really hate it when buttons move around on mouse-over) and once you install the proper 3D-supported display driver it is reasonably stable. The buttons on the side bar work well (and as they don't move around or hide by default it's really a nice way of having all your most frequently used software available in a single mouse click. Kind of a tidier desktop with icons that also doubles as a task bar. For anyone who uses a lot of various pieces of software infrequently I would suggest installing the Classic Menu Indicator as the Dock takes quite a bit of getting used to and can be slower than browsing through the classic (GNOME 2) menus.

In my experience 13.04 is much more stable than 12.10, however, so I would definitely suggest 13.04 to anyone on 12.10. In fact, I find it is about as stable and as fast as the 12.04 LTS, but has a bit more polish.

---

### Post by iamkuriouspurpleoranj on 2013-05-22
Intel graphics driver works out of the box, although I hear it's not great for games. Running Intel now and the shear joy of not having to fear Xorg updates cannot be conveyed through mere words. So here is a small picture to express how it makes me feel : :)

---

### Post by Bucky Ball on 2013-05-22
@ peshko-lnx: Stick to LTS and save the headache, then. It is a known fact that interim releases can be problematic and to expect the unexpected. If you want stability, install a stable OS and have a spare partition or two to play around with the interim releases. It is quite common. Why complain about something that is par for the course and a known fact, i.e. Interim releases are prone to crashes, especially after updates and especially within the first few months after release?

You have the proof: 10.04 is an LTS release and has been out for three years (and now EOL). 13.04 is interim and has been out not quite a month. Go figure. It's logical. One's a stable, tried and test over time workhorse with the bugs ironed out, the other is a wet behind the ears plaything which will stabilise probably just in time for it to reach EOL (by which time 14.04 LTS will have been released anyway). 

You can upgrade directly to 12.04 LTS from 10.04 LTS (LTS is ALWAYS upgradeable directly to the next LTS when it is released without having to go through every interim release on the way). I'd install Xubuntu 12.04 LTS and get into it rather than wasting time on this. Good luck. ;)

---

### Post by prusswan on 2013-05-22
> **peshko-lnx said:**
> Guys, I don't want to poop on the party, but I don't want to make the thread unity vs non-unity. Frankly speaking I was a long time Gnome user, but I don't like Gnome3 and I like xfce. But all this is personal preference...

The idea if the thread was to point the fact that Canonical pasy less and less attention on testing and rather rushes releases out of the door prematurely. I was running 10.04 for years and recently I decided to try 13.04 it for me it was a complete failure!

There are way too many issues that keep out of completely moving to 13.04. I will try 13.10 and see how the development goes...but I just recompiled and installed kernel 3.9.3 and Ubuntu 13.04 looks a bit better. I suspect why they do not put it in mass release, but to me it is questionable...

Well, direction has vastly changed between 10.04 (which runs much faster than 12.04 even on an old machine) and 13.04, now given their different position in the market, they kind of decided that luring people with eye-candy towards a more profitable business model, should be the way to go. Unity is just a small piece of the grand puzzle, but still a significantly annoying one. It's kind of like the Linux parallel to Windows 8, except that the group-think may go on for a little longer since they have less to lose compared to Microsoft.

---

### Post by craig10x on 2013-05-22
I wouldn't compare unity with windows 8 metro interface...unity is easy to use, intuitive and works well for either mouse or touch screens...metro is confusing to use, un-intuitive and only works well for touchscreens...

People go to apple stores (who have only known windows) and ooh and ahh over the mac interface...well, unity desktop is actually very mac like with a dock, global menu and a search that is also like the mac has...nothing annoying about that at all...does everything have to be like windows???

Also, i think the original poster is a little confused...gnome 3 has nothing to do with the interface....gnome itself actually has the gnome shell now...unity is a much sleeker, streamlined version that ubuntu created on it's own...gnome 3 works with gnome shell, unity, gnome fallback, even interfaces like linux mint's cinnamon desktop, and others...

---

### Post by monkeybrain2012 on 2013-05-22
> **prusswan said:**
> Well, direction has vastly changed between 10.04 (which runs much faster than 12.04 even on an old machine) and 13.04, now given their different position in the market, they kind of decided that luring people with eye-candy towards a more profitable business model, should be the way to go. Unity is just a small piece of the grand puzzle, but still a significantly annoying one. It's kind of like the Linux parallel to Windows 8, except that the group-think may go on for a little longer since they have less to lose compared to Microsoft.

Not sure what your point is. I started off with 10.04 and I can tell you everything works a lot better and smoother in 12.04 if you have relatively up to date hardware.My main labtop is 4 years old and got it for $600 in a sale, hardly high end, in 10.04 I have to install the Nvidia driver or the graphic is really glitchy, it wouldn't even work with something like google earth, now I can use nouveau out of the box with all the eye candies and it is smooth as silk (in fact it works better than the blob for most things except games and vdpau). Now if you have <= 1G of ram then unity is not recommended but then kde would be even slower on such spec.For lower end or older machines Lubuntu is excellent and it is an  'official' Ubuntu respin, it is not like you are forced to upgrade your hardware, so I really don't get the complaint (and btw  lubuntu 12.04 is light years ahead of lubuntu 10.04 (or 10.10?, don't  remember if it was even around the time of 10.04) 

You can't expect Ubuntu to cater always to the lowest common denominator hardware and be forever stuck in the past just because some people have ancient hardware and/or  hate changes. 

Luring people with eye candies has always been the case, look at all the Youtube videos with the compiz rotating cube and special effects. I see nothing wrong with trying to expand into the mobile market and get "mainstream". For one thing it brings in better hardware and software support that will enrich the entire Linux ecosystem, yes, even on the desktop.

---

### Post by Bucky Ball on 2013-05-23
> **peshko-lnx said:**
> ... I don't want to make the thread unity vs non-unity.

Please keep this in mind posters past, present and future. If the thread devolves into a debate regarding this (as it threatens) the thread will be either closed or moved to ***Recurring Discussions***. Thanks. ;)

---

### Post by Sam Mills on 2013-05-23
> **ARooster said:**
> as far as I'm aware, Intel's no better.
Not really true. Intel actually develops with linux in mind. The only problem is, is that you will be hard pressed to play the latest and greatest games using Intel graphics unless you turn down the resolution. 

If you are not a gamer, or just a gamer with modest needs, stick with all Intel chipsets. They are pretty much guaranteed to work wonderfully with just about any distro.

Although linux will work on many, many, many, more computers than OSX will, the same approach will go a long way. You can't just install OSX on any old hardware and expect it to work perfectly. The same with linux, except that linux will run just fine on *a lot* of computers. A little research goes a long way when it comes to becoming a long time linux user.

One must weigh the benefits vs. time/effort and make a decision. I made mine a long time ago with no regrets. My linux experience has been outstanding to say the least.

---

### Post by BrokenKingpin on 2013-05-23
I am using Xubuntu 13.04 and am pretty happy with it. It actually resolved some issues I had with my laptop. With the amount of stuff that changes upstream (Kernel, Xorg, etc.), it is hard for them to get everything correct for every piece of hardware on every release.

As others have said, you can always help test, because if you reported those bugs earlier in the cycle there is a higher chance they would have been fixed for the releases. Also keep in mind this is not an LTS, so it will be less stable by definition. I have been using Ubuntu since 5.04, and have had a few hardware regression from release to release, so I understand it can be frustrating, but ranting about it will get you anywhere.

I am getting very sick of the random Microsoft bashing. Their releases go through a ridiculous amount of testing, and their support really is not that bad. The Vista argument is just getting quite old. They changed a lot of fundamental stuff in Vista, so it is normal to have bugs and regression, and of course it needed more hardware resources... people were comparing it to a decade old operating system (XP). It is not like Linux has never introduces issues when introducing new technology into the desktop. When introducing new technology there will be bugs, which is the cost for innovation.

It is fine to not use MS products, and it is fine to dislike MS products, but just throwing out ignorant insults and not backing it up is just ridiculous.

---

### Post by Bucky Ball on 2013-05-23
And further to what BrokenKingpin has posted, a quick reminder to ***_all_***, from the forum Code of Conduct:

> Attacks and derogatory terms of any kind are not welcome. *_This includes references to other operating systems and the companies that produce them._*

OS bashing will result in 1/ the thread being closed or 2/ your post being deleted. Both situations may attract infractions, i.e. temporary suspension. Furthermore, do not hesitate to report any threads that you deem to be OS bashing by hitting the 'Report Post' button in the users details at left or top of their post and leave it with staff. Thanks.

Note: The reason I am posting these reminders is not that this thread has breached any rules yet but it is skirting the line. Let's not go there. ;)

---

### Post by peshko-lnx on 2013-05-23
> **BrokenKingpin said:**
> As others have said, you can always help test, because if you reported those bugs earlier in the cycle there is a higher chance they would have been fixed for the releases...

I am not sure if this goes for me or not (since I opened the thread...) but I have been running 10.04 for pretty long time ~2+ years, tried to move it to 12.04 quite a bit after 12.04.1 was released and it was a frustrating upgrade...way too many issues. The question comes to the point of 1/ how fast a bug would be fixed (and I understand the priorotization process...) and 2/ should you really expereince THAT many problems after x.x.1 sub-release...

> Also keep in mind this is not an LTS, so it will be less stable by definition

Really??? Where is that definition? That does not sound right, does it? So what you are saying is don't buy a house, because there are better houses built down the road, but they will be ready in a couple of years...isn't that an infinite loop? IMHO each official release, should have an appropriate regression testing, regardless. Especially against major, mass populated HW components.

> I am getting very sick of the random Microsoft bashing. Their releases go through a ridiculous amount of testing, and their support really is not that bad. The Vista argument is just getting quite old. They changed a lot of fundamental stuff in Vista, so it is normal to have bugs and regression, and of course it needed more hardware resources... people were comparing it to a decade old operating system (XP). It is not like Linux has never introduces issues when introducing new technology into the desktop. When introducing new technology there will be bugs, which is the cost for innovation.

It is fine to not use MS products, and it is fine to dislike MS products, but just throwing out ignorant insults and not backing it up is just ridiculous.

COMPLETELY AGREE!!! Each argument must have a some kind of a backup!

---

### Post by peshko-lnx on 2013-05-23
> **Bucky Ball said:**
> And further to what BrokenKingpin has posted, a quick reminder to ***_all_***, from the forum Code of Conduct:

OS bashing will result in 1/ the thread being closed or 2/ your post being deleted. Both situations may attract infractions, i.e. temporary suspension. Furthermore, do not hesitate to report any threads that you deem to be OS bashing by hitting the 'Report Post' button in the users details at left or top of their post and leave it with staff. Thanks.

Note: The reason I am posting these reminders is not that this thread has breached any rules yet but it is skirting the line. Let's not go there. ;)

The reason for that thread was to let everyone know the problems that I am experiencing with a plain vanilla 13.04 installation. Not to throw mud at anybody, OS, distros, etc. I already have multiple bugs open, but as expected it would take awhile for a fix...additionally working with the kernel.org development to test some of the latest pathes for the kernels. I really like to make this thing work and I am willing to bend and use some terminal skills to make it so...but certain things cannot be simply fixed that way and requires some really deep analysis and debugging, so you can get it fixed.

The frustrating part is that some of those things are mass populated HW components in today's laptops and it is strange that I am getting those issues....really surprising...

There are other things that I can easily find a solution one way or another, that I would not post here, since most of those are already resolved by other users.

---

### Post by Bucky Ball on 2013-05-23
Re. upgrading: Direct upgrades are known to be problematic at times. I stick to clean installs myself to avoid any of this. Maybe you should do a clean install of 12.04 LTS and see if that works. Does it work from the LiveCD? Does 13.04?

 > So what you are saying is don't buy a house, because there are better houses built down the road, but they will be ready in a couple of years...

The interim releases are a warm-up for the LTS really and yes, there is a lot of testing goes on so breaks are not uncommon. It is a known fact that LTS is designed for production machines, servers and stability. Not necessarily the case with the interims. 

Me? Stable LTS as my main squeeze and a couple of spare partitions for playthings, like interim releases. I need my machine to be reliable. Good luck but this thread is starting to go nowhere fast. ;)

---

### Post by peshko-lnx on 2013-05-24
> **Bucky Ball said:**
> Re. upgrading: Direct upgrades are known to be problematic at times. I stick to clean installs myself to avoid any of this. Maybe you should do a clean install of 12.04 LTS and see if that works. Does it work from the LiveCD? Does 13.04?

 The interim releases are a warm-up for the LTS really and yes, there is a lot of testing goes on so breaks are not uncommon. It is a known fact that LTS is designed for production machines, servers and stability. Not necessarily the case with the interims. 

Me? Stable LTS as my main squeeze and a couple of spare partitions for playthings, like interim releases. I need my machine to be reliable. Good luck but this thread is starting to go nowhere fast. ;)

13.04 LiveCD has the same issues as the installed. Slow wireless speeds, several interface issues, and I have bug reports open on a couple of those, etc. I should try 12.04 and see.

In respect to the thread, everyone has the right of an opinion, regardless of the context, viability, etc. I am surprised it went that far to be  honest. My basic idea of this thread is to share my experience and get everyone else's experience. And I would like to have this unbiased opinions. That's pretty much it. Simple and clear. I have no control what everyone else is writing.

---

### Post by Bucky Ball on 2013-05-24
> **peshko-lnx said:**
> I have no control what everyone else is writing.

+1. Totally, I am completely aware of that. ;)

---

