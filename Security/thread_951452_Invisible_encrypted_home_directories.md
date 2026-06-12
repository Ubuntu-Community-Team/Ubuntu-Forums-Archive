---
title: "Invisible encrypted home directories"
date: 2008-10-18
forum: Security
---

### Post by fommil on 2008-10-18
Hi all,

On Apple there is a feature called FileVault which converts your home directory into a virtual encrypted drive and automatically mounts it when you log in (the password is the same as your login password, enabling this behaviour). On logging out, various cleanup scripts are run to keep the virtual disk to a manageable size, and then it is dismounted. This offers very good protection against theft of the hardware if you are working with sensitive files (or are otherwise paranoid). Of course, it is only as strong as the password you choose.

On Ubuntu, it would appear that the TrueCrypt system enables something similar. However, I cannot find any reference to making this as invisible to the user as FileVault. Does anybody know how to enable encrypted home directories that are individually encrypted, and automatically mounted/unmounted on login/logout?

I could potentially spend a few days on this, hacking away on bash profiles and xinit files to popup a secondary password box and mount the drives from the command line... but that seems like serious overkill*(and not as user friendly). I'm really hoping somebody will say "yes, click the encrypted filesystem button in menu blah blah after installing package blah de blah" :-)

---

### Post by hyper_ch on 2008-10-18
you have fulldisk encryption available on the alternate and server disc and from 8.10 you have also home folder encryption available on alternate and server disc (not sure about desktop one).

---

### Post by stinger30au on 2008-10-18
there is a few programs in the repos that may interest you


one is called cryptkeeper the other gdecrypt

---

### Post by fommil on 2008-10-18
> **hyper_ch said:**
> you have fulldisk encryption available on the alternate and server disc and from 8.10 you have also home folder encryption available on alternate and server disc (not sure about desktop one).

The server home folder encryption sounds interesting! Odd that this should be considered a server, but not desktop feature. Does anybody know what is enabling the home folder encryption?

Full disk encryption is not an option as that involves setting up a complicated partition structure. I'm happy to use virtual disks and mount them to $HOME.

---

### Post by kevdog on 2008-10-18
Even though they may be encrypted, Im fairly certain at least the presence of an encrypted /home partition or any other partition could be detected.

---

