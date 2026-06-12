---
title: "Ubuntu 12.04.3 OpenLDAP configuration"
date: 2014-01-11
forum: Server Platforms
---

### Post by josephrushdoony on 2014-01-11
I am in the process of migration a Centos5 OpenLDAP server over to Ubuntu 12.04.3, and I am running in to an issue with the initial configuration. I am trying to replication the structure that was setup by the  admin a couple of years back (who is no longer around), but I have been unsuccessful at it. I am hoping that someone could point me in the right direction. The structure of the original install is as follows:

 

 First the login:

 Login DN: cn=Manager,o=sun
 

 Structure:
 The top structure only has “o=sun”, no “dc=sun, dc=net”. Then: “ou=Groups, o=sun”,“ou=Users, o=sun”, “sambaDomainName=SUNSERVER”, and “Create new entry here”.

 

 I am new to OpenLDAP, I have been using the following how-to, successfully, but I have not been able to achieve the desired results.
 

 [http://ideasnet.wordpress.com/2012/10/31/ideas-server-how-to-install-and-set-openldap-in-ubuntu-12-04lts-server-edition-part-1/](http://ideasnet.wordpress.com/2012/10/31/ideas-server-how-to-install-and-set-openldap-in-ubuntu-12-04lts-server-edition-part-1/)
 

 Thanks in advance,
 Joe

---

### Post by sandyd on 2014-01-12
Which part are you stuck on?

Once youve configured OpenLDAP and set a password for cn=config, you may want to use Apache Directory Studio instead of the CLI - much much easier to mange OpenLDAP with it

---

### Post by josephrushdoony on 2014-01-12
Using the how-to above I cannot get the login to be "cn=Manager,o=sun" and the top of the strucutre to be "o=sun" without having any "dc=sun,dc=net". I cannot seem to wrap my mind around it.

Thanks,
Joe

---

