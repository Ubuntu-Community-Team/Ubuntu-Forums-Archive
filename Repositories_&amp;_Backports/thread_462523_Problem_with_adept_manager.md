---
title: "Problem with adept manager"
date: 2007-06-02
forum: Repositories &amp; Backports
---

### Post by Kagoul on 2007-06-02
Hello,

I installed kubuntu 7.04 and after I downloaded the updates, I get the following message whenever I run Adept manager :
> 
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
 
and there's no such process when I look into the process table,
any idea what could be causing these, 
I already checked into the french forum [http://forum.kubuntu-fr.org/viewtopic.php?id=124337](http://forum.kubuntu-fr.org/viewtopic.php?id=124337)
the ones that encountred the same problem had to format....
is it the only solution???

---

### Post by Kagoul on 2007-06-02
Hi 
I ran this command and it works ```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

:)

---

