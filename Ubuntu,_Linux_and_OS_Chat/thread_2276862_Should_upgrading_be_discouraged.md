---
title: "Should upgrading be discouraged?"
date: 2015-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by SeijiSensei on 2015-05-05
Now that 15.04 is out, we're seeing an array of complaints from people who upgraded and encountered problems.  Has the time come for the major *bunutu websites to stop pushing current releases and recommend LTS versions instead?  I understand the PR value of appearing to be moving forward all the time, but I also think probably 90% or more of the user base should be using LTS releases.  I've even seen postings lately of people upgrading production servers from 14.04 to 15.04.  Should there be more of an effort to drive most users, especially new users, to the LTS versions and away from interim releases?

---

### Post by d-cosner on 2015-05-05
Actually, the default on the Ubuntu download site is the LTS. Upgrading from one release to the next usually works fine so long as the user has not added a bunch of ppa repos and removed proprietary drivers before doing the upgrade.

---

### Post by SeijiSensei on 2015-05-05
"Usually" isn't "always," of course. People seem to be having problems with basic things like CUPS in 15.04.

And, the current big headline at [ubuntu.com]("http://www.ubuntu.com/") encourages users to install Snappy 15.04 :confused:.  If you look down to the "Get Ubuntu Desktop" link, it also suggests 15.04, though the page it links to recommends 14.04.2 first and 15.04 below it.

---

### Post by craig10x on 2015-05-05
I've done upgrades on upgrades and they have worked fine (14.04...then 14.10 then 15.04) all were 100% perfect...i have found the secret is to uncheck any ppas installed before upgrading...remove proprietary drivers as d-cosner mentioned and just run a "stock ubuntu" with no major modifications (other then adding programs of course...lol). I can say this holds true for me for main edition ubuntu w/unity...experience could be different with the community versions (like kubuntu/xubuntu/lubuntu/etc)...

Also, for best success...do the upgrade "in place" (with software updater) not upgrade with the iso method...

Once snappy is available, then the need to upgrade should be eliminated as even stable snappy will be rolling style and the need for 6 month versions will likely be phased out...
There likely will be just LTS every 2 years, Snappy Stable (gets new stuff when development snaps are deemed ready) and Snappy Development (works much like development does now...you get it NOW whether it's ready or not for general release)...

---

### Post by Y^2om&amp;#7sgP on 2015-05-05
I have tried upgrading between different releases, and on different hardware, sadly each time it's caused issues.

I've learnt that a backup and fresh install is the way to go.

Another good reason to stay on LTS :p

---

### Post by ajgreeny on 2015-05-05
I get the impression that the move to 15.04 with it's change from upstart to systemd has caused more problems than usual this time, but I have no experience of upgrading from one version to another, having always upgraded by clean install.  I have a separate /home partition which makes the whole new installation a 15 min job, with another hour or so to add back in all the extra applications I use a lot, plus the codecs.

I never update whilst installing, nor do I add the third party apps/codecs at that time either; I simply install very quickly and then update and add everything I need afterwards.  It has always seemed a cleaner way to do the whole job, and probably quicker.

I am also another user who sticks firmly to the LTS versions, though I test the intermediate versions in VirtualBox.

---

### Post by Bucky Ball on 2015-05-05
According to Mark Shuttleworth in the pre-conference webcast last night we are moving to Snappy. Snap apps. The idea is there will be a development tree and a stable tree. If you are on the stable tree, I guess you'd be close to an LTS all the time. Figuring this is going to be like a rolling release, in a sense. Stable apps will be pushed to the stable tree from the dev tree when they're ready. 
[URL="https://plus.google.com/hangouts/onair/watch?hid=hoaevent%2Fcdpv7h8eqipl367pht8mc1oscj8&wpsrc=yta&ytl=9IfgX-k7Hag"]
Have a look.[/URL] V. interesting. Convergence is upon us!

PS: I stick to an LTS release because I need a rock solid install always, but I have four partitions for my playthings, and room for more. I even have 10.10 install in there still somewhere! ;)

---

### Post by ian-weisser on 2015-05-05
> **SeijiSensei said:**
> the current big headline at [ubuntu.com]("http://www.ubuntu.com/") encourages users to install Snappy 15.04
And after that blind alley they will discover the correct desktop download.

> **SeijiSensei said:**
> If you look down to the "Get Ubuntu Desktop" link, it also suggests 15.04, though the page it links to recommends 14.04.2 first and 15.04 below it.
LTS is listed first, and "recommended for most users". Pretty powerful magnet there.
Seems already implemented...and perhaps moot in a few years when Snappy Personal, effectively a rolling release, becomes stable enough to take on both LTS and non-LTS roles.

---

### Post by mörgæs on 2015-05-05
Upgrade as in 'do a fresh install of the latest release': Yes, I tend to recommend that. There are many examples that new kernels have brought better graphics drivers and other improvements behind the curtain, though the user interface is more or less the same. Especially if people use new or new-ish hardware I try to direct them into the newest stuff.  

I mostly use X/Lubuntu where development is slower than Unity. This leads to less surprises in each new release. 

