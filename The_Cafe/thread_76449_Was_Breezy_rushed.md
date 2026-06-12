---
title: "Was Breezy rushed?"
date: 2005-10-15
forum: The Cafe
---

### Post by Zotova on 2005-10-15
Maybe I am being unfair has it has only been out a few days... but to me Breezy feels that it was very rushed and was released simply to keep to the deadline.

Before I start I'd like to state I'm using a fresh install of Breezy and also I understand that audio and video support are not in Ubuntu from the start, that isn't my problem.

What is my problem is that the audio and video in particular is awful in Breezy. I've installed all the audio/video packages that I had in Hoary and they simply do not work. When I visit a popular video site such as gamespot.com or bbc.co.uk the streams simply do nothing. They attempt to connect but then the mplayer plugin just states it has stopped. I was using the totem plugin before and that simply stated it didn't have the right codec. I do however have the w32codecs... which my I add, why weren't they available more easily? Would it hurt to make them available via apt-get? Or if there is legal problems at least have some decent how-to so users can install them with ease. At the moment all I have found is unhelpful posts from people saying install a certain plugin but without actually saying which plugin to install! 

Moving on from the video problems, what happened to the lovely Ubuntu login screen? All the fonts are now big and in my opinion ugly. Of course I suppose that is just my opinion but to me it looks a lot less professional looking than the Hoary login screen did. Also, once you login, what happened to the lovely splash screen? It is now some ugly rushed looking thing. Again, that is just my personal taste, but what happened with the font size? The first icon which loads looks like a size 6 and then the next icons text looks like a size 8?! To me that just makes me think it was rushed, silly little bugs like that shouldn't be in the final. 

I would like to say I don't mean to be insulting by saying the artwork is ugly, someone has obviously put time in creating it and I aren't generally attacking that person. I just do feel Hoarys art work was a hell of a lot nicer.

Also, what happened with the boot time? It now takes around a min while my card gets an ip from the dhcp server. Fair enough this has never been a fast process but it didn't take this long in Hoary, 30 secs max.

Another problem I had this morning when turning on to try and get the flippin' video working was that my mouse was very jerky, what did I find? The update program was taking up 32% of the cpu and making my laptop very slow. In the end I had to kill the process. Why are simple things like this happening in Breezy when personally I never had any of these problems with Hoary, to me the only answer I can think of is that Breezy was rushed out the door with a lot of bugs still unfixed.

I won't go on in detail so not to bore, I'll briefly list other problems, or at least what I feel are problems.

#The new add/remove menus, very nice, but very slow to load, at least with the old one you could click advanced as soon as it appeared and the advanced add/remove would them appear - which imho is a lot better to use.

#As far as I can tell gaim 1.50 is still not included, why?, or if it is why haven't you bumped the version to 1.50 to at least put peoples minds at rest? There is no way I'm using 1.15 (I think that was the version I had to un-install from Breezy) when it has numerous security issues.

#Why aren't all the official Ubuntu repositories enabled as default? There are hardly any games, themes etc with the default repositories, if the extra ones are official and supported then why not have the enabled from the go? Makes things easier for newbies and even for experienced users as it is one less thing to do.

Finally I would like to say this isn't just a post to bitch about Ubuntu, I am a bit cranky yes lol as I was up till 3 trying to get the darn video working. I release a lot of hard work has been put in and I don't mean to say you shouldn't have bothered or anything harsh like that. I simply feel from my experience there should have been a RC2 to sort out some of the remaining problems.

Also if anyone does have a real fix for the video problem I'd love to hear it as at the moment the other video threads which are around have been no help what-so-ever.

---

### Post by Synt4x_3rr0r on 2005-10-15
Alot of what you're saying is actually true.
The startup time was the first thing i noticed after installing Breezy for example.
But i think that thay have dona a good job with Breezy after all. It just needs a little fixing and it will be better than Hoary.


About your video problems:
In firefox i use an extension calles "MediaPlayerConnectivity"(search Mozillas pag for extensions and youll find it).
From that plugin i've chosen Xine to be the player for streaming Video and it works grate.

But you need the W32Codecs installed. But you already had those right, so it shouldn't be a prob.

---

### Post by Zotova on 2005-10-15
Thanks for the reply. Well, I have just a few moments a go finally got streaming working in Firefox. It would appear someone gave out a link to a w32codecs package which simply did not work. Once uninstalling that one and installing a different version it has worked.

For future reference and anyone reading this thread I have provided a mirror with the codecs **I found to work.**

I hope these will help someone.

To install do the following:

```
wget http://www.shanghai.me.uk/codecs/w32codecs.deb
dpkg -i w32codecs.deb
```

For DVD.

```
wget http://www.shanghai.me.uk/codecs/dvd.deb
dpkg -i dvd.deb
```

I hope these mirrors are of some use and I will try to keep them up as long as I can.

---

### Post by Synt4x_3rr0r on 2005-10-15
[QUOTE=Zotova]For DVD.

```
wget http://www.shanghai.me.uk/codecs/dvd.deb
dpkg -i dvd.deb
```

I hope these mirrors are of some use and I will try to keep them up as long as I can.[/QUOTE]

Is that for DVD playback or is it something else?
Because if it is for playback i actually found libdvdcss2 when i searched this forum(i think it was).
It came as a .deb file to so it was vary easy to install.

Sorry that i don't remember the link to the .deb but i have the.deb on my computer if you're interrested.

---

### Post by helloyo on 2005-10-15
i agree completely. its nowhere near the standard that hoary set. when i install a distro and i have to fix everything in site, no matter how easy, it leaves a bad taste in my mouth. i had to fix my resolution (xorg.conf), get scroll working on my mouse (dpkg-reconfigure xserver-xorg), get wmv working (downloading codecs from mplayerhq.hu) and a couple other things. how is a newbie going to know how to do those things? i barely know how to do those things. 

i love the concept of a big stable distro that everyone has and uses as a base for everything but this one didn't win me over. i am going to try out mandriva, i will probably be back, but depending on the polish, i may not be.

---

### Post by Zotova on 2005-10-15
[QUOTE=Synt4x_3rr0r]Is that for DVD playback or is it something else?
Because if it is for playback i actually found libdvdcss2 when i searched this forum(i think it was).
It came as a .deb file to so it was vary easy to install.

Sorry that i don't remember the link to the .deb but i have the.deb on my computer if you're interrested.[/QUOTE]

Sorry, yes, that is for dvd playback - I just renamed it for ease.

---

### Post by Synt4x_3rr0r on 2005-10-15
[QUOTE=helloyo]i agree completely. its nowhere near the standard that hoary set. when i install a distro and i have to fix everything in site, no matter how easy, it leaves a bad taste in my mouth. i had to fix my resolution (xorg.conf), get scroll working on my mouse (dpkg-reconfigure xserver-xorg), get wmv working (downloading codecs from mplayerhq.hu) and a couple other things. how is a newbie going to know how to do those things? i barely know how to do those things. 

i love the concept of a big stable distro that everyone has and uses as a base for everything but this one didn't win me over. i am going to try out mandriva, i will probably be back, but depending on the polish, i may not be.[/QUOTE]


Ah, common, If you don't like having to set things up manually then you shouldn't use linux at all.
Ok, I think it should be easier for newbs to, but you can't just switch to Linux and think it will be a walk in the park.
At least not yet. :)

---

### Post by ElVirolo on 2005-10-15
I totally agree ... Many things that worked under Hoary simply don't under Breezy (scanner, printer, webcam, internet connection with static IP)...

---

### Post by GeneralZod on 2005-10-15
I'm not an Ubuntu developer, but I think that Breezy has been a very difficult release for a couple of reasons:

a) Compiler transition - GCC 4.0.x is, I gather, rather more stringent than previous versions, so probably a lot of packages had to be tweaked at the source level to work with it; and most importantly 
b) xorg changes.  The modularisation of xorg sounds like it has been a fairly epic task and for a very long time, Breezy testers had no easily accessible GUI, which probably put a lot of people off testing.

Plus, miscellaneous bits and bobs like definite legal issues over things like libdecss and w32codecs; the transition to Cairo as a GTK back-end; etc. 

I would personally have been happy to wait for an extra fortnight or so while things were being cleared up, especially as a Kubuntu user - a number of Kubuntu-specific issues have cropped up (like the inability to switch to admin user for certain tasks which afflicted Hoary also, and the lack of HAL-awareness) that are pretty close to being show-stoppers, in my humble opinion.

I gather that with Dapper, the focus will be more on getting things polished and bug-free, with as few risky new technologies as possible.  Here's hoping! :D

---

### Post by Sh|fty on 2005-10-15
I guess thats what updates are for :)

I just hope they arnt like the last windows one that reports on your installed programs :rolleyes:

** + Sh|fty**

---

### Post by Zotova on 2005-10-15
Is anyone else having problems with the update manager? It runs and takes about 20-30 cpu making my laptop fan to stay on constantly. I've tried opening it, fiddling with the settings, the only way to stop it is to kill the process.

