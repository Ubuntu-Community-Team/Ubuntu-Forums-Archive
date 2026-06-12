---
title: "Securely Move Files between Ubuntu Servers"
date: 2008-09-19
forum: Security
---

### Post by hattriq27 on 2008-09-19
I will draw out the architecture first, very simple:


SERVER1----SSH Tunnel-----SERVER2

I want to create a batch job to move a file from server1 to server2 using a secure method.  The prior way was to SCP the file but that required putting a user name and password in the script.  I thought about using stunnel and self signed certificates but I wanted to hear other opinions.

Thoughts?

Thx for your time ;)

---

### Post by cdenley on 2008-09-19
> **hattriq27 said:**
> I will draw out the architecture first, very simple:


SERVER1----SSH Tunnel-----SERVER2

I want to create a batch job to move a file from server1 to server2 using a secure method.  The prior way was to SCP the file but that required putting a user name and password in the script.  I thought about using stunnel and self signed certificates but I wanted to hear other opinions.

Thoughts?

Thx for your time ;)

scp or rsync with public key authentication.

---

### Post by hattriq27 on 2008-09-19
> **cdenley said:**
> scp or rsync with public key authentication.

thanks, yeah I have been reading about the options in the sshd config.  Looks like disabling password auth and using keys is the way to go

---