Upgrade as opposed to a fresh install: I agree, they should be discouraged. Swapping a thousand packages or more in one go is a major operation, and I'm surprised that it often works. Still I see it as the biggest hazard to a Linux install.

---

### Post by monkeybrain20122 on 2015-05-05
I don't recommend 'upgrade', I think fresh install is the way to go A separate /home would be recommended too. I don't insist that people should just stick to LTS,-- I normally don't,--but at least wait a few weeks to a month before switching over. New releases tend to be somewhat buggy, unless you are trying to help with reporting bugs it is not a good idea to switch over at the first moment of release. I usually install a new release in an external drive, do some tests, file a few bugs, tweak it to my liking and wait for about a month, if everything works I would just clone it to my main drive.

Now with Unity 8 and Mir looming I am not sure if I want to take risks with the interim releases. 15.04 is very snappy and nice but if I switch over I would have to take a chance with 15.10 because of the short support cycle, as I said I won't switch to 16.04 as my main OS until at least June (same with 14.04) so if 15.10 is as bad as 14.10 I would have to either stick with it for 6 months or switch back to 14.04.

---

### Post by bro2 on 2015-05-05
Agreed that LTS releases should be front and center (most new users like me would think that latest version=best, coming from a Windows mentality), as things are buggy with latest releases (Steam didn't work in 14.10 at first without running the Arch workaround that removes some Steam runtime libraries), and while it can work, the LTS releases require so much less of that maintenance, and much easier to find support for LTS releases online.

---

### Post by monkeybrain20122 on 2015-05-05
The LTS IS featured front and centre on  the download site.

---

### Post by cariboo on 2015-05-05
Interim releases are almost always incomplete when released, this time around, some people seem to have problems with Nvidia drivers, and systemd has actually made most systems boot slower, than when using upstart.

My main system started out as a Utopic install, and has since morphed into Wily, so far there haven't been any show stoppers.

---

### Post by monkeybrain20122 on 2015-05-05
> **cariboo said:**
> Interim releases are almost always incomplete when released, this time around, some people seem to have problems with Nvidia drivers, and systemd has actually made most systems boot slower, than when using upstart.

My main system started out as a Utopic install, and has since morphed into Wily, so far there haven't been any show stoppers.

Well actually driver problems are present in new LTS releases as well, so always a good idea to wait a month at least before one trades in his working OS for a new release, LTS or not. Regarding bootime, 15.04 actually boot faster for me than 14.04 even in an external hard drive. I am quite impressed (both are fast but 15.04 is faster)

---

### Post by buzzingrobot on 2015-05-06
> **d-cosner said:**
> ... so long as the user has not added a bunch of ppa repos and removed proprietary drivers before doing the upgrade.

This.  People often do all kinds of weird stuff to their systems (at least I do) and either don't roll things back to the default state or just forget what they've done (that's me). Whether they stay with an LTS or go with the interim releases, they'll run into the same issues when they do eventually upgrade.

So, prior to attempting an upgrade from one release to another, get the backups in order, roll back the PPA's and the proprietary drivers and all that, and burn a clean install image of the new release on a USB stick so you have something to fall back on if the upgrade attempt trashes everything.

The Linux/Ubuntu media is often *way too* enthusiastic about hyping copy-and-paste instructions without offering any explanations.  Better if at least a few of them would offer help on the "roll back the PPA's and the proprietary drivers.." bit, which I'm sure stumps many users.

(And, yes, the current display about Snappy and Ubuntu Core at ubuntu.com is misleading for first-time visitors.)

---

### Post by monkeybrain20122 on 2015-05-06
> **buzzingrobot said:**
> 

So, prior to attempting an upgrade from one release to another, get the backups in order, roll back the PPA's and the proprietary drivers and all that, and burn a clean install image of the new release on a USB stick so you have something to fall back on if the upgrade attempt trashes everything.


I think people who do "upgrade" instead of a clean install do it for laziness, if they have to do so much work prior to upgrading why not just do a clean install? :) Also I think many people do so out of impulse just because they are prompted by the update manager, that should be disabled since it is dangerous to new users and even old users on a bad day.

---

### Post by craig10x on 2015-05-06
In my case, all i have to do is un check my google chrome ppa in the software settings and i am ready to roll! I always buy computers with intel because they are so linux friendly and intel's closed and open source drivers are identical so i never need to install closed source drivers (in fact, with intel there is no option)...so, not much work for me! ;)

However, before doing it, i always burn an iso of the new version (just in case, as you mentioned) and all my important data (music, photos, videos, documents) are backed up on a usb flash drive in case i need it for a clean install...

That said, so far i have upgraded 14.04 to 14.10 then to 15.04 all without incident...and all went 100% perfect...It takes about and hour and i reboot and i am on the new version...it even cleans up the no longer needed stuff (like old kernels for example) at the end of the process (you just have to tell it it yes when it asks you if you want it to do it's clean up at the end)...

If i do a clean install, it takes several hours for me to get everything back to the way i like it...ex: re-installing apps, transferring data from my back up, make settings, etc...so upgrading saves me the work and seem to run just as good as a clean install...at least that has been my experience...

Again, hopefully in about another year or so, with the snappy stable option, it may be possible to no longer need to upgrade, since it will basically be a rolling style model...

---

### Post by SeijiSensei on 2015-05-06
> **monkeybrain20122 said:**
> Also I think many people do so out of impulse just because they are prompted by the update manager, that should be disabled since it is dangerous to new users and even old users on a bad day.

Things like that prompted my original concern.  There's also the allure of the new.  From my perspective, the main Ubuntu home page should have 14.04LTS as the primary object in the location where Snappy is now, and 15.04 and Snappy down below in the area where "Desktop Linux" now appears with a heading that labels those items "for experienced users."

Other flavors:
Kubuntu: advertises 15.04; rather dangerous I think, given that it includes the upgrade to KDE5
Lubuntu:  advertises 14.04 at the top of the page; 15.04 below
Xubuntu: advertises 14.04 and 15.04 side-by-side with 14.04 described as "the recommended version for all environments that require stability" and 15.04 as the "latest regular release."  With that comparison, I'd probably pick 15.04 even if I had never used Ubuntu before.

---

### Post by monkeybrain20122 on 2015-05-06
> **craig10x said:**
> In my case, all i have to do is un check my google chrome ppa in the software settings and i am ready to roll! I always buy computers with intel because they are so linux friendly and intel's closed and open source drivers are identical so i never need to install closed source drivers (in fact, with intel there is no option)...so, not much work for me! ;)

However, before doing it, i always burn an iso of the new version (just in case, as you mentioned) and all my important data (music, photos, videos, documents) are backed up on a usb flash drive in case i need it for a clean install...

That said, so far i have upgraded 14.04 to 14.10 then to 15.04 all without incident...and all went 100% perfect...It takes about and hour ...

If i do a clean install, it takes several hours for me to get everything back to the way i like it...ex: re-installing apps, transferring data from my back up, make settings, etc...so upgrading saves me the work and seem to run just as good as a clean install...at least that has been my experience...

.

The day before yesterday installed 15.04 on an external drive to take a spin. Took 10 minutes to install from a live usb (it almost took longer to make the live usb), and took about 15 minutes to add ppas and install the applications and tweak the settings, the most time consuming thing was to set the hot corners in compiz and to make sure that they are remembered on reboot (I copied some .config files from 14.04, if I were to do a fresh install on top on Trusty I wouldn't have to do this even because I have a seperate /home) and in less than an hour I was basically done, that included compiling vlc and mpv from source. :) There are some more tricky compiling and installation of third part applications that I haven't gotten around to yet but then most people don't compile from source,--and those wouldn't survive upgrade anyway,--  the third party applications were installed in $HOME that means they would have survived a fresh install had I installed on top of Trusty.

My system is heavily tweaked so it would take me a lot longer just to restore it to a pristine condition for 'upgrade' to even work. :)

---

### Post by mattharris4 on 2015-05-08
I agree that 99% of the population running Canonical OSes should only use LTS versions of them.  I warn people that the interim releases between LTS versions are for developers, testers and programmers only.  Certainly anyone using a version of 15.10 (Wily) as of May 2015 outside of programmers and developers is nuts as that has barely been written, basically untested and is still in alpha status (until reading this thread I didn't even know it was out at all yet).  Certainly any daily computer running a Canonical OS should run a supported LTS version.  Also, daily use computers running Linux should only be running well-developed and supported OSes such as Canonical's.  Linux Mint is probably OK as well but if possible thinly supported OSes such as Damn Small Linux, Puppy Linux, Tiny Core and the like should be reserved for programmers and developers to use on computers that no one is dependent on for daily life.  

Unfortunately with Canonical OSes and Mint requiring at least 1-1.5GB of RAM (Lubuntu) or more and at least a relatively recent Celeron CPU to run for all tasks we do have to send some with older computers to Puppy (which my understanding is that it will run on 256MB of RAM and a Pentium 2 CPU for most people but that is not from personal experience) and hope for the best but that isn't most people.  I wish Canonical would start development on an OS that will run on old computers, be well supported and run both at least median Firefox use including YouTube videos and the OS within 256MB of RAM on a Pentium 2 equipped computer (which takes 700-800MB of RAM in Lubuntu) like Puppy is purported to do.

---

### Post by craig10x on 2015-05-08
Yes, but once the interim (6 month version) is released, it's not just for testers, developers and programmers...we are not talking about upgrading during DEVELOPMENT but after FINAL RELEASE in this thread...
I upgraded from 14.04 to 14.10 and now to 15.04 (upon final release in each case, of course) and 15.04 is the best yet in terms of stability, smoothness and snappy performance for me, so i am very glad i didn't stay on LTS...So, i would disagree that LTS is best for 99%...I also like getting newer kernels, apps and features...

Hopefully, when snappy stable is a practical option...will have a rolling stable version of ubuntu to use instead of needing to upgrade every 6 months for the latest stuff ;)

---

### Post by buzzingrobot on 2015-05-08
> **mattharris4 said:**
> I agree that 99% of the population running Canonical OSes should only use LTS versions of them.

People should use the release that best meets their requirements.  If that's a non-LTS release, then that's what they should use. Personnaly, I've had as much trouble with LTS releases as with non-LTS release, and that amounts to very little trouble, indeed.  It's a myth that the non-LTS releases are fragile and bug-ridden.

IMO, most problems in Ubuntu are the result of user mistakes, typically installing the wrong software from the wrong, unsupported sources, and very often forgetting it's there.  Ditto any other established major distribution.  They're all mature and they are all well-managed.  Play by the rules and you will likely be OK.

  > I warn people that the interim releases between LTS versions are for developers, testers and programmers only.

See above.

  > Certainly anyone using a version of 15.10 (Wily) as of May 2015 outside of programmers and developers is nuts...

15.10 is a different category. It's not yet a release.  Grouping it in with actual non-LTS releases is misleading. Anyone using pre-release software ought to know the risks, and anyone or any website that instructs people how to install it without telling them that is acting irresponsibly.

That said, my experience with the last few pre-release editions has been consistently rather smooth. None have broken and none have caused loss of data.  At this stage, 15.10 will be essentially identical to 15.04. Change comes gradually; it's not like there's a squadron of Canonical coders that start over for every release. (15.10 will eventually see a fair amount of interesting new stuff, so down the road the pre-release may, in fact, get a bit interesting.)

---

### Post by monkeybrain20122 on 2015-05-08
Only problem with non LTS is the short support cycle, so e.g 15.04 is great now but 15.10 may not be (as they are probably "previewing" a lot of not fully baked stuffs that they want to put in 16.04) Other than that I don't find LTS more stable or better performant than interim releases in general.  e.g both 13.04 and 13.10 are much better than 12.04.

---

### Post by mattharris4 on 2015-05-09
> **craig10x said:**
>  Hopefully, when snappy stable is a practical option...will have a rolling stable version of ubuntu to use instead of needing to upgrade every 6 months for the latest stuff ;)

As long as Canonical completely develops and vets everything before rolling it on to general users of the OSes a rolling release plan will be convenient.  Unfortunately it will only take once or twice of some programmer accidentally rolling alpha or beta code/features to general users and the code/features causing major problems for them to cause people to switch to something else in droves.  I don't think I would switch to a rolling release methodology because of that.  It is much safer for Canonical's reputation to vet and approve using the current system of double and triple testing with embargo dates for soon to be released versions allowing for about three weeks to re-vet the release, checking everything at least twice than with a rolling release method where any Canonical programmer could approve and send an update out.

---

### Post by neu5eeCh on 2015-05-09
Every time I've upgraded, something has gone wrong. I was just spending some time in the support threads, and there are a number of issues seemingly related to upgrades. The trouble is in knowing what is upgrade-related and what is new release related. Users write: Blahbity-blah stopped working in 15.04! Well, maybe.  Ubuntu has no skin in the game, so I'd say they have no interest in the matter one way or the other. It's just all the volunteers here at the forum who are having to fix all the upgrade problems. IMHO, time would be better spent teaching users how to make fresh installs easier. I've learned to install a secondary partition which holds my home folder (sort of) via symbolic links. I only link the folders specifically related to apps whose configs I don't want to lose. It makes a fresh install considerably easier. If I were smart enough, I could probably automate the process with a batch file (as others have).

---

### Post by craig10x on 2015-05-09
One thing that was frequently mentioned is that if a package causes a regression it can easily be rolled back to the previous version...not sure exactly how that will work, though...Also, it will be thoroughly tested in the development end of snappy first, and i would imagine that when it did get pushed to stable it will have been well tested already...so that is a BIG advantage over the old style way of doing a rolling release...so i am not sure if you can really judge how this will work on the basis of the old rolling model...this is something entirely different...When was the last time an update borked your android phone?  I think this will work very much in a similar way...

---

### Post by Tadaen_Sylvermane on 2015-05-11
For me anything between LTS releases has always been trouble, vanilla Ubuntu in particular. But then I've always had problems with Unity regardless of version. When I try to turn someone to Linux , or *buntu I only steer them towards the LTS releases as they have consistently given me little to no real difficulties over time. Occasionally there are glitches and such but on average LTS is rock solid for me. Might be blasphemy but I would argue LTS is almost if not more stable (only in my limited experience) than straight Debian, and has a larger repo base as well with many of the packages I need that aren't in the main Debian repos.

---

### Post by CosmicFlux on 2015-05-13
> **SeijiSensei said:**
> Now that 15.04 is out, we're seeing an array of complaints from people who upgraded and encountered problems.  Has the time come for the major *bunutu websites to stop pushing current releases and recommend LTS versions instead?  I understand the PR value of appearing to be moving forward all the time, but I also think probably 90% or more of the user base should be using LTS releases.  I've even seen postings lately of people upgrading production servers from 14.04 to 15.04.  Should there be more of an effort to drive most users, especially new users, to the LTS versions and away from interim releases?

I would go for a fresh install every time. As long as your using a separate **/home **partition your personal data will be unaffected. Upgrades can be tricky, especially if you've made fundamental modifications to the system. If the thought of doing a clean install every 6 months doesn't appeal to you then just use an LTS edition and you'll only have to do it every 5 years, or if you'd like to take advantage of new features then every LTS release.

Cosmic

---

### Post by mikodo on 2015-05-13
I stick to LTS's with fresh installs. Now, symblink / and its ~/ to data. 

I had an interesting thing just happen. I only quit using 12.04 a week ago, as I couldn't find time to do it earlier. Fresh installed 14.04 on a new HD and finished with configuring Xubuntu as I like. I still use (have other plans cooking), bcrypt to encrypt an *important file that holds, contacts, emails, passwords, banking stuff, that I like to have on disk, but not readily available to an intruder or computer loss for anyone to see. I opened up the bcycrt (1.8 it turns out) , instead of the 10.04 and 12.04 bcrypt 1.6 and had added new data since this new install. Yesterday, I couldn't open it, and *eventually got a crash report that included segfaults (whatever that is). I was in good shape because I still have 12.04 on an  unused HD now, with all it's apps and I could have gotten the file open after sticking it in the puter, (saved in case there were problems, in my new install). Long story shorter, I was able to *safely install briefly only bcrypt 1.6 from 12.04 repos, (cause I know how) and it opened the file fine. I am done with bcrypt now, cause I have other plans.

All that to say, that this was a very interesting thread to read, and to share the importance of having some backup plans for stuff, be it LTS, interim releases, upgrading, fresh install and probably with Snappy. Stuff, just happens.

end of rant.

---

### Post by craig10x on 2015-05-14
Well, i have now gone back to 14.04 LTS...

I will have to see if i can "resist" the temptation to return to the current 15.04 version again...I'd like to try to go on a 2 year LTS to LTS (with an upgrade to the new version) if i can...But if i do decide to move back to 15.04 i wouldn't have any hestitation to do it with 2 upgrades rather then clean install, based on my past excellent success using that method, as i previously mentioned...;)

