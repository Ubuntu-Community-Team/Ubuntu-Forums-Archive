---
title: "Remove windows"
date: 2012-04-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clive littlewood on 2012-04-24
Hi All

A little bit of advice required please.

I have a dual boot 12.04 and win 7 and now wish to remove win 7.

I presume that this will be a simple re-partition to give Ubuntu all the drive, but am not sure what happens with grub after this.

Any help or links would be much appreciated.

Clive

---

### Post by dino99 on 2012-04-24
i suppose you have a single hdd on this system (/dev/sda), meaning grub is installed on it. Removing the w7 partitions will hurt the uuids and the bootloader will be lost. So be ready to boot on a livecd (liveusb) to reinstall grub

sudo grub-install /dev/sda
sudo update-grub

---

### Post by clive littlewood on 2012-04-24
Hi

Thanks dino99

Yes only 1 hdd on this machine.

If all else fails I have a backup of all data so can do a fresh install of 12.04.

Just wanted to try something different.    ;)

Clive

---

### Post by clive littlewood on 2012-04-24
Hi

Thanks dino everything OK      :p

Will mark as solved

Clive

---

### Post by YannBuntu on 2012-04-24
For information: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1328483594.png[/IMG]

---

