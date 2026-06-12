---
title: "What happened to _netdev? (12.04 LTS)"
date: 2013-04-15
forum: Server Platforms
---

### Post by zbethel on 2013-04-15
I've got some iscsi volumes I would like my 12.04 LTS server to mount at boot time. My /etc/fstab has something like this in it:

/dev/mapper/mpath1-part1 /mnt ext4 defaults,_netdev,auto 0 0

However, I'm getting tons of "mount: special device /dev/mapper/mpath1-part1 does not exist" errors sprinkled throughout my boot.log right up until the network devices are initialized. _netdev is supposed to delay mounting until this happens (at least it does on my RedHat servers), but it appears to be completely ignored in Ubuntu.

This post suggests that this functionality was recently broken or removed: [http://ubuntuforums.org/showthread.php?t=2131380](http://ubuntuforums.org/showthread.php?t=2131380) 

What gives? This is a mission critical feature for any production server needing to mount network devices. Is there a place I can file a bug about this behavior to get it fixed? Is it intended behavior? If so, what's the (correct) workaround?
Thanks.

---

