---
title: "Raid 1, write-mostly flag lost on reboot"
date: 2011-09-24
forum: Server Platforms
---

### Post by Haaaaakon on 2011-09-24
Hi!

I've been googling around for almost at week without finding an answer to this...

I always lose the write-mostly flag on reboot. The raid is set up with something like this:
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 --write-mostly /dev/sdb1

The raid is created  and works well with the write-mostly flag but after a reboot it is lost. Am I supposed to do something with the mdadm.conf?

Entry added in mdadm.conf
ARRAY /dev/md/0 metadata=1.2 UUID=84af8bfe:0508d9b7:fd06affa:089630eb name=blabla:0

The only way I've found to put one disk/partition into write-mostly is to fail it, remove it and re-add it with --write-mostly, which would look really ugly in a startup script ;)

(Ubuntu Server 11.04 64-bit)

Hope someone can help me with this! Thanks :)

-H

---

