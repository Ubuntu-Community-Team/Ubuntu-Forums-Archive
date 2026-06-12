---
title: "As Sudo User, Receive Prompt to &quot;Enter root's password:&quot;"
date: 2018-06-28
forum: Security
---

### Post by jyanaranknfilesys on 2018-06-28
Lately I have been getting prompted to "Enter root's password:",  even after elevating my permissions as the sudo user, whilst attempting to execute a command, something as simple as "sudo net ads leave -f"

admin@ubuntu:~$ sudo net ads leave -f
[sudo] password for admin: 
Enter root's password:

Previously the root user had been enabled but then I disabled it again. Not sure where to go from here.

---

### Post by Andreyshel on 2018-06-28
Hello.
Can you run
> sudo passwd -S root
?
If you are asked for your root password use recovery   mode to get into root console.


[FONT=Verdana]
[/FONT]

---

### Post by jyanaranknfilesys on 2018-06-28
Thanks for the reply. Here is the output from that command:

admin@ubuntu:~$ sudo passwd -S root 
root L 06/11/2018 0 99999 7 -1

---

### Post by Andreyshel on 2018-06-28
Try 
```
net ads leave -U user%password
``` where user and password is from AD administrator account. This is not ubuntu login issue, but incorrect use of samba.

---

### Post by jyanaranknfilesys on 2018-06-28
Yes you are right, that was a rookie mistake the result of too little sleep, thank you for pointing that out. I think what had tripped me up was that I was convinced that it was happening with other commands as well.

Would be good if net ads returned a better error code.

Cheers!

---

### Post by TheFu on 2018-06-28
Please mark this thread as **solved**, to prevent others wanting to help, like me, from wasting time.  Also, it helps others looking for a similar solution to their problems.
Thanks for helping the community.

---

