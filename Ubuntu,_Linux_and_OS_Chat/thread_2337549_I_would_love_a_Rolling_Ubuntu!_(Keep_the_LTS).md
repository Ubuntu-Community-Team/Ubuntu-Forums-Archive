---
title: "I would love a Rolling Ubuntu! (Keep the LTS)"
date: 2016-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by izznogooood on 2016-09-19
I opened my 16.10 VM today and this greeted me.

[ATTACH=CONFIG]271265[/ATTACH]

This made my day :).
I keep coming back (or stay with) ubuntu for my desktop/server but stick to (newer) other distros for my laptops.

@moderator: If the "public" cant see the vote (or ressults), that was not my intention. Please correct.

---

### Post by Dragonbite on 2016-09-19
I went to Gentoo after Red Hat.  Now the rolling release of choice is openSUSE Tumbleweed.  They have been pretty solid and stable when I had it installed not too long ago.

---

### Post by #&amp;thj^% on 2016-09-19
Kali which is debian based...went to a rolling Distro, and after a couple of  months using it...a big thumbs up.
Ubuntu Devs seem not to favor a rolling OS.:(
Arch has always had a rolling OS and it is making me very lazy...;) No fuss no muss.

---

### Post by izznogooood on 2016-09-19
Dont get me wrong. Ubuntu is and will always be my "go to Distro" (Not necessarily ubuntu plain). I am one of those who embrace Unity, but my choice would be arch with Unity. The problem is that this does not exist... (without issues). EDIT: I will always prefer the LTS´s for my servers!

As for a rolling release.

Wine is a great example. sudo apt install wine = 1.6 , pacman -S wine = 1.9 ...

---

### Post by &amp;KyT$0P# on 2016-09-19
Rolling Ubuntu + Keep the LTS would be perfect for me.  I'd use the rolling release in a VM only though, the LTS model better especially on bare-metal where predictability and stability are strict requirements.

---

### Post by #&amp;thj^% on 2016-09-19
> **izznogooood said:**
> Dont get me wrong. Ubuntu is and will always be my "go to Distro" (Not necessarily ubuntu plain). I am one of those who embrace Unity, but my choice would be arch with Unity. The problem is that this does not exist... (without issues)

Well it dose exist: [https://wiki.archlinux.org/index.php/Unity](https://wiki.archlinux.org/index.php/Unity)
Well just seen this _**"(without issues)" **_There is a handful of users right now that have it somewhat smooth. (But myself I prefer other DE's)

---

### Post by 7dEfOk4AgU on 2016-09-19
What would be the advantages and risks of "Rolling Ubuntu" ?

---

### Post by &amp;KyT$0P# on 2016-09-20
> **mikeb42 said:**
> What would be the advantages and risks of "Rolling Ubuntu" ?
Advantage - you just update the packages and it's up-to-date, period.
No fancy delicate rigamarole, no installing the whole OS from scratch, just [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] and grab some coffee and you're done.  Huge time-saver for people involved in software development in any capacity, where access to "the latest" is often important for compiling and testing applications.


Risk - every software update.

I know, I know, some of you are thinking "*My up-to-date software works fine, how is that a risk?*" type stuff.  Well, lucky old you. :)
Let's examine this more closely.

With the LTS model, most software is pretty much frozen to one version.  Updates are only for security and stability fixes.
So, after updating, you've got something which is more robust, while still behaving the same way, having the same features.  Once you know what you have, you always know what you have.  Reliable and dependable.

In rolling release, **any** software update can be included, regardless of what changed in the software.  This isn't just the 'under-the-hood' stuff.  You know that favorite application of yours that you like?  One undesirable major version update and it could suddenly have a completely different user interface and all kinds of questionable 'features' you don't want.  And when you finally figure the new interface out, you then discover that the application has a new bug and it can no longer correctly do that thing you need it for in the first place.

Sound crazy?  I'd have said so too, but this type of thing repeatedly happened to me in my OS X days and repeatedly happened to some techie Windows users I know.  Downgrading the application on those systems is usually possible and always works the same general way - uninstall what you have, then download and install the older version of the application.  Time-consuming, but doable.
Even in LTS Ubuntu, where you can opt in to software updates using PPAs (and, I think, snap packages in 16.04), but that's a manual process you choose to undertake, and there are usually straightforward ways to revert to the prior/repository version of the software if it doesn't work out (think [FONT=Courier New]ppa-purge[/FONT], for example).

Remember how you get software updates in rolling release model?  Yep, this cycle would become tied to the primary OS package manager & repositories, making downgrading software tricky to do and requiring your system backups.

See the difference?

(Incidentally, this is why someone I know has "**_Always_** check the changelogs BEFORE updating that important software!" as their forum signature.  Good advice when dealing with feature updates.  Well, either that or just try it out in a disposable environment before "really" updating. ;) )



