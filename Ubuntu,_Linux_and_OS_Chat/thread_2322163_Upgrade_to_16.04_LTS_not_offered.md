---
title: "Upgrade to 16.04 LTS not offered"
date: 2016-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by kaweka on 2016-04-26
According to Ubuntu documentation a straightforward upgrade from 14.04 LTS to 16.04 LTS should be possible.
However, our Trusty Tahr does not offer such upgrade.
It does not offer any upgrade until following change in systems settings (Software & Updates) is made: Notify me of new Ubuntu version - For any new version;
the choice "for long-term support versions" is not sufficient enough for Trasty to detect the availability of Xenial Xerus.
User expectation is "for long-term support versions"  enables Trusty to detect availibility of Xenial upgrade.

Even if to enable "Notify me of new Ubuntu version - For any new version" just 15.10 is offered, but not Xenial.

---

### Post by howefield on 2016-04-26
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Upgrading_from_Ubuntu_14.04_LTS_or_15.10](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Upgrading_from_Ubuntu_14.04_LTS_or_15.10)

---

### Post by DuckHook on 2016-04-26
howefield's link shows you that 14.04 to 16.04 upgrades will not be activated until the first point release in roughly 3 month's time. That is to say, you won't get updated until 16.04.1 comes out. The reason for this makes tons of sense in my opinion: users of LTS presumably want stability. So, it makes sense to delay auto-upgrading until the worst bugs have been squashed, which generally happens by the first point release.

If you absolutely must have Xenial right now, then you can force this by doing:```
sudo do-release-upgrade -d
```...the -d switch upgrades to a development release, which is what Wily considers Xenial to still be. I *do not* recommend this unless there is a feature in Xenial that is mission-critical to you. If you decide to go ahead anyway, then heed the warning in my signature, to avoid much potential weeping and gnashing of teeth.

---

### Post by kaweka on 2016-04-27
Thanks for information. I did not anticipated such news in Release Notes as official Ubuntu documents generally claim
upgrade to newer LTS is possible, no exceptions are pointed out at those places.

Yes, it sounds reasonable to wait up a stabilization phase.
My current aim was to try it out with some experimental setup, not a production setup.

---

### Post by QLee on 2016-04-27
> **kaweka said:**
> Thanks for information. I did not anticipated such news in Release Notes as official Ubuntu documents generally claim
upgrade to newer LTS is possible, no exceptions are pointed out at those places.

Yes, it sounds reasonable to wait up a stabilization phase.
My current aim was to try it out with some experimental setup, not a production setup.

Upgrade to LTS is certainly possible, just look through the forums at the problems people are having. At the first point release, the upgrade path will likely be smoother with most bugs squashed. I agree with DuckHook, waiting seems like intelligent design.

That's why one should always read release notes before trying to upgrade, however you know that now, hopefully others reading this can learn something useful.

You can still try it out with an experimental setup, in fact I would advise you should test run on such an experimental setup before trying to upgrade your production system. It is handy to be lucky enough to have additional hardware for testing purposes.

---

### Post by oldrocker99 on 2016-04-27
There's always backing up your /home folder and installing Xenial from a DVD or USB, which will give you a clean system.

---

### Post by yonnie on 2016-04-29
except for the bugs, it seems pretty decent.  Networking doesn't handle setting static IP very well and if you switch from gnome to plasma there doesn't seem to be an easy path back to gnome yet.  Suspend won't do an autologin (at least I haven't found the setting causing the issue).  Scratch-pad can take two fingers for scrolling hoiz. and joy-stick doesn't seem to apply to built-in one.  Buttons for built-in joy-stick work, buttons for scratch-pad don't.  External trackball or mouse seem to work fine. Haven't observed the other reported bugs, Firefox works and so does clamtk and Libreoffice.  Overall, good for a new release, non of the bugs I've seen so far are show-stoppers.

---

### Post by mickee384 on 2016-04-29
you will get that option in about 3 months.. When they are at 16.04.1. (Stable to stable)

---

### Post by yonnie on 2016-04-30
mickee384: Not to be contrarian but...:
what is this page announcing?  [http://www.kubuntu.org/tag/kubuntu-16-04/](http://www.kubuntu.org/tag/kubuntu-16-04/)
what does this command line do?  update-manager -d (this works)
What does this page provide?  [http://www.kubuntu.org/getkubuntu/](http://www.kubuntu.org/getkubuntu/)  (this works)
What does this page help you with?  [http://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts)
I was advised to install 16.04 in an attempt resolve a problem with 14.04, the advisor claimed 16.04 was released as ready for work, this was last week.  Today's updates seems to have addressed some bugs and now I'm going to take it out on the job for a spin in the real world.  I miss the old KDE

---

### Post by Bucky Ball on 2016-05-01
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

