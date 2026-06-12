---
title: "Ubuntu Weekly Newsletter #195"
date: 2010-05-31
forum: Weekly Newsletter
---

### Post by akgraner on 2010-05-31
Welcome to the Ubuntu Weekly Newsletter, Issue 195 for the week May 23rd - May 29th, 2010. In this issue we cover Track the Desktop Team and UNE in Maverick, Ubuntu Server update for Maverick Meerkat. Ubuntu Foundations and Maverick Meerkat 10.10, Maverick Community Team Plans, Welcome: New Ubuntu Members, Winners of the 1st Annual Ubuntu Women World Play Announced, Ubuntu Stats, Ubuntu NC LoCo Team: Guitars to Goat Festivals: Ubuntu For All, Ubuntu Massachusetts LoCo Team: Ubuntu @ Intel LAN Party, Catalan LoCo Team: Ubuntu Lucid release party in Valencia, Why Launchpad Rocks: Great Bug Tracking, Ubuntu Forums News, Interview with Penelope Stowe, The behavioral economics of free software, Return of the Ubuntu Server papercuts, Rethinking the Ubuntu Developer Summit, Testing Indicator Application Menu Support, In The Press, In The Blogosphere, Landscape 1.5 Released with new Enterprise Features, Canonical Pushes Skype into Ubuntu Repository, Linux Security Summit 2010, Full Circle Magazine #37, Ubuntu UK Poscast: Three Friends, Upcoming Meetings and Events, Updates and Security and much much more!

**[size="5"]In This Issue[/size]**

[LIST]
[*]Track the Desktop Team and UNE in Maverick
[*]Ubuntu Server update for Maverick Meerkat
[*]Ubuntu Foundations and Maverick Meerkat 10.10
[*]Maverick Community Team Plans
[*]Welcome: New Ubuntu Members
[*]Winners of the 1st Annual Ubuntu Women World Play Announced
[*]Ubuntu Stats
[*]Ubuntu NC LoCo Team: Guitars to Goat Festivals: Ubuntu For All
[*]Ubuntu Massachusetts LoCo Team: Ubuntu @ Intel LAN Party
[*]Catalan LoCo Team: Ubuntu Lucid release party in Valencia
[*]Why Launchpad Rocks: Great Bug Tracking
[*]Ubuntu Forums News
[*]Full Circle Magazine: Interview with Penelope Stowe
[*]Matt Zimmerman: The behavioral economics of free software
[*]Thierry Carrez: Return of the Ubuntu Server papercuts
[*]Matt Zimmerman: Rethinking the Ubuntu Developer Summit
[*]Jono Bacon: Testing Indicator Application Menu Support
[*]In The Press
[*]In The Blogosphere
[*]Landscape 1.5 Released with new Enterprise Features
[*]Canonical Pushes Skype into Ubuntu Repository
[*]Linux Security Summit 2010
[*]Full Circle Magazine #37
[*]Ubuntu UK Poscast: Three Friends
[*]Upcoming Meetings and Events
[*]Updates and Security
[*]and much much more!
[/LIST]

**[size="5"]General Community News[/size]**

***[size="3"]Track the Desktop Team and UNE in Maverick[/size]***

Rick Spencer, Canonical Desktop Team Manager, gives an overview of what to expect for the Ubuntu Desktop in the Ubuntu 10.10 cycle. Highlights include:

Software Center:
The software center will get many UI improvements. However, the biggie is that we are going to figure out how enable application developers to target the current stable release for new apps! This means new apps that don't modify the underling Ubuntu platform and libraries will be made available in software-center even if the app was written after that version of Ubuntu released.

Gnome Changes:
We always decide at UDS what to take from new Gnome and how. We are very excited about Gnome 3.0, but due to tight release schedules, we are going to be cautious about Gnome 3.0 for Maverick. We will update to the current platform, and we will deliver gsettings and latest versions of apps as appropriate. As usual, we will make gnome-shell available to users who choose to use it.

Browsers and Apps:
We're going to try for Chromium by default in UNE, though we are sticking with Mozilla as the default in the Desktop Edition.

We are also changing to Shotwell as the default image library application.

xorg-xserver:
Interesting decision here is to hold off on promise of 3D support for -Intel 8xx series graphics. If the -Intel driver is not providing sufficient stability we may support those chips with Vesa, and perhaps deliver an older Intel driver for community support for those 8xx users who want to give it a go.

Social From the Start:
We'll work on gwibber start up time and robustness, but also work bake more integration of social services into the desktop.

To find out more about the Desktop team and the blueprints for the Maverick cycle go to:

