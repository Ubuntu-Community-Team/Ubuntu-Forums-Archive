---
title: "Precise Changes / Updates - Please Create a discussion thread in the forum if needed"
date: 2011-10-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2011-10-14
Please only post in this tread with genuine 12.04 changes and updates.

**[COLOR="Red"]Please Create a discussion thread in the forum if needed.[/COLOR] Cheers**

Mail just in.

>  Precise is now open for development, with syncs from testing starting shortly. The development version starts with an

- an updated GCC (4.6.x, Linaro 2011-10) and binutils (2.22 branch), - gnat-4.6 as the default gnat, - python2.6 dropped from the list of supported python 2.x versions, - merged dpkg, debhelper and cdbs, - the swig version updated from 1.3 to 2.0, - jpeg8 as the default jpeg version.

In preparation for the LTS, syncs will run from the Debian testing distribution. If you require a sync request from unstable, please file a sync request (or sync on your own).

Please do avoid syncing libraries changing the soname from unstable or experimental. These may still show build failures in dependent packages, which are not yet fixed in Debian experimental or unstable. Wait until these can be synced/merged from testing.

When merging or requesting a sync, please look at the list of known build failures ([1] and [2]); bugs (tagged `ftbfs') are filed for every packages which fails to build from source. Please close these with the merged uploads.

Please check your uploads in a precise chroot, don't just test in an oneiric environment. See [3] how to setup such a development chroot.

[1] [http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20110816-oneiric.html](http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20110816-oneiric.html) [2] [http://qa.ubuntuwire.com/ftbfs/](http://qa.ubuntuwire.com/ftbfs/)[3] [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

--ubuntu-devel-announce mailing list [email]ubuntu-devel-announce@lists.ubuntu.com[/email] [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

--ubuntu-devel-announce mailing list [email]ubuntu-devel-announce@lists.ubuntu.com[/email] [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

---

### Post by cariboo on 2011-10-14
You can sign up for the pangolin changes mailing list here:

[https://lists.ubuntu.com/mailman/listinfo/Precise-changes](https://lists.ubuntu.com/mailman/listinfo/Precise-changes)

---

### Post by cariboo on 2011-10-14
This just in:

> On Fri, Oct 14, 2011 at 05:34:00PM +0200, Matthias Klose wrote:
> Precise is now open for development, with syncs from testing starting shortly.
Unfortunately the autosyncer is currently broken:

  [https://bugs.launchpad.net/launchpad/+bug/874377](https://bugs.launchpad.net/launchpad/+bug/874377)

I expect we'll get this resolved early next week (I'm not going to do a
late Friday evening at the end of release week!) and we can start
autosyncs then.  Please be patient in the meantime.  If there's anything
particularly urgent to your own work then you can of course sync it
manually using Oneiric's version of syncpackage, but there should be no
harm in most bulk syncs just waiting until next week.

-- Colin Watson

---

### Post by ubudog on 2011-10-20
Hmm... small hickup.  We'll get past it.

Nice to see we're rollin.  :)

---

### Post by philinux on 2011-11-05
UDS shortlist for precise.

[http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html](http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html)

---

### Post by viperdvman on 2011-11-06
It's nice that they're ditching the 700MB limit, especially with Unity taking up so much space. At least the devs will have some breathing room now.

If they do make LightDM somewhat customizable, that'll be a huge plus. My 11.04's GDM has a custom wallpaper on it, so I'd like to be able to do that with LightDM too. But it looks like **all** the official Ubuntu derivatives are gonna be switching over to LightDM. If not now, then eventually. I do like how easy it is to use, though :) I just hope it looks good for Kubuntu with the extra plasma themes *(note, I've never used KDM since my playing with Kubuntu was always a live session, and I use GDM for my Ubuntu, and Fedora doesn't use KDM)*

I also like the proposed improvements to the Ubuntu Software Center, especially checking to have an installed app added to the Unity launcher.

However, it does suck that GNOME Sushi won't be included by default. I wonder why it got rejected? A lot of us here use it. I do, however, think it's good that **low fat settings** will be enabled by default in Kubuntu, just so most any computer can install and run it out of the box. As long as there's an easy way to turn off the **low fat settings**, I think it's a great change and a great way to make Kubuntu that much more accessible.

I like much of what I see so far. I'll definitely be keeping my eyes open on this future release... more so than with Oneric.

---

### Post by thatguruguy on 2011-11-06
> **viperdvman said:**
> 
However, it does suck that GNOME Sushi won't be included by default. I wonder why it got rejected?

One reason is because it won't accept themes, and the close button is hard-coded to be on the right-hand side. It'll still be available in the repos, just not in the default install.

---

### Post by effenberg0x0 on 2011-11-07
> **viperdvman said:**
> It's nice that they're ditching the 700MB limit, especially with Unity taking up so much space. At least the devs will have some breathing room now.

If they do make LightDM somewhat customizable, that'll be a huge plus. My 11.04's GDM has a custom wallpaper on it, so I'd like to be able to do that with LightDM too. But it looks like **all** the official Ubuntu derivatives are gonna be switching over to LightDM. If not now, then eventually. I do like how easy it is to use, though :) I just hope it looks good for Kubuntu with the extra plasma themes *(note, I've never used KDM since my playing with Kubuntu was always a live session, and I use GDM for my Ubuntu, and Fedora doesn't use KDM)*

I also like the proposed improvements to the Ubuntu Software Center, especially checking to have an installed app added to the Unity launcher.

However, it does suck that GNOME Sushi won't be included by default. I wonder why it got rejected? A lot of us here use it. I do, however, think it's good that **low fat settings** will be enabled by default in Kubuntu, just so most any computer can install and run it out of the box. As long as there's an easy way to turn off the **low fat settings**, I think it's a great change and a great way to make Kubuntu that much more accessible.

I like much of what I see so far. I'll definitely be keeping my eyes open on this future release... more so than with Oneric.

You can download Simple Lightdm Manager and change lightdm background. Lightdm greeters are made to be very configurable, even through a webkit. See this example of greeter: [http://www.youtube.com/watch?v=f8nm4NpaVXE](http://www.youtube.com/watch?v=f8nm4NpaVXE)

EDIT: [https://launchpad.net/crowd-greeter](https://launchpad.net/crowd-greeter)

---

### Post by Harry33 on 2011-11-07
> **effenberg0x0 said:**
> You can download Simple Lightdm Manager and change lightdm background. Lightdm greeters are made to be very configurable, even through a webkit. See this example of greeter: [http://www.youtube.com/watch?v=f8nm4NpaVXE](http://www.youtube.com/watch?v=f8nm4NpaVXE)

EDIT: [https://launchpad.net/crowd-greeter](https://launchpad.net/crowd-greeter)

LightDM background can be changed simply by copying a preferred image (png) file into
/usr/share/backgrounds/
and using the same name: warty-final-ubuntu.png

or

by changing appropriate configuration from the file
/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf

---

### Post by philinux on 2011-11-07
It would be beneficial to keep this thread focused on the changes that will appear in precise rather than a discussion thread. Cheers.

---

### Post by philinux on 2011-11-17
[http://fridge.ubuntu.com/2011/11/17/12-04-ubuntu-developer-summit-proceedings/](http://fridge.ubuntu.com/2011/11/17/12-04-ubuntu-developer-summit-proceedings/)

---

### Post by philinux on 2011-11-24
[http://www.piware.de/2011/11/apport-1-90-client-side-duplicate-checking/](http://www.piware.de/2011/11/apport-1-90-client-side-duplicate-checking/)

 > Hello fellow developers,

I just released Apport 1.90 and uploaded it into Precise. This version introduces client-side duplicate checking.

So from now, when you report a crash, you are likely to see &#8220;We already know about this&#8221; right away, without having to upload or type anything, and you will get directed to the bug page.

If you get this, please mark yourself as affected and/or subscribe to the bug, both to get a notification when it gets fixed, and also to properly raise the &#8220;hotness&#8221; of the bug to bubble up to developer attention.

Please let me know at once if you see this system acting up and being wrong. This is still a fairly new and not much tested approach, so there might be cases where the new way of duplicate detection goes wrong.

This also means that from now on it should not be necessary to write manual bug patterns for crashes. We still need bug patterns for common package installation failure situations, or in general any bug which is not a crash which we can identify from log files, etc.

If you are interested in some background and technical details, please see the longer version of this announcemnt [1].

Thanks,

Martin

---

### Post by philinux on 2011-11-26
Thanks to Harry33. Default apps changes.
 [https://launchpad.net/ubuntu/precise/+source/ubuntu-meta/1.251](https://launchpad.net/ubuntu/precise/+source/ubuntu-meta/1.251)

---

### Post by philinux on 2011-12-01
"To photograph is to hold one's breath, when all faculties converge to capture fleeting reality. It's at that precise moment that mastering an image becomes a great physical and intellectual joy." - Henri Cartier-Bresson

We are pleased to bring you the first set of developer images that capture the current fleeting reality of our Precise Pangolin (Ubuntu 12.04 Alpha 1) as it starts to emerge.

Pre-releases of Precise Pangolin are *not* encouraged for anyone needing a stable system or anyone who is not comfortable running into occasional, even frequent breakage. They are, however, recommended for Ubuntu developers and those who want to help in testing, reporting, and fixing bugs as we work towards getting this LTS release ready.

Alpha 1 is the first in a series of milestone CD images that will be released throughout the Precise development cycle. The Alpha images are known to be reasonably free of showstopper CD build or installer bugs, while representing a very recent snapshot of Precise. You can download them here:

[Ubuntu Desktop, Server, ARM]("http://cdimage.ubuntu.com/releases/precise/alpha-1/")

Additional images are also available at:

[Ubuntu Server Cloud and EC2]("http://uec-images.ubuntu.com/releases/precise/alpha-1/")
[Xubuntu]("http://cdimage.ubuntu.com/xubuntu/releases/precise/alpha-1/")
[Edubuntu]("http://cdimage.ubuntu.com/edubuntu/releases/precise/alpha-1/")
[Lubuntu]("http://cdimage.ubuntu.com/lubuntu/releases/precise/alpha-1/")

Alpha 1 includes a number of software updates that are ready for wider testing. This is quite an early set of images, so you should expect some bugs. For a more detailed description of the changes in the Alpha 1 release and the known bugs (which can save you the effort of reporting a duplicate bug, or help you find proven workarounds), please see:

[http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)

If you're interested in following the changes as we further develop Precise, we suggest that you subscribe initially to the ubuntu-devel-announce list. This is a low-traffic list (a few posts a week) carrying announcements of approved specifications, policy changes, alpha releases, and other interesting events.

[http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

Enjoy,

--Kate Stewart, on behalf of the Ubuntu release team

--ubuntu-devel-announce mailing list [email]ubuntu-devel-announce@lists.ubuntu.com[/email] [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

---

### Post by philinux on 2011-12-11
[http://www.omgubuntu.co.uk/2011/12/unity-tweak-tool-myunity-gets-new-look-coming-to-ubuntu-software-centre/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2011/12/unity-tweak-tool-myunity-gets-new-look-coming-to-ubuntu-software-centre/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2011-12-11
[http://www.omgubuntu.co.uk/2011/12/unity-shortcut-overlay-coming-to-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2011/12/unity-shortcut-overlay-coming-to-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2011-12-14
[https://wiki.ubuntu.com/X/Blueprints/LtsPointUpdatesForXorg](https://wiki.ubuntu.com/X/Blueprints/LtsPointUpdatesForXorg)

From [http://ubuntuforums.org/showpost.php?p=11536813&postcount=13](http://ubuntuforums.org/showpost.php?p=11536813&postcount=13)

---

### Post by philinux on 2011-12-22
From omgubuntu.

 [http://www.omgubuntu.co.uk/2011/12/ubuntu-12-04-development-update-9/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2011/12/ubuntu-12-04-development-update-9/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-01-10
[http://www.omgubuntu.co.uk/2012/01/kubuntu-xubuntu-12-04-become-long-term-support-releases/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/01/kubuntu-xubuntu-12-04-become-long-term-support-releases/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-01-19
Update 10.

 [http://www.omgubuntu.co.uk/2012/01/ubuntu-12-04-development-update-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/01/ubuntu-12-04-development-update-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-01-19
[http://www.omgubuntu.co.uk/2012/01/unity-dash-to-ditch-giant-shortcuts/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/01/unity-dash-to-ditch-giant-shortcuts/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-01-25
[http://www.omgubuntu.co.uk/2012/01/hud-new-unity-feature/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/01/hud-new-unity-feature/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-01-26
[http://www.omgubuntu.co.uk/2012/01/ubuntu-12-04-development-update-11/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/01/ubuntu-12-04-development-update-11/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-02-01
[http://www.webupd8.org/2012/02/gnome-components-version-clarifications.html](http://www.webupd8.org/2012/02/gnome-components-version-clarifications.html)

 [http://www.omgubuntu.co.uk/2012/02/developer-week-summary-day-1-outlook-day-2/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/developer-week-summary-day-1-outlook-day-2/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-02-02
Update 12.

[http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-development-update-12/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-development-update-12/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-02-02
It's getting better.

 [http://www.webupd8.org/2012/02/ubuntu-1204-lts-precise-pangolin-alpha.html](http://www.webupd8.org/2012/02/ubuntu-1204-lts-precise-pangolin-alpha.html)

---

### Post by philinux on 2012-02-04
5.2 lands on precise. Overview here.

[http://www.omgubuntu.co.uk/2012/02/unity-5-2-lands-in-precise-brings-numerous-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/unity-5-2-lands-in-precise-brings-numerous-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by VMC on 2012-02-04
> **philinux said:**
> 5.2 lands on precise. Overview here.

[http://www.omgubuntu.co.uk/2012/02/unity-5-2-lands-in-precise-brings-numerous-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/unity-5-2-lands-in-precise-brings-numerous-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Wow, some great changes. I don't know what's come over me, but I'm starting to like Unity. Maybe the case of beer helped :;

---

### Post by ubuntu27 on 2012-02-05
[Ubuntu 12.04 LTS receives new minor but relevant polish]("http://iloveubuntu.net/ubuntu-1204-lts-receives-new-minor-relevant-polish")


[Unity 5.2 released with new home view, shortcut overlay, middle-click pasting and more]("http://iloveubuntu.net/unity-52-released-new-home-view-shortcut-overlay-middle-click-pasting-and-more")

---

### Post by philinux on 2012-02-07
[http://design.canonical.com/2012/02/ubuntu-sound-theme-design/](http://design.canonical.com/2012/02/ubuntu-sound-theme-design/)

---

### Post by philinux on 2012-02-09
[http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-development-update-13/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-development-update-13/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Plus no more dodge windows and global menus might be optional.

 [http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

---

### Post by philinux on 2012-02-10
[With full support for 12.04]("http://www.webupd8.org/2012/02/ubuntu-tweak-061-released-with-support.html")

---

### Post by philinux on 2012-02-12
[http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html](http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html)

---

### Post by philinux on 2012-02-13
[http://www.webupd8.org/2012/02/unity-dash-to-get-cover-flow-support.html](http://www.webupd8.org/2012/02/unity-dash-to-get-cover-flow-support.html)

Includes video demo.

---

### Post by philinux on 2012-02-15
[http://www.omgubuntu.co.uk/2012/02/a-handful-of-minor-ubuntu-12-04-updates/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/a-handful-of-minor-ubuntu-12-04-updates/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-02-16
Feature freeze is almost here.

 [http://www.omgubuntu.co.uk/2012/02/51736/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/51736/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-02-16
Coming soon. !!

[http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-adds-new-video-lens-for-finding-movies-tv-shows-online/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-adds-new-video-lens-for-finding-movies-tv-shows-online/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-02-17
[http://www.omgubuntu.co.uk/2012/02/unity-5-4-lands-in-precise-brings-hud-video-lens-minor-ui-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/02/unity-5-4-lands-in-precise-brings-hud-video-lens-minor-ui-changes/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

[HUD video]("http://www.omgubuntu.co.uk/2012/01/hud-new-unity-feature/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29")

[sabdfl's article on HUD]("http://www.markshuttleworth.com/archives/939")

---

### Post by philinux on 2012-02-23
[http://www.webupd8.org/2012/02/ubuntu-one-gets-new-qt-interface-for.html](http://www.webupd8.org/2012/02/ubuntu-one-gets-new-qt-interface-for.html)

---

### Post by philinux on 2012-02-23
[http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-development-update-14/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/ubuntu-12-04-development-update-14/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29) 

Quote.
Beta freeze for Beta 1 will come into effect in about 8 hours time (23 Feb 2012, 21:00UTC).

User Interface freeze is at the same time.

[https://wiki.ubuntu.com/BetaFreeze](https://wiki.ubuntu.com/BetaFreeze) [https://wiki.ubuntu.com/UserInterfaceFreeze](https://wiki.ubuntu.com/UserInterfaceFreeze)

After the freeze and until Beta 1 is out all uploads will have to be approved manually by the release team.

User interface changes will need approval by the release team ([https://launchpad.net/~ubuntu-release](https://launchpad.net/~ubuntu-release)) and notifications to the docs team and translators.

We'll be needing beta candidates images over the next week so sign up now [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

Jonathan

--ubuntu-devel-announce mailing list [email]ubuntu-devel-announce@lists.ubuntu.com[/email] [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

---

### Post by cariboo on 2012-02-23
> **Hazzabin said:**
> g'day Jonathan

what does this mean 

We'll be needing beta candidates images over the next week so sign up now [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

regards
Hazz

The beta iso images aren't ready yet, but you can sign up as a tester on the page you linked to.

---

### Post by philinux on 2012-02-24
[http://www.omgubuntu.co.uk/2012/02/login-screen-software-center-ubuntu-one-changes-land-in-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/02/login-screen-software-center-ubuntu-one-changes-land-in-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-02-27
[Myunity 3.0]("http://www.webupd8.org/2012/02/myunity-30-released-with-new-gui.html")

> The latest MyUnity 3.0 also comes with a feature that wasn't available for Unity in any GUI applications: easily adding or deleting quicklists

Omgubuntu's take on 3.0 [http://www.omgubuntu.co.uk/2012/02/unity-tweaking-tool-gets-new-look-new-features/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/unity-tweaking-tool-gets-new-look-new-features/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Here's a video showcasing 3.0 [Ubuntugeek Video]("http://www.ubuntugeek.com/myunity-3-0-released-and-ppa-installation-instructions-included.html")

---

### Post by philinux on 2012-03-01
[http://fridge.ubuntu.com/2012/03/01/ubuntu-12-04-development-update-16/](http://fridge.ubuntu.com/2012/03/01/ubuntu-12-04-development-update-16/)

---

### Post by philinux on 2012-03-01
[http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-beta-1-released/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-beta-1-released/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

```
The Ubuntu team is pleased to announce the first beta release of Ubuntu
12.04 LTS (Long-Term Support) Desktop, Server, Cloud, and Core products.

Codenamed "Precise Pangolin", 12.04 continues Ubuntu's proud tradition
of integrating the latest and greatest open source technologies into a
high-quality, easy-to-use Linux distribution. The team has been hard
at work throughout this cycle, introducing new features and fixing bugs.

This release introduces a new set of images for the ARMv7 "hard float"
ABI, denoted as armhf. There are still some armel images around, as
we finish the migration, but 12.04 for ARM will be based on armhf.

The technology that allows GPUs to go into a very low power consumption
state when the GPU is idle (RC6) is now enabled by default for
Sandy Bridge systems, which should result in considerable power savings
when this stage is activated.

The CD image size has been adjusted to 703MB to squeeze in every
bit of package goodness we can on the installation CD images.

With Ubuntu 12.04, Kubuntu, Edubuntu, Xubuntu, Lubuntu, and
Ubuntu Studio also reached Beta 1 status today.


Ubuntu Changes
--------------

Some of the new features now available are:

* A new way to quickly search and access any desktop application's
and indicator's menu, called the HUD, can be accessed by taping the
Alt key and entering characters.

* Unity setting can now be configured by the System Setting panel, and
Nautilus support has been added to the Unity launcher.

* Support for ClickPad devices has been enhanced an now when a button
is pressed on the trackpad surface, a second finger may be used to
drag the cursor.

* The default music player has been switched to Rhythmbox, which again
includes the UbuntuOne music store.

* LibreOffice has been updated to 3.5 beta 2. Please report any
regressions that you notice.

* When installing packages through the software center, the corresponding
language support packages are now installed automatically as well.

Please see http://www.ubuntu.com/testing/ for details.


Ubuntu Server and Cloud Images
------------------------------

* Improvements to OpenStack, LXC, and server provisioning have been
included.

* The identity service (Keystone) used by OpenStack for authentication (authN)
and high-level authorization (authZ) was updated to Keystone-light
(redux branch).


Ubuntu Core
-----------

Ubuntu Core is a minimal rootfs for use in the creation of custom images,
and now includes ARM hard float (armhf) images. Developers can use
Ubuntu Core as the basis for their application demonstrations, constrained
environment deployments, device support packages, and other goals.


Kubuntu
-------

Kubuntu 12.04 Beta 1 has updated KDE's plasma and applications to 4.8. In
addition other significant changes include:

* Telepathy-KDE brings improved instant messaging to Kubuntu, offering
easy chat capabilities on Facebook, MSN, GMail and many other services.

* Amarok 2.5 has added an MP3 shop and integration with GPodder, an
online personal podcast archive.

* The Calligra office and creativity suite is now available,
featuring Krita the world's best painting app and top MS Office file
importers.

Please see https://wiki.kubuntu.org/PrecisePangolin/Beta1/Kubuntu for
details.


Edubuntu
--------

Edubuntu 12.04 Beta 1 now ships the newest upstream version of LTSP 5.3,
offering improved support for fat clients and other improvements. Other
significant changes include:

* Epoptes, the new classroom management software, has an updated
user interface.

* The Ubiquity slideshow has been updated.

* pastebinit and vim are now both installed by default.

For more details on what has changed in Edubuntu 12.04, please refer to
http://www.edubuntu.org.


Xubuntu
-------

Xubuntu 12.04 Beta 1 now uses the new Ubiquity installer.
Other significant changes include:

* Alacarte is available by default, and will show all Xfce-related menu
items on Xubuntu as well.

* New wallpaper and other tweaks and improvements to the
looks of Xubuntu are in, including lots of GTK3 fixes for the
Greybird theme.

For more information about the changes in Xubuntu 12.04, please
go to http://xubuntu.org/.

Lubuntu
-------

Lubuntu 12.04 now uses Lightdm as the display manager with the
default gtk greeter. A new software-center optimized for
Lubuntu is now available by default as well.

For more information about the changes in Lubuntu 12.04,
please go to https://wiki.ubuntu.com/Lubuntu.


Ubuntu Studio
-------------

Ubuntu Studio 12.04 Beta 1 ships a live DVD for the first time,
and is properly configured for the lightdm greeter. The XFCE
transition is now almost complete, and there is an updated
application set for typical desktop tasks (i.e. text editor,
movie player, etc)


Please see http://www.ubuntu.com/testing/precise/beta1 for more details
on the above products.


About Ubuntu
------------

Ubuntu is a full-featured Linux distribution for desktops, laptops, and
servers, with a fast and easy installation and regular releases. A
tightly-integrated selection of excellent applications is included, and
an incredible variety of add-on software is just a few clicks away.

Professional technical support is available from Canonical Limited and
hundreds of other companies around the world. For more information
about support, visit http://www.ubuntu.com/support.

If you would like to help shape Ubuntu, take a look at the list of ways
you can participate at: http://www.ubuntu.com/community/participate.

Your comments, bug reports, patches and suggestions really help us to
improve this and future releases of Ubuntu. Instructions can be
found at: https://help.ubuntu.com/community/ReportingBugs.


To Get Ubuntu 12.04 Beta 1
--------------------------

To upgrade to Ubuntu 12.04 Beta 1 from Ubuntu 11.10, follow
these instructions:

https://help.ubuntu.com/community/PreciseUpgrades

Or, download Ubuntu 12.04 Beta 1 images from a location near you:

http://www.ubuntu.com/testing/download (Ubuntu and Ubuntu Server).

In addition they can be found at the following links:

http://releases.ubuntu.com/precise/ (Ubuntu, Ubuntu Server)
http://cloud-images.ubuntu.com/releases/precise/beta-1/
(Ubuntu Cloud Images)
http://cdimage.ubuntu.com/releases/precise/beta-1/
(Ubuntu DVD, preinstalled ARM images, source)
http://cdimage.ubuntu.com/ubuntu-cor.../12.04/beta-1/
(Ubuntu Core)
http://cdimage.ubuntu.com/netboot/12.04/ (Ubuntu Netboot)
http://cdimage.ubuntu.com/kubuntu/re...recise/beta-1/
(Kubuntu)
http://cdimage.ubuntu.com/xubuntu/re...recise/beta-1/
(Xubuntu)
http://cdimage.ubuntu.com/edubuntu/r...recise/beta-1/
(Edubuntu)
http://cdimage.ubuntu.com/ubuntustud...recise/beta-1/
(Ubuntu Studio)
http://cdimage.ubuntu.com/lubuntu/re...recise/beta-1/
(Lubuntu)


The final version of Ubuntu 12.04 LTS is expected to be released
on April 26, 2012.
```

---

### Post by philinux on 2012-03-03
[http://www.omgubuntu.co.uk/2012/03/10-wallpapers-from-the-precise-contest-pool/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/03/10-wallpapers-from-the-precise-contest-pool/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by NikTh on 2012-03-03
> **philinux said:**
> [http://www.omgubuntu.co.uk/2012/03/10-wallpapers-from-the-precise-contest-pool/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29]("http://www.omgubuntu.co.uk/2012/03/10-wallpapers-from-the-precise-contest-pool/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29")

[LEFT] First is beautiful . Already have it on my desktop. Here is the link for full resolution [_http://ubuntuone.com/3cqDMxJzzekwCj8fCGNdBB _]("http://ubuntuone.com/3cqDMxJzzekwCj8fCGNdBB")  from creator                                                                  [Toro Mojado]("http://www.flickr.com/photos/77281299@N07/") . [/LEFT]

---

### Post by philinux on 2012-03-05
[http://www.webupd8.org/2012/03/locally-integrated-menus-delayed-for.html](http://www.webupd8.org/2012/03/locally-integrated-menus-delayed-for.html)

---

### Post by philinux on 2012-03-08
[http://www.omgubuntu.co.uk/2012/03/new-look-login-screen-for-ubuntu-one-app-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/new-look-login-screen-for-ubuntu-one-app-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-03-08
[http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-development-update-16/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-development-update-16/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-03-12
Global Menu ‘Off Switch’ Won’t Land in 12.04

Please dont discuss this here. Start a normal thread in the forum.

[http://www.omgubuntu.co.uk/2012/03/global-menu-off-switch-wont-land-in-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/global-menu-off-switch-wont-land-in-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-03-12
[http://www.omgubuntu.co.uk/2012/03/bug-fixes-land-for-desktop-youtube-music-app-musictube/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/03/bug-fixes-land-for-desktop-youtube-music-app-musictube/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-03-15
[http://fridge.ubuntu.com/2012/03/15/ubuntu-12-04-development-update-18/](http://fridge.ubuntu.com/2012/03/15/ubuntu-12-04-development-update-18/)

---

### Post by philinux on 2012-03-17
[http://voices.canonical.com/kernelteam/2012/03/16/precise-linux-kernel-3-2-0-19-30-uploaded-abi-bump/](http://voices.canonical.com/kernelteam/2012/03/16/precise-linux-kernel-3-2-0-19-30-uploaded-abi-bump/)

---

### Post by philinux on 2012-03-20
Kernel team minutes.

 [http://voices.canonical.com/kernelteam/2012/03/20/kernel-team-meeting-minutes-march-20-2012/](http://voices.canonical.com/kernelteam/2012/03/20/kernel-team-meeting-minutes-march-20-2012/)

---

### Post by philinux on 2012-03-22
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-03-22
[http://www.omgubuntu.co.uk/2012/03/13-new-photo-wallpapers-chosen-for-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/03/13-new-photo-wallpapers-chosen-for-ubuntu-12-04/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-03-23
[http://release-blog.ubuntu.com/?p=201](http://release-blog.ubuntu.com/?p=201)

---

### Post by philinux on 2012-03-23
[http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-development-update-18/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-development-update-18/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by ubuntu27 on 2012-03-23
[Unity 5.8 released with optimized visuals, new multimonitor options, new animations and more ]("http://iloveubuntu.net/unity-58-released-optimized-visuals-new-multimonitor-options-new-animations-and-more")

Unity Launcher can be configuredh to be displayed for single or multiple monitors now!

And unity 2d.

 [http://iloveubuntu.net/unity-2d-58-released-chameleonic-behavior-multimonitor-enhancements-and-more](http://iloveubuntu.net/unity-2d-58-released-chameleonic-behavior-multimonitor-enhancements-and-more)

---

### Post by philinux on 2012-03-24
[http://iloveubuntu.net/management-service-landscape-landed-precise-pangolin](http://iloveubuntu.net/management-service-landscape-landed-precise-pangolin)

---

### Post by philinux on 2012-03-26
I missed this one.

[http://www.markshuttleworth.com/archives/1082](http://www.markshuttleworth.com/archives/1082)

[http://www.techdrivein.com/2012/03/ubuntu-1204-features-new-easily.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2012/03/ubuntu-1204-features-new-easily.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

---

### Post by philinux on 2012-03-29
[http://www.webupd8.org/2012/03/ubuntu-1204-lts-beta-2-released.html](http://www.webupd8.org/2012/03/ubuntu-1204-lts-beta-2-released.html)

 [http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-development-update-20/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-development-update-20/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Another take on beta 2. 

 [http://iloveubuntu.net/ubuntu-1204-lts-beta-2-released](http://iloveubuntu.net/ubuntu-1204-lts-beta-2-released)

---

### Post by philinux on 2012-03-30
[http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html](http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html)

---

### Post by philinux on 2012-04-03
[http://www.webupd8.org/2012/04/ubuntu-1204-default-wallpaper-revealed.html](http://www.webupd8.org/2012/04/ubuntu-1204-default-wallpaper-revealed.html)

Please dont discuss here there is already a thread in the forum. Cheers.

---

### Post by philinux on 2012-04-04
[http://iloveubuntu.net/new-keyboard-shortcuts-landed-precise-pangolin](http://iloveubuntu.net/new-keyboard-shortcuts-landed-precise-pangolin)

---

### Post by philinux on 2012-04-05
[http://iloveubuntu.net/ubuntu-1204s-dash-probably-receive-new-card-view](http://iloveubuntu.net/ubuntu-1204s-dash-probably-receive-new-card-view)

---

### Post by philinux on 2012-04-11
[http://iloveubuntu.net/xbmc-land-ubuntu-1204-available-ubuntu-software-center](http://iloveubuntu.net/xbmc-land-ubuntu-1204-available-ubuntu-software-center)

XBMC has been accepted into Debian so no ppa's needed now.

---

### Post by philinux on 2012-04-12
[http://iloveubuntu.net/zeitgeist-09-stable-landed-ubuntu-1204-lts](http://iloveubuntu.net/zeitgeist-09-stable-landed-ubuntu-1204-lts)

---

### Post by philinux on 2012-04-12
[http://www.omgubuntu.co.uk/2012/04/ubuntu-12-04-development-update-17/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/04/ubuntu-12-04-development-update-17/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by philinux on 2012-04-13
Nearly here.

[http://www.webupd8.org/2012/04/unity-5100-released-ubuntu-1204-precise.html](http://www.webupd8.org/2012/04/unity-5100-released-ubuntu-1204-precise.html)

---

### Post by philinux on 2012-04-14
Arrived [http://iloveubuntu.net/unity-510-landed-ubuntu-1204-enhanced-card-view-reduced-frost-effect-improved-icon-rendering-and](http://iloveubuntu.net/unity-510-landed-ubuntu-1204-enhanced-card-view-reduced-frost-effect-improved-icon-rendering-and)

2d as well. [http://iloveubuntu.net/unity-2d-510-released-numerous-enhancements-and-bug-fixes](http://iloveubuntu.net/unity-2d-510-released-numerous-enhancements-and-bug-fixes)

---

### Post by philinux on 2012-04-16
[http://www.omgubuntu.co.uk/2012/04/ubuntu-12-04-supports-gnome-menus/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/04/ubuntu-12-04-supports-gnome-menus/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by philinux on 2012-04-19
[http://iloveubuntu.net/unity-greeter-updated-support-disable-ready-sound-ubuntu-1204](http://iloveubuntu.net/unity-greeter-updated-support-disable-ready-sound-ubuntu-1204)

---