Of course, if snappy personal stable is ready for prime time by 16.04 and available, if i decided to try it, i would have to do a clean install, of course...
It certainly would be interesting to try an LTS to LTS upgrade (never did one) that would be interesting to see how it would go...

---

### Post by monkeybrain20122 on 2015-05-14
Snappy is at least one year away to be in production shape. I wouldn't worry about it when folk's dilemma is whether to trade in 14.04 for 15.04 :)

---

### Post by mikodo on 2015-05-14
> **craig10x said:**
> It certainly would be interesting to try an LTS to LTS upgrade (never did one) that would be interesting to see how it would go...
+1

Never tried, and I hope I remember to try this "first", next LTS install.

---

### Post by craig10x on 2015-05-14
Yeah, you figure: "what do i have to lose" cause if it doesn't work out, you were going to clean install it anyway...but if it does...you will be all set ;)

---

### Post by C.S.Cameron on 2015-05-14
Quote Originally Posted by craig10x
It certainly would be interesting to try an LTS to LTS upgrade (never did one) that would be interesting to see how it would go...

I have requested to my wife that she do occasional software updates to her computer and that she avoid any suggestion to upgrade.
Yesterday when I got home she said "It's asking something about keeping configuration files".

So far her upgrade from 12.04 to 14.04 has been flawless.

