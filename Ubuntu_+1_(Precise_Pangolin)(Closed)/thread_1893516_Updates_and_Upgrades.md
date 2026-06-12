---
title: "Updates and Upgrades"
date: 2011-12-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-10
Everyday I do a 
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
While testing 12.04.
Is this a good way to make sure I have the latest updates and upgrades? Or is this over kill?

---

### Post by sgage on 2011-12-10
> **irv said:**
> Everyday I do a 
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
While testing 12.04.
Is this a good way to make sure I have the latest updates and upgrades? Or is this over kill?

'update' refreshes your repo lists, but doesn't upgrade/install/do anything to your existing packages. 'upgrade' does the actual downloading and upgrading.

So they are normally used in tandem, in that order.

---

### Post by irv on 2011-12-10
Thanks for the reply.
If I try to do an update/upgrade with the update manager I always get this message so I do it from the command line.
[ATTACH]208865[/ATTACH]

I never get this message from the terminal command line.

---

### Post by sgage on 2011-12-10
I never use the Update Manager, but I believe it is somewhat broken at the moment.

You're better off using the commandline or synaptic.

---

### Post by zika on 2011-12-10
> **irv said:**
> Thanks for the reply.
If I try to do an update/upgrade with the update manager I always get this message so I do it from the command line.
[ATTACH]208865[/ATTACH]

I never get this message from the terminal command line.In testing there are situations (very often) when non-partial upgrade is not enough. In those cases partial upgrade is a must, in order to remove some obsolete packages and install new ones. There is a sticky thread about that in this room...

---

### Post by coffeecat on 2011-12-10
The dreaded partial upgrade. :) Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by marin123 on 2011-12-10
You may want to do

```
sudo apt-get dist-upgrade
```

so you get kernel updates as well.

---

### Post by irv on 2011-12-10
> **sgage said:**
> I never use the Update Manager, but I believe it is somewhat broken at the moment.

You're better off using the commandline or synaptic.

Yes it is broken and even if you use it at the moment it does nothing.

Thanks

---

### Post by philinux on 2011-12-10
> **marin123 said:**
> You may want to do

```
sudo apt-get dist-upgrade
```

so you get kernel updates as well.

+1 and not just kernels. Caveat for anyone reading this. Make sure you are happy before hitting Y though. It might want to remove packages. If unsure hit N and post a thread here.

---

### Post by irv on 2011-12-10
This was posted on the "Ubuntu Linux Tips and Tricks blogspot" back in Feb 2010: [http://ubuntulinuxtipstricks.blogspot.com/2010/02/dist-upgrade-misnomer-confusion.html]("http://ubuntulinuxtipstricks.blogspot.com/2010/02/dist-upgrade-misnomer-confusion.html")

> The "dist-upgrade" misnomer & confusion

Yesterday in #ubuntu, someone asked, "I am still confused about this. Everything claims that dist-upgrade actually *upgrades* distributions...can someone please clear this up for me"

So I told them:

    [QUOTE]apt-get dist-upgrade differs from apt-get upgrade in that it will remove obsolete packages and add new dependencies, while apt-get upgrade will not. this is necessary when upgrading from one distro release to another, but it is not the *only* time it is necessary. thus, in aptitude, dist-upgrade has been renamed to full-upgrade
    apt-get dist-upgrade will only change you from one release to another if you've modified /etc/apt/sources.list to point to a newer release, but this method of upgrading is not recommended 

They also asked "and if i do want to upgrade the distribution (not that i do), how do i go about that?" to which I responded:

    > the recommended way to change distro releases is sudo do-release-upgrade

They said it was the best explanation in the shortest amount of text, so I'm posting it here, hoping it'll make it easier for people to find. By the way, man apt-get does explain all this…just in slightly more technical terms.[/QUOTE]

Is this explanation correct?

---

### Post by VinDSL on 2011-12-10
> **sgage said:**
> I never use the Update Manager, but I believe it is somewhat broken at the moment.

You're better off using the commandline or synaptic.

> **coffeecat said:**
> The dreaded partial upgrade. :) Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)
I never, never, use Update Mangler (on a dev release)!

I normally use both the commandline (apt-get) AND synaptic.

Not being cute, just saying...

