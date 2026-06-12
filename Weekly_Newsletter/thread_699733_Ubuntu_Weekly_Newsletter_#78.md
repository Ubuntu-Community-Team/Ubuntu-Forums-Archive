---
title: "Ubuntu Weekly Newsletter #78"
date: 2008-02-17
forum: Weekly Newsletter
---

### Post by boredandblogging.com on 2008-02-17
Welcome to the Ubuntu Weekly Newsletter, Issue 78 for the weeks February 10th - February 16th, 2008. In this issue we cover Developer Week, MOTU Freeze Team, Hardy Alpha 5, Hug Day, PulseAudio, and, as always, much, much more!

**[SIZE=5]In This Issue[/SIZE]**
[LIST]
[*]Ubuntu Developer Week
[*]MOTU Freeze Team
[*]Hardy Alpha 5 Coming Thursday, 21 February
[*]Hug Day - 19 February 2008
[*]PulseAudio in 8.04
[*]In The Press & Blogosphere
[*]Meeting Summaries
[*]Upcoming Meetings & Events
[*]Updates & Security
[*]Bugs & Translations[/LIST]
**[SIZE=5]General Community News[/SIZE]**

***[SIZE=3]Ubuntu Developer Week[/SIZE]***

We're very very pleased to announce the first ever Ubuntu Developer Week. What does this mean? We’ll have one week full of action-packed IRC sessions where you can:
[LIST]
[*]learn about different packaging techniques
[*]find out more about different development teams
[*]check out the efforts of the world-wide Development Community
[*]participate in open Q&A sessions with Ubuntu developers
[*]and much much more...[/LIST]
We're absolutely excited to have such a diverse programme and thrilled we have so many excellent speakers in the first ever Ubuntu Developer Week. All your favourite Ubuntu developers will be there, who will introduce you to lots of parts of Ubuntu development including packaging, virtualisation, desktop application testing, development processes, collaboration techniques and lots lots more. This is the perfect time to get started, get up and running and in touch with future team members.

So, what are you waiting for? Go and see the timetable: [https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)

