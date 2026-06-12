---
title: "Update Fatigue!!!"
date: 2018-12-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Mythological on 2018-12-20
I just wonder if anyone else feels like they are suffering update fatigue.  Almost every day when I turn on my system, there are software updates waiting.  Most of the time they are minor ones for individual pieces of software but about every week or two there are kernel updates.  I hate kernel updates with an unbridled hatred, for several reasons:

- They always require rebooting the system, which in turn means that some piece of software (usually Kodi) will start acting flaky and I'll need to reboot the system again some number of times before everything works as it should.
- Every single time I've had a major system problem it's been after a kernel update.
- And just because they are so damned frequent!

I have a Raspbian Pi that runs Raspbian, and a Mac Mini that runs MacOS, and I help with a remote server that runs Debian, and none of those get kernel or OS updates as frequently as my Ubuntu box.  On those systems it can be several weeks or even months between kernel or OS updates, and that's fine by me.  Since Ubuntu is based on Debian I just don't understand why it gets so many more kernel updates than Debian.  It's been less than two weeks since the last one and sure enough another one showed up today.  I've always liked Ubuntu but I am starting to not like it so much because of the too frequent updates.  Software updates are fine and I appreciate that they complete so quickly in Ubuntu (especially compared to MacOS, where you will wait about 45 minutes for a point version update to complete!) but do they really need to show up so often?

And before anyone points out that you don't have to install updates the minute they appear, that is true but Ubuntu will nag you about them until you do.  Really I'd only like to see software updater pop up about once a week, preferably at a time of my choosing, and let me apply all of the week's updates at once.  But kernel updates are another matter, I would say I never want to see those and to some extent that would be true but I realize that sometimes they contain important security fixes.  Still I wish there was some way to say "don't show me a kernel update more often than once every six weeks or so unless it addresses a MAJOR security issue!"

Anyone else feel like they are suffering update fatigue?

---

### Post by QIII on 2018-12-20
Not a support request.

Moved to Ubuntu, Linux and OS Chat.

---

### Post by poorguy on 2018-12-20
If it takes so much out of you to ***install updates*** than go to*** software and updates*** and then ***updates*** and then ***automatically check for updates*** and change it to ***never*** and then you can ***check for updates*** when you feel like ***checking and installing updates***.

---

### Post by TheFu on 2018-12-20
TL;DR

I manually patch our systems every weekend, when not on travel.  More often than that is simply too disruptive for low risk systems and make for a less-than-stable setup.  Nobody wants some patch to break things during a work-week.

IMHO.

Patching on Saturday reduces the risks of any failure being around on Monday when people need to get work done. It also simplifies any troubleshooting since issues that happen the first time someone is back from the weekend could be due to updates.  If it happens later in the week, it is less likely to be from an update.  That is our thought process. It has holes, but it seems to work.

---

### Post by pauljw on 2018-12-21
> **poorguy said:**
> If it takes so much out of you to ***install updates*** than go to*** software and updates*** and then ***updates*** and then ***automatically check for updates*** and change it to ***never*** and then you can ***check for updates*** when you feel like ***checking and installing updates***.

Sheez, there ya go again, making me responsible for how my computer works...  :mad:

---

### Post by poorguy on 2018-12-21
> **pauljw said:**
> Sheez, there ya go again, making me responsible for how my computer works...  :mad:

Damn it!  

I hate when that happens. :lol:

---

### Post by jdeca57 on 2018-12-21
There must be a problem with my system. I use the stable 18.04 and I don't have a new kernel update each week or even each month. Now, on another installation with the 18.10 the updates are more frequent. So, is the answer not more to use the stable versions of the OS?

---

### Post by Impavidus on 2018-12-21
It must be something with your 18.04. I just checked my logs on 18.04:```
$ zcat dpkg.log.5.gz dpkg.log.4.gz dpkg.log.3.gz dpkg.log.2.gz | grep 'status installed linux-image-generic'
2018-07-03 10:44:43 status installed linux-image-generic:amd64 4.15.0.24.26
2018-07-21 10:23:40 status installed linux-image-generic:amd64 4.15.0.29.31
2018-08-07 10:00:18 status installed linux-image-generic:amd64 4.15.0.30.32
2018-08-15 09:21:22 status installed linux-image-generic:amd64 4.15.0.32.34
2018-08-24 10:25:44 status installed linux-image-generic:amd64 4.15.0.33.35
2018-09-12 23:29:00 status installed linux-image-generic:amd64 4.15.0.34.36
2018-10-05 17:39:36 status installed linux-image-generic:amd64 4.15.0.36.38
2018-10-23 18:56:13 status installed linux-image-generic:amd64 4.15.0.38.40
$ cat dpkg.log.1 dpkg.log | grep 'status installed linux-image-generic'
2018-11-14 10:31:29 status installed linux-image-generic:amd64 4.15.0.39.41
2018-12-03 23:54:16 status installed linux-image-generic:amd64 4.15.0.42.44
2018-12-20 10:42:14 status installed linux-image-generic:amd64 4.15.0.43.45
```
11 kernel upgrades in 6 months, that's close to one every 2 weeks. But I don't consider that excessive. They never cause any problem (on my hardware at least) and I shut down my computer every night, so don't care about rebooting. The only upgrade-caused problem I ever had in 12 years using Ubuntu was caused by an upgrade to grub.

So, no, I don't suffer from update fatigue.

---

### Post by Tadaen_Sylvermane on 2018-12-22
I have a bit to much free time right now. Only working part time for the moment. As such I check for updates regularly during the week. Normally when I have a proper schedule though I run them monthly. Regardless of when or what I'm running though, I do always turn off the automatic notifications. I do it on my time, not when the machine decides.

---

### Post by poorguy on 2018-12-22
I have six computers throughout my house running different Linux Distros and when I see I have updates I just install them then restart the computer and carry on without any fatigue what so ever. ;)

---

### Post by pauljw on 2018-12-22
Being retired it's just my morning ritual to check for updates.  I have a couple of systems that I ssh into and update them if needed as well as several vm's on this system.  It doesn't normally take more than a few minutes unless there are kernels, but I'd much rather we get frequent patches and get them done so our systems are as safe as possible.  To my way of thinking, there's nothing worse than having a system get compromised for which corrective patches were available months ago but someone was too busy or lazy to apply them.

---

### Post by poorguy on 2018-12-22
> **pauljw said:**
> It doesn't normally take more than a few minutes unless there are kernels, but I'd much rather we get frequent patches and get them done so our systems are as safe as possible. 
I agree the few minutes it takes to check for updates and install updates is time well spent for exactly the same reason.

---

### Post by ubname on 2018-12-23
> **Mythological said:**
> I just wonder if anyone else feels like they are suffering update fatigue. 

Absolutely no, how it is possible to manage, defer, and decide when and how to install/or not install updates is one of the best features on Ubuntu (or many other distributions).


> **Mythological said:**
> And before anyone points out that you don't have to install updates the minute they appear, that is true but Ubuntu will nag you about them until you do.  ...

Disable auto check for updates; then manually check when you want. Auto check is for your convenience, it's _not a mandatory feature_.

---