As far as the dreaded partial upgrade is concerned, I'll do one every once-in-a-blue-moon, but it has to be a V special circumstance.  Otherwise, I avoid it like the plague! 

Having said that, I've noticed that many times, when apt-get or synaptic warns me about a partial upgrade, using the other program allows a full upgrade.

For instance: apt-get will say it will be holding something back, but if I get out of cli and run synaptic, synaptic will do a full upgrade -- and vice-versa.

If both programs are holding back updates, there is no way I would do a partial upgrade, come hell-or-high-water!

@ OP:  Another good indicator is to simply surf the +1 forum before doing ANY upgrades.  Chances are, if an upgrade is going to bork your install, somebody else has already been there -- done it.  And, in this case, you will want to wait around for a patch BEFORE upgrading.  Doing this has saved my bacon several times!  ;)

---

### Post by tekstr1der on 2011-12-10
> **VinDSL said:**
> I never, never, use Update Mangler (on a dev release)!

update-manager is a fairly important component of the Ubuntu distribution. As we are supposed to be testing during the development phase, this application would be helped by testing and bug reporting as well.

You can always make a judgement call as to whether the changes proposed by update-manager seem safe or not. If in doubt I think the best way to proceed is with aptitude:

```
aptitude update && aptitude safe-upgrade
```

This alleviates the concern when packages/dependencies may not be fully synced in the repos. They will be held back until dependencies are satisfied.

---

### Post by TerryNewton on 2011-12-10
Yep, keeping a dev version updated is a bit tricky.. but not that hard with a bit of common sense. Myself, I use Update Manager (because it has a nice interface that displays what will be updated with changelogs), BUT if it says "partial upgrade" then I exit UM without doing anything and instead run synaptic and click "mark all upgrades" to see what it's wanting to remove. Sometimes it's just a single incompatible package, for example lzma which it was wanting to replace with xz-lzma which includes lzma functions. In these and other cases when it's just wanting to remove one or a few libs (no apps) I write down the packages (in case I have to add them back) then just do it. Sometimes the issue is because packages are uploaded out of order or some other temporary repo inconsistency, so if it looks like it wants to remove a lot of stuff or anything suspicious at all - do nothing. Wait awhile then refresh, usually the conflicts go away. This just happened.. a gcc/libc update was wanting to remove a bunch of i386 32-bit libs, including libncurses5:i386 which I need for manually installed 32 bit apps. Waited about half an hour, conflict vanished. This is what I do, your mileage may vary. I'm running my test system under VirtualBox so I also have the advantage of simply making a copy of the virtual machine directory so if something goes wrong I can instantly restore it.

In my experience, when Update Manager offers a partial upgrade, it's because it refuses to actually remove packages - so seems to me that even if taken likely no real damage would be done (I don't know if that's universally true so I avoid partial upgrade, but it's a nice safety feature that's saved me in the past before I learned not to do it) - but the updates will remain blocked until the blocking package is removed or the repos become consistent again. With a dev system this happens all the time, nothing unusual as lots of things are being updated and sometimes replaced. Happens even on my 10.04 production system, like when wine skips a minor version number like 1.2 to 1.3 - the old version has to be removed before installing the new version and Update Manager won't do it.

---

### Post by zika on 2011-12-11
> **TerryNewton said:**
> Yep, keeping a dev version updated is a bit tricky.. but not that hard with a bit of common sense. Myself, I use Update Manager (because it has a nice interface that displays what will be updated with changelogs), BUT if it says "partial upgrade" then I exit UM without doing anything and instead run synaptic and click "mark all upgrades" to see what it's wanting to remove. Sometimes it's just a single incompatible package, for example lzma which it was wanting to replace with xz-lzma which includes lzma functions. In these and other cases when it's just wanting to remove one or a few libs (no apps) I write down the packages (in case I have to add them back) then just do it. Sometimes the issue is because packages are uploaded out of order or some other temporary repo inconsistency, so if it looks like it wants to remove a lot of stuff or anything suspicious at all - do nothing. Wait awhile then refresh, usually the conflicts go away. This just happened.. a gcc/libc update was wanting to remove a bunch of i386 32-bit libs, including libncurses5:i386 which I need for manually installed 32 bit apps. Waited about half an hour, conflict vanished. This is what I do, your mileage may vary. I'm running my test system under VirtualBox so I also have the advantage of simply making a copy of the virtual machine directory so if something goes wrong I can instantly restore it.

