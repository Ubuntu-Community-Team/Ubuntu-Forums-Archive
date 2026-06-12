---
title: "Open Source &amp; Linux: Controversial Questions"
date: 2007-10-07
forum: The Cafe
---

### Post by Zoiked on 2007-10-07
I was curious about this....

How do developers make there money? Do people actually donate? **Sarcasm**

If there was a feature that the community really wanted in "say" Totem; do we have to wait for gnome to make that feature?
If the Ubuntu developers edit the source to include that feature, what if gnome releases new version of Totem? Do the Ubuntu developers have to edit the source again to add that feature for each new release of Totem?

If there is a new version of "say" Pidgin; do we have to wait for the next release of Ubuntu for the upgrade to show up in the repositories?

Does Linux have standardization? If a develop adds a feature to create a new menu item when you right click on the desktop for gnome; is this item going to show up on the KDE's menu? If it doesn't, doesn't this put more strain on the developers cause they have to code a feature for every desktop environment?

Why can't there be one package type? Is there really a point in having both Rpms and Debs? Can't we create a universal pack type for every linux distribution?

Why do Linux users say that Linux is so stable that it doesn't freeze that much when my Firefox has froze 13 times when viewing youtube.com?

---

### Post by -grubby on 2007-10-07
actually, lots of people donate
GNOME and KDE are seperate projects
I have no Idea why there is more than 1 package manager when apt-get is just fine
you can't blame Linux for Firefox's screwups(well fine!Adobe)

---

### Post by Zoiked on 2007-10-07
> **nathangrubb said:**
> 
you can't blame Linux for Firefox's screwups

Certainly doesn't happen on Windows. ;)

---

### Post by FuturePilot on 2007-10-07
Yes people do donate. Lots of them
> If there is a new version of "say" Pidgin; do we have to wait for the next release of Ubuntu for the upgrade to show up in the repositories?
Officially yes, but that doesn't stop you from compiling it yourself. Or sometimes getdeb.net has a newer version already in a .deb
> Why can't there be one package type? Is there really a point in having both Rpms and Debs? Can't we create a universal pack type for every linux distribution?
This has been discussed numerous times. Linux is about choice.
> Why do Linux users say that Linux is so stable that it doesn't freeze that much when my Firefox has froze 13 times when viewing youtube.com?

This is not an issue with the OS or Firefox, but with Adobe's Flash plugin. And there's nothing we can do about it. Why? Because Flash is closed source.
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688")

---

### Post by Frak on 2007-10-07
People donate
Choice
Don't blame Linux or Firefox for Adobe's screwups.

---

### Post by elvis on 2007-10-07
> **Zoiked said:**
> I was curious about this....

How do developers make there money? Do people actually donate? 

Plenty of people get paid full time to work on Linux.  You are allowed to buy and sell Linux distributions at any price you like.  Nowhere is it written that Linux must be distributed in binary form free of cost.  The only caveat is that the source code is made available, and even companies that sell Linux and make a good profit (SuSE/Novell, RedHat, etc) still do that, and make a very good living.

Likewise, commercial companies pay their own in-house staff to write code for various GPL programs.  Just read through the change-logs of many open source programs, and you'll see employees from Intel, Motorola, IBM and a host of others who use Linux both inhouse and for their customers, and submit patches upstream to help each other out.

---

### Post by Celegorm on 2007-10-07
> **Zoiked said:**
> If there was a feature that the community really wanted in "say" Totem; do we have to wait for gnome to make that feature?
If the Ubuntu developers edit the source to include that feature, what if gnome releases new version of Totem? Do the Ubuntu developers have to edit the source again to add that feature for each new release of Totem?

You can always submit your code to the upstream developers and see if they want to include it, or create a new project based on their software and put in that extra feature.

---

### Post by toupeiro on 2007-10-07
> How do developers make there money? Do people actually donate?

Yes, lots of people do.  I've donated a significant amount of money towards various open source projects and food for people interested in learning more about linux this year  The latest being the Open Source movie, The Peach.  I can't do that consistantly (I wish I could afford to, lol)  but it just so happened that this year I did.

> f there was a feature that the community really wanted in "say" Totem; do we have to wait for gnome to make that feature?
If the Ubuntu developers edit the source to include that feature, what if gnome releases new version of Totem? Do the Ubuntu developers have to edit the source again to add that feature for each new release of Totem?


Yes and Yes, but you are also able to take totem and add whatever you want to it, should you not have the desire to "wait" for someone else to do it for you.  This is the beauty of Open Source.  Microsoft would just sue you.

> there is a new version of "say" Pidgin; do we have to wait for the next release of Ubuntu for the upgrade to show up in the repositories?

If you wanted a package.  You could always scour sourceforge or freshmeat.net and not wait.



> Does Linux have standardization? If a develop adds a feature to create a new menu item when you right click on the desktop for gnome; is this item going to show up on the KDE's menu? If it doesn't, doesn't this put more strain on the developers cause they have to code a feature for every desktop environment?

I've responded to variants of this question on these forums more times than I care to remember.  The short answer to your question is yes, Linux is very standardized, most applications are cross desktop compatible.  if you use apt-get, it will get any gnome or KDE dependencies you don't already have.

> Why can't there be one package type? Is there really a point in having both Rpms and Debs? Can't we create a universal pack type for every linux distribution?

This is actually something I wouldn't mind seeing myself...  There are tools to convert from one to the other that exist.  However, If you are asking this question using Windows as your basis, that is like throwing stones in a glass house..  I was a windows software packager for many years, and I know that microsoft themselves do NOT have a universal package type.  MSI is what they are using now, but there is also nullsoft, Wise packages, Installshield packages, EXE compacted packages, script based installs and an array of others.  My rebuttal to this is, show me an os with a universal package type (other than solaris) that works and people are happy with, and I will happily stand corrected.

> Why do Linux users say that Linux is so stable that it doesn't freeze that much when my Firefox has froze 13 times when viewing youtube.com?

> **Zoiked said:**
> Certainly doesn't happen on Windows. ;)

I humbly beg to differ, it just happened on my windows work laptop (rebuilt 3 days ago)

---

