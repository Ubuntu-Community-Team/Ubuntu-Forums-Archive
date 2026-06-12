---
title: "Vivid Vervet Release Schedule, Partial Upgrades, and Common Questions"
date: 2014-10-23
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-10-23
This is where you will find the Vivid Vervet release schedule, as well as the answers to frequently asked questions.

[Release Schedule]("https://wiki.ubuntu.com/VividVervet/ReleaseSchedule")

If you are asked to do a partial upgrade, please read this first:

[Partial upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")

There always are many questions about what to do and how to do thngs during a release cycle:

[Common problems]("https://wiki.ubuntu.com/U%2B1/common-problems")

Warning: Unless you are willing to have a broken system, please make sure that that Pre-released updates are disabled in Software & Updates, as this repository is now used as a holding area while packages are waiting for dependencies to be built. See attached thumbnail.


If you are looking for the Daily iso's, have a look here:

[Ubuntu]("http://cdimage.ubuntu.com/daily-live/current/") 
[Kubuntu]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/") 
[Xubuntu]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/")
[Lubuntu]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/") 
[Ubuntu Gnome ]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/")
[Ubuntu Mate]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/")


As many of you may know we have created a U+1 testing team to do a better job of reporting bugs, and generally to make things better for all during the testing cycle. To that end, we have created a wiki where a lot of information regarding testing is available. You don't have to be a team member to be able to test , testing is open to everyone regardless of your experience level. That being said, to get the most possible feedback from your bug reports, check this out, before creating a bug report:

[Create a good bug report ]("https://help.ubuntu.com/community/ReportingBugs")

Here are some more useful links:

[Vivid Changes Mailing List ]("https://lists.ubuntu.com/mailman/listinfo/vivid-changes")

[Ubuntu Developers ]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel")

[Unity Design Discussion]("https://unity.ubuntu.com/getinvolved/")

---

### Post by ventrical on 2014-10-24
U+1 Testers Wiki:

[https://wiki.ubuntu.com/U%2B1/tester-wiki#preview](https://wiki.ubuntu.com/U%2B1/tester-wiki#preview)

U+1 Interim Tester Wiki:

[https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

---

### Post by ventrical on 2014-10-24
*note*

 If using /devel it will auto edit the Ubuntu.info file

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


```

---

### Post by zika on 2014-10-24
> **ventrical said:**
> *note*If using /devel it will auto edit the Ubuntu.info fileKind-of: will not: [http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760](http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760)

---

### Post by ventrical on 2014-10-24
> **zika said:**
> Kind-of: will not: [http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760](http://ubuntuforums.org/showthread.php?t=2249736&p=13150760#post13150760)

Yep .. I'm on it .. it's a strike.

Edit :No harm done. Just re-edit utopic/devel to devel/vivid and edit this way here:

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

The only thing it did was knock me off Main server and switch me over to Server for Canada.

Regards..

---

### Post by Cavsfan on 2014-10-25
Is there also going to be a Vivid Vervet Mate version?

Like this: [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

---

### Post by Cavsfan on 2014-10-25
Never mind I answered my own question :lol:.
It's on!

I just entered:

```
sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list

sudo apt-get update && sudo apt-get dist-upgrade
```

Got a ton of updates some of which were mate related. Think I'll just test out Vivid Vervet Mate and not both this go around. :p

---

### Post by cariboo on 2014-10-25
Mate hasn't received official status yet, so it isn't included in the list.

---

### Post by Cavsfan on 2014-10-27
> **cariboo907 said:**
> Mate hasn't received official status yet, so it isn't included in the list.

It sort of looks like it will be included. I hope so. :)

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy mate-themes
mate-themes:
  Installed: 1.9.1-1
  Candidate: 1.9.1-1
  Version table:
 *** 1.9.1-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ [COLOR=#ff0000]vivid[/COLOR]/universe amd64 Packages
        100 /var/lib/dpkg/status
```

```
cavsfan@cavsfan-MS-7529:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu Vivid Vervet (development branch)"
NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Vivid Vervet (development branch)"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

```

---

### Post by Cavsfan on 2014-10-29
@cariboo907
Would this not confirm that Vivid Mate is in the works?
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy mate-desktop-environment
mate-desktop-environment:
  Installed: 1.8.0+7
  Candidate: 1.8.0+7
  Version table:
 *** 1.8.0+7 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status

```

I'm getting tons of Mate updates in Vivid.

Or does this confirm that I'm wasting my time?

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep mate | grep ii | grep 1.8.0+7
ii  mate-desktop-environment                  1.8.0+7                                  all          MATE Desktop Environment ([COLOR=#ff0000]meta[/COLOR] package)
ii  mate-desktop-environment-core             1.8.0+7                                  all          MATE Desktop Environment (essential components, [COLOR=#ff0000]meta[/COLOR] package)
ii  mate-desktop-environment-extra            1.8.0+7                                  all          MATE Desktop Environment (extra components, [COLOR=#ff0000]dummy[/COLOR] package)
ii  mate-desktop-environment-extras           1.8.0+7                                  all          MATE Desktop Environment (extra components, [COLOR=#ff0000]meta[/COLOR] package)
```

Edit: added
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy mate-desktop
mate-desktop:
  Installed: 1.8.1+dfsg1-2
  Candidate: 1.8.1+dfsg1-2
  Version table:
 *** 1.8.1+dfsg1-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status
```

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep mate | grep ii | grep 1.8.1+dfsg1-2
ii  libmate-desktop-2-17:amd64                1.8.1+dfsg1-2                            amd64        Library with common API for various MATE modules (library)
ii  mate-desktop                              1.8.1+dfsg1-2                            amd64        Library with common API for various MATE modules
ii  mate-desktop-common                       1.8.1+dfsg1-2                            all          Library with common API for various MATE modules (common files)
ii  mate-terminal                             1.8.1+dfsg1-2                            amd64        MATE terminal emulator application
ii  mate-terminal-common                      1.8.1+dfsg1-2                            all          MATE terminal emulator application (common files)
```

Then again maybe not. :p

---

### Post by Cavsfan on 2014-10-29
This looks favorable: [http://ubuntuforums.org/showthread.php?t=2248632](http://ubuntuforums.org/showthread.php?t=2248632) :D

---

### Post by syntaxerror74 on 2014-11-13
Just jumping in with a question...

Is MATE intended to eventually become a direct competitor of Unity?

---

### Post by cariboo on 2014-11-13
I can't see why you would ask something like that, as the other derivatives aren't seen as direct competition for Unity. Mate is just another desktop environment option. As of yet it hasn't been made an official flavour.

---

### Post by syntaxerror74 on 2014-11-14
Excuse me, I was comparing apples to oranges. :shock::shock:

Unity is *NOT* a DE, even though I always thought it is one. It is officially regarded as *graphical shell*, not as DE. Maybe that's because I am on Lubuntu (@LXDE+Openbox) and I was always sure that this 'Unity' you (genuine) Ubuntu guys are always referring to *IS* the (resource-hogging) counterpart to "our" lightweight LXDE. But apparently I was totally on the wrong track... *crawls under a rock*

---

### Post by rburkartjo on 2014-12-07
cavs tks used the commands you posted in #7 and worked like a charm. upgraded a version of 14.10 i had on an usb stick

---

### Post by Cavsfan on 2014-12-08
> **rburkartjo said:**
> cavs tks used the commands you posted in #7 and worked like a charm. upgraded a version of 14.10 i had on an usb stick

Good deal. I've since installed Gnome from ISO over that install though.

---

### Post by Cavsfan on 2015-01-25
Mate 15.04 Alpha2 released [http://www.webupd8.org/2015/01/ubuntu-mate-1504-vivid-vervet-alpha-2.html](http://www.webupd8.org/2015/01/ubuntu-mate-1504-vivid-vervet-alpha-2.html)

Philinux posted this in the **Vivid Updates & News** thread.

I guess it just took them awhile.

---

### Post by Cavsfan on 2015-03-16
> **cariboo907 said:**
> Mate hasn't received official status yet, so it isn't included in the list.

Cariboo907, since Mate has officially been added to the Ubuntu flavors could you add the link for the download in the first post?

It would be nice since all the other flavors are there.

Thank you kindly! :)

---

### Post by cariboo on 2015-03-16
> **Cavsfan said:**
> Cariboo907, since Mate has officially been added to the Ubuntu flavors could you add the link for the download in the first post?

It would be nice since all the other flavors are there.

Thank you kindly! :)

Done

---

### Post by Cavsfan on 2015-03-17
> **Cavsfan said:**
> Cariboo907, since Mate has officially been added to the Ubuntu flavors could you add the link for the download in the first post?

It would be nice since all the other flavors are there.

Thank you kindly! :)

> **cariboo907 said:**
> Done

Sweet! Now we have a central place for every one of the flavors. :)

---

### Post by Cavsfan on 2015-03-26
Is today's ISO supposed to be the "beta2" official ISO?

Just curious as this is the date the release schedule said it would be released on. But I don't see beta2.

EDIT: I don't believe it is released yet. That is what google told me. :p

---

### Post by Elfy on 2015-03-26
> **Cavsfan said:**
> Is today's ISO supposed to be the "beta2" official ISO?

Just curious as this is the date the release schedule said it would be released on. But I don't see beta2.

EDIT: I don't believe it is released yet. That is what google told me. :p

Just as the Final Releases when it releases - so do milestones.

Nothing has been released yet. People are still doing final testing. 

The person running this Beta is US time - they'll publish once they are ready to do so.

---

### Post by Cavsfan on 2015-03-26
> **Elfy said:**
> Just as the Final Releases when it releases - so do milestones.

Nothing has been released yet. People are still doing final testing. 

The person running this Beta is US time - they'll publish once they are ready to do so.

OK thanks for the update. I plan on updating much of the Linux systems I have while reducing the number of them.
Too many updates and I wanted to install the beta2. But, there's always plenty of time.

---

### Post by kansasnoob on 2015-03-26
> **Cavsfan said:**
> OK thanks for the update. I plan on updating much of the Linux systems I have while reducing the number of them.
Too many updates and I wanted to install the beta2. But, there's always plenty of time.

Be sure and read the release announcement:

[https://lists.ubuntu.com/archives/ubuntu-announce/2015-March/000194.html](https://lists.ubuntu.com/archives/ubuntu-announce/2015-March/000194.html)

I'm personally very disappointed that they decided to release with the [first of those two nasty bugs]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1436715") mentioned therein:

> 1) After installation is complete, clicking the "reboot now" button
     will eject your installation medium but then fail to reboot.  The
     simple workaround for this is to manually turn off or reset your
     computer and then boot into the freshly installed system.

IMHO hard resets are simply too rough on hardware to even fiddle with a known borked iso :sad:

---

### Post by sudodus on 2015-03-27
It was long ago that a beta 2 version was released with so many red bugs decorating the testing tracker (looking at standard Ubuntu as well as the community flavours).

By the way, are the beta2 versions of the community flavours released yet?

---

### Post by Elfy on 2015-03-27
Did you read the release announcement?

---

### Post by sudodus on 2015-03-27
Yes

*Edit*: So versions, that do not even boot are released?

---

### Post by Elfy on 2015-03-27
> **sudodus said:**
> Yes

*Edit*: So versions, that do not even boot are released?

Why do you ask if community have released then? The links to the community releases are on the announcement.

Yes - -release made the decision to release with that bug.

---

### Post by sudodus on 2015-03-27
I ask because the Lubuntu mailing lists are silent about it.

---

### Post by Elfy on 2015-03-27
> **kansasnoob said:**
> Be sure and read the release announcement:

[https://lists.ubuntu.com/archives/ubuntu-announce/2015-March/000194.html](https://lists.ubuntu.com/archives/ubuntu-announce/2015-March/000194.html)

I'm personally very disappointed that they decided to release with the [first of those two nasty bugs]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1436715") mentioned therein:



IMHO hard resets are simply too rough on hardware to even fiddle with a known borked iso :sad:
You've never had to reisub or reboot at wall?

---

### Post by kansasnoob on 2015-03-27
> **Elfy said:**
> You've never had to reisub or reboot at wall?

AFAIK reisub has not worked for quite some time - I think that was a kernel team decision :-s

By "reboot at wall" I'm not sure what you mean - a hard reset? That's exactly what I wrote in the bug report when I filed it. But hitting the reset button or "pulling the plug" is not something I care to do because it's incredibly rough on hardware, so I just won't use the Beta 2 images. I'll either use earlier images or wait until that bug is fixed.

As a dedicated Ubuntu GNOME iso-tester I refused to continue testing these images, and if it had been up to me the Ubuntu GNOME release notes would say something like, "The Vivid Beta 2 images are too buggy for most users to even consider using, please just use the Beta 1 images and update from them".

---

### Post by sudodus on 2015-03-27
***SysRq R E I S U B*** works for me in Lubuntu Vivid (in most cases, but not always).

I agree that people should be warned like you suggest kansasnoob. But some beta 2 iso files are OK, for example the Lubuntu alternate iso files (that I have iso-tested).

---

### Post by Elfy on 2015-03-27
> **sudodus said:**
> [I][B]...

I agree that people should be warned like you suggest kansasnoob. But some beta 2 iso files are OK, for example the Lubuntu alternate iso files (that I have iso-tested).

That's down to people's release notes - the Xubuntu one should have something on it when we publish.

---

### Post by Cavsfan on 2015-03-28
I use Alt+SysRq(Prt Scr) while pressing r e i s u b one key at a time and that has never failed to reboot on any linux system to date.

Just my 2 cent...

---