Reminds me of the awful Windows update :(

---

### Post by brt on 2005-10-15
[QUOTE=Zotova]
#As far as I can tell gaim 1.50 is still not included, why?, or if it is why haven't you bumped the version to 1.50 to at least put peoples minds at rest? There is no way I'm using 1.15 (I think that was the version I had to un-install from Breezy) when it has numerous security issues.
[/QUOTE]

gaim 1.5.0 is included in breezy !
well the version-number may look a bit  strange it says: Version: 1:1.5.0-1ubuntu3

which is NOT 1.1.5 its 1.5.0

---

### Post by Zotova on 2005-10-15
[QUOTE=brt]gaim 1.5.0 is included in breezy !
well the version-number may look a bit  strange it says: Version: 1:1.5.0-1ubuntu3

which is NOT 1.1.5 its 1.5.0[/QUOTE]

Fair enough then, but that raises the issue of why use stipid version numbers like that which confuse people. It was just the same with that firefox cockup where the ubuntu version of firefox couldn't access the mozilla updates because ubuntu had used incorrect version numbers.

---

### Post by krusbjorn on 2005-10-15
[QUOTE=Zotova]Fair enough then, but that raises the issue of why use stipid version numbers like that which confuse people. It was just the same with that firefox cockup where the ubuntu version of firefox couldn't access the mozilla updates because ubuntu had used incorrect version numbers.[/QUOTE]

Most people who want to know which version they have check the about box in preinstalled programs like gaim and firefox. Cant be less confusing than that.

---

### Post by az on 2005-10-15
[QUOTE=Zotova]Is anyone else having problems with the update manager? It runs and takes about 20-30 cpu making my laptop fan to stay on constantly. I've tried opening it, fiddling with the settings, the only way to stop it is to kill the process.

Reminds me of the awful Windows update :([/QUOTE]

Open up a terminal and run
sudo apt-get -f install
and see if that tells you anything.

Then, try
sudo dpkg --clear-avail
sudo apt-get update
and try the update-manager again.  It may be that your package database is screwed up....

---

### Post by Zotova on 2005-10-15
[QUOTE=azz]Open up a terminal and run
sudo apt-get -f install
and see if that tells you anything.

Then, try
sudo dpkg --clear-avail
sudo apt-get update
and try the update-manager again.  It may be that your package database is screwed up....[/QUOTE]

Thanks for the reply. This is what I got:

```
root@sonyvaio:/home/dave# sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@sonyvaio:/home/dave# sudo dpkg --clear-avail
root@sonyvaio:/home/dave# sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Ign http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy-updates Release
Hit http://archive.ubuntu.com breezy/main Packages
Ign http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Fetched 20.2kB in 1s (18.5kB/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com breezy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://security.ubuntu.com breezy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
root@sonyvaio:/home/dave#

```

For the timebeing I've had to uninstall the update manager as it does the same each time and makes the laptop very slow.

---

### Post by shidai.liu on 2005-10-15
> Moving on from the video problems, what happened to the lovely Ubuntu login screen? All the fonts are now big and in my opinion ugly. Of course I suppose that is just my opinion but to me it looks a lot less professional looking than the Hoary login screen did. Also, once you login, what happened to the lovely splash screen? It is now some ugly rushed looking thing. Again, that is just my personal taste, but what happened with the font size? The first icon which loads looks like a size 6 and then the next icons text looks like a size 8?! To me that just makes me think it was rushed, silly little bugs like that shouldn't be in the final.

run `xdpyinfo |grep resolution' in my laptop, I have:
```
resolution:    96x96 dots per inch
```

So the font is perfect for me.

Initially, I have 120x119.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        [COLOR="Red"]DisplaySize     338 211[/COLOR]
        Option          "DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
```

My laptop resoluion is 1280x800, work out displaysize x=1280/96*25.4=338 y=800/96*25.4=211. Adapt this to your computer.

---

### Post by Arktis on 2005-10-15
Was it rushed? Yes. You try the six month release cycle while keeping to the higher ubuntu standards of reorganizing, revamping, and inovating not only the huge ammount of software needed, but the entire process of advancing it forward across the open source world so that the whole of the developers, development processes, and end users benefit. Yes, it's a massive and ambitious undertaking, and I'm quite pleased with the results myself.

Yes, there are problems, yes, the process is a bit rushed, but I think you're missing the big picture. I also realize from personal experience that things like frustration are inevitable, and understandable, so this is by no means a derogatory post.

---

### Post by trey on 2005-10-15
I guess its the standard STFU and RTFM or move on.  Ubuntu is free and sometimes you get what you pay for.  Of the free world, it's defintely topping the list.

Thanks Ubuntu & Canonical.

---

### Post by doclivingston on 2005-10-15
[QUOTE=Zotova]Fair enough then, but that raises the issue of why use stipid version numbers like that which confuse people. It was just the same with that firefox cockup where the ubuntu version of firefox couldn't access the mozilla updates because ubuntu had used incorrect version numbers.[/QUOTE]

The reason for "stupid" version numbers, is that sometimes things are more complex than a simple number can provide.

The firefox version number problem was caused because mozilla  everyone to update to 1.0.4 so that everyone got the security fixes. Ubuntu's firefox was version 1.0.2 with the security fixes - which meant that mozilla wasn't letting you access the site, even though you had a version with the security fixes. When you have version 1.0.2, with security fixes from 1.0.4, what version number is it?

The "1:" in front of gaims version number is called an Epoch; if a package has one of those in it's version number, there is a _very_ good reason for it.

---

### Post by kvidell on 2005-10-15
I don't feel it was rushed but I do feel that is _not_ a full new release.

I do however, also realise that a lot of what's changed is backend only (Xorg, GCC), and a lot of other things the end user may never actually use.

This will, however, allow for spectacular enhancements down the road, which is what I'm excited for.

A lot of the small changes they made have improved my user experience wonderfully.
I really like some of the silly fadey effects, and I also like that bluetooth, wireless, suspend and a few of my laptop's "special features" work(ed) out of the box.
Gnome is also much smoother now. I am however running with "openbox --replace" because I _hate_ metacity.

Anyway... I'm off for Half Moon Bay for the Pumpkin Festival :)
I'll comment more later if I feel the need.
- Kev

---

### Post by doclivingston on 2005-10-15
[QUOTE=Zotova]What is my problem is that the audio and video in particular is awful in Breezy. I've installed all the audio/video packages that I had in Hoary and they simply do not work. When I visit a popular video site such as gamespot.com or bbc.co.uk the streams simply do nothing. They attempt to connect but then the mplayer plugin just states it has stopped. I was using the totem plugin before and that simply stated it didn't have the right codec. I do however have the w32codecs... which my I add, why weren't they available more easily? Would it hurt to make them available via apt-get? Or if there is legal problems at least have some decent how-to so users can install them with ease. At the moment all I have found is unhelpful posts from people saying install a certain plugin but without actually saying which plugin to install! [/quote]

w32codecs isn't in the repository due to legal reasons, which is why it it so hard to install. There can't be an official howto, for the same reasons.

As to the general video problems, what exactly isn't working? totem-gstreame, totem-xine, xine, vlc, mplayer or something else?


[QUOTE=Zotova]#Why aren't all the official Ubuntu repositories enabled as default? There are hardly any games, themes etc with the default repositories, if the extra ones are official and supported then why not have the enabled from the go? Makes things easier for newbies and even for experienced users as it is one less thing to do.[/QUOTE]

Universe is official, but it's not "officially supported". Packages that are in Universe should work, but there is no guarantee that they do - also universe packages don't get security updated post-release.

[QUOTE=Zotova]I simply feel from my experience there should have been a RC2 to sort out some of the remaining problems.[/QUOTE]

Did you file bugs about the problems you are having? If not, it's quite possible that everyone else who had the same problems though "surely someone else will file a bug about it", and no-one did, so the developers didn't know to fix it.

---

### Post by jdong on 2005-10-15
[QUOTE=Zotova]Maybe I am being unfair has it has only been out a few days... but to me Breezy feels that it was very rushed and was released simply to keep to the deadline.
[/quote]
As someone who dwelled in the developer chat rooms for the last several weeks, I can say that it really wasn't rushed in any way.
> 
What is my problem is that the audio and video in particular is awful in Breezy. I've installed all the audio/video packages that I had in Hoary and they simply do not work. 

This really doesn't have much to do with Ubuntu -- blame your 3rd parties.
> 
 I do however have the w32codecs... which my I add, why weren't they available more easily? Would it hurt to make them available via apt-get? Or if there is legal problems at least have some decent how-to so users can install them with ease. At the moment all I have found is unhelpful posts from people saying install a certain plugin but without actually saying which plugin to install! 

Breezy-extras-staging has w32codecs in fetcher format, but still a bit buggy. However, if you'd like to host w32codecs and get 5 cease-and-desist letters in the mail, and your ISP threatening to cut you off, be my guest :) I'll hand Breezy Extras right over to you!
> 
Also, what happened with the boot time? It now takes around a min while my card gets an ip from the dhcp server. Fair enough this has never been a fast process but it didn't take this long in Hoary, 30 secs max.

How long it takes to do a DHCP has no relevance to distro version. ISC DHClient has remained relatively unchanged. On my LAN, it takes less than 2 seconds to get past a DHCP lease.


> 
#The new add/remove menus, very nice, but very slow to load, at least with the old one you could click advanced as soon as it appeared and the advanced add/remove would them appear - which imho is a lot better to use.

Don't use it then. Synaptic Package Manager is still in the System menu.

> 
#As far as I can tell gaim 1.50 is still not included, why?, or if it is why haven't you bumped the version to 1.50 to at least put peoples minds at rest? There is no way I'm using 1.15 (I think that was the version I had to un-install from Breezy) when it has numerous security issues.

(1) Breezy dos have GAIM 1.5.0
(2) No version of GAIM in any release of Ubuntu had vulnerabilities in GAIM. Relevant security patches have been backported and patched. In other words, "1.1.5" really had all the security patches of 1.5.0. Take a look at the Security Announcements.

> 
#Why aren't all the official Ubuntu repositories enabled as default? There are hardly any games, themes etc with the default repositories, if the extra ones are official and supported then why not have the enabled from the go? Makes things easier for newbies and even for experienced users as it is one less thing to do.

Universe/Multiverse represent snapshots of the larger Debian Sid (development debian) repositories, which are official but not supported by Ubuntu. To leave them open would be an insecure-by-default configuration -- largely undesired. Checking two checkboxes resolve this.

> 
I simply feel from my experience there should have been a RC2 to sort out some of the remaining problems.

Did you test RC1 or the Preview? Did you report any problems you had? Developers don't read minds or track beta installs -- we've done our best in trying to find bugs, and we haven't found any outstanding ones prior to release.

---

### Post by larry_steiner on 2005-10-15
Ok.  Lets be fair.  Here comes the rant.....](*,) 

When have you ever done a major Microsoft Windows install and had everything work first time?  Not me.  Remember digging around the web looking for driver upgrades that MS did not install by default?  I do.  And then the annual releases of MS Office and Front Page to keep you current (for a big $ price).  Plus the anti virus upgrades $, the spy upgrades $,  the firewall upgrades $.  The having the system performance degrade and not knowing why.  Finally needing to reinstall the OS and everthing else once or twice a year just to keep it running smooth (more or less).   Oh and don't forget the support....

Last I knew Ubuntu was open source and is provided free of charge.  Same with the non-Unbuntu specific packages.  And the support is great as people do this because they like to not just some turkey in a call center thousands of miles (ok  km too) away.

I think the developers and other workers are doing great.  So....:razz:

---

### Post by mangar on 2005-10-15
combined with the constant crashes I get in Nautilus, OpenGL apps (fglrx),
Mono application (beagle, blam), OpenOffice2 (I use complex BiDi document,
with lots of equations), and the inability to hear music + use skype, and the
rest of the sound related issues, I'm getting a cerain feeling that , well,
Ubuntu sucks like a vacuum cleaner. I get more frustration per minute than any
other (meaning Windows) I ever got.
I know Skype's and fglrx problems are third party related, and the whole
you-get-it-for-free stuff, but whats the bloody point? I get firefox and
Realplayer for free in windows as well, it's the same codebase, but in Windows
it actually works!

---

### Post by Zotova on 2005-10-15
[QUOTE=doclivingston]Ubuntu's firefox was version 1.0.2 with the security fixes - which meant that mozilla wasn't letting you access the site, even though you had a version with the security fixes. When you have version 1.0.2, with security fixes from 1.0.4, what version number is it?[/QUOTE]

1.0.2 was what version it was, Mozilla released a new version it should have been updated instead of releasing a version which simply didn't work with half the mozilla site. Mozilla also have their version numbers for a reason.

[quote=jdong]No version of GAIM in any release of Ubuntu had vulnerabilities in GAIM. Relevant security patches have been backported and patched. In other words, "1.1.5" really had all the security patches of 1.5.0. Take a look at the Security Announcements.[/quote]

As I said in my previous post I was mistaken.

You all seem to be missing the point with the version numbers though. The whole idea of ubuntu is 'linux for human beings'. Which to me says a distro for everyone and not just the mega geeky. Everyday people don't spend their time reading every official annoucement - when they see a security release for firefox, gaim, whatever they want to get it so they are covered. When they decided to patch firefox like they did with 1.0.2 how are non techy people supposed to know that this is actually 1.0.4? How is this user friendly?

[quote=jdong]Did you test RC1 or the Preview? Did you report any problems you had? Developers don't read minds or track beta installs -- we've done our best in trying to find bugs, and we haven't found any outstanding ones prior to release.[/quote]

No I didn't use RC1/Preview. I don't see the relevance at all, I'm using the final  and I'm saying personally I feel it shouldn't be a final, as it is too buggy. I'm not saying the developers didn't work hard, I'm not saying ubuntu is awful bla bla go use some other distro, I'm a ubuntu fan. I just feel there should have been more work before it was released.

[quote=jdong]Don't use it then. Synaptic Package Manager is still in the System menu.[/quote]

How is that kind of attitude going to get anything fixed? It is slow from my experience, it might just be my laptop, fair enough. but if it slow on others it can then be reported to the developers so they can fix it. How is not using something ever going to help progress Ubuntu?

[quote=doclivingston]Did you file bugs about the problems you are having? If not, it's quite possible that everyone else who had the same problems though "surely someone else will file a bug about it", and no-one did, so the developers didn't know to fix it.[/quote]

No I haven't as I'm not 100% sure they are bugs. The point of this thread was to see if other users are in agreement/having the same sort of problems.

[quote=doclivingston]Universe is official, but it's not "officially supported". Packages that are in Universe should work, but there is no guarantee that they do - also universe packages don't get security updated post-release.[/quote]

Well I personally feel this needs to change. I can't see how anyone is expected to get ubuntu up and running with a decent range of programs with out the extra repositories.

[quote=arktis]Was it rushed? Yes. You try the six month release cycle while keeping to the higher ubuntu standards of reorganizing, revamping, and inovating not only the huge ammount of software needed, but the entire process of advancing it forward across the open source world so that the whole of the developers, development processes, and end users benefit. Yes, it's a massive and ambitious undertaking, and I'm quite pleased with the results myself.

Yes, there are problems, yes, the process is a bit rushed, but I think you're missing the big picture. I also realize from personal experience that things like frustration are inevitable, and understandable, so this is by no means a derogatory post.[/quote]

Then maybe that is something which needs to be addressed. If it was rushed then surely dapper drake is going to be rushed as well? DD is going to be up against vista and if people are seeing a buggy ubuntu then they will stay with MS. More developers or maybe change to a 12 month cycle - the later I personally feel would be wise.

---

### Post by Zotova on 2005-10-15
[QUOTE=mangar]combined with the constant crashes I get in Nautilus, OpenGL apps (fglrx),
Mono application (beagle, blam), OpenOffice2 (I use complex BiDi document,
with lots of equations), and the inability to hear music + use skype, and the
rest of the sound related issues, I'm getting a cerain feeling that , well,
Ubuntu sucks like a vacuum cleaner. I get more frustration per minute than any
other (meaning Windows) I ever got.
I know Skype's and fglrx problems are third party related, and the whole
you-get-it-for-free stuff, but whats the bloody point? I get firefox and
Realplayer for free in windows as well, it's the same codebase, but in Windows
it actually works![/QUOTE]

That really does sound like a bad install. Maybe try installing from fresh again and make sure the cd image you downloaded is not damaged.

[QUOTE=larry_steiner]Ok.  Lets be fair.  Here comes the rant.....](*,) 

