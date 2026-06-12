---
title: "Should I upgrade to daily-live?"
date: 2013-02-23
forum: Ubuntu Development Version
---

### Post by sudo san on 2013-02-23
Hi, I was wondering what was the easiest way to upgrade to the 13.04 daily-live. I though it would be through editing my '/etc/apt/sources.list' and doing 'sudo apt-get update && sudo apt-get dist-upgrade'. Also I would like to know that if I did upgrade to daily-live, would I be able to do update the next day for the next daily-live?

---

### Post by grahammechanical on 2013-02-23
ISO images for Raring Ringtail are built every day. So, when people here talk about the latest daily image they are referring to the latest ISO image that was made available that day.

Once we install Raring Ringtail it ceases to be a daily-live image even if we update it daily. At this stage of the development a person might as well do a clean install from the latest daily image.

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds]("http://iso.qa.ubuntu.com/qatracker/milestones/243/builds")

I have a Raring install that I converted from a clean 12.10 install by running these two commands

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

I ran those commands at the start of the Raring development cycle and I will run a variation of the first command at the start of the 13.10 development cycle because there are not daily images available in the early days of a development cycle. If you try that now with 12.10 be prepared for a lot of updates to be brought in because there is now a big difference between 12.10 and 13.04. Better to use the latest 13.04 ISO image. Less download.

Other than that you will be welcome to join in testing 13.10 when development starts in about two months.

Regards.

---

### Post by sudo san on 2013-02-23
Ok, so if I do a fresh install of raring, I won't have to worry about updates. So by what you said, if I update every day, I won't have to keep re-downloading the daily live image? And once it has been formally released, I will be fully up-to-date and not need to do a fresh install?
I think what you replied with answered my question but could you just clarify that please?

Thanks for the quick reply.
sudo san

---

### Post by deadflowr on 2013-02-23
> **sudo san said:**
> Ok, so if I do a fresh install of raring, I won't have to worry about updates. So by what you said, if I update every day, I won't have to keep re-downloading the daily live image? And once it has been formally released, I will be fully up-to-date and not need to do a fresh install?
I think what you replied with answered my question but could you just clarify that please?

Thanks for the quick reply.
sudo san

Precisely, once you upgrade to raring, be it from a daily build or changing the sources.list, just run the update here and there( usually daily) and you'll roll with the development.

I would also cite that you read through the stickies at the top of this sub-forum for helpful hints for if any problems occur during your testing period. And keep up with the threads in this sub-forum for info on problems others might have come across.

---

### Post by sudo san on 2013-02-23
> **deadflowr said:**
> Precisely, once you upgrade to raring, be it from a daily build or changing the soruces.list, just run the update here and there( usually daily) and you'll roll with the development.

I would also cite that you read through the stickies at the top of this sub-forum for helpful hints for if any problems occur during your testing period. And keep up with the threads in this sub-forum for info on problems others might have come across.

Thanks, now I can upgrade as some of my quantal packages are soiled anyway.

---

### Post by deadflowr on 2013-02-23
I'd also say, outside installing from a fresh daily image, grahammechanical's way of upgrading from a clean fresh install is very simple, and my experience pretty error free. As the packages in the basic install are usually the ones with the most attention and therefore cause the least problems.
Remember, upgrading the sources.list will upgrade everything on the system. Sometimes extra packages you've installed haven't been upgraded yet and they're usually are the ones that cause the most frustration.

---

### Post by jinjorge on 2013-02-23
> **deadflowr said:**
> I'd also say, outside installing from a fresh daily image, grahammechanical's way of upgrading from a clean fresh install is very simple, and my experience pretty error free. As the packages in the basic install are usually the ones with the most attention and therefore cause the least problems.
Remember, upgrading the sources.list will upgrade everything on the system. Sometimes extra packages you've installed haven't been upgraded yet and they're usually are the ones that cause the most frustration.

Totally agree. this is what I did when upgrading from Quantal to Raring.

---

