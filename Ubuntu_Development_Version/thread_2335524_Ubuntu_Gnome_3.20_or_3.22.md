---
title: "Ubuntu Gnome 3.20 or 3.22 ?"
date: 2016-08-29
forum: Ubuntu Development Version
---

### Post by fthx on 2016-08-29
Hello,

There are some 3.22 apps now, but will Gnome shell be entirely running 3.22 for october ?

---

### Post by mc4man on 2016-08-29
What you see now in Ubuntu repos is what you'll get in Ubuntu repos in Oct. (as far as 'major' versions

---

### Post by fthx on 2016-08-29
There was, during a short time in proposed repos today, some Gnome softwares updates from 3.20 to 3.22 beta (gnome-power-manager, gnome-color-manager).

It's somewhat odd that evolution* is 3.22 and it is an essential component for Gnome ? Is the goal to update all Gnome packages that do not need gtk 3.22 ?

---

### Post by mc4man on 2016-08-29
Those 2 you mention just say 'new upstream release'  so maybe they got ffe's or maybe they were done without. 
gtk is at 3.20, can't see that changing. Same for gnome-shell, will it be upgraded before beta freeze, no clue, past history at this date in dev would say no.

---

### Post by jbicha on 2016-08-31
I'm going to try to briefly answer some of the questions.

The Beta 1 [release notes]("https://wiki.ubuntu.com/YakketyYak/Beta1/UbuntuGNOME") mentioned that yakkety now has virtually all of GNOME 3.20 (or higher). The few things that aren't at least 3.20 are fairly unimportant and having older versions is irrelevant to almost everybody. Ubuntu does have nautilus 3.20 now for instance.

"Select apps have been updated to 3.22". Generally, you would have a hard time noticing the differences between the 3.20 and the 3.21 (to be upgraded to 3.22) versions. In some cases, the UI is a bit tweaked (The Disk Usage Analyzer app in particular is [nicer]("https://bugzilla.gnome.org/762874")) or a new feature added (like the Characters app adding the ability to [drag]("https://bugzilla.gnome.org/764757") a character to another app), but these are not massive changes. Why bother then? Easier access to bug fixes and updated upstream translations.

Ubuntu 16.10 will not include GTK 3.22. Upgrading to GTK 3.20 was painful as light-themes (Ambiance and Radiance and the derivatives shipped in Ubuntu MATE, Lubuntu and Ubuntu Kylin) had to be painstakingly ported. (The same could be said for Greybird, Xubuntu's default theme but it's not based on Ambiance.) This happened fairly late before Feature Freeze and there are still UI regressions from it now. (Please report the issues you see!). I think theming barely changed in GTK 3.22 but it did change.

GNOME Shell 3.22 is a relatively quiet update but its underlying library mutter changed a fair amount. mutter is also used by the budgie interface which we don't want to break this late in the release cycle. (Budgie might be fine but it takes time and work to verify). Ubuntu 16.10 will not include GNOME Shell 3.22.

Updating a significant number of things to the brand new GNOME version is a new and different thing than Ubuntu has done recently. I think it's worked ok this time (the GNOME 3.22 release cycle was quieter than some previous cycles). There's no commitment to doing this in future release cycles. It's stressful because the schedule is tight and you have to hope that GNOME doesn't make surprise changes. It's important that updates not introduce regressions to the Unity experience or elsewhere. GNOME's ["Freeze"]("https://wiki.gnome.org/ThreePointTwentyone") is only a day or a few days (depending on when the GNOME maintainer gets around to releasing the new version of whatever app the maintainer is responsible for) before Ubuntu's [Feature Freeze]("https://wiki.ubuntu.com/YakketyYak/ReleaseSchedule").

By the way, the next Debian stable release will include GNOME 3.22 next year.

---

### Post by jbicha on 2016-08-31
Evolution is the notable exception to the minimal changes rule. The new [Evolution]("https://launchpad.net/bugs/1613291") uses the new webkit2gtk which allows Ubuntu GNOME to not include the old webkitgtk on the .iso. (This is one reason Ubuntu GNOME no longer includes empathy by default -- it still uses webkitgtk.)

---

### Post by fthx on 2016-08-31
Thanks for the details !
Ubuntu Gnome is BTW already very reliable (through my experience).
There is still something odd with Nvidia 367 and GDM but it seems to be solved with 370 beta.

---

### Post by sgage on 2016-08-31
> **fthx said:**
> Thanks for the details !
Ubuntu Gnome is BTW already very reliable (through my experience).
There is still something odd with Nvidia 367 and GDM but it seems to be solved with 370 beta.

I am also finding Ubuntu Gnome to be quite solid. I'm glad Nautilus was finally let loose to find the latest version. Everything seems to be working just fine, even Evolution, which is at 3.21.91. All of my favorite Gnome Shell extensions are working just fine - GS has become a very nicely mature platform, and I work with it very comfortably.

---