In the past we have installed to a new HDD and copied home from the old disk, this went smoother than reusing an existing /home partition. 
I recall both of these methods had issues with permissions and such.

---

### Post by craig10x on 2015-05-14
Glad to hear that it went so well...i figured that maybe there was more chance of a problem because over 2 years there is so many more changes then there are in 6 months, but apparently not necessarily so :)

---

### Post by Erik1984 on 2015-05-15
This is a difficult issue. Probably 'noobs' are best served with a stable system for (at least) 2 years and not risking to ruin their installation. OTOH if too many users stick with the LTS edition there are not enough users to get feedback on all new features and application version changes. Suppose everyone had stayed with 10.04 and only upgraded at 12.04... that would've decreased the ability to improve Unity.

---

### Post by SurfaceUnits on 2015-05-15
I have always used 'sudo update-manager -d' to upgrade and have not had any major issues.

---

### Post by ian-weisser on 2015-05-15
> **SurfaceUnits said:**
> If I wait until after 14.10's EoL date to upgrade my 14.04, how does the upgrade proceed?

Hmmm. I don't understand the relevance to the the thread.

The specific answer to the question is: It doesn't proceed.
Once 14.10 is withdrawn, those repositories are disconnected.
(There is one way, the repositories are actually just moved to a different URL. But they are not updated anymore!)

