---
title: "Lost my password to log on, what do i do?"
date: 2008-07-18
forum: Security
---

### Post by sugarplumfairy on 2008-07-18
I've forgotten my password, what the hell do i do??
I read a way to reset it, but i'm worried 
a. it will delete my account and all my information
b. it willd elete everyone elsesa ccounts
or 
c. it will delete everyone's passwords but retain their accounts and the rest of my family will presume i'm hacking into their accounts. 

You can see i'm new to this.

---

### Post by ViRMiN on 2008-07-18
Boot up in either rescue mode or off a live CD and mount you drives.  Replace the entry alongside your username in /etc/shadow which begins with $1 with this (you need to be root to do this):

$1$QKy.GVA3$1fIwfNQDCNYpYhWpmnYad0

Reboot, and login with the password, "password".  Then change it to something a bit more secure.  That should get you back up and running :)

---

### Post by sisco311 on 2008-07-18
Reboot in recovery mode and change
your password from the root shell:
```
passwd YOURUSERNAME
exit
```

The passwd command will change the password
for your user account.

a.) no
b.) no
c.) no

---

### Post by ViRMiN on 2008-07-18
"sisco311"'s method's much simpler! :D

---

### Post by Morty007 on 2008-07-18
I've always wondered about this, thanks for posting sisco311

---

### Post by ViRMiN on 2008-07-18
I'm a little more used to taking over "foreign" machines where you don't have the option of "rescue" options... I overly complicated the situation.  Thanks to "sisco311" for simplifying the task! :)

---

