---
title: "Firefox 3 not able to run on Dapper?"
date: 2007-05-16
forum: The Cafe
---

### Post by salsafyren on 2007-05-16
I just saw the proposed requirements for Firefox 3.

[http://wiki.mozilla.org/Linux/Runtime_Requirements](http://wiki.mozilla.org/Linux/Runtime_Requirements)

They propose Gnome 2.16.X, dapper only has 2.14.

This is really crazy. Do I really have to upgrade my distro just to use the newest browser?

Mozilla really doesn't care about Linux.

---

### Post by macogw on 2007-05-16
Well Firefox 3 isn't even released and won't be released for quite a while longer.  2.16 won't be new by then, but Dapper will certainly be old.  I'm not sure when FF3 comes out, but I think it's not for like a year, and by then there'll be a new LTS.

---

### Post by aidanr on 2007-05-16
> Distros providing longer-term support (i.e. enterprise distributions with long lifecycle requirements and older libraries) will be responsible for maintaining support for older runtimes via build-time switches. This is in line with how many other apps are supported by the distros.

if it's backported it will be compiled against the older gnome version

---

### Post by PriceChild on 2007-05-16
Dapper will not get Firefox 3.

Firefox 3 will not be backported for Dapper.

If you want Firefox 3 then you will have to go with the latest version of Ubuntu that supports it.

We have frozen releases to give you stability. We can't just update everything because you want one or two new shiny things.

---

### Post by aidanr on 2007-05-16
well there you go then :-P 
still should be able to compile it yourself though

---

### Post by salsafyren on 2007-05-16
> **PriceChild said:**
> Dapper will not get Firefox 3.

Firefox 3 will not be backported for Dapper.

If you want Firefox 3 then you will have to go with the latest version of Ubuntu that supports it.

We have frozen releases to give you stability. We can't just update everything because you want one or two new shiny things.

Did you read what I wrote?

Firefox 3 not able to *run* on Dapper?

I am talking about taking the binary from mozilla.com and running it on dapper.

I will probably upgrade my dapper machine to the latest LTS when it comes out, but still I think it is lame of mozilla.

It would be nice if they posted the technical reasoning behind this move.

I think it is time for a new browser based on Webkit or something else, so we are dependent on gecko.

Also, I think that the fact that we cannot replace firefox because of the problems it causes in the gnome desktop is very lame. IE has been bashed by many for that reason alone.

---

### Post by Rhox on 2007-05-16
> **salsafyren said:**
> 
It would be nice if they posted the technical reasoning behind this move.
They did

> I think it is time for a new browser based on Webkit or something else, so we are dependent on gecko.
We all ready have something similar,Konqueror.

> Also, I think that the fact that we cannot replace firefox because of the problems it causes in the gnome desktop is very lame. IE has been bashed by many for that reason alone.

It's not really their fault. One of the benefits of FF3 is that it uses cairo so it needs cairo support.

---

### Post by mips on 2007-05-16
Do you really need firefox 3 ?

There are other browsers like Konqueror, Opera etc.

---

### Post by Polygon on 2007-05-16
firefox 2.0 just came out.... im sure by the time firefox 3.0 comes out, another LTS release will be out and dapper will seem like breezy to us feisty users.

and by that page, its basically saying that firefox wont run on kde unless you have the gnome libraries installed?

i dont use kubuntu or kde but is that the way it is now? do you require the gtk + gnome libraries to run firefox?

---

### Post by zugu on 2007-05-17
Firefox 2 did not make it into Dapper repositories. FF3 won't be there either.
You can compile FF2 on Dapper, but it's not for the faint of heart. FF3 will not build, because Dapper does not meet the minimum requirements for compiling. And that's it. Ubuntu/Mozilla people won't move a finger towards this goal. 

Yet another disadvantage of following a time-based release schedule.

---

### Post by esaym on 2007-05-17
Firefox has really become a mess.  Many are referring to it as "windows crapware".  Opera has always been really good but I can't get used to the gui so I can't use it :(

FF2 was never brought to dapper because it required ~183 other libraries and programs to be backported from edgy.  But there is stuff like Swiftfox that allows you to run FF2 on dapper.

I know what you mean about the LTS though.  I was thrilled when I first installed it thinking that I would get FULL support until 2010.  Unfortunately the support only comes in the form of security fixes, not bug fixes or enhancements.

This is why I moved to debian-testing though. :KS

---

### Post by Gargamella on 2007-05-17
think also the time that passed since 1.0 to 2.0... it is a lot of time 

and you can live peacefully in my point of view even with FF1.5

---

### Post by ixus_123 on 2007-05-17
On the strength of firefox2, I'm not bothered at all.

Firefox 1.5 was great - with 2 all I've had on Windows & Linux is a bloated unstable browser. I think somewhere along the line Firefox forgot it's roots - to be fast & light, just for browsing, wiht no fancy extras

---

### Post by agurk on 2007-05-17
Hmm...I'm not joining in on any Firefox bashing, the Mozilla devs are all heroes in my book, along with every other FOSS developer out there. FF2 had a rough start, granted, and perhaps it was released too soon, but that's said with perfect hindsight. The 2.0 branch has really been shaping up lately stability wise and here's what's in store for the upcoming 2.0.0.4 release: [http://forums.mozillazine.org/viewtopic.php?t=545322](http://forums.mozillazine.org/viewtopic.php?t=545322).

---

### Post by banjobacon on 2007-05-17
Why run an LTS version of Ubuntu if what you really want is new software?

---

### Post by Polygon on 2007-05-17
> **esaym said:**
> Firefox has really become a mess.  Many are referring to it as "windows crapware".  Opera has always been really good but I can't get used to the gui so I can't use it :(

FF2 was never brought to dapper because it required ~183 other libraries and programs to be backported from edgy.  But there is stuff like Swiftfox that allows you to run FF2 on dapper.

I know what you mean about the LTS though.  I was thrilled when I first installed it thinking that I would get FULL support until 2010.  Unfortunately the support only comes in the form of security fixes, not bug fixes or enhancements.

This is why I moved to debian-testing though. :KS

why is firefox becomming "windows crapware"? Its multiplatform (obviously)... and just because it requires a higher gnome version then dapper has in the dapper repos now firefox is now crap? i dont see the reasoning behind it.

and the LTS doesnt recieve anything but security fixes because the whole point of a LTS is that nothing major is going to be updated, so if its working now, it will be working a couple of years later cause the only thing thats been changed are some security fixes. If they updated everything then there would be a bigger chance of some package making something else unstable... etc

---

### Post by Kujen on 2007-05-17
> **banjobacon said:**
> Why run an LTS version of Ubuntu if what you really want is new software?

End of discussion right there.

---

### Post by gnomeuser on 2007-05-17
I don't really see a problem, maintaining compatibility with older libraries is a great deal of work and considering that it's free to upgrade (with Ubuntu it's even dead easy) I doubt it's worth the effort to Mozilla to officially support these users. They give us the code, something like IceWeasel can add the support if they like.

Now hopefully by the time Firefox 3 is a relevant thing to actually worry about, we'll have a new LTS release which they can support. In the meantime one should rejoice in the fact that Dapper is a LTS release and as such is not expected to make a major change like replacing Firefox (since half the desktop depends on it) without good cause.. oh shiny doesn't strike me as good enough.

Really.. we have the code, they already have wide support for at the time of shipping of FF3 old distros, I don't really see a problem.

---

### Post by zugu on 2007-05-18
> **banjobacon said:**
> Why run an LTS version of Ubuntu if what you really want is new software?

What's more reasonable to you? Upgrading the whole OS just to get Firefox 2 (Dapper's case), or removing FF1.5  and installing FF2 without upgrading the whole OS?

I can't believe there are people who love the idea of software tied to a specific version of the OS.

---

### Post by steven8 on 2007-05-18
> **zugu said:**
> What's more reasonable to you? Upgrading the whole OS just to get Firefox 2 (Dapper's case), or removing FF1.5  and installing FF2 without upgrading the whole OS?

I can't believe there are people who love the idea of software tied to a specific version of the OS.

I have to agree with this one, because I fell into that catagory.  I was very happy with Dapper, but moved to Feisty (and I love it) because I wanted to move to Firefox 2.  I read that you could install Firefox 2 on Dapper, but don't remove 1.5 because it was too 'tied in' to the system.  I didn't want that.  I just wanted to upgrade, but couldn't, so I moved to Feisty.  As I said, I love Feisty, but it was disappointing.

---

### Post by salsafyren on 2007-05-18
> **zugu said:**
> What's more reasonable to you? Upgrading the whole OS just to get Firefox 2 (Dapper's case), or removing FF1.5  and installing FF2 without upgrading the whole OS?

I can't believe there are people who love the idea of software tied to a specific version of the OS.

I agree 100%.

It is simply bad practise to tie in the browser so much to the system.

We need a clean architecture, so we can remove the browser without bringing instability and bugs to the desktop.

Also, upgrading a whole OS to get a new application is also a bad design. It means that your system is too tightly integrated.

---

### Post by PriceChild on 2007-05-18
But this is how we work in Linux?

We use shared libraries etc. to prevent having to do the same thing over and over and over again.

Why don't we just get rid of all dependencies etc. If you want to install gnome it comes bundled with xorg 7.2 If you want to install KDE it comes with a seperate xorg7.2

---

### Post by steven8 on 2007-05-18
> **PriceChild said:**
> But this is how we work in Linux?

We use shared libraries etc. to prevent having to do the same thing over and over and over again.

Why don't we just get rid of all dependencies etc. If you want to install gnome it comes bundled with xorg 7.2 If you want to install KDE it comes with a seperate xorg7.2

Actually, my disappointment was in the fact that I used MS's massive integration of IE into their system as a lock-in maneuver, and Linux's wide-open stance that the user could even 'get rid of the provided browser if they wish and install another', as part of my reasoning to get my wife to change from windows to Linux.  I thought I was telling a truth, because I didn't know.  That was my disappointment.

---

### Post by Rhapsody on 2007-05-18
> **zugu said:**
> What's more reasonable to you? Upgrading the whole OS just to get Firefox 2 (Dapper's case), or removing FF1.5  and installing FF2 without upgrading the whole OS?

I can't believe there are people who love the idea of software tied to a specific version of the OS.

I've been thinking about the idea of a 'semi-stable' Linux distro myself, where the apps are upgraded to the latest stable version as they come, but OS components are kept stable except for security updates. This would be a halfway house between 'stable' distros (Ubuntu, Debian, Fedora, etc) and 'unstable' distros (Gentoo, Arch, etc), with most of the desirable effects of the latter but most of the stability of the latter (new apps are unlikely to kill a whole system).

The only operating systems I can think that work like this are Windows and Mac OS X (though they do it in something of a haphazard way), so it's not like it's an unknown idea.

I find it hard to believe this hasn't been done by at least one distro already. Why isn't it done more often? I'd certainly love to see it.

---

### Post by ReiKn on 2007-05-18
> **zugu said:**
> What's more reasonable to you? Upgrading the whole OS just to get Firefox 2 (Dapper's case), or removing FF1.5  and installing FF2 without upgrading the whole OS?