Why would anyone wish to upgrade away from an LTS to an EOL release?
Most EOL-update cases I have seen in these forums are users already on EOL versions trying to update toward an LTS.

---

### Post by neu5eeCh on 2015-05-15
> **ian-weisser said:**
> Why would anyone wish to upgrade away from an LTS to an EOL release?

Kernel.

---

### Post by sudodus on 2015-05-15
The 14.10 'utopic' kernel is 'backported to trusty' in the 14.04.2 LTS release, and we can expect that the 15.04 'vivid' kernel will be 'backported to trusty' in the 14.04.3 LTS release ... until the next LTS release 16.04. That kernel will be 'backported to trusty' in the 14.04.5 LTS release.

---

### Post by mikodo on 2015-05-15
> **sudodus said:**
> The 14.10 'utopic' kernel is 'backported to trusty' in the 14.04.2 LTS release, and we can expect that the 15.04 'vivid' kernel will be 'backported to trusty' in the 14.04.3 LTS release ... until the next LTS release 16.04. That kernel will be 'backported to trusty' in the 14.04.5 LTS release.  Cool! Never knew that. Thanks! Does this help with newer hardware support?

---

### Post by sudodus on 2015-05-15
Yes, if you install from 14.04.2, you get it directly. But update/dist-upgrade  will only bring the bug-fixes. You need to upgrade the HWE (hardware enablement stack) to make the move from the trusty kernel to the utopic kernel (etc for vivid ...).

