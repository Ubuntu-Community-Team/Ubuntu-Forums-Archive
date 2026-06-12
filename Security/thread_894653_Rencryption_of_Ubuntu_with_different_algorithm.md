---
title: "Rencryption of Ubuntu with different algorithm?"
date: 2008-08-19
forum: Security
---

### Post by addison3 on 2008-08-19
Hello,

If I've got Ubuntu set up with dm_crypt for my home, root, and swap to be encrypted with a particular algorithm (blowfish, for example), is it possible to easily re-encrypt these partitions with a new algorithm (aes, for example)? Or would this require me to completely reinstall Ubuntu and select different algorithms during installation?

And a related question: is it possible to change my encryption passwords for my partitions if I'm in the habit of regularly changing passwords?

Thanks

---

### Post by hyper_ch on 2008-08-19
basically: complete reinstall

---

### Post by addison3 on 2008-08-19
> **hyper_ch said:**
> basically: complete reinstall

Both for changing the algorithm and changing my encryption password?

If I wanted to reinstall, could I just load the alternate cd, delete the ubuntu partitions, and reinstall? Will grub be automatically reconfigured after I delete the former ubuntu installation's partitions; will it recognize that the former ubuntu installation is no longer there and replace it with the new one? I assume my XP installation on a separate partition should be fine and grub will continue to allow me to boot into that?

Thanks for your walkthrough about installing ubuntu with encryption, btw; it was a big help!

---

### Post by hyper_ch on 2008-08-19
just for the algorithm... you can store up to 10 passwords/keyfiles that can unlock the encrypted drive.

---

### Post by addison3 on 2008-08-19
And to reinstall Ubuntu on my dual-boot machine with XP, could I use the method with the alternate CD described above? Will grub automatically recognize that one Ubuntu installation has been replaced by another?

---

