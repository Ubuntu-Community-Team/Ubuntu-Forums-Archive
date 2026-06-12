---
title: "ardour problem with ulimit"
date: 2010-04-23
forum: Ubuntu Studio
---

### Post by shanehaua on 2010-04-23
Hi,
when i star ardour i get this warning.
"WARNING: Your system has a limit for maximum amount of locked memory. This might cause Ardour to run out of memory before your system runs out of memory. 

You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf"

when  i checked ulimit -l it came back at 64.

How do I reset it to unlimited?[/I]

---

### Post by trulan on 2010-04-24
```
sudo gedit /etc/security/limits.conf
```
find this line:
```
@audio - memlock 640000
```
and change the number, whatever it is, to unlimited, like this:
```
@audio   -  memlock    unlimited
```
Of course, then Jack will complain in the message window about it being unsafe to set memlock to unlimited.  You either have to ignore the warning from Jack or the warning from Ardour.  (I have my memlock set to unlimited and have never had a problem with it.)

---

### Post by shanehaua on 2010-04-25
Thanks, that bit works. Now just have to figure how to get ardour to play.

---

