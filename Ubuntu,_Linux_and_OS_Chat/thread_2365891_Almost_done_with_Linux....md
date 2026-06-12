---
title: "Almost done with Linux..."
date: 2017-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by atkinskev on 2017-07-11
Way back in 2003, I found myself tearing my hair out with Windows' unreliability, and objected to the idea of upgrading to the then latest XP for 90 quid to fix problems that were of Microsoft's making.. I was trying to get work done and having to reboot multiple times every day, it was ridiculous. I picked up a copy of, I think, PC Plus magazine, which had a cover disk with Mandrake Linux on it - my interest piqued, I decided to give it a try. It was a revelation - sure, back then getting some hardware working was a little tricky (the dial-up modem springs to mind..) but the system was rock solid. 

Such was my introduction to the wonderful world of software libre, and it changed my outlook. I tried a few distros before settling on Ubuntu pretty much right at the beginning - I tried 4.10, then completely switched to 5.04 and have stuck with it ever since, at least on my desktop machines. Over the years, the need for manual intervention has dwindled, the system has tended to 'just work', as was the original intention of this great distro. I can't say I was ever a huge fan of Unity, chiefly on grounds of its relatively clunky performance; I hated Gnome 3; and KDE has always felt just a little unstable; so in latter years, I've used XFCE / Xubuntu, which I found pretty nice. Although right now I'm revisiting Gnome in the wake of the announcement of Unity's demise - still not convinced, but I might not be hanging around desktop Linux for much longer...

.. Over the years, and certainly with the advent of Ubuntu, desktop Linux has, for the most part, done what any decent operating system should do - provide a stable foundation on which to get work / play done, and get out of the way to allow you to do it without hindrance. Even now, every time I use Windows, the plethora of third-party software pop-ups, notifications and general 'noise' drives me mad, and reminds me that it's very much a commercial proposition driven by revenue streams. But much of that rubbish can be tamed, and as a desktop platform, Redmond's latest seems solid and performs well. The same, sadly, cannot be said of Linux. Or, more to the point, systemd. 

Since 16.04, I have been having issues with DNS resolution - yes, that absolutely fundamental thing that makes the internet work. Upgrading to 17.04, it's even worse. It just fails, randomly. I've Googled it, and the problems appear related to systemd-resolved. Sometimes if I restart the service it works; most of the time, it seems a reboot is necessary. Multiple times every day, just like back in 2003 with Windows. Yes, there are a number of workarounds, but this is a really vital part of any modern operating system - how on earth has this been let out in the wild with these sorts of issues? And virtually all the mainstream distributions have jumped on the systemd bandwagon. I haven't now got time to mess around trying various options or distros - I use my machines for business. And sure, attempting to use 17.04 on a business machine might be seen as unwise, but 16.04 was an LTS release, and it, too, had problems, which is why I thought an upgrade might sort it... With such a core part of a modern operating system apparently broken, and the possibility that it affects the greater proportion of current distros, that's a deal-breaker for me...

Perhaps back in 2003 I had a willingness, and the ability, to straighten out problems; now I have less of the former, and the sheer complexity and opaqueness of systemd renders me unable to do the latter. Time, perhaps, to revisit commercial prepackaged software, which feels like a bereavement and defeat after 14 years.

---

### Post by TheFu on 2017-07-11
Before you decide, be sure to review the EULA for Windows.  I think you'll reconsider.

If you don't want systemd, there are other Linux distros without it. These won't be from Canonical and they won't be widely used.

Or you could try one of the BSDs.  Most of them have a Linux compatibility layer, so Linux programs run.  BSD is the only non-hobby distro without systemd at this point.  How many people/organizations actually use gentoo or slackware anymore.  Don't get me wrong, I ran slackware for 7 yrs - at the time it was the easiest of the distros to use. Times have changed, but slackware doesn't appear to have moved forward. I haven't looked at it much in the last 15 yrs, so perhaps my view 2 yrs ago bringing up a VM with it for a hour of use isn't fair. 

