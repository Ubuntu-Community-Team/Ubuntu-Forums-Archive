---
title: "Is Edubuntu Dropping Off of the Xenial Release Development Cycle"
date: 2015-10-31
forum: Ubuntu, Linux and OS Chat
---

### Post by genesoo77072 on 2015-10-31
I had been downloading and testing the installation of Edubuntu.
I was getting the 15.04 and 15.10 Daily code drops up until the GA dates for 15.04 and 15.10 respectively.
Now that Xenial(16.04) directory structures are built and populated, Edubuntu has not been altered nor is there an updated drop.
The Edubuntu org download page recommends 14.04.2 LTS so it looks like Edubuntu has either been abandoned or is seriously late keeping up with the release schedules.

Is Edubuntu still an active Distro or has it been abandoned?

---

### Post by PaulW2U on 2015-10-31
> **genesoo77072 said:**
> Is Edubuntu still an active Distro or has it been abandoned?
Edubuntu is **now** on an LTS only release cycle.

Although you may have been downloading daily builds for 15.04 and 15.10 the general release announcements for Ubuntu do not include Edubuntu.

[Ubuntu 15.04 (Vivid Vervet) released]("https://lists.ubuntu.com/archives/ubuntu-announce/2015-April/000195.html")
[Ubuntu 15.10 (Wily Werewolf) released]("https://lists.ubuntu.com/archives/ubuntu-announce/2015-October/000202.html")

If you join the #edubuntu channel on Freenode you are greeted with the following message:
> Topic for #edubuntu is "Current Edubuntu is 14.04 LTS.
I would imagine the Edubuntu developers, of which there are not many, think that it's far too early to include Edubuntu in the Xenial daily build cycle for what would be a large DVD sized image and one that is largely based on Ubuntu anyway.

So not abandoned - still active - just the developers working in a slightly different way to other official Ubuntu flavours.

---

### Post by Bucky Ball on 2015-10-31
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by genesoo77072 on 2015-11-01
Thanks for the status info and IRC reference.

---

### Post by kansasnoob on 2016-03-20
Sadly there will be no Edubuntu Xenial :(

I sent the following PM to contact-AT-edubuntu.org earlier today:

> Hello and apologies in advance for the intrusion via PM but I'm unable to use IRC chat due to disability. Perhaps someone will recognize me from testing & bug filing efforts (I've been involved in iso/upgrade testing since 2008 as lbsolost):

