---
title: "Workaround: Feisty as an OpenVZ guest."
date: 2007-05-27
forum: Server Platforms
---

### Post by eroper on 2007-05-27
Attempting to run Feisty under OpenVZ appears to be rather problematic at the moment. From what I've read, Edgy is also problematic, though I haven't done any testing with Edgy.

In short it appears as though upstart (the init replacement) doesn't play nice with OpenVZ. It appears to me as though it's a matter of opinion as to whether this is the fault of OpenVZ, or upstart. Frankly, I don't care where the fault lies, it doesn't work.

As a work-around: "apt-get install sysvinit". This will remove upstart and replace it with the old sysvinit, that does work under OpenVZ.

Obviously you'll have problems starting the guest in order to run the command, so I suggest you "chroot /path/to/vz/private/###/ /bin/bash" and then proceed to run apt-get.

As a note, I encountered various threads and discussions in bug trackers that offered various advice. I wasn't able to get anything to work, so this solution is what I reverted to.

I don't knokw what, if anything this will break, but it's probably better than it not working at all.

At the moment my hardware node is not running Ubuntu, so I can't help you with any advice on getting an OpenVZ enabled kernel running under Ubuntu.

---

### Post by humator on 2007-09-24
I've upgraded my VPS to Feisty and init process consumed all CPU time. I followed your advice and removed upstart, it has helped. I worry - how this can affect my future upgrades?

---