tl;dr?  You always want "the latest & greatest" regardless of predictability etc, you'd like rolling.  You want solid stability with up-to-date security, stick with LTS.

---

### Post by izznogooood on 2016-09-20
> **halogen2 said:**
> Advantage - you just update the packages and it's up-to-date, period.
No fancy delicate rigamarole, no installing the whole OS from scratch, just [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] and grab some coffee and you're done.  Huge time-saver for people involved in software development in any capacity, where access to "the latest" is often important for compiling and testing applications.


Risk - every software update.

I know, I know, some of you are thinking "*My up-to-date software works fine, how is that a risk?*" type stuff.  Well, lucky old you. :)
Let's examine this more closely.

With the LTS model, most software is pretty much frozen to one version.  Updates are only for security and stability fixes.
So, after updating, you've got something which is more robust, while still behaving the same way, having the same features.  Once you know what you have, you always know what you have.  Reliable and dependable.

In rolling release, **any** software update can be included, regardless of what changed in the software.  This isn't just the 'under-the-hood' stuff.  You know that favorite application of yours that you like?  One undesirable major version update and it could suddenly have a completely different user interface and all kinds of questionable 'features' you don't want.  And when you finally figure the new interface out, you then discover that the application has a new bug and it can no longer correctly do that thing you need it for in the first place.

Sound crazy?  I'd have said so too, but this type of thing repeatedly happened to me in my OS X days and repeatedly happened to some techie Windows users I know.  Downgrading the application on those systems is usually possible and always works the same general way - uninstall what you have, then download and install the older version of the application.  Time-consuming, but doable.
Even in LTS Ubuntu, where you can opt in to software updates using PPAs (and, I think, snap packages in 16.04), but that's a manual process you choose to undertake, and there are usually straightforward ways to revert to the prior/repository version of the software if it doesn't work out (think [FONT=Courier New]ppa-purge[/FONT], for example).

Remember how you get software updates in rolling release model?  Yep, this cycle would become tied to the primary OS package manager & repositories, making downgrading software tricky to do and requiring your system backups.

See the difference?

(Incidentally, this is why someone I know has "**_Always_** check the changelogs BEFORE updating that important software!" as their forum signature.  Good advice when dealing with feature updates.  Well, either that or just try it out in a disposable environment before "really" updating. ;) )



tl;dr?  You always want "the latest & greatest" regardless of predictability etc, you'd like rolling.  You want solid stability with up-to-date security, stick with LTS.

Well, this is a very good explanation. But it's not entirely correct.

This is correct when it comes to Arch, if Ubuntu went rolling i sure hope its not like that. It will however put more responsibilities on the users. You would have to check news or webpages for a possible breakage following updates, major changes in packages etc. Or one could create an update center of sorts with information.

But i would think that Ubuntu rolling would not be bleeding unless you ask for it.

---

### Post by mwbworld on 2016-09-20
> **halogen2 said:**
> 

(Incidentally, this is why someone I know has "**_Always_** check the changelogs BEFORE updating that important software!" as their forum signature.  Good advice when dealing with feature updates.  Well, either that or just try it out in a disposable environment before "really" updating. ;) )

So right.  I really like the ability to check into what the update does and reports about it before updating in various Linux distros.   

The inability to really do that in more recent Windows updates ("it will crash your system but we'll still force the update on you!") helped me with the decision to shift to Linux completely.

---

### Post by denter2 on 2016-09-20
i've been using archlinux for a long time.
must say, i found it pretty stable.
not sure how that (self created desktop experience) would translate into ubuntu, though...

---

### Post by simonsaysthis on 2016-09-20
> **mwbworld said:**
> So right.  I really like the ability to check into what the update does and reports about it before updating in various Linux distros.   

The inability to really do that in more recent Windows updates ("it will crash your system but we'll still force the update on you!") helped me with the decision to shift to Linux completely.

Interesting, this was also my main reason for completely eliminating Windows from my life. I was tired of Windows 10 updates which literally broke things.

---

### Post by simonsaysthis on 2016-09-20
> **izznogooood said:**
> Well, this is a very good explanation. But it's not entirely correct.

This is correct when it comes to Arch, if Ubuntu went rolling i sure hope its not like that. It will however put more responsibilities on the users. You would have to check news or webpages for a possible breakage following updates, major changes in packages etc. Or one could create an update center of sorts with information.

