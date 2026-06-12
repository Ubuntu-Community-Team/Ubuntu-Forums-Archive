---
title: "3 days and no updates for Hardy?"
date: 2008-04-26
forum: Repositories &amp; Backports
---

### Post by Kilz on 2008-04-26
I installed the Hardy Release candidate before the actual release. Up to the 22nd I received updates daily. Now 3 days have passed and I have not had one update to a newly released operating system. I have checked multiple times a day, my sources.list is good, but no updates. Perhaps Hardy is perfect, but in my past experience at least a few updates happen within days of a release.

---

### Post by McDuff on 2008-04-26
must be perfect then... ;)

---

### Post by Kilz on 2008-04-26
> **McDuff said:**
> must be perfect then... ;)

Nope... while its quite usable, it still has a few minor things that could use tweaking by the developers.

---

### Post by Anduu on 2008-04-26
My guess is the devs are taking a well deserved break.

Cheers :)

---

### Post by Joeb454 on 2008-04-26
Expect some updates in a few weeks. I'd give the devs a break before they start working on updates :p

And on the 23rd the packages were frozen in order to build the disc images :) Just so you know why there was no updates :)

---

### Post by Kilz on 2008-04-26
> **Joeb454 said:**
> Expect some updates in a few weeks. I'd give the devs a break before they start working on updates :p

And on the 23rd the packages were frozen in order to build the disc images :) Just so you know why there was no updates :)

In a few weeks? I think by then a few dozen others will be screaming something is wrong because of no updates. Strangely, my Feisty partition has gotten some.

---

### Post by olskar on 2008-04-26
> **Kilz said:**
> Nope... while its quite usable, it still has a few minor things that could use tweaking by the developers.

Minor bugs wont be fixed. Only critical bugs and those about security will be.

---

### Post by Kilz on 2008-04-26
That may be true, but whats minor to me, may be critical or be a security flaw. I have one bug that stops the desktop starting every 10 or 11 tries. But that is off point. I have a feeling that this install still thinks it a release candidate and not the release.

---

### Post by jery_wang2002 on 2008-04-26
Still no update, 27 April 2008

---

### Post by FredB on 2008-04-26
Just wait. Updates will be there on time. No problems on my computer using hardy since its beta stage.

---

### Post by SunnyRabbiera on 2008-04-26
Yeh i definitely got to get a bug report in about the gnome terminal freezing on me, it needs to be done...

---

### Post by olskar on 2008-04-27
> **Kilz said:**
> That may be true, but whats minor to me, may be critical or be a security flaw. I have one bug that stops the desktop starting every 10 or 11 tries. But that is off point. I have a feeling that this install still thinks it a release candidate and not the release.

I agree with you on that one

---

### Post by ronacc on 2008-04-27
I suspect they are giving the mirrors a break , at release time they are jammed with people downloading the new image , adding a bunch of updates would bring things to a halt , wait a few days .

---

### Post by black3ug on 2008-04-27
+1

I understand about the devs needing a break, I do. But, a day is just no good when I only hit on coffee and not on *sudo apt-get upgrade*...can you understand that?

It's not like I'm addicted. It's like my body's developed this massive ***sudo apt-get upgrade*** deficiency.

:lolflag:

---

### Post by Eclipse. on 2008-04-27
Give the devs a break, theres normally a rush of updates all at the one time.There will be working on stuff for 8.04.1.

---

### Post by the8thstar on 2008-04-27
I've gotten so used to constant updates that I even check my Vista update every couple of hours now, just to hope to see something pop up in the window... That's addiction I say. :)

---

