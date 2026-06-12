---
title: "Gutsy imminent release vs open bugs in Launchpad"
date: 2007-10-17
forum: The Cafe
---

### Post by zugu on 2007-10-17
At the time of this post, there were 30 bugs open in Launchpad for Ubuntu Gutsy.

[https://bugs.launchpad.net/ubuntu/gutsy/+bugs](https://bugs.launchpad.net/ubuntu/gutsy/+bugs)

Ubuntu.com says there's 1 day left until the final release. What if those bugs are not closed in time? Will it delay the release? Will Gutsy be released with open bugs in the bug tracker?

---

### Post by Druke on 2007-10-17
IIRC they'll just release the bug fixes in the update manager

---

### Post by bobbocanfly on 2007-10-17
It will probably be released, but those bugs will hopefully be fixed in the first couple of updates that come out. Like the top one is in progress, so the fix being included is doubtful, but it should be released in the first updates.

---

### Post by chrisccoulson on 2007-10-17
These are only the bugs that people have nominated for Gutsy aren't they? AFAIK, there are many more open bugs that people testing Gutsy have raised. They just haven't been nominated for any particular release

---

### Post by zugu on 2007-10-17
I think the bug list returned by my link reveals only the Gutsy bugs marked as "release critical".

So I assume they have the greatest priority and they are the first to be fixed, but since they're release critical, shouldn't the release be postponed until they're closed and done with?

Will we have a release sent out in the wild with "release critical" bugs in it, just for the sake of meeting a deadline? Surely, they can modify the release date, just as they did with Dapper.

---

### Post by FredB on 2007-10-17
I  think this list is more "useful" :

[https://bugs.launchpad.net/ubuntu/+milestone/ubuntu-7.10/](https://bugs.launchpad.net/ubuntu/+milestone/ubuntu-7.10/)

"Milestone ubuntu-7.10 for Ubuntu due 2007-10-18"

25 bugs.

Opened ? 4. All others are closed. So...

And if you want list of bugs for updates :

[https://bugs.launchpad.net/ubuntu/+milestone/gutsy-updates](https://bugs.launchpad.net/ubuntu/+milestone/gutsy-updates)

22. And half are already closed !

---

### Post by zugu on 2007-10-17
> **FredB said:**
> 30 ? But I can see at least 2 fixed. 
Somewhat irrelevant, yesterday nearly all of them had "fix committed" status so it seems the initial fixes didn't work.

As for blockers, check [this]("https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193") out and tell me it's not a blocker.

So my question still stands: if such "critical" and "blocker" bugs are still standing, will the release be postponed or it will be shipped as if nothing had happened?

Update: it seems yesterday I was looking at the list FredB provided. Nonetheless, I have to notice the difference between Debian and Ubuntu concerning the release policy. Debian releases when ALL the bugs are closed. Ubuntu seems to be shipping with open bugs just to meet some deadline. Why not postpone for a few days in order to fix the existing bugs?

---

### Post by samjh on 2007-10-17
Looks pretty similar to how Feisty and Edgy releases were just prior to their release dates.

---

### Post by undine on 2007-10-17
Yeah there's a bit of a showstopper right now for people who are using Ndiswrapper for their NIC. Heavy network activity, i.e moving files from one machine to another on a LAN, causes a kernel panic.

---

### Post by Druke on 2007-10-17
> **undine said:**
> Yeah there's a bit of a showstopper right now for people who are using Ndiswrapper for their NIC. Heavy network activity, i.e moving files from one machine to another on a LAN, causes a kernel panic.

whoa didn't see that, I'll hold off on my laptop.

---

### Post by Tomosaur on 2007-10-17
This is just how it goes - first release ALWAYS has bugs. If your system is currently working fine, just don't upgrade for a while. For the majority of people, upgrading on release of gutsy should be fine. For some, it may not. If you want to ensure your upgrade goes well, just hold off for a while.

---

### Post by zugu on 2007-10-17
It's wrong. Of course, it's because of the 6 months release policy. I won't challenge that, but consider this:

#1 - every piece of software has bugs, it's just a matter of bugs that are at least known and bugs that will be submitted after the release.
#2 - the final release comes after release candidates that come after betas that come after alfas and so on; this model is used in order to make sure the final release will be bug-free (at least at the moment of the release - see #1).

If the final release has bugs that are still open, it's plain wrong. 

People who want to keep their systems stable shouldn't be asked to refrain from upgrading to the final release. That piece of advice should be kept for betas and release candidates. Otherwise, it's just like Microsoft rushing Vista out in the wild just because it was high time they released another iteration of their crippled operating system.

The last comparison is more or less out of scale, but the idea is the same.

---

### Post by Obor on 2007-10-17
> **zugu said:**
> It's wrong. Of course, it's because of the 6 months release policy. I won't challenge that, but consider this:

#1 - every piece of software has bugs, it's just a matter of bugs that are at least known and bugs that will be submitted after the release.
#2 - the final release comes after release candidates that come after betas that come after alfas and so on; this model is used in order to make sure the final release will be bug-free (at least at the moment of the release - see #1).

If the final release has bugs that are still open, it's plain wrong. 

People who want to keep their systems stable shouldn't be asked to refrain from upgrading to the final release. That piece of advice should be kept for betas and release candidates. Otherwise, it's just like Microsoft rushing Vista out in the wild just because it was high time they released another iteration of their crippled operating system.

The last comparison is more or less out of scale, but the idea is the same.

Ubuntu chose to follow the time based release and unfortunately it means that we sometime get stuff with know bugs (and a lot of unknown) in order to get the knew version our on time.
I think those that want to avoid this can upgrade from one LTS version to another one, which would be postponed if the are any know bugs. I chose to upgrade every 6 moths but about one week after the big date. 

I think they are trying to improve their testing schedule to be more in  line we the amount of time they need for bug fixing. 

Not a lot of people test the beta version and there is a lot of bugs that get fixed in the first few days after the final release. Well, I guess its the price we have to pay we leaving close to the edge :)  It works for me :)

---

### Post by Tomosaur on 2007-10-17
> **zugu said:**
> It's wrong. Of course, it's because of the 6 months release policy. I won't challenge that, but consider this:

#1 - every piece of software has bugs, it's just a matter of bugs that are at least known and bugs that will be submitted after the release.
#2 - the final release comes after release candidates that come after betas that come after alfas and so on; this model is used in order to make sure the final release will be bug-free (at least at the moment of the release - see #1).

If the final release has bugs that are still open, it's plain wrong. 

People who want to keep their systems stable shouldn't be asked to refrain from upgrading to the final release. That piece of advice should be kept for betas and release candidates. Otherwise, it's just like Microsoft rushing Vista out in the wild just because it was high time they released another iteration of their crippled operating system.

The last comparison is more or less out of scale, but the idea is the same.

The only reason Gutsy is getting released as it is, is because there is a 6-month release cycle precedent. Warty Warthog was so named because it was decided that it should be released 'warts and all'. There are always known issues, some are show-stoppers for some people. By the same token as you suggest above - why should the people who aren't affected by such bugs be stopped from upgrading? Surely it's better to release Gutsy to those who want it (and you should understand that while for most individual users, the release date is neither here nor there - but for other groups of users, they have timetabled around the current date.), while those who have fears about it can just wait a little while for the show-stopper bugs to be fixed.

At the end of the day, nobody forces anybody to upgrade - if you want to, go for it, but be prepared for issues. If you don't want to, then don't. It's as simple as that, but the release should go ahead as planned.

---

### Post by FredB on 2007-10-17
> **zugu said:**
> Somewhat irrelevant, yesterday nearly all of them had "fix committed" status so it seems the initial fixes didn't work.

As for blockers, check [this]("https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193") out and tell me it's not a blocker.

It says "fix commited". So, it looks like to be fixed, isn't it ?

> So my question still stands: if such "critical" and "blocker" bugs are still standing, will the release be postponed or it will be shipped as if nothing had happened?

Just ask that to ubuntu coders.

> Update: it seems yesterday I was looking at the list FredB provided. Nonetheless, I have to notice the difference between Debian and Ubuntu concerning the release policy. Debian releases when ALL the bugs are closed. Ubuntu seems to be shipping with open bugs just to meet some deadline. Why not postpone for a few days in order to fix the existing bugs?

Just ask that to ubuntu coders.

My gutsy works perfectly. And it could be the same for a lot of people.

---

### Post by undine on 2007-10-17
> **Obor said:**
> Ubuntu chose to follow the time based release and unfortunately it means that we sometime get stuff with know bugs (and a lot of unknown) in order to get the knew version our on time.
I think those that want to avoid this can upgrade from one LTS version to another one, which would be postponed if the are any know bugs. I chose to upgrade every 6 moths but about one week after the big date. 

I think they are trying to improve their testing schedule to be more in  line we the amount of time they need for bug fixing. 

Not a lot of people test the beta version and there is a lot of bugs that get fixed in the first few days after the final release. Well, I guess its the price we have to pay we leaving close to the edge :)  It works for me :)

