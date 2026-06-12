---
title: "What to use for network project"
date: 2010-04-12
forum: Server Platforms
---

### Post by Hokorippoi on 2010-04-12
I am talking classes at a university. One of my classes has a large  group project.
This is a learning thing. So, no "just use this preset system".

The network I have to setup has windows as the clients, and Linux as server.
I want to do:

[LIST]
[*]email. (got it to work)
[LIST]
[*]I am using postfix, Dovecot, and squirrelmail
[/LIST]
 
[*]Web application server. (I have php, apache2, and mysql)
[LIST]
[*]I have php5, apache2, and mysql installed.
[LIST]
[*]The apache2, and php5 has squirrelmail working.
[/LIST]
 
[/LIST]
 
[*]some type of Single log in.
[LIST]
[*]The prof. said that he would use Samba.
[/LIST]
 
[*]DNS. typing in IP's does not look nice.
[LIST]
[*]I got bind9 installed. I am just not up to doing this part till I am nearer to the final setup.
[/LIST]
 
[*]SSH
[LIST]
[*]remote login
[/LIST]
[*]A window manger:
[LIST]
[*][LEFT]just something so I can use and look at more then one terminal at a time.
[/LEFT]
[/LIST]
[/LIST]
Any feed back on what you think would be nice. From what I keep reading I feel that the Single log in will be the hard part. I would like to find a guide that does not skip things. I want to learn, not just "type in this line and it works".

Thanks for any help.

---

### Post by KB1JWQ on 2010-04-12
I'd use LDAP for single signon; SAMBA can speak it, and many things can't speak SAMBA.

---