I can't believe there are people who love the idea of software tied to a specific version of the OS.

How do you define the OS? I think the ubuntu definition is more or less that the OS version is the ensemble of tested software components (and versions of the chosen software). To be more specific, where do you think the limit goes; which program upgrades would qualify as an whole OS upgrade and which parts should be easily upgradeable without touching too many other packages?

In the case of firefox 3 it would need a whole new version of gnome. That at least in my scale would qualify as an OS update as it changes the desktop environment. Should ubuntu really re-engineer half of dapper just to get the new version running?

I agree that it would be nice to have the new features of the new browser rather easily. But firefox is also a key component of the desktop environment, which as such when upgraded would need careful testing and maybe upgrading and testing a bunch of other stuff as well, especially in a LTS release like 6.06.

---

### Post by zugu on 2007-05-18
> **Rhapsody said:**
> I've been thinking about the idea of a 'semi-stable' Linux distro myself, where the apps are upgraded to the latest stable version as they come, but OS components are kept stable except for security updates. This would be a halfway house between 'stable' distros (Ubuntu, Debian, Fedora, etc) and 'unstable' distros (Gentoo, Arch, etc), with most of the desirable effects of the latter but most of the stability of the latter (new apps are unlikely to kill a whole system).

The only operating systems I can think that work like this are Windows and Mac OS X (though they do it in something of a haphazard way), so it's not like it's an unknown idea.

