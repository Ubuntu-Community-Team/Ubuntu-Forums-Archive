---
title: "print server with dapper?"
date: 2007-02-18
forum: Server Platforms
---

### Post by 95aspire on 2007-02-18
ok i have a lexmark x2350 inkjet printer/scanner combo, i want to network this printer so that my sisters laptop, on wireless, can print without having to run the cable across the room to hook it up lol. 

what software would i have to install, and how would i get a driver for this printer for linux? thanks for any help guys i did a quick search but found nothing of what id have to do to do this, and im gettin rdy to walk out the door, so figured id post and see if yall can get some advice while im gone.

THANKS IN ADVANCE ALL



btw this is a great forum, thanks to everyone thats helped me so far.

---

### Post by polc1410 on 2007-02-18
OK - you don't say if lappy is Win or Linux (or Mac).

Assuming she's on Windows - you need to install SAMBA (and CUPS) - have a search of the forum there are some howto's  - you'll need them

She then prints to it as a windows network printer. (Samba is a windows networking server).

First step would be to get the lexmark setup under cups then think bout samba.

No idea about lexmark under linux (was bad enough under windows from my experience!)

---

### Post by 95aspire on 2007-02-18
ok well i have samba installed, first ive heard of this cups, let me search.

---

### Post by nix4me on 2007-02-18
samba is not required.  Only CUPS.  You need to setup CUPS and then set the windows computers to print via IPP.  Check the wiki for print server instructions.

nix4me

---