See this link [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by neu5eeCh on 2015-05-15
> **sudodus said:**
> The 14.10 'utopic' kernel is 'backported to trusty' in the 14.04.2 LTS release, and we can expect that the 15.04 'vivid' kernel will be 'backported to trusty' in the 14.04.3 LTS release ... until the next LTS release 16.04. That kernel will be 'backported to trusty' in the 14.04.5 LTS release.

Yeah, it's not as straightforward as you make it sound. Not all drivers are backported -- [but selectively]("https://help.ubuntu.com/community/UbuntuBackports"). To find out which? [It's possible.]("http://askubuntu.com/questions/11443/how-can-i-tell-which-drivers-are-backported-to-stable-kernels") Furthermore, just because you're running 14.04 [doesn't mean you get the same kernel as 14.04.2]("http://askubuntu.com/questions/587609/how-to-do-ubuntu-upgrade-14-04-to-14-04-2") unless you specifically update the kernel (see sudodus post directly above).

So, if you want the best chance for hardware compatibility, you upgrade.

---

### Post by monkeybrain20122 on 2015-05-15
> **ian-weisser said:**
> Hmmm. I don't understand the relevance to the the thread.

The specific answer to the question is: It doesn't proceed.
Once 14.10 is withdrawn, those repositories are disconnected.
(There is one way, the repositories are actually just moved to a different URL. But they are not updated anymore!)

Why would anyone wish to upgrade away from an LTS to an EOL release?
Most EOL-update cases I have seen in these forums are users already on EOL versions trying to update toward an LTS.

I don't think he wants to upgrade to an eol release, rather he was wondering what will happen to the 14.04 -> ? upgrade route when the next step of the chain is broken, since usually upgrade from A to B would proceed through all the intermediate releases (i think LTS to LTS proceeds through a direct route, though I am not sure as I always do clean install)

---

### Post by mikodo on 2015-05-15
> **sudodus said:**
> See this link [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) :)

---

### Post by mikodo on 2015-05-15
> **VTPoet said:**
> Yeah, it's not as straightforward as you make it sound. Not all drivers are backported -- [but selectively]("https://help.ubuntu.com/community/UbuntuBackports"). To find out which? [It's possible.]("http://askubuntu.com/questions/11443/how-can-i-tell-which-drivers-are-backported-to-stable-kernels") Furthermore, just because you're running 14.04 [doesn't mean you get the same kernel as 14.04.2]("http://askubuntu.com/questions/587609/how-to-do-ubuntu-upgrade-14-04-to-14-04-2") unless you specifically update the kernel (see sudodus post directly above).

So, if you want the best chance for hardware compatibility, you upgrade.Oh, Okay. Thanks.

---

### Post by sudodus on 2015-05-15
But referring back to the opening post and title of this thread, you should backup your system before upgrading the hardware enablement stack. There might be issues with your hardware (with the new drivers), and complicated to get back to the previous system (unless you have a current backup).

If your computer is running well with the original kernel (and only minor upgrades for security etc), it might be a bad idea to upgrade the hardware enablement stack. At least you should try it live (booted from the corresponding iso file, for example Ubuntu 14.04.2 LTS) before doing it.

---

### Post by monkeybrain20122 on 2015-05-15
While probably safer than a full blown upgrade, the LTS hardware enablement stack is apparently still not quite safe based on 12.04 point upgrade woes threads. 

Way I see it, if you are using the same hardware on the LTS you don't need hwe and if you are getting new machine or the LTS doesn't work well on your hardware you should simply do a clean install of a newer release. The hwe is neither here nor there and since they are not supported through out the duration of the LTS one would need to (manually) migrate to the next hwe when the time comes, defeating the purpose of LTS.

Edited:  if something is not working I want to fix it right now if the driver is  already available, not to wait x months for the next point release. If for some reasons I need a newer kernel I would just grab it from mainline,--kernel 3.19 in Trusty fixed a problem with vlc crashing. I can get up to date graphic driver from ppas such as xorg-edgers or oibaf, if something goes wrong it is easier to roll with ppa-purge. Rolling back would break a whole bunch of things if one goes the route of hardware enablement (I ran a test on 12.04 before I erased it for 13.04)

---

### Post by mikodo on 2015-05-15
I will do the reading in the links. But, I thought I would throw this out now, with the experts here.

