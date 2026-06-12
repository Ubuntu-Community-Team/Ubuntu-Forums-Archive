---
title: "Running Scripts As Users?"
date: 2007-03-23
forum: Server Platforms
---

### Post by z33k3r on 2007-03-23
Hey guys,

I have a reoccuring issue where running scripts on a LAMP installation causes the files to loose permissions. I have been told that this is because the files' ownership changes to the apache's user. I have heard of ways to make it so that the scripts run as a user like an FTP user rather then the default machine user... Can anybody point me in the right direction or clear up my understanding so that I can come up with a solution? I hate having to shell in just to change or delete a file that has been touched by a script...

btw: yes.... I am noob, hear me roar! :lolflag:

---

### Post by Frosty Cold Drink on 2007-03-23
You should check out suexec and suphp. This is what they do.

---

### Post by z33k3r on 2007-03-23
Looking into suPHP now! Will see how it goes. I am currently running Ubunutu 6.10 with ISPC/LAMP. Anybody have experience with running suPHP or others?

---

### Post by z33k3r on 2007-04-12
So does anybody have experience with using either of these with ISPConfig?

---

### Post by z33k3r on 2007-04-12
Along with the previous question, anybody have experience setting up compression with ISPConfig?

---

