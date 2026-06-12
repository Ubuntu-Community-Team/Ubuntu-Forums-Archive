---
title: "Ubuntu Weekly Newsletter #123"
date: 2009-01-04
forum: Weekly Newsletter
---

### Post by johnc4510 on 2009-01-04
Welcome to the Ubuntu Weekly Newsletter, Issue #123 for the weeks December 21st - January 3rd, 2008. In this issue we cover: Notification, indicators and alerts, Making LoCo Teams Rock, Planet Ubuntu and Corporate Blogs, Ubuntu live on TV, Ubuntu Berlin review of 2008, Tunisian Team Events in December, 12 days of Launchpad, Full Circle Magazine #20, Meeting Summaries, and much, much more!

**[size="5"]UWN Translations[/size]**

[LIST]
[*]Note to translators and our readers: We are trying a new way of linking to our translations pages. Please follow the link below for the information you need.
[/LIST]

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations)

**[size="5"]In This Issue[/size]**

[LIST]
[*]Notifications, indicators and alerts
[*]Making LoCo Team Rock
[*]Planet Ubuntu and Corporate Blogs
[*]Ubuntu Stats
[*]Ubuntu Live on TV
[*]Ubuntu Berlin review of 2008
[*]Tunisian Team Events in December
[*]12 days of Launchpad
[*]Ubuntu Forums News
[*]In the Press & Blogosphere
[*]Full Circle Magazine #20
[*]Meeting Summaries
[*]Upcoming Meetings & Events
[*]Updates & Security
[/LIST]

**[size="5"]General Community News[/size]**

***[size="3"]Notifications, indicators, and alerts[/size]***

In a recent blog article from Mark Shuttleworth(here be dragons) we get an insight into the work being considered for notifications, indicators, and alerts. These are the bubble desktop items that draw our attention to various indicators that need our attention. Notifications are interesting, subtle and complex, with a lot of different approaches on many different platforms. The proposed changes are to simplify and eliminate complexity, while still making it possible to meet the use cases known today. The key proposals we are making are that:

[LIST]
[*]There should be no actions on notifications.
[*]Notifications should not be displayed synchronously, but may be queued. Our implementation of the notification display daemon will display only one notification at a time, others may do it differently.
[/LIST]

This work will show up as a new notification display agent, not as a fork or patch to the existing GNOME notification daemon. It isn't felt that the client API - libnotify - needs to be changed for this experiment, though it may not display notifications sent through that API that use capabilities that are thought to be deprecated.

The most controversial part of the proposal is the idea that notifications should not have actions associated with them. In other words, no buttons, sliders, links, or even a dismissal [x]. When a notification pops up, you won’t be able to click on it, you won’t be able to make it go away, you won’t be able to follow it to another window, or to a web page. The core of the idea is to lessen the responsibility of the user by relieving them of having to respond to a notification, but still giving them the information they need.

You can read the whole article, see a short video showing how the new notification might look, and find out what Mark's three pronged attack strategy will be at the link.   [http://www.markshuttleworth.com/archives/253](http://www.markshuttleworth.com/archives/253)

***[size="3"]Making LoCo Teams Rock[/size]***

Jono Bacon has a few things he'd like to see done, to help new teams achieve approved status and help existing teams to be more productive.

[LIST]
[*]Database the list of LoCo teams - This would improve data mining, help keep a current perspective on the LoCo community, and make it easier for new members to find the nearest team to join.
[*]Education - His suggestion is to hold an Open Week style event to improve how great teams can better educate new teams by passing on best practices and great experience.
[*]Contacts and messaging - The ability to share stories, experiences, and tips through blogs, articles, YouTube and anywhere else that would attract attention to the LoCo Teams and their work.
[/LIST]

