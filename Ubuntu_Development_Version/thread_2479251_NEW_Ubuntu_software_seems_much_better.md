---
title: "NEW Ubuntu software seems much better"
date: 2022-09-19
forum: Ubuntu Development Version
---

### Post by corradoventu on 2022-09-19
NEW Ubuntu software aka snap-store totally rewritten in Flutter seems much better than the old one [https://www.omgubuntu.co.uk/2022/09/that-unofficial-snap-store-could-become-more-official](https://www.omgubuntu.co.uk/2022/09/that-unofficial-snap-store-could-become-more-official)
I installed and briefly tested in Ubuntu 22.10 and seems a big step.
The new snap-store is available for install also in Ubuntu 20.04

---

### Post by TheFu on 2022-09-19
Can users with HOME directories outside /home use snaps at all yet?
For example, /nfs/u1/{username} as the LDAP provided HOME?

---

### Post by zebra2 on 2022-09-19
I agree with the OP that 22.10 is getting pretty smooth with some nice Gnome improvements.  That said, I have used every development version since Karmic Koala as my primary system OS and I am certain there will be problems at release time.  Snap seems like a likely candidate. I expect it will be working pretty snappy by the next LTS.   My take on these changes is that Canonical is attempting to design a "out of the box" linux os for new to linux users that doesn't require the advanced user know how. Sandboxing is a messy but necessary security concept and Snap provides a default pre installed sandbox.  I don't know the answer to the question posed in post #2 but it isn't relevant at this point since 22.10 isn't a released version. I am sure if history continues it's normal flow with Ubuntu there will be problems on the ''not yet fixed" list at release time.  Could be that Snap will be on the list.  The suggested install for the new user is currently 22.04 warts and all.   That's the stable version for the non technical installer. I will be using 23.04 by the end of October because I don't use released versions. And PS I don't care what doesn't work.

---

### Post by TheFu on 2022-09-20
zebra2 - the issue that snaps don't work for any user account with a HOME outside of /home/{username} has been known to the snap team since at least 2017.  Hard-coding  /home/{username} is the problem.  

Snaps  should implicitly trust what the password DB, local and ldap, say for where a legal HOME directory is located.  Anything less is a design failure. Since there is nothing special about using /home/ as the only place for HOME directories, hard-coding it is wrong. It is just being lazy.

---

### Post by zebra2 on 2022-09-20
@TheFu
We are on the same page here and I agree with your entire post. My point was, since I don't use snap apps I need to install something that looks into the directory structure to see for myself what is happening.  I am in the process of doing just that. So far as laziness goes, YEP.  And as I have said, if there is a shortcoming with the 22.10 release it will most likely be with Snap. Or not!  Regarding post #2 my point was that it isn't a question that can be answered in a development version that is yet to be released. Canonical could have a fix in the repos right now even as we post our concerns.

---

### Post by TheFu on 2022-09-20
> **zebra2 said:**
> @TheFu
We are on the same page here and I agree with your entire post. My point was, since I don't use snap apps I need to install something that looks into the directory structure to see for myself what is happening.  I am in the process of doing just that. So far as laziness goes, YEP.  And as I have said, if there is a shortcoming with the 22.10 release it will most likely be with Snap. Or not!

Just create a new user account with a home under /u/{username}.
Try to use any snap.

---

### Post by grahammechanical on 2022-09-20
> My take on these changes is that Canonical is attempting to design a  "out of the box" linux os for new to linux users that doesn't require  the advanced user know how.

I agree with that. When I first joined these forums every answer was command line code and there were three GUI utilities to do the same thing. All very confusing to the new user. How much simpler things are today once the OS is installed. I have also noticed next to non existent breakage on the development version.

Redhat is working on what they call an immutable OS (Silverblue). Canonical has something similar. It is called Ubuntu Core. It does not have a Desktop Environment. That is the difference between Silverblue and Ubuntu Core. I think that Canonical is slowly working towards a version of Ubuntu that is an immutable OS. New users will not notice the difference but will be limited as to what damage they can do. Experienced users will complain about the inability to tinker with the OS and mess it up.

Edit: Read the mission statement from Redhat about Silverblue and notice the similarities to what Canonical is working on with Ubuntu and Ubuntu Core.

[https://www.redhat.com/sysadmin/immutability-silverblue](https://www.redhat.com/sysadmin/immutability-silverblue)

Regards

---

### Post by TheFu on 2022-09-20
Canonical has had an immutable OS for over a decade - it is the "Try Ubuntu/kubuntu/kubuntu/xubuntu" mode for every flavor of Ubuntu with the ISO.

It isn't anything new.

ChromeOS has been mounting the running OS as read-only for a long time. The trade-off is that 2 copies of the OS are on the storage. Last time I looked, ChromeOS uses 11 partitions.  With a ROOT-A and ROOT-B used to make OS updates depending on which is currently running.  I think they got that from one of the BSDs.  Simple, effective, elegant, until you have a bloated OS that needs 35G to work.

I sound all negative.  For every thing Canonical does that aren't my favorite, they are doing 1000+ things that I really like!  Felt I needed to say that. It is those little things - sometimes not so little - that make me squeak the loudest.

Provided the CLI stuff all works as expected, I love that the GUI helps people use Ubuntu.  More choices are good, in my mind.  If people are fine with bloated software, that's fine too. There are tradeoffs and for most people, using 30G more storage isn't all that important.  It is only important when your computer came with just 16GB - 32GB of storage total, then wasting 20G on snaps is a terrible, terrible, thing.

I've said my peace on snaps for this month. Sorry for derailing the thread.  New Flutter App for managing software == good. Got it.

---

