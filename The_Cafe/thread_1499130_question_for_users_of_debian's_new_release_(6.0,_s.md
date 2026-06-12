---
title: "question for users of debian's new release (6.0, squeeze)"
date: 2010-06-01
forum: The Cafe
---

### Post by pythonscript on 2010-06-01
Question for any Debian users that are also on this forum:

> 
Once Debian 6.0 (*squeeze*) is released, a new policy of time-based  development freezes on a two-year cycle will come into force.  Time-based freezes will allow the Debian Project to blend the  predictability of time based releases with its well established policy  of feature based releases. The new freeze policy will provide better  predictability of releases for users of the Debian distribution, and  also allow Debian developers to do better long-term planning

I read this online, and I recently started using another Debian based distro, so I'm wondering. Does this mean that future versions of Debian *won't have any new stable features except once every two years?* If not, could someone clarify this for me?

---

### Post by chickengirl on 2010-06-01
they're switching from having stable releases "when it's ready" to every 2 years.

---

### Post by AlexDudko on 2010-06-01
Squeeze hasn't been released yet, it's still in testing.
Debian users don't receive new stable features every day, they receive them with every new stable release. (Though there are backports...).

---

### Post by snowpine on 2010-06-01
> **pythonscript said:**
> Question for any Debian users that are also on this forum:



I read this online, and I recently started using another Debian based distro, so I'm wondering. Does this mean that future versions of Debian *won't have any new stable features except once every two years?* If not, could someone clarify this for me?

Your understanding is correct. Debian [historically averages]("http://en.wikipedia.org/wiki/Debian#Release_history") one stable release roughly every two years. Debian is not a good choice if you need yearly or twice-yearly stable releases; Ubuntu is probably a better choice in that instance (or a "rolling release" distro like Arch or Debian Sid if you need constant updates).

My understanding of their new policy is that the Debian development freeze will indeed be scheduled every 2 years, but the final release date will continue its current policy of "whenever it's ready." So the final releases might be a little more than, or a little less than, two years apart.

---

### Post by pythonscript on 2010-06-01
Thanks for the quick responses. I was looking at using Crunchbang Linux on my netbook, but I don't want to wait over two years for new features. Since the newest version of Crunchbang is moving from an Ubuntu base to a Debian base, I feared this would be the case. 

I prefer the beta quality of Lubuntu and the six month release cycle to the two year release cycle of Debian. Thanks again!

---

### Post by snowpine on 2010-06-01
> **pythonscript said:**
> Thanks for the quick responses. I was looking at using Crunchbang Linux on my netbook, but I don't want to wait over two years for new features. Since the newest version of Crunchbang is moving from an Ubuntu base to a Debian base, I feared this would be the case. 

I prefer the beta quality of Lubuntu and the six month release cycle to the two year release cycle of Debian. Thanks again!

Many CrunchBang users (including myself) are using Debian Testing, Debian Unstable ("Sid"), or mixed Testing/Unstable sources to get the latest "stuff." More details [in this thread]("http://crunchbanglinux.org/forums/topic/6760/suggestion-support-stableunstable-conversion/").

IMHO, Debian Stable is ideal for servers, workstations, and users with conservative needs. Most hobbyists I've come across are using Testing or Unstable for everyday home desktop/laptop/netbook use. (Also note there is currently no CrunchBang based on Debian Stable; you *must *use Testing or newer.) I personally am currently using CrunchBang upgraded to Unstable on my Dell Mini 9 netbook.

---

### Post by NightwishFan on 2010-06-01
You can install Debian Testing or Sid, both of which are rolling releases.  I use "Testing", which imports packages from unstable that have no major bugs. Debian Stable is released "stable" after much testing, and only recieves fixes and security updates. To put it into perspective, Debian Lenny is currently newer than Ubuntu Hardy for most packages.

_Rhythmbox_

Debian Lenny: 0.11.6
Ubuntu Hardy: 0.11.5

---

### Post by pythonscript on 2010-06-01
> **NightwishFan said:**
> You can install Debian Testing or Sid, both of which are rolling releases.  I use "Testing", which imports packages from unstable that have no major bugs. Debian Stable is released "stable" after much testing, and only recieves fixes and security updates. To put it into perspective, Debian Lenny is currently newer than Ubuntu Hardy for most packages.

_Rhythmbox_

Debian Lenny: 0.11.6
Ubuntu Hardy: 0.11.5

It will definitely be an adjustment for me, though, because normally, I upgrade to every version of ubuntu as it comes as to obtain the new(est) software that bundles with it. For much of what I use (eclipse, python, php, open office, etc) the Hardy versions are *far* too out of date, and even the relatively recent Debian ones don't seem much better. I'll still be running Ubuntu and Arch on my production machine, though, so Crunchbang is only for my netbook.

---

### Post by NightwishFan on 2010-06-01
You can check what versions Debian packages are and their bugs here. Just choose any repo. (stable testing unstable etc) If you are confident with Debian you can selectively backport stuff as well. I run testing sometimes with various unstable packages.

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

