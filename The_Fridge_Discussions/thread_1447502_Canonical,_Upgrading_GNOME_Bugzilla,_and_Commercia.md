---
title: "Canonical, Upgrading GNOME Bugzilla, and Commercial Sponsorship"
date: 2010-04-05
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-04-05
Authored by: Sumana Harihareswara

 You may have noticed the spiffy new GNOME Bugzilla. Sumana Harihareswara presents the story of how and why it came to be.

 GNOME is [asking for donations]("http://www.gnome.org/friends/") to hire a [sysadmin]("http://live.gnome.org/Sysadmin/AdvisoryMeeting/JobDescription"). That’s because GNOME’s technological infrastructure—like source control, bug tracking, web and mail servers—make the rest of GNOME possible. Recently, Canonical found its efforts blocked by deficiencies in GNOME’s infrastructure. Specifically, our [bugtracking software]("https://bugzilla.gnome.org/") was too obsolete for them to programmatically interface with. So Canonical recently spent tens of thousands of USD to upgrade the GNOME Bugzilla instance from 2.20 to 3.4—including porting forward several beloved customizations.

 The story started with Launchpad, Canonical’s collaborative development tool and the Ubuntu development hub. Launchpad has [included a Remote Bug Watch feature]("http://blog.launchpad.net/bug-tracking/launchpads-bug-watch-system-and-other-animals") from the start. Launchpad users could use this to associate Launchpad bugs with bugs in several external trackers. As Max Kanat-Alexander of consulting firm Everything Solved explains, “the most popular bug-tracker that Launchpad projects were interfacing without outside of Launchpad itself were Bugzilla installations.”

 Canonical’s Christian Robottom Reis had previously worked on Bugzilla upstream, and appreciated it: “I know how cool a tool it is. We know organizations are invested in the tools they’ve chosen; we don’t expect them to come across to Launchpad for our primary benefit. So we’ve put work into making sure Launchpad plugs well into their infrastructure. All the work around bug watches, branch synchronization and translations emphasizes our coexistence with other tools.”

 Kanat-Alexander had worked with Bugzilla upstream to add Launchpad integration capabilities to Bugzilla 3.4. As FLOSS projects upgrade to Bugzilla 3.4 and up, this may reduce bug duplication across the entire Linux ecosystem.

 But a big part of the equation was missing. “In particular,” Kanat-Alexander continues, “the single most popular bug-tracker for Launchpad projects outside of Launchpad itself was the [GNOME Bugzilla]("https://bugs.edge.launchpad.net/bugs/bugtrackers/gnome-bugs").” Since Ubuntu depends heavily on GNOME, Launchpad bugs often related to (or were duplicates of) GNOME bugs. As you can see from the [list of remote bug trackers]("https://bugs.edge.launchpad.net/bugs/bugtrackers"), GNOME has (at the time of writing) 15761 associated watches, as compared to the next highest bugtrackers, [Debian]("https://bugs.edge.launchpad.net/bugs/bugtrackers/debbugs") at 12231 (followed by KDE, freedesktop.org, SourceForge.net, and Mozilla, all in the thousands).

 But the remote watch didn’t work with GNOME’s fairly ancient Bugzilla. As Bugzilla development passed its 3.4 release and worked on 3.6, GNOME’s instance was still on 2.20, originally released in [September 2005]("http://www.bugzilla.org/news/"). And the age was showing. As Kanat-Alexander notes, “There were productivity issues, many needed new features, and serious, serious performance problems. Bugzilla 2.20 was WAY slower than version 3.0 or above, and it was on a old, slow server to boot.” Bugzilla 2.20 had been end-of-lifed in November 2008, so GNOME’s installation was also barred from getting security fixes.

 Because of the disconnect, Ubuntu developers were wasting substantial time manually associating Launchpad and GNOME bugs. That bottleneck made Reis unhappy. “It’s hard to measure efficiency financially, but our view of engineering process is that it’s absolutely strategic to us. If engineers are spending time doing chores instead of engineering, we try hard to find tools to assist them,” Reis explains.

 Canonical considered asking GNOME sysadmins to install a plugin that older bugtrackers, [such as Bugzilla 3.0]("https://edge.launchpad.net/bugzilla-launchpad"), can use to integrate better with Launchpad’s remote bug watch. “That plugin offers the same kind of API as Max’s additions to Bugzilla 3.4,” says Canonical engineer Graham Binns. “But the GNOME Bugzilla was, at the time, too out-of-date to be able to work with the plugin.”

 GNOME Bugzilla had so many modifications that upgrading it would be arduous. “The GNOME resources available to upgrade Bugzilla to any version after 2.20 were basically nonexistent. Though Olav [Vitters] and the other system administrators had tried for many years to find the time and assistance to port forward the massive GNOME Bugzilla customizations (or even better, contribute them upstream), since everybody was operating on a volunteer basis, the time for such a massive project just couldn’t be found,” says Kanat-Alexander.

 Canonical then offered to pay for Everything Solved to port forward key custom features (such as the Bug-Buddy interface, CSS customizations, and browse.cgi) as Bugzilla 3.4 features or extensions, and then upgrade GNOME’s bugtracker. Everything Solved’s initial estimate (for porting all customizations) had proven prohibitively expensive and lengthy for Canonical’s tastes, so Vitters, GNOME sysadmins and developers, and Everything Solved [developed a list of key features to keep]("http://mail.gnome.org/archives/desktop-devel-list/2008-December/msg00008.html"). They [left]("http://mail.gnome.org/archives/desktop-devel-list/2008-December/msg00033.html") some [low-priority ones out]("http://mail.gnome.org/archives/desktop-devel-list/2009-August/msg00038.html"), such as canned responses and the points system. The GNOME Foundation accepted this offer, acknowledging a tradeoff in some functional regressions just after the upgrade. Stormy Peters, GNOME Foundation Executive Director, was especially pleased to see improvements in GNOME infrastructure coming from a company, a consultant, and the GNOME Foundation working together.

 Kanat-Alexander and Peters worked out an agreement, and in April 2009, the development work began. Graham Binns updated Launchpad’s bug syncing code to work with the API that Kanat-Alexander was adding to Bugzilla.

 In August 2009, Everything Solved [delivered]("http://mail.gnome.org/archives/gnome-infrastructure/2009-August/msg00030.html") the final customizations to GNOME’s volunteer sysadmins. The consultant and sysadmins moved Bugzilla to new servers donated by Red Hat, optimized MySQL performance, [tested the new customizations]("http://mail.gnome.org/archives/desktop-devel-list/2009-July/msg00269.html"), and then did the final rollout. To minimize downtime, Everything Solved also added upstream fixes to speed up the Bugzilla upgrade process.

 GNOME bug-wranglers can now enjoy Bugzilla’s per-product permissions, duplicate prevention, localization, and myriad enhancements from the last few years. And Bugzilla users will get to enjoy several features that started with GNOME’s modifications. The [browse.cgi view]("https://bugzilla.gnome.org/browse.cgi?product=epiphany") gives you a dashboard view of a project’s outstanding bugs and patches. Users can indicate the status of an attachment to a bug (e.g., “accepted-commit_now” or “needs-work”). Everything Solved also developed a stack-trace parsing extension, traceparser, for Bugzilla 3.6. All in all, Everything Solved upstreamed more than forty features or bugfixes.

 GNOME-related Bugzilla contributions are still necessary, Vitters reminds us: we need to port Bugzilla 3.4 extensions to 3.6, and some customizations still haven’t gotten ported at all. But according to Kanat-Alexander:

 “The community (particularly Frédéric Peters) [stepped up to develop the most important of the ‘missing’ features that hadn’t been ported forward]("http://blogs.gnome.org/ovitters/2009/09/14/bugzilla-changes/")! Though before the upgrade it was almost impossible to get a review or any code assistance with developing customizations for Bugzilla, after the upgrade, with a ‘finished’ product in place, the contributions really started rolling in.”

 Launchpad remote bug watch developers still have a lot of work to do from their end. Canonical is eager to see Mozilla, KDE, and Freedesktop.org upgrade their bugtrackers to improve Launchpad integration. GNOME was Canonical’s highest priority, though; “we haven’t worked officially with any other organization to get this installed,” says Reis, confirming GNOME’s critical importance to Ubuntu.

 In short, the makers of Launchpad paid for improvements to Bugzilla, a competing product—not to mention that Ubuntu’s competitors will benefit from improvements to GNOME. As Reis notes, Canonical views this as “bridging the gap” from Ubuntu to upstream.

 In the open source community we’re generally skeptical of bug bounties. We [worry]("http://mako.cc/writing/funding_volunteers/funding_volunteers.html") that paying for development work crowds out volunteer labor instead of adding to it, and degrades intrinsic motivation in favor of extrinsic rewards. And while branded parties and swag feel nice, it’s debatable how much they really contribute to FLOSS. But Canonical, GNOME, and Everything Solved have gone another route, using commercial sponsorship to address longstanding infrastructure rot. Canonical, Google, Collabora, and Nokia recently donated to aid in hiring a fulltime GNOME sysadmin, continuing in (hopefully) corporate/community partnership, not displacement.

 [Discuss this story]("http://gnomesupport.org/forums/viewforum.php?f=24") with other readers on the [GNOME forums]("http://gnomesupport.org/forums/index.php").

 This article originated in <a href="http://www.gnomejournal.org/article/96/canonical-upgrading-gnome-bugzilla-and-commercial-sponsorship">The GNOME Journal<a />

 

[More...](http://fridge.ubuntu.com/node/2007)

---