Also ran gentoo for about 6 months. They claim that since every program is build exactly for your hardware, then it will be faster.  That's the theory. In practice, it isn't true. Full-time kernel optimization MAKES A HUGE difference in system performance. An average highly technical person won't have that knowledge to tune a kernel.

But if you decide to join the proprietary OS group, know that we'll be here when you finally decide to come back.
I wish you luck in finding the best possible solution for your needs.

---

### Post by Eggnog on 2017-07-11
Try something besides Ubuntu.

---

### Post by QIII on 2017-07-11
And yet, so many of of us have no problems at all with systemd. 

I also use Fedora, which has been using it for some time.  I've not had problems.

Might I ask how often you have asked for help here?

---

### Post by #&amp;thj^% on 2017-07-11
> **atkinskev said:**
> 

Perhaps back in 2003 I had a willingness, and the ability, to straighten out problems; now I have less of the former, and the sheer complexity and opaqueness of systemd renders me unable to do the latter. Time, perhaps, to revisit commercial prepackaged software, which feels like a bereavement and defeat after 14 years.
Should of heard my rants in the beginning;)
Hang in there...it gets better.:D
And as QIII ask's have you asked for support?
Regards

---

### Post by vasa1 on 2017-07-12
> **atkinskev said:**
> ...
Since 16.04, I have been having issues with DNS resolution - yes, that absolutely fundamental thing that makes the internet work. Upgrading to 17.04, it's even worse. ... - I use my machines for business. And sure, attempting to use 17.04 on a business machine might be seen as unwise, but 16.04 was an LTS release, and it, too, had problems, which is why I thought an upgrade might sort it... With such a core part of a modern operating system apparently broken, and the possibility that it affects the greater proportion of current distros, that's a deal-breaker for me...
...I'm staying on 16.04 LTS. Unity on one partition, Kubuntu on another; Lubuntu on an older machine. I suppose they're all using systemd because they're all out-of-the-box. No issues here.

If you're facing issues on several machines and they all have differing hardware, then it's possible you could be having some issue with your router or ISP?

Either way, your post won't really help you or help us to help you. So all the best with whatever you decide.

---

### Post by poorguy on 2017-07-12
I don't quite understand the whole systemd thing and apparently not having any problems with systemd. 

My Lubuntu 16.04 is also right OOTB and works without any problems on my old Dell desktop.

---

### Post by TheFu on 2017-07-12
I do have systemd related issues, but I also have pulse-audio related issues.
Can't do anything about systemd. We're stuck. I just avoid touching anything related to it.  I'll admit it did make a few things easier.

IMHO, systemd was a solution needed by 1% of the community.  For the rest of us, the difference between a 10 sec startup and a 30 sec startup just isn't important.  When the udev team stepped away and the systemd team took over that development, we were all screwed.  That stuff is tightly coupled now, going against the Unix philosophy.  SystemD breaks the Unix philosophy is many ways.  That alone is a good enough reason to dislike it.

Used to purge pulse audio, until Firefox started mandating its use a few months ago.  I get to restart pulse-audio about 5 times a day when it crashes.

Have always had issues with network manager - always purge that too, but my network setup isn't trivial.

Because my systems aren't standard, I've never asked for help here.

Of course, there are lots and lots and lots of things that work perfectly too.  10,000 things are good, 5 are bad.  Life with Ubuntu isn't so bad.

---

### Post by sp40140 on 2017-07-12
You should, and I recommend that you try out other OS. I do that frequently and it only reinforces my preference for linux. Yes, sometimes devs make questionable decisions, but that's not exclusive to Linux (or even os). It's nature of software.
In the end, use what works for you best.
As to the problems you are having: the transition to systemd was transparent to me. I didn't notice any change. Not to question your statements. Just saying that it might be something specific to your set-up. And if you prefer to use Linux, this forum can help sort out the issue.

---

### Post by montag dp on 2017-07-12
If you're sure your problem is related to systemd, there are other Linux distros without it. Slackware comes to mind. It's not as pointy-clicky as Ubuntu, but if you could set up Mandrake Linux in 2003, I'm sure you will have no trouble with Slackware today. It's also rock-stable and with no nonsense included. Anyway, it would be worth trying something without systemd before making the much more annoying and disruptive switch back to Windows.