When have you ever done a major Microsoft Windows install and had everything work first time?  Not me.  Remember digging around the web looking for driver upgrades that MS did not install by default?  I do.  And then the annual releases of MS Office and Front Page to keep you current (for a big $ price).  Plus the anti virus upgrades $, the spy upgrades $,  the firewall upgrades $.  The having the system performance degrade and not knowing why.  Finally needing to reinstall the OS and everthing else once or twice a year just to keep it running smooth (more or less).   Oh and don't forget the support....[/QUOTE]

I wasn't trying to compare Breezy to windows with my first post though. My point was that Breezy in my experience isn't up the what was generally a very high standard with Hoary.

---

### Post by Hikaru79 on 2005-10-15
[QUOTE=Zotova]Thanks for the reply. Well, I have just a few moments a go finally got streaming working in Firefox. It would appear someone gave out a link to a w32codecs package which simply did not work. Once uninstalling that one and installing a different version it has worked.

For future reference and anyone reading this thread I have provided a mirror with the codecs **I found to work.**

I hope these will help someone.

To install do the following:

```
wget http://www.shanghai.me.uk/codecs/w32codecs.deb
dpkg -i w32codecs.deb
```

For DVD.

```
wget http://www.shanghai.me.uk/codecs/dvd.deb
dpkg -i dvd.deb
```

I hope these mirrors are of some use and I will try to keep them up as long as I can.[/QUOTE]

Sorry to hijack the thread a bit, but I'm interested in those two packages you mentioned, but they already seem to be down even though you only posted the link 4 hours ago. I'm getting a 404... is there a typo or something similar?

---

### Post by larry_steiner on 2005-10-15
Well, it works fine for me and cost is not an issue.  It's more just for fun and interest.  I worked on the original 80/80 computers so this is a hoot.

Try Linspire, it's not free but works much like Windows.  

Before you do somthing rash like kill your computer or worse (Kill computers that even remind you of your computer) ...  Install XP, go for a walk outside without any electronics and chill.

---

### Post by Zotova on 2005-10-15
[QUOTE=Hikaru79]Sorry to hijack the thread a bit, but I'm interested in those two packages you mentioned, but they already seem to be down even though you only posted the link 4 hours ago. I'm getting a 404... is there a typo or something similar?[/QUOTE]


Sorry, I had to take them down as I didn't have loads of bandwidth to play with.  There is another thread I've seen them posted in however.

[http://ubuntuforums.org/showpost.php?p=411934&postcount=12](http://ubuntuforums.org/showpost.php?p=411934&postcount=12)

The links manicka gave in that thread work.

[quote=larry_steiner]Try Linspire, it's not free but works much like Windows. [/quote]

I'm not saying ubuntu is awful, I hate it etc etc. I'm saying compared to Hoary I feel Breezy is buggy.

---

### Post by Pekkalainen on 2005-10-15
What has happened with the sound? It is extremely annoying to watch a movie in totem now because the sound lags like crazy! The images appear like a full second before the sound. Mplayer is a little better but it lags there too. Is it maybe a soundbuffer problem?

That is my only annoyance with breezy.

---

### Post by mangar on 2005-10-15
zotova: it's a dist-upgrade from hoary.
I'm not going to do a fresh install. I've got something in the order of 
8gb installed on the linux partition (including Matlab and other commercial apps),
plus other work and project - there's no way in hell I'm going to start from scratch (and please don't give me Windows analogies - that is the reason 
I was tempted to use linux in the first place, and now I've got too much time
invested in it to simply erase it). 
I'm using Ubuntu because it was the first distro that had wifi and udev/hal 
working out of the box, and beacuse it made a promise to make my life as a 
desktop user pleasent. well.



Btw: 
I'm not just complaining and doing nothing. I've stole some bits from 
Automatix and EasyUbuntu, plus other bits and pieces, and composed 
(a la frankenstein) HebUbuntu - an automated script that is supposed 
to fix the problems I've had with Ubuntu so far (it's in a community chat 
thread).
Yet I find some problems unsolveable, and the whole experience frustrating.
(and crap, here goes tomboy again, and with it the whole desktop)

---

### Post by doclivingston on 2005-10-15
[QUOTE=Zotova]1.0.2 was what version it was, Mozilla released a new version it should have been updated instead of releasing a version which simply didn't work with half the mozilla site. Mozilla also have their version numbers for a reason.[/quote]

That would work, except that 1.0.3 and 1.0.4 weren't just security fixes - they also contained changed features. Updating to newer versions that aren't just security releases has problems, because changed features need to receive significant testing before being released as a post-release update. That kind of testing can't happen if there needs to be an updated package to fix important security problems.


[QUOTE=Zotova]You all seem to be missing the point with the version numbers though. The whole idea of ubuntu is 'linux for human beings'. Which to me says a distro for everyone and not just the mega geeky. Everyday people don't spend their time reading every official annoucement - when they see a security release for firefox, gaim, whatever they want to get it so they are covered. When they decided to patch firefox like they did with 1.0.2 how are non techy people supposed to know that this is actually 1.0.4? How is this user friendly?[/quote]

Version numbers are a simple concept used so that "average users" can compare two versions of a program and say which one is better. Problems happen when things aren't that simple.

In the firefox case non-techy people aren't supposed to know it was actually 1.0.4, because it wasn't 1.0.4, it was 1.0.2 plus the security fixes from 1.0.2. There isn't a way to give it a simple version number that "average users" can understand.


Another issue is that most people don't understand version numbers anyway. You've made the extremely common error of confusing 1.5.0 and 1.50. Those two version numbers are completely different, but most people don't realise that or understand why.

---

### Post by larry_steiner on 2005-10-15
Ok.  Enough useless talk from me.    

I still can't get my DVD to play with Totum or Mplayer.  I had good luck with Gxine.  The drivers that I have for windows seem to work fine, I followed the instructions in the official guide under the Help pulldown.  Here are my reposits.  Hope this helps you.  Note the debian-marillat repos was used to install "commercial" codecs, then commented out.  


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

###deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

---

### Post by Zotova on 2005-10-15
[QUOTE=doclivingston]That would work, except that 1.0.3 and 1.0.4 weren't just security fixes - they also contained changed features. Updating to newer versions that aren't just security releases has problems, because changed features need to receive significant testing before being released as a post-release update. That kind of testing can't happen if there needs to be an updated package to fix important security problems.[/quote]

I really fail to see the issue. You can go to the mozilla site and download the latest version. I did that when the whole 1.0.2 issue was happening. I installed without a problem and my computer system didn't blow up or anything like that. The same happened with thunderbird, 1.0.7 was out and after a few days the 1.0.6 I had installed via apt-get hadn't updated. So I uninstalled and installed the 1.0.7 of the mozilla website. Which worked flawlessly. I don't see why someone needs to test a program which has already been tested by mozilla.

> Version numbers are a simple concept used so that "average users" can compare two versions of a program and say which one is better. Problems happen when things aren't that simple.

Things are that simple though, there was a new version of firefox out which had new features and/or security fixes. The latest version should have been available instead of a rehashed 1.0.2. People might not understand version numbers but they do understand that newer versions normally mean more secure computers. When they see that the newer version isn't available they get worried.

[quote=larry_steiner]Ok. Enough useless talk from me.

I still can't get my DVD to play with Totum or Mplayer. I had good luck with Gxine. The drivers that I have for windows seem to work fine, I followed the instructions in the official guide under the Help pulldown. Here are my reposits. Hope this helps you. Note the debian-marillat repos was used to install "commercial" codecs, then commented out.[/quote]

Have you got the dvd drivers installed as well as the w32 ones? I haven't tested a dvd in mine yet... I'll see if it works fine on mine and get back to you.

---

### Post by tageiru on 2005-10-15
[QUOTE=Zotova]I do however have the w32codecs... which my I add, why weren't they available more easily? Would it hurt to make them available via apt-get? Or if there is legal problems at least have some decent how-to so users can install them with ease.[/QUOTE]
Yes it would it could be criminal if ubuntu supplied it with the distribution. Even a document describing how to get them could be illegal in som countries.

If you need such codecs you should use windows.

---

### Post by magomago on 2005-10-15
[QUOTE=Pekkalainen]What has happened with the sound? It is extremely annoying to watch a movie in totem now because the sound lags like crazy! The images appear like a full second before the sound. Mplayer is a little better but it lags there too. Is it maybe a soundbuffer problem?

That is my only annoyance with breezy.[/QUOTE]

I'm sorry to hear :'(  But I've had totally the opposite feeling.  Hoary didn't feel as polished to me.  But Breezy is wonderful, The new Gnome makes things look a lot nicer, and I tend to move to the "big font" themes anyways.  If you really don't like how it looks, just go to gnome-look.org and get one that you do want.  

But before when I had sound issues, now I had none.  Before when totem would never play anything, now it does.    DHCP takes like 5 seconds for me...pretty much the same for Windows.
But at the same time, Luckily I haven't had the issues you have had with update manager, etc.  

Hope it works out for you!

---

### Post by spooky-mac on 2005-10-15
For me, 5.10 seems to be less buggy than 5.04. I think it very much depends on your combination of many different hardware parts. ;) 

After all, no software package is perfect. And not every release can outshine the previous one. There will be advances in some areas and stepbacks in others. You simply have to decide for yourself which tradeoffs you can live with and which ones you cannot live with.

---

### Post by doclivingston on 2005-10-15
[QUOTE=Zotova]I really fail to see the issue. You can go to the mozilla site and download the latest version. I did that when the whole 1.0.2 issue was happening. I installed without a problem and my computer system didn't blow up or anything like that. The same happened with thunderbird, 1.0.7 was out and after a few days the 1.0.6 I had installed via apt-get hadn't updated. So I uninstalled and installed the 1.0.7 of the mozilla website. Which worked flawlessly. I don't see why someone needs to test a program which has already been tested by mozilla.[/quote]

I take it you don't use Epiphany, Liferea or anything else that embeds Gecko. There have been cases of an insufficiently tested firefox package completely breaking everything that uses Firefox's gecko library. Firefox in Ubuntu's package isn't identical to the Firefox provided by Mozilla - and some of those differences can be important.


> Things are that simple though, there was a new version of firefox out which had new features and/or security fixes. The latest version should have been available instead of a rehashed 1.0.2. People might not understand version numbers but they do understand that newer versions normally mean more secure computers. When they see that the newer version isn't available they get worried.

The new features bit is the problem, if there were just security updates then Ubuntu would have uses version 1.0.4. There are issues that I've mentioned with having post-release updates the include new features of significant changes, because although it got testing by an outside group, it hasn't recieved testing in the Ubuntu environment.

---

### Post by xbaez on 2005-10-15
so one question, what is the best way to upgrade to breezy?
via apt-get dist-upgrade
or download the Hoary Ubuntu CD (5.10) and then install them

I want to put and end to this conversation right now
w32codecs were available for Ubuntu in the Ubuntuguide
NO distro will give you w32codecs, (unless you want to pay, which brings the "I rather use windows question")
For me Window$ is like PS2 or Xbox, it's a gaming console (for other people it might be something better)

