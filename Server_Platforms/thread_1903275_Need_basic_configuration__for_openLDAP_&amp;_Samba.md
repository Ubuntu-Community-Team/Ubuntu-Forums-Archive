---
title: "Need basic configuration  for openLDAP &amp; Samba ."
date: 2012-01-02
forum: Server Platforms
---

### Post by honey_bee on 2012-01-02
hi,
      I have successfully configured samba server on my ubuntu system.I want to add Open LDAP so that the client machines may authenticate with it.

Kindly guide me the basic configuration for OpenLDAP & samba.

thanks in advance,
honey

---

### Post by rsvancara on 2012-01-02
There are many tutorials online for this sort of thing.  The configuration is not very basic and you need need to make some choices about how to set up your LDAP server.

For SAMBA, I would check out the samba documentation.  There are some good examples of what you need to include and also there is a samba schema you need to load as well.

For Authentication and Authorization, you need to make sure you have the NIS schema loaded so that you will have all the posix account attributes.  

There are several things you need to configure:

1.  /etc/smb.conf
2.  /etc/nsswitch.conf
3.  /etc/pam.d/
4.  /etc/ldap.conf
5.  LDAP schema configuration, depending on how you setup LDAP the configuration for this will vary.

There are several configuration files involved depending on your implementation.

---

### Post by honey_bee on 2012-01-12
Thanks "rsvancara" for your reply. Well at the moment i have only windows xp machine and one ubuntu server in my non production enviroment. If I successfully join with one computer & authenticate it wih LDAP server then I can also do it in production enviroment.
 
As you said > "For Authentication and Authorization, you need to make sure you have the NIS schema loaded so that you will have all the posix account attributes."
 
Kindly just explain  it a little bit ?
 
thank again for your valuable guidance,
 
honey

---

