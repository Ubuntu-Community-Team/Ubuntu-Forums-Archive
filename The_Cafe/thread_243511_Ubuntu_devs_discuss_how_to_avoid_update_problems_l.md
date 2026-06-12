---
title: "Ubuntu devs discuss how to avoid update problems like last recent X update"
date: 2006-08-25
forum: The Cafe
---

### Post by matthew on 2006-08-25
Note (to prevent certain questions I can't answer): I am not a part of the distro team, I just noticed and thought I would share the article.

[http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html](http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html)

From the article:> Incidentially, the distro team is currently in a sprint in Wiesbaden, Germany and we had a large discussion this morning about both how to handle such situations when they happen (and recover from them, mostly in the technical sense) and how to prevent them from happening in the first place.  The latter is obviously more important as we won't have to recover if there is not a problem in the first place.  Note that those ideas listed below were ideas and not finished procedures and we are going to write up a proper policy document.

---

### Post by OffHand on 2006-08-25
This part is really disturbing. Only 1 guy that decides what is getting into the repos. Asking for trouble if you ask me. I am surprised it didn't happen before.

> The current review process for updates to $distro-updates is a review by the release manager who accepts it into $distro-updates. This update passed that review even though the update was faulty

---

### Post by The Pinny Parlour on 2006-08-25
Yes, that is scary.   One person it does appear to be.

Great link matthew, cheers.  :)

---

### Post by monktbd on 2006-08-25
From the atricle:

> Ideas for prevention ranged form using $distro-proposed and explicit call for testers of that to getting more code review for updates. [...] Using $distro-proposed does not prevent the problem from affecting anybody, it just changes the group affected with the goal that the group choosing to enable $distro-proposed will hopefully be able to recover more easily.

I think this would be a good idea.

Proposition:
The current $disto-upgrades should be turned into $distro-proposed. After 24 hours all $distro-proposed packages will go to $distro-upgrades unless feedback indicates a problem.

Like this proficient users can have their - usually rock stable - updates immediately while less proficient ones can be safe by waiting 24 hours longer.

I myself do not mind a second being a tester with $distro-proposed. 

Probably that proposition has a few flaws that need to be adressed (e.g. very critical security updates, etc..).

---

### Post by greggh on 2006-08-25
> We all agreed that being open about the problem, the cause of the problem and how we are working to solve it is important.

Glad to hear it.

---

### Post by TravisNewman on 2006-08-25
At least they've finally said something about it. It was almost eerie how quiet they'd been the past couple of days.

Good ideas.

---

### Post by prizrak on 2006-08-25
Things are going to break that is inevitable. I do wish there was a rollback option in Synaptic. Especially for those of us who like to play with stuff I got a bunch of libraries that are much newer than Ubuntu's but are also much more unstable, that I can't get rid of because Synaptic thinks that newer is better.

---

### Post by Christmas on 2006-08-25
If the updates will get in the repositories after 24 hours, that means fast security updates won't be available immediately but only after at least one day. This is also not a very good way of updating but unfortunately there is no perfect method.

---

### Post by Christmas on 2006-08-25
[quote=prizrak]Things are going to break that is inevitable. I do wish there was a rollback option in Synaptic.[/quote]
Even if it was, being able to only use the CLI would not allow one to run Synaptic. And if there would be a CLI rollback option, it won't help the newbie much, as one who knows it will most likely know how to install the previous stable xserver-xorg-core driver I guess.

---

### Post by matthew on 2006-08-25
> **prizrak said:**
> Things are going to break that is inevitable. I do wish there was a rollback option in Synaptic. Especially for those of us who like to play with stuff I got a bunch of libraries that are much newer than Ubuntu's but are also much more unstable, that I can't get rid of because Synaptic thinks that newer is better.That option does exist. Highlight the package you want to downgrade and take a look at Package->Force Version. If more than one version is available in the various repos you have enabled they will all be listed there and you can choose which one you want. You can even force Synaptic to stick a specific version if you don't want it upgraded ever.

