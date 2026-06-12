---
title: "Gnome 46."
date: 2024-02-13
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2024-02-13
Any idea when Gnome 46 alpha or beta will reach Ubuntu 24.04.  Currently using Gnome 45.3

Henry

---

### Post by corradoventu on 2024-02-14
according release schedule [https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649](https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649)
February 15 	GNOME 46 Beta 
March 21 	GNOME 46.0

---

### Post by Hewjr100 on 2024-02-14
Thank you corradoventu.

Henry

---

### Post by jbicha on 2024-02-14
GNOME 46 Beta for Ubuntu is a work in progress.

It was mentioned in this week's Desktop Team Integration Squad [update]("https://discourse.ubuntu.com/c/desktop/team-updates/23")

Most pieces of GNOME 46 Beta will be stuck in noble-proposed until glib2.0 migrates out of proposed which won't happen until python3-defaults migrates.

By the way, when gnome-control-center 46 Beta is installed, it will report the GNOME version as 46 in Settings > System > About > System Details since the GNOME version now comes from gnome-control-center itself and is rounded to the whole number so 46 Beta, 46.0, and 46.5 will all report "GNOME 46".

---

### Post by Hewjr100 on 2024-02-14
Thank you jbicha

Henry

---

### Post by vicshrike on 2024-02-14
Thank you people, looking forward to it.

---

### Post by Claus7 on 2024-02-24
Hello,

I can see gnome shell 46 in my system after latest updates. 

Regards!

---

### Post by jbicha on 2024-02-24
Settings > System > About > System Details now reports the GNOME version using the version number for gnome-control-center rounded to the whole number. gnome-control-center is now 46.beta in Ubuntu 24.04 LTS but gnome-shell is still 45.3. So the number is reported as 46 and that won't change for the lifetime of Ubuntu 24.04 LTS.

The GNOME Shell visual changes from 45 to 46 are more subtle than they were for the last several GNOME Shell releases.

---

### Post by Claus7 on 2024-02-25
Hello,

I do not know if rounding up is a nice idea. If I'm not mistaken e.g. 45.3 is still 45, irrespective if there are subtle -mostly visual- changes between 45 and 46 or 45.3 and 46. I suppose that there might be a confusion with extensions though.

If on the other hand for ~5 or even 10 years ubuntu will stick to 46 version I do not think that rounding down will cause any confusion.

Regards!

---

### Post by corradoventu on 2024-02-25
Instead of looking at Settings > System > About > System Details look at
```
corrado@corrado-n2-nn-0220:~$ apt policy gnome-shell
gnome-shell:
  Installed: 45.3-1ubuntu1
  Candidate: 45.3-1ubuntu1
  Version table:
 *** 45.3-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-n2-nn-0220:~$ 

```
or
```

corrado@corrado-n2-nn-0220:~$ inxi -Sxc
System:
  Host: corrado-n2-nn-0220 Kernel: 6.6.0-14-generic arch: x86_64 bits: 64
    compiler: gcc v: 13.2.0
  Desktop: GNOME v: 45.3 Distro: Ubuntu 24.04 (Noble Numbat)
corrado@corrado-n2-nn-0220:~$ 

```

---

