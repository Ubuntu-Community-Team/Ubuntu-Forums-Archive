---
title: "amanda backup"
date: 2009-07-16
forum: Server Platforms
---

### Post by bluethundr on 2009-07-16
I am trying to create amanda backups.

disregard the number lines, they are from a pastebin. :)

This is the config file I created with the help of how-to-forge

```

   1.
      tapecycle 6 tapes
   2.
      tapetype DISK
   3.
      tpchanger "chg-disk"
   4.
      changerfile "/etc/amanda/DailySet1/changer"
   5.
      tapedev "file:/var/dumps/amandatapes/DailySet1"
   6.
       
   7.
      define tapetype DISK {
   8.
         comment "Backup to HD"
   9.
         length 3072 mbytes
  10.
      }
  11.
       
  12.
      define dumptype root-tar {
  13.
         global
  14.
         comment "root partitions dumped with tar"
  15.
         compress client fast
  16.
         program "GNUTAR"
  17.
         strategy standard
  18.
         priority high
  19.
      }
```

yet when I go to label the "tapes" to use with amanda this is what I get:

```

   1.
      backup:~# for i in 1 2 3 4 5 6; do /usr/sbin/amlabel DailySet1 DailySet1-${i} slot ${i}; done
   2.
      "/etc/amanda/DailySet1/amanda.conf", line 13: dumptype parameter expected
   3.
      amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"
   4.
      "/etc/amanda/DailySet1/amanda.conf", line 13: dumptype parameter expected
   5.
      amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"
   6.
      "/etc/amanda/DailySet1/amanda.conf", line 13: dumptype parameter expected
   7.
      amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"
   8.
      "/etc/amanda/DailySet1/amanda.conf", line 13: dumptype parameter expected
   9.
      amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"
  10.
      "/etc/amanda/DailySet1/amanda.conf", line 13: dumptype parameter expected
  11.
      amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"
  12.
      "/etc/amanda/DailySet1/amanda.conf", line 13: dumptype parameter expected
  13.
      amlabel: errors processing config file "/etc/amanda/DailySet1/amanda.conf"
```


this was the guide I was trying to use

[http://www.howtoforge.com/disk_based_backups_amanda_debian_etch](http://www.howtoforge.com/disk_based_backups_amanda_debian_etch)

thanks

---

