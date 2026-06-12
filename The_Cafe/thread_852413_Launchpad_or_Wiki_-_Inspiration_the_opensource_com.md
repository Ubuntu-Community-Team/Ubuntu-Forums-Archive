---
title: "Launchpad or Wiki - Inspiration the opensource community to collaborate on papers"
date: 2008-07-07
forum: The Cafe
---

### Post by aphelionos on 2008-07-07
Hi.

I am part of a benevolent network of academics. We are a global network connecting reasearchers from all parts of the world, and usually we meet at conferences to exchange information and work together. This is naturally quite costly, as people from all over the world.

The Open Source community has managed something hardly done before when being able to produce such a quantity of programs and code through loose networks, and i wish to use some of these systems to facilitate close collaboration on papers and reports with people from all over the world.

You could say "use goodle documents" but theres something more to some of the open systems used in software developing. Especially Launchpad is impressive in the way you can hace different users access different spaces, and assign users to different tasks being collected upstream to a complete project (my knowledge of launchpad is limited, but this is my impression). 

My question is: Does anybody know of a project similar to launchpad that could be used for collaboration on academic papers, books and reports? Would a Wiki system be better, which and why?
Are there any open source systems that could be modified (I understand that launchpad is not open source?)?
Any other thoughts on this subject are welcome, thanks a lot.

---

### Post by phrostbyte on 2008-07-07
A wiki system is ideal for academic collaboration. Should you need something more complex then that, a source-control system such as Bazaar or Subversion can be used quite effectively to collaborate on non-code projects, but usually have a higher learning curve.

Launchpad is basically a conglomerate of various specialized tools all merged to one (bug tracker, project planner, source control, etc.). Unfortunately the majority of it isn't open source, and is still a point of contention for some people. 

Here are some links to look at:
[http://trac.edgewall.org/](http://trac.edgewall.org/) - Trac (for project management, very popular in the FOSS world)
[http://subversion.tigris.org/](http://subversion.tigris.org/) - Subversion, a source control system (you can think of it as a non-web wiki geared toward sharing code rather then words)

---

### Post by aphelionos on 2008-07-07
Hi.

Trac looks quite interesting, but as I'm very new to these systems (I can use Bugtracker) I don't understand everything. So Trac integrates Subversion, and how is subversion any use for papers? I thought it was a kind of repo for prgorams.

Are there any Newbie walkthroughs for Wiki use and especially Trac?

---

### Post by phrostbyte on 2008-07-07
> **aphelionos said:**
> Hi.

Trac looks quite interesting, but as I'm very new to these systems (I can use Bugtracker) I don't understand everything. So Trac integrates Subversion, and how is subversion any use for papers? I thought it was a kind of repo for prgorams.

Are there any Newbie walkthroughs for Wiki use and especially Trac?

Subversion can be used to collaborate on any data. It contains features and utilities that make it good for source control (especially shown when there is a merge conflict), but it's not limited to source control. Subversion can be thought of as a tool for general collaboration, as well as Bazaar, Git, Mercurial, and others.

There are plenty of guides on how to use Trac on that site. Again though I think a wiki is the best idea.

MediaWiki is a good one if you didn't know already. It is the software behind Wikipedia.

---

### Post by mikjp on 2008-07-08
I think open source community should in any case use only open source software for collaboration. So forget Google apps and Launchpad.

Mediawiki comes to my mind.

---