In my experience, when Update Manager offers a partial upgrade, it's because it refuses to actually remove packages - so seems to me that even if taken likely no real damage would be done (I don't know if that's universally true so I avoid partial upgrade, but it's a nice safety feature that's saved me in the past before I learned not to do it) - but the updates will remain blocked until the blocking package is removed or the repos become consistent again. With a dev system this happens all the time, nothing unusual as lots of things are being updated and sometimes replaced. Happens even on my 10.04 production system, like when wine skips a minor version number like 1.2 to 1.3 - the old version has to be removed before installing the new version and Update Manager won't do it.Still on Ubuntu 6.06 Dapper ... ;)

---

### Post by coffeecat on 2011-12-11
> **irv said:**
> Is this explanation correct?

To answer your question, I believe it is. Your quote refers to man apt-get being a bit technical, but it's still fairly clear:

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

I *believe* synaptic runs dist-upgrade (I'm happy to be contradicted) when you upgrade with it. Certainly, it has always seemed to offer the same list of packages to be upgraded or removed whenever I've compared it with apt-get dist-upgrade during testing cycles.

---

### Post by VinDSL on 2011-12-11
> **coffeecat said:**
> I *believe* synaptic runs dist-upgrade [...]
Correctamundo!

It's called "Smart Upgrade" in Synaptic's Preferences (enabled by default),

You can also specify "Default Upgrade" in Synaptic, which = apt-get upgrade (or have Synaptic ask you each time).

---

### Post by jerrylamos on 2011-12-11
> **TerryNewton said:**
> 
In my experience, when Update Manager offers a partial upgrade, it's because it refuses to actually remove packages - so seems to me that even if taken likely no real damage would be done 

I've lost several installations and had to re-install all over again because "UPDATE" screwed me, both on development releases (which I've been running starting with Dapper Drake Beta) and on release code.  Took me forever to realize "if it hurts, don't do that!".

I do a sudo aptitude update, sudo aptitude safe-upgrade with much less wreckage than "UPDATE" or even apt-get.  Now on occasion I do a careful sudo aptitude full-upgrade when something isn't being upgraded that looks O.K. to me.

"Caveat emptor".

Jerry

p.s. on development "unstable" code expect to do some installs anyway.  I'll do install at A1 & A1 & B1 & B2 ... anyway since install & grub have lots of bugs to report.

---

### Post by TerryNewton on 2011-12-11
> **jerrylamos said:**
> I've lost several installations and had to re-install all over again because "UPDATE" screwed me, both on development releases (which I've been running starting with Dapper Drake Beta) and on release code.  Took me forever to realize "if it hurts, don't do that!".

I have heard many stories like that - if Update Manager offers a partial upgrade DON'T DO IT. "Seems" and "Likely" no damage as I mentioned means there's a chance of damage if one gets into that habit.. at least by design it seems that Update Manager is trying to cause no damage but I think the warning should be worded differently and should list the conflicting packages to give the user a clue as to if they need to take manual action or simply wait and try again. Also no update mechanism will protect the user in the case of a bad update being uploaded to the repository, which occasionally happens. Also #2, when the configuration process offers to keep or replace a modified config file, that's a very tricky situation with no good default - but it would be nice if it could be indicated if the new config file is required, if not then keep is the choice. Aptitude and other command line update solutions may be superior, but Update Manager is what the normal user sees so the focus as far as users go should be to make that method as safe as possible. If Update Manager ever borks a system (partial upgrade or not) then it is a bug, either in the app, in the repositories, or in the user's configuration.

To answer another poster... no I don't still use 6.06 but the web site doesn't want to let me edit my profile. Last time I tried it said I haven't posted enough. Might be doing something wrong but the implication was that I should post more often.

---

### Post by zika on 2011-12-11
> **TerryNewton said:**
> To answer another poster... no I don't still use 6.06 but the web site doesn't want to let me edit my profile. Last time I tried it said I haven't posted enough. Might be doing something wrong but the implication was that I should post more often.That question was just an innocent joke... ;)

