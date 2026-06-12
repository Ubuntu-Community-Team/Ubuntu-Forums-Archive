---
title: "install fails at grub boot loader"
date: 2010-02-26
forum: Server Platforms
---

### Post by tombutcher1990 on 2010-02-26
Hi guys

had a quick look through, but can't really find anything that relates.

firstly, i'm using the RAID1 setup, which is configured in the BIOS, as it is a HP Proliant server.

i have 2 500GB hard drives configured in a mirror.

when booting the install, it recognises this, and deals with it fine.

the problem is, when it gets to the section of installing the grub2 boot loader, it just stops and gives me the "ubuntu installer main menu" where if i select grub boot loader install it just loops back, and if i select LILO installer, it errors, saying an installation step failed.

any ideas on why this is happening please??

it has the option to skip installing boot loader, but then, can i get it to boot a different way? can i boot manually into the server install and then install GRUB and hope it works? can i install grub1 rather than grub2?

---

### Post by tombutcher1990 on 2010-02-26
don't know is this is any good, but i tried changing it to an ext3 partition and i still get the same problem!

---

### Post by altmiket on 2010-02-26
i have the same problem, on an HP Z800 workstation, using the intel raid bios with 2 disks in a mirror.  ubuntu 9.10 partitions and installs, but then craps out when it tries to install grub.

---

### Post by ICEB3AR on 2010-02-27
I had the same issue. But the Problem at me was that i used a Raid Card (Mylex Acceleraid 160) which driver is by default not compiled in the kernel. So i would have had to compile it into the kernel by hand or use Software Raid or something else.

Hope you get a step forward.

---

### Post by tombutcher1990 on 2010-02-27
hmm i guess it is because of the raid then

i tried using the raid setup in the setup guide that i was following. it didn't exactly work for me!! i don't really understand raid enough to know whats wrong though.

---

### Post by herbie_popnecker on 2010-03-09
Got the same error using my hardware array. Funny thing is, the Ubuntu desktop edition installs just fine.
And I thought it would be easier to add the desktop to a LAMP server than vice versa...

---

