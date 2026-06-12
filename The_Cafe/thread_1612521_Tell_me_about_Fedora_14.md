---
title: "Tell me about Fedora 14"
date: 2010-11-03
forum: The Cafe
---

### Post by t0p on 2010-11-03
Because of Ubuntu's plan to use Unity on the desktop, and some other stuff Shuttleworth mentioned in his keynote, I am thinking about installing Fedora on one of my machines (this after 5 years of Ubuntu use... that Unity thing has peeved me no end).

Anyway, after reading a few good reports about Fedora, I am at this very minute downloading the Fedora 14 .iso.  But, apart from what I've read, I know very little about Fedora, especially in comparison with Ubuntu (the only other Linux distro I have any serious knowledge of).

So, I'm hoping someone here might enlighten me about Fedora: what it's lke, how it compares to Ubuntu, and all the rest of it.  I know Fedora is sort of based on Red Hat, and it uses the rpm system of installing software... but how does this all compare?

All input received gratefully: positive and negative feedback are equally welcome.  I'm going to stick the Fedora .iso on a usb stick and run it in live sessions for a while, to see if the UI etc is what I want.  But live sessions don't tell the whole story.  And the rpm installation system - how does that compare to debs?  Favourable?  Not favourable?  And everything else too: I know nothing!!

Cheers.

---

### Post by kaldor on 2010-11-03
> **t0p said:**
> Because of Ubuntu's plan to use Unity on the desktop, and some other stuff Shuttleworth mentioned in his keynote, I am thinking about installing Fedora on one of my machines (this after 5 years of Ubuntu use... that Unity thing has peeved me no end).


Ever hear of apt-get? Or Mint? 

Fedora's good. But be careful; it does have a slightly different layout from Ubuntu's desktop.

---

### Post by Simian Man on 2010-11-03
They both use Gnome as the default environment, so most things will be pretty much the same.  Package management is the biggest difference.  RPM is roughly the equivalent of dpgkg.  You likely don't use dpkg on Ubuntu too often, and likewise won't use rpm too much on Fedora.

The command-line package manager on Fedora is yum, which I find superior to apt* on Ubuntu.  You can see the yum equivalents of apt* commands [here]("https://wiki.archlinux.org/index.php/Pacman_Rosetta").  The GUI package manager is pretty much comparable to that of Ubuntu.

The thing that might give you trouble is that Fedora doesn't include proprietary codecs or drivers in their repositories, so you will need to get them from [RPM Fusion]("http://rpmfusion.org/").

---

### Post by smellyman on 2010-11-03
Well Gnome 3 will be the new Gnome shell so Unity may be the better option....we will know in 6 months

---

### Post by DZ* on 2010-11-03
> **t0p said:**
> I'm going to stick the Fedora .iso on a usb stick and run it in live sessions for a while, to see if the UI etc is what I want.  But live sessions don't tell the whole story.  And the rpm installation system - how does that compare to debs?  Favourable?  Not favourable?  And everything else too: I know nothing!!

You may want to try GUI front end for the yum installer, called yumex. It's not installed by default, get it as "yum install yumex".

I had some trouble with a full install of F14 to a USB stick. If upon boot it gives you black screen or an error "file not found", stick it in under running Ubuntu, check /boot/grub/grub.conf and make sure that "root" points to hd0,0. You may or may not also have to boot from a liveCD in rescue mode, chroot to the location it will suggest and run "grub-install /dev/sd***" (your stick).

---

### Post by snowpine on 2010-11-03
Fedora and Ubuntu are more similar than different. I predict it will be an easy transition, and you will be happy with the change. :)

For your "non-free" needs check out RPM Fusion or if you want something really simple, EasyLife.

The relationship between Fedora and Red Hat is that Fedora is the "public testing ground" for what eventually becomes Red Hat Enterprise Linux. Fedora is free (as in "costs nothing") and Red Hat is paid subscription. Because of this relationship, Fedora is somewhat "bleeding edge" and the support period is shorter than Ubuntu's (only 13 months with no LTS option, since Red Hat is basically "Fedora LTS"). If you find Fedora  14 a little too "cutting edge" for you, you can actually get a pretty stable experience by staying one release behind (I still have Fedora 13 on my netbook since it ain't broke).

"yum" is awesome, very easy to use ("yum install firefox" for example). Fedora is a very clean and well-engineered distro, well worth taking a look. According to Distrowatch it is consistently in the top 3, with good reason I would argue. Again, the similarities with Ubuntu are greater than the differences.

