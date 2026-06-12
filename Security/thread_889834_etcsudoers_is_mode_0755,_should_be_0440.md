---
title: "/etc/sudoers is mode 0755, should be 0440"
date: 2008-08-14
forum: Security
---

### Post by fib1807 on 2008-08-14
/etc/sudoers is mode 0755, should be 0440

This is what I get when I enter any command.I tried hitting su
I was asked for a password but when I hit it,it resulted in this message 
"su: Authentication failure".I know my crime,I wanted to meddle and play with sudoers file under root.Is there any solution for fixing this problem ? because I can't perform any administrative tasks due to this the same message is displayed when I hit any command.

Thanks all.

---

### Post by caljohnsmith on 2008-08-14
If you want to modify sudoers, you should use "visudo", because that will prevent what happened to you. :) But anyway, to fix it, just boot into recovery mode and "chmod 0440 /etc/sudoers". Or you could do it from a Live CD, but you would have to mount your Ubuntu from your HDD first.

---

### Post by fib1807 on 2008-09-16
> **caljohnsmith said:**
> If you want to modify sudoers, you should use "visudo", because that will prevent what happened to you. :) But anyway, to fix it, just boot into recovery mode and "chmod 0440 /etc/sudoers". Or you could do it from a Live CD, but you would have to mount your Ubuntu from your HDD first.
Hey just forgot to thank you.Sorry budd.Thanks for help.

---

### Post by caljohnsmith on 2008-09-16
You're welcome. Better to receive a late thank you then not at all. Just glad you got your sudoers issue fixed. :)

---

