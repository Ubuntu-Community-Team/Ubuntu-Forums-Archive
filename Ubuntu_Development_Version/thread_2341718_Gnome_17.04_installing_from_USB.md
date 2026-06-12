---
title: "Gnome 17.04 installing from USB"
date: 2016-10-30
forum: Ubuntu Development Version
---

### Post by bearlake on 2016-10-30
Tried a fresh (daily Oct 30) install of gnome 17.04 from a USB stick as it was 4 or 5 days since the last fresh install.

The install went from copying files to installing and then shortly after it started to look for media in the CD drive.

Double check the md5sum and so on and all was good.

Tried another USB stick with the same results.

Anyone try the latest Daily Gnome ISO or another Daily build ISO from another flavor?

---

### Post by VMC on 2016-10-31
I had the same issues using Xubuntu, installing from a live loopback iso. I'll wait a day or two, then try again with latest iso. launchpad didn't reveal much.

---

### Post by bearlake on 2016-10-31
> **VMC said:**
> I had the same issues using Xubuntu, installing from a live loopback iso. I'll wait a day or two, then try again with latest iso. launchpad didn't reveal much.

Thanks, at least it's a common problem between them.

---

### Post by jbicha on 2016-10-31
Does 16.10 have the same problem?

---

### Post by bearlake on 2016-10-31
> **jbicha said:**
> Does 16.10 have the same problem?

There is no more daily 16.10

I had no issues installing the final release and updating.

---

### Post by VMC on 2016-10-31
> **jbicha said:**
> Does 16.10 have the same problem?
No, just 17.04. Tried again today (10.31.16), same problem. I'll try and get info from ubiquity logs.

---

### Post by jbicha on 2016-10-31
[Bug 1637985]("https://launchpad.net/bugs/1637985") was filed about this issue.

---

### Post by VMC on 2016-10-31
> **jbicha said:**
> [Bug 1637985]("https://launchpad.net/bugs/1637985") was filed about this issue.
Thanks for the info. I did a general search on launchpad, but stopped short of package search. I "Yes, it affects me" the bug report.




On a side note, space bar doesn't work on "reply with quotes". Needed to edit in order to use space-bar.

---

### Post by bearlake on 2016-10-31
> **jbicha said:**
> [Bug 1637985]("https://launchpad.net/bugs/1637985") was filed about this issue.

Thanks for the update.

---

### Post by bearlake on 2016-11-01
Well after todays daily build we are back into testing.

Time to play.

---

### Post by VMC on 2016-11-01
Rather odd. I'm using xubuntu dated:
[zesty-desktop-amd64.iso]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/zesty-desktop-amd64.iso") 01-Nov-2016 02:28  1.2G"

Ubuntu is dated:
"[zesty-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/zesty-desktop-amd64.iso")[FONT=Verdana] 01-Nov-2016 16:09  1.5G"

Its at a later  time, but still the bug report is on "[/FONT]Fix Committed" and not "Fix Released".

Strange that yours works.

---

### Post by bearlake on 2016-11-01
Didn't try Xubuntu yet but do have room for it.

Gnome is working good with Nov 1st build.

I will not mark this as solved yet.

---

### Post by jbicha on 2016-11-01
> **VMC said:**
> [FONT=Verdana]
Its at a later  time, but still the bug report is on "[/FONT]Fix Committed" and not "Fix Released".

Strange that yours works.

Comment #12 on the bug says that iso's dated on or after **November 2** should work. iso's are usually only generated once per day and since the bug was fixed on November 1, it makes sense that some iso's would have already been built for the day by the time it was fixed.

---

### Post by VMC on 2016-11-02
Thanks jbicha. I just read note #12.

---

### Post by bearlake on 2016-11-02
Then it could be marked at solved then. Happy testing folks.

---

