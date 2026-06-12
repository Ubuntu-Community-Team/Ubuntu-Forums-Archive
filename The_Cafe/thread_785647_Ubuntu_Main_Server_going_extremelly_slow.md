---
title: "Ubuntu Main Server going extremelly slow"
date: 2008-05-07
forum: The Cafe
---

### Post by Kosimo on 2008-05-07
What's going on with Ubuntu Main servers?  They are really low performance from Catalonia. Anyone else is having extremely slow transfer rates when installing software or updates from main servers?

---

### Post by Half-Left on 2008-05-07
Yep, the simple way is just not to use them and pick another.

---

### Post by miwaypet on 2008-05-07
Try this. Go to Synaptic Package Manager>Settings>repositories.

This displays the Software Sources utility.

In the server box dropdown list select: other.

In new window look in upper right hand corner- click find best.

This will ping all available servers. It will find the best. Select it. Reload your sources. And it should be much faster.

Hope this helps.

---

### Post by eragon100 on 2008-05-07
Yeah from the Netherlands here. There are six servers for this tiny country. I picked ftp.tiscali.nl instead of the main server and it flies. Tiscali is an ISP which apparently houses ubuntu repo's :popcorn:

---

### Post by FuturePilot on 2008-05-07
The US ones are slow as well. Even timed out on me once. :|

---

### Post by MemoryDump on 2008-05-07
> **miwaypet said:**
> Try this. Go to Synaptic Package Manager>Settings>repositories.

This displays the Software Sources utility.

In the server box dropdown list select: other.

In new window look in upper right hand corner- click find best.

This will ping all available servers. It will find the best. Select it. Reload your sources. And it should be much faster.

Hope this helps.
I did this and it made a world of difference! Found another mirror faster than my previous one! woot

---

### Post by Kosimo on 2008-05-07
Looks like the problem is on Main and US servers.
Choosing servers from Barcelona everything works good again.

---

### Post by fredfjr on 2008-05-07
> **miwaypet said:**
> Try this. Go to Synaptic Package Manager>Settings>repositories.

This displays the Software Sources utility.

In the server box dropdown list select: other.

In new window look in upper right hand corner- click find best.

This will ping all available servers. It will find the best. Select it. Reload your sources. And it should be much faster.

Hope this helps.

I know I'm probably only being paranoid by asking this, but I guess it can't hurt to ask...

If I change my repository to something other than the main Ubuntu server will I get stuff like "Not Authenticated" warnings on updates and such?  I don't want to risk lowering my security and such for the sake of faster speeds.

---

### Post by sports fan Matt on 2008-05-07
The real question is WHY?  Why is the main server going slow?  WE are past the HH flip by a week or more

---

### Post by Foster Grant on 2008-05-07
> **miwaypet said:**
> Try this. Go to Synaptic Package Manager>Settings>repositories.

This displays the Software Sources utility.

In the server box dropdown list select: other.

In new window look in upper right hand corner- click find best.

This will ping all available servers. It will find the best. Select it. Reload your sources. And it should be much faster.

Hope this helps.

I did that, and it selected a mirror that was not working. Switched to the nearest one to my house (a university system) and things picked up immensely. :)

The Medibuntu archives are still horribly slow, though. I don't know of any mirrors for those repositories.

---

### Post by tubezninja on 2008-05-07
The HH flip happened 13 days ago, but within the past three days alone there's been update activity.  Compare that to the two weeks before the release of Hardy, where things were comparatively quiet.

I'm guessing it's just a case of everyone who's updated noticing the glitches here and there, inherent with a fresh major release.  People are checking for updates.  A lot.

---

### Post by FuturePilot on 2008-05-07
My guess is that there is a second wave of people installing/upgrading to Hardy. When Hardy was first released we had a whole lot of people upgrade right away. Now the people that decided to wait a while are probably upgrading.

---

### Post by Hooya on 2008-05-08
Damn, I picked the wrong day to do a fresh install (I had the release candidate from about a week before 8.04 was released).  I'll have to check that ping strategy mentioned above, but right now I'm blazing at a whopping 4000B/s (yeah, bytes/second).  Like being on a baud modem.

30 minutes just to install wine... good grief!

Glad it's not just me, I guess.

---

### Post by andrewabc on 2008-05-08
I noticed it was slow (but had latest release compared to other servers).
But I found some decent mirrors that were somewhat up to date.
Tyring to fin the xulrunner firefox update :P
And I found it on one of the mirror I used.

---

### Post by 23meg on 2008-05-08
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) is your friend.

---

