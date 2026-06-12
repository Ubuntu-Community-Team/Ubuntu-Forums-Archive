---
title: "passwords"
date: 2012-06-24
forum: Security
---

### Post by ciscoboy on 2012-06-24
yeah; I was wondering the other day if you could have a password for login and a different password for administration clearances (ex.: program instalations...). So that way, if you let someone on your account, or someone figures out oyur password, they don't have admin clearance.

Thank You

CiscoBoy

---

### Post by whatthefunk on 2012-06-24
Yes.  You just have to make a seperate user account.

---

### Post by uRock on 2012-06-24
> **whatthefunk said:**
> Yes.  You just have to make a seperate user account.

+1 User the User Accounts application to create a new user. When you create the new user account make it an Administrator account. Log into the new account and make sure you can run sudo commands and/or open sofware center and install stuff. Once you are sure the permissions for the new account is good to go, open User Accounts and set the primary account as Standard/Desktop User, which will remove the power of sudo from that account.

---

### Post by ciscoboy on 2012-06-24
So there's no way to have one account with a login password and another password to do stuff like software instalation?

---

### Post by sisco311 on 2012-06-24
> **ciscoboy said:**
> So there's no way to have one account with a login password and another password to do stuff like software instalation?

You can set up a root password; configure sudo to don't allow your user to run commands as root or configure it to prompt you for the root password and set up gksu & polkit to prompt for the root password as well. 

So, there is a way, but it's much easier to create a new (unprivileged) account.

IMO, sharing an account with another person is like sharing a  toothbrush... :rolleyes:

---

### Post by ciscoboy on 2012-06-24
I see; well, thanks for your help it was very useful.

---

