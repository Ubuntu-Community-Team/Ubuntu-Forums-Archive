---
title: "Newly created user's SSH shell looks different?"
date: 2011-01-25
forum: Server Platforms
---

### Post by g3nh on 2011-01-25
Hello - I am running Ubuntu Server 10.04 and I just created a new user. Everything works great except the new user's SSH shell can not do certain things. For example, I cannot arrow up for previous commands on the new user. I just get "^[[A" when I try that. (I can do this on root.)

If this helps, it also looks different on root versus the user, look: 
```
root@server:~#
``` on root

just ```
$
``` on the new account.

Please help.

---

### Post by cariboo on 2011-01-25
It looks like you don't have a .bashrc file in the users directory. How did you create the new user?

---

### Post by g3nh on 2011-01-26
I believe I just did this:
```
useradd username
```

Can I simply copy my root's .bashrc to the new user?

---

### Post by James78 on 2011-01-26
Hello,

That is what the shell looks like when it's set to sh. The added user is not using bash essentially. You could change the users shell, or when you login, just type bash to get to the regular shell.

To change your shell..
```
root@server:~# su - username
$ chsh /bin/bash
$ exit
root@server:~# su - username
username@server:~$ 

# OR just.. (much easier)
root@server:~# chsh username /bin/bash
root@server:~# su - username
username@server:~$ 
```
[http://ubuntuforums.org/showpost.php?p=1295266&postcount=2](http://ubuntuforums.org/showpost.php?p=1295266&postcount=2)

---

### Post by crashed111 on 2011-01-26
useradd is pretty low level. You are better off using adduser which in Ubuntu automatically sets a shell to bash.

---

### Post by matt_symes on 2011-01-26
Hi

It looks like the shell your new user is using is dash and not bash.

Kind regards

---

### Post by wojox on 2011-01-26
You didn't specify a shell:

```
sudo useradd --create-home --shell=/bin/bash <username>
```

---

