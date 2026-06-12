---
title: "Ubuntu Weekly News: Issue #46"
date: 2007-06-26
forum: Weekly Newsletter
---

### Post by beuno on 2007-06-26
Welcome to the Ubuntu Weekly Newsletter, Issue 46 for the week June 17th - June 23rd, 2007. In this issue we cover Dell's live thread about Ubuntu, Jordan Mantha joining the Ubuntu Core Team, planned features for Gutsy, the release of Launchpad 1.1.6 and much more.

[LIST]
[*]Deutsch - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/De](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/De)
[*]Español - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/Es](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/Es)
[*]Français - Start one! [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/Fr](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/Fr)
[*]Italiano - [http://wiki.ubuntu-it.org/NewsletterItaliana](http://wiki.ubuntu-it.org/NewsletterItaliana)
[*]Português - Start one! [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/Pt](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue46/Pt)
[/LIST]

**[size="5"]In This Issue[/size]**

[LIST]
[*]Want to know more about Ubuntu on Dell?
[*]Jordan Mantha Joins Ubuntu Core Team
[*]Gutsy Goals Released
[*]Release of Launchpad 1.1.6
[*]In the Press & In the Blogosphere
[*]Upcoming Meetings
[*]Bug information
[*]Security and updates information
[/LIST]

**[size="5"]General Community News[/size]**

***[size="3"]Dell Refuses to Sell Ubuntu on Business PCs[/size]***

On the Ubuntu Forums, cosborn72 relays his attempt to buy an Ubuntu computer through Dell's Small Business division. He is told pre-installed Ubuntu PCs can only be bought for personal use and cannot be purchased using a business credit card. Read more at [http://ubuntuforums.org/showthread.php?t=478975](http://ubuntuforums.org/showthread.php?t=478975)

***[size="3"]Want to know more about Ubuntu on Dell?[/size]***

Dell will be holding a live thread session featuring two key individuals behind the Dell and Ubuntu partnership: Ben Collins and John Hull. Ben is employed by Canonical and leads the Kernel Team, and John is the manager of the Linux Engineering team at Dell. Both will be available Wednesday, June 27th, from 8am - 10am CST and again from 8pm - 10pm CST here: [http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10231](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10231)

Read more at [http://direct2dell.com/one2one/archive/2007/06/21/18833.aspx](http://direct2dell.com/one2one/archive/2007/06/21/18833.aspx)

***[size="3"]Jordan Mantha Joins Ubuntu Core Team[/size]***
Jordan Mantha has joined the Ubuntu Core Development Team. As a MOTU, Jordan leads the MOTU Science team and is the liaison between the MOTU and Launchpad development teams. Jordan is also the lead author and maintainer of the Ubuntu Packaging guide and an Edubuntu Council member. Read more at [https://lists.ubuntu.com/archives/ubuntu-devel/2007-June/023837.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-June/023837.html)

***[size="3"]Gutsy Goals Released[/size]***
Scott James Remnant, the Ubuntu Development Manager, has released the feature goals for Ubuntu 7.10:
[LIST]
[*]Desktop
[*]Ubuntu will ship with the latest edition of GNOME, 2.20, which will be released a few weeks before Gutsy.
[*]Kubuntu will ship with KDE 3.5.7 and will include packages for KDE 4.0 rc 2 for an optional side-by-side installation.
[*]Compiz Fusion, the merged Compiz and Beryl  projects will be available and enabled as the default window manager for supported combinations of hardware and drivers.
[*]Hardware Support
[*]The kernel will be updated to 2.6.22.
[*]Xorg 7.3 will be used to provide better graphics hardware support and the option of hotplugging monitors and input devices.
[*]Certain "winmodem" chips will be supported and may rely on the use of restricted drivers.
[*]Mobile
[*]A new Mobile and Embedded edition targeting hand-held devices will be available, which integrated the Hildon UI components developed by Nokia on top of the existing Ubuntu platform.
[/LIST]

[LIST]
[*]Stability and Performance
[*]Upstart 0.5 will be included to provide flexible and reliable service supervision.
[*]Improvements to apport and crash report infrastructure will allow for better analysis of issues with installing or upgrading packages. Kernel crashes will also be intercepted on reboot, and may be reported using the tool.
[*]If the filesystem is full or not writable, the user will be allowed to make room and then continue working without interruption.
[/LIST]

Read more at [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-June/000304.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-June/000304.html)

A full list of specs for Gutsy can be found at [https://blueprints.launchpad.net/ubuntu/gutsy/](https://blueprints.launchpad.net/ubuntu/gutsy/)

**[size="5"]New in Gutsy Gibbon[/size]**

***[size="3"]Gnash testing now in progress[/size]***

Alexander Sack, the main Firefox maintainer, has announced that testing of Gnash has now started. The 0.8.0 release has been uploaded to Universe and has been made to work with the auto-installation of codecs. He is looking to make certain this works and to further refine the list of websites which work and those that don't. All of this is in support of the Free Flash spec at [https://blueprints.launchpad.net/ubuntu/+spec/free-flash](https://blueprints.launchpad.net/ubuntu/+spec/free-flash). You can read the full announcement and how to test at [https://lists.ubuntu.com/archives/ubuntu-devel/2007-June/023825.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-June/023825.html).

***[size="3"]xdg-user-dirs now installed[/size]***

Sebastian Bacher of the Desktop Team has announced that the default desktop now includes xdg-user-dirs, a tool to deal with "well-known directories" such as Pictures, Documents or Downloads. The advantage of xdg-user-dirs is that it will deal with the translation issues, meaning no more Pictures directory on a French desktop, for instance. You can read more [https://lists.ubuntu.com/archives/ubuntu-devel/2007-June/023828.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-June/023828.html).

**[size="5"]Launchpad News[/size]**
It's been a busy week for Launchpad! On Wednesday, we release Launchpad 1.1.6,
including a number of important updates for the Ubuntu community:

[LIST]
[*]Improved bug status names: New (was Unconfirmed), Incomplete (was
[/LIST]
   Needs Info) and Invalid (was Rejected).
[LIST]
[*]Two new bug statuses: Triaged and Won't Fix are available to the
[/LIST]
   Ubuntu Bugs and Ubuntu Drivers teams.
[LIST]
[*]Someone with the relevant upload permissions for a component
[/LIST]
   - e.g. universe - can also now nominate bugs in that component.
[LIST]
[*]Answer contacts now receive notification of new questions in their
[/LIST]
   preferred languages only.
[LIST]
[*]Teams can now only join other teams with the approval of the first
[/LIST]
   team’s administrator.
[LIST]
[*]It is now possible to see how many and which translations diverge
[/LIST]
   from upstream.

You can read more about the bug status update on The Fridge at
[http://fridge.ubuntu.com/node/1013](http://fridge.ubuntu.com/node/1013)

Full details of Launchpad 1.1.6 on the new Launchpad News blog at
[http://news.launchpad.net/releases/milestone-116-released](http://news.launchpad.net/releases/milestone-116-released)

**[size="5"]In The Press[/size]**

[LIST]
[*]Martin La``Monica and Richard Thurston, for CNet News.com, writes that Red Hat and Canonical have no intentions of signing a deal with Microsoft like Novell, Xandros, and Linspire. The deals with Microsoft are meant to "cover technical interoperability and offer legal indemnification to some customers who use those Linux distributions." But Mark Shuttleworth says "patent agreements create 'a false sense of security' and do not effectively protect the user from a patent suit from a big company like Microsoft." Mark also believes that Microsoft should support the Open``Document format, since he doesn't "believe that the [Office Open XML] specifications are good enough, nor that Microsoft will hold itself to the specification when it does not suit the company to do so." Read the full article at [http://www.zdnet.com.au/news/software/soa/Ubuntu-Red-Hat-reject-Microsoft-patent-deal/0,130061733,339278741,00.htm](http://www.zdnet.com.au/news/software/soa/Ubuntu-Red-Hat-reject-Microsoft-patent-deal/0,130061733,339278741,00.htm)
[/LIST]

[LIST]
[*]Virtual Appliances are nano-sized Linux virtual machines with web user interfaces for deploying instant infrastructure and applications on virtualization technologies like VMWare and Xen. The LAMP virtual appliance is a 165 MB Ubuntu 7.04 Server installation. Apache, MySQL, and phpMyAdmin are ready to run from first boot with no further configuration. Read more at [http://virtualappliances.org/?p=38](http://virtualappliances.org/?p=38)
[/LIST]

**[size="5"]In The Blogosphere[/size]**

[LIST]
[*]Juergen Haas, at About.com, describes how he got DVD movies to play on his Dell E1505N. He says the computer has many nice features such as being "real quiet, the fan is barely noticeable, the screen fades out slowly when going into stand-by, [and] a little bar pops up when you adjust the volume using the cool buttons at the front of the unit." Juergen describes what packages to install from the repositories and how to install the libdvdcss2 from the Medibuntu repositories. Read more at [http://linux.about.com/b/a/257709.htm](http://linux.about.com/b/a/257709.htm)
[/LIST]

[LIST]
[*]Zolved shows how to make Open``Office run faster by changing memory settings and other helpful tricks. Screenshots are provided to show the simple steps. Read more at [http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)
[/LIST]

[LIST]
[*]Nosredna Ekim thinks Ubuntu enthusiasts are unjustly criticizing Dell for not selling business machines with Ubuntu pre-installed. Nosredna points out that the business division has a completely separate support system and Dell already sells Red Hat and SUSE on them. While Ubuntu may be the best consumer distribution, it is not viewed as enterprise-ready. Dell will probably sell the machines outside the USA if the existing Ubuntu pre-installed Dell computers sell well. Read more at [http://nosrednaekim.wordpress.com/2007/06/21/dirty-dell-or-deliverer-dell/](http://nosrednaekim.wordpress.com/2007/06/21/dirty-dell-or-deliverer-dell/)
[/LIST]

[LIST]
[*]Ron Schenone believes Ubuntu's popularity is based on the fact "the folks at Ubuntu have made it easy to try their product." The LiveCD and variants like Kubuntu, Edubuntu, and Xubuntu give different users to try what fits them best. The Ubuntu promise and clear statements by Mark Shuttleworth to not sign deals like Linspire and Xandros will only enhance Ubuntu's popularity. Read more at [http://www.lockergnome.com/nexus/blade/2007/06/21/the-many-faces-of-ubuntu/](http://www.lockergnome.com/nexus/blade/2007/06/21/the-many-faces-of-ubuntu/)
[/LIST]

[LIST]
[*]All About Ubuntu gives their first impressions of running an Ubuntu PC from Dell. The blog talks how Ubuntu costs nothing and there is no annoying licensing or activation process. There no third-party trial applications and Open``Office is fast. Firefox is easily accessible from the desktop and "there’s something reassuring about running an open source browser on an open source operating system." Read more at [http://allaboutubuntu.wordpress.com/2007/06/22/running-ubuntu-5-first-impressions/](http://allaboutubuntu.wordpress.com/2007/06/22/running-ubuntu-5-first-impressions/)
[/LIST]

**[size="5"]Meetings and Events[/size]**

***[size="3"]Sunday, June 24, 2007[/size]***
==== Georgia US LoCo meeting ====
[LIST]
[*]Start: 19:00
[*]End: 20:00
[*]Location: #ubuntu-georgia
[*]Agenda: [https://wiki.ubuntu.com/GeorgiaUSTeam/Meetings](https://wiki.ubuntu.com/GeorgiaUSTeam/Meetings)
[/LIST]

==== Catalan LoCo meeting ====
[LIST]
[*]Start: 20:00
[*]End: 21:00
[*]Location: #ubuntu-cat
[*]Agenda: [https://wiki.ubuntu.com/CatalanTeam/Reunions](https://wiki.ubuntu.com/CatalanTeam/Reunions)
[/LIST]

***[size="3"]Tuesday, June 26, 2007[/size]***
==== Community Council Meeting ====
[LIST]
[*]Start: 13:00
[*]End: 15:00
[*]Location: #ubuntu-meeting
[*]Agenda: [https://wiki.kubuntu.org/CommunityCouncilAgenda](https://wiki.kubuntu.org/CommunityCouncilAgenda)
[/LIST]

==== Kernel Team Meeting ====
[LIST]
[*]Start: 15:00
[*]End: 16:00
[*]Location: #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/KernelTeam/Meeting](https://wiki.ubuntu.com/KernelTeam/Meeting)
[/LIST]

***[size="3"]Wednesday, June 27, 2007[/size]***
==== Edubuntu Meeting ====
[LIST]
[*]Start: 12:00
[*]End: 14:00
[*]Location: #ubuntu-meeting
[*]Agenda: [https://wiki.edubuntu.org/EdubuntuMeetingAgenda](https://wiki.edubuntu.org/EdubuntuMeetingAgenda)
[/LIST]

==== Xubuntu Developers Meeting ====
[LIST]
[*]Start: 20:00
[*]End: 22:00
[*]Location: #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/Xubuntu/Meetings](https://wiki.ubuntu.com/Xubuntu/Meetings)
[/LIST]

***[size="3"]Thursday, June 28, 2007[/size]***
==== Gutsy Tribe CD 2 Release ====
[LIST]
[*]Start: 00:00
[*]End: 23:59
[/LIST]

==== Ubuntu Development Team Meeting ====
[LIST]
[*]Start: 15:00
[*]End: 17:00
[*]Location: #ubuntu-meeting
[/LIST]

**[size="5"]Updates and security for 6.06, 6.10, and 7.04[/size]**

***[size="3"]Security Updates[/size]***

[LIST]
[*]USN-476-1: redhat-cluster-suite vulnerability - [http://www.ubuntu.com/usn/usn-476-1](http://www.ubuntu.com/usn/usn-476-1)
[*]USN-475-1: evolution-data-server vulnerability - [http://www.ubuntu.com/usn/usn-475-1](http://www.ubuntu.com/usn/usn-475-1)
[/LIST]

***[size="3"]Ubuntu 6.10 Updates[/size]***
[LIST]
[*]psycopg 1.1.21-7ubuntu0.1 - [https://lists.ubuntu.com/archives/edgy-changes/2007-June/008348.html](https://lists.ubuntu.com/archives/edgy-changes/2007-June/008348.html)
[/LIST]

***[size="3"]Ubuntu 7.04 Updates[/size]***

[LIST]
[*]multipath-tools 0.4.7-1.1ubuntu3.1 - [https://lists.ubuntu.com/archives/feisty-changes/2007-June/008635.html](https://lists.ubuntu.com/archives/feisty-changes/2007-June/008635.html)
[*]python-biopython 1.42-2ubuntu1 - [https://lists.ubuntu.com/archives/feisty-changes/2007-June/008636.html](https://lists.ubuntu.com/archives/feisty-changes/2007-June/008636.html)
[*]duplicity 0.4.2-10.1ubuntu1.1 - [https://lists.ubuntu.com/archives/feisty-changes/2007-June/008637.html](https://lists.ubuntu.com/archives/feisty-changes/2007-June/008637.html)
[*]bughelper 0.1.13.2 - [https://lists.ubuntu.com/archives/feisty-changes/2007-June/008638.html](https://lists.ubuntu.com/archives/feisty-changes/2007-June/008638.html)
[*]ktorrent 2.1-0ubuntu2.2 - [https://lists.ubuntu.com/archives/feisty-changes/2007-June/008639.html](https://lists.ubuntu.com/archives/feisty-changes/2007-June/008639.html)
[*]update-manager 1:0.59.23 - [https://lists.ubuntu.com/archives/feisty-changes/2007-June/008640.html](https://lists.ubuntu.com/archives/feisty-changes/2007-June/008640.html)
[/LIST]

**[size="5"]Bug Stats[/size]**

[LIST]
[*]Open (30134) -59 # over last week
[*]Critical (28) +2 # over last week
[*]Unconfirmed (14924) -61 # over last week
[*]Unassigned (22489) -30 # over last week
[*]All bugs ever reported (106648) +757 # over last week
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see  [https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs)

Check out the bug statistics: [http://people.ubuntu-in.org/~carthik/bugstats/](http://people.ubuntu-in.org/~carthik/bugstats/)

**[size="5"]Archives and RSS Feed[/size]**

You can always find older Ubuntu Weekly Newsletter issues at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter)

You can subscribe to the Ubuntu Weekly News via RSS at:
[http://fridge.ubuntu.com/uwn/feed](http://fridge.ubuntu.com/uwn/feed)

**[size="5"]Additional Ubuntu News[/size]**

As always you can find more news and announcements at:

 [http://www.ubuntu.com/news](http://www.ubuntu.com/news)

and

 [http://fridge.ubuntu.com/](http://fridge.ubuntu.com/)

**[size="5"]Conclusion[/size]**

Thank you for reading the Ubuntu Weekly Newsletter.

See you next week!

**[size="5"]Credits[/size]**

The Ubuntu Weekly Newsletter is brought to you by:

[LIST]
[*]Nick Ali
[*]Corey Burger
[*]Martin Albisetti
[*]And many others
[/LIST]

**[size="5"]RSS[/size]**

You can subscribe to the UWN feed at: [http://fridge.ubuntu.com/uwn/feed](http://fridge.ubuntu.com/uwn/feed)

**[size="5"]Feedback[/size]**

If you would like to submit an idea or story you think is worth appearing on the UWN, please send them to [email]ubuntu-marketing-submissions@lists.ubuntu.com[/email].
This document is maintained by the Ubuntu Marketing Team. Please feel free to contact us regarding any concerns or suggestions by either sending an email to [email]ubuntu-marketing@lists.ubuntu.com[/email] or by using any of the other methods on the Ubuntu Marketing Team Contact Information Page ([https://wiki.ubuntu.com/MarketingTeam](https://wiki.ubuntu.com/MarketingTeam)). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send then [email]ubuntu-users@lists.ubuntu.com[/email].

---