Read more at:  [http://www.jonobacon.org/2008/12/30/making-loco-teams-rock/](http://www.jonobacon.org/2008/12/30/making-loco-teams-rock/)

***[size="3"]Planet Ubuntu and Corporate Blogs[/size]***

A proposal is being raised to include Corporate blogs on Planet Ubuntu.  Of course there would be guidelines, such as no advertising, Community Council oversight, and an employee with Ubuntu membership as the responsible person for the blog entry.  Other guidelines also exist.  See them all at:  [https://wiki.ubuntu.com/PlanetUbuntu/CorporateBlogs](https://wiki.ubuntu.com/PlanetUbuntu/CorporateBlogs)

**[size="5"]Ubuntu Stats[/size]**

***[size="3"]Bug Stats[/size]***

[LIST]
[*]Open (47766)+326 over last week
[*]Critical (23)+4 over last week
[*]Unconfirmed (18785)+349 over last week
[*]Unassigned (40405)+1100 over last week
[*]All bugs ever reported (239941)+2135 over last week
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see  [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[size="3"]Translation Stats Intrepid[/size]***

[LIST]
[*]Spanish (15871)-1315 over last week
[*]French (61915)+/-0 over last week
[*]Swedish (72541)+/-0 over last week
[*]Brazilian Protuguese (77812)-2954 over last week
[*]English (UK) (81460)+/-0 over last week
[/LIST]

Remaining strings to translate in Ubuntu 8.10 "Intrepid Ibex," see more at: [https://translations.launchpad.net/ubuntu/intrepid/](https://translations.launchpad.net/ubuntu/intrepid/)

***[size="3"]5-a-day bug stats[/size]***

==== Top 5 contributors for the past 7 days ====

[LIST]
[*]crimsun (179)
[*]vorian (44)
[*]chrisccoulson (33)
[*]andres-mujica (29)
[*]blueyed (26)
[/LIST]

==== Top 5 teams for the past 7 days ====

[LIST]
[*]dcteam (179)
[*]ubuntu-us-ohio (58)
[*]ubuntu-co (29)
[*]ubuntu-chicago (24)
[*]ubuntu-oklahoma (21)
[/LIST]

5-A-Day stats provided by Daniel Holbach. See [http://daniel.holba.ch/5-a-day-stats/](http://daniel.holba.ch/5-a-day-stats/)

***[size="3"]Ubuntu Brainstorm Top 5 this week[/size]***

[LIST]
[*]"Mount anyway" button on NTFS disk mount error
[*]"Speed up" Ubuntu by reducing duration of Compiz animations
[*]Improve External Monitor Support
[*]Ctrl + Z should work in F-Spot too
[*]Panel icons and applets move around too much
[/LIST]

Ubuntu Brainstorm is a community site geared toward letting you add your ideas for Ubuntu. You can submit your own idea, or vote for or against another idea. [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

**[size="5"]LoCo News[/size]**

***[size="3"]Ubuntu Live on TV[/size]***

Milo Casagrande has posted that there would be an interview with Fabio Marzocca on the local Rome TV channel, RomaUno. The interview, in Italian, is about Ubuntu and the Italian community.[1]

 [1] [http://www.ubuntu-it.org/media/romauno.avi](http://www.ubuntu-it.org/media/romauno.avi)

[http://milocasagrande.wordpress.com/2008/12/19/ubuntu-live-on-tv-uds-and/](http://milocasagrande.wordpress.com/2008/12/19/ubuntu-live-on-tv-uds-and/)

***[size="3"]Ubuntu Berlin review of 2008[/size]***

Ubuntu Berlin looks back on some of the achievements of 2008, including things like meetings, Bug Jams, release parties, and much more.  In addition, they include a list of goals for 2009, which include focusing on Ubuntu related topics, release parties, workshops, and Bug Jams.  The entire list can be seen at:  [http://www.screenage.de/blog/2008/12/17/ubuntu-berlin-review-of-2008/](http://www.screenage.de/blog/2008/12/17/ubuntu-berlin-review-of-2008/)

***[size="3"]Tunisian Team Events in December[/size]***

The Tunisian Ubuntu team was invited by the Tunisian Ministry of Communication Technologies to participate in an open source seminar titled "Free Software: A Strong Involvement of IT".  During the course of the presentations they offered testimonies on the use of open source software in companies. They also gave a lecture on Ubuntu, their LoCo, and what activities they participate in. Ali Ben Brahim also talked about the Ubuntu philosophy in business, and the advantages of using Ubuntu in business settings.

In December, they completed the first of 2 phases of migrating the National Engineering School of Sfax (ENIS) to Ubuntu. This first phase included presentations to students, teachers and technical staff of ENIS[1], and installing ubuntu on 150 PC.

 [1] [https://wiki.ubuntu.com/TunisianTeam/Presentations](https://wiki.ubuntu.com/TunisianTeam/Presentations) (presentations are in French)

[https://wiki.ubuntu.com/TunisianTeam/TeamReporting#ENIS%20Event%208.12](https://wiki.ubuntu.com/TunisianTeam/TeamReporting#ENIS%20Event%208.12)

**[size="5"]Launchpad News[/size]**

***[size="3"]12 Days of Launchpad[/size]***

[LIST]
[*]Day one: announcements - [http://news.launchpad.net/12-days-of-launchpad/twelve-days-of-launchpad-announcements](http://news.launchpad.net/12-days-of-launchpad/twelve-days-of-launchpad-announcements)
[*]Day two: sprints & meetings - [http://news.launchpad.net/12-days-of-launchpad/day-two-sprints-and-meetings](http://news.launchpad.net/12-days-of-launchpad/day-two-sprints-and-meetings)
[*]Day three: marking bugs as fixed from within Bazaar - [http://news.launchpad.net/12-days-of-launchpad/day-three-marking-bugs-as-fixed-from-within-bazaar](http://news.launchpad.net/12-days-of-launchpad/day-three-marking-bugs-as-fixed-from-within-bazaar)
[*]Day four: mentoring - [http://news.launchpad.net/12-days-of-launchpad/day-four-mentoring](http://news.launchpad.net/12-days-of-launchpad/day-four-mentoring)
[*]Day five: the bug commenters - [http://news.launchpad.net/12-days-of-launchpad/day-five-the-bug-commenters-header](http://news.launchpad.net/12-days-of-launchpad/day-five-the-bug-commenters-header)
[/LIST]

Look for more of the 12 days of Launchpad here: [http://news.launchpad.net/](http://news.launchpad.net/)

**[size="5"]Ubuntu Forums News[/size]**

The Ubuntu Forums has now surpassed 1 million threads and still growing. With over 6 million posts, and over 700,000 members the Ubuntu Forums remains a mainstay in the ever expanding Ubuntu Community. The forums play an crucial part in helping to introduce and educate new and existing users to Ubuntu and the community. Congratulations on 1 million threads. [http://ubuntuforums.org/](http://ubuntuforums.org/)

**[size="5"]In The Press[/size]**

[LIST]
[*]Ubuntu 9.04 Alpha 2 Screenshot Tour - Ubuntu 9.04 Alpha 2 (codename Jaunty Jackalope) has been released, and Softpedia has a list of the latest changes in the development. A pleasant surprise is that the developers have prepared a Live CD for this second alpha version, which will allow anyone to give it a try without having to install. As the screenshot tour shows though, most of the changes are to the inner workings of this next version of Ubuntu. GNOME has been updated to the latest development release (2.25.3), the Linux kernel has been updated to the latest release candidate of 2.6.28, and X.Org server is now at version 1.6. Other updated applications include The GIMP 2.6.3, Brasero 0.8.3, Transmission 1.40, and Mozilla Firefox 3.0.5, but there's still no OpenOffice.org 3.0. The development team also implemented a small GUI to change the position and theme of the pop-up notifications. Ubuntu 9.04 will be the tenth release of the Ubuntu operating system. [http://news.softpedia.com/news/Ubuntu-9-04-Alpha-2-Screenshot-Tour-100524.shtml](http://news.softpedia.com/news/Ubuntu-9-04-Alpha-2-Screenshot-Tour-100524.shtml)
[/LIST]

[LIST]
[*]Ubuntu vs Windows - Authors tasked with writing articles comparing Windows and Ubuntu never seem to actually use Ubuntu. They just install Ubuntu because their manager told them to compare it to Windows. In these reviews Ubuntu usually loses big time, while the author of this article believes that Ubuntu is a more simple system to use. Common misconceptions such as “you need to do everything from the command line and edit config files to make changes in the system” could not be further from the truth. Almost every program has a GUI now, and almost everything can be configured with a mouse. You won’t find an easier way to install software than on Ubuntu. A user just needs to launch the Synaptic package manager, search for a software that interests them, mark it for installation, and the package manager will handle the download and installation. Ubuntu now prompts if there is a missing codecs, and helps the user download them. An average person who uses their computer to surf the internet, create documents or spreadsheets, watch movies, listen to music or any other simple activity will find that Ubuntu is far easier to use than Windows. The public believes that Windows is easier to use because they have used it for such a long time, but once they get past their “windowsism” they can see how cool Ubuntu is. [http://www.e-linux.it/news_detail.php?id=7366](http://www.e-linux.it/news_detail.php?id=7366)
[/LIST]

[LIST]
[*]Sylvania Netbook With Ubuntu: A Good Mix - Sylvania recently introduced the Sylvania G Netbook Meso (US$369.99), which comes in a variety of colors. Nearly an unknown in the growing field of netbook manufacturers, Sylvania built in enough features to set the Meso apart from the crowd of netbook contenders. Sylvania packs an 80 GB hard drive, 1 GB of RAM, an integrated web cam, a 10/100 ethernet port, 802.11b/g wifi, an 8.9 inch display, an external VGA port, three USB ports, a multi-format card reader, headphone and microphone jacks, and a four-cell battery that lasts nearly three and a half hours into its netbook. One of the most appealing features the Sylvania model has is the option to run the new Ubuntu Netbook Remix, an updated version of 8.04 Linux (Hardy Heron). The OS remix includes a new interface that simplifies accessing favorite on-line and off-line applications and display them more appealingly within the restricted screen size. Unlike other Linux distros sandwiched into netbooks, the Ubuntu Remix is not a watered down or crippled version of the OS. It has all the bells and whistles that users enjoy on their desktops. [http://www.linuxinsider.com/rsstory/65704.html](http://www.linuxinsider.com/rsstory/65704.html)
[/LIST]

[LIST]
[*]Why Ubuntu users should care about Debian - Ubuntu attracts a lot of audience these days, but not all Ubuntu users know about Debian, which is Ubuntu's base, and the relationship between these two distributions. Since Ubuntu is not only a fork but depends on Debians ongoing development, its further existence and a healthy relationship between these two distros is quite important. The details can be found at the ars technica link here: [http://arstechnica.com/news.ars/post/20081230-why-ubuntu-users-should-care-about-debian.html](http://arstechnica.com/news.ars/post/20081230-why-ubuntu-users-should-care-about-debian.html)
[/LIST]

[LIST]
[*]Ted Ts'o: Debian Can Learn from Ubuntu - This provoking statement is meant to let the Debian folks think about a more pragmatic attitude about its distro. Ts'o names the commitment, that "Debian will remain 100% free... We will never make the system require the use of a non-free component" as an example for which he states that 100% free software is good goal, but considerations should also taken into account. [http://www.linux-magazine.com/online/news/ted_ts_o_debian_can_learn_from_ubuntu](http://www.linux-magazine.com/online/news/ted_ts_o_debian_can_learn_from_ubuntu)
[/LIST]

**[size="5"]In The Blogosphere[/size]**

[LIST]
[*]Best Ubuntu Innovations of 2008 - Blogger Christopher Tozzi of WorksWithU gives us his list of the best Ubuntu innovations of 2008. First on Tozzi's list is better wireless drivers. Thanks to the new wireless stack Ubuntu has better support for Broadcom cards and iwl3945/iwl4965 for Intel chips in Ubuntu 8.04. For Atheros users vast improvements to madwifi, especially on 64-bit systems, was implemented in Ubuntu 8.10. The Network Manager compliments the improvements to the wireless drivers with easier configuration of WPA-enterprise access as well as VPN connections. Tozzi lists additional features he feels were the best innovations of 2008, but also notes that many of these features come from upstream developers. While they may not be Ubuntu specific, these contributions have helped refine the Linux desktop experience considerably. [http://www.workswithu.com/2009/01/01/best-ubuntu-innovations-of-2008/](http://www.workswithu.com/2009/01/01/best-ubuntu-innovations-of-2008/)
[/LIST]

[LIST]
[*]Ubuntu Year in Review 2008 - UWN's own Nick Ali compiles a Ubuntu Year in Review for 2008. Nick starts off with noting the hard work LoCos continued to perform in promoting and supporting users in their area. Many held release parties for Ubuntu 8.04 and 8.10. The French Team's 8.10 release party was attended by over 4,000 people! Ubuntu membership applications from community participants continued to grow, and the Community Council created regional boards for EMEA, Asia and Oceania, and the Americas to distribute the applications. The forums continue to grow with over 700,000 registered users, 6 million posts, and almost 1 million threads. Nick continues his review with highlights such as Open Weeks, Brainstorm, Free Culture Showcase, Developer Weeks, Global Bug Jam, and more. [http://boredandblogging.com/2008/12/31/ubuntu-year-in-review-2008/](http://boredandblogging.com/2008/12/31/ubuntu-year-in-review-2008/)
[/LIST]

[LIST]
[*]Ubuntu Enrolls At Cornell College - WorksWithU's Joe Panettieri tells us that Cornell College of Mount Vernon, Iowa is the latest institute of higher education to embrace Ubuntu Server Edition. Cornell College began using Ubuntu in May 2007, when Web Developer/Programmer Brian Steere was hired as a full-time employee. “We realized that many of our Web applications were created and designed for Linux and ill-suited for running on a Windows/IIS [Internet Information Server] stack,” wrote Steere in an email to WorksWithU. Fast forward to December 2008, and Ubuntu currently hosts Cornell College’s Wordpress-Mu install, News center, Master calendar, and Moodle installation. Cornell College is considering migrating their MySQL installation to Ubuntu next as the institution continues to grow its Ubuntu Server deployment. [http://www.workswithu.com/2008/12/22/ubuntu-enrolls-at-cornell-college/](http://www.workswithu.com/2008/12/22/ubuntu-enrolls-at-cornell-college/)
[/LIST]

[LIST]
[*]The Win, Fail and Meh of Open Source in 2008 - Dj Walker-Morgan reports that heise-online-UK considers Ubuntu 8.04 LTS to be a clear win for open source software for 2008.  Reasons for their opinion include the fact that the LTS offers support for longer than 18 months, and that such support is not tied to service contracts or subscriptions.  In addition, they feel that Ubuntu has done more to popularize Linux in 2008 than any other distribution, as demonstrated by the enthusiastic community.  [http://www.heise-online.co.uk/open/The-Win-Fail-and-Meh-of-Open-Source-in-2008--/features/112305](http://www.heise-online.co.uk/open/The-Win-Fail-and-Meh-of-Open-Source-in-2008--/features/112305)
[/LIST]

[LIST]
[*]The beauty of Ubuntu or the adaptability of kids - jbunbury rebuilt a computer and gave it to his sister, her son and daughter.  Not wanting to spend a lot of money on it, he installed Ubuntu as the operating system.  After some initial trepidation on their part, and a couple of weeks between visits, he found that they had taken to Ubuntu quite readily.  Next, they're going to get hooked up with a local ISP and get out on the internet.  [http://jbunbury.wordpress.com/2008/12/29/the-beauty-of-ubuntu-or-the-adaptability-of-kids/](http://jbunbury.wordpress.com/2008/12/29/the-beauty-of-ubuntu-or-the-adaptability-of-kids/)
[/LIST]

[LIST]
[*]RE: Back to Windows - The author of the comment on this site has been caught in a bind.  He switched from Windows to Ubuntu because he loves open source.  But then he found that he couldn't access a number of devices, such as cell phones, mp3 players, and a camera.  Some of the devices he finally managed to access as an external drive, but with nothing of the full functionality that he needed.  He states, "ubuntu is a superior operating system imo, but i’m just not willing to live without full, simple device support."  [http://www.omninerd.com/comments/21356](http://www.omninerd.com/comments/21356)
[/LIST]

**[size="5"]In Other News[/size]**

***[size="3"]Full Circle Magazine: Issue 20[/size]***

[LIST]
[*]Command and Conquer - The Daunting Terminal.
[*]How-To : Program in C - Part 4, Web Development - Part 1, Backup & Sync Your Music.
[*]My Story - Making Money With FOSS
[*]Book Review - Ubuntu Kung Fu
[*]My Opinion - Italy Speaks OSS
[*]MOTU Interview - Andrea Colangelo
[*]Top 5 - Backup Solutions
[/LIST]

Don’t forget to take the FCM reader survey at: [http://url.fullcirclemagazine.org/e78bdf](http://url.fullcirclemagazine.org/e78bdf)

[http://fullcirclemagazine.org/issue-20/](http://fullcirclemagazine.org/issue-20/)

**[size="5"]Meeting Summaries[/size]**

***[size="3"]Community Council[/size]***

[LIST]
[*]Meeting 2008-12-16:
[*]PlanetUbuntu/CorporateBlogs was agreed on and the request for the addition of the Oxford Archeology blog granted. [https://wiki.ubuntu.com/PlanetUbuntu/CorporateBlogs](https://wiki.ubuntu.com/PlanetUbuntu/CorporateBlogs)
[*]Mark will ask Nigel Pugh about interest in a Google Calendar <-> IRC gateway. Daniel will mail Nick Ali about trying to get people involved in finding a solution.
[*]The decision on a Canonical/Ubuntu participation in a Tunisian FOSS conference was unfortunately too late.
[*]The three nominees for the IRC Council were appointed, the IRC Council will be asked for their OK with changing their charter to read "... at least 5 members ..." instead. The possibility of a future "IRC Contributors" team was discussed and the new IRC Council will look into finalising this. The ownership of the `~ubuntu-irc-council` team was transferred to the CC.
[/LIST]

***[size="3"]MOTU Council[/size]***

[LIST]
[*]We're pleased to announce that Stefan Ebner joined the MOTU team.
[*]We're very happy to announce that David Futcher just joined the MOTU team. He did great work in the last weeks and lives in Scotland.
[*]Stéphane Graber joined the MOTU team. Having put a lot of effort into LTSP and friends, we were only too happy to welcome him on board.
[*]Nathan Handler just joined the MOTU team. He has done fantastic work and we're very happy he's on board now.
[/LIST]

***[size="3"]Mobile Team[/size]***

[LIST]
[*]Some of the team on holiday and UDS so a quiet month
[*]Work on armel build failures and depwaits including filing bugs #308834 and bug #308465
[*]Fixed xine-lib FTBFS (4 issues combined).
[*]xulrunner-1.9 ubuntu-mobile hardy ppa upload; seems to be trivial to follow the hardy xulrunner-1.9 branch.
[*]Sent pkg-config cleanups and testsuite fixes upstream.
[*]Sent acpid patches upstream.
[/LIST]

***[size="3"]Xubuntu[/size]***

==== Artwork ====

[LIST]
[*]Pasi (knome) has been working on drafting Xubuntu artwork guidelines.
[/LIST]

==== Bug Triage ====

[LIST]
[*]Bug triage proceeding at a steady pace. Many bugs were triaged this month.
[*]A high number of bugs were reported upstream.
[/LIST]

==== Community ====

[LIST]
[*]Cody, Jannis, Michael, and Pasi all attended the Ubuntu Developer Summit in Mountain View, California
[*]Cody and Pasi attended FOSSCamp in Mountain View, California.
[*]Substantial amount of work has been done on drafting the Jaunty "Growing the Xubuntu Community" specification.
[/LIST]

==== Documentation ====

[LIST]
[*]Jim, Pasi, and Jannis are brainstorming an idea to work closely with upstream and other distributions to rewrite the upstream documentation.
[*]Jim has run some scripts to start converting Ubuntu docs to Xubuntu docs. Docs require some cleanup, but it is a good start.
[/LIST]

==== Marketing ====

[LIST]
[*]New website parallel to Intrepid release.
[*]Substantial amount of work has been done on drafting the Jaunty "Growing the Xubuntu Community" specification.
[/LIST]

==== Packaging, Development, & Testing ====

[LIST]
[*]Alpha 2 released.
[*]Updated xubuntu-meta package to fix armel build failure (Thanks to Sarah Hobbs).
[*]Add libxine1-ffmpeg to recommends for xfmedia.
[*]Michael (NCommander) has begun backport of Xfce 4.4.3 to Intrepid.
[*]Corrected an internationalization issue in en_IN local for Orage where the start/end buttons show the date number, but not the day of the week properly.
[*]Charlie Kravetz (charlie-tca) appointed to Xubuntu QA lead.
[*]Charlie (charlie-tca) has been working on improving the testing wiki pages including the Xubuntu test cases.
[*]Cody Somerville (cody-somerville) packaged Sion, a gio/vfs mount manager, from the Xfce4 goodies.
[*]Lionel (mr_pouit) packaged a new upstream release of xfce4-dict (0.5.2) and xfburn (0.4.0).
[/LIST]

***[size="3"]IRC Council[/size]***
[LIST]
[*]Working on setting up regular monthly meetings
[*]Agenda for IRC Council meetings available at [https://wiki.ubuntu.com/IrcTeam/IrcCouncil/MeetingAgenda](https://wiki.ubuntu.com/IrcTeam/IrcCouncil/MeetingAgenda).
[/LIST]

***[size="3"]LoCo Teams[/size]***

==== German Team(Berlin) ====

[LIST]
[*]2008-12-03: ubuntu-berlin user meeting (Stammtischtreffen)
[*]2008-12-09: our regular BugJam at the c-base
[*]2008-12-10: Talk "Einführung in LaTeX unter GNU/Linux" (Introduction to LaTeX - the full story in german language: [http://www.ubuntu-berlin.de/node/98](http://www.ubuntu-berlin.de/node/98))
[*]2008-12-11: Tux Origami Workshop
[/LIST]

==== Japanese Team ====

[LIST]
[*]Translated The Ubuntu Story to Japanese and published at [http://www.ubuntulinux.jp/community/ubuntustory](http://www.ubuntulinux.jp/community/ubuntustory). [http://www.ubuntulinux.jp/community/ubuntustory](http://www.ubuntulinux.jp/community/ubuntustory)
[*]Have Started planning face-to-face meeting ("Offline Meeting Tokyo 9.01") which will be hold on 17th Jan 2009.
[*]ATOK X3 (propietary Japanese input method software for Linux) supports Ubuntu 8.10 now.
[*]Exhibited at the "Gathering the Linux Distributions" at: [http://www.rakuten.co.jp/event/techconf/2008/](http://www.rakuten.co.jp/event/techconf/2008/) on 29th Nov.
[*]Interviewed by local magazine "Kantan-Ubuntu" [http://www.ascii.co.jp/books/books/detail/978-4-04-867516-1.shtml](http://www.ascii.co.jp/books/books/detail/978-4-04-867516-1.shtml)
[*]Team member have written articles for following local magazines: Software Design:Using software RAID on Linux" [http://gihyo.jp/magazine/SD/archive/2009/200901](http://gihyo.jp/magazine/SD/archive/2009/200901)
[/LIST]

==== Tunisian Team ====

[LIST]
[*]Ubuntu-tn at the 4th edition of the annual seminar on FOSS Tunisia :[https://wiki.ubuntu.com/TunisianTeam/TeamReporting#Ubuntu-tn](https://wiki.ubuntu.com/TunisianTeam/TeamReporting#Ubuntu-tn) at the 4th edition of the annual seminar on FOSS Tunisia
[*]Migration Project of the National Engineering School of Sfax (ENIS) :[https://wiki.ubuntu.com/TunisianTeam/TeamReporting#ENIS](https://wiki.ubuntu.com/TunisianTeam/TeamReporting#ENIS) Event 8.12
[/LIST]

***[size="3"]Chicago Team[/size]***

[LIST]
[*]Made initial plans for participation in the February 2009 Global Bug Jam
[*]Additional planning meeting set for Saturday, January 17th.
[*]Set tentative 6-month plan for Ubuntu-Chicago Loco activities.  Activities to include:
[*]Bug Jam - February
[*]Ubuntu and Free Software advocacy activity day - March
[*]Ubuntu-Chicago at "Flourish" FLOSS conference - April (Presenters & Ubuntu-Chicago representation)
[*]Jaunty Release Party & Install Fest - Early May
[*]Packaging Jam - June
[/LIST]

==== Georgia Team ====

[LIST]
[*]Preparing plans and schedules for 2009.
[/LIST]

==== New York Team ====

[LIST]
[*]Completed a redesign on the entire team wiki page including the creation of several additional sub-areas and pages.
[*]Held elections for new officers: PrivateVoid was elected Vice President, the-stace was elected treasurer and NewJack was elected to the at-large position for the down state region.
[*]The Newsletter team held two meetings (IRC and SIP) and is on its way to producing the teams first newsletter. The team is being headed by DaraAdib.
[*]A meet-up was held at the Barnes & Noble @ RIT in Rochester, NY on December 4th.
[*]A meet-up was held at Potato Republic in New City, NY on December 6th.
[*]Plans are being finalized for events from January through May including an Open Street Map event and participation in the Global Bug Jam.
[/LIST]

==== Pennsylvania Team ====

[LIST]
[*]Continued work on NTR Dual Boot Re-Image Project: [https://wiki.ubuntu.com/PennsylvaniaTeam/CommunityOutreachTeam/NTRDualBootImage](https://wiki.ubuntu.com/PennsylvaniaTeam/CommunityOutreachTeam/NTRDualBootImage)
[*]NTR Imaging Party Event: [https://lists.ubuntu.com/archives/ubuntu-us-pa/2008-December/000710.html](https://lists.ubuntu.com/archives/ubuntu-us-pa/2008-December/000710.html)
[*]Conducted meeting on Dec 17 where Global Big Jam plans were discussed: [https://lists.ubuntu.com/archives/ubuntu-us-pa/2008-December/000715.html](https://lists.ubuntu.com/archives/ubuntu-us-pa/2008-December/000715.html)
[/LIST]

==== Arizona Team ====

[LIST]
[*]Working on installfests to be held at the two major Arizona college campuses. On at U of A in Tucson, and one at ASU in Phoenix.
[*]Starting work on our second open source state conference(ABLEconf) to be held in 2009.
[/LIST]

**[size="5"]Upcoming Meetings and Events[/size]**

***[size="3"]Monday, January 5, 2009[/size]***

==== EMEA Membership Meeting ====

[LIST]
[*]Start: 20:00 UTC
[*]End: 21:00 UTC
[*]Location: #ubuntu-meeting on IRC
[*]Agenda: [https://wiki.ubuntu.com/Membership/RegionalBoards/EMEA](https://wiki.ubuntu.com/Membership/RegionalBoards/EMEA)
[/LIST]

***[size="3"]Tuesday, January 6, 2009[/size]***

==== Server Team Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/ServerTeam/Meeting](https://wiki.ubuntu.com/ServerTeam/Meeting)
[/LIST]

==== Desktop Team Meeting ====

[LIST]
[*]Start: 16:30 UTC
[*]End: 17:30 UTC
[*]Location: IRC channel #ubuntu-desktop
[*]Agenda: [https://wiki.ubuntu.com/DesktopTeam/Meeting](https://wiki.ubuntu.com/DesktopTeam/Meeting)
[/LIST]

==== Kernel Team Meeting ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 18:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: Not listed as of publication
[/LIST]

==== Community Council Meeting ====

[LIST]
[*]Start: 21:00 UTC
[*]End: 23:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/CommunityCouncilAgenda](https://wiki.ubuntu.com/CommunityCouncilAgenda)
[/LIST]

***[size="3"]Wednesday, January 7, 2009[/size]***

==== America's Council Meeting ====

[LIST]
[*]Start: 03:00 UTC
[*]End: 04:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/Membership/RegionalBoards/Americas](https://wiki.ubuntu.com/Membership/RegionalBoards/Americas)
[/LIST]

==== Ubuntu-us-pa LoCo Team Meeting ====

[LIST]
[*]Start: 12:30 UTC
[*]End: 13:30 UTC
[*]Location: IRC channel #ubuntu-us-pa
[*]Agenda: None as of publication
[/LIST]

==== Foundation Team Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: None listed as of publication
[/LIST]

==== QA Team Meeting ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 18:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/QATeam/Meetings/](https://wiki.ubuntu.com/QATeam/Meetings/)
[/LIST]

==== Edubuntu Meeting ====

[LIST]
[*]Start: 18:00 UTC
[*]End: 19:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/Edubuntu/Community/MeetingAgenda](https://wiki.ubuntu.com/Edubuntu/Community/MeetingAgenda)
[/LIST]

***[size="3"]Thursday, January 8, 2009[/size]***

==== Ubuntu Mobile Team Meeting ====

[LIST]
[*]Start: 12:00 UTC
[*]End: 13:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: None listed as of publication
[/LIST]

==== Desktop Team Meeting ====

[LIST]
[*]Start: 13:00 UTC
[*]End: 14:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/DesktopTeam/Meeting](https://wiki.ubuntu.com/DesktopTeam/Meeting)
[/LIST]

==== Ubuntu Java Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: None listed as of publication
[/LIST]

**[size="5"]Updates and Security for 6.06, 7.10, 8.04, and 8.10[/size]**

***[size="3"]Security Updates[/size]***

[LIST]
[*]USN-697-1: Imlib2 vulnerability - [http://www.ubuntu.com/usn/USN-697-1](http://www.ubuntu.com/usn/USN-697-1)
[*]USN-698-1: Nagios vulnerability - [http://www.ubuntu.com/usn/USN-698-1](http://www.ubuntu.com/usn/USN-698-1)
[*]USN-698-2: Nagios3 vulnerabilities - [http://www.ubuntu.com/usn/USN-698-2](http://www.ubuntu.com/usn/USN-698-2)
[*]USN-699-1: Blender vulnerabilities - [http://www.ubuntu.com/usn/USN-699-1](http://www.ubuntu.com/usn/USN-699-1)
[*]USN-698-3: Nagios vulnerabilities - [http://www.ubuntu.com/usn/USN-698-3](http://www.ubuntu.com/usn/USN-698-3)
[*]USN-677-2: OpenOffice.org Internationalization update - [http://www.ubuntu.com/usn/usn-677-2](http://www.ubuntu.com/usn/usn-677-2)
[*]USN-700-1: Perl vulnerabilities - [http://www.ubuntu.com/usn/usn-700-1](http://www.ubuntu.com/usn/usn-700-1)
[/LIST]

***[size="3"]Ubuntu 6.06 Updates[/size]***

[LIST]
[*]None Reported
[/LIST]

***[size="3"]Ubuntu 7.10 Updates[/size]***

[LIST]
[*]None Reported
[/LIST]

***[size="3"]Ubuntu 8.04 Updates[/size]***

[LIST]
[*]hulahop 0.4-1ubuntu3.1 - [https://lists.ubuntu.com/archives/hardy-changes/2009-January/012153.html](https://lists.ubuntu.com/archives/hardy-changes/2009-January/012153.html)
[*]linux-restricted-modules-2.6.24 - [https://lists.ubuntu.com/archives/hardy-changes/2009-January/012152.html](https://lists.ubuntu.com/archives/hardy-changes/2009-January/012152.html)
[/LIST]

***[size="3"]Ubuntu 8.10 Updates[/size]***

[LIST]
[*]cups 1.3.9-2ubuntu6 - [https://lists.ubuntu.com/archives/intrepid-changes/2008-December/009581.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-December/009581.html)
[*]linux-restricted-modules 2.6.27-11.16 - [https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009582.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009582.html)
[*]sugar-hulahop 0.4.6-0ubuntu2.1  - [https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009583.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009583.html)
[*]libv4l 0.5.7-1~intrepid1 - [https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009584.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009584.html)
[*]poppler 0.8.7-1ubuntu0.1 - [https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009585.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-January/009585.html)
[/LIST]

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
[*]John Crawford
[*]Craig A. Eddy
[*]Kenny McHenry
[*]Dave Bush
[*]And many others
[/LIST]

**[size="5"]Glossary of Terms[/size]**

 1. acpid - Advanced Configuration and Power Interface Daemon
 1. API - Application Programming Interface
 1. FOSS - Free Open Source Software
 1. FTBFS - Fails To Build From Source
 1. GUI - Graphicical User Interface
 1. IRC - Internet Relay Chat
 1. LTS - Long Term Support
 1. LTSP - Linux Terminal Server Project
 1. MOTU - Master Of The Universe - Developers responsible for the Universe and Multiverse repositories.
 1. NTR - Nonprofit Technology Resources
 1. OS - Operating System
 1. OSS - Open Source Software
 1. PDA - Personal Digital Assistant
 1. UDS - Ubuntu Developer Summit
 1. USB - Universal Serial Bus
 1. VGA - Video Graphics Array
 1. VPN - Virtual Private Network
 1. WPA - Wi-Fi Protected Access

**[size="5"]Ubuntu - Get Involved[/size]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. [http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)

**[size="5"]Feedback[/size]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send them to [email]ubuntu-users@lists.ubuntu.com[/email].

Except where otherwise noted, content of this publication is licensed under a Creative Commons Attribution 3.0 License BY SA [http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/)

---

