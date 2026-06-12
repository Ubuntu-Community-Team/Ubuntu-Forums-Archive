---
title: "Ubuntu Weekly Newsletter #184"
date: 2010-03-14
forum: Weekly Newsletter
---

### Post by johnc4510 on 2010-03-14
Welcome to the Ubuntu Weekly Newsletter, Issue #184 for the week March 7th - March 13th, 2010. In this issue we cover: Lucid Kernel now Frozen, Ubuntu 10.04 beta 1 freeze now in effect, Intel, Eucalyptus and Canonical join forces to help user build cloud infrastructures confidently, Call for Testing: Cluster Stack – Load Balancing, Google Summer of Code 2010: Ubuntu application, New Ubuntu Members: Asia Oceanic Board & Americas Board, Request for input for Lucid Beta 1 technical overview, International Womens Day "How I Discovered Ubuntu" Winners, Ubuntu Global Jam(LoCo Style), Getting started with launchpadlib: Launchpad’s Python library, Ubuntu Global Jam – what’s it all about, New stuff for the Ubiquity slideshow(Proposed), Alan Pope: Why (I think) Ubuntu is Better Than Windows, Ubuntu hits HTC's Touch Pro2, is any Windows Mobile handset safe, and much, much more!

**[size="5"]UWN Translations[/size]**

[LIST]
[*]Note to translators and our readers: We are trying a new way of linking to our translations pages. Please follow the link below for the information you need.
[/LIST]

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Translations)

**[size="5"]In This Issue[/size]**

[LIST]
[*]Lucid Kernel now Frozen
[*]Ubuntu 10.04 beta 1 freeze now in effect
[*]Intel, Eucalyptus and Canonical join forces to help user build cloud infrastructures confidently
[*]Call for Testing: Cluster Stack – Load Balancing
[*]Google Summer of Code 2010: Ubuntu application
[*]New Ubuntu Members: Asia Oceanic Board & Americas Board
[*]Request for input for Lucid Beta 1 technical overview
[*]International Womens Day "How I Discovered Ubuntu" Winners
[*]Ubuntu Stats
[*]Ubuntu Global Jam(LoCo Style)
[*]Getting started with launchpadlib: Launchpad’s Python library
[*]Ubuntu Global Jam – what’s it all about?
[*]New stuff for the Ubiquity slideshow(Proposed)
[*]Alan Pope: Why (I think) Ubuntu is Better Than Windows
[*]In the Press & Blogosphere
[*]Ubuntu hits HTC's Touch Pro2, is any Windows Mobile handset safe?
[*]Upcoming Meetings & Events
[*]Updates & Security
[/LIST]

**[size="5"]General Community News[/size]**

***[size="3"]Lucid Kernel now Frozen[/size]***

The Lucid Kernel is now frozen. This means that the kernel moves from active development into its stabilization phase. All planned kernel features are now set, included, and enabled and the kernel team focus now moves from new enabling to testing, bug isolation, and fixing of issues found in the kernel. The kernel will now transition over to the stable maintenance team, they will be responsible for patch acceptance from here on.

What does this transition mean for you.  Now is the time to test things you care about and report any issues in Launchpad against the linux package. If you have bugs open found earlier in the cycle please retest with the latest and greatest kernel and report back whether those bugs are still present and where you tested.  The upcoming Beta-1 release is an ideal test platform.

Additionally this transition means that is will be much harder to make a change the kernel. From today patches will need to meet the same criteria as would be required for SRU[1] to a released kernel. That means that the patch must have a Launchpad bug open, it must be a fix for an actual bug being experienced in the field, it must be sent to the kernel-team email list for review, it must receive two acknowledgements from kernel team members, and finally you must test the updated kernels and report back.

 [1] [https://wiki.ubuntu.com/KernelTeam/StableKernelMaintenance](https://wiki.ubuntu.com/KernelTeam/StableKernelMaintenance)

Lucid will be with us for a long time so please help us make this the best kernel possible.  Please test beta-1 and report your issues. Thanks!

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/000689.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/000689.html)

***[size="3"]Ubuntu 10.04 beta 1 freeze now in effect[/size]***

We are now one week from the first beta release of 10.04, scheduled for March 18 [https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule) and have just entered beta freeze.

During the freeze, all uploads to main must be approved by a member of the release team [1], so if you have fixes which are important to get in, please do get in touch as soon as possible. Uploads to universe require a manual push through the queue, but are not subject to release management approval.

