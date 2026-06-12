---
title: "question about permission"
date: 2009-06-19
forum: Security
---

### Post by yousof on 2009-06-19
Hello all,
I am new in Ubuntu, I have a problem I hope you can help me to solve it
I installed ubuntu and PHP, MYSQL appserv, I wanted to use to use www folder to creat folders and file, but I could not (I do not have a permission) suppose my account is yousof, and I wanna to get root permission (to be a member of root group how can I do this) ??

Greetings

---

### Post by clw3388 on 2009-06-19
why dont ya just chown it to yourself?
 ```
sudo chown username 
```
should give ya all permissions needed to create files in that directory for ya.. If not chmod it..

---

### Post by clw3388 on 2009-06-19
oh.. and ubuntu already gives you sudo privs upon install so you are already a sudo root usr..

---

### Post by wojox on 2009-06-19
yousof

You want to change ownership

sudo chown -R yousof www

press enter

---

### Post by yousof on 2009-06-19
Thank you very much guys ;) 
;)

---

