---
title: "Is it possible to have duplicate usernames in different groups?"
date: 2009-06-02
forum: Server Platforms
---

### Post by jeffvdovjak on 2009-06-02
As the title indicates, I'm looking to find out if it's possible to create username's that are not unique if they are in different groups.

Here's the idea:

I have a username called "bill" in the group clientgroup

now I want bill to be able to create a user ("fred") in the group bill but "fred" already exists in the group clientgroup

Is it possible to allow both to exist?  But each group should not be able to have duplicate entries...

I'm a noob so keep it easy (not a super noob... but new enough)...



Jeff

---

### Post by jeffvdovjak on 2009-06-02
The purpose is to allow my clients to create FTP users for themselves through our control panel.  We have a lot of clients - so I don't want them to have to guess and check names - and I don't want to use random names (or even their username with a number tacked on at the end).  Thanks!

---

### Post by regala on 2009-06-02
> **jeffvdovjak said:**
> As the title indicates, I'm looking to find out if it's possible to create username's that are not unique if they are in different groups.

Here's the idea:

I have a username called "bill" in the group clientgroup

now I want bill to be able to create a user ("fred") in the group bill but "fred" already exists in the group clientgroup

Is it possible to allow both to exist?  But each group should not be able to have duplicate entries...

I'm a noob so keep it easy (not a super noob... but new enough)...



Jeff

the question is not about creating a duplicate user in another group, but about adding a previously existing user in another group, right ?

man usermod

(the command you need is exactly ```
usermod -a -G bill fred
```, but you should read the manpage of usermod)

br, mathieu

---

### Post by jeffvdovjak on 2009-06-02
No, I need to be able to create dupicate accounts.  I can't create "bill" in one group and then try to create a new bill and put him into another group.

Here's a (maybe) better explained example.

Bill is a "client" (in the group "client").
Fred is also a "client".

Bill has an employee at his business and needs to give him a username and password to his FTP server.  Bill wants to give him the username "Fred".  This new Fred would only be in the group "Bill" because he's not a client - he's Bill's guy.  But Bill can't create a user named "Fred" because one already exists.

How can I make it so that there can be two fred's?  Or is it possible?

---

### Post by regala on 2009-06-02
> **jeffvdovjak said:**
> No, I need to be able to create dupicate accounts.  I can't create "bill" in one group and then try to create a new bill and put him into another group.

Here's a (maybe) better explained example.

Bill is a "client" (in the group "client").
Fred is also a "client".

Bill has an employee at his business and needs to give him a username and password to his FTP server.  Bill wants to give him the username "Fred".  This new Fred would only be in the group "Bill" because he's not a client - he's Bill's guy.  But Bill can't create a user named "Fred" because one already exists.

How can I make it so that there can be two fred's?  Or is it possible?

no there can't be.

---

### Post by regala on 2009-06-02
> **regala said:**
> no there can't be.

generally, this is why in corporate use, we try and avoid using first names or nicknames when expecting multiple accounts.

on the same machine, you cannot have multiple *Unix* accounts with the same name. but if you just want to give access to FTP, or other services, you should check in the docs for the services you run: apps usually implement several authentication/authorization backend; for example, proftpd can use unix accounts, *sql accounts, ldap accounts...
maybe you should check this out, check what services are needed by which clients. and maybe you should straighten the naming conventions for clients' accounts ;)

br, mathieu

---

### Post by jeffvdovjak on 2009-06-02
well the naming is more sophisticated than that ... just that easy for the example..

however, I did not know that proftpd could work from sql ... thought it only worked from unix -- so I'll check into that!  Thanks!

I figured worst case scenario is that if someone picked a name that already existed (and yes, when you're working with forms which end-users fill out, they will pick "bill" and "fred") I can just change the naming to include group identifiers...

For example, when they create users it could append it to a prefix which would be the domain: 
domain_user (for example)

So Bill could input "fred" and fred's login would be domain_fred.

---

### Post by regala on 2009-06-02
> **jeffvdovjak said:**
> well the naming is more sophisticated than that ... just that easy for the example..

however, I did not know that proftpd could work from sql ... thought it only worked from unix -- so I'll check into that!  Thanks!

I figured worst case scenario is that if someone picked a name that already existed (and yes, when you're working with forms which end-users fill out, they will pick "bill" and "fred") I can just change the naming to include group identifiers...

For example, when they create users it could append it to a prefix which would be the domain: 
domain_user (for example)

So Bill could input "fred" and fred's login would be domain_fred.

first you should definitly prevent clients from choosing their login, this adds no real benefit to your interface and gives you headaches such as this one :)

---