Then see how to attend, [https://wiki.ubuntu.com/UbuntuDeveloperWeek/JoiningIn](https://wiki.ubuntu.com/UbuntuDeveloperWeek/JoiningIn).

Oh, and lets spread the word! Digg It Here! [http://digg.com/linux_unix/First_ever_Ubuntu_Developer_Week_announced](http://digg.com/linux_unix/First_ever_Ubuntu_Developer_Week_announced)

***[SIZE=3]Hardy Alpha 5 Coming Thursday, 21 February[/SIZE]***

The Feature Freeze is now in effect for Hardy. From now until release, the focus is on polishing and bug fixing. If you do believe that a new package, a new upstream version of a package, or a new feature is needed for the release and will not introduce more
problems than it fixes, please follow the Freeze Exception Process by filing bugs and subscribing ubuntu-release or motu-release as appropriate.[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

The next testing milestone, Hardy Alpha 5, is scheduled for next Thursday, February 21. Hardy Alpha 5 will again use a "soft freeze" for main, as described in previous announcements: [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-January/000363.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-January/000363.html). This means that developers are asked to refrain from uploading packages between Tuesday and Thursday which don't bring us closer to releasing the alpha, so that these days can be used for settling the archive and fixing any remaining show stoppers.

The list of bugs targeted for alpha-5 can be found in a couple of different places, according to your tastes:
[LIST]
[*][https://launchpad.net/ubuntu/+milestone/hardy-alpha-5](https://launchpad.net/ubuntu/+milestone/hardy-alpha-5)
[*][https://bugs.launchpad.net/ubuntu/+bugs?field.milestone%3Alist=951](https://bugs.launchpad.net/ubuntu/+bugs?field.milestone%3Alist=951)[/LIST]
***[SIZE=3]New MOTU Member[/SIZE]***

The MOTU Council agreed that Matvey Kozhev has all it takes to become a MOTU. [https://launchpad.net/~sikon]("https://launchpad.net/%7Esikon")

***[SIZE=3]MOTU Freeze Team[/SIZE]***

Ubuntu now has a MOTU Release team for the remainder of the Hardy cycle. It consists of:
[LIST]
[*]Cesare Tirabassi
[*]Luke Yelavich
[*]Sarah Hobbs
[*]Scott Kitterman
[*]Stefan Potyra[/LIST]
This team is responsible for observing the freeze exception process: [https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess) for the Universe and Multiverse repositories. If you have any questions, let them know. The MOTU team is confident that this team will stay on top of things and make sure we have a good Universe and Multiverse in Hardy. [https://lists.ubuntu.com/archives/motu-council/2008-February/000871.html](https://lists.ubuntu.com/archives/motu-council/2008-February/000871.html)

***[SIZE=3]Hug Day - 19 February 2008[/SIZE]***

For the next hug day we'll be working with bug reports regarding printing, so make sure you have plenty of ink and paper! The bug team will be looking at new bug reports regarding cupsys and system-config-printer primarily and with those they'll be following up with reporters, documenting test cases, confirming bug reports.  The event will be held in #ubuntu-bugs on Freenode.  The list of targeted bugs and tasks is posted at: [https://wiki.ubuntu.com/UbuntuBugDay/20080219](https://wiki.ubuntu.com/UbuntuBugDay/20080219)

The goal is to deal with all of the bugs on that list and maybe more!

So on 19 February 2008, and lasting for 3 days in all timezones, the bug team be meeting in #ubuntu-bugs on irc.freenode.net for another Ubuntu Hug Day. [https://lists.ubuntu.com/archives/ubuntu-users/2008-February/137242.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-February/137242.html)

**[SIZE=5]New in Hardy Heron[/SIZE]**

***[SIZE=3]PulseAudio[/SIZE]***

PulseAudio is a sound server that is a proxy for your sound needs. It allows you to do advanced operations on your sound data as it passes between your application and your hardware. Things like transferring the audio to a different machine, changing the sample format or channel count and mixing several sounds into one are easily achieved using a sound server. Currently audio on Linux is a mess. Sound servers like  Esound, Arts, Jack, PulseAudio constantly fight for exclusive access to the sound device. Applications usually support only a small subset of the available sound server/device APIs, and need to be configured for their use. Alpha 4 includes PulseAudio enabled by default. Some non-GNOME applications still need to be changed to output to pulse/esd by default and the volume control tools are still not integrated. The goal is to incorporate Pulse Audio to make a single core sound program that will satisfy not only the desktop user, but the professional sound guru too. [http://pulseaudio.org/](http://pulseaudio.org/)

**[SIZE=5]In The Press[/SIZE]**
[LIST]
[*]Obsidian signs deal to offer Ubuntu training - South African Linux and open source specialists, Obsidian, will be offering official training for the Ubuntu Certified Professional program starting in March. Obsidian will be providing both Ubuntu Professional Courses 1 and 2 for system administrators wanting to pass the required Linux Professional Institute 101 and 102, and also Ubuntu 199 exams to achieve the Ubuntu Certified Professional certification. These courses are two in a series of classroom and e-learning courses available for Ubuntu Linux professionals. Robin Edser, Obsidian Open Systems Architect said: “It is fantastic that Ubuntu has reached the level where relevant certified training has become available for Linux professionals.” [http://www.tectonic.co.za/?p=2138](http://www.tectonic.co.za/?p=2138)[/LIST][LIST]
[*]What if Ubuntu Hosted a Repository and Nobody Came? - Bruce Byfield questions the need for a commercial Ubuntu repository. Last week, Canonical announced that it would be using its Partners repository to sell proprietary applications like Parallels Workstation. You can see the reasoning: Ubuntu already has the infrastructure for on-demand downloads and software installation, so why not monetize it? But, if past incarnations of the idea are any indication, then the results are likely to be disappointing at best. For one thing, neither the free software community nor the software vendors care for the idea, so there's  little market for it. For another, with the recent maturity of many pieces of free software, how many Ubuntu users will insist on a brand name that they will pay for when they can get the functionality for free? Judging by the Ubuntu forums, the most common reaction has been mild curiosity. [http://itmanagement.earthweb.com/article.php/3727706](http://itmanagement.earthweb.com/article.php/3727706)[/LIST][LIST]
[*]Measuring Ubuntu's Boot Performance - Using Bootchart, Phoronix has gone back and performed clean installations of Ubuntu 6.06.1 LTS, Ubuntu 6.10, Ubuntu 7.04, Ubuntu 7.10, and an Ubuntu 8.04 LTS development build to analyze their boot performance. The Ubuntu 8.04 development copy was a daily build from February 7. With Ubuntu 6.06.1 LTS, the time it took to boot and reach the GDM was 32 seconds. The disk throughput maximum was 19MB/s. While more processes had started by default in Ubuntu 6.10, its boot time had decreased by one second. Edgy Eft had booted in 31 seconds with a disk throughput maximum of 31MB/s. In Ubuntu 7.04 the boot time had once again decreased by a second while its disk throughput had dropped to 27MB/s. This performance boost had come while Ubuntu 7.04 had more services starting by default at boot-time. However, the biggest boot performance increase for Ubuntu had come in 7.10 Gutsy Gibbon with the boot time dramatically decreasing down to 22 seconds. Even with many new features and additions appearing in every new Ubuntu release, it's gratifying to see the boot time continuing to drop. While the Ubuntu 8.04 build was three seconds slower than Ubuntu 7.10, expect further optimizations to occur prior to the April release of Hardy Heron. [http://www.phoronix.com/scan.php?page=article&item=ubuntu_boot_perf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_boot_perf&num=1)[/LIST]
**[SIZE=5]In The Blogosphere[/SIZE]**
[LIST]
[*]Commercial Ubuntu - A post by Bruce Byfield (see above), raises an interesting question: will anyone use the Partner repository? If not, could it alienate Ubuntu users from using the distribution? Alex thinks what Bruce doesn't see is that this service is no different from other software distribution methods. The main reason for Canonical to do support a commercial repository is that Ubuntu is not just for home desktop users - its for business users and Ubuntu Server users, who may use proprietary applications for their businesses and need a standard way of installing applications. Sun has its own software distribution system, just as Apple's Mac OS X and MS Windows do. Why is it forbidden for Linux distributions to have one that includes commercial software? Alex thinks Bruce emotionally reacted to the offering of something proprietary for Linux. While it is perfectly fine for some users to be upset, business people might actually be glad that they will be able to get the software they want or need in a standard fashion. [http://www.thetechandcents.com/2008/02/commercial-ubuntu.html](http://www.thetechandcents.com/2008/02/commercial-ubuntu.html)[/LIST]
**[SIZE=5]Meeting Summaries[/SIZE]**

***[SIZE=3]Documentation Team[/SIZE]***
[LIST]
[*][http://doc.ubuntu.com](http://doc.ubuntu.com) is now up and working again as a preview server for documentation for the development version of Ubuntu.
[*]Great work is being done by the server team on improving and expanding the server guide documentation [https://wiki.ubuntu.com/TeamReports/February2008](https://wiki.ubuntu.com/TeamReports/February2008)[/LIST]
**[SIZE=5]Upcoming Meetings and Events[/SIZE]**

***[SIZE=3]Monday, February 18, 2008[/SIZE]***

==== Bugs for Hugs Day ====[LIST]
[*]Start: 12:00 UTC
[*]End: All Day Event
[*]Location: IRC channel #ubuntu-bugs
[*]Agenda: [https://wiki.ubuntu.com/UbuntuBugDay/20080219](https://wiki.ubuntu.com/UbuntuBugDay/20080219)[/LIST]
==== Ubuntu Developer Week ====[LIST]
[*]Start: 16:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-classroom
[*]Agenda: [https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)[/LIST]
***[SIZE=3]Tuesday, February 19, 2008[/SIZE]***

==== Bugs for Hugs Day ====[LIST]
[*]Start: All Day Event
[*]End: All Day Event
[*]Location: IRC channel #ubuntu-bugs
[*]Agenda: [https://wiki.ubuntu.com/UbuntuBugDay/20080219](https://wiki.ubuntu.com/UbuntuBugDay/20080219)[/LIST]
==== Ubuntu Developer Week ====[LIST]
[*]Start: 16:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-classroom
[*]Agenda: [https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)[/LIST]
***[SIZE=3]Wednesday, February 20, 2008[/SIZE]***

==== Bugs for Hugs Day ====[LIST]
[*]Start: 00:00 UTC
[*]End: 13:00 UTC
[*]Location: IRC channel #ubuntu-bugs
[*]Agenda: [https://wiki.ubuntu.com/UbuntuBugDay/20080219](https://wiki.ubuntu.com/UbuntuBugDay/20080219)[/LIST]
==== TriLoCo-Midwest Meeting ====[LIST]
[*]Start: 01:00 UTC
[*]End: 02:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: The TriLoCo-Midwest group, a newly formed entity made up of the 3 approved loco teams Michigan, Ohio, and Chicago (US Teams) will be meeting. The purpose of the TriLoCo-Midwest group is to encourage cooperation between US LoCo teams in the Midwest for events such as conferences.[/LIST]
==== Launchpad users meeting ====[LIST]
[*]Start: 09:00 UTC
[*]End: Not listed
[*]Location: IRC channel #launchpad-meeting
[*]Agenda: [https://help.launchpad.net/UsersMeeting](https://help.launchpad.net/UsersMeeting)[/LIST]
==== Ubuntu Developer Week ====[LIST]
[*]Start: 16:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-classroom
[*]Agenda: [https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)[/LIST]
==== Platform Team Meeting ====[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: No agenda listed as of the publication[/LIST]
==== Education Team Meeting ====[LIST]
[*]Start: 20:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: No agenda listed as of the publication[/LIST]
==== Server Team Meeting ====[LIST]
[*]Start: 21:00 UTC
[*]End: 22:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/ServerTeam/Meeting](https://wiki.ubuntu.com/ServerTeam/Meeting)[/LIST]
***[SIZE=3]Thursday, February 21, 2008[/SIZE]***

==== Desktop Team Meeting ====[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/DesktopTeam/Meeting](https://wiki.ubuntu.com/DesktopTeam/Meeting)[/LIST]
==== Ubuntu Developer Week ====[LIST]
[*]Start: 16:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-classroom
[*]Agenda: [https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)[/LIST]
==== Community Council Meeting ====[LIST]
[*]Start: 20:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/CommunityCouncilAgenda](https://wiki.ubuntu.com/CommunityCouncilAgenda)[/LIST]
***[SIZE=3]Friday, February 22, 2008[/SIZE]***

==== Ubuntu Developer Week ====[LIST]
[*]Start: 16:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-classroom
[*]Agenda: [https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)[/LIST]
**[SIZE=5]Updates and Security for 6.06, 6.10, 7.04, and 7.10[/SIZE]**

***[SIZE=3]Security Updates[/SIZE]***
[LIST]
[*][USN-577-1] Linux kernel vulnerability - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2008-February/000664.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2008-February/000664.html)
[*][USN-578-1] Linux kernel vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2008-February/000665.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2008-February/000665.html)[/LIST]
***[SIZE=3]Ubuntu 6.06 LTS Updates[/SIZE]***
[LIST]
[*]wzdftpd 0.6.1-1ubuntu1.2 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012622.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012622.html)
[*]python-uncertainities 0.001-3.1ubuntu1.1 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012623.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012623.html)
[*]vmware-player-kernel-2.6.15 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012624.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012624.html)
[*]linux-source-2.6.15 2.6.15-51.66 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012625.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012625.html)
[*]linux-backports-modules-2.6.15 2.6.15-51.9 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012626.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012626.html)
[*]linux-restricted-modules-2.6.15 2.6.15.12-51.2 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012627.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012627.html)
[*]clamav_0.92~dfsg-2~dapper1ubuntu0.1 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012628.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012628.html)
[*]update-manager-core 0.56 - [https://lists.ubuntu.com/archives/dapper-changes/2008-February/012629.html](https://lists.ubuntu.com/archives/dapper-changes/2008-February/012629.html)[/LIST]
***[SIZE=3]Ubuntu 6.10 Updates[/SIZE]***
[LIST]
[*]linux-source-2.6.17 - [https://lists.ubuntu.com/archives/edgy-changes/2008-February/008498.html](https://lists.ubuntu.com/archives/edgy-changes/2008-February/008498.html)[/LIST]
***[SIZE=3]Ubuntu 7.04 Updates[/SIZE]***
[LIST]
[*]linux-source-2.6.20 - [https://lists.ubuntu.com/archives/feisty-changes/2008-February/008849.html](https://lists.ubuntu.com/archives/feisty-changes/2008-February/008849.html)
[*]dspam 3.6.8-4ubuntu1.1 - [https://lists.ubuntu.com/archives/feisty-changes/2008-February/008850.html](https://lists.ubuntu.com/archives/feisty-changes/2008-February/008850.html)
[*]clamav_0.90.2-0ubuntu1.6 - [https://lists.ubuntu.com/archives/feisty-changes/2008-February/008851.html](https://lists.ubuntu.com/archives/feisty-changes/2008-February/008851.html)
[*]klavaro 1.0.1-1ubuntu1 - [https://lists.ubuntu.com/archives/feisty-changes/2008-February/008852.html](https://lists.ubuntu.com/archives/feisty-changes/2008-February/008852.html)[/LIST]
***[SIZE=3]Ubuntu 7.10 Updates[/SIZE]***
[LIST]
[*]linux-source-2.6.22 2.6.22-14.52 - [https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010133.html](https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010133.html)
[*]klavaro 1.0.3-1ubuntu1 - [https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010134.html](https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010134.html)
[*]twill 0.9~b1-1ubuntu0.1 - [https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010135.html](https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010135.html)
[*]clamav_0.91.2-3ubuntu2.3 - [https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010136.html](https://lists.ubuntu.com/archives/gutsy-changes/2008-February/010136.html)[/LIST]
**[SIZE=5]Bug Stats[/SIZE]**
[LIST]
[*]Open (39936) +16 # over last week
[*]Critical (23) +2 # over last week
[*]Unconfirmed (20281) -71 # over last week
[*]Unassigned (30476) +83 # over last week
[*]All bugs ever reported (152393) +1505 # over last week[/LIST]
As always, the Bug Squad needs more help. If you want to get started, please see  [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

**[SIZE=5]Translation Stats[/SIZE]**

 1. Spanish (12389) -17 # over last week
 2. French (37728) +/-0 # over last week
 3. Swedish (49176) +/-0 # over last week
 4. English-UK (24947) +/-0 # over last week
 5. German (66051) -3 # over last week

Remaining string to translate in Ubuntu 7.10 "Gutsy Gibbon", see more at: [https://translations.launchpad.net/ubuntu/gutsy/](https://translations.launchpad.net/ubuntu/gutsy/)

**[SIZE=5]Archives and RSS Feed[/SIZE]**

You can always find older Ubuntu Weekly Newsletter issues at: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter)

You can subscribe to the Ubuntu Weekly News via RSS at:
[http://fridge.ubuntu.com/uwn/feed](http://fridge.ubuntu.com/uwn/feed)

**[SIZE=5]Additional Ubuntu News[/SIZE]**

As always you can find more news and announcements at:

 [http://www.ubuntu.com/news](http://www.ubuntu.com/news)

and

 [http://fridge.ubuntu.com/](http://fridge.ubuntu.com/)

**[SIZE=5]Conclusion[/SIZE]**

Thank you for reading the Ubuntu Weekly Newsletter.

See you next week!

**[SIZE=5]Credits[/SIZE]**

The Ubuntu Weekly Newsletter is brought to you by:
[LIST]
[*]Nick Ali
[*]John Crawford
[*]Craig A. Eddy
[*]And many others[/LIST]
**[SIZE=5]Glossary of Terms[/SIZE]**

 1. MOTU - Masters Of The Universe

**[SIZE=5]Feedback[/SIZE]**

If you would like to submit an idea or story you think is worth appearing on the UWN, please send them to [EMAIL="ubuntu-marketing-submissions@lists.ubuntu.com"]ubuntu-marketing-submissions@lists.ubuntu.com[/EMAIL].
This document is maintained by the Ubuntu Marketing Team. Please feel free to contact us regarding any concerns or suggestions by either sending an email to [EMAIL="ubuntu-marketing@lists.ubuntu.com"]ubuntu-marketing@lists.ubuntu.com[/EMAIL] or by using any of the other methods on the Ubuntu Marketing Team Contact Information Page ([https://wiki.ubuntu.com/MarketingTeam](https://wiki.ubuntu.com/MarketingTeam)). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send then [EMAIL="ubuntu-users@lists.ubuntu.com"]ubuntu-users@lists.ubuntu.com[/EMAIL].

---

