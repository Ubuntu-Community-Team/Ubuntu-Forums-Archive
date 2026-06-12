---
title: "Postfix Instances"
date: 2011-04-15
forum: Server Platforms
---

### Post by PhilAd on 2011-04-15
Hi,

i'd like to install a postfix server with two instances. One Instance is binded to the domain example1.com and the other Instance is binded to the domain example2.com. When i send an email to [email]test1@example1.com[/email] the email goes to the local user test1. Now i write an email to the user [email]test1@example2.com[/email] and the email goes also to the local user test1.
I'd like to bind each domain to local users and they should be seperated even if they have the same prefix/user.
Someone an idea how to solve that 'problem'?

greets

philad

---

### Post by elico on 2011-04-15
you can try to run to instances of postfix but it's useless.
the basic setup of postfix is that user in the system is connected to "mydestinations"
so you cant use [email]test1@x.domain[/email]1 and also [email]test1@x.domain[/email]2 on the same machine.
for that reason the invented what called VirtualDomains and VirtualMailbox.
it's very simple to setup and very easy to use and you dont need a database such as mysql and stuff.
you can use files to mange the email domains but it's much more simple to manage using mysql.
you can use POSTFIXADMIN.
you can try look at 
[http://serion.co.nz/content/howto-setup-mailserver-using-postfix-mysql-dovecot-postfixadmin-amavis-new](http://serion.co.nz/content/howto-setup-mailserver-using-postfix-mysql-dovecot-postfixadmin-amavis-new)

im working now on a very nice tutorial in my language on the same idea but more simple and with some modifications to the database for an ISP like config.

---

### Post by venol on 2011-04-15
> Hi,

i'd like to install a postfix server with two instances. One Instance is binded to the domain example1.com and the other Instance is binded to the domain example2.com. When i send an email to [email]test1@example1.com[/email] the email goes to the local user test1. Now i write an email to the user [email]test1@example2.com[/email] and the email goes also to the local user test1.
I'd like to bind each domain to local users and they should be seperated even if they have the same prefix/user.
Someone an idea how to solve that 'problem'?

greets

philad

maybe u can set "transport_maps = example2.com smtp:[mail.example2.com]:25" on mail server example1.com, and set "transport_maps = example1.com  smtp:[mail.example1.com]:25" on mail server example2.com

> you can try to run to instances of postfix but it's useless.
the basic setup of postfix is that user in the system is connected to "mydestinations"
so you cant use [email]test1@x.domain[/email]1 and also [email]test1@x.domain[/email]2 on the same machine.
for that reason the invented what called VirtualDomains and VirtualMailbox.
it's very simple to setup and very easy to use and you dont need a database such as mysql and stuff.
you can use files to mange the email domains but it's much more simple to manage using mysql.
you can use POSTFIXADMIN.
you can try look at 
[http://serion.co.nz/content/howto-se...min-amavis-new](http://serion.co.nz/content/howto-se...min-amavis-new)

im working now on a very nice tutorial in my language on the same idea but more simple and with some modifications to the database for an ISP like config.

hello, I follow tutorial from serion.co.nz to. But for email contains spam is not working properly. Amavis detect spam, but not forward to the receive. I set "final_spam_destination = D_PASS", but spam BLOCKED by amavis. 

what's problem..
thanks..

---

### Post by venol on 2011-04-17
Maybe someone can help me.;)

---

### Post by PhilAd on 2011-04-18
hey, thanks for your reply's ... i'll check your link.
using the virtual file sounds good ... tha could really be my answer :-)

---

