---
title: "no zsync updates since friday"
date: 2014-09-10
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-09-10
utopic-desktop-amd64.iso has not changed since Friday.

Just making a note.

---

### Post by Elfy on 2014-09-10
You sure - I had to check Ubuntu for the lightdm/framebuffer issue - needed to sync yesterday, today's is Read utopic-desktop-amd64.iso. Target 84.4% complete.

---

### Post by ventrical on 2014-09-10
> **Elfy said:**
> You sure - I had to check Ubuntu for the lightdm/framebuffer issue - needed to sync yesterday, today's is Read utopic-desktop-amd64.iso. Target 84.4% complete.


 I got 100% and it bumped me. Says Friday. Will try again.

---

### Post by ventrical on 2014-09-10
nada...must be carfunkled at my end...

```

dale@dale-desktop:~/Desktop$ zsync -i ./utopic-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso.zsync
#################### 100.0% 215.7 kBps DONE     

reading seed file ./utopic-desktop-amd64.iso: ******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read ./utopic-desktop-amd64.iso. Target 100.0% complete.      ******************
reading seed file utopic-desktop-amd64.iso: ********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read utopic-desktop-amd64.iso. Target 100.0% complete.      ******************
verifying download...checksum matches OK
used 1154236416 local, fetched 0
dale@dale-desktop:~/Desktop$ 

```

---

### Post by howefield on 2014-09-10
The iso.qa.ubuntu.com image is dated today.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) is from Friday.

---

### Post by jerrylamos on 2014-09-10
> **howefield said:**
> The iso.qa.ubuntu.com image is dated today.

This post is 10 September.  Daily build says:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
utopic-desktop-amd64.iso           05-Sep-2014 08:58  1.1G  Desktop image for 64-bit PC (AMD64) computers (standard download)

I zsync'd it, booted as old 3.16.0-12.  Did apt-get update and dist-upgrade to 3.14.0-14.  Therefore as of 10 September, the "daily build" amd64 is 5 days old.  In past ths was because development didn't think the daily build was ready yet.

In dailylive/pending there is a 10 September amd64.  Pending usually means hasn't run or hasn't passed the automatic tests.....in fact I've had pending .iso's crash.  I'm waiting...

---

### Post by grahammechanical on 2014-09-10
Have you also noticed that until today updates were thin on the ground?

The other day I was listening in to a Ubuntu Engineering update on Ubuntu On Air and someone was going on about all the improvements to Ubuntu phones/tablets but that they had not got into the daily images or the update channel because of a Jenkins outage. Whatever Jenkins is.

---

### Post by cariboo on 2014-09-10
> **grahammechanical said:**
> Whatever Jenkins is.

A little about jenkins [here]("https://launchpad.net/jenkins")

---

### Post by jerrylamos on 2014-09-10
Well, "daily-live/pending" amd64 .iso did boot, compiz/unity and all, installed clean, first .iso since 7/31 to do so on this Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2

Let the user beware of the "pending".  It's at 3.16.0-14 vs. the "current" still back at 3.16.0-12 on which compiz doesn't like this hardware.

Wonder what changes are pending for pending...

---

### Post by jerrylamos on 2014-09-11
Daily-live current is now marked today, 11 September.  Zsync compared 82% to yesterday's daily-live pending.

The amd64.iso booted normally on this Intel Core 2 Duo, first time the daily-live current amd64 .iso has run normally since July.  
My now long standing bugs aren't reproducible now ubuntu/unity off and running, 

Beware the next dread update.....

---

### Post by ventrical on 2014-09-12
> **jerrylamos said:**
> This post is 10 September.  Daily build says:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
utopic-desktop-amd64.iso           05-Sep-2014 08:58  1.1G  Desktop image for 64-bit PC (AMD64) computers (standard download)

I zsync'd it, booted as old 3.16.0-12.  Did apt-get update and dist-upgrade to 3.14.0-14.  Therefore as of 10 September, the "daily build" amd64 is 5 days old.  In past ths was because development didn't think the daily build was ready yet.

In dailylive/pending there is a 10 September amd64.  Pending usually means hasn't run or hasn't passed the automatic tests.....in fact I've had pending .iso's crash.  I'm waiting...

Jerry,

Thanks for confirmation.

---

### Post by ventrical on 2014-09-12
> **jerrylamos said:**
> Daily-live current is now marked today, 11 September.  Zsync compared 82% to yesterday's daily-live pending.

The amd64.iso booted normally on this Intel Core 2 Duo, first time the daily-live current amd64 .iso has run normally since July.  
My now long standing bugs aren't reproducible now ubuntu/unity off and running, 

Beware the next dread update.....

Ok.. will keep checking in..

---

### Post by ventrical on 2014-09-13
Yep .. it finally zsynced.

---

