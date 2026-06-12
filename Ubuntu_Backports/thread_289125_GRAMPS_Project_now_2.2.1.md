---
title: "GRAMPS Project now 2.2.1"
date: 2006-10-30
forum: Ubuntu Backports
---

### Post by ookooboontoo on 2006-10-30
Hi all,

I apologise, I am new to all this but can I request the backporting of GRAMPS, which is currently in Dapper and edgy Univers repositories as
gramps (2.0.11-2ubuntu1) [universe]
Genealogical Research and Analysis Management Program

The latest version which is a reasonable update is the 2.2.1 version. I am only a messenger, not a coder but I would be happy to look into any further issues you would request (within reason :p)

The project site is [http://gramps-project.org/](http://gramps-project.org/) and the latest .deb version is at sourceforge though the project's download link.

Many thanks for your help.

---

### Post by robocoder on 2006-11-15
I'd like to see an updated Edgy package of the new version of GRAMPS, too. (BTW Gramps is now at 2.2.2.)  Issues should be few given that the project is written in Python.  There's an added dependency  on the Cairo drawing library -- already in main (libcairo-directfb2).

---

### Post by ookooboontoo on 2006-11-15
Yes you are correct Robocoder, I did not add that as I had not a reply. I did speak to Alex on the Live CD, and As he soundly suggested it would be perhaps better still on the Dapper as that has a guaranteed 5 years support.

I know there has been a niggle reported with the grdb file saving, though Don and Alex cannot replicate it themselves. It is worth checking mailing list as a precaution. I believe this is not a life threatening issue tho :)

I have had no response from the team as what to do, so if anyone can give me guidance I would be pleased to help :)

---

### Post by robocoder on 2006-11-21
You're referring to Dapper-based "Linux Genealogy Desktop CD 2.0", I presume.

I think the hold-up is upstream.  Debian hasn't yet propagated 2.2.2 from unstable to at least testing (which is where I think Ubuntu packagers are willing to sync up).

According to the Debian package status, 2.2.2 is in testing, but clicking on the link shows 2.0.11. *boggle*

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=gramps&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=gramps&searchon=names&subword=1&version=all&release=all)

Hmm... Dapper's package is a version behind Edgy's:

[https://launchpad.net/distros/ubuntu/+source/gramps](https://launchpad.net/distros/ubuntu/+source/gramps)

---

### Post by robocoder on 2006-11-27
*chuckle* gramps is now at 2.2.3.

---

### Post by ookooboontoo on 2006-11-28
Yes, frightening isn't it?! I am not sure where to go for anything further. At least I have requested. Sadly I am not familiar with the universe system so I leave it to the experts unless needed for something. Good to know you are keeping up with it Robocoder :)

---

### Post by Eastex Cruiser on 2006-12-30
Well, it appears GRAMPS is now on version 2.2.4. I'm concerned that if I start using 2.0.11, which is in the repositories, will it easily convert over to the 2.2.* once an upgrade is available?

---

### Post by GrumpyBob on 2007-01-05
I played with GRAMPS installed on Edgy from the Repos in October, then used it for real over the Xmas break after upgrading to 2.2.4 with the Ubuntu deb package from gramps-project.org.  No problems (that I am aware of at least).

Robert

---

### Post by jynyl on 2007-01-07
The Gramps web site now has v 2.2.4, and 2.0.11 (the version in Edgy) is from April last year.
It looks like this app wasn't updated for 6.10 Edgy release.
What should we do to ensure an updated version gets into the next release of Ubuntu?

TIA

Peter

---

### Post by ookooboontoo on 2007-01-07
I posted the original in this thread. I have received no word on what else need be done. I am a novice at this. if someone tells me what else to do then maybe we could push it forward. I posted here as the directions said to but nothing has been done. Where are the MOTU, or do we need other heroes?

Thanks, I would love to see these updates regularly backported. We may need to go back to Don and the Team as this thread has gone nowhere I am sad to say :(

---

### Post by ookooboontoo on 2007-02-03
Just a note to anyone following this, it seems that the current version is ready for the repositories in Fiesty when that comes out. The have 2.2.6 available for Feisty.

But the issue of Backporting for ubuntu 6.0.6 remains not done. perhaps we just have to keep the issue within our own community and  they can update with packages off sourceforge. a shame really. but this thread was not really noticed it seems.

---