But i would think that Ubuntu rolling would not be bleeding unless you ask for it. 

I can't speak for Arch directly but if you have a package manager like Pacman on Antergos it gives you the option to review every single package but as you indicated this is a different mentality than just going into a software centre and clicking apply updates when you don't really know what is happening.

---

### Post by #&amp;thj^% on 2016-09-20
> **izznogooood said:**
> Well, this is a very good explanation. But it's not entirely correct.

_**This is correct when it comes to Arch, **_
if Ubuntu went rolling i sure hope its not like that. It will however put more responsibilities on the users. .
Sorry to hear that..I have used Arch for over a year now with no breakage from updates..
Are you using an Arch based distro like Manjaro or Antergos, as that would make more sense to me on the breakage.
If you used A GUI installer then you are not using Arch but rather an Arch Based Distro...and that makes a big Difference.:)
Just trying to keep the facts straight here...and no Offense meant.

---

### Post by Dragonbite on 2016-09-20
> **izznogooood said:**
> Well, this is a very good explanation. But it's not entirely correct.

This is correct when it comes to Arch, if Ubuntu went rolling i sure hope its not like that. It will however put more responsibilities on the users. You would have to check news or webpages for a possible breakage following updates, major changes in packages etc. Or one could create an update center of sorts with information.

But i would think that Ubuntu rolling would not be bleeding unless you ask for it.

If you want to see how a distro can work with rolling release and a stable point release, then look at openSUSE.

Their Tumbleweed rolling release does a great job in being stable despite being up to date on things.  They built a testing process that is so good, even Red Hat is adopting it.

At the same time they have a point-release version called Leap.  This one is more traditional except it is built off of the enterprise SUSE with packages being the up-to-date stable versions rather than the getting-long-in-the-tooth version enterprises usually offer.

I really liked Tumbleweed and it is my first choice for rolling release.

---

### Post by &amp;KyT$0P# on 2016-09-20
> **izznogooood said:**
> This is correct when it comes to Arch, if Ubuntu went rolling i sure hope its not like that.
Hmm, when I think "rolling release" I think [this]("http://www.pclinuxos.com/").  Haven't used it for nearly a year now, but once set up it was a pretty convenient testing OS as I recall.
Not familiar with Arch as it's too advanced for me.

What kind of "rolling" do you have in mind?

> But i would think that Ubuntu rolling would not be bleeding unless you ask for it.
Agreed, but we're not even thinking bleeding-edge/pre-release software here.  Remember what it was like updating Firefox 28 -> Firefox 29?  Or, for the graphics artists among us, Blender 2.49b -> 2.58?
All were the latest stable releases at the times.  Now compare appearance, functionality, and user-experience between the two versions.

---

### Post by izznogooood on 2016-09-20
> **1fallen said:**
> Sorry to hear that..I have used Arch for over a year now with no breakage from updates..
Are you using an Arch based distro like Manjaro or Antergos, as that would make more sense to me on the breakage.
If you used A GUI installer then you are not using Arch but rather an Arch Based Distro...and that makes a big Difference.:)
Just trying to keep the facts straight here...and no Offense meant.

Im sorry if its seems like I experienced a lot of crashes. I dont, I use Antergos so i see your point. I have experienced a break with the mate desktop, but thats all. I just ment i supported his arguments regarding the need for more attention as you update.

All though i must say i dont pay much attention and have little to no issues.

---

### Post by izznogooood on 2016-09-20
> **halogen2 said:**
> Hmm, when I think "rolling release" I think [this]("http://www.pclinuxos.com/"). Haven't used it for nearly a year now, but once set up it was a pretty convenient testing OS as I recall.
Not familiar with Arch as it's too advanced for me.

What kind of "rolling" do you have in mind?

Well, "Wine" is a good example.
If you "sudo apt install wine" you get 1.6
Then theres Arch (Antergos): "pacman -S wine" you´d get 1.9

The latest stable is 1.8* <-- That is what I would be aiming for.
The same goes for a lot of packages I use.
This would practically eliminate the need for extra repos just to keep my software up to date.

There´s also the issue that repos are release specific, meaning running a development version is a pain when it comes to extra repos.

---

### Post by simonsaysthis on 2016-09-21
> **Dragonbite said:**
> If you want to see how a distro can work with rolling release and a stable point release, then look at openSUSE.

Their Tumbleweed rolling release does a great job in being stable despite being up to date on things.  They built a testing process that is so good, even Red Hat is adopting it.

