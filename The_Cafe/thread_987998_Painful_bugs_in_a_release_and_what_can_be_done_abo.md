---
title: "Painful bugs in a release and what can be done about them"
date: 2008-11-20
forum: The Cafe
---

### Post by michaeljt on 2008-11-20
I am one of those affected by [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995), which is essentially a shutdown hang caused by alsamixer.  I see this bug occasionally, and am of course slightly annoyed that yet again something like this is biting me in an Ubuntu release.

Comments to the bug report were that this is something that the community can solve, which I don't quite agree with, as the proper solution would be updated packages from Canonical.  On the other hand, I can sympathise with Canonical when they don't want to fix this sort of issue after a release, as innocent fixes for problems which affect a minority of users have a habit of having unexpected side-effects for other uses who had never seen the original issue at all, and the whole thing can become a nasty resource drain.

So what can reasonably be done about this sort of problem?  I don't have a ready-made answer, only a couple of ideas, and input from others would be welcome.  One thought is that when an issue like this becomes known, Canonical could at least update packages to detect it when it occurs on a user's machine and to log it and point the user to information.  When a fix emerges (as it often does as part of the community discussion in the bug report), updated packages (perhaps community ones, someone usually makes some anyway) could be made available but not uploaded to all Ubuntu users - perhaps they could be put in a special repository which affected users could enable.

What do others think about this subject?

---

### Post by frodon on 2008-11-20
Reading the forum should be enough :
[http://ubuntuforums.org/showpost.php?p=6099553&postcount=18](http://ubuntuforums.org/showpost.php?p=6099553&postcount=18)

This is not because you see nothing moving from your point of view than nothing is on the move, check from time to time proposed-update repository and help testing packages. This is the only way you can help and makes thing moving faster.
Maybe consider testing the beta of jaunty to help catching those bugs before the official release, it's way easier to get such thing fixed before the official release.

---

### Post by michaeljt on 2008-11-20
Thanks for the answer.  Since I can't enabling proposed updates indiscriminately on this box (let alone upgrading to Jaunty), as I need it to be reasonably stable, is there anywhere I can see information on what proposed-updates contains, so that I can try out updates on a case-by-case basis?

Re my original posting, some way of getting this information to the user pro-actively would be very useful - to quote your answer, it "is not because you see nothing moving from your point of view than nothing is on the move", but it isn't always helpful if users give up on problems without discovering that things are on the move.  As per my suggestion above, minor updates to problem packages which detect known failures and provide the user with known information about them (say via a link on the web) if they occur would be one step.

---

### Post by michaeljt on 2008-11-20
Just to add to my last post - like (I suspect) most Ubuntu users, I am capable of finding solutions to this sort of issue myself and getting them working.  But I fear that the sort of user who isn't capable of that, or who doesn't enjoy having to fiddle with computers to keep them working, quickly loses heart and gives up.  I am wondering how life could be made easier (or the barrier lowered) for those sorts of users.

---

### Post by frodon on 2008-11-20
On the forum side we have set a sticky thread in general help section which list all known intrepid bugs which have a known workaround so the information can be found by any users searching a bit on the forum.

Other point is that you will notice that such bugs with known work arounds are less a priority for non LTS ubuntu releases. As a general note i always advise users which want something that "just work" to use only LTS releases. Post LTS releases are always the worst (this has been the case for edgy eft too) because many new stuff are introduced for the benefit of future releases, so it's needed to be a bit more tolerant with such post LTS releases.

It's because new stuff are introduced early in the LTS release cycle than ubuntu can make rock solid LTS releases like dapper and hardy.

---

### Post by michaeljt on 2008-11-20
Frankly, I think that that information (as well as the link to the forum thread) should be featured prominently on the ubuntu.com download page.  It would then also be read by people downloading a release to install for less technically-versed friends, and might save those friends some pain.  Thanks again.

---

### Post by Bruce R on 2008-11-20
As quite a lot of folk know,  I am not a Linux expert,  but this thread struck a painful chord. There's a seriously faulty assumption by some folk that just because there are not a lot of separate Launchpad bug reports,  that only a few folk are effected by an issue and so it can be dismissed as unimportant. The truth is that if folk can get through a LiveCD session and then past the new flakey hard drive installer, such encountered problems are a such a 'turn off' that they don't even know about bug reporting yet _may_ try another distro,  which is why I nearly always suggest that they try the Mint main edition counterpart. Not only does it contain a lot of 'instant use' features,  I'm afraid that it's consistently better 'engineered'. Indeed, Mint6rc1 is already better than Intrepid on my rigs and has become my everyday use distro. Although Hardy may be OK for some,  it's not yet stable,  whilst #294896 has been a more serious Intrepid flaw,  temporarily fixed by the lazarusrat/Robb Topolsky patch.

---

