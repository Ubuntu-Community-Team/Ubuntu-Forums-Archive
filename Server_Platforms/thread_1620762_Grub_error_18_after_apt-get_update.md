---
title: "Grub error 18 after apt-get update"
date: 2010-11-13
forum: Server Platforms
---

### Post by jmidgley on 2010-11-13
Hi

I had to restart my server after it became unstable - strange things like couldn't connect from a Windows machine, becoming unresponsive. When it rebooted, it failed with grub error 18 (this after the machine has been fine for some considerable time, including rebooting).

I ran apt-get upgrade shortly before my problems started, and google suggests that I'm not the only one to get this error after apt-get upgrade, but I can't find a solution.

I really, really don't want to have to rebuild this machine! I can get in using the recover a broken system option on the install CD - the disk seems fine.


Any idea what I'd have to fix to get this working again?

Many thanks
John

---

### Post by jmidgley on 2010-11-13
Hi

Further exploration - the boot directory seems to point to nothing. I get 'cannot access boot - i/o error'. Does that point to an answer?

John

---

### Post by oldfred on 2010-11-13
this is the grub legacy error with some possible solutions. It usually is a new large hard drive that the BIOS does not support.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by jmidgley on 2010-11-13
Thanks for the reply - in this case, the machine has been running in this hardware configuration for about two years, with occasional Ubuntu version upgrades and numerous reboots without any problems.

When I do "ls -la" in the root directory, among the listing is the line:

d?????????     ?    ?    ?     ?   /boot

All the others are fine. This suggests that the boot directory has somehow been shredded in a peculiar way, along with everything that Ubuntu needs to boot - hence error 18?

Is there any way to rebuild a boot directory without re-installing everything?

John

---

### Post by oldfred on 2010-11-13
Is it a separate partition.

You might try this first. Change partition to yours.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

You should be able to reinstall grub and copy kernels from a chroot into system and update.

---

### Post by jmidgley on 2010-11-15
It is with some regret that I have to inform you that the hard disk is no more. It is defunct, deceased; in a word, dead.

Now, how to rebuild the damn thing with no documentation....

Thanks
John

---

### Post by oldfred on 2010-11-15
If it was just a boot drive, you should be able to install grub or grub2 and the kernels & initrd as that is all that a boot really is. But if it is old kernels you may have trouble downloading. Did you have any backups of the /boot?

I always ran this just to document my system as it in effect has a copy of grub.cfg or menu.lst, list of kernels, partitions sizes and details of start locations etc. But if the horse is out of the barn it may be a little late to close the door.:)

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

