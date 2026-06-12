---
title: "Ubuntu 13.04 Still On Course for April Release?"
date: 2013-03-06
forum: Ubuntu Development Version
---

### Post by philinux on 2013-03-06
Interesting. 

[http://www.omgubuntu.co.uk/2013/03/ubuntu-13-04-still-on-course-for-april-release?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2013/03/ubuntu-13-04-still-on-course-for-april-release?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by kansasnoob on 2013-03-06
I thought this discussion on Lubuntu QA with Jono Bacon was interesting:

[https://lists.launchpad.net/lubuntu-qa/msg01857.html](https://lists.launchpad.net/lubuntu-qa/msg01857.html)

Of particular note:

> It is pretty simple: an idea for a release management change was proposed to ubuntu-devel, and now we need to have a detailed, focused, and comprehensive discussion about whether it makes sense. These kinds of big changes take time to discuss and get right. If people are chomping at the bit for an answer, they are just going to need to wait a little until we reach a conclusion...this happens with every large proposed change in our community.

Edit: Actually, to be more accurate, the conversation itself was on Facebook:

[https://www.facebook.com/jonobacon/posts/10151532662746458?notif_t=comment_mention#](https://www.facebook.com/jonobacon/posts/10151532662746458?notif_t=comment_mention#)

---

### Post by grahammechanical on 2013-03-06
From my little understanding of how Ubuntu progress is mapped out, I would have thought that a suggestion like this should been a blueprint at the last UDS, the one for Raring if 13.04 was to become the rolling release. If it had not been for this idea of having an on-line UDS then this suggestion would have had to wait until the physically attended UDS for the 13.10. I am not much of an orderly person but it would make sense to me to get 13.04 out of the door and turn the 13.10 development release into the desired rolling release. This would not prevent discussion and planning and getting things in place in the meantime.

Regards.

---

### Post by craig10x on 2013-03-06
> **grahammechanical said:**
> From my little understanding of how Ubuntu progress is mapped out, I would have thought that a suggestion like this should been a blueprint at the last UDS, the one for Raring if 13.04 was to become the rolling release. If it had not been for this idea of having an on-line UDS then this suggestion would have had to wait until the physically attended UDS for the 13.10. I am not much of an orderly person but it would make sense to me to get 13.04 out of the door and turn the 13.10 development release into the desired rolling release. This would not prevent discussion and planning and getting things in place in the meantime.

Regards.

As anxious as i was for 13.04 to become the rolling, i have to stay, you make a LOT of sense...wish the developers that were at the UDS would read your comment here...
I get the sense that the developers of the community versions of ubuntu (like lubuntu) are getting po'd about the lack of answers as to whether 13.04 would be final released, because
they don't know if they should continue working on it..and most of us in the community also dislike the lack of definite planning with this...

So, in view of that, what you said here makes perfect sense...

---

### Post by nomenkultur on 2013-03-07
if the alpha process of 13.04 is what you could call 'rolling' (numerous daily updates, including kernels,drivers, xorgs etc)

 I see no reason why 13.04 can't be made rolling, had I not remove a bunch of stuff I would have encountered no bugs with 13.04

---

### Post by vasa1 on 2013-03-07
> **kansasnoob said:**
> I thought this discussion on Lubuntu QA with Jono Bacon was interesting:

...
I've been saying for a while that Canonical's communication skills could be better ... much better. It's difficult to comment on the linked material without crossing some sort of line.

---

### Post by kansasnoob on 2013-03-07
I particularly wanted to know what Lubuntu dev was planning on so I asked, and Julien answered:

[https://lists.launchpad.net/lubuntu-qa/msg01865.html](https://lists.launchpad.net/lubuntu-qa/msg01865.html)

> Just to make a quick a update, there is no change in schedule [1]
since the beginning of this cycle. We will push to have a Beta 1, and
a Beta 2, and a 13.04 release.

There is a lot of change ongoing on Canonical side. I'm still in the
process to analyse them and try to find the best way to adapt to this
new direction. But the priority is 13.04, we need to keep this in
mind.

And he then weighed in here also:

[https://lists.launchpad.net/lubuntu-qa/msg01866.html](https://lists.launchpad.net/lubuntu-qa/msg01866.html)

> I can't talk for Ubuntu, but for Lubuntu we are going to release 13.04, as
most of the flavors will do.  When I do a schedule, I like to stay on track
during all the schedule. We decided 6 month ago to do a 13.04, I consider
we have to do this release. What Canonical want to do with their flavor
(Ubuntu) is their problem, not our.

I hope I answered your question. We will still have a lot of discussions
after 13.04 to see how we will handle the new model of development proposed
by Canonical, but let release this version first :-)

So we know that both Kubuntu and Lubuntu plan to release as previously scheduled :guitar:

---

### Post by grahammechanical on 2013-03-07
@kansasnoob

I like the Lubuntu dev's description of Ubuntu as a Canonical flavour. Makes I laugh.

---

### Post by forcecore on 2013-03-09
Finally, it was time to make Ubuntu rolling so everyone can get always fresh software like new VLC, Transmission, SFLphone and many others when tested stable.

---

### Post by grahammechanical on 2013-03-09
> [COLOR=#000000]when tested stable.[/COLOR]

Ah! That is most important. Some people think that "latest" = "greatest." And want it. And demand it. I think that sometimes there is an assumption by maintainers that whatever comes from upstream must be stable and it is merged without it being tested. In Linux the user is the tester but that should not be true in Ubuntu. During Quantal my OS was broken by an updated Nvidia driver that already had a serious bug reported against it. The same bug that I experienced. It should never have been merged.

I am in favour of Community Volunteer Testers testing code before it gets into the main branch. Or, if we are talking about the development branch having a rolling update, after it gets merged into the development branch but before it gets released as an LTS. There must also be a system where issues are reported back to specific developers and not lost in the big heap of bug reports. If a developer fails to fix the issues (and we are willing to test the fixes) then that "latest" code of his does not get into the LTS.

Regards.

---

### Post by craig10x on 2013-03-09
Very true...you know i am the only one who seem to have reported the bug that 13.04 has in that when you change the touchpad settings, they don't "lock in" but go back to the default...i wonder if they even ever looked at my bug report...and i have no way of saying "hey developers...check this out!"...and getting their attention...
And the quicktime videos (on itune movie trailers) is still broken too...neither seem to be getting fixed...

---

### Post by screaminj3sus on 2013-03-09
> **craig10x said:**
> Very true...you know i am the only one who seem to have reported the bug that 13.04 has in that when you change the touchpad settings, they don't "lock in" but go back to the default...i wonder if they even ever looked at my bug report...and i have no way of saying "hey developers...check this out!"...and getting their attention...
And the quicktime videos (on itune movie trailers) is still broken too...neither seem to be getting fixed...

I get the feeling 13.04 is going to end up as an ugly stepchild release. At first I was excited because they seemed to be focusing on daily quality and reducing regressions, and things were great for a while, but recently I've seen a ton of regressions in 13.04, and it worries me since its getting late in the dev cycle. I have a bad feeling that some things may be ignored with ubuntu's current stack (compiz for example) since canonical's developers are moving on to greener QT/QML pastures.

---

### Post by mc4man on 2013-03-10
> **screaminj3sus said:**
> I get the feeling 13.04 is going to end up as an ugly stepchild release. At first I was excited because they seemed to be focusing on daily quality and reducing regressions, and things were great for a while, but recently I've seen a ton of regressions in 13.04, and it worries me since its getting late in the dev cycle. I have a bad feeling that some things may be ignored with ubuntu's current stack (compiz for example) since canonical's developers are moving on to greener QT/QML pastures.

I'd think compiz, compiz/unity will be around for a bit longer, whether it's fixed/improved in that time I don't know, though it appears to still be getting commits, ect.
(don't really get the diff between lp:compiz & lp:compiz/raring, the latter being recently created (at least it says so.
see one of your bugs with a fix approved & jenkins ok on later, jenkins fail on former

If I could bet against a usable unity next & or mir on the desktop in 14.04 I'd certainly do so

---

