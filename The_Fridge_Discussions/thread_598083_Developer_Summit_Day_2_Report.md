---
title: "Developer Summit Day 2 Report"
date: 2007-10-31
forum: The Fridge Discussions
---

### Post by TheFridge on 2007-10-31
Day 2 of the Developer Summit was sunny and beautiful, as many took advantage of the rooftop garden near the conference rooms. Starting the sessions today were roundtables about many topics including the community, desktop, server, and others. After these followed the usual sessions, as per [today&#8217;s schedule]("http://people.ubuntu.com/~scott/uds-boston-2007/2007-10-30/index.html").
 **Community Roundtable**
 The community roundtable covered around many issues but started with the issue of burnout, how to deal with it, how to look for it and what sort of resources need to be available. The possibility of a resource pack was discussed but no overall consensus was reached. Jono emphasized that part of his, Jorge and Daniel&#8217;s roles is to help deal with this sort of issue and that the door is, figuratively speaking, always open, something he later [blogged about]("http://www.jonobacon.org/?p=1067").  The need to de-stress was also talked about, with discussion of some sort of gaming tournament and of course, the need to get out from behind the computer and do something real featuring on the list of potential resolutions.
 **Defining a roadmap for supporting LoCo teams**
 This spec started with a reiteration of the need for the creation of a LoCo council to approve LoCo teams. Exactly who should be on such a council is not yet decided, but it was also restated that the council will help remove the bottleneck for IRC channels, forums, websites, mailing lists and other LoCo resources. The discussion then moved to the mentoring of the AfricaTeams projects, including possible &#8220;twinning&#8221; of wealthier teams with those in less advantaged parts of the world. From there the discussion moved to the need to create an event box, although exact details were not discussed. One of the last pieces discussed was the need to create a QA information list for LoCo teams, to allow them to run testing labs and bug days and the like. The [defining-loco-roadmap spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/defining-loco-roadmap") is still in New and may have another discussion session.
 **Rethinking the logout dialog**
The logout dialog has had many critiques in the year or so since it&#8217;s introduction, mostly due to the nature of having seven options in a single menu. In order to reduce those numbers, the discussion turned to removing restart and shutdown options, making it default to always save the session at logout. However, Hibernate will not work reliably if a user dual-boots, leading to the rejection of that idea. Another idea was raised to possibly make the logout dialog the GDM screen, provided it can be made fast enough.  In the end, no clear consensus was reached on these issues, however there was strong consensus that the shutdown sounds should be disabled by default. The [logout-dialog spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/logout-dialog") is still New and may have another session.
 **Automatix and Ubuntu collaboration**
Making Automatix and Ubuntu teams work better together is a topic of much discussion and today&#8217;s work covered evaluating the list of applications that are installed by Automatix, where they are and what needs to be done to get those that are not in the repositories in, if possible.  Most features currently in Automatix could be turned into packages for Universe, Multiverse, or Partner.
 **Third Party Apt**
*Report provided by Scott Ritchie*
 ThirdPartyApt does for apt repositories what GDebI did for packages. Participants in the discussion expressed some reluctance towards making it easier to install non-Ubuntu supported packages, however there was general consensus that this is something users want.  Moreover, having any sort of standard is better than the current situation, where custom install scripts avoid apt and don&#8217;t leave uninstallation metadata, handle conflicts, or allow security updates. For third parties using apt, complicated instructions like those for [Wine]("http://winehq.org/site/download-deb") and [Google]("http://www.google.com/linuxrepositories/ubuntu704.html") can be replaced with a single file. The [third-party-apt spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/third-party-apt") is now in Drafting and will not have another session.
 As per usual, a single person  cannot exist in such a quantum state and as such, not all of the  dozens of sessions were covered. If you are at UDS and want something you talked about covered, please come and see Corey Burger or [EMAIL="corey.burger@ubuntu.com"]email me[/EMAIL].
 

[More...](http://fridge.ubuntu.com/node/1200)

---

