---
title: "I might have been rooted, pleace help."
date: 2011-05-24
forum: Security
---

### Post by m-momr on 2011-05-24
the rkhunter gives me this output:

```
System checks summary
=====================

File properties checks...
    Files checked: 134
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 245
    Possible rootkits: 3
    Rootkit names    : AjaKit Rootkit, Optic Kit (Tux) Worm, Tuxtendo Rootkit

Applications checks...
    All checks skipped

The system checks took: 3 minutes and 39 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

```

now what? how do i remove the rootkits?
do i need a full format?

---

### Post by Irihapeti on 2011-05-24
Very likely, nothing is wrong. Rkhunter is notorious for false positives.

Search for "rkhunter" in this subforum and you'll find numerous examples.

If you are going to use it at all (I don't), it's best to learn more about how it works e.g. here: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter) Otherwise, you only scare yourself unnecessarily.

---

### Post by m-momr on 2011-05-24
> **Irihapeti said:**
> Very likely, nothing is wrong. Rkhunter is notorious for false positives.

Search for "rkhunter" in this subforum and you'll find numerous examples.

If you are going to use it at all (I don't), it's best to learn more about how it works e.g. here: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter) Otherwise, you only scare yourself unnecessarily.

ok, thats good to hear. 
I have upgraded from linux 8.xx, also i have fooled around alot with this box, so maybe that is influencing the scan.
i have always been focused on security, so i always install the latest updates.
i only have port 80 apache and 22 sshd running, and they have always been updated so unless there has been any 0day hacks that has not been pached quickly in last 3 years i don't think anyone has got a hold of my box :)

---

### Post by Irihapeti on 2011-05-24
If you make sure that you have apache and sshd secured properly, you should be fine.

BTW, sshd is one of the most popular (if you can call it that) ways that people get hacked, so it's probably a good idea to read the security stickies by bodhi.zazen to find out more about that.

---

### Post by m-momr on 2011-05-28
Ok, so i found out that the 3 warnings of rootkits was because the directory /dev/tux exists, and in this directory:
```
^Croot@tux:/dev/tux# ls -lah /dev/tux/
total 0
drwxr-xr-x  2 root root   80 2011-05-20 00:15 .
drwxr-xr-x 18 root root 3.9K 2011-05-20 00:15 ..
lrwxrwxrwx  1 root root   18 2011-05-20 00:15 root -> ../mapper/tux-root
lrwxrwxrwx  1 root root   20 2011-05-20 00:15 swap_1 -> ../mapper/tux-swap_1
root@tux:/dev/tux#

```
which i think has something to do with my lvm group is called tux :P
```
root@tux:/dev/tux# lvm
lvm> lvs
  LV     VG   Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root   tux  -wi-ao 148.13g
  swap_1 tux  -wi-ao 696.00m
lvm> pvs
  PV         VG   Fmt  Attr PSize   PFree
  /dev/sda1  tux  lvm2 a-   148.81g    0
lvm> vgs
  VG   #PV #LV #SN Attr   VSize   VFree
  tux    1   2   0 wz--n- 148.81g    0
lvm> exit
  Exiting.
root@tux:/dev/tux#

```

---

### Post by Soul-Sing on 2011-05-28
did you install tux writer software from sourceforge?

---

### Post by m-momr on 2011-05-29
> **leoquant said:**
> did you install tux writer software from sourceforge?

[http://sourceforge.net/projects/tuxwriter/]("http://sourceforge.net/projects/tuxwriter/")

> Tux Writer is a word processor geared towards young children. It provides a simple and kid-friendly interface, letting them get their work done -- be it a letter to grandma, or a school paper -- without being confused by lots of options.

Don't think so, why?

---

