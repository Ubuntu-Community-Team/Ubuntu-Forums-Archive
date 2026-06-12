---
title: "Ubuntu Server Review (esp. Server-Desktop differences)"
date: 2007-11-27
forum: Server Platforms
---

### Post by MJN on 2007-11-27
Hi everyone,
 
It seems to be a common scenario and discussion point around here about whether one should install the Ubuntu server or desktop edition, and why. One of the most common differences cited as a driver for the decision is the default package installation, particularly with regards to X.
 
There are also of course other differences, in particular the kernel optimisation differences between the two however trying to find the official Ubuntu line on what these are appears futile as they don't seem to exist (if someone knows where they are please do shout out, although it has to be said that such info should not really be so hard to find!).
 
Anyway, in my quest to find these differences I stumbled across the following 3-part review of Ubuntu Server which I thought may be of interest to others. I think it is fairly balanced (as these types of review go) and covers the good and not-so-good aspects (indeed it mentions the state of the official documention which I am disappointed to have to nod in full agreement with).
 
Incidentally, I agree the titles (and the parting comments in the final review) are somewhat evocative but it is of course only one person's opinion and perspective so please don't take this post as flamebait - I am passing on the information purely for interest, not least the non-subjective aspects of the analysis.
 
I will post the link to each part as, at the time of writing, the final part has yet to be linked from the first two articles:
 
Part 1 - 'Ubuntu Server: Attractive Choice, Paltry Documentation'
[http://www.enterprisenetworkingplanet.com/netos/article.php/3709221](http://www.enterprisenetworkingplanet.com/netos/article.php/3709221)
 
Part 2 - 'Ubuntu Server: Considering Kernel Configuration'
[http://www.enterprisenetworkingplanet.com/netos/article.php/3710641](http://www.enterprisenetworkingplanet.com/netos/article.php/3710641)
 
Part 3 - 'Ubuntu Server: Good Concept, Flawed Execution'
[http://www.enterprisenetworkingplanet.com/netos/article.php/3712031](http://www.enterprisenetworkingplanet.com/netos/article.php/3712031)
 
Cheers,
 
Mathew
 
P.S. Sorry if this is actually a duplicate topic - a search for the same review revealed only a passing mention in the newsletter which I assume not everyone is subscribed to.

---

### Post by prodezigner on 2007-11-27
I just read the third part.

The only thing I've got to say is... I hate reviews. Ubuntu is the number one Linux distro for the desktop. Canonical doesn't charge for there server software as most enterprise Linux distros cost (RedHat, SuSE, etc.) so being free is a great thing. She touches on topics that are irrelevant, who cares what packages come with it honestly? It's made to be setup simply. You want a LAMP stack? It's there, bam, installed Linux, Apache, MySQL and PHP/Perl. Want SSH? *POOF* it's there. Same goes for SAMBA and the rest of the server packages. Missing a package apt-get it for crying out loud.

Servers aren't meant to have GUIs (well, not according to me anyways, one of my favorite server distros, TSL, is getting the whack job, I quit using it since 2.2), and it's that way for a reason. The less software installed, the more secure it is.

Example: I install Ubuntu 7.10 server on my home server. I only need two servers (SSH and SAMBA) and a downloading program to share files between my network (rTorrent). I have two ports open, SSH and rTorrent after I configure it. SAMBA may have internet security risks, but I doubt it, it's meant for LAN sharing. I have TWO potential exploits... now throw in a desktop, remote admin if you want to (SWAT, myPHPAdmin, Webmin, CPanel, ISPConfig, etc.) and you have CRAP TONS of holes to play with and try and secure.

Like I said... I don't like reviews, most of the time they're wrong, and only *MY* opinion matters. I like Ubuntu Server. I like the price, setup, features, etc.

---

### Post by MJN on 2007-11-27
And... relax. ;)
 
I intended the reference to be a source of kernel differences as it's a rather moot point if a review like this is right or wrong. It's a shame it's wrapped up in a overall review as it's sure to upset some people!
 
Mathew

---

### Post by Brazen on 2007-11-27
I am curious as to who you think does better documentation?  I support a few different distros, deb and rpm based, and almost always go to the Ubuntu documentation to find out how to do things on those other distros.

This is just one of the things I found completely wrong in that article, and I don't see how MJN agrees with it.

---

### Post by MJN on 2007-11-27
I'm only familiar with Debian and, to a lesser extent, Red Hat. It's the *official* documentation I (sometimes) have a problem with - the Ubuntu community docs are great (not to mention this forum - certainly the best I've seen).
 
You mentioned '..to find out how to do things' - that's not the sort of documentation under discussion so I dare say you've got the wrong end of the stick. ;) Rather, it's the information *about *the releases e.g. architectures, release breakdown and differences etc that's either missing or hard to find.
 
The review already gives specific examples (in part 1) of where documentation is lacking compared with Debian and Fedora so I won't paraphrase here.
 
Mathew
 
P.S. Maybe I should've just copied-and-pasted the kernel differences from the article as that was the primary information of interest!

---

### Post by MJN on 2007-11-27
I couldn't resist a quick test (trying not be biased!) and did a simple Google search for the release notes for the latest Ubuntu and Debian releases.
 
Compare the results:
 
[http://www.debian.org/releases/stable/i386/release-notes/](http://www.debian.org/releases/stable/i386/release-notes/)
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)
 
Now, as a Sys Admin I know _without doubt_ which set is of the most value to me (bearing in mind we are talking about Ubuntu *Server* here and the associated implications this carries).
 
Would you say those two docs are even in the same league?
 
Mathew

---

