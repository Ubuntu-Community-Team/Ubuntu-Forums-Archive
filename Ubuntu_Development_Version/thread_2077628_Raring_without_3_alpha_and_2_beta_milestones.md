---
title: "Raring without 3 alpha and 2 beta milestones?"
date: 2012-10-29
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-10-29
This issue is discussed concerning the RR development.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-schedule](https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-schedule)

---

### Post by Chdslv on 2012-10-29
> **Harry33 said:**
> This issue is discussed concerning the RR development.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-schedule](https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-schedule)

I've already moved to 13.04, and if they keep on adding to the repos, I'd always have a bleeding edge 13.04 until release. :)

I don't believe the distro would break. It didn't in 12.10 and before. This way it is much better than Arch or something. Ubuntu 13.04 would be rolling release until the final release.:)

---

### Post by grahammechanical on 2012-10-29
I did some ISO image testing during the Precise development cycle. I did not see any point of daily testing of an ISO image that was not faulty.

And then there was the period during the Quantal cycle where I could not get a Live CD to run or to start an install without using nomodeset and without ending up with login screen and desktop that was unusable.

What is the point of doing daily ISO image testing if the faults are not being fixed? I recommended to the QA team leader that a working ISO image not be replaced until its replacement has been tested by community volunteer testers. We need to avoid the perception that Ubuntu is buggy. And that is difficult to do as the development branch is available for download to anyone.

I would be willing to ISO image test monthly milestone images. So, long as I know what I am supposed to look for. 

Regards.

---

### Post by jerrylamos on 2012-10-30
Pretty much do daily build installs from time to time.  All I'd need is a heads up that a buncha stuff is in daily build and worth looking for bugs starting from install.

QQ RC was a real mess some of which (not all) was cleared by release.  QQ release has problems booting and NM on my wide screen amd64 and also NM problems on my netbook.  QQ B1 was cleaner. Launchpad bugs written.

Not running QQ any more, just 12.04.1 and RR.

---

### Post by philinux on 2012-10-31
Update from Nick Skaggs.

[http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html](http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html)

---

### Post by balloons on 2012-11-01
I may not be fast on responding, but I am here if you have questions :-) I'll try and hit what you've mentioned already.

Don't get confused by the 'monthly' milestones idea -- there won't be any such thing. No milestones, only cadence testing. Teams will target 'months' in launchpad for development work, but that will be for them to manage schedules. Has no meaning or impact to us. There won't be any special 'blessed' images each month.


Graham, your idea of not replacing a broken iso (daily) from yesterday until today's works is covered by the planned smoke testing before the image is published. If it fails to do a basic install, we won't get the image to prevent us from wasting time testing it.


Jerry, I think this will fit your workflow just fine. We'll have targeted weeks with specific things to look out for and test during that week that is new in the image or has simply been chosen by all of us to take a closer look because of issues :-) You'll use the daily iso of whatever day you happen to chose during the week.

In addition, the results will sit for the entire week (not be lost from one day to the next!), so you will be able to see what's been done and by whom over the course of the week. The previous cadence week will also easily be shown. That should encourage everyone to fan out and do different sets of tests, while also allowing us to see how many tests on different hardware we achieved for some tests. Overall, I think 
you all will find the process much more conducive to getting involved.

As far as bugs go, we as a community can track and focus on things we find from the previous cadence weeks and re-test the next cadence week until they are fixed. I hope this will help too with the bugs getting lost problem.

Overall, I've very happy with the changes. Any more questions? I'll try and answer them as I can.

---

### Post by grahammechanical on 2012-11-01
An Activity Planner would be useful. It does not matter whether it takes the form of the Ubuntu Release Schedule or is based upon a calendar, or some other layout, so long as it shows what is needed and when it should be done. 

Regards.

---

### Post by Slug71 on 2012-11-01
> **grahammechanical said:**
> 
What is the point of doing daily ISO image testing if the faults are not being fixed? I recommended to the QA team leader that a working ISO image not be replaced until its replacement has been tested by community volunteer testers. We need to avoid the perception that Ubuntu is buggy. And that is difficult to do as the development branch is available for download to anyone.

I would be willing to ISO image test monthly milestone images. So, long as I know what I am supposed to look for. 

Regards.

Agreed.

---

### Post by Slug71 on 2012-11-01
> **Harry33 said:**
> This issue is discussed concerning the RR development.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-schedule](https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-schedule)

I still see 2 Betas. The second is just called Final Beta instead of Beta 2.

---

