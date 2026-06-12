---
title: "iSCSI targets automatically mounting on boot? Does it even work?"
date: 2016-01-10
forum: Server Platforms
---

### Post by Tripwirecc on 2016-01-10
I'm currently trying to get select iSCSI targets to mount when Linux boots. From all I've read, once you've done the target discovery, so that it creates the nodes in the /etc/iscsi/nodes directory, I'm almost set. Most tutorials and forum posts then say that you need to get node.startup to "automatic" on the relevant target nodes I want to mount. Except this does not work. At all.

At some point I went perusing the source code, the first thing I kind of found is that beyond parsing the various configuration files, there's no real handling of any manual and automatic options, and finally I landed on a FIXME section that suggests that the code supposed to handle this isn't even there.

Am I crazy or does node-startup=automatic indeed not do anything?

The only other option is using the discoveryd option, but it mounts all targets, and I don't really want that.

---

### Post by darkod on 2016-01-10
You are configuring the ubuntu server as Initiator, not as Target, correct?

If you are using the latest LTS (14.04), according to this the config file is /etc/iscsi/iscsi.conf: [https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

Also don't forget that iscsi only presents the disk (target), you still need to configure /etc/fstab to have an entry for auto mounting that disk. Maybe this is what you're missing?

---

