---
title: "How to set a password to open application"
date: 2010-08-27
forum: Security
---

### Post by guduruvamsi on 2010-08-27
hi all,

I am new to Ubuntu,
I just configured Evolution email client, every thing is fine.
but i need to put password to open this app, this is because many uses my computer.
can any one help!

thank you.

---

### Post by FuturePilot on 2010-08-27
Passwording applications does not provide any real security. It would be better to make separate accounts for other people that use the computer or have them use the guest session.

---

### Post by guduruvamsi on 2010-08-28
thank you,
can i make that application run under root only. (that means: it asks root password if we open it, like when we open synaptic manager which ask for password)

---

### Post by dFlyer on 2010-08-28
Why would you want to run a program as root? That is reserved for system administration.

---

### Post by cariboo on 2010-08-28
The correct way to manage a linux system is to create separate accounts for each user, and set the home directory permissions to 700 so only the owner and the admin have access to them.

---

### Post by guduruvamsi on 2010-08-30
thank u dFlyer & cariboo907

I thought if i make the program to run under root, it asks for password. As no one who uses my laptop don't know my root password, so i can prevent them to open my email client.
can do it in this way?

Cariboo907, i can't do separate accounts for those who uses my laptop all are my good friends and roommates too. I think u understand it.

---

### Post by cariboo on 2010-08-30
Just because they are friends or roommates, there is no reason not to set up at least a friends/guest account. 

Even on Windows, I set up separate accounts for all regular users with passwords, there is also a friend account with no password.

If you want to keep your data secure, separate accounts and an encrypted home directory is the only way to do it.

---

### Post by scorp123 on 2010-08-30
> **guduruvamsi said:**
> I can't do separate accounts for those who uses my laptop all are my good friends and roommates too. This would be the reason #1 why you definitely should give each their own account and password! If you were my room mate I definitely would not want you to read my chat messages and e-mails ... :D

The "root" account is for system-administration purposes only. That account enjoys God-like unlimited powers ... and that's way too much power. It is not supposed to be used for running programs. One wrong click, one false move ... and you can instantly destroy all data on the system. Running programs as "root" means that those programs enjoy unlimited powers they were never ever supposed to have. Running a mail program as "root" _DEFINITELY_ is wrong wrong wrong.

---

### Post by bodhi.zazen on 2010-08-30
> **guduruvamsi said:**
> i can't do separate accounts for those who uses my laptop all are my good friends and roommates too. I think u understand it.

Create a separate account for your private things such as e-mail.

Use a communal account for non-private things.

---

