---
title: "When will MPlayer have an updated version in the  repos ?"
date: 2009-05-15
forum: The Cafe
---

### Post by Regenweald on 2009-05-15
Even after building my last one from SVN, SMPlayer said it was an older version. There was a great tutorial over in the Karmic testing area, but that included adding extra repos which I am not too keen on.

I've tried researching but have not really gotten any concrete info, i know that the repos have quality/compatibility/stability standards to be met but I'd just like an idea when we'll have a better version than rc2 in the repos. If at all.

---

### Post by yabbadabbadont on 2009-05-15
New versions generally only appear with a new release of the OS.  Sometimes the version will be updated if that is the only way to fix a security issue.  The only other possible way to get a new version from the official repositories, is to enable the backports repo, but that doesn't guarantee that you'll see a new version of any specific application.

---

### Post by Regenweald on 2009-05-15
I have the backports enabled, I will check further on MPlayers site, maybe shoot the devs a message. Really just want to understand why the repo version hasn't been updated in a while.

---

### Post by rvm4000 on 2009-05-15
> **Regenweald said:**
> Even after building my last one from SVN, SMPlayer said it was an older version.

If smplayer says that maybe it's still using the old version. I guess you have two mplayers installed, the 1.0rc2 (installed in /usr/bin) and the svn one, probably installed in /usr/local/bin. Adjust the path in the smplayer's preferences.

---

### Post by andrew.46 on 2009-05-15
Hi Regenweald,

> **Regenweald said:**
> Even after building my last one from SVN, SMPlayer said it was an older version. There was a great tutorial over in the Karmic testing area, but that included adding extra repos which I am not too keen on.

Do you mean the guide that formerly was in the *Jaunty* testing area?

> I've tried researching but have not really gotten any concrete info, i know that the repos have quality/compatibility/stability standards to be met but I'd just like an idea when we'll have a better version than rc2 in the repos. If at all.

I believe the Ubuntu devs will stay with the outdated rc2 until rc3 is released. This has less to do with quality and stability and more to do with their attitude towards 'release' versions.

Andrew

---

### Post by sertse on 2009-05-15
> **andrew.46 said:**
> and more to do with their attitude towards 'release' versions.

This.

Even though mplayer has repeatedly said they aren't into the habit of releases and recommmends people check out of svn. See the problem? :)

The simpliest advice is to add Medibuntu

---

### Post by 23meg on 2009-05-15
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by Regenweald on 2009-05-16
Thanks so much for the info. Something so simple as changing the relevant path....
I will build the SVN again. 

Thanks rvm4000 for a great front end, it's all i use now.

---

### Post by FuturePilot on 2009-05-16
It has to do with the fact that Mplayer doesn't frequently make releases. 

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453")

---

### Post by andrew.46 on 2009-05-16
Hi FuturePilot,

> **FuturePilot said:**
> It has to do with the fact that Mplayer doesn't frequently make releases. 

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453")

Interesting reading :-). But this argument has been going around and around for a *looooooooong* time! I guess the good news is that are several methods of getting a newer MPlayer on a personal level (PPAs, svn guides etc) even if the stock MPlayer is not moving. It is a great pity though.

I note the developer of the Gnome-MPlayer in that discussion calling for upgrade as well.

Andrew

---

### Post by Regenweald on 2009-05-16
> **FuturePilot said:**
> It has to do with the fact that Mplayer doesn't frequently make releases. 

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/243453)

Having read it, i do not see why a new version is not in the repos. One updated version could last us another year? year and a half ? :)
But as i said, SVN does not scare me so i shall have the latest version again shortly.

Edit: Just added the Mplayer and SMPlayer pps' courtesy of RVM. So i'm a bit lazy, but it's 2:06am and compiling would have meant a load of dev packages...oog :)

---

### Post by Regenweald on 2009-06-18
Just an Update, It would seem that the latest version of Mplayer has hit the Karmic repos. So Jaunty guys have something to look forward to. Works beautifully.

---

### Post by andrew.46 on 2009-06-19
Hi Regenweald,

> **Regenweald said:**
> Just an Update, It would seem that the latest version of Mplayer has hit the Karmic repos. So Jaunty guys have something to look forward to. Works beautifully.

They are tracking the rc3 svn branch of MPlayer so hopefully the whole process will not stall when rc3 actually arrives. But I agree it is a good move!

Andrew

---

