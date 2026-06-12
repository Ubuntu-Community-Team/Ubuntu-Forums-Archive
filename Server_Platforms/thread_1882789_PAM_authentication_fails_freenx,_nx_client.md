---
title: "PAM authentication fails freenx, nx client"
date: 2011-11-17
forum: Server Platforms
---

### Post by biocyberman on 2011-11-17
Hello there, 
I was trying to reconfigure my PAM and LDAP setup and suddenly I can't login to my server running freenx with my nx client. My server is running Lucid Lynx LTS 64bit. I can still login via ssh. I have deleted the known_hosts file:
```

sudo rm /var/lib/nxserver/home/.ssh/known_hosts
```

I have purged and reinstalled freenx and OpenLDAP numerous times. Now I still have LDAP purged. 

On the client side at my Mac Lion, I got this:

```
The session negotiation failed.

Error is: connection timeout.
```

On the server side, where I enabled log_level 6:
```

-- NX SERVER START:  - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: nxuser
NX> 102 Password: 
Info: Auth method: ssh nxuser@127.0.0.1's password:
Info: Closing connection to slave with pid 4632.

NX> 404 ERROR: wrong password or login
NX> 999 Bye
-- NX SERVER START:  - ORIG_COMMAND=
-- NX SERVER START:  - ORIG_COMMAND=
Info: Using fds #4 and #3 for communication with nxnode.
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: nxuser
NX> 102 Password: 
```

I guess I have to make PAM LDAP work for me first before solving this. However, is there any quick solution to disable PAM LDAP totally and make nx client work first?

Many thanks for any suggestions. 

//
Biocyberman

---

### Post by luvshines on 2011-11-19
If I understand this correctly, you are not able to log into your Server which you were trying to configure against LDAP.
However you can still SSH to your server and now want to first remove the messed up LDAP config which is not allowing login on Server.

Is this right ?

If yes, check if pam_ldap happens to appear anywhere in the /etc/pam.d directory```
cd /etc/pam.d
grep pam_ldap *
```

---

### Post by biocyberman on 2011-11-19
Thanks, Luvshines. I should have checked out the pam_ldap file under /etc/pam.d/ as you suggested. However I solved it in another way. 

I did not find the direct cause of the problem, but I found I was following wrong OpenLdap server guide. I then read more about OpenLDAP in general at:
[http://www.openldap.org/doc/admin24/quickstart.html](http://www.openldap.org/doc/admin24/quickstart.html)

I then follow more carefully the guide for 10.04 LTS at:
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

Even though my LDAP server has not work perfectly, I got back my NX client connection now. 
So I consider the problem solved, and will continue to work on LDAP server configuration.

---

