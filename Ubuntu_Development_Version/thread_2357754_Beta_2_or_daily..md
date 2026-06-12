---
title: "Beta 2 or daily."
date: 2017-04-05
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-04-05
Should I use the beta 2 iso or today's daily iso?

Henry

---

### Post by terry_gardener on 2017-04-05
shouldn't actually matter which you choose as when you update them they will actually be the same.

---

### Post by Hewjr100 on 2017-04-05
Ok thanks.

Henry

---

### Post by ajgreeny on 2017-04-05
Just be careful if you choose the daily iso as you may find that, as in the daily isos of 16.04, the proposed repos are enabled by default, not something that is generally thought to be a good idea.

The entry for proposed repos in software-sources is also in **/etc/apt/sources.list.d** not in the main sources.list file and can not be disabled in the usual way in the **Developer Options** tab of software sources.  I was caught by this when I installed 16.04 back in Nov 2016 and it took me a while to figure out the reason for those proposed repos being enabled, and once I knew they were, how to disable them.  I started a thread in the forum about this at [https://ubuntuforums.org/showthread.php?t=2346590](https://ubuntuforums.org/showthread.php?t=2346590)

---

### Post by howefield on 2017-04-05
> **ajgreeny said:**
> Just be careful if you choose the daily iso as you may find that, as in the daily isos of 16.04, the proposed repos are enabled by default, not something that is generally thought to be a good idea.

Which iso image does this ?

I've installed many of the vanilla Ubuntu daily iso from "pending" and haven't experienced the proposed repository being enabled by default. Can you give me a link and I'll try it out later.

---

### Post by ajgreeny on 2017-04-05
It's not easy to give you the link I used for the specific daily iso file, other than the usual daily cd iso address of [http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/pending/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/pending/xenial-desktop-amd64.iso.zsync) (I zsynced a previous iso to the latest daily at the time back in Nov last year).

That will now give you a different iso image, of course.  However, I also installed Lubuntu to an old netbook in Feb this year, again using a pending daily iso,  and had exactly the same situation of proposed repos being enabled after installation.

Not anything more I can think of to tell you about this, but having happened twice to me I wanted to warn the OP of this thread. Perhaps he will not see the same problem, but I have no idea why I did if he does not suffer in the same way.

---

### Post by howefield on 2017-04-06
> **ajgreeny said:**
> It's not easy to give you the link I used for the specific daily iso file, other than the usual daily cd iso address of [http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/pending/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/pending/xenial-desktop-amd64.iso.zsync).

Cool, I'll try the xubuntu daily later on today. May be different for flavours than it is for vanilla Ubuntu but I doubt it.

---

### Post by lysander6662 on 2017-04-06
RC is due today.

[https://wiki.ubuntu.com/ZestyZapus/ReleaseSchedule](https://wiki.ubuntu.com/ZestyZapus/ReleaseSchedule)

---

### Post by cariboo on 2017-04-06
I just did a fresh install of Xubuntu, due to changing from a HDD to an SSD, proposed was not enabled.

---

### Post by #&amp;thj^% on 2017-04-06
> **cariboo said:**
> I just did a fresh install of Xubuntu, due to changing from a HDD to an SSD, proposed was not enabled.

+1....I have never had that happen "proposed was enabled  by default"
I still think it was ajgreeny's Avatar ** “snuck” **in and enabled it...that's my story and I'M STICKING TO IT..:P

---

