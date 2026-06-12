---
title: "No updates for lil apps"
date: 2006-12-25
forum: Ubuntu Backports
---

### Post by grizzly on 2006-12-25
Thanks to the 3 year support for dapper I planned to use it on a long term basis without updating the distro, but now I am forced to reconsider this due to this backports thing. 
No I am not against the concept of backports, but if I have understood this correctly the thing is , unless anybody is kind enough to backport a particular application(unrtf), I am stuck with the old(ancient?) version of the application till I update my distro (which I can't !). Rght?  
i.e if I apt-get install unrtf version (1.1) , the only way I can update ( without facing dependency hell) is update my distro. compiling and alien both give dependency hell.

I know popular apps will get backported , but there are many non-popular apps that get updated every 3-4 months or so that I use ( pilot-link,plucker-build etc ). Am I asking too much for something thats free or is there something I am completely missing? Isn't there any other way I can update apps without fuss? compiling would be 'fuss' for me.

Thanks

---

### Post by jtfolden on 2006-12-25
Yes, I quite agree that this is a rather major issue over the long term. The idea that a user is essentially 'stuck' with what's available at the time of a distro's release date is a rather sad state of affairs.

I'd much rather have an app bundled with included/static links to libraries at the expense of hard drive space rather than to go without all together. The average person moving to Linux is going to expect to be able to upgrade to the latest and greatest of his often used apps to take advantage of features and misc bug fixes. One shouldn't have to upgrade the whole distro to solve this problem...

---

### Post by PriceChild on 2006-12-25
"stuck" "Stuck!"?

What's wrong with dapper? Its a completely solid distro which will be as solid for the next 2 1/2 years and after.

Is there really any reason you want updated packages? Or just because the version number is higher?

You can always try "prevu" to backport on your own.

---

### Post by jtfolden on 2006-12-25
> **PriceChild said:**
> "stuck" "Stuck!"? 

Yes, "stuck"...


>  What's wrong with dapper? Its a completely solid distro which will be as solid for the next 2 1/2 years and after.

Is there really any reason you want updated packages? Or just because the version number is higher? 

As mentioned, there are many times where a particular app update provides a useful feature or fix. Sure, sometimes a 'bleeding edge' version might be more trouble than it's worth but just as likely it might contain that new feature that a person shouldn't need to wait 6-12 months for - or should need to upgrade distros just to take advantage of.

I mean, I can't imagine a world where a new version of Mac OS X is released but you can - generally - only run apps that were available up until it's release day, meanwhile newer apps sit on a server somewhere that can only be run on an OS revision that won't be available for 6-12 months. it seems counter-productive, imo. 

John

---

### Post by meng on 2006-12-25
This is the tradeoff involved with repository-based software: on the plus side, stability, compatibility and ease of use; on the down side, you may be "stuck" with an older version.

You can update to a new version by finding a .deb file somewhere else (unofficial repositories or other third-party location) or by compiling from source.

Really, this is not all that different from installing software for Windows. You're better off fixing the problem than bellyaching about it.

---

### Post by PriceChild on 2006-12-25
If you're that desperate to update then just go edgy...

---

### Post by grizzly on 2006-12-25
> Is there really any reason you want updated packages?  I don't want updated packages but 'update my applications that i use regularly! like krusader,viewglob, zsh, amarok!!

>  This is the tradeoff involved with repository-based software But does it have to be that way? i mean there are extra repos for amarok, wine. The thing is that after a new OS is realeased the old OS is kind of abandoned. Its like after xp is realeased nobody can use updated apps in 98 *winthout fuss*

> You can update to a new version by finding a .deb file somewhere elsewon't this give dependency problems? updated debs would require updated libraries which in turn would rquire updated other libraries and so on..

---

### Post by jtfolden on 2006-12-25
> **meng said:**
> This is the tradeoff involved with repository-based software: on the plus side, stability, compatibility and ease of use; on the down side, you may be "stuck" with an older version. 

Isn't it really just part of the fall out from the whole dependency issue (well, that and the fact there's no standard package management system across the board)? I mean, if I download an app for OS X 99% of the time all I need is a single file, it's a DnD install and I don't need to add anything else to the system... With Linux, for the same app, I might need to install 6 other dependencies and any one of those might break something else already installed...

