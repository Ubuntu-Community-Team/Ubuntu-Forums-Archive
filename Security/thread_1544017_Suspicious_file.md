---
title: "Suspicious file"
date: 2010-08-01
forum: Security
---

### Post by Deltachord on 2010-08-01
Hello,

I ran a chkrootkit scan and found this:  The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.8/.autoreg /usr/lib/firefox-3.6.8/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo

How do I get rid of this suspicious file? I 'm not that technical. Help.

---

### Post by uRock on 2010-08-02
Those files are normal files. I am sure that they are mostly every ubuntu 10.04 install.

---

### Post by Deltachord on 2010-08-02
Thank you. It said the file was suspicious, so I thought it probably was. Thanks again.

---

### Post by uRock on 2010-08-02
```
root@rabbit-desktop:~# ls -l /usr/lib/jvm/.java-6-openjdk.jinfo
-rw-r--r-- 1 root root 2313 2010-07-17 20:05 /usr/lib/jvm/.java-6-openjdk.jinfo

root@rabbit-desktop:~# ls -l /usr/lib/firefox-3.6.8/.autoreg
-rw-r--r-- 1 root root 0 2010-07-27 06:34 /usr/lib/firefox-3.6.8/.autoreg

root@rabbit-desktop:~# ls -l /usr/lib/xulrunner-1.9.2.8/.autoreg
-rw-r--r-- 1 root root 0 2010-07-27 06:34 /usr/lib/xulrunner-1.9.2.8/.autoreg

root@rabbit-desktop:~# ls -l /usr/lib/pymodules/python2.6/.path
-rw-r--r-- 1 root root 74 2010-08-01 10:42 /usr/lib/pymodules/python2.6/.path
```All four of them are there.

No problem, I gave up on the root kit searches. every time it returned normal files claiming they were rootkits.

---

### Post by cariboo on 2010-08-02
This question has been asked and answered many times, please do some research before running any of the rootkit scanning tools. Both rkhunter and chkrootkit are both well know for generating false positives.

Seeing as the op's question was answered. This thread is closed

---

