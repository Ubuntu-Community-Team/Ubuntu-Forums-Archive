---
title: "Automated fsck &amp; 'maintenance shell'"
date: 2009-03-08
forum: Server Platforms
---

### Post by bkm on 2009-03-08
Greetings,

Today one of my servers running Ubuntu 8.10 Intrepid unexpectedly lost power. (No UPS.. working on that as we're speaking)

First the system started in read-only mode, then after the reboot it was waiting for a root login in a 'maintenance shell'.

I don't have a KVM so I had to drive to the datacenter. For the future, is there any way to automate fsck in 'maintenance mode' and have it rebooted when there the disk is 'dirty' without having to log in? (So the machine is fully functional without user invervention)

Thanks in advance.

Sincerely,
BKM

---

### Post by mrsteveman1 on 2009-03-08
It is generally not a good idea to automate things that can drastically alter the disk, even fsck.

It might be a better idea for you to be able to login over ssh and run whatever you want. People with an encrypted root have this same problem, you kinda have to be there to type a passphrase or fix a dirty filesystem, unless you can ssh in. The idea is to put a small ssh server (dropbear) in the initramfs so that from a very early point you have ssh access to the system.

Check this out:

[http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu]("http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu")

---

### Post by bkm on 2009-03-09
Sounds like a good idea, thanks for your reply.

---

### Post by hyper_ch on 2009-03-09
I haven't tested that howto on 8.10 but it should work also. In the tutorials section here on UF I have also posted that howto. there have been some questions about different things, you might want to have a look at it now.

Someone also posted that the Ubuntu devs are looking into adding such a thing by default (it's also in the tutorial comments here).

---

