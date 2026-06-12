---
title: "With Dell comes great responsibility: Perfect Apt"
date: 2007-05-02
forum: The Cafe
---

### Post by cptnapalm on 2007-05-02
Like most people here, I'm very happy to see that Dell picked Ubuntu for its Linux offering.  With a hardware vendor, the glitches due to drivers should not be a problem as it will, presumably, be pre-tested in order ensure compatibility.  Ubuntu's usability as a desktop needs no introduction to the people on this forum.  The one thing which I do have a concern about, though, is upgrading Ubuntu releases.

My first Ubuntu was 5.10.  Upgrading to 6.06 hosed the install.   6.06 to 6.10 worked for the most part; the part that didn't work was X which is not an insignificant thing.  A second computer was upgraded from 6.06 to 7.04 and was completely hosed; not only did X not start, there was no console login available either.

Windows only has major new versions every few years.  Consequently, most people stick with the version of Windows they have until the system dies or gets sold or given away.  Windows upgrades frequently have problems.  Apple has only a small set of systems, comparatively speaking, to support with their upgrades thus minimizing the possible trouble spots for new OS X versions which appear every couple of years.

Ubuntu has two big releases a year on systems from the delightfully anarchic PC world.  The installer is as sweet as I could ever want; playing tetris and reading Slashdot while installing an operating system at a coffee shop is just awesome.

As I see it, part of the problem is with apt itself.  Apt works 95% of the time.  Of the non-working chunk, 3% are not too bad.  The other 2% are system destroying.  Distribution upgrades disproportionately fall in that 2%.  Apt, during that 95%, is one of the best things that has ever been put into an operating system.  But apt gone wrong is a total disaster.

To a certain extent, Canonical seems to focus on one thing above all else for each release.  The installer got massive attention and is now fantastic.  The shift from the Sys V init to Upstart, while not particularly noticable for most users, was a damn good thing.

As Dell is to offer Ubuntu Linux pre-installed, I think that the best bet is for Canonical to focus on ways of ensuring that the upgrade process becomes rock solid.  There should be one way to do the distribution upgrade which absolutely works instead of the several ways there are now which frequently do not.  A solution which does not necessitate upgrading to each of the intervening releases.

In short, I believe that with the influx of people which is sure to occur with Dell's new offering, the focus of the next version of Ubuntu should go into apt-get dist-upgrade.  It has taken so much work by so many people over so many years for Ubuntu to be the Linux which makes it onto the desktop for the top first tier PC maker.  Ensuring that those people who take the chance on a new operating system are rewarded with a smooth bi-annual transition to the newest, latest release ought to be the top priority.  The goal should be to perfect apt.

---

### Post by PriceChild on 2007-05-02
Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.

---

### Post by cptnapalm on 2007-05-02
Iz uh so-a sory dat i izza so dumm.  U izza jus sooa smarrt.

---

### Post by lapsey on 2007-05-02
Yeah. Upgrading will work perfectly providing you havent installed foreign stuff or tweaked it or done whatever nonstandard thing with your system.

> **cptnapalm said:**
> Iz uh so-a sory dat i izza so dumm.  U izza jus sooa smarrt.

I don't quite understand what this means.

---

### Post by PriceChild on 2007-05-02
> **cptnapalm said:**
> Iz uh so-a sory dat i izza so dumm.  U izza jus sooa smarrt.And you now expect people to take you seriously?

---

### Post by WinterWeaver on 2007-05-02
rofl !!

I'm trying to figure out if he's actually mocking Pricey, being sarcastic, or if he's being serious in a very obscure way?

rofl!
Almost worthy of a Sig-Quote :P

---

### Post by H.E. Pennypacker on 2007-05-02
> **PriceChild said:**
> Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.

I can understand where developers are coming from, but one must also understand the other side.  Users like myself have to do some serious tweaking in order to get certain things working.  That means the configuration files are altered.  

This should not throw developers off, though.  There are so many Broadcom wireless card users, it is fair to assume these people will be changing certain configuration files.  Now, don't get me wrong.  I'd rather not alter anything, but this is how it works.

