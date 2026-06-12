---
title: "Update-manager"
date: 2012-06-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by scradock on 2012-06-03
The latest updates brought in an updated update-manager-core (0.161) that requires update-manager itself to be removed, as it's not updated. After falling for this one on one quantal install, I tried to check the Changelogs, and ran into some indications that update-manager was to be re-named Software Updater, but no information about any intention to remove it.

Anyone got any more information? Luckily I always add Synaptic as soon as I do a new install, so missing update-manager is not fatal, but it does do a much better job of handling dependencies when there is a list of 100+ updates!

---

### Post by mc4man on 2012-06-03
I think it will be a work in progress for a bit, maybe will start showing after A1 releases?

A quick look at what I see today..-not  that much changed

---

### Post by philinux on 2012-06-03
> **scradock said:**
> The latest updates brought in an updated update-manager-core (0.161) that requires update-manager itself to be removed, as it's not updated. After falling for this one on one quantal install, I tried to check the Changelogs, and ran into some indications that update-manager was to be re-named Software Updater, but no information about any intention to remove it.

Anyone got any more information? Luckily I always add Synaptic as soon as I do a new install, so missing update-manager is not fatal, but it does do a much better job of handling dependencies when there is a list of 100+ updates!

Work in progress I guess. I never use it during dev cycles until later on.
 [http://ubuntuforums.org/showpost.php?p=11941533&postcount=11](http://ubuntuforums.org/showpost.php?p=11941533&postcount=11)

---

### Post by jerrylamos on 2012-06-03
Simple fix.

I can't count how many times "update" has screwed an install for me over the years, plus it comes crashing in on top of whatever I'm doing when it wants to, not when I want to - example, during a video or composing an email or reporting a bug...

Install synaptic, settings update to "never", same for "upgrade notification".

Then do sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-upgrade

During development I update daily when I want to, not when update chooses to.

Or, I've had more problems with:
sudo apt-get update
sudo apt-get upgrade 

BTW, this gets rid of the "partial update" disaster...

Jerry

p.s.  O.K., for general population use after release, when updates are more rare, then maybe let "update" check every so often....

---

### Post by philinux on 2012-06-03
In a stable release UM is very reliable. Never had an issue. I have it set to check for updates daily. It just does its job.

---

### Post by scradock on 2012-06-03
> **philinux said:**
> In a stable release UM is very reliable. Never had an issue. I have it set to check for updates daily. It just does its job.

My experience exactly. Most times it's just fine in a development situation too, so long as I make sure NEVER to accept a "Partial Upgrade". 
Never could figure out that aptitude thingy - always wanting to tell me stuff I don't want to know, instead of getting on with the job like Update Manager.

---

### Post by mc4man on 2012-06-03
I see there is now a build going on for the newer version of update-manager (all_deb), so  it will likely be available in a few hr.'s
Package is still named update-manager though will show "Software Updater" in window as attached before, (seems to have a few little issues here
There will also should be the text updater package available

Edit: may take a slight adjustment till seen, noticed this the other day when building - the actual packages build in a few minutes, then the build goes on a seemingly endless deal with some 'Distupgrade' stuff. I canceled it out because the packages where already created, not so in LP. ( build went on for quite a long time, over a day...

---

