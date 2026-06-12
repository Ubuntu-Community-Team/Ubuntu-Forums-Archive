---
title: "Flaky machine died during update; now won't load OS"
date: 2010-03-16
forum: Ubuntu Studio
---

### Post by wizarddrummer on 2010-03-16
Hi,
I would have deleted this question if I could have. The more I think about it this is a question that I should have posted in the Install / Upgrade forum.

So I moved the question to that location.

I hope I have not angered anyone.

---

### Post by FatAngus on 2010-03-26
same thing has just happened to me - was okay after installation until I installed the updates, half way through updating, no mouse, no keyboard and a blank screen.

After turning of computer and switching it back on screen full of i/o errors, (sorry can't be more specific).  Could not load O/S.  Reinstalled Ubuntu for now.

---

### Post by wizarddrummer on 2010-03-26
> **FatAngus said:**
> same thing has just happened to me - was okay after installation until I installed the updates, half way through updating, no mouse, no keyboard and a blank screen.

After turning of computer and switching it back on screen full of i/o errors, (sorry can't be more specific).  Could not load O/S.  Reinstalled Ubuntu for now.

Thanks for the reply, sorry it too so long to thank you.

---

### Post by sgx on 2010-03-27
> **wizarddrummer said:**
> Thanks for the reply, sorry it too so long to thank you.
Hi, just a reminder to create a separate /home partition next time you install, then in future reinstalls  you choose not to format /home, and most of your configs will be intact when you restart. Musicians should not update very often, once recording and playback are stable, little can be gained musically from newer system files, and experts and their systems are prepared to test and report findings on behalf of us non-experts. :)
Hurray for the weekend!

---

### Post by wizarddrummer on 2010-03-28
> **sgx said:**
> Hi, just a reminder to create a separate /home partition next time you install, then in future reinstalls  you choose not to format /home, and most of your configs will be intact when you restart. Musicians should not update very often, once recording and playback are stable, little can be gained musically from newer system files, and experts and their systems are prepared to test and report findings on behalf of us non-experts. :)
Hurray for the weekend!

Here's my confusion factor.

Since I have started messing with Linux (about a month now) I have always created three separate physical partitions. /, /swap and /home (actually I'd like to use /usr instead of /home/. Will that mess anything up? Reason: in the terminal I keep reverting to /usr/bin or /usr/rjw because of my old Unix days in the 80's & 90's)

The problem I have experienced with reinstalling the OS is that when I go to reinstall the partitioner always makes me go through the process of defining my /home partition again. ie: telling it what kind file system is there, i have to retell it to use /home as a mount point and then tell it not to format it. 

Are there configuration files or anything else in my home folder that's necessary for the OS to run?

---

### Post by sgx on 2010-03-29
Hi, many important apps set up folders with contents allowing user control, instead of root.
.hydrogen
.qt (for qjackctl)
.mozilla
.wine

Lots of crucial textfiles are also there
.jackdrc
.basssh history
.dmrc
.fonts.conf
.gtkrc

All these can be kept intact, so your reconfiguration timewaste is minimal. Its good for partition software insure you know what you are getting.  preserving a well crafted /home may not be crucial, but it is a key feature lacking in windows, and since public linux distros will always be beta, its a security feature against the inevitable.

/usr/bin is like C:\Program Files, no point in giving it a mountpoint
on a partion as it gets nuked by a reinstall. A good thing would be to use a 2-drive system, OS on one, recording and large/streaming samples on the other, removing competition for platters and heads during recording and playback.
Terminal commands are mostly to run apps which usually are installed in
/usr/bin or /usr/sbin, can't change that by a partition scheme.

Its good luck to rename certain .folders in /home before reinstalling,
 I do so for
.opera, .hydrogen, and .wine, so  there is no chance of losing things
through a folder getting overwritten. For example, a new install
nukes wine, so  I rename .wine to OLDwine, and when the new .wine folder appears, I just overwrite its contents from OLDwine, so my Reaper, and vst collection fully reinstalls by simply drag/drop.

Makes life just that much easier
;)  Cheers

---

