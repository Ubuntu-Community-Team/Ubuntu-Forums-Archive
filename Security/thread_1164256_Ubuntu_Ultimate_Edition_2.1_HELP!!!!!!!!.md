---
title: "Ubuntu Ultimate Edition 2.1 HELP!!!!!!!!"
date: 2009-05-19
forum: Security
---

### Post by acrinym on 2009-05-19
Help... I have a problem.
I used sudo KUSER to change all my permissions to root. Or so i thought. What I really did was take myself out of any groups except root. Now I can't change it back, can't use sudo at terminal because i get this message "avatar(my user name) is not in the sudoers file. This incident will be reported."

Any suggestions? 


I can login, and do most things, as long as they don't require permission. 

help....
             -Avatar

---

### Post by sisco311 on 2009-05-19
Reboot in Recovery Mode and add your user to the admin group.
```
adduser avatar admin
```

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by acrinym on 2009-05-19
How do you get into recovery mode though? I don't have the install media...

---

### Post by acrinym on 2009-05-19
Mhmm... got it... i think.

---

