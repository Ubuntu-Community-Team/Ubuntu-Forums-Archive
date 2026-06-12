---
title: "Can we run wine safely in a non-sudo user account?"
date: 2011-11-08
forum: Security
---

### Post by clouddeer on 2011-11-08
Hi, Im new to ubuntu. 

I would like to run some windows programs that may contains virus under a non-sudo user "test". 

If it really contains virus, will it damage my whole ubuntu system? or just everything under the /home/test?

How can I config my system to limit the wine from accessing the files/disks outside a specific folder(such as /home/test)?

thanks

---

### Post by Elfy on 2011-11-08
Thread moved to Security Discussions.

There is a sticky here - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) - in which is a section on Wine

---

### Post by undecim on 2011-11-08
Usually, Windows Viruses can't infect Ubuntu systems. In fact, unless a virus is specifically made to target Linux computers through wine, I don't think it can even set itself to automatically start when the computer starts (as most Windows viruses will do)

So I would say that it's safe... I'd still scan it with virustotal.com first though. Wine programs can still access files in your home directory, so it's entirely possible for a Wine program to erase everything but your install programs.

EDIT: If you use a separate user account for Windows programs, then there is no way they can touch files you don't put onto that account.

---

### Post by clouddeer on 2011-11-10
> **undecim said:**
> Usually, Windows Viruses can't infect Ubuntu systems. In fact, unless a virus is specifically made to target Linux computers through wine, I don't think it can even set itself to automatically start when the computer starts (as most Windows viruses will do)

So I would say that it's safe... I'd still scan it with virustotal.com first though. Wine programs can still access files in your home directory, so it's entirely possible for a Wine program to erase everything but your install programs.

EDIT: If you use a separate user account for Windows programs, then there is no way they can touch files you don't put onto that account.

thanks for your reply.

So, I will create an user account for running wine.
If there is any problem, I can just handle it by removing everything under the user account?

---

### Post by clouddeer on 2011-11-10
> **forestpiskie said:**
> Thread moved to Security Discussions.

There is a sticky here - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) - in which is a section on Wine

thanks, solved

---

