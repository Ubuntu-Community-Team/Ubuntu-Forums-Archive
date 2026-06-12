---
title: "So called &quot;cadence testing&quot; is a failure"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-03-23
Look at the standing bugs for just Lubuntu:

[ATTACH=CONFIG]240471[/ATTACH]

And the final Beta dates don't even match between "cadence" and the release schedule:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring](https://wiki.ubuntu.com/QATeam/Cadence/Raring)

[https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

We've been dealing with the same live installer breakage since mid November:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

And now we have a 'network-manager' bug that effects both Ubuntu and Lubuntu for several days!

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1159201](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1159201)

And the source bug is locked as private :mad:

I'm sure the Captain still thinks he's steering the ship but the rudder is totally detached ](*,)

---

### Post by Noskcaj10 on 2013-03-23
While i don't like the idea of candence testing either, you've went too far.
first, the bug list you had shows all bugs found in raring reported on the iso-tracker. for all *buntu's
second, the freeze bug has been found and confirmed (making it no longer a problem caused by bad testing), but is very difficult to fix, if it's "our fault", please, show us how we could have fixed it.
third, the network manager bug is private because it shows private info of some form.
third, i'm shocked that you overlooked the areas even worse, like testdrive, the PPC recursive bug, and the lack of testing for netboot and ppc.

---

### Post by Stinger on 2013-03-24
> **kansasnoob said:**
> I'm sure the Captain still thinks he's steering the ship but the rudder is totally detached ](*,)

+1
I couldn't have said it better myself. 
I hope we don't have a shipwreck ;)

---

### Post by ronacc on 2013-03-24
When I think of the bugs that have persisted or constantly recurred  over the many cycles that I have been doing Ubuntu testing it saddens me that we seem to be beating our heads against a stone wall .

---

### Post by EgoGratis on 2013-03-24
Not in general but i sometimes do see trouble spots where things change drastically between release. For example bluetooth support

[http://ubuntuforums.org/showthread.php?t=2121960](http://ubuntuforums.org/showthread.php?t=2121960)

I did think fixing bugs and making it work in Ubuntu 12.04 should stick for some time but i was wrong. But this are small things in general i am pleased and most things always work as i expect them to.

---

### Post by balloons on 2013-03-25
> **kansasnoob said:**
> Look at the standing bugs for just Lubuntu:

[ATTACH=CONFIG]240471[/ATTACH]

And the final Beta dates don't even match between "cadence" and the release schedule:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring](https://wiki.ubuntu.com/QATeam/Cadence/Raring)

[https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule](https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule)

We've been dealing with the same live installer breakage since mid November:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

And now we have a 'network-manager' bug that effects both Ubuntu and Lubuntu for several days!

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1159201](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1159201)

And the source bug is locked as private :mad:

I'm sure the Captain still thinks he's steering the ship but the rudder is totally detached ](*,)

It's a busy busy week as you know, but I'll address a couple of these points. We should discuss this more later when we all have a bit more time (post-cycle?). 

On the dates being incorrect on the calendar, there was an original note of april 4th for the actual release date for the beta, but it wasn't showing up. I think it was a separate line item even. Anyways, I made sure the note shows up now. That said, the cadence calendar is showing the saturday start dates, not actual event dates, whereas the release schedule is showing the exact important dates. The Final Beta release happens the week of March 30th from our cadence perspective, hence it's listed on that weeks' line -- I hope this makes sense. (EDIT: I should note here that the calendar needs to be easy to understand, so please do give more feedback on tweaks that should happen to make it so. We had an integrated calendar (it was part of the release schedule calendar) for testing last cycle, and it was very confusing to follow because so many events and timelines where trying to be convened on one page; I hope this is an improvement, but let's keep iterating!)

In general we as testers actually like bugs.. Bug counts are funny. A low bug count during the cycle doesn't mean a stable release (it could mean we're not testing!), and a high bug count doesn't necessarily mean the release is horrible (maybe we're testing really well). Now, the caveat with bugs is while we like them, we don't like them in the stable release -- in development though, if we find a large amount of bugs, I would consider our job as successful.

I feel you on the private and long-standing bugs, but we as a testing community have done our part on those by finding and documenting the bug. For the private bug, given the severity and longevity it would likely be worth asking someone to manually prune sensitive info from the report and open it, or ask the original reporter to merely publicize his info willingly if he is able to do so.

All that said, what can we do about high bug counts and longstanding bugs or regressions? If we've reported them and documented them well, we've done our part in helping get the bug fixed. From the development side, we need those folks to also address and work the bugs found. I did a post last year about bug shepherding, and it's important. I know many of you practice this; 

