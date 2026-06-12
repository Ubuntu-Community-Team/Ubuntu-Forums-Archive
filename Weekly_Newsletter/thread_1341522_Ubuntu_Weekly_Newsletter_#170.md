---
title: "Ubuntu Weekly Newsletter #170"
date: 2009-11-29
forum: Weekly Newsletter
---

### Post by johnc4510 on 2009-11-29
Welcome to the Ubuntu Weekly Newsletter, Issue #170 for the week November 22nd - November 28th, 2009. In this issue we cover: Jono Bacon: Introducing Lernid, Mackenzie Morgan Interview, New Developers, LoCo News: Maryland, Massachusetts, Chile & Nicaragua, Ubuntu Forums Tutorial of the Week, The Planet: Laura Czajkowski, Andres Rodriguez, Amber Graner, & Harald Sitter, Full Circle Magazine #31

**[size="5"]UWN Translations[/size]**

[LIST]
[*]Note to translators and our readers: We are trying a new way of linking to our translations pages. Please follow the link below for the information you need.
[/LIST]

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations)

**[size="5"]In This Issue[/size]**

[LIST]
[*]Jono Bacon: Introducing Lernid
[*]Mackenzie Morgan Interview
[*]New Developers
[*]Ubuntu Stats
[*]LoCo News: Maryland, Massachusetts, Chile & Nicaragua
[*]Ubuntu Forums Tutorial of the Week
[*]The Planet: Laura Czajkowski, Andres Rodriguez, Amber Graner, & Harald Sitter
[*]In the Press & Blogosphere
[*]Full Circle Magazine #31
[*]Upcoming Meetings & Events
[*]Security & Updates
[/LIST]

**[size="5"]General Community News[/size]**

***[size="3"]Jono Bacon: Introducing Lernid[/size]***

Last week, while at the Ubuntu Developer Summit in Dallas I mentioned in one of the round-tables about how wicked-cool it would be to have a desktop client for Ubuntu Open Week, Ubuntu Developer Week and other online tuition events that we run. One of the challenges we face every time we run these events is helping new community members figure out how IRC works. Ideally this should be as simple as running a program, selecting an event and connecting. On the flight home I hacked up a little quickly app to get started on this. It is called Lernid.

This is how it works: When you fire up Lernid it will ask you to select an event from a combo box and enter a nickname. The list of events in the combo box is actually held on the server side, which means we add new events and all Lernid clients will see them. This also means that other projects can use Lernid for their online events too. When the user hits OK it then loads up the main interface. In the upper pane the schedule is displayed for the currently selected event, the bottom left pane shows the classroom channel and the bottom right pane shows the chat channel. The user is now all set to take part in the session.

Right now I have focused on getting a basic Lernid together, and I have created a Lernid Launchpad project and published Lernid 0.1 to my PPA.

