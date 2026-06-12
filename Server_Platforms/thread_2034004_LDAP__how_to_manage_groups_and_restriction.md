---
title: "LDAP : how to manage groups and restriction"
date: 2012-07-27
forum: Server Platforms
---

### Post by LeftFoot on 2012-07-27
Hi there.

I have set up a openLDAP server.
Now, a user can log into a server by using a LDAP server.
Wonderful, not next steps, I would like to :

-When a user log in the first time either :
   +create a group name like the user and assign the user to it
     (right now all LDAP users end up in the group 'root' !!
   or
   + Asign all user to a local group called "ldapusers"
     Sure I can add into group.conf this :
                         *;*;*;Al0000-2400;ldapusers
    but I do not want everybody (even local users) to be in this group by default

-Control who can log in into a specific server with a group on the LDAP server.
   Let's say I create a group called "Access_Server1"  n the LDAP server : then I want only users on that group to be able to ssh into 'Server1'
  Any pointer about how to do that ?


Thx for any assistance !

LeftFoot

---

### Post by luvshines on 2012-07-31
> **LeftFoot said:**
> 
-Control who can log in into a specific server with a group on the LDAP server.
   Let's say I create a group called "Access_Server1"  n the LDAP server : then I want only users on that group to be able to ssh into 'Server1'
  Any pointer about how to do that ?


For ssh there is a control parameter in sshd_config file, AllowGroups (do man sshd_config for details) which controls the groups which can login with ssh.
Use with care, I think once you mention this in the config all the groups who need ssh shud be listed, even the local ones too.

---