---

### Post by SeijiSensei on 2010-11-03
Fedora (and all other RedHat-flavored distros) have an active root user account with a separate password.  To undertake root activities in a shell, you need to use the "su" command and enter the root password.  You can convert to Ubuntu's sudo method by deleting the root password from /etc/passwd and making appropriate changes to /etc/sudoers.  

I have the opposite view on yum vs. apt as does Simian Man.  I've found apt much faster than yum, and much better than yum at resolving dependencies if third-party repositories are involved.  I haven't used Fedora in a couple of years now, but I have CentOS 5.5 machines that use yum.  I find it much slower than apt-get.

Fedora won't hold your hand about non-free packages.  You'll need to add the RPMFusion repos and install proprietary items from there.  Usually a few key packages like smplayer, kaffeine, and amarok will bring along a lot of the required binaries and codecs without any extra searching.  If you use a proprietary driver like the one from NVIDIA, you'll need to get it from RPMFusion as well.

I'm a KDE user who has been on Ubuntu as a desktop for two years now.  Kubuntu has generally been a decent distribution for me, but it still sometimes feels like a neglected stepchild.  I'm going to put Fedora 14 with KDE into the empty partition on my Kubuntu 10.10 box and see how it fares.

---

### Post by ubunterooster on 2010-11-03
> **kaldor said:**
> Ever hear of apt-get? Or [COLOR=Lime]Mint[/COLOR]? 

Fedora's good. But be careful; it does have a slightly different layout from Ubuntu's desktop.
Fedora feels more professional and less friendly, IMO

PS: try [COLOR=Lime]Mint[/COLOR]

---

### Post by Simian Man on 2010-11-03
> **SeijiSensei said:**
> Fedora (and all other RedHat-flavored distros) have an active root user account with a separate password.  To undertake root activities in a shell, you need to use the "su" command and enter the root password.  You can convert to Ubuntu's sudo method by deleting the root password from /etc/passwd and making appropriate changes to /etc/sudoers.
I don't recommend deleting the root password, there is no harm of having one, even if you use sudo.  If you do, make sure you do so AFTER enabling sudo :).

> **SeijiSensei said:**
> I have the opposite view on yum vs. apt as does Simian Man.  I've found apt much faster than yum, and much better than yum at resolving dependencies if third-party repositories are involved.  I haven't used Fedora in a couple of years now, but I have CentOS 5.5 machines that use yum.  I find it much slower than apt-get.
apt is a bit faster at resolving the dependencies, but the fact that yum downloads only the delta-rpms which are much smaller than full packages, makes it a lot faster at updating than apt.  The main reason I prefer yum is the simpler, more consistent interface though.

I haven't had problems with yum messing up repositories since the consolidation of RPM Fusion.  Before this there were several 3rd party repos that would have conflicting packages in them which made it impossible for yum to resolve.

---

### Post by SeijiSensei on 2010-11-03
> **Simian Man said:**
> I don't recommend deleting the root password, there is no harm of having one, even if you use sudo.  If you do, make sure you do so AFTER enabling sudo :).

I only mentioned it if the OP wanted to maintain the "Ubuntu way" after installing Fedora.  I'll admit to having added a root password to an Ubuntu installation from time to time.

> I haven't had problems with yum messing up repositories since the consolidation of RPM Fusion.  Before this there were several 3rd party repos that would have conflicting packages in them which made it impossible for yum to resolve.

That's good to hear.  I still encounter this problem from time to time on CentOS 5.5 servers.  It's especially annoying when the only conflicts are man pages, and yum refuses to install.

---

### Post by SlugSlug on 2010-11-03
> **Simian Man said:**
> 
The command-line package manager on Fedora is yum, which I find superior to apt* on Ubuntu.  You can see the yum equivalents of apt* commands [here]("https://wiki.archlinux.org/index.php/Pacman_Rosetta"). 

Thats a nice link - thanks, but is it true there is no apt-get autoremove (or autoclean)  option in Fedora??

---

### Post by Dragonbite on 2010-11-03
> **t0p said:**
> Because of Ubuntu's plan to use Unity on the desktop, and some other stuff Shuttleworth mentioned in his keynote, I am thinking about installing Fedora on one of my machines (this after 5 years of Ubuntu use... that Unity thing has peeved me no end).

Wuss. ;)

So they are doing something you don't like so you'll take your ball and go home?

I'm using Fedora because it handles my Intel video chip and Broadcom wireless card out-of-the-box, but otherwise there is little difference for the most part.