>  You can update to a new version by finding a .deb file somewhere else (unofficial repositories or other third-party location) or by compiling from source. 

...and if the program author (or other maintainer) provides a specific .deb for the software you need then that's great and not a problem at all but it's my understanding that just any .deb won't work... for example, grabbing a release from the Debian Unstable repository might not be a great idea, right? Quite a few authors don't provide the downloads and refer you back to the producer of your specific distro which leaves you where you started.


> Really, this is not all that different from installing software for Windows. You're better off fixing the problem than bellyaching about it.

The "problem" is an issue with the distribution method as created by the developer communities, not by it's users. On Windows (blech) or OS X, it's very easy to update just about any App with a single download. There are plenty of people running an OS X release that's 2+ years old but they can still download the latest version of program "a" and install without issue. So the upgrade handicap with Linux really isn't the same.

It's a valid issue... it may not be important to you but that doesn't change the facts of the situation.

---

### Post by jtfolden on 2006-12-25
> **grizzly said:**
>  But does it have to be that way? i mean there are extra repos for amarok, wine. The thing is that after a new OS is realeased the old OS is kind of abandoned. Its like after xp is realeased nobody can use updated apps in 98 *winthout fuss*

Actually, it's a far worse scenario, imo. Imagine XP coming out in 2002, but you only being able to run Windows apps that were released up until that date (unless someone goes out of their way to make a special package). Meanwhile maintainers create app updates but they're only compiled for future releases of Windows (whether they're available to users or not). It makes more sense if the updates are made available for the distros that are available and currently supported, that people are actually using, rather than some unattainable future target.

I mean, I can download a single, official, file and install OpenOffice 2.1 on Windows 2000 (a 6 year old OS) but I don't even have that option for Ubuntu Edgy or Dapper, both released in the last few months.

---

### Post by PriceChild on 2006-12-25
> **jtfolden said:**
> I mean, I can download a single, official, file and install OpenOffice 2.1 on Windows 2000 (a 6 year old OS) but I don't even have that option for Ubuntu Edgy or Dapper, both released in the last few months.I strongly disagree.

If you really want to update your apps... then update them by building yourself or finding other packages.

Dapper is released as stable and that is not going to be compromised, which I'm sure you would agree is a good thing.

---

### Post by jtfolden on 2006-12-25
> **PriceChild said:**
> I strongly disagree. 

You strongly disagree with what exactly? That a user should have a choice to easily upgrade apps without having to update the whole Distro? It's extremely easy to update most apps on OS X or Windows without effecting the stability of the core OS.


>  If you really want to update your apps... then update them by building yourself or finding other packages. 

I don't think the average user needs to be told they need to build something themselves. A lot of people want to USE the apps, not build them from scratch... Imo, the "Backports" repository, or similar, should be just as important and populated after the release of a distro as the other repos were populated before it's release. Especially for releases that are "supported".

> Dapper is released as stable and that is not going to be compromised, which I'm sure you would agree is a good thing.


Stability is a great thing but a) if simple app upgrades compromise stability of the core OS then this is simply further data that distribution methods need re-thought, and b) it should be up to the user to decide whether they want to stick with an OS as delivered or update portions of it. This problem isn't confined to Dapper in any case. There are already newer packages not available to Edgy - like the previously mentioned OO 2.1 (which the request for a backport has been summarily rejected).

Furthermore, Dapper might be a greatly polished release but it still contains software with bugs and oddities or incomplete/missing features. It's not perfect, hence the need for users to have the ability to easily upgrade frequently used apps.

---

### Post by az on 2006-12-25
> **jtfolden said:**
> You strongly disagree with what exactly? That a user should have a choice to easily upgrade apps without having to update the whole Distro? It's extremely easy to update most apps on OS X or Windows without effecting the stability of the core OS.

That's because they maintain binary-compatibility between versions.  In the linux world, everything is actually a lot more compatible, but on a source-code level.  The practical advantages are that developing the software is a lot easier and less restricted.  It's a little harder to exploit seciruty vulnerabilities, too.

