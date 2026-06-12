---
title: "Gave up waiting for root device"
date: 2010-05-24
forum: Server Platforms
---

### Post by 110686 on 2010-05-24
Hello everyone,

When I was upgrading my system (ubuntu server edition) today from 8.10 to 10.04 (of course in small steps: upgrade version after version) everything seemed running smoothly. But when I restarted it, it gave an error message: Gave up waiting on root device. Screenshot of error and grub menu attached.

PS: I've read some information about it and applied the possible workaround given here: [http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904"). My system is very old and so is the HDD: it uses an IDE connector. Typing 'exit' doesn't work either.

---

### Post by chrone on 2010-06-19
> **110686 said:**
> Hello everyone,

When I was upgrading my system (ubuntu server edition) today from 8.10 to 10.04 (of course in small steps: upgrade version after version) everything seemed running smoothly. But when I restarted it, it gave an error message: Gave up waiting on root device. Screenshot of error and grub menu attached.

PS: I've read some information about it and applied the possible workaround given here: [http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904"). My system is very old and so is the HDD: it uses an IDE connector. Typing 'exit' doesn't work either.

by changing the root device UUID to your device path in the grub menu at first booting will solve this.

for example the root / filesystem is /dev/sda1, then remove the grub boot option (UUID=blablablabla) to /dev/sda1 and then press tab in the grub menu and enter and then press b to boot the drive.

after finally booting the system, go to terminal and then change the boot menu.lst: sudo nano /boot/grub/menu.lst

change the UUID=blablabla in grub boot option to /dev/sda1, save and exit. go: sudo update-grub

hope this will solve your problem. i just did it on ubuntu 9.10 using ext3 filesystem yesterday and it worked!

---

### Post by ichigo6420 on 2011-03-19
i have the same problem, but i don't understand your explanation... 
how do you change the root device to UUID?

---

### Post by Vegan on 2011-03-19
Probably be best to do a clean install given the mess you machine is in.

Hope you have backups of your files

---

### Post by ichigo6420 on 2011-03-19
how did you get to the grub menu? I tried but it didn't work

---

### Post by ichigo6420 on 2011-03-20
b

---

### Post by ichigo6420 on 2011-03-20
> **Vegan said:**
> Probably be best to do a clean install given the mess you machine is in.

Hope you have backups of your files


How do you do a clean install in this situation?

---

