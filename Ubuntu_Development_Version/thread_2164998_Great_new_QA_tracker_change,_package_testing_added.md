---
title: "Great new QA tracker change, package testing added!"
date: 2013-08-02
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-08-02
It's possible I'm just slow catching on, but this may be of interest to others as it was to me. I caught this at Lubuntu QA today:

[https://lists.launchpad.net/lubuntu-qa/msg03387.html](https://lists.launchpad.net/lubuntu-qa/msg03387.html)

> Cadence Week 4 is here!

Week 4 is here, can you believe it? Starting August 3rd, it's time to test images and packages again. Now, you'll notice something a little different about the layout this time around. Thanks to your continued feedback and ideas, we've tweaked the layout even further.


[http://packages.qa.ubuntu.com/qatracker/milestones/300/builds](http://packages.qa.ubuntu.com/qatracker/milestones/300/builds)

For those of you testing on the isotracker, this should look VERY familiar. In short, the testcases are laid out by product, including a section for common tests (like graphics, networking, web browsers). This means flavors are more clearly shown; and as you can see xubuntu is already laid out very nicely! The xubuntu team has been rapidly closing bugs and getting testcases for there core apps, in addition to contributing heavily towards this idea. Thank you David, Pasi, Elfy and xubuntu'ers!


Lubuntu folks, I know you too have some testcases already written and we'll need to get a sectioned sorted for you. Ping me!


Ali, and ubuntu gnome folks, let's get something up and running for you as well! You can file bugs for what needs done specific for gnome, and steal what's already been written :-) Ping me!


The rest of the details are below. Remember, feedback is appreciated! What do you think of the changes?


----

So what is cadence testing? Have a look at this page to get more information:


[https://wiki.ubuntu.com/Testing/Cadence](https://wiki.ubuntu.com/Testing/Cadence)

In short, as a community we're testing different things about every ~2 weeks, and share results to flesh out bugs and problem areas. The full schedule is here:


[https://wiki.ubuntu.com/QATeam/Cadence/Saucy](https://wiki.ubuntu.com/QATeam/Cadence/Saucy)

So what's up for testing this week? The daily images, and the default applications in ubuntu

Full details are here:

[https://wiki.ubuntu.com/QATeam/Cadence/Saucy/Week4](https://wiki.ubuntu.com/QATeam/Cadence/Saucy/Week4)

If you need help submitting results, have a look at the ISO testing and Cadence Week testing walkthroughs.


[https://wiki.ubuntu.com/Testing/Cadence/Walkthrough](https://wiki.ubuntu.com/Testing/Cadence/Walkthrough)
[https://wiki.ubuntu.com/Testing/ISO/Walkthrough](https://wiki.ubuntu.com/Testing/ISO/Walkthrough)

Do note that you don't need anything special to participate in cadence week testing! Both an installed version of the development branch of ubuntu (aka saucy) in a VM or on a real box, or even a live session of the lastest daily image will work.


Good luck! Thanks and Happy Testing everyone,

Nicholas



When I first read that I was confused but now in addition to the standard iso/upgrade testing:

[http://iso.qa.ubuntu.com/qatracker](http://iso.qa.ubuntu.com/qatracker)

we now have a separate space on the QA Tracker for apps:

[http://packages.qa.ubuntu.com/qatracker](http://packages.qa.ubuntu.com/qatracker)

Notice the difference?

We now have "packages.qa" in addition to "iso.qa" :guitar:

I think this will prove to be a very positive change over time. Kudos to all involved in that change :D

---

### Post by mc4man on 2013-08-02
that's been around for a bit, sometimes handy to give a current bug a little 'push' by adding there 
(bug doesn't have to be in or result of  test case to fail an app.
Too bad they don't test compiz though possibly they'd need a bigger hdd  if they did..

---

### Post by ventrical on 2013-08-03
I can't do much with an .iso that just loads the Ubuntu Logo with the 4 dots scrolling indefintely.

saucy-desktop-i386 persistive.

I'll try 'discard elsewhere'.

---

### Post by ventrical on 2013-08-03
Here's what I got so far ..same thing as a couple of days ago.

I would report it at the qa tracker  but this iso is just so slow on the live.

Edit:

Same buisness with Intel  graphics..

```


01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

[URL="https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1208044"]https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1208044
[/URL]

---

### Post by twocamels on 2013-08-04
> **ventrical said:**
> Here's what I got so far ..same thing as a couple of days ago.

I would report it at the qa tracker  but this iso is just so slow on the live.

Edit:

Same buisness with Intel  graphics..

```


01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

[URL="https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1208044"]https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1208044
[/URL]


 It's me , ventrical. hehe .. sheesh .. ummm with saucy-desktop-amd64.iso I still got those bars at the top of the screen when Ubiquity starts up.

---