Read up on restricted formats for playing MP3s and the like.

---

### Post by Ctrl-Alt-F1 on 2010-11-03
> **Dragonbite said:**
> Wuss. ;)

So they are doing something you don't like so you'll take your ball and go home?

Why not?  I didn't realize that being manly included doing what everyone else wants you to do.

Fedora is great operating system.  It takes a little more fine tuning than does Ubuntu but I've had higher yields as a result too.  For example Fedora supported my laptop entirely including my obscure brand webcam ages before Ubuntu did.

I switch back and forth between the two fairly often.  There is not that much different between them but I like the way that Ubuntu handles proprietary drivers a lot better.

---

### Post by snowpine on 2010-11-03
I also have had a few dependency problems in CentOS 5.x, specifically when I mix rpmforge and epel repos. But then again Ubuntu will break too if you mix repos indiscriminantly... 

Never had that problem with Fedora; RPM Fusion has everything extra I need/want.

ps I finished downloading Fedora 14 and I am pleased to report that the problem I had with the Beta in Virtualbox seems to be fixed. :)

---

### Post by Spice Weasel on 2010-11-03
> **SlugSlug said:**
> Thats a nice link - thanks, but is it true there is no apt-get autoremove (or autoclean)  option in Fedora??

There is. It's just clean.

---

