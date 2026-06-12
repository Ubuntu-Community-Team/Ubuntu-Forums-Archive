---
title: "security questions"
date: 2011-01-13
forum: Security
---

### Post by il lupo on 2011-01-13
i'm not completely new to Ubuntu, having used it for nearly a year, now.  i've  been reading a bit on security and have gotten these readings from rkhunter:

[10:46:33] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.

[10:49:13] Warning: Suspicious file types found in /dev:
[10:49:13]          /dev/shm/pulse-shm-2203584018: data
[10:49:13]          /dev/shm/pulse-shm-1809413362: data
[10:49:13]          /dev/shm/pulse-shm-3179628051: data
[10:49:13]          /dev/shm/pulse-shm-1249451809: data
[10:49:14]   Checking for hidden files and directories       [ Warning ]
[10:49:14] Warning: Hidden directory found: /etc/.java
[10:49:14] Warning: Hidden directory found: /dev/.udev
[10:49:14] Warning: Hidden directory found: /dev/.initramfs

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

and this from chkrootkit:

/usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/xulrunner-1.9.2.13/.autoreg /usr/lib/firefox-3.6.13/.autoreg

What constitutes 1) a suspicious file or directory and 2) a hidden directory?  If i opened, say, /etc/.java with any given text editor, how would i differentiate the Linux code from anything else?   i'm going to read a little more on rootkits and worms on my own, and i'd love to to know what anyone thinks my next steps ought to be.

Thank you,
il lupo

---

### Post by CharlesA on 2011-01-13
rkhunter throws back a ton of false positives.

I'd suggest reading the security sticky. :)

---

### Post by il lupo on 2011-01-13
Thanks for the reply, Charles.  i've read and bookmarked the suggested thread, which i should have seen initially.  Realizing, now, that this is truly an open project, i'll mark the thread as solved and return when my questions are more specific.

Thank you, again, Charles.
il lupo

---

### Post by fonsi2099 on 2011-09-05
many time, the CPU resources are used up to 80% and more after I run the rkhunter I get the following:
..
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.7/.path /usr/lib/pymodules/python2.7/PyQt4/uic/widget-plugins/.noinit
...

Do you think are the suspicious files the reason? or are they only false positives?
Thank you for any help!!

---

### Post by CharlesA on 2011-09-05
Those are false positives.

---

