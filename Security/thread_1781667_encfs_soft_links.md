---
title: "encfs soft links"
date: 2011-06-13
forum: Security
---

### Post by lister171254 on 2011-06-13
I´ve used encfs to encrypt directories on my other systems for quite some time without any problems, but have a weird problem on a brand new installation on a laptop.

Ubuntu Version 11.04/32Bit

I've create the the encrypted folder via Cryptkeeper.

I can list the contents of the folder from a terminal:

-------- Terminal output ------------

>> ls -lsa of my home
4 drwx------  5 llist llist  4096 2011-06-13 19:59 personal
4 drwx------  5 llist llist  4096 2011-06-13 19:59 .personal_encfs

llist@CompaqLaptop1:~$ ls -lsa personal/
total 20
4 drwx------  5 llist llist 4096 2011-06-13 19:59 .
4 drwxr-xr-x 36 llist llist 4096 2011-06-14 08:38 ..
4 drwxr-xr-x  3 llist llist 4096 2011-06-13 20:03 .config
4 drwxr-xr-x  3 llist llist 4096 2011-06-13 19:53 .gconf
4 drwxr-xr-x  3 llist llist 4096 2011-06-13 20:00 .local
----------------------------------------------------

I found the problem when I tried to soft link to a directory in personal. There are no errors when I link with

ln -sv personal/.config/evolution .config/evolution

when I list .config with ls -lsa .config/ I get

---------
4 drwxr-xr-x 10 llist llist 4096 2011-06-14 09:37 .
4 drwxr-xr-x 36 llist llist 4096 2011-06-14 08:38 ..
4 drwx------  2 llist llist 4096 2011-06-14 09:37 enchant
0 lrwxrwxrwx  1 llist llist   26 2011-06-13 20:04 evolution -> personal/.config/evolution
4 drwxr-xr-x  3 llist llist 4096 2011-06-13 11:37 gnome-disk-utility

----------------------------------

but when I list the folder with ls -lsaL .config/ I get

---------------
4 drwx------  2 llist llist 4096 2011-06-14 08:37 dconf
4 drwx------  2 llist llist 4096 2011-06-14 09:37 enchant
? l?????????  ? ?     ?        ?                ? evolution
4 drwxr-xr-x  3 llist llist 4096 2011-06-13 11:37 gnome-disk-utility
4 drwx------  3 llist llist 4096 2011-06-13 11:37 ibus
--------------------------------

Thanks

---

### Post by lister171254 on 2011-07-06
Bump

---

