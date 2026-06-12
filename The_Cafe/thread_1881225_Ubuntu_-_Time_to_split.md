---
title: "Ubuntu - Time to split?"
date: 2011-11-15
forum: The Cafe
---

### Post by dawynn on 2011-11-15
I've seen a game that I was mildly interested in (KQ) disappear (intrepid) and reappear (lucid) and then disappear (natty) again.  Today, as I thought about this, I wondered, why are games even in the Ubuntu repositories?

Please review the following sites and consider their potential:
[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)
[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)
[http://medibuntu.org/](http://medibuntu.org/)

The more I think about it, the more I realize that games and the vast majority of applications found in the main Ubuntu repositories have nothing to do with the operating system itself.  Many of these applications and games have code that could be compiled to work just as well with any given supported release of Ubuntu.

I'm thinking that Canonical and the Ubuntu development team should focus strictly on the operating system.  Give us the kernel, and desktop(s) on top of it.  Make sure the functionality works.  Make sure that graphics cards fully work -- that 3D works for gaming and other purposes.  Make sure that network connectivity works.  Make sure that sound works.  Essentially, if its part of the workability of the computer, or part of the lsb definition of what comprises linux, then keep it in the Ubuntu repositories.

But then support playdeb, getdeb and medibuntu.  Making sure that sound comes out of the speakers (pulse, alsa, oss functionality)?  That's basic Ubuntu stuff.  Making sure that I have codecs for every sound format (mp3, ogg, etc), push that off to medibuntu.  Making sure I can connect to the web (wicd, network-connect)?  That's Ubuntu.  Firefox and the plethora of other web browsers?  Push that off to getdeb.  And games?  I can't think of a single game that should really be considered part of an operating system.  Push all games to playdeb, amusements either to playdeb or getdeb.

Maybe then we could have a concentrated focus on making sure that the operating systems themselves work and work well.  And maybe we could see more desktops supported.  Focus on the features of each desktop.  Yes, make KDE and Gnome full-featured.  But keep Xubuntu and Lubuntu lightweight.  Perhaps build desktops for fluxbox and icewm, and ... (sorry if I'm forgetting a few other favorites).

---

### Post by nothingspecial on 2011-11-15
Not a support question.

Moved to the Cafe.

---

### Post by jjex22 on 2011-11-15
JWM? puppy I know but I do like it!

I personally love the massive repo's to be honest; it is a factor that runs through my head every time I test out a new distro and think... maybe! when I first got linux and ran apt-get install I fell in love... when I first ran 

cd /path
tar zxf file.tar.gz
cd /path
ls
cd /path
ls
./configure
make
make install

I celebrated the construction of my time machine... and even now my heart always sinks a bit when I see .tar.gz I know those comments will drive some mad... but it's true for me I am a lazy desktop user most of the time and I do check the app store -sorry software centre- on a regular basis.

---

### Post by Tibuda on 2011-11-15
They should have a different repository for applications and for the core OS (kernel, glib, the desktop environment, etc). The app repos should be rolling release, and the core repos may use a longer release cycle. It was always weird to update the whole ing OS to have the latest Firefox or OpenOffice.

---

### Post by BrokenKingpin on 2011-11-15
I think they are doing a fine job of managing the repos... everything I need is in there. Sure, playdeb has more games, but 95% of it is crap, and the other 5% is managed just fine in the Ubuntu repos. I also trust the Ubuntu repos far more than playdeb.

As for getdeb, well that is even more useless than playdeb, as pretty much every popular app is already in the Ubuntu repos, and if it is not the application developer probably provides a ppa anyways.

Both playdeb and getdeb are still dependent on the version of Ubuntu you are running, so you still see apps available for one version and not the other (even more so than the Ubuntu repos). 

I really cannot understand your reasoning at all. The ubuntu repos are huge and are very well maintained (unlike playdeb/getdeb). There is no reason to question the entire repo system because one games hasn't been well maintained.

The huge repos is why I use Linux in the first place.... thousands of apps ready to install from a trusted source.

---

### Post by thatguruguy on 2011-11-15
> **Tibuda said:**
> They should have a different repository for applications and for the core OS (kernel, glib, the desktop environment, etc). The app repos should be rolling release, and the core repos may use a longer release cycle. It was always weird to update the whole ing OS to have the latest Firefox or OpenOffice.

The "whole -ing OS" no longer has to be updated in order to have the latest Firefox, since it has been repeated *ad nauseum* on here that from 11.10 onwards, Firefox will be updated in the normal Ubuntu repository as soon as it has been security tested and shown compatible.

However, the latest issue with Firefox demonstrates why your idea is a bad one.  Shortly after Firefox 8.0 was released in the wild, and during the period of time that security and integration testing was being done on it so that it could be put into the regular Ubuntu repository, it turned out that there is a security hole in 8.0.  The Mozilla team is working on the issue, and will soon be releasing 8.0.1.  Once that one is released, it will be tested, and barring any significant problems, put into the regular Ubuntu repository so that all users of 11.10 will have it.  Now imagine if that had to be done with each and every package in the repository for each currently-supported version of Ubuntu.

As it is currently, there is a set cutoff for packages to be included in any release of Ubuntu, and that cutoff exists so that there is time to do the requisite testing of the packages to ensure, to the extent possible, that the packages work as they should with the version of Ubuntu to be released.  There just isn't enough manpower at Canonical to test each update to each package to ensure compatibility with each supported release of Ubuntu.  That's why the ppa system exists, so that third-party package maintainers can do the necessary testing.

---

### Post by dawynn on 2011-11-15
thatguruguy: I thank you for your courtesy, but have to admit that you've confused me.  You indicate that we will no longer need to upgrade the "whole -ing OS" in order to upgrade Firefox / LibreOffice / {{my favorite app}}.  That instead, as new releases of the apps are tested they will be released in the supported releases, but then back off and indicate that there's not enough manpower at Canonical to test all applications for each currently supported release.  If they won't be testing and releasing the latest versions to each currently supported OS, then yes, I still need to upgrade the "whole -ing OS" in order to upgrade Firefox / LibreOffice / {{my favorite app}}.  Although, to be honest, that puts us right on par with Mac and Win.  Can't really install the latest versions of certain apps if your OS is a few generations behind.  So, definitely no advantage to the Penguin on this point.

BrokenKingpin: I realize that GetDeb and PlayDeb are not what they should be.  That's why I indicated -- imagine the *potential*.  I'm honestly surprised by PlayDeb -- that they've made very very little effort to start including games.  But they indicate that they could use support funds.  My thought was that, if Ubuntu could focus on providing the OS, then that could free up resources that could be moved to building PlayDeb and GetDeb.

And if Canonical is doing so well at managing the repos, then help me understand why Xubuntu, supposedly a "light" -buntu, consistently clocks in as more resource hungry than Ubuntu itself?  Why have we just with Oneiric made available a supported lightweight -buntu again (thanks, Lubuntu!)?  Why is there an OpenGeu project, instead some kind of Enlightenment based -buntu?  Why a need for Linux Mint, which should just be {{Name your favorite -buntu flavor}} + Medibuntu?

I'd personally prefer to see Canonical focus on providing properly built OS's, and have separate repositories that would provide the apps and games (I believe, if Ubuntu doesn't provide them, then a GetDeb, PlayDeb, or some other resource would rise to meet the need), then to see a mish-mash of some good, some poorly built -buntu's and child projects all over the place trying to fill in the gaps that the -buntu's are leaving behind.

---

### Post by snowpine on 2011-11-15
Ah yes, the old "Feature X should be dropped from the project because I don't personally see the need for it" argument.

I think you need an Ubuntu history lesson. 99% of the apps in the Ubuntu repositories are there because somebody volunteered their time to package that app for Debian. Ubuntu simply "borrows" the Debian repos. It would actually be a lot more work to go through those repos and selectively remove packages that are "unnecessary for the core Ubuntu system" than to simply continue to provide them all.

Ubuntu could not exist without the Linux kernel, GNU, Xorg and video drivers, Gnome/KDE/Xfce, Debian repos, and lots of other free software projects. Canonical is first and foremost a synthesizer and packager of existing GNU/Linux software. If Canonical were to limit the Ubuntu repos to only those apps that are Ubuntu-specific, we'd have Unity, the Software Center, and not much else.

---

### Post by drawkcab on 2011-11-15
> **dawynn said:**
> The more I think about it, the more I realize that games and the vast majority of applications found in the main Ubuntu repositories have nothing to do with the operating system itself.  Many of these applications and games have code that could be compiled to work just as well with any given supported release of Ubuntu.

I'm thinking that Canonical and the Ubuntu development team should focus strictly on the operating system

[...]

Maybe then we could have a concentrated focus on making sure that the operating systems themselves work and work well.

I just want to point out that you're saying two logically incompatible things:

On the one hand you're saying that Ubuntu spends too much time packaging apps--especially games--and is therefore distracted in some way from improving the essential elements of the operating system.

On the other hand, you've prefaced this complaint with the observation that it doesn't look as if packaging the apps requires a lot of resources in the first place.  

What exactly are you saying?

---

### Post by thatguruguy on 2011-11-15
> **dawynn said:**
> thatguruguy: I thank you for your courtesy, but have to admit that you've confused me.  You indicate that we will no longer need to upgrade the "whole -ing OS" in order to upgrade Firefox / LibreOffice / {{my favorite app}}.  That instead, as new releases of the apps are tested they will be released in the supported releases, but then back off and indicate that there's not enough manpower at Canonical to test all applications for each currently supported release.  If they won't be testing and releasing the latest versions to each currently supported OS, then yes, I still need to upgrade the "whole -ing OS" in order to upgrade Firefox / LibreOffice / {{my favorite app}}.  Although, to be honest, that puts us right on par with Mac and Win.  Can't really install the latest versions of certain apps if your OS is a few generations behind.  So, definitely no advantage to the Penguin on this point.


No, I stated that you don't need to upgrade the entire OS to get the latest Firefox, since Firefox will now be updated in the regular Ubuntu repository.  Just like you get normal updates when security fixes come out for packages in the default installation, as long as you're using a supported version of Ubuntu.  As to other packages, you can install ppas.

If your OS is "a few generations behind" (for instance, more than 3 years old for an LTS or more than 18 months for a non-LTS), you do, indeed need to update the whole OS.

Incidentally, starting with 12.04, the LTS will be supported for 5 years.

Not to be rude, but I probably won't respond to any other points you attempt to make, because I have a hard time understanding what you're trying to convey.

---

### Post by dawynn on 2011-11-15
Yes, I got far more ranty than I should have.  And an apology now can't cover enough.

Guess I was just going through a build-up of frustration.  Please let this thread die.

---