The dissadvantage is that you can not generally click 'n' run applications willy-nilly. 


> **jtfolden said:**
> 
I don't think the average user needs to be told they need to build something themselves. A lot of people want to USE the apps, not build them from scratch... Imo, the "Backports" repository, or similar, should be just as important and populated after the release of a distro as the other repos were populated before it's release. Especially for releases that are "supported".

It's not that way because people want it to be difficult.  It's that way because there is not enough manpower to make that aspect of the community shine.  Until a lot more people can give backports as much ease and stability, it is a catch-22 - the apps can make the release less stable, so people tend to not want to mess with it.  If there was an army of developers who would solve problems well enough, you would get better backports.

Dapper also has the dapper-updates repo.  It was more heavily used before the xorg breakage.  The dapper-updates (not dapper-security) is meant for new featuers and new versions of packages - just like you mention.

> **jtfolden said:**
> 
Stability is a great thing but a) if simple app upgrades compromise stability of the core OS then this is simply further data that distribution methods need re-thought, and b) it should be up to the user to decide whether they want to stick with an OS as delivered or update portions of it. This problem isn't confined to Dapper in any case. There are already newer packages not available to Edgy - like the previously mentioned OO 2.1 (which the request for a backport has been summarily rejected).

a) again, source-based, not binary-compatible.
b) you are completely free to do it yourself.  The reason that you are complaining is not that you cannot (not allowed, not encouraged), but that it is inconvenient.  A distribution's purpose is to compile all the upstream stuff and deliver it to the user - that's a convenience.  In this case, they are not going far enough in providing that convenience to you.  Yes, it would be nice if that changed.

> **jtfolden said:**
> 
Furthermore, Dapper might be a greatly polished release but it still contains software with bugs and oddities or incomplete/missing features. It's not perfect, hence the need for users to have the ability to easily upgrade frequently used apps.

Dapper-security fixes security vulnerabilities and some bugs.  Dapper-updates fixes some bugs and does add new features.

---

### Post by zmr on 2006-12-26
I would have to second some of the comments by jtfolden. The inability to update packages in Dapper without numerous dependency headaches  seems to be a fundamental flaw that should not be ignored (although I entirely understand that many of these issues come down to matters of manpower etc. as mentioned above). 

Further, what do we mean by "stable" anyways? Does it mean it's using a stable linux kernel? That all of the applications that come with the OS are dependable? Or what is meant by "long term support"?   Does "long term support" mean that people won't help me if I've introduced non-stable apps into my stable OS -- as if the whole idea of long term support is centered around some kind of warranty paradigm? Openoffice 2.1 *is* the latest stable version of OpenOffice. Firefox 2 is the latest stable version of FF. (The people at mozilla want you switch before they cut off support for the old version in a few months). Both introduce fundamental improvements cutting across issues of security and language support. But you can't get either in Dapper without some jumping through some hoops.  Are many of us really sitting back happy with the old Firefox--less secure, less international support and less user-friendly -- just because it's "stable"? 

I realize these are not new issues and there are many factors that need to be addressed. But at the very least I would like to bring into question some of the very assumptions operating behind current Ubuntu distribution practices. To speak casually for the sake of adding some constructive discord, far from "stable" I see dapper as very much a broken OS from the start-- for just the reasons mentioned above (stable not being the latest stable version, the ambiguity of exactly who ubuntu is talking to when they say "long term support,") Again, speaking very generally and casually.

---

### Post by grizzly on 2006-12-26
pity pity. I guess its good-bye to ubuntu then . Unfortunately I will say that ubuntu is kind of cheating people, with the tag of long-term-support. Seriously who the hell will use dapper's so called  long term support? This will get quite embarrasing for the dapper-developers in a year or so, when the dapper-security updates get zero traffic lol . The people cabable of compiling would have moved on to fiesty fawn and those not-so-capable(ppl with lives?) would surely move to other-things (macs,pc-bsd, windows?). 
> If you really want to update your apps... then update them by building yourself or finding other packages.

