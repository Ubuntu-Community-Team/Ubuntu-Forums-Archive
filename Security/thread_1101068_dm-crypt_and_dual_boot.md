---
title: "dm-crypt and dual boot"
date: 2009-03-19
forum: Security
---

### Post by street spirit on 2009-03-19
First of all I have to admit that I'm completely new to dm-crypt - I've never used device based encryption with Linux before, please bear with me.

I'm currently planning a reinstall of my laptop; the end result should be dual-booting an encrypted Windows XP installation and an encrypted Ubuntu Linux (probably Kubuntu 8.04 or 8.10). The XP side of this is actually a bit more complicated, but probably off-topic here. I've described what I'm going for in [this thread on the TrueCrypt forums]("http://forums.truecrypt.org/viewtopic.php?p=65648").

Question #1: Should I do all the Windows/TrueCrypt stuff before I start installing Ubuntu, or is it better to have Ubuntu in place first so that the TrueCrypt bootloader can find it?

Question #2: I have absolutely no idea how the whole device mapper / dm-crypt thing works. The way I understand it, I can take a single physical partition (/dev/sda3) and let the mapper create swap, /home, and / for me. A friend told me that the alternate installer disk for Intrepid can do that out of the box, is that correct? If there is a better way, or if I should do the partitioning manually, is there a good tutorial or how-to out there?

Thanks in advance,
street spirit

---

### Post by hyper_ch on 2009-03-20
[http://blog.redinnovation.com/2008/07/15/perfect-dual-boot-crypted-hard-disk-setup-with-truecrypt-and-luks/](http://blog.redinnovation.com/2008/07/15/perfect-dual-boot-crypted-hard-disk-setup-with-truecrypt-and-luks/)

That way you can setup an encrypted windows and encrypted linux.

It's rather easy once you know how.

Well, with luks/dm-crypt you create an encrypted block device (usually a partition). Then to make it "transparent" you need to enter your key and a mapper is created. And finally it's the mapper that then gets mounted in the filesystem tree.

There's one difficulty in this process. usuall the /etc/crypttab contains the list of encrypted devices and the mapper names which will then be used by /etc/fstab. Of course that is also encrypted. So linux needs to create an initrd that already contains information to unlock "/" and hence gain access to /etc/crypttab and /etc/fstab.

As for swap, it will be encrypted with a random key. But as normal swap it also requires an own partition. If you don't want to use the installer default setup (e.g. just one / partition and a swap partition) you need to manually set it up. It's simple actually, except that there's still a bug in 8.04 and 8.10 about the random key for swap.

Here's my little howto for manual encryption (selecting mount points, sizes etc.):  [http://ubuntuforums.org/showthread.php?t=848691](http://ubuntuforums.org/showthread.php?t=848691)

You might also find those here interesting: [http://ubuntuforums.org/showthread.php?t=837416](http://ubuntuforums.org/showthread.php?t=837416) and [http://ubuntuforums.org/showthread.php?t=829768](http://ubuntuforums.org/showthread.php?t=829768)

---

### Post by street spirit on 2009-03-20
Thanks, hyper_ch, your reply has been very helpful to me. The link to [Martti Kuparinen's article]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html") was especially valuable - it practically walked me through the whole process of creating the encrypted device, the volume group, and the logical volumes. I was going to encrypt the whole system anyway, not only /home, because you never know where sensitive data might show up (in /etc, /var, /srv, /tmp, and non-standard places like /backup).

The only problem I encountered was that I somehow missed the option that tells the installer where to put GRUB. So I accidently let it overwrite the MBR on /dev/sda and had to use the TrueCrypt rescue disk to restore the TC boot loader. I also had to relocate GRUB to its intended place with 'grub-install /dev/sda3'.

One more thing to watch out for: somewhere along the way the 'bootable' flag was removed from /dev/sda1. This caused weird behavior from the TC loader: it asked for the decoy system's password, then sent me to the GRUB bootloader, and it refused to accept the hidden system's password. So (for the archives) if that happens to you, check if the Windows partition is still marked as bootable, and reset it with fdisk if necessary.

All in all, this setup is working very well (in a virtual machine, for now), and was easy enough to get running.

On the other hand, I'm having second thoughts if I really need a hidden OS. I was curious how it would work out, but I don't really have a use for it at the moment. One definite disadvantage of TC's hidden operating systems is that they won't let you write to any other partitions, not even encrypted ones. Only other hidden volumes can be mounted as writable. The manual describes this as a necessary security feature, but it sure makes things a lot more complicated.

Thanks again, I'm marking the thread solved now.
(EDIT: well, I would but there's no option for this anymore in the Thread Tools)

---

### Post by hyper_ch on 2009-03-21
just don't forget to also make backups onto encrypted devices of your valuable data :)

---

