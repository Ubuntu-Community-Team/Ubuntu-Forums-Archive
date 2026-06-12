---
title: "Auto Update Hardy Desktop"
date: 2008-09-05
forum: Security
---

### Post by Rever75 on 2008-09-05
Hi all,
   We will be install approximately 30 Ubuntu Desktops in our company. I was wondering if there is a way to have the workstations automatically update each week. We want to make sure all components of the system remain secure. If a script is needed and placed in cron that is fine I was just wondering if there was another way with Ubuntu.

---

### Post by Oldsoldier2003 on 2008-09-05
As a side note, with 30 workstations it might be worth the effort to mirror the repos locally and point your machines to you own server as their sofwtare source.

---

### Post by Gallardo Spyder on 2008-09-05
You can just set auto update / update manager to update weekly, daily, etc.  You can also have it autoinstall security fixes (or all). 

First check if you have update manager in your System/admisitration folder.

Then open Software Sources in system administration menu...

You can go to the update tab and take a look at the options.  You would have to set this on all the PC's - but should only take a few minutes each...

---

### Post by Rever75 on 2008-09-05
Yeah I was planning on doing that. Kinda like a WSUS Server for Linux. Do you know if I could get Stats as to which systems have been updated by using a local mirror?

---

### Post by Rever75 on 2008-09-05
Cool thanks this should not be much of an issue. We can do i t during the install. We are also looking at installing using CloneZilla.

---

### Post by shibu on 2008-09-05
Announced at the Ubuntu Live conference, Landscape is a web-based systems management platform that simplifies administration of desktop and server computers running Ubuntu.
Landscape makes it possible to remotely deploy patches, updates, and packages. 

or check the below 

Puppet is system administration — Automated

[http://reductivelabs.com/trac/puppet/wiki/InstallationGuide](http://reductivelabs.com/trac/puppet/wiki/InstallationGuide)
[http://reductivelabs.com/trac/puppet/wiki/FrequentlyAskedQuestions](http://reductivelabs.com/trac/puppet/wiki/FrequentlyAskedQuestions)

---

