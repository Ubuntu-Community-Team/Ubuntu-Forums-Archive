---
title: "Full disk encryption without LVM?"
date: 2009-12-16
forum: Security
---

### Post by FuturePilot on 2009-12-16
I'm thinking of switching from Ecryptfs to just doing full disk encryption but I don't want to use LVM. I've been loosely following [this]("http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04") since the installer has changed slightly, but for the most part it's the same. Anyway, when I get my partitions all set up and configure the encrypted partitions, it wants to automatically assign one of them as swap. See the first screenshot. I want that to be my /home but for some reason it automatically assigned it as swap. Now when I try to change it to something else, it really doesn't give me too many options. See the second screen shot. Why is it doing that and how can I make it use that partition for my /home?

---

### Post by FuturePilot on 2009-12-19
Anyone?

---

### Post by Agent ME on 2009-12-19
Any reason that you don't want to use LVM? It doesn't really impact performance at all last I saw a benchmark, and it gives you the ability to resize partitions easily (and span them acrpss multiple hard drives).
Not really much help to the problem, but maybe the installer won't bug up if you choose the encryption with LVM option?

---

### Post by bodhi.zazen on 2009-12-19
Yes, you can do it (encryption) without LVM. Each partition will be a unique crypt (with LVM you can divide the crypt).

Just curious, may I ask, what is wrong with using LVM ?

---

### Post by FuturePilot on 2009-12-19
LVM adds a whole extra layer of complexity that I'd rather not deal with. If I would need to resize my partition it would be a major pain with LVM. If I understand things correctly, LVM will be pretty much obsoleted by file systems like BTRFS which have a lot of the features of LVM built into the file system.

---

### Post by bodhi.zazen on 2009-12-20
In general what you say is true, but, FYI, in this case LVM may actually make it easier.

First, crypts are not easily resized either, they are harder to resize then a LVM partition.

Second, if you use LUKS, you would have 3 in your cruuent scheme, One for / , one for swap, and one for /home.

Either way, it is possible to use LUKS without LVM =)

---

### Post by Gtklocker on 2009-12-20
Try LUKS.

---

### Post by FuturePilot on 2009-12-20
Ah, I figured out why the installer was giving me a hard time. I had selected "Random Key" instead of "Passphrase" when I was setting up the partition. Apparently when you select that option, it only lets you use the partition for certain things.

---

### Post by bodhi.zazen on 2009-12-20
> **FuturePilot said:**
> Ah, I figured out why the installer was giving me a hard time. I had selected "Random Key" instead of "Passphrase" when I was setting up the partition. Apparently when you select that option, it only lets you use the partition for certain things.

I agree, the Ubuntu installer is not so straight forward. glad you got it sorted =)

---

