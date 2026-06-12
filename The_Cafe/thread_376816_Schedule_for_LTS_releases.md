---
title: "Schedule for LTS releases?"
date: 2007-03-05
forum: The Cafe
---

### Post by sbergman27 on 2007-03-05
Hello all,

I come from a RedHat/Fedora/CentOS going back to about 1996.  (Actually, SCO Unix and AT&T Unix 386 before that, so really more like 1988.)

But I have been using Ubuntu on my own desktop and notebook now for about a year.

After much consideration, I have pretty much decided to start migrating my customers over to Ubuntu.  Much of what I do is serving XDMCP sessions to X thin clients, so Ubuntu would fit in quite nicely.

I have two questions, though.  What is the schedule for the release of LTS versions of Ubuntu?

My impression is that the goals for the next release are more or less made as we go, and that there is no long term schedule for LTS releases.  Ideal for me (and, I would think, many others) would be every 3rd release, or 18 months between LTS releases.  24 months would really be a bit too long, I think, for a desktop server, as I have discovered with CentOS.

My other question is about the difference between Ubuntu desktop and server.  For political reasons, it is easier for me to pitch Ubuntu Server to clients.  However, what I *really* want for them is Ubuntu Desktop.  If I install Ubuntu Server, what is involved in pulling all the desktop niceties into my server installation?  Is it as simple as installing the Ubuntu-Desktop package?

Thanks for any feedback.

-Steve Bergman

---

### Post by PriceChild on 2007-03-05
LTS releases will be made when they're made :)

Basically when the majority of technology reaches a good level of stability to warrant the extra support life.

If you install an ubuntu server,```
sudo apt-get install ubuntu-desktop
```Will pull the rest of the components on top for the DE. use kubuntu-desktop for kde etc.

The server and desktop use exactly the same base.

---

### Post by maniacmusician on 2007-03-05
you're right, there is no set schedule so far for LTS releases. I'm pretty sure that LTS's are declared whenever the code seems to be most stable. I would guess probably once every 3 or 4 releases would be a good bet. However, keep in mind that non-LTS releases can be stable too. It all depends on what's being done with your customer's computers.

The difference between desktop and server is that a server install is just a command line interface with server oriented tools; apache, etc. To get the full desktop, you would install *buntu-desktop and then the appropriate X libraries (I think if you just install xserver-xorg, it will pull in the rest of the dependencies, but I'm not sure, so check that).

---

### Post by bonzodog on 2007-03-05
I do believe that i once saw it discussed with Mark that the LTS releases would be aimed at every 4th release, or one every two years.

---

### Post by Mathiasdm on 2007-03-05
> **bonzodog said:**
> I do believe that i once saw it discussed with Mark that the LTS releases would be aimed at every 4th release, or one every two years.

That's how I understood it too. 8.04 should be LTS too.

---

### Post by sbergman27 on 2007-03-05
Thank you for the response.  Yes, that's what I expected.

From my perspective as a systems integrator who does a lot of work deploying centralized desktop environments to thin clients, and hence need something with one foot in the enterprise server domain and a foot on the desktop domain, it seems to me that it would be beneficial to Ubuntu as a distro to have some sort of set schedule.  RedHat specifies 18-24 months between releases, e.g.

I think that Ubuntu is poised to position itself as the best of both worlds, having stable releases every six months, unlike RedHat's freewheeling and hobbyist oriented Fedora, and periodic LTS releases for those who need them.  But a bit of a road map as to how frequently LTS releases would be made available would be crucial for uptake.  We like to have a general idea what to expect so that we can plan properly and have something to tell our clients.

As it is, with Fedora and CentOS, moving a client from one to the other is a big deal.  It is a side-grade that is technically "unsupported" and involves allowing the machine to get about 6 months behind the package release levels of the new target OS to really work.

With Ubuntu, I could move clients to whatever release is current, and then when we hit an LTS release, leave those machines on it which need it, and move the ones that I feel I can be a bit less conservative with, to the current release.

It's truly a dream set up.  If only there were at least a target window, like 18-24 months, that I could plan for.

---

### Post by sbergman27 on 2007-03-05
"""I do believe that i once saw it discussed with Mark that the LTS releases would be aimed at every 4th release, or one every two years."""

Thanks.

That sounds good.

I'm really looking forward to these migrations.  The difference in package availability alone would make it worth the move.

-Steve

---

### Post by PriceChild on 2007-03-05
> **bonzodog said:**
> I do believe that i once saw it discussed with Mark that the LTS releases would be aimed at every 4th release, or one every two years.

> **Mathiasdm said:**
> That's how I understood it too. 8.04 should be LTS too.Again... I do not know where you heard this, but they're just rumours.

No-one knows yet :)

---