Other than that  I LOVE ubuntu, because by following the Ubuntu guide and some commercial software it was the only OS that I could do everything (play NFS Underground, EA 2004 games, GTA, Run WindowsXP with VMware, Office XP, Macromedia DrewamWeaver...)

I tried SO Many distros that I'm sick of trying new ones. (RedHat, Mandrake, Debian, Mepis, Fedora... like 10 distros before I used Ubuntu). Belive me, if you want to use Linux, Ubuntu is the best one out there.

Try OpenSuse, no w32codecs there. 
Download the Mandrivia version, no w32codes there (correct me if I'm wrong)

So what's the big issue of installing w32codes from somewere else?

---

### Post by Nasso on 2005-10-15
I think the releases are to close to each other. Each release takes alot of work. Upgrading often gives problems. I dont think the difference between hoary and breezy is that huge, really.

Why 6 months, that is really short! I think 12 months is better. It is still pretty close between releases but not annoyingly close :)

wrote some more about it in this thread.
[http://ubuntuforums.org/showthread.php?t=75953](http://ubuntuforums.org/showthread.php?t=75953)

---

### Post by joelito on 2005-10-15
I dist-upgraded from hoary to breezy during last month without any major issue except for 3d acceleration (wich I don't use anway) as for those codecs, I got them trough third party sarge repositories and enabling the standard sarge(Didn't do that in hoary because  of library dependencies) I also enabled the debian sid source repository just in case I wanted to backport something. Of course, I'm not exactly a total n00b, altough  I did made my research and found the tools and guides I needed to get my PC running (by mixing the guides with my own Ideas to narrow the process down to a couple of steps)

What I think that happened is that many of those who tried breezy in the pre-release versions, actually knew what they needed to workaround many of the little annoyances that newbies report.

---

### Post by agger on 2005-10-15
[QUOTE=helloyo]i agree completely. its nowhere near the standard that hoary set. when i install a distro and i have to fix everything in site, no matter how easy, it leaves a bad taste in my mouth. i had to fix my resolution (xorg.conf), get scroll working on my mouse (dpkg-reconfigure xserver-xorg), get wmv working (downloading codecs from mplayerhq.hu) and a couple other things. how is a newbie going to know how to do those things? i barely know how to do those things. 
[/QUOTE]

My experience is completely different, for what it's worth.

Dist-upgrade failed for me, so I had to do a clean install. After copying my /home in place i went to the Ubuntu guide - [www.ubuntuguide.org](www.ubuntuguide.org) - use it!
- enabled universe and multiverse in my sources.list (you have to do as the
ubuntuguide says, but replace hoary with breezy), and now everything 
works fine: Sound, video, fonts - all in place!

If I'm going to say something bad about the upgrade it is that there's not much of a difference to be *seen*.

---

### Post by Owdy on 2005-10-15
[QUOTE=Zotova]Is anyone else having problems with the update manager? [/QUOTE]
I do, That graphical version doesnt work: [http://ubuntuforums.org/showthread.php?t=74682](http://ubuntuforums.org/showthread.php?t=74682) . In terminal it works.

Oher issue, why wasnt all bugs fixed before release?

---

### Post by pmj on 2005-10-15
[QUOTE=Owdy]I do, That graphical version doesnt work: [http://ubuntuforums.org/showthread.php?t=74682](http://ubuntuforums.org/showthread.php?t=74682) . In terminal it works.

Oher issue, why wasnt all bugs fixed before release?[/QUOTE]
It's impossible to fix ALL bugs, especially those you don't know about.

I see no signs of it being rushed. For me, Breezy has been both faster and more stable than Hoary. That along with many small improvements makes me happy I upgraded.

---

### Post by Owdy on 2005-10-15
I mean reported BUGS.

---

### Post by cowlip on 2005-10-15
I'm finding Breezy quite slow and of course spca5xx crashes everytime, this was known a week before release.

---

### Post by kelsey23 on 2005-10-15
Breezy was VERY rushed, which is why I am switching to Debian soon ;-)

---

### Post by joelito on 2005-10-15
Breezy was VERY rushed, which is why I switched from Debian...

---

### Post by Jvaldezjr on 2005-10-15
My only problem with this new release is that when I installed KDE and log in, I get a soundserver crash.  Its probably not an Ubuntu issue- so I'll have to update or go back to a lower version of KDE.  I also have a problem with Amarok.  It crashes everytime I try to start a mp3.  Again, I dont think that is an ubuntu issue.  The biggest pro for me was the HP PSC support out of the box.  I dont have to compile and install the drivers manually anymore.  Ubuntu is working so far, but I haven't done much because I'm still trying to figure out why Amarok is crashing, and why my sound server crashes upon KDE start.  I hate using GNOME, and no I wont switch to MEPIS.

---

### Post by Leif on 2005-10-15
[QUOTE=Pekkalainen]What has happened with the sound? It is extremely annoying to watch a movie in totem now because the sound lags like crazy! The images appear like a full second before the sound. Mplayer is a little better but it lags there too. Is it maybe a soundbuffer problem?

That is my only annoyance with breezy.[/QUOTE]

have you tried to install totem-xine instead ? I always have problems with gstreamer (the default)

---

### Post by yesplease on 2005-10-15
It is ironic to see that people who complain a lot get a lot of help in their posts.

The first poster is just annoyed because he had a long fight with some software and blames the developers for not being perfect.

Another poster thinks that dist-upgrades every six months is too often. Well, wait another six months before you upgrade.

I dont like this kind of posts, it is unbalanced because breezy solved a number of problems too.

I am very gratefull that so many people work on Ubuntu and provide us with so much. They should get some credit for their work.

---

### Post by Leif on 2005-10-15
[QUOTE=yesplease]It is ironic to see that people who complain a lot get a lot of help in their posts.
[/QUOTE]

it's not really ironic, it's actually a classic tactic, whether they employ it knowingly or not. you can try it too someday if you have a problem so obscure that noone can answer it on the forums. the expanded version includes "linux sucks, microsoft is way better because of X", "you guys are all losers, linux doesn't even do X" and so on. people will start falling over themselves to prove linux doesn't suck.

---

### Post by kaaredyret on 2005-10-15
I think Breezy was rushed. Hoary was running like a dream on this machine. The Breezy preview was a nightmare... update a failure and even a total reinstall a failure.

Now I have been struggling with tons of minor problems that just didnt exist on Hoary, even getting the Really Slick Screensaver to work was a problem (and the reason.. a bug).

Releasing every 6 months is just to often, I think. Nice for us to have something to look foreard to, but I really regret this update. I had nothing but trouble it really wasnt an important update after all.

It really is important to underline that decision makers or ordinary people that hear about Ubuntu can struggle with tons of stupid minor problems just like I did... and get a bad impression.

Even loggin off now is a problem on a fresh install of Breezy... come on man, that is the sort of !"#!"**¤# I hated Windows for.

---

### Post by xbaez on 2005-10-16
[QUOTE=kelsey23]Breezy was VERY rushed, which is why I am switching to Debian soon ;-)[/QUOTE]

Switching to debian, what are you talking about?
Debian doesn't uses Xorg, KDE 3.4.2, nor it has software such as eclipse 3 (it has version 2)

I installed a fresh new copy of Mepis, which is basically a working version of debian (I haven't tried sarge but woody was the ONLY of the 10 distros that I tried that wasn't capable of showing a graphical screen with XFree86)

Apart from that, Debian releases a new distro every 3 year or so, and I read somewere that "25% of the users will have problem upgrading distros"

When I tried Mepis, it had the unstable and testing repositories enabled.
I tried to install kmultimedia-dev and other package and there were dependencies problems. In ubuntu (unless you enable debian repos and start doing what you shouldn't) you see a clean, stable, descent distro, 100% open source like Debian, only that it works ok :)

---

### Post by Zotova on 2005-10-16
[QUOTE=yesplease]It is ironic to see that people who complain a lot get a lot of help in their posts.

The first poster is just annoyed because he had a long fight with some software and blames the developers for not being perfect.[/QUOTE]

I also get annoyed by posts like yours. I talked about some problems and why I feel Breezy should have been delayed. I'm not saying I wanted a 100% bug free Breezy, I know that would never have happened. What I think should have happened is maybe another month tops to iron out some of the remaining bugs. I mean look at the forum there are a handful of sound topics with people who have problems. The flash firefox sound problem is common.

But the attitude from posts likes yours seems to be unless people are praising Breezy they should not post anything. My first post was critical of Breezy yes, but if you actually read it I said that my comments weren't disrespectful of the developers and that I am a great fan of Ubuntu. The aim of my topic is to get the point over that I personally felt that the release should have been delayed a while to fix some final problems and that I hope when DD is released it will be less buggy. With my criticism and the criticism of others I'd hope to see a better DD &#8211; if we all sit here not daring to say  a bad word then improvements would never happen. :roll:

---

### Post by doclivingston on 2005-10-16
[QUOTE=Zotova]What I think should have happened is maybe another month tops to iron out some of the remaining bugs. I mean look at the forum there are a handful of sound topics with people who have problems. The flash firefox sound problem is common.[/quote]

Ubuntu are doing time-based releases approimately every six months, which means they probably wouldn't move the release date by a month unless there were major[0] problems. If they moved away from time-based releases, the decision on when exactly the distro is "ready for release" become much harder.


One option is that they could plan to do releases every seven months, instead of six, but that would have it's own problems:

1) A lot of people start testing the new release N weeks before the final release (such as the preview), and with a longer cycle they will still start testing N weeks before the end. That means that a lot of the bugs that gets shown by wider testing probably won't have any extra time to be fixed

2) Ubuntu is timed to be released approximately one months after the new stable Gnome release. Moving to anything which isn't a multiple of six months means that it will get out of step. That wouldn't be a problem per se, but having them synchronised is nice.


[0] I'm calling the issues you mention minor because a) they only affect a small group of users, and b) people can live without flash sound, etc.

---

### Post by alper_tr on 2005-10-16
Exactly the same idea was on my mind this morning, after spending 2 days with Breezy.

I still love Ubuntu, I totally congratulate the people putting effort on it... However after spending 2 days over it, it gives the taste of a alpha quality software... There are even simple bugs like, not being able to change the keyboard layout(it doenst works on international keyboards.) Somehow dependencies even doesnt feel as safe as it was over Hoary.

No big changes(anything worth to upgrade Breezy) than Hoary. I think before too late Ubuntu Admins rename Breezy stable to Breezy Alpha, and not allow joe users to install it... There are many nice things on it, but really seems unstable..

There is just one good thing, at least thousends of people are testing and encountring bugs... so in a month or something it would get more stable with the updates.

Anyways, all i can say is, we would have been more patient or we would have waited untill it got more stable... hopefully this release and bugs would be a nice experience for us all, and next time everyone would have been more carefull and neath before making such release. Its no shame to release a something later than the deadline...and so much better to release a product which would please everyone/// always like that in businesslife.

---

### Post by jdong on 2005-10-16
Any time new technology is used, there is always the appearance of rushing or unpolishedness. Take Redhat 9 when NPTL was first introduced, or FC4, where the GCC4 migration was done -- there were massive issues when users started adopting these products, which neither was rushed. Even RHEL4 had its share of incompatibilities upon release.

Breezy definitely was a big step up from Hoary, working in the cairo backends and GCC4, etc etc etc. These are definitely necessary changes that we need by Dapper Drake, if we want a fighting chance against Vista (which, no matter how much you hate Windows/MS, has several compelling technological advances).

I think what we'll find in the future is that every few releases, there'll be one (like Dapper) regarded as the MAJOR release, supported for the longest period of time, and the interim releases as 'technology previews' building up to the big release.



I've yet to experience any problems with Breezy, and began using it about a month before the release. As far as switching to Debian, two years down the road it'll really suck using Firefox 1.0.2+debian-patch-number-5000 and Gaim 1.2.1 :)

---

### Post by blu.gecko on 2005-10-16
WOW,

so much input here, Im not sure I want to jump ship yet, always one question on my mind, are they working twards a faster boot process, thats the only thing I like about MS.

blu:confused:

---

### Post by Stormy Eyes on 2005-10-16
[QUOTE=Nasso]Why 6 months, that is really short! I think 12 months is better. It is still pretty close between releases but not annoyingly close :)[/QUOTE]