Dapper is released as stable and that is not going to be compromised, which I'm sure you would agree is a good thing. You mean upgrading firefox to version 2.0 would compromise dapper's stability? 
Edit: ok after reading azz's reply again - the answer is the source-compatibility thing.

> The reason that you are complaining is not that you cannot (not allowed, not encouraged), but that it is inconvenient.
it is not inconvenient compiling  is a HEADACHE!!

> That's because they(windows/macs) maintain binary-compatibility between versions. In the linux world, everything is actually a lot more compatible, but on a source-code level. This sums it up nicely for me! Thank you azz ( nicely explained)
linux == for developers(source code compatible)
windows/macs == users(binary)

I am not saying its a bad thing btw, its just the way it is but seriously don't expect the average joe, who opens the PC to do stuf on it to actually 'use' ubuntu

---

### Post by az on 2006-12-26
> **grizzly said:**
> 
it is not inconvenient compiling  is a HEADACHE!!
Tomato or tom**ah**to?

> **grizzly said:**
> 
 This sums it up nicely for me! Thank you azz ( nicely explained)
linux == for developers(source code compatible)
windows/macs == users(binary)

Actually, there is nothing that says that Ubuntu is only for developers.  It currently is a pain to do certain things as a user in Ubuntu, but you should have seen things just a few years ago!

I have no doubt that these issues will be tackled.  They just currently are unresolved. 

> **grizzly said:**
> 
I am not saying its a bad thing btw, its just the way it is but seriously don't expect the average joe, who opens the PC to do stuf on it to actually 'use' ubuntu

Why not?  Not a lot of people actually need their applications to be cutting-edge.  Most people, in fact, will not use the most current versino of firefox or even microsoft office, for that matter...

---

### Post by PriceChild on 2006-12-26
On machines in familie's houses, most still run office 2000,XP or w/e came with their computer.

They don't really need to update because there's not exactly that much new.

MS just kids you into thinking that new shiny blue interface & new version number makes everything 100 times better... just as you're probably thinking about the version number right now.

---

### Post by az on 2006-12-26
Okay, I'm home now and can better elabotate on a few things...

The package management system we use in Ubuntu is wonderful.  It provides a full-featured, sane and stable way to manage the software.  Considering that the software interfaces on the source code level, that's quite a feat!  However, there are still a lot of things to be ironed out.

Ubuntu is a strealined distro.  It only officially supports a small number of packages.  The rest of the software is supported by the community.  That means that you may or may not get an update to the latest version of firefox, depending on how invasive the changes are.  And if you are using a relatively obscure application from the community-supported repository, you will not get an update.

Now, people who use Debian live a little differently.  To get the most recent apps, they will run Debian Sid.  Every package in Sid has it's own maintainer.  While the distribution itself is unstable, it is pretty much the version of Debian that gets the most attention from developers;  they only really work on Sid packages.  Once they are stable enough and meet criteria, they go into Testing and then eventually into Stable.

Long story short, it's a big deal to run Sid.  How does this help Ubuntu?  No much until the community of packaging ninjas that take care of the Universe repository becomes immense.

Are there other solutions?  Sure.

The packaging infrastructure needs some improvements.  

It should be made a lot easier to integrate new apps or new versions of apps into the released distro.  Currently you have to compile them by hand which involves a few steps:
1- get the packages that the applications needs to be built
2- get the toolchain
3- compile and install the app
4- rinse.  Repeat for all other apps you need.

It should also be easy to use 32-bit apps alongside 64-bit apps.  Currently, you need to install a 64-bit system and then create a 32-bit chroot where you install the 32-bit apps.  The package manager should be smart enough to know to install the 32-bit version of an app into such a chroot and manage it alongside the "regular" 64-bit apps.

When you install something that needs to share a libraby, but you are using a different version of the said library, the app will crash.  It should be able to manage what functions are available from the shared library at run time.  This is currently not so.

I'm sure there is lots more, but I can't think of anything else right now.

