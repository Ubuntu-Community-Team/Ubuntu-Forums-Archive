---
title: "installing server using hardware raid 0"
date: 2017-01-22
forum: Server Platforms
---

### Post by intertan on 2017-01-22
in order to get better read speed I upgraded from a single laptop drive to 2 ssd in raid 0. I'm not to worried about something happening as I have the important data on another backup.

hardware is a bit dated but I need something till I get the budget to build something new [current board]("http://www.gigabyte.com/products/product-page.aspx?pid=3768#ov") with a i5 2400. It has 2 sata6 and using the built in raid from intel.


I tried to install the desktop but got grub errors, switched to server and install seems to go fine but upon reboot just get a screen like it is checking the files/drives.

---

### Post by darkod on 2017-01-22
Not sure about now but earlier grub was not installing correctly on fakeraid (bios raid). You can try booting into live mode with the desktop cd and installing grub on the array mbr. Be careful to select the array mbr, not any of the partitions on it for grub destination.

---

### Post by intertan on 2017-01-22
guess I should mention I am using 16.04.1 64bit

raid like this is new to me. will be taking this hardware with me to figure it out, gone out of town and give me something to do while i have some free time

---

### Post by darkod on 2017-01-22
This is really outdated it seems, but it might be able to clear few points for you: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The basic is the same, you need grub installed to the MBR of the array device, not any of the partitions you created.

---