When I fresh installed Xubuntu 14.04 last week, to a new HD, I chose the .iso for Xubuntu 14.04.1 because it was (I thought), not to enable the the newer hardware support of 14.04.2.) I have older hardware now). I was surprised to see the update come soon after the install, for 14.02. But, no problems with hardware. see this:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
mikodo@mikodo:~$ lsb_release -r
Release:    14.04
uname -r
3.13.0-52-generic
uname -a
Linux mikodo 3.13.0-52-generic #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by sudodus on 2015-05-15
Yes, that is confusing. A lot of software is upgraded. But the HWE is not upgraded, and you are still running the trusty kernel (3.13 series, not 3.16 series of utopic). You can check that with

```
uname -a
```

---

### Post by monkeybrain20122 on 2015-05-15
You can have 14.04.2 without the hardware enablement. I am on 14.04.2 now,--upgraded from 14.04.0 installed one year ago,-- but no hwe, still same kernel 3.13, -- I am running 4.02 but I installed it manually from mainline.
Check your kernel version instead of ubuntu version

---

### Post by mikodo on 2015-05-15
> **monkeybrain20122 said:**
> You can have 14.04.2 without the hardware enablement. Thank you. That's what I was guessing it was. I still need to read the links.

Edit: uname -r, uname -a  added to earlier post. So, as sudodus said, no  3.16 series of utopic)

Now I know what this means, from here:

