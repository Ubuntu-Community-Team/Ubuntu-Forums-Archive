---
title: "On repositories"
date: 2007-05-04
forum: Repositories &amp; Backports
---

### Post by dellinger on 2007-05-04
These are just a few general questions rather than configuration help, so apologies if this isn't quite the right place to ask (if not, please tell me where this belongs). 

1. How does a particular program get into the repositories? Is it somehow based on community demand? Is there an approval committee? So far I have tended to trust the programs I install through synaptic, at least to not contain any malicious code. Going forward, I'd like to at least understand what criteria got them there before I install them.

2. Besides things such as media codecs or proprietary software/drivers which may have legal implications, what exactly differentiates a package that is in the restricted repositories vs one that is the main one(s)?

3. Before switching to Kubuntu, I tried 2 RPM-based distros. So far with Kubuntu (5 months), I haven't had any problems with dependencies, much unlike my previous distros. Is there a specific advantage to .dep packages that make managing packages and dependencies easier? Or does Ubuntu just have more extensive repositories? Or was I just clueless (a strong possibility :) ?

Thanks!

---

### Post by dfreer on 2007-05-04
I'm kinda tired so I don't have any links for you to click on, this is off the top of my head.

(1) you have to register as a developer on ubuntu somewhere (for official repositories), and submit your package (following pretty strict guidelines). I dunno from there, but I'm pretty sure all the official packages are checked for rootkits and the like, also I don't think that Ubuntu *approves* if a package can make it in based on the program itself (like let's say you made a new media player. I do not think it would be rejected on the basis of "We think your media player sucks/we have too many media players/we just don't like you").

(2) I believe the restricted/multiverse/universe repositories all have to do with liscensing, the main pure repositories only include OSS software, and even then it has to be under a certain copyright. Mainly ubuntu just wants to be a pure open-source driven OS, so it doesn't like to included stuff that isn't completely free to use/modify/redistribute.

(3) I haven't used an RPM distro for about 2-3 years, from what I understand of it Fedora Core and Yum have made things easier. But the main difference is that in order for a package to be in the repository, all of it's dependencies need to be in there along with there depends, and so on. On red hat I remember downloading xine for the first time from another computer on dialup and putting it on a floppy (or CD can't remember) to install it, only to sadly learn it needed 3 or more programs. I then ran back downstairs, downloaded those, brought them back up only to cry and learn that those 3 were dependent on like 50 others. I gave up red hat that day :( RPM's and .DEBs aren't really that different from what I understand of things, the main problem was that red hat didn't provide an easy and central way for users to download a package and it's depends.

---

### Post by dellinger on 2007-05-04
Thanks, that clears a lot up.

---

### Post by szabgab on 2007-05-06
Maybe this post can be of help: [http://ubuntuforums.org/showthread.php?t=414355](http://ubuntuforums.org/showthread.php?t=414355)

---

