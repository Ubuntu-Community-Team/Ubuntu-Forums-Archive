---
title: "What is the root password on the 6.06 Server"
date: 2006-06-06
forum: Server Platforms
---

### Post by explorer1979 on 2006-06-06
Hi all,

I installed the 6.06 LTS Server today, but on the login screen type root

it ask me the root password .. but on the installing process before, it have not ask me enter the root password, just ask me creat a user . then I follwoing the inst. on the installing to make a user ..

And yes, I can using this user to login, but it is not root ...

All 6.06 also same like that??

How to using the root to login to the system?

Thx

---

### Post by cskeide on 2006-06-06
On Ubuntu, there is no root user by default. Use sudo to run commands as root.

Also, [**read this**]("https://wiki.ubuntu.com/RootSudo") if you want to now more about root and sudo on ubuntu.

---

### Post by explorer1979 on 2006-06-06
Thx for your response.

It is very useful inform for me, since I am first time see a dist. like that, no the root user ..

---

### Post by rayichi on 2007-12-12
so like... you could do

sudo chmod 755 /var

and sudo would be a root "mask"?

---

### Post by rsw686 on 2007-12-12
I prefer to assign a password to the root account with

sudo passwd

Then I can switch to root or login as root

su -

I find this useful when I need to run multiple commands as root without having to use sudo for each command.

---

### Post by aysiu on 2007-12-12
> **rayichi said:**
> so like... you could do

sudo chmod 755 /var

and sudo would be a root "mask"?
*sudo* allows you to perform certain tasks with root-like privileges.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

