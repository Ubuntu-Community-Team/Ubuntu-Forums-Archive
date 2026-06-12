---
title: "Sudo NOPASSWD not working...?"
date: 2006-02-23
forum: Server Platforms
---

### Post by IanWright on 2006-02-23
I'm trying to get Sudo to work without requring a password for a set of commands, I've had a search of the forums and tried all the things I've seen but it doesn't seem to be working... Was wondering if anyone can help.

I've got in it:

Defaults          !lecture,tty_tickets,!fqdn

root       ALL= (ALL) ALL
ipw101   ALL= PASSWD:ALL, NOPASSWD: /sbin/tc, /sbin/ifconfig, /usr/sbin/brctl

%admin ALL= (ALL) ALL

I've also tried: 
ipw101   ALL= NOPASSWD: /sbin/tc, /sbin/ifconfig, /usr/sbin/brctl

Neither seems to work, any suggestions anyone?

Thanks

---

### Post by nanotube on 2006-02-27
try:
```
ipw101 ALL= (ALL) NOPASSWD: /sbin/tc, /sbin/ifconfig, /usr/sbin/brctl
```

---

### Post by mlind on 2006-03-08
NOPASSWD entries must be the last ones on sudoers file. That admin group entry is
probably overwriting your expression.

---

### Post by IanWright on 2006-03-14
Thanks mlind, that was the problem :)

Wish I'd have known that before! I hate being new to Linux :(

---

### Post by Darkriser on 2006-03-14
[QUOTE=IanWright]I hate being new to Linux :([/QUOTE]

Hm...I LOVE to be new to linux - so many new things, so many surprises, so many miracles, such a great feeling if I succeed solving another small problem from the huge heap I have ;)

---

### Post by quinreis on 2007-11-30
I have been trying to solve the same problem. The trick seems to be to put the NOPASSWD lines at the *end* of the file. Good luck.

---

