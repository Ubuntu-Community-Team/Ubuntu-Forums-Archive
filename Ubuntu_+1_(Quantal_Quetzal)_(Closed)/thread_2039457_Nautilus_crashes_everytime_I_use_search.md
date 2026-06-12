---
title: "Nautilus crashes everytime I use search"
date: 2012-08-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GreatDanton on 2012-08-08
I was searching for hidden directory (.fonts), and everytime I used this function Nautilus crashed. I tried same thing for couple of times and Nautilus crash every time.

I report a bug via Apport. Here is the link: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1034720](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1034720)

One strange thing I noticed from Apport retracing service (at the bottom of the page). They said this is the duplicate of bug and provide some link, however if I click on link I get this message: Bug 1034548 cannot be found.

I am not familiar with Bug reporting (I have read Ubuntu documentation) so maybe this is normal thing.

Any explanation?

Regards.
[]("https://launchpad.net/%7Eapport")

---

### Post by dino99 on 2012-08-08
**Bug 1034548 cannot be found.**

might be due to its private status

---

### Post by mc4man on 2012-08-09
I think that in 3.5.4 searching a . file nautilus would return no results. If so then in 3.5.5 when no results are returned nautilus now crashes.

*easy to test - create a folder with 1 file in it. Open that folder & search using letters **not** in the file name. - nautilus should crash

upstream bug
[https://bugzilla.gnome.org/show_bug.cgi?id=681479](https://bugzilla.gnome.org/show_bug.cgi?id=681479)

---

### Post by GreatDanton on 2012-08-09
> **mc4man said:**
> I think that in 3.5.4 searching a . file nautilus would return no results. If so then in 3.5.5 when no results are returned nautilus now crashes.

*easy to test - create a folder with 1 file in it. Open that folder & search using letters **not** in the file name. - nautilus should crash

upstream bug
[https://bugzilla.gnome.org/show_bug.cgi?id=681479](https://bugzilla.gnome.org/show_bug.cgi?id=681479)


+1. It's really like you said. It's seems after I filled bug report there are no more new messages from apport.

---

### Post by balloons on 2012-08-09
Same issues here, but seems to be fixed in the new version -- course search doesn't seem to work, hah!, but it doesn't crash

---

### Post by mc4man on 2012-08-09
> **guitara said:**
> Same issues here, but seems to be fixed in the new version -- course search doesn't seem to work, hah!, but it doesn't crash

There was a quick update today to stop the segfault on no results
> nautilus (1:3.5.5-0ubuntu2) quantal; urgency=low

  * debian/patches/git_no_empty_search_segfault.patch:
    - don't segfault when a search returns no result (lp: #1034548)

 -- Sebastien Bacher <seb128@ubuntu.com>  Thu, 09 Aug 2012 13:47:01 +0200
So as far as . files one would be back to 3.5.5 doesn't search them

To some extent may be mooted as per a number of mails today it seems quite likely 12.10 will default to naut 3.4.x & make 3.6 available.
If so then 3.4 does search . files but only in current dir.

---