Me too :) I always test the development versions; and even when I encounter the sort of show-stoppers I mentioned in my previous post, it doesn't ruffle me too much... I work around it.

---

### Post by Flyingjester on 2007-10-17
I know I haven't been here long, but I would think that if they always postponed the date of a release untill all known bugs were squashed then we would be using utterly obsolete software. Software will always have bugs, like it was mentioned before, in order to have the newer versions of software you have to deal with a few. As far as i see it, that's what the LTS versions are for.... those get most of the bugs ironed out, as it can be tweaked and modified longer to make it run that way.

---

### Post by Depressed Man on 2007-10-17
> **Tomosaur said:**
> The only reason Gutsy is getting released as it is, is because there is a 6-month release cycle precedent. Warty Warthog was so named because it was decided that it should be released 'warts and all'. There are always known issues, some are show-stoppers for some people. By the same token as you suggest above - why should the people who aren't affected by such bugs be stopped from upgrading? Surely it's better to release Gutsy to those who want it (and you should understand that while for most individual users, the release date is neither here nor there - but for other groups of users, they have timetabled around the current date.), while those who have fears about it can just wait a little while for the show-stopper bugs to be fixed.

At the end of the day, nobody forces anybody to upgrade - if you want to, go for it, but be prepared for issues. If you don't want to, then don't. It's as simple as that, but the release should go ahead as planned.

Would that mean Feisty Fawn because a Feisty system gives you issue and Gutsy Gibbon with strong gust issues?:confused:

---

### Post by Tomosaur on 2007-10-17
> **Depressed Man said:**
> Would that mean Feisty Fawn because a Feisty system gives you issue and Gutsy Gibbon with strong gust issues?:confused:

Actually not too far off - if I remember correctly Edgy Eft was so-called because it was mildly unstable, same deal with Feisty.

Gutsy I think is one of those with just a silly name, but I like to think of it as gutsy in terms of pushing ahead - 'it's got guts!'.

---

