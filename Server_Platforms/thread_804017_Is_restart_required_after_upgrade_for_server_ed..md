---
title: "Is restart required after upgrade for server ed. ?"
date: 2008-05-22
forum: Server Platforms
---

### Post by Joel Duckworth on 2008-05-22
Hi, 

Does any know how to check if a restart is required after performing an upgrade from the command line?

I suspect that restarts are required for the same packages that require restarts on the desktop edition.

Thanks!

---

### Post by kidders on 2008-05-24
Hi there,

It would be unreasonable to *require* a reboot on a server. Having said that, there are some occasions when rebooting might be a good idea. For example, if an update installs a kernel fix you want to take advantage of right away, you'll often need to reboot in order to do so. Similarly, performing updates to certain system libraries could cause odd behaviour if you don't reboot, depending on what you've installed, and where the software came from.

In general though, restarting individual services impacted by an update (which the install process tends to do for you anyway) is sufficient.

I would say that server admins are expected to recognise situations where a reboot is necessary to keep their box happy. If in doubt, performing software updates on a scheduled basis (and always rebooting, regardless of what gets updated) is probably best. That way, your users can expect not to have access to your box's services for a few minutes, and the next time your server does something weird, you can be sure that it's not simply because you updated package X three months ago, and didn't reboot.

---

