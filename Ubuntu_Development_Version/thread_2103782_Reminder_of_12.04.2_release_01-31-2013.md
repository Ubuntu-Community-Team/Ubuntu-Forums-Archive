---
title: "Reminder of 12.04.2 release 01-31-2013"
date: 2013-01-11
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-01-11
For those who love testing we're approaching the second step release of Precise :)

If you have any existing Precise bugs you'd like to follow up on this is probably the time. A recent 'apport' update reminded me :D

Images are available here:

[http://iso.qa.ubuntu.com/qatracker/milestones/204/builds](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds)

---

### Post by kansasnoob on 2013-01-11
RUH-roh ............... that should be "Reminder of 12.04.2 release 01-31-201**[COLOR="Red"]3[/COLOR]**", but what's a year between friends :redface:

---

### Post by grahammechanical on 2013-01-11
This 12.04.2 release should upgrade Grub 1.99 to Grub 2.0. Expect surprised chatter in other parts of the forums.

Regards.

---

### Post by zombifier25 on 2013-01-11
> **grahammechanical said:**
> This 12.04.2 release should upgrade Grub 1.99 to Grub 2.0. Expect surprised chatter in other parts of the forums.

Regards.

Whoa, when GRUB 2 came out, I have always presumed my 12.04 comp is using it.

And now, after a simple apt-cacheing,... nope :lolflag:

---

### Post by kansasnoob on 2013-01-11
> **grahammechanical said:**
> This 12.04.2 release should upgrade Grub 1.99 to Grub 2.0. Expect surprised chatter in other parts of the forums.

Regards.

Aargh, that could be problematic:

[http://ubuntuforums.org/showthread.php?t=2101763](http://ubuntuforums.org/showthread.php?t=2101763)

Then again it's really only noticeable if you have more than 2 *buntu's on a machine and I'd hope most mega-multi-booters know their way around grub well enough to deal with it.

---

### Post by grahammechanical on 2013-01-11
The new look will surprise a lot of people. And I have just found another possible problem that some may have.

The 12.04.2 release gets the Quantal kernel (3.5.0). I tested this out a few months ago. It worked fine with Nouveau and with Nvidia current-updates 304.43 but not with Nvidia current recommended.

I have just now run this 12.04.1 install with kernel 3.5.0 and it will not let you activate Nvidia current recommended. Which stops it breaking the system at least.

We will see how things turn out with ordinary users.

Regards.

---

### Post by cariboo on 2013-01-11
I just received this email:

> Ubuntu 12.04.2 is currently scheduled to be released on Jan 31st [0].

This is the first time we have shipped a backported Hardware
Enablement stack in a LTS release, comprised of a new kernel and
graphics subsystem.  At this time we feel it is better to delay the release
by two weeks to allow time for extra QA testing.

This would put the new release date on 14 Feb 2013.  No other dates
would change (i.e. freezes etc.), we are just using the extra two weeks
for testing and possible bug fixing for identified issues.

The QA Test Plan will be to have the Community Team conduct
extensive manual testing with the Ubuntu Testing Community.  In addition,
the Canonical QA team & Certification teams will be running
further automated testing to ensure that the 12.04.2 point release is of
superior quality.

Provided there are no major objections I will update the Release
Schedule [0] before the end of today.

[0] [https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

Thanks

~pete
--
Pete Graner - Ubuntu Release Engineering & QA Team Manager -

---

### Post by Gyokuro on 2013-01-11
Sorry but I do not understand this decision - why get an Ubuntu LTS release an EOL kernel?? Sure someone from marketing can sell it me that canonical is supporting it but 3.2.XX is a LTS kernel not 3.5 and this promise is not enough for me.  Maybe someone from the decision makers should check [www.kernel.org](www.kernel.org) which releases are EOL!! If I want an unstable system I will install non LTS releases maybe it's better to wait for Debian 7.0 and do not roll out anymore a  12.04 system.

---

### Post by jbicha on 2013-01-11
Ubuntu 12.04.2 is a bit different than any previous LTS. It will come with the Quantal kernel and graphics drivers backported. It will also support Secure Boot. This way you can have the stable OS but with support for brand new 2012 hardware.

People who are already using Ubuntu 12.04 LTS will not automatically get the Quantal kernel and graphics drivers, so if you don't want those, just use your Ubuntu 12.04.1 CD instead.

---

### Post by grahammechanical on 2013-01-11
I think that there is a mis-understanding of what End Of Life means for a Linux kernel. The link on this page provides some information.

[http://en.wikipedia.org/wiki/Linux_kernel]("http://en.wikipedia.org/wiki/Linux_kernel")

From the chart under the heading of Maintenance we can see this regarding the 3.5 series of kernels

> EOL (Maintained by Kroah-Hartman until the release of 3.6.1), Unofficial extended support until March 2014[120]

and for the 3.2 series

> 8th long-term stable release from March 2012 to 2015, used in Ubuntu 12.04 LTS, Debian 7 Wheezy and Slackware 14.0

If this update to the 3.5 kernel is successful then 12.04 might later be updated to the 3.7 and later still the 3.8 kernels. It is after all going to be around until 2016.

That chart also shows that if 12.04 never moves off of the 3.2 series then it will be using an unsupported kernel for about a year before 12.04 itself reaches EOL.

A responsibility of promising that a release will be supported both on the desktop and on the server for 5 years must surely include the ability to be installed on hardware that will come on the market after the OS was released. That may require more up to date Linux kernels.

I do not understand why this improvement should be a problem. anyone who is concerned about the stability of the OS due to this decision can always join the testing program. As I indicated in my earlier post I already have a 12.04 installed with both Grub 2.0 and the 3.5 kernel installed.

Regards.

---

### Post by kansasnoob on 2013-01-11
> **cariboo907 said:**
> I just received this email:

You beat me to the punch :)

I personally love the idea of "delaying until ready". I rather wish we'd use that policy more often :D

Rather off-topic but this is going to be somewhat of a challenge for me because I'm moving office again ..... this time because the foundation of my house shifted due to a water line break this summer resulting from the drought. I'm sure glad I rent :lolflag:

Edit: many thanks to you or whoever edited my title, I wonder how many months it will take this year to start writing the proper date on my checks.

---

### Post by Gyokuro on 2013-01-11
> **jbicha said:**
> Ubuntu 12.04.2 is a bit different than any previous LTS. It will come with the Quantal kernel and graphics drivers backported. It will also support Secure Boot. This way you can have the stable OS but with support for brand new 2012 hardware.

People who are already using Ubuntu 12.04 LTS will not automatically get the Quantal kernel and graphics drivers, so if you don't want those, just use your Ubuntu 12.04.1 CD instead.

Hi and thank you and that's all fine for users who want to play games via steam to enjoy their games but in some environments you are testing LTS releases for weeks and later after everything got tested and systems get rolled out somebody thought it's good to update the kernel, graphic stack,... and if you check the release notes of Debian you will not find that they change in such a way a release (6.0.1 - 6.0.6) - you can count on them and that's why it's called a stable platform/LTS release and not in this way how it get handled in Ubuntu.

---

### Post by iMac71 on 2013-01-11
just a question: if, before than the 12.04.2 is released, I disable the ubuntu update manager's new version warning, this won't allow the upgrade from 12.04.1 to 12.04.2, right? Or what should I do for maintaining the 12.04.1?

---

### Post by kansasnoob on 2013-01-11
> **iMac71 said:**
> just a question: if, before than the 12.04.2 is released, I disable the ubuntu update manager's new version warning, this won't allow the upgrade from 12.04.1 to 12.04.2, right? Or what should I do for maintaining the 12.04.1?

I assume that's **wrong**!

But I can only base my comments on previous experience so **I could be wrong**.

ATM I'd assume the safest bet is to set updates to security only, but this is a whole new strategy in play, so who knows?

---

### Post by kansasnoob on 2013-01-11
> **jbicha said:**
> Ubuntu 12.04.2 is a bit different than any previous LTS. It will come with the Quantal kernel and graphics drivers backported. It will also support Secure Boot. This way you can have the stable OS but with support for brand new 2012 hardware.

People who are already using Ubuntu 12.04 LTS will not automatically get the Quantal kernel and graphics drivers, so if you don't want those, just use your Ubuntu 12.04.1 CD instead.

OK as I think about this more ............ what will happen with 10.04 -> 12.04 upgrades?

We already know we're going to get swamped with a new round of the "what fresh hell is this UI" complaints, but this is going to be very interesting. If it's done well then great :D

If it's not done well :cry:

---

### Post by cariboo on 2013-01-11
@iMac71, I personally really dislike Update Manager, so I always disable checking for updates and notifications. This doesn't stop the update from happening, but it does allow you to chose what and when you want to update.

---

### Post by iMac71 on 2013-01-12
thanks to both of you, [post=12450738]kansasnoob[/post] and [post=12450809]cariboo907[/post], for your explanations.

---

### Post by Nidec on 2013-01-12
Hi, a little question for the ATI fglrx blob users : does the upgrade to Quantal's graphic stack mean no more support for "legacy" (pre-HD5000) ATI cards in Precise 12.04.2 ?

---

### Post by nomenkultur on 2013-01-12
why not delay it until mid to late february and bring 12.04 up to kernel 3.8?

 this might sound stupid but wouldn't it make sense to have the two supported versions in 2013 share the same kernel?

 I'm sure there are advantages in only having to maintain one kernel version throughout 2013.

 I've actually seen people with 12.04 manually upgrade to 3.7...  what breaks from 3.2 to 3.8 will most likely also break from 3.2 to 3.8

---

### Post by kansasnoob on 2013-01-12
I have no answers for anyone yet but I finally logged into my stable Precise to check proposed updates and regarding Xorg I see this:

> xorg (1:7.6+12ubuntu2) precise-proposed; urgency=low

  * **Update package to enable support for quantal backport stack** (LP: #1095686)
  * **[COLOR="Red"]Add xserver-xorg-lts-precise which can be installed to rollback from renamed stack[/COLOR]**
    - depends on unrenamed xserver-xorg, recommends unrenamed versions of packages
  * Allow xserver-xorg-renamed to satisfy xorg's xserver-xorg dependency
  * Require unrenamed versions of packages in xserver-xorg
  * Add conflicts/replaces in xserver-xorg to xorg-renamed-package,
    and provide xserver-xorg-renamed

 -- Maarten Lankhorst <maarten.lankhorst@ubuntu.com>  Thu, 22 Nov 2012 00:00:43 +0100

I'll keep looking at changelogs and see what I can learn, but it looks like the devs have planned on the need for some needing to "roll back" ;)

---

### Post by kansasnoob on 2013-01-12
Regarding the kernel I see nothing yet about the Quantal version in the proposed updates but the daily images have both:

> linux-generic-lts-quantal	3.5.0.22.29
linux-headers-3.2.0-36	3.2.0-36.57
linux-headers-3.2.0-36-generic-pae	3.2.0-36.57
linux-headers-3.5.0-22	3.5.0-22.34~precise1
linux-headers-3.5.0-22-generic	3.5.0-22.34~precise1
linux-headers-generic-lts-quantal	3.5.0.22.29
linux-headers-generic-pae	3.2.0.36.42
linux-image-3.5.0-22-generic	3.5.0-22.34~precise1
linux-image-generic-lts-quantal	3.5.0.22.29

So it looks to me like they have all the bases covered. I'd bet they'll address the whole issue in the release notes :D

---

### Post by craig10x on 2013-01-13
Does this coming release of 12.04.2 have any new stuff on it (for example, the more current version of rhythmbox that wasn't in 12.04 but is in 12.10) or any of the improvements found in 12.10 that weren't included in 12.04?

Or is it primarily just an up-to date version of 12.04 (up to date meaning all it does is spare you of having to download tons of updates that came in since the last release of 12.04)...

---

### Post by kansasnoob on 2013-01-13
I just decided to try an image to see what's up and ubiquity is borked :( I believe 12.04.1 was released 2012-08-23, and I tested an image on 2012-11-30 to verify a bug fix, so the only changes to ubiquity since 11-30 are:

> ubiquity (2.10.23) precise-proposed; urgency=low

  * Honour base-installer/kernel/altmeta when deciding which kernels to
    install or keep installed.

 -- Colin Watson <cjwatson@ubuntu.com>  Thu, 06 Dec 2012 17:20:32 +0000

ubiquity (2.10.22) precise-proposed; urgency=low

  [ Dmitrijs Ledkovs ]
  * Make user-setup-encrypted-swap wait until partitioning has finished
    before attempting to adjust /target/etc/fstab. (LP: #1024343)
    (LP: #1068178)

  [ Colin Watson ]
  * Don't remove kernel headers just because we're removing signed kernel
    images of the same flavour (LP: #1070427).

 -- Colin Watson <cjwatson@ubuntu.com>  Sat, 01 Dec 2012 01:02:01 +0000


Basically what happens is you're not even offered any partitioning options at all :shock:

I'll try to grab some screenshots and then file a bug report.

EDIT: This didn't happen on my other set of testing hardware so I need to do some more serious studying. In fact this second trial worked perfectly.

EDIT #2: It appears to have just been a problem with my optical drive. I swapped in one I had recently cleaned and all seems well. Darn dust bunnies.

---

### Post by kansasnoob on 2013-01-13
> **craig10x said:**
> Does this coming release of 12.04.2 have any new stuff on it (for example, the more current version of rhythmbox that wasn't in 12.04 but is in 12.10) or any of the improvements found in 12.10 that weren't included in 12.04?

Or is it primarily just an up-to date version of 12.04 (up to date meaning all it does is spare you of having to download tons of updates that came in since the last release of 12.04)...

Generally the latter but this is an uncommon LTS point release so all bets are off :)

---

### Post by craig10x on 2013-01-13
thank you Kansasnoob :)

I thought that might be the case...anyway, i am running 12.10 and i have previewed 13.04 on daily builds and it seems to have some nice improvements so i guess i will just wait for that (rather then install 12.04)...

---

### Post by kansasnoob on 2013-01-13
> **craig10x said:**
> thank you Kansasnoob :)

I thought that might be the case...anyway, i am running 12.10 and i have previewed 13.04 on daily builds and it seems to have some nice improvements so i guess i will just wait for that (rather then install 12.04)...

In deed, I love swimming in the deep end with the newest (and usually greatest), but I support over 40 individual PC's spread out over two counties so I keep them on LTS receiving only security updates :D

There have only been three Ubuntu releases that I skipped over since Gutsy, those were Intrepid, Karmic, and Quantal due to changes that simply stunk for me. Both Intrepid and Karmic were kernel related problems, but I believe Quantal was due to the Compiz + llvmpipe thing .... I'm not actually sure but both Lubuntu and Xubuntu Quantal run great.

It's just awesome to know that there's a great LTS to fall back on in times of need :guitar:

---

### Post by kansasnoob on 2013-01-13
I'm awe struck at how snappy this fresh Precise install is :)

It does have both the new kernel:

```
lance@lance-desktop:~$ uname -a
Linux lance-desktop 3.5.0-22-generic #34~precise1-Ubuntu SMP Wed Jan 9 21:37:29 UTC 2013 i686 i686 i386 GNU/Linux

```

And the new Xorg stack:

> xorg (1:7.6+12ubuntu2) precise-proposed

Now I need to see why this is snappier than my old every-day stable Precise :)

It should be fairly easy because the Xorg stack is in proposed updates, and I know it'll be possible to update to the Quantal kernel w/o a reinstall.

---

### Post by kansasnoob on 2013-01-14
Hmmm, looking at an older Precise (installed 2012-04-23) 'linux-generic-lts-quantal' is available in the repos:

[ATTACH]230031[/ATTACH]

So it looks to me like the devs are covering all the bases :D

---

### Post by kansasnoob on 2013-01-14
Regarding grub it looks to me like they backported some fixes/patches for UEFI and secure-boot to version "1.99-21ubuntu3.7" rather than bumping it up to version 2.*. But that's just my best guess :D

---

### Post by Cavsfan on 2013-01-16
> **grahammechanical said:**
> This 12.04.2 release should upgrade Grub 1.99 to Grub 2.0. Expect surprised chatter in other parts of the forums.

Regards.

I believe that will be a good change. For anyone dual booting with windows that has a custom grub2 menu from my wiki, grub 1.99 gives an erroneous error when windows is selected:
```
Error: No argument specified.

Press any key to continue...
```But, waiting a couple of seconds or pressing a key, it continues into windows.
Grub 1.98 did not and Grub 2.00 does not produce that error either.

---

### Post by kevpan815 on 2013-01-20
I don't know if this is an error in Cariboo907's Updated Release Calendar or not, but if you take a good look at February 14th, 2013, it says: 12.04.2 Release (Opt In Flavors Only). Could someone please clarify exactly what that means, as I see the same thing written next to all the 13.04 Alpha's/Beta 1! Does this mean that there is NOT going to be a Ubuntu 12.04.2, but there will be a Kubuntu/Xubuntu 12.04.2, or does this just simply mean that Releases that are not LTS (like Lubuntu 12.04, for example) will not get the Update, and Ubuntu will get 12.04.2 after all? Could Cariboo907 or any one else that knows the answer to my question reply in this post? TIA.

---

### Post by cariboo on 2013-01-20
> **kevpan815 said:**
> I don't know if this is an error in Cariboo907's Updated Release Calendar or not, but if you take a good look at February 14th, 2013, it says: 12.04.2 Release (Opt In Flavors Only). Could someone please clarify exactly what that means, as I see the same thing written next to all the 13.04 Alpha's/Beta 1! Does this mean that there is NOT going to be a Ubuntu 12.04.2, but there will be a Kubuntu/Xubuntu 12.04.2, or does this just simply mean that Releases that are not LTS (like Lubuntu 12.04, for example) will not get the Update, and Ubuntu will get 12.04.2 after all? Could Cariboo907 or any one else that knows the answer to my question reply in this post? TIA.

The second LTS point release was supposed to be on January 29th, but it was set back two weeks in order to get some extra testing done.

See [this]("http://ubuntuforums.org/showpost.php?p=12450165&postcount=7") post for an explanation

---

### Post by kevpan815 on 2013-01-20
> **cariboo907 said:**
> The second LTS point release was supposed to be on January 29th, but it was set back two weeks in order to get some extra testing done.

See [this]("http://ubuntuforums.org/showpost.php?p=12450165&postcount=7") post for an explanation

I know that, but why does it say Opt In Flavors Only?

---

### Post by cariboo on 2013-01-20
It says Opt-In releases, as some of the flavours, Lubuntu for one don't have an LTS release, Kubuntu and Xubuntu do.

---

### Post by kansasnoob on 2013-01-20
> **cariboo907 said:**
> The second LTS point release was supposed to be on January 29th, but it was set back two weeks in order to get some extra testing done.

See [this]("http://ubuntuforums.org/showpost.php?p=12450165&postcount=7") post for an explanation

That was a duh moment on my part .......... I should have edited my OP the next day when that announcement came out :oops:

---

### Post by yuripg1 on 2013-02-05
> **Nidec said:**
> Hi, a little question for the ATI fglrx blob users : does the upgrade to Quantal's graphic stack mean no more support for "legacy" (pre-HD5000) ATI cards in Precise 12.04.2 ?I have to bring this up again, since I didn't see anyone answering it. It is important to me because I'm planning a fresh upgrade on my machine at work (and it has an AMD HD4000-series GPU).

Is there going to be a way of remaining on the binary driver with Ubuntu 12.04.2? (Perhaps with some legacy package to change X.org and other packages to proper/older versions)

Thanks anyway!

---

### Post by kuvanito on 2013-02-05
with the aproaching release of RR 13.04 and all the goodies it brings,new features and latest tech,who wants a 12.04.xxx release,not me.hehehehehe

---

### Post by ventrical on 2013-02-05
It should be a solid, stable release for noobs.  Those guys at Canonical gotta eat to ya know :)

---

### Post by jerrylamos on 2013-02-05
> **kuvanito said:**
> with the aproaching release of RR 13.04 and all the goodies it brings,new features and latest tech,who wants a 12.04.xxx release,not me.hehehehehe

Me.  When 13.04 unstable is too unstable to run then I use 12.04 daily build updated.

Also, I do some finances and stock stuff with 12.04 daily build updated and really want stable for those.  Among other things, Firefox AOL "compose" is really flaky on 13.04.  Yahoo & Gmail O.K., Opera is O.K. with all.

---

### Post by CharlesA on 2013-02-05
> **kuvanito said:**
> with the aproaching release of RR 13.04 and all the goodies it brings,new features and latest tech,who wants a 12.04.xxx release,not me.hehehehehe

*raises hand*

I prefer running LTS releases as it is easier for me to set it and forget it. :p

---

### Post by zika on 2013-02-06
> **CharlesA said:**
> *raises hand*

I prefer running LTS releases as it is easier for me to set it and forget it. :pWriting such statement in _this_ forum is somehow kind of party-breaking... [img]http://www.sherv.net/cm/emo/laughing/animated-laughing-smiley-emoticon.gif[/img]

---

### Post by Cavsfan on 2013-02-06
> **jerrylamos said:**
> Me.  When 13.04 unstable is too unstable to run then I use 12.04 daily build updated.

Also, I do some finances and stock stuff with 12.04 daily build updated and really want stable for those.  Among other things, Firefox AOL "compose" is really flaky on 13.04.  Yahoo & Gmail O.K., Opera is O.K. with all.

> **CharlesA said:**
> *raises hand*

I prefer running LTS releases as it is easier for me to set it and forget it. :p

Me three! I am hanging on to Lucid Lynx right up until April. :) Plus I have 12.04.1 on here too. 
I guess I will always have 2 of the other releases on here also but, LTS's are for the good, important stuff.

---

### Post by kansasnoob on 2013-02-06
> **Cavsfan said:**
> Me three! I am hanging on to Lucid Lynx right up until April. :) Plus I have 12.04.1 on here too. 
I guess I will always have 2 of the other releases on here also but, LTS's are for the good, important stuff.

Me four :D

I still test all of the interim releases but I usually start using each LTS as my "stable" OS when the first point release drops.

Although 9.04 (Jaunty) was an exception, it just worked so well I preferred it to 8.04. Then 10.04 was super great also :D

---

### Post by Cavsfan on 2013-02-07
This seems pretty strange:

```
cavsfan@cavsfan-MS-7529:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"
```Why would it say this?

---

### Post by kansasnoob on 2013-02-07
> **Cavsfan said:**
> This seems pretty strange:

```
cavsfan@cavsfan-MS-7529:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"
```Why would it say this?

What part seems strange?

---

### Post by Cavsfan on 2013-02-07
> **kansasnoob said:**
> What part seems strange?

That it says 12.04.2 already. I thought that hadn't been released yet and I have noticed my conky has reported that for quite a while.

Should it not say 12.04.1 right now?

---

### Post by kansasnoob on 2013-02-07
> **Cavsfan said:**
> That it says 12.04.2 already. I thought that hadn't been released yet and I have noticed my conky has reported that for quite a while.

Should it not say 12.04.1 right now?

They pushed that update here:

> base-files (6.5ubuntu6.5) precise; urgency=low

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
    version number to 12.04.2 in preparation for the point release.

 -- Colin Watson <cjwatson@ubuntu.com>  Fri, 25 Jan 2013 11:07:10 +0000

But the official download is still 12.04.1.

---

### Post by Cavsfan on 2013-02-07
> **kansasnoob said:**
> They pushed that update here:



But the official download is still 12.04.1.

Thanks. I noticed my Lucid install says 12.04.4 even though I did not do a clean install with 12.04.4

---

### Post by kansasnoob on 2013-02-07
> **Cavsfan said:**
> Thanks. I noticed my Lucid install says 12.04.4 even though I did not do a clean install with 12.04.4

Since everyone is spell checking everyone else lately I assume you mean 10.04.4 :lolflag:

---

### Post by kansasnoob on 2013-02-07
> **yuripg1 said:**
> I have to bring this up again, since I didn't see anyone answering it. It is important to me because I'm planning a fresh upgrade on my machine at work (and it has an AMD HD4000-series GPU).

Is there going to be a way of remaining on the binary driver with Ubuntu 12.04.2? (Perhaps with some legacy package to change X.org and other packages to proper/older versions)

Thanks anyway!

This is a good question, and one I can't answer, so I thought I'd give it a bump :)

---

### Post by Cavsfan on 2013-02-07
> **kansasnoob said:**
> Since everyone is spell checking everyone else lately I assume you mean 10.04.4 :lolflag:
You got that right! LOL! I did mean 10.04.4!

I sure hope 12.04.2 does away with the read only file system on recovery! That has caused me countless headaches!
Today I could not get into Precise: it would allow me to enter my password and "start" to begin the login process and after 2 seconds back to the login screen.

I had gone by Paddy's workaround to install the most current nvidia driver:
1) Login to recovery.
2) Select root console and enter:
```
mount --options remount,rw /
mount --all
```Today what saved me was root console and entering **nvidia-installer --uninstall** which totally got rid of the driver.
Then I could select one from SPM and I got it back. Whew! I thought I lost it but, it seems there is almost always a way to fix it.
The more experience you have, the more options you have. :guitar:

