---
title: "Autologin with Encrypted Drives"
date: 2012-07-29
forum: Security
---

### Post by kid1000002000 on 2012-07-29
Hi,

I have a file server that stores sensitive information on it. Because I use it sporadically, I like shutting down the machine when not in use. This machine has 2 2TB drives and a 120gb boot drive containing Ubuntu 12.10 LTS. I would like to be able to boot the server by issuing a WOL packet and have it set itself up on the network automatically. I also would like to have it's 2 big drives encrypted via truecrypt (or an alternative). If possible, I'd like for the bootable drive to have an encrypted home directory as well, but this is not a necessity. I've done a lot of googling but am not sure how my first question will affect the next two if it is all made automatic.

My questions are:
what is the best way to accomplish all of this, 
how can everything be automated so all I have to do is power on the machine, and
will your method still protect my data? E.g., **passwords must not be accessible **should someone steal the drives.

Thank you.

---

### Post by cryptotheslow on 2012-07-30
Autologin with encrypted drives defeats the purpose of encrypting them - that's if you could get some kind of automated login to work (maybe possible with LUKS and keyfiles).

Encryption only protects the drive's contents when powered off (or the partition is unmounted). If the system is up and running with the encrypted partition mounted then it is as vulnerable as any other unencrypted filesystem.

If you setup an autologin which mounts up the encrypted partitions automatically - then if your "opponent" gains physical access to your machine even in a powered off state, all they have to do is switch it on and wait for it to autologin. At which point everything is available to them in the clear.

If you have an exact scenario where an individual drive will be stolen from the machine whilst it's powered off, then I suppose you could use LUKS to encrypt the 2TB drives using keyfiles kept on the boot drive or even on a flash thumb-drive etc. If they took ~just~ one of the 2TB drives then it would be useless to them. But reality is they would probably wander off with all three drives and the flash thumb-drive if present.

---

### Post by BkkBonanza on 2012-07-30
If you're going to manually turn power on then there's no point using WOL. The idea with WOL is to be to boot up with just a magic packet across the network.

Now given you do WOL you could boot the system remotely to a small drive which could even be just a flash stick. At that point it waits for your login (or your script to login) that authenticates and mounts the encrypted drives. Doing it this way doesn't negate having the encrypted drives.

---