[https://launchpad.net/~lbsolost](https://launchpad.net/~lbsolost)

I recently posted a question about Xenial builds at edubuntu-devel:

[https://lists.ubuntu.com/archives/edubuntu-devel/2016-March/003883.html](https://lists.ubuntu.com/archives/edubuntu-devel/2016-March/003883.html)

As you can see I've received no response as yet and final beta is due next week. As long as I'm talking I also notice that some documentation is not being updated, for example 14.04.2 being the latest update here:

[https://www.edubuntu.org/](https://www.edubuntu.org/)

I know Edubuntu is now on an LTS only release schedule, which is fine, but I wonder if some members of the Edubuntu team have left to pursue other things and left a void without being noticed?

Thanks in advance and apologies again for the intrusion,

Lance 

And I received the following reply:

> Pretty much everyone left a while back, it's been down to just Jonathan
and I for the past couple of years and even the two of us don't have
enough time to work on Edubuntu 16.04.

As it stands, it's very likely that we'll be announcing that we will not
be releasing Edubuntu 16.04 and will instead only work on continuing
support for Edubuntu 14.04 LTS.

That will leave until 18.04 for a new team to start contributing and
take over the Edubuntu project from us.

I then forwarded that to the owner of the Canonical Foundations Team to be certain they are aware.

---

### Post by ventrical on 2016-03-20
Thanks kansasnoob.   I always liked Edubuntu. Somehow it seemed to get less and less attention and I rarely seen anyone filing bugs or actually using the desktop. As it stood it was a very large download and I think this deterred people from actually trying it out. Maybe they will still have updates for Edubuntu Desktop in the future.

and yep .. resources mostly used now for viable snappy, 'snapcrafts' and workable unity7 for 16.04

regards..

---

### Post by ventrical on 2016-03-20
Ok .. we are getting bumped from development version to here.

---

### Post by kansasnoob on 2016-03-20
> **ventrical said:**
> Ok .. we are getting bumped from development version to here.

No one bumped anything. I just posted a link to this news over in the dev section of the forums:

[http://ubuntuforums.org/showthread.php?t=2317871](http://ubuntuforums.org/showthread.php?t=2317871)

I posted here first because i knew the thread existed. I just hadn't commented here because I had nothing to add to what *PaulW2U* said until now.

I will try like the devil to at least get a 5th point release spun for Trusty so people can perform a fresh install without using the 14.04.2 media which would immediately require upgrading to the Xenial HWE stack after August, but now is not the time for that. I'll put that on my June calendar.

---

### Post by Bucky Ball on 2016-03-20
That is a real pity. I like the artwork and always install that. :|

Not to mention the loss of all the other Edubuntu goodness which I'm sure is enjoyed by others. Hoping it can resurrect by 18.04 LTS.

---

### Post by kansasnoob on 2016-03-20
I had long thought that Edubuntu was supported by Canonical more so than the other flavors because [this page]("https://www.edubuntu.org/sponsors") says:

> Canonical Ltd is the primary sponsor behind the Edubuntu project. Since 2004, the company has contributed to Edubuntu in the form of:

    **Employee time working on the project**
    Travel and accommodation to Ubuntu related events
    Build service resources for packages and ISO images
    Web hosting for the Edubuntu website


But the Canonical Foundations Team leader just replied:

> It wasn't something I was aware of, but it's also not really a Canonical
matter.  Edubuntu is a community flavor, and it's up to the Edubuntu
community, in conjunction with the larger Ubuntu community, to decide what
and if they release.

If you think this needs further follow-up, I think it would be appropriate
to discuss it on the ubuntu-release and ubuntu-devel mailing lists.


So my wrong assumption makes me think now that Edubuntu may be in quite serious danger of no longer meeting the requirements as an official flavor:

[https://wiki.ubuntu.com/RecognizedFlavors](https://wiki.ubuntu.com/RecognizedFlavors)

> Guidelines to become and remain a recognized flavor:

    Image has track record of community interested in creating, supporting and promoting its use.
    Leading members have signed Ubuntu Code of Conduct.
    One or more developer with upload rights.
    Flavor lead identified and responsive though 6 month cycle.
    Flavor QA lead (may be different from flavor lead) identified to coordinate testing of image at milestones during release.
    Follow the milestone and release processes.
    Best effort support from flavor community for security updates and high priority bug fixes for default 9 month support period.

    If flavor ceases to do active releases for consecutive cycles, release team may request the TechnicalBoard review whether it should remain recognized flavor. 

I'm subscribed to ubuntu-release so I'll raise the entire issue there after Xenial final Beta is released.

---

### Post by kansasnoob on 2016-03-20
All of the Trusty images are here:

[http://cdimage.ubuntu.com/edubuntu/releases/14.04.4/release/](http://cdimage.ubuntu.com/edubuntu/releases/14.04.4/release/)

So anyone wanting to use Trusty would be smart to use the 14.04.1 images for fresh installs until this all gets hashed out.

BTW it appears that even Skolelinux' Jessie version is stalled on Beta:

[https://wiki.debian.org/DebianEdu/ReleaseNotes/Jessie](https://wiki.debian.org/DebianEdu/ReleaseNotes/Jessie)

---

### Post by kansasnoob on 2016-03-21
The announcement is now official:

[https://lists.ubuntu.com/archives/edubuntu-devel/2016-March/003884.html](https://lists.ubuntu.com/archives/edubuntu-devel/2016-March/003884.html)

> I'm sending this e-mail on behalf of the current Edubuntu project
leaders, Jonathan Carter and myself.

Jonathan and I have both been involved in Edubuntu for a long time
(almost 10 years for Jonathan and almost 9 for me). We were at first
just contributors, then became council members and after the council got
disolved due to lack of candidates, as the two project leaders.


A lot changes in that many years and while at the start we both had a
considerable amount of spare time to invest in making Edubuntu great,
even getting paid for it at times, that is simply not the case anymore.

We've both moved on to new projects, with the hope that we would one day
find some time to work on Edubuntu again. That's why we decided to make
Edubuntu LTS-only after the 14.04 release, hoping that over the course
of two years we would find the needed time to make a good Edubuntu 16.04 LTS.

This plan didn't quite work out as we're now a month away from the 16.04
release with little to no work having been done on Edubuntu.

We could of course patch things up a bit, drop the things that don't
work and call it good enough. But we don't think that would be fair to
our users who are expecting a well thought through distribution where
all details have been taken care of.


That's why I'm announcing today that Edubuntu will NOT be releasing a
16.04 LTS version. Instead, Jonathan and I will focus on ongoing support
of Edubuntu 14.04 LTS until it goes EOL in April 2019.


That's not to say that Edubuntu is dead, at least not yet.

While Jonathan and I will solely focus on fulfilling our promise of
support for Edubuntu 14.04 LTS, new contributors are absolutely welcome
to take over the Edubuntu project and shape it to their liking.

The two of us will be happy to sponsor any Edubuntu related uploads,
will help new contributors get Edubuntu membership and then hold
elections to setup a new Edubuntu Council which would finally take
the whole project over from us.


Should none of that happen by the time Ubuntu 17.10 is released,
Jonathan and I will ask the Technical Board to revoke Edubuntu as an
official flavour and will be removing any leftover packages from the
archive, remove our seeds and any cdimage build integration, effectively
removing Edubuntu from the Ubuntu release process.



While a bit late as far as announcing this, I think our plan fulfills
the "Step down considerately" clause of the Ubuntu Code of Conduct,
allowing for new contributors to pick things where we left them or to
come up with a completely new vision if they prefer.



It's been a fun ride for the two of us and we very much hope that this
won't be the end of Edubuntu but instead a new beginning for this great
Ubuntu flavour!

Sincerely,

The retiring Edubuntu project leaders, Jonathan Carter and Stéphane Graber.

---

### Post by Portaro on 2016-03-25
I hope that people of Edubuntu can be more time to maintain the project, its an important project of the community then is important that can be maintained.
Thanks for the amazing work to Jonathan and Stéphane.

:popcorn:

---

### Post by Brinstar on 2016-04-24
[http://cdimage.ubuntu.com/edubuntu/dvd/current/](http://cdimage.ubuntu.com/edubuntu/dvd/current/)

Is this an actual working nightly of Edubuntu 16.04? I'm not able to install/test it at the moment so I can't tell.

---

### Post by Bucky Ball on 2016-04-24
> **Brinstar said:**
> [http://cdimage.ubuntu.com/edubuntu/dvd/current/](http://cdimage.ubuntu.com/edubuntu/dvd/current/)

Is this an actual working nightly of Edubuntu 16.04? I'm not able to install/test it at the moment so I can't tell.

Not sure there is one. Read [this]("http://news.softpedia.com/news/edubuntu-16-04-xenial-xerus-will-not-be-a-long-term-support-lts-release-502003.shtml"). Looks like they have no intention of releasing one at this point. But sure enough, your link points to the Edubuntu 16.04 LTS daily. :-k

Perhaps more digging required into this anomaly.

---

### Post by kansasnoob on 2016-04-24
But the date of that iso is January 30, 2016 ............................ so nearly 3 months old. There will be no official release of Edubuntu Xenial.

---