I think that the six month interval was chosen as a counter to one of the big gripes about mainline Debian: that releases are done at a glacial pace (2-3 years might as well be a geological epoch in terms of Linux development).

---

### Post by Stormy Eyes on 2005-10-16
[QUOTE=blu.gecko]so much input here, Im not sure I want to jump ship yet, always one question on my mind, are they working twards a faster boot process, thats the only thing I like about MS.[/QUOTE]

Microsoft's "faster" boot process is a lie. Sure, you might get a login screen and a desktop faster, but Windows is still loading daemon processes in the background, rendering your quick-booting desktop useless for at least a minute after you've logged in.

---

### Post by aysiu on 2005-10-16
[QUOTE=Stormy Eyes]Microsoft's "faster" boot process is a lie. Sure, you might get a login screen and a desktop faster, but Windows is still loading daemon processes in the background, rendering your quick-booting desktop useless for at least a minute after you've logged in.[/QUOTE] I haven't found this to be true on my desktop. I timed it from selecting the OS at Grub to a workable Firefox (launched and able to use), and Windows XP took 30 seconds; Ubuntu took 45 seconds. I don't know if it's because my computer is somehow customized for XP or if Ubuntu tacked on some extra processes at startup (I did manage to stop Bluetooth from activating at startup), but XP is a bit faster *on my computer*--I can't speak for anyone else.

P.S. I forgot that I tacked on some extra processes at startup, too--I have a few partitions mounted at startup. Do you think that might make 15 seconds of difference?

---

### Post by blu.gecko on 2005-10-16
as far as boot time, I have a 1.5 celeron laptop that loads xp to the screen with no running processes in the background in 25 seconds, ubuntu is a tad slower at this say 70 seconds, MEPIS is WOW fast on loading time, so my question in will they ever do anything about this? or do I need to weed through what I need running in the backgroun or what?

and please dont buy into the fact that I like MS, my wife and the company I consult for are anal about MS only products....

:rolleyes:

---

### Post by jdong on 2005-10-16
Fast boot is relative to how much you load at bootup. I have specialized Ubuntu setups that boot in about 15 seconds on a mid-grade Celeron. Once you load down any OS with a significant number of bootup services, bootup speed suffers.


Fortunately, there are ways of circumventing bootup speeds. First of all, Linux/UNIX are OS'es designed to be left running -- in fact, many housekeeping chores will not run properly unless the system is left on. (Same with Windows XP -- prefetch causes so much hell if the system isn't left on for a few days every month)

Also, Hibernation comes to the rescue -- it works on a surprisingly large portion of mobile systems.

---

### Post by aysiu on 2005-10-16
[QUOTE=blu.gecko]as far as boot time, I have a 1.5 celeron laptop that loads xp to the screen with no running processes in the background in 25 seconds, ubuntu is a tad slower at this say 70 seconds, MEPIS is WOW fast on loading time, so my question in will they ever do anything about this?[/QUOTE] More evidence that it all depends. Mepis takes 90 seconds for me--double the time Ubuntu takes (same machine).

---

### Post by joelito on 2005-10-16
And did anyone noticed the many ports that Mepis opens by default, I mean, why the heck do I need apache to run by default on a desktop?

---