At the same time they have a point-release version called Leap.  This one is more traditional except it is built off of the enterprise SUSE with packages being the up-to-date stable versions rather than the getting-long-in-the-tooth version enterprises usually offer.

I really liked Tumbleweed and it is my first choice for rolling release.

I know a lot of people would disagree but my pet hate in Opensuse is actually Yast. I don't find it user-friendly and IMO there is too much duplication with other Gnome or KDE apps. Then it also looks like it's stuck in the 90s. I'd rather learn how to use the terminal to do the extra configurations Yast offers.

---

### Post by Dragonbite on 2016-09-21
> **simonsaysthis said:**
> I know a lot of people would disagree but my pet hate in Opensuse is actually Yast. I don't find it user-friendly and IMO there is too much duplication with other Gnome or KDE apps. Then it also looks like it's stuck in the 90s. I'd rather learn how to use the terminal to do the extra configurations Yast offers.

I don't use Yast. I use the terminal and "zypper" is not a bad package manager.

---

### Post by TheFu on 2016-09-21
I don't care for rolling releases. Tried Arch for a few months and found it highly unstable for the things I did.  From week to week, never knew if some big issue would happen or not.  I want a system that will work in a predictable manner for years, not days.

I'd rather Canonical spend time on supporting 32-bit minimal releases. I run lots of relatively small VMs and just don't need a 64-bit OS or that amount of RAM for those systems.  Keep the bloated DEs out of the 32-bit releases - no need to provide KDE, Unity, Gnome, Mate, XFCE versions - LXDE and straight openbox are fine.  Actually, zero GUI would be fine, though my chromebooks DO like a 32-bit OS too.

---

### Post by #&amp;thj^% on 2016-09-21
> **TheFu said:**
> 
I'd rather Canonical spend time on supporting 32-bit minimal releases. I run lots of relatively small VMs and just don't need a 64-bit OS or that amount of RAM for those systems.  Keep the bloated DEs out of the 32-bit releases - no need to provide KDE, Unity, Gnome, Mate, XFCE versions - LXDE and straight openbox are fine.  Actually, zero GUI would be fine, though my chromebooks DO like a 32-bit OS too.
Hehe I keep hearing about Arch not being stable...but I will leave this alone..as it will most certainly turn to a flame-bait.
And I am glad to see the other choices available...at least for myself:)
Score one for Choice..:KS

---

### Post by TheFu on 2016-09-21
> **1fallen said:**
> Hehe I keep hearing about Arch not being stable...but I will leave this alone..as it will most certainly turn to a flame-bait.
And I am glad to see the other choices available...at least for myself:)
Score one for Choice..:KS

Each "choice" costs Canonical money.  They are claiming that supporting **any** 32-bit version of Ubuntu is too costly to continue.  Just proposing a way to limit the support for the purposes likely to be useful. Old systems and VMs that have/use less than 3G of RAM.  People still have VIA CPU-based systems out there - all 32-bit. I'd prefer to run Ubuntu on mine, but debian is a viable choice. As I'm forced to use debian more and more, eventually it will make sense to stop using *buntu anything, just to keep my sanity with the tiny differences.

I didn't intend to imply that arch as an OS wasn't relatively stable - only remember 1 system-wide lockup during my use.  I meant to say that applications and tools I needed to work from week to week with long dependency chains would often get broke.  Since that time, I've become an LTS-only guy.  16.10 and 17.xx won't be touched by me.  In the mid-1990s, I did my time on bleeding edge stuff. Never again.

---

### Post by #&amp;thj^% on 2016-09-21
<Snip>By OP
Might as well edit it right then.

---

### Post by Dragonbite on 2016-09-22
When I started with Linux, rolling releases were fine.  If it were unstable, then I would learn.

Now I am wanting to spend less time maintaining the systems and more time using them (or going outside) plus I don't want to keep having to "fix" the family's various computers so I go with systems that are more stable and supported even if that means it isn't the "latest and greatest".

But the appeal with a rolling release is not having to do another install when the next version comes out!

---

### Post by kevdog on 2016-09-25
Ive used Arch for years and can attest that sometimes things break, however usually I didn't read the Arch home page prior to updating.  After I noticed the breakage there usually is a fix on the home page with a link to the forum post.  Some fixes required a chroot, however honestly the fix wasn't all that difficult -- it seemed like the fix would be a lot longer than it turned out to be.  I think I've only had 2 breakages in 3 years, all which could be recovered, although once I needed to boot from the install disk or image.  Comparing time needed, fixing the occasional breakage is far more efficient than installing a new LTS every 2 years.  Although the LTS install is pretty straightforward, the time to install and get things "re-setup" is far more time -- usually several hours -- than fixing the occasional breakage with the rolling Arch release. Based on this factor, I'd really just like to stick to a rolling release if possible.

