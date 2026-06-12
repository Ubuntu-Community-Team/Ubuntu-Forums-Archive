---
title: "How to avoid chrome store password in seahorse?"
date: 2014-09-16
forum: Security
---

### Post by Random20220612 on 2014-09-16
Hello, 

I am very concerned about the unencrypted passwords saved by chrome in seahorse. 

This equipment is shared and used by several people, so any user with the root password can change my user password and copy all passwords stored in seahorse. The password to unlock seahorse is the same password i use to login the unity session. 

I have chrome under password to protect my profile ( i have activated the new chrome profile management and now i can use password for private use and protect all my data) but seahorse has stored all passwords in a file. 

There must be some way to prevent passwords from being stored in seahorse (NOT ENCRYPTED)

Why the passwords seahorse save are visible and aren't encrypted with MD5?

Thanks.-

---

### Post by bashiergui on 2014-09-16
> This equipment is shared and used by several people, so any user with the root password can change my user password and copy all passwords stored in seahorse. The password to unlock seahorse is the same password i use to login the unity session. It's functioning exactly as its designed. The keyring is unlocked when a user logs in. If all your users use the same account, then your keyring is unlocked for them all.

If you want several people using the machine then create a user account for each user. They'll each get their own home folder where their own keyring will be stored. You can put the users in the sudo group to allow certain or all root functions.

If you give all the users the root password, then you can't hope to control anything they do.

md5 is a hashing algorithm, it is not encryption. You should not consider a hash to be secret.

---

### Post by Random20220612 on 2014-09-16
Hello,

Each user has their own account of course, but users with root password can change every user account password and login their session and unlock the seahorse.

Thank you.-

---

### Post by Sef on 2014-09-16
> [COLOR=#000000]Each user has their own account of course, but users with root password can change every user account password and login their session and unlock the seahorse.[/COLOR]

Why does each other have root access?

---

### Post by Random20220612 on 2014-09-16
Hello,

Because it's a shared PC and the idiot of my manager insist each users (and of course he) must have root password...

thanks.-

---

### Post by bashiergui on 2014-09-16
> **marceloramone said:**
> Each user has their own account of course, but users with root password can change every user account password and login their session and unlock the seahorse.Yes. Again, functioning exactly as designed. Root sees all.

---