### Post by burningbed on 2005-10-16
[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")
This is has everything you need to get audio, video, java, etc. working.

---

### Post by Deusiah on 2005-10-16
I feel Zotova made some very good points. I had more trouble setting up thing in Breezy than in Hoary, having said that I think it's only the Multimedia side of Breezy which has given me trouble apart from a few packages like Eclipse which don't work fresh from synaptic.

Breezy is still a great distro and Ubuntu is still the best Linux distro I have used to date. If it wasn't for Ubuntu I'd probably still be using Windows.

---

### Post by kaaredyret on 2005-10-16
[QUOTE=yesplease]It is ironic to see that people who complain a lot get a lot of help in their posts.

The first poster is just annoyed because he had a long fight with some software and blames the developers for not being perfect.

Another poster thinks that dist-upgrades every six months is too often. Well, wait another six months before you upgrade.

I dont like this kind of posts, it is unbalanced because breezy solved a number of problems too.

I am very gratefull that so many people work on Ubuntu and provide us with so much. They should get some credit for their work.[/QUOTE]


They do get their credit. But think of all the potential users will less knowledge about Ubuntu, they wont credit anyone for Ubuntu if it doesnt work or simply is a pain to get up and running. They will perhaps run away and we wont even hear about them. 

Every post here I have seen really asked this question with a good intention: to help improve the quality of Breezy. If you dont realize that CRITISISM is an essential cornerstone in development of any kind, then dont get too involved in development. It is just comes with the the territory. Ubuntu is not a religion we must praise, but a product in an early development phase.

Developers make bad decisions too, and we really dont know that this update is troublesome before we try it, do we? I myself juped right into it believing that it would be of the same high quality as Hoary. It simply wasnt... so it is my fault because I updated? Not really. And do you really think that the NEXT update would be as stable as Hoary? The whole issue here is that to reach their goal for any given release, they have to work pretty damn fast. 

Having followed other development processes I just cant imagine that 6 months is enough. In my line of businesses we ALWAYS delay products rather than letting costumers suffer. Chances are, if they suffer, we will suffer too... and starve some day.

I love Ubuntu, recommend it to others, use it myself. But I think Breezy was rushed and no one but the developers made the bugs that I struggled with and no one but them decided that it was ready for release. I just doubt that they can deliever rock solid software to many many many users and configurations every 6 months. I'd rather wait a few more months.

---

### Post by trash on 2005-10-17
[QUOTE=kaaredyret]They do get their credit. But think of all the potential users will less knowledge about Ubuntu, they wont credit anyone for Ubuntu if it doesnt work or simply is a pain to get up and running. They will perhaps run away and we wont even hear about them. 

Every post here I have seen really asked this question with a good intention: to help improve the quality of Breezy. If you dont realize that CRITISISM is an essential cornerstone in development of any kind, then dont get too involved in development. It is just comes with the the territory. Ubuntu is not a religion we must praise, but a product in an early development phase.

Developers make bad decisions too, and we really dont know that this update is troublesome before we try it, do we? I myself juped right into it believing that it would be of the same high quality as Hoary. It simply wasnt... so it is my fault because I updated? Not really. And do you really think that the NEXT update would be as stable as Hoary? The whole issue here is that to reach their goal for any given release, they have to work pretty damn fast. 

Having followed other development processes I just cant imagine that 6 months is enough. In my line of businesses we ALWAYS delay products rather than letting costumers suffer. Chances are, if they suffer, we will suffer too... and starve some day.

I love Ubuntu, recommend it to others, use it myself. But I think Breezy was rushed and no one but the developers made the bugs that I struggled with and no one but them decided that it was ready for release. I just doubt that they can deliever rock solid software to many many many users and configurations every 6 months. I'd rather wait a few more months.[/QUOTE]


ever since Hoary, I for some reason have been thinking 6 months is way too rushed... personally i couldn't work under that kind of pressure. I also don't think the majority of users want to go though this every 6 months(could be wrong)... not that anybody is forced to but lets face it, newer = better no?
Anyway, I also think 8 months would be way better

---

### Post by flyingbrass on 2005-10-17
IMO, something needs to change.  When the RC came out was it really a RC or merely "Final -7"?  I'm not terribly familiar with the development process, but from what I've seen in most scenarios the first RC is released when most bugs have been mashed.  Test it for awhile.  Then RC2.  Test again.  Then RC3, etc. if necessary.  When stable enough, release.  I realize Ubuntu is aiming for set release dates, but a 6 month to the very day release schedule may not be feasible.

I first installed Ubuntu before Warty was official, and dist-upgraded it to Hoary months before Hoary was released.  Until a few days ago I had that same installation.  It worked with few problems. I was impressed.

I should have known better after skimming the development forum here and seeing daily updates that were still fixing things and breaking others right up until the last minute, but I opted for a clean Breezy installation to clear out any cobwebs and start anew.  That was a mistake.  I should have stuck with Hoary.  Oh well.

Personally, I'd rather see Ubuntu have a release window or ETA instead of a concrete date if it means a better distro.

---

### Post by GeneralZod on 2005-10-17
[QUOTE=kaaredyret]Great post[/QUOTE]

'Nuff said :)

I especially agree with the points about criticism; if you love something, then you'll want it to be as good as it can be, and the only way to do this is to make thorough, well-reasoned criticisms and let - nay, encourage! - other people to do the same.

See [this](http://ubuntuforums.org/showthread.php?t=75886) thread for an excellent example of good criticisms.  Well, technically it is a wish list, but it can be argued that criticism is implicit in the act of making a wish as a wish for a change or new feature entails a statement of imperfection about the current setup.

---

### Post by dickmorrell on 2005-10-17
How boring it would be if everything worked out the box.

Personally having been using Linux 10+ years and having worked at Linuxcare, VA Linux and started SmoothWall this is the most polished and impressive distro I've ever used. 

Who uses a stock distro ?? Where would the fun be there. Half the fun is trying to work out whats missing and customising your own image. If we wanted boring we'd all marry a mannequin, wear plaid, drive stationwagons and use Windows.

I'd prefer to be an individual and enjoy getting indigestion trying to find the odd missing package or strange repository, it keeps the fun in what we do.

Congrats to the release team for all your hard work.

Richard

---

### Post by Zotova on 2005-10-17
[QUOTE=GeneralZod]but it can be argued that criticism is implicit in the act of making a wish as a wish for a change or new feature entails a statement of imperfection about the current setup.[/QUOTE]

That was the intention of my post. Whilst it may be too late to fix the problems in Breezy things can be changed/done different when it comes to DD.

---

### Post by kaaredyret on 2005-10-17
[QUOTE=dickmorrell]How boring it would be if everything worked out the box.

Personally having been using Linux 10+ years and having worked at Linuxcare, VA Linux and started SmoothWall this is the most polished and impressive distro I've ever used. 

Who uses a stock distro ?? Where would the fun be there. Half the fun is trying to work out whats missing and customising your own image. If we wanted boring we'd all marry a mannequin, wear plaid, drive stationwagons and use Windows.

I'd prefer to be an individual and enjoy getting indigestion trying to find the odd missing package or strange repository, it keeps the fun in what we do.

Congrats to the release team for all your hard work.

Richard[/QUOTE]


Why do you use a polished distro, if you find a working-out-of-the-box distro boring?

Don't confuse yourself with the users Ubuntu is aiming for.

I do not want my OS to be a hobby or a toy. I have a girlfriend, I have a kid, I have a job, I have sparetime I would like to use with my family and friends, and my hobbies.

My computer is a tool. A tool that I use for work, and my homepage, not a OS that I love to tweak and polish. Life is too short for that. I installed Ubuntu to see what I could get for free and to have a secure OS... pretty tired of Windows XP.

Ubuntu tries to be an alternative to Windows, a tool that is available to everyone, especially people that cannot afford commercial software.

I dont understand why it is so hard to understand that THIS distro is not a semi-religious project, a made-by-nerds-for-nerds project, but a damn fine attemt at bringing an easy-to-use-and-config distro to the masses.

This is Linux! You almost drown in distros, choice is there! But this particular distro, Ubuntu, is already known for its stability and great support of hardware. The only goal now is to make it better... and better... and better. Relasing it prematurely is not a step in the right direction.

---

### Post by moglenstar on 2005-10-17
the video codec problems can be solved easy enough, [http://ubuntuguide.org](http://ubuntuguide.org) states how, and even a complete linux novice can follow that..

the dhcp problem - well, i noticed that too, and it seemed to change the ip of my ubuntu computer randomly, so i decided to manually assign an ip, and leave it at that

speed issues - not a complete resolve, but i found enabling hardware acceleration with xcompmgr (if youre using an nvidia video card) without any of the fancy stuff, like shadows, or transparency, made things a lot snappier.

there is also the option of switching to a different wm, such as xfce4 - which is blazingly fast compared to gnome, but i wont go into that .. ;) (sudo apt-get install xfce4)

the login screen - hell yeah, i agree its ugly - but theres not a lot stopping you from downloading an alternate login screen, its customizable

extra repositories, easier way to install codecs, java, etc - get easy ubuntu ( [http://placelibre.ath.cx/keyes/index.php/2005/10/16/57-easy-ubuntu-231-correction-de-bugs](http://placelibre.ath.cx/keyes/index.php/2005/10/16/57-easy-ubuntu-231-correction-de-bugs) ) the page is in french, but its easy enough.. extract the tar to a folder somewhere, and doubleclick "EasyUbuntu" and choose to "run" .. select the options you'd like, and sit back while it does its thing

---

### Post by acascianelli on 2005-10-17
I don't believe that Breezy was rushed.  But, when I installed Breezy I found myself having many more problems than with Hoary.  I should have waiting to upgrade to Breezy, I had to reinstall Windows on my laptop for the time being because of school and all.

The main problem I had was with running Windows programs I needed.  Wine was not working right, it kept having segmentation faults (tried using package from Ubuntu and Wine repo).  Crossover Office wouldn't work either.  VMWare had problems installing because of the compiler version used to compile the kernel.  GCC 4.0 is the standard and the kernel was compiled with a version of GCC 3.4.

---

### Post by dickmorrell on 2005-10-17
[QUOTE=kaaredyret]Why do you use a polished distro, if you find a working-out-of-the-box distro boring?

----

I don't use a polished distro I use Ubuntu - it's a distro - and if people expect day one for every repository and everything to just work then thats just misunderstanding the community.

Forgetting your girlfriend, son, cousin, best friends dog and your cousins masseur I think I've rolled and released enough distro ISO's to the community to more than understand the "market of Ubuntu". If you're going to teach egg sucking lessons go teach someone who won't read your post raise his eyebrows and sigh.

Richard

---

### Post by nuopus on 2005-10-17
[quote=trash]ever since Hoary, I for some reason have been thinking 6 months is way too rushed... personally i couldn't work under that kind of pressure. I also don't think the majority of users want to go though this every 6 months(could be wrong)... not that anybody is forced to but lets face it, newer = better no?
Anyway, I also think 8 months would be way better[/quote]

Ubuntu has an annoying policy IMHO of not upgrading packages to the next version until the next release. They tend to like to backport all of the new security fixes from the new version of the application into the one current one in the OS release.

For me, if I had to wait a full year to get new release versions of packages I would definately not use Ubuntu. This backporting of security updates and bug fixes is not good enough for me ... sometimes I just want to latest version!

Unless of course, they changed the idiotic policy and just start including new release versions as they come out (with some testing of course) like other distros do it.

With current policy, 6 months is barable and anything longer would get me to look elsewhere.

---

### Post by jdong on 2005-10-17
You don't have to upgrade every six months... Basically you're forced into upgrading every 18 months, on a 6-month multiple... I don't find that unreasonable.


I don't want to present myself as a Ubuntu fanatic... I'm very open to other development models, too. In fact, I regularly use CentOS, and am testing OpenSuSE as we speak.


I just want to say that I see no more bugginess/rushedness than I see in enterprise-class (CentOS) distros or other consumer-based distros (SuSE 9.3/10.0)

---

### Post by acascianelli on 2005-10-17
[QUOTE=jdong]I just want to say that I see no more bugginess/rushedness than I see in enterprise-class (CentOS) distros or other consumer-based distros (SuSE 9.3/10.0)[/QUOTE]

I agree, Ubuntu still uses the same version of Gnome as many other distros, Ubuntu won't make certain bugs disappear.  I Believe that the problems I was experiencing was an incompatability with some software installed.  Personally, i'd much rather wait the extra time for apps to become compatible again than have a lower version of something packaged into Ubuntu.

---

### Post by kaaredyret on 2005-10-18
[QUOTE=dickmorrell]Why do you use a polished distro, if you find a working-out-of-the-box distro boring?

----

I don't use a polished distro I use Ubuntu - it's a distro - and if people expect day one for every repository and everything to just work then thats just misunderstanding the community.

Forgetting your girlfriend, son, cousin, best friends dog and your cousins masseur I think I've rolled and released enough distro ISO's to the community to more than understand the "market of Ubuntu". If you're going to teach egg sucking lessons go teach someone who won't read your post raise his eyebrows and sigh.

Richard[/QUOTE]

So, this is a distro for the "community" ? No, you are deadly wrong. It is a distro that tries to reach ordinary people as well, not just a secret club.

Forget about your past, and the PAST ... this distro is concerned about the FUTURE and ALL those who do not use Linux yet as well... not the current tiny community that sticks to Linux no matter how much time it demands for basic tasks.

While your eyebrows are raised, open your eyes as well, and look around. You will see many potential Ubuntu users, but they are not like you or not even from the community. They want Ubuntu to be an OS, a servant, a tool.

---

### Post by yesplease on 2005-10-18
[QUOTE=Zotova]I also get annoyed by posts like yours. I talked about some problems and why I feel Breezy should have been delayed. I'm not saying I wanted a 100% bug free Breezy, I know that would never have happened. What I think should have happened is maybe another month tops to iron out some of the remaining bugs. I mean look at the forum there are a handful of sound topics with people who have problems. The flash firefox sound problem is common.

But the attitude from posts likes yours seems to be unless people are praising Breezy they should not post anything. My first post was critical of Breezy yes, but if you actually read it I said that my comments weren't disrespectful of the developers and that I am a great fan of Ubuntu. The aim of my topic is to get the point over that I personally felt that the release should have been delayed a while to fix some final problems and that I hope when DD is released it will be less buggy. With my criticism and the criticism of others I'd hope to see a better DD – if we all sit here not daring to say  a bad word then improvements would never happen. :roll:[/QUOTE]

Oke, you say your intented to provide critisism in order to improve Ubuntu, and I have no issue with helpfull critisism.

My suggestion for posts with critisism in general is to put some balance in it. Put yourself in the place of the people who make Ubuntu possible. They solved many known problems, try to get the latest packages working and build in new features. They provide a release candidate so that users can report bugs (now that is helpful). If there are problems after the release they wil solve them for you. In general I suggest that when you have a problem just ask a question without saying this or that sucks. Put some balance in your posts and give credit where credit is due.

I am not saying that this all necessarily applies to Zotova's post, Zotova can judge for himself. I still have the impression that the first post in this thread was borne out of frustration after a time-consuming issue with some apps, but perhaps I am wrong about that.

---

### Post by David Marrs on 2005-10-18
Here's my two penneth. The one critical flaw I see with Ubuntu is the strict frozen release concept across the whole package base. It's fine for Debian where every package is rigorously tested to death before it makes it to Stable, but I just don't see the sense in it when you have a 6 month deadline to work to and two of the three repositories aren't significantly tested (if at all) anyway. Yes, yes, I know they're not supported, not Ubuntu's responsibility, blah blah blah, but that only adds to my argument: If they're not supported then what's the harm in the community maintaining them? It can only mean improved stability overall and allows Ubuntu to become a supported platform in its own right, which is possibly important given its popularity.

---

### Post by rolfotto on 2005-10-21
[QUOTE=dickmorrell]Who uses a stock distro ?? Where would the fun be there. Half the fun is trying to work out whats missing and customising your own image. If we wanted boring we'd all marry a mannequin, wear plaid, drive stationwagons and use Windows.

I'd prefer to be an individual and enjoy getting indigestion trying to find the odd missing package or strange repository, it keeps the fun in what we do.[/quote]

Sorry, but when I read this, I thought of this:D

[img]http://www.rolfotto.com/images/conformity.jpg[/img]

And what's wrong with marrying mannequins? >:(

Anyway Zotova,

I think most of us can share your frustration and can remember a time when, for whatever software, let alone an entire distro, a certain upgrade didn't live up to expectations or was even worse than its predecessor.  For me the experience was mixed - my monitor was finally detected right and I booted into 1280x1024 mode right off the bat instead of 640x480.  But Firefox seems really buggy and hogs the CPU until shutdown, thankfully Opera came out free recently and I downloaded that.  Along with a host of other ups and downs.

My hope in this situation, is that unlike a lot of other propietary software, this isn't rushed out the door to make money or just keep people on the upgrade treadmill.  I think the nearly definite date is a smart thing because it's a kick in the pants to get something done, I've been on my share of software teams where the product kept dragging because of a lack of a date to get definite things done (or to stop adding feature upon feature) and this type of kick in the pants works wonders^_^

Anyway, my question is - if you still wrestling all those problems with Breezy, why don't you switch back to Hoary which you said was much better and wait until Dapper Drake or the one after that?  A six months old distro isn't that bad unless you are running a server, and even then......:)

---

### Post by DarthGroznii on 2005-10-21
I have different problems with Breezy - for the most part I've got it up and running on my HP Compaq nx7000 laptop, and running well - it was the first Linux distro that I found that worked completely right with the sound card.

My problem is with wireless cards.  nx7000 has the Centrino chipset, but is only 802.11b compliant.  As such, I've been trying 802.11g PCMCIA cards from the recommended hardware list on the Ubuntu site, and not one of them has worked out of the box, even though the site says it should.  Linuxant says it doesn't support this distribution, when I tried DriverLoader.  Ndiswrapper refused to play with a 3Com card and a Linksys card I tried. 

I finally found a vendor who deals in Orinoco cards, so fingers crossed, that will solve the problem.

I'm not saying this is an problem that only Ubuntu has - I tried Mandriva, and it was crap at wireless cards too, but it's worth noting for the developers, please think about these issues as you're working on the next release.

---

### Post by Magneto on 2005-10-21
Just installed Breezy and it was a breeze

Cons-
( which arent really cons to me since I've had much harder times with many different operating systems at more difficult times)

Had to add my own monitor specs for proper resolution
Had to add nvidia driver to xorg too and its options
No wpa support for atheros without adding on other programs - very n00b unfriendly and very unsecure since wep is almost totally worthless
Having to install all the "Restricted" items and updating sources.list takes longer than installing the OS. 


Overall I give it an A+. Good job. Like the nautilus change(no need to open gconf right away). 
I have had no sound, networking or video problems with standard use. Wireless configuration and video tweaking could use improvement.
Also none of the speed issues other people mentioned. I do have to note that I have been forced back into using Windoze XP as my workstation since Hoary and I can't see myself returning to anything more than 40% of the time on Ubuntu.  Evolution is not Outlook and running apps in Wine is not generally something I have enjoyed. I will make an attempt at it though just to try to buck Billy BathGates again.

Performance on a amd sempron 2400 with 512mb of ram is very very very fast compared to what it was. My boot time has decreased from Hoary too.

Anyone know of a better distro? I don't, although I know some close seconds.

---

### Post by Penguin Skinner on 2005-10-21
Very interesting thread, so thought I'd share some comments as a somewhat established *nix user who migrated over to Debian some months ago, and installed 'Breezy' just the other day.

First let me say, the frankness of comments I see here has raised my estimation of the Ubuntu community.  Up until now, it seems as though all I've heard about Ubuntu was either a) unwaivering love for the distro by those who seem to consider it nearly flawless, or b) seemingly unwarranted criticism by users of other OSes who give no real indication of having actually tried Ubuntu.

The only reason I've never tried Ubuntu before now, BTW, is because none of the earlier releases would boot or install on my fairly new hardware.  Despite finding the latest Kubuntu LiveCD rather disappointing -- it's far-and-away the slowest booting LiveCD I've ever seen, and the lack of apps for all that load time was a real let-down -- plus not being much of a fan of Gnome, I downloaded the Breezy install iso and decided to give it a go.

Having installed and used FreeBSD, Slackware and Debian, non-graphical installers don't intimidate me.  The Ubuntu installer was OK, except I found the partitioning tool very annoying: I don't really need or like smilies, and I particularly don't care for the partitioning tool just assuming that I'm a rank noob who cannot be permitted to install to an existing partition.

The installer left my hard drive in an unbootable state, and although I chose to install GRUB to the partition rather than MBR, the routine did not offer to make a boot floppy.  This wasn't a problem for me, as I'm always prepared for these kinds of glitches with a whole battery of boot diskette utilities, but for a less experienced user, this could have been very troublesome, even though no real damage was done, just a mis-set active flag.

Once installed, I found some features of Ubuntu/Breezy that impressed me.  The installer detected my ATI video card and installed the ATI driver; true, I don't have 3D, but I have working DPMS out-of-the-box, which I don't get with the (lame) vesa driver nearly all other distros set up with initially.  Gnome 2.12 affords the luxury of a menu editor -- finally! -- and the automatic updater seems pretty cool, offering me eight application upgrades right off the bat.

On the downside, for a distro that tries to discourage one from running as root, I was very surprised how difficult and buggy trying to run as adm-group user was.  Within Gnome, programs such as Synaptic, which require the root password, don't properly accept the password when entered, and thus won't launch from the desktop.  While configuring Xscreensaver, my mouse refused for a while to move over into the left two inches or so of the screen, and when setting monitor power saving features, there's an incredible bog in the system, accompanied by a lot of disk thrashing.

Performance and overall system speed seemed quite good most of the time, but at various times the system would completely bog down, presumably from some background process(es) that take priority and/or consume massive amounts of resources.  BTW, this kind of thing is common under FreeBSD, but I've never seen anything like this under Linux.

Under the hood Ubuntu certainly looks Debian enough that I would have no problem working with it, but there seem to be some significant problems with this release that will dissuade me from doing much with it.  Something I enjoy doing with Debian-based distros is learning new Debian tricks, and hopefully something worthwhile will come of this.

Final comment ... someone above mentioned the significant changes and transitions in Debian lately as possibly contributing to some of the 'issues' seen with Breezy.  I have to disagree with this, inasmuch as my Debian Sid install has been comfortably dist-upgrading for the last several weeks, and I tend to be a bit of a late adopter.  Ubuntu's developers really shouldn't have any problems of that sort.

Anyway, thanks to the intelligent posts I see here, I intend to follow Ubuntu a little more closely in the future.

---

### Post by zenodaddy on 2005-10-21
I had issues with 5.04 when I first installed it but once I become a regular user of linux and learned the commands I didn't have any problems after that. The biggest mistake I made was reinstalling ubuntu after hosing my machine by installing the then latest ATI driver. I had no idea that I could have just ran some diagnostics, update and upgrade and then reboot and all would be well. Once I figured out I had to run the config program all was well... and now I had installed the newest version of ubuntu 5.10 and you know what? I have had very few problems and the few that I did get were minor to say the least.

I still have no figured out how to get celedega (I think that is what it is called) and never could get xwine to run anything but these are minor since I duel boot anyway.

All is well on my machine so far and I hope it stays that way ;)

I have used Suse 9.3 and it did not like my BIOS at all, system would always crash, and the distro lasted a whole 24 hours on my machine before I almost threw it out the window. IMO the people who made ubuntu are doing the best job ever. I am not one of those cheerleaders who only will use ubuntu, but I will say that their distro is the best I have seen yet.

---

### Post by regeya on 2005-10-23
[QUOTE=trey]I guess its the standard STFU and RTFM or move on.[/QUOTE] Any personal suggestions? My own thought is to move back to Hoary, Hoary Backports, and the list of unofficial repos I was using until last week. With that awful mishmash of poorly-matched repos, I had a stable system where everything worked. Now? I could voice my opinion that arbitrary release dates are stupid, but since you told people who aren't happy to **shut the **** up** I guess I should be looking for an alternative.

Suggestions, anyone, on what to use while Ubuntu competes with the original release of Windows 98 on Worst OS Ever?  I say this out of the experience of having my machine lock up every five minutes or so if powernowd is running.  With it, the machine locks up.  Without it, the machine runs full-throttle all the time.  Not acceptable, even if I *am* getting the system for free.

And why *should* I STFU?  We're not talking about rank amateurs putting together a hyper-l33t distribution here; we're talking about people putting together a desktop Linux distribution *for the masses* here--and *as part of their job*, at that.  This sort of problem is acceptable in, say, Gentoo, where the user is expected to be able to fix things on their own, or at least willing to Google for it and search through the Forums.  Ubuntu and Kubuntu, OTOH, want to grab the eyeballs of people who're currently using Windows and MacOS.  To do that you need to have releases that *don't* cause major issues like power-management causing lockups, and you can't fall back on the 'if you don't like it go away 'coz you're not paying for it' whining and moaning fests.  

Either you want to appeal to the masses or you don't.  If you don't, Canoical, give up and stop wasting our time; I'll be willing (not happy, but willing) to go back to running Gentoo, FreeBSD, Debian with unofficial repos, whatever it takes to get my system running stable without having to put up with some goofy list of distro-specific software as most Linux desktop distros are bad to do.Back in the Warty days I could forgive it; in Hoary I could tolerate a bit.

I'm still rootin' for you, guys; I doubt that I'll be recommending the distro anytime soon, though.  If this is the result of a braindead arbitrary release cycle, the release cycle program is broken and needs to be fixed.  This isn't rocket science.  Please save the distribution we all know and love by **ditching Ubuntu's weakest point**.

Thank you for your time and I'm very sorry if you're offended, but I'm not sorry enough to take any of it back.  You've done an excellent job of pushing the Linux world forward; now step up to the plate *again* and fix your broken development cycle.  

I'm still happy to get any suggestions on different distributions.  Much as I love Ubuntu, I need a stable desktop-oriented system and XP is *not* an option for a variety of reasons.

---

### Post by Magneto on 2005-10-23
regeya - I understand your points as do most people here. Remember this distro is still young.  Your Hoary rollback suggestion seems like your best bet if you were satisfied with it and Breezy is proving problematic. Like any OS upgrade or new release you have to take your time with it and allowing some time for some bugs to be worked out. Pre-release or official release to me its still bleeding edge and that's whether its microshaft or canonical.

As for me, my list of Breezy pros keeps growing. 
Madwifi finally works for my card
Amarok with no gstreamer or database problems with my 400gb of mp3s -2309 album covers fetched with no crash or slow down in system speed :)
Smeg being added

I had to scrap use of ubuntu - hoary because I didnt have the time to treat it like gentoo. Breezy is definitely better for me.

---

### Post by Cl1mh4224rd on 2005-10-23
Alright, this kind of attitude really irks me, so... apologies in advance...
> **dickmorrell]How boring it would be if everything worked out the box.[/quote]
Boring? Maybe... Not frustrating? Most definitely...

> Personally having been using Linux 10+ years [...]

Who uses a stock distro ?? Where would the fun be there. Half the fun is trying to work out whats missing and customising your own image.
I guess that 10+ years of Linux experience makes you an expert on what other people want from an OS, huh?

Gas prices nowadays are pretty high, and steadily rising. This results in people looking to switch to more fuel-efficient vehicles. I'd be pretty angry if I bought a hybrid and found out there was "Some assembly required."

Just like someone shouldn't have to know how to build a car to use a car, no one should be required to know, or figure out, how to build an OS to *use* that OS. *Especially* when that OS is marketed as "for human beings".

I suppose you can make the "you get what you pay for" argument, but when many people loudly and publically claim the free alternative as being superior to the commercial one (and Linux zealots do this *all the time*), things *better* just work "out of the box".

Further customization by the user is something else entirely.

> If we wanted boring we'd all marry a mannequin, wear plaid, drive stationwagons and use Windows.
Since when was the desire for usability a herd mentality? If there's one thing Microsoft did right, that was it (to the detriment of other aspects, sadly).

> I'd prefer to be an individual and enjoy getting indigestion trying to find the odd missing package or strange repository, it keeps the fun in what we do.
You are you said:**
> Congrats to the release team for all your hard work.
I agree.

---

### Post by snarkout on 2005-10-24
If anyone is interested in my opinion, the 6 month cycle should be scrapped by *all* distros.

---

### Post by teevee on 2005-10-24
Junk filtering in Evolution is severely broken by *silently omitting* that it is actually *not filtering any mails*, even though all relevant options are checked, because spamassassin from the *officially unsupported universe* is needed. But even if manually enabling universe, installing spamassassin and changing some variable in some config file (Ubuntu's target group won't get that far) it will still not filter mails on its own.

If bugs like these that would qualify as blockers in other distros can't be fixed with this 6-months release cycle than this release cycle is probably a bad idea.

---

### Post by nix4me on 2005-10-24
i don't get it.  My Ubuntu 5.10 is working flawlessly!

I had problems with repositories - fixed using de sites.
I had problems with codecs - fixed w32codecs.
Firefox 1.07 is crap - fixed with beta 1.5.

Mine is truly working great right now.  Granted it took a couple days to get everything working just like I wanted.

nix4me

---

### Post by Whatsisname on 2005-10-24
What I have noticed is that using the cd image, the dvd image, and apt get, a problem was encountered with the kernel-headers package that made the install process very difficult and I had to do it by hand. For apt-get it caused a cascade of broken dependencies that I was never able to fix, and had to take the gamble of upgrading from the dvd, risking destruction of my raid partitions, only to encounter the broken package yet again.

---

### Post by doclivingston on 2005-10-25
[QUOTE=teevee]Junk filtering in Evolution is severely broken by *silently omitting* that it is actually *not filtering any mails*, even though all relevant options are checked, because spamassassin from the *officially unsupported universe* is needed. But even if manually enabling universe, installing spamassassin and changing some variable in some config file (Ubuntu's target group won't get that far) it will still not filter mails on its own.[/QUOTE]

All I had to do was install spamassasin, and it started filtering mail as junk immediately after that. It obvously started working better once I trained it on the kind of spam I get, but it was working before that.

---

### Post by ions on 2005-10-26
Well if Breezy wasn't rushed some things were just missed.  Fact is I see a lot more problems being posted now than I did at this point after Hoary's release.  Maybe that's due to a much larger user-base?  I dunno.  I do know the two machines I have put Breezy on have not taken to it well.  

Problems with Machine A:

1.  No streaming video in FF.  I have searched here and Google and tried just about everything I've found.  It worked fine with Hoary.  I figure I'll wait for the Ubuntuguide to come out so at least I'll have some sort of base level of information to explain what I've tried other than "everything". Yes I do have the codecs.  Sound does work though so I can hear the videos.

2. Evolution Mail.  As soon as I have to download or view an attachment Evolution becomes unusably laggy.  Real bad.  Receiving, sending or forwarding any mail with an attachment is a long painful process.  7 or 8 minutes to send an email with a 100KB attachment.  And no, it's not my connection.

3. FF Crashes.  Just disappears.  Not as much as it used to when I had the tabbrowser extension but it still does once in a while.  No rhyme or reason.  Sometimes it'll just disappear when idling with one local tab open.  I'll get up to use the can and come back to find FF gone.

4. Evolution Calendar.  I add an appointment.  "Go crazy at 11AM on Tuesday".  If I click the Gnome clock in the panel it displays that I have set an appointment to go crazy at 7AM.  If I set my appointment for later in the afternoon, 4PM for example, the calendar under that clock says I have set it for noon.  

5. My apps do not appear on the same virtual desktops that they were on when I shut down as they did in Hoary.  No big deal but I need to do a bit of sorting I never had to in Hoary.

6. Going to Places > Recent Documents does not work unless I have already opened a document.  So when I first start my machine and want to work on the same doc I was working on yesterday I may as well just go through Nautilus and open it that way cause Recent Documents does nothing at startup.

Problems with Machine B:

1.  No streaming video in FF.  I have searched here and Google and tried just about everything I've found.  It worked fine with Hoary.  I figure I'll wait for the Ubuntuguide to come out so at least I'll have some sort of base level of information to explain what I've tried other than "everything". Yes I do have the codecs.  Sound does work though so I can hear the videos.

2. Instead of the pleasent GDM login screen I get an error and a default login screen.  The error says:

> 
**The Configuration is not correct!**

This configuration file contains an invalid command line for the login dialogue, so running the default command.  Please fix your configuration.

I am given an OK button to click.

Just to add that getting them to this point wasn't a smooth trouble free road.  Following these directions: [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes) did not lead to a trouble free process.  It was a pain on both machines I've upgraded from Hoary.

---

### Post by joplass on 2005-10-26
Another useless thread.  I haven't seen a Linux distro "ready" for...???  It is up to the user to get it ready.

My Breezy is better than my Hoary.  This is the first time I set up a wireless card in less than 30 min.

Should people always whine?  Besides your experience isn't my experience and vise-versa.

---

### Post by NewWithoutClue on 2005-10-26
IMO....
I respect everything these people have done, and their offspring ( ubuntu ).
Me? i know next to nothing about linux, ubuntu has made learning much easier..and the fact that some thing's missing or otherwise not correct is part of a sysadmins job..after all i migrated to linux simply becuase i feel at home when i'm running it; **I'M** in control when i'm running it. When i figure something out i feel a sence of pride...anyway getting off topic and i'm tired...but, i have to say i was offened by this post; GNU and everything related should not be asked for 100%, although, i'm sure they give it. Mistakes are born everyday( bugs ), the fun part is fixing it, after creating it...there is nothing wrong enough with the distro to make someone dispise it or otheriwse rid themselfs of it.

I know no one wanted to offend anybody, but you have to see the big picture.

Remember these are my opinions.

Forgive the spelling; i'm tired. -.-"

Regards,
Paul.

---

### Post by ions on 2005-10-26
Are we too busy arguing over whether we should post about problems here?  Should I post my problems somewhere else?  :rolleyes:

---

### Post by NewWithoutClue on 2005-10-26
[QUOTE=ions]Are we too busy arguing over whether we should post about problems here?  Should I post my problems somewhere else?  :rolleyes:[/QUOTE]

No, i stated that ubuntu ( INCLUDING THE COMMUNITY ) is making it easier to learn.

I love this community, as do many other people ( how could they not? )

Paul.

---

### Post by Malphas on 2005-10-26
I think the regular six month release cycle is the Ubuntu's greatest strength, even if it does mean it's a little buggy.  If you get rid of that then we might as well just use Debian and wait for years before seeing a new release (albeit a rock solid one).

---

### Post by darrenrxm on 2005-10-26
This is the first version of linux that hibernate and power management has worked properly for me. Boot times are way faster when you use hibernate. Not to mention it recognized the two big ones sound and video. My tvtuner card isn't supported yet. But im willing to sell it and buy one that is. I like ubuntu that much.** No version of linux has come so far in such a short time**. Im not the least bit surprised that it is number one on distrowatch.

---

### Post by Zotova on 2005-10-27
[QUOTE=joplass]Another useless thread.  I haven't seen a Linux distro "ready" for...???  It is up to the user to get it ready.

My Breezy is better than my Hoary.  This is the first time I set up a wireless card in less than 30 min.

Should people always whine?  Besides your experience isn't my experience and vise-versa.[/QUOTE]

How is the future of Ubuntu/Linux useless :rolleyes: If changes can be made to make Dapper even better then I'd sure like to see them.

Also, I suggest you read what Ubuntu is actually about, a distro for the people, NOT geeks. It isn't up to the user to get it ready, it should be up to the creators - the only thing the user should have to do is install and setup programs to their taste. If you want a distro where you have to do half the work yourself to get things running then you should be using gentoo. Ubuntu is supposed to be for everyone, a friendly distro - that is the point people are missing when moaning at people for speaking up and saying x,y and z could be improved.

[quote=ions]Well if Breezy wasn't rushed some things were just missed. Fact is I see a lot more problems being posted now than I did at this point after Hoary's release. Maybe that's due to a much larger user-base? I dunno. I do know the two machines I have put Breezy on have not taken to it well.[/quote]

Whilst I do sympathise on problems with Firefox it isn't really Ubuntu's fault. I have experienced the random closing myself but at the end of the day Ubuntu don't make and maintain Firefox. So any problems should really be taken up with Mozilla.

The same goes for Evolution (I think) as far as I know that is created and maintained by Novel.

--

After a few weeks of Breezy however I do admit I may have been harsh with my initial post. However there are a few bugs which I see as major. I have had to un-install the update manager as it simply uses a lot of cpu at random times. Some times when I start it is fine, others it slows the computer down as it is using up the cpu. I have also done a fresh install since and the problem is still there.

On the topic of codecs though I still feel Ubuntu isn't doing enough to help users – even though they are strictly not supported it is obvious the vast amount of users will want to install them. There is a how-to that I am aware of but I personally found it very outdated and inaccurate.

---

### Post by Magneto on 2005-10-27
zotova - Ubuntu is not the only distro to HAVE to deal with codecs and other licensing issues this way. This is a legal matter. I'm not sure if advising people how to break the law is something Canonical wants to do.

Just like Mozilla, Evolution and Gnome aren't Ubuntu creations neither are the licensing issues we are all forced to deal with. Any user can use the SEARCH function on this board and find hundreds of posts about codecs and how to use them.  You won't find documentation on how to use color printers illegally on the manufacturer's website.  Again, this situation was not created by Canonical.

---

### Post by carlosqueso on 2005-10-27
Admittedly, I haven't used previous versions of Ubuntu, but Mandrake 10 was so "polished" that the standard KDE setups were all hidden by much worse Mandrake windows and half my hardware didn't work.  Then I switched to BLAG (non-standard Fedora distro), which was NOWHERE near as bug-free as ubuntu.    I have to say that Ubuntu's the best working distro out of the box I've used today.  

On the other hand, having a time-dictated release cycle could be dangerous if it is viewed as a hard date instead of a target which can be missed if major problems exist.

---

### Post by egon spengler on 2005-10-27
[QUOTE=Zotova]Also, I suggest you read what Ubuntu is actually about, a distro for the people, NOT geeks. It isn't up to the user to get it ready, it should be up to the creators - the only thing the user should have to do is install and setup programs to their taste. If you want a distro where you have to do half the work yourself to get things running then you should be using gentoo. Ubuntu is supposed to be for everyone, a friendly distro - that is the point people are missing when moaning at people for speaking up and saying x,y and z could be improved.[/QUOTE]

To be honest I don't really know what canonical's stated aims of ubuntu are but I would be very surprised if ubuntu was supposed to be a newbie distribution. Based on what I have read (I haven't really tried many other distros so this is based on feedback from others) ubuntu makes much more extensive use of the command line, which, apparently, is intimidating for new users, than several other distros which are all point and click. 

On top of that there is of course the issue of no codecs. I think we would all agree that a massive amount of people who might switch to Linux want to watch videos and listen to mp3s and so hunting for the info on how to enable the codecs is not going to appeal much to them.

It's good that ubuntu works so well out the box with so many people that it's gained a "beginner friendly" tag but based on what I see around here two key aspects of beginner friendlyness are never having to use the command line and having built in mp3 support. Neither of which seem to be aims of ubuntu so I can't help but wonder if 100% beginner friendliness is really something ubuntu is aiming for; despite what the slogan might say (although it should be noted that Linux for humans has as many different interpretations as there are forum members here)

---

### Post by poofyhairguy on 2005-10-27
[QUOTE=Zotova]
On the topic of codecs though I still feel Ubuntu isn't doing enough to help users – even though they are strictly not supported it is obvious the vast amount of users will want to install them. There is a how-to that I am aware of but I personally found it very outdated and inaccurate.[/QUOTE]

Its a matter that is out of Ubuntu's hands. Read the disclaimer:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by aysiu on 2005-10-28
[QUOTE=egon spengler]To be honest I don't really know what canonical's stated aims of ubuntu are[/quote] You can read about them if you look on Ubuntu's main site. They aren't hidden away somewhere.

> but I would be very surprised if ubuntu was supposed to be a newbie distribution. Based on what I have read (I haven't really tried many other distros so this is based on feedback from others) ubuntu makes much more extensive use of the command line, which, apparently, is intimidating for new users, than several other distros which are all point and click. I have to say I, too, take issue with people touting Ubuntu as a "newbie distro." I would never hand anyone who has no Linux experience a Ubuntu CD and say, "Here. Try this." I would possibly do that with Linspire, Mepis, or Blag, though. Ubuntu is a wonderful *second* distribution. It's certainly not advanced, but it's not for the uninitiated. At the very least, you have to have a little bit of computer savvy (and access to these wonderful support forums) to make it work... but once you do, it's one a great experience.

---

### Post by Zotova on 2005-10-28
[QUOTE=Magneto]Any user can use the SEARCH function on this board and find hundreds of posts about codecs and how to use them. [/QUOTE]

That is my point, half of those threads are topics where people have given out incorrect versions of the codecs. I had problems getting the codecs because I had used one of these threads.

I don't see the problem however, people are very rightly saying the same thing over and over again - the codecs aren't strictly legal... however like you have rightly pointed out there are numerous threads on how to install them. So why is it so impossible to have one thread stickyied in an easy to find place with detailed instructions which actually work? (unlike the how-to in the wiki)

I think it is fair to say the desktop-support is the main ubuntu section for help? - in that section there is only one sticky with basic how to post instructions.

---

### Post by aysiu on 2005-10-28
We generally don't sticky HowTos, from what I can see from the other mods and staff. There are a lot of great HowTos out there, and if we stickied them all, it'd be a cluttered Desktop Support forum. What's a better solution than stickying them all? How about creating a HowTo section?

That's what we have--a HowTo section. In fact, as you can see from [this search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+howto+codecs&btnG=Google+Search), because of the existence of a HowTo section, it's easy to find whatever you're looking for. There's also the ever-so-popular [Automatix](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=site%3Aubuntuforums.org+automatix&btnG=Search).

---

### Post by poofyhairguy on 2005-10-28
[QUOTE=aysiu] There's also the ever-so-popular [Automatix](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=site%3Aubuntuforums.org+automatix&btnG=Search).[/QUOTE]

I stickied that. That is the solution the forum gives. If it does not work yet perfectly its because Breezy is new and testing was needed. Very soon it will all be in place and the point will be irrelevent.

---

### Post by rsgooch on 2005-10-28
IMHO i think that Zotova has missed the whole idea of Linux/Ubuntu in general.  This and most distros are designed for the people.  We have some responsibilty and opportunity to provide feedback during the development process.  I would put to him and every person who has bagged Breezy how many bug reports did they submit for RC1 and the prior beta releases.  If you submitted feedback then good for you! If you did not submit feedback then you are stuck with the product that was released.  I have used Ubuntu for about a year and it has come a long way. It will only get better if we the end-users get involved during the beta phase, not bagging it after it is released.

I have to admiit everytime I use Ubuntu I am impressed.  I tend to stick with mainstream hardware and I think that is why I have such great sucess with the Ubuntu installs in general.  My install went flawlessly, I did have to do some tweaking to get everything the way I wanted it but the forums helped me with that.  Ubuntu has a very strong community around it and that is the main reason I use it and will continue to use it.

To the development team "Good job thank you for all the hard work!"

Rueben
Registerd Linux user #368958

---

### Post by der.brain on 2005-10-29
Hi from germany,

for sure this was a hard release xorg, gcc4 and do not forget nfs4 wich is not included yet.

What i do not understand are the problems with folder sharing over gui the fu ... wizzard where you can choose smb or nfs wich is both not working over the wizzard and the diks manger wich mounts you share with root rights ;-) 

... or if you want connect to a windows share you have first to login at the station wich is the master browser and after that at the WS you want to connect to even if username and password is the same for both stations ???

I am sure that the most problems we read in the forums are based on a not working "virtual mounting" ... most workarounds are all based on hard mouting.

Disks Manager is another friend of mine ... when it mounts you need root rights for access ... good joke under breezy wich is base on sudo. ... O.K. you can go over "do as other user" root and run nautilus ... bur this is not newbie freindly and at the end it was not the idea of easy network sharing over the gui.

This are my expressions.

Sorry for my bad english

Michael


I hope this major bug is fixed soon.


Michael

---

### Post by der.brain on 2005-10-29
O.K. i thing our intension is where it should be.

I read in german linux paper that Mr. Mark Shuttleworth suggest the developers
just to work on the bugs and do no implementaion of other stuff. The idea is getting Breezy stable until 2006 to be an alternative to windows vista wich also comes up 2006.

I thing this is the right way and this words could come dirkt out of my hard.

until than i downgrade to 5.04

If this is the way this thread can be closed for me.

Best wishes from germany

michael

---

### Post by DarkKnight on 2005-12-11
I think the biggest thing people are forggeting is that Breezy is **not** 'stable', as such. It has only just been released, there will be teething problems, but if you spend your time fixing them, everyone benifits. :)

The alternative is Debian 3.1 release speed...
(And I have given 4 or 5 disks to 'newbies', I've not heard any problems back from them so far.:])

---

