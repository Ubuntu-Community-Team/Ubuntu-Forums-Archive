---
title: "Affect to Applications caused by Security Updates?"
date: 2015-02-24
forum: Security
---

### Post by amilauduwerella on 2015-02-24
I want my Server to run "unattended-upgrades" regularly and Keep my server auto update and install only security Updates.

But I have a problem, that I don't want to update the main version of few software.

For Example: I want my server to have PHP 5.4 running I am OK with minor updates such as:

5.4.30 to 5.4.37 or 5.4.xx to 5.4.yy
But I don't want to change the main version updates, such as:

5.4.48 to 5.5.1 or 5.x.a to 5.y.a
Can this be done with "unattended-upgrades" ?

Right now what I have done was: exclude PHP5-* from being auto updated by unattended-upgrades. Is there a better way to do this?

Or Is there a standard on Ubuntu Security Updates, like they do not upgrade the main version of an application, Such as:

5.4.48 to 5.5.1 or 5.x.a to 5.y.a

---

### Post by ian-weisser on 2015-02-24
> **amilauduwerella said:**
> I want my Server to run "unattended-upgrades" regularly and Keep my server auto update and install only security Updates.

But I have a problem, that I don't want to update the main version of few software.

Your system isn't smart enough to know if a particular update includes a new feature, a bugfix, or a security patch.
It only knows the software's *repository*.
Happily, you can tell (and filter) based on the repository.

If the upstream project releases a security patch for a CVE, the Ubuntu Security Team applies it to the current version, and it goes into the *-security repository.
*-security does not include updates. CVE patches only.
The upstream version number does not change, the Debian or Ubuntu version number does change: Foo 1.2.3-1ubuntu2 becomes Foo 1.2.3-1ubuntu3

You can easily enable automatic updates for -security repos in /etc/apt/apt.conf.d/50unattended-upgrades or in Ubuntu's Software & Updates control panel.

Also: If you enable the *-updates repository, then you will get those minor improvements you don't mind. But the system has no way to determine if an update is too much for your comfort...it's not psychic...so perhaps you should disable that repository. 


Finally: Some users get confused when a famous vulnerability gets discovered, and the upstream project seems to recommend upgrading to the latest version to fix it. Follow the CVE number at security.ubuntu.com instead of following the hype.

---

