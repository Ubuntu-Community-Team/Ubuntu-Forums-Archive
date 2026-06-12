---
title: "Karmic -&gt; Lucid not booting"
date: 2010-06-06
forum: Server Platforms
---

### Post by awacs on 2010-06-06
server configuration: SCSI 36gig -> sdd; boot and root as it was first in the box;
2 IDE hard drives -> sda/sdb for data; and
1 SATA drive -> sdc for data.

After upgrading to Lucid (not right away, but a bit later), it stopped booting:

'Gave up waiting for root device.'
ALERT! /dev/disk/by-uuid/........... does not exist. Dropping to a shell!
(initramfs)

Happily, pushing ^D let it resume booting, but it kept repeating. After some study, I found the Lucid release notes that said "if you upgrade to ext4, you have to manually update Grub". A quick check showed that sdd was now, indeed ext4 - nobody told me! And, why couldn't it update Grub by itself? But, I dutifully ran grub-install and life went back to normal.

Until last night, when I updated the kernel, etc. with apt-get and restarted, and grub dropped dead:

More googling turned up this solution, which I used with an install CD:
[http://tinyurl.com/2dhswzz](http://tinyurl.com/2dhswzz)

Which worked, but it brought back the first problem, and running grub-install doesn't fix it. So, what do I do now?

(dmesg upon request.)

Thanks!

---

### Post by oldfred on 2010-06-07
Check out this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by awacs on 2010-06-07
> **oldfred said:**
> Check out this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

I did, thanks. The grep return empty, no minix: magic string. The hexdump returned 1ced, which was not in the article. Dead end?

---

### Post by awacs on 2010-06-07
by the by, could changing back to ext3 (the original format) help? Is that even possible (without, ugh, reformatting)?

---

### Post by awacs on 2010-06-07
Uncommenting GRUB_DISABLE_LINUX_UUID=true in /etc/default/grub seems to have fixed the problem ... for now.

Of course, it just illustrates, in stark relief, just how little I know about grub2. Oh, well.

---

### Post by torrya01 on 2010-06-07
I have also encountered this, and a slightly different fix also might be of interest. It seems to affect newer Dell Poweredge servers.

I had to add the "rootdelay=60" to this line in /etc/default/grub. (Don't forget to run sudo update-grub after editing this file).

> GRUB_CMDLINE_LINUX_DEFAULT="quiet rootdelay=60"It seems that without this, Lucid is trying to mount the root filesystem before the hardware actually allows it to appear.

---