To get back to the topic: several days ago I had a nice exercise solving upgrade conundrum with libatk-adaptor-schemas and ati-spi... ;) I do not think there was a simpler solution than to purge ubuntu-desktop and install it again after proper installation of aforementioned packages... Developers should be very precise and make dependencies as straghtforward and unambiguous as possible...

---

### Post by TerryNewton on 2011-12-11
> **zika said:**
> That question was just an innocent joke... ;)

No prob, was wondering when someone would comment.. :p
6.06 was a nice release, learned a lot from it.

---

### Post by ranch hand on 2011-12-11
> **TerryNewton said:**
> I have heard many stories like that - if Update Manager offers a partial upgrade DON'T DO IT. "Seems" and "Likely" no damage as I mentioned means there's a chance of damage if one gets into that habit.. at least by design it seems that Update Manager is trying to cause no damage but I think the warning should be worded differently and should list the conflicting packages to give the user a clue as to if they need to take manual action or simply wait and try again. Also no update mechanism will protect the user in the case of a bad update being uploaded to the repository, which occasionally happens. Also #2, when the configuration process offers to keep or replace a modified config file, that's a very tricky situation with no good default - but it would be nice if it could be indicated if the new config file is required, if not then keep is the choice. Aptitude and other command line update solutions may be superior, but Update Manager is what the normal user sees so the focus as far as users go should be to make that method as safe as possible. If Update Manager ever borks a system (partial upgrade or not) then it is a bug, either in the app, in the repositories, or in the user's configuration.

To answer another poster... no I don't still use 6.06 but the web site doesn't want to let me edit my profile. Last time I tried it said I haven't posted enough. Might be doing something wrong but the implication was that I should post more often.
The best thing to do to avoid problems with Update Mangler is to not use it at all.

Doing a partial upgrades with it is a self inflicted wound.

I disable it at every install, first thing I do, testing or release.  First problem I had with it was ruining a perfectly good 8.04.1 install.

I have heard before how important it is and just do not buy it at all.  It should quietly disappear.

---

### Post by sgage on 2011-12-11
> **ranch hand said:**
> The best thing to do to avoid problems with Update Mangler is to not use it at all.

Doing a partial upgrades with it is a self inflicted wound.

I disable it at every install, first thing I do, testing or release.  First problem I had with it was ruining a perfectly good 8.04.1 install.

I have heard before how important it is and just do not buy it at all.  It should quietly disappear.

I completely agree. I personally use synaptic - it tells you exactly what is going on and why. Then you can exercise due diligence to understand what's going on.

Perhaps Update Manager could be improved to give more useful information? Sometimes it seems like the devs feel that information is the enemy. I suppose it's part of the whole "protect the newbies from complexity" thing, just like removing configurability. But it's the newbies that get nailed by this approach sometimes...

---

### Post by effenberg0x0 on 2011-12-11
As a related tip, apt-listchanges + common sense works here. Just a fast scroll on the changelogs before installing gives me a) the option to ctrl+c if I don't wanna risk that particular change right now b) a lead on the origin of any different behavior after updating (the knowledge on what to remove/revert in this case).

---

### Post by VinDSL on 2011-12-12
> **TerryNewton said:**
> To answer another poster... no I don't still use 6.06 but the web site doesn't want to let me edit my profile. Last time I tried it said I haven't posted enough. Might be doing something wrong but the implication was that I should post more often.
Posts don't mean jack here!  They mock you by calling them beans, e.g. posts don't mean beans... Er... whatever!

I've submitted 100's if not 1000's of posts about Conky, but they are deemed unworthy because they don't concern Ubuntu specifically.

In your case, it's collateral damage.  They're trying to stop spammers with some sort of 50 post rule.  

Bwahahahahahaha!  Please stop!  My sides are hurting!!!  :D

OMG!!!  Okay, anyway, you're doing fine.  Don't let their silliness get to you.  ;)

---

### Post by VinDSL on 2011-12-12
> **tekstr1der said:**
> update-manager is a fairly important component of the Ubuntu distribution. As we are supposed to be testing during the development phase, this application would be helped by testing and bug reporting as well.[...]
~Cool!

Let's see your Update Mangler Bug Reports. I'd love to read them.

Linkage, please...

---

### Post by VinDSL on 2011-12-12
> **ranch hand said:**
> The best thing to do to avoid problems with Update Mangler is to not use it at all.

Doing a partial upgrades with it is a self inflicted wound.

