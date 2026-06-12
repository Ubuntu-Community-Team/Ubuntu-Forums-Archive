---
title: "I don't want to lose faith in Ubuntu"
date: 2008-04-10
forum: Testimonials &amp; Experiences
---

### Post by PypeBros on 2008-04-10
It's now been about 10 years that i made the switch to Linux, and Ubuntu is now my OS of choice on virtually any system i install. As a network researcher, i sometimes need to get into nitty-gritty details or write down firewall rules by hand as well as i sometimes need a USB device to just work.

Ubuntu typically handle both kind of situations in a very pleasing way.

Yet i stumbled today upon an issue that makes me wonder whether ubuntu is still on the good tracks. I dismissed the latest Hardy Beta release due to a collection of (minor) things that weren't going as well as i hoped, and just installed a Gutsy Gibbon on my machine. Just Fine.
Then i tried to connect that odd-wifi-USB stick on the machine, and suddenly everything freezed and stopped.

As i've said, i'm both a network researcher and a confirmed kernel hacker, so seeing the stack dump of a good kernel crash is much like a challenge to me. I figured out where the problem was and finally got the confirmation in this bug report ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130998](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130998)) that it was due to a stupid mistake (one line removed in driver source that can be fixed by swapping two lines).

I just thought i should have run "apt-get upgrade" more often, but then i cross-checked the bug status:

reported on 2007/08/08 (ages ago, imho)
severity : medium (come on? a complete system crash is "medium" importance?)
status : won't fix (just two lines to be swapped, and you won't do it ?)
maintainer comment (iirc) "Zydas support is much improved in 2.6.24. Please try the upcoming Hardy alpha 5 release."

I'm sorry to have to say it, but i think the ubuntu community is about to have a *real* problem soon or late if this is how things typically go. Rush for the next eye-candy release and don't fix known issues of well-deployed distributions ? How many times haven't we blame Big Corporates for behaving like this ? ...

Should the maintainer of the driver be blamed ?
Who should be reported about behaviour like this ?
Do Ubuntu need more volunteers in packaging kernels/apps and in integrating patches ?

I'm certainly not the first guy to think that way. I wish i'll be the last.
I figured out maybe making it "my story of ubuntu" might make its path to the proper person.

Cheers.
Keep up with the good work.

---

### Post by wieman01 on 2008-04-11
In fact - despite the fact that Ubuntu is my preferred distribution - I have to agree with you. There have been many issues that Ubuntu developers did not have high on their priority list and that have been bugging me since day one (Breezy). Wireless, Ralink drivers, Bluetooth (Kubuntu), FN keys, various system freezes (more than I ever experienced in XP), etc. In fact my system went down nearly every day last week because there is a (known) bug in the 'ndiswrapper' module (I know how to fix it now).

All in all, all flavors of Ubuntu are nice, but frankly it isn't the most stable distribution I have tried. Occasionally I wished I had chosen something else in the first place, but then again I am here because of this great community. Ubuntu lets me down far too often, something the community never does.

---

