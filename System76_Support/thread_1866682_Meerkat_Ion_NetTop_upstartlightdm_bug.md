---
title: "Meerkat Ion NetTop: upstart/lightdm bug"
date: 2011-10-21
forum: System76 Support
---

### Post by Schluppy on 2011-10-21
My Mother had the Meerkat Ion NetTop delivered today. Everything went smoothly - ordering, shipping, set-up, and configuration - until reboot. I don't recall the exact error but it was something about upstart and the lightdm job being already started. The error left her unable to log in - just a black screen.

Anyways, should anyone else experience this, the fix was rather simple: Ctrl-Alt-F2, login, rm any files or folders under the /var/run/dbus/ folder, then reboot.

The hint came from [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810) - comment #17.

Probably needless to say, but this would have been a show stopper had she not had a relatively savvy Ubuntu user (me) nearby,

Nice kit BTW. We used Mom as the System76 guinea pig (the entire family uses Linux) and, aside from the bug, we're pretty impressed by the whole experience. So, there may very well be some more purchases in the future.

---

### Post by isantop on 2011-10-24
That's a pretty strange issue. I know there have been a few issues with Nvidia systems and race conditions, so I'll have a look to see if this could be related.

---