EDIT: I read your post to mean "having the ability to roll back a specific package." I realize that you may have meant "having the ability to roll the entire install back to a certain snapshot taken at a specific moment in time" in which case my comments do not apply. :)

---

### Post by RAV TUX on 2006-08-25
> **prizrak said:**
> Things are going to break that is inevitable. I do wish there was a rollback option in Synaptic. Especially for those of us who like to play with stuff I got a bunch of libraries that are much newer than Ubuntu's but are also much more unstable, that I can't get rid of because Synaptic thinks that newer is better.

Sort of like a restore date to an earlier time like with Windows?

It would be a great idea...

I would like a "burn current setup as is" function....at any given time I could burn a backup CD image, this would be very helpful if the system crashed, also. I could install my pre-configured Ubuntu to any other computer....or better yet nest to a USB pen drive....hmm?

---

### Post by prizrak on 2006-08-25
> **matthew said:**
> That option does exist. Highlight the package you want to downgrade and take a look at Package->Force Version. If more than one version is available in the various repos you have enabled they will all be listed there and you can choose which one you want. You can even force Synaptic to stick a specific version if you don't want it upgraded ever.

EDIT: I read your post to mean "having the ability to roll back a specific package." I realize that you may have meant "having the ability to roll the entire install back to a certain snapshot taken at a specific moment in time" in which case my comments do not apply. :)

Both are pretty helpful :) Thanks for the info by the way that really needs to make it into the Ubuntu guide. Not the most obvious of options. Also it will attempt to remove some other stuff but that can be unchecked later. 

> Even if it was, being able to only use the CLI would not allow one to run Synaptic. And if there would be a CLI rollback option, it won't help the newbie much, as one who knows it will most likely know how to install the previous stable xserver-xorg-core driver I guess.
If I understand correctly Synaptic is simply a GUI front end for apt-get so both would be able to do it. I do normally mean both GUI and CLI having the option as Linux w/o CLI is not even an OS.

---

### Post by The Pinny Parlour on 2006-08-25
matthew,  do you have anymore rambling from the dev's about this situation?

---

### Post by professor_chaos on 2006-08-25
> **prizrak said:**
> Things are going to break that is inevitable. I do wish there was a rollback option in Synaptic. Especially for those of us who like to play with stuff I got a bunch of libraries that are much newer than Ubuntu's but are also much more unstable, that I can't get rid of because Synaptic thinks that newer is better.

I second this!!! A simple rollback option would be a GREAT idea. 

Screw your system and then just press ctrl+z and all is good again.   :)

---

### Post by matthew on 2006-08-26
> **The Pinny Parlour said:**
> matthew,  do you have anymore rambling from the dev's about this situation?This is all I have heard so far. If/when I hear more I'll add it here.

---

### Post by matthew on 2006-08-27
> **The Pinny Parlour said:**
> matthew,  do you have anymore rambling from the dev's about this situation?I've found some more (Mark Shuttleworth himself has responded publicly) and I started a new thread about it...here's that new thread: [http://ubuntuforums.org/showthread.php?p=1428609](http://ubuntuforums.org/showthread.php?p=1428609)

---

### Post by jnuneziglesias on 2006-09-10
I absolutely second the motion to have rollback in synaptic! You could keep a small cache of recent updates. 500MB-1GB of spare disk space is available for most people these days, and it should be more than enough to roll back the latest update, which is what is most needed (a long history is nice but not essential).

I use XGL/Compiz, and as some of you may know the latest update nearly gave us all a heart attack. A quick rollback to pre-last update would have been perfect.

I also second the motion for a system backup utility! Saving the entire system to a CD, DVD, or a network or USB drive would be heaven -- no more fear of updates!

Anyway, I really hope this gets addressed with the next dist-upgrade!

!! Juan.

---