What is the solution?  SMART package manager ([http://labix.org/smart)](http://labix.org/smart))?  Autopackage ([http://autopackage.org/)](http://autopackage.org/))?

I dunno.  But it's comming.

---

### Post by jtfolden on 2006-12-26
> **PriceChild said:**
> MS just kids you into thinking that new shiny blue interface & new version number makes everything 100 times better... just as you're probably thinking about the version number right now.

This kind of post makes it sound as though people never thought about software revisions and updates until MS decided to make money on the idea. That's hardly the case.

Furthermore, it seems the people that are justifying the idea that you don't need to update to newer releases on particular Linux distros the most (because you often currently can't) are more concerned about the version number changing than the new features/fixes that come with it. Which is in truth, the exact OPPOSITE of the people who want to upgrade - the version number is irrelevant it's the NEW FEATURES AND IMPROVEMENTS that people want access to in this case. It's not up to any one person to decide for others whether an upgrade is worth it to them or not.

A lot of people don't update Windows or MS Office (or to a lesser extent OS X) on their PCs because it costs $$$$ to do it, not because there aren't true improvements. If the updates were free then you can be sure even my mother would be grabbing a new copy of Office. This is one of the things that draws many of my customers to OpenOffice - because it's free and the updates are free and easy to access and install. People who search out and use apps like FireFox and iTunes, also, tend to stay uptodate on those apps. 

Sure, occasionally, a software update might be more trouble than the last but this is rare (at least it is on OS X) and is no justification for why people don't need updates. This mindset that you should be afraid up updates seems rampant among a select group of desktop Linux users, to a degree I've never seen on any other OS. 

It's a problem. There are valid reasons why the situation is currently as it is in Linux (which Azz points out and seems to have a good understanding of) but it's a problem that needs to be dealt with... this is especially an issue with a distro like Ubuntu, that strives to be for the people.  So, the solution is to work towards fixing this limitation, not to convince others they don't need updates.

Until that time, terms like "Stable" or "Long Term Support" are near worthless on the desktop.

---

### Post by durant1958 on 2006-12-28
I tried to adopt Dapper as my Linux OS several months ago.  

When FireFox 2.0 was released the maintainers basically blew a Raspberry at the world when they were asked when it would appear in the Repos.

This caused me to review my decision to go with the Long Term Support release and eventually I moved over to the OpenSUSE world.

If this problem is going to be addressed in Ubuntu it will have to come down from On-High, the people that are charged with maintaining the Long Term Support just don't get it.

---

### Post by PriceChild on 2006-12-28
durant1958: then use Edgy?

---

### Post by jtfolden on 2006-12-28
> **PriceChild said:**
> durant1958: then use Edgy?

That doesn't seem like a valid option for the people that are drawn to Ubuntu because of the LTS and then find it lacking...

---

### Post by durant1958 on 2006-12-28
> **PriceChild said:**
> durant1958: then use Edgy?

PriceChild,

I installed Edgy on one of my other machines, PIII @466 Mhz old Dell beater, and it runs OK.

That isn't the point.

The point is that Long Term Support means something to most people that is at odds with the Dapper maintainer's definition of LTS.

If any Linux Distro, Ubuntu, Xandros, SUSE, etc, is going to be taken seriously as a replacement for Windows then it will need to support, in a timely fashion, at the bare minimum, the most current versions of the most popular applications on any release of the Distro that is held to be current.

Dapper LTS, because it was designated as LTS, is still a current release of Ubuntu.  So's Edgy, no rule against there being more than one current release.

The work-around that has been promoted on this board for FireFox 2.0 & Dapper is not enough.  Anything that takes you out of the normal patches / upgrade channel violates the ground rules of software maintenance.  At least to the best of my understanding.

I really liked Ubuntu ( Kubuntu ), but I can't take the distribution seriously if it's creators don't see their responsibilities in the same light as the rest of the world does.

Mark Gosdin

---

### Post by PriceChild on 2006-12-28
> **durant1958 said:**
> The work-around that has been promoted on this board for FireFox 2.0 & Dapper is not enough.  Anything that takes you out of the normal patches / upgrade channel violates the ground rules of software maintenance.  At least to the best of my understanding.This life is about compromises... You can't have up to the minute feature updates, but also complete support!

With every feature addition comes more bits of dodgy, unrefined code which probably has holes. You just can't fully support a system like this for a long period of time.

You have to choose whether you want a stable system, or one with a few extra shiny bits.

---

### Post by jtfolden on 2006-12-28
> **PriceChild said:**
> This life is about compromises... You can't have up to the minute feature updates, but also complete support!

With every feature addition comes more bits of dodgy, unrefined code which probably has holes. You just can't fully support a system like this for a long period of time.

You have to choose whether you want a stable system, or one with a few extra shiny bits.


PriceChild, the more you follow this line of reasoning the more you illustrate the major issue that Linux must overcome in order to go mainstream. There may currently be valid, technical reasons as to why Linux is so horribly limited in this respect compared to other OS offerings but the answer is not to make excuses for it but rather to solve the issue and move forward.

I have no trouble taking advantage of the up-to-the-minute new, stable software releases on OS X and, also, getting full support for it.

A static distro used on a server might be fine with LTS, but by the same token LTS on a desktop used by real human beings quickly becomes useless if the software can't be updated during that time. God forbid I'd hate to be stuck running Windows but I can take a 6 year old copy of Windows 2000 and still run the latest version of OpenOffice on it.

---

### Post by PriceChild on 2006-12-28
> **jtfolden said:**
> PriceChild, the more you follow this line of reasoning the more you illustrate the major issue that Linux must overcome in order to go mainstream. There may currently be valid, technical reasons as to why Linux is so horribly limited in this respect compared to other OS offerings but the answer is not to make excuses for it but rather to solve the issue and move forward.I would hardly say horribly limited! You're missing a few features from edgy but most is still the same.

> **jtfolden said:**
> I have no trouble taking advantage of the up-to-the-minute new, stable software releases on OS X and, also, getting full support for it.Noticed how many support updates you get? ;) And how many vulnerabilities are unresolved?

