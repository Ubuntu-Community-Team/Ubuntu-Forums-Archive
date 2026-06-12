---
title: "Where do I post to whine about out of date packages in canonical?"
date: 2010-01-17
forum: The Cafe
---

### Post by tehwalrus on 2010-01-17
What I am really looking for is some kind of voting system for packages that I would like to see updated in the central repos sooner rather than later; for the admins to take into account while prioritising .deb development.

Principal example is BloGTK, which is still v1.something in canonical, but is out as 2.0 (stable) from it's homepage on launchpad, and has been since September. The important point here being that v1 fails to work entirely on netbook remix (i.e. it just fails to log into newer blog systems) whereas v2 is stable and functional.

Similarly, I would like to vote for thunderbird 3 being integrated ASAP, and I would like to know the status of google chrome being available in universe.

I don't mind installing these programs from their respective websites instead of using [FONT=Courier New]sudo apt-get install[/FONT], but other users will suffer (and in the case of BloGTK form a negative impression of the project) if they download an old, broken version from canonical and don't go and check the project's homepage.

---

### Post by SuperSonic4 on 2010-01-17
Save your breath because they won't listen. It's one of ubuntu's core philosophies that after the feature freeze only bugfixes and security issues are dealt with until the next release 6 months later. This is done in the name of stability and I can see where they're coming from even though I disagree.

Your best bet is to compile from source, find a PPA or move to a rolling release distro

---

### Post by mkvnmtr on 2010-01-17
It is not all hard to learn how to enable the other repositories or download from a site that has a deb. They will not change. If you need a rolling release there are some out there.

---

### Post by tehwalrus on 2010-01-17
ok...

...so when I run [FONT=Courier New]sudo apt-get upgrade[FONT=Verdana], and it downloads a load of application updates, those are, what, only security fixes? I'm sure I've seen firefox and thunderbird updates coming down in that stream, as well as loads of library updates.

is that "not canonical", or something?

As I said, *I* am happy to install stuff from source/random .debs I find elsewhere (it's the only way to install chrome), it's other people having a negative experience with the distro, or with 3rd party projects because of the distro, that's annoying/avoidable.

The reason I stick with Ubuntu is because they spend so much time sorting out driver issues for you; I don't think I could switch to like Debian or Gentoo without going insane trying to get my wireless networking back up again.

Thanks for the replies, let me know if I've just phrased my question badly...
[/FONT][/FONT]

---

### Post by tehwalrus on 2010-01-17
@mkvnmtr: ah, that may be the solution. I will do a bit of research and see if there's a good repo with up to the minute releases of stuff.

Thanks!

---

### Post by louieb on 2010-01-17
> **tehwalrus said:**
> [FONT=Courier New][FONT=Verdana]... those are, what, only security fixes? I'm sure I've seen firefox and thunderbird updates coming down ...
[/FONT][/FONT]

Thats what backports do. Ubuntu has a backport team. If they decide a package is worth backporting to a previous release - they will test it and if it seems good will add it to the backport repository. 

BTW: backported applications are not supported by the security team - use at your own risk.

---

### Post by mkvnmtr on 2010-01-17
To start finding repositories go to the getdeb page.  While there download Ubuntu Tweek. That will get you a good start on having repositories for most late model stuff. I like having a repository enabled for the updates that will come through it.

---

### Post by Joeb454 on 2010-01-17
You need to enable the backports repository though.

I know that Firefox has released both 3.5.6 and 3.5.7 as security releases, so they would come through as updates either way, which is why you would've seen them

---

### Post by tehwalrus on 2010-01-17
I think there are enough suggestions for workarounds now, thanks everyone!

I will give it a go when my netbook gets back from repair (dodgy battery).

Cheers,

thewalrus.

---

