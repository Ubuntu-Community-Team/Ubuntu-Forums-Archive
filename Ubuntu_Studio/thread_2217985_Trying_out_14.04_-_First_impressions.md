---
title: "Trying out 14.04 - First impressions"
date: 2014-04-19
forum: Ubuntu Studio
---

### Post by brianmc on 2014-04-19
I threw Thursday's official release of 14.04 onto my spare box, but I'd recommend people read the [issues list]("http://ubuntustudio.org/2014/04/ubuntu-studio-14-04-lts-final-release-is-out/") before letting it near anything but a test/spare machine. This was a from-scratch install, and I'd assume most people would adopt a similar approach: keep /home on a separate partition, and lay down the latest software version around it.


[LIST]
[*]I didn't see anything in the installer allowing selective software installation; since it is referred to as a plugin, I'm not sure what I should expect to see. Didn't read the release notes to dig deeper into that one. 
[*]Glad to see lowlatency rolled into generic kernel maintenance; again, not checked release notes - simply assuming this is the ability to tweak relevant kernel options at boot. 
[*]If you're outside the US, those locale issues are going to be annoying. Not difficult to fix, just annoying until you do. 
[*]I'm glad I *didn't install it on a laptop,* that suspend bug sounds like a really unpleasant problem which could give people a fright. 
[*]The missing IBus didn't hit me due to a fresh install, *but lots of the locale-related stuff depends on IBus*. A range of settings still assume it's there - not that its been yanked from the distro. 
[/LIST]

I quite liked what I ended up with. It errored like hell after the first boot, significantly less-so once I'd put in the load of patches following on from Thursday's release. After that, I've patched together a 3.14.1-rt1 generic AMD kernel; which seems to work well, but a bit poorer on performance than my prior 3.12.XX-rtXX kernels on 13.10.

Depending on where kernel versioning goes, and how -rt keeps up, I suspect 14.04-1 will be the one to wait for if you're doing audio work. However, for a few-days-old release, it's pretty good.

---

