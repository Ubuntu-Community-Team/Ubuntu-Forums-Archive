---
title: "LDAP Client can't find group"
date: 2009-04-19
forum: Server Platforms
---

### Post by smythsys on 2009-04-19
Good afternoon,

          I've got an LDAP server up and running (8.10 Ubuntu). The client can getent passwd, see teh ldap users and even su *ldapuser*.
 
         However when I try to login on the client laptop it says something like "could not establish user's group so you can't be allowed to log in, check with your administrator".
   
         It does that only for ldap users so it does get to the server.Users have been assigned to users group (1001 although I've tried GID 100).

¿What could be going on?

---

### Post by smythsys on 2009-04-19
Hi,
 
     I found this somewhere else. It seems the solution to this is as easy as restarting the client. Once that is done it works. Seems strange that it is not said in the manuals.

     It worked for me though!

---