Developers could take into account the number of people like me, and prepare for the configurations that we change.  The same goes for others (e.g. Nvidia people, but I don't know much about Nvidia to say much).

My problem is not APT so much.  I have a bigger problem with upgrades erasing or changing all the hard work that I've put into an installation.  A backup is a great way of dealing with this, but you can't possibly know everything an upgrade is going to change (I've backed up everything the upgrade tool told me it was going to replace, but this did not help).  Backing up everything is not an option either.  

My opinion: make upgrades more smooth.

---

### Post by cptnapalm on 2007-05-02
So installing Listen, Compiz and XGL is a massive change which will completely destroy an upgrade?  That is ALL that was done and the system was completely borked.  No X.  No command line login.

Did you miss the little X problem from last year?

Did you miss all the reports of problems upgrading from Dapper to Edgy?

Adding programs should NEVER destroy an OS upgrade.   Never.

---

### Post by davahmet on 2007-05-02
Apt, alonog with Synaptic, is an awesome package manager, usually.  As you say, for the most part, everything works well and life is grand.  However, on those infrequent occasions that things go wrong, it can go very, very, horribly wrong.  This is the type of going wrong that causes massive discharges of brain-goo in a fit of frustration.  When we are now suddenly exposed to a much broader market because of Dell's decision, it is also the type of wrong that is frankly disasterous.

Normally in release management, there is a back out plan to roll back changes when things go wrong.  Now of course we can also do this with Apt and Synaptic, but the process for doing so can be a bit cryptic and certainly intimidating for someone newly introduced to Ubuntu.  The worst thing would be for someone who has suddenly lost their graphics capability because of either a kernel or Xorg update to reach for an installation CD, any installation CD.  Only slightly less damaging is for them to feel they need to call Dell tech support.  Putting the novice user in this position is a betrayal of trust in that the implication has been that Ubuntu on Dell "just works".  With our package manager, we need to provide an easy-to-use rollback.

By this, I mean that the user needs to have a one-click option to say, "No, that update borked everything. Please undo it and report the problem."  To keep the well-earned trust of novice users, this realy is a huge deal.  For us more exerienced users, it may seem trivial, but through the fresh eyes of the newly initiated, this is an absolute must.

---

### Post by PriceChild on 2007-05-02
> **H.E. Pennypacker said:**
> I can understand where developers are coming from, but one must also understand the other side.  Users like myself have to do some serious tweaking in order to get certain things working.  That means the configuration files are altered.  Then do tweaking the "right" way and don't break things?

> **H.E. Pennypacker said:**
> This should not throw developers off, though.  There are so many Broadcom wireless card users, it is fair to assume these people will be changing certain configuration files.  Now, don't get me wrong.  I'd rather not alter anything, but this is how it works.

Developers could take into account the number of people like me, and prepare for the configurations that we change.  The same goes for others (e.g. Nvidia people, but I don't know much about Nvidia to say much).Nvidia drivers are supported by Ubuntu in Main. 7184, 9631 AND 9755. These "could" "break" an upgrade if someone installed it manually for some strange reason. However its a very quick fix which you should know if you installed it manually. I don't see how installing broadcom drivers manually could ever break the rest of ubuntu on upgrades?

> **H.E. Pennypacker said:**
>  My problem is not APT so much.  I have a bigger problem with upgrades erasing or changing all the hard work that I've put into an installation.  A backup is a great way of dealing with this, but you can't possibly know everything an upgrade is going to change (I've backed up everything the upgrade tool told me it was going to replace, but this did not help).  Backing up everything is not an option either.  

My opinion: make upgrades more smooth.Package upgrades do not replace user altered configuration files without asking.

---

### Post by dca on 2007-05-02
Howza' bout I senz you a copy 'o Windows ME???

---

### Post by aysiu on 2007-05-02
> **dca said:**
> Howza' bout I senz you a copy 'o Windows ME???
Upgrades of entire operating systems (Windows, Mac, or Ubuntu) often lead to breakage. For example: [My wife "dist-upgraded" to Tiger and it messed up her user profile...](http://ubuntuforums.org/showthread.php?t=80341&highlight=wife+tiger)

The real shock to new users won't be that upgrades break your system. The real shock will be that upgrades happen every six months instead of every three to six years!

This is a real issue. If you skip an upgrade, that can lead to even more breakage (Dapper to Feisty, or Edgy to Gutsy).

Not sure what the solution is, though.

---

### Post by PriceChild on 2007-05-02
> **cptnapalm said:**
> So installing Listen, Compiz and XGL is a massive change which will completely destroy an upgrade?  That is ALL that was done and the system was completely borked.  No X.  No command line login.Compiz/beryl/compositing are alpha software. You are warned that it is unstable and "use at own risk". Don't you dare try and call that stable.

> **cptnapalm said:**
> Did you miss the little X problem from last year?That is a problem with broken packages during a release's life... not between an upgrade from one distro to the next. It was human error and fixed as soon as it could be. New measures have been put in place such as the "proposed" repository.

> **cptnapalm said:**
> Did you miss all the reports of problems upgrading from Dapper to Edgy?No. Most of these were due to certain 3rd party scripts forcing package installs.

I repeat: If you use "Ubuntu Supported Software" from the ubuntu repositories then you will have minimal problems. Nothing like what you are describing.

> **cptnapalm said:**
>  Adding programs should NEVER destroy an OS upgrade.   Never."Adding programs *from the ubuntu repositories* should NEVER destroy an OS upgrade.   Never."

We can't be held responsible because you don't maintain your system properly and install things badly.

---

### Post by FyreBrand on 2007-05-02
> **cptnapalm said:**
> So installing Listen, Compiz and XGL is a massive change which will completely destroy an upgrade?  That is ALL that was done and the system was completely borked.  No X.  No command line login.

Did you miss the little X problem from last year?

Did you miss all the reports of problems upgrading from Dapper to Edgy?

Adding programs should NEVER destroy an OS upgrade.   Never.Sarcasm is mostly lost in writing and generally does little to credibility.

I've yet to have APT break my OS.  I have had apt and aptitude break my OS when I've made an alteration that I didn't understand, or when I've upgraded and didn't answer the upgrade question properly.  In the first instance I've installed third party binaries and didn't realize what was happening, at the time, to Linux itself.  In the second instance I've had to reconfigure some of my Apache and MySQL config files that I overwrote upon upgrade.

Either way what I hear PriceChild saying is that if you modify your system take special care to see what you've done.  This is true in any OS or Linux distribution and not just K/Ubuntu.  Install something in Windows and it writes to the registry and maybe in ways you don't like or understand.  Install something in Ubuntu and it changes links and default bin paths, possibly in ways you might not realize.  There is no way a developer or programmer can anticipate every single way this is done on over two million installations.

If you, or anyone highly customizes their system and then wants to upgrade the OS every six months, they need to learn how to install and remove programs properly.  Sometimes a clean reinstall is the best practice.

---

### Post by insane_alien on 2007-05-02
hmm. the only time apt hosed an install for me was when i had lots of kernel tweaks and stuff going on.

---

### Post by aretei on 2007-05-02
Well, for users who would be using ubuntu distributed by Dell, they will not have to alter config since Dell will sell their computers with close-to-perfect functionality. If users swapped parts in their computer, they must be aware that they are taking the risk. So all Dell has to do to ensure quality is to simply test and find out if the upgrading works on the hardware config for the models they offer ubuntu. To say the least, all the burden and responsibilities will be on Canonical and not on ubuntu developers in case of any problems, and if Canonical sees lots of troubles coming from Dell users, they will take an action in raising the quality standards.

---

### Post by aysiu on 2007-05-02
I think you have to be realistic about this and not blow the problem out of proportion. It is a problem, but it's not a disaster.

Upgrades won't be necessary until five months after Dell starts selling these Ubuntu computers.

The first customers will undoubtedbly be current Ubuntu users who know enough about potential *dist-upgrade* problems to deal with them.
The second group of customers will be friends and family members of Ubuntu users who, whenever doing *anything* to their new computers, will consult the tech-savvy friend or relative.
The third set of groups will probably be businesses and schools, both of which should have system administrators who know what they're doing. End users at businesses and schools shouldn't be upgrading the operating system or any of the software installed.

By the time the fourth group comes along--people who have virtually no Linux experience and who don't know someone who does--and buys Dell Ubuntu computers, there will be enough developer interest in Ubuntu that GUI-friendly tools will help people with upgrade issues ("Install this from the repositories and have an easy, two-click way to back up your files and installed programs for a reinstall"). At the same time, Ubuntu will probably be making more money off support for businesses and schools and will have more money to hire more developers, ensuring a better product.

---

### Post by Adamant1988 on 2007-05-02
Perhaps an upgrade-tool should be proposed to determine the likely-hood of something borking your system?  I know that at this point Windows has decided that an 'upgrade tool' that gives you a worst case scenario of your upgrade (or realistic scenario, your pick), perhaps Ubuntu should get one too.

---

### Post by igknighted on 2007-05-02
FWIW, Cannonical is supporting the SMART package manager, so I expect that in the not too distant future we will have that as opposed to apt anyways:

[http://labix.org/smart](http://labix.org/smart)

> Credits:

    *      Conectiva Inc. - Funded the creation of Smart, and its development up to August of 2005.
    *      Canonical Ltd. - Is funding Smart development since September of 2005.
    ...

---

### Post by PatrickMay16 on 2007-05-02
In my experience, upgrades went very well. I first installed Ubuntu in September 2005, with version 5.04. I have not reinstalled it since then; I've been doing the upgrade process each time. When I upgraded from 5.04 to 5.10, there were barely any problems. When I upgraded from 5.10 to 6.06, there were problems which were caused by me using an unsupported repository for a while. I managed to fix those without much hassle.

---

### Post by JerseyShoreComputer on 2007-05-02
I second what Patrick said. My first distro of Ubuntu was Dapper, which was upgraded to Edgy, and now to Fiesty - all with no problems at all. Everything worked the way it had previously. We all have different configurations of equipment, and some people "tweak" it while others don't. I think that by having the software properly installed on the new Dell models with the proper drivers ect.. that upgrades should go well, unless the individual user decides to make drastic changes. I think the most important hurdles that will be faced is proper drivers, for video, wireless, and bluetooth. If Dell can have all that working 100% out of the box, which I think they can, it will be a great boost for Ubuntu, Dell, and Linux in general.

---

### Post by dca on 2007-05-02
Well guys (and girls) there really is no solution.  Linux by design is set up for you to break the hell out of it (not recommended but source code is available) if you please...  All MS software is so closed source it's not even funny, look at Paul Allen's yacht.  Thus, preventing you from actually fixing problems (or causing them I guess) in an MS product.  It's inconsequential, though, really, the only people who will end up purchasing those products (Dell PCs w/ Linux) are those vehemently against MS.  Until there is a serious price point or some great marketing ploy that's showed during the next Superbowl I'm not seeing it.
 
I think APT is pretty darn good for what it is.  I'm not going to plead ignorant, there is a steep learning curve from migrating from Windows to a Linux-based distro but that's just stating the obvious.

---

### Post by prizrak on 2007-05-02
> **H.E. Pennypacker said:**
> I can understand where developers are coming from, but one must also understand the other side.  Users like myself have to do some serious tweaking in order to get certain things working.  That means the configuration files are altered.  

This should not throw developers off, though.  There are so many Broadcom wireless card users, it is fair to assume these people will be changing certain configuration files.  Now, don't get me wrong.  I'd rather not alter anything, but this is how it works.

Developers could take into account the number of people like me, and prepare for the configurations that we change.  The same goes for others (e.g. Nvidia people, but I don't know much about Nvidia to say much).

My problem is not APT so much.  I have a bigger problem with upgrades erasing or changing all the hard work that I've put into an installation.  A backup is a great way of dealing with this, but you can't possibly know everything an upgrade is going to change (I've backed up everything the upgrade tool told me it was going to replace, but this did not help).  Backing up everything is not an option either.  

My opinion: make upgrades more smooth.

Why would you need to tweak anything on a preinstalled system to get it working? 

Couple of counter points:
1) Dell is selling to business customers not your grandmother. Business customers for one have IT departments that test their own systems to make sure everything works for two are likely to use LTS releases only making upgrades few and far between. Business customers are also highly unlikely to require new versions of packages as long as what is necessary works. Not to mention that if the IT people have any kind of sense they will not give their users sudo abilities making upgrades pretty much non-issue.

2) One of the major reasons for breaking in Linux is hardware. Either you had to recompile your kernel to work with something or tweak the hell out of something else to make your hardware work. On a preinstalled system that is a non-issue things WILL work 100% and all the drivers and kernels will be available. Moreover all preinstalled systems have known configurations and can be tested for (same as Mac in this case). Dell can also step in with testing. 

3) If Dell has any kind of technical ability they will set up their systems for easy recovery. Meaning that the home directory will be a separate partition and the recovery CD will not attempt to delete it. 

4) If we talk about eventual home user adoption, they are unlikely to ever bother going outside of the repos to get software. I know a huge number of people who will be as content with AmaroK/Rhythmbox as they would be with iTunes/Winamp/WMP/anything else.

---

### Post by aysiu on 2007-05-02
5) If Dell and Ubuntu are announcing this together, you can bet your good eye that Ubuntu will do extensive testing on those three or four Dell Ubuntu systems.

They can't test *every single hardware configuration out there*. But they can test the handful of systems that come preloaded with Ubuntu.

---

### Post by karellen on 2007-05-02
for me apt is the best package manager that I've ever used. I've upgraded from edgy to feisty without problems

---

### Post by deanlinkous on 2007-05-02
> **cptnapalm said:**
>  The one thing which I do have a concern about, though, is upgrading Ubuntu releases.

 IMO normal computer users do not upgrade their OS themselves, they either pay someone or go buy a new system....

---

### Post by Anthem on 2007-05-02
> **PriceChild said:**
> Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.
Not true.  Just one example:  Every laptop user that upgraded from Edgy to Feisty lost their sound in the process.  I use a plain-vanilla install, with an all-intel laptop.  And I lost sound when I upgraded.

This isn't rare.

---

### Post by cptnapalm on 2007-05-02
> **deanlinkous said:**
> IMO normal computer users do not upgrade their OS themselves, they either pay someone or go buy a new system....

That is true only because of the infrequency of Microsoft upgrades and people having to go to a store to buy it.  Ubuntu pops up an invitation to download and install the new version.  This is drastically different.

---

### Post by prizrak on 2007-05-02
> **cptnapalm said:**
> That is true only because of the infrequency of Microsoft upgrades and people having to go to a store to buy it.  Ubuntu pops up an invitation to download and install the new version.  This is drastically different.

I'll have to agree with you here when the upgrade is that easy even "normal" users will be doing it.

---

### Post by deanlinkous on 2007-05-02
> **cptnapalm said:**
> That is true only because of the infrequency of Microsoft upgrades and people having to go to a store to buy it.  Ubuntu pops up an invitation to download and install the new version.  This is drastically different.

And will drastically send granny into a heart attack and broken hip when it breaks her system. The Ubuntu will have a reputation of being more *broke* than vista.

Of course Kevin Carmony the President and CEO thinks that dell wont sell many Ubuntu systems and that Linspire will rule the market later. Sounds like he has Dell exactly where he wants them.
Interesting Linspire Letter
[http://www.linspire.com/linspire_letter.php](http://www.linspire.com/linspire_letter.php)
and here is a quote from 
[http://forum.freespire.org/showpost.php?p=56504&postcount=18](http://forum.freespire.org/showpost.php?p=56504&postcount=18)
When told by a user that it was too bad Linspire didn't have the right product Mr Carmony replied
> It will only be "too bad," if Dell goes on to sell hundreds of thousands of these. They won't.

---

### Post by aysiu on 2007-05-02
[quote=Kevin Carmony]The current enthusiast market is just too small, and many prefer to build their own PC from white box baselines. [/quote] That may be true of desktops, but not as much for laptops. A lot of enthusiasts would be more than happy to buy a prebuilt laptop.

By the way, is it any surprise that Carmony would spin it this way? What Linspire CEO is going to say "Yeah, they obviously chose the better distribution. I guess Linspire should just pack up its bags"?

---

### Post by deanlinkous on 2007-05-02
No I would expect a CEO to say how pleased he was that Linux is finally getting noticed and congrats to ubuntu and he hoped that his product gains attention too. Instead he does the magic spin to make it sound like he told dell exactly what to do. :)

Basically he says that the state of Linux sucks so I am confused what his company offers? A distro with a last release of about two years ago. :) Debian releases more often than Linspire!

And some want CNR from this guy? Scary....

---

### Post by Brunellus on 2007-05-02
> **PriceChild said:**
> Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.
+ 1

If you, as a user, feel hot enough to use non-standard versions, non-official repositories, and drivers not packaged by the distro, you should not expect distribution developers to come to your aid when your system breaks.  If you walk on the cutting edge, you WILL bleed.

---

### Post by stchman on 2007-05-02
I am going to imagine that the Ubuntu that will be pre-loaded on a Dell will be a little different than the one you download.  I am going to imagine that 7.04 will become LTS and will be supported until about 2012.  It would be smart for Dell and Canonical to do this.

The Dell release probably tell you to upgrade to the lastest distro.

I myself am happy with 6.10.  I know that it will only be supported for another 18 months, but that is fine with me.  In another year I may upgrade.

---

### Post by agurk on 2007-05-02
I think cptnapalm's prayers have a chance of being answered to a larger extent than in the previous release cycle. From the latest weekly [newsletter](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue38):
> Tollef Fog Heen has announced that the next release, Gutsy Gibbon, is ready for development. The main purpose of Gutsy is improvement and quality. There will not be much in terms of new or experimental features but stabilising and polishing the existing features.
Sounds promising and sensible to me.

---

### Post by jdong on 2007-05-02
> **Anthem said:**
> Not true.  Just one example:  Every laptop user that upgraded from Edgy to Feisty lost their sound in the process.  I use a plain-vanilla install, with an all-intel laptop.  And I lost sound when I upgraded.

This isn't rare.

That is a completely rash overgeneralization. The proportion of laptop users who lost sound is very minor compared to those who have sound working.

---

### Post by aysiu on 2007-05-02
I'm a laptop user and didn't lose sound from Edgy to Feisty.

---

### Post by Nonno Bassotto on 2007-05-02
> **Anthem said:**
> Every laptop user that upgraded from Edgy to Feisty lost their sound in the process.

I am a laptop user.
I upgraded from Edgy to Fiesty.
I didn't lose my sound in the process.

---

### Post by agurk on 2007-05-02
I lost it on two laptops (Intel) as well as on my workstation (SoundBlaster 2), so I'm cancelling you out. ;)

---

### Post by aysiu on 2007-05-02
> **agurk said:**
> I lost it on two laptops (Intel) as well as on my workstation (SoundBlaster 2), so I'm cancelling you out. ;)
You can't cancel anything out.

The original statement didn't say "for every user who didn't lose sound, there was another user who did."

This is the original statement: > Every laptop user that upgraded from Edgy to Feisty lost their sound in the process. Every means all without exception. Two exceptions mean that statement is wrong.

---

### Post by agurk on 2007-05-02
It was just a little joke. Written communication is difficult.

---

### Post by macogw on 2007-05-02
> **cptnapalm said:**
> 
 A second computer was upgraded from 6.06 to 7.04 and was completely hosed; not only did X not start, there was no console login available either.
That's because you CANNOT skip a release.  You skipped 6.10.  That's not allowed.

> 
As Dell is to offer Ubuntu Linux pre-installed, I think that the best bet is for Canonical to focus on ways of ensuring that the upgrade process becomes rock solid.  There should be one way to do the distribution upgrade which absolutely works instead of the several ways there are now which frequently do not.  A solution which does not necessitate upgrading to each of the intervening releases.
The "one way which will always work" is the 
gksu "update-manager -c"
method.  DO NOT edit your /etc/apt/sources.list and then dist-upgrade.  It does not check for errors and fix things.  It is BAD.  Last I looked for Feisty that was -d, but that might have been because it was a "d"evelopment version at the time.

---

### Post by IgnorantGuru on 2007-05-02
I agree with the OP...  Ubuntu should focus on getting updates rock-solid.  Contrary to what some here have said, many DID have system failures with updates, and often the cause was a mistake (a package was not updated that should have been, for example).  Often the fixes are relatively simple if you read the forums - but if the fixes are that simple then they should be incorporated into the update before it is released.  This is especially true of critical areas like video drivers (if the video goes, most users are sunk right there).

I think automated system partition backups and restoration would also provide a nice comfort zone for novices - ROLL IT BACK.  I do this manually before an update and it doesn't take long.

Apt is great - one of my favorite aspects of Ubuntu after coming from SUSE (which was hell to maintain and install software on compared to Ubuntu).  But if you're talking mainstream, it needs some attention, particularly in the area of explaining why packages are being updated (what the changes are so users can make informed choices), and warnings about the possible consequences.  For example, "Warning: you have a proprietary driver installed and if you update the kernel without an updated driver, the earth WILL implode."

Beyond this, I think Windows users will LOVE the ease of installing (and removing!) software with Apt - choose it from a list and press "DO IT".  Compared to Windows and other linux dists, it's a breeze, and dependencies are handled amazingly well.

---

### Post by STREETURCHINE on 2007-05-02
> **PriceChild said:**
> Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.

if this is correct i would like to know what is stuffing up my upgrade ?
i have edgy running on one partition and it is setup fine and works well,on anouther partition i have a clean install of edgy no tweaks no fiddling just straight of the disk on to the computer,
i have now tried three times to upgrade that instalation with 3 failures.
so if apt isnt breaking the upgrade what is.?
the upgrade from dapper to edgy worked well(3 tries 3 succesfull upgrades)
i am now just waiting for my feisty disks to come

---

### Post by aysiu on 2007-05-02
> **IgnorantGuru said:**
> Contrary to what some here have said, many DID have system failures with updates Who said that?

---

### Post by jdong on 2007-05-02
For everyone who has a failed upgrade, posting upgrade logs from Update Manager to a Launchpad bug would be an excellent start.

It does developers no good when someone just says "my upgrade broke", or "my sound stopped working".

Developers do their best to test on all their configurations everything they can think of testing, but of course they are only human and with finite resources available. Contributing at least a detailed picture of what went wrong so that developers have the tools to fix it would be an excellent start.

I will not doubt that of our 15,000+ packages, at least SOME of them will have faulty postinst or postrm script, or even incorrectly written dependencies such that they will interfere with an update. The trouble is finding them -- that's some place where users have to help out.


FWIW midway through every release cycle, I will make an image of all my system configurations (from minimally to heavily customized) and attempt an upgrade with that configuration in a virtual machine or external junk hard drive setting, to try to identify and report any potential upgrade faults.

---

### Post by IgnorantGuru on 2007-05-02
> **aysiu said:**
> Who said that?

I did.  :)

Pricechild:
If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.

lapsey:
Yeah. Upgrading will work perfectly providing you havent installed foreign stuff or tweaked it or done whatever nonstandard thing with your system.


I would describe those as overstatements.  Don't get me wrong - the devs do an excellent job in the time frame they have.  But there are problems introduced even in generic installations, as well as common installations (such as merely having a proprietary video driver from the repos installed, which is not exactly exotic).  I think it is an area that can use an overhaul.

For example, after a recent kernel update a lot of nvidia users were booted to text-only.  The fix was as simple as:
```
apt-get install linux-restricted-modules-2.6.17-11-386
```

Despite this being a proprietary driver, the error was in the simple fact that the update forgot to update that package (even though it updated the proprietary nvidia driver itself, it didn't update the corresponding kernel module for that driver).

Errors occur, of course.  But it is an area that begs for more testing and stability.

---

### Post by Daveski on 2007-05-02
> **IgnorantGuru said:**
> 
Errors occur, of course.  But it is an area that begs for more testing and stability.

I expect that the crop of Dell machines which have been sold with the Ubuntu option will probably get more testing by the Dev's, and so one could argue that the Dell's might be the most reliable with version upgrades.

---

### Post by IgnorantGuru on 2007-05-02
> **macogw said:**
> That's because you CANNOT skip a release.  You skipped 6.10.  That's not allowed.

Yet that's a good example.  If it's not allowed, Apt should not allow it.  Or it should at least give the user a stark warning.

---

### Post by IgnorantGuru on 2007-05-02
> **Daveski said:**
> I expect that the crop of Dell machines which have been sold with the Ubuntu option will probably get more testing by the Dev's, and so one could argue that the Dell's might be the most reliable with version upgrades.

Yeah I think the scope of it will help.  And hopefully Dell will chip in some money or resources to the repository servers - I wonder what the nature of the deal with Ubuntu is.

---

### Post by jdong on 2007-05-02
> **IgnorantGuru said:**
> Yet that's a good example.  If it's not allowed, Apt should not allow it.  Or it should at least give the user a stark warning.

The warning is stated clearly on any upgrade documentation, which one ought to read before blindly attempting a system upgrade. The operating system cannot ask "are you sure" "don't do this" for every single possible thing a user might do wrong.... there's a certain 20GB OS out there that does that right now, and is getting heavily criticized for it ;-)

---

### Post by Mateo on 2007-05-02
They need to make it so that apt remove also removes the home directory configuration stuff.  I have a lot of .something directories that I don't know what they are.  I don't know if I have the software installed or not.  So it adds up to wasted space.

---

### Post by jdong on 2007-05-02
> **Mateo said:**
> They need to make it so that apt remove also removes the home directory configuration stuff.  I have a lot of .something directories that I don't know what they are.  I don't know if I have the software installed or not.  So it adds up to wasted space.

APT cannot decide whether or not you want to be purging per-user information, nor does it know how to purge per-user information for packages.

What an application decides to write to the system after it is installed is out of the scope of the package manager, and it is not realistic to expect it to be able to clean it up, or to assume users would want APT purging what it thinks are configuration directories.

The little bits of space wasted by text configuration files are probably very insignificant, while if there were any files of significant size, they probably are of some value to the user.

---

### Post by dspari1 on 2007-05-02
> **PriceChild said:**
> Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.

This is very untrue(you can't blame the users 99.999% of the time) because when I installed 6.10 to 7.10 after a clean install, I downloaded the files fine, but halfway through the install, some of the files downloaded were corrupt. The installer should do an error check on the files' integrity in a similar way that BitTorrent does to make sure that the computer does not attempt to install corrupted data.

---

### Post by IgnorantGuru on 2007-05-02
> **jdong said:**
> The warning is stated clearly on any upgrade documentation, which one ought to read before blindly attempting a system upgrade. The operating system cannot ask "are you sure" "don't do this" for every single possible thing a user might do wrong.... there's a certain 20GB OS out there that does that right now, and is getting heavily criticized for it ;-)

I agree to a point, but most casual users don't read documentation.  And I don't think an upgrade is a minor thing - there I would say "are you sure" is a good thing, especially as adept asks the user "do you want to upgrade?" after doing a routine update. In fact the little warning could be put in that same dialog - a little description of or link to what an upgrade is and the possible issues (especially if you're hopping over a version). 

If we're talking novices (people who don't do system installations and heavy maintenance), caution is advised, especially where it may kill the system.  Also, if people stop using updates because they've come to fear breaking their system, they will not get security updates, which becomes a problem.  The various levels of update, security update, kernel update, and upgrade need to be better separated and explained - in the window that is doing them.

---

### Post by Mateo on 2007-05-02
> **jdong said:**
> APT cannot decide whether or not you want to be purging per-user information, nor does it know how to purge per-user information for packages.

I know it can't do it now, that's why I said they should make it so it **can** do it.

> The little bits of space wasted by text configuration files are probably very insignificant, while if there were any files of significant size, they probably are of some value to the user.

Insignificant to you.  To me any wasted space is significant.  I paid for the hard drive, I should only have stuff on it that I want on it.  And I don't want configuration files for software I don't have installed on my computer.

---

### Post by jimrz on 2007-05-02
> **dca said:**
> Howza' bout I senz you a copy 'o Windows ME???

don't forget to put the "haz-mat" stickers on the package

---

### Post by kitterma on 2007-05-02
> **Anthem said:**
> Not true.  Just one example:  Every laptop user that upgraded from Edgy to Feisty lost their sound in the process.  I use a plain-vanilla install, with an all-intel laptop.  And I lost sound when I upgraded.

This isn't rare.

Oh nonsense.  Every user that upgraded a laptop did NOT lose sound.  I certainly didn't.  For me sound was broken in Edgy and fixed in Feisty.  

Guess what, I installed early flight releases of Feisty (on a spare HD), reported bugs when they could be fixed, and guess what, they got fixed.

The developers only have so many different hardware suites to test with and so many people to do testing.  They need help.  It's to late to complain now.  Where were you when it mattered?

---

### Post by kitterma on 2007-05-03
> **Mateo said:**
> I know it can't do it now, that's why I said they should make it so it **can** do it.



Insignificant to you.  To me any wasted space is significant.  I paid for the hard drive, I should only have stuff on it that I want on it.  And I don't want configuration files for software I don't have installed on my computer.

Then learn sudo dpkg -P packagename and don't worry.

---

### Post by Mateo on 2007-05-03
> **kitterma said:**
> Then learn sudo dpkg -P packagename and don't worry.

this removes the configuration files?  also, doesn't this depend on you having the deb in your computer?

---

### Post by kvonb on 2007-05-03
> **PriceChild said:**
> Apt doesn't break break distribution upgrades, users do.

There is a LOT of testing that goes into the upgrade paths, even with the universe repository enabled. The problem comes when users change their configurations in ways the developers can't expect/plan for. If you _ONLY_ used software from the main/restricted/universe/multiverse repositories and didn't make changes that you didn't understand to your system's configuration then distribution upgrades would (99.999% of the time) still work.

This is exactly the attitude that will keep Linux back, and has done successfully for decades!

One way around this is to check the entire system for modifications before performing an update/upgrade, then warn the user about potential problems.  Apt does this already to a small extent, it warns about modified config files.

If it can't be done, then there needs to be a bloody obvious warning displayed when the user tries to install an evil third party application, or do something seriously system altering like say changing the desktop wallpaper!

This was the argument back in 1998, they said that it was impossible to implement a unified package manager because of all the different libraries and changed config files.  But guess what, Debian came along and sorted that mess out!

You CANNOT say to a user that anything you change will "invalidate the warranty" so to speak, this is reminiscent of another O/S's philosophy.

It can be done, and it will be done........eventually :).

---

### Post by dspari1 on 2007-05-03
> **kvonb said:**
> This is exactly the attitude that will keep Linux back, and has done successfully for decades!

One way around this is to check the entire system for modifications before performing an update/upgrade, then warn the user about potential problems.  Apt does this already to a small extent, it warns about modified config files.

If it can't be done, then there needs to be a bloody obvious warning displayed when the user tries to install an evil third party application, or do something seriously system altering like say changing the desktop wallpaper!

This was the argument back in 1998, they said that it was impossible to implement a unified package manager because of all the different libraries and changed config files.  But guess what, Debian came along and sorted that mess out!

You CANNOT say to a user that anything you change will "invalidate the warranty" so to speak, this is reminiscent of another O/S's philosophy.

It can be done, and it will be done........eventually :).


Exactly, blaming users is not the way to sell a product. It should be up to the devs to put in safeguards that will prevent users from messing up config files.

---

### Post by kitterma on 2007-05-03
> **Mateo said:**
> this removes the configuration files?  also, doesn't this depend on you having the deb in your computer?

dpgk needs the .deb on your computer to install, but not to remove.  To remove it's the package name, not the file name of the .deb.

the -P option (P, not p) purges all config files.

---

### Post by kitterma on 2007-05-03
> **dspari1 said:**
> Exactly, blaming users is not the way to sell a product. It should be up to the devs to put in safeguards that will prevent users from messing up config files.

Who's selling a product?

In an ideal world you are correct.  Go edit your registry and then see how much help you get from Microsoft.

The bottom line is that modern software systems are far to complex to test all possible configurations and computational paths.  If you stick with tried and true, well tested configurations you are more likely to get good reliable performance.  This is just the way things work and it doesn't matter if it's proprietary or open source.

It's a little harder in an open source environment like Ubuntu, because most of the developers are volunteers.  You can't force volunteers to do stuff they don't want to.

---

### Post by nalmeth on 2007-05-03
Exactly how can Canonical and the devs possibly be responsible for everything YOU may do to YOUR OWN SYSTEM??

:confused:

I fully appreciate and enjoy simply the fact that we have such a fast release cycle. 
I think it is irresponsible almost to the point of disrespect to suggest someone else be responsible for your own actions.

I've never had any major problems upgrading (done it from breezy to dapper, twice), but considering the amount of crap I do to my system, I think it is only COMMON SENSE to at least backup my data regularly, and reinstall fresh when there is a new release.

I can't believe this thread.

I think the people who use Linux, give nothing back, and then complain are the ones "holding it back".

Good night everyone :sigh:

---

### Post by jdong on 2007-05-03
There are some valid points being raised in this thread -- APT should not bork out because one package's configuration script did not succeed. This is something that can be -- and some developers are saying they plan to -- work on.

This will add some level of robustness to the system not there before, but still there may be unknown interactions caused by unofficial packages.

---

### Post by dspari1 on 2007-05-03
> **kitterma said:**
> Who's selling a product?

In an ideal world you are correct.  Go edit your registry and then see how much help you get from Microsoft.

The bottom line is that modern software systems are far to complex to test all possible configurations and computational paths.  If you stick with tried and true, well tested configurations you are more likely to get good reliable performance.  This is just the way things work and it doesn't matter if it's proprietary or open source.

It's a little harder in an open source environment like Ubuntu, because most of the developers are volunteers.  You can't force volunteers to do stuff they don't want to.


1. Dell is selling a product. That's who.
2. I'm sure Canonical is not providing everything to Dell for Free.
3. In a Microsoft product, I don't have to edit my registry to get my hardware working.
4. I had an install that broke my system because half way through the install, the system reported corrupted files(the files that were downloaded). This could have been prevented if the install did an error check on these files before starting the install.
5. You are no longer a volunteer when you are making income; you are a business.
6. These devs will be forced to do stuff they don't want to if they want to continue to operate as a business.

---

### Post by Daishiman on 2007-05-03
Assuming regular users will not install stuff from third party repositories is not a reasonable position to take.

Just take a look at bleeding edge projects like Beryl or any new media editing apps where new versions are out much faster than repository updates. Users will eventually end up looking at those projects and downloading whatever shiny .deb beta package is available. The user should then expect to take care of that on his own, however, he should NOT have to expect system breakage because of it!

A proposed solution that I have for that is for the dist-upgrade script to do the following:
-Check the entire apt database to make sure that all files that should exist, do.
-Check for any packages that are not from the mainline Ubuntu repos,
-Warn the user about those and recommend their removal

Despite the massive awesomeness of APT there's still a few things that it's missing. For example, the AIX package manager supports rolling back packages to their previous version. That is, you install a package and you can use it, but if you don't like it or it conflicts, you can roll it back until you commit the current version. I know it's wishful thinking, but if APT could implement functionality like that (rolling back to a previous dist version) that would be the ultimate in system upgrading capacity.

The other thing that could be done for an upgrade would be, for the installation scripts of highly critical patches, to have the user test functionality before proceeding. For example, when the X11 package is upgraded, tell the user that the X server will be restarted, and if it doesn't start again, roll back (there could be a CLI prompt asking if the user sees a screen after n seconds).

A lot of great ideas can be implemented as far as that goes. That would be another major hurdle to overcome, and one that once passed would put Linux in its own, unmatched league of OS upgrade ease.

---

### Post by dspari1 on 2007-05-03
> **nalmeth said:**
> Exactly how can Canonical and the devs possibly be responsible for everything YOU may do to YOUR OWN SYSTEM??

:confused:

I fully appreciate and enjoy simply the fact that we have such a fast release cycle. 
I think it is irresponsible almost to the point of disrespect to suggest someone else be responsible for your own actions.

I've never had any major problems upgrading (done it from breezy to dapper, twice), but considering the amount of crap I do to my system, I think it is only COMMON SENSE to at least backup my data regularly, and reinstall fresh when there is a new release.

I can't believe this thread.

I think the people who use Linux, give nothing back, and then complain are the ones "holding it back".

Good night everyone :sigh:

If Canonical can't handle criticism, how do you expect them to make their product better? Ubuntu is by far the best distro IMO, but you can't let fanaticism over the OS fog your judgment on what needs to be done to improve.

A nice warning saying "This debian package will modify x config file; your system may become at risk if you proceed" would do wonders. Blaming the customers is not the way to succeed in business.

---

### Post by nalmeth on 2007-05-03
I'm sorry, ignore my grumpiness. 

I often have problems with Ubuntu that frustrate me aswell, and criticism isn't a bad thing.

That was just my gut reaction to _some_ of the comments made. 

> Ubuntu is by far the best distro IMO, but you can't let fanaticism over the OS fog your judgment on what needs to be done to improve.
Fanaticism isn't for me

Now I must sleep,
Seriously, Goodnight everyone :)

---

### Post by dspari1 on 2007-05-03
> **nalmeth said:**
> I'm sorry, ignore my grumpiness. 

I often have problems with Ubuntu that frustrate me aswell, and criticism isn't a bad thing.

That was just my gut reaction to _some_ of the comments made. 


Fanaticism isn't for me

Now I must sleep,
Seriously, Goodnight everyone :)

