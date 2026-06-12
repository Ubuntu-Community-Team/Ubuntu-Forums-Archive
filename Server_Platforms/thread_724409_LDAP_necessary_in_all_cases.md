---
title: "LDAP necessary in all cases?"
date: 2008-03-14
forum: Server Platforms
---

### Post by cocotu on 2008-03-14
Not sure if we need LDAP in our case:

1. We have around 30 users: 50% PC, 50% MACs
2. Everyone needs access to our MAC server (file server) currently we access this by typing the server name and accessing the shares.
3. We have 2 win (application servers) servers that not everyone needs to have access to.

My question is: Do we need LDAP? thanks

---

### Post by Harlequin on 2008-03-14
> **cocotu said:**
> Not sure if we need LDAP in our case:

1. We have around 30 users: 50% PC, 50% MACs
2. Everyone needs access to our MAC server (file server) currently we access this by typing the server name and accessing the shares.
3. We have 2 win (application servers) servers that not everyone needs to have access to.

My question is: Do we need LDAP? thanks

You never "need" Ldap.  However it does give advantages in managing your users and what they can and can't access.  At the moment do all your users log in the your file server anonymously (ie can they all access everything) or do they each have their own user names.

If they all login in as the same user and this is ok security and privacy wise then LDAP doesn't have great uses for you...  If they log in individually or you want them to LDAP allows you to have all the user details stored in one place.  

Every user tends to have a desktop login, a mail login and a file share login at the minimum.  Quite often you can add a webmail login, a database login and dependent on you system a proxy log in as well.  So you are looking at a min of 3+ usernames and passwords per user.  The LDAP server allows all of these different servers to just look in the one place to see if the user details are corrects and whether they have permission to access the resource they a connecting to.  This means that you and the user only have to keep track of 1 username and password per user rather than multiple.

You have a minimum of 5 systems that some people need to log in to... LDAP will mean you can manage them infinitely easier then you can atm.  Its not necessary to have an LDAP system but once set up you will lovce it.

---

