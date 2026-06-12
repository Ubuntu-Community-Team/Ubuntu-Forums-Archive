---
title: "Why are software packages in Ubuntu so OLD?"
date: 2015-11-23
forum: The Cafe
---

### Post by moma on 2015-11-23
Hello,
I need the latest HPLIP-driver for my printer. OK?,  but Ubuntu 15.10 has a very old HPLIP v3.15.7 package.
The latest version released by Hewlett Packard is 3.15.11 and we have to install it manually from a tar-ball. LOL ;-) 
[http://hplipopensource.com/hplip-web/install/install/](http://hplipopensource.com/hplip-web/install/install/)

$ **apt-cache  show hplip**
Package: hplip
Version: 3.15.7-0ubuntu4
--------------

Another example is the ImageMagick package.
Ubuntu provides version 6.8. 

$ **dpkg -s imagemagick** 
Package: imagemagick
Version: 6.8.9.9-5ubuntu2

Windows' users and Fedora/RedHat'ers run ImageMagick 6.9 and ImageMagick 7.0 (preview) with all their new tricks.  
--------------
[COLOR="#FF0000"]WHY[/COLOR]?

ps. Audio-recorder already runs on Ubuntu 16.04.  (just cleaning off my own doorstep first ;.)
[https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

---

### Post by QDR06VV9 on 2015-11-23
A Ubuntu release goes through several stages before it actually makes it to the public as a finished product:
Some time before Ubuntu launches a release it freezes its packages at a certain point.
Before a release is out but after the package freezing, work is done mostly to fix all the bugs and issues that there might be in those packages. New package versions are not imported into the repositories anymore after package or feature freezing.
Once the release happens additional changes to those packages only happen for bug fixing and security issues. There are no more upgrades done to the packages in the official repository even if new versions of the packages are released.
New version of packages are consistently being imported (from Debian) for the next release of Ubuntu, until the next freeze happens and the same process repeats itself.
Regards
And on Xenial for imagemagick 
> apt-cache policy imagemagickimagemagick:
  Installed: 8:6.8.9.9-6
  Candidate: 8:6.8.9.9-6
  Version table:
 *** 8:6.8.9.9-6 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial/main amd64 Packages
        100 /var/lib/dpkg/status



And for hplib
> apt-cache policy  hpliphplip:
  Installed: 3.15.7-0ubuntu5
  Candidate: 3.15.11-0ubuntu1
  Version table:
     3.15.11-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial/main amd64 Packages
 *** 3.15.7-0ubuntu5 0
        100 /var/lib/dpkg/status




---

### Post by moma on 2015-11-23
Ok, I understand, Debian is the mother of many applications.

Luckily Ubuntu-Phone and Unity 9 or 10 will run on the Mir display system and the most important apps are delivered by Snappy packages.
Debian stays in the old world of .deb packages while Ubuntu goes for Snappy and QT/QML/HTML5 apps. At least native Ubuntu apps are always up2date. 
I can see this on my E5 Aquaris Ubuntu Phone from BQ.  Ref: [http://goo.gl/MCRKYV](http://goo.gl/MCRKYV)  (no delays, well delivered)

Ubuntu cuts (partly) its umbilical-cord to Debian.  

Obrigado e boa noite,
  Moma, Portugal

---

### Post by buzzingrobot on 2015-11-23
HP releases Window driver updates for new printers because it's in the business of selling Windows printers.  Eventually, drivers are made available for FOSS systems. I'd guess HP has large institutional customers who use both Linux and HP printers.

Vendors releasing drivers for Windows have one target to build for.  Vendors releasing drivers for Linux have hundreds of distributions and several major mutually exclusive software packaging schemes to build for. In all of its ancient primitiveness, the compressed tar format is the only archive format a vendor can release that's digestible by every Linux distro. If they wanted to release actual RPM's, deb's, etc., for use by the packaging managers in distros, they'd need to create, release and support a different package for each different release of each specific Linux distribution they wanted to target. There's a good chance they'd have to chase kernel updates. That means increased expense to support a market that does not generate profit for them.  It's not going to happen.

---

### Post by ajgreeny on 2015-11-23
If you really want to have the most up-to-date versions of packages you will have to always run the most recent version of Ubuntu, but even then you will not keep up with the versions that are always available from the developers of software and which you could try to install from source code.

You can always search for PPA repos for specific packages such as LibreOffice for Ubuntu 14.04 which has LO-5.0.3 instead of LO-4.2.8.

Newer does not always mean better, however, in my opinion, so I am very happy to stick with 14.04 which is extremely stable and never lets me down.

---

### Post by 1clue on 2015-11-23
The process by which upstream packages find their way to the end user is part of what makes a distro unique.  Debian/Ubuntu do it as defined above.

As was previously mentioned, this process is there to help make the systems running the distro more stable.

Other distros do things differently:  You could try Arch, for example, which foregoes the entire process except for a few tiny packages.  In Arch, you download the source from the vendor and compile it yourself.

Gentoo is source-based, and they create a package descriptor for each package, change things a bit to allow easy modification by the end user, and then send it to mainstream users after the bug count is down below a certain threshold.

For most people who just want it to work, the Debian/Ubuntu method works pretty well.  If you need bleeding edge software then Arch is the way to go, at least if you have huge amounts of time on your hands to maintain your system(s).  Gentoo I find to be a happy medium.

That said, nothing stops you from compiling the latest in Ubuntu, except possibly massive dependencies being the wrong version.

I've never really understood the idea of brand loyalty in Linux. You don't pay for the distro, and you don't get anything tangible by sticking to a single brand.  I use the distro which most fits the purpose of the system I'm installing.  It makes life more interesting and makes it easier to do what you want with some specific box.  Of all my boxes, the majority use some *buntu or some Debian variant.  Then Gentoo and a few others come into play.

---

### Post by yetimon_64 on 2015-11-23
> **moma said:**
> Hello,
I need the latest HPLIP-driver for my printer. OK?...

From ...
1. [http://askubuntu.com/questions/10082/which-is-the-best-way-to-install-new-hplip-versions](http://askubuntu.com/questions/10082/which-is-the-best-way-to-install-new-hplip-versions)
check the first answer which mentions the hplip automatic installer.

and for the actual installer usage instructions check out ...
2. [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
this link says to download the 3.15.11 version and follow the walkthrough.

Hope this is of some help, good luck, yeti.

---

### Post by moma on 2015-11-24
Yes, the script worked fine on me and I can scan documents directly from my laptop. This did not work earlier. Printing did.
$ bash hplip-3.15.11.run 
 
Though, some other users struggle.
[https://bugs.launchpad.net/hplip/+bug/1517494](https://bugs.launchpad.net/hplip/+bug/1517494)

I think some packages, like drivers (HPLIP,...) and SDKs should have higher priority in Ubuntu.
For example, if HP says their tar-ball is good to go, then Ubuntu should not wait or test more.

HPLIP supports 2300 printers and all-in-one machines.
This involves a lot of users and businesses.

EDIT: Kudos @runrickus. HPLIP 3.15.11 is alaready in Ubuntu 16.04.

---

### Post by buzzingrobot on 2015-11-24
> **moma said:**
> 
...if HP says their tar-ball is good to go, then Ubuntu should not wait or test more.

.

A strictly small-time hobbyist distro might get away with that.  But, any organization -- like Canonical, Red Hat and Suse, to name three -- that is in the business of selling support for commercial and enterprise deployments of its distribution can't simply take HP's word.  It, not HP, is contractually obligated to stand behind the product it ships. Financial liability for costs a customer incurs as a result of software problems can also be involved. Why increase risk by shipping software you haven't tested?

As for Arch and other "rolling" releases:  Users receive new packages sooner because these distros push out upstream revisions as they happen after some minimal tests,  But, anyone who *needs* to use the very latest hardware really should stay with Windows or OS X.  Hardware vendors always ensure their new devices work on those systems from the day of release. They lack a reason to do that for Linux.

---

### Post by moma on 2015-11-24
No!, device-drivers (like HPLIP) are not ordinary software that can be tested by Canonical or other 3.part companies.

F.ex HPLIP can only be tested by Hewlett Packard or end-users (as a large group).
* HP has a big test-center with hundreds of printers. They can do all relevant testing.
* End-users as a large group can also test the HPLIP. You release an updated driver package to public and end-users will (after a while) report possible bugs.

Canonical, Debian or Ubuntu cannot test 2300 printers (but of course they can test the install-script itself).
The best thing they can do is to release new packages as soon as possible. 
**Every new, updated package has probably more bugfixes and improvements than the old one! **  
I have a proof: My scanner (on the HP-printer) worked after the update. Ergo, I am also a tester.

---

### Post by buzzingrobot on 2015-11-24
Of course HP drivers can be tested by others.  That's pretty much standard practice in the IT business:  Third-party code is tested before pushing it out to users, particularly if -- and because -- you don't have access to the source.  The *only* way to know how that new driver works on your hardware on your systems is to test it yourself.

And that's ignoring the fact that you, not HP, are held legally responsible for the software you provided your customers.

Why do you think buyers of Windows 10 Enterprise are exempt from the automatic updating Home and Pro feature? Precisely because they insist on testing updates prior to pushing them out on their networks. Microsoft would lose most of them as customers if it took that away.


Here's a small chunk from Red Hat's software agreement:

> 
Subject to the other terms in this Agreement, Red Hat will (i) defend Client against the Claim and (ii) pay costs, damages and/or attorneys fees that are included in a final judgment against Client (without right of appeal) or in a settlement approved by Red Hat that are attributable to Client's use of the Covered Software; and
If Client's use of Covered Software is found by a court to infringe Third Party Rights (or Red Hat believes that such a finding is likely), then Red Hat will, at its expense...


Red Hat, or Canonical, or Suse or anyone else in the business of selling and signing Linux support contracts is not going to release binary drivers from somewhere without at least some amount of in-house testing. 

If you want the latest drivers as soon as they are available, then pull them from the developer sites and install them yourself. Failing that, use a hobbyist distro like Arch, which has nothing to lose if its updates break your systems.

---

### Post by QDR06VV9 on 2015-11-24
> **buzzingrobot said:**
> Of course HP drivers can be tested by others.  That's pretty much standard practice in the IT business:  Third-party code is tested before pushing it out to users, particularly if -- and because -- you don't have access to the source.  The *only* way to know how that new driver works on your hardware on your systems is to test it yourself.

And that's ignoring the fact that you, not HP, are held legally responsible for the software you provided your customers.

Why do you think buyers of Windows 10 Enterprise are exempt from the automatic updating Home and Pro feature? Precisely because they insist on testing updates prior to pushing them out on their networks. Microsoft would lose most of them as customers if it took that away.


Here's a small chunk from Red Hat's software agreement:



Red Hat, or Canonical, or Suse or anyone else in the business of selling and signing Linux support contracts is not going to release binary drivers from somewhere without at least some amount of in-house testing. 

If you want the latest drivers as soon as they are available, then pull them from the developer sites and install them yourself. Failing that, use a hobbyist distro like Arch, which has nothing to lose if its updates break your systems.
+1 
Here on Arch hplip  3.15.9-2

---

### Post by monkeybrain20122 on 2015-11-24
> **ajgreeny said:**
> 
Newer does not always mean better, however, in my opinion, so I am very happy to stick with 14.04 which is extremely stable and never lets me down.

Newer is not always better, but usually it is. Even if you don't care for the new features, bug fixes would make new versions better ( upstream minor updates usually don't have new features, just bug fixes) 

On the other hand, it is too much that they package old versions of software that are not even supported upstream anymore, e.g With all the point releases for 14.04 and 12.04 LO is stuck at the versions when the OSes were first released, these versions had gone eol upstream long time ago. I use a lot of ppas for things that I want to keep up to date and also compile a few from source myself.  

I think ppa is one of the best feature of Ubuntu, it gives you the flexibility to get the latest for selected software and is easy to go back if experience regressions (ppa-purge) Debian does not have that flexibility and you are stuck with ancient software or risk breaking your system with Debian unstable and experimental (you can still compile of course) On the other hand Arch rolls the whole system and as far as I know there is no way to "go back"

---

### Post by mcduck on 2015-11-24
It's also worth remembering that Ubuntu does usually apply security & bug patches to the tested, stable version instead of upgrading to new version (which might bring other changes with it than just the security fixes).

For example, the hplip package mentioned in the first post... Notice the "-0ubuntu4"-part in the version number? 3.15.7-0ubuntu4 is not the same as 3.15.7 directly from HP, quite likely many of the fixes in the more recent version directly from HP have actually been patched to the Ubuntu package.

From the hplip package changelog (Check out the -0ubuntu3-version, which includes bug fix from 3.15.9.):
```
hplip (3.15.7-0ubuntu4) wily; urgency=low

  * debian/local/scripts/hp-plugin-ubuntu: Use pkexec instead of
    gksu (LP: #1496980).

 -- Till Kamppeter <till.kamppeter@gmail.com>  Thu, 17 Sep 2015 21:24:00 -0300

hplip (3.15.7-0ubuntu3) wily; urgency=low

  * debian/patches/common-definitions-h-fix.patch: Fixed hpcups crash,
    patch backported from HPLIP 3.15.9 (LP: #1475022, LP: #1476920,
    LP: #1480332, LP: #1483073).

 -- Till Kamppeter <till.kamppeter@gmail.com>  Tue, 15 Sep 2015 14:03:00 -0300

hplip (3.15.7-0ubuntu2) wily; urgency=low

  * debian/rules: Do not do the PPD file uncompression twice, especially
    do not uncompress the fax PPDs, as hp-setup accesses them directly
    instead of getting them through CUPS (LP: #1470300).
  * debian/rules: When patching the PPD files, remove the *.orig files so
    that they do not get shipped with the binary packages.

 -- Till Kamppeter <till.kamppeter@gmail.com>  Mon, 24 Aug 2015 22:33:00 -0300
```


As already mentioned here, after release Ubuntu gets updates for security reasons and to fix serious bugs, other than those two reasons any changes are avoided in favor of stable system. ("stable" as in "not changing" ;)). So anything that works correctly on Ubuntu version at the time of it's release, should work exactly the same way throughout the whole support time. While individual package sources like HP can test their own package and it's quality, they won't test it against every other package in Ubuntu so same promise of stable system wouldn't be possible. Not a big deal for home user, but for any larger company or organisation, not to even mention industrial use and more specific hardware, that level of stability can be really, really important as changing and updating systems can be expensive and difficult.

---

### Post by ajgreeny on 2015-11-24
And seeing as we are talking here a lot about hplip, I can tell you that the latest version 3.15.11 will not work properly with my (old but working perfectly) HP Deskjet F2180 MFP; it just errors out with a "Cartridge not latched" message and nothing I do stops that happening, making the HP Toolbox useless.

HPLIP 3.15.9 works perfectly, so this is definitely a case of newer (3.15.11) not being better for me!

---

### Post by nargaroth_reg on 2015-11-27
> **monkeybrain20122 said:**
> I think ppa is one of the best feature of Ubuntu, it gives you the flexibility to get the latest for selected software and is easy to go back if experience regressions (ppa-purge) Debian does not have that flexibility and you are stuck with ancient software or risk breaking your system with Debian unstable and experimental (you can still compile of course) On the other hand Arch rolls the whole system and as far as I know there is no way to "go back"
I agree, PPAs permit a very good balance between updates and stability, and the fact that they can be updated along with the official packages makes things even better.

---

### Post by buzzingrobot on 2015-11-28
PPA's do eliminate the hassle of building from source and dealing with dependencies. However, PPA's introduce the possibility that dependencies they require and install conflict with official packages from the repos.  This can cause breakage and failed updates with or without use of ppa-purge.

PPA packages are "you break it, you fix it" for good reason.  Users should at least visit a PPA's page on launchpad.net before installing from it, rather than simply copy-and-paste from some web site.

---

### Post by flocculant on 2015-11-28
>  Users should at least visit a PPA's page on launchpad.net before installing from it, rather than simply copy-and-paste from some web site. For sure. Might cut down on the fails people get because they can't be bothered to see if something in a ppa from 2012 is actually updated - forgive me for not holding my breath however ;)

---

### Post by stephen91 on 2015-11-28
:-)

---

### Post by monkeybrain20122 on 2015-11-30
> **flocculant said:**
> For sure. Might cut down on the fails people get because they can't be bothered to see if something in a ppa from 2012 is actually updated - forgive me for not holding my breath however ;)

And avoid large ppas that contain a lot packages, if you want foo better look for one just contains foo instead of a whole bunch of other stuffs you don't want/need to upgrade.

---

### Post by ChuangTzu on 2015-12-07
Usually printers and scanners will work fine with one of the generic drivers as well.  I use to install the Brother driver from their site, however, the Generic driver CUPS suggested works just as well.

---