---

### Post by kansasnoob on 2013-02-07
> **Cavsfan said:**
> You got that right! LOL! I did mean 10.04.4!

I sure hope 12.04.2 does away with the read only file system on recovery! That has caused me countless headaches!
Today I could not get into Precise: it would allow me to enter my password and "start" to begin the login process and after 2 seconds back to the login screen.

I had gone by Paddy's workaround to install the most current nvidia driver:
1) Login to recovery.
2) Select root console and enter:
```
mount --options remount,rw /
mount --all
```Today what saved me was root console and entering **nvidia-installer --uninstall** which totally got rid of the driver.
Then I could select one from SPM and I got it back. Whew! I thought I lost it but, it seems there is almost always a way to fix it.
The more experience you have, the more options you have. :guitar:

Yes! The recovery mode has stunk for how long now?

I think it was borked at least as far back as Oneiric :(

---

### Post by Cavsfan on 2013-02-07
> **kansasnoob said:**
> Yes! The recovery mode has stunk for how long now?

I think it was borked at least as far back as Oneiric :(

Definitely! I was complacent on Lucid and then when I found out grub changed my how to needed updating.

I loaded 12.04 with Grub 1.99 and **Drs305** and **Bogan** helped me right it. I have been keeping up with every version 
since then and yes most had that horrible read-only file system at recovery.

Grub 2.00 seems to be the best. 

So, you are saying that they are definitely doing away with the read-only recovery on 12.04.2 which comes out on the 14th? I so hope so! :)

---

### Post by grahammechanical on 2013-02-07
> I sure hope 12.04.2 does away with the read only file system on recovery! That has caused me countless headaches!

That is really weird. An invitation to drop to a root shell prompt with a file system that is read only. Cannot even update the OS to see if that fixes the problem. And they call it Friendly Recovery.

I get around it by first going to Failsafe and then backing out and choosing Root. Failsafe gets a read/write file system. Root does not.

Regards.

---

### Post by kansasnoob on 2013-02-07
Is this the correct bug report:

[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454)

I suspect we'll still have an actual iso-testing session next week for 12.04.2 and it might be beneficial to turn up the heat on this bug :)

---

### Post by Cavsfan on 2013-02-07
> **grahammechanical said:**
> That is really weird. An invitation to drop to a root shell prompt with a file system that is read only. Cannot even update the OS to see if that fixes the problem. And they call it Friendly Recovery.

I get around it by first going to Failsafe and then backing out and choosing Root. Failsafe gets a read/write file system. Root does not.

Regards.

Nothing in recovery works for me except drop to root shell. I cannot get network access, failsafe also just leads to a dead OS. 
All I can do is press the reset button on my PC. If I have to download anything I have to do it on another Ubuntu and copy it to Precise.
As you say, basically worthless and even worse for me.

> **kansasnoob said:**
> Is this the correct bug report:

[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454)

I suspect we'll still have an actual iso-testing session next week for 12.04.2 and it might be beneficial to turn up the heat on this bug :)

Yes that is the bug and I had already added my name and commented at the bottom. I added an additional comment too.
That is also where I found Paddy Landau's workaround. I managed to install the latest Nvidia driver straight from Nvida but, that went kablooey this morning.

Precise has been the only version I have not been able to install the Nvidia driver.

I so hope that is fixed. The whole concept of "Recovery mode" is basically broken for me.
Can't believe there are only 14 names on that bug including myself. :o
I wish we could get everyone that has Precise installed to add their name to that bug! :)