you report the bug in detail, making sure it can be reproduced by others
you follow-up on the bug to make sure it's properly filed and can be seen by those who can fix it
you help test the fix if necessary

Beyond that, the actual bug fix is in the hands of the developers. We can and should do everything we can to help make sure the bug is fixed, but the fixes themselves rely on a developer.

---

### Post by phillw on 2013-03-25
Regarding [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1159201]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1159201") This has now been un-privatised (or should that be nationalised?). If you come across bugs marked private, or your own bug suddenly goes private, please do ask on #ubuntu-bugs. If you're not a fan of IRC, then please email the quality mailing list [email]ubuntu-quality@lists.ubuntu.com[/email] Yes, bugs that carry over are infuriating, I've been on the receiving end of one that prevented my 3G device working for two cycles before it got finally fixed.

Don't give up hope! A lot of what has happened in cadence, has in itself been a test. 

Regards,

Phill.

---

### Post by kansasnoob on 2013-03-29
> **Noskcaj10 said:**
> While i don't like the idea of candence testing either, you've went too far.
**[COLOR="#FF0000"]first, the bug list you had shows all bugs found in raring reported on the iso-tracker. for all *buntu's[/COLOR]**
second, the freeze bug has been found and confirmed (making it no longer a problem caused by bad testing), but is very difficult to fix, if it's "our fault", please, show us how we could have fixed it.
third, the network manager bug is private because it shows private info of some form.
third, i'm shocked that you overlooked the areas even worse, like testdrive, the PPC recursive bug, and the lack of testing for netboot and ppc.

You're right, it's per testcase rather than per flavor.

---

### Post by kansasnoob on 2013-03-29
> **Noskcaj10 said:**
> While i don't like the idea of candence testing either, you've went too far.
first, the bug list you had shows all bugs found in raring reported on the iso-tracker. for all *buntu's
**[COLOR="#FF0000"]second, the freeze bug has been found and confirmed (making it no longer a problem caused by bad testing), but is very difficult to fix, if it's "our fault", please, show us how we could have fixed it.[/COLOR]**
third, the network manager bug is private because it shows private info of some form.
third, i'm shocked that you overlooked the areas even worse, like testdrive, the PPC recursive bug, and the lack of testing for netboot and ppc.

I made a suggestion to narrow down the cause a long time ago:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701/comments/48](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701/comments/48)

> 

Super dumb question :^)

Is there a way to temporarily revert these partman changes on the live image:

ubiquity (2.13.2) raring; urgency=low

* Try to copy signed kernel from vmlinuz.efi in preference to
vmlinuz.efi.signed; vmlinuz.efi is friendlier to archaic 8.3 file name
restrictions which apply to isolinux.
* Automatic update of included source packages: partman-auto 105ubuntu1,
partman-auto-lvm 46ubuntu1, partman-crypto 55ubuntu1, partman-lvm
82ubuntu1.

-- Colin Watson <cjwatson@ubuntu.com> Mon, 12 Nov 2012 15:11:08 +0000

I'm asking because I archive some testing discs and as best I can tell that's about when things broke. I'm thinking a temporary reversion would be acceptable just for testing purposes since we're not doing alphas in Raring.

Sorry to be a pain in the neck.


Of course it's now far too late to think about that because we've been building on top of an unstable foundation for 4 months :(

---

### Post by kansasnoob on 2013-03-29
> **Noskcaj10 said:**
> While i don't like the idea of candence testing either, you've went too far.
first, the bug list you had shows all bugs found in raring reported on the iso-tracker. for all *buntu's
second, the freeze bug has been found and confirmed (making it no longer a problem caused by bad testing), but is very difficult to fix, if it's "our fault", please, show us how we could have fixed it.
**[COLOR="#FF0000"]third, the network manager bug is private because it shows private info of some form.[/COLOR]**
third, i'm shocked that you overlooked the areas even worse, like testdrive, the PPC recursive bug, and the lack of testing for netboot and ppc.

Eerm, maybe. I've reported bugs with loads of personal info and I was asked whether or not to allow that info to be posted while actually using "apport". But if a bug is reported using "http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect" the bug is frequently marked private with no outstanding warning.

In fact I need to check one against the netboot mini.iso right now :)

Edit: One more thing, maybe the bug-bot could be reprogrammed to never mark a bug report as a duplicate of a private report. Maybe it could just add a note to the private report about potential dupes.

---

