---
title: "dpkg and apt vs. portage"
date: 2007-04-30
forum: Repositories &amp; Backports
---

### Post by Dolda2000 on 2007-04-30
Hi!

I'm a long time Gentoo user, but for a couple of reasons, I've been considering switching to Ubuntu as of late. Before thinking any further, though, I'd really appreciate if anyone could put the following issues to rest. I'm using Gentoo's portage a bit outside the standard behavior, and I'm concerned whether dpkg and apt will be able to do the same things. I know everything is *possible* ;), so the question is rather one of how easy it is. The most important ones are:

1) Is it easy to apply a couple of patches when building a deb package from sources?
2) Is it easy to keep a local APT repo with packages that override the official ones from Ubuntu (for packages that have been patched locally)?
3) Is it easy to rebuild packages with patches automatically whenever the master package from Ubuntu is updated? (I realize that there most likely is no shrink-wrapped process for this, but how easy is it to automatically fetch sources for building deb packages, and to detect master updates even in the presence of local overrides, etc.?)

Is there anyone else who has done any of these things and/or know about them? Also, where can I find general documentation about building deb packages from sources?

---