Issues which are important for the beta release will be tracked by the release team here: [https://bugs.launchpad.net/ubuntu/lucid/+bugs?field.milestone=21446](https://bugs.launchpad.net/ubuntu/lucid/+bugs?field.milestone=21446)

If you have bugs on this list, please fix them at the earliest possible opportunity, or (in consultation with other developers and the Ubuntu QA team) un-milestone them if they are not required for beta. If you have bugs you think should be on this list, talk with the Ubuntu QA team or the Ubuntu release team about having them milestoned.

Please also do not lose sight of the list of bugs affecting the release as a whole: [https://bugs.launchpad.net/ubuntu/lucid/+bugs](https://bugs.launchpad.net/ubuntu/lucid/+bugs)

Over the next few days, please pay attention to eliminating inconsistencies in the archive, including:

[LIST]
[*]uninstallable packages in main and restricted - [http://people.canonical.com/~ubuntu-archive/testing/lucid_probs.html](http://people.canonical.com/~ubuntu-archive/testing/lucid_probs.html)
[*]obsolete packages which still have reverse-dependencies - and [http://people.canonical.com/~ubuntu-archive/NBS/](http://people.canonical.com/~ubuntu-archive/NBS/)
[/LIST]

Archive administrators should spend time ensuring that any pending main<->universe component changes have been processed [http://people.canonical.com/~ubuntu-archive/component-mismatches.txt](http://people.canonical.com/~ubuntu-archive/component-mismatches.txt) Developers, if you are waiting for something on this list, please help out by filing good main inclusion reports.

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/000691.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-March/000691.html)

***[size="3"]Canonical Blog: Intel, Eucalyptus and Canonical join forces to help user build cloud infrastructures confidently[/size]***

A few weeks ago myself and Dustin Kirkland had the privilege of travelling to the Intel facility in Hillsboro, Oregon to work with Billy Cox, Rekha Raghu, Paul Guermonprez, Trevor Cooper and Kamal Natesan of Intel and Dan Nurmi and Neil Soman of Eucalyptus Systems and a few others on developing a proof of concept whitepaper on the use of Ubuntu Enterprise Cloud on Intel Xeon processors (Nehalem). [http://www.intel.com/software/cloudbuilder](http://www.intel.com/software/cloudbuilder)

The whitepaper is published today on the Intel site (registration required) so it seems like a good time to talk about why we collaborated.

The Intel Cloud Builder program is intended to develop some best practice information for businesses and institutions looking to take advantage of the promise of cloud computing. As we do consistently with UEC, we are being specific when we talk about cloud as the ability to build Infrastructure as a Service behind a corporate firewall – that is on your own systems, protected by your own security protocols.

In Portland we had access to some great hardware and as an ex-Intel man, it was good to mess directly with the metal again. Intel defined a number of use and test cases and the guys from Intel, Eucalyptus and myself were able to have some fun putting UEC through its paces. And the results were good. We documented them and the whitepaper gives numerous code and scenario examples to help anyone new to cloud to get up to speed really quickly and the make the most of the capabilities of the Xeon processor in supporting an internal IaaS infrastructure. You can find out how to get started on UEC with existing documentation. but this whitepaper takes it to the next stage. [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

Being able to test the software as part of the Intel Cloud Builder program and jointly publish this whitepaper is a great endorsement of what is still a young technology. And I hope it will give users confidence to start building their own UEC deployment on x86 technology.

Nick Barcet, Ubuntu Server Product Manager

[http://blog.canonical.com/?p=348](http://blog.canonical.com/?p=348)

***[size="3"]Call for Testing: Cluster Stack – Load Balancing[/size]***

Continuing with the Ubuntu Cluster Stack testing, it is time now for Load Balancing. During UDS, we discussed that we should based the Load Balancing as part of the Ubuntu Cluster Stack using Keepalived due to its speed. However, since the main Cluster Stack is based in Pacemaker, we decided to do Load Balancing with Pacemaker/ldirectord too.

The wiki page showing the procedure is here: [https://wiki.ubuntu.com/ClusterStack/LucidTesting#Load%20Balancing](https://wiki.ubuntu.com/ClusterStack/LucidTesting#Load%20Balancing) If you find any bugs in the documentation, please let us know by leaving your comments at the END of the wikipage in preparation for the Documentation that might be included in the Ubuntu Server Guide.

All the packages are now in the archives. So please test the configurations and if you find any bugs, please report them in LP.

[http://www.roaksoax.com/2010/03/call-for-testing-cluster-stack-load-balancing](http://www.roaksoax.com/2010/03/call-for-testing-cluster-stack-load-balancing)

***[size="3"]Google Summer of Code 2010: Ubuntu application[/size]***

We are very excited to announce that Ubuntu has applied as to be a participating organization in the Google Summer of Code 2010! We submitted an organizational application, along with suggested ideas for potential projects for students. We also encourage students to come up with their own ideas.

If you're a student interested in Open Source (or if you know students who are), now is the time to act to get involved in Google's wonderful Summer of Code program. Also, if you are thinking about becoming a student's mentor please visit: [https://wiki.ubuntu.com/GoogleSoC2010](https://wiki.ubuntu.com/GoogleSoC2010)

Make sure you read all the necessary information carefully and join the IRC channel and mailing list for more discussion.

The timeline is as follows:

[LIST]
[*]The list of accepted Mentoring Organisations will be announced on
[/LIST]
   March 18, 2010 at 12 noon PDT / 19:00 UTC and will be posted on the
   Google Summer of Code 2010 site.

[LIST]
[*]The student application period begins March 29, 2010 at 12 noon PDT
[/LIST]
   / 19:00 UTC and ends April 9, 2010 at 12:00 at 12 noon PDT / 19:00
   UTC. Please see the Google Summer of Code 2010 timeline and FAQs for
   further information.

[https://lists.ubuntu.com/archives/ubuntu-news-team/2010-March/000894.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2010-March/000894.html)

***[size="3"]New Ubuntu Members: Asia Oceanic Board & Americas Board[/size]***

==== Asia Oceanic Board ====

K. Vishnoo Charan Reddy

Vish concentrates on artwork for apps or projects which are in need of artwork. He also does some triage bug reports in launchpad. He is not actually a programmer, but he has submitted one minor patch, which changes the default options in compiz for a papercut bug.

[LIST]
[*]Wiki: [https://wiki.ubuntu.com/vish](https://wiki.ubuntu.com/vish)
[*]Launchpad: [https://launchpad.net/~vish.../](https://launchpad.net/~vish.../)
[/LIST]

Nigel Babu

nigelb is a computer applications student who has contributed to both the Beginners Team and the Ubuntu Community Project where he been reviewing and updating courses. Nigel also works with the Bug Squad and the Ubuntu Classroom Team.

[LIST]
[*]Wiki: [https://wiki.ubuntu.com/NigelBabu](https://wiki.ubuntu.com/NigelBabu)
[*]Launchpad: [https://launchpad.net/~nigelbabu](https://launchpad.net/~nigelbabu)
[/LIST]

==== Americas Board ====

Duncan McGreggor

Oubiwann is the Ubuntu Project manager for the Platform Team at Canonical. He has also worked with the Landscape Team for over a year, and has maintained the AWS Python library that will be included in Lucid.

[LIST]
[*]Wiki: [https://wiki.ubuntu.com/Oubiwann](https://wiki.ubuntu.com/Oubiwann)
[*]Launchpad: [https://edge.launchpad.net/~oubiwann](https://edge.launchpad.net/~oubiwann)
[/LIST]

Ronald McCollam

fader works at testing hardware for Ubuntu. This includes laptops, desktops, and servers. The testing includes the current development release as well as the point releases for previous versions. Ronald also hangs out in #ubuntu-quality, #ubuntu-testing, and on the Ubuntu QA mailing list where he helps folks get into testing and QA.

[LIST]
[*]Wiki: [https://wiki.ubuntu.com/fader](https://wiki.ubuntu.com/fader)
[*]Launchpad: [https://edge.launchpad.net/~fader](https://edge.launchpad.net/~fader)
[/LIST]

Joe Smith

Yasumoto is a senior at Chapman University in Orange, California, where he am studying Computer Science. Joe is the leader of the Ubuntu California LoCo where he has hosted several release parties and global jams at Chapman. He also gave a presentation about conference exibition at Ubuntu Open Week.

[LIST]
[*]Wiki: [https://wiki.ubuntu.com/Yasumoto](https://wiki.ubuntu.com/Yasumoto)
[*]Launchpad: [https://edge.launchpad.net/~yasumoto7](https://edge.launchpad.net/~yasumoto7)
[/LIST]

dmizer

dmizer is a US expatriate living and working in Japan as a technical writer for Yamaha motors. He has almost 8000 posts to the Ubuntu Forums, and has been a Forum's staff member since 2008. He spends most of his time trying to help people with zero replies to their posts.

[LIST]
[*]Wiki: [https://wiki.ubuntu.com/dmizer](https://wiki.ubuntu.com/dmizer)
[*]Launchpad: [https://edge.launchpad.net/~dmizer](https://edge.launchpad.net/~dmizer)
[/LIST]

The Asia Oceanic Board, the Americas Board, and the Ubuntu Community wish to welcome these new Ubuntu Members.

[https://lists.ubuntu.com/archives/ubuntu-news-team/2010-March/000889.html](https://lists.ubuntu.com/archives/ubuntu-news-team/2010-March/000889.html)

***[size="3"]Request for input for Lucid Beta 1 technical overview[/size]***

The first beta of Lucid Lynx is coming up next week, on March 18. It would be good to have a refresh of [https://wiki.ubuntu.com/LucidLynx/TechnicalOverview](https://wiki.ubuntu.com/LucidLynx/TechnicalOverview) leading up to this, with more input from people who can say what's great about Lucid. So, if everyone that is using Lucid could amble over to the tech page and give their input it would be greatly appreciated.

[https://lists.ubuntu.com/archives/ubuntu-marketing/2010-March/003939.html](https://lists.ubuntu.com/archives/ubuntu-marketing/2010-March/003939.html)

***[size="3"]International Womens Day "How I Discovered Ubuntu" Winners[/size]***

The Ubuntu Women Project celebrated International Womens Day 2010 by conducting a contest to select favorite stories from how women in the Ubuntu community discovered Ubuntu. [http://wiki.ubuntu-women.org/InternationalWomensDay](http://wiki.ubuntu-women.org/InternationalWomensDay)

The stories were all inspirational and exciting, but a few were selected to receive "Ubuntu goodie bags" as well as having an honorable mention:

[LIST]
[*]Winner by popular vote: Elvira Martinez
[*]Winner as selected by Jono Bacon: Karen Y. Perez
[*]Winner by random drawing: Caterina Brigandi
[*]Honorable Mention: Jen Phillips
[/LIST]

We are grateful for everyone involved in the Ubuntu Women Project and the greater Ubuntu Community as a whole, They are continually helping to provide both the platform and encouragement for women to contribute to Ubuntu. You can read each of the winners submission at the link below.

[http://wiki.ubuntu-women.org/InternationalWomensDay/HowIDiscoveredUbuntu](http://wiki.ubuntu-women.org/InternationalWomensDay/HowIDiscoveredUbuntu)

**[size="5"]Ubuntu Stats[/size]**

***[size="3"]Bug Stats[/size]***

[LIST]
[*]Open (76367) -1087 over last week
[*]Critical (29) +2 over last week
[*]Unconfirmed (36973) -1782 over last week
[/LIST]

As always, the Bug Squad needs more help. If you want to get started, please see  [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad)

***[size="3"]Translation Stats Karmic[/size]***

 1. English (United Kingdom) (2273) +5601 # over last week
 2. Spanish (10317) +83 # over last week
 3. French (40137) &#8722;41 # over last week
 4. Brazilian Portuguese (40342) +38 # over last week
 5. German (64952) Not listed last week

Remaining strings to translate in Ubuntu 9.10 "Karmic Koala", see more at: [https://translations.launchpad.net/ubuntu/karmic/](https://translations.launchpad.net/ubuntu/karmic/)

***[size="3"]Ubuntu Brainstorm Top 5 this week[/size]***

[LIST]
[*]A developer that is not used to develop for Ubuntu needs help at first - [http://brainstorm.ubuntu.com/idea/23968/](http://brainstorm.ubuntu.com/idea/23968/)
[*]We should make better use of Nautilus scripts - [http://brainstorm.ubuntu.com/idea/23910/](http://brainstorm.ubuntu.com/idea/23910/)
[*]Titlebar and menubar are wasting too much vertical space - [http://brainstorm.ubuntu.com/idea/23919/](http://brainstorm.ubuntu.com/idea/23919/)
[*]Release Ubuntu 10.10 on October the 10th 2010 - [http://brainstorm.ubuntu.com/idea/23954/](http://brainstorm.ubuntu.com/idea/23954/)
[*][http://brainstorm.ubuntu.com/idea/23966/](http://brainstorm.ubuntu.com/idea/23966/) - [http://brainstorm.ubuntu.com/idea/23966/](http://brainstorm.ubuntu.com/idea/23966/)
[/LIST]

Ubuntu Brainstorm is a community site geared toward letting you add your ideas for Ubuntu. You can submit your own idea, or vote for or against another idea. [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

**[size="5"]LoCo News[/size]**

***[size="3"]Daniel Holbach: Ubuntu Global Jam(LoCo Style)[/size]***

March 26th - 28th, 2010

There’s a lot of people planning their participation right now. If you’re not on the list yet, have a look what others are planning to get some inspiration. [https://wiki.ubuntu.com/UbuntuGlobalJam/Events](https://wiki.ubuntu.com/UbuntuGlobalJam/Events)

[LIST]
[*]Manchester (England, England), UK - [http://madlab.org.uk/content/manchester-lucid-ubuntu-global-jam/](http://madlab.org.uk/content/manchester-lucid-ubuntu-global-jam/)
[*]Montréal, Canada - [http://blog.cyphermox.net/2010/03/global-jam-event-in-montreal-again.html](http://blog.cyphermox.net/2010/03/global-jam-event-in-montreal-again.html)
[*]Waterloo region, Canada - [http://kwartzlab.ca/lucid-jam](http://kwartzlab.ca/lucid-jam)
[*]Budapest, Hungary - [http://ubuntu.hu/node/16836](http://ubuntu.hu/node/16836)
[*]Århus, Denmark - [http://martinpihl.dk/blog/ubuntu-community-dag-i-arhus-i-aften](http://martinpihl.dk/blog/ubuntu-community-dag-i-arhus-i-aften)
[*]Prague, Czech Republic - [http://forum.ubuntu.cz/index.php/topic,43251.0.html](http://forum.ubuntu.cz/index.php/topic,43251.0.html)
[*]and there’s lots and lots of others planning and discussing it.
[/LIST]

Just hop on #ubuntu-locoteams on irc.freenode.net and discuss it there. At 21:00 UTC today (10th March) Jorge Castro will give a session about to run YOUR jam. Awesome!

[LIST]
[*]More good docs here: [https://wiki.ubuntu.com/UbuntuGlobalJam](https://wiki.ubuntu.com/UbuntuGlobalJam)
[*]and here: [https://wiki.ubuntu.com/Jams](https://wiki.ubuntu.com/Jams)
[/LIST]

**[size="5"]Launchpad News[/size]**

***[size="3"]Getting started with launchpadlib: Launchpad’s Python library[/size]***

Launchpad’s strategist, Jonathan Lange, has started a series of blog posts on getting started with Launchpad’s Python library, launchpadlib.

[LIST]
[*]launchpadlib is the Python client-side library that talks to Launchpad’s own REST API. It turns out that customize scripted control of a bug-tracker-code-hosting-translation-distribution-building-cross-project-collaboration thing is actually quite handy.
[/LIST]

Catch-up with the first two posts in the series:

[LIST]
[*]Get started with launchpadlib: [http://code.mumak.net/2010/03/get-started-with-launchpadlib.html](http://code.mumak.net/2010/03/get-started-with-launchpadlib.html)
[*]launchpadlib powerup: [http://code.mumak.net/2010/03/launchpadlib-powerup.html](http://code.mumak.net/2010/03/launchpadlib-powerup.html)
[/LIST]

And you can subscribe to Jonathan’s blog: [http://code.mumak.net/](http://code.mumak.net/) or follow blogs from both Jonathan and other members of the Launchpad community on Planet Launchpad. [http://planet.launchpad.net/](http://planet.launchpad.net/)

[http://blog.launchpad.net/api/getting-started-with-launchpadlib-launchpads-python-library](http://blog.launchpad.net/api/getting-started-with-launchpadlib-launchpads-python-library)

**[size="5"]The Planet[/size]**

***[size="3"]Daniel Holbach: Ubuntu Global Jam – what’s it all about?[/size]***

You want to know what the  Ubuntu Global Jam is all about? It’s easy.

Any of the Ubuntu Jams is a session where people get together locally (yes, in real time and in a real place) and do something to make Ubuntu better and have lots of fun. At the Ubuntu Global Jam we are going to have lots and lots of different kinds of jams around the world for a whole weekend. Make sure you add 26th to 28th of March to you calendar.

Part of our menagerie of Jams are:

[LIST]
[*]Bug Jams - [https://wiki.ubuntu.com//Jams/Bugs](https://wiki.ubuntu.com//Jams/Bugs)
[*]Packaging Jams - [https://wiki.ubuntu.com//Jams/Packaging](https://wiki.ubuntu.com//Jams/Packaging)
[*]Translation Jams - [https://wiki.ubuntu.com//Jams/Translations](https://wiki.ubuntu.com//Jams/Translations)
[*]Doc Jams - [https://wiki.ubuntu.com//Jams/Docs](https://wiki.ubuntu.com//Jams/Docs)
[*]Testing Jams - [https://wiki.ubuntu.com//Jams/Testing](https://wiki.ubuntu.com//Jams/Testing)
[*]Upgrade Jams - [https://wiki.ubuntu.com//Jams/Upgrade](https://wiki.ubuntu.com//Jams/Upgrade)
[/LIST]

It just depends on what you really enjoy doing.

It doesn’t matter if it’s just you and your friends meeting at your house for a jam or if you get together a giant LoCo team to rock out and jam, in any case, we want you to add yourself here: [https://wiki.ubuntu.com/UbuntuGlobalJam/Events](https://wiki.ubuntu.com/UbuntuGlobalJam/Events)

If you’re new to organizing jams, you might want to do one or more of the following:

[LIST]
[*]talk to the fine people in #ubuntu-locoteams
[*]mail the fine people on loco-contacts - [https://lists.ubuntu.com/mailman/listinfo/loco-contacts](https://lists.ubuntu.com/mailman/listinfo/loco-contacts)
[*]email the folks at ubuntu-event-planners - [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-event-planners](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-event-planners)
[*]attend the fine Ubuntu Global Jam tuition sessions (#ubuntu-locoteams: 12 March, 9:00 UTC: Packaging Jams, 16 March, 9:00 UTC: Translation Jams) [https://wiki.ubuntu.com/UbuntuGlobalJam#TrainingSessions](https://wiki.ubuntu.com/UbuntuGlobalJam#TrainingSessions)
[*]blog about it and let your friends know!
[/LIST]

[http://daniel.holba.ch/blog/?p=623](http://daniel.holba.ch/blog/?p=623)

***[size="3"]Dylan McCall: New stuff for the Ubiquity slideshow(Proposed)[/size]***

Remember that slideshow when you did a fresh install of Ubuntu Karmic? For Lucid, ubiquity-slideshow is rocking, if I may say so myself. This is a really simple project with the goal of providing an introductory slideshow that runs when people install Ubuntu. The ubiquity-slideshow packages are all content packages, then Ubiquity displays that content at the right time.

The slideshow is implemented with Webkit, since all the cool people use Webkit. (It also renders things nicely, it's flexible, quick, we can quickly throw it on the web, people can make content really easily, and Javascript allows us a good split between interactive goodies and actual functionality like installing the operating system).

Michael Forrest and Otto Greenslade, from the design team, sent me a mockup and some graphics to fit with the exciting new Ubuntu branding. I worked them into the CSS and played with the text a little. Thus, behold, the proposed new look for the Ubuntu slideshow! [http://people.ubuntu.com/~dylanmccall/ubiquity-slideshow-ubuntu/redesign-lucid/ubuntu-transitions/slides/index.html#controls](http://people.ubuntu.com/~dylanmccall/ubiquity-slideshow-ubuntu/redesign-lucid/ubuntu-transitions/slides/index.html#controls)

Keep in mind this is still a proposal, just fully implemented (granted a few clunky bits).
Any constructive feedbacks or cries of “stop, you maniac!” are certainly not in vain.

[http://dylanmccall.blogspot.com/2010/03/new-stuff-for-ubiquity-slideshow.html](http://dylanmccall.blogspot.com/2010/03/new-stuff-for-ubiquity-slideshow.html)

***[size="3"]Alan Pope: Why (I think) Ubuntu is Better Than Windows[/size]***

When comparing operating systems people tend to roll out the same old reasons every time. I think those of us who use Ubuntu are already aware that we have less viruses than Windows, less malware, it’s free of cost and so on. I’m sure we’ve pointed out plenty of times that you’re legally entitled to copy the CD and even create your own remix.

However I wanted to look at some of the things I’ve done recently on Ubuntu that under Windows would be costly, difficult or impossible. Here's my list:

[LIST]
[*]Hardware support is better than you think
[*]Access more than 4GiB RAM on a 32-bit install out of the box
[*]Easily create a bootable, functional operating system on a USB stick
[*]Find out where each file comes from
[*]Email me when system updates are available
[*]Go from blank disk to fully installed in under an hour
[*]Move a hard disk
[*]Compiling and packaging applications for older OS releases
[*]Fixing a bug
[*]Re-install the OS and Applications without losing your data
[/LIST]

Alan goes into detail about each of the above bullet points at the link below.

[http://popey.com/blog/2010/03/11/why-ubuntu-is-better-than-windows/](http://popey.com/blog/2010/03/11/why-ubuntu-is-better-than-windows/)

**[size="5"]In The Press[/size]**

***[size="3"]The Linux Desktop Will Have Its Day: Q&A With Canonical Founder Mark Shuttleworth[/size]***

LinuxInsider's Jack M. Germain had an opportunity to interview Canonical founder Mark Shuttleworth recently, and he asked Shuttleworth questions such as "Given the growing reach of the Ubuntu server and desktop editions, what do you see as the driving factors for their acceptance?", and, "What will take Ubuntu to the next level?" To the second question Shuttleworth answered, "On the consumer front, we're seeing a shift in the way people think about alternative platforms to Windows amongst the PC companies. It used to be a kiss of death to present yourself as a genuine alternative to Windows. But the success of the Web and the success of Apple have really made the PC companies think that it is possible to offer something that is perceived to be valuable even if it is not Windows." Click on the following link to read what else Shuttleworth had to say, or listed to the Podcast of the interview.

[http://www.linuxinsider.com/rsstory/69444.html](http://www.linuxinsider.com/rsstory/69444.html)

***[size="3"]PC-BSD 8.0 vs. Kubuntu 9.10 Benchmarks[/size]***

Michael Larabel of Phoronix states that PC-BSD 8.0 was released last week and he took this opportunity to deliver a fresh set of PC-BSD 8.0 x64 benchmarks against Kubuntu 9.10 x86_64. In a majority of the tests, Kubuntu 9.10 performed better than PC-BSD 8.0, but the tests that Larabel used in this article are just a subset of what is available to run on both platforms via the Phoronix Test Suite so for those deciding between running PC-BSD / FreeBSD it is important to run the tests relevant to you and also consider the other features at hand for both free software operating systems. Click on this link to see the details of how Kubuntu 9.10 x86_64 compares to PC-BSD 8.0 x64.

[http://www.phoronix.com/scan.php?page=article&item=pcbsd8_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=pcbsd8_benchmarks&num=1)

***[size="3"]Ubuntu 10.04 To Hang Onto Old Intel Driver[/size]***

Phoronix's Michael Larabel says that when it comes to Intel's X.Org driver for Linux, xf86-video-intel, the most recent release was version 2.10 and it arrived in early January complete with Pineview (their next-generation Intel Atom systems) support, X-Video improvements, and various other features. The xf86-video-intel 2.11 driver is now emerging as their next quarterly update that brings in the KMS page-flipping and DRI2 swap events support. However, Ubuntu 10.04 LTS, which is set to be released in April, will not be shipping with either of these drivers. Instead Canonical's Bryce Harrington has announced that they have decided to stick with the xf86-video-intel 2.9 driver that was released last September. The decision to stick with this aging release is based on the fact that Intel stripped out user-space mode-setting (UMS) support from the xf86-video-intel 2.10 driver and that leaves this X.Org driver to only supporting kernel mode-setting.

[http://www.phoronix.com/scan.php?page=news_item&px=ODA1Mw](http://www.phoronix.com/scan.php?page=news_item&px=ODA1Mw)

***[size="3"]Redesigning Ubuntu – behind the scenes on 10.04[/size]***

Dave Walker of LinuxUser reminds us that the next version of Ubuntu – codename Lucid Lynx – will be the 10.04 release, and is scheduled to be released and declared stable in April.  As a long-term support version, coupled with increasing popularity, this is undoubtedly the most important Ubuntu release to date. Walker was privileged to be invited to the Canonical offices in London recently to preview the image changes and comment on how LinuxUser might adopt them; offer opinions on how he felt the community would interpret the changes, and offer feedback. Walker states that he is really positive about the changes and he's greatly motivated with Canonical's extended effort with requesting non-employee influence.  It really helps reinforce Canonical’s stance of community empowerment.  Particularly, as they made it clear they wanted to increase community involvement in this area which hasn’t traditionally had a massive community commitment.

[http://www.linuxuser.co.uk/news/redesigning-ubuntu-behind-the-scenes-on-10-04/](http://www.linuxuser.co.uk/news/redesigning-ubuntu-behind-the-scenes-on-10-04/)

***[size="3"]Taking Ubuntu 9.10 Netbook Remix out for a Spin[/size]***

IT News Today's Jeremy LaCroix tells us that for quite some time he has been intrigued by Ubuntu’s Netbook Remix (UNR), but he's never given it a shot up until now. LaCroix says that he's been using UNR for a couple of months now. When he first started playing with it, he didn’t own a netbook, so instead he tried it out on a Dell Latitude E6400 laptop. About a month later, he was gifted a Dell Mini 10 netbook, which afforded him the opportunity to try UNR in it’s intended environment. Overall, even though LaCroix typically doesn’t use GNOME, the way the desktop was presented in UNR 9.10 was actually pretty cool. "Sure, it took some getting used to, and I probably have strange tastes, but I did enjoy using it, despite the little issues I ran into." UNR also seems like the best choice for any compatible Netbook, because LxCroix says that he has tried using Windows on Netbooks and it’s not pretty at all.

[http://www.itnewstoday.com/?p=1427](http://www.itnewstoday.com/?p=1427)

***[size="3"]Ubuntu Server: The Linux OS Dark Horse[/size]***

Kenneth Hess of ServerWatch knows that everyone has heard of Ubuntu Linux and how great it is on the desktop, but have you heard that there's a server version of that same uber-cool operating system? There is, and you should know about it. Ubuntu Server not only follows the same twice yearly updates (April and October) as its desktop counterpart does, but it also benefits from unsurpassed commercial support, consulting and training available through Canonical. Ubuntu melds outstanding performance with easy installation and excellent hardware support. Add those features to its superior commercial support, long-term support commitment and unique cloud computing platform, and you have a formidable rival to its entrenched competition. Keep an eye on Ubuntu, it's likely to be a photo finish for this dark horse.

[http://www.serverwatch.com/trends/article.php/3870141/Ubuntu-Server-The-Linux-OS-Dark-Horse.htm](http://www.serverwatch.com/trends/article.php/3870141/Ubuntu-Server-The-Linux-OS-Dark-Horse.htm)

***[size="3"]Ubuntu, The Ultimate Linux Distribution[/size]***

DaniWeb's Ken Hess thinks that from its Debian roots to its commercially available support to its overwhelming popularity, Ubuntu is the ultimate Linux distribution. Ubuntu is the distribution most often recommended to users new to Linux or those switching from other distributions. Its ease of installation, quick boot times, GNOME user interface and twice yearly major updates keep it at the top of everyone's best distribution list. And, every two years, a new LTS (Long Term Support) version is released. Ubuntu has two major subversions: Desktop and Server. For the desktop, you may choose something other than the default GNOME desktop: Kubuntu, Xubuntu, Edubuntu and a Netbook Remix. On the server side, you can select the standard Ubuntu server or the Ubuntu Enterprise Cloud. It's no wonder that Ubuntu is the world's most popular Linux distribution with several choices for any purpose or application, an absolutely easy to install system, commercial support and a successful track record of security and popularity that speaks volumes since its inception.

[http://www.daniweb.com/news/story265826.html#](http://www.daniweb.com/news/story265826.html#)

**[size="5"]In The Blogosphere[/size]**

***[size="3"]16 things that could be improved in Ubuntu 10.04[/size]***

Over on the OMG!Ubuntu site Benjamin Humphrey writes about the 16 things that he thinks could be improved in Lucid. Hunphrey addresses the issues in detail and offers solutions. He acknowledges that these fixes are a matter of his opinion as well. Humphrey states that the object of this post is to make readers think about ways we could improve each one. If there are bugs he links to those as well. The post has screen shots of each issue that were taken about two hours after he installed Lucid Lynx alpha 3, daily build from Saturday March 6th 2010 after the UI freeze.

 1. Window Controls
 2. Bug #403135 – Notification area background transparency Fixed in the default themes
 3. Rhythmbox search for plugin
 4. Software Center progress bar Fixed!
 5. Gnome menu icons
 6. Notification area margins
 7. Notification area
 8. Default font size and default pointer Probably won’t be changed!
 9. Ctrl+Alt+Delete Probably won’t be changed!
 10. Pidgin should minimize to messaging menu, instead of closing
 11. Computer Janitor should not be in Ubuntu
 12. Preferences menu is huge!
 13. Volume applet now looks terrible
 14. What happened to the nice battery stats window?
 15. MeMenu doesn’t pick up the image from About Me Fixed!
 16. MeMenu text box doesn’t explain what it does

If any or all of these issues are of interest to you take time to check out the article at: [http://www.omgubuntu.co.uk/2010/03/16-things-that-could-be-improved-in.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29](http://www.omgubuntu.co.uk/2010/03/16-things-that-could-be-improved-in.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29)

***[size="3"]Ubuntu 10.04 Live CD Installer gets a slick new look[/size]***

In this article the folks over at OMG!Ubuntu take a look at the Ubuntu 10.04 Live CD installer.  For those of you who haven't installed Ubuntu 10.04 you will get to see the screen shots of the new look.  The screen shots take a look at the new installer, and points out both the similarities and the differences between earlier releases and what you can expect in Ubuntu 10.04. [http://www.omgubuntu.co.uk/2010/03/ubuntu-1004-live-cd-installer-gets.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29](http://www.omgubuntu.co.uk/2010/03/ubuntu-1004-live-cd-installer-gets.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29)

***[size="3"]Ubuntu Software Centre Gets Brand New Look for Lucid; Paid software to feature soon?[/size]***

In this article the OMG!Ubuntu folks will take you on a screen shot tour of the fresh new look of the Ubuntu Software Centre. The screen shots show the "Featured" button that is now in a prominently place of display. The article notes that the application view has been brightened up as well.  The author also notes that a new "Themes and Tweaks category has been added. The author points out the button that specifically states "Install-Free" and wonders if this is a possible hint that non-free software may be included in the future.  The author notes that there are still some issues to be addressed but the new look of the Ubuntu Software Centre screams professionalism.  [http://www.omgubuntu.co.uk/2010/03/ubuntu-software-centre-gets-brand-new.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29](http://www.omgubuntu.co.uk/2010/03/ubuntu-software-centre-gets-brand-new.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29)

**[size="5"]In Other News[/size]**

***[size="3"]Ubuntu hits HTC's Touch Pro2, is any Windows Mobile handset safe?[/size]***

Tim Stevens, engadget, takes a look at Brandon Miniman's post on pocketnow.com, in which Miniman demos Ubuntu 8.04 on an HTC Touch Pro2. This article not only has the video but also walks you though how to install Ubuntu on the device. .  Also noted is the fact that Ubuntu also runs on the Xperia X1.  Stevens states, "It looks quite easy: just download a 200MB zip, extract it to your phone, then run an exe within. A few moments later you'll be in open source heaven, and, from what we can tell looking at the video below, it works remarkably well"  [http://www.engadget.com/2010/03/09/ubuntu-hits-htcs-touch-pro2-is-any-windows-mobile-handset-safe/](http://www.engadget.com/2010/03/09/ubuntu-hits-htcs-touch-pro2-is-any-windows-mobile-handset-safe/)

**[size="5"]Upcoming Meetings and Events[/size]**

***[size="3"]Monday, March 15, 2010[/size]***

==== Security Team Catch-up ====

[LIST]
[*]Start: 18:00 UTC
[*]End: 18:30 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: nothing formal, just a weekly catch-up.
[/LIST]

***[size="3"]Tuesday, March 16, 2010[/size]***

==== Community Council Meeting ====

[LIST]
[*]Start: 11:00 UTC
[*]End: 13:00 UTC
[*]Location: #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/CommunityCouncilAgenda](https://wiki.ubuntu.com/CommunityCouncilAgenda)
[/LIST]

==== Ubuntu Mobile Team Meeting ====

[LIST]
[*]Start: 13:00 UTC
[*]End: 14:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/MobileTeam/Meeting](https://wiki.ubuntu.com/MobileTeam/Meeting)
[/LIST]

==== Developer Membership Board ====

[LIST]
[*]Start: 15:00 UTC
[*]End: 16:00 UTC
[*]Location: Not listed as of publication
[*]Agenda: Not listed as of publication
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
[*]Location:  IRC channel #ubuntu-meeting
[*]Agenda: Not listed as of publication
[/LIST]

==== LoCo Council Meeting ====

[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/LoCoCouncilAgenda](https://wiki.ubuntu.com/LoCoCouncilAgenda)
[/LIST]

***[size="3"]Wednesday, March 17, 2010[/size]***

==== Server Team Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda:  [https://wiki.ubuntu.com/ServerTeam/Meeting](https://wiki.ubuntu.com/ServerTeam/Meeting)
[/LIST]

==== Foundation Team Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:00 UTC
[*]Location:  IRC channel #ubuntu-meeting
[*]Agenda:  Not listed as of publication
[/LIST]

==== QA Team Meeting ====

[LIST]
[*]Start: 17:00 UTC
[*]End: 18:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda:  [https://wiki.ubuntu.com/QATeam/Meetings/](https://wiki.ubuntu.com/QATeam/Meetings/)
[/LIST]

==== Edubuntu Meeting ====

[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [https://wiki.ubuntu.com/Edubuntu/Meetings/Agenda](https://wiki.ubuntu.com/Edubuntu/Meetings/Agenda)
[/LIST]

***[size="3"]Thursday, March 18,2010[/size]***

==== Lucid Lynx, Ubuntu 10.04 Beta 1 Release ====

==== Ubuntu Java Meeting ====

[LIST]
[*]Start: 14:00 UTC
[*]End: 15:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda:  None listed as of publication
[/LIST]

==== Ubuntu Backports team ====

[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: Free discussion
[/LIST]

***[size="3"]Friday, March 19, 2010[/size]***

==== Lucid Weekly Release Meeting ====

[LIST]
[*]Start: 16:00 UTC
[*]End: 17:30 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda: [http://wiki.ubuntu.com/ReleaseTeam/Meeting/2010-03-19](http://wiki.ubuntu.com/ReleaseTeam/Meeting/2010-03-19)
[/LIST]

***[size="3"]Saturday, March 20, 2010[/size]***

==== BugJam ====

[LIST]
[*]Start: 20:00 UTC
[*]End: 22:00 UTC
[*]Location: IRC channel #ubuntu-us-dc and IRC channel #ubuntu-bugs
[*]Agenda: None listed as of publication
[/LIST]

==== DC Loco IRC meeting ====

[LIST]
[*]Start: 22:00 UTC
[*]End: 23:00 UTC
[*]Location: IRC channel #ubuntu-us-dc
[*]Agenda: None listed as of publication
[/LIST]

***[size="3"]Sunday, March 21, 2010[/size]***

==== Xubuntu Team Meeting ====

[LIST]
[*]Start: 19:00 UTC
[*]End: 20:00 UTC
[*]Location: IRC channel #ubuntu-meeting
[*]Agenda:  [https://wiki.ubuntu.com/Xubuntu/Meetings](https://wiki.ubuntu.com/Xubuntu/Meetings)
[/LIST]

**[size="5"]Updates and Security for 6.06, 8.04, 8.10, 9.04 and 9.10[/size]**

***[size="3"]Security Updates[/size]***

[LIST]
[*]USN-907-1: gnome-screensaver vulnerabilities - [http://www.ubuntu.com/usn/USN-907-1](http://www.ubuntu.com/usn/USN-907-1)
[*]USN-908-1: Apache vulnerabilities - [http://www.ubuntu.com/usn/USN-908-1](http://www.ubuntu.com/usn/USN-908-1)
[*]USN-909-1: dpkg vulnerability - [http://www.ubuntu.com/usn/USN-909-1](http://www.ubuntu.com/usn/USN-909-1)
[*]USN-911-1: MoinMoin vulnerabilities - [http://www.ubuntu.com/usn/USN-911-1](http://www.ubuntu.com/usn/USN-911-1)
[/LIST]

***[size="3"]Ubuntu 6.06 Updates[/size]***

[LIST]
[*]langpack-locales 2.3.18.31 - [https://lists.ubuntu.com/archives/dapper-changes/2010-March/012819.html](https://lists.ubuntu.com/archives/dapper-changes/2010-March/012819.html)
[*]langpack-locales 2.3.18.32 - [https://lists.ubuntu.com/archives/dapper-changes/2010-March/012820.html](https://lists.ubuntu.com/archives/dapper-changes/2010-March/012820.html)
[*]apache2 (delayed)- [https://lists.ubuntu.com/archives/dapper-changes/2010-March/012821.html](https://lists.ubuntu.com/archives/dapper-changes/2010-March/012821.html)
[*]dpkg- [https://lists.ubuntu.com/archives/dapper-changes/2010-March/012822.html](https://lists.ubuntu.com/archives/dapper-changes/2010-March/012822.html)
[*]moin (delayed)- [https://lists.ubuntu.com/archives/dapper-changes/2010-March/012823.html](https://lists.ubuntu.com/archives/dapper-changes/2010-March/012823.html)
[/LIST]

***[size="3"]Ubuntu 8.04 Updates[/size]***

[LIST]
[*]tzdata 2010c~repack-0ubuntu0.8.04 - [https://lists.ubuntu.com/archives/hardy-changes/2010-March/012418.html](https://lists.ubuntu.com/archives/hardy-changes/2010-March/012418.html)
[*]tzdata 2010e~repack-0ubuntu0.8.04 - [https://lists.ubuntu.com/archives/hardy-changes/2010-March/012419.html](https://lists.ubuntu.com/archives/hardy-changes/2010-March/012419.html)
[*]apache2 (delayed)- [https://lists.ubuntu.com/archives/hardy-changes/2010-March/012420.html](https://lists.ubuntu.com/archives/hardy-changes/2010-March/012420.html)
[*]apache2-mpm-itk- [https://lists.ubuntu.com/archives/hardy-changes/2010-March/012421.html](https://lists.ubuntu.com/archives/hardy-changes/2010-March/012421.html)
[*]dpkg_1.14.16.6ubuntu4.1_i386_translations.tar.gz- [https://lists.ubuntu.com/archives/hardy-changes/2010-March/012422.html](https://lists.ubuntu.com/archives/hardy-changes/2010-March/012422.html)
[*]moin_1.5.8-5.1ubuntu2.3_i386_translations.tar.gz (delayed)- [https://lists.ubuntu.com/archives/hardy-changes/2010-March/012423.html](https://lists.ubuntu.com/archives/hardy-changes/2010-March/012423.html)
[/LIST]

***[size="3"]Ubuntu 8.10 Updates[/size]***

[LIST]
[*]tzdata 2010c~repack-0ubuntu0.8.10	- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009854.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009854.html)
[*]gnome-screensaver- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009855.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009855.html)
[*]tzdata 2010e~repack-0ubuntu0.8.10	- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009856.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009856.html)
[*]apache2 (delayed)- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009857.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009857.html)
[*]apache2-mpm-itk- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009858.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009858.html)
[*]dpkg_1.14.20ubuntu6.3_ia64_translations.tar.gz- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009859.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009859.html)
[*]moin- [https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009860.html](https://lists.ubuntu.com/archives/intrepid-changes/2010-March/009860.html)
[/LIST]

***[size="3"]Ubuntu 9.04 Updates[/size]***

[LIST]
[*]tzdata 2010c~repack-0ubuntu9.04 - [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010019.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010019.html)
[*]gnome-screensaver_2.24.0-0ubuntu6.1_powerpc_translations.tar.gz- [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010020.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010020.html)
[*]tzdata 2010e~repack-0ubuntu9.04 - [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010021.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010021.html)
[*]apache2 (delayed)- [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010022.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010022.html)
[*]apache2-mpm-itk- [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010023.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010023.html)
[*]dpkg_1.14.24ubuntu1.1_amd64_translations.tar.gz- [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010024.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010024.html)
[*]moin- [https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010025.html](https://lists.ubuntu.com/archives/jaunty-changes/2010-March/010025.html)
[/LIST]

***[size="3"]Ubuntu 9.10 Updates[/size]***

[LIST]
[*]tzdata 2010c-0ubuntu0.9.10 - [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012277.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012277.html)
[*]gnome-screensaver_2.28.0-0ubuntu3.5_sparc_translations.tar.gz	(delayed)- [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012278.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012278.html)
[*]openbravo-erp 2.50MP-11-4 - [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012279.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012279.html)
[*]get-iplayer 2.41-1ubuntu0.1 - [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012280.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012280.html)
[*]tzdata 2010e-0ubuntu0.9.10 - [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012281.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012281.html)
[*]apache2 (delayed)- [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012282.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012282.html)
[*]dpkg_1.15.4ubuntu2.1_powerpc_translations.tar.gz- [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012283.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012283.html)
[*]moin- [https://lists.ubuntu.com/archives/karmic-changes/2010-March/012284.html](https://lists.ubuntu.com/archives/karmic-changes/2010-March/012284.html)
[/LIST]

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
[*]John Crawford
[*]Craig A. Eddy
[*]Dave Bush
[*]Amber Graner
[*]J Scott Gwin
[*]Liraz Siri
[*]And many others
[/LIST]

**[size="5"]Glossary of Terms[/size]**

 1. API - Application Programming Interface
 1. IRC - Internet Relay Chat
 1. LTS - Long Term Support. - Said of a release that will receive support for 3-years/5-years rather than the typical 18 months
 1. OS - Operating System
 1. Q&A - Question And Answer
 1. QA - Quality Assurance
 1. SRU - Stable release updates. - [http://wiki.ubuntu.com/StableReleaseUpdates](http://wiki.ubuntu.com/StableReleaseUpdates)
 1. UEC - Ubuntu Enterprise Cloud
 1. UNR - Ubuntu Netbook Remix
 1. UTC - Coordinated Universal Time: UTC replaced GMT as the basis for the main reference time scale or civil time in various regions on January 1, 1972

Other acronyms can be found at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/glossary)

**[size="5"]Ubuntu - Get Involved[/size]**

The Ubuntu community consists of individuals and teams, working on different aspects of the distribution, giving advice and technical support, and helping to promote Ubuntu to a wider audience. No contribution is too small, and anyone can help. It's your chance to get in on all the community fun associated with developing and promoting Ubuntu. [http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)

**[size="5"]Feedback[/size]**

This document is maintained by the Ubuntu Weekly News Team. If you have a story idea or suggestions for the Weekly Newsletter, join the Ubuntu News Team mailing list at [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-news-team) and submit it. Ideas can also be added to the wiki at [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Ideas). If you'd like to contribute to a future issue of the Ubuntu Weekly Newsletter, please feel free to edit the appropriate wiki page. If you have any technical support questions, please send them to [email]ubuntu-users@lists.ubuntu.com[/email].

Except where otherwise noted, content in this issue is licensed under a Creative Commons Attribution 3.0 License
[http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/)

---

