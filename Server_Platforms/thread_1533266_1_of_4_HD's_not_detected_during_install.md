---
title: "1 of 4 HD's not detected during install"
date: 2010-07-17
forum: Server Platforms
---

### Post by supdawg on 2010-07-17
Hello all, I'm trying to install Ubuntu Server 64 Bit on a server I have built for a friend.

I have 4x1TB, but only three drives are seen by the partioner during install: sda, sdc, sdd. 

dmesg shows that sdb is detected.
fdisk recognizes /dev/sdb. 

I have tried to zero the MBR, but it has not helped. There must be another step to take, but I don't know what else to try. Any thing else to try?

---

### Post by _Mark_ on 2010-07-17
In a terminal
> sudo apt-get remove dmraid

Then run the installer again

---

### Post by supdawg on 2010-07-17
So you're saying install to one of the drives (/dev/sda for example), then remove dmraid, then install again?

Update: As expected, that did nothing. Guess I can always use CTRL ALT F2 to get busy box and then do the partitions via command-line.

Update 2: SOLVED. 
> sudo dmraid -x 
Ran the installer again and all my 4 of my SATA drives are there. This might be an obvious fix, but it took me a while to get there. The big clue was 
> sudo dmraid -r 
Which returned some error message.

Hopefully someone else will find this useful.

---

