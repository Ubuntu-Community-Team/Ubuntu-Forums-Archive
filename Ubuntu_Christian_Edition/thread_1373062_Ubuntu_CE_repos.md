---
title: "Ubuntu CE repos"
date: 2010-01-05
forum: Ubuntu Christian Edition
---

### Post by refdoc on 2010-01-05
Are the repos published anywhere and is it possible to use them without going the whole hog of a Ubuntu CE conversion? I.e. only make use of some of your packages and customisations?

Thanks

---

### Post by stlsaint on 2010-01-05
for 32bit this should work: 
deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_i386/


just add that to sources list and run in terminal: 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

NOTE: DK can either give correct repos or give ok on these...i am not currently in UCE so i cant give what i have...actually if you wait 5mins i will get you my entire sources list! :D

---

### Post by stlsaint on 2010-01-05
the reply i did above is correct...those are the uce repos...the ppa for crosswire is seperate though...if you were wondering about it. you can either add the repos via software sources or thru /etc/apt/sources.list manually.

---

### Post by jonathonblake on 2010-01-05
> **stlsaint said:**
> for 32bit this should work: 
deb [http://ubuntuce.com/repos/Ubuntu_CE/](http://ubuntuce.com/repos/Ubuntu_CE/) karmic_i386/  

Going by Software Sources, it looks like the 64 bit one is
[http://ubuntuce.com/repos/Ubuntu_CE/jaunty_amd/](http://ubuntuce.com/repos/Ubuntu_CE/jaunty_amd/)



jonathon

---