[LIST]
[*]Lernid Launchpad project: [https://www.launchpad.net/lernid](https://www.launchpad.net/lernid)
[*]Lernid 0.1 at my PPA: [https://edge.launchpad.net/~jonobacon/+archive/ppa](https://edge.launchpad.net/~jonobacon/+archive/ppa)
[/LIST]

I think there is bags of room for additional features. Some ideas include:

[LIST]
[*]Filtering IRC channels – filter out the ‘QUESTION’ lines, hide join/part traffic etc.
[*]Scheduling – include a feature to schedule a given event on the system calendar.
[*]Notifications – pop up a box to indicate that an event is about to begin.
[*]Session leader tools – it could also be useful to include a feature for a session leader to scribe down notes, share links or twitter right from Lernid.
[/LIST]

Hopefully Lernid can act as a starting point for the community to add new features. Screenshots at the link.

[http://www.jonobacon.org/2009/11/25/introducing-lernid/](http://www.jonobacon.org/2009/11/25/introducing-lernid/)

***[size="3"]Mackenzie Morgan Interview[/size]***

Mackenzie goes by maco in IRC and lives in Washington, DC, loves studying languages, and is learning American Sign Language. She started experimenting with Linux in May of 2006 and has used Ubuntu since July of 2006 when a friend introduced her to it. Submitting a patch in 2008, she started doing MOTU team work and hasn't looked back since. Packaging wasn't a breeze when a friend tried to guide her along, but the Ubuntu Developer videos did the trick. She admits that "rewind" was her friend when it came to the packaging videos. Her favorite MOTU work however might just be triaging and fixing bugs. She has some great advice for folks wanting to help out in MOTU, "Don't be afraid", you don't have to be a programmer, just be willing to learn some new commands and general MOTU policy. Morgan also devotes her time to other groups including the DC LoCo team. So what is Mackenzie's focus going to be for Lucid? She says she wants to get through the huge backlog of patches in Launchpad. The Ubuntu Community is lucky to have such a tireless worker as Mackenzie Morgan.

[http://fridge.ubuntu.com/node/1943](http://fridge.ubuntu.com/node/1943)

***[size="3"]New Developers[/size]***

[LIST]
[*]Evan Broder joined the MOTU team
[/LIST]

  *Launchpad: [https://launchpad.net/~broder](https://launchpad.net/~broder)
  *MOTU application: [https://wiki.ubuntu.com/EvanBroder/MOTUApplication](https://wiki.ubuntu.com/EvanBroder/MOTUApplication)

[LIST]
[*]Alberto Milone was recommended for Core-Dev.
[/LIST]

[LIST]
[*]Launchpad: [https://launchpad.net/~albertomilone](https://launchpad.net/~albertomilone)
[*]Wiki: [https://wiki.ubuntu.com/AlbertoMilone](https://wiki.ubuntu.com/AlbertoMilone)
[*]Core Developer application: [https://wiki.ubuntu.com/AlbertoMilone/CoreDeveloperApplication](https://wiki.ubuntu.com/AlbertoMilone/CoreDeveloperApplication)
[/LIST]

[LIST]
[*]Adrian Perez was recommended for upload rights for azureus, eclipse and swt-gtk
[/LIST]

[LIST]
[*]Launchpad: [http://launchpad.net/~adrianperez-deb](http://launchpad.net/~adrianperez-deb)
[*]Uploader application: [https://wiki.ubuntu.com/AdrianPerez/PerPackageUploaderApplication](https://wiki.ubuntu.com/AdrianPerez/PerPackageUploaderApplication)
[/LIST]

**[size="5"]Ubuntu Stats[/size]**

***[size="3"]Bug Stats[/size]***

[LIST]
[*]Open (76109) +524 over last week
[*]Critical (33) +2 over last week
[*]Unconfirmed (39431) +344 over last week
[*]Unassigned (66751) +473 over last week
[*]All bugs ever reported (352677) +2061 over last week
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see  [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[size="3"]Translation Stats Karmic[/size]***

 1. Spanish (13157) -312 over last week
 2. Brazilian Portuguese (45576) -116 over last week
 3. French (46061) -784 over last week
 4. Swedish (65160) -400 over last week
 5. English (United Kingdom) (73135) -237 over last week

Remaining strings to translate in Ubuntu 9.10 "Karmic Koala", see more at: [https://translations.launchpad.net/ubuntu/karmic/](https://translations.launchpad.net/ubuntu/karmic/)

***[size="3"]Ubuntu Brainstorm Top 5 this week[/size]***

[LIST]
[*]Make launchpad package installation simple - [http://brainstorm.ubuntu.com/idea/22676/](http://brainstorm.ubuntu.com/idea/22676/)
[*]Finding alternatives to proprietary software is too difficult for newcomers - [http://brainstorm.ubuntu.com/idea/22661/](http://brainstorm.ubuntu.com/idea/22661/)
[*]Software descriptions are in English (not localized) - [http://brainstorm.ubuntu.com/idea/22696/](http://brainstorm.ubuntu.com/idea/22696/)
[*]Many docks - [http://brainstorm.ubuntu.com/idea/22664/](http://brainstorm.ubuntu.com/idea/22664/)
[*]A way to automate available solutions (workarounds, fixes,...) - [http://brainstorm.ubuntu.com/idea/22602/](http://brainstorm.ubuntu.com/idea/22602/)
[/LIST]

Ubuntu Brainstorm is a community site geared toward letting you add your ideas for Ubuntu. You can submit your own idea, or vote for or against another idea. [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

**[size="5"]LoCo News[/size]**

***[size="3"]Maryland LoCo Team State Tour Info[/size]***

The Maryland LoCo Team has started a new project called "The State Tour". The goal of this project is to go to a different parts of the state that are not close enough to our group's center to participate in person.
Currently the plan is once a month they will visit an area that is 45 minutes or further from their current meeting spot in Columbia, MD. They will go out and meet the people that are interested in Ubuntu and FOSS in different places. They hope to set a starting point for Ubuntu sub-teams in the areas we visit.

The first Tour stop will be in Finksburg, MD at the local library on December 5th from 9:30am until 11:30am. Among the plans for the visit are:

[LIST]
[*]The main presentation about Ubuntu
[*]A few demo machines so people can touch and feel an ubuntu machine
[*]Free Ubuntu CDs
[*]If a person brings a flash drive with 1gb or more of free space they'll create a LiveUSB disk for them!
[*]And the best part, Meeting New Friends!
[*]For more details please visit [http://mdtour.ubuntu-maryland.org/](http://mdtour.ubuntu-maryland.org/)
[/LIST]

[https://lists.ubuntu.com/archives/ubuntu-news-team/2009-November/000775.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2009-November/000775.html)

***[size="3"]Massachusetts LoCo: Can Ubuntu reach over 16,000 anime lovers in April[/size]***

The Ubuntu MA LoCo are organizing a booth at the upcoming 2010 Anime Boston convention and need support to get a booth and print materials to distribute! [http://blog.thesilentnumber.me/2009/11/can-ubuntu-reach-over-16000-anime.html](http://blog.thesilentnumber.me/2009/11/can-ubuntu-reach-over-16000-anime.html)

[LIST]
[*]Project page: [http://linuxfund.org/projects/ubuntu/](http://linuxfund.org/projects/ubuntu/)
[*]Press release: [http://www.ubuntu-massachusetts.com/news/1/](http://www.ubuntu-massachusetts.com/news/1/)
[/LIST]

Can Ubuntu reach over 16,000 anime lovers in April? Of course it can, with the support of the rapidly expanding super mega-awesome community...that's you all!

[https://lists.ubuntu.com/archives/ubuntu-news-team/2009-November/000777.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2009-November/000777.html)

***[size="3"]Ubuntu-cl: LoCo Team Contact Change[/size]***

Ubuntu Chile, one of the first Latin American Ubuntu Communities has a new LoCo Team Contact. Mauricio Peñaloza writes: "After a couple of months as the LoCo Contact of Ubuntu Chile, I’m very pleased to give the charge in very good hands! Yes, I’m talking about Cristian Barahona (aka cristianvirtual), he’s one of our Council Members, and the most important thing, a very good person. I hope he will make a good job of it with the help of all of us." The LoCo Council joins Mauricio in welcoming Cristian and wishing Ubuntu-cl the very best.

[http://effiejayx.wordpress.com/2009/11/26/ubuntu-cl-loco-team-contact-change/](http://effiejayx.wordpress.com/2009/11/26/ubuntu-cl-loco-team-contact-change/)

***[size="3"]Karmic Release Parties Nicaragua[/size]***

The Ubuntu Nicaragua LoCo Team celebrated the release of Ubuntu Karmic Koala with two events in capital city Managua. The fiesta kicked off on November 12, with a series of conferences in the Central American University (UCA). [http://go2.wordpress.com/?id=725X1342&site=leogg.wordpress.com&url=http%3A%2F%2Fwww.uca.edu.ni%2F](http://go2.wordpress.com/?id=725X1342&site=leogg.wordpress.com&url=http%3A%2F%2Fwww.uca.edu.ni%2F)

Keandro Gomez gave his usual talk about how to get involved and contribute with the community. Second on line was benevolent dictator Adolfo “K” Fitoria, who showed everyone the latest news on Kubuntu 9.10, followed by the Gnome fan-boy José Ernesto Dávila with all the goodies in Ubuntu 9.10, including a great presentation of gnome shell. Then multimedia guru Rodrigo “RoRo” Rodríguez gave an introduction to video and audio editing in Ubuntu, and last but not least, daredevil Marcelo Gutierrez showed the awesomeness of Xubuntu. 9.10. It was a cool event, lots of new faces and many people interested in getting involved with the community. After the event, the party continued with some cold beers at a local bar.

The following week, on November 20, the Ubuntu Ninjas crashed the Pizza Bash 11 event at the Mansión Teodolinda hotel. There was some BoF sessions, including one about GPG keys and the attendees got the opportunity to test drive Karmic.

Special thanks goes to Neville Cross from the local Fedora community for taking pictures of both events and for letting us raid the PB11 event.

[LIST]
[*]Pictures: [http://go2.wordpress.com/?id=725X1342&site=leogg.wordpress.com&url=http%3A%2F%2Fpicasaweb.google.com%2Fnacross%2FKrp](http://go2.wordpress.com/?id=725X1342&site=leogg.wordpress.com&url=http%3A%2F%2Fpicasaweb.google.com%2Fnacross%2FKrp)
[*]Pictures: [http://go2.wordpress.com/?id=725X1342&site=leogg.wordpress.com&url=http%3A%2F%2Fpicasaweb.google.com%2Fnacross%2FPizzaBash11](http://go2.wordpress.com/?id=725X1342&site=leogg.wordpress.com&url=http%3A%2F%2Fpicasaweb.google.com%2Fnacross%2FPizzaBash11)
[/LIST]

[http://leogg.wordpress.com/2009/11/26/karmic-release-parties-nicaragua/](http://leogg.wordpress.com/2009/11/26/karmic-release-parties-nicaragua/)

**[size="5"]Ubuntu Forums News[/size]**

***[size="3"]Tutorial of the Week[/size]***

When the trend is to always have shinier and more interactive installs, some like them minimal, because they use older machines, netbooks, laptops configured for speed.. You can tweak and adjust Linux distributions to fit your own needs, that is one of the magic features Ubuntu (and other distributions) offers.

TheShiv ([http://ubuntuforums.org/member.php?u=691298](http://ubuntuforums.org/member.php?u=691298)) started a thread this spring, and others have taken over since then: "How To Achieve Ubuntu-Desktop-Minimal." If you skip the past few negative comments, the thread is full of useful information, suggestions, scripts and points of view. For karmic tweaks, please reach the end of the thread.

Enjoy !

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

**[size="5"]The Planet[/size]**

***[size="3"]Laura Czajkowski: UDS Summaries[/size]***

Thanks to Laura, we can get a real feel for the day to day happenings at the recently concluded UDS Lucid conference in Dallas. Not only does she include lots of info on the daily sessions, but also gives us a look at the fun things that go on after the sessions have ended. After all, all work and no play make Jack/Jill a dull boy/girl. Check out the following links to get all the news on UDS Lucid.

[LIST]
[*][http://www.lczajkowski.com/2009/11/17/uds-lucid-day-1/](http://www.lczajkowski.com/2009/11/17/uds-lucid-day-1/)
[*][http://www.lczajkowski.com/2009/11/26/uds-lucid-day-2/](http://www.lczajkowski.com/2009/11/26/uds-lucid-day-2/)
[*][http://www.lczajkowski.com/2009/11/26/uds-lucid-day-3/](http://www.lczajkowski.com/2009/11/26/uds-lucid-day-3/)
[/LIST]

[http://www.lczajkowski.com/](http://www.lczajkowski.com/)

***[size="3"]Andres Rodriguez: Ubuntizing People!![/size]***

About two months ago Andres made a post where he mentioned how he introduced some friends into Ubuntu… They showed their desired to see what it was and how it worked. The post is here: [http://www.roaksoax.com/2009/09/the-need-to-ubuntize-people](http://www.roaksoax.com/2009/09/the-need-to-ubuntize-people)

Before going to the UDS he showed one of his friends Ubuntu working with full Compiz Effects and his friend was just amazed. He told Andres that it just looks like a Mac!! Andres told him… well they are similar and explained to him the whole concept behind Unix and Linux again. Back from the UDS, Andres brought back some CDs and the Ubuntu User Magazine. He gave a CD and the Magazine to his friend (with some stickers) and he was just excited about it. He told Andres: “I just installed Ubuntu and I love it!!.” Andres thought, “wow, he just did it by himself without requiring my help!!”… and well, he did it using Wubi… but, that doesn’t not matter… he took his first step by jumping into it by himself!! Afterward he told me that he had been using Ubuntu for quite a few hours, he was setting up all he needed. He got Empathy and Evolution with his accounts working without any help.

In conclusion… Ubuntu ROCKS!! Andres was not only happy, but amazed that he did pretty much everything he needed without any help. He is just happy that he does not have the same problems he has with Windows in the same time frame. This is all thanks to the developers who put so much effort in the Upstream Projects, and to all of those who make Ubuntu Rock!!

[http://www.roaksoax.com/2009/11/ubuntizing-people](http://www.roaksoax.com/2009/11/ubuntizing-people)

***[size="3"]Amber Graner: UDS and Ubuntu Women[/size]***

At UDS there were 3 sessions dedicated to the progression of the Ubuntu Women Project. Amber was excited and still is about the fact that the group has grown to the point where they are beginning to have measurable goals for each cycle. That to Amber is a WIN! Out of the sessions came a Blue Print [https://blueprints.edge.launchpad.net/ubuntu-women.org/+spec/community-ubuntu-women-project](https://blueprints.edge.launchpad.net/ubuntu-women.org/+spec/community-ubuntu-women-project) and specs around the goals they want to complete during the Lucid cycle. [https://wiki.ubuntu.com/Roadmaps/Lucid/UbuntuWomen](https://wiki.ubuntu.com/Roadmaps/Lucid/UbuntuWomen)

Ubuntu Women is focusing on recruiting, supporting, encouraging and retaining women in the Ubuntu project, and does so by providing positive role models, mentoring, encouragement, and resources for women within the Ubuntu community. Amber hopes you will take a look at the Blue Print, and the Specs and get just as excited as she is about bringing more women into the Ubuntu Project, and seeing the Ubuntu Woman Project Members work together as a team to accomplish these goals.

[http://amber.redvoodoo.org/2009/11/uds-and-ubuntu-women.html](http://amber.redvoodoo.org/2009/11/uds-and-ubuntu-women.html)

***[size="3"]Harald Sitter: Ubuntu One KDE Tech Preview[/size]***

[LIST]
[*]NOTE: This is not for production machines or anyone unable to cope with frequent system crashes.
[/LIST]

Herald has started working on getting Ubuntu One a KDE frontend. First results are now available as a tech preview. The Ubuntu One KDE client is a small application that lives in your system tray (the thing next to your clock). It notifies you when a new transfers from or to the Ubuntu One server have been started and when they are finished. Additionally it will show up whenever there is a problem with the connection. [http://gitorious.org/ubuntuone-client-kde/ubuntuone-client-kde](http://gitorious.org/ubuntuone-client-kde/ubuntuone-client-kde)

You can get an impression of what it does from the two prototype sceencasts:

[LIST]
[*][http://aplg.kollide.net/screencasts/ubuntuone-kde1.ogv](http://aplg.kollide.net/screencasts/ubuntuone-kde1.ogv)
[*][http://aplg.kollide.net/screencasts/ubuntuone-kde2.ogv](http://aplg.kollide.net/screencasts/ubuntuone-kde2.ogv)
[/LIST]

What can you expect from this preview? Crashes, startup failures and missing functionality, as to be expected from a tech preview. Please note that this preview is directly based on a prototype, so the internals are most likely to change a lot. You can get the client from a special PPA. Just add the source lines and install ubuntuone-client-kde. Before you do anything you need to run the GNOME client (ubuntuone-client-applet) at least once to obtain authentication from the Ubuntu One server, then you can just quit the GNOME client and start the KDE one (you need to start it with --nofork or it will not work). PPA - [https://launchpad.net/~apachelogger/+archive/ubuntuone-kde](https://launchpad.net/~apachelogger/+archive/ubuntuone-kde) I have also create a screencast showing all that: [http://aplg.kollide.net/screencasts/ubuntuone-kde3.ogv](http://aplg.kollide.net/screencasts/ubuntuone-kde3.ogv)

Once authentication is implemented and the client works properly Herald will take a look into implementing Dolphin integration (most likely via a kio slave, due to lack of other options). Meanwhile the Desktop CouchDB Akonadi resources get finished. So we will hopefully have meaningful integration into the KDE Platform by the time Kubuntu 10.04 LTS gets released.

[http://apachelog.blogspot.com/2009/11/ubuntu-one-kde-tech-preview.html](http://apachelog.blogspot.com/2009/11/ubuntu-one-kde-tech-preview.html)

**[size="5"]In The Press[/size]**

***[size="3"]Chromium OS, Moblin, Ubuntu Netbook Remix Benchmarks[/size]***

Phoronix's Michael Larabel informs us that Intel released Moblin 2.1 earlier this month, Canonical released Ubuntu Netbook Remix 9.10 late last month, and various other vendors have offered up their fall distribution refreshes too. Oh yeah, and Google just released the Chromium OS source code a few days ago! With all of the netbook-focused distribution updates, Larabel found it was time to run an onslaught of new benchmarks, comparing some of the leaders in this field along with running a couple full-blown desktop distributions for this round of Linux netbook benchmarking. The results were certainly interesting to say the least and surprised Larabel in some areas. When it came to netbook performance tests from the desktop, there were not too many dissenting test results between the gaming, video playback, encoding, and disk test profiles. However, for those tests that did differ, Ubuntu Netbook Remix 9.10 usually came out in front as being the best performer. [http://www.phoronix.com/scan.php?page=article&item=chromium_moblin_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=chromium_moblin_benchmarks&num=1)

***[size="3"]Google's New Chrome OS Partner: Ubuntu[/size]***

Serdar Yegulalp of Information Week tells us that among the people Google (NSDQ: GOOG)'s partnering with to build Chrome OS, there's now a very familiar name: Canonical, the folks behind Ubuntu. In their words: "Canonical is contributing engineering to Google under contract" (for Chrome OS). That doesn't mean Chrome OS and Ubuntu are going to become interchangeable, though. While the two operating systems share some core components, Google Chrome OS will provide a very different experience to Ubuntu. Ubuntu will continue to be a general purpose OS, however Chrome has been designed to provide a very specific -- one might even say closed-ended -- set of experiences. From the way Canonical talks about this partnership, Google's clearly interested in more than just a respin of what's under Ubuntu's hood. They want good minds, too, like the folks on Canonical's design team. And one great mind is better than any hundred thousand lines of code. [http://www.informationweek.com/blog/main/archives/2009/11/googles_new_chr.html;jsessionid=YPX2VUTPCLON1QE1GHPCKH4ATMY32JVN](http://www.informationweek.com/blog/main/archives/2009/11/googles_new_chr.html;jsessionid=YPX2VUTPCLON1QE1GHPCKH4ATMY32JVN)

***[size="3"]Nouveau To Enter The Ubuntu 10.04 LTS Kernel[/size]***

Michael Larabel of Phoronix reports that the Nouveau driver, the X.Org project designed to provide a open-source NVIDIA graphics driver for Linux with 2D/3D/Video acceleration that's developed by cleanly reverse-engineering NVIDIA's binary driver, is about to get promoted in Ubuntu 10.04 LTS. Not too many details beyond that or their intentions are known at this time, but Nouveau developers are currently being asked about the matter. For Ubuntu Lucid we will likely not see Nouveau's Gallium3D driver appear for providing OpenGL acceleration by default for this NVIDIA hardware, but even just a proper 2D driver will be quite exciting and a huge step forward. This will also mean that a majority of the graphics cards (ATI, Intel, and NVIDIA) would all be supported by kernel mode-setting in this next Ubuntu release. [http://www.phoronix.com/scan.php?page=news_item&px=NzczMA](http://www.phoronix.com/scan.php?page=news_item&px=NzczMA)

***[size="3"]Canonical Drops Support for LPIA on Ubuntu 10.04[/size]***

Phoronix's Michael Larabel notes that two years ago Ubuntu began supporting LPIA, or the Low-Power Intel Architecture. LPIA is i386, but with different compile-time optimizations. LPIA was in use by the Ubuntu Mobile project with Intel's recent mobile CPUs supporting this lower-power architecture. Tests that Larabel carried out earlier this year at Phoronix showed Ubuntu's LPIA-based MID spin can conserve 10%+ power. However, Canonical is now abandoning this Intel architecture. Steve Kowalik has announced on behalf of the Ubuntu development community that the LPIA architecture will be retired. Beginning with Ubuntu 10.04 LTS and going forward, LPIA packages will not be available. [http://news.softpedia.com/news/Canonical-Drops-Support-for-LPIA-on-Ubuntu-10-04-128175.shtml](http://news.softpedia.com/news/Canonical-Drops-Support-for-LPIA-on-Ubuntu-10-04-128175.shtml)

***[size="3"]Giving up the GIMP is a sign of Ubuntu's mainstream maturity[/size]***

ARS Technica's Ryan Paul reminds us that Canonical hosted its biannual Ubuntu Developer Summit (UDS) last week in Dallas, Texas. Paul was one of many open source software developers who attended the event and participated in the collaborative process of planning Ubuntu 10.04, the next version of the popular Linux distribution. An important part of the 10.04 roadmap that emerged during UDS is a tentative plan to remove the GIMP, the GNU Image Manipulation Tool, from the default Ubuntu installation. Although this decision is viewed by some as controversial, the reasoning behind it is valid. The removal of a niche professional graphics editing tool reflects Ubuntu's growing maturity as a mainstream platform for regular users. [http://arstechnica.com/open-source/news/2009/11/giving-up-the-gimp-is-a-sign-of-ubuntus-mainstream-maturity.ars](http://arstechnica.com/open-source/news/2009/11/giving-up-the-gimp-is-a-sign-of-ubuntus-mainstream-maturity.ars)

***[size="3"]Ubuntu 10.04 LTS Has 100 Paper Cuts Again[/size]***

Michael Larabel of Phoronix recalls that during the Ubuntu 9.10 development cycle there was an Ubuntu project to address paper cuts in Ubuntu, or rather small usability bugs in Ubuntu and the Linux desktop that are often only minor impairments or annoyances, but these easy-to-fix issues have never been heavily targeted for correction. Most of the 100 paper cuts targeted for Ubuntu 9.10 were addressed (the official count seems to be at 76), but this project is going to live on with Ubuntu 10.04 LTS. Ubuntu 10.04 LTS will have ten rounds to fix 100 (or more) paper cuts in time for the Lucid Lynx before it is released in April. Each of these paper cut healing rounds are themed from "Kibosh on Karmic" to "Paper Jam: Sound & Video" to "Paper Jam: Compiz Settings." If all goes according to plan, 100 paper cuts will be healed by the end of February. [http://www.phoronix.com/scan.php?page=news_item&px=NzczNA](http://www.phoronix.com/scan.php?page=news_item&px=NzczNA)

***[size="3"]The Incredible Guide to NEW Ubuntu (Karmic Koala)[/size]***

Make Use Of's Simon Slangen takes note that there are a lot of people still stuck with Windows because it’s the ‘easier alternative’. Linux is both cheaper and more versatile than Microsoft’s operating system, but the learning curve has frightened off many people. In the past, "Make Use Of" published "A Newbie’s Getting Started Guide to Linux", aimed at the making you familiar with the most basic Linux principles. With the release of a new Ubuntu (Linux for human beings) distribution, Karmic Koala, "Make Use Of" felt it was time to go back to the roots and beyond. They teamed up with Guvnr.com to create the Ubuntu Karmic Koala Bible – a guide that’s both great for Linux initiates, and invariably useful for Linux intermediates. With over fifty pages of copy-paste tutorials, this guide belongs in the virtual library of every Linux user! Follow this link for more information and the Ubuntu Karmic Koala Bible: [http://www.makeuseof.com/tag/the-incredible-guide-to-ubuntu-karmic-koala-linux-pdf/](http://www.makeuseof.com/tag/the-incredible-guide-to-ubuntu-karmic-koala-linux-pdf/)

***[size="3"]Ubuntu 9.10 on SSD[/size]***

Dmitri Popov of Linux Magazine had been thinking about replacing the hard disk on his production notebook with a solid-state disk (SSD) for quite a while. So when he stumbled upon a good offer on Kingston 64GB SSDNow V series SSD he decided to take the plunge. While Popov was hoping to get a slight speed boost, his expectations weren't very high: the Kingston V-series SSD is designed for the consumer market and the disk offers relatively modest read/write speeds. He was pleasantly surprised when the Ubuntu 9.10's installer zoomed through the installation process in about 10 minutes. Popov was completely blown away by how fast his notebook booted into Ubuntu 9.10 -- it took about 10-15 seconds. While Popov hasn't done any scientific measurements, he does say that switching to the SSD disk has had a more significant impact on the system's performance than doubling the amount of RAM. [http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Ubuntu-9.10-on-SSD](http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Ubuntu-9.10-on-SSD)

**[size="5"]In The Blogosphere[/size]**

***[size="3"]Pegatron Displays 10-inch Ubuntu Smartbook[/size]***

On Friday November 20th, at the Connected Community Technical Symposium in Taipei, a 10-inch Ubuntu ARM processor based Smartbook was being displayed by Pegatron.  Smartbooks features include the always on feeling of a mobile phone - boots quickly and less power.  Pegatron plans on releasing a $200 smartbook early next year.  Many of the details still haven't been released yet but take a look and see if this is something you could see yourself using in the future.[http://www.coated.com/pegatron-displays-10-inch-ubuntu-smartbook-1123090002/](http://www.coated.com/pegatron-displays-10-inch-ubuntu-smartbook-1123090002/)

***[size="3"]Why Does Everyone Hate Ubuntu?[/size]***

Bruce Byfield, Datamation,  discusses both the upside and downside to being the most popular Linux distribution ever.  In this article Byfield sites a Christopher Dawson article where Ubuntu users are estimated at 13 million.  Byfield takes a look at the flip side of Ubuntu's popularity "If Ubuntu is the most popular distribution, it is also the most hated."  In this article Byfield talks to Jono Bacon, Ubuntu Community Manager about this flip side. The dialogue between Byfield and Bacon bring to light some interesting ideas on how Ubuntu can be both popular and hated at the same time.  The article is full of links to supporting the popularity of Ubuntu as well as possible reasons for the "hatred".  Byfield discusses, "Complaints represent more eyeballs", "The Ire of the old timers", and "The three ages of success".  If you want to know more about "Why Does Everyone Hate Ubuntu?", take moment to read Byfield's article in detail. [http://itmanagement.earthweb.com/features/article.php/3849976/Why-Does-Everyone-Hate-Ubuntu.htm](http://itmanagement.earthweb.com/features/article.php/3849976/Why-Does-Everyone-Hate-Ubuntu.htm)

***[size="3"]Canonical Landscape And Ubuntu: Government Boost?[/size]***

Joe Panettieri, WorksWithU, discusses Canonical's Landscape (systems management and Monitoring tool for Ubuntu systems). Looks like Autonomic Resources has cleared the way to have Landscape approved on its GSA  (Government Services Administration) Price list.  As Panettieri states in his article this does not mean that Landscape has won and official US Government business, it just means it's cleared a path to make it easier to gain some government business.  As Panettieri mentions in this article the relationship with Autonomic Resources could be a boost for Canonical, Ubuntu and Landscape in the federal market. [http://www.workswithu.com/2009/11/24/canonical-landscape-and-ubuntu-government-boost/](http://www.workswithu.com/2009/11/24/canonical-landscape-and-ubuntu-government-boost/)

***[size="3"]Ubuntu: Time for Another Reality Check[/size]***

Christopher Tozzi, WorksWithU, talks about criticism of Ubuntu, and Canonical as "nothing new".  He admits in this "Reality Check" article that "no matter how many flaws one can find with Ubuntu and its developers, they have succeeded in respects where every similar endeavor to date has failed; namely, they’ve achieved a public image that blows every other Linux distribution out of the water."  Tozzi, talks about "Canonical-haters" and where this feeling stems from.  Tozzi,  discusses why Ubuntu is "Not the Best" and "What Matters".  Year of the Linux Desktop, who knows but Tozzi reminds readers "no matter how much we may question certain aspects of Ubuntu, or certain practices of its developers, anyone who hopes to see the Linux desktop go mainstream and the proprietary monopoly broken can’t deny the centrality of Canonical in bringing that vision closer to reality in a way that sets Ubuntu far apart from all its competitors." [http://www.workswithu.com/2009/11/24/ubuntu-time-for-another-reality-check/](http://www.workswithu.com/2009/11/24/ubuntu-time-for-another-reality-check/)

***[size="3"]Who’s afraid of Ubuntu Women?[/size]***

Matt Zimmerman, Canonical CTO, talks about the Ubuntu Women project in his post UDS blog  "Who’s afraid of Ubuntu Women?"  Zimmerman talks about the Gobby notes from the session as well as the roadmap that is and was in place before UDS.  In this post, Zimmerman talks about the goals for the Ubuntu Women project for the Lucid cycle:

[LIST]
[*]Clarify the purpose of the #ubuntu-women channel
[*]Create a safe space IRC channel
[*]Appoint a leaser of the Ubuntu Women Team
[*]Change the perception of Ubuntu Women
[/LIST]

Zimmerman sums up his post with "Hopefully that’s the end of this apparent stigma, and Ubuntu Women can get on with the business of helping the Ubuntu community to welcome more women." [http://mdzlog.alcor.net/2009/11/23/whos-afraid-of-ubuntu-women/](http://mdzlog.alcor.net/2009/11/23/whos-afraid-of-ubuntu-women/)

**[size="5"]In Other News[/size]**

***[size="3"]Full Circle magazine #31[/size]***

Full Circle - the independent magazine for the Ubuntu Linux community are proud to announce the release of our thirty-first issue.

This month:

[LIST]
[*]Command and Conquer.
[*]How-To: Program in Python – Part 5, The Perfect Server – Part 1, and Universe of Sound.
[*]My Story – The Conversion.
[*]My Opinion – Windows 7.
[*]Review – Linux Mint 7.
[*]MOTU Interview – Andreas Wenning.
[*]Top 5 – Subversion Clients.
[*]Ubuntu Women, Ubuntu Games and all the usual goodness!
[/LIST]

Download it here: [http://fullcirclemagazine.org/issue-31](http://fullcirclemagazine.org/issue-31)

[https://lists.ubuntu.com/archives/ubuntu-news-team/2009-November/000781.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2009-November/000781.html)

**[size="5"]Upcoming Meetings and Events[/size]**

***[size="3"]Monday, November 30, 2009[/size]***

==== Security Team Catch-up ====

[LIST]
[*]Start: 18:00 UTC
[*]End: 18:30 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: nothing formal, just a weekly catch-up.
[/LIST]

***[size="3"]Tuesday, December 1, 2009[/size]***

==== Ubuntu Mobile Team Meeting ====

[LIST]
[*]Start: 13:00 UTC
[*]End: 14:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/MobileTeam/Meeting](https://wiki.ubuntu.com/MobileTeam/Meeting)
[/LIST]

==== Technical Board Meeting ====

[LIST]
[*]Start: 15:00 UTC
[*]End: 16:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: None listed as of publication
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
[*]Agenda: None listed as of publication
[/LIST]

==== LoCo Teams Meeting ====

[LIST]
[*]Start: 18:00 UTC
[*]End: 19:00 UTC
[*]Location: IRC channel #ubuntu-locoteams
[*]Agenda: None listed as of publication
[/LIST]

==== EMEA Membership Meeting ====

[LIST]
[*]Start: 20:00 UTC
[*]End: 21:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/Membership/RegionalBoards/EMEA](https://wiki.ubuntu.com/Membership/RegionalBoards/EMEA)
[/LIST]

==== Ubuntu Beginners Team Meeting ====

[LIST]
[*]Start: 22:00 UTC
[*]End: 23:00 UTC
[*]Location: IRC channel #ubuntu-beginners
[*]Agenda: [https://wiki.ubuntu.com/BeginnersTeam/Meetings](https://wiki.ubuntu.com/BeginnersTeam/Meetings)
[/LIST]

==== Community Council Meeting ====

[LIST]
[*]Start: 22:00 UTC
[*]End: 24:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/CommunityCouncilAgenda](https://wiki.ubuntu.com/CommunityCouncilAgenda)
[/LIST]

***[size="3"]Wednesday, December 2, 2009[/size]***

==== Server Team Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meetin
[*]Agenda: [https://wiki.ubuntu.com/ServerTeam/Meeting](https://wiki.ubuntu.com/ServerTeam/Meeting)
[/LIST]

==== Cameroonian LoCoTeam monthly IRC meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 16:00 UTC
[*]Location: IRC channel #ubuntu-cm
[*]Agenda: [https://wiki.ubuntu.com/CameroonianTeam/NextMeeting](https://wiki.ubuntu.com/CameroonianTeam/NextMeeting)
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

***[size="3"]Thursday, December 3, 2009[/size]***

==== Ubuntu Java Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: None listed as of publication
[/LIST]

==== Ubuntu Translations Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/TranslatingUbuntu/Events/Meetings](https://wiki.ubuntu.com/TranslatingUbuntu/Events/Meetings)
[/LIST]

***[size="3"]Friday, December 4, 2009[/size]***

==== Lucid Weekly Release Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:30 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/ReleaseTeam/Meeting/2009-12-04](https://wiki.ubuntu.com/ReleaseTeam/Meeting/2009-12-04)
[/LIST]

***[size="3"]Saturday, December 5, 2009[/size]***

[LIST]
[*]None listed as of publication
[/LIST]

***[size="3"]Sunday, December 6, 2009[/size]***

[LIST]
[*]None listed as of publication
[/LIST]

**[size="5"]Updates and Security for 6.06, 8.04, 8.10, 9.04 and 9.10[/size]**

***[size="3"]Security Updates[/size]***

[LIST]
[*]USN-861-1: libvorbis vulnerabilities - [http://www.ubuntu.com/usn/USN-861-1](http://www.ubuntu.com/usn/USN-861-1)
[*]USN-862-1: PHP vulnerabilities - [http://www.ubuntu.com/usn/USN-862-1](http://www.ubuntu.com/usn/USN-862-1)
[/LIST]

***[size="3"]Ubuntu 6.06 Updates[/size]***

[LIST]
[*]sun-java5 1.5.0-22-0ubuntu0.6.06.1 - [https://lists.ubuntu.com/archives/dapper-changes/2009-November/012795.html](https://lists.ubuntu.com/archives/dapper-changes/2009-November/012795.html)
[*]langpack-locales 2.3.18.29 - [https://lists.ubuntu.com/archives/dapper-changes/2009-November/012796.html](https://lists.ubuntu.com/archives/dapper-changes/2009-November/012796.html)
[/LIST]

***[size="3"]Ubuntu 8.04 Updates[/size]***

[LIST]
[*]sun-java5 1.5.0-22-0ubuntu0.8.04 - [https://lists.ubuntu.com/archives/hardy-changes/2009-November/012332.html](https://lists.ubuntu.com/archives/hardy-changes/2009-November/012332.html)
[*]sun-java6 6-17-0ubuntu1.8.04 - [https://lists.ubuntu.com/archives/hardy-changes/2009-November/012333.html](https://lists.ubuntu.com/archives/hardy-changes/2009-November/012333.html)
[*]libvorbis 1.2.0.dfsg-2ubuntu0.3 - [https://lists.ubuntu.com/archives/hardy-changes/2009-November/012334.html](https://lists.ubuntu.com/archives/hardy-changes/2009-November/012334.html)
[*]tzdata 2009s~repack-0ubuntu0.8.04 - [https://lists.ubuntu.com/archives/hardy-changes/2009-November/012335.html](https://lists.ubuntu.com/archives/hardy-changes/2009-November/012335.html)
[/LIST]

***[size="3"]Ubuntu 8.10 Updates[/size]***

[LIST]
[*]libvorbis 1.2.0.dfsg-3.1ubuntu0.8.10.2 - [https://lists.ubuntu.com/archives/intrepid-changes/2009-November/009782.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-November/009782.html)
[*]tzdata 2009s~repack-0ubuntu0.8.10 - [https://lists.ubuntu.com/archives/intrepid-changes/2009-November/009783.html](https://lists.ubuntu.com/archives/intrepid-changes/2009-November/009783.html)
[/LIST]

***[size="3"]Ubuntu 9.04 Updates[/size]***

[LIST]
[*]gst-plugins-bad-multiverse0.10 0.10.11-0ubuntu1.1 - [https://lists.ubuntu.com/archives/jaunty-changes/2009-November/009936.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-November/009936.html)
[*]libvorbis 1.2.0.dfsg-3.1ubuntu0.9.04.2 - [https://lists.ubuntu.com/archives/jaunty-changes/2009-November/009937.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-November/009937.html)
[*]tzdata 2009s~repack-0ubuntu9.04 - [https://lists.ubuntu.com/archives/jaunty-changes/2009-November/009938.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-November/009938.html)
[/LIST]

***[size="3"]Ubuntu 9.10 Updates[/size]***

[LIST]
[*]image-store-proxy 1.0.4-0ubuntu1.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012059.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012059.html)
[*]xf86-input-evtouch 0.8.8-0ubuntu6.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012060.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012060.html)
[*]treeline 1.2.3-1ubuntu0.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012061.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012061.html)
[*]kdeedu 4:4.3.2-0ubuntu1.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012062.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012062.html)
[*]nautilus 1:2.28.1-0ubuntu3 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012063.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012063.html)
[*]deja-dup 10.2-0ubuntu1.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012064.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012064.html)
[*]bld 0.3.4.1-3ubuntu0.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012065.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012065.html)
[*]ifupdown-scripts-zg2 0.3-4ubuntu0.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012066.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012066.html)
[*]kdeplasma-addons 4:4.3.2-0ubuntu5.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012067.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012067.html)
[*]libvorbis 1.2.0.dfsg-6ubuntu0.1 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012068.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012068.html)
[*]tzdata 2009s-0ubuntu0.9.10 - [https://lists.ubuntu.com/archives/karmic-changes/2009-November/012069.html](https://lists.ubuntu.com/archives/karmic-changes/2009-November/012069.html)
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
[*]John Crawford
[*]Craig A. Eddy
[*]Dave Bush
[*]Isabelle Duchatelle
[*]Amber Graner
[*]Sayak Banerjee
[*]Liraz Siri
[*]And many others
[/LIST]

**[size="5"]Glossary of Terms[/size]**

 1. BOF - Birds of a Feather - An informal discussion group, based on a shared interest, discussing without a pre-planned agenda
 1. FOSS - Free Open Source Software.
 1. MOTU - Master Of The Universe - Developers responsible for the Universe and Multiverse repositories. [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

Other acronyms can be found at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary)

**[size="5"]Ubuntu - Get Involved[/size]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. [http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)

**[size="5"]Feedback[/size]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send them to [email]ubuntu-users@lists.ubuntu.com[/email].

Except where otherwise noted, content in this issue is licensed under a Creative Commons Attribution 3.0 License BY SA
[http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/)

---

