---
title: "How to connect a client to my LDAP server"
date: 2010-02-01
forum: Server Platforms
---

### Post by makak06 on 2010-02-01
Hi, 

First of all, excuse my english, because i'm french.

I have read and install this "howto" [http://ubuntuforums.org/showthread.php?t=1330637](http://ubuntuforums.org/showthread.php?t=1330637) on my server Ubuntu.
I tried to connect an XP computer and it's works wonderful.

But i don't know how to connect an Ubuntu desktop to my Server ?

I have read more tutorial, and i have set up some file like :

/etc/nsswitch
> 
passwd : files ldap
group : files ldap
And then I don't know if the ldap.conf have to be in /etc/ldap.conf or /etc/ldap/ldap.conf

And for the other files like /etc/pam.d/common-* I don't know what to put in...

Thanks for your help

---

