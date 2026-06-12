---
title: "rkhunter warnings for 10.04"
date: 2012-08-01
forum: Security
---

### Post by PeterB on 2012-08-01
For the last couple of weeks rkhunter has been emailing me this warning message. I have tried Google, checked the hashes, downloaded [http://packages.ubuntu.com/lucid/i386/procps](http://packages.ubuntu.com/lucid/i386/procps) and checked the hashes (they don't match either the current or the stored hash) per the thread at [http://forum.ubuntuusers.de/topic/rkhunter-warnmeldungen/](http://forum.ubuntuusers.de/topic/rkhunter-warnmeldungen/) -- the only other mention of this problem I can find on the web.

Is there an issue, and if so - given that dpkg is one of the warnings, how can I best fix?

```
Warning: The file properties have changed:
         File: /bin/kill
         Current hash: cfb465a12b8631d37bcedaf1666190981b313c1d
         Stored hash : 2526f22ed8a7cd7a967ca4dda75938083ab31557
         Current inode: 5931018    Stored inode: 5931034
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /bin/ps
         Current hash: cb1a06cdbecabf6c7949791cd45a3be08a4f17ac
         Stored hash : 1892268bf195ac118076b1b0f53e7a637eb6fbb3
         Current inode: 5931064    Stored inode: 5931066
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /usr/bin/dpkg
         Current hash: 45f0c273b3fceafb06f8c1926bf8d1e08303e63f
         Stored hash : 8293a33f45da47e2402e8094b2974803b7a756a0
         Current inode: 6587481    Stored inode: 6588086
         Current size: 227284    Stored size: 379700
         Current file modification time: 1319643588 (26-Oct-2011 16:39:48)
         Stored file modification time : 1294343030 (06-Jan-2011 19:43:50)
Warning: The file properties have changed:
         File: /usr/bin/dpkg-query
         Current hash: 263360daf9a19c45b11db66f5882f0caa083a8bd
         Stored hash : b1d3bb8a4e52865ea11d6a9860147620cf5cab15
         Current inode: 6587485    Stored inode: 6588097
         Current size: 104204    Stored size: 96172
         Current file modification time: 1319643588 (26-Oct-2011 16:39:48)
         Stored file modification time : 1294343030 (06-Jan-2011 19:43:50)
Warning: The file properties have changed:
         File: /usr/bin/ldd
         Current hash: f1e2ca5aa3a28994e2cebb64c993a72b7d97b28c
         Stored hash : 295d9cedb121a5e431a39a6d201ecd7ce5640497
         Current inode: 6586831    Stored inode: 6588002
         Current size: 5280    Stored size: 5279
         Current file modification time: 1331165514 (08-Mar-2012 00:11:54)
         Stored file modification time : 1295653965 (21-Jan-2011 23:52:45)
Warning: The file properties have changed:
         File: /usr/bin/pgrep
         Current hash: c79882a961dbb040b7644ea09f78c7e4b8f9ea18
         Stored hash : ce265d0db9964b173fe5036f703a9b8d66e55df3
         Current inode: 6586452    Stored inode: 8341234
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /usr/bin/sudo
         Current hash: 4ed0b135dcbd930c6ab713ccf288329782769fd9
         Stored hash : e708e94892e607fbb0b52318dc94845cb45a1205
         Current inode: 8344059    Stored inode: 8339510
         Current file modification time: 1337145936 (16-May-2012 06:25:36)
         Stored file modification time : 1295460070 (19-Jan-2011 18:01:10)
Warning: The file properties have changed:
         File: /usr/bin/top
         Current hash: fd3f600bc1cc692661f9a9ed4c34ceeb68ae5b98
         Stored hash : c7b495ecef3982eeb6f08a511861b1a1ae8775e6
         Current inode: 6586454    Stored inode: 8341199
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /usr/bin/vmstat
         Current hash: d3c3ad4900948f5800d55e3570abf932c11f8879
         Stored hash : 30eac3292345043bb03e134856016d4571daf68c
         Current inode: 6586453    Stored inode: 8341212
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /usr/bin/w
         Current hash: 6dd252a13a48e14b7d853af8784b18ae645a88b9
         Stored hash : e54c58e3a7119ff2f42e0415c10d9ee9a580ce3a
Warning: The file properties have changed:
         File: /usr/bin/watch
         Current hash: 3fd8cb14018adcdf1c00403074ef589e520762fe
         Stored hash : 43ceaf39fc42aa541fef4bd8fbbf6286cf6d856b
         Current inode: 6586437    Stored inode: 8341213
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /usr/bin/w.procps
         Current hash: 6dd252a13a48e14b7d853af8784b18ae645a88b9
         Stored hash : e54c58e3a7119ff2f42e0415c10d9ee9a580ce3a
         Current inode: 6586467    Stored inode: 8341266
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /sbin/sysctl
         Current hash: 670072340c870f79aac37a8aac331721e5453475
         Stored hash : 7804b99188776460a565c6fdd9ddddd1a9bc0f02
         Current inode: 2198548    Stored inode: 2195494
         Current file modification time: 1342492315 (17-Jul-2012 03:31:55)
         Stored file modification time : 1260992081 (16-Dec-2009 19:34:41)
Warning: The file properties have changed:
         File: /usr/sbin/cron
         Current hash: e783ca973f970aa8a4bf5edc670e690b33914c3d
         Stored hash : 4718257a8060736b9058aed025c992f02a74a5a7
         Current inode: 8340095    Stored inode: 6684875
         Current file modification time: 1330965568 (05-Mar-2012 16:39:28)
         Stored file modification time : 1271287741 (15-Apr-2010 00:29:01)
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Hidden file found: /dev/.blkid.tab: ASCII text
Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```

---

### Post by Ms. Daisy on 2012-08-01
Did you recently update the kernel?  If you didn't run another baseline then you'll get lots of false positives.

---

### Post by claracc on 2012-08-02
Take a look: [http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

---

### Post by PeterB on 2012-08-02
> **Ms. Daisy said:**
> Did you recently update the kernel?  If you didn't run another baseline then you'll get lots of false positives.

I did indeed, that could well be the reason!

---

