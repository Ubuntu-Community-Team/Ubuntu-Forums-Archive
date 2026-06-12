---
title: "Revive JeOS builds?"
date: 2011-04-04
forum: Server Platforms
---

### Post by Datz on 2011-04-04
Hello,
I am interested in Ubuntu JeOS: [https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS) I think that ubuntu would benefit from a JeOS, like Debian's "netinst" where users could install a minimal system, and build it according to their needs.  It seems the latest builds are 8.04. [http://cdimage.ubuntu.com/jeos/releases/](http://cdimage.ubuntu.com/jeos/releases/)  

I was wondering if there was any way to revive these builds, or perhaps a tutorial aimed at transforming a 10.04 build into ubuntu-minimal could be created if not in existence.  

thanks
Datz

---

### Post by perspectoff on 2011-04-04
You can do a "Minimal Install" which is the same thing as the JeOS.

It's one of the installation options.

I think you can even download a "Minimal Install" LiveCD .iso.

---

### Post by samosamo on 2011-04-04
Are you doing this for virtual machines? Check out python-vm-builder

---

### Post by BkkBonanza on 2011-04-04
The Minimal Install ISOs are [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). They're much smaller than Jeos was so I assume you need to add a fair bit after the initial step, but these really give you a bare essentials start.

---

### Post by Datz on 2011-04-05
Yes, I am using the image for a VM. Thanks for your help guys, the minimal install iso is pretty much what I was looking for. Although the minimal is not set to a -virtual kernel by defaut it was easy enough to add. It is a small iso! :) I guess the minimal install grabs a lot from the net.
thanks again,
Datz

P.S. I've looked for the minimal install option on the server install cd, but never saw it.  Maybe I just keep overlooking it. (I'm also taking a look at python-vm-builder, thanks)

---

### Post by nutznboltz on 2011-06-02
> **Datz said:**
> Although the minimal is not set to a -virtual kernel by default it was easy enough to add.

I actually do not use -virtual kernels on my VM guests.

I could if I would use grub1 but grub2 fails with virtio disk see [LP: #604335]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604335") especially comments 12 and 13.

---

