---
title: "Quick question regarding updates on the Alpha"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bastones on 2012-01-20
Hi,

This may seem like a simple question to others but I'm not entirely sure so all I can do is ask. In regards to receiving updates with the Alpha (I have it installed on a separate partition), it continues to receive updates which we can install via Update Manager. However, as the beta arrives and in April, the stable release, will I need to download the stable release via the Ubuntu website in order to upgrade or does Alpha and Beta releases continue to receive updates via Update Manager right up until the stable release? (i.e. when the stable release is out in April, I can upgrade to it via Update Manager?)

Thanks,
Ben.

---

### Post by dino99 on 2012-01-20
its kind of question poping regularly on this forum and answered each time in the same way :) Even after final release, updates continue to come.And you might seen some of them in the 5 coming years as PP is an LTS :)

---

### Post by bastones on 2012-01-20
> **dino99 said:**
> its kind of question poping regularly on this forum and answered each time in the same way :) Even after final release, updates continue to come.And you might seen some of them in the 5 coming years as PP is an LTS :)

Thank you for answering :P. What I meant was, will the Alpha, in the form of continued updates, be eventually upgradeable to the stable release via the Update Manager instead of (what I presume) having to download stable release (in April) from ubuntu.com and upgrading manually, so to speak.

---

### Post by bmbaker on 2012-01-20
it is a good question one that gets asked alot.......... if you look in the sticky threads you will find this [http://ubuntuforums.org/showthread.php?t=1859235](http://ubuntuforums.org/showthread.php?t=1859235)

its good to be informed :-)

If I install the alpha/beta now, do I need to reinstall the final version when it's released? 

You don't have to (Update Manager will let you upgrade to the final version), but you may want to, if one or more of the below apply:
You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 
You have replaced essential components of your installation with versions from external repositories/PPAs
You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community
You have applied hacks/workarounds for testing purposes for good reason (prompted during structured testing, bug triage etc.), which may cause problems during daily usage of a stable installation
You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes)

---

### Post by xyzzyman on 2012-01-20
Actually the last 2-3 days before final is released, we should all install 11.10 and upgrade as a final field test. :) THEN when it's final do our permanent install.

---

### Post by zika on 2012-01-20
> **xyzzyman said:**
> Actually the last 2-3 days before final is released, we should all install 11.10 and upgrade as a final field test. :) THEN when it's final do our permanent install.[img]http://images.zaazu.com/img/afraid-male-afraid-frightened-smiley-emoticon-000293-large.gif[/img]It is easy for You to say, You're still on 11.10 according to stuff on the left...

---

### Post by dino99 on 2012-01-20
and some still think they can win an extra bonus :) :)

---

### Post by zika on 2012-01-20
> **dino99 said:**
> and some still think they can win an extra bonus :) :)Of cource they can! But not „win“, maybe „ubuntu“... [img]http://images.zaazu.com/img/Distort-crazy-mad-insane-smiley-emoticon-001038-large.gif[/img]

---

### Post by xyzzyman on 2012-01-20
> **zika said:**
> [img]http://images.zaazu.com/img/afraid-male-afraid-frightened-smiley-emoticon-000293-large.gif[/img]It is easy for You to say, You're still on 11.10 according to stuff on the left...

I have both. Only keeping one full PP test install this cycle and one in a VM, but right now the main one is a tad borked while we work on the headphone jack detection. Pulse audio is now working but still some other regressions with kernel/driver.

Once 12.04 is closer to final I'll do an upgrade also over my main 11.10 install to make sure no show stoppers pop up on a well used install, then I'll do a fresh install. Ubuntu installs so fast from an SD card it's ridiculous when I look at the competition (Outside of linux), figuring how much software is preinstalled. This time should be much smoother than 11.04 to 11.10. I had a dbus failure a few times during the beta that turned out to be a problem with /var/run or something being moved. 12.04 from 11.10 seems more like the vista to win7 progression. Optimization & tweaks and usability enhancements.

---

### Post by grahammechanical on 2012-01-20
It is true that doing a daily or at least regular update will bring a development (alpha) branch up to the level of the distribution release but I found that for 11.10 I had to run the dreaded partial distribution upgrade to get some final small changes. In the case of 11.10 beta I did not get the new look login screen until I ran that distribution upgrade.

Regards.

---

### Post by zika on 2012-01-20
> **grahammechanical said:**
> It is true that doing a daily or at least regular update will bring a development (alpha) branch up to the level of the distribution release but I found that for 11.10 I had to run the dreaded partial distribution upgrade to get some final small changes. In the case of 11.10 beta I did not get the new look login screen until I ran that distribution upgrade.

Regards.&#8222;Dist-upgrade&#8220; is unavoidable in (almost) all testing cycles I've joined. I do have dist-upgrade (almost) every day now in 12.04. It is not a bad thing once You (hope or think) know what is going to be replaced and (roughly) why...
No use making a great villain out of it...
Caution is (as always) imperative, yes...

---

### Post by philinux on 2012-01-20
Never mind all that imagine someone upgrading from 10.04. 

Could go well :P

or not. [IMG]http://oi39.tinypic.com/andjqe.jpg[/IMG]

---

