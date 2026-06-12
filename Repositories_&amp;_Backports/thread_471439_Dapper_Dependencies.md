---
title: "Dapper Dependencies"
date: 2007-06-12
forum: Repositories &amp; Backports
---

### Post by OmahaVike on 2007-06-12
Any and all (and I truly mean this) help is greatly appreciated.

i am having extreme difficulty installing build-essential.  I have waded through all the dependencies, and the dependencies of those dependencies, and what I'm finding is that my libc6 is currently at version 2.4-1ubuntu12 and i need version 2.3.6-0ubuntu20.4 to install build-essential (or the thread of dependencies, anyway).

so, i go into synaptic and attempt to force the old version. upon doing so, synaptic warns me that it will uninstall the kitchen sink, the bathtub and all plumbing. just a quick glance at all of the uninstalls, and i quickly discover that this is a road i do not wish to traverse.

anyone have an idea of how we can roll back versions of libc6 without a minor thermonuclear detonation?

thanks once more for any and all help.

---

### Post by tgalati4 on 2007-06-12
What application are you trying to build?

Perhaps you can change the configuration parameters so ./config will accept the latest libc6 library.  It's a risk, but if the application works, then why worry about it.

I would rather have one doubtful application with untested dependencies than to trash your OS by rolling back.

---

### Post by OmahaVike on 2007-06-12
thanks for the reply, tgalati4.

i'm not building anything from scratch (this time), but rather trying to install AcetoneISO.  the .deb package looks for the build-essential dependency among other things.

i've tried building on my own (mythtv, hauppauge drivers) but gave up after i couldn't get the build-essential working.  i guess i have now been pushed over the edge.

since it's a .deb package, i'm assuming that i cannot simply edit a config file to force a higher version.  true or non?

i'm stumped.

---

