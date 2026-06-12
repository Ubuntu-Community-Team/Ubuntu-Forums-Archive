---
title: "Problem with running a startup script"
date: 2010-04-14
forum: Ubuntu Dev Link Forum
---

### Post by usmanajmal on 2010-04-14
Hi


Is there a way I can run myProgram  when ubuntu's desktop appears no  matter if root , administrator, desktop user or an unprivileged user  logged in? 



  I actually developed a script which I set to run at startup via *System > Preferences > Startup Application *i.e. when the  Desktop appears. In the script I mounted a partition using
  ```
sudo mount /dev/sda1 /mnt &> result.txt
```  After executing script a file named result.txt was created which  contained 
  ```
sudo: no tty present and no askpass program specified
```  In other words the mounting failed. If I run the script  myself from the terminal using sudo  ./myProgram i don't face this problem and the drive gets mounted  successfully.
  Any suggestions please....

---

### Post by alfplayer on 2010-04-14
Do you know about /etc/fstab ?

---

### Post by usmanajmal on 2010-04-15
Yes I know about /etc/fstab.

Okay I have added an entry for mounting /dev/sda1 in /etc/fstab. The problem is still there i.e. when my desktop appears my startup program says 

```
sudo: no tty present and no askpass program specified
```

I get this message when I use 'sudo' before 'dd'. If I use the dd without 'sudo' as:

```
dd if=/dev/sda2 of=/dev/sda5 ?> result.txt
```

Then, the result.txt contains 

```
dd: opening '/dev/sda2': Permission denied
```

How can I copy a partition at startup no matter if root, admin, desktop or an unprivileged user logs in?

I thought it will really be easy but seems like I was wrong. Am I not explaining the question clearly?

---

