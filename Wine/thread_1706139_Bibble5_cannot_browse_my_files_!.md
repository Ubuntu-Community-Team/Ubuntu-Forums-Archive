---
title: "Bibble5 cannot browse my files !"
date: 2011-03-13
forum: Wine
---

### Post by rostamiani on 2011-03-13
Hi

I installed Bibble5 in mu UBUNTU 10.10 using wine 1.2.1
Every thing is perfect but I Bibble5 just shows the files on my Desktop at Directory View :lolflag:

In windows Desktop involes My Computer and all files ... but here is just my desktop !!!

How Can I browse all of my partitions ?

Thanks :)

---

### Post by cogadh on 2011-03-13
You need to configure Wine to "see" directories and partitions other than your home directory. Run winecfg and go to the Drives tab, then just add the drives you need/want. NOTE: It's not really a good idea to give Wine access to the root of your Linux drive. Wine can't really do anything with it anyway, but it opens a massive potential security hole in your system.

---

### Post by rostamiani on 2011-03-13
Thanks a lot
The / is added to the drives ... but Bibble stil can't browse my files !
I attached some screenshots

---

### Post by cogadh on 2011-03-13
Something is not right there. Your entire home directory, except for the winetricks cache, has been excluded. Also, adding "/" is the exact potential security hole I was talking about. Remove that and add "/home/<your username>/" and you should be able to access those files. Alternatively, you could just move the files from your desktop into the directory where Wine has the app installed and it should find them normally.

---