Night, please don't take what I said personal. I only want the OS to succeed as much as everyone else. I hope I wasn't overly critical.

---

### Post by STREETURCHINE on 2007-05-03
if dell wish to put ubuntu on there computers i hope they have improved,
i bought a dell demension e520 about 6 months ago and i cant get dapper to load on it it wont even load the live disks i got from shipit,
all i get on my dell with dapper is failed to start xserver

edgy runs fine ,yet to try feisty,but absolutly no luck with dapper

---

### Post by Brunellus on 2007-05-03
> **Daishiman said:**
> Assuming regular users will not install stuff from third party repositories is not a reasonable position to take.

Just take a look at bleeding edge projects like Beryl or any new media editing apps where new versions are out much faster than repository updates. Users will eventually end up looking at those projects and downloading whatever shiny .deb beta package is available. The user should then expect to take care of that on his own, however, he should NOT have to expect system breakage because of it!

A proposed solution that I have for that is for the dist-upgrade script to do the following:
-Check the entire apt database to make sure that all files that should exist, do.
-Check for any packages that are not from the mainline Ubuntu repos,
-Warn the user about those and recommend their removal

Despite the massive awesomeness of APT there's still a few things that it's missing. For example, the AIX package manager supports rolling back packages to their previous version. That is, you install a package and you can use it, but if you don't like it or it conflicts, you can roll it back until you commit the current version. I know it's wishful thinking, but if APT could implement functionality like that (rolling back to a previous dist version) that would be the ultimate in system upgrading capacity.

