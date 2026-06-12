---
title: "Heh, random question I had."
date: 2009-05-04
forum: The Cafe
---

### Post by CJ Master on 2009-05-04
How can sudo elevate you to root privileges? Wouldn't sudo itself need to be run as root?

---

### Post by swoll1980 on 2009-05-04
> **CJ Master said:**
> How can sudo elevate you to root privileges? Wouldn't sudo itself need to be run as root?

What came first, the chicken, or the egg? You may have just found a hole in space/time.

---

### Post by mister_pink on 2009-05-04
For the answer to that, type 
```

ls -l /usr/bin/sudo

```
Note the s - that means it is run as its owner - root (its called SETUID). So it is run as root.

---

### Post by benj1 on 2009-05-04
> **CJ Master said:**
> How can sudo elevate you to root privileges? Wouldn't sudo itself need to be run as root?

root .bashrc
alias $1='sudo $1; $password' ?

---

### Post by CJ Master on 2009-05-04
> **mister_pink said:**
> For the answer to that, type 
```

ls -l /usr/bin/sudo

```
Note the s - that means it is run as its owner - root (its called SETUID). So it is run as root.

Thats cool, but it's kind of scary that if a program is run as root it can automatically be set up to run with root privileges all the time. Trojan horses, anybody?

> root .bashrc
alias $1='sudo $1; $password' ? 

Not quite sure what that alias is, but it looks like you have an infinite loop. I wouldn't try it.

---

### Post by benj1 on 2009-05-04
>  Not quite sure what that alias is, but it looks like you have an infinite loop. I wouldn't try it.

well it was supposed to be a joke :rolleyes:

i don't think it would work anyway, can you assign $1 as an alias name ??? im fairly sure inputting a password like that wouldn't work anyway, at least i hope not.

---

### Post by saulgoode on 2009-05-04
> **CJ Master said:**
> Thats cool, but it's kind of scary that if a program is run as root it can automatically be set up to run with root privileges all the time. Trojan horses, anybody?
That is why you want to be very careful about any programs on your system which run SUID root. Such programs need to perform their own security checking and user privilege validations. 

Most SUID programs perform any root-privileged tasks as soon as possible, then demote themselves back to normal user-level privileges. SUDO is atypical in this sense (root-level privileges are granted to all processes until they terminate), but it has been around for close to 25 years and is well-tested against vulnerabilities. Nonetheless, some system administrators prefer not to install the SUDO package at all, and thereby avoid any chance of it being exploited.

---

### Post by cariboo on 2009-05-04
That's why there is no root password set in Ubuntu. Sudo times out after fifteen minutes by default, so would have to enter your password every fifteen minutes in order to keep running as root.

There is a way around it, but I'll let you figure it out for your self. Have a look at:

```
man sudo
```

---

### Post by 3rdalbum on 2009-05-05
It's like the Barber Paradox:

There is a program on your computer called Sudo that elevates all programs to root, except those who can elevate themselves. So how does Sudo elevate itself to root?

...well, that's what it reminded me of.

> Thats cool, but it's kind of scary that if a program is run as root it can automatically be set up to run with root privileges all the time. Trojan horses, anybody?

Heck, you don't need setuid binaries for that. Any program that runs as root can create an init script that spawns itself automatically on startup. Any program started from an init script is automatically run as root.

---

