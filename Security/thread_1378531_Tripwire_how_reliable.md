---
title: "Tripwire how reliable"
date: 2010-01-11
forum: Security
---

### Post by Victor43 on 2010-01-11
Does anyone know whether Tripwire can guard against rootkits and scripts which are saved as hidden files that make their way to the host file system via remote code execution using a browser vulnerability ?

Another words will Tripwire catch everything which comes via browser vulnerability ?

---

### Post by running_rabbit07 on 2010-01-11
Not sure about tripwire, but AppArmor is a great.

---

### Post by rookcifer on 2010-01-11
> **Victor43 said:**
> Does anyone know whether Tripwire can guard against rootkits and scripts which are saved as hidden files that make their way to the host file system via remote code execution using a browser vulnerability ?

Another words will Tripwire catch everything which comes via browser vulnerability ?

Tripwire is an IDS, and its purpose is to alert you to any suspicious changes in system owned filed.  Basically, you should install Tripwire upon a fresh installation of your linux distro of choice and then keep the image on a separate disk.  That way you can compare the clean image to the installation on your hard drive and see if anything suspicious has occurred.  

I think an IDS on a desktop box is overkill, and way more trouble than its worth.  I suggest you use AppArmor instead (which is a MAC system).

---

### Post by Victor43 on 2010-01-12
Thanks to both replies will take a look at AppArmor but still would not mind knowing how much of an effort would Tripwire be. 

Cheers

---

### Post by bodhi.zazen on 2010-01-12
Tripwire takes a fair amount of effort and upkeep. You need to keep the data base up to date every time you update the system or edit config files.

Tripwire watches known files and will not detect and additional hidden file.

I agree, tripwire is probably not the tool you want for this task.

[http://www.linuxjournal.com/article/8758](http://www.linuxjournal.com/article/8758)

---

