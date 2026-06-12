---
title: "recover lost admin password"
date: 2009-04-07
forum: Security
---

### Post by LORD_PoLvO on 2009-04-07
hey all, i was wondering if its possible to recover a forgotten admin password ? ive been on a tour in East Timor for the past 6 months and come home to find i cant remember my administrator password which makes it hard for me to really do anything i cant use apt or anything like that anymore without my admin password and i really dont want to have to do a clean install is there anything i can do to recover the password ??

---

### Post by mhgsys on 2009-04-07
Hey, in this link there's information to recover your password.
Seems to me the passwd command will also work in recovery modes, but you
best read it yourself.

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

---

### Post by LORD_PoLvO on 2009-04-07
*slaps forehead* single-user-mode

instant root and then just use passwd...

why didnt i remember to do that in the first place thanks for the memory jog mate much appreciated lol 

problem SOLVED, thread can be closed thanks again

---

### Post by mhgsys on 2009-04-07
):P

Don't slap your forehead to much, you'll need reminders again.


:lolflag:

---

### Post by pbhound on 2009-04-07
ok this is just plain weird, i installed the drivers for my pcmcia wireless card only to get a constant disconnect. after rebooting i can no longer sign in under the username and password i was using before! i have tried to follow the instructions here, to no avail!

please help me in resetting this PW, im running unbuntu 8.10.

---

### Post by mhgsys on 2009-04-08
@ Pbhound. 

What happens if you boot into recovery mode, leaving you in a root console.
Could you 
```
 cd /home/

```

```

ls -a

```


You'll find your username there. 
then 

```

passwd username

```

Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully 

reboot, log in with your username and passwd.

---