[http://theravingrick.blogspot.com/2010/05/track-desktop-and-une-in-maverick.html](http://theravingrick.blogspot.com/2010/05/track-desktop-and-une-in-maverick.html)

***[size="3"]Ubuntu Server update for Maverick Meerkat[/size]***

Canonical Server Team Manager, Jos Boumans, writes about what's in store for the next release of Ubuntu Server.

With the Maverick cycle kicking off and UDS-M just behind us, it’s time to take a look at what’s in store for the next release of Ubuntu Server. In broad strokes, these will be the likely topics:

[LIST]
[*]Better integration with Upstart
[*]Further improvements to Mail & Cluster stack
[*]Adopt Ceph & GlusterFS, MongoDB, Drizzle & Cassandra
[*]Ease deployments & load balancing in the cloud
[*]For UEC: enabling kernel upgrades, virtio support, new admin UI, easier developer deployment, cloud on a stick and lots more testing
[*]Adopt & improve the following Java stacks: Tomcat, Ehcache, Hibernate, Hadoop and Pig
[/LIST]

Like last iteration, we’ll be reviewing and accepting blueprints proposed for Maverick on a per milestone basis. This week, we’ll review the work for Alpha2 and you’ll be able to track the progress on the work item tracker.
If you’d like to contribute to the Maverick release, please join us at our weekly IRC meetings on Tuesdays between 1800 and 1900 UTC on #ubuntu-meeting on irc.freenode.net. We could especially use your help in the papercuts project and bug triaging!

For more information on Ubuntu Server please go to:

[http://ubuntuserver.wordpress.com/2010/05/26/ubuntu-server-update-for-maverick-meerkat/](http://ubuntuserver.wordpress.com/2010/05/26/ubuntu-server-update-for-maverick-meerkat/)

***[size="3"]Ubuntu Foundations and Maverick Meerkat 10.10[/size]***

Duncan McGreggor, of the Canonical Foundations Team, discusses what to expect from the Foundations team for Maverick Meerkat, Ubuntu 10.10.

For those that don't know, The Ubuntu Foundations Team is responsible for delivering the core Ubuntu system, which is common to the whole Ubuntu family of products and services. For the past couple months, I had the pleasure and honor to work with the Foundations team, assisting in preparation for the Foundations Track at UDS and planning for the 10.10 cycle.

Below is a brief summary of the generated scheduled work items that were produced at UDS.

Boot Work: Several boot-related areas were identified for work during Maverick. These include the following:

[LIST]
[*]cd boot - by converting CD boot to use grub2 with its new graphical goodness, we will only need to maintain use of a single bootloader
[*]continued performance improvements
[*]grub2 framebuffer - the end goal being a near flicker-free graphical boot splash experience
[*]UEFI - support booting on systems that use UEFI firmware
[/LIST]

btrfs: In Maverick, we will be adding support for btrfs. Our tasks include such work as making ureadahead work with btrfs, adding btrfs support to grub2, integration work, and features support.

Cleanup: Just after an LTS release is a perfect time to clean house. We will be taking this opportunity to do so, with such work as dropping unused/unneeded packages from the base system, double-checking package dependencies, and investigating space-saving measures.

Installer Redesign: The installer is getting a serious make-over. Foundations and the Design team are working very closely together, improving the workflow, minimizing user clicks, improving the look-and-feel, and providing utility with increased ease of use.

Software Center: We want to get new applications into the Software Center, ideally providing developers with a means of generating revenue with the applications. For the former, we need to define some good social and technical processes to ensure ongoing quality and excellent producer/consumer experience. In conjunction with that, we need to work on getting a billing system in place.

Upstart: Upstart is getting major work this cycle. New and improved features include the following:

[LIST]
[*]Manual mode
[*]Resource limits
[*]Dependencies
[*]Better support for UIs that want to use Upstart
[*]Simple skeleton to make life easier for sysadmins
[*]Provide an API for services and tasks so that folks don't have to think about the event-based model if they don't need to
[*]Explore the conversion of conf files into jobs
[*]Possibly extend the debug capabilities into an interactive mode
[*]Improve job disabling
[/LIST]

Foundations will also be working closely with the server team to get their init scripts converted to Upstart. Conversely, the Kernel team will be providing new features that will allow Foundations to fully develop the planned Upstart features.

Miscellaneous: There is lots of other work we'll be doing, some of which are highlighted in the following:

[LIST]
[*]i686 Default Compile
[*]Stop building the ia64 and sparc community ports
[*]Multiarch Support for gcc, binutils, dpkg, and apt
[*]Foundations Python improvements
[*]Upgrade and install testing
[/LIST]

To see the blueprints related to each of the these work items and to find out more about The Foundations Team please go to:

[http://oubiwann.blogspot.com/2010/05/ubuntu-foundations-and-maverick-meerkat.html](http://oubiwann.blogspot.com/2010/05/ubuntu-foundations-and-maverick-meerkat.html)

***[size="3"]Jono Bacon: Maverick Community Team Plans[/size]***

Jono Bacon, Ubuntu Community Team Manager discusses what to expect from the Community Team during the Ubuntu 10.10 cycle.

As many of you will know, I manage the Ubuntu Community Team at Canonical, which has horsemen Holbach, Castro and Planella in it. A large chunk of my job is to take into account the wide range of needs from our different stakeholders (community teams, Canonical teams, upstreams etc) and to flesh out a strategy for my team for each cycle. To do this I gather input and feedback from the team and these stakeholders and put together strategy that will guide the team’s work through the cycle. Today I want to share this strategy with you all.
Most components in this strategy includes a blueprint which itself includes a set of actions that outlines the goals for Maverick. The benefit of this approach is that you can subscribe to blueprints you are interested in and keep track of those projects as we work through them. If there are elements of these blueprints that you would like to contribute to and get involved with, do let us know.

Below is a list of areas the Ubuntu Community Team will be focusing on during the Ubuntu 10.10 cycle:

[LIST]
[*]Ayatana
[*]Daily Builds
[*]Developer Growth
[*]Patch Review
[*]Upstreams
[*]Best Practice
[*]Translations
[*]Software Delivery
[*]Infrastructure Improvements
[*]Regular Cycle Activities
[/LIST]

As you can see the Community Team will have a lot to keep them busy.  To read the article in full, find out how you can get involved as well as see the blueprints for each of these areas go to:

[http://www.jonobacon.org/2010/05/28/maverick-community-team-plans/](http://www.jonobacon.org/2010/05/28/maverick-community-team-plans/)

***[size="3"]Welcome: New Ubuntu  Members[/size]***

Welcoming all new Ubuntu members - Congratulations!

Roman Azarenko

[LIST]
[*][https://wiki.ubuntu.com/BasicXP](https://wiki.ubuntu.com/BasicXP)
[/LIST]

Known as BasicXP, Roman Azarenko contributues to translation, Q&A, bug tracking and is part of Moscow LoCo Team.
[https://lists.ubuntu.com/archives/ubuntu-news-team/2010-May/001072.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2010-May/001072.html)

Manoj Iyer

[LIST]
[*][https://wiki.ubuntu.com/ManojIyer](https://wiki.ubuntu.com/ManojIyer)
[*][https://launchpad.net/~manjo](https://launchpad.net/~manjo)
[/LIST]

Manoj has been an Ubuntu user since Warty.  He's been working on the Ubuntu kernel for a few years now and is responsible for the new hardware testing tools released over the last year. Outside of his work on the kernel, he's
involved in the Texas LoCo team.

David Tomaschik

[LIST]
[*][https://wiki.ubuntu.com/Matir](https://wiki.ubuntu.com/Matir)
[*][https://launchpad.net/~matir](https://launchpad.net/~matir)
[/LIST]

David has been very active in Georgia both as an organizer of Atlanta LinuxFest (and its UbuCon) and now as the Georgia LoCo Team leader.  He's also been working with BugSquad both as a triager and in a developer capacity writing patches.  When he's not doing those, he's converting new users.

Pete Graner

[LIST]
[*][https://wiki.ubuntu.com/PeteGraner](https://wiki.ubuntu.com/PeteGraner)
[*][https://launchpad.net/~pgraner](https://launchpad.net/~pgraner)
[/LIST]

Pete's been working on Ubuntu since Hardy and managing the kernel team since the start of the Intrepid release cycle and by all accounts done a great job of it.  When he's not busy traveling for work or traveling to speak at
LinuxFests around the US, he spends some time with the North Carolina LoCo.

[https://lists.ubuntu.com/archives/ubuntu-news-team/2010-May/001075.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2010-May/001075.html)

For more information on Ubuntu Membership please go to:

[https://wiki.ubuntu.com/Membership](https://wiki.ubuntu.com/Membership)

***[size="3"]Winners of the 1st Annual Ubuntu Women World Play Announced[/size]***

Jono Bacon announced the Winners of the 1st Annual Ubuntu Women World Play Day Competition via his UStreamTV cast on May 28th, 2010.

The Community pick and winner of the Terra A20 Ubuntu Netbook is Photo #25 Orla O'Donohue.

Canonical CEO Jane Silber's pick and winner of the Dell Netbook is Photo #20 Jordan McCarthy.

The name drawn by Jono Bacon, Ubuntu Community Manager, and winner of the Canonical-sponsored Ubuntu SWAG and ZaReason USB Necklace is Photo #18 - Erika Hamilton.

All winners listed above will also receive a complimentary subscription, of their choice, to either Linux Pro or Ubuntu User magazine.

If you haven't had a chance to look at all the photos submitted please do.

CONGRATULATIONS to Orla O'Donohue, Jordan McCarthy, Erika Hamilton!

For more information on the Ubuntu Women World Play, sponsors, and winners go to:

[http://fridge.ubuntu.com/node/2046](http://fridge.ubuntu.com/node/2046)

**[size="5"]Ubuntu Stats[/size]**

***[size="3"]Bug Stats[/size]***

[LIST]
[*]Open (76831) -4377 over last week
[*]Critical (30) +2 over last week
[*]Unconfirmed (36553) +3 over last week
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see:

[https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[size="3"]Translation Stats Lucid[/size]***

 1. English (United Kingdom) (710) -0 over last week
 2. Spanish (10601) -83 over last week
 3. Brazilian Portuguese (35681) -129 over last week
 4. French (39486) -245 over last week
 5. German (54716) -142 over last week

Remaining strings to translate in Ubuntu 10.04 "Lucid Lynx", see more at:

[https://translations.launchpad.net/ubuntu/lucid/](https://translations.launchpad.net/ubuntu/lucid/)

***[size="3"]Ubuntu Brainstorm Top 5 this week[/size]***

[LIST]
[*]Users don't know which application they need - [http://brainstorm.ubuntu.com/idea/24921/](http://brainstorm.ubuntu.com/idea/24921/)
[*]Ubuntu Control Center - [http://brainstorm.ubuntu.com/idea/24934/](http://brainstorm.ubuntu.com/idea/24934/)
[*]Ubuntu Software Center doesn't remove file configuration - [http://brainstorm.ubuntu.com/idea/24963/](http://brainstorm.ubuntu.com/idea/24963/)
[*]Automatically select the user in GDM if there's only one - [http://brainstorm.ubuntu.com/idea/24977/](http://brainstorm.ubuntu.com/idea/24977/)
[*]Error messages in non-English languages - [http://brainstorm.ubuntu.com/idea/24974/](http://brainstorm.ubuntu.com/idea/24974/)
[/LIST]

Ubuntu Brainstorm is a community site geared toward letting you add your ideas for Ubuntu. You can submit your own idea, or vote for or against another idea. [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

**[size="5"]LoCo News[/size]**

***[size="3"]Ubuntu NC LoCo Team: Guitars to Goat Festivals: Ubuntu For All[/size]***

Amber Graner, of the North Carolina LoCo team, as well as Pete Graner and Jeremy Fooshee, Ubuntu Kernel Team members, attended the 1st Annual American Dairy Goat Festival, held in Spindale, on May 22, 2010.  There were between 1000 and 1500 people who reportedly visited the Festival between 9am and 7pm last Saturday.  Amber notes that there were some users of Ubuntu who live in the area.  She also states that she talked to local businesses and individuals about migrating to Ubuntu.

To Read more about Guitars and Goat Festivals go to:

[http://akgraner.com/?p=471](http://akgraner.com/?p=471)

***[size="3"]Ubuntu Massachusetts LoCo Team: Ubuntu @ Intel LAN Party[/size]***

Martin Owens of the Massachusetts LoCo Team describes his participation in this yearly event where some local Ubuntu advocates go and attempt to convince local hard core gamers to try and have a dual boot of Ubuntu and see what progress is being made on gaming in the platform.

It was a very positive event with a great number of people exclaiming their pain at not being able to run their most cherished games on Ubuntu. Almost everyone knew about Ubuntu and a great number of them loved it… if it wasn’t for some of the pain you have to go through to make it work.

That’s where getting the word out about playonlinux and getdeb… programs and sites that can really make a difference to the average PC gamer trying out Ubuntu.

To see the pictures from the event and to learn more about Martin Owens and the Massachusetts LoCo Team go to:

[http://doctormo.org/2010/05/24/ubuntu-intel-lan-party/](http://doctormo.org/2010/05/24/ubuntu-intel-lan-party/)

***[size="3"]Catalan LoCo Team: Ubuntu Lucid release party in Valencia[/size]***

David Planella blogs about the Catalan LoCo Teams's release party .

Last weekend the Catalan LoCo team reunited again to celebrate yet another unforgettable Ubuntu release party in València, at the emblematic Octubre Culture Centre in the heart of the city. There were two days packed with activities, presentations, conferences, unconferences, installs, excellent food and even better company. In summary, good fun for everyone

As most of the LoCo team members come from different parts of the Catalonia region, they were traveling on Friday to be fresh for the big day on Saturday. Be it with car, train or motorbike, everyone had arrived by the evening and some of us met for a nice  dinner and enjoyed the warm Valencian night.

To read the full post,find out more about this two day event and see all the pictures go to:

[http://davidplanella.wordpress.com/2010/05/26/ubuntu-lucid-release-party-in-valencia/](http://davidplanella.wordpress.com/2010/05/26/ubuntu-lucid-release-party-in-valencia/)

***[size="3"]Launchpad News[/size]***

***[size="3"]Why Launchpad Rocks: Great Bug Tracking[/size]***

Jono Bacon continues his "Why Launchpad Rocks" series.  In this installment Jono talks about Launchpad's Bug Tracking features.

Jono notes, "The general consensus seems to be that everyone thinks that all bug trackers suck. A strong view, but one not entirely without merit given the fact that a vast majority of bug trackers do indeed suck. In the past I have mainly used Trac, SourceForge, Mantis and Bugzilla, and I have to say that I find Launchpad best suited to my needs and more importantly, most usable by my users who I expect to file a bug when something goes belly up.

I just want to zip through some of the reasons why I find bug tracking in Launchpad a breeze and well suited to all of my applications."

Jono breaks those reasons into the following areas:

[LIST]
[*]Simplicity
[*]Bug Linking
[*]Fixes
[*]Extensibility
[/LIST]

To read the more about the Bug Tracking features Launchpad offers please go to:

[http://www.jonobacon.org/2010/05/24/why-launchpad-rocks-great-bug-tracking/](http://www.jonobacon.org/2010/05/24/why-launchpad-rocks-great-bug-tracking/)

**[size="5"]Ubuntu Forums News[/size]**

***[size="3"]Tutorial of the Month[/size]***

June 2010 - AppArmor

What a subject... We'll step out of the T&T section this month to visit the Security Discussions area.
bodhi.zazen ([http://ubuntuforums.org/member.php?u=89054](http://ubuntuforums.org/member.php?u=89054)) spends a lot of time in this section, educating and providing support.

apparmor (Application Armor) does what its name suggests, it helps protecting the system if an application gets compromised. apparmor works with specific application profiles that regulate and define the applications access in addition to the usual system permissions (which apparmor can only restrict).

By default, Ubuntu comes with apparmor profiles for CUPS, evince, dhclient3, Firefox (which is not enabled) and the guest session.

The first thread to read is Introduction to AppArmor (1) which is closed for posting.
Two other threads are open for discussion: Share your AppArmor Profiles (2) and AppArmor Support Thread (3).

Enjoy the readings, test it out and report back in the threads!

 1. [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
 2. [http://ubuntuforums.org/showthread.php?t=1008911](http://ubuntuforums.org/showthread.php?t=1008911)
 3. [http://ubuntuforums.org/showthread.php?t=1049698](http://ubuntuforums.org/showthread.php?t=1049698)

***[size="3"]Ubuntu Forums Staff Selection[/size]***

The process had never been formally documented so far.

For several years, integrating new Staff people has been a rather easy process : current Staff would suggest new names, the FC (in particular ubuntu-geek ([http://ubuntuforums.org/member.php?u=1](http://ubuntuforums.org/member.php?u=1)) and matthew ([http://ubuntuforums.org/member.php?u=17635](http://ubuntuforums.org/member.php?u=17635))) would work on a list and selected people would get invited to join.

With the strong and steady expansion of our community, the process needed a better definition so that other FC members could handle it too. We will continue to ask the current Staff for suggestions, it has worked really well so far.

We have been adding new Staff roughly before every new Ubuntu release, before a jump in user number, so that people have time to adjust and learn the tools and habits. Two volunteering FC members will be delegated to handle the process.

Four main steps take place :

[LIST]
[*]A post is created in the Staff area asking for suggestions
[*]Two FC members compile a list of names from the suggestions
[*]They present the list to the FC to vote on
[*]They approach the new Staff by PM and ask them if they would like to join
[/LIST]

After they accept, new Staff forums permissions are adjusted to place them in the UF Staff group and grant them access to the appropriate IRC channels.

Once a year, the delegated FC members will track Staff who are MIA.

bodhi.zazen ([http://ubuntuforums.org/member.php?u=89054](http://ubuntuforums.org/member.php?u=89054)) and bapoumba ([http://ubuntuforums.org/member.php?u=171805](http://ubuntuforums.org/member.php?u=171805)) have volunteered and been designed by the FC to take the lead on this project. Matthew will mentor them as he had been taking care of the process with UG so far.

[http://ubuntuforums.org/showthread.php?p=9280735](http://ubuntuforums.org/showthread.php?p=9280735)

**[size="5"]The Planet[/size]**

***[size="3"]Full Circle Magazine: Interview with Penelope Stowe[/size]***

Penelope Stowe, was interviewed by Isabell Long, for the Ubuntu Women Series, in Issue 37 of Full Circle Magazine.  In this interview Penelope talks about how she got involved with the Ubuntu Community.  Penelope noted that a friend encouraged her to get involved in the community.  Penelope says, "I love the Ubuntu community. It’s one of the friendliest communities I know of any type, and I do think the community is the strongest part of the operating system." Penelope also talks about the various roles she plays within the community, those roles include reviving the Accessibility Team, member of the Ubuntu User Days Team, as well as an active member in the Ubuntu Women Project. Isabell notes that in Penelope's short time as an active community member she has done a lot, and when asked if there was something else she would like to do Penelope states, "I definitely want to get involved with documentation...I’d also like to learn how to bug triage and help out the bug squad...try to learn to program." In this interview she also talks about things she is interested in outside of Ubuntu and FOSS.

To read more the full interview and more about Penelope go to:

[http://fridge.ubuntu.com/node/2045](http://fridge.ubuntu.com/node/2045)

***[size="3"]Matt Zimmerman: The behavioral economics of free software[/size]***

Why do we choose to use and promote free software? We can say free software is of a higher quality, but comparing different software 'apples to apples' can be challenging. We can also say that there is a greater sense of community involved with free software and its use, and that developers appreciate the freedom to adapt the software to specific needs. This author poses that we look at our reasons for prefering free software, and not take these preferences at face value. The author also poses these questions for our own thoughts, and asks for any information on studies that have looked into these topics. "Does using free software make us happier? Do we believe in free software because we have a great experience using it, or because we feel good about having used it? Why do we want other people to use free software, is it only because we want them to share our preference, or because we will benefit ourselves, or do we believe they will appreciate it for their own reasons?"

To read article in full and learn more about "The behavioral economics of free software" go to:

[http://mdzlog.alcor.net/2010/05/25/the-behavioral-economics-of-free-software/](http://mdzlog.alcor.net/2010/05/25/the-behavioral-economics-of-free-software/)

***[size="3"]Thierry Carrez: Return of the Ubuntu Server papercuts[/size]***

Papercuts are back, and now the process is started before 'feature freeze'. This effort will take place during the first three development iterations. ALSO, small new features or behavior changes are accepted as well. To nominate, follow this process:

 1. If the papercut isn’t already filed as an Ubuntu bug in Launchpad, file a bug against the affected Ubuntu package.
 2. Look up the bug you want to nominate as a Server papercut, then click on “Also affects project”.
 3. Click “Choose another project” and type in “server-papercuts”, click “Continue”.
 4. Click on “Add to Bug report”.

The goal is to have 16 candidates for the next Ubuntu Server Meeting, Tuesday June 1st, 1800 UTC in the #ubuntu-meeting IRC channel on Freenode.

To find out more about Ubuntu Server Papercuts and how you can get involved go to:

[http://fnords.wordpress.com/2010/05/25/return-of-the-ubuntu-server-papercuts/](http://fnords.wordpress.com/2010/05/25/return-of-the-ubuntu-server-papercuts/)

***[size="3"]Matt Zimmerman: Rethinking the Ubuntu Developer Summit[/size]***

The purpose of UDS has always been to help Ubuntu developers explore plans for the subsequent release. In rethinking this basic purpose, several ideas have been proposed to help better facilitate this goal. We would like to concentrate on projects that CAN be completed in the upcoming cycle, and postpone unrealistic projects to future blueprints. Getting similar groups of people together to 'attack' similar projects, helping to switch context less often could be helpful in fighting fatigue. Organizing cross-team participation, rather than dividing teams into tracks might help circumvent compatibility issues down the road. Also, building in opportunities to tackle larger problems in a longer duration of time.

To read more this article in full and join the discussion go to:

[http://mdzlog.alcor.net/2010/05/27/rethinking-the-ubuntu-developer-summit/](http://mdzlog.alcor.net/2010/05/27/rethinking-the-ubuntu-developer-summit/)

***[size="3"]Jono Bacon: Testing Indicator Application Menu Support[/size]***

In this post, Jono Bacon discusses how you can help test the Indicator Application Menu Support. Jono states, "In the Ubuntu 10.10 cycle we have committed to implementing application menus in the Ubuntu Netbook Edition release of Ubuntu...I personally think this is going to be a tremendously valuable feature and continues to optimize Ubuntu for screen real-estate."

Jono notes, "For the majority of applications that use standard menu widgets, applications should just work out of the box. We are though keen to test as many applications as possible to ensure they work and identify problem spots. Like the last cycle, this new code has been released very early for testing and improvements, and we are keen to have as many folks test, file bugs and where possible file patches to fixes."

Jono 's article gives you all the links to make it simple and easy to get involved. He also points out,  "Importantly, you don’t have to be running Ubuntu Netbook Edition to test – you can use the normal Ubuntu desktop edition!. Packages are already available in a PPA for Lucid and we have listed all of the apps that could do with some testing. We have also includes instructions for how to file bugs for apps that have issues; this will make it easier to produce fixes. One important note: up until alpha 2 we are deliberately leaving the menus switched on in both the application and in the panel – this provides a great way to compare and contrast the normal app menu with the panel menu to ensure they are the same."

To find out more about helping test the Indicator Application Menu Support and read the article in full go to:

[http://www.jonobacon.org/2010/05/28/testing-indicator-application-menu-support/](http://www.jonobacon.org/2010/05/28/testing-indicator-application-menu-support/)

**[size="5"]In The Press[/size]**

***[size="3"]Ubuntu 10.04 LTS: Lucid Lynx Benchmarked And Reviewed[/size]***

Yet another 10.04 review, this one pits the previous 8.04 LTS against 10.04 and the progress that Canonical has achieved shines through.

Adam Overa at Tom's Hardware writes a very detailed review of Ubuntu 10.04. He specifically compares it against 8.04, Hardy Heron, which was the Ubuntu release that converted him to full-time Linux use and to Ubuntu, specifically. Adam gives information on the methodology used to test both the 64-bit and 32-bit desktops.

The first thing covered is the Ubuntu Software Center, where Adam sees some improvements to the Ubuntu Software Center in Karmic (which he very much did not like), however, feels like there are still things that he misses from Add/Remove Programs. Next he moves onto covering the new changes to Ubuntu, including the panel indicators, F-Spot instead of The GIMP, split panes in Nautilus, Gwibber, PiTiVi, and the Ubuntu One Music store. He continues to talk about the look and feel with the new Ambiance and Radiance themes, re-branding of Ubuntu, and the window controls on the left.

After this information about the changes in Lucid, Adam gives an overview to what he experienced and saw with the various test systems. He tested 64-bit & 32-bit on desktops. He also tested using a notebook and even installed Ubuntu Netbook Edition on a netbook. Finally, he tested running the system off a USB stick.

From there, Adam moved on to a series of benchmark results. He started with boot, hibernate, wake, and shut down times, which were mostly an improvement over Hardy (the exception being the time it takes to go into hibernate). Next he looks at the times for file copy and compression, which are again mostly improved in Lucid compared to Hardy. He goes on to look at multimedia applications by testing Handbrake, Lame, POV-Ray, Blender and Raw Therapee; again, Lucid is generally faster than Hardy. The next benchmarks reported are Peacekeeper (using Firefox) and Geekbench, where Lucid again performed well.

In the UNiGiNE Heaven benchmarch testing, the testers discovered that there is something in the desktop effects settings in Lucid that slows framerates considerably. To fix this, they disabled the desktop effects setting, at which point Lucid outperformed Hardy, again. For the benchmark results on Tropics, Sanctuary, and Lightsmark things were mixed. In most cased Lucid with desktop effects disabled outperformed Hardy, except for Lightsmark 2008, where Hardy does much better than Lucid. The last benchmark results checked are those for games. These were all very close with Lucid winning some and Hardy winning others. Clearly, however, disabling desktop effects did much to improve Lucid's performance.

Adam concludes that Lucid is the desktop Linux distro king, however, worries that it will get quickly replaced in advertising by 10.10, which he fears will not be as good.

For all the details of Adam's review:

[http://www.tomshardware.com/reviews/ubuntu-10.04-lucid-lynx,2634.html](http://www.tomshardware.com/reviews/ubuntu-10.04-lucid-lynx,2634.html)

***[size="3"]Ubuntu's Unity Desktop: Reality vs. Rationales[/size]***

Is Ubuntu's Unity desktop meeting up to Mark Shuttleworth's expectations for a fast-booting, simple, 'finger-friendly' cloud distribution? Take a look at the Unity desktop (which is to become the desktop for the Ubuntu Netbook Remix release, and the upcoming 'Ubuntu Light') and see for yourself. Is the layout more touch screen friendly? Does it have a lightning fast boot time? Is the screen layout more horizontal rather that vertical to better suit netbooks? This author says no. However, Unity does deliver quite well on a few key features, while targeting a market of 'cloud' users who do not necessarily want or need many locally installed applications, and just want an 'instant-web' portal. If we look at Shuttleworth's goals, we can see that Unity is not a polished final project, but rather a playground on which the ideas can be worked out. This author feels that Ubuntu's Unity desktop may undergo MANY changes, including changes in vision and target markets.

To for more information on this article please go to:

[http://itmanagement.earthweb.com/osrc/article.php/12068_3884051_1/Ubuntus-Unity-Desktop-Reality-vs-Rationales.htm](http://itmanagement.earthweb.com/osrc/article.php/12068_3884051_1/Ubuntus-Unity-Desktop-Reality-vs-Rationales.htm)

**[size="5"]In The Blogosphere[/size]**

***[size="3"]Five Usability Improvements in Ubuntu 10.04[/size]***

Christopher Tozzi at WorksWithU writes about five features that are in Ubuntu 10.04 (some started in Ubuntu 9.10) which improve usability. He notes that they may be so small that you don't notice them; however, they are things that make Ubuntu a more intuitive operating system to use.

Christopher focuses on these five usability enhancements:

[LIST]
[*]Screenshot Utility
[*]Syntax Highlighting in Nano
[*]Archive Mounter
[*]RAR Files
[*]Better PDF Reader
[/LIST]

While he notes that there is still more work, Christopher says the usability improvements in 9.10 and 10.04 show a real commitment to usability, and he's looking forward to see what comes next.

For more information about what Christopher thinks of the usability changes in 10.04 see:
[http://www.workswithu.com/2010/05/25/five-usability-improvements-in-ubuntu-10-04/](http://www.workswithu.com/2010/05/25/five-usability-improvements-in-ubuntu-10-04/)

***[size="3"]HTML5 Video on Ubuntu[/size]***

Christopher Tozzi at WorksWithU tried out HTML5 on Ubuntu using Google Chrome. Christopher is not a fan of Flash, partially because it is closed and proprietary, but also because it is slow, insecure, and buggy. While Adobe has worked to improve Flash, these improvements do not help a Linux user.

HTML5 has the potential to replace flash with the <video> tag included in the codec. The main concern with HTML5 for Christopher is that most video currently used on sites using HTML5 use the H.264 codec, which is not free. This means that Firefox does not support HTML5 videos on sites such as YouTube which use H.264. As a result, Christopher downloaded Google Chrome to test HTML5. His actual experience using HTML5 on YouTube was that it worked well with little effort.

For more information on Christopher's experience with HTML5:
[http://www.workswithu.com/2010/05/25/html5-video-on-ubuntu/](http://www.workswithu.com/2010/05/25/html5-video-on-ubuntu/)

***[size="3"]Ubuntu Netbook 10.10 Will Get a Global Menu By Default[/size]***

WebUpD8 reports that Mark Shuttleworth has announce that Ubuntu Netbook Edition 10.10 (and only Ubuntu Netbook Edition) will have a global menu. The reason for using a global menu is that it should increase available vertical space. Mark clarified on the Ayatana mailing list the details of how the menu will work. When the window is not maximized, the menu will be in the panel. When maximized, the panel will contain the window controls, the window title, and the indicators. When you mouse towards the window title, or press Alt, it will chance to the menu.

WebUpD8 questions what will happen for switching between running applications, as Mark has stated it will be addressed separately. The writer for WebUpD8 wonders if this will mean that a dock-like application will be added.

WebUpD8 also provides instructions for installing the Global Menu in your current version of Ubuntu.

For more information see:

[http://www.webupd8.org/2010/04/ubuntu-1010-will-get-global-menu-by.html](http://www.webupd8.org/2010/04/ubuntu-1010-will-get-global-menu-by.html)

**[size="5"]In Other News[/size]**

***[size="3"]Landscape 1.5 Released with new Enterprise Features[/size]***

Canonical released the latest version of Landscape, an enterprise class systems management and monitoring service. Landscape 1.5 debuts this week and is timed to support the newest LTS release 10.04. Many new features have been integrated; such as SSO integration allowing users to log into Landscape with existing credentials, through authentication modules such as LDAP and Active Directory. Package configuration, pinning and improved LTS to LTS upgrades are now part of the standard feature set of the improved Landscape 1.5.

Ken Drachnik, Canonical Landscape Manager, covers all the important points in the article.

To learn more about Landscape and read what Ken Drachnick has to say about Landscape go to:

[http://blog.canonical.com/?p=396](http://blog.canonical.com/?p=396)

***[size="3"]Canonical Pushes Skype into Ubuntu Repository[/size]***

The popular closed source VoIP application, Skype, can now be found in the Canonical Third Party Repositories. The Skype package is available in the Lucid 10.04 Partner Repositories, which can be enabled according to this tutorial [1] and then installed using the Software Center. Skype can be found on Launchpad [2] and package development can be followed at [https://launchpad.net/ubuntu/+source/skype/2.1.0.81-1ubuntu4](https://launchpad.net/ubuntu/+source/skype/2.1.0.81-1ubuntu4)

 1. - [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)
 2. - [https://launchpad.net/skype](https://launchpad.net/skype)

For more information see:

[http://www.phoronix.com/scan.php?page=news_item&px=ODI4Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI4Mg)

***[size="3"]Linux Security Summit 2010[/size]***

Kees Cooks, Ubuntu Security Manager, posts on his blog that the call for papers at LinuxCon is now open.

The Call For Participation is open for the 2010 Linux Security Summit, being held just before this year’s LinuxCon.

If you’re interested in helping make Linux more secure, you’ve got ideas to present, want to have your opinion heard, or generally just want to hang out, please join us and/or suggest a topic for discussion (CFP ends June 4th, so please hurry).

I’m hoping to get a chance to discuss what I’m calling the “popular kernel hardening patches” which appear in a lot of distros yet remain missing from the upstream Linux kernel.

For more information on the Linux Security Summit 2010 please go to:

[http://www.outflux.net/blog/archives/2010/05/29/linux-security-summit-2010/](http://www.outflux.net/blog/archives/2010/05/29/linux-security-summit-2010/)

***[size="3"]Full Circle Magazine #37[/size]***

Full Circle - the independent magazine for the Ubuntu Linux community is proud to announce the release of issue thirty-seven.

In this month's issue:

[LIST]
[*]Command and Conquer.
[*]How-To : Program in Python – Part 11, Adding Screenlets, and Streaming Media.
[*]Review – Lubuntu.
[*]MOTU Interview – Stefan Lesicnik.
[*]Top 5 – Tiling Window Managers.
[*]plus: Ubuntu Women, Ubuntu Games, My Opinion, My Story, and all the usual goodness!
[/LIST]

Get it while it's hot! [http://fullcirclemagazine.org/issue-37/](http://fullcirclemagazine.org/issue-37/)

**[size="5"]Featured Podcasts[/size]**

***[size="3"]Ubuntu UK Podcast: Three Friends[/size]***

Laura Cowen and Tony Whitmore introduce a special post-developer-summit episode of the Ubuntu Podcast from the UK LoCo Team featuring three interviews from UDS

What we've been doing -

Interviews with:
[LIST]
[*]Robbie Williamson (@undacuvabrutha), the platform lead for Ubuntu 10.04
[*]Kees Cook (@keescook) from the SecurityTeam
[*]Rick Spencer (@rickspencer3) the Desktop Team lead.
[/LIST]

Comments and suggestions are welcomed to: [email]podcast@ubuntu-uk.org[/email]

[LIST]
[*]OGG download High: [http://podcast.ubuntu-uk.org/download/uupc_s03e08_high.ogg](http://podcast.ubuntu-uk.org/download/uupc_s03e08_high.ogg)
[*]OGG download Low: [http://podcast.ubuntu-uk.org/download/uupc_s03e08_low.ogg](http://podcast.ubuntu-uk.org/download/uupc_s03e08_low.ogg)
[*]MP3 download High: [http://podcast.ubuntu-uk.org/download/uupc_s03e08_high.mp3](http://podcast.ubuntu-uk.org/download/uupc_s03e08_high.mp3)
[*]MP3 download Low: [http://podcast.ubuntu-uk.org/download/uupc_s03e08_low.mp3](http://podcast.ubuntu-uk.org/download/uupc_s03e08_low.mp3)
[/LIST]

For more information on the Ubuntu-UK Podcast go to:

[http://podcast.ubuntu-uk.org/](http://podcast.ubuntu-uk.org/)

**[size="5"]Upcoming Meetings and Events[/size]**

***[size="3"]Monday, May 31, 2010[/size]***

==== Docs, Learning, Manual Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: Discuss blueprint [https://blueprints.launchpad.net/ubuntu/+spec/community-m-documentation-teams-collaboration](https://blueprints.launchpad.net/ubuntu/+spec/community-m-documentation-teams-collaboration)
[/LIST]

==== Security Team Catch-up ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 17:30 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: nothing formal, just a weekly catch-up. Weekly Ubuntu Security Team catch-up meeting. Anyone is welcome to join if they want to watch, contribute, etc.
[/LIST]

***[size="3"]Tuesday, June 1, 2010[/size]***

==== Ubuntu Mobile Team Meeting ====

[LIST]
[*]Start: 13:00 UTC
[*]End: 14:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda:  [https://wiki.ubuntu.com/MobileTeam/Meeting](https://wiki.ubuntu.com/MobileTeam/Meeting)
[/LIST]

==== Technical Board Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: None given at time of publication
[/LIST]

==== Desktop Team Meeting ====

[LIST]
[*]Start: 16:30 UTC
[*]End: 17:30 UTC
[*]Location: IRC channel #ubuntu-desktop on irc.freenode.net
[*]Agenda: [https://wiki.ubuntu.com/DesktopTeam/Meeting](https://wiki.ubuntu.com/DesktopTeam/Meeting)
[/LIST]

==== Kernel Team Meeting ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 18:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: Not listed as of publication
[/LIST]

==== LoCo Teams Meeting ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 18:00 UTC
[*]Location: IRC channel #ubuntu-locoteams on irc.freenode.net
[*]Agenda: Not listed as of publication
[/LIST]

==== Server Team Meeting ====

[LIST]
[*]Start: 18:00 UTC
[*]End: 19:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: [https://wiki.ubuntu.com/ServerTeam/Meeting](https://wiki.ubuntu.com/ServerTeam/Meeting)
[/LIST]

==== EMEA Membership Meeting ====

[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: [https://wiki.ubuntu.com/Membership/RegionalBoards/EMEA](https://wiki.ubuntu.com/Membership/RegionalBoards/EMEA)
[/LIST]

==== Community Council Meeting ====

[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: [https://wiki.ubuntu.com/CommunityCouncilAgenda](https://wiki.ubuntu.com/CommunityCouncilAgenda) Per CC Agenda page, as of 11/29/08
[/LIST]

***[size="3"]Wednesday, June 2, 2010[/size]***

==== Cameroonian LoCo Team monthly IRC meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 16:00 UTC
[*]Location: IRC channel #ubuntu-cm on irc.freenode.net
[*]Agenda:  [https://wiki.ubuntu.com/CameroonianTeam/NextMeeting](https://wiki.ubuntu.com/CameroonianTeam/NextMeeting)
[/LIST]

==== Foundation Team Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda:  None listed as of publication
[/LIST]

==== QA Team Meeting  ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 18:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: [https://wiki.ubuntu.com/QATeam/Meetings/](https://wiki.ubuntu.com/QATeam/Meetings/)
[/LIST]

==== Jono Bacon @ Home Videocast : Various Topics and Q+A ====

[LIST]
[*]Start: 18:00 UTC
[*]End: 19:00 UTC
[*]Location: [http://www.ustream.tv/channel/at-home-with-jono-bacon](http://www.ustream.tv/channel/at-home-with-jono-bacon)
[*]Agenda: This is a weekly videocast by the Ubuntu Community Manager, Jono Bacon in which he discusses a range of topics and also provides a regular weekly Q+A.
[/LIST]

***[size="3"]Thursday, June 3, 2010[/size]***

==== Ayatana UX Team Meeting ====

[LIST]
[*]Start: 12:00 UTC
[*]End: 12:30 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: * Introductions * Review team charter * Organize first UX activity * Brainstorm future UX activities
[/LIST]

==== Ubuntu Java Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: none listed as of publication
[/LIST]

==== Ubuntu Translations Meeting ====

[LIST]
[*]Start: 15:00 UTC
[*]End: 16:00 UTC
[*]Location: IRC channel #ubuntu-meeting on irc.freenode.net
[*]Agenda: [https://wiki.ubuntu.com/TranslatingUbuntu/Events/Meetings](https://wiki.ubuntu.com/TranslatingUbuntu/Events/Meetings)
[/LIST]

***[size="3"]Friday, June 4, 2010[/size]***

***[size="3"]Saturday, June 5, 2010[/size]***

==== DC LoCo Team BugJam ====

[LIST]
[*]Start: 20:00 UTC
[*]End: 22:00 UTC
[*]Location: IRC channel #ubuntu-us-dc on irc.freenode.net
[*]Agenda: none listed as of publication
[/LIST]

==== DC LoCo IRC meeting ====

[LIST]
[*]Start: 22:00 UTC
[*]End: 23:00 UTC
[*]Location: IRC channel #ubuntu-us-dc on irc.freenode.net
[*]Agenda: none listed as of publication
[/LIST]

***[size="3"]Sunday, June 6, 2010[/size]***

None listed as of publication

**[size="5"]Updates and Security for 6.06, 8.04, 9.04, 9.10, and 10.04[/size]**

***[size="3"]Security Updates[/size]***

[LIST]
[*]USN-944-1 GNU C Library vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-May/001096.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-May/001096.html)
[*]USN-945-1 ClamAV vulnerabilities - [https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-May/001097.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-May/001097.html)
[/LIST]

***[size="3"]Ubuntu 6.06 Updates[/size]***

[LIST]
[*]glibc- [https://lists.ubuntu.com/archives/dapper-changes/2010-May/012845.html](https://lists.ubuntu.com/archives/dapper-changes/2010-May/012845.html)
[*]clamav (delayed)- [https://lists.ubuntu.com/archives/dapper-changes/2010-May/012846.html](https://lists.ubuntu.com/archives/dapper-changes/2010-May/012846.html)
[/LIST]

***[size="3"]Ubuntu 8.04 Updates[/size]***

[LIST]
[*]glibc_2.7-10ubuntu6_i386_translations.tar.gz- [https://lists.ubuntu.com/archives/hardy-changes/2010-May/012470.html](https://lists.ubuntu.com/archives/hardy-changes/2010-May/012470.html)
[*]clamav_0.95.3+dfsg-1ubuntu0.09.04~hardy2.4_sparc_translations.tar.gz    (delayed)- [https://lists.ubuntu.com/archives/hardy-changes/2010-May/012471.html](https://lists.ubuntu.com/archives/hardy-changes/2010-May/012471.html)
[/LIST]

***[size="3"]Ubuntu 9.04 Updates[/size]***

[LIST]
[*]glibc_2.9-4ubuntu6.2_ia64_translations.tar.gz- [https://lists.ubuntu.com/archives/jaunty-changes/2010-May/010072.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-May/010072.html)
[*]clamav_0.95.3+dfsg-1ubuntu0.09.04.2_lpia_translations.tar.gz- [https://lists.ubuntu.com/archives/jaunty-changes/2010-May/010073.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-May/010073.html)
[/LIST]

***[size="3"]Ubuntu 9.10 Updates[/size]***

[LIST]
[*]eglibc_2.10.1-0ubuntu17_ia64_translations.tar.gz- [https://lists.ubuntu.com/archives/karmic-changes/2010-May/012379.html](https://lists.ubuntu.com/archives/karmic-changes/2010-May/012379.html)
[*]clamav_0.95.3+dfsg-1ubuntu0.09.10.2_powerpc_translations.tar.gz- [https://lists.ubuntu.com/archives/karmic-changes/2010-May/012380.html](https://lists.ubuntu.com/archives/karmic-changes/2010-May/012380.html)
[/LIST]

***[size="3"]Ubuntu 10.04 Updates[/size]***

[LIST]
[*]gtkmm2.4 1:2.20.3-0ubuntu1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011313.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011313.html)
[*]rhythmbox 0.12.8-0ubuntu5 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011314.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011314.html)
[*]telepathy-butterfly 0.5.9-0ubuntu1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011315.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011315.html)
[*]skype 2.1.0.81-1ubuntu5 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011316.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011316.html)
[*]netbook-meta 2.025 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011317.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011317.html)
[*]hamster-applet 2.30.1-0ubuntu0.1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011318.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011318.html)
[*]eglibc_2.11.1-0ubuntu7.1_amd64_translations.tar.gz- [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011319.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011319.html)
[*]nvidia-graphics-drivers    195.36.24-0ubuntu1~10.04 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011320.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011320.html)
[*]gnome-keyring 2.92.92.is.2.30.1-0ubuntu2    - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011321.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011321.html)
[*]brasero 2.30.1-0ubuntu1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011322.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011322.html)
[*]brasero 2.30.1-0ubuntu2 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011323.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011323.html)
[*]clamav_0.96.1+dfsg-0ubuntu0.10.04.1_armel_translations.tar.gz- [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011324.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011324.html)
[*]get-iplayer 2.66-1ubuntu1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011325.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011325.html)
[*]harpia 1.0-0ubuntu1.1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011326.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011326.html)
[*]kdepimlibs 4:4.4.2-0ubuntu2.1 - [https://lists.ubuntu.com/archives/lucid-changes/2010-May/011327.html](https://lists.ubuntu.com/archives/lucid-changes/2010-May/011327.html)
[/LIST]

**[size="5"]UWN Translations[/size]**

[LIST]
[*]Note to translators and our readers please follow the link below for the information you need.
[/LIST]

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations)

**[size="5"]Subscribe[/size]**

Get your copy of the Ubuntu Weekly Newsletter delivered each week to you via email at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-news](https://lists.ubuntu.com/mailman/listinfo/ubuntu-news)

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
[*]Amber Graner
[*]Chris Johnston
[*]Isabelle Duchatelle
[*]Penelope Stowe
[*]Liraz Siri
[*]Daniel Caleb
[*]J. Scott Evan
[*]Mike Holstein
[*]Mackenzie Morgan
[*]And many others
[/LIST]

**[size="5"]Glossary of Terms[/size]**

Other acronyms can be found at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary)

**[size="5"]Ubuntu - Get Involved[/size]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. [http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)

**[size="5"]Feedback[/size]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send them to [email]ubuntu-users@lists.ubuntu.com[/email].

Except where otherwise noted, content in this issue is licensed under a Creative Commons Attribution 3.0 License - [http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/)

---