---

### Post by kansasnoob on 2013-02-07
> **Cavsfan said:**
> Nothing in recovery works for me except drop to root shell. I cannot get network access, failsafe also just leads to a dead OS. 
All I can do is press the reset button on my PC. If I have to download anything I have to do it on another Ubuntu and copy it to Precise.
As you say, basically worthless and even worse for me.



Yes that is the bug and I had already added my name and commented at the bottom. I added an additional comment too.
That is also where I found Paddy Landau's workaround. I managed to install the latest Nvidia driver straight from Nvida but, that went kablooey this morning.

Precise has been the only version I have not been able to install the Nvidia driver.

I so hope that is fixed. The whole concept of "Recovery mode" is basically broken for me.
Can't believe there are only 14 names on that bug including myself. :o
I wish we could get everyone that has Precise installed to add their name to that bug! :)

I've seen no indication that it'll be fixed :(

---

### Post by Cavsfan on 2013-02-08
> **kansasnoob said:**
> I've seen no indication that it'll be fixed :(
 
I guess 14 people are not enough to worry about. But, I cannot believe that many others including the developers are not familiar with this bad recovery mode!
This is an LTS for heaven's sake! But, that is also what I gather from looking at that bug report. :(

---

### Post by Cavsfan on 2013-02-08
When I upgrade my version of Lucid 10.04 to 12.04.2 will it pull in Grub 2.00 or is that only on a clean install.
Also, on my current 12.04 install will it too pull in Grub 2.00 when 12.04.2 is released?

Just curious about what to expect.

---

### Post by dino99 on 2013-02-08
Cant say whats doing right now; but anyway:

-dist upgrade, then purge everything about the installed grub: grub, grub-pc, grub*, menu.lst
- clean the system: clean/autoclean/autoremove/gtkorphan/bleachbit
- update the repo again
- then reinstall grub-pc

that will let you a clean bootloader config.

---

### Post by jerrylamos on 2013-02-08
I don't pay any attention to "release" dates.  I just do a rsync from the daily live current, install if there's been a lot of change, then do apt-get update from time to time.

As would be expected, 12.04 LTS is stable especially compared to raring which I run in other partitions.  I use stable when I want to do something reliable on the internet etc.

Likely keep 12.04 LTS until some other LTS shows up that appears to be good.  Do note I run 2D on the 12.04 which I find crisp, sharp, and doesn't try to do a lot of things for me that I don't want done.

Having done a couple things I didn't want to mess up on the internet, I'll boot raring & update to see what works.

---

### Post by kevpan815 on 2013-02-10
I was going to install the 20130210 AMD64 Ubuntu 12.04.2 Alternate Build until I noticed that someone filed a Bug Report about it Installing Mesa 8.04 instead of Mesa 9.00. His Bug Report was eventually Closed by the Ubuntu Developers, but he has now Reopened his own Bug Report himself insisting that. 12.04.2 should have Mesa 9.00 instead of Mesa 8.04! So my question is the following: Is it safe to install today's AMD64 Ubuntu 12.04.2 Nightly Build (20130210), and is the other guys Bug Report really a Bug?

---

### Post by U202E on 2013-02-10
you could install mesa9 manually, there is an updated-and-optimized-grafic-drivers ppa.
^^or build from source.

---

### Post by wildmanne39 on 2013-02-10
*Thread moved to **General Help**.*

---

### Post by Mopar1973Man on 2013-02-10
I'm running the 12.04.2 LTS - Linux 3.2.0-37 no problem here.

---

### Post by kevpan815 on 2013-02-10
> **Wild Man said:**
> *Thread moved to **General Help**.*

Are posts about Pre-Release 12.04.2 Nightly Builds supposed to be posted in General Help? I mean right now we are doing the same ISO.QA.UBUNTU.COM Testing on 12.04.2 as we are doing on 13.04 Alpha 2 right now. Did I really post this Message in the Wrong Forum, Cariboo907 told me that 12.04.2 Official Release was Delayed until February, 14th, 2013, (Valentine's Day in the U.S.A.)?

---

### Post by kevpan815 on 2013-02-10
> **U202E said:**
> you could install mesa9 manually, there is an updated-and-optimized-grafic-drivers ppa.
^^or build from source.

This was NOT my Bug Report by the way, the only reason I noticed it is when I went to ISO.QA.UBUNTU.COM, someone had Filed this Bug Report against the AMD64 Ubuntu 12.04.2 20130210 Alternate CD (DVD really as the Build is Oversized) Nightly Build.

---

### Post by kevpan815 on 2013-02-10
> **Mopar1973Man said:**
> I'm running the 12.04.2 LTS - Linux 3.2.0-37 no problem here.

Actually, you most likely have 12.04.1 installed as 12.04.2 is still in Pre-Release Testing, and has a Linux Kernel 3.5.something instead of 3.2.something as they are now going to include the Quantal Kernel with Precise 12.04.2, by the way, at least according to what Cariboo907 told me in the Ubuntu +1 Forum.

---

### Post by mc4man on 2013-02-10
As to your question ...safe, sure, there should be no real issues.

If after install you wish to upgrade mesa/xserver to the '..lts-quantal' versions then that's certainly possible.
There may be some easy way, (ppa or whatever), or you can do so in synaptic with a little bit of patience & paying attention, just did so here to see
(basically you'd remove most the current non lts packages in mesa/xserver along with a whole lot more (compiz, unity*, ect. ect.

Then after refreshing sources install the lts ones & then all the previous removed packages (or install ubuntu-desktop should pull most of those back.. unity*, compiz ect.

---

### Post by howefield on 2013-02-10
> **kevpan815 said:**
> Actually, you most likely have 12.04.1 installed as 12.04.2 is still in Pre-Release Testing, and has a Linux Kernel 3.5.something instead of 3.2.something as they are now going to include the Quantal Kernel with Precise 12.04.2, by the way, at least according to what Cariboo907 told me in the Ubuntu +1 Forum.

Actually, he is more likely to be running 12.04.02 if he is fully updated.

Anyone running 12.04 will have to deliberately install the newer 3.5 kernel to get it, either by manually installing from the repos or installing fresh from a 12.04.2  installation media.

---

### Post by kevpan815 on 2013-02-10
> **howefield said:**
> Actually, he is more likely to be running 12.04.02 if he is fully updated.

Anyone running 12.04 will have to deliberately install the newer 3.5 kernel to get it, either by manually installing from the repos or installing fresh from a 12.04.2  installation media.

What I was referring to is the following: If you Clean Install Today's Nightly Build of 12.04.2, you will end up with Kernel Linux 3.5.0-23-generic on an AMD64 Ubuntu 12.04.2 Clean Install.

---

### Post by kevpan815 on 2013-02-10
> **mc4man said:**
> As to your question ...safe, sure, there should be no real issues.

If after install you wish to upgrade mesa/xserver to the '..lts-quantal' versions then that's certainly possible.
There may be some easy way, (ppa or whatever), or you can do so in synaptic with a little bit of patience & paying attention, just did so here to see
(basically you'd remove most the current non lts packages in mesa/xserver along with a whole lot more (compiz, unity*, ect. ect.

Then after refreshing sources install the lts ones & then all the previous removed packages (or install ubuntu-desktop should pull most of those back.. unity*, compiz ect.

Actually, all I wanted to know was if today Build worked or NOT (which the other guy who Filed the Bug Report marked the Installation as a Fail rather than a Pass and then used his Bug Report as a Reason for Marking it as a Fail rather than a Pass, and then Re-opened his own Bug Report even after the Ubuntu Developer's told him that it was an Invalid Bug Report). I just finished installing today's 12.04.2 Nightly Build and am pleased to report that it is a Pass, NOT A FAIL. Problem Solved.

---

### Post by kansasnoob on 2013-02-10
> **Wild Man said:**
> *Thread moved to **General Help**.*

I really don't think this should have been moved because we've been discussing 12.04.2 testing in Ubuntu + 1.

This sort of dates all the way back to here:

[http://ubuntuforums.org/showthread.php?t=2044030](http://ubuntuforums.org/showthread.php?t=2044030)

---

### Post by kansasnoob on 2013-02-10
I've not had time to try any of the alternate images yet :(

I really wore myself out trying some upgrade/replace options with the live image ........ something I'm trying to figure out myself:

[http://ubuntuforums.org/showpost.php?p=12465489&postcount=36](http://ubuntuforums.org/showpost.php?p=12465489&postcount=36)

---

### Post by kevpan815 on 2013-02-10
> **kansasnoob said:**
> I really don't think this should have been moved because we've been discussing 12.04.2 testing in Ubuntu + 1.

This sort of dates all the way back to here:

[http://ubuntuforums.org/showthread.php?t=2044030](http://ubuntuforums.org/showthread.php?t=2044030)

I'm confused as well, I thought Ubuntu +1 was the proper place to discuss 12.04.2 as it has still not been officially released yet, at least not till Thursday at the earliest (assuming that it does not get delayed again), as the Alternate Builds are still Oversized.

---

### Post by kevpan815 on 2013-02-10
> **kansasnoob said:**
> I've not had time to try any of the alternate images yet :(

I really wore myself out trying some upgrade/replace options with the live image ........ something I'm trying to figure out myself:

[http://ubuntuforums.org/showpost.php?p=12465489&postcount=36](http://ubuntuforums.org/showpost.php?p=12465489&postcount=36)

I've been doing LVM + Encryption Installs of the 12.04.2 Nightly Builds and everything has been working just fine so far other than the fact that the Alternate Builds are still Oversized, so I have to use a DVD instead just like I do with 13.04 Nightly Builds. Other than that, no problems so far.

---

### Post by Bucky Ball on 2013-02-10
Posted in error. ;)

---

### Post by grahammechanical on 2013-02-11
From what I have read in this thread I conclude that someone thought that a certain library should be in the 12.04.2 ISO image and when it was not included this person reported its absence as a bug. It is not a bug type bug. It is a non-bug type bug.

This kind of mis-reporting gives the impression that Ubuntu is buggy. I think that it is an abuse of the bug reporting system.

Canned response

> Thank you for taking the time to make Ubuntu better. Since what you submitted is not really a bug, or a problem, but rather an idea to improve Ubuntu, you are invited to post your idea in Ubuntu Brainstorm at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) where it can be discussed, voted on by the community, and reviewed by developers. Thanks for taking the time to share your opinion!

[https://wiki.ubuntu.com/Bugs/HowToTriage]("https://wiki.ubuntu.com/Bugs/HowToTriage")

Regards.

---

### Post by kevpan815 on 2013-02-11
I was NOT trying to get anyone in trouble, I was just curious if it was actually safe to install Yesterday's 12.04.2 Nightly Build, seeing how this other guy Marked Yesterday's Build as a Fail rather than a Pass, as I already said, the problem is solved as I was successfully able to install Yesterday's Build without any Problems.

---

### Post by ventrical on 2013-02-12
> **kevpan815 said:**
> I was NOT trying to get anyone in trouble, I was just curious if it was actually safe to install Yesterday's 12.04.2 Nightly Build, seeing how this other guy Marked Yesterday's Build as a Fail rather than a Pass, as I already said, the problem is solved as I was successfully able to install Yesterday's Build without any Problems.


Basically that is why we are all testing and what may be a FAIL on one machine will be a PASS on another. I see all sorts of bug reports this cycle .. amd64 no way starting up and on my machines all is working well.  So there are all sorts of different scenarios .. that's what makes it so much fun...

---

### Post by grahammechanical on 2013-02-13
My point (and I also am not wishing to get anybody in trouble) is that we test what is in the build image.

Ubuntu 12.04.2 has the Linux 3.5 kernel as expected. It does not have Grub 2.0. I think that Grub 2.0 would give a better user experience to the person who has a simple two OS dual boot set up. But I would not mark the daily build as a fail because it does not have a package I think that it should have. I not see that as part of development testing.

And I also agree with you that Ubuntu+1 is the place to discuss the testing of point releases of the stable Ubuntu release. It is what this section is here for.

Regards.

---

### Post by yuripg1 on 2013-02-13
> **Nidec said:**
> Hi, a little question for the ATI fglrx blob users : does the upgrade to Quantal's graphic stack mean no more support for "legacy" (pre-HD5000) ATI cards in Precise 12.04.2 ?> **yuripg1 said:**
> I have to bring this up again, since I didn't see anyone answering it. It is important to me because I'm planning a fresh upgrade on my machine at work (and it has an AMD HD4000-series GPU).

Is there going to be a way of remaining on the binary driver with Ubuntu 12.04.2? (Perhaps with some legacy package to change X.org and other packages to proper/older versions)

Thanks anyway!Any news on that matter?

Thanks anyway!

---

### Post by kansasnoob on 2013-02-13
> **yuripg1 said:**
> Any news on that matter?

Thanks anyway!

I'm clueless :redface:

I do know that upgrades from both Lucid and Oneiric stay with the 3.2* kernel instead of jumping to 3.5* but I have no ATI graphics to test with :(

---

### Post by kevpan815 on 2013-02-14
> **grahammechanical said:**
> My point (and I also am not wishing to get anybody in trouble) is that we test what is in the build image.

Ubuntu 12.04.2 has the Linux 3.5 kernel as expected. It does not have Grub 2.0. I think that Grub 2.0 would give a better user experience to the person who has a simple two OS dual boot set up. But I would not mark the daily build as a fail because it does not have a package I think that it should have. I not see that as part of development testing.

And I also agree with you that Ubuntu+1 is the place to discuss the testing of point releases of the stable Ubuntu release. It is what this section is here for.

Regards.

Actually, I dual boot on my Primary Computer Only (between Windows 8 and Raring). On my Secondary Computer it's Precise + LVM + Encryption (by using the Alternate CD) all the way.

---

### Post by kevpan815 on 2013-02-14
My problems with AMD64 and ATI only exist 13.04, although 12.04.2 says No Video Mode Selected at Boot Up on 12.04.2, it still boots up just fine, 13.04 is a different story altogether.

---

### Post by cariboo on 2013-02-14
Merged two similar threads.

---

### Post by ventrical on 2013-02-14
> **kansasnoob said:**
> I'm clueless :redface:

I do know that upgrades from both Lucid and Oneiric stay with the 3.2* kernel instead of jumping to 3.5* but I have no ATI graphics to test with :(


On a raring install , using older ATi graphics cards it is using the Gallium 0.4 driver.

---

### Post by kevpan815 on 2013-02-14
> **ventrical said:**
> On a raring install , using older ATi graphics cards it is using the Gallium 0.4 driver.

Well all I can tell you is that there are Boot Up Problems on my Dell Zino 400 HD Desktop with 13.04 which has an AMD 64 Bit Processor, and an ATI Radeon 3200 HD Graphics Card, Just FYI.

---

### Post by ventrical on 2013-02-14
I just updated Precise to 12.04.2LTS and this is the driver that it is using:

```

   *-display:0
                description: VGA compatible controller
                product: RV350 AQ [Radeon 9600]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
              

```

---

### Post by kevpan815 on 2013-02-14
> **ventrical said:**
> I just updated Precise to 12.04.2LTS and this is the driver that it is using:

```

   *-display:0
                description: VGA compatible controller
                product: RV350 AQ [Radeon 9600]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
              

```

What do you type in to get that read out?

---

### Post by ventrical on 2013-02-14
sudo -i
lshw

---

### Post by zika on 2013-02-15
> **ventrical said:**
> sudo -i
lshwCaveat: Be careful not to forget to leave that root shell... I know I did (not once)...
After that I use simple```
sudo lshw
```

---

### Post by ventrical on 2013-02-15
Of course. You can just use lshw without sudo -i but it recommends to drop to root for full information.

Thanks for the reminder for exiting out of root.  I often forget when I am intently involved.

---

### Post by kansasnoob on 2013-02-15
How do you report a bug about the Release Notes?

Two of the download links are borked:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Download](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Download)

[http://releases.ubuntu.com/12.04.1/](http://releases.ubuntu.com/12.04.1/)

[http://cdimage.ubuntu.com/releases/12.04.1/](http://cdimage.ubuntu.com/releases/12.04.1/)

Obviously just didn't get updated ;)

---

### Post by kansasnoob on 2013-02-15
> **kansasnoob said:**
> This is a good question, and one I can't answer, so I thought I'd give it a bump :)

Still clueless but you might want to see the release notes:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)

> On systems with an ATI Radeon 9200 graphics card the system will boot to a black screen. As a work around edit the kernel command line in the boot loader and add "nomodeset".

---

### Post by ventrical on 2013-02-15
> **kansasnoob said:**
> How do you report a bug about the Release Notes?

Two of the download links are borked:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Download](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Download)

[http://releases.ubuntu.com/12.04.1/](http://releases.ubuntu.com/12.04.1/)

[http://cdimage.ubuntu.com/releases/12.04.1/](http://cdimage.ubuntu.com/releases/12.04.1/)

Obviously just didn't get updated ;)

  I have edit privlidges for the wiki links but not for the other two links. I think those are exlcusively Canonical.

Good eye, Hawkeye ! :)

---

### Post by kansasnoob on 2013-02-15
> **ventrical said:**
> I have edit privlidges for the wiki links but not for the other two links. I think those are exlcusively Canonical.

Good eye, Hawkeye ! :)

Maybe I'll PM Nicholas ;)

---

### Post by ventrical on 2013-02-15
> **kansasnoob said:**
> How do you report a bug about the Release Notes?

Two of the download links are borked:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Download](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Download)

[http://releases.ubuntu.com/12.04.1/](http://releases.ubuntu.com/12.04.1/)

[http://cdimage.ubuntu.com/releases/12.04.1/](http://cdimage.ubuntu.com/releases/12.04.1/)

Obviously just didn't get updated ;)

@kansasnoob

Ok... enter the number 2 where the number 1 is .. ie;

[http://releases.ubuntu.com/12.04.2/](http://releases.ubuntu.com/12.04.2/)

[http://cdimage.ubuntu.com/12.04.2/](http://cdimage.ubuntu.com/12.04.2/)

but I hardly see where there is any release information here .. just how to download and install

regards...

ventrical

---

### Post by bogan on 2013-02-15
Hi!, All,

The delayed release of 12.04.2 -  even now it is still not offered as an Update Manager option - persuaded me to do a clean, formatted install.

One very good thing, after rebooting it only needed 21 updates, so the installation was complete in less than 20 minutes, despite a slow network connection.

Not all good though, despite a separate Home partition I lost all my Firefox configs, and my grub has gone from messy and bad to almost totally corrupt - 69 Menu entries, some of them three lines long!!

It includes two pairs of entries for 12.04.2, one with 3.2.0.-37 in sda5 - it said, actually sda5 was /home, and one for 3.5.0.23 in sda8 as root.

The graphics are a mess too as the nvidia-current-updates-304, which was running very well is no longer offered and the only alternatives do not support a 7xxx card.

Is anyone else having problems??

I will Post separately for the individual difficulties.

Chao!, bogan.

---

### Post by grahammechanical on 2013-02-15
>  my grub has gone from messy and bad to almost totally corrupt - 69 Menu entries, some of them three lines long!!

That is because 12.04.2 still has Grub 1.99 and not Grub 2.0. We get that mess if we have multiple Ubuntus installed. The Grub menu entries are made up not only from kernels that os-prober finds but also from reading grub configuration files on the other installs. Hence the duplicate or triplicate entries.

It is better to have all the ubuntu running Grub 2.0. Much neater. Boot into a Ubuntu with Grub 2.0 and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

or the equivalent of sda in your case. You will see a neater menu next time.

Regards.

---

### Post by cariboo on 2013-02-15
You don't need to do a re-install, or even a dist-upgrade to get 12.04.2. If yu just do your normal updates, you'll eventually be running the LTS point release. 

I just did a normal update on my server, and After a reboot, I'm running the latest release:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
```

---

### Post by bogan on 2013-02-17
HI1, grahammechanical,

Thanks for the response. I had, of course, already run sudo grub-install /dev/sda to revert control to my main 12.10 installation. 
I had to do that as the 12.04.2 grub menu was virtually un-useable.

But I ran 'update-grub' after, not before the 'grub-install' - was that a mistake?

Are you suggesting that it is possible to install Grub 2 v2.00 in 12.04.2 with the 3.5 kernal?, instead of v1.99-2; which, i understand, is actually Grub2 as well, but without the Additional Options sub-menus.

@cariboo907,

I needed to do a clean install to clear out some problem; normal updates did not offer, or carry out the 3.5 kernal upgrade.

There is discussion in this thread, and elsewhere, pointing out that /etc/lsb-release had been pre- updated in preparation for the release of 12.04.2.

Two days before release my fully updated 12.04.1 still showed 3.2.0.37-generic-pae from 'uname -r', but 'cat /etc/lsb-release' already showed Precise 12.04.2 LTS, exactly as in your Post. 

Try:  'uname -ar'. May-be a 'dist-upgrade' would do it.

**Edit**: Currently, I get:>  :~$ uname -ar
Linux alan-MS-7616 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS" Chao!, bogan.

---

### Post by howefield on 2013-02-17
> **bogan said:**
> Two days before release my fully updated 12.04.1 still showed 3.2.0.37-generic-pae from 'uname -r', but 'cat /etc/lsb-release' already showed Precise 12.04.2 LTS, exactly as in your Post.

And two days after 12.04.2 was released you would still see the same results.

An updated 12.04 or 12.04.1 install will keep you on the 3.2 kernel.  

Therefore no surprise to see your results above.

You have to manually install the newer kernel, either by  installing the relevant packages via terminal/synaptic/whatever or performing a fresh install from 12.04.2 media, you won't get it automatically by updating a 12.04 or 12.04.1 machine.

---

### Post by mc4man on 2013-02-17
Just to note - 
On a fresh 12.04.2 **amd64** install, if wanting wine installed you must first manually install
libgl1-mesa-glx-lts-quantal:i386

Either thru apt or synaptic
```
sudo apt-get install libgl1-mesa-glx-lts-quantal:i386
```

After that should be ok but may still be preferrable to run a sim first, then install if no issues or removals shown

```
 sudo apt-get [COLOR="Red"]-s[/COLOR] install wine1.4
```

---

### Post by screaminj3sus on 2013-02-17
this is pretty ridiculous. there is no multiarch packages available for a lot of the lts quantal backported xorg packages. so if you install a 32 bit app like steam that needs these it tries to downgrade the whole system to the 12.04.1 versions. please tell me canonicol knows about this and will fix it...

to test just try installing ia32-libs-multiarch:i386 on a 12.04.2 machine, it will want to downgrade every single xorg package to the non backported ones. How could they release 12.04.2 with such a bad oversight?

EDIT: I think a lot of the problem with steam is valve's fault because it has outdated dependencies. If I do: sudo apt-get install libgl1-mesa-glx-lts-quantal:i386 like mc4man suggested for wine, steam will now install fine via USC. however when I launch steam it always pops up a terminal trying to install the old non quantal packages (but if I close this prompt steam launches and works fine). but the fact that installing stuff like ia32-libs-multiarch:i386 from the official repos tries to downgrade the graphics subsystem, and as bogan experienced installing the nvidia drivers from the repo trying to downgrade everything still seems like some cause for alarm on ubuntu's end.

---

### Post by bogan on 2013-02-17
Hi!, **screamingj3sus**,

+1 to that!

The same thing happened when I tried to install an nvidia driver from Synaptic, that was not offered by Additional Drivers.

It told me - luckily - that it would un-install all the linux 3.5 headers, images and backports, and a lot of  'lts' files !!

I did not see Xorg in the list, but it was so long I gave up.

Chao!, **bogan.**

---

### Post by Kow on 2013-02-17
Tip for you folks using 12.04 who will be manually updating to the 3.5 kernel:

Save yourself a lot of headaches by installing linux-headers-generic-lts-quantal BEFORE installing linux-image-generic-lts-quantal

DKMS needs the headers for the new kernel in order to attempt to build existing kernel modules against the new kernel. Personally, I think all linux kernel packages should depend on their respective headers package for this reason, but that's just me.

---

### Post by mc4man on 2013-02-17
> **screaminj3sus said:**
>  however when I launch steam it always pops up a terminal trying to install the old non quantal packages (but if I close this prompt steam launches and works fine). but the fact that installing stuff like ia32-libs-multiarch:i386 from the official repos tries to downgrade the graphics subsystem, and as bogan experienced installing the nvidia drivers from the repo trying to downgrade everything still seems like some cause for alarm on ubuntu's end.

I've checked thru the installer & extracted packages, doesn't seem to easy to get rid of that message/terminal popup. 
May be possible if one created appropiate files in .local/share/Steam/ubuntu12_32/steam-runtime/i386/installed for the 2 'so-called' missing or the 2 actual lts
(plus possibly editing some other files

Doesn't seem to affect running other that the nag terminal & better for steam to adjust their installer+package files for lts X if they are inclined.

As far as using nvidia drivers (preferred for steam), just tried the 3.10, seemed ok, will see what a reboot brings...

Edit: - no 'real' issue with the 3.10, nvidia-settings said wasn't running so put in a xorg.conf & all seems fine.
(- this setup needs a specific xorg.conf anyway to use nvidia drivers (need/want to disable powermizer on ac) so will remove the nvidia-xconfig created one which would certainly be overblown & replace with a simple one

---