### Post by ssam on 2008-04-27
there is a feed of updates.
[http://feeds.ubuntu-nl.org/HardyChanges](http://feeds.ubuntu-nl.org/HardyChanges)

virtinst 0.300.2-0ubuntu6
xmms-crossfade 0.3.14-1build1

have been uploaded since the release.

remember that updates to the stable release go into hardy-proposed for testing before hitting hardy-updates. if you want you can enable hardy-proposed in software-sources.

---

### Post by Kilz on 2008-04-27
> **ssam said:**
> there is a feed of updates.
[http://feeds.ubuntu-nl.org/HardyChanges](http://feeds.ubuntu-nl.org/HardyChanges)

virtinst 0.300.2-0ubuntu6
xmms-crossfade 0.3.14-1build1

have been uploaded since the release.

remember that updates to the stable release go into hardy-proposed for testing before hitting hardy-updates. if you want you can enable hardy-proposed in software-sources.

Thanks for that link, it gives some good info and removes all the guesswork about what has been released.

---

### Post by Kilz on 2008-04-30
There have now been numerous updates to Hardy per the link a few posts up. Including gtk, hal and the update manage. To date I have had a whopping 0 updates. Something is wrong.

---

### Post by almostlinux on 2008-05-01
> **Kilz said:**
> There have now been numerous updates to Hardy per the link a few posts up. Including gtk, hal and the update manage. To date I have had a whopping 0 updates. Something is wrong.
hardy-proposed

---

### Post by Kilz on 2008-05-02
> **almostlinux said:**
> hardy-proposed

I dont want proposed packages, or pre release packages. What I am saying is that it has now been a week since release. Per post 17, [This page lists the following releases]("http://feeds.ubuntu-nl.org/HardyChanges")
1. The 23rd - 5 packages released
2. The 24th - 4 packages including the gnome file system and compiz plugins that I have installed.
3. The 25th and 26th 1 package released per day
4. The 28th 4 packages released including gtk that I know is installed for my Gnome desktop.
5. The 29th 17 packages released including evolution and the update manager that I know are installed on my system
6. The 30th 7 packages including hal, sudo, nautilus, gnome-desktop, and gnome-control-center that I know are installed on my system.
7. May 1st 6 updates including the linux kernel, linux-ubuntu-modules, update-manager that I know are installed on my system

7 days of releases, not one, and **I repeat not one update has shown** in the update manager, in the terminal, anyplace. I have checked multiple times a day, all repositories are enabled on my sources.list.

---

### Post by Kilz on 2008-05-02
I have filed a bug report on launchpad
[https://bugs.launchpad.net/ubuntu/+bug/225734](https://bugs.launchpad.net/ubuntu/+bug/225734)

---

### Post by jazz452 on 2008-05-03
It seems to me that software sources updates unchecked themselves.After i ticked proposed updates i got 82 updates.

---

### Post by ssam on 2008-05-03
the updates go into proposed-updates for testing before hitting the hardy-updates repo.

if you want to help testing the proposed updates, then enable the proposed repo, read the changelogs, expect occasional problems, and file bugs if you spot regressions.

---

### Post by Ayuthia on 2008-05-11
> **Kilz said:**
> I dont want proposed packages, or pre release packages. What I am saying is that it has now been a week since release. Per post 17, [This page lists the following releases]("http://feeds.ubuntu-nl.org/HardyChanges")
1. The 23rd - 5 packages released
2. The 24th - 4 packages including the gnome file system and compiz plugins that I have installed.
3. The 25th and 26th 1 package released per day
4. The 28th 4 packages released including gtk that I know is installed for my Gnome desktop.
5. The 29th 17 packages released including evolution and the update manager that I know are installed on my system
6. The 30th 7 packages including hal, sudo, nautilus, gnome-desktop, and gnome-control-center that I know are installed on my system.
7. May 1st 6 updates including the linux kernel, linux-ubuntu-modules, update-manager that I know are installed on my system

7 days of releases, not one, and **I repeat not one update has shown** in the update manager, in the terminal, anyplace. I have checked multiple times a day, all repositories are enabled on my sources.list.

Have you compared the packages in your package lists (/var/lib/apt/lists) with the repos(Example: [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-amd64)](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-amd64))?  I have received a few updates, but I have been waiting for 2.6.24-17 for awhile and I have not gotten it.  The package lists matches with the repos and the repos for main is listed at Apr 29.  I have finally viewed the package lists in hardy-proposed and have found that the package is still there.  It looks like the Hardy Changes link matches up with the proposed than the actual.

In short, I think that the packages that you are waiting for are still in proposed.  You might just take a look at the proposed package lists (example - [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-amd64/](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-amd64/)) and see if they match your list for post 17.

---