[http://www.omgubuntu.co.uk/2015/02/ubuntu-14-04-2-lts-released-includes-3-16-kernel](http://www.omgubuntu.co.uk/2015/02/ubuntu-14-04-2-lts-released-includes-3-16-kernel)

"*The new hardware enablement stack will be installed by default if you  install from 14.04.2 installation media, but if you’re humming along  nicely with the current versions of Xorg and the Linux kernel on 14.04  and 14.04.1, fear not – the new stack is not installed by default and is  completely opt-in".*

---

### Post by mikodo on 2015-05-15
> **monkeybrain20122 said:**
> Edited:  if something is not working I want to fix it right now if the driver is  already available, not to wait x months for the next point release. If for some reasons I need a newer kernel I would just grab it from mainline,--kernel 3.19 in Trusty fixed a problem with vlc crashing. I can get up to date graphic driver from ppas such as xorg-edgers or oibaf, if something goes wrong it is easier to roll with ppa-purge. Rolling back would break a whole bunch of things if one goes the route of hardware enablement (I ran a test on 12.04 before I erased it for 13.04) Thanks, for all you said. I finally got to reading all the links, (it "can be confusing", sudodus). Then, tried to learn what you said here, monkeybrain... An example that seems pertinent, is that I have noticed in this new 14. 04.1/2 install, that vlc doesn't play the video always. I tried a supposed lighter player gnome-mplayer, and it did the same thing, initially. With both, reboots would allow them to show visual. Point  to what you said here, I could try [xorg-edgers]("http://www.ubuntuupdates.org/ppa/xorg-edgers") to see if that might fix it, on my intel machine and if there are problems, I could run  ppa-purge and go back. I think I have that right. There is, really a lot to learn about package-management, if that is what this, is.

To OP. I apologize for hi-jacking your thread.

---

### Post by SeijiSensei on 2015-05-16
> **VTPoet said:**
> So, if you want the best chance for hardware compatibility, you upgrade.
That applies to only a very small fraction of all the hardware out there, and it should only matter when the hardware you have isn't working properly.  The vast majority of users running vanilla hardware, like the millions of all-Intel boxes, should never need to do this.  

"If it ain't broke, don't fix it," applies strongly to computers and software.

> **monkeybrain20122 said:**
> if something is not working I want to fix it right now if the driver is  already available, not to wait x months for the next point release. If for some reasons I need a newer kernel I would just grab it from mainline,--kernel 3.19 in Trusty fixed a problem with vlc crashing. I can get up to date graphic driver from ppas such as xorg-edgers or oibaf, if something goes wrong it is easier to roll with ppa-purge. Rolling back would break a whole bunch of things if one goes the route of hardware enablement (I ran a test on 12.04 before I erased it for 13.04)

Anyone who understands this paragraph isn't the sort of person I was talking about when I started this thread.

---

### Post by buzzingrobot on 2015-05-16
> **SeijiSensei said:**
> That applies to only a very small fraction of all the hardware out there, and it should only matter when the hardware you have isn't working properly.  The vast majority of users running vanilla hardware, like the millions of all-Intel boxes, should never need to do this.  

"If it ain't broke, don't fix it," applies strongly to computers and software.



True, true. 

On the other hand, if someone has maintained a default (and that means, among other things, no PPA's and no proprietary drivers) system that's got happy hardware, moving up to the next release version *should* turn out OK, if that distribution's packagers have been behaving themselves. Fresh installs are likely safer than inplace upgrades, because, if for nothing else, we forget what we've done to our systems. 

Booting a live image and checking things out ought to be done in all cases. Stuff happens, and you might be the first to find it.

More of us, also, should be reading release notes, etc., before we jump to the new stuff. Not every bug found in the development phase is, or can be, fixed before release. Sometimes workarounds are needed.  (One thing Fedora does that I like is post a "Common Bugs" page for each release. It's what it sounds like, and often offers workarounds and solutions.)

---

### Post by sudodus on 2015-05-16
> **buzzingrobot said:**
> [QUOTE=SeijiSensei;13286254]That applies to only a very small fraction  of all the hardware out there, and it should only matter when the  hardware you have isn't working properly.  The vast majority of users  running vanilla hardware, like the millions of all-Intel boxes, should  never need to do this.  

"If it ain't broke, don't fix it," applies strongly to computers and software.



True, true. 

On the other hand, if someone has maintained a default (and that means,  among other things, no PPA's and no proprietary drivers) system that's  got happy hardware, moving up to the next release version *should*  turn out OK, if that distribution's packagers have been behaving  themselves. Fresh installs are likely safer than inplace upgrades,  because, if for nothing else, we forget what we've done to our systems. 

Booting a live image and checking things out ought to be done in all  cases. Stuff happens, and you might be the first to find it.

More of us, also, should be reading release notes, etc., before we jump  to the new stuff. Not every bug found in the development phase is, or  can be, fixed before release. Sometimes workarounds are needed.  (One  thing Fedora does that I like is post a "Common Bugs" page for each  release. It's what it sounds like, and often offers workarounds and  solutions.)
[/QUOTE]

+1

---

### Post by bravo sierra echo on 2015-05-16
In eight years with Ubuntu I've never had an upgrade work properly.  And I don't use bleeding edge stuff, no dodgy repos etc. Just tried it again with 15.04 and got the usual result - really buggy video and some very odd bugs - until I gave up and did a fresh install from a DVD.  I don't know why I keep trying even.

---

### Post by ian-weisser on 2015-05-16
...and in the same period I've had perfect upgrades every time.

---

### Post by craig10x on 2015-05-16
and the same here...100% perfect every time ;)

---

### Post by mikodo on 2015-05-17
On Upgrading:
> **buzzingrobot said:**
> The Linux/Ubuntu media is often *way too* enthusiastic about hyping copy-and-paste instructions without offering any explanations.  Better if at least a few of them would offer help on the "roll back the PPA's and the proprietary drivers.." bit, which I'm sure stumps many users.
On Fresh-installs:
> **VTPoet said:**
>   Ubuntu has no skin in the game, so I'd say they have no interest in the matter one way or the other. It's just all the volunteers here at the forum who are having to fix all the upgrade problems. IMHO, time would be better spent teaching users how to make fresh installs easier. 

So, I glanced to see what the official Ubuntu pages said about [Ubuntu Upgrading]("http://www.ubuntu.com/download/desktop/upgrade") and [Ubuntu Downloading]("http://www.ubuntu.com/download/desktop"). 

Both, gave not that much insight, on how to avoid problems.

Both, say:
 
         **Helping hands**

         If you get stuck, help is always at hand.
         
[LIST]
[*][Ask Ubuntu &#8250;]("http://askubuntu.com/") 
[*][Ubuntu Forums &#8250;]("http://ubuntuforums.org/") 
[*][Ubuntu Discourse &#8250;]("http://discourse.ubuntu.com") 
[*][Live Support Chat &#8250;]("https://help.ubuntu.com/community/InternetRelayChat") 
[/LIST]
It seems, Ubuntu is expecting the "forums and such", to help with problems, "after the fact". Maybe, it would be helpful if experts could start a thread and have  other experts contribute in it, on how to avoid pitfalls, with both. Possibly, someone could even make a succinctly polished Community Page on it. It might help "all" concerned.

I am in no position to do any of this but, would certainly benefit from the efforts of our experts, from something like this.

Are these enough?

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

[URL="https://help.ubuntu.com/community/GettingUbuntu"]https://help.ubuntu.com/community/GettingUbuntu

[/URL][http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

---

### Post by SurfaceUnits on 2015-05-17
I just went from Ubuntu Gnome 14.04-->14.10-->15.04 and installed Gnome 3.16 and it is working perfectly. I hate setting up a new install and getting it back to how I want it. Had one file issue in the 04 to 10 upgrade; un-installed the file and the update went fine. All my extensions are working with 3.16.

[ATTACH=CONFIG]262026[/ATTACH]

---

### Post by ian-weisser on 2015-05-17
> **mikodo said:**
> It seems, Ubuntu is expecting the "forums and such", to help with problems, "after the fact". Maybe, it would be helpful if experts could start a thread and have  other experts contribute in it, on how to avoid pitfalls, with both.

The Ubuntu release team can test only a finite number of upgrade paths.
Ubuntu does already automatically detect and prevent many common pain points. Example: Automatically disabling non-Ubuntu sources.
The "forums and such" are the proper community support channels.

I think we already have plenty of documentation and advice on how to upgrade well. It is often unread.
We've helped enough people with broken upgrades over the years to know what the common pitfalls are: Mostly apt conflicts caused by non-Ubuntu sources. Some bugs and regressions. A few total failures, usually traced to the impatient user doing something quite unwise.

---

### Post by mikodo on 2015-05-17
> **ian-weisser said:**
> 
I think we already have plenty of documentation and advice on how to upgrade well. It is often unread. Alright.

---

