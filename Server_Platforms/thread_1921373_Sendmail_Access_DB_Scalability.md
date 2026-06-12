---
title: "Sendmail Access DB Scalability"
date: 2012-02-06
forum: Server Platforms
---

### Post by citaliano on 2012-02-06
Hello,

So here's what I am trying to accomplish. We have a sendmail server and we are trying to stop backscattering. One idea that we came up with to prevent this is to utilize sendmail's access database.

Basically we'd have the first line bounce all mail coming in to our mail server to users in our domain. So for example if my domain is example.com:

example.com           REJECT

After that, we'd have a list of users that we'll accept and relay through our servers, like so:

[email]user1@example.com[/email]         RELAY
[email]user2@example.com[/email]         RELAY
[email]user3@example.com[/email]         RELAY
[email]user4@example.com[/email]         RELAY
...

To get this list of users, we'd have a script that runs a query to our ldap server for a list of active users and dump all of those users into the access file.

My question is, how scalable is the access database file? Would this approach work if our domain contained nearly 50k users?

Thanks in advance,
Corey

---

### Post by nutznboltz on 2012-02-07
Does your LDAP server use SSL?  If so you should be aware of this:
[https://bugs.launchpad.net/bugs/926350](https://bugs.launchpad.net/bugs/926350)

---

