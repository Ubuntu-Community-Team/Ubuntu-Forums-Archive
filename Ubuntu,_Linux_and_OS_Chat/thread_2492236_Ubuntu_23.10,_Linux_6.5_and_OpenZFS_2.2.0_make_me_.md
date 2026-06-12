---
title: "Ubuntu 23.10, Linux 6.5 and OpenZFS 2.2.0 make me happy :)"
date: 2023-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2023-11-04
I've  upgraded from 22.04 by reinstalling Ubuntu of course.  I boot my desktop  from OpenZFS and I like it now!  Unlike a few releases back, when Ubuntu-ZFS tried to solve all problems vaguely related to ZFS.  Ubuntu 23.10 is now behaving  more modest like FreeBSD and that made me **happy** :)

Today I did run  my first incremental backup of say 70 VMs and it finished within 10  minutes, that made me **very happy**, because with 22.04 it took 1 to 2  hours.  The difference; the transfer speed is now constantly between 80  and 105 MB/s, going from a desktop 2TB HDD to a laptop 2TB HDD. In  22.04 the speed dropped after some time occasionally to KB/s and even  sometimes for ~10 seconds all transfers were halted.  I wrote a bug  report, but I already did give up on it after 1.5 year.

During the  transfer to 23.10 I had problems with my 12 years old HP Elitebook 8460p (i5-2520M, 8GB DDR3), because  the BIOS had a warning about using its UEFI prototype, but in the end I  got it working booting from FAT32 (/boot/efi) and ext4 (/), note that  all my data and VMs are stored in OpenZFS.

Finally I have the **happy** feeling that the desktop system is more efficient with Ubuntu 23.10; Linux 6.5 and OpenZFS 2.2, the CPU load during my normal usage dropped from ~20% to ~18%.

---

