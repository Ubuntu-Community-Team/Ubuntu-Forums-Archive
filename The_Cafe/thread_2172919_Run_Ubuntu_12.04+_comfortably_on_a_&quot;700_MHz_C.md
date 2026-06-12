---
title: "Run Ubuntu 12.04+ *comfortably* on a &quot;700 MHz CPU with 512 MB RAM&quot;? (=Ubuntu info)"
date: 2013-09-07
forum: The Cafe
---

### Post by sanderj on 2013-09-07
Hi,

Ubuntu's page [https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition) says:

> The Recommended Minimum System Requirements, here, should allow even someone fairly new to installing Ubuntu or Gnu&Linux to easily install a usable system with enough room to be comfortable. A good "rule of thumb" is that machines that could run XP, Vista, Windows 7 or x86 OS X will almost always be a lot faster with Ubuntu even if they are lower-spec than described below. Simply try Ubuntu CD as a LiveCD first to check the hardware works.

Ubuntu Desktop Edition
700 MHz processor (about Intel Celeron or better)
512 MiB RAM (system memory)

IMHO this info is outdated; it might have been true for Ubuntu 10.04, but for the current Ubuntu Desktop version (12.04+), I would recommend 2 GHz with 2GB RAM as a minium to run it comfortably. 
FWIW: I do use Ubuntu 12.04 on a Netbook (1.6 GHz Atom, 1 GB RAM), and technically that works, but not "comfortable". So I'm considering to install Lubuntu on that system.

So: what do you think about the **Recommended** Minimum System Requirements to run Ubuntu 12.04+ **comfortably** for someone fairly new?

---

### Post by carl4926 on 2013-09-07
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_Requirements](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_Requirements)