I disable it at every install, first thing I do, testing or release.  First problem I had with it was ruining a perfectly good 8.04.1 install.

I have heard before how important it is and just do not buy it at all.  It should quietly disappear.
Well said, ranch hand!

Thank you!  ;)

---

### Post by irv on 2011-12-12
This morning I went to run my update/upgrade and with the upgrade I used:
```
sudo aptitude safe-upgrade
```
and got this message:
> Resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver.
What would happen if I run with --full-resolver?

---

### Post by paul_in_london on 2011-12-12
> **irv said:**
> This morning I went to run my update/upgrade and with the upgrade I used:
```
sudo aptitude safe-upgrade
```
and got this message:

What would happen if I run with --full-resolver?

I've had this sometimes recently. From the aptitude man page:

```
--full-resolver
           When package dependency problems are encountered, use the default “full” resolver to solve them. Unlike the “safe” resolver activated by
           --safe-resolver, the full resolver will happily remove packages to fulfill dependencies. It can resolve more situations than the safe
           algorithm, but its solutions are more likely to be undesirable.
```

You have to be a bit more careful using that option.

Alternatively in these situations run:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zika on 2011-12-12
> **irv said:**
> This morning I went to run my update/upgrade and with the upgrade I used:
```
sudo aptitude safe-upgrade
```
and got this message:

What would happen if I run with --full-resolver?Only You can tell... We do not know what packages are offered and how...
&#8220;Dist-upgrade&#8220; is necessity, sometimes, I wrote that a page ago...
Even then You might have to resort to manual resolution of conflicts... Not often, but...
I have a feeling we are going the same path, for at least second time... There is a sticky about this and there is a whole (at least one) thread from previous testing...

---

### Post by irv on 2011-12-12
I just ran 
```
sudo apt-get update
```
and 
```
sudo apt-get upgrade
```
and everything seems to be running OK.
This is what I have been doing since installing 12.04 Alpha 1.
I have done this everyday since the install.
I think I will stick with this way.

---

### Post by kansasnoob on 2011-12-12
In defense of the Update Manager I can't recall it ever causing me an insurmountable problem in a stable release. 

Development releases are a different animal though. I personally still like to begin with the update manager so I can somewhat quickly scroll thru the updates and read the changelogs that most interest me.

From there I'll generally open synaptic, whether or not I was offered a partial upgrade, so I can even more closely examine exactly what's being upgraded, installed, or removed - and while I'm there I can check to see if ubiquity or casper are being upgraded in the background, and if so, read their changelogs also.

Outside of those GUI apps I tend to prefer apt to aptitude for most things just due to familiarity, but I do prefer aptitude for checking package "status" (version number, whether installed or not, etc).

But, as with all things Linux, it's nearly impossible to find two end users that do things identically. Wouldn't that be boring anyway?

---

### Post by ranch hand on 2011-12-12
> **kansasnoob said:**
> In defense of the Update Manager I can't recall it ever causing me an insurmountable problem in a stable release. 

Development releases are a different animal though. I personally still like to begin with the update manager so I can somewhat quickly scroll thru the updates and read the changelogs that most interest me.

From there I'll generally open synaptic, whether or not I was offered a partial upgrade, so I can even more closely examine exactly what's being upgraded, installed, or removed - and while I'm there I can check to see if ubiquity or casper are being upgraded in the background, and if so, read their changelogs also.

Outside of those GUI apps I tend to prefer apt to aptitude for most things just due to familiarity, but I do prefer aptitude for checking package "status" (version number, whether installed or not, etc).

But, as with all things Linux, it's nearly impossible to find two end users that do things identically. Wouldn't that be boring anyway?
Very boring indeed.  If we all agreed on everything there would be little point to life at all.

Kind of like the old Dylan lyric "no sense talkin to you, just like talkin to me".

---

### Post by VinDSL on 2011-12-13
> **zika said:**
> &#8220;Dist-upgrade&#8220; is necessity, sometimes, I wrote that a page ago...
You can set the prefs in Synaptic to ask you which method to use, each time you upgrade... provides a nice description, in case ppl forget which does what.  :)


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-13-dec-2011-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-13-dec-2011-1.png")
[/INDENT]


I wrote that a page ago, too.  LoL!  :D

---

