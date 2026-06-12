---
title: "About Oneiric not displaying notifications for security updates"
date: 2011-11-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2011-11-05
I made a brief mention of this here:

[http://ubuntuforums.org/showpost.php?p=11425421&postcount=35](http://ubuntuforums.org/showpost.php?p=11425421&postcount=35)

And as I said there, it appears that there is no actual update notification in Oneiric :(

Or am I somehow missing something?

NOTE: before someone slams me for posting a question about Oneiric here please understand the following:

#1: I followed Lubuntu development more closely than Ubuntu development during the Oneiric cycle.

#2: As with all dev cycles the previous release has to serve to some degree as a "baseline" to compare changes.

Just before posting this I installed a fresh Oneiric (i386) and chose NOT to dl updates. The only thing I did was import a .mozilla profile from another installation and I see no update notification.

The only thing I see is this **if I click on the applet in the upper right hand corner**:

[ATTACH]206466[/ATTACH]

Yet if I look at Update Manager there are Security updates available:

[ATTACH]206467[/ATTACH]

Is that not a security issue?

BTW, and quite off-topic, I had to boot into a lateral Natty install to post this because Unity "flipped out" regarding the ability to add another screenshot after the first one.

---

### Post by ventrical on 2011-11-05
When there are security updates, display imediately.

---

### Post by kansasnoob on 2011-11-05
> **ventrical said:**
> When there are security updates, display imediately.

Yes, it's set there by default but where is the notification:

[ATTACH]206472[/ATTACH]

[ATTACH]206473[/ATTACH]

Is that not a nasty security flaw that everyone's overlooked in favor of pretty and fancy?

---

### Post by gsmanners on 2011-11-05
I would have to say, yes it is: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

---

### Post by kansasnoob on 2011-11-05
> **gsmanners said:**
> I would have to say, yes it is: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

But I think this is a new bug. That began 2009 and and the last comment was in 2010.

I'm tired ATM but, unless someone else comes up with an answer, I'll file a new bug report tomorrow.

I'd just like to know how something so bad can go unnoticed :rolleyes:

---

### Post by kansasnoob on 2011-11-07
Cross-post:

[http://ubuntuforums.org/showpost.php?p=11435074&postcount=76](http://ubuntuforums.org/showpost.php?p=11435074&postcount=76)

---

### Post by Mr. Picklesworth on 2011-11-07
> **kansasnoob said:**
> Yes, it's set there by default but where is the notification:

[ATTACH]206472[/ATTACH]

[ATTACH]206473[/ATTACH]

Is that not a nasty security flaw that everyone's overlooked in favor of pretty and fancy?

Probably just one of those nice little details that was overlooked in the specification. You can take a look at [mpt's wireframe on the wiki]("https://wiki.ubuntu.com/DeviceMenuAndUserMenu") to see how it was intended, and the rationale.
Asking &#8220;are updates available?&#8221; is easier than asking that followed by &#8220;how important are they?&#8221;, so it's naturally what one would do without additional design requirements. I'd agree with you there are a few decent reasons to convey the latter in that menu item, particularly that this string and the one in the update manager itself are quite similar&#8230;
With that said, there might be some decent reasons not to do it ;)

I'd suggest you chat with the designers on IRC, or file a bug report. They'd probably appreciate it.

By the way, that isn't a notification. (Well, it is in practice, but it isn't a notification as in the notification system). Notifications are the little bubbles that appear while you're doing other things. This is just a menu item in the device menu.

---

