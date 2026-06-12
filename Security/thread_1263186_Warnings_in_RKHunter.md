---
title: "Warnings in RKHunter"
date: 2009-09-10
forum: Security
---

### Post by alexeix on 2009-09-10
Hi,

I've run rkhunter for the first time and it's produced a number of warnings.

Should I be concerned and what do they mean?

/usr/sbin/unhide                                  [ Warning ]
/usr/sbin/unhide-linux26                          [ Warning ]

Warning: Suspicious file types found in /dev:
[22:58:32]          /dev/shm/pulse-shm-1846995094: data

Thanks in advance!

---

### Post by cariboo on 2009-09-10
Both of those files are installed by rkhunter. The /dev/shm has to do with pulse audio.

---

### Post by unspawn on 2009-09-11
> **cariboo907 said:**
> Both of those files are installed by rkhunter. 
No they are not. If unsure please look things up before you post. [Rootkit Hunter]("http://ns2.canonical.com/karmic/rkhunter") and [Unhide]("http://ns2.canonical.com/karmic/unhide") are two different packages with different purposes. Also note the rkhunter.log will have details about these warnings, usually showing people did not install it.


> **cariboo907 said:**
> The /dev/shm has to do with pulse audio.
The **better** way is to show people how to find out the purpose of the file for themselves and how to get it rid of the FP (whitelisting in rkhunter.conf).

---

### Post by cariboo on 2009-09-11
Unhide and rkhunter are two different packages, but unhide is installed as a dependency of rkhunter, as for /dev/shm have a look at this [post]("http://ubuntuforums.org/showpost.php?p=4908163&postcount=5").

---

