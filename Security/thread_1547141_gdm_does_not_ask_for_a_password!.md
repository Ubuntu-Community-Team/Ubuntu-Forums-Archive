---
title: "gdm does not ask for a password!"
date: 2010-08-06
forum: Security
---

### Post by kvtb on 2010-08-06
Hi,

I can login without entering a password. I simply click on my name, and press Enter.
I did not change my configuration and for sure I did not enable password-less login for my account.

This behaviour is on all computers on my network: any user can login with MY username, and GDM will NOT ask for a password!!!

Other users on my network do have to enter their password when they login

The only difference is that my username has some admin privileges (e.g. I have sudo rights)

---

### Post by bodhi.zazen on 2010-08-06
As this is not the default behavior, you must have configured something. From your post you imply some type of network login ? Are you using NFS or kerberos ?

It would help if you provided more information ;)

---

### Post by kvtb on 2010-08-12
I'm using NIS (with nscd) and NFS.
If you need more details, let me know.

I cannot imagine that I've configured GDM to allow password-less logins for myself on all computers.
How can I check if GDM is configured to allow password-less logins for certain users?

---

### Post by Frogs Hair on 2010-08-12
Go to Administration > Log in and see if you have log in set to automatic.

---

### Post by kvtb on 2010-09-01
Hi
login is *not* set to automatic.
People can select my user name from the list in gdm, double click on it, and without entering my password, login as me.

Is anything is unclear in my posts, please let me know, because I've the idea my problem is not well understood. This is a big security flaw.

---

### Post by kvtb on 2010-09-01
Okay, so I uninstalled nscd, and it looks like the problem has been solved.
So apparantly there is an issue with nscd, it allows gdm to continue when an empty password is given......

---

