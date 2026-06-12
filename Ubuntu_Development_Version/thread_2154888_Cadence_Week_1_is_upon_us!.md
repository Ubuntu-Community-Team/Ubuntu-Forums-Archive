---
title: "Cadence Week 1 is upon us!"
date: 2013-06-16
forum: Ubuntu Development Version
---

### Post by Mathor on 2013-06-16
> 
   On Fri, Jun 14, 2013 at 6:49 PM, 
Nicholas Skaggs <[EMAIL="nicholas.skaggs@canonical.com"]nicholas.skaggs@canonical.com[/EMAIL]> wrote: 

Alright, I know several of you are particularly excited about this. Our first cadence week is here. Starting June 15th, we'll be testing images and packages over the course of the next week. So what is cadence testing? Have a look at this page to get more information:  [https://wiki.ubuntu.com/Testing/Cadence](https://wiki.ubuntu.com/Testing/Cadence)   In short, as a community we're testing different things about every ~2 weeks in ubuntu, and sharing results to flesh out bugs and problem areas.The full schedule is here, but note the release schedule changed TODAY, so this will be updated as well to reflect those changes very soon.  [https://wiki.ubuntu.com/QATeam/Cadence/Saucy](https://wiki.ubuntu.com/QATeam/Cadence/Saucy)  So what's up for testing this week? The daily images, the default applications in ubuntu (we'll start tracking them all throughout the cycle) and a new version of alsa testing. Full details are here:  [https://wiki.ubuntu.com/QATeam/Cadence/Saucy/Week1](https://wiki.ubuntu.com/QATeam/Cadence/Saucy/Week1)  If you need help submitting results, have a look at this page, [https://wiki.ubuntu.com/Testing/QATracker](https://wiki.ubuntu.com/Testing/QATracker), and the walkthroughs listed. Of particular interest is the ISO testing and Cadence Week testing walkthroughs.  [https://wiki.ubuntu.com/Testing/Cadence/Walkthrough](https://wiki.ubuntu.com/Testing/Cadence/Walkthrough) [https://wiki.ubuntu.com/Testing/ISO/Walkthrough](https://wiki.ubuntu.com/Testing/ISO/Walkthrough)  Do note that you don't need anything special to participate in cadence week testing! Both an installed version of the development branch of ubuntu (aka saucy) in a VM or on a real box, or even a live session of the lastest daily image will work.  Good luck! Bear in mind this is the first week for our new format, so there may be growing pains. Feedback is very much appreciated. Thanks and Happy Testing everyone,  Nicholas Skaggs

On top of the usual daily isos, there are a lot of individual package testcases that need testing. Enjoy testers! :p

---

### Post by anca-emanuel on 2013-06-16
I test saucy every day from months.
```
The following packages have unmet dependencies: python-twisted-names : Depends: python-twisted-core (>= 13.0) but 12.3.0-1ubuntu6 is to be installed
E: Unable to correct problems, you have held broken packages.
```
Somebody need to be ... actualized or out.

---

### Post by smartboyhw on 2013-06-16
> **anca-emanuel said:**
> I test saucy every day from months.
```
The following packages have unmet dependencies: python-twisted-names : Depends: python-twisted-core (>= 13.0) but 12.3.0-1ubuntu6 is to be installed
E: Unable to correct problems, you have held broken packages.
```
Somebody need to be ... actualized or out.

According to the source page of the "twisted" package ([https://launchpad.net/ubuntu/+source/twisted](https://launchpad.net/ubuntu/+source/twisted)), the version in the Ubuntu Saucy repositories is still 12.3.0-1ubuntu6. 13.0 hasn't been packaged yet, so please check whether you have some PPAs with the updated package.

---

### Post by anca-emanuel on 2013-06-16
Hi smartboyhw,
 here is the ppa(s) I have:
[IMG]http://i.imgur.com/O2qNwE6.png[/IMG]

---

### Post by anca-emanuel on 2013-06-21
> **anca-emanuel said:**
> I test saucy every day from months.
```
The following packages have unmet dependencies: python-twisted-names : Depends: python-twisted-core (>= 13.0) but 12.3.0-1ubuntu6 is to be installed
E: Unable to correct problems, you have held broken packages.
```

SOLVED by the latest updates. Thanks.

---

