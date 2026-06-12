---
title: "Upgraded - Wireless Borked"
date: 2009-11-14
forum: System76 Support
---

### Post by Eyore15 on 2009-11-14
I just new it was going to happen.

I upgraded my Starling last night.  When all was said and done, the wireless didn't work.

I tried it with applying what I thought was the latest System76 driver and then tried the "restore" function as well. I then found Mr. Aaron's most recent email (I last checked the forms around 3 yesterday afternoon) that there was a newer version of the driver.

I've tried to use the 2.4 driver, but it's been installing for an hour, so that's apparently broken too.

What I have now is a very small boat anchor.

In retrospect, I would have loved it if there had been a message from System76 (or somebody) that said, simply,

"It's not recommended that Starling owners upgrade to 9.10 due to a problem with the wireless."

I've looked through the archives and can't find anyplace where there was such a warning.  There were some vague references to distance-from-access point problems, but nothing I can find that said it was going to break my system.

I'm not a tech guy, so if fixing this means CLI stuff, please speak slowly and use small words.

tia

mcm

---

### Post by jdb on 2009-11-14
> **Eyore15 said:**
> I just new it was going to happen.

I upgraded my Starling last night.  When all was said and done, the wireless didn't work.

I tried it with applying what I thought was the latest System76 driver and then tried the "restore" function as well. I then found Mr. Aaron's most recent email (I last checked the forms around 3 yesterday afternoon) that there was a newer version of the driver.

I've tried to use the 2.4 driver, but it's been installing for an hour, so that's apparently broken too.

What I have now is a very small boat anchor.

In retrospect, I would have loved it if there had been a message from System76 (or somebody) that said, simply,

"It's not recommended that Starling owners upgrade to 9.10 due to a problem with the wireless."

I've looked through the archives and can't find anyplace where there was such a warning.  There were some vague references to distance-from-access point problems, but nothing I can find that said it was going to break my system.

I'm not a tech guy, so if fixing this means CLI stuff, please speak slowly and use small words.

tia

mcm

They did, it got buried by later posts, it was the first one:

[http://ubuntuforums.org/showthread.php?t=1304532&highlight=starling+upgrade]("http://ubuntuforums.org/showthread.php?t=1304532&highlight=starling+upgrade")

There needs to be a way to keeps messages like that visable.

jdb

---

### Post by allersj on 2009-11-14
Eyore15,

Were you connected to the internet through a wireless connection or a wired connection while trying to perform the System76 restore function?

I'm just wondering if the problems you had were due to poor wireless connectivity.

---

### Post by Eyore15 on 2009-11-14
> **allersj said:**
> Eyore15,

Were you connected to the internet through a wireless connection or a wired connection while trying to perform the System76 restore function?

I'm just wondering if the problems you had were due to poor wireless connectivity.

I was/am using wired.

FYI

The "install" for the system76 driver is now on it's 7th hour of the little line bouncing back and forth.  My suspicion is that there may be something wrong.

---

### Post by Eyore15 on 2009-11-14
> **jdb said:**
> They did, it got buried by later posts, it was the first one:

[http://ubuntuforums.org/showthread.php?t=1304532&highlight=starling+upgrade]("http://ubuntuforums.org/showthread.php?t=1304532&highlight=starling+upgrade")

There needs to be a way to keeps messages like that visable.

jdb

They can make it a sticky and it stays in the top, before the regular threads begin.  To my mind, that is what should happen.  But System76 doesn't control the forum, so I don't know what's involved.

---

### Post by robtg on 2009-11-14
> **Eyore15 said:**
> I was/am using wired.

FYI

The "install" for the system76 driver is now on it's 7th hour of the little line bouncing back and forth.  My suspicion is that there may be something wrong.

Mark:  The "little line bouncing back and forth" has happened to me a number of times installing the s76 driver.  What I do is force the application closed, reboot, and try again.  It always works on the second try; I have no idea why.  

Rob

---

### Post by Eyore15 on 2009-11-15
They problem lay in grub.

A forum member discovered that the driver was dependent on Grub2.  Somewhere in the upgrade, we ended up with Grub.  Once I went into synaptic and installed grub two, I could run the s76 driver 3.4.0.  Now I'm like everyone else, operating within 30 feet or so of the AP.  My thanks to all who tried to help.

mcm

---

### Post by theorysavage on 2009-11-15
although I did get the short range wireless working on the starling with karmic, i decided to go through the trouble to reinstall old reliable jaunty with the 2.3.7 driver. wireless works at a much better distance for me now and i'm going to hold off on the upgrade until more bugs are worked out.

---

### Post by HotShotDJ on 2009-11-15
> **Eyore15 said:**
> They can make it a sticky and it stays in the top, before the regular threads begin.  To my mind, that is what should happen.  But System76 doesn't control the forum, so I don't know what's involved.I agree here.  System76 should make use of the "sticky" function.  Of course, that would require that Thomasaaron get moderator privileges. If ubuntuforums.org doesn't wish to grant those privilages or Thomasaaron doesn't wish to have those privilages, I'm sure they could set up a way to request that a moderator do it for him.  It would make life much easier for System76 users if important announcements and common problems appeared as stickies.

---

### Post by thomasaaron on 2009-11-16
Yes it would be nice.

Just to verify... I'm not a moderator. In the past, when I've requested a sticky, it didn't happen. I'll talk to some folks about it to see what can be done.

---

### Post by Tart on 2009-11-16
Can they make you moderator for system76 subforum? or just moderator?

---

### Post by thomasaaron on 2009-11-17
We're checking into that. I really don't want to be a moderator. I have plenty to keep me buried already. But it would be nice if I could post/delete stickies.

---

