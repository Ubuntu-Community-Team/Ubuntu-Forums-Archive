---
title: "SSH locally into www"
date: 2008-10-19
forum: Server Platforms
---

### Post by gerryvye on 2008-10-19
I am trying to use ubuntu server as a test platform for some web development projects. I am trying to ssh with filezilla from my other machine to deposit files in the apache www directory. I am semi new to Ubuntu and cannot figure out how to give myself access from another 192.168 connection. My ultimate goal is to ssh files from one machine to my ubuntu machines www directory. standard (/var/www). Naturally security is restricting it.

Command:	
put "C:\Users\owner\Desktop\PHP Site\wrox.html" "wrox.html"
Error:	/var/www/wrox.html: open for write: permission denied

I am sure this is an easy fix. If someone could give me suggestions that would be awesome. Thanks.

---

### Post by hvc123 on 2008-10-19
hi, the answer is in the question.... 

try using sudo <command> you gotta do this unless you have enabled the root account in which case just login as root.

---

### Post by iason86 on 2008-10-19
i am not an  expert and what i am going to tell you may not work but you don't have anything to lose trying it

type
ssh computers_name@machine_name

---