> **jtfolden said:**
>  A static distro used on a server might be fine with LTS, but by the same token LTS on a desktop used by real human beings quickly becomes useless if the software can't be updated during that time.Useless? You really are taking this way too far. The system is perfectly usable. I have many friends still using their Dapper machines despite the Edgy release. They know that dapper is fine for them and they don't really "need" a few extra bits at the price of an unstable release.

> **jtfolden said:**
> God forbid I'd hate to be stuck running Windows but I can take a 6 year old copy of Windows 2000 and still run the latest version of OpenOffice on it.I think a closer comparison would be Microsoft Office... You require Windows XP, Windows server 2003 or newer.

---

### Post by jtfolden on 2006-12-28
> **PriceChild said:**
> I would hardly say horribly limited! You're missing a few features from edgy but most is still the same. 

Unless things change then over the course of it's 3 years of LTS, Dapper will become horribly limited for desktop use With every day that goes by there is more and more software that is unavailable to Dapper users through standard channels. and it's only 6 months into supposed LTS. What's that going to look like 2 years into it? Even Edgy, only 2 months out of the gate, is falling under the same issues, as evidenced by word coming down that OO 2.1 won't be backported.

> Noticed how many support updates you get? ;) And how many vulnerabilities are unresolved? 

In relation to me installing updated apps?  ZERO the last time I checked. A new version of OpenOffice doesn't make the core OS any more/less stable than it already was. It's not like Dapper has been immune to bugs or security holes even sticking with the shipping apps.

>  Useless? You really are taking this way too far. The system is perfectly usable. I have many friends still using their Dapper machines despite the Edgy release. They know that dapper is fine for them and they don't really "need" a few extra bits at the price of an unstable release. 

Again, it gets worse as the days go by and, again, you hi-light it's weaknesses if an updated word processor or web browser or music player drastically effects the core OS.

> I think a closer comparison would be Microsoft Office... You require Windows XP, Windows server 2003 or newer.

That's a really flawed argument. Obviously the closest comparison is made when using the same software. I can install new releases of OpenOffce, VLC, FireFox etc on Windows and OS X without effecting the core OS itself whatsoever.

However, even in the case of MS Office 2007, I can turn around and install it on a version of Windows released nearly 5 years ago.

The average, mainstream user is not going to re-install their system just to get a newer version of a particular app they need and they aren't going to be happy when someone tells them they can't just install a new version on top of what they already have.

