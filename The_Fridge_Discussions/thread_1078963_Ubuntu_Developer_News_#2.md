---
title: "Ubuntu Developer News #2"
date: 2009-02-23
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-02-23
Welcome to the second edition of Ubuntu Developer News.  For past items or to submit your own please see [https://wiki.ubuntu.com/UbuntuDevelopment/News](https://wiki.ubuntu.com/UbuntuDevelopment/News). More submissions for the developer news would be very much appreciated.

In this issue we have

[LIST]
[*]Karmic Koala Announced
[*]Jaunty Feature Freeze
[*]Per-package uploaders and developer team structure
[*]Python 2.6
[*]Removal of aRts
[*]Progress of the Mono 2.0 transition
[*]Packaging large Java stacks
[*]Kernel Stable Release Updates
[*]White-listing external repositories in apturl
[*]Kernel changes in Jaunty
[*]Hardware Clock handling
[*]The Stracciatella GNOME session
[*]Pulseaudio in Jaunty
[*]Status of Sugar on Ubuntu
[*]Kubuntu and ports
[*]Reinhard Tartler (siretart) resigns as MOTU Launchpad Liason
[*]MySQL and Amarok
[*]New REVU Coordinator
[*]Ubuntu Studio in Jaunty
[*]Brainstorm for packaging requests?
[*]REVU gets Filtering and Tags
[*]Tools
[*]Developer ChangesMeeting Minutes/Weekly Reports
[/LIST]Karmic Koala Announced
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  If you haven&#8217;t been under a rock for the past few days, you would have heard or seen the announcement of the codename for Ubuntu 9.10 - Karmic Koala. The announcement included some of the things that will be an emphasis for the release, and first details of where UDS will be for that cycle. Jono Bacon posted more details of the UDS, including details of how to apply for sponsorship to be in Barcelona.

  [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html)
  [http://www.jonobacon.org/2009/02/19/announcing-the-karmic-koala-ubuntu-developer-summit/](http://www.jonobacon.org/2009/02/19/announcing-the-karmic-koala-ubuntu-developer-summit/)

Jaunty Feature Freeze
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Steve Langasek announced the Jaunty feature freeze for Thursday 19th February 2009.  The mail included details of freeze exceptions, and in particular a list of the delegations motu-release have in place for handling specific areas of interest.

  [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000533.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000533.html)

Per-package uploaders and developer team structure
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  As the proposal for per-package uploaders is nearing ratification by the Technical Board, Colin Watson posted proposed changes to the structure of the relationships between the developer teams in Launchpad to accommodate them. The proposal would allow per-package uploaders to become members of &#8220;ubuntu-dev&#8221;, and so gain voting rights etc., without gaining upload privileges this currently
  grants.

  [https://wiki.ubuntu.com/UbuntuDevelopers/PerPackageUploaders](https://wiki.ubuntu.com/UbuntuDevelopers/PerPackageUploaders)
  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027427.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027427.html)

Python 2.6
&#8212;&#8212;&#8212;&#8212;&#8212;

  Matthias Klose posted the plans for python 2.6 in Jaunty, along with a plan for separating packaged python modules from administrator installed ones, as is common in many other languages. There will be a transition period for all packages building python modules. The changes for each package will be straightforward, and are detailed in the mail.

  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027439.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027439.html)

Removal of aRts
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  aRts is (was) the sound system for KDE3. Since the release of KDE4 aRts is no longer maintained upstream. There are no KDE4 packages that require aRts. Since we no longer provide a KDE3 desktop in jaunty there is no requirement for aRts.

  All packages that depend on aRts or one of it&#8217;s libraries needs to be recompiled without aRts support. There is a list of affected packages along with further instructions here: [https://wiki.kubuntu.org/RemoveArts](https://wiki.kubuntu.org/RemoveArts)

  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027310.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027310.html)

Progress of the Mono 2.0 transition
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Jo Shields posted an update on the progress of the Mono 2.0 transition, undertaken in conjunction with Debian. Phase 1, which was transitioning the applications, is now complete, and work can start on transitioning the libraries. One major effect of the transition will be reducing the amount of space Mono takes up on CDs, an area where improvements are always welcome.

  [https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005488.html](https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005488.html)

Packaging large Java stacks
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  An interesting discussion around the packaging of large Java stacks was raised by Thierry Carrez.  Some of the problems that currently exist were explained, and in the discussion that followed several possible approaches were discussed.

  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027272.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027272.html)

