---
title: "VMware Kernel Module Updater"
date: 2012-12-19
forum: Virtualisation
---

### Post by SpeedoJoe on 2012-12-19
VMware Workstation 9 doesn't seem to react very well to the latest kernel update.

[IMG]http://img.fae.ro/1f47e2.png[/IMG]

Has anyone else come across this?

---

### Post by SpeedoJoe on 2012-12-19
Solved.

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by dcstar on 2012-12-21
> **SpeedoJoe said:**
> Solved.


Then MARK the thread.

---

### Post by SpeedoJoe on 2012-12-21
> **dcstar said:**
> then mark the thread.

done,

---

### Post by mrgoodfox on 2013-03-03
> **SpeedoJoe said:**
> Solved.

```
sudo apt-get install linux-headers-`uname -r`
```

Here is a newbie question, am I replacing the **uname -r** with my ubuntu username?

---

### Post by Cheesemill on 2013-03-03
No you aren't.

Just copy and paste the exact text.

---

### Post by woxuxow on 2013-05-12
I've the same problem

sudo apt-get install linux-headers-3.8.0-19-generic

linux-headers-3.8.0-19-generic is already the newest version.
linux-headers-3.8.0-19-generic set to manually installed.

in /usr/src i have "linux-headers-3.8.0-19-generic" but vmware don't accept it

what should i do?where is linux-headers-3.8.0-19-generic? what path should i choose for vmware?

---

### Post by mnsky on 2013-05-13
> **woxuxow said:**
> I've the same problem

sudo apt-get install linux-headers-3.8.0-19-generic

linux-headers-3.8.0-19-generic is already the newest version.
linux-headers-3.8.0-19-generic set to manually installed.

in /usr/src i have "linux-headers-3.8.0-19-generic" but vmware don't accept it

what should i do?where is linux-headers-3.8.0-19-generic? what path should i choose for vmware?


I had the same problem today. Solved by updating VMware player from 5.0.1 to 5.0.2

---

### Post by specialalaa on 2013-05-13
> **woxuxow said:**
> I've the same problem

sudo apt-get install linux-headers-3.8.0-19-generic

linux-headers-3.8.0-19-generic is already the newest version.
linux-headers-3.8.0-19-generic set to manually installed.

in /usr/src i have "linux-headers-3.8.0-19-generic" but vmware don't accept it

what should i do?where is linux-headers-3.8.0-19-generic? what path should i choose for vmware?
I had the same problem, and here's how I fixed it. Create a script with the following: [http://paste.kde.org/677882/raw/](http://paste.kde.org/677882/raw/) and run it. VMware should work fine after that. (*This script was obtained from here: [http://ubuntuforums.org/showthread.php?t=2107900](http://ubuntuforums.org/showthread.php?t=2107900).)*

---