I'm happy that the current distribution method/cycle works for you but it doesn't work for everybody - obviously. There's a reason why 70% plus of Debian users and developers tend to spend a good amount of time running Sid.

---

### Post by PriceChild on 2006-12-28
Ok I'm leaving this argument here as we aren't getting anywhere.

I will however leave you with one final idea.... "Maybe Ubuntu isn't for you?"

---

### Post by jtfolden on 2006-12-28
> **PriceChild said:**
> I will however leave you with one final idea.... "Maybe Ubuntu isn't for you?"

Oh, I'll stick around to help move it forward... I have hopes that one day it will be good enough to go on one of my primary systems. It just has a bit of catching up to do in a few areas first.

---

### Post by beefcurry on 2007-01-15
nah I think its just a ubuntu thing. Being a photographer Digikam 0.9 was like WOAOG!! must get! but having to compile it myself was not hard but awefully painful. Same goes with WINE. It gets updated so quickly i wish i could always have the newest one....

---

### Post by Frem on 2007-01-21
You people are being awfully demanding. This issue has been around for at least a decade. Please, think.

We've had Windows XP out there... how long? Six years, almost? Has Microsoft been releasing major updates every six months? No?

Does Microsoft have to manage updates for every single piece of XP compatible software out there? Of course not. Individual developers handle that. The thing is, with Linux, our faithful Ubuntu repo devs quite frequently are not the main developer of the packages they offer. They can't give the same careful attention to each package and backport everything.

In addition, Windows developers have a single, uniform platform to target. *They usually include or statically link all dependencies*, something we don't do all that often in Linux. Linux devs have to decide which distros to target with Binary packages, if they even provide binaries. There can be compatibility issues between distros.

In short, *you can't really compare to two*. Windows isn't a moving target. Linux is.

Really, there are three ways to manage getting the latest packages on Linux:
a) Freeze the platform for extended periods of time, aka LTS. Unfortunately, new apps often need new libraries, which frequently need more new libraries, which leads to dll hell, which is why the new apps aren't coming. People don't appear to be liking this. It's much easier to b) Update the entire system frequently. This is why the Ubuntu six-month release schedule is so popular.

Ubuntu has a rolling release cycle. Some other distros like ArchLinux and Gentoo have c) a constantly updating single release. The trouble with that is, if something breaks, it's **broken**, and it's a real pain in the neck. I personally tried it and came back with a much greater appreciation for the Ubuntu release cycles.

If you can't wait six months to upgrade to the latest versions of everything, or *are too lazy* to find or make the updated packages yourself, I'm sorry, but you need to stop using Ubuntu.

---

### Post by beefcurry on 2007-01-22
> **Frem said:**
> If you can't wait six months to upgrade to the latest versions of everything, or *are too lazy* to find or make the updated packages yourself, I'm sorry, but you need to stop using Ubuntu.

Thats not very constructive is it, I believe the whole point of this thread is not the discussion to flame poor volunteer package maintainers but raise the issue that maybe there should be some simplified standardized way to .... erm without effort create .deb or .rpm . A way to make it so easy that software developers do not need to have another person to maintain it but only needs two seconds to easily package all dependencies and such into one simple installable file. This is something we might learn from windows. We need to be a society that advances through criticisms ...not "if you dont like it, dont use it". After all we all are humans and we are trying to make this distribution for humans. Don't I have a point here? (hence the name "Ubuntu")

---

### Post by jtfolden on 2007-01-22
> **beefcurry said:**
> Thats not very constructive is it, I believe the whole point of this thread is not the discussion to flame poor volunteer package maintainers but raise the issue that maybe there should be some simplified standardized way to .... erm without effort create .deb or .rpm . A way to make it so easy that software developers do not need to have another person to maintain it but only needs two seconds to easily package all dependencies and such into one simple installable file. This is something we might learn from windows. We need to be a society that advances through criticisms ...not "if you dont like it, dont use it". After all we all are humans and we are trying to make this distribution for humans. Don't I have a point here? (hence the name "Ubuntu")

