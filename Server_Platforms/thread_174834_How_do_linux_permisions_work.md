---
title: "How do linux permisions work?"
date: 2006-05-12
forum: Server Platforms
---

### Post by david049 on 2006-05-12
Hello,

Am I missing something here, or does the *nix file permission systems seem vastly inferior to the Microsoft/Netware ACL method.

How in the world can you sanely use Linux in a complex network with ActiveDirectory/NDS/LDAP?  

What am I missing?

Thanks,
David

---

### Post by cgjones on 2006-05-12
How exactly are they that much different?

---

### Post by david049 on 2006-05-12
From what I know about Linux, a file has a single "user" and a single "group" assigned to it.

How can you give different groups different levels of access to the same file?

---

### Post by cgjones on 2006-05-12
You can use the **getfacl** and **setfacl** commands to more finely define permissions.

---

### Post by Socratez on 2006-05-13
I have been using linux for 3 years and I still have no idea how they work ... I use the good ol chmod -R 777 for any permission problems but I would like to have a plain english explaination of the permissions myself. I have read and read and read but I just am not able to grasp the concept for one reason or another .... Can anybody show an example of a chmod setting permissions and then explain it to make sense or show the use of it ?

---

### Post by kabus on 2006-05-13
[QUOTE=Socratez]I have been using linux for 3 years and I still have no idea how they work ... I use the good ol chmod -R 777 for any permission problems but I would like to have a plain english explaination of the permissions myself.[/QUOTE]


[http://tldp.org/LDP/intro-linux/html/sect_03_04.html](http://tldp.org/LDP/intro-linux/html/sect_03_04.html)

---

### Post by cgjones on 2006-05-13
[Here](http://www.linuxjournal.com/article/1190) is a pretty nice article on **chmod**.

---

