---
title: "Unmet Dependencies for pbuilder-satisfydepends-dummy"
date: 2009-10-27
forum: Ubuntu Backports
---

### Post by Drunky on 2009-10-27
_The Goal_
I am attempting to backport several apps for Ubuntu Studio 8.04.  This will provide later versions of JACK and Ardour and also add fire wire driver support via libffado.

_The Problem_
While using prevu to build jack-audio-connection-kit-0.116.1 pbuilder-satisfydepends-dummy has an unmet dependency of libcelt-dev.

I looked and 0.109.1 does not include this library but 0.116.1 lists it for a build-depends.

_The Question_
I'm frightening new and ignorant to building packages (I've done it a few times by hand for libffado and JACK) so I would like some advice to avoid a dead end.

Therefore I'm wondering what the best approach would be to solve this problem.

I could build CELT with prevu first, but would this cause any problems for the typical Ubuntu Studio Hardy user because CELT is not available for Hardy in the repositories?  Or would JACK just have additional capabilities that Hardy users would not be able to use?

Should I remove the libcelt-dev from the build-depends in the control file?  Wouldn't I have to update the changelog and have a new version number for the package?

Is there another, more subtle answer?

Thank you in advance.

P.S. I am aware that 8.04LTS will be supplanted by 10.04 in six months.  But I want to learn the backports now so that I can help maintain other LTS versions in the future for the Ubuntu Studio dev group.

---

### Post by Drunky on 2009-11-19
I ended up building CELT first for libcelt-dev in order build JACK.

I rationalized that it was easiest (and most educational) to build CELT first.  Including CELT capabilities (which should only be used for netjack if I'm not mistaken) for most JACK users would be a problem I thought.

I was mistaken about the changelog though.  I needed to update it anyway to the backport and for building it in my ppa.

All in all, it was a smashing success and the results can be found here:
[http://ubuntuforums.org/showthread.php?t=1323550](http://ubuntuforums.org/showthread.php?t=1323550)

If I can provide any assistance to anyone else please contact me.

---

