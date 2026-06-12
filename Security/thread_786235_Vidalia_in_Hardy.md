---
title: "Vidalia in Hardy?"
date: 2008-05-07
forum: Security
---

### Post by mocha on 2008-05-07
How do you compile Vidalia in Hardy.  I followed the instructions on the Vidalia page but I still have a dependancy problem.  After running cmake I get:


```
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
QT_QT_INCLUDE_DIR (ADVANCED)
```

Can anyone help?  Thanks.

---

### Post by aashay on 2008-06-25
> **mocha said:**
> How do you compile Vidalia in Hardy.  I followed the instructions on the Vidalia page but I still have a dependancy problem.  After running cmake I get:


```
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
QT_QT_INCLUDE_DIR (ADVANCED)
```

Can anyone help?  Thanks.

You can install it from the following repositories
```

#Vidalia
deb http://ppa.launchpad.net/adnarim/ubuntu hardy main
deb-src http://ppa.launchpad.net/adnarim/ubuntu hardy main
```
The program itself stops responding at startup, atleast for me. Try it out if you want to

---

### Post by Dr Small on 2008-06-25
I always just install tor and privoxy. Works just as good ;)

---

### Post by mriedel on 2008-07-12
> **aashay said:**
> You can install it from the following repositories
```

#Vidalia
deb http://ppa.launchpad.net/adnarim/ubuntu hardy main
deb-src http://ppa.launchpad.net/adnarim/ubuntu hardy main
```
The program itself stops responding at startup, atleast for me. Try it out if you want to

What/whose repositories are those?

---

### Post by QCompson on 2008-07-17
> **aashay said:**
> You can install it from the following repositories
```

#Vidalia
deb http://ppa.launchpad.net/adnarim/ubuntu hardy main
deb-src http://ppa.launchpad.net/adnarim/ubuntu hardy main
```
The program itself stops responding at startup, atleast for me. Try it out if you want to

I have the same problem.  Vidalia GUI freezes at startup.  Hardy 64bit here.  Anyone know of a solution?

---

### Post by Jitz0722 on 2008-07-17
Vidalia stops responding,

If I sudo Vidalia it gets further but then complains that .tor is owned by someone other than root??

How should user permissions and such be setup to use Vidalia with Ubuntu??

---

### Post by mihai.ile on 2008-12-22
about the freezing bug in [https://bugs.launchpad.net/ubuntu/+bug/110666](https://bugs.launchpad.net/ubuntu/+bug/110666) comment 8 there is a fix.
I tested under 8.10 and it works!
downlodaded from [http://packages.ubuntu.com/jaunty/vidalia](http://packages.ubuntu.com/jaunty/vidalia) in thebottom you have download for 64bit or i386 deb.

---