> [COLOR=#333333][FONT=Ubuntu Beta]The minimum memory requirement for Ubuntu 12.04 is 384 MB of memory for Ubuntu Desktop. [/FONT][/COLOR]But > [COLOR=#333333][FONT=Ubuntu Beta]Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD.[/FONT][/COLOR]

Umm...
I wouldn't like less than 1GB RAM myself

---

### Post by sanderj on 2013-09-07
Yep. And if 512 MB were enough, it makes you wonder why the Ubuntu Edge Phone had 4GB RAM ... ;-) ([http://www.indiegogo.com/projects/ubuntu-edge](http://www.indiegogo.com/projects/ubuntu-edge))

---

### Post by santosh83 on 2013-09-07
> **sanderj said:**
> Hi,

Ubuntu's page [https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition) says:



IMHO this info is outdated; it might have been true for Ubuntu 10.04, but for the current Ubuntu Desktop version (12.04+), I would recommend 2 GHz with 2GB RAM as a minium to run it comfortably. 
FWIW: I do use Ubuntu 12.04 on a Netbook (1.6 GHz Atom, 1 GB RAM), and technically that works, but not "comfortable". So I'm considering to install Lubuntu on that system.

So: what do you think about the **Recommended** Minimum System Requirements to run Ubuntu 12.04+ **comfortably** for someone fairly new?

I am running Ubuntu 10.10 here. The info above may be true "strictly speaking", although I haven't tried out the latest desktop version yet. But that's useless for a newbie cause simply running the system is not what they want. They expect to be able to open and use at least 3 to 4 apps simultaneously and comfortably, and there, anything less than 2 Gb will give a bad experience these days. It's not so much the fault of the base system as all the GUI layers and apps. Firefox or Chrome guzzles memory. I would imagine Unity or KDE to also be memory heavy. OpenOffice would take quite some RAM, as would GIMP, Thunderbird, Adobe PDF Reader and the like... common apps which any newbie will expect to run, and often simultaneously.

I have 1 Gb of RAM here on a 1.6 GHz dual core, and the base 10.10 system (including the GNOME desktop) uses roughly 25% of RAM after a fresh start. But open Firefox and already RAM use is at 65-70%. :-( Maybe one more app, but that's all before swapping starts.

For normal comfortable use of the latest Ubuntu Desktop version these days I'd say go get at least 2 Gb of RAM, and don't even try to run the base system alone without at least 1 Gb.

---

### Post by Bucky Ball on 2013-09-07
If you're running 10.10 and you are online you are running a vulnerable system and running a security risk. But we have told you that already in another thread if memory serves ...

---

### Post by rrnbtter on 2013-09-07
Greetings,
I have Raring running on my wife's Toshiba 10" with Atom dual core 1.6G and 2G RAM. It has the same speed as my 2.16Ghz Laptop with 4Gig of memory. I don't think we have reached critical mass yet. Perhaps Saucy Final will do the job.

---

### Post by santosh83 on 2013-09-07
> **Bucky Ball said:**
> If you're running 10.10 and you are online you are running a vulnerable system and running a security risk. But we have told you that already in another thread if memory serves ...

I know that but the problem is my current hardware (1.6 GHz dual core + 1 Gb RAM, Integrated graphics) is just enough to run 10.10 as it is, and even then I can't have too many heavy apps open at once. At least until I've added one more Gb RAM I don't think I'd get a useful experience from either 12.04 or upwards. I could go the Xubuntu/Lubuntu route, but I decided on staying with 10.10 till I can add RAM and try the latest Unity.

To mitigate risks I've all ports closed, run Firefox with NoScript + Adblock + RequestPolicy, and all plugins disabled, and I don't run s/w like Adobe Reader. With cautious browsing I hope to minimise risks.

---

### Post by ibjsb4 on 2013-09-07
Maybe you would be a good candidate for something new

[http://ubuntuforums.org/showthread.php?t=2172971](http://ubuntuforums.org/showthread.php?t=2172971)

---

### Post by carl4926 on 2013-09-07
> **santosh83 said:**
> I know that but the problem is my current hardware (1.6 GHz dual core + 1 Gb RAM, Integrated graphics) is just enough to run 10.10 as it is, and even then I can't have too many heavy apps open at once. At least until I've added one more Gb RAM I don't think I'd get a useful experience from either 12.04 or upwards. I could go the Xubuntu/Lubuntu route, but I decided on staying with 10.10 till I can add RAM and try the latest Unity.

To mitigate risks I've all ports closed, run Firefox with NoScript + Adblock + RequestPolicy, and all plugins disabled, and I don't run s/w like Adobe Reader. With cautious browsing I hope to minimise risks.

Probably the wrong choice.
I've used Mint Mate where customers are in similar needs as yours.

---

### Post by sudodus on 2013-09-07
See also this post comparing different versions and flavours

[http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12769646#post12769646](http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12769646#post12769646)

---

### Post by Mr.Dunham on 2013-09-07
You guys who are low on RAM should try Xubuntu, it's great for low-end systems and comes with a set of lightweight apps. I still use it from time to time (12.04 with latest updates) on an old Athlon XP 2Ghz w/ 1 Gb RAM. More info on lightweight software here: [http://wiki.xfce.org/recommendedapps](http://wiki.xfce.org/recommendedapps)

---

### Post by santosh83 on 2013-09-08
To all those who replied, thanks! Since Ubuntu shortened the support period to 9 months, there's no point in installing 13.04 now as it's life will be ending in 4 months. So I shall wait a month more and install 13.10 when it comes out. I will go with 'regular' Ubuntu, the one with Unity on Mir, as it's about time I got myself acquainted with the new way to do GUIs. :-)

---

### Post by Bucky Ball on 2013-09-08
Why not the solid 12.04 LTS? Supported until April 2017. Might be easier working with a known entity. If you are intending installing 13.10 on the day of release expect breakages and issues for awhile. You might be lucky, you might not. You can install and start testing it now. Just post any issues in the ***Ubuntu +1*** sub-forum until release.

What I'm saying is by waiting until 13.10 is released might be wasting a bit of time and you are not guaranteed a stable system when it is released (which is why, if you have a spare partition, I would advising sticking it on there now and testing).

Good luck whatever you do.

PS: The rule of thumb used to be to wait two or three months after release til things settled down and most issues were ironed out. For me, kinda pointless with a 9 month cycle and I've only used the LTS releases since 8.04 LTS as my main squeeze (but have four partitions for playthings, naturally).

---

### Post by mikewhatever on 2013-09-08
> **sanderj said:**
> Yep. And if 512 MB were enough, it makes you wonder why the Ubuntu Edge Phone had 4GB RAM ... ;-) ([http://www.indiegogo.com/projects/ubuntu-edge](http://www.indiegogo.com/projects/ubuntu-edge))

Well, Ubuntu Edge was supposed to be the phone of the future, released in 2014 with Android and Ubuntu Phone integration. Apparently, the designers thought it could use more RAM. Mordern RAM is considerably cheeper then SDRAM or DDR tipically found in old machines.
...and, of cause, all of that is irrelevant to the minimal requirements for 12.04.

---

### Post by santosh83 on 2013-09-08
> **Bucky Ball said:**
> Why not the solid 12.04 LTS? Supported until April 2017. Might be easier working with a known entity. If you are intending installing 13.10 on the day of release expect breakages and issues for awhile. You might be lucky, you might not. You can install and start testing it now. Just post any issues in the ***Ubuntu +1*** sub-forum until release.

My long experience with 10.10 since it was released has shown how most of the apps start leaving the system behind after 1 1/2 to 2 years, and although Canonical will provide security fixes and a few important backports till '17, I do want to run the latest apps as well. And besides, recently I did a major separation of all my data from the system HDD to an external one, so I no longer depend on a rock solid system, nor having to shuffle data to DVDs every time I needed to wipe and reinstall. Now my internal HDD is almost purely the OS and programs, so I can afford to get on the "reinstall every X months" bandwagon and try out the latest stuff now! :-D

Having to redo a lot of twiddling and customisations would still be a pain every six months, but I mostly run a vanilla system except for a dozen or so extra apps which I can reinstall within a short while.

> PS: The rule of thumb used to be to wait two or three months after release til things settled down and most issues were ironed out. For me, kinda pointless with a 9 month cycle and I've only used the LTS releases since 8.04 LTS as my main squeeze (but have four partitions for playthings, naturally).

So far I've used Dapper, Jaunty and Meerkat, all installed within days of them being released, and didn't encounter any issues. In fact 10.10 has been rock solid even through a major change of motherboard and most peripherals, and hence I'm still with it. Agree though with the new 9 month gestation I'd be pointless to wait even a day longer than necessary!

If I install the 13.10 beta now, do I've to reinstall when the release happens or it can simply be upgraded? If the latter, then I'll try it out now.

---

### Post by codingman on 2013-09-08
12.04 will run the latest apps. Plus, why not go to 13.04 and then upgrade to 13.10 when it comes out?

---

### Post by Bucky Ball on 2013-09-08
> **santosh83 said:**
> My long experience with 10.10 since it was released has shown how most of the apps start leaving the system behind after 1 1/2 to 2 years ... 

??? 10.10 was only supported for 18 months, so yea, not much would have happened for a long time now ... !

Good luck.

---

### Post by Bucky Ball on 2013-09-08
> **santosh83 said:**
> My long experience with 10.10 since it was released has shown how most of the apps start leaving the system behind after 1 1/2 to 2 years ... 

??? 10.10 was only supported for 18 months, so yea, not much would have happened for a long time now and what you describe is *exactly* what is supposed to happen, what you would expect to happen, and if it didn't happen it would be an anomoly ... ! 

Your long experience with 10.10 is around 18 months too long as support for it finished in April 2012 (which is when 12.04 LTS was released)!

Good luck.

---

### Post by howefield on 2013-09-08
> **santosh83 said:**
> If I install the 13.10 beta now, do I've to reinstall when the release happens or it can simply be upgraded? If the latter, then I'll try it out now.

Keep updating, you'll end up on the finished release.

---

### Post by sudodus on 2013-09-08
> **santosh83 said:**
> 
If I install the 13.10 beta now, do I've to reinstall when the release happens or it can simply be upgraded? If the latter, then I'll try it out now.

No major programs or features should be added from now until the release. It should be mainly bug-fixing etc and artwork. So I think (am almost sure) that you need *not* reinstall 13.10 when released. But you might have an occasional broken system, so keep a *good backup* if your tweaks take a lot of time!

If you can dedicate an old computer 100% to the new system, I suggest that you try the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") with the SaucyBeta1 tarball.

---

### Post by santosh83 on 2013-09-09
> **codingman said:**
> 12.04 will run the latest apps. Plus, why not go to 13.04 and then upgrade to 13.10 when it comes out?

To take just one example, I like to run Flightgear, and searching on packages.ubuntu.com indicates that the Flightgear version in 12.04 is 2.4 while the one in 13.10 is 2.10. Big difference there, and I'm sure this is the case for many other applications as well. There are of course PPAs, but even they slowly start dropping builds for older systems as time goes on, so I'd prefer to start with the latest possible base (Saucy) rather than 12.04. Now that I've separated all my data onto external media I don't mind reinstalling (or upgrading) every 9 months or so.

> **Bucky Ball said:**
> ??? 10.10 was only supported for 18 months, so yea, not much would have happened for a long time now and what you describe is *exactly* what is supposed to happen, what you would expect to happen, and if it didn't happen it would be an anomoly ... ! 

I certainly understand. The bit you replied to was me explaining why I now want to go with the latest (13.10) rather than 12.04. :-)

> **howefield said:**
> Keep updating, you'll end up on the finished release.

> **sudodus said:**
> No major programs or features should be added from now until the release. It should be mainly bug-fixing etc and artwork. So I think (am almost sure) that you need *not* reinstall 13.10 when released. But you might have an occasional broken system, so keep a *good backup* if your tweaks take a lot of time!

If you can dedicate an old computer 100% to the new system, I suggest that you try the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") with the SaucyBeta1 tarball.

Noted! I'll try out the beta as soon as it arrives (26th Sep?)! :-)

---

### Post by sudodus on 2013-09-09
There are already Saucy Beta 1 versions available at
 [http://iso.qa.ubuntu.com/qatracker/milestones/302/builds](http://iso.qa.ubuntu.com/qatracker/milestones/302/builds)
and
[http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/)

You can but need not wait for Saucy Beta 2 :-P

---

### Post by santosh83 on 2013-09-09
> **sudodus said:**
> There are already Saucy Beta 1 versions available at
 [http://iso.qa.ubuntu.com/qatracker/milestones/302/builds](http://iso.qa.ubuntu.com/qatracker/milestones/302/builds)
and
[http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/)
You can but need not wait for Saucy Beta 2 :-P

Okay, in the second link which one of those tarballs is 13.10 with Unity and Mir?

I read somewhere else that a release of 13.10 with Unity hasn't yet been made, as it'll skip the first beta or so...

---

### Post by sudodus on 2013-09-09
> **santosh83 said:**
> Okay, in the second link which one of those tarballs is 13.10 with Unity and Mir?

I read somewhere else that a release of 13.10 with Unity hasn't yet been made, as it'll skip the first beta or so...

You are right.

I am testing Lubuntu, and there is only Lubuntu saucybeta1 in the second link. I thought Unity is included in the Ubuntu beta 1 flavours tested, that are available from the first link, but I checked, and although there are daily builds of standard Ubuntu, there is no beta 1 available. Probably it was not good enough to 'publish'. So if you are not interested in any other flavour, you'd better wait unless you want to take part in the beta testing.

---

