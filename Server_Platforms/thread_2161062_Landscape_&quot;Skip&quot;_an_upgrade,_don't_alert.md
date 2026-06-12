---
title: "Landscape: &quot;Skip&quot; an upgrade, don't alert again until newer upgrade released?"
date: 2013-07-09
forum: Server Platforms
---

### Post by libove on 2013-07-09
Hi ubuntu Forums Community,
I am looking for a patch management system for ubuntu Linux servers, with most of the functionality that Landscape offers (around package management), plus one really important thing that Landscape does not offer:
Sometimes a security-related upgrade will become available (that is, within the existing distribution e.g. 12.04, a package has a newer version released in one of ubuntu's production repositories), and I don't want to apply it.

Why would I not want to apply a security related upgrade? Because not all security bugs are actually a threat to all installations. Whereas all package upgrades (any kind of change) requires testing and could cause operational disruption. (It's rare, I agree, but it's possible).

So, augmenting the old advice a bit "If it ain't broke _in my particular environment_, don't fix it", when I receive an Alert from Landscape which says "security-related upgrade package-version-minor is available", I need to be able to select a server or an access group and mark that particular upgrade as "acknowledged, not to be installed, not to be further alerted until a yet newer version of the upgrade becomes available" (for that particular selected server[s] or access group[s]).

Reading the Landscape docs and talking with someone from Canonical, it seems that Landscape can't do this. It can be very roughly approximated with a fairly large amount of work by creating our own local mirrors of the repositories, and only adding upgraded packages to our local mirror when we feel that the upgrade should apply. But then we might have to create mutliple local mirrors (if, in some access groups, a particular security-related upgrade would apply, but in other of our access groups that same security-related upgrade would not be applied). And the effort of maintaining these local repositories would be high, plus the likelihood of making a mistake in managing those repositories is quite real.

Does someone know how to make Landscape do what I want? .. or know of another patch management tool (or service) for ubuntu servers to do it?

thanks,
Jay

---

### Post by f23 on 2013-07-31
Hello Jay,
  The way you would do this in Landscape is by creating a local package repository, mirroring the entire Ubuntu archive.  You would then create a second repository (serving your internal production set), and only have Landscape link packages into the production set that you want your managed devices to install.

  In this way, the alerts are always useful, and you can limit access to "unwanted" updates.

  Repository management is in the Landscape Dedicated Server API, with UI coming soon. Landscape SAAS does not presently offer repo management.

  Hope this helps -F2

---

### Post by libove on 2013-07-31
Hi F2,
This is the one way which I know is possible to achieve what I'm looking for. However, it is absolutely not what I want, as it provokes more administration than should be necessary.
My decision unfortunately has to be that Landscape does not yet have a critical feature, to enable security conscious and change conservative businesses to patch for only RELEVANT security issues as relate to their own environment. (And please do not open a discussion regarding "A future change could make it relevant". Yes, it could. That's what change control is all about; this is about a needed feature in a patch management solution).
thank you,

---

