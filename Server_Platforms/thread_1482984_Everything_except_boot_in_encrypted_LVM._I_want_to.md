---
title: "Everything except /boot in encrypted LVM. I want to SSH in and give the password"
date: 2010-05-14
forum: Server Platforms
---

### Post by tnek on 2010-05-14
Hi,

I want to have /boot as an ext2 (I don't need journaling and I might want to undelete something) and all other partitions in an LVM.

When the server starts it will prompt me for the LVM password. I would like to be able to contact the server using SSH (or using another secure method) and tell the password. Since /usr/sbin and all the other partitions are inside the LVM I guess I have a problem?

Is it possible to setup something like this? The SSH session for the LVM authentication does not have to be a daemon. It can be something which just sits and waits until I connect and input the password. And then the "real" SSH deamon kicks in.

---

### Post by cdenley on 2010-05-14
[http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu](http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu)

---

### Post by psusi on 2010-05-14
You found the problem already.  Without the password being entered at the console, root can't be mounted so the system can't boot, so you can't start sshd.

Why don't you just worry about having /home encrypted and leave the root alone.

---

### Post by tnek on 2010-05-16
Thank you cdenley! I'll try that method.

Yes psusi, it's probably going too far. But it feels kind of good having everything encrypted. I'll try that route first, I'm going down with en encryption ship. :-)

---

