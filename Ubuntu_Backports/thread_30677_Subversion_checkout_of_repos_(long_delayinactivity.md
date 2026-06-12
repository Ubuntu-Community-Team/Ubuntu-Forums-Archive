---
title: "Subversion checkout of repos (long delay/inactivity)"
date: 2005-04-29
forum: Ubuntu Backports
---

### Post by skoal on 2005-04-29
I'm trying to check out the repositories using subversion (part 2 of the cheat sheet) *for the first time*:

svn co [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) .

* I normally get ~250 KB/s download speeds with a 5Mbps pipe to the internet (and even right now am getting those speeds while using synaptic).  For some reason though, it's taking forever just to check these repos out.

Here's where I'm at now:

A  dists/hoary-extras/restricted/binary-i386/libdvdcss2_1.2.8-1~5.04ubp1_i386.deb

It's been over 1 hour now tyring to check out the repos, and I'm still waiting for it to end.  How long does it normally take for this process?

---

### Post by skoal on 2005-04-29
Whoa!  Man, I'm a moron.  I thought I was just checking out some sort of package setup files, not the entire source as well.  I now see why it's been over 2 hours and 1.2 G of hard drive usage and climbing.  I think I'll just let it finish overnite anyways.

When I was building packages for another distro, it was a simple matter of checking out the package files in *all* the repos (taking less than 1 minute for 1000+ packages).  Then, that package file would wget (from the supplied URL) any source for any *individual* packages I wanted to build.

Please ignore my original post.  oops!

---

### Post by jdong on 2005-04-30
First, make sure you know what you're doing :)

Checking out the repository fetches a copy of _ALL_ the packages in the Ubuntu Backports tree. You do **NOT** need to do this to build Backports, unless you have commit rights to the repository!

If you want to submit/contribute packages, all you need to do is build the sources against a cleanly installed Hoary (or chroot -- just make sure everything currently installed comes from Backports or Ubuntu) and e-mail the packages to me.


BTW, a working copy of the repository is currently priced at **10GB**! :)

---

### Post by skoal on 2005-04-30
Thanks for the reply.  I basically wanted to learn how to build packages in Ubuntu.  I've managed/built packages for my old distro so I'm familiar with most package management methods.

I realized shortly after my original post that I was checking out the entire backport repos.  Unless I'm missing something, they were only ~1.3 G and I checked them all out in about 2 hours.

skoal@morpheus:///data/ubuntu $ du -sh backports-arena/
1.3G    backports-arena/

I've read the Debian maintainers guide and some instructions/tools are missing or not applicable on Ubuntu (from what I gather, dh_make for example).  I'm learning it bit by bit and I'll get on the developers mailing list if I need help.  I've found what I basically need in these forums and the Debian documentation.

My goals:

1. Learn how to modify/change existing Ubuntu packages for my own custom needs.
2. Setup a local repo to manage them.
3. Create a package from scratch not currently in the Ubuntu repos.  I have one picked out already for that purpose.
4. Possibly contribute to Ubuntu with some of my packages, following the Debian maintainer policies/guidelines and through the proper Ubuntu channels, like you mention with an email.

* I've read/searched the Wiki, forums, and elsewhere for a guide *specific* to Ubuntu, not Debian.  My prior Debian experience is dated back 5+ years so I have some catching up to do.  I cannot seem to find one at present with my goals in mind.  If you know of one, please let me know.  I'd like to contribute in any way I can, and if nothing else, at least get more familiar with my Ubuntu system in the process.

Thanks.

---

### Post by jdong on 2005-04-30
All of the Debian Maintainer's guide still applies. dh_make, etc are available, but do need to be installed separately. When in doubt, use package.ubuntu.com to perform a file search.

Building a package has remained much unchanged from Debian to Ubuntu, but changed a bit from 5 years ago... ;)

---

### Post by skoal on 2005-04-30
Thank you sir.  One last question before I proceed with my first build.  I was about to install the 'fakeroot' package but I got some sort of warning:

WARNING: The following packages cannot be authenticated!
  fakeroot

I can't say I've seen that warning before while installing from multiverse, universe or other repos.  What does that mean?

By the way, feel free to move this thread to the recycling bin or another forum if necessary.  I didn't know where to originally post it and my original subject line is quite misleading.  My apologies.

Thanks.

---

### Post by jdong on 2005-04-30
It probably means it's a backport....

Backports are yet to be GPG-signed, mostly because:

1. **False Sense of Security** -- GPG sigs are useful when you have mirrors, and are afraid of mirrors tampering with the packages. There are NO Backports mirrors -- the only place to get them is backports.ubuntuforums.org, on a carefully administered and watched FreeBSD server. If that thing is compromised, what stops an attacker from just regenerating illegitimate signatures?

2. **Lack of time** -- I have very little free time to be playing around with GPG signatures...

I think it's better to leave the WARNING there, because it lets people know that they're installing from a 3rd party repository that isn't supported by Ubuntu, and should use their best judgement on whether or not to install the packages.

---