The other thing that could be done for an upgrade would be, for the installation scripts of highly critical patches, to have the user test functionality before proceeding. For example, when the X11 package is upgraded, tell the user that the X server will be restarted, and if it doesn't start again, roll back (there could be a CLI prompt asking if the user sees a screen after n seconds).

A lot of great ideas can be implemented as far as that goes. That would be another major hurdle to overcome, and one that once passed would put Linux in its own, unmatched league of OS upgrade ease.
sorry, no.  It is a *pefectly* reasonable position to take.  Please tell me why an end user *needs* beryl/compiz.  I don't care why he might *want* it, but why he *needs* it.  Desktop chrome is not a core OS function.  Indeed, the linux desktop chrome that exists is under heavy development.  It has broken in the past.  It will break in the future.  Why go through all the headache?

You beta fever sufferers are all the same.  You fall all over yourselves to get whatever seems shiny at the moment, willfully ignoring every warning that $SHINY_PACKAGE is not yet ready/stable/secure.  Then, when $SHINY_PACKAGE breaks, you expect other people to save you from your own foolishness.

OS distributors cannot reasonably be expected to forsee every possible breakage that might occur when an end-user decides to experiment with his system.  Ubuntu has taken a realistic path, defining at least three levels of support:

* MAIN: Core distribution components, actively maintained by the dev team.  If these break, you should pitch a fit.

