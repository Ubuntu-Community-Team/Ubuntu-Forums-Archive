---
title: "how can I get crash report ?"
date: 2012-03-16
forum: Security
---

### Post by yavuz.maslak on 2012-03-16
Hello 

I use ubuntu11.10 server 64bit
my server crashed this morning. 
I can't see errors in its syslog or kernel.log. 
I had to push button to restart.
How can I see crash report?

in my boot.log;
 * Starting automatic crash report generation[ OK ]

---

### Post by mraandtux on 2012-03-16
See /var/log/ ?

---

### Post by yavuz.maslak on 2012-03-16
I can't see it in /var/log

ls -ltr /var/log/

-rw-r--r-- 1 root      root     253907 2012-03-16 06:16 udev
-rw-r--r-- 1 root      root       1021 2012-03-16 06:16 boot.log
-rw-r----- 1 root      adm       62031 2012-03-16 06:16 dmesg
-rw-r--r-- 1 root      root      10211 2012-03-16 06:16 Xorg.0.log
-rw-r----- 1 syslog    adm      185213 2012-03-16 06:16 kern.log


What should be its name ?

---

### Post by Diametric on 2012-03-16
If I'm not mistaken, if you're not seeing any error reporting in the boot.log file, the issue is happening prior to the syslog/kernel being loaded.  At that point, you'll have to check the out pit from your screen to see where the issue is.

Can someone confirm what I've stated, please?

Thanks, and good luck.

---

### Post by yavuz.maslak on 2012-03-16
because after I had to reboot by the servers button the server booted normaly but I could not see any errors in kernel.log and boot.log. Therefore I want to see crash report or another error log file.

---

### Post by cariboo on 2012-03-16
If an automatic crash report is created, check /var/crash. I'm running Precise, and I currently have two crash reports in that directory.

---

### Post by yavuz.maslak on 2012-03-17
i saw there.
but there is no file in the /var/crash

how can i supply the server make a crash report when it goes crash?

---