---

### Post by vasa1 on 2017-07-12
A friendlier systemd-free distro may be found here: [http://pclinuxoshelp.com/index.php/Main_Page](http://pclinuxoshelp.com/index.php/Main_Page)

---

### Post by mastablasta on 2017-07-12
or how about this: [http://without-systemd.org/wiki/index.php/Main_Page](http://without-systemd.org/wiki/index.php/Main_Page)

Make sure the issue is because of systemd not because of your config.

---

### Post by poorguy on 2017-07-12
[http://antix.mepis.com/index.php?title=Main_Page](http://antix.mepis.com/index.php?title=Main_Page)

Scroll the page to:**16 June 2017** 
**antiX-16.2 (Berta Cáceres) point release available** 

 and it is systemd free.

---

### Post by 1clue on 2017-07-12
> **TheFu said:**
> I do have systemd related issues, but I also have pulse-audio related issues.


Isn't that odd?  I wonder what these two packages could have in common?

> 
Can't do anything about systemd. We're stuck. I just avoid touching anything related to it.  I'll admit it did make a few things easier.


Speaking as someone who has watched several init systems come and go, that's not a happy solution. I still don't fully understand systemd but I realize that sooner or later I'm going to have to figure it out.

> 
IMHO, systemd was a solution needed by 1% of the community.  For the rest of us, the difference between a 10 sec startup and a 30 sec startup just isn't important.  When the udev team stepped away and the systemd team took over that development, we were all screwed.  That stuff is tightly coupled now, going against the Unix philosophy.  SystemD breaks the Unix philosophy is many ways.  That alone is a good enough reason to dislike it.


I agree completely, only I would have added a lot more verbiage. Some of which would almost certainly earn me the ire of the moderators.

> 
Used to purge pulse audio, until Firefox started mandating its use a few months ago.  I get to restart pulse-audio about 5 times a day when it crashes.

Have always had issues with network manager - always purge that too, but my network setup isn't trivial.

Because my systems aren't standard, I've never asked for help here.

Of course, there are lots and lots and lots of things that work perfectly too.  10,000 things are good, 5 are bad.  Life with Ubuntu isn't so bad.

The problem with systemd and pulseaudio is that their sponsor has deep pockets and lots of developers who are intent on making Linux look Just Like Windows, at least with respect to the opacity of the code they inject into the Linux world.


The OP should focus on distributions which do not use gnome. Anything that uses gnome will inevitably already use systemd or be in the process of converting to it. 

Gentoo, for example, still defaults to a non-systemd init system and has a significant group of users and developers who want nothing to do with systemd. The cost of using Gentoo is that you'll have to actually know something about how your system works, and spend more time maintaining it.

---

### Post by Habitual on 2017-07-12
This is a nice list
[http://distrowatch.com/search.php?defaultinit=SysV#simple](http://distrowatch.com/search.php?defaultinit=SysV#simple)

But...LInux Mint is at the top, so its recent 18.x series forward has systemd, and the 17.x series has init. 
```

inxi -S
System:    Host: toaster Kernel: 3.19.0-32-generic x86_64 (64 bit) Desktop: Cinnamon 2.8.8
           Distro: Linux Mint 17.3 Rosa

jj@toaster ~ $ cat /proc/1/comm
init
```

---

### Post by mikodo on 2017-07-12
The Devaun folks have done away with systemd successfully. One will still use the Debian Repos with it. They even recommend people look at the many distros that have adopted Devaun, that cater to specific use case scenarios: [https://devuan.org/](https://devuan.org/)

---

### Post by rosswmcgee on 2017-07-13
Antergos is real fine,easy to use like instant support if you need it.

---

### Post by vasa1 on 2017-07-13
> **rosswmcgee said:**
> Antergos is real fine,easy to use like instant support if you need it.
What issue of the OP does that address? :???:


Does Antergos _not_ use systemd? I think it does since it's derived from or based upon Arch Linux.

---

### Post by mikewhatever on 2017-07-14
> **TheFu said:**
> ...

IMHO, systemd was a solution needed by 1% of the community.  For the rest of us, the difference between a 10 sec startup and a 30 sec startup just isn't important.  When the udev team stepped away and the systemd team took over that development, we were all screwed.  That stuff is tightly coupled now, going against the Unix philosophy.  SystemD breaks the Unix philosophy is many ways.  That alone is a good enough reason to dislike it.
...


+1, except I don't know who those 1% are, and what they got from systemd. ...and I've seen zero boot time improvements, in fact, quite the opposite is true.

---

### Post by cariboo on 2017-07-14
I may be one of the 1%, I've used journalctl to solve a couple of problems I created myself.It helped speed up the process, instead of me having to comb through the various log files.

---

### Post by #&amp;thj^% on 2017-07-14
> **cariboo said:**
> I may be one of the 1%, I've used journalctl to solve a couple of problems I created myself.It helped speed up the process, instead of me having to comb through the various log files.

1 more for the 1%...Just took me some time to adjust to the changes. And with the timely upgrades in systemd becoming better.:)
I did Look at Devaun for a bit but came back here.

---

### Post by Rocky_Bennett on 2017-07-15
Just to touch on one point that the OP has mentioned, pop-ups in Windows. I have used Windows for a couple of decades, and I have been using Windows 10 for almost three years (I'm a Windows beta tester), and I have never seen any pop-ups, EVER. Zero pop-ups in about 20 years with several dozen different PCs.

 Since I have installed Windows 10 on approx. 34 different PCs for friends and family, zero pop-ups on any of the PCs, EVER. 

Right now I am triple booting with Ubuntu 17.04 and Linux Mint 18.2, and I have zero DNS problems. ...

Rocky Bennett

---

### Post by 1clue on 2017-07-17
> **Rocky_Bennett said:**
> Just to touch on one point that the OP has mentioned, pop-ups in Windows. I have used Windows for a couple of decades, and I have been using Windows 10 for almost three years (I'm a Windows beta tester), and I have never seen any pop-ups, EVER. Zero pop-ups in about 20 years with several dozen different PCs.

 Since I have installed Windows 10 on approx. 34 different PCs for friends and family, zero pop-ups on any of the PCs, EVER. 

Right now I am triple booting with Ubuntu 17.04 and Linux Mint 18.2, and I have zero DNS problems. ...

Rocky Bennett

Rocky,

How many of these PCs are off-the-shelf consumer PCs and how many use a pure Microsoft installer, and how many are a custom corporate build?

I don't really use Windows, but have to maintain a VM for testing purposes since pretty much all of my company's customers use Windows. I always use a Microsoft VM, never accepting something from Walmart or any pre-built home PC vendor-supplied image. I haven't had any real problem with pop-ups or DNS issues either.

My wife, on the other hand, has a Windows laptop from Walmart and it has tons of problems. The freeware and adware they pack those systems full of is the real problem here.

---

### Post by Rocky_Bennett on 2017-07-17
> **1clue said:**
> Rocky,

How many of these PCs are off-the-shelf consumer PCs and how many use a pure Microsoft installer, and how many are a custom corporate build?

I don't really use Windows, but have to maintain a VM for testing purposes since pretty much all of my company's customers use Windows. I always use a Microsoft VM, never accepting something from Walmart or any pre-built home PC vendor-supplied image. I haven't had any real problem with pop-ups or DNS issues either.

My wife, on the other hand, has a Windows laptop from Walmart and it has tons of problems. The freeware and adware they pack those systems full of is the real problem here.



Most of the PCs are simple laptops from HP and or Dell, but I have done the custom install myself. I believe that you are right concerning an off-the-shelf PC with bloatware containing pop-ups, but from reading the OP's comments it would seem that he is at the level to perform a custom install.

But again, I do agree with you regarding an off-the-shelf PC, yes they probable do have pop-ups.

---

### Post by mikewhatever on 2017-07-18
> **Rocky_Bennett said:**
> Most of the PCs are simple laptops from HP and or Dell, but I have done the custom install myself. I believe that you are right concerning an off-the-shelf PC with bloatware containing pop-ups, but from reading the OP's comments it would seem that he is at the level to perform a custom install.

But again, I do agree with you regarding an off-the-shelf PC, yes they probable do have pop-ups.

Well, that's a step forward, and now, how about DNS?
Wouldn't you agree there were reports of DNS problems around Zesty release date? 
Wouldn't you agree it was no OP's fault  that he was affected?

[https://ubuntuforums.org/showthread.php?t=2356729](https://ubuntuforums.org/showthread.php?t=2356729)
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1650877](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1650877)

---

### Post by Rocky_Bennett on 2017-07-18
True enough on that. But re-reading the OP's initial post it seems again, like the way he described his experience that he was competent enough to work through that little issue as well.

I might be reading more into his statements than he intended.

---

### Post by poorguy on 2017-07-18
I cut teeth on Ubuntu 14,04 and at present date I use Lubuntu 16.04 which works well.
Most all of my desktops are ten year old computers and where Ubuntu wouldn't work Linux Mint 18 Sarah Xfce has without any problems.
Give Linux Mint 18 Sarah Xfce a try for some reason it works without problems where Ubuntu hasn't.
The is based on my own use on my own computers.

Linux Mint 18 Sarah Xfce

[https://www.linuxmint.com/release.php?id=27](https://www.linuxmint.com/release.php?id=27)

---

### Post by mc4man on 2017-07-18
> **mikewhatever said:**
> Well, that's a step forward, and now, how about DNS?
Wouldn't you agree there were reports of DNS problems around Zesty release date? 
Wouldn't you agree it was no OP's fault  that he was affected?

[https://ubuntuforums.org/showthread.php?t=2356729](https://ubuntuforums.org/showthread.php?t=2356729)
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1650877](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1650877)
Clearly there were, 17.04 actually released broken for many. (- you would have had one opportunity to upgrade systemd* before losing internet access.
Ubuntu was too wrapped up in their convergence nonsense the last couple of years to give due diligence to what they were releasing to actual users.
One 17.04 bug that affected many was here, noting it never made the release image, (- an admitted mistake the bug fixed though other bug reports about such issues were filed **4+** months prior to release - 
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1682499](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1682499)

Edit: it didn't even make the release notes..

---

### Post by shantiq on 2017-07-22
> **montag dp said:**
> If you're sure your problem is related to systemd, there are other Linux distros without it. Slackware comes to mind. It's not as pointy-clicky as Ubuntu, but if you could set up Mandrake Linux in 2003, I'm sure you will have no trouble with Slackware today. It's also rock-stable and with no nonsense included. Anyway, it would be worth trying something without systemd before making the much more annoying and disruptive switch back to Windows.

+1
yes running back to The Great Vaccinator's highly surveilled wares seems like really giving up like a man being caught out by the tide running in the wrong direction towards the sea and not the beach ...  I installed Slackware on my older [changed at Christmas last] computer and was fearful of the level of competence that would be required to even install basic software; but in 2017 they have a package installer called [Sbopkg]("https://www.sbopkg.org/docs.php") which is so easy to use a 10-year-old could manage and ALL software i can think of is there it seems

So do not run away to The Big Bad Wolf ...   go deeper into Linux not back to "rubbish" ...   when I changed to new box at Christmas it had Windows 10 so I thought let us be open-minded and try it ....    when I saw how long it took to load up I wiped it all out ... maybe you forgot how bad it is ....   go Linux deeper in not out would be my advice here

---

### Post by Finston on 2017-08-03
Hi,

Try Zorin 12.1 Ultimate (~£15) - its based on Ubuntu 16.04 LTS, so is supported till 2021 - and has free Zorin developer's support.

It is more Windows like, out of the box (I found installing it from a DVD best) - but can simulate OS and Mac layouts, if you wish.

It comes with great software and has a simple user support group (not quite so many sections as on here - needles and haystacks comes to mind).


I find it more straightforward to use than Ubuntu - but, of course - it is Ubuntu!.

---

### Post by oldos2er on 2017-08-03
Zorin &#8800; Ubuntu

Thread begun with a drive-by post closed.

---

