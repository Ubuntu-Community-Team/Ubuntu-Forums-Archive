---
title: "How do I change passwords in MySQLAdmin?"
date: 2008-12-10
forum: Server Platforms
---

### Post by ShaolinF on 2008-12-10
Title says it all.

---

### Post by eder.apt-get on 2008-12-10
Have you tryed **la01ks92**?

---

### Post by taurus on 2008-12-10
There is no root password; it's locked.  Instead, you use sudo if you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by iponeverything on 2008-12-10
By default its turned off.

```
sudo <command>

```

---

### Post by ShaolinF on 2008-12-10
Thanks. Its just that I cannot change pwords on my mysql server using the mysqladmin file. I get the following error:

'Access denied; you need the SUPER prilege for this operation'. I am logged into my account so it should work..

---

### Post by binbash on 2008-12-10
try the command with

sudo su -

---

### Post by king_lear on 2008-12-10
try 
'sudo passwd'
this should create a new root password with which you can do 'su'

---