### Post by kansasnoob on 2013-03-29
> **Noskcaj10 said:**
> While i don't like the idea of candence testing either, you've went too far.
first, the bug list you had shows all bugs found in raring reported on the iso-tracker. for all *buntu's
second, the freeze bug has been found and confirmed (making it no longer a problem caused by bad testing), but is very difficult to fix, if it's "our fault", please, show us how we could have fixed it.
third, the network manager bug is private because it shows private info of some form.
**[COLOR="#FF0000"]third, i'm shocked that you overlooked the areas even worse, like testdrive, the PPC recursive bug, and the lack of testing for netboot and ppc.[/COLOR]**

I recently used testdrive w/virtualbox and noticed no problems different than those I'd encountered on bare metal. I have no hardware to test PPC. I did just run a test on the latest netboot mini.iso that failed:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1161898](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1161898)

I'm doing my job as a tester. I report bugs and I follow up on my bugs. And I don't create a new forum user ID to flame someone that tries to point out an obvious problem with the current testing scenario.

---

### Post by ventrical on 2013-03-29
> **kansasnoob said:**
> I recently used testdrive w/virtualbox and noticed no problems different than those I'd encountered on bare metal. I have no hardware to test PPC. I did just run a test on the latest netboot mini.iso that failed:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1161898](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1161898)

I'm doing my job as a tester. I report bugs and I follow up on my bugs. And I don't create a new forum user ID to flame someone that tries to point out an obvious problem with the current testing scenario.


Most of us know you are one of the best beta-testers @ ubuntu-forums. When we point things out about  programs that are  buggy or a process that just does not work, we are going to raise hair up on devlopers backs.  Thats part of being a good beta-tester.

regards,
ventrical

---

### Post by kansasnoob on 2013-03-29
> **guitara said:**
> It's a busy busy week as you know, but I'll address a couple of these points. We should discuss this more later when we all have a bit more time (post-cycle?). 

On the dates being incorrect on the calendar, there was an original note of april 4th for the actual release date for the beta, but it wasn't showing up. I think it was a separate line item even. Anyways, I made sure the note shows up now. That said, the cadence calendar is showing the saturday start dates, not actual event dates, whereas the release schedule is showing the exact important dates. The Final Beta release happens the week of March 30th from our cadence perspective, hence it's listed on that weeks' line -- I hope this makes sense. (EDIT: I should note here that the calendar needs to be easy to understand, so please do give more feedback on tweaks that should happen to make it so. We had an integrated calendar (it was part of the release schedule calendar) for testing last cycle, and it was very confusing to follow because so many events and timelines where trying to be convened on one page; I hope this is an improvement, but let's keep iterating!)

In general we as testers actually like bugs.. Bug counts are funny. A low bug count during the cycle doesn't mean a stable release (it could mean we're not testing!), and a high bug count doesn't necessarily mean the release is horrible (maybe we're testing really well). Now, the caveat with bugs is while we like them, we don't like them in the stable release -- in development though, if we find a large amount of bugs, I would consider our job as successful.

I feel you on the private and long-standing bugs, but we as a testing community have done our part on those by finding and documenting the bug. For the private bug, given the severity and longevity it would likely be worth asking someone to manually prune sensitive info from the report and open it, or ask the original reporter to merely publicize his info willingly if he is able to do so.

All that said, what can we do about high bug counts and longstanding bugs or regressions? If we've reported them and documented them well, we've done our part in helping get the bug fixed. From the development side, we need those folks to also address and work the bugs found. I did a post last year about bug shepherding, and it's important. I know many of you practice this; 

you report the bug in detail, making sure it can be reproduced by others
you follow-up on the bug to make sure it's properly filed and can be seen by those who can fix it
you help test the fix if necessary

Beyond that, the actual bug fix is in the hands of the developers. We can and should do everything we can to help make sure the bug is fixed, but the fixes themselves rely on a developer.

You're completely missing the point. There's no better proof of that than this:

[http://ubuntuforums.org/showthread.php?t=2129906](http://ubuntuforums.org/showthread.php?t=2129906)

It's too late to recruit new testers in the middle of final Beta testing, and it's a waste of time to try and teach old testers new tricks!

The problem is that our so-called cadence testing in no way syncs with the various freezes during the dev cycle.

---

### Post by kansasnoob on 2013-03-29
I wish I could change that Lubuntu flag to "all variants".

At the time I posted this I was testing Lubuntu images per the "cadence testing" schedule (week 9).

What's really important ATM is that we hammer down on serious bugs in this final Beta!

---

