---
title: "Epiphany 1.6.1 Javascript security"
date: 2005-04-23
forum: Server Platforms
---

### Post by RHTopics on 2005-04-23
With the javascript security problem for Firefox 1.0.2 in Ubuntu 5.04, I started using the Epiphany 1.6.1 web browser in Hoary.  Yet, since it uses the same underlying Mozilla code (rv: 1.7.6), it appears to have the same javascript security problem as Firefox.

After looking around at the home website for Epiphany ([http://www.gnome.org/projects/epiphany)](http://www.gnome.org/projects/epiphany)), I did not see anything about a new release to fix this problem.

Are there any plans for a new release of Epiphany for Ubuntu 5.04?

User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050405 Epiphany/1.6.1 (Ubuntu) (Ubuntu package 1.0.2)

---

### Post by TravisNewman on 2005-04-24
Well, if there are no releases of Epiphany coming out to fix this, then there can't be a fix for Ubuntu since none exist.

However, even if there WERE one being released by the Epiphany devs, there's a fine line between a security fix and a new version. After a release of Ubuntu, there are no upgrades to software, only security fixes. They KNOW that these software versions work, so they aren't inclined to change that and break things. So I wouldn't expect one any time soon. However, jdong is working on a backport of Firefox 1.0.3 which fixes this, so that's an option to get you moving.

---

### Post by RHTopics on 2005-04-25
What is Ubuntu's policy towards making users aware of current, unfixed security problems?

Are USNs (Ubuntu Security  Notifications) posted for unresolved security problems?

Using the current JavaScript security problems in both Firefox 1.0.2 and Epiphany 1.6.1 as an example, is there an advisory page on Ubuntu's Web site to describe the proper actions one should take (i.e. turn off JavaScript in Firefox) before an official patch/update becomes available?

---