---

### Post by poorguy on 2016-09-25
> **halogen2 said:**
> Advantage - you just update the packages and it's up-to-date, period.grab some coffee and you're done.I have all that now with my LTS Distro.> **halogen2 said:**
> With the LTS model, most software is pretty much frozen to one version.  Updates are only for security and stability fixes.So, after updating, you've got something which is more robust, while still behaving the same way, having the same features.  Once you know what you have, you always know what you have.  Reliable and dependable. The perfect world install and use right out of the box.> **halogen2 said:**
> You want solid stability with up-to-date security, stick with LTS.I'll stick to a sure deal all of the time.I want to use my Linux Distro not repair it.

---

### Post by poorguy on 2016-09-25
> **TheFu said:**
> Each "choice" costs Canonical money.  They are claiming that supporting **any** 32-bit version of Ubuntu is too costly to continue.  Just proposing a way to limit the support for the purposes likely to be useful. Old systems and VMs that have/use less than 3G of RAM.  People still have VIA CPU-based systems out there - all 32-bit. I'd prefer to run Ubuntu on mine, but debian is a viable choice. As I'm forced to use debian more and more, eventually it will make sense to stop using *buntu anything, just to keep my sanity with the tiny differences.

I understand the cost of keeping 32 bit alive since all of the world is going to 64 bit.
There are other 32 bit choices available to worry about what Canonical supports.
Canonical is no different than any other corporation that does what it is told to do. 

I like to keep old computers running as lots of cool hardware around for not alot of money.
I don't need the newest cheaply made computer hardware products of today.
Older computers are built to last with less component failure unlike computers of today.
I have a shelf full of 2 year and 3 year old Dell desktops and laptops in my shop with hardware problems more money in my pocket.  =d>

The world is full of choices and nobody cares what I think.

Life is Good.

---

### Post by poorguy on 2016-09-25
> **TheFu said:**
> Keep the bloated DEs out of the 32-bit releases - no need to provide KDE, Unity, Gnome, Mate, XFCE versions - LXDE and straight openbox are fine.  Actually, zero GUI would be fine,
I agree with  no need to provide KDE, Unity, Gnome, XFCE versions.

Why leave out Mate?

LXDE and straight openbox are fine for you but maybe not for the rest of us.
I would rather use Mate.

---

### Post by user1397 on 2016-09-25
Honestly, it wouldn't be a bad idea for Canonical to keep the LTS and keep promoting it as the standard default install, and then for anyone willing to test out the next version have a more-or-less stable rolling release.  I understand that there technically is an Ubuntu rolling release, namely just using whatever ubuntu+1 dev version is, but that's bleeding edge using pre-release software and the like.  Maybe have a debian style system where LTS = stable, rolling = testing (but still stable versions of packages), and bleeding edge = unstable.

Then again, I don't know, maybe they see no incentive to release a slightly more stable rolling version of their desktop OS.  Maybe not enough demand.  

I don't really see the point of the current "stable" releases that are released between LTS's.  Who is that really for?  I mean, for most people aka non-tech users, the LTS is the go to.  Servers = always LTS.  Advanced users who don't like to fiddle with maintenance ever? = LTS.  So are the other "stable" releases solely for hobbyists and tinkerers?  Might as well make it rolling IMO.

---

### Post by mikodo on 2016-09-25
I see snappy-core being snapped and with snaps with apps too, as a form of a safer rolling release format. I think it is part of what what Ubuntu is becoming. There might still be something like a LTS for server installs and individuals and organizations that need "Debian Stable" type of unchanging stability.

---

### Post by izznogooood on 2016-09-26
> **user1397 said:**
> I don't really see the point of the current "stable" releases that are released between LTS's.  Who is that really for?  I mean, for most people aka non-tech users, the LTS is the go to.  Servers = always LTS.  Advanced users who don't like to fiddle with maintenance ever? = LTS.  So are the other "stable" releases solely for hobbyists and tinkerers?  Might as well make it rolling IMO.

This is what I think. Not to mention the "separat" PPA´s for each release. This is what bugs me the most. With a rolling and a LTS all you need are 2 PPA´s. So one could run LTS on your Desktop and Rolling on your laptop. At least this is what I would do ;).

Now if I want to run yak many of the PPA´s have no options for yak, even though they have for 16.04. I would end up with some packages older than possible to achieve on 16.04. 

I´m, sure we could argue pro´s and con´s for ever. It´s a matter of personal choice ;)

---

