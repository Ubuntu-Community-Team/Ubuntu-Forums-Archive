---
title: "What Happens During a Distro Upgrade?"
date: 2014-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by badowskiryan on 2014-04-03
I can't seem to find a complete answer to that question.

14.04 is about to release. I've upgraded many times before (since Edgy Eft, lol) and I know a lot of *stuff* happens when I do. But I don't know what, exactly.

I mean, updates happen almost daily -- packages, and occasionally the kernel. And a Linux distro is essentially a kernel with packages, right?

**So what happens during a distro upgrade?**

---

### Post by dbass81 on 2014-04-03
> **badowskiryan said:**
> I can't seem to find a complete answer to that question.

14.04 is about to release. I've upgraded many times before (since Edgy Eft, lol) and I know a lot of *stuff* happens when I do. But I don't know what, exactly.

I mean, updates happen almost daily -- packages, and occasionally the kernel. And a Linux distro is essentially a kernel with packages, right?

**So what happens during a distro upgrade?**

Taken from man apt-get:

[quote=man apt-get]
update
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.


       upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.


       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
[/quote]

---

### Post by lykwydchykyn on 2014-04-03
I'm guessing you mean a release-upgrade, rather than a "dist-upgrade" which is a specific APT command.

Essentially, a release-upgrade works like this:
- Change sources to the new release
- Dist-upgrade
- Cleanup & reboot

And on some distros (like Debian), this is pretty much what you do to upgrade to the new release.

On Ubuntu, you don't want to do that manually.  The release-upgrade tool does a lot more stuff, like safety checks (making sure you have enough disk space, the repos are available, etc), disabling bad PPAs, and handling those corner-cases that APT alone can't deal with.

If you want to see a little more verbose version of a release upgrade, you can always do it at a terminal with the command-line tool "do-release-upgrade".

---