### Post by davidvandoren on 2010-11-03
To make your live easier with flash, java, virtualbox ,codecs, fonts, etc you can use the script from Dangermouse autoten [http://forums.fedoraforum.org/showthread.php?t=171660](http://forums.fedoraforum.org/showthread.php?t=171660)

NVIDIA proprietary driver guide is here [http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

---

### Post by JDShu on 2010-11-03
Two problems I had with Fedora 14 (I went back to Ubuntu this morning),

1. Ndiswrapper is considered non-free, so I had to use rpmfusion to get my wireless to work. The problem is that when Fedora comes out fresh from the oven, the rpmfusion repos do not yet have many of the packages including ndiswrapper.

2. Dropbox installs a currently nonexistent repo, and whenever you try to install something through yum, it 404s as yum tries to get the dropbox repo, and fails.

The lesson I learned is, if you use Non-Free sutff, don't install Fedora the day it comes out.

---

### Post by YeOK on 2010-11-04
> **JDShu said:**
> Two problems I had with Fedora 14 (I went back to Ubuntu this morning),

1. Ndiswrapper is considered non-free, so I had to use rpmfusion to get my wireless to work. The problem is that when Fedora comes out fresh from the oven, the rpmfusion repos do not yet have many of the packages including ndiswrapper.

2. Dropbox installs a currently nonexistent repo, and whenever you try to install something through yum, it 404s as yum tries to get the dropbox repo, and fails.

The lesson I learned is, if you use Non-Free sutff, don't install Fedora the day it comes out.

Interesting, I updated Fedora yesterday and its updated my Nvidia driver, plus some other none Fedora stuff via preupgrade. I have not had to fix a single thing. Kind of disappointed now TBH. 

Guess its a night with the girlfriend after all.

---

### Post by Dragonbite on 2010-11-05
> **JDShu said:**
> Two problems I had with Fedora 14 (I went back to Ubuntu this morning),

1. Ndiswrapper is considered non-free, so I had to use rpmfusion to get my wireless to work. The problem is that when Fedora comes out fresh from the oven, the rpmfusion repos do not yet have many of the packages including ndiswrapper.

2. Dropbox installs a currently nonexistent repo, and whenever you try to install something through yum, it 404s as yum tries to get the dropbox repo, and fails.

The lesson I learned is, if you use Non-Free sutff, don't install Fedora the day it comes out.

Fedora is slightly more challenging with non-free stuff (though Skype and Flash work for me just fine) and off-the-beaten-path applications since they don't have any PPAs or OBSs to host programs outside of official and a few un-official repositories.

---

### Post by kaldor on 2010-11-05
> **JDShu said:**
> Two problems I had with Fedora 14 (I went back to Ubuntu this morning),

1. Ndiswrapper is considered non-free, so I had to use rpmfusion to get my wireless to work. The problem is that when Fedora comes out fresh from the oven, the rpmfusion repos do not yet have many of the packages including ndiswrapper.

2. Dropbox installs a currently nonexistent repo, and whenever you try to install something through yum, it 404s as yum tries to get the dropbox repo, and fails.

The lesson I learned is, if you use Non-Free sutff, don't install Fedora the day it comes out.

If you want a trouble-free experience, don't install Fedora on the first day :)

I had numerous issues. I'll wait a while.

---

### Post by t0p on 2010-11-05
Thanks to everyone who responded to my query.

I've now downloaded the Fedora 14 .iso but haven't done anything with it yet.  I haven't decided whether to put it on a usb stick or give it a go in VirtualBox.  I'm ever so indecisive, me.

---

### Post by Spice Weasel on 2010-11-05
Strange. I had no problems with non free stuff around one week before the release.

Maybe Feddy just hates you guys. :P

---

### Post by ubunterooster on 2010-11-05
> **t0p said:**
> Thanks to everyone who responded to my query.

I've now downloaded the Fedora 14 .iso but haven't done anything with it yet.  I haven't decided whether to put it on a usb stick or give it a go in VirtualBox.  I'm ever so indecisive, me.
Vbox, then you won't need to reboot

---

### Post by HermanAB on 2010-11-06
Linux is Linux is Linux...

The better you know Linux, the less important the differences between the distros are.  Debian and Redhat use different initialization methods, so the difference amounts to about 30 seconds at startup and if you only reboot once in 3 years, then it is infinitesimal.

---

### Post by I'mGeorge on 2010-11-06
I've tried Fedora a year ago and I wasn't really happy with it, after a major system upgrade it becomes kinda laggy. It has a lot of interesting features but for me stability it's crucial so I left it by the time fedora got to leonidas.

You have to consider that Fedora it's actually the testing environment for RHEL, so many things won't work as smooth as they should to. At least this it's my opinion.

---

### Post by I'mGeorge on 2010-11-06
> **HermanAB said:**
> Linux is Linux is Linux...

The better you know Linux, the less important the differences between the distros are.  Debian and Redhat use different initialization methods, so the difference amounts to about 30 seconds at startup and if you only reboot once in 3 years, then it is infinitesimal.

That's so true.

---

### Post by NCLI on 2010-11-06
My experience with Fedora has hardly been positive. While Ubuntu usually contains cutting-edge software at release, AKA the latest and greatest, but still stable, I feel that Fedora focuses way more on features over stability, so much so that I'd say a final Fedora release feels like an Ubuntu beta or late alpha.

---

### Post by linux-hack on 2010-11-06
Personally I find Fedora rely fast and more stable then Ubuntu. Still the apt-get system is better then the yum, but you can always install it on fedora too. But you can still take a look at Debian.. The stability of this system has nothing to prove any more. Or symplay linux mint also.. But it is good to use a lot of distros and get an idea of what is out there. Once you'v used linux you can always use it no mater the distro that you choose... There are slight diferences yes but the essential is always the same

---

### Post by mkarl on 2010-11-06
Well, my experiences echo much of the above replies.  I found Fedora pretty great, my main gripe being that there was a lot less community focused around it (less articles dealing specifically with it - less forums post asking for help with it), in comparison to Ubuntu, although I may just have struggled with this because I was fairly new to it.  

With regards to the RPM, I found that Fedora offered a great deal of packages, and all install in a very similar (and just as easy) way than .debs.  

Karl :)

---

### Post by Stan_1936 on 2010-11-06
> **NCLI said:**
> .... a final Fedora release feels like an Ubuntu beta or late alpha.

Oh yuck! That sounds horrible.

---

### Post by Spice Weasel on 2010-11-07
> **Stan_1936 said:**
> Oh yuck! That sounds horrible.

Fortunately, it's not true for a lot of people.

ymmv.

---

### Post by cprofitt on 2010-11-07
I freaked out a bit when they moved the buttons to the left...

I found out it didn't matter once I tried it... and I had the option to change it.

Why leave Ubuntu because of Unity? I would wait to try it... and if I did not like it I would just install Gnome.

To be honest -- Ubuntu is more than just an OS. Its a community. It is a community that far and away is better than the other Linux communities I have experienced.

---

### Post by simpleblue on 2010-11-07
> **NCLI said:**
> I'd say a final Fedora release feels like an Ubuntu beta or late alpha.

I found that Fedora 14 ran excellent. Evolution loads email MUCH faster and the entire notification system all finally works. The default window sizing on many of the programs in Ubuntu were so that the windows went off the page, making it difficult, or impossible to fill setup info out and run programs. Gwibber is one example.

Suspend/Hibernate (one or the other, not sure which) both work in F14, and didn't in Ubuntu, unless it got fixed.

And the rest just seems to work.

---

### Post by Zlatan on 2010-11-07
ubuntu>fedora because:
[LIST=1]
[*]deb
[*]proprietary drivers
[/LIST]

---

### Post by simpleblue on 2010-11-07
> **Zlatan said:**
> ubuntu>fedora because:
[LIST=1]
[*]deb
[*]proprietary drivers
[/LIST]

Agree with the deb.

I like the way they only use free software. It gives YOU the choice to be fully free, or add on proprietary stuff. If they just offered prop drivers in the box then nobody would be inspired to make opensource drivers.

---

### Post by NCLI on 2010-11-07
To everyone who quoted me:
What I posted was my personal impression of Fedora, which I've tried several times, most recently Fedora 13. YMMV.

BTW, I think [the Linux Action Show has an awesome Fedora 14 review]("http://www.youtube.com/watch?v=gxhEkeO3TJY"), which pretty much matches my general impression of the earlier releases. The review begins ~00:34:00.

---

### Post by NightwishFan on 2010-11-07
To those that stated the differences between distributions are slim, thanks. The main differences are in community and release schedules, and sometimes a default focus. Also in package management.

---

### Post by Spice Weasel on 2010-11-08
Why all of the hat e on RPM? Isn't it almost the same as deb/dpkg?


[LIST=1]
[*]Gives you the choice of apt-get, aptitude, yum as well as urpmi.
[*]Is a community project.
[*]More universal - part of the Linux Standard Base.
[*]PackageKit works for RPM.
[*]Synaptic works for RPM.
[*]Installs packages and the frontends handle dependencies.
[/LIST]
Whereas for deb/dpkg:


[LIST=1]
[*]Gives you those choice of apt-get or aptitude for console frontends (there's probably more that I haven't heard of).
[*]Is managed by Debian and built for Debian.
[*]Slightly more available.
[*]PackageKit also works for deb.
[*]Synaptic also works for deb.
[*]Installs packages and the frontends handle dependencies.
[/LIST]
I just use whatever comes with the distribution.
 
Also, I've just realised that dpkg is available in the Fedora repository. :P

---

### Post by I'mGeorge on 2010-11-08
Fedora it's some kind of a testing environment for RHEL, and really feels like it. Unpolished graphics, I know it struggles to look clean but for me just looks neglected, small bugs that might make you think Fedora it's for pros. Common an intermediate linux user could easily deal with them, so it's all about them being annoying. RHEL on the other hand, well I pick up my [COLOR="Red"]red hat[/COLOR] in front of it. I still remember those days back in 2003 when Red Hat was one stylish popular distro. Well anyway now you have to pay for it but in my opinion deserves all the money. But as for fedora really don't bother with it, there are other distros that are as rich as Fedora in applications and they also have a far more improved functionality ,stability not to mention the aspects regarding the actual community.

---

### Post by wojox on 2010-11-08
It's crisper, faster, and my new distro of choice.

---

### Post by realzippy on 2010-11-08
> **wojox said:**
> It's crisper, faster, and my new distro of choice.

...so fedoraforum.org will get also 10.2 posts/day?

---

### Post by Dragonbite on 2010-11-08
> **I'mGeorge said:**
> Fedora it's some kind of a testing environment for RHEL, and really feels like it. Unpolished graphics, I know it struggles to look clean but for me just looks neglected, small bugs that might make you think Fedora it's for pros. 

I think that is in part because Fedora focuses on maintaining the upstream (Gnome) and benefitting from it when it is accepted while Ubuntu spends more effort on the downstream (Ubuntu) and then passes things upstream (either Gnome or Debian, not sure which "upstream" they pass things to).

For example, I don't see Fedora releasing with the buttons changed to the left side until Gnome releases with buttons on the left side.

I'm not saying one or the other method is better because Ubuntu, due to their leadership and culture, is able to make tough changes and make it work while others would be strapped by the same community that supports them.  At the same time by being involved in the upstream project you gain the beneift of even more developers (Gnome has developers who use Feodra, openSUSE, Ubuntu, etc...).

---

### Post by Simian Man on 2010-11-08
> **cprofitt said:**
> To be honest -- Ubuntu is more than just an OS. Its a community. It is a community that far and away is better than the other Linux communities I have experienced.
Yeah, I especially like the way that a proprietary company passes down decisions without consultation or input from the community.  Great!  Ubuntu does have the *biggest* Linux community, but it definitley does not have the best.

> **Zlatan said:**
> ubuntu>fedora because:
[LIST=1]
[*]deb
[*]proprietary drivers
[/LIST]
Ubuntu does make proprietary drivers easier to install, but how is deb better than rpm?  So many people say this unthinkingly but give absolutely no reason for it.

> **NCLI said:**
> To everyone who quoted me:
BTW, I think [the Linux Action Show has an awesome Fedora 14 review]("http://www.youtube.com/watch?v=gxhEkeO3TJY"), which pretty much matches my general impression of the earlier releases. The review begins ~00:34:00.

You're welcome to your opinion, but that show was incredibly stupid.  They gave Fedora 14 a pretty terrible review, but the only actual problems they pointed out were: that they mentioned libjpeg-turbo as a feature, and that the installer wasn't spaced in a way they found pleasing.  They talked so disparagingly about it and even suggest it's intenitionally bad to push people to RHEL and that's all they could come up with?  Not to mention that they seem to think they're WAY funnier than they actually are.  Lame.

---

### Post by Ric_NYC on 2010-11-08
I installed it today and I didn't like it.

Not ready for the desktop (average user).

---

### Post by simpleblue on 2010-11-08
> **Simian Man said:**
> [Pertaining to a comment about the Fedora Review on the Linux Action Show]

You're welcome to your opinion, but that show was incredibly stupid.  They gave Fedora 14 a pretty terrible review, but the only actual problems they pointed out were: that they mentioned libjpeg-turbo as a feature, and that the installer wasn't spaced in a way they found pleasing.  They talked so disparagingly about it and even suggest it's intenitionally bad to push people to RHEL and that's all they could come up with?  Not to mention that they seem to think they're WAY funnier than they actually are.  Lame.

I think Chris and Brian (Brian Mostly) want Fedora to be something that it's not. Fedora is a testbed and they are NOT looking for users, they are looking for programmers. Fedora clearly states that this edition was to help programmers get the job done better so they can build better software. Ubuntu invested in clearing bugs last edition, and Fedora invested in making it easier for programmers. Different goals. Different OS's.


> It's crisper, faster, and my new distro of choice.

This is true for me as well.

---

### Post by Dragonbite on 2010-11-08
One thing I found annoying with Fedora was being behind with Mono versions. I think it was 13 was trying to upgrade.

Ubuntu at least has BadgerPorts to get the "latest and greatest" mono, and the individual programs (Banshee, F-Spot) I think has PPAs.

---

### Post by snowpine on 2010-11-08
There is a great interview with the Fedora Project Leader in today's DW Weekly:

[http://distrowatch.com/weekly.php?issue=20101108](http://distrowatch.com/weekly.php?issue=20101108)

Fedora absolutely 100% is targeted as a general-purpose distro (as evidenced by the recent website redesign) and it is inaccurate to call it a "developer only" distro.

---

### Post by oldsoundguy on 2010-11-08
I switched from ATTEMPTING to use a very buggy Fedora, that would not run most of my hardware to Ubuntu, that ran everything OUT OF THE BOX 3 years ago and have not regretted it one iota.
That switch allowed me to put my Windows computer in the corner and only use it for my photography. (If I was a gamer, it would be used for that also .. using a KVM switch.)
I now do everything else using Ubuntu.

Beside the difference in the quality of the distros at the time, there was the forums.  Fedora's common answer was "RTFM NOOB".  That is not allowed on the Ubuntu forum.

---

### Post by Spice Weasel on 2010-11-08
> **oldsoundguy said:**
> Beside the difference in the quality of the distros at the time, there was the forums.  Fedora's common answer was "RTFM NOOB".  That is not allowed on the Ubuntu forum.

Nobody is forcing you to use a specific forum for a specific distribution. You can ask for help on any forum you like and it will apply to almost any distribution.

---

### Post by oldsoundguy on 2010-11-08
> **Spice Weasel said:**
> Nobody is forcing you to use a specific forum for a specific distribution. You can ask for help on any forum you like and it will apply to almost any distribution.

You missed the point entirely.
Point being, the Ubuntu forums are much more user friendly.

---

### Post by NightwishFan on 2010-11-08
Things happen I would not judge either forums. I am sure both are good. As are both distributions.

---

### Post by simpleblue on 2010-11-08
> **snowpine said:**
> There is a great interview with the Fedora Project Leader in today's DW Weekly:

[http://distrowatch.com/weekly.php?issue=20101108](http://distrowatch.com/weekly.php?issue=20101108)

That article you gave me says it right here:

"*In the end the impression I get from Fedora is that it is more a development and testing platform than it is a desktop for your average home user. There is very little multimedia support, no Flash, and (on the live CD) no office suite installed by default and the project maintains a short support cycle (about thirteen months). The project has a more friendly feel to it now than it did six months ago, but it is still targeting the more technically inclined members of the community who don't mind working around the occasional quirk. If you like to stay on the cutting edge without being cut, or if you want to keep up with the technology going into Red Hat, then Fedora 14 is an excellent choice.*"

courtesy of [http://distrowatch.com/weekly.php?issue=20101108](http://distrowatch.com/weekly.php?issue=20101108)

---

### Post by NCLI on 2010-11-09
> **Simian Man said:**
> You're welcome to your opinion, but that show was incredibly stupid.  They gave Fedora 14 a pretty terrible review, but the only actual problems they pointed out were: that they mentioned libjpeg-turbo as a feature, and that the installer wasn't spaced in a way they found pleasing.
I removed the irrelevant parts from your post which was your opinion on their style. 

Anyway, they didn't delve into new feature and differences from other distros that much, but like they said, the differences aren't really that big. What they did do was state their general feelings after using it, which I find way more interesting.

---

### Post by tommy1987 on 2010-11-09
> **ubunterooster said:**
> Fedora feels more professional and less friendly, IMO

PS: try [COLOR=Lime]Mint[/COLOR]

Agree with this comment.

I started out with Ubuntu and moved on to Fedora where I stuck for a few years, I've just moved back to Ubuntu.

---

### Post by Dragonbite on 2010-11-09
Fedora 13 is currently the best working distro on my laptop. Ubuntu 10.04 works second, with some patch or other installed. Ubuntu 10.10 works better than 10.04 out of the box, but now with the patches installed and still not perfect.  OpenSUSE works, until an upgrade makes it go "splat".

Last night I checked for updates on my Fedora box and there were like 57 of them.  When I was done, I noticed I was upgraded to KDE 4.5.2 and everything still works (and works better)!  No need for changing repositories or using additional 3rd party repositories.

So since I have the better KDE (compared to what was previously installed) I am not rushing to change to Fedora 14 and may wait until Fedora 15!

Multimedia works on this as well.  Last week I was using my laptop and a projector to play a safety DVD for a non-profit group my wife and I volunteer for.  Ubuntu 10.04 cannot connect to the projector (external monitor), Ubuntu 10.10 only shows the screen in a 1/4 screen size plus it didn't want to play the DVD correctly (something about a Gstreamer bug).  Fedora 13, though, connected to the projector and played the DVD (which I had copied onto a USB stick) just fine!  Only "hiccup" I got was when the screensaver tried to kick on midway through the video!

Fedora for newbies? It's getting there.
Ubuntu for professionals? It's getting there.
OpenSUSE for .... um....? It's getting there. ;)
Much better than any of them being stagnant!  
:guitar:

---

### Post by beew on 2010-11-20
The F14 live usb created by Fedora's live usb creator doesn't boot. 

Here is a thread in the Fedora forums where someone came up with a work around but only for Windows (mwesten post #9). I would be interested if someone can make it works in Linux
[http://forums.fedoraforum.org/showthread.php?t=253636](http://forums.fedoraforum.org/showthread.php?t=253636)

Unetbootin does work but it doesn't support persistence.

---

### Post by czr114 on 2010-11-20
Fedora is a good distro, but don't install it if you mind an occasional bit of Linux work. As the bleeding edge for RHEL, there are always going to be issues and quirks. Ubuntu is more fire and forget.

One thing Fedora doesn't have is a community as active as Ubuntu's. Given how awkward and unproductive Unity will be, expect Unity-free remixes and good support for other DEs. Ubuntu is an open platform, and it won't be force feeding Unity to anyone the way Microsoft did with the horrible start menu in 7. It may be a misplaced development priority, and a bit of work to replace on a fresh system, but we aren't going to be stuck using it.

---

### Post by rjbl on 2010-11-20
Depends on what you want to do with your computer. If you want to explore its capabilities and have a lot of techno-fun then any Redhat distro will give you years of pleasure. fedora is the Redhat development environment and is a very comprehensive GNU/Linux+Apps+GUI package - fedora 14 is the latest in a long line of Redhat distros, going back a couple of decades.

If you just want to compute, surf, enjoy etc then Ubuntu is about the best personal computing system available today. You don't need to be a geek. It installs easily every time and works flawlessly all the time.

rjbl

---

### Post by rjbl on 2010-11-20
PS I was redhatted until this year; and a Windows pro. I switched to Ubuntu only this year when I finally got fed up with hacking around. Ubuntu is as good as I have ever seen - for my purposes.

rjbl

---

### Post by nm_geo on 2010-11-20
Just now trying both distros and for now Ubuntu 10.04 is more user friendly to noobs like me.  Right now I am running on F14 which I had mucho trouble getting installed on a live USB drive using the recommended Fedora USB installation.  The multi boot installation went ok on the second try and now I have XP3, Ubuntu and F14 all booting off my D620 laptop. 

I am still struggling with fan monitor in F14 through the gnome applet but Ubuntu has it just fine.

The different root su or sudo differences slowed me down too, 

 Both distros are  fast with Ubuntu booting up a little faster for me 20 seconds is pretty danged fast.

My choice is Ubuntu right now, but time and testing may change that.;)

---

### Post by ilovelinux33467 on 2010-11-20
One nice thing you will like about Fedora is its delta updates. When you are doing package updates and you are updating Package X from 1.0 to 1.1 it will only download the difference between the two packages and use that to update instead of downloading the whole package again (e.g. downloading 3MB delta update vs 100MB full update)

---

### Post by nm_geo on 2010-11-20
> **ilovelinux33467 said:**
> One nice thing you will like about Fedora is its delta updates. When you are doing package updates and you are updating Package X from 1.0 to 1.1 it will only download the difference between the two packages and use that to update instead of downloading the whole package again (e.g. downloading 3MB delta update vs 100MB full update)

That is a certainly a better method and time saver.

---

### Post by garvinrick4 on 2010-11-20
If know one has mentioned it if installing Fedora 14 just choose not to install grub at all in anaconda the installation program. Boot into Ubuntu grub2 installation and update grub and os-prober will find Fedora and into grub config she will go. If updating from 13 they have a procedure that will put all new software in .cache and then uses boot to put you into anaconda to install Fedora 14 would not work for me since I did not have a grub-legacy from Fedora. Had to do normal update and remove packages from cache or I was using
like 9 gig in / and only use a 10 gig partition and share /home with all other installs. I cannot quite remember but it was something like pre-installation procedure.
Other than that same as others more of a Unix background for terminal. /etc/sudoers is a bit more complicated, firewall had to be worked with for samba and workgroup, do of course have to get used to rpms and yum with different commands than debian. Lots of little things to install that make rpm's work better it seems. Have an install of Redhat 6 Beta and pretty darn close, Fedora better for me. 
It was enjoyable for me to learn but will not replace Ubuntu as my choice by far.

---

### Post by ilovelinux33467 on 2010-11-20
Also I like the fact that Fedora is bleeding edge. rpm is on par with deb IMHO and personally I haven't seen any advantage of using deb over rpm. Just like the Ubuntu forums I found everyone on the Fedora forums to be very friendly and helpful. I am very happy about the Fedora 14 release and looking forward to Fedora 15. My 2 cents

---

### Post by kvant on 2010-11-20
From my experience (used both):

Fedora is a Mercedes among Linux distros. Loads of tiny bits that are broken in Ubuntu are working perfectly in Fedora. The system is much more responsive. It's all very, so to speak, logical.

Ubuntu is holding your hand a bit more (especially when installing non-free software). But this can all (more or less) be done in Fedora too, but it takes more pain.

The thing that got me back to Ubuntu (among others) is that font rendering is 10000 times better. My eyes were very strained from the way that Firefox etc. were rendering fonts in Fedora (there should be a way to fix it, but I couldn't be bothered after doing many other setup tasks).

There you go.

---

### Post by simpleblue on 2010-11-21
I like Fedora's security out of the box:

Firewall Enabled
SELinux Enabled
Full HD Encryption (just check the box during installation)

This is most important to me.

---

### Post by Ad@m on 2010-11-22
> **kvant said:**
> The thing that got me back to Ubuntu (among others) is that font rendering is 10000 times better. My eyes were very strained from the way that Firefox etc. were rendering fonts in Fedora (there should be a way to fix it, but I couldn't be bothered after doing many other setup tasks).


Here is the fix.

[http://linuxtweaking.blogspot.com/2010/11/fedora-14-how-to-improve-font-rendering.html](http://linuxtweaking.blogspot.com/2010/11/fedora-14-how-to-improve-font-rendering.html)

---