### Post by sudo san on 2013-02-23
> **deadflowr said:**
> I'd also say, outside installing from a fresh daily image, grahammechanical's way of upgrading from a clean fresh install is very simple, and my experience pretty error free. As the packages in the basic install are usually the ones with the most attention and therefore cause the least problems.
Remember, upgrading the sources.list will upgrade everything on the system. Sometimes extra packages you've installed haven't been upgraded yet and they're usually are the ones that cause the most frustration.

I was recently thinking about using the minimal install iso for quantal to make my own personalised system instead of having unity dump its large self on my hard drive and install gnome-shell. But now I know that even if there is no minimal cd for raring yet I can still build it. Even though you mention that some packages will get in the way, with a minimal install, they won't anymore!

Thanks a lot people!:)

---

### Post by cariboo on 2013-02-23
> **sudo san said:**
> I was recently thinking about using the minimal install iso for quantal to make my own personalised system instead of having unity dump its large self on my hard drive and install gnome-shell. But now I know that even if there is no minimal cd for raring yet I can still build it. Even though you mention that some packages will get in the way, with a minimal install, they won't anymore!

Thanks a lot people!:)

No need to do a minimal install, there is a Gnome Remix iso available [here]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10"), it hasn't been updated to Raring yet, but you can use the commands that grahammechanical posted to upgrade to Raring. You can then enjoy Gnome-shell goodness in Raring. :-D

---

### Post by jerrylamos on 2013-02-24
> **deadflowr said:**
> I'd also say, outside installing from a fresh daily image, grahammechanical's way of upgrading from a clean fresh install is very simple, and my experience pretty error free. As the packages in the basic install are usually the ones with the most attention and therefore cause the least problems.
Remember, upgrading the sources.list will upgrade everything on the system. Sometimes extra packages you've installed haven't been upgraded yet and they're usually are the ones that cause the most frustration.
On 3 test pc's, netbook notebook tower, I'm doing a daily live install every week or so on one or the other.  Cleans out the cobwebs of the tangled upgrades.  Despite best efforts of removing and purging the space taken on the partition grows and grows, especially the amd64 ubuntu's.

Now I've had more than my fair share of ubiquity/install bugs certainly at a higher rate than just sitting tight and updating....

Oh, first thing I do on an install is set software-properties-gtk to add partners and turn automatic updates off.

On a daily live there are invariably updates already that same day so I install those.  On occasion the updates to that day's daily live fix a problem on the daily live that day....

---

### Post by sudo san on 2013-02-24
> **jerrylamos said:**
> On 3 test pc's, netbook notebook tower, I'm doing a daily live install every week or so on one or the other.  Cleans out the cobwebs of the tangled upgrades.  Despite best efforts of removing and purging the space taken on the partition grows and grows, especially the amd64 ubuntu's.

Now I've had more than my fair share of ubiquity/install bugs certainly at a higher rate than just sitting tight and updating....

Oh, first thing I do on an install is set software-properties-gtk to add partners and turn automatic updates off.

On a daily live there are invariably updates already that same day so I install those.  On occasion the updates to that day's daily live fix a problem on the daily live that day....

What do you mean by cobwebs? Package cache?

---

### Post by cariboo on 2013-02-24
> **sudo san said:**
> What do you mean by cobwebs? Package cache?

I'm not sure what jerrylamos means by cobwebs, but on my system, I try different things during the testing cycle, and after a while things tend to work differently than they are supposed to, so I usually do a couple of clean installs during the cycle just to clean up any of the problems I've run into.

---

### Post by sudo san on 2013-02-24
About 10 hours ago I turned my singe boot into a dual-boot of both quantal any upgraded to raring. And now I can say there is no need for the gnome remix as I am thoroughly impressed with the improvements in unity. It runs a lot faster on my low-spec notebook and nautilus does not lag at all. I will definetly be keeping to unity now.:p

---

### Post by sudo san on 2013-02-24
If I change quantal to raring and raring to the next release code name in the command that grahammechanical posted, then will it change the ```
/etc/apt/sources.list
``` file to suit the next release?

---

### Post by cariboo on 2013-02-24
Yes it will. Most of us do a clean install of the released version, shortly before the toolchain is opened up, and use the commands to change the /etc/apt/sources.list before upgrading to the next testing version.

---

