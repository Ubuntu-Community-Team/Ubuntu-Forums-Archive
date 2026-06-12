---
title: "LDAP this and that"
date: 2009-10-02
forum: Server Platforms
---

### Post by mogliii on 2009-10-02
Hi,

I managed to somehow setup an LDAP server with an Mozilla address book. 

I have some general questions about LDAP that, even after reading through the Wikipedia article twice carefully, I cannot answer myself.

[SIZE="4"]1) What is this "dc" stuff?[/SIZE]
Many howto show [FONT="Courier New"][SIZE="3"]dc=example,dc=com[/SIZE][/FONT] or [SIZE="3"][FONT="Courier New"]dc=example,dc=local[/FONT][/SIZE]. Of course I have to be consistent, but could I use [SIZE="3"][FONT="Courier New"]dc=google,dc=com[/FONT][/SIZE] or even [FONT="Courier New"][SIZE="3"]dc=a[/SIZE][/FONT]? Or can I completely skip it? Maybe as a web-sufer my view is distorted.

[SIZE="4"]2) Why is the login-user for phpldapadmin or for the Thunderbird settings so painful?[/SIZE]
[SIZE="3"][FONT="Courier New"]cn=admin,dc=example,dc=local[/FONT][/SIZE]
I mean everywhere else in the universe you can just login with simple ASCII username/password. Why then is LDAP so popular, or why is there no other way of including an online address book into Thunderbird, eg.  based on MySQL?

Just I am confused and intimidated by the fact that LDAP is so much different than I expected for a database.

---

