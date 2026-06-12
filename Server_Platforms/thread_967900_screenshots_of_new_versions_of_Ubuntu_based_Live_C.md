---
title: "screenshots of new versions of Ubuntu based Live CDs"
date: 2008-11-02
forum: Server Platforms
---

### Post by lirazsiri on 2008-11-02
Hi guys,

As you may recall we launched [TurnKey Linux]("http://www.turnkeylinux.org/") about a month and a half ago, with the goal of creating an Ubuntu-based opensource project that specialized in making certain niche tasks (e.g., setting up a LAMP stack, a CMS, etc.) easier by pre-integrating solutions into a software appliance type package.

The response we got from the Ubuntu community was fantastic, and we used the feedback to guide our efforts as while working the kinks out of our current crop of appliances.

Our main focus has been to try and figure out how to dramatically improve the usability of the handful of appliances we have released so that they appeal to a much wider audience (e.g., not everybody likes mucking around with the command line).

We are proud to announce that recently released versions of our [Lamp stack]("http://www.turnkeylinux.org/appliances/lamp"), [Joomla]("http://www.turnkeylinux.org/appliances/joomla"), and [Drupal]("http://www.turnkeylinux.org/appliances/drupal") appliances now feature:

* an easy to use configuration console (written from scratch in Python)
* a beautiful web management interface
* auto-login while in demo/live mode
* root password configuration during installation

As usual, detailed information, screenshots and release notes are available in the [appliances section]("http://www.turnkeylinux.org/appliances") on our website. You may also want to check out our [Launchpad blueprints]("https://blueprints.launchpad.net/turnkeylinux/2008.10.17-hardy-x86") for this release.

With the most pressing usability issues under our belt we are now in the process of expanding the range of appliances we're building...

Here are a few screenshots:

[IMG]http://www.turnkeylinux.org/files/images/screenshot-webmin3.png[/IMG]
[IMG]http://www.turnkeylinux.org/files/images/screenshot-webmin2.png[/IMG]
[IMG]http://www.turnkeylinux.org/files/images/screenshot-confconsole1.png[/IMG]
[IMG]http://www.turnkeylinux.org/files/images/screenshot-confconsole2.png[/IMG]
[IMG]http://www.turnkeylinux.org/files/images/screenshot-boot.png[/IMG]

What do you think?

Cheers,
Liraz

---

### Post by garyedwardjohnston on 2008-11-14
Nice idea, but needs documentation.

---

### Post by cdtech on 2008-11-14
> **garyedwardjohnston said:**
> nice idea, but needs documentation.

lots!

---

### Post by lirazsiri on 2008-11-15
Thanks for the feedback guys. 

Improving the usability of our appliances, by improving the documentation or by other means is definitely something we are interested in, but we need feedback from the community in order for that to happen. If users share their experience, expectations and ideas (on the [forums]("http://www.turnkeylinux.org/forum"), [mailing list]("http://lists.turnkeylinux.org/"), etc.) it will be much easier for us to improve.

Keep in mind however that the appliances are pretty much vanilla versions of Ubuntu hardy that are optimized for specific tasks, so all of the Ubuntu documentation applies. We also publish manifests of all of the packages that go into every appliance (see the release notes). 

The [community documentation]("http://www.turnkeylinux.org/docs") can be updated and extended freely by anyone that registers for an account on the website. It is an opensource project. If you found some area of documentation lacking, why not help improve it?

Finally we have some technical information on our [development wiki]("http://wiki.turnkeylinux.org/").

---

### Post by BlackHero on 2008-11-15
beutiful but need more complements :D
in my opinion is a good project :D

COngratulations :D
i am dowloading now for test :D

---

### Post by Thirtysixway on 2008-11-16
The Drupal 5 version is outdated.  It's at 5.10, latest release is 5.12.

---

### Post by lirazsiri on 2008-11-20
We are using the latest stable version of Drupal 5 for which a package exists (5.10-3) in Ubuntu and Debian. We don't update to upstream package versions ourselves unless absolutely necessary.

Incidentally, the version in our security updates archive includes backported security fixes from 5.12.

---