Kernel Stable Release Updates
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  The kernel team is handling the way they push out stable updates for non-LTS releases. Tim Gardner published the updated plan that had grown out of discussion between the kernel team and the SRU team, notably Steve Langasek. Relatedly a discussion was spawned by mismatches between the version of the compiler used to build the kernel, and that which was available to build modules in Hardy.  This was caused by the environment the kernel was built in, and so changes to way kernel and gcc updates were handled were discussed.

  [https://lists.ubuntu.com/archives/kernel-team/2009-February/004322.html](https://lists.ubuntu.com/archives/kernel-team/2009-February/004322.html)
  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027366.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027366.html)

White-listing external repositories in apturl
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Alexander Sack raised an RFC regarding the process  that defines how third party repositories can apply for apturl whitelisting and how we can ensure that such repositories are of high maintenance quality.

  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027355.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027355.html)

Kernel changes in Jaunty
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  Pete Graner blogged about some changes to the kernel in Jaunty. Notably the availability of &#8220;vanilla&#8221; kernel packages which will help greatly in the process of testing whether a bug exists in the upstream kernel.

  [http://blog.redvoodoo.org/2009_02_11_archive.html](http://blog.redvoodoo.org/2009_02_11_archive.html)
  [http://blog.redvoodoo.org/2009/02/as-of-jaunty-alpha-5-we-have-enabled.html](http://blog.redvoodoo.org/2009/02/as-of-jaunty-alpha-5-we-have-enabled.html)

Hardware Clock handling
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Scott James Remnant posted a call for testing of his proposed hwclock changes, after an extensive analysis of how the hardware clock is currently handled, and what is needed. The results of his and Colin&#8217;s review were written up in a wiki page.

  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027384.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027384.html)
  [https://wiki.ubuntu.com/HardwareClock](https://wiki.ubuntu.com/HardwareClock)

The Stracciatella GNOME session
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Martin Pitt blogged about the availability of the &#8220;Stracciatella GNOME session&#8221;, which allows users and developers to easily access an environment that is closer to the one from upstream GNOME. It still contains the Ubuntu patches, as providing packages without them is not currently feasible, but it does remove Ubuntu added components, initially the new notification system.

  [http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)
  [http://www.markshuttleworth.com/archives/265](http://www.markshuttleworth.com/archives/265)

Pulseaudio in Jaunty
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  Daniel Chen posted the the mailing list about the status of and plans for pulseaudio in Jaunty, specifically about autospawn and glitch-free. Luke Yelvaich sent a call for testing of preview packages of the 0.9.15 release.

  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027433.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027433.html)
  [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027333.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027333.html)

Status of Sugar on Ubuntu
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Morgan Collett provided details of how the Sugar educational environment is progressing on Ubuntu, both Intrepid and Jaunty. Great progress has been made, but there are many areas that need work,
  so help is welcome.

  [https://lists.ubuntu.com/archives/edubuntu-devel/2009-February/002783.html](https://lists.ubuntu.com/archives/edubuntu-devel/2009-February/002783.html)

Kubuntu and ports
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Scott Kitterman posted 3 updates on the status of Kubuntu on the ports, showing the progress being made towards having KDE available on all architectures for Jaunty.

  [https://lists.ubuntu.com/archives/kubuntu-devel/2009-February/002655.html](https://lists.ubuntu.com/archives/kubuntu-devel/2009-February/002655.html)
  [https://lists.ubuntu.com/archives/kubuntu-devel/2009-February/002673.html](https://lists.ubuntu.com/archives/kubuntu-devel/2009-February/002673.html)
  [https://lists.ubuntu.com/archives/kubuntu-devel/2009-February/002676.html](https://lists.ubuntu.com/archives/kubuntu-devel/2009-February/002676.html)

Reinhard Tartler (siretart) resigns as MOTU Launchpad Liason
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  William Grant (wgrant) and Morten Kjeldgaard (mok0) will share the duties.  The Launchpad Liason provides Launchpad developers with prioritized  bugs/specs relevant to MOTU and MOTU with information on Launchpad  changes and progress.

  [https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005371.html](https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005371.html)

MySQL and Amarok
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  The Ubuntu server team list hosted a continuation of the discussion surrounding the effort to have MySQL packages that work for both the server team and Kubuntu, with Amarok now using MySQL.

  [https://lists.ubuntu.com/archives/ubuntu-server/2009-January/002588.html](https://lists.ubuntu.com/archives/ubuntu-server/2009-January/002588.html)

New REVU Coordinator
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  Nathan Handler has taken over Siegfried Gevatter&#8217;s (RainCT) role of REVU Coordinator.  There were also some suggestions on how to make the REVU process quicker for new packages.

  [https://lists.ubuntu.com/archives/ubuntu-motu/2009-January/005261.html](https://lists.ubuntu.com/archives/ubuntu-motu/2009-January/005261.html)

Ubuntu Studio in Jaunty
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

  Cory Kontros posted a quick update of the status of Ubuntu studio for Jaunty.

  [https://lists.ubuntu.com/archives/ubuntu-studio-devel/2009-February/001450.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2009-February/001450.html)

Brainstorm for packaging requests?
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

  Brian Murry pointed out the specification [https://wiki.ubuntu.com/QATeam/Specs/NeedsPackagingBugs](https://wiki.ubuntu.com/QATeam/Specs/NeedsPackagingBugs)

  [https://lists.ubuntu.com/archives/ubuntu-motu/2009-January/005301.html](https://lists.ubuntu.com/archives/ubuntu-motu/2009-January/005301.html)

REVU gets Filtering and Tags
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;
  Tags can be formed by alphanumeric characters and dashes (&#8220;-&#8220;), and both Reviewers (ie, MOTUs) and Moderators can change the tags assigned to source packages. Any name can be used as a tag, but the idea is that there will be a few &#8220;official&#8221; ones used as part of the normal workflow.

  [https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005466.html](https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005466.html)

Tools
&#8212;&#8212;-

  Martin Pitt announce the availability of apport-collect, which can attach information gathered by apport to an existing bug report.

  Ara Pulido announced that Jaunty now contains the &#8220;ubuntu-qa-tools&#8221; package, which contains many useful tools for doing QA-related work on Ubuntu. Proposals for other tools to add to the package are welcomed.

  Jorge Castro announced the availability of a tool written by Graham Binns to help open empty upstream tasks on Ubuntu bugs. This can help in the process of getting Ubuntu bugs reported upstream.

  [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000535.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000535.html)
  [https://lists.ubuntu.com/archives/ubuntu-qa/2009-February/000375.html](https://lists.ubuntu.com/archives/ubuntu-qa/2009-February/000375.html)
  [https://lists.ubuntu.com/archives/ubuntu-bugsquad/2009-February/001292.html](https://lists.ubuntu.com/archives/ubuntu-bugsquad/2009-February/001292.html)

Developer Changes
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

[LIST]
[*]Nick Ellery (nellery) became an Ubuntu Contributing Developer in recognition of the work he has put in to help Ubuntu development. He has been very active merging packages from Debian in the Jaunty cycle.
[*]Didier Roche (didrocks) joined the MOTU team, thanks to his great contributions to the desktop team and other activities.
[*]Christophe Sauthier (huats) was the second person from France to become a MOTU at the first MOTU Council membership IRC meeting. Christophe has also been very active on the desktop team, and is currently the leader of the MOTU mentoring reception.
[*]At the same meeting Iain Lane (Laney) was also accepted as a MOTU, thanks to his sterling work in many areas.
[*]Alessio Treglia (quadrispro) was the last person to become a MOTU through the old membership process. After contributing a lot of work in the Jaunty cycle he was deemed ready to become a MOTU.
[*]Nicolas Valcarcel (nxvl) steps down from MOTU-SRU
    https://lists.ubuntu.com/archives/ubuntu-motu/2009-January/005255.html</p>
[*]Iulian Udrea accepted as a MOTU Release Member
    https://lists.ubuntu.com/archives/ubuntu-motu/2009-February/005398.html</p>Nathan Handler accepted as a MOTU Release Member
    [https://lists.ubuntu.com/archives/motu-council/2009-February/002029.html](https://lists.ubuntu.com/archives/motu-council/2009-February/002029.html)
[/LIST]Meeting minutes/Weekly reports
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

Technical Board

[LIST]
[*][https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027287.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027287.html)[https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027415.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027415.html)
[/LIST]Server Team

[LIST]
[*][https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027288.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027288.html)
[*][https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027332.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027332.html)
[*][https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027347.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027347.html)[https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027419.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027419.html)
[/LIST]Desktop Team

[LIST]
[*][https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027289.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-January/027289.html)[https://lists.ubuntu.com/archives/ubuntu-desktop/2009-February/001954.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2009-February/001954.html)
[/LIST]Foundations Team

[LIST]
[*][https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027324.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027324.html)[https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027428.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027428.html)
[/LIST]Contributors
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;

[LIST]
[*]James WestbyStefan Lesicnik
[/LIST]

[More...](http://fridge.ubuntu.com/node/1833)

---

