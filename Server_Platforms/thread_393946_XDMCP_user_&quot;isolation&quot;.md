---
title: "XDMCP user &quot;isolation&quot;?"
date: 2007-03-26
forum: Server Platforms
---

### Post by ifeldt on 2007-03-26
I am attempting to have about 4 users connect to an XDMCP server. There is also 1 user locally on the machine.

Is there a way to "isolate" the users so that they don't see system related messages, either from the local account or each other?

As an example, if I do a system update via the "Update Manager", if a restart is required all the remote users see the pop up for the notification and have a chance to restart the machine. I would like this not to happen.

Also, is there a more granular control for locking down what the remote users have access to in terms of administration/system settings? I saw something in the "Users and Groups" settings when I created the users but it did not seem very extensive at all.

I would like to be able to disable update notifications, shutdown, sleep, network settings and things like that.

Any help would be most appreciated.

Thanks,

Ian Feldt

---

### Post by elst on 2007-03-26
The Sabayon utility lets you build custom desktops and apply them to accounts, so you can easily remove the admin utilities from user desktops that way. Ubuntu and Debian use groups to manage access to hardware resources, so you can completely block access to some resources by removing the appropriate accounts from the groups.

I don't know how the Update Manager notifications work, but it sounds like it would be worth filing a bug on Launchpad if there isn't a convenient way of turning them off for non-administrative users.

---

### Post by ifeldt on 2007-03-27
Sabayon is pretty cool, and just about exactly what I need. It is slightly buggy, but I'm sending in crash reports.

That was a great help elst, thanks.

Ian Feldt

---