* UNIVERSE:  Additional components, maintained/packaged by community volunteers.  Most beta-fever-sufferers complain about the staleness fo the Universe, but at least Universe packages are *known to work* on stock Ubuntu installs.

* MULTIVERSE & EVERYWHERE ELSE:  You're on your own, kid.

If you are not mature or responsible enough to know what you're putting on your computer and why, maybe you shouldn't have root access.

---

### Post by deanlinkous on 2007-05-03
> **Brunellus said:**
> 
If you are not mature or responsible enough to know what you're putting on your computer and why, maybe you shouldn't have root access.
most *normal* users aren't - that is why windows is such a mess- will ubuntu fair any better if a *normal* user gets ahold of it - nope!

---

### Post by PriceChild on 2007-05-03
> **IgnorantGuru said:**
> 

For example, after a recent kernel update a lot of nvidia users were booted to text-only.  The fix was as simple as:
```
apt-get install linux-restricted-modules-2.6.17-11-386
```Despite this being a proprietary driver, the error was in the simple fact that the update forgot to update that package (even though it updated the proprietary nvidia driver itself, it didn't update the corresponding kernel module for that driver).I really can't be bothered to argue against your earlier bits. However this is so incorrect its unreal. There is NO reason that you should have to install the -386 kernel. The -generic kernel works absolutely perfectly with the nvidia-glx* packages. If you think otherwise then sort out your dependencies manually as you've put apt into a strange position.

> **dspari1 said:**
> This is very untrue(you can't blame the users 99.999% of the time) because when I installed 6.10 to 7.10 after a clean install, I downloaded the files fine, but halfway through the install, some of the files downloaded were corrupt. The installer should do an error check on the files' integrity in a similar way that BitTorrent does to make sure that the computer does not attempt to install corrupted data.It does check integrity afaik by checking the GPG signature AND an MD5sum.

> **kvonb said:**
> This is exactly the attitude that will keep Linux back, and has done successfully for decades!

One way around this is to check the entire system for modifications before performing an update/upgrade, then warn the user about potential problems.  Apt does this already to a small extent, it warns about modified config files.

If it can't be done, then there needs to be a bloody obvious warning displayed when the user tries to install an evil third party application, or do something seriously system altering like say changing the desktop wallpaper!

This was the argument back in 1998, they said that it was impossible to implement a unified package manager because of all the different libraries and changed config files.  But guess what, Debian came along and sorted that mess out!

You CANNOT say to a user that anything you change will "invalidate the warranty" so to speak, this is reminiscent of another O/S's philosophy.

It can be done, and it will be done........eventually :).Debian package management has a system. The system most definitely works very well. However if you break that system, you can not complain to the developers. It is just ridiculously unfair. It is attitudes like this that make sure that most of the devs wouldn't want to touch the forums with a 12 foot pointy stick.

---

### Post by 23meg on 2007-05-03
> **IgnorantGuru said:**
> Yet that's a good example.  If it's not allowed, Apt should not allow it.  Or it should at least give the user a stark warning.

A good example indeed; if you're trying to upgrade using apt in the command line, you're not carrying out the officially recommended upgrade procedure in the first place, and didn't read [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading), which says:

> 
**Manual command-line upgrade (not recommended)**

Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. Using Update Manager (see above) is likely to be much less problematic.

Instructions for this method can be found on FeistyUpgradesManual. 

---

### Post by jdong on 2007-05-03
Out of curiousity, what prompts a user to apt-get dist-upgrade? Most new users would see update manager prompting about a new version, or read the upgrade documentation in the release notes, while experienced Debianites would be the ones familiar with apt-get dist-upgrade (and also experienced and skilled at fixing what goes wrong).

---

### Post by prizrak on 2007-05-03
> Debian package management has a system. The system most definitely works very well. However if you break that system, you can not complain to the developers. It is just ridiculously unfair. It is attitudes like this that make sure that most of the devs wouldn't want to touch the forums with a 12 foot pointy stick.
What about some recent breakages that were due to developers mistakes? There have been quite a few of those. 

I see nothing wrong with implementing a reliable rollback system. Developers are people and can make mistakes even if the testing was 100% sometimes a package is in the repos before something it depends on is updated and that's when you end up with breakage. 

Sure installing 3rd party stuff is likely to break your system but at the same time what's wrong with easy rollback?

---

### Post by aberry5555 on 2007-05-03
I think the main problems are the packages themselves. I know they're **meant** to work but, for anything to do with the system itself, they seemingly almost never do. For instance (and I know a large proportion of this blame can be placed on the manufacturer) the ATI FGLRX installer package is broken, and has been as such for a long time. ANYONE trying to install them HAS TO change configuration files and install stuff manually. I don't know the statistics of who uses which gfx cards, but that has to be at the very least 25% of the market share. 

I also know that you try to encourage open source and that the "radeon" drivers to work quite well (although they need fiddling with to get working half the time too). Surely it would be a safe bet to say that many packages need to be re-assessed and re-tested to make sure that people don't have the problem of having to go elsewhere and fiddling to make their PC work.

Another example is ndiswrapper, now I know, again, that you want everything open-source, so this is not a desirable bit of software, but surely a program could be built to re-build it every time you get a kernel upgrade. it is a NIGHTMARE having to fix the thing without internet every time I get a new kernel. And I know what the answer to that is: learn how to program and do it yourself. I'd like to, but I can't as I havnt the foggiest idea where to start, but I do know one thing, the developers seem to be getting ahead of themselves. 

As 7.04 seems to be pretty stable, installs very well and is already a fair few miles better than XP why not stop and do some "service packs" (excuse my language!). Take some polls or user feedback, find out what bugs *bug* users and fix them up, then move on to the next slightly upgraded version. We can all moan about Microsoft being outdated, dodgy etc but they did, at least, get one thing right. They didn't fix it if it wasn't broken, they fixed the (huge amount of) broken things and then moved on to upgrading.

Maybe, in order to get a hold of the market, you might have to ignore good practice; continuing to develop ubuntu itself, and start making sure it doesnt just work as an OS by itself, but also works with all the amazing stuff there is to offer from the rest of the community, and even the truly shocking stuff, so that it matches Windows in terms of "reliability". 

Realistically linux is far more reliable than windows but, at least, when someone who knows jack about computers gets at it, it will still work, horifically and with errors, but it won't destroy itself like Ubuntu can do.

p.s. Im trying not to be insulting Im just trying to give constructive criticism

---

### Post by jdong on 2007-05-03
> **prizrak said:**
> What about some recent breakages that were due to developers mistakes? There have been quite a few of those. 

I see nothing wrong with implementing a reliable rollback system. Developers are people and can make mistakes even if the testing was 100% sometimes a package is in the repos before something it depends on is updated and that's when you end up with breakage. 

Sure installing 3rd party stuff is likely to break your system but at the same time what's wrong with easy rollback?

Nothing is wrong with it -- it's a good idea, but sitting around and just tossing ideas around isn't going to do anything..

If someone can write a spec even with rough technical ideas of how a rollback system may be implemented, it can get the ball rolling!

---

### Post by dca on 2007-05-03
By the by, Ubuntu is free.  A company I consulted for shelled out bucks for a used copy/license of Windows 2000 Server...  The time it took to deploy the Windows server versus the time to deploy an Ubuntu server just for file sharing can not be meaured in minutes or hours.  I think a lot of the posts in this thread have a Windows bias.  Not pro-Windows but all the complaints, all the short-comings are from exposure.  With all the kids growing up and learning Windows in the mean time is causing issue(s) when they get to a point where they realize there are alternatives to Windows out there.  Things will break, Windows = $200 XP license, Ubuntu = $0.  I don't care if Linux is or isn't ready for the desktop.  I've used it on all my systems for years, some of the hardware I service run POSIX-compliant OSs forcing me to know my way around the command line.  Not to mention, Windows has had it's share of snafus.  The reason why nobody brings it up is because of PC architecture and configuration causing limited exposure to a severe problem.  Windows released an update that created a memory fault at the location of where the sound cards utility that loads on start-up resides forcing the user to loose sound for the session and have a big red error screen on every start-up.  Your only recourse (was to call MS, please) was to apply the name of the .dll file into a search engine and navigate to the correct fix.  Now, this didn't happen on EVERY SINGLE PC running Windows, only Intel boards w/ a particular rather popular on-board sound card.  I have tons of Windows stories like that...  Not to sound like a zealot but for what it is, Ubuntu is pretty powerful.  Heck, you could install it on a close hamper if you wanted to.

---

### Post by Wiebelhaus on 2007-05-03
> **cptnapalm said:**
> Iz uh so-a sory dat i izza so dumm.  U izza jus sooa smarrt.


that was the funniest damn thing I've seen or heard all day at work , simple yet effective.

thanks.

---

### Post by PriceChild on 2007-05-03
To roll back a package you can use synaptic or the following command:
```
sudo apt-get install *package*=*version*
```Rolling back everything back to previous distributions like edgy > dapper is not supported.

---

### Post by kitterma on 2007-05-03
> **dspari1 said:**
> 1. Dell is selling a product. That's who.
2. I'm sure Canonical is not providing everything to Dell for Free.
3. In a Microsoft product, I don't have to edit my registry to get my hardware working.
4. I had an install that broke my system because half way through the install, the system reported corrupted files(the files that were downloaded). This could have been prevented if the install did an error check on these files before starting the install.
5. You are no longer a volunteer when you are making income; you are a business.
6. These devs will be forced to do stuff they don't want to if they want to continue to operate as a business.

1.  Yes, then complain to them.
2.  I wouldn't know.  It depends on whether or not Dell wanted to buy support.  Ubuntu is free software for corporations and individuals both.
3.  OK.  It comes up that people need to and try to get support after you do.  Actually, try to get support from MS period.
4.  Yes, there are things that could improve.  No doubt.
5.  Sure, but most of the people working on Ubuntu development are not Canonical employees.  Paid devs are a minority. 
6.  Sure, the paid ones, but that's not most of us.

---

### Post by dspari1 on 2007-05-03
> **kitterma said:**
> 1.  Yes, then complain to them.
2.  I wouldn't know.  It depends on whether or not Dell wanted to buy support.  Ubuntu is free software for corporations and individuals both.
3.  OK.  It comes up that people need to and try to get support after you do.  Actually, try to get support from MS period.
4.  Yes, there are things that could improve.  No doubt.
5.  Sure, but most of the people working on Ubuntu development are not Canonical employees.  Paid devs are a minority. 
6.  Sure, the paid ones, but that's not most of us.


If Canonical is receiving money from Dell, logic says not many devs would want to continue to work for free. Why would anyone want to make some company rich off of their own hard work for free? (That does not compute in my mind.) I would imagine that the devs that are working for free would want to either get hired or move on to another distro that is not business oriented.

Dell needs to pay a lot of attention to detail. For example, people are not going to know how to load modules to get software or hardware midi synth installed and working. This needs to be enabled by default in the Dell version of Ubuntu. Dell is going to have to be providing support in a way or another if they want to sell their product.

I do agree that when a product is free that there is little to no room for complaints, but as a Dell customer, I no longer see it as free since customer support is paid, and I would expect a level of service. If you believe that Microsoft's support is negligent, then you can blame that on the monopolistic nature of the company. In order to dethrone Microsoft, you have to do things better. 

As for a final point, Apple should also be considered in all of this too because they are leading the leading Microsoft alternative; therefore, they are a threat to Canonical. Canonical's product needs to be above all the competition in order to succeed and remain in business in the long run. Accepting to be anything less than #1 is not the proper way to conduct business. A company should always strive to be the best and nothing less.

---

### Post by lindkvis on 2007-05-04
> **cptnapalm said:**
> So installing Listen, Compiz and XGL is a massive change which will completely destroy an upgrade?  That is ALL that was done and the system was completely borked.  No X.  No command line login.

Did you miss the little X problem from last year?

Did you miss all the reports of problems upgrading from Dapper to Edgy?

Adding programs should NEVER destroy an OS upgrade.   Never.

I completely agree on the X problem of last year, but Compiz and XGL are not "apps" in the same form that other operating systems deal with. Windows users do not change their window manager (apart from a tiny proportion, and they can mess Windows up as well) and Windows users certainly do not change their Display system. XGL is a fairly massive change.

I think people have to accept that once you start messing around with experimental display systems, the install becomes "unsupported" and Canonical has no obligation to test your setup. Otherwise the Q & A just becomes an unmanageable nightmare.

---

### Post by ssam on 2007-05-04
> **H.E. Pennypacker said:**
> I can understand where developers are coming from, but one must also understand the other side.  Users like myself have to do some serious tweaking in order to get certain things working.  That means the configuration files are altered.

on the dell computers users will not need to do any tweaking to make the hardware work.

even if dell have to put in somethings that are not in the default ubuntu install, they will have done this in a consistent way across all the ubuntu machines sell. this configuration can then be thoroughly tested.

also now that things like extra-codecs get installed by an automatic system when you need them. there will be less people who have used strange methods to get them.

if dell are really worried about this they could create a dell edition of ubuntu, and have a bit more control over updates. for example they could not have gutsy show in the automatic updates untill a month after its general release.

> **cptnapalm said:**
> Did you miss the little X problem from last year?

this was taken very seriously and the updates policy was changed to make it less likely to happen in the future. Also X is becoming more resilient to configuration problems, and will soon be able to fall back to basic drivers if something bad happens.

---

### Post by lindkvis on 2007-05-04
> **jdong said:**
> The warning is stated clearly on any upgrade documentation, which one ought to read before blindly attempting a system upgrade. The operating system cannot ask "are you sure" "don't do this" for every single possible thing a user might do wrong.... there's a certain 20GB OS out there that does that right now, and is getting heavily criticized for it ;-)

What a ludicrous statement. Just because you can't stop the user from doing every single possible wrong thing , doesn't mean you can't try to stop the user from doing the most obvious and destructive things wrong.

There are many, many things the system should ask "are you sure?" about. And many things the system simply shouldn't allow the user to do, unless he adds a "--force-possible-messup" switch to the application on the command line.

Some of these include deleting libc.so.6 from current generation Ubuntu releases and upgrading the OS along an upgrade-path which is KNOWN not to work.

---

### Post by prizrak on 2007-05-04
> If Canonical is receiving money from Dell, logic says not many devs would want to continue to work for free. Why would anyone want to make some company rich off of their own hard work for free? (That does not compute in my mind.) I would imagine that the devs that are working for free would want to either get hired or move on to another distro that is not business oriented.
Why don't you ask Fedora Core and OpenSuSE devs? Alot of them work for free while RedHat and Novell sell an "Enterprise" version of the software for profit. Ubuntu always had a core development team that was getting paid and a volunteer community, no one is complaining. Also if you think that Dell is the first one to pay Canonical for support (if they even are) you are sorely mistaken.
> As for a final point, Apple should also be considered in all of this too because they are leading the leading Microsoft alternative; therefore, they are a threat to Canonical. Canonical's product needs to be above all the competition in order to succeed and remain in business in the long run. Accepting to be anything less than #1 is not the proper way to conduct business. A company should always strive to be the best and nothing less.
HAHAHAHAHAHA. Apple is only a threat on the mp3 player market. For one right now Linux desktop usage is about the same as Apple usage and this is before Dell sold anything. For two Apple suffers very serious drawbacks, it has same issues as Linux as far as lack of certain software goes and it costs quite a bit more than a comparable "PC" system (15" MacBookPro is $500 more than a comparable ThinkPad). Apple is also not nearly as well established in the enterprise sector as Linux is. There are tons of Linux servers deployed in pretty much any company, not so much with Apple. To make matters worse Dubuntu machines are gonna pretty cheap and still have all the benefits of using a Mac. You also need to keep in mind that as of right now Dell is targeting it's Enterprise customers with Ubuntu systems while Apple is targeting home users.

---

### Post by prizrak on 2007-05-04
> **PriceChild said:**
> To roll back a package you can use synaptic or the following command:
```
sudo apt-get install *package*=*version*
```Rolling back everything back to previous distributions like edgy > dapper is not supported.

Way too involved for an average user. I know how to force a package version (even in GUI), it didn't come out of nowhere though. It would be beneficial to be able to roll back to previous version (of the distro). However if we are talking preinstalled, all that needs to be done is /home on a separate partition with perhaps an auto generated script that will install all the software from repos that user has installed. This would make reinstalling the OS easier than sending 2 bytes.

---

### Post by Brunellus on 2007-05-04
> **lindkvis said:**
> What a ludicrous statement. Just because you can't stop the user from doing every single possible wrong thing , doesn't mean you can't try to stop the user from doing the most obvious and destructive things wrong.

There are many, many things the system should ask "are you sure?" about. And many things the system simply shouldn't allow the user to do, unless he adds a "--force-possible-messup" switch to the application on the command line.

Some of these include deleting libc.so.6 from current generation Ubuntu releases and upgrading the OS along an upgrade-path which is KNOWN not to work.
If you wanted this--you would be running Windows.

Windows is notoriously annoying because it assumes (correctly?) that you are an idiot.  The *nix OSes assume you know what you are doing.  

If you do not know what you are doing--*stop doing it*.  It really is that simple.

---

### Post by PriceChild on 2007-05-04
> **lindkvis said:**
> What a ludicrous statement. Just because you can't stop the user from doing every single possible wrong thing , doesn't mean you can't try to stop the user from doing the most obvious and destructive things wrong.

There are many, many things the system should ask "are you sure?" about. And many things the system simply shouldn't allow the user to do, unless he adds a "--force-possible-messup" switch to the application on the command line.

Some of these include deleting libc.so.6 from current generation Ubuntu releases and upgrading the OS along an upgrade-path which is KNOWN not to work.Yes. Developers can do this... and they do do this.

However we still get people complaining that it isn't easy to recover a "rm -rf"'d file. Even though -f is what you describe above and shouldn't be used unless you are 200% sure.

Or that lots of packages got removed because they didn't look what it was asking properly when they pressed yet... "even though it told me what it was doing and I still pressed Yes it shouldn't have let me remove X without asking again."

I don't go up to a car and try to get it to run by pouring coffee into the engine. Learn how you are meant to use things and do it as the makers intended. Its not our fault if you break things off of your own back.

---

### Post by jdong on 2007-05-04
If you don't want to run the risk of breaking anything, **don't run any sudo commands on the terminal**. It's as simple as that. Otherwise, some users (like me) appreciate the power that Linux affords and the ability to heavily customize the systems in ways unimaginable with Windows.

And there can be cases where you'd want to seriously modify low-level system components that I would not like to be nagged about. Furthermore, the nagging mechanism would have to be at the kernel level to work, which is a lot of overhead, not to mention annoyance.

---

### Post by koenn on 2007-05-04
With Dell comes great responsibility ... for Dell.

I'm not buying the "we need a monkey-proof apt because Dell will sell PC's with Ubuntu on it". It's Dell's problem. Either they sell these systems "with O.S. Ubuntu Feisty Fawn" (or whatever release) and have the Terms and Conditions of the sale stipulate something along the lines of "you bought this with Feisty on it - Dell does not support any upgrades", or they worked out an arrangement with Canonical on how to handle upgrades. Neither Dell nor Canonical is going to be stupid enough to have forgotten all about that - they shouldn't be in the computer business if they are that stupid. 

As for apt. It works. Very well. It doesn't cause breakage. It checks for version numbers and dependencies, and installs packages. If things break in an upgrade, there are other causes : it's because a package maintainer made a mistake in defining dependencies for his package. Or the dependencies are correct but the system contains rogue packages that messed up the package management. 

I fully agree with those that said that using beta software, 3th party repo's, unsopported install methods etc etc etc is a recipy for disaster and that you can't expect anyone else to take resposibility for it - not the devs, not Canonical, not Dell, ...   
 "... bleeding edge ... you will bleed". Simple as that. 

Granted, a roll back / commit mechanism could be usefull.  
Also, as I think dependencies are a majot factor in breakage, some quality standards / packaging guidlines for Universe would be usefull. I've been looking around for them but haven't found any. It looks like for Universe, you grab a deb from Debian or a source package from any website, compile it on an Ubuntu system, and it's ready for Universe. If it doesn't compile - maybe tweak the controll files a bit until it compiles. It's easy to imagine how this can result in unreliable dependencies that cause trouble in (some) upgrades.
So while I have full confidence in the reliability of  Main, Universe might need some quality assurance mechanism. 

Lastly, what seems to be missing from Ubuntu overall, are upgrade paths or migration paths. Whith the fast release cycle, it's easy to skip a release. Even between consecutive releases, the "migration path" seems to be "burn a CD and run it". A more serious approach would be to give step by step instructions on how to move from one release to another, covering common mistakes and pitfalls. Along the lines of : make sure you have ubuntu-desktop installed, check that your kernel is at least version so and so, run the installer in such and such manner, make sure NOT to choose this or that option if you're upgrading ... etc. 

As for 'skip version' upgrades, they could be supported in the same way - eg the "migration path" would be upgrade to dapper following these instructions here, then upgrade to Edgy following those instrucions there, then upgrade to Feisty following that procedure over yonder. Or a procedure could be worked out to skip a release by eg. upgrading key packages to certain versions first, and so on.

Again, I haven't seen anything remotely resembling such upgrade procedures (I didn't look very hard yet, I'm sticking with Dapper for proven stability for another while). 
As an example [http://www.microsoft.com/windows/products/windowsvista/buyorupgrade/upgradepaths.mspx](http://www.microsoft.com/windows/products/windowsvista/buyorupgrade/upgradepaths.mspx) shows upgrade paths to Windows Vista from previous releases. A Chart indicates when a clean install is required or when an in-place uopgrade can be performed. There are some hints at how to save settings and preferences. Although this is still rather rudimentary, and upgrade paths for Microsoft are often linked to licenses as well, not merely technical issues, it gives an idea of what at. 

These are more detailed examples (which versions of XP can upgrade to what versions of Vista) and step by step instructions :
[http://www.extremetech.com/article2/0,1697,2082982,00.asp](http://www.extremetech.com/article2/0,1697,2082982,00.asp)
[http://www.extremetech.com/article2/0,1697,2082984,00.asp](http://www.extremetech.com/article2/0,1697,2082984,00.asp)

---

### Post by chashock on 2007-05-06
> **PriceChild said:**
> 

We can't be held responsible because you don't maintain your system properly and install things badly.

This is the fundamental attitude problem that if the community does not overcome, no Linux distribution will ever go mainstream and become a driving force in displacing the Microsoft dominance we all seem to have a problem with.

The issue to me has not been one of maintaining things properly.  It has been that in ORDER to maintain my system properly, I have to do what are apparently non-standard things.  To get my ATI video card, MS laser 6000 mouse, dual ViewSonic flat panels, dual DVD writers, wireless keyboard, etc., etc., I have to tweak, twist, torment, and in many other ways modify several files, any one of which can get horked in a system upgrade or even a simple package upgrade.

In a Windows environment, I have an easy mechanism to undo this by creating recover points.  Is it perfect?  No.  Does it work 100% of the time?  No, but in my experience it does work at least 90% of the time.  

The bottom line is this -- as long as every package upgrade has the potential to destroy a stable installation if there are changes made to any config file that isn't considered "standard", or it is done in some way that isn't considered "standard" (which introduces a whole different problem, since you can generally find 25 ways in 30 different newsgroups to solve any given issue), we're not going to gain the kind of mindshare we'd like.  The end user experience is not sufficient to go mainstream.  If all we're interested in is providing the best distro for enthusiasts, then this doesn't really matter, because enthusiasts will always be more willing than the general population to tinker.  

If we want to capitalize on the Dell decision, serious resources need to go into making the end user experience BETTER than what they have with Windows.  Different is good, but different and not better doesn't win us the mindshare, and if we don't win the mindshare, Ubuntu will be replaced with something else they think will.

---

### Post by Brunellus on 2007-05-07
> **chashock said:**
> This is the fundamental attitude problem that if the community does not overcome, no Linux distribution will ever go mainstream and become a driving force in displacing the Microsoft dominance we all seem to have a problem with.

The issue to me has not been one of maintaining things properly.  It has been that in ORDER to maintain my system properly, I have to do what are apparently non-standard things.  To get my ATI video card, MS laser 6000 mouse, dual ViewSonic flat panels, dual DVD writers, wireless keyboard, etc., etc., I have to tweak, twist, torment, and in many other ways modify several files, any one of which can get horked in a system upgrade or even a simple package upgrade.

You are adapting software to fit an existing (and non-standard!) hardware set-up, and you are complaining?

The hardware you're using works reasonably well on Windows because the software to drive it was written for Windows.  That same software is unusable on other operating systems because of the terms of its licence(s).  

The "great responsibility" that Dell has is to offer hardware that works "out of the box" with the operating systems they offer to the end-user.  The most elegant way of doing that for Dell--which, remember, is a *hardware* vendor-- is to offer Ubuntu on those systems on which Ubuntu is known to work, and furiously disclaim responsibility for any other configuration.

If that sounds familiar, it is:  Apple have done it forever.  You can argue that the closed Apple approach has been bad for the general uptake of Apple computers, and I wouldn't disagree.  But the difference here is that no single vendor will have total control of the hardware specification.  Nothing stops HP from offering a better, even more compatible Linux computer, or from providing Linux drivers.  Nothing prevents third-party hardware vendors from doing the same, either. 

 In the long term, the Dell move might end up increasing the installed base of OSes that use the Linux kernel. The fact that more and more hardware will be "known to work" with Linux will shift the balance away from MSFT-only devices, drivers, and specifications.  

The community cannot be held hostage by a relative minority of users who demand bleeding-edge libraries for unsupported devices.

---

