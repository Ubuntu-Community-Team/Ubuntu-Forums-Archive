---
title: "editing suduers"
date: 2009-03-24
forum: Security
---

### Post by rawandnet on 2009-03-24
Hi All,

I am using sudoers to enalble user to run a specific command.

Cmnd_Alias MYCMNDS=/usr/sbin/useradd, /usr/sbin/userdel
john ALL=MYCMNDS 

john ALL=(ALL) NOPASSWD: ALL 


every time I want to run the command as john I have to type **sudo** command. Is there a way to type the command only without **sudo**, just like root user.

thanks

---

### Post by kpatz on 2009-03-24
You have to use sudo to run root commands.

A workaround would be to use an alias.  For example:

```
alias useradd='sudo /usr/sbin/useradd'
```

Add this to your .bashrc file, and log out/in again.  Then useradd will run without the sudo command.  Do something similar for userdel.

---

### Post by rawandnet on 2009-03-24
> **kpatz said:**
> You have to use sudo to run root commands.

A workaround would be to use an alias.  For example:

```
alias useradd='sudo /usr/sbin/useradd'
```

Add this to your .bashrc file, and log out/in again.  Then useradd will run without the sudo command.  Do something similar for userdel.




thank you, that is a good approach. this is my first time using this forum i don't know how to give you quot?

---

### Post by bodhi.zazen on 2009-03-24
If you wish to run commands without typing sudo, have you considered simple obraining a root shell ?

```
sudo -i
```

At least that has been my approach when I wish to enter more then a single command as root.

---

