---
title: "LDAP Users and Groups problem!"
date: 2007-11-01
forum: Server Platforms
---

### Post by Steve_Ub on 2007-11-01
Hi there,

I am a new user on these forums, so please excuse me if this topic has been raised before. I did a general search, but could find nother relevant to my problem.

While using the Webmin console in Ubuntu 7.04, I am trying to add users using the LDAP Users and Groups under the System heading. When I click on it, it comes up with the Create User screen that asks me to complete details such as First Name, Last Name, etc, etc. After I fill in the basic stuff, I click on the Create button at the bottom of that page. On clicking on the Create button, I get the following error:

Failed to save user : Failed to add user to LDAP database : objectclass: value #3 invalid per syntax

Anyone have any idea what this problem could be talking about? Please help.

Thanks in advance,

Steve.

---

### Post by BillDozer on 2007-11-01
Just to make sure, You have installed LDAP server the system? It is not installed out of the box.

---

### Post by Steve_Ub on 2007-11-01
> **BillDozer said:**
> Just to make sure, You have installed LDAP server the system? It is not installed out of the box.

Yes, installed LDAP with the SLAPD Daemon.

---

### Post by Steve_Ub on 2007-11-02
Is there anyone else who is able to help me with this problem, please...:KS

---

### Post by process91 on 2007-11-14
I got this error as well. When you create a new user do NOT select "Samba Login" as yes.

I have been having other problems creating and authenticating against an LDAP server, and I was hoping you could help me. I don't want to go in another direction with this thread. If you could, please check out [my thread]("http://ubuntuforums.org/showthread.php?t=613109"). Thanks.

---