### Post by Beardedturtle on 2012-11-18
[http://news.softpedia.com/news/It-s-Official-Ubuntu-13-04-Will-Drop-Alpha-Releases-303458.shtml](http://news.softpedia.com/news/It-s-Official-Ubuntu-13-04-Will-Drop-Alpha-Releases-303458.shtml)

Beta is in March. No alpha/release candidates

---

### Post by offgridguy on 2012-11-18
Interesting, thank you.

---

### Post by Beardedturtle on 2012-11-18
> **offgridguy said:**
> Interesting, thank you.

Your welcome.

---

### Post by jpeddicord on 2012-11-18
Edited your thread title; please remember to use descriptive titles as "Raring Ringtail" isn't very helpful in the Raring Ringtail forum. ;)

Jacob

---

### Post by kansasnoob on 2012-11-19
No alphas in Lubuntu either, but they chose to have two betas; Mar 14 : Beta 1, and; Mar 28 : Beta 2. Source:

[https://lists.launchpad.net/lubuntu-qa/msg01658.html](https://lists.launchpad.net/lubuntu-qa/msg01658.html)

I'm still curious just how Cadence Testing will work? The schedule has it running every other week, for a full week.

Previously we'd have 3 to 5 days of iso/upgrade testing prior to each alpha or beta. This new testing schedule more than doubles the total amount of testing days which I actually fear will scare off many testers :(

---

### Post by Elfy on 2012-11-19
Xubuntu is the same as Lubuntu, 2 beta's.

With testing of specific issues as called for.

---

### Post by ventrical on 2012-11-19
We can sort of assign our own psuedo-alphas  Dec. 6th and  Feb.7th.

---

### Post by philinux on 2012-11-19
> **Beardedturtle said:**
> [http://news.softpedia.com/news/It-s-Official-Ubuntu-13-04-Will-Drop-Alpha-Releases-303458.shtml](http://news.softpedia.com/news/It-s-Official-Ubuntu-13-04-Will-Drop-Alpha-Releases-303458.shtml)

Beta is in March. No alpha/release candidates

[http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html](http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html)

Was confirmed a while back.

Threads Merged.

---

### Post by kansasnoob on 2012-11-19
Does anyone know what Kubuntu's plans are?

I posted Lubuntu's plans and Elfy posted Xubuntu's plans so I'm just curious :)

---

### Post by philinux on 2012-11-19
Sorry can't find anything for kubuntu as yet.

There is more info on raring schedule and the road to 14.04.

[http://theravingrick.blogspot.co.uk/2012/11/the-road-to-1404.html?m=1](http://theravingrick.blogspot.co.uk/2012/11/the-road-to-1404.html?m=1)

---

### Post by VinDSL on 2012-11-19
> **Beardedturtle said:**
> 
Beta is in March. No alpha/release candidates
Heh!  I don't know why I'm telling you guys this, but... it's yours for free.

I haven't done a fresh install since Ubu 11.10 (Oneric Ocelot) Final :D

```

vindsl@Zuul:~$  ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
**[COLOR="Red"]Oct 13 2011[/COLOR]**
vindsl@Zuul:~$ 

```
I don't have time to .iso test, so I don't see the point, you know?

Sorry!  Carry on...

---

### Post by kansasnoob on 2012-11-19
> **philinux said:**
> Sorry can't find anything for kubuntu as yet.

There is more info on raring schedule and the road to 14.04.

[http://theravingrick.blogspot.co.uk/2012/11/the-road-to-1404.html?m=1](http://theravingrick.blogspot.co.uk/2012/11/the-road-to-1404.html?m=1)

Lots, and lots of good info there :)

Of course the proof is in the pudding so we'll see if all works out as planned.

---

### Post by jerrylamos on 2012-11-20
> **VinDSL said:**
> Heh!  I don't know why I'm telling you guys this, but... it's yours for free.

I haven't done a fresh install since Ubu 11.10 (Oneric Ocelot) Final :D

```

vindsl@Zuul:~$  ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
**[COLOR="Red"]Oct 13 2011[/COLOR]**
vindsl@Zuul:~$ 

```
I don't have time to .iso test, so I don't see the point, you know?

Sorry!  Carry on...

What I find is after update after update and dist-upgrade Ubuntu gets fatter and fatter and I think slower and slower with all the junk left over in spite of apt-get clean, autoclean, autoremove, going thru synaptic and removing old headers, etc.

vinds, how do you get rid of all the old obsolete clutter?

---

### Post by jppr on 2012-11-20
> **jerrylamos said:**
> What I find is after update after update and dist-upgrade Ubuntu gets fatter and fatter and I think slower and slower with all the junk left over in spite of apt-get clean, autoclean, autoremove, going thru synaptic and removing old headers, etc.



You can also install the Bleachbit to clean up your system... that works :popcorn:

---

### Post by VinDSL on 2012-11-20
> **jerrylamos said:**
> vindsl, how do you get rid of all the old obsolete clutter?
Believe it or not, a combination of PPA-Purge & Ubuntu-Tweak, with a sprinking of Synaptic, does a very nice job of keeping the cruft at bay.  ;)

---

