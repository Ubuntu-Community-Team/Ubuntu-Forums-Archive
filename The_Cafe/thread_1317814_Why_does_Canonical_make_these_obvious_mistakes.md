---
title: "Why does Canonical make these obvious mistakes?"
date: 2009-11-07
forum: The Cafe
---

### Post by jespdj on 2009-11-07
Look at [the download page for Ubuntu Netbook Remix](http://www.ubuntu.com/getubuntu/download-netbook).

There are two links there that explain how to make a bootable USB stick. On the right under "You may also want to...", you see a link [Learn how to create a UNR flash drive](https://help.ubuntu.com/community/Installation/FromImgFiles). That page explains how to create a bootable USB stick from an **img** file. But Netbook Remix 9.10 is not available as an img file, but as an iso file!! So, why is that misleading link there?

The second link, [How to create a bootable flash drive](https://help.ubuntu.com/community/Installation/FromUSBStick), points to a page that explains how to make a bootable USB stick from an **iso** file. Fine. But that page looks messy and incomplete.

Second, I've installed it on my Dell Mini 9. Wireless networking doesn't work. It did in Netbook Remix 9.04. I remember reading a page on the Ubuntu website that mentioned something about Broadcomm wireless not being switched on properly. But I can't find the page that said that now (so, complaint: Why is this information so hard to find?).

Why is there such an obvious wireless networking bug in Netbook Remix 9.10? This looks like a pretty critical error which is going to affect a lot of users, they should regard something like this a show stopper for release.

It's this kind of stupid and obvious things that make Ubuntu seem like a lower-quality, amateur OS compared to Windows or Mac OS X.

Please Canonical, do not make these stupid and glaring mistakes.

Sorry for the rant, but this disappoints me and it lowers the quality of Ubuntu.

---

### Post by Paqman on 2009-11-07
> **jespdj said:**
> 
Second, I've installed it on my Dell Mini 9. Wireless networking doesn't work. It did in Netbook Remix 9.04. I remember reading a page on the Ubuntu website that mentioned something about Broadcomm wireless not being switched on properly. But I can't find the page that said that now (so, complaint: Why is this information so hard to find?).


Does [this link]("http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html") help?

---

### Post by jespdj on 2009-11-07
Thanks Paqman, the wireless issue is fixed now.

Still, an obvious error which is going to affect a lot of users which even has a simple solution should not be in an official Ubuntu release! Canonical could easily have fixed this before the official release, that would have saved lots of users a lot of agony. Too bad that they allow such mistakes to happen.

---

### Post by quinnten83 on 2009-11-07
> **jespdj said:**
> Thanks Paqman, the wireless issue is fixed now.

Still, an obvious error which is going to affect a lot of users which even has a simple solution should not be in an official Ubuntu release! Canonical could easily have fixed this before the official release, that would have saved lots of users a lot of agony. Too bad that they allow such mistakes to happen.

propietary drivers that can not be installed with the distribution perhaps based on legal matters?
I do agree that they should make it readily apparent what the fix is.

---

### Post by Tipped OuT on 2009-11-07
An **Img** file can be sub suited with any disc image file. I could use ISO, MDS, NRG, etc.

It's relevant.

---

### Post by jespdj on 2009-11-07
> **quinnten83 said:**
> propietary drivers that can not be installed with the distribution perhaps based on legal matters?
I do agree that they should make it readily apparent what the fix is.
I don't buy that, because with previous versions of Ubuntu it worked out-of-the-box.
> **Tipped OuT said:**
> An **Img** file can be sub suited with any disc image file. I could use ISO, MDS, NRG, etc.

It's relevant.
I guess you meant to say **ir**relevant. Well, it is not irrelevant, because the instructions on the page about making a bootable USB from an img file do not work with an iso file (I tried). Those kinds of image files are not 100% the same. There should not be a link to instructions that aren't applicable to Ubuntu Netbook Remix 9.10 on the download page, a lot of people are going to click that and be confused.

---

### Post by Paqman on 2009-11-07
> **jespdj said:**
> 
Still, an obvious error which is going to affect a lot of users which even has a simple solution should not be in an official Ubuntu release!

Ubuntu does rely on users to report any hardware-specific bugs they encounter. Perhaps there aren't enough Mini 9 users helping out with testing? Maybe you would like to help with the next release?

---

### Post by mivo on 2009-11-07
> **Tipped OuT said:**
> An **Img** file can be sub suited with any disc image file. I could use ISO, MDS, NRG, etc.

That isn't actually true. There are differences between an ISO file and the raw data (i.e. IMG) version of it, and most of the tools I'm familiar with require a raw data file, not an ISO. There is a way to achieve this in Linux, but it is more involved.

---

### Post by 23meg on 2009-11-07
Website bugs are [tracked on Launchpad]("https://bugs.launchpad.net/ubuntu-website/"), similar to Ubuntu bugs. When you encounter faults of any kind (typos, ambiguous statements, broken links; everything) at the Ubuntu website, the more helpful thing to do (than ranting on forums) is to [file a bug report]("https://bugs.launchpad.net/ubuntu-website/+filebug") for them to be corrected.

---

### Post by graabein on 2009-11-07
> **23meg said:**
> Website bugs are [tracked on Launchpad]("https://bugs.launchpad.net/ubuntu-website/"), similar to Ubuntu bugs. When you encounter faults of any kind (typos, ambiguous statements, broken links; everything) at the Ubuntu website, the more helpful thing to do (than ranting on forums) is to [file a bug report]("https://bugs.launchpad.net/ubuntu-website/+filebug") for them to be corrected.

Good call. Making a bug known is important, but it's even more useful to let the right people know about it. ;)

---

