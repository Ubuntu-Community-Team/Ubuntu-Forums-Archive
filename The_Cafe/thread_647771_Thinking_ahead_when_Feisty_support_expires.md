---
title: "Thinking ahead: when Feisty support expires"
date: 2007-12-22
forum: The Cafe
---

### Post by Phil Airtime on 2007-12-22
Hello,

Here's a thought. I genuinely prefer Feisty to Gutsy for a number of reasons which I won't go into here because they're not relevant. I'm reluctant to upgrade my machine because I need it for work, but I'll probably try Hardy on a spare partition or hard disc as it's an LTS. 

However, if I'm unhappy with Hardy, I'll want to keep using Feisty. I'm aware that it becomes unsupported and updates become unavailable in October next year. Is there some unofficial way to keep an old version running with security updates after this date, or am I stuck?

---

### Post by bufsabre666 on 2007-12-22
well as i do not know the answer to this, i realize your arguments to this, but i wonder, why wouldnt you want to upgrade your os. for me i've had nothing but good experiences with new version after new version after new version. is seems to be getting better all the time. in 18 months (now 16 months gutsy and 10 months feisty) when support stops i cant even imagine how advanced the os could possibly be, i remember installing a copy of 6.06 on my dads old computer and seeing how far behind it is to gutsy i would never want to bee that far back.

but as stated i can see what you mean, support is the big thing, but as long as we have these helpful people at these forums and the great collective of linux users you should be well supported for a long time

---

### Post by smartboyathome on 2007-12-22
Your pretty much stuck. I would advise you to use Hardy anyway once it comes out, since it will be an LTS (and consequently being stable will be a high priority). Besides, most of the stuff can be changed rather easily.

---

### Post by p_quarles on 2007-12-22
There's always Debian Stable. It's not bleeding edge, but it's already got a bunch of packages that are newer than the one's Feisty. It's a rolling release, so you're never going to find yourself ridiculously outdated, but at the same time you won't have any packages that haven't been through meticulous debugging in the Testing and Unstable releases.

---

### Post by ~LoKe on 2007-12-22
I don't see the problem...

The only issue is the lack of updates, which happens with all distros when a new one is released as stable.  Nothing will be "different", just nothing will be new.  There are always security updates.  I can't imagine what your reason for sticking with Feisty is, as Gutsy is significantly better.  Hardy will be LTS so even better.

---

### Post by p_quarles on 2007-12-22
> **~LoKe said:**
> I don't see the problem...

The only issue is the lack of updates, which happens with all distros when a new one is released as stable.  Nothing will be "different", just nothing will be new.  There are always security updates.  I can't imagine what your reason for sticking with Feisty is, as Gutsy is significantly better.  Hardy will be LTS so even better.
Nope. The end of support means no more security updates. Currently, that will be in October of next year for Feisty.

---

### Post by ~LoKe on 2007-12-22
> **p_quarles said:**
> Nope. The end of support means no more security updates. Currently, that will be in October of next year for Feisty.

Eep.  I messed that up.  The updates stop when a new distro comes out, and security updates stop once the support is over. My mistake. :)

---

### Post by flatko on 2008-09-24
Does this mean that the repo will be down and no more new proggies can be installed?

Since Feisty is the last version that can run smoothly on my quiet old PC, and still has the Studio packages in there, I have to stay with this version...

---

### Post by LaRoza on 2008-09-24
> **flatko said:**
> Does this mean that the repo will be down and no more new proggies can be installed?

Proggies?

No. It means it won't get updates. It will still work, just not change or improve. For home use, that won't matter unless there is something drastic.

---

### Post by Joeb454 on 2008-09-24
I'm not sure. I think the edgy repo's don't work anymore, so yes possibly. They may still work for a while.

That said, I'd imagine upgrading to Gutsy or Hardy should be fine now :)

---

### Post by LaRoza on 2008-09-24
> **Joeb454 said:**
> I'm not sure. I think the edgy repo's don't work anymore, so yes possibly. They may still work for a while.

That said, I'd imagine upgrading to Gutsy or Hardy should be fine now :)

And this thread has been necromanced.

---

### Post by earthpigg on 2008-09-24
"My name is flatko, and i bring threads back from the dead"

couldn't resist, Dr Frankenstein :)

i wouldn't be suprised if there was some set of unofficial repositories out there just for guys in your position... no idea where to find em tho.

---

### Post by lisati on 2008-09-24
I use Feisty. I upgraded to Gutsy a few months back - apart from a bit of tinkering (mainly installing new sound drivers) it went smoothly. I went back to Feisty after a muck up meant the need for a fresh install. I'll be watching with insterest....
(Could be time for a cleanup of my system and make a custom "Live CD" with all the updates included.....)

---

### Post by tcpip on 2009-05-07
I think there's a bigger problem here for people like us who want to keep using an old release. I believe the repositories themselves are removed after the release expires. This means that "apt-get update" starts reporting dozens of errors, and "apt-get install XYZ" fails to find the .deb file even when its meta-data is there locally with me.

I am using 7.10 and I have begun facing this problem. I am willing to live without security updates, but I can't imagine how I can continue to work with my current installed Ubuntu if I can't install common packages which I need now.

Please let's not get into "why won't you upgrade?" The reason for me was that 8.04 and 8.10 both broke very basic and core functionality on my laptop (e.g. display management). But as I said, let's not get into that discussion.

How does a user continue to use Ubuntu after the release expires, if even the repositories are removed?

---

### Post by 23meg on 2009-05-07
[QUOTE=tcpip]How does a user continue to use Ubuntu after the release expires, if even the repositories are removed?[/QUOTE]

Possibly by creating a local repository mirror.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

---

