---
title: "Question: Is Launchpad starving upstream of Bug reports"
date: 2012-04-12
forum: The Cafe
---

### Post by b1ackcr0w on 2012-04-12
Before I get to the point, a couple of contextual points.

This is a genuine query, not a whinge about when my bug will be fixed nor a criticism of the wonderful people who handle and fix bugs.

Bearing that in mind! I recently filed a bug ( [https://bugs.launchpad.net/nouveau/+bug/969121](https://bugs.launchpad.net/nouveau/+bug/969121) ) because my shiny new nvidia card doesn't seem to play nice with Nouvaeu drivers, and so I can't go distro hopping :(

On reflection, I realised this isn't really an Ubuntu problem, even though it's stopping me use Ubuntu. It's actually XOrg's problem, or whoever is hacking Nouveau. Which leads me to wonder, how many people are like me, naively logging bugs against Ubuntu in Launchpad, and expecting them to get fixed as if by magic. 

Is the expectation that I should be making more of an effort to report bugs that affect Ubuntu to outside bodies? Or is it that the bugs should be getting passed out to the third parties/other communities, but for lack of resource or whatever, this isn't happening. Is it actually happening, but because I can't see it happening, I erroneously believe it's just sitting there like Norman no mates?

Although I hold my hand up to admit I would quite like somebody to fix my bug, I also have a less selfish concern. Are upstream bugs in upstream sources such as Debian, Xorg, Pulse Audio etcetera ad infinitum, not getting their essential bug reports, because hapless newbs like me are spotting them but shoving them into Launchpad where they aren't reaching the upstream devs?

Apologies in advance to anybody affected by my stupidity.

---

### Post by forrestcupp on 2012-04-12
That's a really good question. The way I understand things is if a filed bug is something that needs to be fixed upstream, that they will pass it on and work with them on it in whatever way they are able. I hope I'm right about that.

---

### Post by roelforg on 2012-04-12
> **forrestcupp said:**
> That's a really good question. The way I understand things is if a filed bug is something that needs to be fixed upstream, that they will pass it on and work with them on it in whatever way they are able. I hope I'm right about that.
 
I think so,
just look at the gedit "Assestion failed (r==n_visible_rows)" bug

---

### Post by castrojo on 2012-04-12
> **b1ackcr0w said:**
> Before I get to the point, a couple of contextual points.
Is the expectation that I should be making more of an effort to report bugs that affect Ubuntu to outside bodies? Or is it that the bugs should be getting passed out to the third parties/other communities, but for lack of resource or whatever, this isn't happening. Is it actually happening, but because I can't see it happening, I erroneously believe it's just sitting there like Norman no mates?

Launchpad is designed for this very purpose. What you can do in this case is file a bug in the upstream Xorg package and then click "Also affects" and then paste in the URL of their bugzilla tracker. Launchpad will then keep track of it's status as well. 

You'll want to mention the URL to the launchpad report in the upstream tracker as well, as (hopefully) you've used the ubuntu tools that automatically gather the logs and stuff for everything they might need.

---

### Post by castrojo on 2012-04-12
> Are upstream bugs in upstream sources such as Debian, Xorg, Pulse Audio etcetera ad infinitum, not getting their essential bug reports, because hapless newbs like me are spotting them but shoving them into Launchpad where they aren't reaching the upstream devs?

I'm answering this separately as this might get long. 

I worked on upstream and Launchpad stuff for a few years and as it turns out for most upstreams this is totally opposite of what they want. Most upstreams don't want user bug reports, they want good bug reports only, not junk. Unfortunately the vast majority of user reported bugs are worthless. 

Forwarding all those to upstream bug trackers automatically would just cause a mess, so Launchpad acts as a sort of middleman to make sure no junk bugs make it to the upstream. The kind of bugs we want going to upstreams have things like stacktraces, logs, and hopefully, patches! This is where launchpad is useful because the Ubuntu tools we ship in the distro can automatically gather all the crash reports and put them in the bug tracker with the kinds of things upstream developers want. This is the sort of bugs that Ubuntu maintainers are expected to forward on.

We actually keep track of how well we're doing this here with external bug trackers here:

[https://launchpad.net/ubuntu/+upstreamreport](https://launchpad.net/ubuntu/+upstreamreport)

The last column, for "Watch" and "Watch percentage" shows how many bugs that could be upstream problems have a link to an upstream bug already, so as you might have guessed, we like to keep that number high.

Most of the major upstreams you mention, like Xorg and the Kernel have maintainers who do this every single day, but there's nothing stopping you from just doing the same thing if you feel it will help!

---

### Post by grahammechanical on 2012-04-12
An open invitation

[https://wiki.ubuntu.com/BugSquad]("https://wiki.ubuntu.com/BugSquad")

Also keep in mind that if the bug needs fixing upstream then we all must wait for the patched package to come back downstream.

Regards.

---

### Post by b1ackcr0w on 2012-04-13
All excellent points which furthers my understanding. Thankyou.

One point about using the tool to create the diagnostic log. The system fails before boot completes, and I don't get to a command line, just a hang during the boot just prior to X initiating. In that circumstance, how can I get usable info out to augment my bug report?

---

