---
title: "Authentication sugession to implement email server with windows AD"
date: 2015-09-10
forum: Server Platforms
---

### Post by pradish on 2015-09-10
Hi All,
This is my first question in Ubuntu Forum and till now I have followed the wiki and forum suggestion. 
My setup is as follows.
Ubuntu server is added to Windows Domain Controller with Samba server.
Email server is implemented with PostFix and Dovecot. 
I would like to have signal sign on for the IDs on Windows AD and connect to Dovecot email server. My question is how best I can further the implementation to achieve this. Should I use Kerbose or LDAP to replicate Windows AD. Anyother way than these two.

---

### Post by darkod on 2015-09-10
These instructions are for iredmail which basically uses postfix and dovecot too. They show how to integrate iredmail with AD.
[http://www.iredmail.org/docs/active.directory.html](http://www.iredmail.org/docs/active.directory.html)

You should be able to use them even when not installing iredmail, just use the AD integration part.

---

### Post by pradish on 2015-09-10
Thanks Darko
In my case the domain lets say test.corp and the email system is example.com. In such case I believe I would need virtual mail configured in postfix to implement the LDAP. Is this correct assumption?

---

### Post by darkod on 2015-09-10
The mail config is "virtual" anyway, if you see the section for LDAP integration it starts with setting virtual_mailbox_domains parameter.

But AD domain is rarely directly public, almost always it's local. So you can make it to match the email domain, as good practice. It saves you complications like this.

You should search on google for modifications of the procedure for such case. It might be as simple as using the email domain as virtual mail domain, and using the [email]vmail@test.corp[/email] user in the AD which should authenticate correctly in the domain.

---