I find it hard to believe this hasn't been done by at least one distro already. Why isn't it done more often? I'd certainly love to see it.

That would be awesome. Imagine a core built in a similar-to-BSD manner - with basic software frozen to stable versions (xorg, kernel, etc). And then GNOME, KDE, GIMP, Konqueror, XMMS, whatever - on top of it, where the applications can be removed / upgraded at one's discretion. The packaging could be an issue for some time, because various distros use different formats, but once we have a *platform*, and developers start developing on it, they will be the only ones responsible for the dependency issues that arise.> **ReiKn said:**
> How do you define the OS?An OS is exactly what it is: an operating system. Ubuntu is an OS plus a plethora of applications. Ubuntu is *not* challenging the definition of "OS" (as you're implying). The repositories exist not because Ubuntu wants us to rethink the definition of an operating system, but because it would be unusable for the common user otherwise.

---

### Post by ReiKn on 2007-05-18
> **zugu said:**
> That would be awesome. Imagine a core built in a similar-to-BSD manner - with basic software frozen to stable versions (xorg, kernel, etc). And then GNOME, KDE, GIMP, Konqueror, XMMS, whatever - on top of it, where the applications can be removed / upgraded at one's discretion. The packaging could be an issue for some time, because various distros use different formats, but once we have a *platform*, and developers start developing on it, they will be the only ones responsible for the dependency issues that arise. 

Could one use debian unstable in quite this manner? Just upgrade those packages that you want? I'm not sure about this though..

> **zugu said:**
>  An OS is exactly what it is: an operating system. Ubuntu is an OS plus a plethora of applications. Ubuntu is *not* challenging the definition of "OS" (as you're implying). The repositories exist not because Ubuntu wants us to rethink the definition of an operating system, but because it would be unusable for the common user otherwise.

Ok. I was merely asking what basic software do you mean with "with basic software frozen to stable versions (xorg, kernel, etc)". But still I kind of get the point so let's not argue that any further (unless you insist). Maybe I should change the abbreviation OS to distribution. Which software should one be able to upgrade without upgrading the whole distribution? All on top of xorg? all besides the kernel? Clearly at least the distribution version in ubuntu world seems to be defined in the way I erroneously defined the OS. (the ensemble of specific tested, compatible versions of software...)

---

### Post by salsafyren on 2007-05-18
There is definitely a need for another kind of "distro".

This could easily be a Ubuntu core, and then some sort of 3rd-party package manager (would zeroinstall work?).

I would like to help out doing such a distro, doing it all alone is too big a task.

---

### Post by banjobacon on 2007-05-18
Isn't there a way to compile Firefox in a static binary so that it would solve this problem for people who insist on using the latest version of Firefox on on unsupported distros?

---

### Post by salsafyren on 2007-05-18
> **banjobacon said:**
> Isn't there a way to compile Firefox in a static binary so that it would solve this problem for people who insist on using the latest version of Firefox on on unsupported distros?

gtk, glib maybe, but not dbus and hal, I think.

---

### Post by Adamant1988 on 2007-05-18
> **salsafyren said:**
> I just saw the proposed requirements for Firefox 3.

[http://wiki.mozilla.org/Linux/Runtime_Requirements](http://wiki.mozilla.org/Linux/Runtime_Requirements)

They propose Gnome 2.16.X, dapper only has 2.14.

This is really crazy. Do I really have to upgrade my distro just to use the newest browser?

Mozilla really doesn't care about Linux.

Such is the nature of not upgrading with the times, even though Dapper is only about a year old, it's so antiqued to the point that it's like using Windows ME now.

---

### Post by Hobbsee on 2007-05-19
> **Rhapsody said:**
> I've been thinking about the idea of a 'semi-stable' Linux distro myself, where the apps are upgraded to the latest stable version as they come, but OS components are kept stable except for security updates. This would be a halfway house between 'stable' distros (Ubuntu, Debian, Fedora, etc) and 'unstable' distros (Gentoo, Arch, etc), with most of the desirable effects of the latter but most of the stability of the latter (new apps are unlikely to kill a whole system).

You'd probably get a whole heap of unsupported hardware if you did that - seeing as a lot of the drivers for hardware get updated each kernel...

My laptop doesnt even get X on dapper - and I only bought the laptop last year.

---

### Post by TheMono on 2007-05-19
The only reason to run Dapper is stability and predictability. If those are your goals, then new versions of XMMS and Firefox aren't really the end of the world.

---

### Post by andrew.46 on 2007-05-25
Hi,

 I read your post with interest:

> **Adamant1988 said:**
> Such is the nature of not upgrading with the times, even though Dapper is only about a year old, it's so antiqued to the point that it's like using Windows ME now.

 Can I politely disagree with your 'upgrading with the times' idea. I think it is a mistake to leapfrog from one version of an OS to another blindly looking forward to the next version in 6 months. It matters more what you can accomplish with the tools available to you, whether that be Feisty, Dapper or Windows ME. Well I am not so sure about Windows ME ;)

                  Andrew

---

### Post by Bachstelze on 2007-05-25
That's crazy, Firefox requires X ! Which means I cannot run it on my 60 MHz with 16 MiB of RAM which runs Debian Potato. Mozilla really doesn't care about Linux !

---

### Post by bikeboy on 2007-05-25
The **proposal** looks perfectly good and sane to me.

There are 3 paragraphs on the wiki there, all of which show that the Linux community and the workability of the proposal are the top priorities. I could quote any of the paragraphs to support my view that they have every right to change the runtime requirements and are proposing to do it in a responsible way, I'll choose just this quote.
> Distros providing longer-term support (i.e. enterprise distributions with long lifecycle requirements and older libraries) will be responsible for maintaining support for older runtimes via build-time switches. This is in line with how many other apps are supported by the distros.

Note, build time switches, so you *are* going to be able to run Firefox 3 on Dapper if you know how, it's just going the be that Mozilla themselves won't have to do the extra supporting work. If you want new software on a stable release, you will have the option of building with the right switches. Taking bets on the number of hours after Fx3 release before someone writes a howto and it becomes a non-issue...

---

### Post by PatrickMay16 on 2007-05-25
> **salsafyren said:**
> I just saw the proposed requirements for Firefox 3.

[http://wiki.mozilla.org/Linux/Runtime_Requirements](http://wiki.mozilla.org/Linux/Runtime_Requirements)

They propose Gnome 2.16.X, dapper only has 2.14.

This is really crazy. Do I really have to upgrade my distro just to use the newest browser?

Mozilla really doesn't care about Linux.

I see it as a bonus. Firefox has really started to suck with version 2, I can only imagine what 3 will be like. Heh heh heh heh... Just kidding.

---

### Post by eeried on 2007-08-01
> You can compile FF2 on Dapper, but it's not for the faint of heart
Oh yes: just download the tar.gz fle from mozilla.com and untar it where you want Firefox to be installed /opt, for instance.

Pre-compiled binary tar.gz files are that easy to install.

Of course installing Firefox 3 on dpper would be more difficult until someone finds a way and share it with us all.

By the way you can install thunderbird 2 on Feisty, too. :)

Three cheers for Dapper which is better with older software than Edgy or Feisty.

PS: you can unistall firefox 1.5 from Dapper -- only it removes ubuntu-desktop which isn't useful until you want to upgrade to Edgy through the network. When you want to do that, you only have to reinstall ubuntu-desktop. If you don't have DSL you won't upgrade to a newer version of ubuntu through the network, anyway.

So removing ubuntu-desktop, or even ubuntu-minimal is no big deal. TSo says the documentation. I've got rid of all I don't need on my Xubuntu feisty (printing, gaim, in particular, which makes the system swifter on my old PII 400MHZ. Of course I have no printer...)

So you can't compare IE on M$Windoze and Firefox on Linux: the integration is no way similar. To remove IE you really have to install PCLight (and reinstall windoze)  or at least that was my experience with Windows98).

If you want even less integration go Debian.

---

### Post by Incense on 2007-08-01
It is very easy to run FF2 on dapper without removing 1.5. But really, why would  you want to? 1.5 was a solid release. I read everywhere about how much FF2 crashes, how bloated it is... The only reason I would want to upgrade, is for the built in spell check. :D

---

### Post by eeried on 2007-08-02
Everytime a new version comes out reports fliy about saying it Firefox keeps crashing, and is bloated.

The problem with Firefox 1.5 may be that it will no longer be maintained, or is already no longer maintained by the Mo/Fo-Co. On this forum I read the Ubuntu team would still deliver security patches even if Mozilla no longer does.
cheers

---

### Post by zugu on 2007-08-02
> **eeried said:**
> Everytime a new version comes out reports fliy about saying it Firefox keeps crashing, and is bloated.

The problem with Firefox 1.5 may be that it will no longer be maintained, or is already no longer maintained by the Mo/Fo-Co. On this forum I read the Ubuntu team would still deliver security patches even if Mozilla no longer does.
cheers

Yes, but just because you like the 1.5 branch more doesn't make it less of a problem. People will still not be able to run Firefox 3 on Dapper (if I remember correctly, not even FF2 made it in the repositories), unless they use hacks, third party debs or testing repositories.

I think the problem here is much worse, it's this time-based release model of Ubuntu, with no respect to new versions of software and new features.

---

### Post by Crashmaxx on 2007-08-02
> **zugu said:**
> Yes, but just because you like the 1.5 branch more doesn't make it less of a problem. People will still not be able to run Firefox 3 on Dapper (if I remember correctly, not even FF2 made it in the repositories), unless they use hacks, third party debs or testing repositories.

I think the problem here is much worse, it's this time-based release model of Ubuntu, with no respect to new versions of software and new features.

Its not a problem, because LTS releases are meant to be unchanging for use in servers or for people that otherwise want a rock solid system. You can install Firefox 2 without too much difficultly on Dapper, if you so desire. But I'm sure the recommend policy is to just upgrade to Feisty.

Regardless, running Alpha software on a LTS distro, goes completely against the whole point of the distro, and would be considered a hack in itself. Demanding that Alpha software be back ported to a intentionally stable release is absurd.

I see nothing wrong with the time based release schedule, and think it helps the distro be very stable and integrated and allows devs to focus on moving ahead with improvements.

If you have a problem with this, and want all packages as soon as they are stable, then I recommend you switch to Debian Testing.

And if you have to be on the bleeding edge and run Alpha software, then perhaps Debian Unstable, or Experimental is what you want.

BTW, Ubuntu is based on Debian Testing which is very stable, unlike the name suggests.

---

### Post by jrusso2 on 2007-08-02
> **banjobacon said:**
> Isn't there a way to compile Firefox in a static binary so that it would solve this problem for people who insist on using the latest version of Firefox on on unsupported distros?

Opera already offers a static .deb and .rpm package, I don't see why this couldn't be done with Firefox 3.

This would make upgrades easier.

I have used the Opera static binaries  many times and they work well.

---

### Post by FuturePilot on 2007-08-02
There's no point in building a Firefox binary for a specific distro because it's already in binary format. All you need to do is extract it to /opt do a few more commands and you've got the latest version of Firefox. I'm running the latest Firefox 2.0.0.6 right now on Dapper.

---

### Post by zugu on 2007-08-09
> **ReiKn said:**
> Could one use debian unstable in quite this manner? Just upgrade those packages that you want? I'm not sure about this though..

Debian unstable is not an operating system recommended for common daily usage. It is a test bed for packages. Why would I want to use that? The only real, supported and advertised version is Debian stable, and it cannot be used in the manner I described, either.

Of course, I could go grab some .deb file from third party repositories, but we all know it's dangerous to use such repos. I could compile it myself, if I had the knowledge, but it will certainly break things, as all compiled software is software that the apt-get package manager is not aware of. This can easily break dist-upgrades.

So the only choice left is to dist-upgrade to the latest stable version every six months in order to get access to newer versions of basic things like the browser, the media players, the IM application and so on.

Even Windows lets me install whatever I want and doesn't force me to upgrade every 6 months.

---

### Post by zugu on 2007-08-09
> **FuturePilot said:**
> There's no point in building a Firefox binary for a specific distro because it's already in binary format. All you need to do is extract it to /opt do a few more commands and you've got the latest version of Firefox. I'm running the latest Firefox 2.0.0.6 right now on Dapper.

And how is the integration with the OS? I bet it's not the same as with the official version.

---

### Post by bikeboy on 2007-08-09
It's pretty close actually. Once you set it as the preferred app, the only thing I notice that's different is a few bookmark and search plugin customisations. Not particularly important.

---

### Post by insane_alien on 2007-08-09
so, on the one hand, we have dapper, a solid OS that was designed to only have security updates but otherwise remain static. primarily used for servers that aren't going to be changed for years.

on the otherhand, we have users on this who want the latest and greatest software. i think the users picked the wrong distro.

should the mozilla devs go out of their way to make firefox 3 compatible with BBC's? or how about windows 1.1?

obviously, the older version of gnome in dapper is missing some sort of functionality that the newer gnome has and the newer firefox uses. either because it is more stable more secure has more features or most likely a mixture of them all.

if you want the latest and greatest, use something like gentoo or at the least feisty. if you want stability, don't bother with anything but security updates and go for dapper.

and as has been mentioned before, if you really need it that bad you have two choices, upgrade the distro or compile it yourself.

---

### Post by zugu on 2007-08-10
And did you ever fantasized about having all the latest and greatest AND enjoying stability from your operating system? 

I personally find Windows XP to be both stable and allowing me to run all the latest and greatest. Of course, this is just how **I** feel, but because of that I would like to see something similar in Linux.

---

### Post by Crashmaxx on 2007-08-10
> **zugu said:**
> Debian unstable is not an operating system recommended for common daily usage. It is a test bed for packages. Why would I want to use that? The only real, supported and advertised version is Debian stable, and it cannot be used in the manner I described, either.


Testing is fine. Ubuntu is based on Debian Testing and we simply freeze the package updates every six months. Debian Stable is all about servers, I can't see anyone wanting to use it on a desktop with it being so old.

So if you don't want to wait for a new release all the time, then using Debian Testing is the way to go. You will get all the newest packages as soon as they are tested enough to be stable.

> Of course, I could go grab some .deb file from third party repositories, but we all know it's dangerous to use such repos. I could compile it myself, if I had the knowledge, but it will certainly break things, as all compiled software is software that the apt-get package manager is not aware of. This can easily break dist-upgrades.

But Firefox 3 is total Alpha, it goes against everything you are saying about stability. It is sure to be full of bugs and crash a LOT. Why you would even think about it for daily use is beyond me.

---

### Post by g2g591 on 2007-08-10
actually firefox 3 alpha 7 is fairly stable, its the nightly builds that are where the breakage happens.

---

### Post by Joer4x4 on 2007-08-11
> **PriceChild said:**
> But this is how we work in Linux?

We use shared libraries etc. to prevent having to do the same thing over and over and over again.

Why don't we just get rid of all dependencies etc. If you want to install gnome it comes bundled with xorg 7.2 If you want to install KDE it comes with a seperate xorg7.2

There is nothing wrong with shared libraries and dependencies. It's the nature of the beast.

What is wrong then? It's either conceptual or design. There is no excuse for not allowing users to use the latest version of a given application for its new features or security. To expect users to swapout their systems every year for the latest applications is unreasonalble. It does not make sense nor is it cost effective. Each upgrade should be backward and forward compatible for years.

This is why there is no 3rd party application software availble for Linux. If I wanted to start a business I'd have to go back to MS. Commercial developers don't want to rewrite their applications every year due to OS changes. 

For instance, my mapping software I bought 6 years ago can still be run along with latest versions of OO, FF, and whatever. It it were Linux based, I suspect I would have to repurchase it 3 or 4 times already! That's crazy! Except for security changes, there is no reason to constantly change the core of an OS. It makes it harder and costly for everyone involved.

As I read many think Firefox is bloatware. I think that's a perception based on performance (execution time). I know programs that are twice the size of FF and run blazingly fast. I think either XUL was a poor choice to write code or they need to work on the optimizing compiler. Mozilla products are very good but very poor performers. 

"But this is how we work in Linux" sums it up. Linux is about what I (the developer) wants to do - not what's good for the end user. As much as I dislike MS, I give them credit for making it easy on the user.

Having delt with Linux for over a year now, that's how I see it.

---

### Post by angryfirelord on 2007-09-21
> **zugu said:**
> Debian unstable is not an operating system recommended for common daily usage. It is a test bed for packages. Why would I want to use that? The only real, supported and advertised version is Debian stable, and it cannot be used in the manner I described, either.

Of course, I could go grab some .deb file from third party repositories, but we all know it's dangerous to use such repos. I could compile it myself, if I had the knowledge, but it will certainly break things, as all compiled software is software that the apt-get package manager is not aware of. This can easily break dist-upgrades.

So the only choice left is to dist-upgrade to the latest stable version every six months in order to get access to newer versions of basic things like the browser, the media players, the IM application and so on.

Even Windows lets me install whatever I want and doesn't force me to upgrade every 6 months.
A lot of Debian users run Testing, which in reality should be called "tested" because the packages can only have so many bugs before they are pulled from Unstable. That way, you can have close to the latest and greatest without having to worry about breaking your system.

Personally, I'm fine with the 6 month upgrade cycle. All I do is backup my $HOME directory and do a fresh install. It's not like you have to pay $99+ for every new release of Ubuntu. ;)

---

### Post by bruce89 on 2007-09-21
Why do so many people use Dapper, it's anchient.

Do people think that Dapper is the latest stable or something?

---

### Post by TeraDyne on 2007-09-21
> **bruce89 said:**
> Why do so many people use Dapper, it's anchient.

Do people think that Dapper is the latest stable or something?

It's an LTS release, and it probably works better for them.

Meh, I don't have any real say in FF stuff. I have avoided it since 1.5.0. and use SeaMonkey instead.

---

### Post by bruce89 on 2007-09-21
Mozilla are taking the piss with their version numbers.

> **TeraDyne said:**
> It's an LTS release, and it probably works better for them.

It seems odd that the OP is using Dapper and demanding the latest version of something.

Gutsy has grand paridiso in the repos.

---

### Post by TeraDyne on 2007-09-21
> **bruce89 said:**
> It seems odd that the OP is using Dapper and demanding the latest version of something..

People with the several years old Windows XP get new versions of Firefox. Dapper isn't even two yet. I think that's part of the problem.

---

### Post by bruce89 on 2007-09-21
> **TeraDyne said:**
> People with the several years old Windows XP get new versions of Firefox. Dapper isn't even two yet. I think that's part of the problem.

Are you saying that shared libraries aren't worth the advantages?

That's not how packaging works. Free Software advances at a huge rate and programs start depending on newer things. 6 months is a long time in FOSS.

If you want the latest stuff, run Gutsy.

Firefox 3 could be run on Dapper, it just requires backporting loads of libraries (GTK+, Glib, cairo, Pango, DBus, HAL)

---

### Post by TeraDyne on 2007-09-21
bruce, you didn't get what I ment. You're saying that he's asking for something new while running an old operating system. I was pointing out that WinXP is older than Dapper by several years, and they still get the latest. As a result, some users expect being able to run the latest on an older OS.

---

### Post by angryfirelord on 2007-09-21
> **TeraDyne said:**
> People with the several years old Windows XP get new versions of Firefox. Dapper isn't even two yet. I think that's part of the problem.
The whole point of using a stable release is that the package versions don't change. I wouldn't exactly call windows a "stable" platform. Plus, how many libraries does the Windows version of firefox have in order to make it work with XP?

---

### Post by Polygon on 2007-09-21
dapper is perfectly capable of running ff 3

the thing is, they dont do major upgrades of programs after an ubuntu release comes out. Why? because it might cause other problems that cascade into other things breaking. For example, in Fesity, thunderbird 2 came out, but it never got put into the feisty repos because making the jump from like 1.5.0.12 or whatever to 2, it goes against the ubuntu policy

this is really important in LTS releases, which are designed to be as stable as possible, so they throughorly test the OS and all the programs that are in the repos to make sure stuff doesnt break, and doing a major upgrade of a package is a good way to introduce problems

so thats the downside of using a LTS release. its more stable, but you have to use outdated stuff until the next LTS comes out (if you stick to the repos)

---

### Post by Joer4x4 on 2007-09-23
> **bruce89 said:**
> Why do so many people use Dapper, it's ancient.

Do people think that Dapper is the latest stable or something?

Perhaps since over 60% of internet users use dialup you have to ask the question - Is it worth tying up your phone line for 2 days just to update every 6 months and then go through the hassle of reconfiguring their ppp  or whatever else fails which is a pain? What they have now is working.

I think this is another nail in the coffin for Linux. Every day users just want to get their work done without added fuss. They don't care about (nor should they) the technical details. Those that do care just want to update what they already have with the latest and greatest.

Personally, I think the way the 6 month cycle to a new release is done is crazy. It just introduces the possibility of higher error rates. Release updates can be done without changing the whole OS every time. If the latest software cannot be made available on what is current then something is inherently wrong! 

I'm still on Dapper because it works fine. I know when I go to the next release something will fail and if that failure involves internet access (**which is needed to fix it**) then I'm hosed and have nothing (*amazing how common sense points out the big picture*)! Besides, I really don't have time to fuss with software these days...I just want it to work for me.

If I can't get to the next long term release from Dapper, then I'll go elsewhere. It took me a week to get dapper going and I don't want to go through that again!

Will Linux ever get it?

---

### Post by andrew.46 on 2007-09-23
Hi,

Read your post:

> **Joer4x4 said:**
> 
Personally, I think the way the 6 month cycle to a new release is done is crazy. It just introduces the possibility of higher error rates. Release updates can be done without changing the whole OS every time. If the latest software cannot be made available on what is current then something is inherently wrong! [...]
Will Linux ever get it?

Of course not all Linux distros release quite so ambitiously. Slackware for instance only releases when Pat is ready to release :-)

              Andrew

---

### Post by kerry_s on 2007-09-24
[https://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2007-09-22-04-trunk/firefox-3.0a9pre.en-US.linux-i686.tar.bz2](https://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/2007-09-22-04-trunk/firefox-3.0a9pre.en-US.linux-i686.tar.bz2)

i run it out of my user account.

---

### Post by drivel on 2007-09-24
maybe,firefox is a part of Gnome....

---

### Post by missmoondog on 2007-11-02
joer4x4 is pretty close to how i feel about linux/kubuntu. upgrading to a whole new version every 6 months is insane. i installed dapper because of the lts and i know this old machine can't handle much more! was just searching for updating firefox when i found this thread. never have cared for firefox anyway, but do like being up to date on security issues, and firefox sure has those!

---