Exactly, the forward thinking approach is to look for solutions, not stick your heads in the sand... and this whole "if you don't like it, don't use it' mentality doesn't fit with the goals of Ubuntu at all, imo.

Comparison with Windows isn't really the point BUT when you're trying to market yourself toward the mainstream this is a valid issue that mainstream operating systems don't have a problem with and it will turn a great number of users away. Frem, please think.

---

### Post by houstonbofh on 2007-01-25
Allow me to join in with the example that brought me here.  I am running a server.  Servers need to be stable, not the latest and greatest eye candy.  The LTS aspect of Dapper appealed to me, and Edgy was not out yet. :)  So I installed Dapper.  I have one bit of software that is not a package.  It is also one of the main reasons for the server. (vTiger CRM)  So I **have** to go outside the repositories for this.  I want to keep everything clean for stability, and upgrades.  As it is a server on the internet I want it secure.  I installed fail2ban from the repositories.  The dapper version is way behind.  The Edgy version is still behind.  The Feisty version is also behind the Debian version.  That is behind the developer version.  I can not get the old version to keep people out of my ftp server.  The googled solution is "Upgrade.  It is now supported out of the box."  But I do not want another compiled possibly unstable package on my box.  I also do not want to take chances with a security app.

Clif Notes: Latest version does not always mean eye candy.

---

### Post by jtfolden on 2007-07-03
I've not tried a new version of Ubuntu in the last 6 months. Has there been any improvement in this area?

---

### Post by houstonbofh on 2007-07-03
> **jtfolden said:**
> I've not tried a new version of Ubuntu in the last 6 months. Has there been any improvement in this area?
Each distribution is an improvement over the last.  But old versions are still forgotten.  The answer for me is, upgrade early and often.  I will be installing Gutsy on a test server tonight.

For my fail2ban problem, I did a partial backport myself.  We will see what it breaks when I get the guts to upgrade the server.  This may be soon...

---

### Post by 3rdalbum on 2007-07-05
> **jtfolden said:**
> I mean, I can't imagine a world where a new version of Mac OS X is released but you can - generally - only run apps that were available up until it's release day, meanwhile newer apps sit on a server somewhere that can only be run on an OS revision that won't be available for 6-12 months. it seems counter-productive, imo. 

Apple does a similar thing with Mac OS X's programs. All new programs run on the latest version of the OS, and maybe the one before that, but those programs are never fully backward compatible with the older versions of OS X. That doesn't make sense to me, although I know exactly why they do it.

At least with Ubuntu, you can find an unofficial Debian package or compile from source. Compiling from source is not difficult, you've just got to practice it a couple of times to get the hang of it.

---

### Post by 3rdalbum on 2007-07-05
> **beefcurry said:**
> ...raise the issue that maybe there should be some simplified standardized way to .... erm without effort create .deb or .rpm . A way to make it so easy that software developers do not need to have another person to maintain it but only needs two seconds to easily package all dependencies and such into one simple installable file. This is something we might learn from windows.

1. There's a simplified way to create .debs. Doing it "by hand" is simpler than creating an InstallShield on Windows. And you don't need another person to maintain it anymore - Virtualisation is on the desktop. But COMPILING IS NOT DIFFICULT.

Windows only supports one architecture - x86. When Windows supports 12 architectures, and application developers find a way to maintain binaries for all of those, and it's more simple than the Linux way, then we'd have something to learn from Windows. Right now, our way is better, and that's all there is to it.

---

### Post by marco.catunda on 2007-07-07
> **PriceChild said:**
> "stuck" "Stuck!"?

What's wrong with dapper? Its a completely solid distro which will be as solid for the next 2 1/2 years and after.

Is there really any reason you want updated packages? Or just because the version number is higher?

You can always try "prevu" to backport on your own.

For me , update packages is not a problema because we have backport project. 

But I have a big problema using Dapper release. The kernel of cd installer is too old. 
I bought a new hardware and the old kernel (Dapper Release) didn't find any HD installed, but the new
kernel (Feisty Release) found. So, How can I deal with this issue?

I think all distro have to have  two kinds of releases, one for core system (kernel, glib, ...) and other for apps.

---

