---
title: "System Encryption?"
date: 2010-06-21
forum: Security
---

### Post by GrantStoner on 2010-06-21
I was wondering if there's any way to encrypt my entire drive except /boot ***WITHOUT*** using the Alternate CD? I'm not completely savvy with running programs in the terminal, so anything with a GUI would be awesome. If there aren't any good ones with a GUI I'm sure I can learn to use it in the terminal. Any suggestions are welcome.

---

### Post by bodhi.zazen on 2010-06-21
> **GrantStoner said:**
> I was wondering if there's any way to encrypt my entire drive except /boot ***WITHOUT*** using the Alternate CD? I'm not completely savvy with running programs in the terminal, so anything with a GUI would be awesome. If there aren't any good ones with a GUI I'm sure I can learn to use it in the terminal. Any suggestions are welcome.

If you are wanting to install Ubuntu into an encrypted partition, the Alternate CD is by far the easiest solution.

If you wish, you can boot the desktop CD and manually install the necessary packages. You would then manually mount the encrypted partition and install via debootstrap, then modify the initrd. 

This link would get you started with that :

[http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/](http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/)

I am not aware of any graphical interface to do this.

Alternately you could install Fedora. Encrypt the installation is an option during the install.

---

### Post by GrantStoner on 2010-06-21
Thanks. I'm not looking to install Ubuntu into a partition that's already encrypted. I'm just trying to fully encrypt the Ubuntu I already have. There's no other programs for this?

---

### Post by bodhi.zazen on 2010-06-21
> **GrantStoner said:**
> Thanks. I'm not looking to install Ubuntu into a partition that's already encrypted. I'm just trying to fully encrypt the Ubuntu I already have. There's no other programs for this?

No, you can not do that (convert your current installation to an encrypted partition).

If you look at the links, you need to write random data to the partition -> then you create a crypt -> then you install.

The first two steps would destroy any data you have on the partition.

You can certainly back up your data and restore post install.

The other option would be to resize your current install, make a new partition, encrypt the partition, transfer the data.

You can use several tools, including ecryptfs and others, to encrypt your data.

---

