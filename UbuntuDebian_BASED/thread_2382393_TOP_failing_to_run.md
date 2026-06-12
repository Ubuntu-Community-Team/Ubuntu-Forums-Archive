---
title: "TOP failing to run"
date: 2018-01-12
forum: Ubuntu/Debian BASED
---

### Post by Geoff_Lane on 2018-01-12
Folks,

Appreciate this is not specific to Ubuntu but am sure some knowledgeable person may assist.

My main system is Ubuntu 16:04 but I have a number of Raspberry Pi devices on my network.

One such device has a relatively new installation of Raspian stretch, used only as a server so all contact via SSH from my Ubuntu machine and no monitor attached.

Currently got apache, SMB, minidlna running fine but ran command 'top' recently and got the following;
```

 
top: error while loading shared libraries: /lib/arm-linux-gnueabihf/libncurses.so.5: nonzero padding in e_ident

```
  On checking the directory this is the output of mentioned file;
```
 
lrwxrwxrwx 1 root root      17 Sep  7 17:05 libncurses.so.5 -> libncurses.so.5.9
-rw-r--r-- 1 root root  111976 Sep  7 17:05 libncurses.so.5.9
lrwxrwxrwx 1 root root      18 Sep  7 17:05 libncursesw.so.5 -> libncursesw.so.5.9
-rw-r--r-- 1 root root  157032 Sep  7 17:05 libncursesw.so.5.9

```

  So far all the popular commands seem to work and TOP is the first problem I have encountered.

I have naturally updated and upgraded etc but still same problem.

Any suggestions to resolve would be appreciated.

Geffers

---

### Post by howefield on 2018-01-12
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

